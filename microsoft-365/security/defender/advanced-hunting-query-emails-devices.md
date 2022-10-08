---
title: Rechercher les menaces sur les appareils, les e-mails, les applications et les identités avec repérage avancé
description: Étudiez les scénarios de chasse courants et les exemples de requêtes qui couvrent les appareils, les e-mails, les applications et les identités.
keywords: repérage avancé, données Office365, appareils Windows, messages électroniques Office 365 normalisés, e-mails, applications, identités, repérage des menaces, repérage de cybermenaces, recherche, requête, télémétrie, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: article
ms.openlocfilehash: 8be215f0b9707e6f8d53787433f49d8d1af9b3da
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066957"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Repérer des menaces sur les appareils, les e-mails, les applications, et les identités

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[La chasse avancée](advanced-hunting-overview.md) dans Microsoft 365 Defender vous permet de rechercher de manière proactive les menaces :
- Appareils gérés par Microsoft Defender pour point de terminaison
- E-mails traités par Microsoft 365
- Activités d’application cloud, événements d’authentification et activités de contrôleur de domaine suivies par Microsoft Defender for Cloud Apps et Microsoft Defender pour Identity

Avec ce niveau de visibilité, vous pouvez rapidement rechercher les menaces qui traversent des sections de votre réseau, notamment les intrusions sophistiquées qui arrivent sur le courrier électronique ou le web, élever les privilèges locaux, acquérir des informations d’identification de domaine privilégiés et passer latéralement sur vos appareils. 

Voici des techniques générales et des exemples de requêtes basés sur différents scénarios de chasse qui peuvent vous aider à explorer comment vous pouvez construire des requêtes lors de la recherche de menaces aussi sophistiquées.

## <a name="get-entity-info"></a>Obtenir des informations sur l’entité
Utilisez ces requêtes pour découvrir comment obtenir rapidement des informations sur les comptes d’utilisateur, les appareils et les fichiers. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Obtenir des comptes d’utilisateur des adresses de messagerie électronique :
Lorsque vous construisez des requêtes sur des [tableaux qui traitent des appareils et des e-mail](advanced-hunting-schema-tables.md), vous devez peut-être obtenir des noms de compte d’utilisateur à partir des adresses e-mail d’expéditeur ou de destinataire. Vous pouvez généralement effectuer cette opération pour le destinataire ou l’adresse de l’expéditeur à l’aide de l’hôte local à partir de l’adresse *e-mail* .

Dans l’extrait de code ci-dessous, nous utilisons la fonction Kusto [tostring()](/azure/data-explorer/kusto/query/tostringfunction) pour extraire l’hôte local juste avant les `@` adresses e-mail du destinataire dans la colonne `RecipientEmailAddress`.

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
La requête ci-dessous montre comment cet extrait de code peut être utilisé :

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>Fusionner la table IdentityInfo

Vous pouvez obtenir des noms de compte et d’autres informations de compte en fusionnant ou en joignant la [table IdentityInfo](advanced-hunting-identityinfo-table.md). La requête ci-dessous obtient la liste des détections de hameçonnage et de programmes malveillants à partir de la [table EmailEvents](advanced-hunting-emailevents-table.md) , puis joint ces informations à la `IdentityInfo` table pour obtenir des informations détaillées sur chaque destinataire. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where ThreatTypes has "Malware" or ThreatTypes has "Phish"
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, ThreatTypes, 
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

Regardez cette [courte vidéo](https://www.youtube.com/watch?v=8qZx7Pp5XgM) pour découvrir comment utiliser Langage de requête Kusto pour joindre des tables.  

### <a name="get-device-information"></a>Obtenir des informations sur l’appareil

Le [schéma de chasse avancé](advanced-hunting-schema-tables.md) fournit des informations détaillées sur les appareils dans différentes tables. Par exemple, la [table DeviceInfo](advanced-hunting-deviceinfo-table.md) fournit des informations complètes sur l’appareil en fonction des données d’événement agrégées régulièrement. Cette requête utilise la `DeviceInfo` table pour vérifier si un utilisateur potentiellement compromis (`<account-name>`) s’est connecté à des appareils, puis répertorie les alertes qui ont été déclenchées sur ces appareils.

>[!Tip]
> Cette requête utilise `kind=inner` pour spécifier une [jointure interne](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor), ce qui empêche la déduplication des valeurs de gauche pour `DeviceId`.

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


### <a name="get-file-event-information"></a>Obtenir des informations sur l’événement de fichier

Utilisez la requête suivante pour obtenir des informations sur les événements liés aux fichiers. 

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceFileEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="get-network-event-information"></a>Obtenir des informations sur les événements réseau

Utilisez la requête suivante pour obtenir des informations sur les événements liés au réseau.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-agent-version-information"></a>Obtenir les informations de version de l’agent d’appareil

Utilisez la requête suivante pour obtenir la version de l’agent en cours d’exécution sur un appareil.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="example-query-for-macos-devices"></a>Exemple de requête pour les appareils macOS

Utilisez l’exemple de requête suivant pour voir tous les appareils exécutant macOS avec une version antérieure à Catalina.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OSPlatform == "macOS" and  OSVersion !contains "10.15" and OSVersion !contains "11."
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-status-info"></a>Obtenir les informations d’état de l’appareil

Utilisez la requête suivante pour obtenir l’état d’un appareil. Dans l’exemple suivant, la requête vérifie si l’appareil est intégré.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OnboardingStatus != "Onboarded"
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


## <a name="hunting-scenarios"></a>Scénarios de repérage

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>Répertorier les activités d’ouverture de session des utilisateurs qui ont reçu des e-mails qui n’ont pas été ajoutés avec succès

[Le vidage automatique de zéro heure (ZAP) traite les e-mails](../office-365-security/zero-hour-auto-purge.md) malveillants une fois qu’ils ont été reçus. Si ZAP échoue, le code malveillant peut éventuellement s’exécuter sur l’appareil et laisser les comptes compromis. Cette requête recherche l’activité d’ouverture de session effectuée par les destinataires des e-mails qui n’ont pas été traités avec succès par ZAP.

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

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>Obtenir des tentatives d’ouverture de session par des comptes de domaine ciblés par le vol d’informations d’identification

Cette requête identifie d’abord toutes les alertes d’accès aux informations d’identification dans la `AlertInfo` table. Il fusionne ou joint ensuite la `AlertEvidence` table, qu’il analyse uniquement pour les noms des comptes ciblés et les filtres pour les comptes joints à un domaine. Enfin, il vérifie la `IdentityLogonEvents` table pour obtenir toutes les activités d’ouverture de session par les comptes ciblés joints à un domaine.

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

En supposant que vous savez qu’une adresse e-mail envoie des fichiers malveillants (`MaliciousSender@example.com`), vous pouvez exécuter cette requête pour déterminer si des fichiers de cet expéditeur existent sur vos appareils. Vous pouvez utiliser cette requête, par exemple, pour identifier les appareils affectés par une campagne de distribution de programmes malveillants.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256, DeviceName, DeviceId
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Examiner les tentatives de connexion après la réception des e-mails malveillants

Cette requête recherche les 10 dernières connexions effectuées par les destinataires du courrier dans un délai de 30 minutes après la réception des e-mails malveillants connus. Vous pouvez utiliser cette requête pour vérifier si les comptes des destinataires de l’e-mail ont été compromis.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where ThreatTypes has "Malware" 
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

Les e-mails malveillants contiennent souvent des documents et d'autres pièces jointes spécialement conçues qui exécutent des commandes PowerShell pour offrir d'autres charges utiles. Si vous êtes au courant des e-mails provenant d’un expéditeur malveillant connu (`MaliciousSender@example.com`), vous pouvez utiliser cette requête pour répertorier et examiner les activités PowerShell qui se sont produites dans les 30 minutes suivant la réception d’un e-mail de l’expéditeur.  

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
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
