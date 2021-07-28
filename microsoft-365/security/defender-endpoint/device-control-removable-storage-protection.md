---
title: Microsoft Defender for Endpoint Device Control Removable Stockage Protection
description: Comprendre les fonctionnalités qui empêchent l’utilisateur ou l’ordinateur ou les deux d’utiliser un support de stockage amovible non autorisé
keywords: support de stockage amovible
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-smandalika
author: v-smandalika
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8d36d01c0ccedf11e40f980df8c21997a11ad49f
ms.sourcegitcommit: 87d994407fb69a747239b8589ad11ddf9b47e527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2021
ms.locfileid: "53596279"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender for Endpoint Device Control Removable Stockage Protection

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender pour endpoint Device Control Removable Stockage Protection empêche l’utilisateur ou l’ordinateur ou les deux d’utiliser un support de stockage amovible non autorisé.

## <a name="protection-policies"></a>Stratégies de protection

### <a name="device-installation"></a>Installation de l’appareil

**Fonctionnalités** : empêcher l’installation avec ou sans exclusion basée sur différentes propriétés d’appareil.

**Windows 10 de support technique**:

- Appliqué au niveau de l’ordinateur : la même stratégie s’applique à tout utilisateur connecté.
- Prend en charge mem et GPO.
- Propriétés[d’appareil « pris](#device-properties)en charge » comme répertoriés.
- Pour plus d’informations Windows, voir Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de [Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

**Plateforme prise en charge** : Windows 10

**Détails de la prise en charge de macOS**:

- Appliqué au niveau de l’ordinateur : la même stratégie s’applique à tout utilisateur connecté
- Pour obtenir des informations spécifiques à macOS, voir [Contrôle d’appareil pour macOS.](mac-device-control-overview.md)

**Plateforme prise en** charge : macOS Contrôle 10.15.4+ (avec extensions système activées)

### <a name="removable-storage-access-control"></a>Contrôle d’accès au stockage amovible

**Capabilities**

- *Audit* Accès en lecture ou en écriture ou en exécution au stockage amovible en fonction de différentes propriétés d’appareil, avec ou sans exclusion.
- *Empêcher* Accès en lecture ou en écriture ou exécution avec ou sans exclusion : autorisez un appareil spécifique en fonction de différentes propriétés de l’appareil.

**Windows 10 de support technique**:

- Appliqué à l’ordinateur, à l’utilisateur ou aux deux. Autorisez uniquement des personnes spécifiques qui effectuent un accès en lecture/écriture/exécution à un stockage amovible spécifique sur un ordinateur spécifique.
- Prise en charge de MEM OMA-URI et GPO.
- Propriétés[d’appareil « pris](#device-properties)en charge » comme répertoriés.
- Pour plus d’Windows, voir [Contrôle d’accès au stockage amovible.](device-control-removable-storage-access-control.md)

**Plateforme prise en charge** : Windows 10

**Détails de la prise en charge de macOS**:

- Appliqué au niveau de l’ordinateur : la même stratégie s’applique à tout utilisateur connecté.
- Pour obtenir des informations spécifiques à macOS, voir [Contrôle d’appareil pour macOS.](mac-device-control-overview.md)

**Plateforme prise en** charge : macOS Contrôle 10.15.4+ (avec extensions système activées)

### <a name="windows-portable-device-access-control"></a>Windows Contrôle d’accès des appareils portables

**Fonctionnalités** : refuser l’accès en lecture ou en écriture à [Windows’appareil portable,](/windows-hardware/drivers/portable/)par exemple : tablette, iPhone.

**Description**:

- Appliqué à l’ordinateur, à l’utilisateur ou aux deux.
- Prise en charge de MEM OMA-URI et GPO.

**Plateforme prise en charge** : Windows 10

### <a name="endpoint-dlp-removable-storage"></a>Point de terminaison de stockage amovible DLP

**Fonctionnalités** : auditer ou avertir ou empêcher un utilisateur de copier un élément ou des informations sur un support amovible ou un périphérique USB.

**Description** : pour plus d’informations sur Windows, consultez la Microsoft 365 protection contre la perte de données de point [de terminaison.](../../compliance/endpoint-dlp-learn-about.md)

**Plateforme prise en charge** : Windows 10

### <a name="bitlocker"></a>BitLocker

**Fonctionnalités**:

- Bloquez les données à écrire sur les lecteurs amovibles qui ne sont pas protégés par BitLocker.
- Bloquer l’accès aux lecteurs amovibles, sauf s’ils ont été chiffrés sur un ordinateur de votre organisation

**Description** - Pour plus d’informations sur Windows, voir [BitLocker - Paramètres](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Plateforme prise en charge** : Windows 10

## <a name="device-properties"></a>Propriétés des appareils

Microsoft Defender pour endpoint Device Control Removable Stockage Protection vous permet de restreindre l’accès au stockage amovible en fonction des propriétés décrites dans le tableau ci-dessous :

<br>

****

|Nom de la propriété|Stratégies applicables|S’applique aux systèmes d’exploitation|Description|
|---|---|---|---|
|Classe Device|[Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md)|Windows|Pour plus d’informations sur les formats d’ID d’appareil, voir [la classe d’installation de l’appareil.](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) **Remarque**: l’installation de l’appareil peut être appliquée à n’importe quel appareil, pas seulement au stockage amovible.|
|ID principal|Contrôle d’accès au stockage amovible|Windows|L’ID principal inclut le stockage amovible et le CD/DVD.|
|ID d’appareil|Comment contrôler les périphériques USB et autres supports amovibles à [l’aide de Microsoft Defender pour endpoint](control-usb-devices-using-intune.md); Contrôle d’accès au stockage amovible|Windows|Pour plus d’informations sur les formats d’ID d’appareil, voir Identificateurs [USB](/windows-hardware/drivers/install/standard-usb-identifiers)standard, par exemple, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|ID matériel|Comment contrôler les périphériques USB et autres supports amovibles à [l’aide de Microsoft Defender pour endpoint](control-usb-devices-using-intune.md); Contrôle d’accès au stockage amovible|Windows|Une chaîne a identifié l’appareil dans le système, par exemple USBSTOR\DiskGeneric_Flash_Disk______8.07 ; **Remarque**: l’ID matériel n’est pas unique ; différents appareils peuvent partager la même valeur.|
|ID d’instance|Installation de l’appareil ; Contrôle d’accès au stockage amovible|Windows|Une chaîne identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Nom convivial|Contrôle d’accès au stockage amovible|Windows|Chaîne attachée à l’appareil, par exemple, périphérique USB de disque mémoire générique|
|ID fournisseur/ID de produit|Contrôle d’accès au stockage amovible|Windows Mac|L’ID de fournisseur est le code fournisseur à quatre chiffres que le comité USB affecte au fournisseur. L’ID de produit est le code de produit à quatre chiffres que le fournisseur affecte à l’appareil . Prise en charge des caractères génériques.|
|Serial NumberId|Contrôle d’accès au stockage amovible|Windows Mac|Par exemple, <SerialNumberId>002324B534BCB431B000058A</SerialNumberId>|
|

## <a name="related-topic"></a>Rubrique connexe

- [Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control](device-control-removable-storage-access-control.md)
