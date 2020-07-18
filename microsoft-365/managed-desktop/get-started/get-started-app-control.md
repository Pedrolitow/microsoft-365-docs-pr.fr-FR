---
title: Prise en main du contrôle d’application
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 12df7b074019ea47f2e293b71c6b0b25fe46f66f
ms.sourcegitcommit: 63887d742c59cc660fc85537b335e98a9dc66fbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2020
ms.locfileid: "45170694"
---
# <a name="get-started-with-app-control"></a>Prise en main du contrôle d’application

Avant d’activer le contrôle d’application dans votre environnement, veillez à consulter et à comprendre [Comment Microsoft Managed Desktop l’implémente](../service-description/app-control.md) , ainsi que vos rôles et responsabilités.

Microsoft Managed Desktop simplifie le contrôle des applications en prenant en charge les aspects les plus délicats de l’obtention d’une stratégie de base sécurisée. Vos administrateurs informatiques doivent toujours tester vos applications dans l’anneau de test et consulter les journaux pour rechercher des erreurs ou des avertissements. Si une application a besoin d’une exemption, vous pouvez classer une requête ou l’opération de bureau géré Microsoft peut, en fonction de qui la détecte au préalable.

## <a name="initial-deployment-of-apps"></a>Déploiement initial d’applications

Lorsque vous déployez pour la première fois des applications, le bureau géré Microsoft doit évaluer son comportement actuel. Les étapes exactes d’activation du contrôle d’application varient selon que des appareils ont déjà été déployés dans votre environnement.

### <a name="devices-already-in-use"></a>Appareils déjà utilisés

Si au moins un périphérique de bureau géré Microsoft est déjà utilisé, procédez comme suit :

1. Ouvrez un ticket de service avec les opérations de bureau géré Microsoft qui demandent que nous activions le contrôle des applications. Les opérations déploient une [stratégie d’audit](../service-description/app-control.md#audit-policy) sur tous les appareils.
2. [Testez vos applications](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) pour déterminer si elles seraient bloquées. Si une application est bloquée, ouvrez une [demande de signataire](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer). 
3. Une fois que vous avez terminé le test (quel que soit le résultat), informez les opérations en notant les demandes de signataire en attente. Les opérations déploient progressivement des stratégies vers des groupes de déploiement suivant cette planification :

|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 3       |
|Larges     | Enforced        |  Jour 7       |

Vous pouvez toujours ouvrir une autre demande de service pour suspendre ou restaurer une partie de ce déploiement à tout moment pendant le déploiement.

### <a name="devices-not-yet-in-use"></a>Appareils qui ne sont pas encore utilisés

Si vous n’avez pas encore de périphériques en cours d’utilisation, ouvrez un ticket de service avec Microsoft Managed Desktop Operations demandant à activer le contrôle des applications. Les opérations déploient progressivement des stratégies vers des groupes de déploiement suivant cette planification :

|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 3       |
|Larges     | Enforced        |  Jour 7       |

Vous pouvez toujours ouvrir une autre demande de service pour suspendre ou restaurer une partie de ce déploiement à tout moment pendant le déploiement.

