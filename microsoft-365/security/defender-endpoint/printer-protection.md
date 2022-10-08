---
title: Microsoft Defender pour point de terminaison Device Control Printer Protection
description: Microsoft Defender pour point de terminaison Device Control Printer Protection empêche les utilisateurs d’imprimer via des imprimantes non d’entreprise ou des imprimantes USB non approuvées.
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: dansimp
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.subservice: mde
ms.topic: article
ms.collection:
- m365-security
- tier3
ms.custom: admindeeplinkDEFENDER
search.appverid: met150
ms.openlocfilehash: c93cb1d3280976337a6174f15c2a668b9d84091b
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68231745"
---
# <a name="device-control-printer-protection"></a>Protection de l’Imprimante de Contrôle d’Appareil

**S’applique à**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender pour point de terminaison Device Control Printer Protection empêche les utilisateurs d’imprimer via des imprimantes non d’entreprise ou des imprimantes USB non approuvées.

## <a name="licensing"></a>Licences

Avant de commencer à utiliser Printer Protection, vous devez [confirmer votre abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). Pour accéder à Printer Protection et l’utiliser, vous devez disposer des éléments suivants :

- Microsoft 365 E3 pour le déploiement de fonctionnalités/stratégies
- Microsoft 365 E5 pour la création de rapports

## <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, pour déployer une stratégie via OMA-URI, le compte doit disposer des autorisations nécessaires pour créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser l’un des rôles intégrés avec les autorisations suivantes :

- Rôle Gestionnaire de stratégies et de profils.
- Ou un rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lire/Supprimer/Afficher les rapports activées pour les profils de configuration d’appareil
- Ou administrateur général

Pour afficher les rapports de configuration d’appareil, le compte doit disposer d’autorisations d’affichage des rapports. Vous pouvez créer des rôles personnalisés ou utiliser les rôles intégrés avec les autorisations suivantes :

- Administrateur général de la sécurité
- Administrateur de la sécurité
- Lecteur de sécurité

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Assurez-vous que les appareils Windows 10 ou Windows 11 que vous prévoyez de déployer Printer Protection pour répondre à ces exigences.

1. Les mises à jour Windows suivantes sont installées.
    - Pour Windows 1809 : installez Windows Update [KB5003217](https://support.microsoft.com/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46)
    - Pour Windows 1909 : installez Windows Update [KB5003212](https://support.microsoft.com/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - Pour Windows 2004 ou version ultérieure

2. Si vous envisagez de déployer une stratégie via stratégie de groupe, l’appareil doit être intégré à Microsoft Defender pour point de terminaison joint ; si vous envisagez de déployer une stratégie via Microsoft Endpoint Manager, l’appareil doit être joint à l’aide de Microsoft Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>Déployer la stratégie device control Printer Protection

Vous pouvez déployer la stratégie via stratégie de groupe ou Intune.

<br>

****

|Titre|Description|Prise en charge du fournisseur de solutions Cloud | Prise en charge de l’objet de stratégie de groupe | Prise en charge basée sur l’utilisateur | Prise en charge basée sur l’ordinateur |
|---|---|:---:|:---:|:---:|:---:|
|**Activer les restrictions d’impression du contrôle d’appareil**|Empêcher les utilisateurs d’imprimer via une imprimante autre qu’une imprimante d’entreprise|Oui|Oui|Oui|Oui|
|**Liste des périphériques d’impression connectés à USB approuvés**\*|Autoriser une imprimante USB spécifique|Oui|Oui|Oui|Oui|
|

\* Cette stratégie doit être utilisée avec **activer les restrictions d’impression du contrôle d’appareil**.

## <a name="deploy-policy-via-intune"></a>Déployer une stratégie via Intune

Pour Intune, device Control Printer Protection prend uniquement en charge OMA-URI.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-intune"></a>Scénario 1 : Empêcher les utilisateurs d’imprimer via une imprimante autre qu’une imprimante d’entreprise à l’aide de Intune

- Appliquer une stratégie sur une machine :

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl`

- Appliquer la stratégie sur l’utilisateur :

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser`

La chaîne de prise en charge CSP avec `<enabled/>`:

:::image type="content" source="../../media/customeditrow.png" alt-text="Page Personnalisée" lightbox="../../media/customeditrow.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-intune"></a>Scénario 2 : Autoriser des imprimantes USB approuvées spécifiques à l’aide de Intune

- Appliquer une stratégie sur une machine :

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices`

- Appliquer la stratégie sur l’utilisateur :

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser`

La chaîne de prise en charge CSP avec imprimantes USB approuvées via la propriété « ApprovedUsbPrintDevices », par exemple `<enabled><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`:

:::image type="content" source="../../media/editrow.png" alt-text="Volet Modifier la ligne" lightbox="../../media/editrow.png":::

## <a name="deploy-policy-via-group-policy"></a>Déployer une stratégie via stratégie de groupe

Si l’appareil n’est pas Intune joint, vous pouvez également déployer la stratégie via stratégie de groupe.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-group-policy"></a>Scénario 1 : Empêcher les utilisateurs d’imprimer via une imprimante autre qu’une imprimante d’entreprise à l’aide de stratégie de groupe

- Appliquer une stratégie sur une machine :

  Imprimante Modèles \> d’administration de configuration \> d’ordinateur : Activer les restrictions d’impression du contrôle d’appareil

- Appliquer la stratégie sur l’utilisateur :

  Modèles d’administration de configuration \> utilisateur \> Panneau de configuration \> imprimantes : Activer les restrictions d’impression du contrôle d’appareil

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="Volet Activer les restrictions d’impression du contrôle d’appareil" lightbox="../../media/enable-device-ctrl-printing-restrictions.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-group-policy"></a>Scénario 2 : Autoriser des imprimantes USB approuvées spécifiques à l’aide de stratégie de groupe

- Appliquer une stratégie sur une machine :

  Imprimante modèles d’administration de configuration \> d’ordinateur : liste des périphériques \> d’impression connectés à USB approuvés

- Appliquer la stratégie sur l’utilisateur :

  Modèles d’administration de configuration \> utilisateur \> Panneau de configuration \> imprimantes : liste des périphériques d’impression connectés à USB approuvés

:::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="Liste des périphériques d’impression connectés à USB approuvés" lightbox="../../media/list-of-approved-connected-print-devices.png":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>Afficher les données device control Printer Protection dans Microsoft Defender pour point de terminaison portail

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> affiche l’impression bloquée par la stratégie Device Control Printer Protection ci-dessus.

```kusto
DeviceEvents
| where ActionType == 'PrintJobBlocked'
| extend parsed=parse_json(AdditionalFields)
| extend PrintedFile=tostring(parsed.JobOrDocumentName)
| extend PrintPortName=tostring(parsed.PortName)
| extend PrinterName=tostring(parsed.PrinterName)
| extend Policy=tostring(parsed.RestrictionReason) 
| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName, Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields
| order by Timestamp desc
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="repérage avancé" lightbox="../../media/device-control-advanced-hunting.png":::

 Vous pouvez utiliser l’événement PnP pour rechercher l’imprimante USB utilisée dans l’organisation :

```kusto
//find the USB Printer VID/PID
DeviceEvents
| where ActionType == "PnpDeviceConnected"
| extend parsed=parse_json(AdditionalFields)
| extend DeviceDescription = tostring(parsed.DeviceDescription) 
| extend PrinterDeviceId = tostring(parsed.DeviceId) 
| extend VID_PID_Array = split(split(PrinterDeviceId, "\\")[1], "&")
| extend VID_PID = replace_string(strcat(VID_PID_Array[0], '/', VID_PID_Array[1]), 'VID_', '')
| extend VID_PID = replace_string(VID_PID, 'PID_', '')
| extend ClassId = tostring(parsed.ClassId) 
| extend VendorIds = tostring(parsed.VendorIds) 
| where DeviceDescription == 'USB Printing Support'
| project Timestamp , DeviceId, DeviceName, ActionType, DeviceDescription, VID_PID, ClassId, PrinterDeviceId, VendorIds, parsed
| order by Timestamp desc
```

 :::image type="content" source="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png" alt-text="Page Repérage avancé" lightbox="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png":::
