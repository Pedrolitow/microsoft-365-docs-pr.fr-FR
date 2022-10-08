---
title: Configurer Microsoft 365 Business Basic
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- VSBFY23
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
- BEA160
description: Découvrez comment configurer votre abonnement Microsoft 365 Business Basic.
ms.openlocfilehash: 592f3553e0e403276fc8d91028545dca5210e91e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68168966"
---
# <a name="set-up-microsoft-365-business-basic"></a>Configurer Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>Configurer Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="add-an-existing-domain-to-your-microsoft-365-business-basic-subscription"></a>Ajouter un domaine existant à votre abonnement Microsoft 365 Business Basic

Lorsque vous achetez Microsoft 365 Business Basic, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un pendant l’inscription.

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. Choisissez **Configurer** pour démarrer l’Assistant.

3. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l’inscription, vous ne verrez pas l’étape **Ajouter un domaine** ici. Accédez à [Ajouter des utilisateurs](#add-users-and-assign-licenses) à la place.

4. Suivez les étapes de l’Assistant pour [Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes le propriétaire du domaine. Si vous connaissez votre hôte de domaine, voir aussi [Ajouter un domaine à Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](../add-users/add-users.md) dans le Centre d’administration.

Les utilisateurs que vous ajoutez à l’Assistant reçoivent automatiquement une licence Microsoft 365 Business Basic.

1. If your Microsoft 365 Business Basic subscription has existing users (for example, if you used Azure AD Connect), you get an option to assign licenses to them now. Go ahead and add licenses to them as well.

2. After you've added the users, you'll also get an option to share credentials with the new users you added. You can choose to print them out, email them, or download them.

## <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas,[Modifier les serveurs de noms de manière à configurer Office 365 avec n'importe quel bureau d'enregistrement de domaines](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - If you have existing DNS records with other DNS hosts (not enabled for domain connect), you'll want to manage your own DNS records to make sure the existing services stay connected. See [domain basics](/office365/admin/get-help-with-domains/dns-basics) for more info.

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

    Une fois le processus d'inscription terminé, vous êtes dirigé vers le centre d'administration, où vous pouvez ajouter votre domaine, ajouter des utilisateurs et attribuer des licences. Une fois la configuration initiale terminée, vous pouvez utiliser la page de **configuration** dans le centre d'administration pour continuer la mise en place et la configuration des services qui accompagnent vos abonnements.

    Pour plus d'informations sur l'assistant de configuration et la page de **configuration** du centre d'administration, consultez la rubrique [Différence entre l'assistant de configuration et la page de configuration](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>Regardez : configurer le courrier électronique d’entreprise avec un nouveau domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Étapes : configurer le courrier électronique d’entreprise avec un nouveau domaine

1. Sur la page Web **Comment vous connecter** de l'inscription à Microsoft 365 Business Standard, choisissez **Créer un nouveau compte de messagerie professionnelle (avancé)**.

2. Suivez les étapes pour acheter un nouveau domaine et entrez le nom de domaine que vous souhaitez utiliser (par contoso.com). Une fois que vous avez acheté votre domaine, vous pouvez ajouter des utilisateurs et des [licences](../add-users/add-users.md) et installer vos applications Office dans le Centre d’administration.

## <a name="finish-setting-up"></a>Terminez la configuration

Suivez les étapes ci-dessous pour configurer Outlook, Teams, OneDrive et votre site web.

### <a name="step-set-up-outlook-for-email"></a>Étape : configurer Outlook pour le courrier électronique

1. Dans le menu Démarrer de Windows, recherchez Outlook, puis sélectionnez-le.

    (Si vous utilisez un Mac, ouvrez Outlook à partir de la barre d’outils ou recherchez-le à l’aide du Finder).

    Si vous venez d’installer Outlook, sur la page Accueil, sélectionnez **Suivant**.

2. Choisissez **Fichier** \> **Informations** \> **Ajouter un compte**.

3. Entrez votre adresse e-mail Microsoft , puis sélectionnez **Se connecter**.

## <a name="watch-set-up-outlook-for-email"></a>Observation : Configurer Outlook pour l’e-mail

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

## <a name="watch-import-and-redirect-email"></a>Observation : Importer et rediriger un e-mail

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Pour plus d’informations, voir [Importer le courrier avec Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Vous pouvez également utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> pour importer le courrier électronique de tout le monde. Pour obtenir plus d'informations, consultez l'article [Migrer plusieurs comptes de messagerie](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>Configurer Microsoft Teams et OneDrive pour les entreprises

Select the OneDrive cloud icon from your taskbar and follow the steps to move your files to your new OneDrive for Business folder. Select **Next** to set up Microsoft Teams.

1. Ouvrez Microsoft Teams, sélectionnez votre icône de profil, puis **ajoutez un compte scolaire ou scolaire.** Suivez les étapes pour ajouter votre nouveau compte à Teams.

## <a name="use-a-public-website"></a>Utiliser un site web public

Microsoft 365 n'inclut pas de site web public pour votre entreprise. Si vous voulez en configurer un, vous pouvez utiliser un partenaire Microsoft, tel que GoDaddy ou WIX.
  
1. Dans le centre d’administration, accédez à **Ressources**, puis sélectionnez **Site web public**.

2. Sélectionnez **En savoir plus** sous l’une des options, puis inscrivez-vous à un site web partenaire et servez-vous de ses outils pour configurer et concevoir votre site.

## <a name="watch-create-your-business-website"></a>Observation : Créez votre site web professionnelle

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Inviter des utilisateurs à rejoindre votre abonnement et votre organisation

Une fois que vous avez configuré votre organisation, vous pouvez inviter d’autres utilisateurs à rejoindre votre abonnement d’entreprise Microsoft 365. Ils auront accès à toutes les fonctionnalités de l’abonnement.

[Inviter des utilisateurs dans mon abonnement](../simplified-signup/admin-invite-business-standard.md)

Informez vos utilisateurs qu’ils peuvent suivre la procédure des articles ci-dessous pour rejoindre votre organisation et votre abonnement.

- [Accepter une invitation par e-mail](../simplified-signup/user-invite-business-standard.md)

- [Accepter une invitation par e-mail à l’aide d’Outlook, de Yahoo, de Gmail ou d’un autre compte (utilisateur)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>Rubriques connexes

[Migrer des données vers mon abonnement Microsoft 365 Business Standard abonnement](../simplified-signup/migrate-data-business-standard.md)
