---
title: Configurer les fonctionnalités antivirus Microsoft Defender
description: Vous pouvez configurer les Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, la stratégie de groupe et PowerShell.
keywords: Antivirus Microsoft Defender, anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, Microsoft Endpoint Configuration Manager, SCCM, Intune, GDM, gestion des appareils mobiles, GP, stratégie de groupe, PowerShell
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
ms.openlocfilehash: 52556d3193843eecfb9130ead349a20bd16fab34
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61164141"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous pouvez configurer Antivirus Microsoft Defender avec un certain nombre d’outils, tels que :

- Microsoft Endpoint Manager (qui inclut les Microsoft Intune et Microsoft Endpoint Configuration Manager)
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)
- [Joint au client](/mem/configmgr/tenant-attach/)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection cloud. Voir protection et protection des services [cloud Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

- Protection en temps réel toujours continue, y compris la protection comportementale, heuristique et basée sur l’apprentissage automatique. Voir [Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)

- Interaction des utilisateurs finaux avec le client sur des points de terminaison individuels. Consultez les ressources suivantes :
  - [Empêcher les utilisateurs de voir ou d’interagir avec l Antivirus Microsoft Defender’interface utilisateur](prevent-end-user-interaction-microsoft-defender-antivirus.md)
  - [Empêcher ou autoriser les utilisateurs à modifier localement les paramètres Antivirus Microsoft Defender stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md)

> [!TIP]
> Consulter les [rubriques de référence pour les outils de gestion et de configuration.](configuration-management-reference-microsoft-defender-antivirus.md)
