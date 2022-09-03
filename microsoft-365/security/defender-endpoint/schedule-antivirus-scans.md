---
title: Planifier des analyses rapides et complètes régulières avec l’Antivirus Microsoft Defender
description: Configurer des analyses périodiques (planifiées), notamment quand elles doivent s’exécuter et si elles s’exécutent en tant qu’analyses complètes ou rapides
keywords: analyse rapide, analyse complète, rapide ou complète, analyse planifiée, quotidienne, hebdomadaire, heure, planifiée, périodique, régulière
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 08/09/2022
ms.reviewer: pauhijbr, ksarens, mkaminska
manager: dansimp
ms.subservice: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 81903fdbb78fdb465ce578e07926fcce85672daf
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67578639"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Configurer des analyses antivirus Microsoft Defender rapides ou complètes

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Outre la protection en temps réel et les analyses antivirus à [la demande](run-scan-microsoft-defender-antivirus.md) , vous pouvez configurer des analyses antivirus régulières et planifiées. Vous pouvez configurer le type d’analyse, le moment où l’analyse doit se produire et si l’analyse doit se produire après une [mise à jour de la protection](manage-protection-updates-microsoft-defender-antivirus.md) ou lorsqu’un point de terminaison n’est pas utilisé. Vous pouvez également configurer des analyses spéciales pour effectuer des actions de correction si nécessaire.

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

- [En savoir plus sur les analyses rapides, les analyses complètes et les analyses personnalisées](#quick-scan-full-scan-and-custom-scan)
- [Utiliser stratégie de groupe pour planifier des analyses antivirus](schedule-antivirus-scans-group-policy.md)
- [Utiliser Windows PowerShell pour planifier des analyses antivirus](schedule-antivirus-scans-powershell.md)
- [Utiliser Windows Management Instrumentation pour planifier des analyses antivirus](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Gardez à l’esprit les points suivants

- Par défaut, l’Antivirus Microsoft Defender recherche une mise à jour 15 minutes avant l’heure des analyses planifiées. Vous pouvez [gérer la planification du moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) pour remplacer cette valeur par défaut.

- Si un appareil est débranché et en cours d’exécution sur batterie pendant une analyse complète planifiée, l’analyse planifiée s’arrête avec l’événement 1002, qui indique que l’analyse s’est arrêtée avant la fin. L’Antivirus Microsoft Defender exécutera une analyse complète à l’heure planifiée suivante.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Analyse rapide, analyse complète et analyse personnalisée

Lorsque vous configurez des analyses planifiées, vous pouvez spécifier si l’analyse doit être complète ou rapide. Dans la plupart des cas, une analyse rapide est recommandée ; Toutefois, nous vous recommandons également d’exécuter au moins une analyse complète après l’installation ou l’activation de l’Antivirus Defender. Cette analyse permet de rechercher des menaces existantes et permet de remplir le cache pour les analyses futures.

|Analyse rapide|Analyse complète|Analyse personnalisée|
|---|---|---|
|(Recommandé) Une analyse rapide examine tous les emplacements où des programmes malveillants peuvent être inscrits pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus. <br/><br/>Combinée à une protection en temps réel toujours activée, qui examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur accède à un dossier, une analyse rapide permet de fournir une protection forte contre les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau.<br/><br/>Dans la plupart des cas, une analyse rapide est suffisante et est l’option recommandée pour les analyses planifiées.|Une analyse complète commence par exécuter une analyse rapide, puis se poursuit avec une analyse séquentielle de tous les disques fixes montés et des lecteurs amovibles/réseau (si l’analyse complète est configurée pour ce faire).<br/><br/>L’analyse complète peut prendre quelques heures ou jours, en fonction de la quantité et du type de données à analyser.<br/><br/>Une fois l’analyse complète terminée, de nouvelles informations de sécurité sont disponibles et une nouvelle analyse est ensuite nécessaire pour s’assurer qu’aucune autre menace n’est détectée avec le nouveau renseignement de sécurité.<br/><br/>En raison du temps et des ressources impliqués dans une analyse complète, en général, Microsoft ne recommande pas la planification des analyses complètes.|Une analyse personnalisée s’exécute sur les fichiers et dossiers que vous spécifiez. Par exemple, vous pouvez choisir d’analyser un lecteur USB ou un dossier spécifique sur le lecteur local de votre appareil.|

> [!NOTE]
> Par défaut, les analyses rapides s’exécutent sur les appareils amovibles montés, tels que les lecteurs USB.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Comment faire savez quel type d’analyse choisir ?

Utilisez le tableau suivant pour choisir un type d’analyse.
<br/><br/>

|Scénario|Type d’analyse recommandé|
|---|---|
|Vous souhaitez configurer des analyses régulières et planifiées|Analyse rapide <p> Une analyse rapide vérifie les processus, la mémoire, les profils et certains emplacements sur l’appareil. Combinée à la [protection en temps réel always-on](configure-real-time-protection-microsoft-defender-antivirus.md), une analyse rapide permet de fournir une couverture renforcée à la fois pour les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. La protection en temps réel examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur accède à un dossier.|
|Les menaces, telles que les programmes malveillants, sont détectées sur un appareil individuel|Analyse rapide <p> Dans la plupart des cas, une analyse rapide intercepte et nettoie les programmes malveillants détectés.|
|Vous souhaitez exécuter une [analyse à la demande](run-scan-microsoft-defender-antivirus.md)|Analyse rapide|
|Vous souhaitez vous assurer qu’un appareil portable, tel qu’un lecteur USB, ne contient pas de programmes malveillants|Analyse personnalisée <p> Une analyse personnalisée vous permet de sélectionner des emplacements, des dossiers ou des fichiers spécifiques, et exécute une analyse rapide.|
| Vous venez d’installer ou de réactiver l’Antivirus Microsoft Defender | Analyse complète <p>L’exécution d’une analyse complète une fois que vous venez d’activer ou d’installer l’antivirus Microsoft Defender permet de remplir le cache pour les analyses futures. L’analyse complète peut également aider à détecter les menaces existantes sur l’appareil. |

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Que dois-je savoir d’autre sur les analyses rapides et complètes ?

- Les fichiers malveillants peuvent être stockés dans des emplacements qui ne sont pas inclus dans une analyse rapide. Toutefois, la protection en temps réel toujours active examine tous les fichiers ouverts et fermés, ainsi que tous les fichiers qui se trouvent dans des dossiers accessibles par un utilisateur. La combinaison de la protection en temps réel et d’une analyse rapide permet de fournir une protection forte contre les programmes malveillants.

- La protection à l’accès avec [une protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md) permet de s’assurer que tous les fichiers accessibles sur le système sont analysés à l’aide des derniers modèles d’intelligence de sécurité et de machine learning cloud.

- Lorsque la protection en temps réel détecte les programmes malveillants et que l’étendue des fichiers affectés n’est pas déterminée initialement, l’Antivirus Microsoft Defender lance une analyse complète dans le cadre du processus de correction.

- Une analyse complète peut détecter les fichiers malveillants qui n’ont pas été détectés par d’autres analyses, telles qu’une analyse rapide. Toutefois, une analyse complète peut prendre un certain temps et utiliser des ressources système précieuses.

- Si un appareil est hors connexion pendant une période prolongée, l’analyse complète peut prendre plus de temps.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
