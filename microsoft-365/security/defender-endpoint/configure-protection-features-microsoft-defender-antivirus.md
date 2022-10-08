---
title: Activer et configurer Microsoft Defender fonctionnalités de protection antivirus
description: Activez la protection basée sur le comportement, heuristique et en temps réel dans Microsoft Defender Antivirus.
keywords: heuristic, machine learning, moniteur de comportement, protection en temps réel, always-on, antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender
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
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: b9b2bd120e622238d681e6208361bd58f02e16f0
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68202648"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Configurer la protection comportementale, heuristique et en temps réel.


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows

Microsoft Defender Antivirus utilise plusieurs méthodes pour fournir une protection contre les menaces :

- Protection cloud pour la détection quasi instantanée et le blocage des menaces nouvelles et émergentes
- Analyse always on, à l’aide de la surveillance du comportement des fichiers et des processus et d’autres heuristiques (également appelées « protection en temps réel »)
- Mises à jour de protection dédiées basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, et la recherche approfondie sur la résistance aux menaces

Vous pouvez configurer la façon dont Microsoft Defender Antivirus utilise ces méthodes avec stratégie de groupe, System Center Configuration Manage, les applets de commande PowerShell et Windows Management Instrumentation (WMI).

Cette section décrit la configuration de l’analyse always on, notamment la façon de détecter et de bloquer les applications considérées comme non sécurisées, mais qui peuvent ne pas être détectées comme des programmes malveillants.

Pour savoir comment activer et configurer Microsoft Defender protection cloud antivirus, consultez [Utiliser les technologies antivirus Microsoft Defender suivantes via la protection cloud](cloud-protection-microsoft-defender-antivirus.md).

## <a name="in-this-section"></a>Dans cette section

| Rubrique|Description |
|---|---|
| [Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Détecter et bloquer les applications qui peuvent être indésirables dans votre réseau, telles que les logiciels publicitaires, les modificateurs de navigateur et les barres d’outils, et les applications antivirus non autorisées ou fausses |
| [Activer et configurer Microsoft Defender fonctionnalités de protection antivirus](configure-real-time-protection-microsoft-defender-antivirus.md)|Activer et configurer la protection en temps réel, l’heuristique et d’autres fonctionnalités de surveillance de l’antivirus Microsoft Defender en permanence |

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
