---
title: rapports de groupes Centre d'administration Microsoft 365
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: Obtenez un rapport Groupes Microsoft 365 pour obtenir des insights sur l’activité des groupes de votre organisation et voir combien de groupes sont créés et utilisés.
ms.openlocfilehash: dce585ddb496be67b1045baa4b7cea0dc3b7fc24
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66662677"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>Rapports Microsoft 365 dans le Centre d’administration - Groupes Microsoft 365

Le tableau de bord Rapports Microsoft 365 affiche la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport des groupes Microsoft 365, vous pouvez obtenir des insights sur l’activité des groupes de votre organisation et voir combien de groupes sont créés et utilisés.

## <a name="how-to-get-to-the-groups-report"></a>Comment accéder au rapport de groupes

1. Dans le Centre d’administration, sélectionnez **Rapports**, puis **Utilisation**.

2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte Utilisateurs actifs - Microsoft 365 Apps ou Utilisateurs actifs - Services Microsoft 365 pour accéder à la page de rapport Office 365.

## <a name="interpret-the-groups-report"></a>Interpréter le rapport de groupes

Vous pouvez afficher les activations dans le rapport Office 365 en choisissant l’onglet **Activité groupes**.

:::image type="content" alt-text="Rapports Microsoft 365 - activité de groupes Microsoft Office 365." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

:::image type="content" alt-text="Office 365 le rapport d’activité des groupes : choisissez des colonnes." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter** . Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. 

Le rapport de **groupes** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

### <a name="groupid-hidden-by-default"></a>GroupID masqué par défaut
Lorsque vous exportez les données du rapport, par défaut, vous ne pouvez pas afficher la variable **GroupID** dans le fichier Excel .csv que vous téléchargez. Si vous souhaitez afficher les informations GroupID et toutes les autres informations identifiables dans les rapports d’utilisation de Microsoft 365, vous pouvez choisir [d’afficher les détails de l’utilisateur dans les rapports](../../admin/activity-reports/activity-reports.md#show-user-details-in-the-reports) par le biais des paramètres organisationnels du Centre d'administration Microsoft 365.  Vous devez être un administrateur général pour apporter ces modifications.

Voici les définitions des métriques disponibles dans la table de rapports.

|Métrique|Définition|
|:-----|:-----|
|Nom du groupe |Nom du groupe. |
|Deleted |Nombre de groupes supprimés. Si le groupe est supprimé, mais qu'il a connu une activité dans la période du rapport, il apparaît dans la grille avec cet indicateur défini sur true. |
|Propriétaire du groupe |Nom du propriétaire du groupe. |
|Date de la dernière activité (UTC) |Date la plus récente à laquelle un message a été reçu par le groupe. Il s'agit de la date la plus récente à laquelle une activité a eu lieu dans une conversation par courrier, dans Yammer ou sur le site. |
|Type |Type de groupe. Il peut être privé ou public. |
|E-mails reçus dans Exchange |Nombre de messages reçus par le groupe.|
|E-mails dans Exchange (total) |Nombre total d’éléments dans la boîte aux lettres du groupe. |
|Stockage de boîte aux lettres utilisé pour Exchange (Mo) |Stockage utilisé par la boîte aux lettres du groupe. |
|Fichiers SharePoint (total) |Nombre de fichiers stockés dans les sites de groupe SharePoint. |
|Fichiers SharePoint (actifs) |Nombre de fichiers du site de groupe SharePoint qui ont été activés (affichés ou modifiés, synchronisés, partagés en interne ou en externe) pendant la période de rapport. |
|Total du stockage de site utilisé pour SharePoint (Mo) |Quantité de stockage en Mo utilisée pendant la période de rapport. |
|Messages dans Yammer (publié) |Nombre de messages publiés dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (lecture) |Nombre de conversations lues dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (aimé) |Nombre de messages aimés dans le groupe Yammer au cours de la période de rapport. |
|Members |Nombre de membres dans le groupe. |
|Membres externes |Nombre d’utilisateurs externes dans le groupe.|
|Nombre total de réunions organisées  |Somme des réunions ponctuelles planifiées et périodiques qu’un utilisateur a organisées pendant la période spécifiée.|
|Messages de canal  |Nombre de messages uniques qu’un utilisateur a publiés dans une conversation d’équipe pendant la période spécifiée. Cela inclut les publications d’origine et les réponses. |

## <a name="related-content"></a>Contenu associé

[Rapports Microsoft 365 dans le centre d’administration](activity-reports.md) (article)\
[Rapports Microsoft 365 dans le centre d’administration - Utilisateurs actifs](../../admin/activity-reports/active-users-ww.md) (article)
