---
title: Utiliser des étiquettes de confidentialité pour hiérarchiser les réponses aux incidents
description: Découvrez comment utiliser des étiquettes de confidentialité pour hiérarchiser et examiner les incidents
keywords: informations, protection, données, perte, prévention, étiquettes, dlp, incident, examen, investigation
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
- tier2 - EngageScoreSep2022
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 5dcc47dde921eb2e8c94fbb38b828bfc2f1c2d5b
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68646746"
---
# <a name="use-sensitivity-labels-to-prioritize-incident-response"></a>Utiliser des étiquettes de confidentialité pour hiérarchiser les réponses aux incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Un cycle de vie des menaces persistantes avancées classique implique l’exfiltration des données. Dans un incident de sécurité, il est important d’avoir la possibilité de hiérarchiser les enquêtes où les fichiers sensibles peuvent être compromis afin que les données et les informations d’entreprise soient protégées.

Defender pour point de terminaison facilite considérablement la définition des priorités des incidents de sécurité avec l’utilisation d’étiquettes de confidentialité. Les étiquettes de confidentialité identifient rapidement les incidents qui peuvent impliquer des appareils avec des informations sensibles telles que des informations confidentielles.

## <a name="investigate-incidents-that-involve-sensitive-data"></a>Examiner les incidents impliquant des données sensibles

Découvrez comment utiliser des étiquettes de confidentialité des données pour hiérarchiser l’investigation des incidents.

> [!NOTE]
> Les étiquettes sont détectées pour Windows 10, version 1809 ou version ultérieure, et Windows 11.

1. Dans Microsoft 365 Defender portail, sélectionnez **Incidents & alertes** \> **Incidents**.

2. Faites défiler vers la droite pour afficher la colonne **de confidentialité des données** . Cette colonne reflète les étiquettes de confidentialité qui ont été observées sur les appareils liés aux incidents, indiquant si les fichiers sensibles peuvent être affectés par l’incident.

   :::image type="content" source="images/data-sensitivity-column.png" alt-text="Option Hautement confidentiel dans la colonne de confidentialité des données" lightbox="images/data-sensitivity-column.png":::

    Vous pouvez également filtrer en fonction **de la sensibilité des données**

    :::image type="content" source="images/data-sensitivity-filter.png" alt-text="Filtre de sensibilité des données" lightbox="images/data-sensitivity-filter.png":::

3. Ouvrez la page d’incident pour approfondir l’examen.

   :::image type="content" source="images/incident-page.png" alt-text="Détails de la page d’incident" lightbox="images/incident-page.png":::

4. Sélectionnez l’onglet **Appareils** pour identifier les appareils qui stockent des fichiers avec des étiquettes de confidentialité.

   :::image type="content" source="images/investigate-devices-tab.png" alt-text="Onglet Appareil" lightbox="images/investigate-devices-tab.png":::

5. Sélectionnez les appareils qui stockent des données sensibles et effectuez une recherche dans la chronologie pour identifier les fichiers susceptibles d’être affectés, puis prenez les mesures appropriées pour vous assurer que les données sont protégées.

   Vous pouvez affiner les événements affichés dans la chronologie de l’appareil en recherchant des étiquettes de confidentialité des données. Cette opération affiche uniquement les événements associés aux fichiers qui ont dit le nom de l’étiquette.

   :::image type="content" source="images/machine-timeline-labels.png" alt-text="Chronologie de l’appareil avec des résultats de recherche réduits en fonction de l’étiquette" lightbox="images/machine-timeline-labels.png":::

> [!TIP]
> Ces points de données sont également exposés par le biais de « DeviceFileEvents » dans la chasse avancée, ce qui permet aux requêtes avancées et à la détection de planification de prendre en compte les étiquettes de confidentialité et l’état de protection des fichiers.
