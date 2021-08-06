---
title: Configurer Microsoft 365 Business Basic
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
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
- BEA160
description: Découvrez comment configurer votre abonnement Microsoft 365 Business Basic.
ms.openlocfilehash: 07e2aae24b74f12925d94eb1bd2104654cd89fb00e418a943da990c15c6b0445
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53821518"
---
# <a name="set-up-microsoft-365-business-basic"></a>Configurer Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>Configurer Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="add-your-domain-to-personalize-sign-in"></a>Ajouter votre domaine pour personnaliser la connexion

Lorsque vous achetez Microsoft 365 Business Basic, vous avez la possibilité d’utiliser un domaine que vous possédez ou d’en acheter un pendant l’inscription.

- Si vous avez acheté un nouveau domaine lorsque vous vous êtes inscrit, votre domaine est configuré et vous pouvez accéder à [Ajouter des utilisateurs et attribuer des licences](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Choisissez **Configurer** pour démarrer l’Assistant.
    
3. Dans l’étape **ajouter un domaine**, entrez le nom de domaine que vous voulez utiliser (par exemple, contoso.com).

    > [!IMPORTANT]
    > Si vous avez acheté un domaine pendant l'inscription, vous ne verrez pas l'étape **Ajouter un domaine** ici. Allez à [Ajouter](#add-users-and-assign-licenses) des utilisateurs à la place.

    
4. Suivez les étapes de l’Assistant pour [Créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS pour Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) qui vérifie que vous êtes le propriétaire du domaine. Si vous connaissez votre hôte de domaine, voir aussi [Ajouter un domaine à Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Si votre fournisseur d’hébergement est GoDaddy ou si un autre hôte est activé avec [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), le processus est simple et vous êtes automatiquement invité à vous connecter et à laisser Microsoft s’authentifier en votre nom.

    ![Sur la page Confirmer l’accès GoDaddy, sélectionnez Autoriser.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

Vous pouvez ajouter des utilisateurs dans l’Assistant, mais vous pouvez également [Ajouter des utilisateurs plus tard](../add-users/add-users.md) dans le Centre d’administration. De plus, si vous avez un contrôleur de domaine local, vous pouvez ajouter des utilisateurs avec [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>Ajouter des utilisateurs dans l’Assistant

Les utilisateurs que vous ajoutez à l’Assistant reçoivent automatiquement une licence Microsoft 365 Business Basic.

1. Si votre abonnement Microsoft Office 365 Petite Entreprise est associé à des utilisateurs existants (par exemple, si vous utilisiez Azure AD Connect), vous avez désormais la possibilité de leur attribuer des licences. Poursuivez et ajoutez des licences pour eux aussi.

2. Après avoir ajouté des utilisateurs, vous avez également la possibilité de partager des informations d'identification avec les nouveaux utilisateurs que vous avez ajouté. Vous pouvez choisir de les imprimer, de les envoyer par e-mail ou les télécharger.

## <a name="connect-your-domain"></a>Sélectionner votre domaine

> [!NOTE]
> Si vous avez choisi d’utiliser le domaine .onmicrosoft, ou si vous avez utilisé Azure AD Connect pour configurer des utilisateurs, vous ne verrez pas cette étape.
  
Pour configurer des services, vous devez mettre à jour des enregistrements au niveau de votre hôte DNS ou de votre bureau d’enregistrement de domaines.
  
1. L’Assistant Configuration détecte généralement votre bureau d’enregistrement et vous fournit un lien vers des instructions détaillées vous permettant de mettre à jour vos enregistrements NS sur le site web du bureau d’enregistrement. Si ce n’est pas le cas,[Modifier les serveurs de noms de manière à configurer Office 365 avec n'importe quel bureau d'enregistrement de domaines](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Si vous avez des enregistrements DNS existants (par exemple, un site web existant), mais que votre hôte DNS est activé pour [connexion de domaine](/office365/admin/get-help-with-domains/domain-connect), sélectionnez **Ajouter des enregistrements pour moi**. Sur la page **sélectionnez votre services en ligne**, acceptez toutes les valeurs par défaut, puis sélectionnez **Suivant**, puis sélectionnez **Autoriser** sur la page de votre hôte DNS.
    - Si vous avez des enregistrements DNS existants avec d'autres hôtes DNS (non activés pour la connexion de domaine), vous devrez gérer vos propres enregistrements DNS pour vous assurer que les services existants restent connectés. [Voir les bases du domaine pour plus d'informations](/office365/admin/get-help-with-domains/dns-basics).

2. Suivez les étapes de l’Assistant, et la messagerie électronique et d’autres services sont configurés pour vous.

    Une fois le processus d'inscription terminé, vous êtes dirigé vers le centre d'administration, où vous pouvez ajouter votre domaine, ajouter des utilisateurs et attribuer des licences. Une fois la configuration initiale terminée, vous pouvez utiliser la page de **configuration** dans le centre d'administration pour continuer la mise en place et la configuration des services qui accompagnent vos abonnements.

    Pour plus d'informations sur l'assistant de configuration et la page de **configuration** du centre d'administration, consultez la rubrique [Différence entre l'assistant de configuration et la page de configuration](o365-setup-wizard-and-setup-page.md).