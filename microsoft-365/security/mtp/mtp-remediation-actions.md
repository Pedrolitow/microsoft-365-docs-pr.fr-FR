---
title: Actions de correction dans Microsoft 365 Defender
description: Obtenir une vue d’ensemble des actions de correction qui suivent des enquêtes automatisées dans Microsoft 365 Defender
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
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.date: 12/09/2020
ms.reviewer: evaldm, isco
ms.openlocfilehash: 9e489e3b0100aa138b11d4bfb4ccc8048a2113f4
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49683294"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Actions de correction dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

## <a name="remediation-actions"></a>Actions de correction

Pendant et après une enquête automatisée dans Microsoft 365 Defender, les actions de correction sont identifiées pour les éléments malveillants ou suspects. Certains types d’actions de correction sont pris sur les appareils, également appelés points de terminaison. D’autres actions de correction sont appliquées au contenu du courrier électronique. Analyses automatiques terminées après que les actions de correction ont été effectuées, approuvées ou rejetées.

> [!IMPORTANT]
> Les actions correctives effectuées automatiquement ou uniquement en cas d’approbation dépendent de certains paramètres, tels que le mode d’automatisation des niveaux. Pour en savoir plus, consultez les articles suivants :
> - [Configurer vos fonctionnalités d’analyse et de réponse automatisées dans Microsoft 365 Defender](mtp-configure-auto-investigation-response.md)
> - [Comment les menaces sont corrigées sur les appareils](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
> - [Menaces et actions correctives sur le courrier électronique & le contenu collaboratif](https://docs.microsoft.com/microsoft-365/security/office-365-security/air-remediation-actions#threats-and-remediation-actions)

Le tableau suivant récapitule les actions de correction actuellement prises en charge dans Microsoft 365 Defender : 

|Actions de correction du périphérique (point de terminaison)  |Actions de correction des e-mails  |
|---------|---------|
|-Créer un package d’enquête <br/>-Isoler le périphérique (cette action peut être inachevée)<br/>-Ordinateur débarquement <br/>-Exécution du code de la version <br/>-Libérer de la quarantaine <br/>-Exemple de requête <br/>-Restreindre l’exécution du code (cette action peut être terminée) <br/>-Exécuter l’analyse antivirus <br/>-Arrêter et mettre en quarantaine      |-Bloquer l’URL (temps de clic)<br/>-Supprimer les messages électroniques ou les clusters par suppression douce<br/>-Courrier en quarantaine<br/>-Mettre en quarantaine une pièce jointe de courrier électronique<br/>-Désactiver le transfert de courrier externe          |

Les actions de correction, qu’elles soient en attente d’approbation ou déjà terminées, peuvent être affichées dans le [Centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Actions de correction qui suivent des enquêtes automatisées

Lorsqu’une enquête automatisée se termine, un verdict est atteint pour chaque élément de preuve impliqué. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, des actions de correction sont effectuées automatiquement. dans d’autres cas, les actions de correction attendent une approbation. Tout dépend de la configuration de l’analyse [et de la réponse automatisées](mtp-configure-auto-investigation-response.md).

Le tableau suivant répertorie les verdicts et résultats possibles :

| Verdict    | Domaine    | Résultats|
|------|------|------|
| Malveillant    | Appareils (points de terminaison)    | Les actions de correction sont prises automatiquement (en supposant que les [groupes d’appareils](mtp-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) de votre organisation sont configurés pour effectuer **automatiquement des** corrections de menace).|
| Malveillant    | Contenu de l’e-mail (URL ou pièces jointes) | Les actions de correction recommandées sont en attente d’approbation|
| Suspect    | Appareils ou contenu de l’e-mail | Les actions de correction recommandées sont en attente d’approbation|
| Aucune menace détectée    | Appareils ou contenu de l’e-mail    | Aucune action de correction n’est nécessaire|


## <a name="remediation-actions-that-are-taken-manually"></a>Actions correctives prises manuellement

En plus des actions de correction qui suivent des enquêtes automatiques, votre équipe des opérations de sécurité peut prendre certaines actions correctives manuellement. Il s’agit des actions suivantes :

- Action manuelle du périphérique, telle que l’isolation de l’appareil ou la mise en quarantaine du fichier.
- Action de messagerie manuelle, telle que la suppression logicielle de messages électroniques. 
- Action de [chasse avancée](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) sur les appareils ou le courrier électronique.
- Action de l' [Explorateur](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer) sur le contenu du courrier électronique, comme le transfert du courrier électronique vers le courrier indésirable, la suppression logicielle ou la suppression définitive de courrier électronique.
- Action de [réponse dynamique](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/live-response) manuelle, telle que la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche planifiée.
- Action de réponse en direct avec [Microsoft Defender pour les API de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/management-apis#microsoft-defender-for-endpoint-apis), telles que l’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier. 

## <a name="next-steps"></a>Étapes suivantes

- [Visiter le Centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center)
- [Approuver ou refuser des actions en attente](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir-actions)
- [Gérer les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées](mtp-autoir-report-false-positives-negatives.md)
