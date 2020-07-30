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
ms.openlocfilehash: e0f76f6a232edeac350d08eeeb47188535ffe688
ms.sourcegitcommit: 1b83b6bcacb997324bc4be355deba6daf319591d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502936"
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

Les actions de correction, qu’elles soient en attente d’approbation ou qui sont déjà terminées, peuvent être affichées dans le [Centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).

## <a name="remediation-actions-follow-automated-investigations"></a>Les actions de correction suivent les enquêtes automatiques

Lorsqu’un examen automatisé se termine, un verdict est atteint pour chaque élément de preuve impliqué et des actions de correction sont identifiées. Dans certains cas, des actions de correction sont effectuées automatiquement. dans d’autres cas, les actions de correction attendent une approbation. Le tableau suivant répertorie les verdicts et résultats possibles :

|Verdict    |Domaine    |Résultats|
|------|------|------|
|Malveillant    |Appareils (points de terminaison)    |Les actions d'assainissement prennent automatiquement effet|
|Malveillant    |Contenu de l’e-mail (URL ou pièces jointes) | Les actions de correction recommandées sont en attente d’approbation|
|Suspect    |Appareils ou contenu de l’e-mail |Les actions de correction recommandées sont en attente d’approbation|
|Aucune menace détectée    |Appareils ou contenu de l’e-mail    |Aucune action de correction n’est nécessaire|

[Examiner une action en attente dans le centre de notifications](mtp-autoir-actions.md#review-a-pending-action-in-the-action-center)

> [!TIP]
> Si vous pensez qu’un message a été manqué ou incorrectement détecté par les fonctionnalités d’analyse et de réponse automatiques dans Microsoft Threat Protection, faites-le nous savoir. [Signalez les faux positifs/négatifs](mtp-autoir-report-false-positives-negatives.md).

## <a name="next-steps"></a>Étapes suivantes

- [Approuver ou rejeter des actions](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir-actions)

- [En savoir plus sur le centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).
