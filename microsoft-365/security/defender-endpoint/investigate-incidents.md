---
title: Examiner les incidents dans Microsoft Defender pour point de terminaison
description: Consultez les alertes associées, gérez l’incident et consultez les métadonnées d’alerte pour vous aider à examiner un incident
keywords: examiner, incident, alertes, métadonnées, risque, source de détection, appareils affectés, modèles, corrélation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 0fed7977e9ce9c348831c03f693f0d507215c5af
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68636473"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>Examiner les incidents dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Examinez les incidents qui affectent votre réseau, comprenez ce qu’ils signifient et rassemblez des preuves pour les résoudre.

Lorsque vous examinez un incident, vous voyez :

- Détails de l’incident
- Commentaires et actions d’incident
- Onglets (alertes, appareils, investigations, preuves, graphique)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>Analyser les détails de l’incident

Cliquez sur un incident pour afficher le **volet Incident**. Sélectionnez **Ouvrir la page d’incident** pour afficher les détails de l’incident et les informations associées (alertes, appareils, investigations, preuves, graphique).

:::image type="content" source="images/atp-incident-details.png" alt-text="Détails d’un incident" lightbox="images/atp-incident-details.png":::

### <a name="alerts"></a>Alertes

Vous pouvez examiner les alertes et voir comment elles ont été liées dans un incident. Les alertes sont regroupées en incidents en fonction des raisons suivantes :

- Investigation automatisée : l’enquête automatisée a déclenché l’alerte liée lors de l’examen de l’alerte d’origine
- Caractéristiques des fichiers : les fichiers associés à l’alerte ont des caractéristiques similaires
- Association manuelle : un utilisateur a lié manuellement les alertes
- Délai d’expiration : les alertes ont été déclenchées sur le même appareil dans un délai donné
- Même fichier : les fichiers associés à l’alerte sont exactement les mêmes
- Même URL : l’URL qui a déclenché l’alerte est exactement la même

:::image type="content" source="images/atp-incidents-alerts-reason.png" alt-text="Onglet Alertes avec la page détails de l’incident montrant les raisons pour lesquelles les alertes ont été liées dans cet incident" lightbox="images/atp-incidents-alerts-reason.png":::

Vous pouvez également gérer une alerte et afficher les métadonnées d’alerte ainsi que d’autres informations. Pour plus d’informations, consultez [Examiner les alertes](investigate-alerts.md).

### <a name="devices"></a>Appareils

Vous pouvez également examiner les appareils qui font partie d’un incident donné ou y sont associés. Pour plus d’informations, consultez [Examiner les appareils](investigate-machines.md).

:::image type="content" source="images/atp-incident-device-tab.png" alt-text="Onglet Appareils dans la page détails de l’incident" lightbox="images/atp-incident-device-tab.png":::

### <a name="investigations"></a>Enquêtes

Sélectionnez **Investigations** pour voir toutes les investigations automatiques lancées par le système en réponse aux alertes d’incident.

:::image type="content" source="images/atp-incident-investigations-tab.png" alt-text="Onglet Investigations dans la page détails de l’incident" lightbox="images/atp-incident-investigations-tab.png":::

## <a name="going-through-the-evidence"></a>Passer en revue les preuves

Microsoft Defender pour point de terminaison examine automatiquement tous les événements pris en charge par les incidents et les entités suspectes dans les alertes, ce qui vous fournit une réponse automatique et des informations sur les fichiers, processus, services, etc. importants.

Chacune des entités analysées sera marquée comme infectée, corrigée ou suspecte.

:::image type="content" source="images/atp-incident-evidence-tab.png" alt-text="Onglet Preuve dans la page détails de l’incident" lightbox="images/atp-incident-evidence-tab.png":::

## <a name="visualizing-associated-cybersecurity-threats"></a>Visualisation des menaces de cybersécurité associées

Microsoft Defender pour point de terminaison agrège les informations sur les menaces dans un incident afin que vous puissiez voir les modèles et les corrélations provenant de différents points de données. Vous pouvez afficher cette corrélation via le graphique des incidents.

### <a name="incident-graph"></a>Graphique des incidents

Le **graphe** raconte l’histoire de l’attaque contre la cybersécurité. Par exemple, il vous montre quel était le point d’entrée, quel indicateur de compromission ou d’activité a été observé sur quel appareil. Etc.

:::image type="content" source="images/atp-incident-graph-tab.png" alt-text="Graphique d’incident" lightbox="images/atp-incident-graph-tab.png":::

Vous pouvez cliquer sur les cercles du graphe d’incidents pour afficher les détails des fichiers malveillants, les détections de fichiers associées, le nombre d’instances dans le monde entier, le nombre d’instances observées dans votre organisation, le cas échéant.

:::image type="content" source="images/atp-incident-graph-details.png" alt-text="Page détails de l’incident" lightbox="images/atp-incident-graph-details.png":::

## <a name="related-topics"></a>Voir aussi

- [File d’attente des incidents](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Examiner les incidents dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [Gérer les incidents Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/manage-incidents)
