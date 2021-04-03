---
title: Tester le fonctionnement des fonctionnalités de Microsoft Defender for Endpoint en mode audit
description: Le mode audit vous permet de voir comment Microsoft Defender pour point de terminaison protégerait vos appareils s’il était activé.
keywords: exploit guard, audit, audit, mode, activé, désactivé, test, démonstration, évaluer, atelier
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: dansimp
ms.author: dansimp
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7ce652d58be2d9ff28d82c088d5471a7bffdf6dc
ms.sourcegitcommit: 6e5c00f84b5201422aed094f2697016407df8fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51570971"
---
# <a name="test-how-microsoft-defender-for-endpoint-features-work-in-audit-mode"></a>Tester le fonctionnement des fonctionnalités de Microsoft Defender for Endpoint en mode audit

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Vous pouvez activer les règles de réduction de la surface d’attaque, Exploit Protection, la protection réseau et l’accès contrôlé aux dossiers en mode audit. Le mode audit vous permet  d’enregistrer ce qui se serait passé si vous aviez activé la fonctionnalité.

Vous pouvez activer le mode audit lors du test du fonctionnement des fonctionnalités dans votre organisation. Cela vous permettra de vous assurer que vos applications métier ne sont pas affectées. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent sur une période donnée.

Les fonctionnalités ne bloquent pas ou empêchent la modification des applications, des scripts ou des fichiers. Toutefois, le journal des événements Windows enregistre les événements comme si les fonctionnalités étaient entièrement activées. Avec le mode audit, vous pouvez consulter le journal des événements pour voir l’impact que la fonctionnalité aurait eu si elle était activée.

Pour rechercher les entrées auditées, go to **Applications and Services**  >  **Microsoft**  >  **Windows**  >  **Windows Defender**  >  **Operational**.

Vous pouvez utiliser Defender pour le point de terminaison pour obtenir des détails plus détaillés pour chaque événement, en particulier pour examiner les règles de réduction de la surface d’attaque. L’utilisation de la console Defender for Endpoint vous permet d’examiner les problèmes dans le cadre de la chronologie des alertes et des [scénarios d’enquête.](investigate-alerts.md)

Vous pouvez utiliser la stratégie de groupe, PowerShell et les fournisseurs de services de configuration (CSP) pour activer le mode audit.

> [!TIP]
> Vous pouvez également consulter le site Windows Defender Testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités fonctionnent et voir comment elles fonctionnent.

 **Options d’audit** | **Comment activer le mode audit** | **Comment afficher les événements**
|---------|---------|---------|
| L’audit s’applique à tous les événements | [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md) | [Événements d’accès contrôlé aux dossiers](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer)
| L’audit s’applique à des règles individuelles | [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md) | [Événements de règle de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md#review-attack-surface-reduction-events-in-windows-event-viewer)
| L’audit s’applique à tous les événements | [Activer la protection réseau](enable-network-protection.md) | [Événements de protection du réseau](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer)
| L’audit s’applique aux atténuations individuelles | [Activer la protection la protection contre les codes malveillants exploitant une faille de sécurité](enable-exploit-protection.md) | [Événements Exploit Protection](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer)

## <a name="related-topics"></a>Voir aussi

* [Protéger les appareils contre les codes malveillants exploitant une faille de sécurité](exploit-protection.md)
* [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)
* [Protéger votre réseau](network-protection.md)
* [Protéger les dossiers importants](controlled-folders.md)
