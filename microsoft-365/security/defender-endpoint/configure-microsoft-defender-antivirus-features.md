---
title: Configurer les fonctionnalités antivirus Microsoft Defender
description: Vous pouvez configurer Microsoft Defender fonctionnalités antivirus avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe et PowerShell.
keywords: Microsoft Defender Antivirus, logiciel anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, Configuration Manager de point de terminaison Microsoft, SCCM, Intune, GPM, gestion des appareils mobiles, stratégie de groupe, PowerShell
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
ms.openlocfilehash: 7fd4f302d0e24ea72fc2b63eea652f479e72201b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68201834"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Vous pouvez configurer Microsoft Defender Antivirus avec un certain nombre d’outils, tels que :

- Microsoft Endpoint Manager (qui inclut Microsoft Intune et Configuration Manager de point de terminaison Microsoft)
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)
- [Attachement du client](/mem/configmgr/tenant-attach/)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection fournie par le cloud. Voir [protection fournie par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- Protection en temps réel en permanence, y compris la protection comportementale, heuristique et basée sur l’apprentissage automatique. Consultez [Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md).

- Comment les utilisateurs finaux interagissent avec le client sur des points de terminaison individuels. Consultez les ressources suivantes :
  - [Empêcher les utilisateurs de voir ou d’interagir avec l’interface utilisateur Microsoft Defender Antivirus](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Empêcher ou autoriser les utilisateurs à modifier localement Microsoft Defender paramètres de stratégie antivirus](configure-local-policy-overrides-microsoft-defender-antivirus.md)

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
