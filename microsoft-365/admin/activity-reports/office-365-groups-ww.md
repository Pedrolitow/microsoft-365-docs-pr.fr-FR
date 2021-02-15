---
title: Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Obtenez un rapport de groupes Microsoft 365 pour connaître les groupes et leurs activités.
ms.openlocfilehash: 4a89f09f89e399905d0cb6927eca76c1242dfc62
ms.sourcegitcommit: 039205fdaaa2a233ff7e95cd91bace474b84b68c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "49611949"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport des groupes Microsoft 365, vous pouvez obtenir des informations sur l’activité des groupes dans votre organisation et voir combien de groupes sont créés et utilisés.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
  
## <a name="how-to-get-to-the-groups-report"></a>Comment obtenir le rapport des groupes

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. À partir de la page  d’accueil du tableau de bord, cliquez sur le bouton Afficher plus sur les utilisateurs actifs - Applications Microsoft 365 ou utilisateurs actifs - Carte Services Microsoft 365 pour obtenir la page de rapport Office 365.
  
## <a name="interpret-the-groups-report"></a>Interpréter le rapport des groupes

Vous pouvez afficher les activations dans le rapport Office 365 en choisissant l’onglet **Activité groupes.**<br/>![Rapports Microsoft 365 : Microsoft Office 365 groupes.](../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’activité des groupes Office 365 : choisir les colonnes](../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 

|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|Nom du groupe  <br/> |Nom du groupe.  <br/> |
|Deleted  <br/> |Nombre de groupes supprimés. Si le groupe est supprimé, mais qu'il a connu une activité dans la période du rapport, il apparaît dans la grille avec cet indicateur défini sur true.  <br/> |
|Propriétaire du groupe  <br/> |Nom du propriétaire du groupe.  <br/> |
|Date de la dernière activité (UTC)  <br/> |Date à laquelle un message a été reçu au plus tard par le groupe. Il s'agit de la date la plus récente à laquelle une activité a eu lieu dans une conversation par courrier, dans Yammer ou sur le site.  <br/> |
|Type  <br/> |Type de groupe. Il peut être privé ou public.  <br/> |
|Courriers électroniques reçus dans Exchange  <br/> |Nombre de messages reçus par le groupe.|
|Courriers électroniques dans Exchange (total)  <br/> |Nombre total d’éléments dans la boîte aux lettres du groupe.  <br/> |
|Stockage de boîtes aux lettres utilisé pour Exchange (Mo)  <br/> |Stockage utilisé par la boîte aux lettres du groupe. <br/>|
|Fichiers SharePoint (total)  <br/> |Nombre de fichiers stockés dans les sites de groupe SharePoint.  <br/> |
|Fichiers SharePoint (actifs)  <br/> |Nombre de fichiers sur le site de groupe SharePoint qui ont été modifiés (vues ou modifiées, synchronisés, partagés en interne ou en externe) pendant la période de rapport.  <br/> |
|Espace de stockage de site total utilisé pour SharePoint (Mo)  <br/> |Quantité de stockage en Mo utilisée pendant la période de rapport.  <br/> |
|Messages en Yammer (publié)  <br/> |Nombre de messages publiés dans le groupe Yammer au cours de la période de rapport.  <br/> |
|Messages dans Yammer (lecture)  <br/> |Nombre de conversations lues dans le groupe Yammer au cours de la période de rapport.  <br/> |
|Messages en Yammer (aimé)  <br/> |Nombre de messages aimés dans le groupe Yammer au cours de la période de rapport.  <br/> |
|Members  <br/> |Nombre de membres du groupe.  <br/> |
|Membres externes |Nombre d’utilisateurs externes dans le groupe.|
|||