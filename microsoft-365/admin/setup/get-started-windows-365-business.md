---
title: Démarrage avec les PC Windows 365 Business et Cloud
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
- MOE150
description: Découvrez comment acheter Windows 365 Business pour votre organisation et aider les utilisateurs à commencer à utiliser leurs PC Cloud.
ms.openlocfilehash: f806991bfd00cbaf9b96b7750d0358409785b206
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569236"
---
# <a name="get-started-with-windows-365-business-and-cloud-pcs"></a>Démarrage avec les PC Windows 365 Business et Cloud

Cet article est réservé aux personnes qui prévoient d’acheter et de configurer Windows 365 Business pour leur organisation.
  
[Windows 365 Business](https://www.microsoft.com/windows-365/business) est une version de Windows 365 qui est spécialement conçu pour être utilisé dans les petites entreprises (jusqu’à 300 sièges). Il offre aux organisations un moyen simple et simplifié de fournir des PC Cloud à leurs utilisateurs.  Avec Windows 365 Cloud, vous pouvez diffuser vos applications, données, contenu, paramètres et stockage à partir du cloud Microsoft.

> [!NOTE]  
> Avant de commencer, assurez-vous que les paramètres de votre appareil Azure AD pour les [utilisateurs](/azure/active-directory/devices/device-management-azure-portal#configure-device-settings) peuvent joindre des appareils **à Azure AD.**

   ![Les utilisateurs peuvent joindre des appareils aux paramètres Azure AD.](../../media/deschutes/azure-device-settings.png)
## <a name="prerequisites"></a>Configuration requise
Il n’existe aucune condition préalable de licence pour configurer Windows 365 Business.

Pour une expérience d’intégration optimisée, consultez le [guide](troubleshoot-windows-365-business.md) de dépannage de l’installation pour vous assurer que vos préférences d’environnement sont optimisées pour Windows 365 Entreprise. 

## <a name="buy-subscriptions"></a>Acheter des abonnements

Vous pouvez acheter des abonnements 365 Windows 365 Business de deux manières différentes pour vos utilisateurs :

- Site [Windows produits 365](https://www.microsoft.com/windows-365/business/compare-plans-pricing)
- Centre d’administration Microsoft 365

Après avoir acheté un abonnement, vous pouvez utiliser la Centre d’administration Microsoft 365 pour attribuer des licences aux utilisateurs de votre organisation.

### <a name="buy-subscriptions-through-the-windows-365-products-site"></a>Acheter des abonnements via le site Windows produits 365

Si vous n’avez pas encore d’abonnement Microsoft 365, vous pouvez acheter vos abonnements Windows 365 Business sur le site des produits [Windows 365.](https://www.microsoft.com/windows-365/business/compare-plans-pricing) Utilisez les étapes suivantes pour acheter un abonnement Windows 365 Business via la page Windows produits 365.

1. Dans la page [Windows 365 Entreprise,](https://www.microsoft.com/windows-365/business) sélectionnez Voir **les plans et les tarifs.**
2. Sur la page suivante, sélectionnez l’abonnement que vous souhaitez acheter, puis **sélectionnez Acheter maintenant.**
3. Dans la page **Merci d’avoir choisi Windows 365** Entreprise, suivez les étapes pour configurer votre compte.
4. À **l’étape 5 - Détails** de confirmation, si  vous êtes prêt à attribuer des licences aux utilisateurs, sélectionnez Commencer à aller à votre page d’accueil Windows 365 sur https://windows365.microsoft.com .
5. Sur la page Windows 365, dans la section **Actions** rapides, **sélectionnez Gérer votre organisation.** Cela vous permet d’Centre d’administration Microsoft 365 où vous pouvez attribuer des licences aux utilisateurs.

Les utilisateurs sans rôle d’administrateur général ou de facturation peuvent utiliser l’achat en libre-service pour acheter un abonnement pour Windows 365 Business directement à partir du site des produits [Windows 365 Business.](https://www.microsoft.com/windows-365/business?rtc=1) Un utilisateur qui achète un abonnement de cette façon se voie accorder une vue limitée de [l’Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339), où il peut attribuer des licences pour cet abonnement à d’autres utilisateurs de son organisation. L’attribution d’une licence à un autre utilisateur crée automatiquement un PC cloud Windows 365 Business, accessible à partir de la page d’accueil [Windows 365.](https://windows365.microsoft.com/)

> [!NOTE]
> L’achat en libre-service n’est pas disponible en Inde, ni pour les clients du secteur public ou de l’éducation.

Pour en savoir plus sur l’achat en libre-service, consultez le FAQ sur les [achats en libre-service.](../../commerce/subscriptions/self-service-purchase-faq.yml)

### <a name="buy-a-subscription-through-the-microsoft-admin-center"></a>Acheter un abonnement via le Centre d’administration Microsoft

Si vous avez déjà un client Microsoft 365 et que vous êtes administrateur global ou de facturation, vous pouvez utiliser le Centre d’administration Microsoft 365 pour acheter un abonnement Windows 365 Business pour votre organisation.

1. Dans le Centre d’administration Microsoft, go to the **Billing > Purchase services** page.
2. Dans la page **Acheter des services,** recherchez **Windows 365 Business**. Lorsque vous le trouvez, sélectionnez **Détails.**
3. Dans la page **Windows 365** Entreprise, dans la section **Processor/Ram/Stockage Options,** utilisez le **menu** Sélectionner un abonnement pour sélectionner un abonnement pour vos utilisateurs en fonction de leurs besoins en processeur, en RAM et en stockage. Consultez Windows options de resserrement [365 Business](windows-365-business-sizing.md) pour obtenir des instructions sur la sélection de l’abonnement qui répond le mieux aux besoins de vos utilisateurs.
4. Dans la page **d’achat,** entrez le nombre d’abonnements que vous souhaitez acheter, ainsi que vos informations de paiement. Ensuite, **sélectionnez Placer une commande.**
5. Vous **êtes prêt !** s’affiche pour confirmer votre achat.

## <a name="assign-licenses-to-users"></a>Attribuer des licences aux utilisateurs

Que vous avez acheté vos abonnements via le site des produits Windows 365 ou via le Centre d’administration Microsoft 365, vous pouvez attribuer des [licences](/microsoft-365/admin/manage/assign-licenses-to-users) aux utilisateurs via la **page** Facturation du Centre d’administration Microsoft 365.

Vous pouvez affecter différents types Windows licence 365 Business à un utilisateur, en fonction des besoins professionnels des utilisateurs. Consultez Windows options de resserrement [365 Business](windows-365-business-sizing.md) pour obtenir des conseils sur le type de licence qui peut convenir à vos utilisateurs.

> [!IMPORTANT]
> La première fois qu’une licence Windows 365 est attribuée à votre client, un compte système appelé utilisateur permanent **WINDOWS 365 BPRT** est automatiquement créé dans Azure Active Directory. Ne supprimez pas ce compte et n’a modifiez pas ce compte (par exemple, en modifiant le nom ou l’UPN). Si le compte système est supprimé, le programme d’installation peut échouer. Ce compte système garantit un processus de mise en place fluide et n’a pas de fonctionnalités d’écriture ni d’accès à votre client au-delà des fonctionnalités de service étendues de Windows 365 Business. Si vous supprimez cet utilisateur, déposez un ticket via le Support central.

## <a name="get-your-users-started-with-cloud-pc"></a>Démarrer vos utilisateurs avec Cloud PC

Une fois les licences attribuées, faites savoir à vos utilisateurs qu’il existe deux façons différentes d’accéder à leurs PC Cloud :

- Via la Windows page d’accueil 365 (https://windows365.microsoft.com)
- Utilisation d’un client Bureau à distance Microsoft client

### <a name="windows-365-home-page"></a>Windows page d’accueil 365

Les utilisateurs peuvent accéder **https://windows365.microsoft.com** à leurs PC cloud.  

Sur leur page d Windows 365, les utilisateurs voient les PC cloud accessibles dans la section Vos **PC cloud.**

![Windows famille 365.](../../media/deschutes/cloudpc-home.png)

Les utilisateurs **peuvent sélectionner Ouvrir dans le navigateur** pour ouvrir leur PC cloud.

> [!NOTE]  
> Les appareils mobiles ne sont actuellement pas pris en charge.

#### <a name="user-actions"></a>Actions de l’utilisateur

Sur la page d Windows 365, les utilisateurs peuvent effectuer des actions sur leurs PC Cloud en sélectionnant l’icône d’engrenage sur une carte PC cloud.

![Menu Carte.](../../media/deschutes/cloudpc-gear.png)

- **Redémarrer**: redémarre le PC cloud.

- **Réinitialiser**: réinitialiser :

    - Réinstalle Windows 10.
    - Supprime vos fichiers personnels.
    - Supprime toutes les modifications que vous avez apportées aux paramètres.
    - Supprime vos applications.

    > [!IMPORTANT]  
    > Avant de réinitialiser votre PC Cloud, veillez à stocker tous les fichiers importants que vous devez conserver dans un service de stockage cloud ou un stockage externe. La réinitialisation de votre PC Cloud supprimera ces fichiers.

- **Renommer**: modifie le nom du PC Cloud affiché à l’utilisateur sur la page d Windows 365.

- **Résolution des problèmes**: résolution des problèmes et tentative de résolution des problèmes qui empêchent peut-être un utilisateur de se connecter à son PC Cloud. Le tableau suivant décrit les états qui peuvent résulter des vérifications.

    | Statut | Description |
    |:-----|:-----|
    |Aucun problème détecté |Aucune des vérifications n’a détecté un problème avec le PC cloud. |
    |Problèmes résolus |Un problème a été détecté et résolu. |
    |Ne peut pas se connecter à Cloud PC. We’re working to fix it, try again later. |Un service Microsoft requis pour la connectivité n’est pas disponible. Essayez de vous connecter à nouveau ultérieurement. |
    |Nous n’avons pas pu résoudre les problèmes avec votre PC Cloud. Contactez votre administrateur. |Un problème a été détecté, mais il n’a pas pu être résolu. Cela peut être dû à une mise à jour Windows jour ou à un autre problème. Si cette erreur persiste pendant une période prolongée, il se peut que le PC cloud devra être réinitialisé. |

### <a name="remote-desktop"></a>Bureau à distance

L Bureau à distance Microsoft permet aux utilisateurs d’accéder et de contrôler un PC distant, y compris un PC cloud. Windows 365 utilisateurs peuvent télécharger et installer le client Bureau à distance dont ils ont besoin à partir de la page d Windows 365.

#### <a name="install-the-microsoft-remote-desktop-app"></a>Installer l’application Bureau à distance Microsoft de messagerie

Pour configurer leur client Bureau à distance, les utilisateurs suivent les étapes suivantes :

1. Sur la **page d Windows 365,** sélectionnez l’icône **Bureau à distance Microsoft applications** (sous l’icône d’accueil).
2. Sur la page **Bureau à distance Microsoft applications,** téléchargez et installez l’application Bureau à distance dont vous avez besoin.

   ![Clients Bureau à distance.](../../media/deschutes/remote-desktop-apps.png)

Pour obtenir la liste des clients par système d’exploitation, voir [Clients Bureau à distance.](/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients)

## <a name="installing-apps"></a>Installation des applications

Les utilisateurs peuvent installer des applications sur leur PC Cloud comme ils le feraient normalement dans Windows en les téléchargeant à partir du site web de l’application ou en les téléchargeant à partir du Microsoft Store.

Tous Windows 365 Entreprise ont des privilèges d’administrateur local sur leur PC Cloud, ils doivent donc avoir les autorisations requises pour installer des applications dans leurs espaces de travail.

> [!IMPORTANT]
> Si un utilisateur tente d’utiliser une licence Microsoft 365 Business Standard sur son PC Cloud, il peut voir l’erreur suivante : « Problème de compte : les produits que nous avons trouvés dans votre compte ne peuvent pas être utilisés pour activer les Office dans les scénarios d’ordinateurs partagés ». Dans ce scénario, l’utilisateur doit désinstaller la version de Office installée sur son PC Cloud et installer une nouvelle copie à partir de Office.com.

## <a name="management-through-intune"></a>Gestion via Intune

Windows 365 Business n’inscrit pas les PC cloud à [Intune](/mem/intune/fundamentals/what-is-intune) dans le cadre du processus d’approvisionnement. Si l’organisation et les utilisateurs sont correctement titulaires d’une licence, les PC cloud peuvent être inscrits à Intune à l’aide de la même procédure pour inscrire des ordinateurs Windows 10 à [Intune.](/mem/intune/user-help/enroll-windows-10-device)

## <a name="sending-outbound-email-messages-using-port-25-is-not-supported"></a>L’envoi de messages électroniques sortants à l’aide du port 25 n’est pas pris en charge

L’envoi de messages électroniques sortants directement sur le port 25 à partir d’Windows 365 Business Cloud PC n’est pas pris en charge. La communication sur le port TCP/25 est bloquée sur Windows réseau 365 Business pour des raisons de sécurité. Si votre service de messagerie utilise SMTP (Simple Mail Transfer Protocol) pour votre application cliente de messagerie, vous pouvez utiliser son interface web, si disponible. Vous pouvez également demander de l’aide à votre fournisseur de services de messagerie pour configurer son application cliente de messagerie afin d’utiliser le service SMTP sur TLS (Secure SMTP over Transport Layer Security), qui utilise un port différent.

## <a name="how-to-get-help"></a>Comment obtenir de l’aide

Si vous avez besoin d’aide lors de la configuration de Windows 365 Business dans le Centre d’administration Microsoft 365, consultez Obtenir de l’aide [ou du support.](/microsoft-365/business-video/get-help-support)

## <a name="related-content"></a>Contenu associé

[Windows 365 Business](https://www.microsoft.com/windows-365/business) <br/>
[Options de dimensionnement de Windows 365 Business](windows-365-business-sizing.md) <br/>
[Windows 365 Business plan comparison](https://www.microsoft.com/windows-365/business/compare-plans-pricing) <br/>
[Comparaison des applications clientes Bureau à distance](/windows-server/remote/remote-desktop-services/clients/remote-desktop-app-compare)<br/>
[Configurer Microsoft Teams dans votre petite entreprise](/microsoftteams/deploy-small-business)
