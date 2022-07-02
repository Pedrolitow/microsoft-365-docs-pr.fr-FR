---
title: Examiner les alertes dans Microsoft Defender pour point de terminaison
description: Passez en revue les informations d’alerte, y compris un récit d’alerte visualisé et des détails pour chaque étape de la chaîne.
keywords: incidents, incidents, machines, appareils, utilisateurs, alertes, alertes, investigation, graphe, preuves
ms.prod: m365-security
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.date: 5/1/2020
ms.technology: mde
ms.openlocfilehash: 76503c180dfdd2314254efc9315235c0802ab7f8
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607527"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Examiner les alertes dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

La page d’alerte dans Microsoft Defender pour point de terminaison fournit un contexte complet à l’alerte, en combinant les signaux d’attaque et les alertes liés à l’alerte sélectionnée, pour construire une histoire d’alerte détaillée.

Triez, examinez et prenez rapidement des mesures efficaces sur les alertes qui affectent votre organisation. Comprendre pourquoi ils ont été déclenchés et leur impact à partir d’un seul emplacement. Pour en savoir plus, consultez cette vue d’ensemble.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Prise en main d’une alerte

Si vous sélectionnez le nom d’une alerte dans Defender pour point de terminaison, vous accédez à sa page d’alerte. Dans la page d’alerte, toutes les informations sont affichées dans le contexte de l’alerte sélectionnée. Chaque page d’alerte se compose de 4 sections :

1. **Le titre de l’alerte** affiche le nom de l’alerte et est là pour vous rappeler quelle alerte a démarré votre enquête actuelle, quel que soit ce que vous avez sélectionné sur la page.
2. [**Les ressources affectées**](#review-affected-assets) répertorient les cartes des appareils et des utilisateurs affectés par cette alerte qui peuvent être cliqués pour plus d’informations et d’actions.
3. **L’article d’alerte** affiche toutes les entités liées à l’alerte, interconnectées par une arborescence. L’alerte dans le titre sera celle qui sera mise en évidence lorsque vous accédez pour la première fois à la page de votre alerte sélectionnée. Les entités de l’article d’alerte sont extensibles et cliquables, pour fournir des informations supplémentaires et accélérer la réponse en vous permettant d’effectuer des actions directement dans le contexte de la page d’alerte. Utilisez l’article d’alerte pour démarrer votre enquête. Découvrez comment [examiner les alertes dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. Le **volet d’informations** affiche d’abord les détails de l’alerte sélectionnée, avec les détails et les actions associés à cette alerte. Si vous sélectionnez l’une des ressources ou entités affectées dans l’article d’alerte, le volet d’informations change pour fournir des informations contextuelles et des actions pour l’objet sélectionné.

Notez l’état de détection de votre alerte.

- Empêché : la tentative d’action suspecte a été évitée. Par exemple, un fichier n’a pas été écrit sur le disque ou exécuté.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Page montrant la prévention d’une menace" lightbox="images/detstat-prevented.png":::

- Bloqué : le comportement suspect a été exécuté, puis bloqué. Par exemple, un processus a été exécuté, mais comme il a par la suite présenté des comportements suspects, le processus a été arrêté.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Page montrant le blocage d’une menace" lightbox="images/detstat-blocked.png":::

- Détecté : une attaque a été détectée et est peut-être toujours active.

  :::image type="content" source="images/detstat-detected.png" alt-text="Page montrant la détection d’une menace" lightbox="images/detstat-detected.png":::

Vous pouvez ensuite également consulter *les détails de l’enquête automatisée* dans le volet d’informations de votre alerte, pour voir quelles actions ont déjà été effectuées, ainsi que lire la description de l’alerte pour les actions recommandées.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Volet d’informations avec la description de l’alerte et les sections d’investigation automatique mises en évidence" lightbox="images/alert-air-and-alert-description.png":::

D’autres informations disponibles dans le volet d’informations lorsque l’alerte s’ouvre incluent les techniques MITRE, la source et des détails contextuels supplémentaires.

> [!NOTE]
> Si vous voyez un état *d’alerte de type d’alerte non pris en charge* , cela signifie que les fonctionnalités d’investigation automatisée ne peuvent pas récupérer cette alerte pour exécuter une investigation automatisée. Toutefois, vous pouvez [examiner ces alertes manuellement](../defender/investigate-incidents.md#alerts).

## <a name="review-affected-assets"></a>Passer en revue les ressources affectées

La sélection d’un appareil ou d’une carte utilisateur dans les sections des ressources affectées passe aux détails de l’appareil ou de l’utilisateur dans le volet d’informations.

- **Pour les appareils**, le volet d’informations affiche des informations sur l’appareil lui-même, telles que domaine, système d’exploitation et ADRESSE IP. Les alertes actives et les utilisateurs connectés sur cet appareil sont également disponibles. Vous pouvez agir immédiatement en isolant l’appareil, en limitant l’exécution de l’application ou en exécutant une analyse antivirus. Vous pouvez également collecter un package d’investigation, lancer une enquête automatisée ou accéder à la page de l’appareil pour effectuer une enquête du point de vue de l’appareil.

   :::image type="content" source="images/device-page-details.png" alt-text="Volet d’informations lorsqu’un appareil est sélectionné" lightbox="images/device-page-details.png":::

- **Pour les utilisateurs**, le volet d’informations affiche des informations détaillées sur l’utilisateur, telles que le nom SAM et le SID de l’utilisateur, ainsi que les types d’ouverture de session effectués par cet utilisateur, ainsi que les alertes et incidents qui lui sont associés. Vous pouvez sélectionner *Ouvrir la page utilisateur* pour poursuivre l’investigation du point de vue de cet utilisateur.

   :::image type="content" source="images/user-page-details.png" alt-text="Volet d’informations lorsqu’un utilisateur est sélectionné" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente des incidents](view-incidents-queue.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
