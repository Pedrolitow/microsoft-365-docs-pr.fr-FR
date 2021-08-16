---
title: Créer une stratégie de type d’informations sensibles à l’aide chiffrement de messages Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- Strat_O365_Enterprise
description: Découvrez comment créer une stratégie de type d’informations sensibles pour votre organisation à l’aide de chiffrement de messages Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1cf9432adbe2cecb889d6e744077d8807ae556089b388f321e1348199e1ee165
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53879286"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Créer une stratégie de type d’informations sensibles pour votre organisation à l’aide du chiffrement de messages

Vous pouvez utiliser les Exchange de flux de messagerie ou la protection contre la perte de données (DLP) pour créer une stratégie de type d’informations sensibles avec chiffrement de messages Office 365. Pour créer une règle Exchange flux de messagerie, vous pouvez utiliser le Centre d’administration Exchange (EAC) ou PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Pour créer la stratégie à l’aide de règles de flux de messagerie dans le EAC

Connectez-vous au Centre Exchange’administration centrale (EAC) et allez aux **règles de flux de**  >  **messagerie.** Dans la page Règles, créez une règle qui s’applique chiffrement de messages Office 365. Vous pouvez créer une règle basée sur des conditions telles que la présence de certains mots clés ou types d’informations sensibles dans le message ou la pièce jointe.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Pour créer la stratégie à l’aide de règles de flux de messagerie dans PowerShell

Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Utilisez les cmdlets Set-IRMConfiguration et New-TransportRule pour créer la stratégie.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Exemple de règle de flux de messagerie créée avec PowerShell

Exécutez les commandes suivantes dans PowerShell pour créer une règle de flux de messagerie Exchange qui chiffre automatiquement les messages électroniques envoyés à l’extérieur de votre organisation avec l’option chiffrer uniquement si les messages électroniques ou leurs pièces jointes contiennent les types d’informations sensibles suivants :

- Numéro de routage ABA
- Numéro de carte de crédit
- Numéro de la Drug Enforcement Agency (DEA)
- États-Unis/Royaume-Uni numéro de passeport
- Numéro de compte bancaire américain
- Numéro d’identification fiscale individuel (ITIN) États-Unis
- Numéro de sécurité sociale (SSN) États-Unis

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Pour plus d’informations, [voir Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) et [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Accès des destinataires aux pièces jointes

Une fois que Microsoft a chiffré un message, les destinataires ont un accès illimité aux pièces jointes lorsqu’ils accèdent à leurs messages électroniques chiffrés et les ouvrent.

## <a name="to-prepare-for-this-change"></a>Pour préparer cette modification

Vous pouvez mettre à jour la documentation et les supports de formation applicables aux utilisateurs finaux pour préparer les membres de votre organisation à cette modification. Partagez ces chiffrement de messages Office 365 ressources avec vos utilisateurs, le cas échéant :

- [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 Vidéo Essentials : chiffrement Office messages](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Afficher ces modifications dans le journal d’audit

Microsoft 365 audite cette activité et la met à la disposition des administrateurs. L’opération est « New-TransportRule » et un extrait d’un exemple d’entrée d’audit du Centre de sécurité et conformité du journal d'& audit se trouve ci-dessous :

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"…etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Pour désactiver ou personnaliser la stratégie des types d’informations sensibles

Une fois que vous avez créé la règle [](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) de flux de messagerie Exchange, vous pouvez désactiver ou modifier la règle en allant dans Règles de flux de messagerie dans le Centre d’administration Exchange (EAC) et en désactivant la règle « Chiffrer les messages électroniques   >   *sensibles sortants (règle* d’envoi) ».