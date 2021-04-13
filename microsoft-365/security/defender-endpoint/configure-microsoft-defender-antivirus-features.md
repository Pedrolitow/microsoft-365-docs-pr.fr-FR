---
title: Configurer les fonctionnalités de l'Antivirus Microsoft Defender
description: Vous pouvez configurer les fonctionnalités de l'Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, la stratégie de groupe et PowerShell.
keywords: Antivirus Microsoft Defender, anti-programme malveillant, sécurité, defender, configurer, configuration, Gestionnaire de configuration, Microsoft Endpoint Configuration Manager, SCCM, Intune, GDM, gestion des appareils mobiles, GP, stratégie de groupe, PowerShell
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 3dcf0ab24541a8837fbab91049fed0157b7f1fc9
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690297"
---
# <a name="configure-microsoft-defender-antivirus-features"></a>Configurer les fonctionnalités de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez configurer l'Antivirus Microsoft Defender avec un certain nombre d'outils, notamment :

- Microsoft Intune
- Microsoft Endpoint Configuration Manager
- Stratégie de groupe
- Cmdlets PowerShell
- WMI (Windows Management Instrumentation)

Les grandes catégories de fonctionnalités suivantes peuvent être configurées :

- Protection cloud
- Protection en temps réel toujours continue, y compris la protection comportementale, heuristique et basée sur l'apprentissage automatique
- Interaction des utilisateurs finaux avec le client sur des points de terminaison individuels

Les articles suivants décrivent comment effectuer des tâches clés lors de la configuration de l'Antivirus Microsoft Defender. Chaque article contient des instructions pour l'outil de configuration applicable (ou les outils).

|Article  |Description  |
|---------|---------|
|[Utiliser la protection de l'Antivirus Microsoft Defender fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md)     | Utilisez la protection cloud pour une détection avancée, rapide et robuste de l'antivirus.        |
|[Configurer la protection comportementale, heuristique et en temps réel](configure-protection-features-microsoft-defender-antivirus.md)     |Activez la protection antivirus en temps réel, heuristique et basée sur le comportement.         |
|[Configurer l'interaction de l'utilisateur final avec l'Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) | Configurez la façon dont les utilisateurs finaux de votre organisation interagissent avec l'Antivirus Microsoft Defender, les notifications qu'ils voient et s'ils peuvent remplacer les paramètres. |

> [!TIP]
> Vous pouvez également consulter les rubriques de référence pour les [outils](configuration-management-reference-microsoft-defender-antivirus.md) de gestion et de configuration pour obtenir une vue d'ensemble de chaque outil et des liens pour obtenir de l'aide supplémentaire.