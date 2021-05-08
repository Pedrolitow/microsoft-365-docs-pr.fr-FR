---
title: Configurer les fonctionnalités antivirus Microsoft Defender
description: Vous pouvez configurer les Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, la stratégie de groupe et PowerShell.
keywords: Antivirus Microsoft Defender, anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, Microsoft Endpoint Configuration Manager, SCCM, Intune, GDM, gestion des appareils mobiles, GP, stratégie de groupe, PowerShell
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 4408d5e788449c0d094008261f5e7db9bfe38758
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275107"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez configurer Antivirus Microsoft Defender avec un certain nombre d’outils, notamment :

- Microsoft Intune
- Microsoft Endpoint Configuration Manager
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection fournie par le cloud
- Protection en temps réel toujours continue, y compris la protection comportementale, heuristique et basée sur l’apprentissage automatique
- Interaction des utilisateurs finaux avec le client sur des points de terminaison individuels

Les articles suivants décrivent comment effectuer des tâches clés lors de la configuration Antivirus Microsoft Defender. Chaque article contient des instructions pour l’outil de configuration applicable (ou les outils).

|Article  |Description  |
|---------|---------|
|[Utiliser la protection de Antivirus Microsoft Defender microsoft fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md)     | Utilisez la protection cloud pour une détection avancée, rapide et robuste de l’antivirus.        |
|[Configurer la protection comportementale, heuristique et en temps réel.](configure-protection-features-microsoft-defender-antivirus.md)     |Activez la protection antivirus en temps réel, heuristique et basée sur le comportement.         |
|[Configurer l’interaction de l’utilisateur final avec Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) | Configurez la façon dont les utilisateurs finaux de votre organisation interagissent avec Antivirus Microsoft Defender, les notifications qu’ils voient et s’ils peuvent remplacer les paramètres. |

> [!TIP]
> Vous pouvez également consulter les rubriques de référence pour les [outils](configuration-management-reference-microsoft-defender-antivirus.md) de gestion et de configuration pour obtenir une vue d’ensemble de chaque outil et des liens pour obtenir de l’aide supplémentaire.