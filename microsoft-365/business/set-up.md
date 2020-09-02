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
description: Découvrez les étapes de configuration de Microsoft 365 Business Premium, y compris l’ajout d’un domaine et d’utilisateurs, la configuration des stratégies de sécurité, et bien plus encore.
ms.openlocfilehash: cc20637d7a78bd34ecb61a4ed46eb06d564d63df
ms.sourcegitcommit: 25afc0c34edc7f8a5eb389d8c701175256c58ec8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "47324493"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Configurer Microsoft 365 Business Premium dans l’Assistant Installation

Regardez cette vidéo pour obtenir une vue d’ensemble de l’installation de Microsoft 365 Business Premium.<br><br>

## <a name="add-your-domain-users-and-set-up-policies"></a>Ajouter votre domaine, vos utilisateurs et configurer des stratégies

Lorsque vous achetez Microsoft 365 Business Premium, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un lors de l' [inscription](sign-up.md).

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Choisissez **Configurer** pour démarrer l’Assistant.

    ![Sélectionnez atteindre le programme d’installation.](../media/gotosetupinadmincenter.png)

3. Sur la page **Installer vos applications Office**, vous pouvez installer les applications sur votre ordinateur.
    
4. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape **Ajouter un domaine** ici. Accédez à [Ajouter des utilisateurs](#add-users-and-assign-licenses) à la place.

    ![Capture d’écran de la page Personnalisez votre connexion.](../media/adddomain.png)

    
4. Suivez les étapes de l’Assistant pour [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Microsoft 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes propriétaire du domaine. Si vous savez qu’il s’agit de votre hôte de domaine, consultez également les [Instructions propres à l’hôte](https://docs.microsoft.com/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](add-users-m365b.md) dans le Centre d’administration. De plus, si vous avez un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Tous les utilisateurs que vous ajoutez dans l’Assistant reçoivent automatiquement une licence Microsoft 365 Business Premium.

![Capture d’écran de la page Ajouter de nouveaux utilisateurs dans l’Assistant](../media/addnewuserspage.png)

1. Si votre abonnement Microsoft 365 Business Premium comporte des utilisateurs existants (par exemple, si vous avez utilisé Azure AD Connect), vous avez la possibilité de leur attribuer des licences. Poursuivez et ajoutez des licences pour eux aussi.

2. Une fois que vous avez ajouté les utilisateurs, vous avez également la possibilité de partager des informations d’identification avec les nouveaux utilisateurs que vous ajoutez. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.

### <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas, [Modifiez les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/change-nameservers-at-any-domain-registrar)d’enregistrement de domaine. 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d’autres hôtes DNS (non activé pour la connexion de domaine), vous pouvez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. Pour plus d’informations, consultez [notions de base du domaine](https://docs.microsoft.com/office365/admin/get-help-with-domains/dns-basics).

        ![Page activer les enregistrements.](../media/activaterecords.png)

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

### <a name="protect-your-organization"></a>Protéger votre organisation 

Les stratégies que vous configurez dans l’Assistant sont appliquées automatiquement à un [groupe de sécurité](https://docs.microsoft.com/office365/admin/create-groups/compare-groups#security-groups) appelé *tous les utilisateurs*. Vous pouvez également créer des groupes supplémentaires auxquels affecter des stratégies dans le centre d’administration.

1. Sur la **protection renforcée contre les menaces informatiques avancées**, il est recommandé d’accepter les valeurs par défaut pour permettre à [Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) d’analyser les fichiers et les liens dans les applications Office.

    ![Capture d’écran de la page d’augmentation de la protection.](../media/increasetreatprotection.png)


2. Sur la page **empêcher les fuites de données sensibles** , acceptez les valeurs par défaut pour activer la protection contre la perte de données (DLP) d’Office 365 pour effectuer le suivi des données sensibles dans les applications Office et empêcher le partage accidentel de ces derniers à l’extérieur de votre organisation.

3. Sur la page **protéger les données dans Office pour les appareils mobiles** , conservez la gestion des applications mobiles activée, développez les paramètres et examinez-les, puis sélectionnez **créer une stratégie de gestion des applications mobiles**.

    ![Capture d’écran de la page protéger les données dans Office pour les appareils mobiles.](../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Sécurisation des PC Windows 10

Dans le volet de navigation de gauche, sélectionnez **configuration** , puis sous **connexion et sécurité**, choisissez **sécuriser vos ordinateurs Windows 10**. Choisissez **affichage** pour commencer. Pour plus d’informations, consultez [la rubrique sécuriser vos ordinateurs Windows 10](secure-win-10-pcs.md) .

## <a name="deploy-office-365-client-apps"></a>Déployer des applications clientes Office 365

Si vous avez choisi d’installer automatiquement les applications Office lors de l’installation, les applications sont installées sur les appareils Windows 10 une fois que les utilisateurs se sont connectés à Azure AD à partir de leurs appareils Windows, à l’aide de leurs informations d’identification professionnelles.

Pour installer Office sur des appareils mobiles iOS ou Android, consultez la rubrique [configurer des appareils mobiles pour les utilisateurs de Microsoft 365 Business Premium](set-up-mobile-devices.md).

Vous pouvez également installer Office individuellement. Pour obtenir des instructions, voir [installer Office sur un PC ou un Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) .

## <a name="see-also"></a>Voir aussi

[Vidéos de formation Microsoft 365 Entreprise](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816)
