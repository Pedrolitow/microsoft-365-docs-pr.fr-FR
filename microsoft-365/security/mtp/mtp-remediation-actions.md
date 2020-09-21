---
title: Actions de correction suite à des enquêtes automatisées dans Microsoft Threat Protection
description: Obtenir une vue d’ensemble des actions de correction qui suivent des enquêtes automatisées dans Microsoft Threat Protection
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
ms.date: 09/16/2020
ms.reviewer: evaldm, isco
ms.openlocfilehash: 205809bac14cc82e850ea1cbc0349256432bfe68
ms.sourcegitcommit: 7c0873d2a804f17697844fb13f1a100fabce86c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "47962584"
---
# <a name="remediation-actions-following-automated-investigations-in-microsoft-threat-protection"></a>Actions de correction suite à des enquêtes automatisées dans Microsoft Threat Protection

**S’applique à :**
- Protection Microsoft contre les menaces


## <a name="remediation-actions"></a>Actions de correction

Pendant et après une enquête automatisée dans Microsoft Threat Protection, les actions de correction sont identifiées pour les éléments malveillants ou suspects. Certains types d’actions de correction sont pris sur les appareils, également appelés points de terminaison. D’autres actions de correction sont appliquées au contenu du courrier électronique. Analyses automatiques terminées après que les actions de correction ont été effectuées, approuvées ou rejetées.

Le tableau suivant récapitule les actions de correction actuellement prises en charge dans Microsoft Threat Protection : 

|Actions de correction du périphérique (point de terminaison)  |Actions de correction des e-mails  |
|---------|---------|
|-Créer un package d’enquête <br/>-Isoler le périphérique (cette action peut être inachevée)<br/>-Ordinateur débarquement <br/>-Exécution du code de la version <br/>-Libérer de la quarantaine <br/>-Exemple de requête <br/>-Restreindre l’exécution du code (cette action peut être terminée) <br/>-Exécuter l’analyse antivirus <br/>-Arrêter et mettre en quarantaine      |-Bloquer l’URL (temps de clic)<br/>-Supprimer les messages électroniques ou les clusters par suppression douce<br/>-Courrier en quarantaine<br/>-Mettre en quarantaine une pièce jointe de courrier électronique<br/>-Désactiver le transfert de courrier externe          |

Les actions de correction, qu’elles soient en attente d’approbation ou déjà terminées, peuvent être affichées dans le [Centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).

## <a name="remediation-actions-follow-automated-investigations"></a>Les actions de correction suivent les enquêtes automatiques

Lorsqu’une enquête automatisée se termine, un verdict est atteint pour chaque élément de preuve impliqué. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, des actions de correction sont effectuées automatiquement. dans d’autres cas, les actions de correction attendent une approbation. Tout dépend de la configuration de l’analyse [et de la réponse automatisées](mtp-configure-auto-investigation-response.md).

Le tableau suivant répertorie les verdicts et résultats possibles :

|Verdict    |Domaine    |Résultats|
|------|------|------|
|Malveillant    |Appareils (points de terminaison)    |Les actions de correction sont prises automatiquement (en supposant que les [groupes d’appareils](mtp-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) de votre organisation sont configurés pour effectuer **automatiquement des**corrections de menace).|
|Malveillant    |Contenu de l’e-mail (URL ou pièces jointes) | Les actions de correction recommandées sont en attente d’approbation|
|Suspect    |Appareils ou contenu de l’e-mail |Les actions de correction recommandées sont en attente d’approbation|
|Aucune menace détectée    |Appareils ou contenu de l’e-mail    |Aucune action de correction n’est nécessaire|

> [!IMPORTANT]
> La prise automatique ou non des actions de correction dépend de certains paramètres, tels que les stratégies de groupe d’appareils de votre organisation. Pour en savoir plus, consultez les articles suivants :
> - [Configurer les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection](mtp-configure-auto-investigation-response.md)
> - [Comment les menaces sont corrigées sur les appareils](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

## <a name="next-steps"></a>Étapes suivantes

- [Visiter le centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center)
- [Approuver ou refuser des actions en attente](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir-actions)
- [Gérer les faux positifs/négatifs dans les fonctionnalités d’analyse et de réponse automatisées](mtp-autoir-report-false-positives-negatives.md)
