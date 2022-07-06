---
title: Gérer le chiffrement de messages Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Une fois que vous avez terminé de configurer Office 365 chiffrement des messages (OME), découvrez comment personnaliser votre déploiement de plusieurs façons.
ms.openlocfilehash: b3d7ffe5db987b9fb3bd29682c8e101ffd99946a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635280"
---
# <a name="manage-office-365-message-encryption"></a>Gérer le chiffrement de messages Office 365

Une fois que vous avez terminé de configurer Office 365 chiffrement des messages (OME), vous pouvez personnaliser la configuration de votre déploiement de plusieurs façons. Par exemple, vous pouvez configurer l’activation des codes de passe uniques, l’affichage du bouton **Chiffrer** dans Outlook sur le web, etc. Les tâches décrites dans cet article décrivent comment procéder.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Déterminez si les destinataires de comptes Google, Yahoo et Microsoft peuvent utiliser ces comptes pour se connecter au portail Office 365 Message Encryption

Lorsque vous configurez les nouvelles fonctionnalités de chiffrement des messages Office 365, les utilisateurs de votre organisation peuvent envoyer des messages aux destinataires qui ne font pas partie de votre organisation. Si le destinataire utilise un *ID social* tel qu’un compte Google, un compte Yahoo ou un compte Microsoft, le destinataire peut se connecter au portail OME avec un ID de réseau social. Si vous le souhaitez, vous pouvez choisir de ne pas autoriser les destinataires à utiliser des ID de réseaux sociaux pour se connecter au portail OME.

### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Pour déterminer si les destinataires peuvent utiliser des ID de réseaux sociaux pour se connecter au portail OME

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-OMEConfiguration avec le paramètre SocialIdSignIn comme suit :

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   Par exemple, pour désactiver les ID sociaux :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   Pour activer les ID sociaux :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Gérer l’utilisation de codes de passe uniques pour le portail Office 365 Message Encryption

Si le destinataire d’un message chiffré par OME n’utilise pas Outlook, quel que soit le compte utilisé par le destinataire, le destinataire reçoit un lien d’affichage web à durée limitée qui lui permet de lire le message. Ce lien inclut un code de passe unique. En tant qu’administrateur, vous pouvez décider si les destinataires peuvent utiliser des codes de passe uniques pour se connecter au portail OME.

### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Pour déterminer si OME génère des codes de passe uniques

1. Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation et connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-OMEConfiguration avec le paramètre OTPEnabled :

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Par exemple, pour désactiver les codes de passe uniques :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Pour activer les codes de passe uniques :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Gérer l’affichage du bouton Chiffrer dans Outlook sur le web

En tant qu’administrateur, vous pouvez gérer l’affichage de ce bouton pour les utilisateurs finaux.

### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Pour déterminer si le bouton Chiffrer apparaît dans Outlook sur le web

1. Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation et connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-IRMConfiguration avec le paramètre -SimplifiedClientAccessEnabled :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Par exemple, pour désactiver le bouton **Chiffrer** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Pour activer le bouton **Chiffrer** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Activer le déchiffrement côté service des messages électroniques pour les utilisateurs d’applications de messagerie iOS

L’application de messagerie iOS ne peut pas déchiffrer les messages protégés par Office 365 Chiffrement des messages. En tant qu’administrateur Microsoft 365, vous pouvez appliquer le déchiffrement côté service pour les messages remis à l’application de messagerie iOS. Lorsque vous choisissez d’utiliser le déchiffrement côté service, le service envoie une copie déchiffrée du message à l’appareil iOS. L’appareil client stocke une copie déchiffrée du message. Le message conserve également des informations sur les droits d’utilisation, même si l’application de messagerie iOS n’applique pas les droits d’utilisation côté client à l’utilisateur. L’utilisateur peut copier ou imprimer le message même s’il n’avait pas à l’origine les droits de le faire. Toutefois, si l’utilisateur tente d’effectuer une action qui nécessite le serveur de messagerie Microsoft 365, telle que le transfert du message, le serveur n’autorise pas l’action si l’utilisateur n’a pas initialement le droit d’utilisation de le faire. Toutefois, les utilisateurs finaux peuvent contourner la restriction d’utilisation « Ne pas transférer » en transférant le message à partir d’un autre compte au sein de l’application de messagerie iOS. Que vous configuriez ou non le déchiffrement côté service du courrier, les pièces jointes à des messages chiffrés et protégés par des droits ne peuvent pas être affichées dans l’application de messagerie iOS.

Si vous choisissez de ne pas autoriser l’envoi de messages déchiffrés aux utilisateurs de l’application de messagerie iOS, les utilisateurs reçoivent un message indiquant qu’ils ne disposent pas des droits nécessaires pour afficher le message. Par défaut, le déchiffrement côté service des messages électroniques n’est pas activé.

Pour plus d’informations et pour obtenir une vue de l’expérience client, consultez [Afficher les messages chiffrés sur votre iPhone ou iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).

### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Pour déterminer si les utilisateurs d’applications de messagerie iOS peuvent afficher les messages protégés par Office 365 Chiffrement des messages

1. Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation et connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-ActiveSyncOrganizations avec le paramètre AllowRMSSupportForUnenlightenedApps :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Par exemple, pour configurer le service afin de déchiffrer les messages avant qu’ils ne soient envoyés à des applications non redessinées comme l’application de messagerie iOS :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Ou, pour configurer le service afin de ne pas envoyer de messages déchiffrés à des applications non mises à jour :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Les stratégies de boîte aux lettres individuelles (OWA/ActiveSync) remplacent ces paramètres (par exemple, si -IRMEnabled est défini sur False dans la stratégie de boîte aux lettres OWA ou la stratégie de boîte aux lettres ActiveSync correspondante, ces configurations ne s’appliquent pas).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Activer le déchiffrement côté service des pièces jointes pour les clients de messagerie du navigateur web

Normalement, lorsque vous utilisez Office 365 chiffrement des messages, les pièces jointes sont automatiquement chiffrées. En tant qu’administrateur, vous pouvez appliquer le déchiffrement côté service pour les pièces jointes que les utilisateurs téléchargent à partir d’un navigateur web.

Lorsque vous utilisez le déchiffrement côté service, le service envoie une copie déchiffrée du fichier à l’appareil. Le message est toujours chiffré. La pièce jointe conserve également des informations sur les droits d’utilisation, même si le navigateur n’applique pas les droits d’utilisation côté client à l’utilisateur. L’utilisateur peut copier ou imprimer la pièce jointe même s’il n’avait pas à l’origine les droits nécessaires. Toutefois, si l’utilisateur tente d’effectuer une action qui nécessite le serveur de messagerie Microsoft 365, telle que le transfert de la pièce jointe, le serveur n’autorise pas l’action si l’utilisateur n’a pas initialement le droit d’utilisation de le faire.

Que vous configuriez ou non le déchiffrement côté service des pièces jointes, les utilisateurs ne peuvent pas afficher de pièces jointes à des messages chiffrés et protégés par des droits dans l’application de messagerie iOS.

Si vous choisissez de ne pas autoriser les pièces jointes déchiffrées, qui est la valeur par défaut, les utilisateurs reçoivent un message indiquant qu’ils ne disposent pas des droits nécessaires pour afficher la pièce jointe.

Pour plus d’informations sur la façon dont Microsoft 365 implémente le chiffrement pour les e-mails et les pièces jointes avec l’option Encrypt-Only, consultez [l’option Chiffrer uniquement pour les e-mails.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Pour déterminer si les pièces jointes sont déchiffrées lors du téléchargement à partir d’un navigateur web

1. Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation et connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande Set-IRMConfiguration avec le paramètre DecryptAttachmentForEncryptOnly :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Par exemple, pour configurer le service pour déchiffrer les pièces jointes de courrier lorsqu’un utilisateur les télécharge à partir d’un navigateur web :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Pour configurer le service de manière à conserver les pièces jointes de courrier chiffrées telles qu’elles sont lors du téléchargement :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Vérifier que tous les destinataires externes utilisent le portail OME pour lire le courrier chiffré

Vous pouvez utiliser des modèles de personnalisation personnalisés pour forcer les destinataires à recevoir un courrier wrapper qui les dirige vers la lecture d’e-mails chiffrés dans le portail OME au lieu d’utiliser Outlook ou Outlook sur le web. Vous souhaiterez peut-être effectuer cette opération si vous souhaitez mieux contrôler la façon dont les destinataires utilisent le courrier qu’ils reçoivent. Par exemple, si des destinataires externes affichent l’e-mail dans le portail web, vous pouvez définir une date d’expiration pour l’e-mail et révoquer l’e-mail. Ces fonctionnalités sont prises en charge uniquement via le portail OME. Vous pouvez utiliser l’option Chiffrer et l’option Ne pas transférer lors de la création des règles de flux de courrier.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Utiliser un modèle personnalisé pour forcer tous les destinataires externes à utiliser le portail OME et pour les e-mails chiffrés

1. Utilisez un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation et connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez l’applet de commande New-TransportRule :

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    où :

   - `mail flow rule name` est le nom que vous souhaitez utiliser pour la nouvelle règle de flux de messagerie.

   - `option name` est soit `Encrypt` ou `Do Not Forward`.

   - `template name` est le nom que vous avez donné au modèle de personnalisation, par exemple `OME Configuration`.

   Pour chiffrer tous les e-mails externes avec le modèle « Configuration OME » et appliquer l’option Encrypt-Only :

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Pour chiffrer tous les e-mails externes avec le modèle « Configuration OME » et appliquer l’option Ne pas transférer :

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Personnaliser l’apparence des messages électroniques et du portail OME

Pour plus d’informations sur la façon dont vous pouvez personnaliser Chiffrement de messages Microsoft Purview pour votre organisation, consultez [Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md). Pour pouvoir suivre et révoquer des messages chiffrés, vous devez ajouter votre personnalisation au portail OME.

## <a name="disable-microsoft-purview-message-encryption"></a>Désactiver Chiffrement de messages Microsoft Purview

Nous espérons qu’elle n’y arrivera pas, mais si nécessaire, la désactivation de Chiffrement de messages Microsoft Purview est très simple. Tout d’abord, vous devez supprimer toutes les règles de flux de courrier que vous avez créées qui utilisent Chiffrement de messages Microsoft Purview. Pour plus d’informations sur la suppression des règles de flux de messagerie, consultez [Gérer les règles de flux de courrier](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Ensuite, effectuez ces étapes dans Exchange Online PowerShell.

### <a name="to-disable-microsoft-purview-message-encryption"></a>Pour désactiver Chiffrement de messages Microsoft Purview

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Si vous avez activé le bouton **Chiffrer** dans Outlook sur le web, désactivez-le en exécutant l’applet de commande Set-IRMConfiguration avec le paramètre SimplifiedClientAccessEnabled. Sinon, ignorez cette étape.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Désactivez la Chiffrement de messages Microsoft Purview en exécutant l’applet de commande Set-IRMConfiguration avec le paramètre AzureRMSLicensingEnabled défini sur false :

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
