---
title: Actions de correction dans Microsoft 365 Defender
description: Obtenir une vue d’ensemble des actions de correction qui suivent des enquêtes automatisées dans Microsoft 365 Defender
keywords: automatisation, examen, alerte, déclencheur, action, correction
search.appverid: met150
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
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: c8d3838194c25ba49b2611dc355b21e228291b01
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180940"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Actions de correction dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pendant et après un examen automatisé dans Microsoft 365 Defender, des actions de correction sont identifiées pour les éléments malveillants ou suspects. Certains types d’actions de correction sont prises sur les appareils, également appelés points de terminaison. D’autres mesures correctives sont prises sur le contenu du courrier électronique. Les enquêtes automatisées se terminent après que des mesures correctives ont été prises, approuvées ou rejetées.

> [!IMPORTANT]
> Le fait que des mesures correctives soient prises automatiquement ou uniquement après approbation dépend de certains paramètres, tels que la façon dont les niveaux d’automatisation sont mis en place. Pour en savoir plus, consultez les articles suivants :
> - [Configurez vos fonctionnalités d’examen et de réponse automatisées dans Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Comment les menaces sont corrigés sur les appareils](../defender-endpoint/automated-investigations.md)
> - [Menaces et actions de correction sur le contenu de collaboration & courrier électronique](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Le tableau suivant récapitule les actions de correction actuellement prises en charge dans Microsoft 365 Defender. 

|Actions de correction de l’appareil (point de terminaison)  |Actions de correction des e-mails  |
|:---------|:---------|
|- Collecter le package d’examen <br/>- Isoler l’appareil (cette action peut être annulée)<br/>- Appareil hors-carte <br/>- Exécution du code de publication <br/>- Sortir de la quarantaine <br/>- Exemple de requête <br/>- Restreindre l’exécution du code (cette action peut être annulée) <br/>- Exécuter une analyse antivirus <br/>- Arrêter et mettre en quarantaine      |- Bloquer l’URL (heure du clic)<br/>- Suppression de messages électroniques ou de clusters de suppression (soft)<br/>- E-mail de mise en quarantaine<br/>- Mettre en quarantaine une pièce jointe d’un e-mail<br/>- Désactiver le forwarding de courrier externe          |

Les actions de correction, qu’elles soient en attente d’approbation ou déjà terminées, peuvent être vues dans le centre [de correction.](m365d-action-center.md)

## <a name="remediation-actions-that-follow-automated-investigations"></a>Actions de correction qui suivent des enquêtes automatisées

Lorsqu’une enquête automatisée se termine, un verdict est atteint pour chaque élément de preuve impliqué. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, des actions de correction sont effectuées automatiquement. dans d’autres cas, les actions de correction attendent une approbation. Tout dépend de la façon dont [l’examen et la réponse automatisés sont configurés.](m365d-configure-auto-investigation-response.md)

Le tableau suivant répertorie les verdicts et résultats possibles :

| Verdict    | Entités affectées    | Résultats|
|------|------|------|
| Malveillant    | Appareils (points de terminaison)    | Des mesures correctives sont prises automatiquement [](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) (en supposant que les groupes d’appareils de votre organisation sont entièrement corrects - corriger **les menaces automatiquement)**|
| Malveillant    | Contenu de l’e-mail (URL ou pièces jointes) | Les actions de correction recommandées sont en attente d’approbation|
| Suspect    | Appareils ou contenu de l’e-mail | Les actions de correction recommandées sont en attente d’approbation|
| Aucune menace détectée    | Appareils ou contenu de l’e-mail    | Aucune action de correction n’est nécessaire|


## <a name="remediation-actions-that-are-taken-manually"></a>Mesures correctives prises manuellement

En plus des actions de correction qui suivent des enquêtes automatisées, votre équipe des opérations de sécurité peut prendre certaines mesures correctives manuellement. Elles incluent notamment les éléments suivants :

- Action manuelle de l’appareil, telle que l’isolation de l’appareil ou la mise en quarantaine des fichiers
- Action de messagerie manuelle, telle que la suppression possible des messages électroniques 
- [Action de recherche](../defender-endpoint/advanced-hunting-overview.md) avancée sur les appareils ou les e-mails
- [Action de](../office-365-security/threat-explorer.md) l’Explorateur sur le contenu du courrier électronique, telle que le déplacement du courrier électronique vers le courrier indésirable, la suppression possible ou la suppression de courriers électroniques durs
- Action [de réponse en direct](/windows/security/threat-protection/microsoft-defender-atp/live-response) manuelle, telle que la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche programmée
- Action de réponse en direct [avec les API Microsoft Defender pour point](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis)de terminaison, telle que l’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier

## <a name="next-steps"></a>Étapes suivantes

- [Visiter le Centre de notifications](m365d-action-center.md)
- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
- [Corriger les faux positifs ou les faux négatifs](m365d-autoir-report-false-positives-negatives.md)
