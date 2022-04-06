---
title: Microsoft Defender pour point de terminaison Protection Stockage amovible du contrôle d’appareil
description: Comprendre les fonctionnalités qui permettent d’empêcher l’utilisateur ou l’ordinateur ou les deux d’utiliser un média de stockage amovible non autorisé
keywords: support de stockage amovible
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3d679cfa4f09b06e2c7923ee1fe6e47247d90f76
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665071"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender pour point de terminaison Protection Stockage amovible du contrôle d’appareil


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

**Windows 10 et Windows 11 les détails du support :**

- Appliqué au niveau de l’appareil, au niveau de l’utilisateur. ou les deux. Autorisez uniquement des personnes spécifiques qui effectuent un accès en lecture/écriture/exécution à un stockage amovible spécifique sur un ordinateur spécifique.
- Prise en charge de MEM OMA-URI et GPO.
- Prise en charge des « [propriétés de l’appareil](#device-properties) » comme indiqué.
- Pour connaître la fonctionnalité dans Windows, consultez [Access Control de stockage amovible](device-control-removable-storage-access-control.md).

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
- Prise en charge des « [propriétés de l’appareil](#device-properties) » comme indiqué.
- Pour plus d’informations sur Windows, consultez [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md).

**Plateforme prise en charge** - Windows 10, Windows 11

**Détails du support macOS** :

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté
- Pour plus d’informations sur macOS, consultez [Contrôle d’appareil pour macOS](mac-device-control-overview.md).

**Plateforme prise en charge** - macOS Catalina 10.15.4+ (avec extensions système activées) ou version ultérieure

### <a name="endpoint-dlp-removable-storage"></a>Stockage amovible DLP du point de terminaison

**Fonctionnalités** : auditez, avertissez ou empêchez un utilisateur de copier un élément ou des informations sur un support amovible ou un périphérique USB.

**Description** : pour plus d’informations sur Windows, consultez [En savoir plus sur Microsoft 365 protection contre la perte de données](../../compliance/endpoint-dlp-learn-about.md) de point de terminaison.

**Plateforme prise en charge** - Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Fonctionnalités** :

- Bloquer l’écriture de données sur des lecteurs amovibles qui ne sont pas protégés par BitLocker.
- Bloquer l’accès aux lecteurs amovibles, sauf s’ils ont été chiffrés sur un ordinateur appartenant à votre organisation

**Description** - Pour plus d’informations sur Windows, consultez [BitLocker - Paramètres de lecteur amovible](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Plateforme prise en charge** - Windows 10, Windows 11

## <a name="device-properties"></a>Propriétés du périphérique

Microsoft Defender pour point de terminaison Device Control Amovible Stockage Protection vous permet de restreindre l’accès au stockage amovible en fonction des propriétés décrites dans le tableau ci-dessous :

<br/><br/>

|Nom de la propriété|Stratégies applicables|S’applique aux systèmes d’exploitation|Description|
|---|---|---|---|
|Classe d’appareil|[Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md)|Windows|Pour plus d’informations sur les formats d’ID d’appareil, consultez [la classe d’installation de l’appareil](/windows-hardware/drivers/install/overview-of-device-setup-classes). Les deux liens suivants fournissent la liste complète des classes d’installation d’appareil. Les classes « Utilisation du système » font principalement référence aux appareils fournis avec un ordinateur/ordinateur de la fabrique, tandis que les classes « Vendor » font principalement référence aux appareils qui peuvent être connectés à un ordinateur/machine existant : [classes d’installation d’appareil définies par le système disponibles pour les fournisseurs - pilotes Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) et [classes d’installation d’appareil définies par le système réservées à l’utilisation du système - pilotes Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **Remarque** : l’installation de l’appareil peut être appliquée à tous les appareils, pas seulement au stockage amovible.|
|ID principal|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md)|Windows|L’ID principal inclut le stockage amovible et le CD/DVD et Windows périphérique portable/WPD.|
|ID d'appareil|[Access Control de stockage amovible](device-control-removable-storage-access-control.md) ; <p> [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md)|Windows|Pour plus d’informations sur les formats d’ID d’appareil, consultez [Identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers), par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|ID matériel|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md) <p> [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour point de terminaison](control-usb-devices-using-intune.md)|Windows|Une chaîne a identifié l’appareil dans le système, par exemple USBSTOR\DiskGeneric_Flash_Disk___8.07 ; **Remarque** : L’ID matériel n’est pas unique ; différents appareils peuvent partager la même valeur.|
|ID d’instance|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md) <p> Installation d’appareil|Windows|Une chaîne identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Nom convivial|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md)|Windows|Chaîne attachée à l’appareil, par exemple, périphérique USB de disque flash générique|
|ID du fournisseur /ID de produit|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md)|Windows <p> macOS|L’ID du fournisseur est le code fournisseur à quatre chiffres que le comité USB attribue au fournisseur. L’ID de produit est le code de produit à quatre chiffres que le fournisseur affecte à l’appareil ; Prise en charge du caractère générique.|
|Serial NumberId|[Access Control de stockage amovibles](device-control-removable-storage-access-control.md)|Windows <p> macOS |Par exemple, `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
