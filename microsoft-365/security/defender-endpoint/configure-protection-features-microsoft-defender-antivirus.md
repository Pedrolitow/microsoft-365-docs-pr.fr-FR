---
title: Activer et configurer les fonctionnalités de protection antivirus Microsoft Defender
description: Activez la protection basée sur le comportement, heuristique et en temps réel dans l’antivirus Microsoft Defender.
keywords: heuristic, machine learning, moniteur de comportement, protection en temps réel, always-on, Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 52ddae872fbb41c9cab6329a9d9ef4ff8381556f
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481501"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Configurer la protection comportementale, heuristique et en temps réel.


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows

L’Antivirus Microsoft Defender utilise plusieurs méthodes pour fournir une protection contre les menaces :

- Protection cloud pour la détection quasi instantanée et le blocage des menaces nouvelles et émergentes
- Analyse always on, à l’aide de la surveillance du comportement des fichiers et des processus et d’autres heuristiques (également appelées « protection en temps réel »)
- Mises à jour de protection dédiées basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, et la recherche approfondie sur la résistance aux menaces

Vous pouvez configurer la façon dont l’Antivirus Microsoft Defender utilise ces méthodes avec stratégie de groupe, System Center Configuration Manage, les applets de commande PowerShell et Windows Management Instrumentation (WMI).

Cette section décrit la configuration de l’analyse always on, notamment la façon de détecter et de bloquer les applications considérées comme non sécurisées, mais qui peuvent ne pas être détectées comme des programmes malveillants.

Consultez [Utiliser les technologies antivirus Microsoft Defender de prochaine génération via la protection cloud](cloud-protection-microsoft-defender-antivirus.md) pour savoir comment activer et configurer la protection cloud de l’Antivirus Microsoft Defender.

## <a name="in-this-section"></a>Dans cette section

| Rubrique|Description |
|---|---|
| [Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Détecter et bloquer les applications qui peuvent être indésirables dans votre réseau, telles que les logiciels publicitaires, les modificateurs de navigateur et les barres d’outils, et les applications antivirus non autorisées ou fausses |
| [Activer et configurer les fonctionnalités de protection antivirus Microsoft Defender](configure-real-time-protection-microsoft-defender-antivirus.md)|Activer et configurer la protection en temps réel, l’heuristique et d’autres fonctionnalités de surveillance de l’antivirus Microsoft Defender en permanence |

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
