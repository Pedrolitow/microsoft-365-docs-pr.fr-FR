---
title: Microsoft Defender pour point de terminaison Access Control de stockage amovible du contrôle d’appareil, support de stockage amovible
description: Une procédure pas à pas sur Microsoft Defender pour point de terminaison
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
ms.date: 09/15/2022
ms.reviewer: tewchen
search.appverid: met150
ms.openlocfilehash: 9a5add52188afcecc4df6a369f65468e79452e95
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67799393"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Microsoft Defender pour point de terminaison Access Control de stockage amovible du contrôle d’appareil

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion stratégie de groupe et Intune gestion OMA-URI/Custom Policy de ce produit sont désormais en disponibilité générale (4.18.2106) : consultez le [blog Tech Community : Protéger votre stockage amovible et votre imprimante avec Microsoft Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="overview"></a>Vue d’ensemble

Microsoft Defender pour point de terminaison fonctionnalité de stockage amovible de contrôle d’appareil Access Control vous permet d’auditer, d’autoriser ou d’empêcher l’accès en lecture, en écriture ou en exécution au stockage amovible avec ou sans exclusion.

|Privilège|Autorisation|
|---|---|
|Access|Lecture, Écriture, Exécution|
|Action Mode|Auditer, autoriser, empêcher|
|Prise en charge du fournisseur de solutions Cloud|Oui|
|Prise en charge de l’objet de stratégie de groupe|Oui|
|Prise en charge basée sur l’utilisateur|Oui|
|Prise en charge basée sur l’ordinateur|Oui|

Microsoft Defender pour point de terminaison fonctionnalité de Access Control de stockage amovible device control vous offre les fonctionnalités suivantes :

### <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez des Access Control de stockage amovibles sur les appareils Windows 10 et Windows 11 qui ont la version **4.18.2103.3 ou ultérieure** du client anti-programme malveillant.

- **4.18.2104 ou version ultérieure** : Ajouter `SerialNumberId`, `VID_PID`, prise en charge de l’objet de stratégie de groupe basée sur filepath, et `ComputerSid`

- **4.18.2105 ou version ultérieure** : ajout de la prise en charge des caractères génériques pour `HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId`la combinaison d’un utilisateur spécifique sur un ordinateur spécifique, d’un disque SSD amovible (SSD SanDisk Extreme)/d’une prise en charge DESI (USB Attached SCSI)

- **4.18.2107 ou version ultérieure** : Ajout de la prise en charge de l’appareil portable Windows (WPD) (pour les appareils mobiles, tels que les tablettes) ; ajouter `AccountName` à la [chasse avancée](device-control-removable-storage-access-control.md#view-data-in-microsoft-defender-for-endpoint)

- **4.18.2205 ou version ultérieure** : développez l’application par défaut de **l’imprimante**. Si vous le **définissez sur Refuser**, il bloque également l’imprimante. Par conséquent, si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie personnalisée pour autoriser l’imprimante

:::image type="content" source="images/powershell.png" alt-text="Capture d’écran de l’interface PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Aucun composant Sécurité Windows n’a besoin d’être actif, car vous pouvez exécuter le stockage amovible Access Control indépendamment de l’état Sécurité Windows.

## <a name="device-control-removable-storage-access-control-properties"></a>Propriétés de Access Control de stockage amovibles du contrôle d’appareil

Le Access Control de stockage amovible inclut la création de groupes de stockage amovibles et la création de règles de stratégie d’accès :

- Le groupe de stockage amovible vous permet de créer un groupe. Par exemple, un groupe USB autorisé ou un groupe USB chiffré.
- La règle de stratégie d’accès vous permet de créer une stratégie pour restreindre chaque groupe de stockage amovible. Par exemple, autorisez uniquement l’utilisateur autorisé à écrire un groupe USB avec accès autorisé.
- Pour bloquer une classe de stockage amovible spécifique, mais autoriser un média spécifique, vous pouvez utiliser «`IncludedIdList` un groupe par le biais `PrimaryId` d’un groupe et `ExcludedIDList` un groupe via`HardwareId``DeviceId`\/ /etc. » Pour obtenir des conseils supplémentaires, consultez Déployer le [stockage amovible Access Control à l’aide de Intune OMA-URI](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri).

Voici les propriétés que vous pouvez utiliser lorsque vous créez les fichiers XML de groupe et de stratégie.

### <a name="removable-storage-group"></a>Groupe de stockage amovible

|Nom de la propriété|Description|Options|
|---|---|---|
|**GroupId**|GUID, un ID unique, représente le groupe et sera utilisé dans la stratégie.||
|**DescriptorIdList**|Répertoriez les propriétés de l’appareil que vous souhaitez utiliser pour couvrir le groupe. Toutes les propriétés respectent la casse. |**PrimaryId** : L’ID principal inclut `RemovableMediaDevices`, `CdRomDevices`, `WpdDevices``PrinterDevices`. <p>**InstancePathId** : InstancePathId est une chaîne qui identifie de façon unique l’appareil dans le système, par exemple. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0` C’est le `Device instance path` Gestionnaire de périphériques. Le nombre à la fin (par exemple &0) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple : `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`. <p>**DeviceId** : pour effectuer une transformation `Device instance path` au format ID d’appareil, consultez les [identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers), par exemple, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07` <p>**HardwareId** : chaîne qui identifie l’appareil dans le système, par exemple, `USBSTOR\DiskGeneric_Flash_Disk___8.07`. C’est `Hardware Ids` dans le Gestionnaire de périphériques. <br>**Remarque** : L’ID matériel n’est pas unique ; différents appareils peuvent partager la même valeur.<p>**FriendlyNameId** : il s’agit d’une chaîne attachée à l’appareil, par exemple. `Generic Flash Disk USB Device` C’est le `Friendly name` Gestionnaire de périphériques. <p>**BusId** : Par exemple, USB, SCSI <p>**SerialNumberId** : Vous pouvez trouver SerialNumberId à partir de `Device instance path` la Gestionnaire de périphériques, par exemple SerialNumberId `03003324080520232521` dans USBSTOR\DISK&VEN__USB&PROD__SANDISK_3.2GEN1&REV_1.00\\`03003324080520232521`&0 <p>**VID_PID** : L’ID du fournisseur est le code fournisseur à quatre chiffres que le comité USB attribue au fournisseur. L’ID de produit est le code de produit à quatre chiffres que le fournisseur affecte à l’appareil. Il prend en charge le caractère générique. Pour passer `Device instance path` au format ID fournisseur et ID de produit, consultez [Identificateurs USB standard](/windows-hardware/drivers/install/standard-usb-identifiers). Par exemple : <br>`0751_55E0`: correspond à cette paire exacte VID/PID<br>`_55E0`: faire correspondre n’importe quel média avec PID=55E0 <br>`0751_`: faire correspondre n’importe quel média avec VID=0751 <p> **Remarque** : consultez [Comment faire trouver la propriété multimédia dans le Gestionnaire de périphériques ?](device-control-removable-storage-access-control-faq.md#how-do-i-find-the-media-property-in-the-device-manager) pour comprendre comment trouver la propriété dans Gestionnaire de périphériques.|
|**Matchtype**|Quand plusieurs propriétés d’appareil sont utilisées dans le `DescriptorIDList`, MatchType définit la relation.|**MatchAll** : tous les attributs sous la `DescriptorIdList` relation will be **And** ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système vérifie si l’USB répond aux deux valeurs. <p> **MatchAny** : les attributs sous DescriptorIdList seront **ou** la relation ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système effectue l’application tant que l’USB a une valeur **DeviceID** ou **InstanceID** identique.|

### <a name="access-policy-rule"></a>Règle de stratégie d’accès

Vous pouvez utiliser les propriétés suivantes pour créer la stratégie de contrôle d’accès :

| Nom de la propriété | Description | Options |
|---|---|---|
| **PolicyRule Id** | GUID, un ID unique, représente la stratégie et sera utilisé dans les rapports et la résolution des problèmes. | |
| **IncludedIdList** | Les groupes auxquels la stratégie sera appliquée. Si plusieurs groupes sont ajoutés, la stratégie est appliquée à n’importe quel média de tous ces groupes.|L’ID/GUID de groupe doit être utilisé dans cette instance. <p> L’exemple suivant illustre l’utilisation de GroupID : <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Groupe auquel la stratégie ne sera pas appliquée. | L’ID/GUID de groupe doit être utilisé dans cette instance. |
| **ID d’entrée** | Une policyRule peut avoir plusieurs entrées ; chaque entrée avec un GUID unique indique à Device Control une restriction.| |
| **Type** | Définit l’action pour les groupes de stockage amovibles dans IncludedIDList. <p>Application : Autoriser ou refuser <p>Audit : AuditAllowed ou AuditDenied<p> | Autoriser<p>Refuser <p>AuditAllowed : définit la notification et l’événement lorsque l’accès est autorisé <p>Audit refusé : définit la notification et l’événement lorsque l’accès est refusé ; doit fonctionner avec l’entrée **Deny** .<p> Lorsqu’il existe des types de conflit pour le même média, le système applique le premier type de stratégie. **Autoriser** et **refuser** est un exemple de type de conflit. |
| **SID** | Le SID d’utilisateur local, le groupe SID d’utilisateur ou le SID de l’objet AD détermine s’il faut appliquer cette stratégie à un utilisateur ou à un groupe d’utilisateurs spécifique. Une entrée peut avoir un maximum d’un SID et une entrée sans SID signifie appliquer la stratégie sur l’ordinateur. |  |
| **ComputerSID** | Le SID d’ordinateur local ou le groupe SID d’ordinateur ou le SID de l’objet AD définit s’il faut appliquer cette stratégie sur un ordinateur ou un groupe d’ordinateurs spécifique. Une entrée peut avoir un maximum d’un ComputerSID et une entrée sans ComputerSID signifie appliquer la stratégie sur l’ordinateur. Si vous souhaitez appliquer une entrée à un utilisateur spécifique et à un ordinateur spécifique, ajoutez SID et ComputerSID dans la même entrée. |  |
| **Options** | Définit s’il faut afficher ou non une notification |**Lorsque l’option Type Allow est sélectionnée** : <p>0 : rien<p>4 : désactivez **AuditAllowed** et **AuditDenied** pour cette entrée. Même si **Allow** se produit et que le paramètre AuditAllowed est configuré, le système n’envoie pas d’événement. <p>8 : capturez les informations du fichier et disposez d’une copie du fichier comme preuve de l’accès en écriture. <p>16 : capturer les informations de fichier pour l’accès en écriture. <p>**Lorsque le refus de type est sélectionné** : <p>0 : rien<p>4 : désactiver **l’audit refusé** pour cette entrée. Même si **le blocage** se produit et que le paramètre AuditDenied est configuré, le système n’affiche pas de notification. <p>**Quand type **AuditAllowed** est sélectionné** : <p>0 : rien <p>1 : rien <p>2 : événement d’envoi<p> **Lorsque **l’audit** de type refusé est sélectionné** : <p>0 : rien <p>1 : afficher la notification <p>2 : événement d’envoi<p>3 : afficher l’événement de notification et d’envoi |
|AccessMask|Définit l’accès. | **Accès au niveau du disque** : <p>1 : Lecture <p>2 : Écrire <p>4 : Exécuter <p>**Accès au niveau du système de fichiers** : <p>8 : Lecture du système de fichiers <p>16 : Écriture du système de fichiers <p>32 : Exécution du système de fichiers <p><p>Vous pouvez avoir plusieurs accès en effectuant une opération OR binaire. Par exemple, accessMask pour lecture et écriture et exécution est égal à 7 ; AccessMask pour lecture et écriture est 3.|

Pour obtenir des conseils spécifiques, consultez :

| Rubrique | Description |
|---|---|
| [Déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](deploy-manage-removable-storage-group-policy.md) | Utilisez stratégie de groupe pour déployer la stratégie.|
| [Déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI](deploy-manage-removable-storage-intune.md) | Utilisez Intune pour déployer la stratégie.|

## <a name="view-data-in-microsoft-defender-for-endpoint"></a>Afficher les données dans Microsoft Defender pour point de terminaison

Le [portail Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) affiche les événements déclenchés par le Access Control de stockage amovible Device Control. Pour accéder à la sécurité Microsoft 365, vous devez disposer de l’abonnement suivant :

- Rapports Microsoft 365 pour E5

Si `AuditAllowed` ou `AuditDenied` est configuré dans votre stratégie et si **l’événement Envoyer** est sélectionné dans **Options**, un événement est envoyé à La chasse avancée ou au rapport de contrôle d’appareil pour chaque accès couvert (`AccessMask` dans l’entrée), qu’il ait été initié par le système ou par l’utilisateur qui s’est connecté.

```kusto
//RemovableStoragePolicyTriggered: event triggered by Disk level enforcement
DeviceEvents
| where ActionType == "RemovableStoragePolicyTriggered"
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)
| extend MediaBusType = tostring(parsed.BusType)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
|project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber
| order by Timestamp desc
```

```kusto
//information of file written to removable storage
DeviceEvents
| where ActionType contains "RemovableStorageFileEvent"
| extend parsed=parse_json(AdditionalFields)
| extend Policy = tostring(parsed.Policy)
| extend PolicyRuleId = tostring(parsed.PolicyRuleId)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaInstanceId = tostring(parsed.InstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
| extend FileInformationOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation)
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, Policy, PolicyRuleId, FileInformationOperation, MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber, FileName, FolderPath, FileSize, FileEvidenceLocation, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="Écran illustrant le blocage du stockage amovible.":::
