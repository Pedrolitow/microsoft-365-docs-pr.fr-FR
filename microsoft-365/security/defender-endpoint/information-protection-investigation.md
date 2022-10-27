---
title: Utiliser Microsoft Defender pour point de terminaison étiquettes de confidentialité pour protéger vos données et hiérarchiser la réponse aux incidents de sécurité
description: Découvrez comment utiliser les étiquettes de confidentialité Defender pour point de terminaison pour protéger, hiérarchiser et examiner les incidents qui impliquent des incidents de perte de données, dlp et de sécurité.
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
- ContentEngagementFY23
- tier2 - EngageScoreSep2022
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: cdb1d9eb306fd472690cc756fdbe0a1b412d7ab8
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68729938"
---
# <a name="microsoft-defender-for-endpoint-sensitivity-labels-protect-and-prioritize-incident-response"></a>Microsoft Defender pour point de terminaison étiquettes de confidentialité protègent et hiérarchisent la réponse aux incidents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Un cycle de vie des menaces persistantes (ou APT) avancé classique implique une exfiltration de données, c’est-à-dire le point auquel les données *sont extraites* de l’organisation. Dans ces situations, les étiquettes de confidentialité peuvent indiquer aux opérations de sécurité par où commencer en indiquant quelles données sont les plus prioritaires à protéger.

Defender pour point de terminaison permet de simplifier la hiérarchisation des incidents de sécurité avec l’utilisation d’étiquettes de confidentialité. Par exemple, les étiquettes de confidentialité identifient rapidement les incidents qui peuvent impliquer des appareils contenant des informations sensibles (telles que des informations confidentielles).

Voici comment utiliser les étiquettes de confidentialité dans Defender pour point de terminaison.

## <a name="investigate-incidents-that-involve-sensitive-data-on-devices-with-defender-for-endpoint"></a>Examiner les incidents qui impliquent des données sensibles sur des appareils avec Defender pour point de terminaison

Découvrez comment utiliser des étiquettes de confidentialité des données pour hiérarchiser l’investigation des incidents.

> [!NOTE]
> Les étiquettes sont détectées pour Windows 10, version 1809 ou une version ultérieure et Windows 11.

1. Dans Microsoft 365 Defender portail, sélectionnez **Incidents & alertes** \> **Incidents**.

2. Faites défiler vers la droite pour afficher la colonne **Sensibilité des données** . Cette colonne reflète les étiquettes de confidentialité qui ont été observées sur les appareils liés aux incidents, indiquant si les fichiers sensibles peuvent être affectés par l’incident.

   :::image type="content" source="images/data-sensitivity-column.png" alt-text="Option Hautement confidentiel dans la colonne de confidentialité des données" lightbox="images/data-sensitivity-column.png":::

    Vous pouvez également filtrer en fonction **de la sensibilité des données**

    :::image type="content" source="images/data-sensitivity-filter.png" alt-text="Filtre de confidentialité des données" lightbox="images/data-sensitivity-filter.png":::

3. Ouvrez la page de l’incident pour approfondir l’examen.

   :::image type="content" source="images/incident-page.png" alt-text="Détails de la page d’incident" lightbox="images/incident-page.png":::

4. Sélectionnez l’onglet **Appareils** pour identifier les appareils stockant des fichiers avec des étiquettes de confidentialité.

   :::image type="content" source="images/investigate-devices-tab.png" alt-text="Onglet Appareil" lightbox="images/investigate-devices-tab.png":::

5. Sélectionnez les appareils qui stockent des données sensibles et parcourez la chronologie pour identifier les fichiers susceptibles d’être affectés, puis prenez les mesures appropriées pour vous assurer que les données sont protégées.

   Vous pouvez affiner les événements affichés dans la chronologie de l’appareil en recherchant des étiquettes de confidentialité des données. Cette opération affiche uniquement les événements associés aux fichiers dont le nom d’étiquette est indiqué.

   :::image type="content" source="images/machine-timeline-labels.png" alt-text="Chronologie de l’appareil avec des résultats de recherche réduits en fonction de l’étiquette" lightbox="images/machine-timeline-labels.png":::

> [!TIP]
> Ces points de données sont également exposés via « DeviceFileEvents » dans la chasse avancée, ce qui permet aux requêtes avancées et à la détection de planification de prendre en compte les étiquettes de confidentialité et l’état de protection des fichiers.

## <a name="related-information-about-sensitivity-labels"></a>Informations connexes sur les étiquettes de confidentialité

- [En savoir plus sur les étiquettes de confidentialité dans Office 365](../../compliance/sensitivity-labels.md)
- [Apprendre à appliquer une étiquette de confidentialité à l’intérieur de la messagerie ou d’Office](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
- [Découvrez comment utiliser des étiquettes de confidentialité comme condition lors de l’application de la protection contre la perte de données](../../compliance/dlp-sensitivity-label-as-condition.md)