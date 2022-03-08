---
title: Configurer Microsoft 365 Business Premium
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez les étapes de configuration de Microsoft 365 Business Premium, notamment l’ajout d’un domaine et d’utilisateurs, la configuration de stratégies de sécurité, etc.
ms.openlocfilehash: b4d12d34e535a58c952a752fca63af6f67e30a61
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312388"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Configurer des Microsoft 365 Business Premium dans l’Assistant Installation

## <a name="watch-overview-of-microsoft-365-setup"></a>Regardez : Vue d’ensemble de Microsoft 365 configuration

Regardez cette vidéo pour obtenir une vue d’ensemble Microsoft 365 Business Premium configuration.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>Watch: Set up Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, puis **sélectionnez Aller à l’installation**. L’Assistant Installation démarre.
1. Une fois l’installation terminée, revenir au Centre d’administration Microsoft. Dans le Centre d’administration, vous pouvez continuer à configurer des fonctionnalités telles que Windows 10 stratégies, DLP, etc. sur la page **d’installation**.

## <a name="add-your-domain-users-and-set-up-policies"></a>Ajouter votre domaine, vos utilisateurs et configurer des stratégies

Lorsque vous achetez Microsoft 365 Business Premium, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un lors de [l’inscription](../admin-overview/sign-up-for-office-365.md).

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Choisissez **Configurer** pour démarrer l’Assistant.

    ![Sélectionnez Aller à l’installation.](../../media/gotosetupinadmincenter.png)

3. Sur la page **Installer vos applications Office**, vous pouvez installer les applications sur votre ordinateur.
    
4. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l'inscription, vous ne verrez pas l'étape **Ajouter un domaine** ici. Allez à [Ajouter](#add-users-and-assign-licenses) des utilisateurs à la place.

    ![Capture d’écran de la page Personnaliser votre connectez-vous.](../../media/adddomain.png)

    
4. Suivez les étapes de l’Assistant pour créer des enregistrements DNS chez un fournisseur d’hébergement [DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) Microsoft 365 qui vérifie que vous êtes propriétaire du domaine. Si vous connaissez votre hôte de domaine, voir aussi [Ajouter un domaine à Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](../add-users/add-users.md) dans le Centre d’administration. De plus, si vous avez un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Tous les utilisateurs que vous ajoutez dans l’Assistant obtiennent automatiquement une licence Microsoft 365 Business Premium licence.

![Capture d’écran de la page Ajouter de nouveaux utilisateurs dans l’Assistant.](../../media/addnewuserspage.png)

1. Si votre abonnement Microsoft 365 Business Premium compte des utilisateurs existants (par exemple, si vous avez utilisé Azure AD Connecter), vous avez la possibilité de leur attribuer des licences maintenant. Poursuivez et ajoutez des licences pour eux aussi.

2. Après avoir ajouté des utilisateurs, vous avez également la possibilité de partager des informations d'identification avec les nouveaux utilisateurs que vous avez ajouté. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou les télécharger.

### <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas, modifiez les serveurs de noms pour configurer [Microsoft 365 auprès d’un bureau d’enregistrement de domaines](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d'autres hôtes DNS (non activés pour la connexion de domaine), vous devrez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. [Voir les bases du domaine pour plus d'informations](/office365/admin/get-help-with-domains/dns-basics).

        ![Page Activer les enregistrements.](../../media/activaterecords.png)

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

### <a name="protect-your-organization"></a>Protéger votre organisation 

Les stratégies que vous avez définies dans l’Assistant sont appliquées automatiquement à un groupe [de sécurité](/office365/admin/create-groups/compare-groups#security-groups) appelé *Tous les utilisateurs*. Vous pouvez également créer des groupes supplémentaires pour attribuer des stratégies dans le Centre d’administration.

1. Dans l’option Augmenter la protection contre les **cybermenaces** avancées, il est recommandé d’accepter les valeurs par défaut pour Office 365 fichiers d’analyse et les liens de la [Protection](../../security/office-365-security/defender-for-office-365.md) avancée contre les menaces dans Office applications.

    ![Capture d’écran de la page Augmenter la protection.](../../media/increasetreatprotection.png)


2. Dans la page Empêcher les **fuites de données sensibles**, acceptez les valeurs par défaut pour activer la protection contre la perte de données Office 365 (DLP) pour suivre les données sensibles dans les applications Office et empêcher le partage accidentel de ces données à l’extérieur de votre organisation.

3. Dans la page Protéger les données **dans Office pour appareils** mobiles, laissez la gestion des applications mobiles en place, développez les paramètres et examinez-les, puis sélectionnez Créer une stratégie de gestion des applications **mobiles**.

    ![Capture d’écran de La protection des Office pour la page mobile.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Sécuriser les PC Windows 10

Dans le navigation de gauche, sélectionnez **Installation**, puis, sous Se **connectez-vous** et sécurité, sélectionnez Sécuriser **Windows 10 ordinateurs.** Choose **View** to get started. Pour [obtenir des instructions complètes, Windows 10 vos ordinateurs](secure-win-10-pcs.md) de sécurité.

## <a name="deploy-office-365-client-apps"></a>Déployer Office 365 applications clientes

Si vous avez choisi d’installer automatiquement des applications Office lors de l’installation, elles s’installeront sur les appareils Windows 10 une fois que les utilisateurs se sont connectés à Azure AD à partir de leurs appareils Windows, à l’aide de leurs informations d’identification professionnelles.

Pour installer Office sur des appareils mobiles iOS ou Android, voir Configurer des appareils [mobiles pour Microsoft 365 Business Premium utilisateurs](set-up-mobile-devices.md).

Vous pouvez également installer Office individuellement. Voir [installer Office sur un PC ou Mac pour](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) obtenir des instructions.

## <a name="related-content"></a>Contenu associé

[Vidéos de formation Microsoft 365 Entreprise](../../business-video/index.yml) (page de liens)
