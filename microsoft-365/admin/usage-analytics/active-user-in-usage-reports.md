---
title: Utilisateur actif dans les rapports d’utilisation de Microsoft 365
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 093a6d0d-890b-489e-9f46-b15687d3fe4f
description: Découvrez un utilisateur actif de l’analytique de l’utilisation de Microsoft 365, des rapports d’activité et des métriques d’adoption.
ms.openlocfilehash: bddd946c9062d7fa98c5c88091ef8d92f4372e4e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193452"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Utilisateur actif dans les rapports d’utilisation de Microsoft 365

## <a name="active-user-in-usage-reports"></a>Utilisateur actif dans les rapports d’utilisation

Un utilisateur actif des produits Microsoft 365 pour [l’analytique de l’utilisation de Microsoft 365](usage-analytics.md) et les [rapports d’activité dans le centre d’administration](../activity-reports/activity-reports.md) est défini comme suit. 
  
|**Produit**|**Définition d'un utilisateur actif**|**Notes**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Tout utilisateur qui a effectué l’une des actions suivantes : marquer comme lus, envoyer des messages, créer des rendez-vous, envoyer des demandes de réunion, accepter (provisoirement) ou refuser des demandes de réunion, annuler des réunions.  <br/> |Aucune information de calendrier n'est représentée. Ces informations seront ajoutées lors d'une prochaine mise à jour.  <br/> |
|SharePoint Online  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients sur un site, ou ayant affiché une page sur un site.  <br/> |Les métriques utilisateur actives pour SharePoint Online dans l’application modèle Microsoft 365 Usage Analytics reflètent uniquement les utilisateurs qui ont effectué une activité de fichier sur un site SharePoint Team ou un site de groupe. L’application modèle sera mise à jour pour synchroniser la définition avec la même valeur que celle des rapports d’utilisation dans le Centre d’administration.  <br/> |
|OneDrive Entreprise  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients.  <br/> ||
|Yammer  <br/> |Tout utilisateur ayant lu, publié ou aimé un message sur Yammer.  <br/> ||
|Skype Entreprise  <br/> |Tout utilisateur ayant participé à une session P2P (messages instantanés, appels audio et vidéo, partage d'application, transferts de fichiers, etc.) ou ayant organisé ou participé à une conférence.  <br/> ||
|Office  <br/> |Tout utilisateur qui a activé son abonnement Microsoft 365 Pro Plus, Visio Pro ou Project Pro sur au moins un appareil.  <br/> ||
|Groupes Microsoft 365  <br/> |Tout membre d'un groupe présentant une activité de boîte aux lettres (si un message a été envoyé au groupe)  <br/> |Cette définition sera améliorée avec l’activité de fichier de site de groupe et l’activité de groupe Yammer (activité de fichier sur le site de groupe et message publié dans le groupe Yammer associé au groupe.) Ces données ne sont actuellement pas disponibles dans l’application modèle Microsoft 365 Usage Analytics  <br/> |
|Microsoft Teams  <br/> |Tout utilisateur qui a participé à des messages de conversation, des messages de conversation privés, des appels, des réunions ou d’autres activités. D’autres activités sont définies comme le nombre d’autres activités d’équipe par l’utilisateur, dont certaines incluent, et non limitées, : aimer les messages, les applications, travailler sur des fichiers, effectuer des recherches, suivre les équipes et canaliser et les favoritiser.  <br/> ||
   
## <a name="adoption-metrics"></a>Métriques d’adoption

[L’analytique de l’utilisation de Microsoft 365](usage-analytics.md) contient d’autres métriques d’adoption liées aux utilisateurs actifs pour montrer l’adoption des produits au fil du temps. Ces métriques sont valides pour le mois, l’année et le produit sélectionnés et sont définies comme suit. 
  
|**Métrique**|**Description**|
|:-----|:-----|
|EnabledUsers  <br/> |Nombre d’utilisateurs activés pour utiliser le produit dans le mois.  <br/> |
|ActiveUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois.  <br/> |
|MoMReturningUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois qui étaient également actifs le mois précédent.  <br/> |
|FirstTimeUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois qui n’avaient jamais utilisé le service auparavant.  <br/> |
|CumulativeActiveUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois et mois précédent.  <br/> |
|ActiveUsers(%)  <br/> |Pourcentage d’utilisateurs, arrondi au dixième le plus proche, actif au cours du mois par rapport au nombre d’utilisateurs activés au cours de ce mois.  <br/> |
|MoMReturningUsers(%)  <br/> |Pourcentage d’utilisateurs, arrondis au dixième le plus proche, actifs au cours du mois qui étaient également actifs le mois précédent par rapport au nombre d’utilisateurs actifs.  <br/> |
   
MoMReturningUsers, FirstTimeUsers, &amp; CumulativeActiveUsers ont été réinitialisés à partir du 1er janvier 2018 avec l’inclusion de Microsoft Teams.
  
