---
title: Rapports Microsoft 365 dans le centre d’administration-activité des formulaires
ms.author: sirkkuw
author: sirkkuw
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
description: Découvrez comment obtenir un rapport d’activité Microsoft Forms à l’aide du tableau de bord des rapports Microsoft 365 dans le centre d’administration Microsoft 365.
ms.openlocfilehash: 78b09edfbfeb83c056af16787085b7c4cfe93fc6
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47949203"
---
# <a name="microsoft-365-reports-in-the-admin-center---forms-activity"></a>Rapports Microsoft 365 dans le centre d’administration-activité des formulaires

Le tableau de bord **rapports** Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l’activité de chaque utilisateur titulaire d’une licence pour utiliser Microsoft Forms en examinant leur interaction avec les formulaires. Elle vous aide également à comprendre le niveau de collaboration en examinant le nombre de formulaires créés et les formulaires auxquels l’utilisateur a répondu.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, teams, Team communications ou Skype entreprise pour afficher des rapports. 

## <a name="how-to-get-to-the-forms-activity-report"></a>Comment accéder au rapport d’activité de formulaires

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la liste déroulante **Sélectionner un rapport** , sélectionnez activité des **formulaires** \> **activity**.

## <a name="interpret-the-forms-activity-report"></a>Interpréter le rapport d’activité de formulaires

Vous pouvez obtenir une vue de l’activité des formulaires de votre utilisateur en examinant les graphiques **activité** et **utilisateurs** . 

![Rapport d’activité de formulaires](../../media/adminformsactivity.png)

|Item|Description|
|:-----|:-----|
|1.  <br/> |Le rapport d' **activité de formulaires** peut être consulté pour connaître les tendances des 7, 30, 90 ou 180. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours après la date actuelle (pas la date de génération du rapport).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement les 24 à 48 heures.  <br/> |
|3.  <br/> |La vue **utilisateurs** vous permet de comprendre la tendance du nombre d’utilisateurs de formulaires actifs. Un utilisateur est considéré comme actif s’il a exécuté une activité relative à un formulaire (création, modification, affichage, etc.) ou a répondu à un formulaire pendant une période spécifique.  <br/> |
|4.  <br/> |La vue **activité** vous permet de comprendre la tendance du nombre d’utilisateurs actifs. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) ou consulté une page au cours de la période spécifiée.<br/> Remarque : une activité peut se produire plusieurs fois pour un seul formulaire, mais ne comptera qu’en tant que formulaire actif. Par exemple, vous pouvez créer un formulaire et continuer à modifier le même formulaire plusieurs fois sur une période spécifiée, mais il ne comptera qu’un seul formulaire. Toutefois, si un utilisateur a envoyé plusieurs réponses pour le même formulaire, chaque réponse sera toujours une réponse individuelle et sera donc comptée plusieurs fois. <br/> |
|5.<br/>|Sur le graphique **utilisateurs** , l’axe Y indique le nombre d’utilisateurs uniques. L’axe X représente la date à laquelle les utilisateurs uniques sont actifs. Les légendes sont les suivantes :<br/><br/>Les **concepteurs** signifient que l’utilisateur a créé ou modifié un formulaire.<br/>Les **répondeurs** signifie que l’utilisateur a envoyé des réponses à un formulaire.<br/> Le **nombre total d’utilisateurs** désigne tout le monde dans la société qui a été concepteur ou répondeur.<br/><br/> Dans le graphique **activité** , l’axe Y représente le nombre de formulaires ou de réponses uniques. L’axe X représente la date à laquelle l’activité du formulaire ou de la réponse s’est produite. Les légendes sont les suivantes :<br/><br/>**Formulaires créés** indique le nombre de formulaires uniques créés par les utilisateurs.<br/> **Réponses de connexion** nombre de réponses de connexion reçues par les utilisateurs de l’organisation.<br/> Les **réponses anonymes** sont le nombre de réponses anonymes reçues par les utilisateurs de l’organisation.<br/><br/>|
|6.<br/>|Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique utilisateurs, sélectionnez concepteurs, répondeurs ou nombre total d’utilisateurs pour voir uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations dans le tableau de grille en dessous.|
|7.<br/>|Le tableau montre une répartition des activités au niveau de chaque utilisateur. Les légendes sont les suivantes :<br/><br/>**Username** est l’adresse de messagerie de l’utilisateur qui a effectué l’activité sur Microsoft Forms.<br/>**Date de la dernière activité (UTC)** est la dernière date à laquelle une activité de formulaire a été effectuée par l’utilisateur pour la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.<br/><br/>Cette opération filtre le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs ayant effectué l’activité à ce jour spécifique.<br/><br/>Le **nombre de formulaires créés** est le nombre de formulaires créés par l’utilisateur.<br/> **Nombre de formulaires** auxquels l’utilisateur a envoyé des réponses a répondu.|
|8.<br/>|Sélectionnez l’icône **gérer les colonnes** pour ajouter ou supprimer des colonnes dans le rapport.|
|9.<br/>|Vous pouvez également exporter les données du rapport dans un fichier. csv Excel en sélectionnant le lien **Exporter** . Cette opération exporte les données de tous les utilisateurs et vous permet d’effectuer une agrégation, un tri et un filtrage simples à des fins d’analyse approfondie. Si vous avez moins de 100 utilisateurs, vous pouvez trier et filtrer dans le tableau du rapport proprement dit. Si vous avez plus de 100 utilisateurs, pour filtrer et trier les données, vous devez les exporter.|