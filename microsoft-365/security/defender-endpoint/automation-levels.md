---
title: Niveaux d’automatisation dans l’examen et la correction automatisés
description: Obtenir une vue d’ensemble des niveaux d’automatisation et de leur fonctionnement dans Microsoft Defender for Endpoint
keywords: automatisé, examen, niveau, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: JoeDavies-MSFT
ms.author: josephd
ms.date: 10/22/2020
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.custom: AIR
ms.openlocfilehash: ba206002415fcd4ae968cc88563136399b78f435
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274773"
---
# <a name="automation-levels-in-automated-investigation-and-remediation-capabilities"></a>Niveaux d’automatisation dans les fonctionnalités automatisées d’examen et de correction

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Les fonctionnalités d’investigation et de correction automatisées (AIR) dans Microsoft Defender for Endpoint peuvent être configurées sur l’un des différents niveaux d’automatisation. Votre niveau d’automatisation a une incidence sur le fait que les actions de correction à la suite d’examens AIR soient prises automatiquement ou uniquement après approbation.  
- *L’automatisation complète* (recommandée) signifie que des actions de correction sont prises automatiquement sur les artefacts déterminés comme malveillants.
- *La semi-automatisation signifie* que certaines actions de correction sont prises automatiquement, mais que d’autres actions de correction attendent l’approbation avant d’être prises. (Consultez le tableau dans [Niveaux d’automatisation.)](#levels-of-automation)
- Toutes les actions de correction, qu’elles soient en attente ou terminées, sont effectuées dans le centre de actions ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ). 

> [!TIP]
> Pour de meilleurs résultats, nous vous recommandons d’utiliser l’automatisation complète lorsque vous [configurez AIR.](configure-automated-investigations-remediation.md) Les données collectées et analysées au cours de l’année précédente montrent que les clients qui utilisent l’automatisation complète ont supprimé 40 % plus d’échantillons de programmes malveillants à haut niveau de confiance que les clients qui utilisent des niveaux d’automatisation inférieurs. L’automatisation complète peut vous aider à libérer vos ressources d’opérations de sécurité pour vous concentrer davantage sur vos initiatives stratégiques.

## <a name="levels-of-automation"></a>Niveaux d’automatisation

Le tableau suivant décrit chaque niveau d’automatisation et son fonctionnement.

|Niveau d’automatisation | Description|
|:---|:---|
|**Complète : corriger automatiquement les menaces** <br/>(également appelé *automatisation complète)*| Avec l’automatisation complète, les actions de correction sont effectuées automatiquement. Toutes les actions correctives prises peuvent être vues dans le centre [de](auto-investigation-action-center.md) actions sous **l’onglet** Historique. Si nécessaire, une action de correction peut être annulée.<br/><br/>**_L’automatisation_* complète est recommandée et est sélectionnée par défaut pour les clients qui ont été créés le 16 août 2020 avec Microsoft Defender pour endpoint, sans groupe d’appareils défini pour le moment.*  |
|**Semi - exiger l’approbation de toutes les corrections** <br/>(également appelé *semi-automatisation)*| Avec ce niveau de semi-automatisation, une approbation est requise pour toute action *de* correction. Ces actions en attente peuvent être vues et approuvées dans le centre [de](auto-investigation-action-center.md)actions, sous **l’onglet En** attente.<br/><br/>*Ce niveau de semi-automatisation est sélectionné par défaut pour les clients qui ont été créés avant le 16 août 2020 avec Microsoft Defender pour endpoint, sans aucun groupe d’appareils défini.*|
|**Semi - exiger l’approbation pour la correction des dossiers principaux** <br/>(également un type de *semi-automatisation*)  | Avec ce niveau de semi-automatisation, l’approbation est requise pour toutes les actions de correction nécessaires sur les fichiers ou les fichiers exécutables qui se trouve dans des dossiers principaux. Les dossiers principaux incluent les répertoires du système d’exploitation, tels que **Windows** ( `\windows\*` ).<br/><br/>Des actions de correction peuvent être prises automatiquement sur des fichiers ou des fichiers exécutables qui se trouver dans d’autres dossiers (non essentiels). <br/><br/>Les actions en attente pour les fichiers ou les fichiers exécutables dans les dossiers principaux peuvent être vues et approuvées dans le Centre de [actions,](auto-investigation-action-center.md)sous **l’onglet En** attente. <br/><br/>Les actions qui ont été prises sur des fichiers ou des fichiers exécutables dans d’autres dossiers peuvent être vues dans le centre de [actions,](auto-investigation-action-center.md)sous l’onglet **Historique.** |
|**Semi - exiger l’approbation pour la correction des dossiers non temporaires** <br/>(également un type de *semi-automatisation*)| Avec ce niveau de semi-automatisation, l’approbation est requise pour toutes  les actions de correction nécessaires sur les fichiers ou les fichiers exécutables qui ne se trouve pas dans des dossiers temporaires. <br/><br/>Les dossiers temporaires peuvent inclure les exemples suivants : <br/>- `\users\*\appdata\local\temp\*`<br/>- `\documents and settings\*\local settings\temp\*` <br/>- `\documents and settings\*\local settings\temporary\*`<br/>- `\windows\temp\*`<br/>- `\users\*\downloads\*`<br/>- `\program files\` <br/>- `\program files (x86)\*`<br/>- `\documents and settings\*\users\*`<br/><br/>Des actions de correction peuvent être prises automatiquement sur des fichiers ou des fichiers exécutables qui se trouver dans des dossiers temporaires. <br/><br/>Les actions en attente pour les fichiers ou les fichiers exécutables qui ne sont pas dans des dossiers temporaires peuvent être vues et approuvées dans le Centre de [actions,](auto-investigation-action-center.md)sous **l’onglet** En attente.<br/><br/>Les actions qui ont été prises sur des fichiers ou des fichiers exécutables dans des dossiers temporaires peuvent être vues et approuvées dans le Centre de [actions,](auto-investigation-action-center.md)sous **l’onglet** Historique.   |
|**Aucune réponse automatisée** <br/>(également appelé aucune *automatisation)* | Sans automatisation, l’examen automatisé ne s’exécute pas sur les appareils de votre organisation. Par conséquent, aucune action de correction n’est prise ou en attente à la suite d’un examen automatisé. Toutefois, d’autres fonctionnalités de protection contre les menaces, telles que la protection contre les [applications](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)potentiellement indésirables, peuvent être en vigueur, selon la configuration de votre antivirus et des fonctionnalités de protection nouvelle génération.<br/><br/>****L’utilisation de l’option*** Sans automatisation n’est pas recommandée, car elle réduit la posture de sécurité des appareils de votre organisation. [Envisagez de définir votre niveau d’automatisation sur automatisation complète (ou](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/machine-groups)au moins semi-automatisation) *. |

## <a name="important-points-about-automation-levels"></a>Points importants sur les niveaux d’automatisation

- L’automatisation complète s’est révélée fiable, efficace et sûre, et est recommandée pour tous les clients. L’automatisation complète libère vos ressources de sécurité critiques afin qu’elles se concentrent davantage sur vos initiatives stratégiques.

- Les nouveaux clients (qui incluent les clients qui ont été créés le 16 août 2020 ou après) avec Microsoft Defender pour point de terminaison sont entièrement automatisés par défaut.

- Si votre équipe de sécurité a défini des groupes d’appareils avec un niveau d’automatisation, ces paramètres ne sont pas modifiés par les nouveaux paramètres par défaut en cours de déploiement. 

- Vous pouvez conserver vos paramètres d’automatisation par défaut ou les modifier en fonction des besoins de votre organisation. Pour modifier vos paramètres, [définissez votre niveau d’automatisation.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation#set-up-device-groups)

## <a name="next-steps"></a>Étapes suivantes

- [Configurer des fonctionnalités automatisées d’examen et de correction dans Microsoft Defender pour endpoint](configure-automated-investigations-remediation.md)

- [Visiter le centre de travail](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/auto-investigation-action-center#the-action-center)
