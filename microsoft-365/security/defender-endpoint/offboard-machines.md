---
title: Hors-carte des appareils à partir du service Microsoft Defender for Endpoint
description: Intégrer Windows 10, serveurs, appareils non Windows à partir du service Microsoft Defender for Endpoint
keywords: offboarding, Microsoft Defender for Endpoint offboarding, offboarding
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
ms.openlocfilehash: cd9849151fbaf0de3b353c5fe26c440368579e68
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53623707"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Hors-carte des appareils à partir du service Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux
- Windows Server 2012 R2
- Windows Server 2016

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Suivez les instructions correspondantes en fonction de votre méthode de déploiement préférée.

>[!NOTE]
> L’état d’un appareil passe à [Inactif](fix-unhealthy-sensors.md#inactive-devices) 7 jours après laboardage. <br> Les données des appareils horsboard (par exemple, Chronologie, Alertes, Vulnérabilités, etc.) restent dans le portail jusqu’à l’expiration de la période de [rétention](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) configurée. <br>
> Le profil de l’appareil (sans [](machines-view-overview.md) données) reste dans la liste des appareils pendant 180 jours au plus.
> En outre, les appareils qui ne sont pas actifs au cours des 30 derniers jours ne sont pas factorés sur les données qui reflètent le [score](tvm-exposure-score.md) d’exposition Gestion des menaces et des vulnérabilités de votre organisation et le score de sécurité Microsoft pour les appareils. <br>
> Pour afficher uniquement les appareils [](machines-view-overview.md#health-state)actifs, vous pouvez filtrer par état d’état d’état, [balises d’appareil](machine-tags.md) ou groupes [d’ordinateurs.](machine-groups.md) 

## <a name="offboard-windows-10-devices"></a>Appareils hors Windows 10 d’appareil
- [Hors-carte des appareils à l’aide d’un script local](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Appareils de tableau de bord à l’aide de la stratégie de groupe](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Appareils hors appareil à l’aide des outils de gestion des périphériques mobiles](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Serveurs horsboard
- [Serveurs horsboard](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Appareils non-Windows par carte
- [Appareils non-Windows par carte](configure-endpoints-non-windows.md#offboard-non-windows-devices)

