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
ms.openlocfilehash: ec5cfa78852d65db808c4e853f90f5639df25d6f
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52300209"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender for Endpoint Device Control Removable Stockage Protection

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender pour endpoint Device Control Removable Stockage Protection empêche l’utilisateur ou l’ordinateur ou les deux d’utiliser un support de stockage amovible non autorisé.

**Microsoft Defender for Endpoint Removable Stockage Protection**


|Stratégie  |Fonctionnalité |Description  |
|---------|---------|---------|
|Installation de l’appareil    |  Empêcher l’installation avec ou sans exclusion : autoriser des appareils spécifiques basés sur différentes propriétés ; Pour plus d’informations, voir la section [Propriétés de l’appareil](#device-properties) ci-dessous.        |    Fonctionne sur l’ordinateur : différents utilisateurs se connectant au même ordinateur seront restreints par la même stratégie. Pour plus d’informations, voir Comment contrôler des périphériques USB et d’autres supports amovibles à [l’aide de Microsoft Defender for Endpoint](control-usb-devices-using-intune.md).     |
|Contrôle d’accès au stockage amovible      | (1) Auditez l’accès en lecture ou écriture ou exécution au stockage amovible en fonction de différentes propriétés de l’appareil, avec ou sans exception. Pour plus d’informations, voir la section [Propriétés de l’appareil](#device-properties) ci-dessous. (2) Empêcher l’accès en lecture ou écriture ou exécution avec ou sans exclusion : autoriser des appareils spécifiques basés sur différentes propriétés d’appareil ; Pour plus d’informations sur les propriétés de l’appareil, voir la section [Propriétés de l’appareil](#device-properties) ci-dessous.     |     Fonctionne sur l’ordinateur ou l’utilisateur ou les deux : autoriser uniquement des personnes spécifiques qui effectuent un accès en lecture/écriture/exécution à un stockage amovible spécifique sur un ordinateur spécifique ; pour la fonctionnalité dans Windows, voir [Contrôle d’accès au stockage amovible](device-control-removable-storage-access-control.md); pour la fonctionnalité dans Mac, voir [Contrôle d’appareil pour macOS.](mac-device-control-overview.md)     |
|Point de terminaison de stockage amovible DLP      |    Auditer, avertir ou empêcher un utilisateur de copier un élément ou des informations sur un support amovible ou un périphérique USB.     |  Pour plus d’informations, voir [Point de terminaison Microsoft DLP.](/compliance/endpoint-dlp-learn-about.md)       |
|BitLocker    |     Bloquer les données à écrire sur des lecteurs amovibles qui ne sont pas protégés BitLocker : bloquer l’accès aux lecteurs amovibles, sauf s’ils ont été chiffrés sur un ordinateur de votre organisation.    |   Pour plus d’informations, voir BitLocker – [Paramètres](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings#bitlocker---removable-drive-settings.md).      |

## <a name="device-properties"></a>Propriétés des appareils

Microsoft Defender pour endpoint Device Control Removable Stockage Protection vous permet de restreindre l’accès au stockage amovible en fonction des propriétés décrites dans le tableau ci-dessous :


|Nom de la propriété  |Stratégies applicables  |S’applique aux systèmes d’exploitation  |Description  |
|---------|---------|---------|---------|
|Classe Device    |     [Comment contrôler des périphériques USB et d’autres supports amovibles à l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md)     |   Windows      |  Pour plus d’informations sur les formats d’ID d’appareil, voir [la classe d’installation de l’appareil.](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) **Remarque**: l’installation de l’appareil peut être appliquée à n’importe quel appareil, pas seulement au stockage amovible.       |
|ID principal   |     Contrôle d’accès au stockage amovible    |   Windows      |      L’ID principal inclut le stockage amovible et le CD/DVD.   |
|ID d’appareil     |  Comment contrôler les périphériques USB et autres supports amovibles à [l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md); Contrôle d’accès au stockage amovible       |      Windows   |    Pour plus d’informations sur les formats d’ID d’appareil, voir Identificateurs [USB](/windows-hardware/drivers/install/standard-usb-identifiers)standard, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07      |
|ID matériel     |     Comment contrôler les périphériques USB et autres supports amovibles à [l’aide de Microsoft Defender pour le point de terminaison](control-usb-devices-using-intune.md); Contrôle d’accès au stockage amovible    |     Windows    |    Une chaîne a identifié l’appareil dans le système, par exemple USBSTOR\DiskGeneric_Flash_Disk______8.07 ; **Remarque**: l’ID matériel n’est pas unique ; différents appareils peuvent partager la même valeur.|
|ID d’instance    | Installation de l’appareil ; Contrôle d’accès au stockage amovible     |     Windows    |   Une chaîne identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0      |
|Nom convivial     |     Contrôle d’accès au stockage amovible    |   Windows      |    Chaîne attachée à l’appareil, par exemple, périphérique USB de disque mémoire générique     |
|ID fournisseur/ID de produit     |  Contrôle d’accès au stockage amovible       |   Windows Mac      |     L’ID de fournisseur est le code fournisseur à quatre chiffres que le comité USB affecte au fournisseur. L’ID de produit est le code de produit à quatre chiffres que le fournisseur affecte à l’appareil . Prise en charge des caractères génériques.    |
|Serial NumberId     |     Contrôle d’accès au stockage amovible    |      Windows Mac   |     Par exemple, <SerialNumberId>002324B534BCB431B000058A</SerialNumberId>    |

## <a name="related-topic"></a>Rubrique connexe

- [Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control](device-control-removable-storage-access-control.md)
