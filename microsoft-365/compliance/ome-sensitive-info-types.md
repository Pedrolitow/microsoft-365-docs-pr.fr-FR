---
title: Créer une stratégie de type d’informations sensibles à l’aide de Office 365 Message Encryption
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- tier1
- purview-compliance
- Strat_O365_Enterprise
description: Découvrez comment créer une stratégie de type d’informations sensibles pour votre organisation à l’aide de Office 365 Chiffrement des messages.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: a3c6797750c25e876e1df159d75f1a269decee80
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68634539"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Créer une stratégie de type d’informations sensibles pour votre organisation à l’aide du chiffrement des messages

Vous pouvez utiliser des règles de flux de messagerie Exchange ou la protection contre la perte de données (DLP) Microsoft Purview pour créer une stratégie de type d’informations sensibles avec Office 365 Chiffrement des messages. Pour créer une règle de flux de messagerie Exchange, vous pouvez utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange (EAC)</a> ou PowerShell.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Pour créer la stratégie à l’aide de règles de flux de messagerie dans le CAE

Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> et accédez aux **règles** de **flux de messagerie** > . Dans la page Règles, créez une règle qui s’applique Office 365 chiffrement des messages. Vous pouvez créer une règle basée sur des conditions telles que la présence de certains mots clés ou types d’informations sensibles dans le message ou la pièce jointe.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Pour créer la stratégie à l’aide de règles de flux de messagerie dans PowerShell

Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Utilisez les applets de commande Set-IRMConfiguration et New-TransportRule pour créer la stratégie.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Exemple de règle de flux de messagerie créée avec PowerShell

Exécutez les commandes suivantes dans PowerShell pour créer une règle de flux de messagerie Exchange qui chiffre automatiquement les e-mails envoyés en dehors de votre organisation avec l’option chiffrer uniquement si les e-mails ou leurs pièces jointes contiennent les types d’informations sensibles suivants :

- Numéro de routage ABA
- Numéro de carte de crédit
- Numéro de l’Agence de contrôle de la drogue (DEA)
- États-Unis / Royaume-Uni numéro de passeport
- Numéro de compte bancaire américain
- Numéro d’identification fiscale individuel (ITIN) États-Unis
- Numéro de sécurité sociale (SSN) États-Unis

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Pour plus d’informations, consultez [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) et [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Comment les destinataires accèdent aux pièces jointes

Une fois que Microsoft a chiffré un message, les destinataires ont un accès illimité aux pièces jointes lorsqu’ils accèdent et ouvrent leur courrier chiffré.

## <a name="to-prepare-for-this-change"></a>Pour préparer ce changement

Vous souhaiterez peut-être mettre à jour la documentation et le matériel de formation des utilisateurs finaux applicables pour préparer les membres de votre organisation à cette modification. Partagez ces ressources Office 365 Message Encryption avec vos utilisateurs selon les besoins :

- [Envoyer, afficher et répondre à des messages chiffrés dans Outlook pour PC](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Vidéo Microsoft 365 Essentials : Chiffrement des messages](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Afficher ces modifications dans le journal d’audit

Microsoft 365 audite cette activité et la met à la disposition des administrateurs. L’opération est « New-TransportRule » et un extrait d’un exemple d’entrée d’audit de la recherche dans le journal d’audit dans le Centre de sécurité & conformité est ci-dessous :

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"...etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Pour désactiver ou personnaliser la stratégie de types d’informations sensibles

Une fois que vous avez créé la règle de flux de messagerie Exchange, vous pouvez [désactiver ou modifier la règle](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) en accédant aux **règles** de **flux** >  de messagerie dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> et en désactivant la règle « *Chiffrer les e-mails sensibles sortants (règle out of box)* ».
