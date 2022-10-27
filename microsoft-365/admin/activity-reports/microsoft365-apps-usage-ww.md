---
title: rapports d’utilisation des applications Centre d'administration Microsoft 365
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: Découvrez comment obtenir un rapport d’utilisation Microsoft 365 Apps pour voir l’activité des utilisateurs sous licence dans les applications et comment les applications sont utilisées sur les plateformes.
ms.openlocfilehash: 9efa15c1e4204ea29eadd14ed32bec8af688e480
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722899"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - utilisation Microsoft 365 Apps

Le tableau de bord Rapports Microsoft 365 vous montre la vue d’ensemble de l’activité dans les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).

Par exemple, vous pouvez comprendre l’activité de chaque utilisateur autorisé à utiliser Microsoft 365 Apps applications en examinant son activité dans les applications et la façon dont elles sont utilisées sur les plateformes.

> [!NOTE]
> Les activations d’ordinateurs partagés ne sont pas incluses dans ce rapport.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Comment accéder au rapport d’utilisation Microsoft 365 Apps

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** de la carte Utilisateurs actifs - Microsoft 365 Apps.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Interpréter le rapport d’utilisation Microsoft 365 Apps

Vous pouvez obtenir une vue de l’activité Microsoft 365 Apps de votre utilisateur en examinant les **graphiques Utilisateurs** et **Plateforme**.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Apps rapport d’utilisation.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

Le rapport **d’utilisation Microsoft 365 Apps** peut être consulté pour connaître les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, la table affiche les données pendant jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Les données de chaque rapport couvrent généralement jusqu’aux deux derniers jours. Tous les six jours, nous actualiserons le rapport avec des mises à jour mineures pour garantir la qualité des données.

La vue **Utilisateurs** affiche la tendance du nombre d’utilisateurs actifs pour chaque application : Outlook, Word, Excel, PowerPoint, OneNote et Teams. Les « utilisateurs actifs » sont tous ceux qui effectuent des actions intentionnelles au sein de ces applications.

La vue **Plateformes** montre la tendance des utilisateurs actifs dans toutes les applications pour chaque plateforme : Windows, Mac, Web et Mobile.

Dans le graphique Utilisateurs, l’axe Y correspond au nombre d’utilisateurs actifs uniques pour l’application respective. Dans le graphique Plateformes, l’axe Y est le nombre d’utilisateurs uniques pour la plateforme respective. L’axe X des deux graphiques est la date à laquelle une application a été utilisée sur une plateforme donnée.

Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique Utilisateurs, sélectionnez Outlook, Word, Excel, PowerPoint, OneDrive ou Teams pour afficher uniquement les informations relatives à chacun d’eux. La modification de cette sélection ne modifie pas les informations de la table de grille située en dessous.

Le tableau présente une répartition des données au niveau utilisateur. Vous pouvez ajouter ou supprimer des colonnes.


|Élément|Description|
|---|---|
|Nom d’utilisateur|Adresse e-mail de l’utilisateur qui a effectué l’activité sur Microsoft Apps.|
|Date de la dernière activation (UTC)|Date la plus récente à laquelle l’utilisateur a activé son abonnement Microsoft 365 Apps sur une machine ou se connecte sur un ordinateur partagé et démarre l’application avec son compte.|
|Date de la dernière activité (UTC)|Date la plus récente à laquelle une activité intentionnelle a été effectuée par l’utilisateur. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.|


Les autres colonnes déterminent si l’utilisateur était actif sur cette plateforme pour cette application (dans Microsoft 365 Apps) au cours de la période sélectionnée.

Sélectionnez l’icône **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

Vous pouvez également exporter les données du rapport dans un fichier .csv Excel en sélectionnant le lien **Exporter** . Cela exporte des données pour tous les utilisateurs et vous permet d’effectuer une agrégation, un tri et un filtrage simples pour une analyse plus approfondie. 