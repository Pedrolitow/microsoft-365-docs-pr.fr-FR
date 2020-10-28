---
title: Outils et méthodes d’intégration pour les appareils Windows 10 (aperçu)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Périphériques Windows 10 embarqués afin qu’ils puissent envoyer des données de capteur aux solutions de conformité de Microsoft 365
ms.openlocfilehash: 5f5a777d11dda900116b6095166ffffed6efa31b
ms.sourcegitcommit: bd36c88e731e3fee2a3a5cb3564fdc94f11bab94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769641"
---
# <a name="onboarding-tools-and-methods-for-windows-10-devices-preview"></a>Outils et méthodes d’intégration pour les appareils Windows 10 (aperçu)

**S’applique à :**
- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

Les appareils de votre organisation doivent être configurés de manière à ce que le service de protection contre la perte de données du point de terminaison de Microsoft 365 puisse obtenir des données de capteur. Il existe plusieurs méthodes et outils de déploiement que vous pouvez utiliser pour configurer les appareils dans votre organisation.

Les méthodes et les outils de déploiement suivants sont pris en charge :

- stratégie de groupe
- Microsoft Endpoint Configuration Manager
- Gestion des appareils mobiles (y compris Microsoft Intune)
- script local

## <a name="in-this-section"></a>Dans cette section
Rubrique | Description
:---|:---
[Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md) | Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Appareils Windows intégrés utilisant le gestionnaire de configuration de point de terminaison Microsoft](dlp-configure-endpoints-sccm.md) | Vous pouvez utiliser Microsoft Endpoint Configuration Manager (branchy) version 1606 ou Microsoft Endpoint Configuration Manager (branchy) version 1602 ou antérieure pour déployer le package de configuration sur les appareils.
[Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md) | Utilisez les outils de gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Périphériques Windows 10 embarqués à l’aide d’un script local](dlp-configure-endpoints-script.md) | Découvrez comment utiliser le script local pour déployer le package de configuration sur des points de terminaison.
[Périphériques VDI (Virtual Desktop Infrastructure) non persistants](dlp-configure-endpoints-vdi.md) | Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.
