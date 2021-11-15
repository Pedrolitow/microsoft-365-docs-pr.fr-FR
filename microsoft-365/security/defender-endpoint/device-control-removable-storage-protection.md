---
title: Microsoft Defender for Endpoint Device Control Removable Stockage Protection
description: Comprendre les fonctionnalités qui empêchent l’utilisateur ou l’ordinateur ou les deux d’utiliser un support de stockage amovible non autorisé
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
ms.openlocfilehash: cf57eb6e08278625ac8887985a39d355266f47d5
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60962926"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender for Endpoint Device Control Removable Stockage Protection

La protection du stockage amovible des contrôles d’appareil dans Microsoft Defender pour point de terminaison empêche les utilisateurs, les points de terminaison ou les deux d’utiliser un support de stockage amovible non autorisé.

## <a name="protection-policies"></a>Stratégies de protection

### <a name="removable-storage-access-control"></a>Contrôle d’accès au stockage amovible

**Capabilities**

- *Audit* Accès en lecture ou en écriture ou en exécution au stockage amovible en fonction de différentes propriétés d’appareil, avec ou sans exclusion.
- *Empêcher* Accès en lecture ou en écriture ou exécution avec ou sans exclusion : autorisez un appareil spécifique en fonction de différentes propriétés de l’appareil.

**Windows 10 et Windows 11 de prise en charge :**

- Appliqué au niveau de l’appareil, au niveau de l’utilisateur. ou les deux. Autorisez uniquement des personnes spécifiques qui effectuent un accès en lecture/écriture/exécution à un stockage amovible spécifique sur un ordinateur spécifique.
- Prise en charge de MEM OMA-URI et GPO.
- Propriétés[d’appareil « prise](#device-properties)en charge » telles que répertoriées.
- Pour plus d’Windows, voir [Contrôle d’accès au stockage amovible.](device-control-removable-storage-access-control.md)

**Plateforme prise en charge** : Windows 10, Windows 11

**Détails de la prise en charge de macOS**:

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté.
- Pour plus d’informations spécifiques à macOS, voir [Contrôle d’appareil pour macOS.](mac-device-control-overview.md)

**Plateforme prise en** charge : macOS Contrôle 10.15.4+ (avec extensions système activées)


### <a name="device-installation"></a>Installation de l’appareil

**Fonctionnalités :** empêcher l’installation avec ou sans exclusion basée sur différentes propriétés d’appareil.

**Windows 10 et Windows 11 de prise en charge :**

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté.
- Prend en charge Microsoft Endpoint Manager et les objets de stratégie de groupe.
- Propriétés[d’appareil « prise](#device-properties)en charge » telles que répertoriées.
- Pour plus d’informations sur Windows, voir Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de [Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).

**Plateforme prise en charge** : Windows 10, Windows 11

**Détails de la prise en charge de macOS**:

- Appliqué au niveau de l’appareil : la même stratégie s’applique à tout utilisateur connecté
- Pour plus d’informations spécifiques à macOS, voir [Contrôle d’appareil pour macOS.](mac-device-control-overview.md)

**Plateforme prise en** charge - macOS Contrôle 10.15.4+ (avec extensions système activées) ou ultérieure

### <a name="endpoint-dlp-removable-storage"></a>Point de terminaison de stockage amovible DLP

**Fonctionnalités :** auditer, avertir ou empêcher un utilisateur de copier un élément ou des informations sur un support amovible ou un périphérique USB.

**Description** : pour plus d’informations sur Windows, consultez la Microsoft 365 protection contre la perte de données de point [de terminaison.](../../compliance/endpoint-dlp-learn-about.md)

**Plateforme prise en charge** : Windows 10, Windows 11

### <a name="bitlocker"></a>BitLocker

**Fonctionnalités**:

- Bloquer les données à écrire sur des lecteurs amovibles qui ne sont pas protégés par BitLocker.
- Bloquer l’accès aux lecteurs amovibles, sauf s’ils ont été chiffrés sur un ordinateur de votre organisation

**Description** - Pour plus d’informations sur Windows, voir [BitLocker - Paramètres](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**Plateforme prise en charge** : Windows 10, Windows 11

## <a name="device-properties"></a>Propriétés du périphérique

Microsoft Defender for Endpoint Device Control Removable Stockage Protection vous permet de restreindre l’accès au stockage amovible en fonction des propriétés décrites dans le tableau ci-dessous :

<br/><br/>

|Nom de la propriété|Stratégies applicables|S’applique aux systèmes d’exploitation|Description|
|---|---|---|---|
|Classe Device|[Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md)|Windows|Pour plus d’informations sur les formats d’ID d’appareil, voir [la classe d’installation de l’appareil.](/windows-hardware/drivers/install/overview-of-device-setup-classes) Les deux liens suivants fournissent la liste complète des classes d’installation de périphériques. Les classes « Utilisation du système » font principalement référence à des appareils qui sont produits avec un ordinateur ou un ordinateur à partir de la fabrique, tandis que les classes « Fournisseur » font principalement référence à des appareils qui peuvent être connectés à un ordinateur/ordinateur existant : classes d’installation de périphériques [définies](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) par le système disponibles pour les fournisseurs - pilotes Windows et classes d’installation de périphériques définies par le système [réservées](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use)à l’utilisation du système - pilotes Windows . **Remarque**: l’installation de l’appareil peut être appliquée à n’importe quel appareil, pas seulement au stockage amovible.|
|ID principal|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md)|Windows|L’ID principal inclut le stockage amovible, le CD/DVD et Windows appareil portable/WPD.|
|ID d’appareil|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md); <p> [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md)|Windows|Pour plus d’informations sur les formats d’ID d’appareil, voir Identificateurs [USB](/windows-hardware/drivers/install/standard-usb-identifiers)standard, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|ID matériel|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md) <p> [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md)|Windows|Une chaîne a identifié l’appareil dans le système, par exemple USBSTOR\DiskGeneric_Flash_Disk___8.07 ; **Remarque**: l’ID matériel n’est pas unique ; différents appareils peuvent partager la même valeur.|
|ID d’instance|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md) <p> Installation d’appareil|Windows|Une chaîne identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|Nom convivial|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md)|Windows|Chaîne attachée à l’appareil, par exemple, périphérique USB de disque mémoire générique|
|ID fournisseur/ID de produit|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md)|Windows <p> macOS|L’ID de fournisseur est le code fournisseur à quatre chiffres que le comité USB affecte au fournisseur. L’ID de produit est le code de produit à quatre chiffres que le fournisseur affecte à l’appareil . Prise en charge des caractères génériques.|
|Serial NumberId|[Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md)|Windows <p> macOS |Par exemple, <SerialNumberId>002324B534BCB431B000058A</SerialNumberId>|
