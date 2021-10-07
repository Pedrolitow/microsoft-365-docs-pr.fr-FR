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
ms.date: 5/8/2019
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Une fois que vous avez terminé la configuration chiffrement de messages Office 365 (OME), découvrez comment personnaliser votre déploiement de plusieurs manières.
ms.openlocfilehash: c402b5f414e81fbb7403d56a7314c9255c8cf1b4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60192222"
---
# <a name="manage-office-365-message-encryption"></a>Gérer le chiffrement de messages Office 365

Une fois que vous avez terminé la configuration chiffrement de messages Office 365 (OME), vous pouvez personnaliser la configuration de votre déploiement de plusieurs manières. Par exemple, vous pouvez configurer s’il faut activer  les codes de passe à temps partiel, afficher le bouton Chiffrer dans Outlook sur le web, etc. Les tâches de cet article décrivent comment.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Déterminer si les destinataires des comptes Google, Yahoo et Microsoft peuvent utiliser ces comptes pour se connecter au portail chiffrement de messages Office 365 web

Lorsque vous définissez les nouvelles fonctionnalités chiffrement de messages Office 365, les utilisateurs de votre organisation peuvent envoyer des messages à des destinataires extérieurs à votre organisation. Si le destinataire utilise un *ID social* tel qu’un compte Google, un compte Yahoo ou un compte Microsoft, le destinataire peut se connecter au portail OME avec un ID social. Si vous le souhaitez, vous pouvez choisir de ne pas autoriser les destinataires à utiliser les ID de réseau social pour se connecter au portail OME.
  
### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Pour déterminer si les destinataires peuvent utiliser des ID sociaux pour se connecter au portail OME
  
1. [Connecter à Exchange Online à l’aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lSet-OMEConfiguration cmdlet avec le paramètre SocialIdSignIn comme suit :

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

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Gérer l’utilisation de codes de passe à usage unique pour le portail chiffrement de messages Office 365 web

Si le destinataire d’un message chiffré par OME n’utilise pas Outlook, quel que soit le compte utilisé par le destinataire, le destinataire reçoit un lien d’affichage web à durée limitée qui lui permet de lire le message. Ce lien inclut un code de passe à une seule fois. En tant qu’administrateur, vous pouvez décider si les destinataires peuvent utiliser des codes de passe à usage unique pour se connecter au portail OME.
  
### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Pour savoir si OME génère des codes de passe à temps partiel
  
1. Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la cmdlet Set-OMEConfiguration avec le paramètre OTPEnabled :

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Par exemple, pour désactiver les codes de passe à une seule heure :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Pour activer les codes de passe à une seule fois :

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Gérer l’affichage du bouton Chiffrer dans Outlook sur le web

En tant qu’administrateur, vous pouvez décider d’afficher ou non ce bouton pour les utilisateurs finaux.
  
### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Pour déterminer si le bouton Chiffrer s’affiche dans Outlook sur le web
  
1. Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lSet-IRMConfiguration cmdlet avec le paramètre -SimplifiedClientAccessEnabled :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Par exemple, pour désactiver le bouton **Chiffrer** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Pour activer le **bouton Chiffrer** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Activer le déchiffrement côté service des messages électroniques pour les utilisateurs de l’application de messagerie iOS

L’application de messagerie iOS ne peut pas déchiffrer les messages protégés par chiffrement de messages Office 365. En tant qu Microsoft 365 de messagerie, vous pouvez appliquer le déchiffrement côté service pour les messages remis à l’application de messagerie iOS. Lorsque vous choisissez d’utiliser le déchiffrement côté service, le service envoie une copie déchiffrée du message à l’appareil iOS. L’appareil client stocke une copie déchiffrée du message. Le message conserve également des informations sur les droits d’utilisation, même si l’application de messagerie iOS n’applique pas de droits d’utilisation côté client à l’utilisateur. L’utilisateur peut copier ou imprimer le message même s’il n’en avait pas à l’origine les droits. Toutefois, si l’utilisateur tente d’effectuer une action qui nécessite le serveur de messagerie Microsoft 365, telle que le forwarding du message, le serveur n’autorise pas l’action si l’utilisateur n’en avait pas à l’origine le droit d’utilisation. Toutefois, les utilisateurs finaux peuvent contourner la restriction d’utilisation « Ne pas transmettre » en axant le message à partir d’un autre compte dans l’application de messagerie iOS. Que vous définissez ou non le déchiffrement côté service du courrier, les pièces jointes au courrier chiffré et protégé par des droits ne peuvent pas être vues dans l’application de messagerie iOS.
  
Si vous choisissez de ne pas autoriser l’envoi de messages déchiffrés aux utilisateurs de l’application de messagerie iOS, les utilisateurs reçoivent un message qui indique qu’ils ne sont pas en droit d’afficher le message. Par défaut, le déchiffrement côté service des messages électroniques n’est pas activé.
  
Pour plus d’informations et pour une vue de l’expérience client, voir Afficher les messages chiffrés [sur iPhone ou iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).
  
### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Pour déterminer si les utilisateurs de l’application de messagerie iOS peuvent afficher les messages protégés par chiffrement de messages Office 365
  
1. Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la cmdlet Set-ActiveSyncOrganizations avec le paramètre AllowRMSSupportForUnenlightenedApps :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Par exemple, pour configurer le service pour déchiffrer les messages avant qu’ils ne sont envoyés à des applications nonlightened telles que l’application de messagerie iOS :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Vous pouvez également configurer le service pour qu’il n’envoie pas de messages déchiffrés à des applications non configurées :

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Les stratégies de boîte aux lettres individuelles (OWA/ActiveSync) remplacent ces paramètres (par exemple, si -IRMEnabled est définie sur False dans la stratégie de boîte aux lettres OWA ou activeSync, ces configurations ne s’appliquent pas).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Activer le déchiffrement côté service des pièces jointes pour les clients de messagerie de navigateur web

Normalement, lorsque vous utilisez le chiffrement Office 365 messages, les pièces jointes sont automatiquement chiffrées. En tant qu’administrateur, vous pouvez appliquer le déchiffrement côté service pour les pièces jointes de courrier que les utilisateurs téléchargent à partir d’un navigateur web.
  
Lorsque vous utilisez le déchiffrement côté service, le service envoie une copie déchiffrée du fichier à l’appareil. Le message est toujours chiffré. La pièce jointe conserve également les informations sur les droits d’utilisation, même si le navigateur n’applique pas de droits d’utilisation côté client à l’utilisateur. L’utilisateur peut copier ou imprimer la pièce jointe même s’il n’en avait pas à l’origine les droits. Toutefois, si l’utilisateur tente d’effectuer une action qui nécessite le serveur de messagerie Microsoft 365, telle que le forwarding de la pièce jointe, le serveur n’autorise pas l’action si l’utilisateur n’en avait pas à l’origine le droit d’utilisation.
  
Que vous setiez ou non le déchiffrement côté service des pièces jointes, les utilisateurs ne peuvent pas afficher les pièces jointes des messages chiffrés et protégés par des droits dans l’application de messagerie iOS.
  
Si vous choisissez de ne pas autoriser les pièces jointes déchiffrées, qui est la valeur par défaut, les utilisateurs reçoivent un message qui indique qu’ils ne sont pas en droit d’afficher la pièce jointe.
  
Pour plus d’informations sur la façon dont Microsoft 365 implémente le chiffrement pour les e-mails et les pièces jointes avec l’option Encrypt-Only, voir l’option Chiffrer uniquement pour [les e-mails.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)
  
### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Pour déterminer si les pièces jointes sont déchiffrées lors du téléchargement à partir d’un navigateur web
  
1. Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez Set-IRMConfiguration cmdlet avec le paramètre DecryptAttachmentForEncryptOnly :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Par exemple, pour configurer le service afin de déchiffrer les pièces jointes lorsqu’un utilisateur les télécharge à partir d’un navigateur web :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Pour configurer le service afin qu’il laisse les pièces jointes chiffrées telles qu’elles sont au téléchargement :

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Vérifier que tous les destinataires externes utilisent le portail OME pour lire les messages chiffrés

Vous pouvez utiliser des modèles de personnalisation pour obliger les destinataires à recevoir un message de wrapper qui les dirige vers la lecture de messages chiffrés dans le portail OME au lieu d’utiliser Outlook ou Outlook sur le web. Vous pouvez le faire si vous souhaitez mieux contrôler la façon dont les destinataires utilisent le courrier qu’ils reçoivent. Par exemple, si des destinataires externes visualisent le courrier électronique dans le portail web, vous pouvez définir une date d’expiration pour le courrier électronique et révoquer le courrier électronique. Ces fonctionnalités sont uniquement pris en charge via le portail OME. Vous pouvez utiliser l’option Chiffrer et l’option Ne pas forwarder lors de la création des règles de flux de messagerie.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Utiliser un modèle personnalisé pour forcer tous les destinataires externes à utiliser le portail OME et pour le courrier électronique chiffré

1. Utilisez un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez lNew-TransportRule cmdlet :

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    où :

   - `mail flow rule name` est le nom que vous souhaitez utiliser pour la nouvelle règle de flux de messagerie.

   - `option name` est soit `Encrypt` `Do Not Forward` ou .

   - `template name` est le nom que vous avez donné au modèle de personnalisation, par exemple `OME Configuration` .

   Pour chiffrer tous les messages externes à l’aide du modèle « Configuration OME » et appliquer lEncrypt-Only option :

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Pour chiffrer tous les messages externes à l’aide du modèle « Configuration OME » et appliquer l’option Ne pas forwarder :

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Personnaliser l’apparence des messages électroniques et du portail OME

Pour plus d’informations sur la façon dont vous pouvez personnaliser OME pour votre organisation, voir Ajouter la marque de votre organisation [à vos messages chiffrés.](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="disable-the-new-capabilities-for-ome"></a>Désactiver les nouvelles fonctionnalités pour OME

Nous espérons qu’elle n’y arrive pas, mais si nécessaire, la désactivation des nouvelles fonctionnalités pour OME est très simple. Tout d’abord, vous devez supprimer toutes les règles de flux de messagerie que vous avez créées qui utilisent les nouvelles fonctionnalités OME. Pour plus d’informations sur la suppression des règles de flux de messagerie, voir [Gérer les règles de flux de messagerie.](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) Ensuite, complétez ces étapes dans Exchange Online PowerShell.
  
### <a name="to-disable-the-new-capabilities-for-ome"></a>Pour désactiver les nouvelles fonctionnalités pour OME
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Si vous avez  activé le bouton Chiffrer dans Outlook sur le web, désactivez-le en exécutant la cmdlet Set-IRMConfiguration avec le paramètre SimplifiedClientAccessEnabled. Sinon, ignorez cette étape.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Désactivez les nouvelles fonctionnalités pour OME en exécutant la cmdlet Set-IRMConfiguration avec le paramètre AzureRMSLicensingEnabled définie sur false :

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
