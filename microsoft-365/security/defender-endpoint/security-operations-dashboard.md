---
title: tableau de bord des opérations de sécurité Centre de sécurité Microsoft Defender
description: Utilisez le tableau de bord pour identifier les appareils à risque, suivre l’état du service et afficher des statistiques et des informations sur les appareils et les alertes.
keywords: tableau de bord, alertes, nouvelles, en cours, résolues, à risque, appareils à risque, infections, rapports, statistiques, graphiques, graphiques, intégrité, détections de programmes malveillants actifs, catégorie de menaces, catégories, vol de mot de passe, ransomware, exploit, menace, gravité faible, programmes malveillants actifs
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: be52ed0d0c4ac2d2388f4d8dd3009e56ee6dbcab
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67693948"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>tableau de bord des opérations de sécurité Centre de sécurité Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Le **tableau de bord Des opérations de sécurité** est l’endroit où les fonctionnalités de détection et de réponse des points de terminaison sont exposées. Il fournit une vue d’ensemble générale de l’endroit où les détections ont été observées et met en évidence les endroits où des actions de réponse sont nécessaires.

Le tableau de bord affiche un instantané des éléments suivants :

- Alertes actives
- Appareils à risque
- Intégrité du capteur
- L’intégrité du service
- Rapports quotidiens sur les appareils
- Investigations automatisées actives
- Statistiques des enquêtes automatisées
- Utilisateurs à risque
- Activités suspectes

:::image type="content" source="images/atp-sec-ops-dashboard.png" alt-text="Tableau de bord des opérations de sécurité" lightbox="images/atp-sec-ops-dashboard.png":::

Vous pouvez explorer et examiner les alertes et les appareils pour déterminer rapidement si, où et quand des activités suspectes se sont produites dans votre réseau pour vous aider à comprendre le contexte dans lequel elles sont apparues.

Dans le **tableau de bord Des opérations de sécurité** , vous verrez des événements agrégés pour faciliter l’identification d’événements ou de comportements significatifs sur un appareil. Vous pouvez également explorer les événements granulaires et les indicateurs de bas niveau.

Il comporte également des vignettes cliquables qui donnent des indications visuelles sur l’état d’intégrité global de votre organisation. Chaque vignette ouvre une vue détaillée de la vue d’ensemble correspondante.

## <a name="active-alerts"></a>Alertes actives

Vous pouvez afficher le nombre total d’alertes actives des 30 derniers jours dans votre réseau à partir de la vignette. Les alertes sont regroupées en **nouvelles** et **en cours**.

:::image type="content" source="images/active-alerts-tile.png" alt-text="Page Alertes actives" lightbox="images/active-alerts-tile.png":::

Chaque groupe est sub-catégorisé dans ses niveaux de gravité d’alerte correspondants. Cliquez sur le nombre d’alertes à l’intérieur de chaque anneau d’alerte pour afficher une vue triée de la file d’attente de cette catégorie (**nouveau** ou **en cours**).

Pour plus d’informations, consultez la [vue d’ensemble des alertes](alerts-queue.md).

Chaque ligne inclut une catégorie de gravité d’alerte et une brève description de l’alerte. Vous pouvez cliquer sur une alerte pour afficher son affichage détaillé. Pour plus d’informations, consultez [Examiner Microsoft Defender pour point de terminaison alertes](investigate-alerts.md) et [vue d’ensemble des alertes](alerts-queue.md).

## <a name="devices-at-risk"></a>Appareils à risque

Cette vignette affiche la liste des appareils avec le plus grand nombre d’alertes actives. Le nombre total d’alertes pour chaque appareil est affiché dans un cercle en regard du nom de l’appareil, puis catégorisé par niveaux de gravité à l’extrémité de la vignette (pointez sur chaque barre de gravité pour voir son étiquette).

:::image type="content" source="images/devices-at-risk-tile.png" alt-text="Page Appareils à risque" lightbox="images/devices-at-risk-tile.png":::

Cliquez sur le nom de l’appareil pour afficher des détails sur cet appareil. Pour plus d’informations, consultez [Examiner les appareils dans la liste Microsoft Defender pour point de terminaison Appareils](investigate-machines.md).

Vous pouvez également cliquer sur **Liste des appareils** en haut de la vignette pour accéder directement à la **liste Appareils**, triée par le nombre d’alertes actives. Pour plus d’informations, consultez [Examiner les appareils dans la liste Microsoft Defender pour point de terminaison Appareils](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>Appareils présentant des problèmes de capteur

La vignette **Appareils présentant des problèmes de capteur** fournit des informations sur la capacité de chaque appareil à fournir des données de capteur au service Microsoft Defender pour point de terminaison. Il indique le nombre d’appareils qui nécessitent une attention particulière et vous aide à identifier les appareils problématiques.

:::image type="content" source="images/atp-tile-sensor-health.png" alt-text="Vignette Appareils avec problèmes de capteur" lightbox="images/atp-tile-sensor-health.png":::

Il existe deux indicateurs d’état qui fournissent des informations sur le nombre d’appareils qui ne signalent pas correctement au service :

- **Mal configuré :** ces appareils peuvent signaler partiellement des données de capteur au service Microsoft Defender pour point de terminaison et peuvent avoir des erreurs de configuration qui doivent être corrigées.
- **Inactif** : appareils qui ont cessé de signaler au service Microsoft Defender pour point de terminaison pendant plus de sept jours au cours du mois dernier.

Lorsque vous cliquez sur l’un des groupes, vous êtes dirigé vers la liste des appareils, filtré selon votre choix. Pour plus d’informations, consultez [Vérifier l’état du capteur](check-sensor-status.md) et [examiner les appareils](investigate-machines.md).

## <a name="service-health"></a>L’intégrité du service

La vignette **État des services** vous indique si le service est actif ou s’il y a des problèmes.

:::image type="content" source="images/status-tile.png" alt-text="Page État des services" lightbox="images/status-tile.png":::

Pour plus d’informations sur l’intégrité du service, consultez [Vérifier l’intégrité du service Microsoft Defender pour point de terminaison](service-status.md).

## <a name="daily-devices-reporting"></a>Rapports quotidiens sur les appareils

La vignette **de création de rapports d’appareils quotidiens** affiche un graphique à barres qui représente le nombre d’appareils qui ont été signalés quotidiennement au cours des 30 derniers jours. Pointez sur des barres individuelles sur le graphique pour voir le nombre exact d’appareils signalés chaque jour.

:::image type="content" source="images/atp-daily-devices-reporting.png" alt-text="Vignette de création de rapports d’appareils quotidiens" lightbox="images/atp-daily-devices-reporting.png":::

## <a name="active-automated-investigations"></a>Investigations automatisées actives

Vous pouvez afficher le nombre global d’investigations automatisées des 30 derniers jours dans votre réseau à partir de la vignette **Active Automated Investigations** . Les investigations sont regroupées en **action en attente**, **en attente d’appareil** et **en cours d’exécution**.

:::image type="content" source="images/atp-active-investigations-tile.png" alt-text="Les investigations automatisées actives" lightbox="images/atp-active-investigations-tile.png":::

## <a name="automated-investigations-statistics"></a>Statistiques des enquêtes automatisées

Cette vignette affiche les statistiques relatives aux investigations automatisées au cours des sept derniers jours. Il indique le nombre d’enquêtes terminées, le nombre d’enquêtes corrigées avec succès, le temps d’attente moyen nécessaire au lancement d’une enquête, le temps moyen nécessaire pour corriger une alerte, le nombre d’alertes examinées et le nombre d’heures d’automatisation enregistrées à partir d’une enquête manuelle classique. 

:::image type="content" source="images/atp-automated-investigations-statistics.png" alt-text="Statistiques sur les enquêtes automatisées" lightbox="images/atp-automated-investigations-statistics.png":::

Vous pouvez cliquer sur **Investigations automatisées**, **Investigations corrigées** et **Alertes examinées** pour accéder à la page **Investigations** , filtrée par la catégorie appropriée. Cela vous permet de voir une répartition détaillée des investigations dans le contexte.

## <a name="users-at-risk"></a>Utilisateurs à risque

La vignette affiche une liste de comptes d’utilisateurs avec les alertes les plus actives et le nombre d’alertes vues sur les alertes élevées, moyennes ou faibles. 

:::image type="content" source="images/atp-users-at-risk.png" alt-text="Page Utilisateurs à risque" lightbox="images/atp-users-at-risk.png":::

Cliquez sur le compte d’utilisateur pour afficher des détails sur le compte d’utilisateur. Pour plus d’informations, consultez [Examiner un compte d’utilisateur](investigate-user.md).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Comprendre le portail Microsoft Defender pour point de terminaison](use.md)
- [Vue d’ensemble du portail](portal-overview.md)
- [Afficher le tableau de bord Gestion des vulnérabilités Microsoft Defender](tvm-dashboard-insights.md)
- [Afficher le tableau de bord Analyse des menaces et prendre les mesures d’atténuation recommandées](threat-analytics.md)
