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
description: Découvrez comment obtenir un rapport d’utilisation Microsoft 365 Apps pour voir l’activité des utilisateurs sous licence dans les applications et comment les applications sont utilisées sur plusieurs plateformes.
ms.openlocfilehash: f8d9baf29089b7dd37a3655dec4c33dfb873bb67
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68165226"
---
# <a name="microsoft-365-reports-in-the-admin-center---microsoft-365-apps-usage"></a>Rapports Microsoft 365 dans le Centre d’administration - utilisation Microsoft 365 Apps

Le tableau de bord Rapports Microsoft 365 affiche la vue d’ensemble de l’activité sur les produits de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit. Voir [la rubrique Présentation des rapports](activity-reports.md).

Par exemple, vous pouvez comprendre l’activité de chaque utilisateur sous licence pour utiliser Microsoft 365 Apps applications en examinant leur activité dans les applications et la façon dont elles sont utilisées sur plusieurs plateformes.

> [!NOTE]
> Les activations d’ordinateurs partagés ne sont pas incluses dans ce rapport.

## <a name="how-to-get-to-the-microsoft-365-apps-usage-report"></a>Comment accéder au rapport d’utilisation Microsoft 365 Apps

1. Dans le centre d’administration, accédez à la page **Rapports** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Utilisation</a>. 
2. Dans la page d’accueil du tableau de bord, cliquez sur le bouton **Afficher plus** sur la carte Utilisateurs actifs - Microsoft 365 Apps.

## <a name="interpret-the-microsoft-365-apps-usage-report"></a>Interpréter le rapport d’utilisation Microsoft 365 Apps

Vous pouvez obtenir une vue de l’activité Microsoft 365 Apps de votre utilisateur en examinant les **graphiques Utilisateurs** et **plateforme**.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Apps rapport d’utilisation.](../../media/0bcf67e6-a6e4-4109-a215-369f9f20ad84.png)

Le **rapport d’utilisation Microsoft 365 Apps** peut être consulté pour les tendances des 7 derniers jours, 30 jours, 90 jours ou 180 jours. Toutefois, si vous sélectionnez un jour particulier dans le rapport, le tableau affiche les données jusqu’à 28 jours à partir de la date actuelle (et non la date à laquelle le rapport a été généré).

Les données de chaque rapport couvrent généralement jusqu’aux deux derniers jours. Tous les six jours, nous actualisons le rapport avec des mises à jour mineures pour garantir la qualité des données.

La vue **Utilisateurs** affiche la tendance du nombre d’utilisateurs actifs pour chaque application : Outlook, Word, Excel, PowerPoint, OneNote et Teams. Les « utilisateurs actifs » sont tous ceux qui effectuent des actions intentionnelles au sein de ces applications.

La vue **Plateformes** montre la tendance des utilisateurs actifs dans toutes les applications pour chaque plateforme : Windows, Mac, Web et Mobile.

Dans le graphique Utilisateurs, l’axe Y correspond au nombre d’utilisateurs actifs uniques pour l’application correspondante. Dans le graphique Plateformes, l’axe Y correspond au nombre d’utilisateurs uniques pour la plateforme correspondante. L’axe X des deux graphiques correspond à la date à laquelle une application a été utilisée sur une plateforme donnée.

Vous pouvez filtrer la série que vous voyez sur le graphique en sélectionnant un élément dans la légende. Par exemple, dans le graphique Utilisateurs, sélectionnez Outlook, Word, Excel, PowerPoint, OneDrive ou Teams pour afficher uniquement les informations relatives à chacune d’elles. La modification de cette sélection ne modifie pas les informations contenues dans la table de grille située sous celle-ci.

Le tableau présente une répartition des données au niveau utilisateur. Vous pouvez ajouter ou supprimer des colonnes.


|Élément|Description|
|---|---|
|Nom d’utilisateur|Adresse e-mail de l’utilisateur qui a effectué l’activité sur Microsoft Apps.|
|Dernière date d’activation (UTC)|Date la plus récente à laquelle l’utilisateur a activé son abonnement Microsoft 365 Apps sur un ordinateur ou se connecte sur un ordinateur partagé et démarre l’application avec son compte.|
|Date de la dernière activité (UTC)|Date la plus récente à laquelle une activité intentionnelle a été effectuée par l’utilisateur. Pour voir l'activité qui s'est produite à une date spécifique, sélectionnez celle-ci directement dans le graphique.|


Les autres colonnes identifient si l’utilisateur était actif sur cette plateforme pour cette application (dans Microsoft 365 Apps) au cours de la période sélectionnée.

Sélectionnez l’icône **Choisir des colonnes** pour ajouter ou supprimer des colonnes du rapport.

Vous pouvez également exporter les données du rapport dans un fichier Excel .csv en sélectionnant le lien **Exporter** . Cette opération exporte des données pour tous les utilisateurs et vous permet d’effectuer une agrégation, un tri et un filtrage simples pour une analyse plus approfondie. 