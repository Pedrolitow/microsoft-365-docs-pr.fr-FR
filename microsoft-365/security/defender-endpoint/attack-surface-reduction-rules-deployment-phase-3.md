---
title: 'Phase 3 de déploiement des règles asr : implémenter'
description: Fournit des conseils pour implémenter le déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.reviewer: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 6556389ecef571626c1927aca9341945f113d150
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61217406"
---
# <a name="attack-surface-reduction-rules-deployment-phase-3-implement"></a>Phase 3 de déploiement des règles de réduction de la surface d’attaque : implémenter

La phase d’implémentation déplace l’anneau du test à l’état fonctionnel.

> [!div class="mx-imgBorder"]
> ![Étapes d’implémentation des règles asr](images/asr-rules-implementation-steps.png)

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Étape 1 : Transition des règles de la asr de l’audit au blocage

1. Une fois toutes les exclusions déterminées en mode audit, commencez à définir certaines règles asr en mode « bloquer », en commençant par la règle qui a le moins d’événements déclenchés. Voir « Activer [les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)».
2. Consultez la page de rapports dans le portail Microsoft 365 Defender' ; voir le rapport sur la protection contre les [menaces dans Microsoft Defender for Endpoint](threat-protection-reports.md). Examinez également les commentaires de vos champions de la asr.
3. Affinez les exclusions ou créez de nouvelles exclusions selon les besoins.
4. Revenir aux règles problématiques vers Audit.

  >[!Note]
  >Pour les règles problématiques (règles créant trop de bruit), il est préférable de créer des exclusions plutôt que de désactiver les règles ou de revenir à Audit. Vous devez déterminer ce qui est le mieux pour votre environnement.

  >[!Tip]
  >Lorsque ce paramètre est disponible, tirez parti du paramètre Du mode Avertissement dans les règles pour limiter les perturbations. L’activation des règles asr en mode Avertissement vous permet de capturer les événements déclenchés et d’afficher leurs perturbations potentielles, sans bloquer l’accès des utilisateurs finaux. En savoir plus : [mode d’avertissement pour les utilisateurs.](attack-surface-reduction.md#warn-mode-for-users)

### <a name="how-does-warn-mode-work"></a>Comment fonctionne le mode Avertissement ?

Le mode Avertissement est en réalité une instruction bloquer, mais avec la possibilité pour l’utilisateur de « débloquer » les exécutions suivantes du flux ou de l’application donné. Le mode Avertissement se débloque sur une combinaison d’appareils, d’utilisateurs, de fichiers et de processus. Les informations du mode avertissement sont stockées localement et ont une durée de 24 heures.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Étape 2 : développer le déploiement pour sonner n + 1

Lorsque vous êtes certain d’avoir correctement configuré les règles asr pour l’anneau 1, vous pouvez élargir l’étendue de votre déploiement à l’anneau suivant (anneau n + 1).

Le processus de déploiement, étapes 1 à 3, est essentiellement le même pour chaque anneau suivant :

1. Règles de test dans Audit
2. Passer en revue les événements d’audit déclenchés par la asr dans le portail Microsoft 365 Defender de recherche
3. Créer des exclusions
4. Révision : affiner, ajouter ou supprimer des exclusions si nécessaire
5. Définir des règles sur « bloquer »
6. Examinez la page de rapports dans le portail Microsoft 365 Defender web.
7. Créez des exclusions.
8. Désactivez les règles problématiques ou revenir à Audit.

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiements

[Guide de déploiement des règles asr : vue d’ensemble](attack-surface-reduction-rules-deployment.md)

[Phase de déploiement des règles asr 1 : planifier](attack-surface-reduction-rules-deployment-phase-1.md)

[Phase de déploiement des règles asr 2 : test](attack-surface-reduction-rules-deployment-phase-2.md)

[Phase de déploiement des règles asr 4 : opérationnel](attack-surface-reduction-rules-deployment-phase-4.md)
