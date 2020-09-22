---
title: Examen et réponses automatisés dans Protection Microsoft contre les menaces
description: Obtenir une vue d’ensemble des fonctionnalités d’analyse et de réponse automatisées, également appelées auto-réparation, dans Microsoft Threat Protection
keywords: automatisation, examen, alerte, déclenchement, action, correction, auto-réparation
search.appverid: met150
ms.prod: microsoft-365-enterprise
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
ms.topic: conceptual
ms.custom: autoir
ms.date: 09/16/2020
ms.reviewer: evaldm, isco
ms.openlocfilehash: 2131af5e35aa0cf9f236940d2b4aaa2bed85190a
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48199780"
---
# <a name="automated-investigation-and-response-in-microsoft-threat-protection"></a>Examen et réponses automatisés dans Protection Microsoft contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

À mesure que des alertes de sécurité sont déclenchées, c’est à votre équipe chargée des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. La hiérarchisation et l’examen des alertes peuvent prendre beaucoup de temps, en particulier lorsque de nouvelles alertes continuent d’arriver pendant qu’un examen est en cours. Les équipes en charge des opérations de sécurité peuvent être submergées par le volume des menaces qu’elles doivent gérer. Les fonctionnalités d’analyse et de réponse automatisées, avec auto-réparation, dans Microsoft Threat Protection peuvent vous aider.

Regardez la vidéo suivante pour voir le fonctionnement de la réparation automatique :

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4BzwB]

Dans Microsoft Threat Protection, l’analyse et la réponse automatisées avec des fonctionnalités d’autoréparation fonctionnent sur vos appareils, le contenu & le courrier électronique et les identités. La protection de Microsoft contre les menaces rassemble les fonctionnalités suivantes : 
- [Recherche et correction automatisées dans la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [Recherche et réponse automatisées dans Office 365 protection avancée contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)
- [Détection de menaces avancées Azure](https://docs.microsoft.com/azure/security/fundamentals/threat-detection)
- [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
 
Cet article décrit le fonctionnement de l’instruction et de la réponse automatisées. Pour configurer ces fonctionnalités, consultez la rubrique [configure Automated Investigation and Response Capabilities in Microsoft Threat Protection](mtp-configure-auto-investigation-response.md).

## <a name="your-virtual-analyst"></a>Votre analyste virtuel

Imaginez un analyste virtuel au sein de votre équipe de sécurité de niveau 1/2. L’analyste virtuel est fidèle aux étapes recommandées par les opérations de sécurité pour examiner et corriger les menaces. L’assistant virtuel peut fonctionner 24h/24, 7j/7, avec une capacité illimitée et une charge considérable d’examens et de correction des menaces. Un assistant virtuel pourrait considérablement réduire le temps de réponse, libérant ainsi l’équipe en charge des opérations de sécurité pour d’autres projets stratégiques importants. Si ce scénario ressemble à science fiction, ce n’est pas le cas. Un tel analyste virtuel fait partie de votre suite Microsoft Threat Protection, et son nom est une *enquête et une réponse automatisées*.

L’analyse et la réponse automatisées permettent à votre équipe d’opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et les incidents de sécurité. Grâce à l’analyse et à la réponse automatisées, vous pouvez réduire le coût de traitement des activités d’enquête et de correction et tirer le meilleur parti de votre suite de protection contre les menaces. l’analyse et la réponse automatisées aident votre équipe chargée des opérations sur la sécurité à :

1. déterminer si une menace nécessite une action ;
2. effectuer (ou recommander) les actions de correction nécessaires ;
3. déterminer des examens supplémentaires qui doivent avoir lieu ; et
4. répéter le processus autant de fois que nécessaire pour d’autres alertes.

## <a name="the-automated-investigation-process"></a>Processus d’examen automatisé

**Alerte** > **incident** > **examen automatisé** > **verdict** > **action de correction**

Une alerte déclenchée crée un incident, qui peut lancer une enquête automatisée. Cet examen peut donner lieu à une ou plusieurs actions de correction. Dans Protection Microsoft contre les menaces, chaque examen automatisé met en corrélation les signaux entre Azure - Protection avancée contre les menaces (Azure ATP), Microsoft Defender - Protection avancée contre les menaces (Microsoft Defender DAV) et Office 365 - Protection avancée contre les menaces (Office 365 DAV), comme décrit dans le tableau suivant : 

|Entités |Services de protection contre les menaces  |
|---------|---------|
|Appareils (également appelés points de terminaison)     |[Microsoft Defender - PACM](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)<br/>[Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) |      
|Contenu de l’e-mail (fichiers et messages dans les boîtes aux lettres)     |[Office 365 – Protection avancée contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)         |

Chaque enquête génère des verdicts (*malveillants*, *suspects*ou *aucune menace détectée*) pour chaque preuve examinée. Selon le type de menace et le verdict résultant, les actions de correction se produisent automatiquement ou après approbation de l’équipe des opérations de sécurité de votre organisation. Les actions en attente et achevées sont répertoriées dans le [Centre de notifications](mtp-action-center.md).

Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité suspecte est détectée ailleurs, l’examen automatisée s’étend pour inclure cette entité, et un manuel de sécurité général s’exécute. 

> [!NOTE]
> Toutes les alertes ne déclenchent pas une enquête automatisée, et toutes les recherches ne génèrent pas de mesures correctives automatisées ; tout cela dépend de la configuration de l’analyse et de la réponse automatisées pour votre organisation. Voir [configurer les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection](mtp-configure-auto-investigation-response.md).


## <a name="next-steps"></a>Étapes suivantes

- [Consultez les conditions préalables pour une enquête et une réponse automatisées dans Microsoft Threat Protection](mtp-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-threat-protection)
- [Configurer une enquête et une réponse automatisées pour votre organisation](mtp-configure-auto-investigation-response.md)
- [En savoir plus sur le centre de notifications](mtp-action-center.md).
