---
title: rapports de groupes Centre d'administration Microsoft 365
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: a27f1a99-3557-4f85-9560-a28e3d822a40
description: Obtenez un rapport Groupes Microsoft 365 pour obtenir des insights sur l’activité des groupes dans votre organisation et voir le nombre de groupes créés et utilisés.
ms.openlocfilehash: 814d1ca174024c06cff20c36d05d886178035cbc
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722855"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport groupes Microsoft 365, vous pouvez obtenir des insights sur l’activité des groupes dans votre organisation et voir le nombre de groupes créés et utilisés.

## <a name="how-to-get-to-the-groups-report"></a>Comment accéder au rapport des groupes

1. Dans le Centre d’administration, sélectionnez **Rapports**, puis **Utilisation**.

2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** dans la carte Utilisateurs actifs - Microsoft 365 Apps ou Utilisateurs actifs - Services Microsoft 365 pour accéder à la page du rapport Office 365.

## <a name="interpret-the-groups-report"></a>Interpréter le rapport de groupes

Vous pouvez afficher les activations dans le rapport Office 365 en choisissant l’onglet **Activité des groupes**.

:::image type="content" alt-text="Rapports Microsoft 365 : activité Microsoft Office 365 groupes." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

Sélectionnez **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

:::image type="content" alt-text="Office 365 rapport d’activité des groupes : choisissez des colonnes." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 

Le rapport des **groupes** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

### <a name="groupid-hidden-by-default"></a>GroupID masqué par défaut
Lorsque vous exportez les données du rapport, vous ne pouvez pas afficher par défaut la variable **GroupID** dans le fichier de .csv Excel que vous téléchargez. Si vous souhaitez afficher les informations GroupID et toutes les autres informations d’identification dans les rapports d’utilisation Microsoft 365, vous pouvez choisir [d’afficher les détails de l’utilisateur dans les rapports](../../admin/activity-reports/activity-reports.md#show-user-details-in-the-reports) via les paramètres de l’organisation dans le Centre d'administration Microsoft 365.  Vous devez être administrateur général pour effectuer ces modifications.

Voici les définitions des métriques disponibles dans la table de rapport.

|Métrique|Définition|
|:-----|:-----|
|Nom du groupe |Nom du groupe. |
|Deleted |Nombre de groupes supprimés. Si le groupe est supprimé, mais qu'il a connu une activité dans la période du rapport, il apparaît dans la grille avec cet indicateur défini sur true. |
|Propriétaire du groupe |Nom du propriétaire du groupe. |
|Date de la dernière activité (UTC) |Date la plus récente à laquelle un message a été reçu par le groupe. Il s'agit de la date la plus récente à laquelle une activité a eu lieu dans une conversation par courrier, dans Yammer ou sur le site. |
|Type |Type de groupe. Il peut être privé ou public. |
|E-mails reçus dans Exchange |Nombre de messages reçus par le groupe.|
|E-mails dans Exchange (total) |Nombre total d’éléments dans la boîte aux lettres du groupe. |
|Stockage de boîtes aux lettres utilisé pour Exchange (Mo) |Stockage utilisé par la boîte aux lettres du groupe. |
|Fichiers SharePoint (total) |Nombre de fichiers stockés dans les sites de groupe SharePoint. |
|Fichiers SharePoint (actifs) |Nombre de fichiers du site de groupe SharePoint qui ont été traités (affichés ou modifiés, synchronisés, partagés en interne ou en externe) au cours de la période de création de rapports. |
|Stockage total de site utilisé pour SharePoint (Mo) |Quantité de stockage en Mo utilisée pendant la période de création de rapports. |
|Messages dans Yammer (publiés) |Nombre de messages publiés dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (lecture) |Nombre de conversations lues dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (j’aime) |Nombre de messages aimés dans le groupe Yammer au cours de la période de rapport. |
|Members |Nombre de membres dans le groupe. |
|Membres externes |Nombre d’utilisateurs externes dans le groupe.|
|Nombre total de réunions organisées  |Somme des réunions planifiées et périodiques qu’un utilisateur a organisées pendant la période spécifiée.|
|Messages de canal  |Nombre de messages uniques qu’un utilisateur a publiés dans une conversation d’équipe pendant la période spécifiée. Cela inclut les publications et les réponses d’origine. |

## <a name="related-content"></a>Contenu associé

[Rapports Microsoft 365 dans le Centre d’administration](activity-reports.md) (article)\
[Rapports Microsoft 365 dans le Centre d’administration - Utilisateurs actifs](../../admin/activity-reports/active-users-ww.md) (article)
