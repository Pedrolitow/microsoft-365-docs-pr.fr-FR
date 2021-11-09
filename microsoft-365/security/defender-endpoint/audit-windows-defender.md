---
title: Tester le fonctionnement des fonctionnalités de Microsoft Defender for Endpoint en mode audit
description: Le mode audit vous permet de voir comment Microsoft Defender pour point de terminaison protégerait vos appareils s’il était activé.
keywords: exploit guard, audit, audit, mode, activé, désactivé, test, démonstration, évaluer, atelier
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: ''
manager: dansimp
ms.topic: article
ms.technology: mde
ms.date: 10/14/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: fd5966380b23b13ab43b3e0e0c6583db03971541
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60882932"
---
# <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Tester la réduction de la surface d’attaque dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Dans le cadre de l’équipe de sécurité de votre organisation, vous pouvez configurer les fonctionnalités de réduction de la surface d’attaque pour qu’elles s’exécutent en mode audit pour voir comment elles fonctionneront. En mode audit, vous pouvez activer :

- Règles de réduction de la surface d’attaque
- Exploit Protection
- Protection réseau
- Accès contrôlé aux dossiers en mode audit

Le mode audit vous permet  d’enregistrer ce qui se serait passé si vous aviez activé la fonctionnalité.

Vous pouvez activer le mode audit lors du test du fonctionnement des fonctionnalités. Cela vous permettra de vous assurer que vos applications métier ne sont pas affectées. Vous pouvez également avoir une idée du nombre de tentatives de modification de fichier suspectes qui se produisent sur une certaine période de temps.

Les fonctionnalités ne bloquent pas ou n’empêchent pas les applications, les scripts ou les fichiers d’être modifiés. Toutefois, le Windows journal des événements enregistre les événements comme si les fonctionnalités étaient entièrement activées. Avec le mode audit, vous pouvez consulter le journal des événements pour voir l’impact que la fonctionnalité aurait eu si elle avait été activée.

Pour rechercher les entrées auditées, allez à **Applications et services** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Opérationnel**.

Utilisez Defender pour le point de terminaison pour obtenir plus de détails pour chaque événement, en particulier pour examiner les règles de réduction de la surface d’attaque. L’utilisation de la console Defender for Endpoint vous permet d’examiner les problèmes dans le cadre de la chronologie des alertes et des [scénarios d’enquête.](investigate-alerts.md)

Vous pouvez activer le mode audit à l’aide de la stratégie de groupe, de PowerShell et des fournisseurs de services de configuration (CSP).

> [!TIP]
> Vous pouvez également visiter le site Windows Defender Testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités fonctionnent et voir comment elles fonctionnent.

|Options d’audit|Comment activer le mode audit|Comment afficher les événements|
|---|---|---|
|L’audit s’applique à tous les événements|[Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md)|[Événements d’accès contrôlé aux dossiers](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer)
|L’audit s’applique à des règles individuelles|[Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)|[Événements de règle de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md#review-attack-surface-reduction-events-in-windows-event-viewer)
|L’audit s’applique à tous les événements|[Activer la protection du réseau](enable-network-protection.md)|[Événements de protection du réseau](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer)
|L’audit s’applique aux atténuations individuelles|[Activer la protection la protection contre les codes malveillants exploitant une faille de sécurité](enable-exploit-protection.md)|[Événements Exploit Protection](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer)
