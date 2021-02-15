---
title: Rapports Microsoft 365 dans le Centre d’administration - Utilisation du site SharePoint
ms.author: pebaum
author: pebaum
manager: pamgreen
audience: Admin
ms.topic: overview
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
- SPO160
- BSA160
ms.assetid: 4ecfb843-e5d5-464d-8bf6-7ed512a9b213
description: 'Obtenez le rapport d’utilisation du site SharePoint pour connaître le nombre de fichiers stockés par les utilisateurs dans les sites SharePoint, le nombre d’utilisations actives et le stockage total utilisé. '
ms.openlocfilehash: 7da72dccb4a90ed204ffa785040b1968ac70feb3
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688204"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation du site SharePoint

En tant qu’administrateur Microsoft  365, le tableau de bord Rapports vous présente la vue d’ensemble de l’activité sur différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d'ensemble de la valeur que vous apporte SharePoint, en termes de nombre total de fichiers que les utilisateurs stockent sur les sites SharePoint, de nombre de fichiers activement utilisés, et de stockage utilisé sur ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site pour tous les sites. 
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.
Les rapports Microsoft 365 dans le Centre d’administration ne sont pas pris en charge pour les clients GCC High et DoD.
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le Centre d’administration, allez sur **Utilisation des** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">rapports.</a>
    
2. Sous fichiers **SharePoint, cliquez** **sur Afficher plus.** 

3. En de **côté de l’activité SharePoint,** cliquez sur la flèche vers le bas pour ouvrir le menu.

4. Sélectionnez **l’utilisation du site SharePoint.** \> 
  
## <a name="interpreting-the-sharepoint-site-usage-report"></a>Interprétation du rapport Utilisation du site SharePoint

![SharePoint Site Usage Report](../../media/4f88fb7d-9aa8-470e-9e23-e31caaf77d78.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation du site SharePoint** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux 24 à 48 dernières heures. <br/> |
|3.  <br/> |Le graphique **Sites** indique le nombre total de sites actifs et le nombre de sites actifs, y compris les sites dans lesquels les utilisateurs ont vu, modifié, téléchargé, téléchargé, partagé ou synchronisé un fichier ou ont visionisé une page au cours de la période de rapport.  <br/> |
|4.  <br/> |Le graphique **Fichiers** affiche le nombre total de fichiers sur l'ensemble des sites et le nombre de fichiers actifs. Le nombre total de fichiers inclut les fichiers des utilisateurs et les fichiers système. Un fichier est considéré comme étant actif s'il a été enregistré, synchronisé, modifié ou partagé au cours de la période spécifique.  |
|5.  <br/> |Le graphique **Stockage** présente la tendance de stockage alloué et utilisé pendant la période de rapport.  <br/> |
|6.  <br/> |Le graphique **Pages** présente le nombre de pages affichées sur tous les sites.  <br/> |
|7.  <br/> |Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Fichiers,** sélectionnez **Fichiers** **ou Fichiers actifs.** Dans le graphique **Sites,** vous pouvez sélectionner **Le nombre total de sites** ou les sites **actifs.** Dans le **graphique stockage,** vous pouvez sélectionner **Stockage alloué** ou **stockage consommé.** La modification de cette sélection ne modifie pas les informations du tableau grille.  <br/> |
|8.  <br/> | Le tableau montre une répartition des activités au niveau du site.  <br/> ![Options de colonne pour le rapport d’utilisation](../../media/sharepointsite-usage.png)           <br/> **URL du site** indique l'URL complète du site.  <br/> **Supprimé** est l'état de suppression du site. La suppression effective des sites prend au minimum 7 jours.  <br/> **Propriétaire du site** indique le nom d'utilisateur du propriétaire principal du site.  <br/>**Le nom principal du propriétaire du site** est l’adresse e-mail du propriétaire du site.  <br/> **Date de la dernière activité (UTC)** indique la date à laquelle une activité de fichier a été détectée ou une page affichée pour la dernière fois sur le site.  <br/> **Fichiers** indique le nombre de fichiers sur le site.  <br/> **Les fichiers actifs** sont le nombre de fichiers actifs sur le site.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.<br/>**Espace de stockage utilisé (Mo)** indique le volume de stockage utilisé sur le site.  <br/> **Espace de stockage alloué (Mo)** indique le volume maximal de stockage alloué pour le site.  <br/> **Affichages de page** indique le nombre de fois où des pages ont été affichées sur le site.  <br/> **Pages visitées** indique le nombre de pages uniques visitées sur le site.  <br/> **Modèle web racine** indique le modèle utilisé pour créer le site.  <br/> REMARQUE : si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne Modèle Web racine. <br/>Si les stratégies de votre organisation vous empêchent d’afficher les rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|9.  <br/> |Sélectionnez **Gérer les colonnes** ![ Gérer les ](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) colonnes pour ajouter ou supprimer des colonnes dans le rapport.    <br/> |
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** ![ ](../../media/4dc548cc-8061-48d5-9240-6793affca43a.png) l’exportation. Cela a pour effet d'exporter les données de tous les sites afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 sites, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 sites, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> REMARQUE : lorsque les données sont exportées vers un fichier Excel, notez que la  date à laquelle le rapport de contenu a été généré est reflétée dans le fichier dans la colonne Données.      <br/>   |
|||
