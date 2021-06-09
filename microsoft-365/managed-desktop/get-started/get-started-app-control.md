---
title: Prise en main du contrôle d’application
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 431e6cb3b8d7ab7e1dd317918fab4821889c7d4e
ms.sourcegitcommit: 583fd1ac1f385c58b93bda648907a1bd8e0a1950
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45430458"
---
# <a name="get-started-with-app-control"></a>Prise en main du contrôle d’application

Avant d’activer le contrôle d’application dans votre environnement, n’oubliez pas de passer en revue et de comprendre comment Bureau géré Microsoft l’implémente, ainsi que vos [rôles](../service-description/app-control.md) et responsabilités.

Bureau géré Microsoft simplifie le contrôle des applications en prenant en charge les aspects les plus complexes liés à l’obtention d’une stratégie de base sécurisée. Vos administrateurs informatiques doivent toujours tester vos applications dans l’anneau Test et consulter les journaux pour y trouver des avertissements ou des erreurs. Si une application a besoin d’une exemption, vous pouvez déposer une demande, ou Bureau géré Microsoft operation peut, selon qui la détecte en premier.

## <a name="initial-deployment-of-apps"></a>Déploiement initial des applications

Lorsque vous déployez des applications pour la première fois, Bureau géré Microsoft devez évaluer leur comportement actuel. Les étapes exactes d’activation du contrôle d’application varient selon que des appareils ont déjà été déployés dans votre environnement.

### <a name="devices-not-yet-in-use"></a>Appareils pas encore utilisés

Si vous n’avez pas encore d’appareils en cours d’utilisation, ouvrez un ticket de service avec Bureau géré Microsoft Operations demandant que nous ouvrez le contrôle d’application. Les opérations déploieront progressivement des stratégies dans des groupes de déploiement en suivant cette planification :

|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Jour 2       |
|Larges     | Enforced        |  Jour 3       |

Vous pouvez toujours ouvrir une autre demande de service pour suspendre ou revenir en arrière une partie de ce déploiement à tout moment pendant le déploiement.

### <a name="devices-already-in-use"></a>Appareils déjà utilisés

Si vous avez déjà au moins Bureau géré Microsoft appareil en cours d’utilisation, suivez les étapes suivantes :

1. Ouvrez un ticket de service avec Bureau géré Microsoft Operations demandant que nous ouvrez le contrôle d’application. Les opérations déploient une [stratégie d’audit](../service-description/app-control.md#audit-policy) sur tous les appareils.
2. [Testez vos applications](../working-with-managed-desktop/work-with-app-control.md#add-a-new-app) pour voir si certaines d’entre elles sont bloquées. Si une application est bloquée, ouvrez une demande [de signataire.](../working-with-managed-desktop/work-with-app-control.md#add-or-remove-a-trusted-signer) 
3. Une fois que vous avez terminé vos tests (quels que soient les résultats), informez les opérations, en notant les demandes de signataire en attente. Les opérations déploieront progressivement des stratégies dans des groupes de déploiement en suivant cette planification :

|Groupe de déploiement  |Type de stratégie  |Calendrier  |
|---------|---------|---------|
|Tester     |  Audit       |  Jour 0       |
|Premier     | Enforced        | Jour 1        |
|Rapide     | Enforced        |  Suspendu, déploiement sur demande       |
|Larges     | Enforced        |  Suspendu, déploiement sur demande       |

Vous pouvez toujours ouvrir une autre demande de service pour suspendre ou revenir en arrière une partie de ce déploiement à tout moment pendant le déploiement.



