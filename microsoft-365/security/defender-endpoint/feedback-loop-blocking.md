---
title: Blocage de la boucle de commentaires
description: Le blocage de boucle de commentaires, également appelé protection rapide, fait partie des fonctionnalités de blocage comportemental et d’endiguement dans Microsoft Defender pour point de terminaison
keywords: blocage comportemental, protection rapide, blocage des commentaires, Microsoft Defender pour point de terminaison
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 42e3a8ac53d407e19457ab84cad85a1a3bcbcc92
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194310"
---
# <a name="feedback-loop-blocking"></a>Blocage de la boucle de commentaires

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

## <a name="overview"></a>Vue d'ensemble

Le blocage de boucle de commentaires, également appelé protection rapide, est un composant des [fonctionnalités de blocage comportemental et d’endiguement](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) dans [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/). Avec le blocage de boucle de commentaires, les appareils de votre organisation sont mieux protégés contre les attaques. 

## <a name="how-feedback-loop-blocking-works"></a>Fonctionnement du blocage de boucle de commentaires

Lorsqu’un comportement ou un fichier suspect est détecté, par exemple par [Microsoft Defender Antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10), des informations sur cet artefact sont envoyées à plusieurs classifieurs. Le moteur de boucle de protection rapide inspecte et met en corrélation les informations avec d’autres signaux pour déterminer s’il faut bloquer un fichier. La vérification et la classification des artefacts se produisent rapidement. Il se traduit par un blocage rapide des programmes malveillants confirmés et entraîne la protection dans l’ensemble de l’écosystème. 

Avec une protection rapide en place, une attaque peut être arrêtée sur un appareil, d’autres appareils de l’organisation et sur des appareils d’autres organisations, à mesure qu’une attaque tente d’élargir sa présence.


## <a name="configuring-feedback-loop-blocking"></a>Configuration du blocage de boucles de commentaires

Si votre organisation utilise Defender pour point de terminaison, le blocage de boucle de commentaires est activé par défaut. Toutefois, la protection rapide se produit par le biais d’une combinaison de fonctionnalités Defender pour point de terminaison, de fonctionnalités de protection de Machine Learning et de partage de signal entre les services de sécurité Microsoft. Vérifiez que les fonctionnalités et fonctionnalités suivantes de Defender pour point de terminaison sont activées et configurées :

- [Microsoft Defender pour point de terminaison lignes de base](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [Appareils intégrés à Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboard-configure)

- [PEPT en mode blocage](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [Réduction de la surface d’attaque](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [Protection de nouvelle génération](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (antivirus)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)

- [(Blog) Blocage et confinement comportementaux : transformation de l’optique en protection](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [Ressources de Microsoft Defender pour point de terminaison utiles](/microsoft-365/security/defender-endpoint/helpful-resources)
