---
title: Fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection
description: Obtenez une vue d’ensemble des fonctionnalités d’examen et réponses automatisés dans Protection Microsoft contre les menaces
keywords: automatisation, examen, alerte, déclencheur, action, correction
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
ms.openlocfilehash: 6ac6d74b027cc533f689c1d67c7fce246c73984f
ms.sourcegitcommit: 46644f9778bc70ab6d62783e0a1e60ba2eccc27f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "44166160"
---
# <a name="automated-investigation-and-response-air-capabilities-in-microsoft-threat-protection"></a>Fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection

**S’applique à :**
- Protection Microsoft contre les menaces

À mesure que des alertes de sécurité sont déclenchées, c’est à votre équipe chargée des opérations de sécurité d’examiner ces alertes et de prendre des mesures pour protéger votre organisation. La hiérarchisation et l’examen des alertes peuvent prendre beaucoup de temps, en particulier lorsque de nouvelles alertes continuent d’arriver pendant qu’un examen est en cours. Les équipes en charge des opérations de sécurité peuvent être submergées par le volume des menaces qu’elles doivent gérer. Les fonctionnalités d’analyse et de réponse automatisées de Microsoft Threat Protection peuvent vous aider. AIR est comme un analyste virtuel dans votre centre d’opérations sur la sécurité.

## <a name="your-virtual-analyst"></a>Votre analyste virtuel

Imaginez un analyste virtuel au sein de votre équipe de sécurité de niveau 1/2. L’analyste virtuel est fidèle aux étapes recommandées par les opérations de sécurité pour examiner et corriger les menaces. L’assistant virtuel peut fonctionner 24h/24, 7j/7, avec une capacité illimitée et une charge considérable d’examens et de correction des menaces. Un assistant virtuel pourrait considérablement réduire le temps de réponse, libérant ainsi l’équipe en charge des opérations de sécurité pour d’autres projets stratégiques importants. Si ce scénario ressemble à science fiction, ce n’est pas le cas. Cette analyste virtuel fait partie de votre suite Protection Microsoft contre les menaces, et son nom est *Examen et réponse automatisés* (AIR).

AIR permet à l’équipe en charge des opérations de sécurité d’augmenter considérablement la capacité de votre organisation à gérer les alertes et incidents de sécurité. AIR vous permet de réduire les coûts de gestion des activités d’examen et de correction et tirer le meilleur parti de votre suite de protection contre les menaces. AIR permet à vos équipes en charge des opérations de sécurité à :

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

> [!TIP]
> Si vous pensez qu’un message a été manqué ou incorrectement détecté par les fonctionnalités d’analyse et de réponse automatiques dans Microsoft Threat Protection, faites-le nous savoir. Découvrez [Comment signaler des faux positifs/négatifs dans les capacités d’inspection et de réponse automatiques de Microsoft Threat Protection](mtp-autoir-report-false-positives-negatives.md).

Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité suspecte est détectée ailleurs, l’examen automatisée s’étend pour inclure cette entité, et un manuel de sécurité général s’exécute. 

> [!NOTE]
> Toutes les alertes ne déclenchent pas un examen automatisé et tous les examens ne génèrent pas des actions de correction automatisées. tout dépend de la façon dont l’AIR est configuré pour votre organisation. 

## <a name="requirements-for-air-in-microsoft-threat-protection"></a>Configuration requise pour l’AIR dans la Protection Microsoft contre les menaces

| | |
|--|--|
|Conditions d’abonnement |Un des éléments suivants : <br/>-Microsoft 365 E5 <br/>-Microsoft 365 a5 <br/>-Microsoft 365 E5 sécurité<br/>-Microsoft 365 a5 Security<br/>-Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5<br/><br/>Consultez la rubrique [licences de protection contre les menaces Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites?#licensing-requirements).|
|Configuration réseau requise |- [Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) activé<br/>- [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) (MCAS) configuré<br/>- [MCAS intégré à Azure ATP](https://docs.microsoft.com/cloud-app-security/aatp-integration) |
|Configuration requise pour ordinateur Windows |-Windows 10, version 1709 ou ultérieure installé (voir [informations sur la version Windows 10](https://docs.microsoft.com/windows/release-information/)) avec les services de protection contre les menaces suivants configurés :<br/>- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) <br/>- [Antivirus Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) |
|Protection du contenu de messagerie et des fichiers Office |[Office 365 Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) configurée |
|Autorisations |-Pour configurer AIR, vous devez disposer du rôle Administrateur général ou Administrateur de Sécurité affecté dans Azure Active Directory ([https://portal.azure.com](https://portal.azure.com)) ou dans le Centre d’administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)).<br/><br/>- Pour utiliser le fonctionnalités de l’AIR, veuillez consulter [Autorisations requises pour les tâches du centre de notifications](mtp-action-center.md#required-permissions-for-action-center-tasks). |

## <a name="next-steps"></a>Étapes suivantes

- [Approuver ou refuser les actions liées à un examen et réponse automatisées](mtp-autoir-actions.md)
- [En savoir plus sur le centre de notifications](mtp-action-center.md).
