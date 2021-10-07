---
title: Recherchez les menaces sur les appareils, les e-mails, les applications et les identités avec le chasse avancée
description: Étudiez les scénarios de chasse courants et les exemples de requêtes qui couvrent les appareils, les e-mails, les applications et les identités.
keywords: recherche avancée, données Office365, appareils Windows, normalisation des e-mails Office365, courriers électroniques, applications, identités, recherche de menace, recherche, requête, télémétrie, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 9058d0e80d2c37009ad340f7b50424ea1bbb6ab7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60210756"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>Repérer des menaces sur les appareils, les e-mails, les applications, et les identités

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[Le recherche avancée](advanced-hunting-overview.md) dans Microsoft 365 Defender vous permet de chercher de manière proactive les menaces dans :
- Appareils gérés par Microsoft Defender pour le point de terminaison
- Courriers électroniques traitées par Microsoft 365
- Activités des applications cloud, événements d’authentification et activités de contrôleur de domaine suivis par Microsoft Cloud App Security et Microsoft Defender pour l’identité

Avec ce niveau de visibilité, vous pouvez rapidement chercher les menaces qui traversent des sections de votre réseau, y compris les intrusions sophistiquées qui arrivent sur le courrier électronique ou le web, élever les privilèges locaux, acquérir des informations d’identification de domaine privilégiées et passer par la suite sur vos appareils. 

Voici des techniques générales et des exemples de requêtes basés sur différents scénarios de chasse qui peuvent vous aider à explorer la façon dont vous pouvez créer des requêtes lors du recherche de menaces aussi sophistiquées.

## <a name="get-entity-info"></a>Obtenir des informations sur l’entité
Utilisez ces requêtes pour savoir comment obtenir rapidement des informations sur les comptes d’utilisateur, les appareils et les fichiers. 

### <a name="obtain-user-accounts-from-email-addresses"></a>Obtenir des comptes d’utilisateur des adresses de messagerie électronique :
Lorsque vous construisez des requêtes sur des [tableaux qui traitent des appareils et des e-mail](advanced-hunting-schema-tables.md), vous devez peut-être obtenir des noms de compte d’utilisateur à partir des adresses e-mail d’expéditeur ou de destinataire. Vous pouvez généralement le faire pour l’adresse du destinataire ou de l’expéditeur à l’aide de l’hôte local à partir de l’adresse *e-mail.*

Dans l’extrait de code ci-dessous, nous utilisons la fonction [tostring()](/azure/data-explorer/kusto/query/tostringfunction) Kusto pour extraire l’hôte local juste avant les adresses de messagerie du destinataire dans `@` la `RecipientEmailAddress` colonne.

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

Vous pouvez obtenir des noms de compte et d’autres informations de compte en fusionnant ou en rejoignant la [table IdentityInfo](advanced-hunting-identityinfo-table.md). La requête ci-dessous obtient la liste des détections de hameçonnage et de programmes malveillants à partir de la [table EmailEvents,](advanced-hunting-emailevents-table.md) puis joint ces informations au tableau pour obtenir des informations détaillées sur chaque `IdentityInfo` destinataire. 

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

### <a name="get-device-information"></a>Obtenir des informations sur l’appareil
Le [schéma de recherche avancé fournit des](advanced-hunting-schema-tables.md) informations complètes sur l’appareil dans différents tableaux. Par exemple, le tableau [DeviceInfo fournit](advanced-hunting-deviceinfo-table.md) des informations complètes sur l’appareil en fonction des données d’événements agrégées régulièrement. Cette requête utilise la table pour vérifier si un utilisateur potentiellement compromis ( ) s’est connecté à des appareils, puis répertorie les alertes qui ont été déclenchées sur `DeviceInfo` `<account-name>` ces appareils.

>[!Tip]
> Cette requête permet de spécifier une jointure interne, ce qui empêche `kind=inner` la déduplication des valeurs côté [](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor)gauche pour `DeviceId` .

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


### <a name="get-file-event-information"></a>Obtenir des informations sur les événements de fichier

Utilisez la requête suivante pour obtenir des informations sur les événements liés au fichier. 

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

Utilisez l’exemple de requête suivant pour voir tous les appareils exécutant macOS avec une version antérieure à Celle-ci.

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

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>List logon activities of users that received emails that were notpé successfully
[La purge automatique d’heure zéro (ZAP)](../office-365-security/zero-hour-auto-purge.md) adresse les e-mails malveillants après leur réception. En cas d’échec de ZAP, du code malveillant peut éventuellement s’exécuter sur l’appareil et laisser les comptes compromis. Cette requête vérifie si l’activité de la logon est réalisée par les destinataires des e-mails qui n’ont pas été correctement adressés par ZAP.

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
Cette requête identifie d’abord toutes les alertes d’accès aux informations d’identification dans la `AlertInfo` table. Il fusionne ou joint ensuite la table, qu’il recherche uniquement pour les noms des comptes ciblés et les filtres pour les comptes `AlertEvidence` joints au domaine. Enfin, il vérifie la table pour obtenir toutes les activités d’accès par les comptes ciblés `IdentityLogonEvents` joints au domaine.

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
En supposant que vous connaissez une adresse de messagerie envoyant des fichiers malveillants ( ), vous pouvez exécuter cette requête pour déterminer si des fichiers de cet expéditeur existent `MaliciousSender@example.com` sur vos appareils. Vous pouvez utiliser cette requête, par exemple, pour identifier les appareils affectés par une campagne de distribution de programmes malveillants.

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
Les e-mails malveillants contiennent souvent des documents et d'autres pièces jointes spécialement conçues qui exécutent des commandes PowerShell pour offrir d'autres charges utiles. Si vous avez connaissance d’e-mails provenant d’un expéditeur malveillant connu ( ), vous pouvez utiliser cette requête pour ré lister et passer en revue les activités PowerShell qui se sont produites dans les 30 minutes après la réception d’un e-mail de `MaliciousSender@example.com` l’expéditeur.  

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

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
