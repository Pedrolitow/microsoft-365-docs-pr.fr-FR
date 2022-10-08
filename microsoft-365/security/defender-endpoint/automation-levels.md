---
title: Niveaux d’automatisation dans l’examen et la correction automatisés
description: Obtenir une vue d’ensemble des niveaux d’automatisation et de leur fonctionnement dans Microsoft Defender pour point de terminaison
keywords: automatisé, investigation, niveau, Microsoft Defender pour point de terminaison
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.service: microsoft-365-security
ms.subservice: mde
ms.author: dansimp
ms.localizationpriority: medium
ms.date: 08/22/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
search.appverid: met150
ms.openlocfilehash: 4f00523c62846f5341fe2c17a5fd26ea255d60b5
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68151604"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Niveaux d’automatisation dans les fonctionnalités d’investigation et de correction automatisées

**S’applique à :**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

Les fonctionnalités d’investigation et de correction automatisées (AIR) dans Microsoft Defender pour entreprises sont préconfigurées et ne sont pas configurables. Dans Microsoft Defender pour point de terminaison, vous pouvez configurer AIR à l’un des différents niveaux d’automatisation. Votre niveau d’automatisation détermine si les actions de correction qui suivent les investigations AIR sont effectuées automatiquement ou uniquement lors de l’approbation.

- *L’automatisation complète* (recommandée) signifie que les actions de correction sont effectuées automatiquement sur les artefacts considérés comme malveillants. (*L’automatisation complète est définie par défaut dans Defender pour Entreprises*.)
- *La semi-automatisation* signifie que certaines actions de correction sont effectuées automatiquement, mais d’autres actions de correction attendent l’approbation avant d’être effectuées. (Consultez le tableau dans [Niveaux d’automatisation](#levels-of-automation).)
- Toutes les actions de correction, qu’elles soient en attente ou terminées, sont suivies dans le Centre d’actions ([https://security.microsoft.com](https://security.microsoft.com)).

> [!TIP]
> Pour de meilleurs résultats, nous vous recommandons d’utiliser l’automatisation complète lorsque vous [configurez AIR](configure-automated-investigations-remediation.md). Les données collectées et analysées au cours de la dernière année montrent que les clients qui utilisent l’automatisation complète ont supprimé 40 % plus d’exemples de programmes malveillants à haut niveau de confiance que les clients qui utilisent des niveaux d’automatisation inférieurs. L’automatisation complète peut vous aider à libérer vos ressources d’opérations de sécurité pour vous concentrer davantage sur vos initiatives stratégiques.

> [!NOTE]
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

## <a name="levels-of-automation"></a>Niveaux d’automatisation

|Niveau d’automatisation|Description|
|---|---|
|**Complet : corriger automatiquement les menaces** <br> (également appelé *automatisation complète*)|Avec l’automatisation complète, les actions de correction sont effectuées automatiquement sur les entités considérées comme malveillantes. Toutes les actions de correction effectuées peuvent être affichées dans le [Centre d’actions](auto-investigation-action-center.md) sous l’onglet **Historique** . Si nécessaire, une action de correction peut être annulée. <p> **_L’automatisation complète est recommandée_* et est sélectionnée par défaut pour les locataires avec Defender pour point de terminaison qui ont été créés le 16 août 2020 ou après, sans aucun groupe d’appareils défini pour le moment.*<p>*L’automatisation complète est définie par défaut dans Defender entreprise.*|
|**Semi - exiger l’approbation de toute correction** <br> (également appelé *semi-automatisation*)|Avec ce niveau de semi-automatisation, l’approbation est requise pour *toute* action de correction. Ces actions en attente peuvent être affichées et approuvées dans le [Centre d’actions](auto-investigation-action-center.md), sous l’onglet **En attente** . <p> *Ce niveau de semi-automatisation est sélectionné par défaut pour les locataires créés avant le 16 août 2020 avec Microsoft Defender pour point de terminaison, sans aucun groupe d’appareils défini.*|
|**Semi - Exiger l’approbation pour la correction des dossiers principaux** <br> (également un type de *semi-automatisation*)|Avec ce niveau de semi-automatisation, l’approbation est requise pour toutes les actions de correction nécessaires sur les fichiers ou les exécutables qui se trouvent dans les dossiers principaux. Les dossiers principaux incluent des répertoires de système d’exploitation, tels que **Windows** (`\windows\*`). <p> Les actions de correction peuvent être effectuées automatiquement sur les fichiers ou les exécutables qui se trouvent dans d’autres dossiers (non-core). <p> Les actions en attente pour les fichiers ou les exécutables dans les dossiers principaux peuvent être affichées et approuvées dans le [Centre d’actions](auto-investigation-action-center.md), sous l’onglet **En attente** . <p> Les actions qui ont été effectuées sur des fichiers ou des exécutables dans d’autres dossiers peuvent être affichées dans le [Centre d’actions](auto-investigation-action-center.md), sous l’onglet **Historique** .|
|**Semi - Exiger l’approbation pour la correction des dossiers non temporaires** <br> (également un type de *semi-automatisation*)|Avec ce niveau de semi-automatisation, l’approbation est requise pour toutes les actions de correction nécessaires sur les fichiers ou les exécutables qui ne se trouvent *pas* dans des dossiers temporaires. <p> Les dossiers temporaires peuvent inclure les exemples suivants : <ul><li>`\users\*\appdata\local\temp\*`</li><li>`\documents and settings\*\local settings\temp\*`</li><li>`\documents and settings\*\local settings\temporary\*`</li><li>`\windows\temp\*`</li><li>`\users\*\downloads\*`</li><li>`\program files\`</li><li>`\program files (x86)\*`</li><li>`\documents and settings\*\users\*`</li></ul> <p> Les actions de correction peuvent être effectuées automatiquement sur les fichiers ou les exécutables qui se trouvent dans des dossiers temporaires. <p> Les actions en attente pour les fichiers ou les exécutables qui ne se trouvent pas dans des dossiers temporaires peuvent être affichées et approuvées dans le [Centre d’actions](auto-investigation-action-center.md), sous l’onglet **En attente** . <p> Les actions qui ont été effectuées sur des fichiers ou des exécutables dans des dossiers temporaires peuvent être affichées et approuvées dans le [Centre d’actions](auto-investigation-action-center.md), sous l’onglet **Historique** .|
|**Aucune réponse automatisée** <br> (également appelé *aucune automatisation*)|Sans automatisation, l’investigation automatisée ne s’exécute pas sur les appareils de votre organisation. Par conséquent, aucune action de correction n’est effectuée ou en attente à la suite d’une investigation automatisée. Toutefois, d’autres fonctionnalités de protection contre les menaces, telles que la [protection contre les applications potentiellement indésirables](/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus), peuvent être en vigueur, selon la façon dont vos fonctionnalités de protection antivirus et de nouvelle génération sont configurées. <p> ***L’utilisation de l’option *aucune automatisation* n’est pas recommandée**, car elle réduit la posture de sécurité des appareils de votre organisation. [Envisagez de configurer votre niveau d’automatisation sur une automatisation complète (ou au moins une semi-automatisation).](/microsoft-365/security/defender-endpoint/machine-groups)|

## <a name="important-points-about-automation-levels"></a>Points importants sur les niveaux d’automatisation

- L’automatisation complète s’est avérée fiable, efficace et sûre, et est recommandée pour tous les clients. L’automatisation complète libère vos ressources de sécurité critiques afin qu’elles puissent se concentrer davantage sur vos initiatives stratégiques.

- Les nouveaux locataires (qui incluent les locataires qui ont été créés le 16 août 2020 ou après) avec Defender pour point de terminaison sont définis sur l’automatisation complète par défaut.

- [Defender entreprise](../defender-business/compare-mdb-m365-plans.md) utilise l’automatisation complète par défaut. Defender entreprise n’utilise pas les groupes d’appareils de la même façon que Defender pour point de terminaison. Par conséquent, l’automatisation complète est activée et appliquée à tous les appareils dans Defender entreprise.

- Si votre équipe de sécurité a défini des groupes d’appareils avec un niveau d’automatisation, ces paramètres ne sont pas modifiés par les nouveaux paramètres par défaut qui sont en cours de déploiement.

- Vous pouvez conserver vos paramètres d’automatisation par défaut ou les modifier en fonction des besoins de votre organisation. Pour modifier vos paramètres, [définissez votre niveau d’automatisation](/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups).

## <a name="next-steps"></a>Prochaines étapes

- [Configurer des fonctionnalités d’investigation et de correction automatisées dans Defender pour point de terminaison](configure-automated-investigations-remediation.md)
- [Visitez le Centre d’action](/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
