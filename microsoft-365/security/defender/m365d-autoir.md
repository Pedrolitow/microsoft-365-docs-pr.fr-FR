---
title: Enquête et réponse automatisées dans Microsoft 365 Defender
description: Obtenez une vue d’ensemble des fonctionnalités automatisées d’investigation et de réponse, également appelées auto-guérison, dans Microsoft 365 Defender
keywords: automatisé, investigation, alerte, déclencheur, action, correction, auto-guérison
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 07/19/2022
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: deb0a7be8dcf359c901d714006ea3b46862586fb
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67050741"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Enquête et réponse automatisées dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Si votre organisation utilise [Microsoft 365 Defender](microsoft-365-defender.md), votre équipe chargée des opérations de sécurité reçoit une alerte dans le portail Microsoft 365 Defender chaque fois qu’une activité ou un artefact malveillant ou suspect est détecté. Étant donné le flux apparemment sans fin de menaces qui peuvent entrer, les équipes de sécurité sont souvent confrontées au défi de résoudre le volume élevé d’alertes. Heureusement, Microsoft 365 Defender inclut des fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent aider votre équipe chargée des opérations de sécurité à traiter les menaces plus efficacement et plus efficacement.

Cet article fournit une vue d’ensemble d’AIR et inclut des liens vers les étapes suivantes et des ressources supplémentaires.

## <a name="how-automated-investigation-and-self-healing-works"></a>Fonctionnement de l’investigation automatisée et de l’auto-guérison

À mesure que les alertes de sécurité sont déclenchées, c’est à votre équipe des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. La hiérarchisation et l’examen des alertes peuvent prendre beaucoup de temps, en particulier lorsque de nouvelles alertes continuent d’arriver pendant qu’un examen est en cours. Les équipes en charge des opérations de sécurité peuvent être submergées par le volume des menaces qu’elles doivent gérer. Les fonctionnalités automatisées d’investigation et de réponse, avec auto-guérison, dans Microsoft 365 Defender peuvent vous aider.

Regardez la vidéo suivante pour voir comment fonctionne l’auto-guérison : <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Dans Microsoft 365 Defender, l’investigation et la réponse automatisées avec des fonctionnalités d’auto-réparation fonctionnent sur vos appareils, le contenu & par e-mail et les identités.
 
> [!TIP]
> Cet article décrit le fonctionnement de l’investigation et de la réponse automatisées. Pour configurer ces fonctionnalités, consultez [Configurer les fonctionnalités d’investigation et de réponse automatisées dans Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Votre propre analyste virtuel

Imaginez avoir un analyste virtuel dans votre équipe des opérations de sécurité de niveau 1 ou 2. L’analyste virtuel est fidèle aux étapes recommandées par les opérations de sécurité pour examiner et corriger les menaces. L’analyste virtuel peut travailler 24 h/24, 7 j/7, avec une capacité illimitée, et prendre une charge importante d’investigations et de correction des menaces. Un tel analyste virtuel pourrait réduire considérablement le temps de réponse, libérant votre équipe des opérations de sécurité pour d’autres menaces importantes ou des projets stratégiques. Si ce scénario ressemble à de la science-fiction, ce n’est pas le cas ! Un tel analyste virtuel fait partie de votre suite Microsoft 365 Defender, et son nom est *une investigation et une réponse automatisées*.

Les fonctionnalités d’investigation et de réponse automatisées permettent à votre équipe des opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et les incidents de sécurité. Grâce à l’examen et à la réponse automatisés, vous pouvez réduire les coûts liés aux activités d’investigation et de réponse et tirer le meilleur parti de votre suite de protection contre les menaces. Les fonctionnalités d’investigation et de réponse automatisées aident votre équipe des opérations de sécurité à :

1. Déterminer si une menace nécessite une action.
2. Suivre (ou recommander) les actions de correction nécessaires.
3. Déterminer si et quelles autres enquêtes doivent se produire.
4. Répéter le processus autant de fois que nécessaire pour d’autres alertes.

## <a name="the-automated-investigation-process"></a>Processus d’examen automatisé

Une alerte crée un incident, qui peut démarrer une investigation automatisée. L’enquête automatisée donne lieu à un verdict pour chaque élément de preuve. Les verdicts peuvent être :
- *Malveillant*
- *Suspect* 
- *Aucune menace détectée* 

Les actions de correction pour les entités malveillantes ou suspectes sont identifiées. Voici quelques exemples d’actions de correction :

- Envoi d’un fichier en quarantaine
- Arrêt d’un processus
- Isolation d’un appareil
- Blocage d’une URL 
- Autres actions

Pour plus d’informations, consultez [Actions de correction dans Microsoft 365 Defender](m365d-remediation-actions.md).

Selon la [façon dont les fonctionnalités d’investigation et de réponse automatisées sont configurées](m365d-configure-auto-investigation-response.md) pour votre organisation, les actions de correction sont effectuées automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Toutes les actions, qu’elles soient en attente ou terminées, sont répertoriées dans le [Centre d’actions](m365d-action-center.md).

Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité affectée est vue ailleurs, l’enquête automatisée étend son étendue pour inclure cette entité, et le processus d’examen se répète. 

Dans Microsoft 365 Defender, chaque investigation automatisée met en corrélation les signaux entre Microsoft Defender pour Identity, Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365, comme résumé dans le tableau suivant : 

|Entités |Services de protection contre les menaces  |
|:---------|:---------|
|Appareils (également appelés points de terminaison ou machines) |[Defender pour point de terminaison](../defender-endpoint/automated-investigations.md) |      
|Utilisateurs Active Directory locaux, comportement d’entité et activités     |[Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp) |      
|Email contenu (messages électroniques pouvant contenir des fichiers et des URL)     |[Defender pour Office 365](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Toutes les alertes ne déclenchent pas une investigation automatisée, et toutes les investigations n’entraînent pas des actions de correction automatisées. Cela dépend de la façon dont l’investigation et la réponse automatisées sont configurées pour votre organisation. Consultez [Configurer les fonctionnalités d’investigation et de réponse automatisées](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Affichage d’une liste d’investigations

Pour afficher les enquêtes, accédez à la page **Incidents** . Sélectionnez un incident, puis sélectionnez l’onglet **Investigations** . Pour en savoir plus, consultez [Détails et résultats d’une enquête automatisée](m365d-autoir-results.md).

## <a name="automated-investigation--response-card"></a>Carte de réponse & d’investigation automatisée 

La nouvelle carte de réponse d’examen automatisé & est disponible dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Cette nouvelle carte permet de voir le nombre total d’actions de correction disponibles. La carte donne également une vue d’ensemble de toutes les alertes et du temps d’approbation requis pour chaque alerte.

:::image type="content" source="../../media/automated-investigation-response-card.png" alt-text="Capture d’écran montrant la carte de réponse & d’investigation automatisée.":::

À l’aide de la carte de réponse & d’enquête automatisée, votre équipe chargée des opérations de sécurité peut accéder rapidement au Centre d’actions en sélectionnant le lien **Approuver dans le Centre d’actions** , puis en effectuant les actions appropriées. La carte permet à votre équipe des opérations de sécurité de gérer plus efficacement les actions en attente d’approbation. 


## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Utilisez ce module d’apprentissage de Microsoft Learn pour comprendre comment Microsoft 365 Defender utilise l’auto-réparation automatisée pour l’investigation et la réponse aux incidents.

|Formation :|Automatiser la réparation automatique avec Microsoft 365 Defender|
|---|---|
|![Automatiser l’auto-guérison avec Microsoft 365 Defender icône d’entraînement.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender utilise l’IA pour automatiser la correction des incidents, ce qui aide votre équipe chargée des opérations de sécurité à résoudre les menaces de manière plus efficace et efficace. <p> 11 min - 5 unités |

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Prochaines étapes

- [Consultez les prérequis pour une investigation et une réponse automatisées](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Configurer l’investigation et la réponse automatisées pour votre organisation](m365d-configure-auto-investigation-response.md)
- [En savoir plus sur le centre de notifications](m365d-action-center.md).
