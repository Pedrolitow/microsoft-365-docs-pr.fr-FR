---
title: Configurer Microsoft 365 Business Standard
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
- BEA160
description: Découvrez comment configurer votre abonnement Microsoft 365 Business Standard.
ms.openlocfilehash: 9efd14af2955e85b9b13c437ad869710f69a90f6
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579085"
---
# <a name="set-up-microsoft-business-standard"></a>Configurer Microsoft Business Standard



## <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

Lorsque vous achetez Microsoft 365 Business Standard, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un pendant l’inscription.

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification d’administrateur général. 

2. Choisissez **Configurer** pour démarrer l’Assistant.

3. Sur la page **Installer vos applications Office**, vous pouvez installer les applications sur votre ordinateur.
    
4. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape **Ajouter un domaine** ici. Accédez à [Ajouter des utilisateurs](#add-users-and-assign-licenses) à la place.

    
4. Suivez les étapes de l’Assistant pour [Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes le propriétaire du domaine. Si vous savez qu’il s’agit de votre hôte de domaine, consultez également les [Instructions propres à l’hôte](/office365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](../add-users/add-users.md) dans le Centre d’administration. De plus, si vous avez un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Les utilisateurs que vous ajoutez à l’Assistant reçoivent automatiquement une licence Microsoft 365 Business Standard.

1. Si votre abonnement Microsoft 365 Business Standard est associé à des utilisateurs existants (par exemple, si vous utilisiez Azure AD Connect), vous avez la possibilité de leur attribuer des licences à ce stade. Poursuivez et ajoutez des licences pour eux aussi.

2. Une fois que vous avez ajouté les utilisateurs, vous avez également la possibilité de partager des informations d’identification avec les nouveaux utilisateurs que vous ajoutez. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou de les télécharger.

## <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas,[Modifier les serveurs de noms de manière à configurer Office 365 avec n'importe quel bureau d'enregistrement de domaines](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d’autres hôtes DNS (non activé pour la connexion de domaine), vous pouvez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. Pour plus d’informations, consultez [notions de base du domaine](/office365/admin/get-help-with-domains/dns-basics).

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

    Une fois le processus d'inscription terminé, vous êtes dirigé vers le centre d'administration, où vous suivez un assistant qui vous aide à installer les applications Office, ajouter votre domaine, ajouter des utilisateurs et attribuer des licences. Une fois la configuration initiale terminée, vous pouvez utiliser la page de **configuration** dans le centre d'administration pour continuer la mise en place et la configuration des services qui accompagnent vos abonnements.

    Pour plus d'informations sur l'assistant de configuration et la page de **configuration** du centre d'administration, consultez la rubrique [Différence entre l'assistant de configuration et la page de configuration](o365-setup-wizard-and-setup-page.md).

## <a name="finish-setting-up"></a>Terminez la configuration

### <a name="set-up-outlook-for-email"></a>Configurer Outlook pour le courrier électronique

1. Dans le menu Démarrer de Windows, recherchez Outlook, puis sélectionnez-le.

    (Si vous utilisez un Mac, ouvrez Outlook à partir de la barre d’outils ou recherchez-le à l’aide du Finder).

    Si vous venez d’installer Outlook, sur la page Accueil, sélectionnez **Suivant**.

2. Choisissez **Fichier** \> **Informations** \> **Ajouter un compte**.

3. Entrez votre adresse e-mail Microsoft , puis sélectionnez **Se connecter**.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
Pour plus d’informations, voir [Configurer Outlook pour le courrier](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>Importer le courrier électronique

Si vous utilisiez Outlook avec un autre compte de courrier, vous pouvez importer vos e-mails, votre calendrier et vos contacts antérieurs dans votre nouveau compte Microsoft.
  
1. **Exporter vos anciens e-mails**

    Dans Outlook, choisissez **Fichier** \> **Ouvrir &amp; Exporter** \> **Importer/Exporter**.

    Sélectionnez **Exporter vers un fichier**, puis suivez la procédure pour exporter votre fichier de données Outlook (.pst) et tous les sous-dossiers.

2. **Importer vos anciens e-mails**

    Dans Outlook, choisissez de nouveau **Fichier** \> **Ouvrir &amp; Exporter** \> **Importer/Exporter**.

    Cette fois, sélectionnez **Importer à partir d’un autre programme ou fichier** et suivez la procédure pour importer le fichier de sauvegarde que vous avez créé lors de l’exportation de vos anciens e-mails.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Pour plus d’informations, voir [Importer le courrier avec Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Vous pouvez également utiliser le Centre d’administration Exchange pour importer le courrier électronique de tout le monde. Pour obtenir plus d'informations, consultez l'article [Migrer plusieurs comptes de messagerie](/Exchange/mailbox-migration/mailbox-migration).
  
### <a name="use-a-public-website"></a>Utiliser un site web public

Microsoft 365 n'inclut pas de site web public pour votre entreprise. Si vous voulez en configurer un, vous pouvez utiliser un partenaire Microsoft, tel que GoDaddy ou WIX.
  
1. Dans le centre d’administration, accédez à **Ressources**, puis sélectionnez **Site web public**.

2. Sélectionnez **En savoir plus** sous l’une des options, puis inscrivez-vous à un site web partenaire et servez-vous de ses outils pour configurer et concevoir votre site.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

Pour plus d’informations, voir [Utiliser un site web public](https://support.microsoft.com/office/3325d50e-d131-403c-a278-7f3296fe33a9).