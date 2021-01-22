---
title: Examen et réponse automatisés dans Microsoft 365 Defender
description: Obtenir une vue d’ensemble des fonctionnalités d’examen et de réponse automatisées, également appelées auto-ressource, dans Microsoft 365 Defender
keywords: automatisé, examen, alerte, déclencheur, action, correction, auto-réparation
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.date: 12/09/2020
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 905455e4cd70485e099f8005b5f8876b1a5d9caf
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930329"
---
# <a name="automated-investigation-and-response-in-microsoft-365-defender"></a>Examen et réponse automatisés dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous souhaitez découvrir Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](https://aka.ms/mtp-trial-lab) ou exécuter votre projet pilote en [production.](https://aka.ms/m365d-pilotplaybook)
>

## <a name="how-automated-investigation-and-self-healing-works"></a>Fonctionnement de l’examen automatisé et de la auto-ressource

Lorsque des alertes de sécurité sont déclenchées, c’est à votre équipe des opérations de sécurité d’examiner ces alertes et de prendre les mesures nécessaires pour protéger votre organisation. La hiérarchisation et l’examen des alertes peuvent prendre beaucoup de temps, en particulier lorsque de nouvelles alertes continuent d’arriver pendant qu’un examen est en cours. Les équipes en charge des opérations de sécurité peuvent être submergées par le volume des menaces qu’elles doivent gérer. Les fonctionnalités automatisées d’examen et de réponse, avec auto-ressource, dans Microsoft 365 Defender peuvent vous aider.

Regardez la vidéo suivante pour voir comment fonctionne la auto-ressource :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Dans Microsoft 365 Defender, l’examen et la réponse automatisés grâce à des fonctionnalités de auto-ressource fonctionnent sur vos appareils, vos & de messagerie et vos identités.
 
> [!TIP]
> Cet article décrit le fonctionnement de l’examen et de la réponse automatisés. Pour configurer ces fonctionnalités, voir Configurer les fonctionnalités d’investigation et de réponse [automatisées dans Microsoft 365 Defender.](mtp-configure-auto-investigation-response.md)

## <a name="your-own-virtual-analyst"></a>Votre propre analyste virtuel

Imaginez un analyste virtuel au sein de votre équipe de sécurité de niveau 1/2. L’analyste virtuel est fidèle aux étapes recommandées par les opérations de sécurité pour examiner et corriger les menaces. L’assistant virtuel peut fonctionner 24h/24, 7j/7, avec une capacité illimitée et une charge considérable d’examens et de correction des menaces. Un assistant virtuel pourrait considérablement réduire le temps de réponse, libérant ainsi l’équipe en charge des opérations de sécurité pour d’autres projets stratégiques importants. Si ce scénario ressemble à une science fictive, ce n’est pas le cas ! Cet analyste virtuel fait partie de votre suite Microsoft 365 Defender et son nom est examen et *réponse automatisés.*

L’examen et la réponse automatisés permettent à votre équipe en charge des opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et les incidents de sécurité. Grâce à l’examen et à la réponse automatisés, vous pouvez réduire le coût de traitement des activités d’examen et de correction et utiliser au mieux votre suite de protection contre les menaces. L’examen et la réponse automatisés aident votre équipe en matière d’opérations de sécurité en :

1. déterminer si une menace nécessite une action ;
2. effectuer (ou recommander) les actions de correction nécessaires ;
3. déterminer des examens supplémentaires qui doivent avoir lieu ; et
4. répéter le processus autant de fois que nécessaire pour d’autres alertes.

## <a name="the-automated-investigation-process"></a>Processus d’examen automatisé

**Alerte** > **incident** > **examen automatisé** > **verdict** > **action de correction**

Une alerte déclenchée crée un incident, qui peut démarrer une enquête automatisée. Cet examen peut donner lieu à une ou plusieurs actions de correction. Dans Microsoft 365 Defender, chaque enquête automatisée met en corrélation les signaux entre Microsoft Defender pour l’identité, Microsoft Defender pour le point de terminaison et Defender pour Office 365, comme résumé dans le tableau suivant : 

|Entités |Services de protection contre les menaces  |
|---------|---------|
|Appareils (également appelés points de terminaison)     |[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)<br/>[Microsoft Defender pour Identity](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) |      
|Contenu de l’e-mail (fichiers et messages dans les boîtes aux lettres)     |[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)         |

Chaque enquête génère des verdicts *(malveillants,* suspects ou aucune menace *trouvée)* pour chaque élément de preuve examiné. Selon le type de menace et le verdict qui en résulte, les actions de correction se produisent automatiquement ou après approbation par l’équipe des opérations de sécurité de votre organisation. Les actions en attente et achevées sont répertoriées dans le [Centre de notifications](mtp-action-center.md).

Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité suspecte est détectée ailleurs, l’examen automatisée s’étend pour inclure cette entité, et un manuel de sécurité général s’exécute. 

> [!NOTE]
> Toutes les alertes ne déclenchent pas une enquête automatisée, et toutes les enquêtes n’entraînent pas des actions de correction automatisées ; Tout dépend de la façon dont l’examen et la réponse automatisés sont configurés pour votre organisation. Voir Configurer les fonctionnalités d’investigation et de réponse [automatisées dans Microsoft 365 Defender.](mtp-configure-auto-investigation-response.md)


## <a name="next-steps"></a>Étapes suivantes

- [Consultez les conditions préalables à l’examen et à la réponse automatisés dans Microsoft 365 Defender](mtp-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
- [Configurer l’examen et la réponse automatisés pour votre organisation](mtp-configure-auto-investigation-response.md)
- [En savoir plus sur le centre de notifications](mtp-action-center.md).
