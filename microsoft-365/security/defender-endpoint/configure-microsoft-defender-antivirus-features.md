---
title: Configurer les fonctionnalités antivirus Microsoft Defender
description: Vous pouvez configurer les fonctionnalités de l’Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe et PowerShell.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, point de terminaison Microsoft Configuration Manager, SCCM, Intune, GPM, gestion des appareils mobiles, stratégie de groupe, PowerShell
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
ms.openlocfilehash: c0950ead64f39dced48bbdea0e242bdc1d8fe3b6
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479529"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez configurer l’antivirus Microsoft Defender avec un certain nombre d’outils, tels que :

- Microsoft Endpoint Manager (qui inclut Microsoft Intune et Configuration Manager de point de terminaison Microsoft)
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)
- [Attachement du client](/mem/configmgr/tenant-attach/)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection fournie par le cloud. Consultez [la protection fournie par le cloud et l’antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- Protection en temps réel en permanence, y compris la protection comportementale, heuristique et basée sur l’apprentissage automatique. Consultez [Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md).

- Comment les utilisateurs finaux interagissent avec le client sur des points de terminaison individuels. Consultez les ressources suivantes :
  - [Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur de l’Antivirus Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres de stratégie antivirus Microsoft Defender](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Consultez [les rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md).
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
