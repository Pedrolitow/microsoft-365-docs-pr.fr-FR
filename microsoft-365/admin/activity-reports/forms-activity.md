---
title: Rapports Microsoft 365 dans le Centre d’administration - Activité des formulaires
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
description: Découvrez comment obtenir un rapport d’activité Microsoft Forms à l’aide du tableau de bord Rapports Microsoft 365 dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: 843548e77067c7598cfa78ba6fac985237f6f62c
ms.sourcegitcommit: e56894917d2aae05705c3b9447388d10e2156183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48841112"
---
# <a name="microsoft-365-reports-in-the-admin-center---forms-activity"></a>Rapports Microsoft 365 dans le Centre d’administration - Activité des formulaires

Le tableau de  bord Rapports Microsoft 365 vous présente la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).
  
Par exemple, vous pouvez comprendre l’activité de chaque utilisateur titulaire d’une licence d’utilisation de Microsoft Forms en regardant leur interaction avec les formulaires. Il vous permet également de comprendre le niveau de collaboration en cours en regardant le nombre de formulaires créés et les formulaires à partir des formulaires à partir des utilisateurs.
  
> [!NOTE]
> Vous devez être un administrateur général, un lecteur global ou un lecteur de rapports dans Microsoft 365 ou un administrateur Exchange, SharePoint, Teams Service, Teams Communications ou Skype Entreprise pour voir les rapports. 

## <a name="how-to-get-to-the-forms-activity-report"></a>Comment obtenir le rapport d’activité Formulaires

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

    
2. Dans la **drop-down Sélectionner un rapport,** sélectionnez **Activité** \> **formulaires.**

## <a name="interpret-the-forms-activity-report"></a>Interpréter le rapport d’activité des formulaires

Vous pouvez obtenir une vue de l’activité de formulaires de votre utilisateur en regardant les **graphiques** Activité **et** Utilisateurs. 

![Rapport d’activité des formulaires](../../media/adminformsactivity.png)

|Item|Description|
|:-----|:-----|
|1.  <br/> |Le **rapport d’activité** forms permet d’afficher les tendances des 7, 30, 90 ou 180 derniers jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau (7) affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).  <br/> |
|2.  <br/> |Les données de chaque rapport couvrent généralement jusqu’aux dernières 24 à 48 heures.  <br/> |
|3.  <br/> |**L’affichage** Utilisateurs vous permet de comprendre la tendance du nombre d’utilisateurs de formulaires actifs. Un utilisateur est considéré comme actif s’il a exécuté une activité autour d’un formulaire (créer, modifier, afficher, etc.) ou a répondu à un formulaire au cours de la période spécifique.  <br/> |
|4.  <br/> |**L’affichage** Activité vous permet de comprendre la tendance du nombre d’utilisateurs actifs. Un utilisateur est considéré comme actif s'il a eu une activité de fichier (enregistrer, synchroniser, modifier ou partager) ou consulté une page au cours de la période spécifiée.<br/> REMARQUE : une activité peut se produire plusieurs fois pour un seul formulaire, mais ne compte qu’en tant que formulaire actif. Par exemple, vous pouvez créer un formulaire et continuer à modifier le même formulaire plusieurs fois sur une période spécifiée, mais il ne compte qu’en tant que formulaire unique. Toutefois, si un utilisateur a envoyé plusieurs réponses pour le même formulaire, chaque réponse reste une réponse individuelle et est donc comptabilisée plusieurs fois. <br/> |
|5.<br/>|Dans le **graphique Utilisateurs,** l’axe Y indique le nombre d’utilisateurs uniques. L’axe X est la date à laquelle les utilisateurs uniques sont actifs. Les légendes sont les suivantes :<br/><br/>**Les concepteurs** signifient que l’utilisateur a créé ou modifié un formulaire.<br/>**Les répondeurs** signifient que l’utilisateur a envoyé des réponses à un formulaire.<br/> **Le nombre total** d’utilisateurs signifie toute personne de l’entreprise qui a été concepteur ou répondeur.<br/><br/> Dans le **graphique d’activité,** l’axe Y est le nombre de formulaires ou de réponses uniques. L’axe X est la date à laquelle l’activité de formulaire ou de réponse s’est produite. Les légendes sont les suivantes :<br/><br/>**Les formulaires** créés sont le nombre de formulaires uniques créés par les utilisateurs.<br/> **Réponses signées le** nombre de réponses signées reçues par les utilisateurs de l’organisation.<br/> **Les réponses anonymes** sont le nombre de réponses anonymes reçues par les utilisateurs de l’organisation.<br/><br/>|
|6.<br/>|Vous pouvez filtrer les séries que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique Utilisateurs, sélectionnez les concepteurs, les répondeurs ou le nombre total d’utilisateurs pour voir uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations du tableau de grille en dessous.|
|7.<br/>|Le tableau présente une répartition des activités au niveau de chaque utilisateur. Les légendes sont les suivantes :<br/><br/>**Le nom** d’utilisateur est l’adresse e-mail de l’utilisateur qui a effectué l’activité sur Microsoft Forms.<br/>**La date de la dernière activité (UTC)** est la date la plus récente à laquelle une activité de formulaire a été effectuée par l’utilisateur pour la plage de dates sélectionnée. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.<br/><br/>Cela permet de filtrer le tableau pour afficher les données d’activité des fichiers uniquement pour les utilisateurs qui ont effectué l’activité ce jour-là.<br/><br/>**Le nombre de formulaires** créés est le nombre de formulaires créés par l’utilisateur.<br/> **Le nombre de formulaires répondus** est le nombre de formulaires à qui l’utilisateur a envoyé des réponses.|
|8.<br/>|Sélectionnez **l’icône Gérer les** colonnes pour ajouter ou supprimer des colonnes dans le rapport.|
|9.<br/>|Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter.** Cela exporte les données pour tous les utilisateurs et vous permet d’obtenir une agrégation, un tri et un filtrage simples pour une analyse plus approfondie. Si vous avez moins de 100 utilisateurs, vous pouvez trier et filtrer dans le tableau du rapport lui-même. Si vous avez plus de 100 utilisateurs, pour filtrer et trier, vous devez exporter les données.|