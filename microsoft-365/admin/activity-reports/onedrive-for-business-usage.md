---
title: Rapports Microsoft 365 dans le Centre d’administration - Utilisation de OneDrive Entreprise
ms.author: pebaum
author: pebaum
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
- ODB150
- ODB160
ms.assetid: 0de3b312-c4e8-4e4b-a02d-32b2f726a680
description: 'Obtenez le rapport d’utilisation de OneDrive Entreprise pour connaître le nombre total de fichiers et de stockage utilisés au sein de votre organisation. '
ms.openlocfilehash: e08dff4e763479afa197377d37e474384492c012
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47948915"
---
# <a name="microsoft-365-reports-in-the-admin-center---onedrive-for-business-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - Utilisation de OneDrive Entreprise

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Consultez [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, la carte OneDrive du tableau de bord offre une vue d'ensemble de ce que vous apporte OneDrive Entreprise en termes de nombre total de fichiers et d'espace de stockage utilisé au sein de votre organisation. Vous pouvez l'explorer pour connaître les tendances des comptes OneDrive actifs, le nombre de fichiers avec lesquels les utilisateurs interagissent ainsi que l'espace de stockage utilisé. Elle vous fournit également des détails pour chaque utilisateur OneDrive.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports.  
 
## <a name="how-do-i-get-to-the-onedrive-usage-report"></a>Comment accéder au Rapport Utilisation de OneDrive ?

1. Dans le Centre d’administration, allez sur **Utilisation des** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">rapports.</a>

    
2. Dans la **drop-down Sélectionner un** rapport, sélectionnez Utilisation de **OneDrive.** \>  
  
## <a name="interpret-the-onedrive-usage-report"></a>Interpréter le rapport Utilisation de OneDrive

Vous pouvez obtenir un aperçu de l'utilisation de OneDrive Entreprise en consultant les affichages **Comptes**, **Fichiers** et **Stockage**. 
  
![OneDrive Usage Report](../../media/49c5b93b-d081-436e-8992-236343a6d46b.png)
  
|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport **Utilisation de OneDrive** peut être consulté pour connaître les tendances des derniers 7 jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures. <br/>|
|3.  <br/> |L'affichage **Comptes** présente la tendance du nombre total et du nombre de comptes OneDrive actifs. Les « comptes actifs » sont ceux où des utilisateurs consultent, modifient, mettent en ligne, téléchargent, partagent ou synchronisent des fichiers.  <br/> |
|4.  <br/> |La vue **Fichiers** présente le nombre total de fichiers et le nombre de fichiers actifs. Un fichier est considéré comme actif s’il a été enregistré, synchronisé, modifié ou partagé au cours d’une période spécifique.  <br/> REMARQUE : une activité de fichier peut se produire plusieurs fois pour un seul fichier, mais ne compte qu’en tant que fichier actif. Par exemple, si vous enregistrez et synchronisez le même fichier plusieurs fois sur une période de temps spécifiée, cette activité ne compte que pour un seul fichier actif et un seul fichier synchronisé dans les données.           |
|5.  <br/> |L'affichage **Stockage** présente la tendance de l'espace de stockage de OneDrive que vous utilisez. Si vous souhaitez vérifier les limites de stockage, voir Vérifier si un utilisateur dispose de la limite de stockage par défaut [ou d’une limite spécifique.](https://docs.microsoft.com/onedrive/set-default-storage-space#check-if-a-user-has-the-default-storage-limit-or-a-specific-limit)  <br/> REMARQUE : la taille inclut toutes les versions et métadonnées associées aux fichiers.           |
|6.  <br/> | Sur le graphique **Comptes**, l'axe Y indique le nombre de comptes OneDrive.  <br/>  Sur le graphique **Fichiers**, l'axe Y indique le nombre de fichiers stockés dans OneDrive.  <br/>  Sur le graphique **Stockage**, l'axe Y indique l'espace de stockage OneDrive utilisé.  <br/>  L'axe X sur tous les graphiques représente la plage de dates sélectionnée pour ce rapport particulier.  <br/> |
|7.  <br/> |Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique **Fichiers,** sélectionnez **Nombre total de fichiers** ou fichiers **actifs.** Dans le **graphique Comptes,** sélectionnez **Nombre total de comptes** ou comptes **actifs.** Ou sur le graphique **de stockage,** sélectionnez **Stockage utilisé.** Le changement de sélection ne modifie pas le contenu du tableau.  <br/> |
|8.  <br/> | Le tableau présente une répartition des données pour chacun des utilisateurs OneDrive. Pour apparaître dans le tableau, un utilisateur doit disposer d'une licence de produit qui inclut OneDrive, et doit avoir activé SharePoint Online. L'utilisateur doit également soit se connecter à la synchronisation client de OneDrive, soit parcourir sonOneDrive en utilisant un navigateur web.  <br/>  Si le OneDrive présente une activité de fichier, la date de la dernière activité sur le fichier sera indiquée. Les lignes de la table sont classées par **Date de la dernière activité**. Par conséquent le OneDrive dont l'activité de fichier est la plus récente apparaît en haut de la liste.  <br/>  Vous pouvez ajouter ou supprimer des colonnes du tableau.  <br/> ![Options de colonne](../../media/onedriveusage-columns.png)  <br/> **L’URL** est l’adresse web du OneDrive de l’utilisateur.  <br/> **Supprimé** indique l'état de suppression du OneDrive. La suppression effective des comptes prend au minimum 7 jours.  <br/> **Propriétaire** indique le nom d'utilisateur du propriétaire principal du OneDrive.  <br/> **Le nom principal du** propriétaire est l’adresse e-mail du propriétaire de OneDrive.  <br/> **Date de la dernière activité (UTC)** indique la dernière date à laquelle une activité de fichier a été effectuée sur OneDrive. Si le OneDrive ne présente aucune activité de fichier, la valeur sera vide.  <br/> **Fichiers** indique le nombre de fichiers sur le OneDrive.  <br/> **Fichiers actifs** indique le nombre de fichiers actifs sur la période de temps.<br/> REMARQUE : si des fichiers ont été supprimés pendant la période spécifiée pour le rapport, le nombre de fichiers actifs affichés dans le rapport peut être supérieur au nombre actuel de fichiers dans OneDrive. Les utilisateurs supprimés continueront d’apparaître dans les rapports pendant 180 jours.<br/>**Stockage utilisé (Mo)** indique l'espace de stockage utilisé sur le OneDrive, exprimé en Mo. <br/>  Si les stratégies de votre organisation vous empêchent d’afficher les rapports où les informations utilisateur sont identifiables, vous pouvez modifier le paramètre de confidentialité de tous ces rapports. Consultez la section **Comment puis-je masquer les détails** au niveau de l’utilisateur ? dans les rapports d’activité du Centre d’administration [Microsoft 365.](activity-reports.md)  <br/> |
|9.  <br/> |Sélectionnez **l’icône Gérer les colonnes** ![ Gérer les ](../../media/13d2e536-de88-4db3-80c7-7a3a57298eb4.png) colonnes pour ajouter ou supprimer des colonnes dans le rapport.  <br/> |
|10.  <br/> |Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela a pour effet d'exporter la date de chacun des OneDrive afin d'effectuer simplement un tri et un filtrage pour des analyses complémentaires. Si vous avez moins de 2000 comptes OneDrive, vous pouvez trier et filtrer dans la table, au sein du rapport. Si vous avez plus de 2000 comptes OneDrive, pour filtrer et trier les données, vous devrez préalablement les exporter.  <br/> REMARQUE : lorsque les données sont exportées vers un fichier Excel, la date à  laquelle le rapport de contenu a été généré est reflétée dans le fichier dans la colonne Données.  <br/> |
|||
   
