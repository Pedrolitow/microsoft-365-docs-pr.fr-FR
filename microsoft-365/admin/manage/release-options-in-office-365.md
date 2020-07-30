---
title: Configurer les options de publication standard ou ciblée
f1.keywords:
- CSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 3b3adfa4-1777-4ff0-b606-fb8732101f47
description: Découvrez comment configurer l’option de publication pour les mises à jour de nouveaux produits et fonctionnalités dans le centre d’administration 365 de Microsoft.
ms.openlocfilehash: 3baec050f33893357b25c832552643cf3a6d10d0
ms.sourcegitcommit: 1b83b6bcacb997324bc4be355deba6daf319591d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502878"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Configurer les options de publication standard ou ciblée

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Avec Microsoft 365, vous recevez de nouvelles mises à jour de produits et de nouvelles fonctionnalités dès qu’elles sont disponibles au lieu d’effectuer des mises à jour coûteuses tous les ans. Vous n'avez donc plus besoin de procéder à des mises à jour onéreuses chaque année. De plus, vous pouvez gérer la manière dont votre organisation reçoit ces mises à jour. Par exemple, vous pouvez vous inscrire à une publication anticipée et faire profiter l'ensemble de votre organisation des mises à jour en avance, ou sélectionner un panel restreint d'utilisateurs qui les testeront. Vous pouvez également décider de rester sur le programme de publication standard et recevoir les mises à jour plus tard. Cet article décrit les différentes options de publication et comment vous pouvez les utiliser pour votre organisation.
  
> [!IMPORTANT]
> Les mises à jour de Microsoft 365 décrites dans cet article s’appliquent à Microsoft 365, SharePoint Online et Exchange Online. Ces options de publication sont des canaux ciblés et privilégiés pour la publication de modifications apportées à Office 365. Ces options de publication sont ciblées, meilleures moyens de publier les modifications apportées à Microsoft 365, mais elles ne sont pas garanties à tout moment ou pour toutes les mises à jour. 

> [!NOTE]
> Pour plus d’informations sur les canaux de mise à jour pour les applications, voir [vue d’ensemble des canaux de mise à jour pour les applications Microsoft 365](https://docs.microsoft.com/deployoffice/overview-update-channels). 
  
## <a name="how-it-works---release-validation"></a>Mode de fonctionnement - Validation de publication

Toute nouvelle version est d’abord testée et validée par l’équipe de fonctionnalité, puis par l’équipe de fonctionnalité Microsoft 365 entière, suivie par Microsoft. Un fois les tests et la validation internes accomplis, l'étape suivante consiste en une **publication ciblée** (anciennement nommée First Release) à destination des clients inscrits. À chaque cycle de publication, Microsoft recueille des commentaires, puis valide davantage la qualité en surveillant des métriques d'utilisation clés. Cette validation progressive est en place pour s'assurer que la publication à l'échelle mondiale est aussi robuste que possible. Les publications sont illustrées dans la figure suivante. 
  
![Sonneries de validation de publication pour Microsoft 365](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Pour les mises à jour importantes, les clients sont initialement avertis par la feuille de [route Microsoft 365](https://products.office.com/business/office-365-roadmap). Une fois que la mise à jour s’avère plus proche du déploiement, elle est communiquée via votre [Centre de messages Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Vous avez besoin d’un compte Microsoft 365 ou Azure AD pour accéder à votre centre de messages via le [Centre d’administration](https://docs.microsoft.com/office365/admin/admin-overview/about-the-admin-center). Plan d’accueil Microsoft 365 les utilisateurs ne disposent pas d’un centre d’administration.


## <a name="standard-release"></a>Publication standard

Il s’agit de l’option par défaut où vous et vos utilisateurs recevez les dernières mises à jour lorsqu’elles sont publiées à grande échelle pour tous les clients.
  
Une bonne pratique consiste à laisser à la majorité des utilisateurs de la **version standard** , aux professionnels de l’informatique et aux utilisateurs chevronnés de la **version ciblée** pour évaluer de nouvelles fonctionnalités et préparer teams pour prendre en charge les utilisateurs et les cadres professionnels. 
  
> [!NOTE]
> Si, après avoir souscrit au programme de publication ciblée, vous décidez de revenir au programme de publication standard, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication standard. 
  
## <a name="targeted-release"></a>Version ciblée

Cette option vous permet, ainsi qu'à vos utilisateurs, d'être les premiers à profiter des dernières mises à jour, ainsi que de contribuer au développement du produit en envoyant des commentaires avant la mise à disposition générale. Vous pouvez choisir de diffuser les mises à jour de façon anticipée à des personnes spécifiques ou à l'ensemble de l'organisation.
  
> [!IMPORTANT]
> Les mises à jour d'envergure ou complexes peuvent demander plus de temps avant d'être diffusées, de sorte qu'aucun utilisateur ne soit affecté. Aucune garantie ne peut être apportée quant au calendrier exact des publications. 
  
### <a name="targeted-release-for-entire-organization"></a>Publication ciblée pour l'organisation entière

Si vous [configurez l’option de publication dans le centre d’administration](#set-up-the-release-option-in-the-admin-center) pour cette option, tous vos utilisateurs bénéficieront de l’expérience de publication ciblée. Aux organisations comptant plus de 300 utilisateurs, nous recommandons d'utiliser un abonnement d'essai pour cette option. Pour plus d'informations sur les abonnements d'essai, veuillez vous adresser à votre contact Microsoft. 
  
### <a name="targeted-release-for-selected-users"></a>Publication ciblée pour des utilisateurs sélectionnés

Si vous [configurez l’option de publication dans le centre d’administration](#set-up-the-release-option-in-the-admin-center) pour cette option, vous pouvez définir des utilisateurs spécifiques, généralement des utilisateurs avec pouvoir, pour bénéficier d’un accès anticipé aux fonctionnalités. 
  
## <a name="benefits-of-targeted-release"></a>Avantages de la publication ciblée

La publication ciblée permet aux administrateurs, responsables des modifications ou autres personnes responsables des mises à jour de Microsoft 365 de se préparer aux modifications à venir en les autorisant :
  
- tester et valider les nouvelles mises à jour avant qu'elles soient publiées pour tous les utilisateurs au sein de l'organisation ;
    
- préparer la notification et la documentation à l'adresse des utilisateurs avant la publication des mises à jour à l'échelle mondiale ;
    
- préparer le support technique interne aux changements à venir ;
    
- effectuer les contrôles de sécurité et de conformité ;
    
- utiliser des contrôles de fonctionnalité, le cas échéant, pour contrôler la publication des mises à jour aux utilisateurs finaux.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Configurer l’option de publication dans le centre d’administration

Vous pouvez modifier la façon dont votre organisation reçoit les mises à jour de Microsoft 365 en procédant comme suit. Vous devez être un administrateur général dans Microsoft 365 pour y participer.
  
> [!IMPORTANT]
> Le suivi des modifications suivantes peut prendre jusqu’à 24 heures pour être pris en compte dans Microsoft 365. Si vous décidez de ne plus participer au programme de publication ciblée après l'avoir activé, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication planifiée. 
  
1. Dans le centre d’administration, accédez au **Settings**  >  **paramètre org**paramètres, puis sous l’onglet Profil de l' **organisation** , choisissez **publier les préférences**.

5. Pour désactiver la version ciblée, sélectionnez **version standard**, puis **enregistrer les modifications**. 
    
6. Pour activer la publication ciblée pour tous les utilisateurs de votre organisation, sélectionnez **publication ciblée pour tout le monde**, puis **enregistrer les modifications**. 
    
7. Pour activer la publication ciblée pour certaines personnes de votre organisation, sélectionnez **publication ciblée pour les utilisateurs sélectionnés**, puis cliquez sur **enregistrer les modifications**. 
    
8. Choisissez **Sélectionner les utilisateurs** pour ajouter un utilisateur à la fois ou **Télécharger des utilisateurs** pour les ajouter en bloc.
    
9. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **enregistrer les modifications**.


  
## <a name="learn-more"></a>En savoir plus

Découvrez comment [gérer les messages](https://docs.microsoft.com/office365/admin/manage/message-center) dans votre [Centre de messages Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) pour obtenir des notifications sur les mises à jour et les versions futures de Microsoft 365.
