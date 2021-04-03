---
title: Configurer les options de publication standard ou ciblée
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
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
description: Découvrez comment configurer l’option de publication pour les nouvelles mises à jour de produits et de fonctionnalités dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: d3692f2e1cca58fec81f2ad492b9232d5576f99b
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579253"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Configurer les options de publication standard ou ciblée

> [!IMPORTANT]
> Les mises à jour Microsoft 365 décrites dans cet article s’appliquent à Microsoft 365, SharePoint Online et Exchange Online. Ces options de publication sont des méthodes ciblées et efficaces pour publier les modifications apportées à Microsoft 365, mais ne peuvent pas être garanties en permanence ou pour toutes les mises à jour. Elles ne s’appliquent pas aux applications Microsoft 365, Skype Entreprise, Microsoft Teams et aux services associés. Pour plus d’informations sur les options de publication de Microsoft 365 Apps, voir Vue d’ensemble des canaux de mise à jour [pour Les applications Microsoft 365.](/deployoffice/overview-update-channels)

Avec Microsoft 365, vous recevez de nouvelles mises à jour et fonctionnalités de produit dès qu’elles sont disponibles au lieu de faire des mises à jour coûteuses tous les quelques années. Vous n'avez donc plus besoin de procéder à des mises à jour onéreuses chaque année. De plus, vous pouvez gérer la manière dont votre organisation reçoit ces mises à jour. Par exemple, vous pouvez vous inscrire à une publication anticipée et faire profiter l'ensemble de votre organisation des mises à jour en avance, ou sélectionner un panel restreint d'utilisateurs qui les testeront. Vous pouvez également décider de rester sur le programme de publication standard et recevoir les mises à jour plus tard. Cet article décrit les différentes options de publication et la façon dont vous pouvez les utiliser pour votre organisation.

## <a name="how-it-works---release-validation"></a>Mode de fonctionnement - Validation de publication

Toute nouvelle version est d’abord testée et validée par l’équipe de fonctionnalités, puis par l’ensemble de l’équipe de fonctionnalités Microsoft 365, puis par l’ensemble de Microsoft. Un fois les tests et la validation internes accomplis, l'étape suivante consiste en une **publication ciblée** (anciennement nommée First Release) à destination des clients inscrits. À chaque cycle de publication, Microsoft recueille des commentaires, puis valide davantage la qualité en surveillant des métriques d'utilisation clés. Cette validation progressive est en place pour s'assurer que la publication à l'échelle mondiale est aussi robuste que possible. Les publications sont illustrées dans la figure suivante. 
  
![Libérer des anneaux de validation pour Microsoft 365](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Pour les mises à jour importantes, les clients sont initialement avertis par la feuille [de route Microsoft 365.](https://products.office.com/business/office-365-roadmap) À mesure qu’une mise à jour approche du déploiement, elle est communiquée par le biais de votre centre de messages [Microsoft 365.](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter)

> [!NOTE]
> Vous avez besoin d’un compte Microsoft 365 ou Azure AD pour accéder à votre centre de messages via le [Centre d’administration.](/office365/admin/admin-overview/about-the-admin-center) Les utilisateurs du plan d’accueil Microsoft 365 n’ont pas de centre d’administration.


## <a name="standard-release"></a>Publication standard

Il s’agit de l’option par défaut dans laquelle vous et vos utilisateurs recevez les dernières mises à jour lorsqu’elles sont publiées largement pour tous les clients.
  
Une bonne pratique consiste à laisser la majorité des utilisateurs  dans la version **Standard** et les professionnels de l’informatique et les utilisateurs avec pouvoir dans la version ciblée pour évaluer les nouvelles fonctionnalités et préparer les équipes à prendre en charge les utilisateurs professionnels et les cadres. 
  
> [!NOTE]
> Si, après avoir souscrit au programme de publication ciblée, vous décidez de revenir au programme de publication standard, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication standard. 
  
## <a name="targeted-release"></a>Version ciblée

Cette option vous permet, ainsi qu'à vos utilisateurs, d'être les premiers à profiter des dernières mises à jour, ainsi que de contribuer au développement du produit en envoyant des commentaires avant la mise à disposition générale. Vous pouvez choisir de diffuser les mises à jour de façon anticipée à des personnes spécifiques ou à l'ensemble de l'organisation.
  
> [!IMPORTANT]
> Les mises à jour d'envergure ou complexes peuvent demander plus de temps avant d'être diffusées, de sorte qu'aucun utilisateur ne soit affecté. Aucune garantie ne peut être apportée quant au calendrier exact des publications. 
  
### <a name="targeted-release-for-entire-organization"></a>Publication ciblée pour l'organisation entière

Si vous [définissez l’option de publication](#set-up-the-release-option-in-the-admin-center) dans le Centre d’administration pour cette option, tous vos utilisateurs obtiennent l’expérience de publication ciblée. Aux organisations comptant plus de 300 utilisateurs, nous recommandons d'utiliser un abonnement d'essai pour cette option. Pour plus d'informations sur les abonnements d'essai, veuillez vous adresser à votre contact Microsoft. 
  
### <a name="targeted-release-for-selected-users"></a>Publication ciblée pour des utilisateurs sélectionnés

Si vous [définissez l’option](#set-up-the-release-option-in-the-admin-center) de publication dans le Centre d’administration pour cette option, vous pouvez définir des utilisateurs spécifiques, généralement des utilisateurs avec pouvoir, pour bénéficier d’un accès en avant-première aux fonctionnalités et fonctionnalités. 
  
## <a name="benefits-of-targeted-release"></a>Avantages de la publication ciblée

La publication ciblée permet aux administrateurs, aux responsables des modifications ou à toute autre personne responsable des mises à jour Microsoft 365 de se préparer aux modifications à venir en leur permettant de :
  
- tester et valider les nouvelles mises à jour avant qu'elles soient publiées pour tous les utilisateurs au sein de l'organisation ;
    
- préparer la notification et la documentation à l'adresse des utilisateurs avant la publication des mises à jour à l'échelle mondiale ;
    
- préparer le support technique interne aux changements à venir ;
    
- effectuer les contrôles de sécurité et de conformité ;
    
- utiliser des contrôles de fonctionnalité, le cas échéant, pour contrôler la publication des mises à jour aux utilisateurs finaux.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Configurer l’option de publication dans le Centre d’administration

Vous pouvez modifier la façon dont votre organisation reçoit les mises à jour Microsoft 365 en suivant ces étapes. Vous devez être un administrateur global dans Microsoft 365 pour vous y rendre.
  
> [!IMPORTANT]
> L’application des modifications ci-dessous dans Microsoft 365 peut prendre jusqu’à 24 heures. Si vous décidez de ne plus participer au programme de publication ciblée après l'avoir activé, vos utilisateurs risquent de perdre l'accès aux fonctionnalités qui n'ont pas encore atteint le niveau de publication planifiée. 
  
1. Dans le Centre d’administration, sélectionnez **Paramètres** de l’organisation, puis sous l’onglet Profil de l’organisation, choisissez Préférences  >   **de publication.** 

5. Pour désactiver la publication ciblée, sélectionnez **Publication standard,** puis **sélectionnez Enregistrer les modifications.** 
    
6. Pour activer la publication ciblée pour tous les utilisateurs de votre organisation, sélectionnez Publication ciblée **pour** tout le monde, puis **sélectionnez Enregistrer les modifications.** 
    
7. Pour activer la publication ciblée pour certaines personnes de votre organisation, sélectionnez **Publication** ciblée pour les utilisateurs sélectionnés, puis **sélectionnez Enregistrer les modifications.** 
    
8. Sélectionnez **Sélectionner des utilisateurs** pour ajouter des utilisateurs un par un ou Télécharger des utilisateurs **pour** les ajouter en bloc.
    
9. Lorsque vous avez terminé d’ajouter des utilisateurs, **sélectionnez Enregistrer les modifications.**


  
## <a name="learn-more"></a>En savoir plus

Découvrez comment gérer [les messages](/office365/admin/manage/message-center) dans votre centre de messages [Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) pour recevoir des notifications sur les mises à jour et les mises à jour Microsoft 365 à venir.

## <a name="related-articles"></a>Articles connexes

[Office Insider](https://insider.office.com/join/windows)
