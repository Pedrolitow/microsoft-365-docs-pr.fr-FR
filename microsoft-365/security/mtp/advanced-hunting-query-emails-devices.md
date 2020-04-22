---
title: Trouvez des menaces sur divers appareils et messages électroniques à l’aide du repérage avancé
description: Étudiez les scénarios de repérage et les exemples de requêtes qui couvrent les appareils et les courriers électroniques.
keywords: repérage avancé, données Office 365, appareils Windows, normalisation des e-mails Office365, e-mails, repérage de menace, cybermenace, recherche, requête, télémétrie, Microsoft 365, Protection Microsoft contre les menaces
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: ec7f9083401fdf7a2114d99ddd2dcc009411e34b
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43633506"
---
# <a name="hunt-for-threats-across-devices-and-emails"></a>Repérer les menaces sur divers appareils et e-mails

**S’applique à :**
- Protection Microsoft contre les menaces



La recherche [avancée](advanced-hunting-overview.md) dans la protection de Microsoft contre les menaces vous permet de rechercher de façon proactive les menaces entre vos appareils Windows et vos courriers électroniques Microsoft. Voici quelques scénarios de repérage et exemples de requêtes qui peuvent vous aider à découvrir comment créer des requêtes sur les appareils et les e-mails.

## <a name="obtain-user-accounts-from-email-addresses"></a>Obtenir des comptes d’utilisateur des adresses de messagerie électronique :
Lorsque vous construisez des requêtes sur des [tableaux qui traitent des appareils et des e-mail](advanced-hunting-schema-tables.md), vous devez peut-être obtenir des noms de compte d’utilisateur à partir des adresses e-mail d’expéditeur ou de destinataire. Pour ce faire, utilisez l'*hôte local* de l'adresse e-mail :

```kusto
AccountName = tostring(split(SenderFromAddress, "@")[0])
```

Cette technique de normalisation est utilisée dans les scénarios suivants.

## <a name="hunting-scenarios"></a>Scénarios de repérage

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>Vérifier si les fichiers d’un expéditeur malveillant connu figurent sur vos appareils
En supposant que vous savez qu’une adresse e-mail envoie des fichiers malveillants, vous pouvez exécuter cette requête pour déterminer si des fichiers de cet expéditeur existent sur vos appareils. Vous pouvez utiliser cette requête (par exemple, pour déterminer le nombre d’appareils concernés par une campagne de distribution de programmes malveillants).

```kusto
//Get prevalence of files sent by a malicious sender in your organization
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
| where isnotempty(SHA256)
| join (
DeviceFileEvents
| project FileName, SHA256
) on SHA256
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>Examiner les tentatives de connexion après la réception des e-mails malveillants
Cette requête recherche les 10 dernières connexions effectuées par les destinataires du courrier dans un délai de 30 minutes après la réception des e-mails malveillants connus. Vous pouvez utiliser cette requête pour vérifier si les comptes des destinataires de l’e-mail ont été compromis.

```kusto
//Find logons that occurred right after malicious email was received
let MaliciousEmail=EmailEvents
| where MalwareFilterVerdict == "Malware" 
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmail
| join (
DeviceLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>Examiner les activités PowerShell après réception d'e-mails d'expéditeurs malveillants connus.
Les e-mails malveillants contiennent souvent des documents et d'autres pièces jointes spécialement conçues qui exécutent des commandes PowerShell pour offrir d'autres charges utiles. Si vous connaissez les e-mails provenant d’un expéditeur malveillant connu, vous pouvez utiliser cette requête pour répertorier et examiner les activités PowerShell qui se sont produites dans un délai de 30 minutes après la réception d’un e-mail envoyé par l’expéditeur.  

```kusto
//Find PowerShell activities right after email was received from malicious sender
let x=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
x
| join (
DeviceProcessEvents
| where FileName =~ "powershell.exe"
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
