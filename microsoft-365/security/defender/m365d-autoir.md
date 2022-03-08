---
title: Enquête et réponse automatisées dans Microsoft 365 Defender
description: Obtenez une vue d’ensemble des fonctionnalités automatisées d’examen et de réponse, également appelées auto-ressource, dans Microsoft 365 Defender
keywords: automatisé, examen, alerte, déclencheur, action, correction, auto-réparation
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
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 180599007a47fe9cfa9ae68d6647f7494dd2f410
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314264"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Enquête et réponse automatisées dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Si votre organisation utilise [Microsoft 365 Defender](microsoft-365-defender.md), votre équipe des opérations de sécurité reçoit une alerte dans le portail Microsoft 365 Defender chaque fois qu’une activité ou un artefact malveillant ou suspect est détecté. Étant donné le flux de menaces qui peut s’écouler sans fin, les équipes de sécurité doivent souvent relever le défi de traiter le volume élevé d’alertes. Heureusement, Microsoft 365 Defender inclut des fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent aider votre équipe des opérations de sécurité à gérer les menaces plus efficacement et efficacement.

Cet article fournit une vue d’ensemble d’AIR et inclut des liens vers les étapes suivantes et des ressources supplémentaires.

> [!TIP]
> Voulez-vous faire l'expérience de Microsoft 365 Defender? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).

## <a name="how-automated-investigation-and-self-healing-works"></a>Fonctionnement de l’examen automatisé et de la auto-ressource

Lorsque des alertes de sécurité sont déclenchées, c’est à votre équipe des opérations de sécurité d’examiner ces alertes et de prendre les mesures nécessaires pour protéger votre organisation. La hiérarchisation et l’examen des alertes peuvent prendre beaucoup de temps, en particulier lorsque de nouvelles alertes continuent d’arriver pendant qu’un examen est en cours. Les équipes en charge des opérations de sécurité peuvent être submergées par le volume des menaces qu’elles doivent gérer. Les fonctionnalités automatisées d’examen et de réponse, avec auto-Microsoft 365 Defender aideront.

Regardez la vidéo suivante pour voir comment fonctionne la auto-ressource : <p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Dans Microsoft 365 Defender, l’examen et la réponse automatisés avec des fonctionnalités de auto-ressourcement fonctionnent sur vos appareils, votre & contenu et vos identités.
 
> [!TIP]
> Cet article décrit le fonctionnement de l’examen et de la réponse automatisés. Pour configurer ces fonctionnalités, voir Configurer les fonctionnalités d’investigation et de réponse automatisées [dans Microsoft 365 Defender](m365d-configure-auto-investigation-response.md).

## <a name="your-own-virtual-analyst"></a>Votre propre analyste virtuel

Imagine un analyste virtuel dans votre équipe des opérations de sécurité de niveau 1 ou 2. L’analyste virtuel est fidèle aux étapes recommandées par les opérations de sécurité pour examiner et corriger les menaces. L’analyste virtuel peut travailler 24 heures sur 24, 7 jours sur 7, avec une capacité illimitée et prendre en charge une charge importante d’examens et de correction des menaces. Un tel analyste virtuel pourrait réduire considérablement le temps de réponse, libérant ainsi votre équipe des opérations de sécurité pour d’autres menaces importantes ou projets stratégiques. Si ce scénario ressemble à une science fictive, ce n’est pas le cas ! Un analyste virtuel de ce type fait partie de Microsoft 365 Defender suite, et son nom est *examen et réponse automatisés*.

Les fonctionnalités d’examen et de réponse automatisées permettent à votre équipe en charge des opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et les incidents de sécurité. Grâce à l’examen et à la réponse automatisés, vous pouvez réduire le coût de traitement des activités d’examen et de réponse et utiliser au mieux votre suite de protection contre les menaces. Les fonctionnalités d’examen et de réponse automatisées aident votre équipe en matière d’opérations de sécurité en :

1. Déterminer si une menace nécessite une action.
2. Suivre (ou recommander) les actions de correction nécessaires.
3. Déterminer si et quelles autres enquêtes doivent se produire.
4. Répéter le processus autant de fois que nécessaire pour d’autres alertes.

## <a name="the-automated-investigation-process"></a>Processus d’examen automatisé

Une alerte crée un incident, qui peut démarrer une enquête automatisée. L’enquête automatisée entraîne un verdict pour chaque élément de preuve. Les verdicts peuvent être :
- *Malveillant*
- *Suspect* 
- *Aucune menace détectée* 

Les actions de correction pour les entités malveillantes ou suspectes sont identifiées. Voici quelques exemples d’actions de correction :

- Envoi d’un fichier en quarantaine
- Arrêt d’un processus
- Isolation d’un appareil
- Blocage d’une URL 
- Autres actions

Pour plus d’informations, voir [actions de correction dans Microsoft 365 Defender](m365d-remediation-actions.md).

Selon la [façon dont les](m365d-configure-auto-investigation-response.md) fonctionnalités d’examen et de réponse automatisées sont configurées pour votre organisation, des mesures correctives sont prises automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Toutes les actions, en attente ou terminées, sont répertoriées dans le centre [de actions](m365d-action-center.md).

Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité affectée est vue ailleurs, l’enquête automatisée étend son étendue pour inclure cette entité, et le processus d’examen se répète. 

Dans Microsoft 365 Defender, chaque enquête automatisée met en corrélation les signaux entre Microsoft Defender pour l’identité, Microsoft Defender pour le point de terminaison et Microsoft Defender pour Office 365, comme résumé dans le tableau suivant : 

|Entités |Services de protection contre les menaces  |
|:---------|:---------|
|Appareils (également appelés points de terminaison ou ordinateurs) |[Defender pour point de terminaison](../defender-endpoint/automated-investigations.md) |      
|Utilisateurs Active Directory locaux, comportement des entités et activités     |[Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp) |      
|Contenu du courrier électronique (messages électroniques qui peuvent contenir des fichiers et des URL)     |[Defender pour Office 365](../office-365-security/defender-for-office-365.md) |

> [!NOTE]
> Toutes les alertes ne déclenchent pas une enquête automatisée, et toutes les enquêtes n’entraînent pas des actions de correction automatisées. Cela dépend de la façon dont l’examen et la réponse automatisés sont configurés pour votre organisation. Voir [Configurer les fonctionnalités d’examen et de réponse automatisées](m365d-configure-auto-investigation-response.md).

## <a name="viewing-a-list-of-investigations"></a>Affichage d’une liste d’enquêtes

Pour afficher les enquêtes, consultez la page **Incidents** . Sélectionnez un incident, puis l’onglet **Investigations** . Pour plus d’informations, voir [Détails et résultats d’une enquête automatisée](m365d-autoir-results.md).

## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Utilisez ce module d’apprentissage de Microsoft Learn pour comprendre comment Microsoft 365 Defender automatique pour l’examen et la réponse aux incidents.

|Formation :|Automatiser la réparation automatique avec Microsoft 365 Defender|
|---|---|
|![Automatisez la auto-ressource à l’Microsoft 365 Defender de formation.](../../media/m365d-autoir/m365-defender-auto-self-healing.svg)| Microsoft 365 Defender l’IA pour automatiser la correction des incidents, ce qui permet à votre équipe des opérations de sécurité de traiter les menaces plus efficacement. <p> 11 min - 5 unités |

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/defender-self-healing/)

## <a name="next-steps"></a>Étapes suivantes

- [Voir les conditions préalables à l’examen et à la réponse automatisés](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Configurer l’examen et la réponse automatisés pour votre organisation](m365d-configure-auto-investigation-response.md)
- [En savoir plus sur le centre de notifications](m365d-action-center.md).
