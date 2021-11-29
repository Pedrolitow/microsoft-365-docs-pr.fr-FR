---
title: Activer et configurer les fonctionnalités Antivirus Microsoft Defender protection des données
description: Activez la protection en temps réel, heuristique et basée sur le comportement dans Microsoft Defender AV.
keywords: heuristique, machine learning, moniteur de comportement, protection en temps réel, toujours en Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender
ms.prod: m365-security
ms.technology: mde
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
ms.openlocfilehash: 374e955641a5b74a36bc506e3dfda32e1081e1a5
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61218609"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>Configurer la protection comportementale, heuristique et en temps réel.


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Antivirus Microsoft Defender utilise plusieurs méthodes pour fournir une protection contre les menaces :

- Protection cloud pour la détection et le blocage quasi instantanés des menaces nouvelles et émergentes
- Analyse toujours continue, à l’aide de la surveillance du comportement des fichiers et des processus et d’autres heuristiques (également appelée « protection en temps réel »)
- Mises à jour de la protection dédiées, fondées sur l’apprentissage automatique, l’analyse humaine et automatisée du Big Data, et des recherches approfondies sur la résistance aux menaces

Vous pouvez configurer la façon dont Antivirus Microsoft Defender utilise ces méthodes avec la stratégie de groupe, System Center Configuration Manage, les cmdlets PowerShell et Windows Management Instrumentation (WMI).

Cette section couvre la configuration de l’analyse toujours en ligne, notamment la détection et le blocage des applications qui sont considérées comme non sûres, mais qui peuvent ne pas être détectées comme des programmes malveillants.

Voir [Utiliser les technologies de Antivirus Microsoft Defender nouvelle](cloud-protection-microsoft-defender-antivirus.md) génération via la protection cloud pour savoir comment activer et configurer Antivirus Microsoft Defender protection cloud.

## <a name="in-this-section"></a>Dans cette section

| Rubrique|Description |
|---|---|
| [Détecter et bloquer des applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| Détecter et bloquer les applications qui peuvent être indésirables sur votre réseau, telles que les logiciels publicitaires, les modificateurs de navigateur et les barres d’outils, ainsi que les applications antivirus malveillantes ou factices |
| [Activer et configurer les fonctionnalités Antivirus Microsoft Defender protection des données](configure-real-time-protection-microsoft-defender-antivirus.md)|Activer et configurer la protection en temps réel, l’heuristique et d’autres fonctionnalités de surveillance Antivirus Microsoft Defender en temps réel |
