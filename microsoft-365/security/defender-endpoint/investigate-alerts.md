---
title: Examiner les alertes Microsoft Defender pour point de terminaison
description: Utilisez les options d’investigation pour obtenir des détails sur les alertes qui affectent votre réseau, ce qu’elles signifient et comment les résoudre.
keywords: examiner, examiner, appareils, appareil, file d’attente d’alertes, tableau de bord, adresse IP, fichier, envoyer, soumissions, analyse approfondie, chronologie, recherche, domaine, URL, ADRESSE IP
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
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.subservice: mde
ms.openlocfilehash: a2bc1b44cc49e2ded0a3079360436df2880b2f58
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67522959"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>Examiner les alertes dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

Examinez les alertes qui affectent votre réseau, comprenez ce qu’elles signifient et comment les résoudre.

Sélectionnez une alerte dans la file d’attente d’alertes pour accéder à la page d’alerte. Cette vue contient le titre de l’alerte, les ressources affectées, le volet côté détails et l’histoire de l’alerte.

À partir de la page d’alerte, commencez votre investigation en sélectionnant les ressources affectées ou l’une des entités sous l’arborescence d’histoires d’alerte. Le volet d’informations se remplit automatiquement avec des informations supplémentaires sur ce que vous avez sélectionné. Pour voir le type d’informations que vous pouvez afficher ici, lisez [Les alertes de révision dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>Examiner à l’aide de l’article d’alerte

L’histoire de l’alerte explique pourquoi l’alerte a été déclenchée, les événements connexes qui se sont produits avant et après, ainsi que d’autres entités associées.

Les entités sont cliquables et chaque entité qui n’est pas une alerte peut être développée à l’aide de l’icône développer située à droite de la carte de cette entité. L’entité en focus est indiquée par une bande bleue sur le côté gauche de la carte de cette entité, avec l’alerte dans le titre étant en cours de focus au début.

Développez les entités pour afficher les détails en un clin d’œil. La sélection d’une entité change le contexte du volet d’informations sur cette entité et vous permet d’examiner d’autres informations, ainsi que de gérer cette entité. La sélection *...* à droite de la carte d’entité révélera toutes les actions disponibles pour cette entité. Ces mêmes actions apparaissent dans le volet d’informations lorsque cette entité est en focus.

> [!NOTE]
> La section d’histoire des alertes peut contenir plusieurs alertes, avec des alertes supplémentaires liées à l’arborescence d’exécution qui s’affiche avant ou après l’alerte que vous avez sélectionnée.

:::image type="content" source="images/alert-story-tree.png" alt-text="une histoire d’alerte avec une alerte au focus et quelques cartes développées" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>Effectuer une action à partir du volet d’informations

Une fois que vous avez sélectionné une entité d’intérêt, le volet d’informations change pour afficher des informations sur le type d’entité sélectionné, des informations historiques lorsqu’elle est disponible et offre des contrôles pour **prendre des mesures** sur cette entité directement à partir de la page d’alerte.

Une fois que vous avez terminé l’examen, revenez à l’alerte avec laquelle vous avez commencé, marquez l’état de l’alerte comme **résolu** et classifiez-la comme **alerte False** ou **True**. La classification des alertes permet d’optimiser cette fonctionnalité pour fournir plus d’alertes vraies et moins de fausses alertes.

Si vous la classifiez comme une véritable alerte, vous pouvez également sélectionner une détermination, comme illustré dans l’image ci-dessous.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="Volet d’informations avec une alerte résolue et la liste déroulante de détermination développée" lightbox="images/alert-details-resolved-true.png":::

Si vous rencontrez une fausse alerte avec une application métier, créez une règle de suppression pour éviter ce type d’alerte à l’avenir.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="Actions et classification dans le volet d’informations avec la règle de suppression mise en surbrillance" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> Si vous rencontrez des problèmes non décrits ci-dessus, utilisez le 🙂 bouton pour fournir des commentaires ou ouvrir un ticket de support.

## <a name="related-topics"></a>Voir aussi

- [Afficher et organiser la file d’attente d’alertes Microsoft Defender pour point de terminaison](alerts-queue.md)
- [Gérer les alertes Microsoft Defender pour point de terminaison](manage-alerts.md)
- [Examiner un fichier associé à une alerte Defender pour point de terminaison](investigate-files.md)
- [Examiner les appareils dans la liste Des appareils Defender pour point de terminaison](investigate-machines.md)
- [Examiner une adresse IP associée à une alerte Defender pour point de terminaison](investigate-ip.md)
- [Examiner un domaine associé à une alerte Defender pour point de terminaison](investigate-domain.md)
- [Examiner un compte d’utilisateur dans Defender pour point de terminaison](investigate-user.md)
