---
title: Configurer Microsoft 365 Business
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Découvrez comment configurer Microsoft 365 Business.
ms.openlocfilehash: e635b828609fc47cd8b92bb179a25bcc43cb0a1a
ms.sourcegitcommit: db1dfb2df2c2f7beced3b57bc772d106c189e88a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "33660776"
---
# <a name="set-up-microsoft-365-business"></a>Configurer Microsoft 365 Business

Avant de commencer, reportez-vous à la rubrique obtenir les détails de l’inscription de [Microsoft 365 Business](get-microsoft-365-business.md) .

Visionnez une [courte vidéo sur la configuration de Microsoft 365 Business](https://support.office.com/article/38003e30-9d10-44cf-b596-f1b5f662bfa1) à l’aide de l’Assistant de configuration et lorsque vous n’avez pas d’Active Directory local.
  

## <a name="overview"></a>Vue d’ensemble

La plupart des étapes de configuration peuvent être effectuées dans l’Assistant Installation, mais les autres options sont également répertoriées.

1. [Ajouter votre domaine](#add-your-domain-to-personalize-sign-in) (si vous avez acheté votre domaine lors de l' [inscription](sign-up.md), cette étape est déjà terminée).
2. Ajouter des utilisateurs. Pour ce faire, vous pouvez procéder de l’une des manières suivantes:
    - Dans l' [Assistant Installation](#add-users-in-the-wizard).
    - Utilisez la synchronisation d’annuaires pour [Ajouter des utilisateurs à l’aide d’Azure ad Connect](#add-users-by-using-azure-ad-connect) si vous disposez d’un annuaire Active Directory local.
    - Vous pouvez également [Ajouter des utilisateurs ultérieurement](add-users-m365b.md) dans le centre d’administration.
3. Configurez les stratégies de sécurité et configurez les appareils. Pour ce faire, vous pouvez procéder de l’une des manières suivantes:
    - Dans l' [Assistant Installation](#set-up-policies-in-the-wizard).  
    - Dans le [Centre d’administration](#modify-or-add-policies-in-the-admin-center).
    - Dans le [Centre d’administration Intune](https://docs.microsoft.com/intune/what-is-device-management).
4. Configurez et gérez les appareils Windows 10.

    Lorsque vous joignez un appareil WIndows 10 à Azure AD, toutes les stratégies sont appliquées.
    - Configurez les configurations des appareils Windows 10 dans l' [Assistant Installation](#set-up-policies-in-the-wizard).
    - Rejoignez un [nouveau périphérique Windows 10](set-up-windows-devices.md#for-a-brand-new-or-newly-upgraded-windows-10-pro-device) à Azure ad.
    - Associez un [appareil Windows 10](set-up-windows-devices.md#for-a-device-already-set-up-and-running-windows-10-pro) à Azure ad.
1. Installez Office 365 Business.
    - Vous pouvez installer automatiquement Office sur les appareils Windows à l’aide de l' [Assistant Installation](#set-up-policies-in-the-wizard).
    - [Installer automatiquement Office](auto-install-or-uninstall-office.md) à partir du centre d’administration.
    - Autorisez les utilisateurs à [installer les applications Office](https://docs.microsoft.com/office365/admin/setup/install-applications) pour Windows et les appareils.
     
1. Configurez une sécurité supplémentaire.
    - L’Assistant installation ajoute des stratégies pour sécuriser vos appareils, mais vous pouvez également tirer parti de fonctionnalités de [sécurité supplémentaires](#additional-security-settings) pour sécuriser vos données, vos comptes et vos e-mails. 

## <a name="add-your-domain-users-and-set-up-policies"></a>Ajouter votre domaine, vos utilisateurs et configurer des stratégies

![Bannière pointant vers https://aka.ms/aboutM365preview.](media/m365admincenterchanging.png)

Lorsque vous achetez Microsoft 365 Business, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un lors de l' [inscription](sign-up.md).

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez le déplacer pour [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Sélectionnez **Ajouter un domaine** pour démarrer l’Assistant.

    ![Sélectionnez Ajouter un domaine.](media/addadomainadmincenter.png)
    
3. Dans l’Assistant, entrez le nom de domaine que vous souhaitez utiliser (par exemple, contoso.com).


    ![Capture d’écran de la page Personnalisez votre connexion.](media/personalizesignin.png)

    
4. Suivez les étapes de l’Assistant pour [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes propriétaire du domaine. Si vous êtes conscient de votre hôte de domaine, reportez-vous aux [instructions spécifiques](https://docs.microsoft.com/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions)de l’hôte.

    Si votre fournisseur d’hébergement est GoDaddy, le processus est facile et vous êtes automatiquement invité à vous connecter et à permettre à Microsoft de s’authentifier à votre place:

    ![Sur GoDaddy, sélectionnez Autoriser.](media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs ultérieurement](add-users-m365b.md) dans le centre d’administration. En outre, si vous disposez d’un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Tous les utilisateurs que vous ajoutez dans l’Assistant reçoivent automatiquement une licence d’entreprise Microsoft 365.
Si vous disposez d’un contrôleur de domaine local et que vous utilisez Active Directory, voir [How to DDD Users by using Azure ad Connect](#add-users-by-using-azure-ad-connect).

![Capture d’écran de la page Ajouter de nouveaux utilisateurs dans l’Assistant](media/addnewuserspage.png)

1. Si votre abonnement Microsoft 365 Entreprise est associé à des utilisateurs existants (par exemple, si vous utilisiez Azure AD Connect), vous avez la possibilité de leur attribuer des licences à ce stade. Poursuivez et ajoutez des licences pour eux aussi.

3. Une fois que vous avez ajouté les utilisateurs, vous pouvez également partager les informations d’identification avec les nouveaux utilisateurs que vous avez ajoutés. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.

4. Ignorez la migration des messages e-mail et sélectionnez **Suivant** dans la page **Migrer les messages e-mail**. 

    Si vous effectuez une migration à partir d’un autre fournisseur de courrier et que vous souhaitez copier vos données ultérieurement, vous pouvez migrer le [courrier électronique et les contacts vers Office 365](https://support.office.com/article/a3e3bddb-582e-4133-8670-e61b9f58627e).

#### <a name="add-users-by-using-azure-ad-connect"></a>Ajouter des utilisateurs à l’aide d’Azure AD Connect

 Si vous disposez d’un contrôleur de domaine local avec Active Directory, vous synchronisez vos utilisateurs avec Microsoft 365 Business à l’aide d' [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-express). Effectuez cette opération avant de démarrer l’Assistant installation. Vous pouvez le télécharger dans le centre d’administration:

- Accédez à **** \> utilisateurs **actifs utilisateurs**, sélectionnez les ellipses en haut de la page, puis sélectionnez **synchronisation d’annuaires** pour télécharger Azure ad Connect.

    ![Sur la page utilisateurs actifs, sélectionnez ellipses > Directory snchronization.](media/setupdirsync.png)

    > [!IMPORTANT]
    > Si vous créez des utilisateurs de cette manière, vous devrez toujours leur attribuer des licences dans le centre d’administration.

##### <a name="continue-to-access-domain-joined-apps-and-devices"></a>Continuer à accéder aux applications et aux appareils joints au domaine

Si vous souhaitez continuer à accéder aux applications et aux appareils joints par le domaine, lisez les articles suivants pour les deux façons d’activer ce qui suit:
  
- [Activer la gestion des appareils Windows 10 associés à un domaine par Microsoft 365 Business](manage-windows-devices.md)
    - Il s’agit de la méthode recommandée.

- [Accéder aux ressources locales à partir d’un appareil joint à Azure AD dans Microsoft 365 Business](access-resources.md)

### <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine. onmicrosoft ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d'enregistrement de domaines.
  
1. L'Assistant Configuration détecte généralement votre bureau d'enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d'enregistrement. Si ce n’est pas le cas, [Modifiez les serveurs de noms pour configurer Office 365 avec n’importe quel](https://support.office.com/article/a8b487a9-2a45-4581-9dc4-5d28a47010a2)Bureau d’enregistrement de domaine. 

    - Si vous avez des enregistrements DNS existants, par exemple un site Web existant, vous devez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. Pour plus d’informations, voir [notions de base](https://docs.microsoft.com/office365/admin/get-help-with-domains/dns-basics) sur le domaine.

        ![Connecter votre page de domaine avec je vais gérer mes propres enregistrements DNS.](media/connectyourdomainpage.png)

2. Suivez les étapes de l’Assistant et de la messagerie et d’autres services sont configurés pour vous.

### <a name="set-up-security-policies-and-device-configurations"></a>Configurer les stratégies de sécurité et les configurations des appareils 

Ces stratégies s’appliquent à tous les utilisateurs auxquels vous octroyez une licence, ou à un groupe d’utilisateurs si vous décidez d’affecter des stratégies différentes à un ensemble d’utilisateurs.

#### <a name="set-up-policies-in-the-wizard"></a>Configurer des stratégies dans l’Assistant

Les stratégies que vous configurez dans l’Assistant sont appliquées automatiquement à un [groupe de sécurité](https://docs.microsoft.com/office365/admin/create-groups/compare-groups#security-groups) appelé *tous les utilisateurs*.

1. Dans la case à cocher **protéger vos fichiers professionnels sur les appareils mobiles** , l’option **protéger les fichiers de travail lorsque les appareils sont perdus ou volés** est sélectionnée par défaut. Vous avez la possibilité d’activer **la gestion de la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles**, ce qui est recommandé.

    ![Capture d’écran de la page protéger les fichiers de travail sur les appareils mobiles.](media/protectworkfilesondevices.png)

     - Si vous développez **protéger les fichiers de travail en cas de perte ou de vol des appareils**, les [valeurs par défaut](protect-work-files-on-lost-or-stolen-device.md) sont présélectionnées:

        ![Capture d’écran des valeurs par défaut pour la protection des fichiers sur les appareils perdus.](media/protectworkfilesondevicesdefault.png)

    - Si vous sélectionnez **gérer la manière dont les utilisateurs accèdent aux fichiers Office sur les appareils mobiles** et les développer, les [valeurs par défaut](manage-user-access-on-mobile-devices.md) sont affichées. Nous vous recommandons d'accepter les valeurs par défaut lors de l'installation pour créer des stratégies d'application pour Windows 10, iOS et Android qui s'appliquent à tous les utilisateurs. Vous pouvez créer des stratégies supplémentaires une fois l'installation terminée.

        ![Capture d’écran des paramètres de protection pour les fichiers Office sur mobile.](media/useraccessonmobile.png)

2. La dernière étape sur la protection des données et des périphériques vous permet de configurer des stratégies pour sécuriser les appareils Windows 10. Ces paramètres sont appliqués automatiquement lorsque le Windows 10 d’un utilisateur se connecte à votre organisation. Vous pouvez développer des **appareils Windows 10 sécurisés** pour afficher et modifier les [valeurs par défaut](secure-windows-10-devices.md).
3. Vous pouvez également choisir d' [installer automatiquement Office](install-office-on-windows-10-during-setup.md) sur les appareils Windows 10.

    ![Capture d’écran de la page définir la configuration de l’appareil Windows 10.](media/setwin10config.png)

#### <a name="modify-or-add-policies-in-the-admin-center"></a>Modifier ou ajouter des stratégies dans le centre d’administration

Consultez la rubrique [Manage Microsoft 365 Business](manage.md) pour obtenir des liens vers des rubriques expliquant comment afficher et modifier des stratégies de protection des applications et des périphériques, et comment supprimer ou réinitialiser des appareils utilisateur.

## <a name="deploy-and-manage-windows-10"></a>Déployer et gérer Windows 10
Consultez la rubrique [configurer les appareils Windows pour les utilisateurs professionnels de Microsoft 365](set-up-windows-devices.md) pour se connecter manuellement à Azure ad, soit lors de la configuration des nouveaux ordinateurs, soit en modifiant le profil de connexion pour les ordinateurs existants. 

### <a name="use-autopilot-to-set-up-new-devices"></a>Utiliser AutoPilot pour configurer de nouveaux appareils

Vous pouvez utiliser [Windows AutoPilot](add-autopilot-devices-and-profile.md) pour préconfigurer automatiquement les **nouveaux** appareils Windows 10 pour un utilisateur, mais il peut être plus facile d’obtenir un [partenaire](https://www.microsoft.com/solution-providers/search) qui peut le faire pour vous. Vous pouvez également accéder à [Microsoft Store](https://go.microsoft.com/fwlink/?linkid=874598) et demander à un spécialiste de la technologie Cloud de configurer de nouveaux appareils que vous achetez pour vous.

### <a name="access-on-premises-resources"></a>Accéder aux ressources locales

Si votre organisation utilise Windows Server Active Directory en local, vous pouvez configurer Microsoft 365 entreprise pour protéger vos appareils Windows 10, tout en conservant l’accès aux ressources locales qui nécessitent une authentification locale. Suivez les étapes de la procédure [activer les appareils Windows 10 appartenant à un domaine pour qu’ils soient gérés par Microsoft 365 Business](manage-windows-devices.md) pour le configurer. Il s’agit de la méthode préférée et les appareils dans cet État sont appelés appareils hybrides Azure AD.

Si votre entreprise dispose d’un annuaire local Active Directory qui contient certaines ressources locales (telles que des partages de fichiers et des imprimantes), vous pouvez donner à vos appareils joints à Azure AD l’accès à ces ressources en suivant les étapes ci-dessous: accéder à des [ressources locales à partir d’un Appareil rejoint Azure AD dans Microsoft 365 Business](access-resources.md).

## <a name="deploy-office-365-client-apps"></a>Déployer des applications clientes Office 365

Si vous avez choisi d’installer automatiquement les applications Office dans lors de la configuration, les applications s’installeront sur les appareils Windows 10 une fois que les utilisateurs se sont connectés à Azure AD à partir de leurs appareils Windows avec leurs informations d’identification professionnelles.
Pour installer Office sur des appareils mobiles iOS ou Android, consultez la rubrique [configurer des appareils mobiles pour les utilisateurs professionnels de Microsoft 365](set-up-mobile-devices.md).

Vous pouvez également installer Office individuellement. Pour obtenir des instructions, voir [installer Office sur un PC ou un Mac](https://support.office.com/article/4414eaaf-0478-48be-9c42-23adc471665) .

## <a name="additional-security-settings"></a>Paramètres de sécurité supplémentaires

Outre le paramètre de sécurité et de conformité dans l’Assistant Installation, vous pouvez également configurer les paramètres supplémentaires suivants:
  
- **Protection contre les programmes malveillants**
- **Pièces jointes sûres de protection avancée contre les menaces**
- **Liens fiables ATP**
- **Protection contre le hameçonnage APT**
- **Archivage Exchange Online**
- **Protection contre la perte de données (DLP)**
- **Azure information protection** (Plan 1)
- **Disponibilité du portail Intune**

Pour commencer, consultez la rubrique [configurer des stratégies de sécurité avancées](set-up-advanced-security.md).

Consultez également les [10 meilleures façons de sécuriser votre entreprise Microsoft 365](https://docs.microsoft.com/office365/admin/security-and-compliance/secure-your-business-data) pour obtenir une feuille de route des meilleures pratiques en matière de sécurité.