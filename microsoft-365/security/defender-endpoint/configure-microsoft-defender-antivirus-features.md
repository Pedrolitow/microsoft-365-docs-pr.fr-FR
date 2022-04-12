---
title: Configurer les fonctionnalités antivirus Microsoft Defender
description: Vous pouvez configurer Antivirus Microsoft Defender fonctionnalités avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe et PowerShell.
keywords: Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, Microsoft Endpoint Configuration Manager, SCCM, Intune, GPM, gestion des appareils mobiles, stratégie de groupe, PowerShell
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
ms.date: 10/14/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 8a1aa78a153e11f1a36fe9f7dcbd85322e6f258d
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787949"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez configurer Antivirus Microsoft Defender avec un certain nombre d’outils, tels que :

- Microsoft Endpoint Manager (qui inclut Microsoft Intune et Microsoft Endpoint Configuration Manager)
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)
- [Attachement du client](/mem/configmgr/tenant-attach/)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection fournie par le cloud. Voir protection [et Antivirus Microsoft Defender fournies par le cloud](cloud-protection-microsoft-defender-antivirus.md)

- Protection en temps réel en permanence, y compris la protection comportementale, heuristique et basée sur l’apprentissage automatique. Consultez [Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md).

- Comment les utilisateurs finaux interagissent avec le client sur des points de terminaison individuels. Consultez les ressources suivantes :
  - [Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur Antivirus Microsoft Defender](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Empêcher ou autoriser les utilisateurs à modifier localement Antivirus Microsoft Defender paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Consultez [les rubriques de référence pour les outils de gestion et de configuration](configuration-management-reference-microsoft-defender-antivirus.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)