---
title: Recherche de menaces sur les appareils, les e-mails, les applications et les identités à l’aide de la chasse avancée
description: Étude des scénarios de chasse courants et des exemples de requêtes couvrant les appareils, les e-mails, les applications et les identités.
keywords: chasse avancée, données Office 365, appareils Windows, normalisation des courriers électroniques Office 365, e-mails, applications, identités, recherche de menace, recherche de menace, recherche, requête, télémétrie, Microsoft 365, protection contre les menaces Microsoft
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 9f5468ccb853bbbe126198a14f7b824d953a2738
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48412633"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Recherche de menaces sur les appareils, les e-mails, les applications et les identités

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

La recherche [avancée](advanced-hunting-overview.md) dans Microsoft Threat Protection vous permet de rechercher de façon proactive les menaces parmi les éléments suivants :
- Appareils gérés par Microsoft Defender ATP
- Messages électroniques traités par Microsoft 365
- Activités d’application Cloud, événements d’authentification et activités de contrôleur de domaine suivis par Microsoft Cloud App Security and Azure ATP

Ce niveau de visibilité vous permet de rechercher rapidement les menaces qui traversent les sections de votre réseau, notamment les intrusions sophistiquées qui arrivent sur le courrier électronique ou le Web, d’élever les privilèges locaux, d’acquérir des informations d’identification de domaine privilégié et de se déplacer par la suite vers l’ensemble de vos appareils. 

Voici des techniques générales et des exemples de requêtes basés sur différents scénarios de chasse qui peuvent vous aider à découvrir comment créer des requêtes lors de la recherche de ces menaces sophistiquées.

## <a name="get-entity-info"></a>Obtenir des informations sur l’entité
Utilisez ces requêtes pour savoir comment obtenir rapidement des informations sur les comptes d’utilisateur, les appareils et les fichiers. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Obtenir des comptes d’utilisateur des adresses de messagerie électronique :
Lorsque vous construisez des requêtes sur des [tableaux qui traitent des appareils et des e-mail](advanced-hunting-schema-tables.md), vous devez peut-être obtenir des noms de compte d’utilisateur à partir des adresses e-mail d’expéditeur ou de destinataire. Vous pouvez généralement effectuer cette opération pour le destinataire ou l’adresse de l’expéditeur à l’aide de l' *hôte local* à partir de l’adresse de messagerie.

Dans l’extrait de code ci-dessous, nous utilisons la fonction [ToString ()](https://docs.microsoft.com/azure/data-explorer/kusto/query/tostringfunction) Kusto pour extraire le droit de l’hôte local avant les `@` adresses de messagerie des destinataires dans la colonne `RecipientEmailAddress` .

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
La requête ci-dessous illustre l’utilisation de cet extrait de code :

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>Fusionner la table IdentityInfo

Vous pouvez obtenir des noms de compte et d’autres informations de compte en fusionnant ou en joignant la [table IdentityInfo](advanced-hunting-identityinfo-table.md). La requête ci-dessous obtient la liste des détections de hameçonnage et de programmes malveillants dans la [table EmailEvents](advanced-hunting-emailevents-table.md) , puis joint ces informations à la `IdentityInfo` table pour obtenir des informations détaillées sur chaque destinataire. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where MalwareFilterVerdict == 'Malware' or PhishFilterVerdict == 'Phish'
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, PhishFilterVerdict, MalwareFilterVerdict,
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

### <a name="get-device-information"></a>Obtenir des informations sur les appareils
Le [schéma de chasse avancé](advanced-hunting-schema-tables.md) fournit des informations détaillées sur l’appareil dans différentes tables. Par exemple, le [tableau DeviceInfo](advanced-hunting-deviceinfo-table.md) fournit des informations complètes sur l’appareil en fonction des données d’événements regroupées régulièrement. Cette requête utilise la `DeviceInfo` table pour vérifier si un utilisateur potentiellement compromis () s' `<account-name>` est connecté à un appareil, puis répertorie les alertes déclenchées sur ces appareils.

>[!Tip]
> Cette requête utilise `kind=inner` pour spécifier une [jointure interne](https://docs.microsoft.com/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor), ce qui empêche la déduplication des valeurs côté gauche de `DeviceId` .

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```

## <a name="hunting-scenarios"></a>Scénarios de repérage

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Répertorier les activités de connexion des utilisateurs qui ont reçu des courriers électroniques qui n’ont pas été zapped
La [purge automatique à zéro heure (ZAP)](../office-365-security/zero-hour-auto-purge.md) traite les messages électroniques malveillants une fois qu’ils ont été reçus. Si l’opération ZAP échoue, le code malveillant peut finir par s’exécuter sur l’appareil et laisser des comptes compromis. Cette requête vérifie l’activité d’ouverture de session effectuée par les destinataires des messages électroniques qui n’ont pas été correctement traités par ZAP.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Obtenir des tentatives de connexion par des comptes de domaine ciblés par le vol d’informations d’identification
Cette requête identifie d’abord toutes les alertes d’accès aux informations d’identification dans le `AlertInfo` tableau. Il fusionne ou rejoint la `AlertEvidence` table, qu’elle analyse pour les noms des comptes et filtres ciblés pour les comptes joints au domaine uniquement. Enfin, il vérifie le `IdentityLogonEvents` tableau pour obtenir toutes les activités d’ouverture de session par les comptes ciblés joints au domaine.

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Vérifier si les fichiers d’un expéditeur malveillant connu figurent sur vos appareils
En supposant que vous connaissiez une adresse de messagerie qui envoie des fichiers malveillants ( `MaliciousSender@example.com` ), vous pouvez exécuter cette requête pour déterminer si les fichiers de cet expéditeur existent sur vos appareils. Vous pouvez utiliser cette requête, par exemple, pour identifier les appareils affectés par une campagne de distribution de programmes malveillants.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Examiner les tentatives de connexion après la réception des e-mails malveillants
Cette requête recherche les 10 dernières connexions effectuées par les destinataires du courrier dans un délai de 30 minutes après la réception des e-mails malveillants connus. Vous pouvez utiliser cette requête pour vérifier si les comptes des destinataires de l’e-mail ont été compromis.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where MalwareFilterVerdict == "Malware"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Examiner les activités PowerShell après réception d'e-mails d'expéditeurs malveillants connus.
Les e-mails malveillants contiennent souvent des documents et d'autres pièces jointes spécialement conçues qui exécutent des commandes PowerShell pour offrir d'autres charges utiles. Si vous êtes conscient des e-mails provenant d’un expéditeur malveillant connu ( `MaliciousSender@example.com` ), vous pouvez utiliser cette requête pour répertorier et passer en revue les activités PowerShell qui se sont produites dans les 30 minutes suivant la réception d’un message électronique de l’expéditeur.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
