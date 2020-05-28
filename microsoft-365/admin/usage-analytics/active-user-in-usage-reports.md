---
title: Utilisateur actif dans les rapports d’utilisation de Microsoft 365
ms.author: sirkkuw
author: Sirkkuw
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
description: Découvrez un utilisateur actif de l’analyse de l’utilisation, des rapports d’activité et des mesures d’adoption de Microsoft 365.
ms.openlocfilehash: b4834d96b2f762d77f0d27309cf8c71a782b0dcd
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44402881"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Utilisateur actif dans les rapports d’utilisation de Microsoft 365

## <a name="active-user-in-usage-reports"></a>Utilisateur actif dans les rapports d’utilisation

Un utilisateur actif de produits Microsoft 365 pour l' [analyse de l’utilisation de microsoft 365](usage-analytics.md) et les [rapports d’activité dans le centre d’administration](../activity-reports/activity-reports.md) sont définis comme suit. 
  
|**Produit**|**Définition d'un utilisateur actif**|**Notes**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Tout utilisateur ayant lu ou envoyé un e-mail.  <br/> |Aucune information de calendrier n'est représentée. Ces informations seront ajoutées lors d'une prochaine mise à jour.  <br/> |
|SharePoint Online  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients sur un site, ou ayant affiché une page sur un site.  <br/> |La mesure utilisateur active pour SharePoint Online dans l’application de modèle d’analyse de l’utilisation de Microsoft 365 ne reflète que les utilisateurs qui ont fait des activités de fichier sur un site d’équipe SharePoint ou un site de groupe. L’application de modèle est mise à jour pour synchroniser la définition avec les mêmes que celles des rapports d’utilisation dans le centre d’administration.  <br/> |
|OneDrive Entreprise  <br/> |Tout utilisateur ayant interagi avec un fichier en le créant, en le modifiant, en l'affichant, en le supprimant, en le partageant en interne ou en externe, ou en le synchronisant avec des clients.  <br/> ||
|Yammer  <br/> |Tout utilisateur ayant lu, publié ou aimé un message sur Yammer.  <br/> ||
|Skype Entreprise  <br/> |Tout utilisateur ayant participé à une session P2P (messages instantanés, appels audio et vidéo, partage d'application, transferts de fichiers, etc.) ou ayant organisé ou participé à une conférence.  <br/> ||
|Office  <br/> |Tout utilisateur ayant activé son abonnement Microsoft 365 Pro plus, Visio Pro ou Project Pro sur au moins un appareil.  <br/> ||
|Groupes Microsoft 365  <br/> |Tout membre d'un groupe présentant une activité de boîte aux lettres (si un message a été envoyé au groupe)  <br/> |Cette définition sera améliorée avec l’activité de fichier de site de groupe et l’activité de groupe Yammer (activité de fichier sur le site de groupe et message publié dans le groupe Yammer associé au groupe.) Ces données ne sont actuellement pas disponibles dans l’application de modèle d’analyse de l’utilisation de Microsoft 365  <br/> |
|Microsoft Teams  <br/> |Tout utilisateur qui a participé à des messages de conversation, des messages de conversation privés, des appels, des réunions ou d’autres activités. Les autres activités se définissent comme le nombre d’autres activités d’équipe de l’utilisateur qui incluent, et non, les messages, les applications, le travail sur les fichiers, la recherche, les équipes et les canaux et les Favoriting.  <br/> ||
   
## <a name="adoption-metrics"></a>Mesures d’adoption

[L’analyse de l’utilisation de Microsoft 365](usage-analytics.md) contient des mesures d’adoption supplémentaires relatives aux utilisateurs actifs pour montrer l’adoption des produits au fil du temps. Ces mesures sont valides pour le mois, l’année et le produit sélectionnés et sont définies comme suit. 
  
|**Métrique**|**Description**|
|:-----|:-----|
|EnabledUsers  <br/> |Nombre d’utilisateurs activés pour utiliser le produit dans le mois.  <br/> |
|ActiveUsers  <br/> |Nombre d’utilisateurs actifs dans le mois.  <br/> |
|MoMReturningUsers  <br/> |Nombre d’utilisateurs actifs dans le mois qui ont également été actifs au cours du mois précédent.  <br/> |
|FirstTimeUsers  <br/> |Nombre d’utilisateurs actifs dans le mois qui n’ont jamais utilisé le service auparavant.  <br/> |
|CumulativeActiveUsers  <br/> |Nombre d’utilisateurs actifs dans le mois plus tout mois précédent.  <br/> |
|ActiveUsers (%)  <br/> |Pourcentage d’utilisateurs, arrondi au dixième le plus proche, actif dans le mois par rapport au nombre d’utilisateurs activés dans ce mois.  <br/> |
|MoMReturningUsers (%)  <br/> |Pourcentage d’utilisateurs, arrondi au dixième le plus proche, actif dans le mois qui étaient également actifs au cours du mois précédent par rapport au nombre d’utilisateurs actifs.  <br/> |
   
MoMReturningUsers, FirstTimeUsers, &amp; CumulativeActiveUsers ont été réinitialisés à partir du 1er janvier 2018 avec l’inclusion de Microsoft Teams.
  
