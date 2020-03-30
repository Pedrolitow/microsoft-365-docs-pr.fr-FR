---
title: Rapports Microsoft 365 dans le centre d’administration-utilisation du site SharePoint
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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- SPO160
- BSA160
ms.assetid: 4ecfb843-e5d5-464d-8bf6-7ed512a9b213
description: 'Obtenez le rapport sur l’utilisation du site SharePoint pour savoir combien de fichiers stockent les utilisateurs dans les sites SharePoint, combien sont utilisés activement et le stockage total consommé. '
ms.openlocfilehash: 92ff9c4dbfcc7fcd9f9fdc511584400273030f21
ms.sourcegitcommit: 2b626a7924b4be08f6eb21181453b778e6fde418
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "43047118"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Rapports Microsoft 365 dans le centre d’administration-utilisation du site SharePoint

En tant qu’administrateur Microsoft 365, le tableau de bord **rapports** vous montre l’activité vue d’ensemble des différents produits de votre organisation. Il vous permet d'explorer pour obtenir des informations plus précises sur les activités spécifiques de chaque produit. Par exemple, vous pouvez obtenir une vue d'ensemble de la valeur que vous apporte SharePoint, en termes de nombre total de fichiers que les utilisateurs stockent sur les sites SharePoint, de nombre de fichiers activement utilisés, et de stockage utilisé sur ces sites. Ensuite, vous pouvez explorer le rapport de l'utilisation du site SharePoint pour comprendre les tendances et les détails par niveau de site pour tous les sites. 
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports. 
 
## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Comment accéder au Rapport Utilisation du site SharePoint

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez **utilisation du site** **SharePoint** \> .
  
## <a name="interpreting-the-sharepoint-site-usage-report"></a>Interprétation du rapport Utilisation du site SharePoint

![SharePoint Site Usage Report](../../media/4f88fb7d-9aa8-470e-9e23-e31caaf77d78.png)
  
|||
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation du site SharePoint** permet d'observer les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures. <br/> |
|3.  <br/> |Le graphique **Sites**affiche le nombre total de sites SharePoint et le nombre de sites actifs. Il comprend tous les sites dans lesquels des utilisateurs ont effectué des activités d'affichage, de modification, de chargement, de téléchargement, de partage ou de synchronisation d'un fichier ou d'affichage d'une page durant la période de rapport.  <br/> |
|4.  <br/> |Le graphique **Fichiers** affiche le nombre total de fichiers sur l'ensemble des sites et le nombre de fichiers actifs. Le nombre total de fichiers inclut les fichiers des utilisateurs et les fichiers système. Un fichier est considéré comme étant actif s'il a été enregistré, synchronisé, modifié ou partagé au cours de la période spécifique.  <br/> Remarque : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais ne comptera qu’en tant que fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois sur une période de temps spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données.           |
|5.  <br/> |Le graphique **Stockage** présente la tendance de stockage alloué et utilisé pendant la période de rapport.  <br/> |
|6.  <br/> |Le graphique **Pages** présente le nombre de pages affichées sur tous les sites.  <br/> |
|7.  <br/> |Vous pouvez filtrer les graphiques que vous voyez en sélectionnant un élément dans la légende. Par exemple, dans le graphique **fichiers** , sélectionnez **fichiers** ou **fichiers actifs**. Dans le graphique **sites** , vous pouvez sélectionner le **nombre total de sites** ou de **sites actifs**. Dans le graphique **stockage** , vous pouvez sélectionner le **stockage alloué** ou **consommé.** La modification de cette sélection ne modifie pas les informations du tableau grille.  <br/> |
|8.  <br/> | Le tableau montre une répartition des activités au niveau du site.  <br/> ![Options de colonne pour le rapport d’utilisation](../../media/sharepointsite-usage.png)           <br/> **URL du site** indique l'URL complète du site.  <br/> **Supprimé** est l'état de suppression du site. La suppression effective des sites prend au minimum 7 jours.  <br/> **Propriétaire du site** indique le nom d'utilisateur du propriétaire principal du site.  <br/>**Nom principal du propriétaire du site** est l’adresse de messagerie du propriétaire du site.  <br/> **Date de la dernière activité (UTC)** indique la date à laquelle une activité de fichier a été détectée ou une page affichée pour la dernière fois sur le site.  <br/> **Fichiers** indique le nombre de fichiers sur le site.  <br/> **Fichiers actifs** indique le nombre de fichiers actifs sur le site. Un fichier est considéré comme étant actif s'il a été enregistré, synchronisé, modifié ou partagé au cours de la période spécifique.  <br/> Remarque : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais ne comptera qu’en tant que fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois sur une période de temps spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données. >  Si des fichiers ont été supprimés au cours de la période spécifiée pour le rapport, le nombre de fichiers actifs indiqué dans le rapport peut être supérieur au nombre actuel de fichiers sur le site.<br/>**Espace de stockage utilisé (Mo)** indique le volume de stockage utilisé sur le site.  <br/> **Espace de stockage alloué (Mo)** indique le volume maximal de stockage alloué pour le site.  <br/> **Affichages de page** indique le nombre de fois où des pages ont été affichées sur le site.  <br/> **Pages visitées** indique le nombre de pages uniques visitées sur le site.  <br/> **Modèle web racine** indique le modèle utilisé pour créer le site.  <br/> Remarque : Si vous souhaitez filtrer les données par différents types de sites, exportez les données et utilisez la colonne de modèle Web racine. <br/>Si les stratégies de votre organisation vous empêchent d’afficher des rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **comment masquer les détails au niveau de l’utilisateur ?** dans les [rapports d’activité du centre d’administration 365 de Microsoft](activity-reports.md).  <br/> |
|9.  <br/> |Sélectionnez **gérer**![les colonnes](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) pour gérer les colonnes afin d’ajouter ou de supprimer des colonnes dans le rapport.    <br/> |
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant **le lien exporter l'** ![exportation](../../media/4dc548cc-8061-48d5-9240-6793affca43a.png) . Cela a pour effet d'exporter les données de tous les sites afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 sites, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 sites, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> Remarque : lorsque les données sont exportées vers un fichier Excel, Notez que la date à laquelle le rapport de contenu a été généré est reflétée dans le fichier dans les **données à partir de** la colonne.      <br/>   |
|||
   

