---
title: Incidents dans Microsoft 365 Defender
description: Enquêter sur les incidents détectés entre les appareils, les utilisateurs et les boîtes aux lettres.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: e1e028f7b58df07eccf945b3a79012b4ea12366d
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861622"
---
# <a name="incidents-in-microsoft-365-defender"></a>Incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Un incident dans Microsoft 365 Defender est une collection d'alertes corrélées et de données associées qui constitue l'histoire d'une attaque. 

Les applications et services Microsoft 365 créent des alertes lorsqu'ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques pour différents types d'entités, telles que les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client. 

Étant donné que l'agrégation des alertes individuelles pour obtenir des informations sur une attaque peut être difficile et chronophage, Microsoft 365 Defender regroupe automatiquement les alertes et leurs informations associées dans un incident.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Comment Microsoft 365 Defender met en corrélation les événements des entités avec un incident":::

Regardez cette courte présentation des incidents dans Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Le regroupement d'alertes associées dans un incident vous offre une vue complète d'une attaque. Par exemple, vous pouvez voir :

- L'endroit où l'attaque a commencé.
- Quelles tactiques ont été utilisées .
- Jusqu'où l'attaque est passée dans votre client.
- Étendue de l'attaque, telle que le nombre d'appareils, d'utilisateurs et de boîtes aux lettres touchés. 
- Toutes les données associées à l'attaque.

[S'il est](m365d-enable.md)activé, Microsoft 365 Defender peut automatiquement examiner et résoudre les alertes par le biais de l'automatisation et de l'intelligence artificielle. Vous pouvez également effectuer des étapes de correction supplémentaires pour résoudre l'attaque. 

## <a name="incidents-and-alerts-in-the-microsoft-365-security-center"></a>Incidents et alertes dans le Centre de sécurité Microsoft 365

Vous gérez les incidents à partir **d'incidents & alertes** > Incidents dans le lancement rapide du Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le Centre de sécurité Microsoft 365":::

La sélection d'un nom d'incident affiche un résumé de l'incident et donne accès aux onglets avec des informations supplémentaires.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Exemple de page Résumé d'un incident dans le Centre de sécurité Microsoft 365":::

Les onglets supplémentaires pour un incident sont les suivants :

- Alertes 

  Toutes les alertes liées à l'incident et leurs informations.

- Appareils

  Tous les appareils identifiés comme faisant partie ou liés à l'incident.

- Utilisateurs

  Tous les utilisateurs identifiés comme faisant partie ou associés à l'incident.

- Boîtes aux lettres

  Toutes les boîtes aux lettres identifiées comme faisant partie ou liées à l'incident.

- Examens

  Toutes les enquêtes automatisées déclenchées par des alertes dans l'incident.

- Preuve et réponse

  Tous les événements pris en charge et entités suspectes dans les alertes dans l'incident.

Voici la relation entre un incident et ses données et les onglets d'un incident dans le Centre de sécurité Microsoft 365.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relation d'un incident et de ses données avec les onglets d'un incident dans le Centre de sécurité Microsoft 365":::

## <a name="next-step"></a>Étape suivante

La file d'attente des incidents de la page **Incidents** répertorie les incidents les plus récents. À partir de là, vous pouvez :

- Voir quels incidents doivent [être](incident-queue.md) hiérarchisés en fonction de la gravité et d'autres facteurs. 
- Effectuer une [investigation d'un](investigate-incidents.md) incident.
- [Gérer les incidents,](manage-incidents.md)ce qui inclut le changement de nom, leur affectation, la classification et l'ajout de balises pour votre flux de travail de gestion des incidents.
