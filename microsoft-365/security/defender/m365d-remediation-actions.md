---
title: Actions de correction dans Microsoft 365 Defender
description: Obtenir une vue d’ensemble des actions de correction qui suivent des investigations automatisées dans Microsoft 365 Defender
keywords: automatisation, examen, alerte, déclencheur, action, correction
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.openlocfilehash: 6e1648b8c2e02eb17635597026e48535c4bfa402
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479419"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Actions de correction dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Pendant et après une enquête automatisée dans Microsoft 365 Defender, des actions de correction sont identifiées pour les éléments malveillants ou suspects. Certains types d’actions de correction sont effectuées sur les appareils, également appelés points de terminaison. D’autres actions de correction sont effectuées sur les identités, les comptes et le contenu des e-mails. Les investigations automatisées se terminent après que des actions de correction ont été prises, approuvées ou rejetées.

> [!IMPORTANT]
> La question de savoir si les actions de correction sont effectuées automatiquement ou uniquement après approbation dépend de certains paramètres, tels que les niveaux d’automatisation. Pour en savoir plus, consultez les articles suivants :
>
> - [Configurer vos fonctionnalités d’investigation et de réponse automatisées dans Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [Configurer des comptes d’action dans Microsoft Defender pour Identity](/defender-for-identity/manage-action-accounts)
> - [Comment les menaces sont corrigées sur les appareils](../defender-endpoint/automated-investigations.md)
> - [Menaces et actions de correction sur le contenu de collaboration & par e-mail](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Le tableau suivant récapitule les actions de correction actuellement prises en charge dans Microsoft 365 Defender.

|Actions de correction de l’appareil (point de terminaison)  |Actions de correction des e-mails  |Utilisateurs (comptes)  |
|:---------|:---------|----------|
|- Collecter le package d’investigation <br/>- Isoler l’appareil (cette action peut être annulée)<br/>- Machine hors-bord <br/>- Exécution du code de mise en production <br/>- Libération de la quarantaine <br/>- Exemple de requête <br/>- Restreindre l’exécution du code (cette action peut être annulée) <br/>- Exécuter une analyse antivirus <br/>- Arrêter et mettre en quarantaine <br/>- Contenir des appareils à partir du réseau     |- Bloquer l’URL (time-of-click)<br/>- Suppression réversible de messages électroniques ou de clusters<br/>- E-mail de mise en quarantaine<br/>- Mettre en quarantaine une pièce jointe<br/>- Désactiver le transfert de courrier externe          |- Désactiver l’utilisateur<br />- Réinitialiser le mot de passe utilisateur<br />- Confirmer que l’utilisateur est compromis          |

Les actions de correction, qu’elles soient en attente d’approbation ou déjà terminées, peuvent être affichées dans le [Centre d’actions](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>Actions de correction qui suivent les investigations automatisées

Une fois l’enquête automatisée terminée, un verdict est rendu pour chaque élément de preuve impliqué. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, des actions de correction sont effectuées automatiquement. dans d’autres cas, les actions de correction attendent une approbation. Tout dépend de la façon dont [l’investigation et la réponse automatisées sont configurées](m365d-configure-auto-investigation-response.md).

Le tableau suivant répertorie les verdicts et résultats possibles :

| Verdict    | Entités affectées    | Résultats|
|------|------|------|
| Malveillant    | Appareils (points de terminaison)    | Les actions de correction sont effectuées automatiquement (en supposant que les [groupes d’appareils](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) de votre organisation sont définis sur **Complet - corriger automatiquement les menaces**)|
| Compromis | Utilisateurs | Les actions d'assainissement prennent automatiquement effet |
| Malveillant    | Contenu de l’e-mail (URL ou pièces jointes) | Les actions de correction recommandées sont en attente d’approbation|
| Suspect    | Appareils ou contenu de l’e-mail | Les actions de correction recommandées sont en attente d’approbation|
| Aucune menace détectée    | Appareils ou contenu de l’e-mail    | Aucune action de correction n’est nécessaire|

## <a name="remediation-actions-that-are-taken-manually"></a>Actions de correction effectuées manuellement

En plus des actions de correction qui suivent des investigations automatisées, votre équipe des opérations de sécurité peut effectuer certaines actions de correction manuellement. Elles incluent notamment les éléments suivants :

- Action manuelle de l’appareil, telle que l’isolation de l’appareil ou la mise en quarantaine de fichiers
- Action de messagerie manuelle, telle que la suppression réversible des messages électroniques
- Action manuelle de l’utilisateur, telle que désactiver l’utilisateur ou réinitialiser le mot de passe utilisateur
- [Action de repérage avancée](../defender-endpoint/advanced-hunting-overview.md) sur les appareils, les utilisateurs ou les e-mails
- [Action de l’Explorateur](../office-365-security/threat-explorer.md) sur le contenu de l’e-mail, telle que le déplacement d’e-mails vers un courrier indésirable, la suppression réversible d’e-mails ou la suppression définitive d’e-mails
- Action de [réponse dynamique](/windows/security/threat-protection/microsoft-defender-atp/live-response) manuelle, telle que la suppression d’un fichier, l’arrêt d’un processus et la suppression d’une tâche planifiée
- Action de réponse en direct avec [des API Microsoft Defender pour point de terminaison](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis), telles que l’isolation d’un appareil, l’exécution d’une analyse antivirus et l’obtention d’informations sur un fichier

## <a name="next-steps"></a>Prochaines étapes

- [Visiter le Centre de notifications](m365d-action-center.md)
- [Afficher et gérer les actions de correction](m365d-autoir-actions.md)
- [Résoudre les faux positifs ou les faux négatifs](m365d-autoir-report-false-positives-negatives.md)
- [Contenir des appareils à partir du réseau](../defender-endpoint\respond-machine-alerts.md#contain-devices-from-the-network)
