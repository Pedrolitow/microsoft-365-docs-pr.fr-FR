---
title: Microsoft Defender pour point de terminaison protection de stockage amovible du contrôle d’appareil
description: Comprendre les fonctionnalités qui permettent d’empêcher l’utilisateur ou l’ordinateur ou les deux d’utiliser un média de stockage amovible non autorisé
keywords: support de stockage amovible
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 08/01/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 9c863e39704d0695940e6d32df7b599e6a8ea310
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67697866"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender pour point de terminaison protection de stockage amovible du contrôle d’appareil


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

La protection de stockage amovible du contrôle d’appareil dans Microsoft Defender pour point de terminaison empêche les utilisateurs, les points de terminaison ou les deux d’utiliser un média de stockage amovible non autorisé.

## <a name="protection-policies"></a>Stratégies de protection

### <a name="removable-storage-access-control"></a>Contrôle d’accès au stockage amovible

**Capabilities**

- *Audit* Accès en lecture, écriture ou exécution au stockage amovible en fonction de différentes propriétés d’appareil, avec ou sans exclusion.
- *Empêcher* Accès en lecture, écriture ou exécution avec ou sans exclusion : autorisez un appareil spécifique en fonction de différentes propriétés de l’appareil.

Pour gérer le stockage externe, utilisez le contrôle d’accès au stockage amovible au lieu de [l’installation de l’appareil](#device-installation).

**Windows 10 et Windows 11 les détails du support :**

- Appliqué au niveau de l’appareil, au niveau de l’utilisateur. ou les deux. Autorisez uniquement des personnes spécifiques qui effectuent un accès en lecture/écriture/exécution à un stockage amovible spécifique sur un ordinateur spécifique.
- Prise en charge de MEM OMA-URI et GPO.
- Pour les appareils Windows, consultez [Access Control de stockage amovible](device-control-removable-storage-access-control.md).

**Plateforme prise en charge** - Windows 10, Windows 11

**Détails du support macOS** :

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté.
- Pour plus d’informations sur macOS, consultez [Contrôle d’appareil pour macOS](mac-device-control-overview.md).

**Plateforme prise en charge** - macOS Catalina 10.15.4+ (avec extensions système activées)


### <a name="device-installation"></a>Installation de l’appareil

**Fonctionnalités** : empêcher l’installation avec ou sans exclusion en fonction de différentes propriétés d’appareil.

**Windows 10 et Windows 11 les détails du support :**

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté.
- Prend en charge les objets Microsoft Endpoint Manager et stratégie de groupe.
- Pour plus d’informations sur Windows, consultez [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md).

**Plateforme prise en charge** - Windows 10, Windows 11

**Détails du support macOS** :

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté
- Pour plus d’informations sur macOS, consultez [Contrôle d’appareil pour macOS](mac-device-control-overview.md).

**Plateforme prise en charge** - macOS Catalina 10.15.4+ (avec extensions système activées) ou version ultérieure

### <a name="endpoint-dlp-removable-storage"></a>Stockage amovible DLP du point de terminaison

**Fonctionnalités** : auditez, avertissez ou empêchez un utilisateur de copier un élément ou des informations sur un support amovible ou un périphérique USB.

**Description** : pour plus d’informations sur Windows, consultez [En savoir plus sur la protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md) de point de terminaison.

**Plateforme prise en charge** - Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Fonctionnalités** :

- Bloquer l’écriture de données sur des lecteurs amovibles qui ne sont pas protégés par BitLocker.
- Bloquer l’accès aux lecteurs amovibles, sauf s’ils ont été chiffrés sur un ordinateur appartenant à votre organisation

**Description** - Pour plus d’informations sur Windows, consultez [BitLocker - Paramètres de lecteur amovible](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Plateforme prise en charge** - Windows 10, Windows 11
