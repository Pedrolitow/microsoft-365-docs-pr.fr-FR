---
title: Configurer Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez les étapes de configuration de Microsoft 365 Business Premium, notamment l’ajout d’un domaine et d’utilisateurs, la configuration de stratégies de sécurité, etc.
ms.openlocfilehash: 4d49ba7ccdb65691756aaa505d0856deb115595b
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51052231"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Configurer Microsoft 365 Business Premium dans l’Assistant Installation

Regardez cette vidéo pour obtenir une vue d’ensemble de la configuration de Microsoft 365 Business Premium.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="add-your-domain-users-and-set-up-policies"></a>Ajouter votre domaine, vos utilisateurs et configurer des stratégies

Lorsque vous achetez Microsoft 365 Business Premium, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un lors de [l’inscription.](sign-up.md)

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Choisissez **Configurer** pour démarrer l’Assistant.

    ![Sélectionnez Aller à l’installation.](../media/gotosetupinadmincenter.png)

3. Sur la page **Installer vos applications Office**, vous pouvez installer les applications sur votre ordinateur.
    
4. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape **Ajouter un domaine** ici. Accédez à [Ajouter des utilisateurs](#add-users-and-assign-licenses) à la place.

    ![Capture d’écran de la page Personnaliser votre connectez-vous.](../media/adddomain.png)

    
4. Suivez les étapes de l’Assistant pour créer des enregistrements DNS chez un fournisseur d’hébergement [DNS pour Microsoft 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes propriétaire du domaine. Si vous savez qu’il s’agit de votre hôte de domaine, consultez également les [Instructions propres à l’hôte](/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](../admin/add-users/add-users.md) dans le Centre d’administration. De plus, si vous avez un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Les utilisateurs que vous ajoutez dans l’Assistant obtiennent automatiquement une licence Microsoft 365 Business Premium.

![Capture d’écran de la page Ajouter de nouveaux utilisateurs dans l’Assistant](../media/addnewuserspage.png)

1. Si votre abonnement Microsoft 365 Business Premium dispose d’utilisateurs existants (par exemple, si vous avez utilisé Azure AD Connect), vous avez la possibilité de leur attribuer des licences maintenant. Poursuivez et ajoutez des licences pour eux aussi.

2. Une fois que vous avez ajouté les utilisateurs, vous avez également la possibilité de partager des informations d’identification avec les nouveaux utilisateurs que vous ajoutez. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.

### <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas, modifiez les serveurs de noms pour configurer [Microsoft 365 auprès d’un bureau d’enregistrement de domaines.](../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md) 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d’autres hôtes DNS (non activé pour la connexion de domaine), vous pouvez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. Pour plus d’informations, consultez [notions de base du domaine](/office365/admin/get-help-with-domains/dns-basics).

        ![Page Activer les enregistrements.](../media/activaterecords.png)

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

### <a name="protect-your-organization"></a>Protéger votre organisation 

Les stratégies que vous avez définies dans l’Assistant sont appliquées automatiquement à un groupe [de sécurité](/office365/admin/create-groups/compare-groups#security-groups) appelé Tous *les utilisateurs.* Vous pouvez également créer des groupes supplémentaires pour attribuer des stratégies dans le Centre d’administration.

1. Dans l’option Augmenter la **protection** contre les cybermenaces avancées, il est recommandé d’accepter les valeurs par défaut pour laisser [Office 365 Advance Threat Protection](../security/defender-365-security/defender-for-office-365.md) analyser les fichiers et les liens dans les applications Office.

    ![Capture d’écran de la page Augmenter la protection.](../media/increasetreatprotection.png)


2. Dans la page Empêcher les fuites de données **sensibles,** acceptez les valeurs par défaut pour activer la protection contre la perte de données Office 365 (DLP) pour suivre les données sensibles dans les applications Office et empêcher le partage accidentel de ces données à l’extérieur de votre organisation.

3. Dans la page Protéger les données dans Office pour **appareils mobiles,** laissez la gestion des applications mobiles en place, développez les paramètres et examinez-les, puis sélectionnez Créer une stratégie de gestion des applications **mobiles.**

    ![Capture d’écran de la page Protéger les données dans Office pour appareils mobiles.](../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Sécuriser les PC Windows 10

Dans le navigation de gauche, sélectionnez **Programme** d’installation, puis, sous Se connectez **et sécurité,** sélectionnez Sécuriser **vos ordinateurs Windows 10.** Choose **View** to get started. Pour obtenir des instructions complètes, consultez sécuriser vos ordinateurs [Windows 10.](secure-win-10-pcs.md)

## <a name="deploy-office-365-client-apps"></a>Déployer des applications clientes Office 365

Si vous avez choisi d’installer automatiquement les applications Office lors de l’installation, elles s’installent sur les appareils Windows 10 une fois que les utilisateurs se sont connectés à Azure AD à partir de leurs appareils Windows, à l’aide de leurs informations d’identification professionnelles.

Pour installer Office sur des appareils iOS ou Android mobiles, voir Configurer des appareils mobiles pour les utilisateurs [de Microsoft 365 Business Premium.](set-up-mobile-devices.md)

Vous pouvez également installer Office individuellement. Voir [installer Office sur un PC ou Mac pour](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) obtenir des instructions.

## <a name="see-also"></a>Voir aussi

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
