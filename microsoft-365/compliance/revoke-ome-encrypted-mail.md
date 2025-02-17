---
title: Révoquer les e-mails chiffrés par le chiffrement de message avancé
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/02/2022
ms.collection:
- tier1
- purview-compliance
search.appverid:
- MET150
description: En tant qu’administrateur et en tant qu’expéditeur de messages, vous pouvez révoquer certains e-mails chiffrés avec microsoft Purview Advanced Message Encryption.
ms.openlocfilehash: bdae122260b932111017b1a0af31bb268d46a9d6
ms.sourcegitcommit: a88aadf5786f1bd9e5bae763f603a2b690473322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68817448"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Révoquer les e-mails chiffrés par le chiffrement de message avancé

Email révocation est proposée dans le cadre de Microsoft Purview Advanced Message Encryption. Microsoft Purview Advanced Message Encryption est inclus dans [Microsoft 365 Entreprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarification du personnel à but non lucratif), Office 365 Entreprise E5 (tarification du personnel à but non lucratif) et Office 365 Éducation A5. Pour utiliser les fonctions avancées de révocation et d’expiration du chiffrement des messages, activez l’option **Chiffrement Premium dans Office 365** dans votre licence E5.

Si votre organisation dispose d’un abonnement qui n’inclut pas microsoft Purview Advanced Message Encryption, vous pouvez l’acheter avec le module complémentaire de référence SKU Microsoft 365 E5 Conformité pour Microsoft 365 E3, Microsoft 365 E3 (tarification du personnel à but non lucratif) ou Conformité avancée Office 365 module complémentaire de référence SKU pour Microsoft 365 E3, Microsoft 365 E3 (tarification du personnel à but non lucratif) ou Office 365 références SKU.

Cet article fait partie d’une plus grande série d’articles sur [Office 365 chiffrement des messages](ome.md).

Si un message a été chiffré à l’aide de Microsoft Purview Advanced Message Encryption et que vous êtes administrateur Microsoft 365 ou que vous êtes l’expéditeur du message, vous pouvez révoquer le message sous certaines conditions. Les administrateurs révoquent des messages à l’aide de PowerShell. En tant qu’expéditeur, vous révoquez un message que vous avez envoyé directement à partir de Outlook sur le web. Cet article décrit les circonstances dans lesquelles la révocation est possible et comment procéder.

> [!NOTE]
> Pour garantir que la possibilité de suivre et de révoquer les messages OME est disponible, vous devez ajouter un modèle de personnalisation personnalisé. Consultez [Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md)
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="encrypted-emails-that-you-can-revoke"></a>E-mails chiffrés que vous pouvez révoquer

Les administrateurs et les expéditeurs de messages peuvent révoquer les e-mails chiffrés si le destinataire a reçu un e-mail chiffré basé sur un lien et personnalisé. Si le destinataire a reçu une expérience intégrée native dans un client Outlook pris en charge, vous ne pouvez pas révoquer le message.

Le type d’identité du destinataire dépend du type d’identité du destinataire : Office 365 et les destinataires du compte Microsoft (par exemple, outlook.com utilisateurs) bénéficient d’une expérience inline dans les clients Outlook pris en charge. Tous les autres types de destinataires, tels que les destinataires Gmail et Yahoo, bénéficient d’une expérience basée sur des liens.

Les administrateurs et les expéditeurs de messages peuvent révoquer les messages chiffrés à l’aide du chiffrement appliqué directement à Outlook sur le web. Par exemple, les messages chiffrés avec l’option Chiffrer uniquement.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Capture d’écran montrant l’option Chiffrer uniquement dans Outlook sur le web.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Expérience du destinataire pour les e-mails chiffrés révoqués

Une fois qu’un e-mail a été révoqué, le destinataire reçoit une erreur lorsqu’il accède à l’e-mail chiffré via le portail de chiffrement des messages Office 365 : « Le message a été révoqué par l’expéditeur ».

![Capture d’écran montrant un e-mail chiffré révoqué.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Comment révoquer un message chiffré que vous avez envoyé

Vous pouvez révoquer un courrier que vous avez envoyé à un seul destinataire qui utilise un compte social tel qu’gmail.com ou yahoo.com. En d’autres termes, vous pouvez révoquer un e-mail envoyé à un seul destinataire qui a reçu l’expérience basée sur les liens.

Vous ne pouvez pas révoquer un courrier que vous avez envoyé à un destinataire qui utilise un compte professionnel ou scolaire à partir de Office 365 ou Microsoft 365 ou d’un utilisateur qui utilise un compte Microsoft, par exemple un compte outlook.com. 

Pour révoquer un message chiffré que vous avez envoyé, procédez comme suit

1. Dans Outlook sur le web, dans votre dossier **Envoyé**, accédez au message que vous souhaitez révoquer.

   Si le message est révocable, le lien « Supprimer l’accès externe » s’affiche en haut du message.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Capture d’écran montrant le courrier chiffré que vous souhaitez révoquer dans Outlook sur le web.":::

2. Cliquez sur **Supprimer l’accès externe** pour révoquer le message.

   Le message indique que son état est révoqué.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Capture d’écran montrant un message chiffré révoqué dans Outlook sur le web.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Comment révoquer un message chiffré en tant qu’administrateur

Les administrateurs Microsoft 365 suivent ces étapes générales pour révoquer un e-mail chiffré éligible :

- Obtenez l’ID de message de l’e-mail.
- Vérifiez que vous pouvez révoquer le message.
- Révoquez le courrier.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Étape 1. Obtenir l’ID de message de l’e-mail

Avant de pouvoir révoquer un message chiffré, rassemblez l’ID de message du message. MessageId est généralement au format :

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Il existe plusieurs façons de trouver l’ID de message de l’e-mail que vous souhaitez révoquer. Cette section décrit quelques options, mais vous pouvez utiliser n’importe quelle méthode qui fournit l’ID.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-microsoft-purview-compliance-portal"></a>Pour identifier l’ID de message de l’e-mail que vous souhaitez révoquer à l’aide de la trace des messages dans le portail de conformité Microsoft Purview

1. Recherchez l’e-mail par expéditeur ou destinataire à l’aide [de Nouvelle trace de message dans portail de conformité Microsoft Purview](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Une fois que vous avez localisé l’e-mail, sélectionnez-le pour afficher le volet **Détails de la trace des** messages. Développez **Plus d’informations** pour localiser l’ID de message.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-encryption-reports-in-the-microsoft-purview-compliance-portal"></a>Pour identifier l’ID de message de l’e-mail que vous souhaitez révoquer à l’aide des rapports de chiffrement de messages dans le portail de conformité Microsoft Purview

1. Dans le portail de conformité Microsoft Purview, accédez au **rapport de chiffrement des messages**. Pour plus d’informations sur ce rapport, consultez [Afficher les rapports de sécurité des e-mails dans le Centre de conformité de la sécurité&amp;](../security/office-365-security/view-email-security-reports.md).

2. Choisissez le tableau **Afficher les détails** et identifiez le message que vous souhaitez révoquer.

3. Double-cliquez sur le message pour afficher les détails qui incluent l’ID de message.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Étape 2. Vérifier que le courrier est révocable

Pour vérifier si vous pouvez révoquer un message, vérifiez si le champ État de révocation est visible dans le rapport Chiffrement, dans la table **Détails** du portail de conformité Microsoft Purview.

Pour vérifier si vous pouvez révoquer un message électronique particulier à l’aide de Windows PowerShell, procédez comme suit.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Get-OMEMessageStatus comme suit :

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Cette commande retourne l’objet du message et indique si le message peut être révocable. Par exemple :

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Étape 3. Révoquer le courrier

Une fois que vous connaissez l’ID de message de l’e-mail que vous souhaitez révoquer et que vous avez vérifié que le message est révocable, vous pouvez révoquer l’e-mail à l’aide du portail de conformité Microsoft Purview ou Windows PowerShell.

Pour révoquer le message à l’aide de la portail de conformité Microsoft Purview

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous au portail de conformité Microsoft Purview.

2. Dans le **rapport Chiffrement**, dans la table **Détails** du message, choisissez **Révoquer le message**.

Pour révoquer un e-mail à l’aide de Windows PowerShell, utilisez l’applet de commande Set-OMEMessageRevocation.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-OMEMessageRevocation comme suit :

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. Pour vérifier si l’e-mail a été révoqué, exécutez l’applet de commande Get-OMEMessageStatus comme suit :

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Si la révocation a réussi, l’applet de commande retourne le résultat suivant :  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Plus d’informations sur microsoft Purview Advanced Message Encryption

- [Chiffrement avancé des messages Microsoft Purview](ome-advanced-message-encryption.md)

- [Chiffrement avancé des messages Microsoft Purview - Expiration des e-mails](ome-advanced-expiration.md)

- [Stratégie de message et description du service de conformité](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
