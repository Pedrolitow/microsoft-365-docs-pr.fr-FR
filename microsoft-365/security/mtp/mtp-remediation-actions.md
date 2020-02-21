---
title: Actions de correction dans les fonctionnalités d’enquête et de réponse automatisées dans Microsoft Threat Protection
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
ms.openlocfilehash: 73bb90a0537df8e6f23e4e0e50a748aebda3a487
ms.sourcegitcommit: 2f117a6fd27a097ca25afa933dd088b69d483974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "42175919"
---
# <a name="remediation-actions-in-automated-investigation-and-response-capabilities-in-microsoft-threat-protection"></a>Actions de correction dans les fonctionnalités d’enquête et de réponse automatisées dans Microsoft Threat Protection

**S’applique à :**
- Protection Microsoft contre les menaces

Les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection incluent certaines actions de correction. Certains types d’actions de correction sont pris sur les appareils, également appelés points de terminaison. D’autres actions de correction sont appliquées au contenu du courrier électronique.

Le tableau suivant récapitule les actions de correction actuellement prises en charge dans Microsoft Threat Protection : 

|Actions de correction des points de terminaison  |Actions de correction des e-mails  |
|---------|---------|
|Fichier de quarantaine<br/>Supprimer une clé de Registre<br/>Processus d’arrêt <br/>Arrêter le service <br/>Supprimer une clé de Registre <br/>Désactiver le pilote <br/>Supprimer une tâche planifiée.      |Supprimer (récupération possible) le courrier ou des clusters<br/>Bloquer l’URL (heure du clic)<br/>Désactiver le transfert de courrier externe          |

Les actions de correction, qu’elles soient en attente d’approbation ou qui sont déjà terminées, peuvent être affichées dans le [Centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).

## <a name="next-steps"></a>Étapes suivantes

- [Approuver ou refuser les actions liées à un examen et réponse automatisées](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir-actions)
- [En savoir plus sur le centre de notifications](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-action-center).
