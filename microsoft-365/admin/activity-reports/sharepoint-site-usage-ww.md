---
title: Rapports Microsoft 365 dans le Centre d’administration - Utilisation du site SharePoint
f1.keywords:
- NOCSH
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
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Obtenez le rapport d’utilisation du site SharePoint pour connaître le nombre de fichiers stockés par les utilisateurs dans les sites SharePoint, le nombre d’utilisations actives et le stockage total utilisé.
ms.openlocfilehash: bc9345a5e281f1e7343bf62a2dc6832587d0786e
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48649826"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation du site SharePoint

En tant qu’administrateur Microsoft  365, le tableau de bord Rapports vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d'ensemble de la valeur que vous apporte SharePoint, en termes de nombre total de fichiers que les utilisateurs stockent sur les sites SharePoint, de nombre de fichiers activement utilisés, et de stockage utilisé sur ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site pour tous les sites. 
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.
Les rapports Microsoft 365 dans le Centre d’administration ne sont pas pris en charge pour les clients GCC High et DoD.
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur **le** bouton Afficher plus sur la carte SharePoint.
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Interpréter le rapport d’utilisation du site SharePoint

Vous pouvez afficher l’utilisation du site dans le rapport SharePoint en choisissant l’onglet **Utilisation du** site.<br/>![Rapports Microsoft 365 - Rapport d’utilisation du site Microsoft SharePoint.](../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png)

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes dans le rapport.  <br/> ![Rapport d’utilisation du site SharePoint : choisir des colonnes](../../media/639f3cfd-6725-4318-a225-6d5c2f01770c.png)

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant **le** lien Exporter. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 
  
|Item|Description|
|:-----|:-----|
|**Métrique**|**Définition**|
|URL du site  <br/> |URL complète du site. <br/> |
|Deleted  <br/> |État de suppression du site. La suppression effective des sites prend au minimum 7 jours.  <br/> |
|Propriétaire du site  <br/> |Nom d’utilisateur du propriétaire principal du site.   <br/> |
|Nom principal du propriétaire du site  <br/> |Adresse de messagerie du propriétaire du site. <br/> |
|Date de la dernière activité (UTC)  <br/> | Date de la dernière détection de l’activité de fichier ou de l’affichage d’une page sur le site.  <br/> |
|Fichiers  <br/> |Nombre de fichiers sur le site. <br/>|
|Fichiers actifs  <br/> | Nombre de fichiers actifs sur le site.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.  <br/> |
|Stockage utilisé (Mo)  <br/> |Quantité de stockage actuellement utilisée sur le site.  <br/>|
|Stockage alloué (Mo)  <br/> |Quantité maximale de stockage allouée au site.  <br/>|
|Vues de page  <br/> |Nombre de fois où des pages ont été vues sur le site.  <br/>|
|Pages visitées  <br/> |Nombre de pages uniques visitées sur le site.  <br/>|
|Modèle web racine  <br/> |Modèle utilisé pour créer le site.  <br/> REMARQUE : si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne Modèle Web racine. |
|||