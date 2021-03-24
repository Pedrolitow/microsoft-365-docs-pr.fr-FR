---
title: Révoquer le courrier électronique chiffré par le chiffrement de messages avancé
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 06/11/2020
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: En tant qu’administrateur et expéditeur de message, vous pouvez révoquer certains messages électroniques qui ont été chiffrés avec le chiffrement de messages avancé Office 365.
ms.openlocfilehash: 340a9e73dba50e28223ee561db749a089c649df6
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051716"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Révoquer le courrier électronique chiffré par le chiffrement de messages avancé

La révocation du courrier électronique est proposée dans le cadre du chiffrement avancé des messages Office 365. Le chiffrement de messages avancé Office 365 est inclus dans [Microsoft 365 Entreprise E5,](https://www.microsoft.com/microsoft-365/enterprise/home)Office 365 E5, Microsoft 365 E5 (tarifs pour le personnel à but non lucratif), Office 365 Entreprise E5 (prix du personnel à but non lucratif) et Office 365 Éducation A5. Si votre organisation dispose d’un abonnement qui n’inclut pas le chiffrement de messages avancé Office 365, vous pouvez l’acheter avec le module SKU de conformité Microsoft 365 E5 pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou le module SKU de conformité avancée Office 365 pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou Office 365 SKU.

Cet article fait partie d’une série plus importante d’articles sur le chiffrement de [messages Office 365.](ome.md)

Si un message a été chiffré à l’aide du chiffrement de messages avancé Office 365 et que vous êtes un administrateur Microsoft 365 ou si vous êtes l’expéditeur du message, vous pouvez révoquer le message dans certaines conditions. Les administrateurs révoquent les messages à l’aide de PowerShell. En tant qu’expéditeur, vous révoquez un message que vous avez envoyé directement à partir d’Outlook sur le web. Cet article décrit les circonstances dans lesquelles la révocation est possible et comment le faire.
  
## <a name="encrypted-emails-that-you-can-revoke"></a>Messages électroniques chiffrés que vous pouvez révoquer

Les administrateurs et les expéditeurs de messages peuvent révoquer des messages électroniques chiffrés si le destinataire a reçu un message électronique chiffré de marque basé sur un lien. Si le destinataire a reçu une expérience inline native dans un client Outlook pris en charge, vous ne pouvez pas révoquer le message.

Le fait qu’un destinataire reçoit une expérience basée sur un lien ou une expérience en ligne dépend du type d’identité du destinataire : les destinataires de compte Office 365 et Microsoft (par exemple, les utilisateurs outlook.com) bénéficient d’une expérience en ligne dans les clients Outlook pris en charge. Tous les autres types de destinataires, tels que les destinataires Gmail et Yahoo, offrent une expérience basée sur les liens.

Les administrateurs et les expéditeurs de messages peuvent révoquer les messages chiffrés à l’aide du chiffrement appliqué directement à partir d’Outlook sur le web. Par exemple, les messages chiffrés avec l’option Chiffrer uniquement.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Capture d’écran montrant l’option Chiffrer uniquement dans Outlook sur le web.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Expérience de destinataire pour les e-mails chiffrés révoqués

Une fois qu’un e-mail a été révoqué, le destinataire reçoit une erreur lorsqu’il accède au courrier chiffré via le portail de chiffrement de messages Office 365 : « Le message a été révoqué par l’expéditeur ».

![Capture d’écran shows a revoked encrypted email.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Comment révoquer un message chiffré que vous avez envoyé

Vous pouvez révoquer un message que vous avez envoyé à un destinataire unique qui utilise un compte social tel que gmail.com ou yahoo.com. En d’autres termes, vous pouvez révoquer un message électronique envoyé à un seul destinataire qui a reçu l’expérience basée sur un lien.

Vous ne pouvez pas révoquer un courrier que vous avez envoyé à un destinataire qui utilise un compte scolaire ou scolaire à partir d’Office 365 ou De Microsoft 365 ou d’un utilisateur qui utilise un compte Microsoft, par exemple, un compte outlook.com. 

Pour révoquer un message chiffré que vous avez envoyé, complétez ces étapes

1. Dans Outlook sur le web, dans votre dossier **Envoyé,** accédez au message que vous souhaitez révoquer.

   Si le message est révocable, vous verrez le lien « Supprimer l’accès externe » en haut du message.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Capture d’écran montrant le courrier chiffré que vous souhaitez révoquer dans Outlook sur le web.":::

2. Cliquez **sur Supprimer l’accès** externe pour révoquer le message.

   Le message indique que son état est révoqué.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Capture d’écran montrant un message chiffré révoqué dans Outlook sur le web.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Comment révoquer un message chiffré en tant qu’administrateur

Les administrateurs Microsoft 365 suivent les étapes générales suivantes pour révoquer un e-mail chiffré éligible :

- Obtenez l’ID de message de l’e-mail.
- Vérifiez que vous pouvez révoquer le message.
- Révoquer le message.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Étape 1. Obtenir l’ID de message de l’e-mail

Avant de pouvoir révoquer un courrier chiffré, collectez l’ID de message du message. Le MessageId est généralement au format :

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Il existe plusieurs façons de rechercher l’ID de message de l’e-mail que vous souhaitez révoquer. Cette section décrit quelques options, mais vous pouvez utiliser n’importe quelle méthode qui fournit l’ID.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Pour identifier l’ID du message que vous souhaitez révoquer à l’aide du suivi des messages dans le Centre de conformité &amp; de sécurité

1. Recherchez le courrier électronique par expéditeur ou destinataire à l’aide du Nouveau suivi des messages dans le [Centre de sécurité & conformité.](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/)

2. Une fois que vous avez localisé l’e-mail, sélectionnez-le pour faire monter le volet **Détails** du suivi des messages. Développez **plus d’informations** pour localiser l’ID de message.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>Pour identifier l’ID du message que vous souhaitez révoquer à l’aide des rapports de chiffrement de messages Office dans le Centre de conformité &amp; de sécurité

1. Dans le Centre de &amp; conformité de sécurité, accédez au rapport de **chiffrement des messages.** Pour plus d’informations sur ce rapport, voir Afficher les rapports de sécurité du courrier [électronique dans le Centre de conformité de &amp; sécurité.](../security/defender-365-security/view-email-security-reports.md)

2. Choisissez la **table Afficher les détails** et identifiez le message que vous souhaitez révoquer.

3. Double-cliquez sur le message pour afficher les détails qui incluent l’ID de message.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Étape 2. Vérifier que le courrier est révocable

Pour vérifier si vous pouvez révoquer un message, vérifiez si le champ État de révocation est visible dans le rapport de chiffrement, dans la table **Détails** du Centre de conformité de &amp; sécurité.

Pour vérifier si vous pouvez révoquer un message électronique particulier à l’Windows PowerShell, complétez ces étapes.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la cmdlet Get-OMEMessageStatus suivante :

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Cette commande renvoie l’objet du message et si le message est révocable. Par exemple :

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Étape 3. Révoquer le courrier

Une fois que vous connaissez l’ID du message que vous souhaitez révoquer et que vous avez vérifié que le message est révocable, vous pouvez révoquer le message à l’aide du Centre de conformité de sécurité ou &amp; Windows PowerShell.

Pour révoquer le message à l’aide du Centre de &amp; conformité de sécurité

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous au Centre de sécurité & conformité.

2. In the **Encryption report**, in the **Details** table for the message, choose **Revoke message**.

Pour révoquer un e-mail à l’Windows PowerShell, utilisez la cmdlet Set-OMEMessageRevocation'accès.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, connectez-vous [à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la cmdlet Set-OMEMessageRevocation suivante :

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. Pour vérifier si l’e-mail a été révoqué, exécutez la cmdlet Get-OMEMessageStatus suivante :

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Si la révocation a réussi, la cmdlet renvoie le résultat suivant :  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Plus d’informations sur le chiffrement avancé des messages Office 365

- [Chiffrement de messages avancé Office 365](ome-advanced-message-encryption.md)

- [Chiffrement avancé des messages Office 365 : expiration du courrier électronique](ome-advanced-expiration.md)

- [Description du service de conformité et de stratégie de message](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)