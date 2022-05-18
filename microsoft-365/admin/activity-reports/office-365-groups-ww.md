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
ms.openlocfilehash: 1c51ddf997fb0c1c3e2416d979b83b339c414d93
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467369"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-groups"></a>rapports Microsoft 365 dans le Centre d’administration - groupes Microsoft 365

Le tableau de bord Microsoft 365 Rapports vous montre la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md). Dans le rapport Microsoft 365 groupes, vous pouvez obtenir des insights sur l’activité des groupes dans votre organisation et voir combien de groupes sont créés et utilisés.
  
## <a name="how-to-get-to-the-groups-report"></a>Comment accéder au rapport de groupes

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>.

2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur les utilisateurs actifs - Microsoft 365 Apps ou utilisateurs actifs - Microsoft 365 carte Services pour accéder à la page de rapport Office 365.
  
## <a name="interpret-the-groups-report"></a>Interpréter le rapport de groupes

Vous pouvez afficher les activations dans le rapport Office 365 en choisissant l’onglet **Activité groupes**.

:::image type="content" alt-text="Microsoft 365 rapports : activité de groupes Microsoft Office 365." source="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png" lightbox="../../media/ab90e30b-8938-4110-ab3d-ee472a4cfe21.png":::

**Sélectionnez Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

:::image type="content" alt-text="Office 365 le rapport d’activité des groupes : choisissez des colonnes." source="../../media/1600556a-f5f1-47d9-b325-cd77c78f4004.png":::

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter**. Cela a pour effet d'exporter les données de tous les utilisateurs afin d'effectuer un tri et un filtrage simples à des fins d'analyse approfondie. Si vous avez moins de 2000 utilisateurs, vous pouvez trier et filtrer dans le tableau, au sein du rapport proprement dit. Si vous avez plus de 2000 utilisateurs, pour filtrer et trier les données, vous devez préalablement les exporter. 

Le rapport de **groupes** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

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
|fichiers SharePoint (total) |Nombre de fichiers stockés dans SharePoint sites de groupe. |
|fichiers SharePoint (actifs) |Nombre de fichiers dans le site de groupe SharePoint qui ont été activés (affichés ou modifiés, synchronisés, partagés en interne ou en externe) pendant la période de rapport. |
|Total du stockage de site utilisé pour SharePoint (Mo) |Quantité de stockage en Mo utilisée pendant la période de rapport. |
|Messages dans Yammer (publié) |Nombre de messages publiés dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (lecture) |Nombre de conversations lues dans le groupe Yammer au cours de la période de rapport. |
|Messages dans Yammer (aimé) |Nombre de messages aimés dans le groupe Yammer au cours de la période de rapport. |
|Members |Nombre de membres dans le groupe. |
|Membres externes |Nombre d’utilisateurs externes dans le groupe.|


## <a name="related-content"></a>Contenu connexe

[Microsoft 365 rapports dans le centre d’administration](activity-reports.md) (article)\
[Rapports intelligents et insights dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/reports-and-insights-in-security-and-compliance) (article)\
[Microsoft 365 rapports dans le centre d’administration - Utilisateurs actifs](../../admin/activity-reports/active-users-ww.md) (article)

