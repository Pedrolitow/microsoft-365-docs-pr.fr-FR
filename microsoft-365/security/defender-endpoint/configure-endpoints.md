---
title: Outils et méthodes d’intégration pour les appareils Windows 10.
description: Intégrer Windows 10 appareils afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
keywords: Intégrer Windows 10, stratégie de groupe, gestionnaire de configuration de point de terminaison, gestion des appareils mobiles, script local, gp, sccm, mdm, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f1ef2670a1ca749e0a2f1ebc96300d4eca043bf8
ms.sourcegitcommit: 55791ddab9ae484f76b30f0470eec8a4cf7b46d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51892828"
---
# <a name="onboarding-tools-and-methods-for-windows-10-devices"></a>Outils et méthodes d’intégration pour les appareils Windows 10.

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 Gestion des risques internes](/microsoft-365/compliance/insider-risk-management)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les appareils de votre organisation doivent être configurés pour que le service Defender for Endpoint puisse obtenir des données de capteur de leur part. Il existe différentes méthodes et outils de déploiement que vous pouvez utiliser pour configurer les appareils de votre organisation.

Les méthodes et outils de déploiement suivants sont pris en charge :

- Stratégie de groupe
- Microsoft Endpoint Configuration Manager
- Gestion des appareils mobiles (y compris Microsoft Intune)
- Script local

## <a name="in-this-section"></a>Dans cette section
Rubrique | Description
:---|:---
[Intégrer des Windows 10 à l’aide de la stratégie de groupe](configure-endpoints-gp.md) | Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer Windows appareils à l’aide Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) | Vous pouvez utiliser la version Microsoft Endpoint Manager (branche actuelle) 1606 ou la version 1602 de Microsoft Endpoint Manager (branche actuelle) ou une version antérieure pour déployer le package de configuration sur les appareils.
[Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md) | Utilisez les outils de gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Intégrer les appareils Windows 10 utilisant un script local](configure-endpoints-script.md) | Découvrez comment utiliser le script local pour déployer le package de configuration sur les points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md) | Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configureendpoints-belowfoldlink)
