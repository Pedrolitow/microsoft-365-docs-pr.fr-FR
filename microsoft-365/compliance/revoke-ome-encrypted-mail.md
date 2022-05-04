---
title: Révoquer les e-mails chiffrés par Advanced Message Encryption
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
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: En tant qu’administrateur et en tant qu’expéditeur de messages, vous pouvez révoquer certains e-mails chiffrés avec Microsoft Purview Advanced Message Encryption.
ms.openlocfilehash: 79d09c13755c0c73e4d68598e83ac41344b9281a
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65187940"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Révoquer les e-mails chiffrés par Advanced Message Encryption

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

La révocation des e-mails est proposée dans le cadre du chiffrement avancé des messages Microsoft Purview. Microsoft Purview Advanced Message Encryption est inclus dans [Microsoft 365 Entreprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (tarification du personnel à but non lucratif), Office 365 Entreprise E5 (prix du personnel à but non lucratif) et Office 365 Éducation A5. Pour utiliser les fonctions de révocation et d’expiration d’Advanced Message Encryption, activez l’option **de chiffrement Premium dans Office 365** de votre licence E5.

Si votre organisation dispose d’un abonnement qui n’inclut pas Microsoft Purview Advanced Message Encryption, vous pouvez l’acheter avec le module complémentaire de référence SKU Microsoft 365 E5 Conformité pour Microsoft 365 E3, Microsoft 365 E3 (prix du personnel à but non lucratif) ou le Conformité avancée Office 365 module complémentaire SKU pour Microsoft 365 E3, Microsoft 365 E3 (Prix du personnel à but non lucratif) ou Office 365 références SKU.

Cet article fait partie d’une série plus importante d’articles sur [Office 365 chiffrement](ome.md) des messages.

Si un message a été chiffré à l’aide de Microsoft Purview Advanced Message Encryption et que vous êtes administrateur Microsoft 365 ou que vous êtes l’expéditeur du message, vous pouvez révoquer le message dans certaines conditions. Les administrateurs révoquent les messages à l’aide de PowerShell. En tant qu’expéditeur, vous révoquez un message que vous avez envoyé directement à partir de Outlook sur le web. Cet article décrit les circonstances dans lesquelles la révocation est possible et comment procéder.

> [!NOTE]
> Pour garantir que la possibilité de suivre et de révoquer les messages OME est disponible, vous devez ajouter un modèle de personnalisation. Voir [Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>E-mails chiffrés que vous pouvez révoquer

Les administrateurs et les expéditeurs de messages peuvent révoquer des e-mails chiffrés si le destinataire a reçu un e-mail chiffré de marque basé sur un lien. Si le destinataire a reçu une expérience inline native dans un client Outlook pris en charge, vous ne pouvez pas révoquer le message.

Le fait qu’un destinataire reçoive une expérience basée sur des liens ou une expérience inline dépend du type d’identité du destinataire : les destinataires Office 365 et de compte Microsoft (par exemple, les utilisateurs outlook.com) bénéficient d’une expérience inline dans les clients Outlook pris en charge. Tous les autres types de destinataires, tels que les destinataires Gmail et Yahoo, bénéficient d’une expérience basée sur des liens.

Les administrateurs et les expéditeurs de messages peuvent révoquer les messages chiffrés à l’aide du chiffrement appliqué directement à partir de Outlook sur le web. Par exemple, les messages chiffrés avec l’option Chiffrer uniquement.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Capture d’écran montrant l’option Chiffrer uniquement dans Outlook sur le web.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Expérience du destinataire pour les e-mails chiffrés révoqués

Une fois qu’un e-mail a été révoqué, le destinataire reçoit une erreur lorsqu’il accède à l’e-mail chiffré via le portail Office 365 Message Encryption : « Le message a été révoqué par l’expéditeur ».

![Capture d’écran montrant un e-mail chiffré révoqué.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Comment révoquer un message chiffré que vous avez envoyé

Vous pouvez révoquer un courrier que vous avez envoyé à un seul destinataire qui utilise un compte social tel que gmail.com ou yahoo.com. En d’autres termes, vous pouvez révoquer un e-mail envoyé à un seul destinataire qui a reçu l’expérience basée sur le lien.

Vous ne pouvez pas révoquer un courrier que vous avez envoyé à un destinataire qui utilise un compte professionnel ou scolaire à partir d’Office 365 ou d’un Microsoft 365 ou d’un utilisateur qui utilise un compte Microsoft, par exemple un compte outlook.com. 

Pour révoquer un message chiffré que vous avez envoyé, procédez comme suit

1. Dans Outlook sur le web, dans votre dossier **Envoyé**, accédez au message que vous souhaitez révoquer.

   Si le message est révocable, le lien « Supprimer l’accès externe » s’affiche en haut du message.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Capture d’écran montrant le courrier chiffré que vous souhaitez révoquer dans Outlook sur le web.":::

2. Cliquez sur **Supprimer l’accès externe** pour révoquer le message.

   Le message indique que son état est révoqué.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Capture d’écran montrant le message chiffré révoqué dans Outlook sur le web.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Comment révoquer un message chiffré en tant qu’administrateur

Microsoft 365 administrateurs suivent ces étapes générales pour révoquer un e-mail chiffré éligible :

- Obtenez l’ID de message de l’e-mail.
- Vérifiez que vous pouvez révoquer le message.
- Révoquez le courrier.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Étape 1. Obtenir l’ID de message de l’e-mail

Avant de pouvoir révoquer un courrier chiffré, collectez l’ID de message du courrier. Le MessageId est généralement au format suivant :

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Il existe plusieurs façons de rechercher l’ID de message de l’e-mail que vous souhaitez révoquer. Cette section décrit quelques options, mais vous pouvez utiliser n’importe quelle méthode qui fournit l’ID.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Pour identifier l’ID de message de l’e-mail que vous souhaitez révoquer à l’aide de la trace des messages dans le Centre de conformité de sécurité &amp;

1. Recherchez l’e-mail par l’expéditeur ou le destinataire à l’aide [de la nouvelle trace de message dans le Centre de sécurité & conformité](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Une fois que vous avez localisé l’e-mail, sélectionnez-le pour afficher le volet Détails de la **trace des** messages. Développez **plus d’informations** pour localiser l’ID de message.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-encryption-reports-in-the-security-amp-compliance-center"></a>Pour identifier l’ID de message de l’e-mail que vous souhaitez révoquer à l’aide de rapports de chiffrement de messages dans le Centre de conformité de sécurité &amp;

1. Dans le Centre de conformité de sécurité &amp; , accédez au **rapport de chiffrement des messages**. Pour plus d’informations sur ce rapport, consultez [Afficher les rapports de sécurité par e-mail dans le Centre de conformité de la sécurité&amp;](../security/office-365-security/view-email-security-reports.md).

2. Choisissez la table **afficher les détails** et identifiez le message que vous souhaitez révoquer.

3. Double-cliquez sur le message pour afficher les détails qui incluent l’ID de message.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Étape 2. Vérifier que le courrier est révocable

Pour vérifier si vous pouvez révoquer un message, vérifiez si le champ État de révocation est visible dans le rapport de chiffrement, dans la table **Détails** du Centre de conformité de &amp; sécurité.

Pour vérifier si vous pouvez révoquer un e-mail particulier à l’aide de Windows PowerShell, procédez comme suit.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Get-OMEMessageStatus comme suit :

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Cette commande retourne l’objet du message et indique si le message est révocable. Par exemple :

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Étape 3. Révoquer le courrier

Une fois que vous connaissez l’ID de message de l’e-mail que vous souhaitez révoquer et que vous avez vérifié que le message est révocable, vous pouvez révoquer l’e-mail à l’aide du Centre de conformité de &amp; sécurité ou de Windows PowerShell.

Pour révoquer le message à l’aide du Centre de conformité de sécurité &amp;

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous au Centre de sécurité & conformité.

2. Dans le **rapport de chiffrement**, dans la table **Détails** du message, choisissez **Révoquer le message**.

Pour révoquer un e-mail à l’aide de Windows PowerShell, utilisez l’applet de commande Set-OMEMessageRevocation.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

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

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Plus d’informations sur le chiffrement avancé des messages Microsoft Purview

- [Chiffrement avancé des messages Microsoft Purview](ome-advanced-message-encryption.md)

- [Microsoft Purview Advanced Message Encryption - Expiration du courrier électronique](ome-advanced-expiration.md)

- [Description de la stratégie de message et du service de conformité](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
