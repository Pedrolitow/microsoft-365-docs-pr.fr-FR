---
title: Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365
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
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Obtenez un rapport de groupes Microsoft 365 pour connaître les groupes et leurs activités.
ms.openlocfilehash: 9ab034531099b5572c42eb3a48ec28d99487ac99
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51579553"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport des groupes Microsoft 365, vous pouvez obtenir des informations sur l’activité des groupes dans votre organisation et voir combien de groupes sont créés et utilisés.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
  
## <a name="how-to-get-to-the-groups-report"></a>Comment obtenir le rapport des groupes

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

2. Dans les options, **sélectionnez Afficher plus sous** **Utilisateurs actifs - Services Microsoft 365**.
3. Dans la **drop-down Sélectionner un** rapport, sélectionnez Activité groupes Office **365.** \> 
  
## <a name="interpret-the-groups-report"></a>Interpréter le rapport des groupes

Vous pouvez obtenir une vue de l’activité des groupes en regardant les graphiques **Groupes,** **Activité,** **Fichiers** et **Stockage.** 
  
![Rapports Microsoft 365 : activités de groupes](../../media/852027a4-8eab-47d1-b770-2bb874bdc403.png)
  
|Élément|Description|
|:-----|:-----|
|1.  <br/> |Le rapport des groupes **Microsoft 365** permet d’afficher les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.  <br/> |
|3.  <br/> |L’affichage Groupes affiche un nombre total de groupes qui existaient un jour donné et des groupes actifs ce jour-là en fonction des conversations par courrier électronique, des publications Yammer et des activités de fichiers SharePoint et des pages SharePoint vues.   <br/> |
|4.  <br/> |L'affichage **Activité** indique le nombre d'activités de groupe entre les charges de travail de groupe. Vous pouvez afficher les e-mails Exchange envoyés aux boîtes aux lettres de tous les groupes n'importe quel jour de la période du rapport. Vous pouvez également voir les messages publiés, lus et aimés dans Yammer groupes associés à un groupe. <br/> |
|5.  <br/> |**L’affichage** Fichiers vous indique le nombre total de fichiers et le nombre de fichiers actifs sur tous les sites de groupe associés à un groupe.  <br/> |
|6.  <br/> |L'affichage **Stockage** indique l'espace de stockage total utilisé sur les boîtes aux lettres de tous les groupes et sites de groupe.  <br/> |
|7.  <br/> | Sur le graphique **Groupes**, l'axe Y représente le nombre de groupes (total comparé à actifs).  <br/>  Dans le **graphique d’activité,** l’axe Y indique le nombre de fois qu’une activité a été effectuée en groupes.  <br/>  Sur le graphique **Fichiers**, l'axe Y représente le nombre total de fichiers ou le nombre de fichiers actifs.  <br/>  Sur le graphique **Stockage**, l'axe Y représente l'espace de stockage total utilisé par la boîte aux lettres du groupe ou par le site.  <br/>  L'axe X sur les trois graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|8.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Groupes,** sélectionnez **Total** ou Total **actif** et Nombre actif de groupes pour voir uniquement les informations relatives ![ à chacun ](../../media/8eebd496-5955-4419-8d53-5f3ba1ad1c88.png) d’eux. Cette sélection ne modifie nullement les informations figurant dans le tableau grille.  <br/> |
|9.  <br/> | La liste des groupes affichés est déterminée par l'ensemble de tous les groupes qui ont existé (non supprimés) dans l'intervalle de temps de création de rapports (180 jours) le plus large. Le nombre d'activités (conversations par courrier, publications Yammer et activités sur les fichiers SharePoint) varie en fonction de la date choisie.  <br/> REMARQUE : vous ne verrez peut-être pas tous les éléments de la liste ci-dessous dans les colonnes tant que vous ne les avez pas ajoutés.<br/>**Nom du groupe** correspond au nom du groupe.  <br/> **Supprimé** correspond au nombre de groupes supprimés. Si le groupe est supprimé, mais qu'il a connu une activité dans la période du rapport, il apparaît dans la grille avec cet indicateur défini sur true.  <br/> **Propriétaire du groupe** correspond au nom du propriétaire du groupe.  <br/> **La date de la** dernière activité est la date la plus récente à laquelle un message a été reçu par le groupe. Il s'agit de la date la plus récente à laquelle une activité a eu lieu dans une conversation par courrier, dans Yammer ou sur le site.  <br/> **Type** correspond au type de groupe. Il peut être privé ou public.  <br/> **Membres** correspond au nombre de membres du groupe.  <br/> **Membres externes** correspond au nombre d'utilisateurs externes du groupe.  <br/> **Exchange** <br/> **Courriers électroniques reçus** correspond au nombre de messages reçus par le groupe.  <br/> **Nombre total d'éléments dans la boîte aux lettres** correspond au nombre d'éléments présents dans la boîte aux lettres du groupe.  <br/> **Stockage de boîte aux lettres utilisé** correspond à l'espace de stockage utilisé par la boîte aux lettres du groupe.  <br/> **Fichiers SharePoint** <br/> **Nombre total de fichiers** correspond au nombre de fichiers stockés sur des sites de groupe SharePoint.  <br/> **Fichiers actifs** correspond au nombre de fichiers du site de groupe SharePoint exécutés (affichés, modifiés, synchronisés, partagés en interne ou en externe) pendant la période du rapport.  <br/> **Stockage du site utilisé (Mo)** correspond au stockage en Mo utilisé pendant la période du rapport.  <br/> **Messages Yammer** <br/> **Publié** correspond au nombre de messages publiés dans le groupe Yammer pendant la période couverte par le rapport.  <br/> **Lu** correspond au nombre de conversations lues dans le groupe Yammer pendant la période couverte par le rapport.  <br/> **Aimé** correspond au nombre de messages aimés dans le groupe Yammer pendant la période couverte par le rapport.  <br/>  Si la politique de votre organisation vous empêche de consulter les rapports sur lesquels figurent des informations propres aux utilisateurs, vous pouvez modifier les paramètres de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|10,  <br/> |Select or tap **More Actions** button Mobile OWA More Actions next to a column heading to add or remove columns from ![ the ](../../media/80044eef-2368-4c7e-8d31-7155b029e0cf.png) report.  <br/> ![Rapport de groupes : choisir des colonnes](../../media/d7fb95d6-2a2e-4144-b80d-581223e48043.png)|
|11,  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter.  <br/> |
|||
   
