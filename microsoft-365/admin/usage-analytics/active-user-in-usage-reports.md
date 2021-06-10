---
title: Utilisateur actif dans les rapports Microsoft 365'utilisation
ms.author: efrene
author: efrene
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
ms.assetid: 093a6d0d-890b-489e-9f46-b15687d3fe4f
description: Découvrez un utilisateur actif de l’analyse Microsoft 365'utilisation, des rapports d’activité et des mesures d’adoption.
ms.openlocfilehash: 21663722d1a3850389db2ad79321daf363d314c6
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579073"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Utilisateur actif dans les rapports Microsoft 365'utilisation

## <a name="active-user-in-usage-reports"></a>Utilisateur actif dans les rapports d’utilisation

Un utilisateur actif de produits [](usage-analytics.md) Microsoft 365 pour l’analyse Microsoft 365'utilisation et les rapports d’activité dans le Centre [d’administration](../activity-reports/activity-reports.md) est défini comme suit. 
  
|**Produit**|**Définition d'un utilisateur actif**|**Notes**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Tout utilisateur ayant effectué l’une des actions suivantes : marquer comme lu, envoyer des messages, créer des rendez-vous, envoyer des demandes de réunion, accepter (provisoirement) ou refuser des demandes de réunion, annuler des réunions.  <br/> |Aucune information de calendrier n'est représentée. Ces informations seront ajoutées lors d'une prochaine mise à jour.  <br/> |
|SharePoint Online  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients sur un site, ou ayant affiché une page sur un site.  <br/> |La mesure utilisateur active pour SharePoint Online dans l’application modèle d’analyse de l’utilisation Microsoft 365 reflète uniquement les utilisateurs qui ont fait une activité de fichier sur un site d’équipe SharePoint ou un site de groupe. L’application de modèle sera mise à jour pour synchroniser la définition avec celle des rapports d’utilisation dans le Centre d’administration.  <br/> |
|OneDrive Entreprise  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients.  <br/> ||
|Yammer  <br/> |Tout utilisateur ayant lu, publié ou aimé un message sur Yammer.  <br/> ||
|Skype Entreprise  <br/> |Tout utilisateur ayant participé à une session P2P (messages instantanés, appels audio et vidéo, partage d'application, transferts de fichiers, etc.) ou ayant organisé ou participé à une conférence.  <br/> ||
|Office  <br/> |Tout utilisateur ayant activé son abonnement Microsoft 365 Pro Plus, Visio Pro ou Project Pro au moins un appareil.  <br/> ||
|Groupes Microsoft 365  <br/> |Tout membre d'un groupe présentant une activité de boîte aux lettres (si un message a été envoyé au groupe)  <br/> |Cette définition sera améliorée avec l’activité de fichier de site de groupe et l’activité de groupe Yammer (activité de fichier sur le site de groupe et message publié dans Yammer groupe associé au groupe.) Ces données ne sont actuellement pas disponibles dans l’application Microsoft 365 modèle Analyse de l’utilisation  <br/> |
|Microsoft Teams  <br/> |Tout utilisateur ayant participé à des messages de conversation, des messages de conversation privée, des appels, des réunions ou toute autre activité. D’autres activités sont définies comme le nombre d’autres activités d’équipe par l’utilisateur, dont certaines incluent, sans s’y limiter, : aimer des messages, des applications, travailler sur des fichiers, rechercher, suivre les équipes et le canal et les favoritiser.  <br/> ||
   
## <a name="adoption-metrics"></a>Mesures d’adoption

[Microsoft 365'analyse de l’utilisation contient](usage-analytics.md) des mesures d’adoption supplémentaires relatives aux utilisateurs actifs pour montrer l’adoption des produits au fil du temps. Ces mesures sont valides pour le mois, l’année et le produit sélectionnés et sont définies comme suit. 
  
|**Métrique**|**Description**|
|:-----|:-----|
|EnabledUsers  <br/> |Nombre d’utilisateurs activés pour utiliser le produit au cours du mois.  <br/> |
|ActiveUsers  <br/> |Nombre d’utilisateurs actifs dans le mois.  <br/> |
|MoMReturningUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois qui ont également été actifs au cours du mois précédent.  <br/> |
|FirstTimeUsers  <br/> |Nombre d’utilisateurs actifs au cours du mois qui n’avaient jamais utilisé le service auparavant.  <br/> |
|CumulativeActiveUsers  <br/> |Nombre d’utilisateurs actifs dans le mois plus un mois précédent.  <br/> |
|ActiveUsers(%)  <br/> |Pourcentage d’utilisateurs, arrondi au dixième le plus proche, actifs dans le mois par rapport au nombre d’utilisateurs activés dans ce mois.  <br/> |
|MoMReturningUsers(%)  <br/> |Pourcentage d’utilisateurs, arrondis au dixième le plus proche, actifs dans le mois qui étaient également actifs le mois précédent par rapport au nombre d’utilisateurs actifs.  <br/> |
   
MoMReturningUsers, FirstTimeUsers, CumulativeActiveUsers ont été réinitialisés à partir du &amp; 1er janvier 2018 avec l’inclusion de Microsoft Teams.
  
