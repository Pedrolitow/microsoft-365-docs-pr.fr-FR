---
title: Désintégrage des appareils du service Microsoft Defender pour point de terminaison
description: Intégrer des appareils Windows, des serveurs et des appareils non Windows à partir du service Microsoft Defender pour point de terminaison
keywords: désintégrage, Microsoft Defender pour point de terminaison désintégrage, désintégrage
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 076ee98c8885cd48416e7e2cfdce73a792155a29
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67686832"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>Désintégrage des appareils du service Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux
- Windows Server 2012 R2
- Windows Server 2016

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

Suivez les instructions correspondantes en fonction de votre méthode de déploiement préférée.

> [!NOTE]
> L’état d’un appareil est basculé sur [Inactif](fix-unhealthy-sensors.md#inactive-devices) 7 jours après la désintégrage.
>
> Les données des appareils désinsgrés (par exemple, Chronologie, Alertes, Vulnérabilités, etc.) restent dans le portail jusqu’à l’expiration de la [période de rétention](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) configurée.
>
> Le profil de l’appareil (sans données) reste dans la [liste des appareils](machines-view-overview.md) pendant plus de 180 jours.
>
> En outre, les appareils qui ne sont pas actifs au cours des 30 derniers jours ne sont pas pris en compte sur les données qui reflètent le [score d’exposition](tvm-exposure-score.md) de la gestion des vulnérabilités Defender de votre organisation et le score de sécurité Microsoft pour les appareils.
>
> Pour afficher uniquement les appareils actifs, vous pouvez filtrer par [état d’intégrité du capteur](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views), [balises d’appareil](machine-tags.md) ou [groupes d’ordinateurs](machine-groups.md).

## <a name="offboard-windows-devices"></a>Désintégrage des appareils Windows

- [Désintégrage des appareils à l’aide d’un script local](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [Désintégrage des appareils à l’aide de stratégie de groupe](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Désintégrage des appareils à l’aide des outils de Gestion des appareils mobile](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Serveurs hors-carte

- [Serveurs hors-carte](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>Désintégrage des appareils non Windows

- [Désintégrage des appareils non Windows](configure-endpoints-non-windows.md#offboard-non-windows-devices)
