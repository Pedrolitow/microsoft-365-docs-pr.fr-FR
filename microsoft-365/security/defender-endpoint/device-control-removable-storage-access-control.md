---
title: Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control
description: Une présentation de Microsoft Defender pour point de terminaison
keywords: support de stockage amovible
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4765477c4faf583fd9906aaa700aafc3fb26a992172f81eb4d3f6978724724be
ms.sourcegitcommit: 4f074a8598a430344a2361728a64b8b8c0e1d215
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2021
ms.locfileid: "54520695"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender for Endpoint Device Control Removable Stockage Access Control vous permet d’accomplir la tâche suivante :

- audit, autoriser ou empêcher l’accès en lecture, écriture ou exécution au stockage amovible avec ou sans exclusion

<br>

****

|Privilège|Autorisation|
|---|---|
|Access|Lecture, Écriture, Exécution|
|Action Mode|Auditer, autoriser, empêcher|
|Prise en charge du programme CSP|Oui|
|Prise en charge des GPO|Oui|
|Prise en charge basée sur l’utilisateur|Oui|
|Prise en charge basée sur l’ordinateur|Oui|
|||

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez le contrôle d Stockage’accès amovible sur Windows 10 qui ont un client anti-programme malveillant version **4.18.2103.3** ou ultérieure.

- **4.18.2104** ou version ultérieure : Ajouter SerialNumberId, VID_PID, prise en charge des GPO basés sur filepath, ComputerSid
- **4.18.2105** ou version ultérieure : ajouter la prise en charge des caractères génériques pour HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, la combinaison d’un utilisateur spécifique sur un ordinateur spécifique, la prise en charge du SSD (Un SSD Extrême SanDisk)/USB Attached SCSI (UAS)
- **4.18.2107** ou une ultérieure : ajouter la prise en charge Windows appareil portable (WPD) (pour les appareils mobiles, tels que les tablettes)

:::image type="content" source="images/powershell.png" alt-text="Interface PowerShell":::

> [!NOTE]
> Aucun des Sécurité Windows n’a besoin d’être actif, car vous pouvez exécuter le contrôle d’accès Stockage amovible indépendamment de Sécurité Windows statut.

## <a name="policy-properties"></a>Propriétés de stratégie

Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible :

### <a name="property-name-group-id"></a>Nom de la propriété : ID de groupe

**Description**: GUID, un ID unique, représente le groupe et sera utilisé dans la stratégie.

### <a name="property-name-descriptoridlist"></a>Nom de la propriété : DescriptorIdList

**Description**: liste des propriétés d’appareil que vous souhaitez utiliser pour couvrir dans le groupe.

Pour chaque propriété d’appareil, voir la section **Propriétés de** l’appareil ci-dessus pour plus d’informations.

**Options**:

- ID principal
  - RemovableMediaDevices
  - CdRomDevices
- DeviceId
- HardwareId
- InstancePathId : InstancePathId est une chaîne qui identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0.

Le numéro à la fin (par **exemple,&0**) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour obtenir de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.

- FriendlyNameId
- SerialNumberId
- VID
- PID
- VID_PID
  - 0751_55E0 : correspondre à cette paire VID/PID exacte
  - _55E0 : faire correspondre n’importe quel média avec PID=55E0
  - 0751_: faire correspondre n’importe quel média avec VID=0751

### <a name="property-name-matchtype"></a>Nom de la propriété : MatchType

**Description**: lorsqu’il existe plusieurs propriétés d’appareil utilisées dans DescriptorIDList, MatchType définit la relation.

**Options**:

- MatchAll : tous les attributs sous la relation DescriptorIdList seront **And** ; par exemple, si l’administrateur place DeviceID et InstancePathID, pour chaque clé USB connectée, le système vérifie si la clé USB répond aux deux valeurs.
- MatchAny : les attributs sous la relation DescriptorIdList seront **Or** ; par exemple, si l’administrateur place DeviceID et InstancePathID, pour chaque clé USB connectée, le système appliquera l’application tant que la clé USB aura une valeur **DeviceID** ou **InstanceID** identique.

Voici les propriétés de stratégie de contrôle d’accès :

### <a name="property-name-policyruleid"></a>Nom de la propriété : PolicyRuleId

**Description**: GUID, un ID unique, représente la stratégie et sera utilisé dans le rapport et la résolution des problèmes.

### <a name="property-name-includedidlist"></a>Nom de la propriété : IncludedIdList

**Description**: groupe(s) à appliquer à la stratégie. Si plusieurs groupes sont ajoutés, la stratégie est appliquée à n’importe quel média de tous ces groupes.

**Options** L’ID de groupe/GUID doit être utilisé à cette instance.

L’exemple suivant illustre l’utilisation de GroupID :

`<IncludedIdList> <GroupId>{EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>`

### <a name="property-name-excludedidlist"></a>Nom de la propriété : ExcludedIDList

**Description**: les groupes à qui la stratégie ne sera pas appliquée.

**Options**: l’ID de groupe/GUID doit être utilisé à cette instance.

### <a name="property-name-entry-id"></a>Nom de la propriété : ID d’entrée

**Description**: un policyRule peut avoir plusieurs entrées ; chaque entrée avec un GUID unique indique à Device Control une restriction.

### <a name="property-name-type"></a>Nom de la propriété : Type

**Description**: définit l’action pour les groupes de stockage amovibles dans IncludedIDList.

- Application : autoriser ou refuser
- Audit : AuditAllowed ou AuditDenied

**Options**:

- Autoriser
- Refuser
- AuditAllowed : définit la notification et l’événement lorsque l’accès est autorisé
- AuditDenied : définit la notification et l’événement lorsque l’accès est refusé ; doit fonctionner avec **l’entrée** de refus.

Lorsqu’il existe des types de conflit pour le même média, le système applique le premier de la stratégie. Un exemple de type de conflit est **Allow** et **Deny**.

### <a name="property-name-options"></a>Nom de la propriété : Options

**Description**: définit s’il faut afficher la notification ou non.

:::image type="content" source="images/device-status.png" alt-text="Écran sur lequel l’état de l’appareil est visible":::

**Options**: 0-4.

Lorsque le type **Autoriser** ou **Refuser** est sélectionné :

- 0 : rien
- 4 : désactivez **AuditAllowed** et **AuditDenied** pour cette entrée. Même si **le blocage** se produit et que le paramètre **AuditDenied** est configuré, le système n’affiche pas de notification.

Lorsque type **AuditAllowed ou** **AuditDenied** est sélectionné :

- 0 : rien
- 1 : afficher la notification, fonctionne uniquement pour AuditDenied
- 2 : événement d’envoi
- 3 : afficher la notification et envoyer un événement. Si vous l’appliquez à AuditAllowed, l’événement sera uniquement en cours de signalement, mais la notification ne s’affichera pas.

### <a name="property-name-sid"></a>Nom de la propriété : Sid

**Description**: définit s’il faut appliquer cette stratégie sur un utilisateur ou un groupe d’utilisateurs spécifique ; une entrée peut avoir un maximum d’un SID et d’une entrée sans SID signifie appliquer la stratégie sur l’ordinateur.

### <a name="property-name-computersid"></a>Nom de la propriété : ComputerSid

**Description**: définit s’il faut appliquer cette stratégie sur un ordinateur ou un groupe d’ordinateurs spécifique ; Une entrée peut avoir un maximum d’un ComputerSID et une entrée sans ComputerSID signifie appliquer la stratégie sur l’ordinateur. Si vous souhaitez appliquer une entrée à un utilisateur spécifique et à un ordinateur spécifique, ajoutez sid et ComputerSID dans la même entrée.

### <a name="property-name-accessmask"></a>Nom de la propriété : AccessMask

**Description**: définit l’accès.

Options 1 à 7 :

- 1 : lecture
- 2 : Écriture
- 3 : Lecture et écriture
- 4 : Exécuter
- 5 : Lecture et exécution
- 6 : Écriture et exécution
- 7 : Lecture et écriture et exécution

## <a name="common-removable-storage-access-control-scenarios"></a>Scénarios courants Stockage contrôle d’accès des périphériques amovibles

Pour vous aider à vous familiariser avec Microsoft Defender pour endpoint Removable Stockage Access Control, nous avons mis en place des scénarios courants que vous pouvez suivre.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scénario 1 : empêcher l’accès en écriture et en exécution à tous les utilisateurs approuvés spécifiques, mais autoriser

1. Créer des groupes
    1. Groupe 1 : Tout stockage amovible et CD/DVD. Un exemple de stockage amovible et cd/DVD est le groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Stockage amovible et [cd-DVD Group.xml.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)
    2. Groupe 2 : approbations de base de données basées sur les propriétés de l’appareil. Voici un exemple de ce cas d’utilisation : ID d’instance - Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données approuvé. [](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    > [!NOTE]
    > Vous devez remplacer `&` par `&amp;` dans la valeur.

2. Création d’une stratégie
    1. Stratégie 1 : bloquer l’écriture et exécuter l’accès, mais autoriser les usbs approuvés. Voici un exemple de ce cas d’utilisation : PolicyRule **c544a991-5786-4402-949e-a032cb790d0e dans** l’exemple Scénario [1](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) Bloquer l’écriture et exécuter l’accès, mais autoriser le fichier USBs.xmlapprouvé.
    2. Stratégie 2 : Auditer l’accès en écriture et en exécution aux stratégies de groupe de sécurité universels autorisées. Voici un exemple de ce cas d’utilisation : PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** dans l’exemple scénario [1 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et en exécution au fichier USBs.xmlapprouvé.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scénario 2 : Auditer l’accès en écriture et en exécution à toutes les stratégies de groupe de sécurité universels non désapprouvées, sauf bloquer

1. Créer des groupes
    1. Groupe 1 : Tout stockage amovible et CD/DVD. Voici un exemple de ce cas d’utilisation : Groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Stockage amovible et de [CD-DVD Group.xml.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)
    2. Groupe 2 : listes de contrôle d’appareil non désapprouvées en fonction des propriétés de l’appareil, par exemple, ID fournisseur/ID de produit, Nom convivial – Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données des [états-Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) non accepté.

    > [!NOTE]
    > Vous devez remplacer `&` par `&amp;` dans la valeur.

2. Création d’une stratégie
    1. Stratégie 1 : bloquer l’accès en écriture et en cours d’exécution à tous les usbs non désapprouvés spécifiques, sauf à les bloquer. Voici un exemple de ce cas d’utilisation : PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès à l’écriture et à l’exécution de tous les fichiers USBs.xmlnon désapprouvés, sauf bloquer.
    2. Stratégie 2 : auditer l’écriture et exécuter l’accès à d’autres personnes. Voici un exemple de ce cas d’utilisation : PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et exécution au fichier others.xml.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion d’une stratégie via une stratégie de groupe

La fonctionnalité De Stockage contrôle d’accès amovible vous permet d’appliquer une stratégie via la stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

Avant de commencer avec le contrôle d’accès Stockage amovible, vous devez confirmer [votre abonnement Microsoft 365.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder au contrôle d’accès Stockage et l’utiliser, vous devez Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Déploiement d’une stratégie via une stratégie de groupe

1. Combinez tous les groupes `<Groups>` `</Groups>` au sein d’un fichier xml.

    L’image suivante illustre l’exemple du scénario 1 : empêcher l’accès en écriture et en exécution à tous les [usbs approuvés spécifiques,](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)sauf autoriser.

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Écran affichant les paramètres de configuration qui autorisent des usbs approuvés spécifiques sur les appareils":::

2. Combinez toutes les règles `<PolicyRules>` `</PolicyRules>` dans un fichier xml.

    Si vous souhaitez limiter un utilisateur spécifique, utilisez la propriété SID dans l’entrée. S’il n’existe aucun SID dans l’entrée de stratégie, l’entrée est appliquée à l’instance de connexion de tout le monde pour l’ordinateur.

    L’image suivante illustre l’utilisation de la propriété SID et un exemple de scénario 1 : Empêcher l’accès en écriture et en exécution à tous les [usbs approuvés spécifiques,](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)sauf autoriser.

    :::image type="content" source="images/usage-sid-property.png" alt-text="Écran affichant un code qui indique l’utilisation de l’attribut de propriété SID":::

3. Enregistrez les fichiers XML de règle et de groupe sur le dossier  de partage réseau et placez le chemin d’accès du dossier de partage réseau dans le paramètre de stratégie de groupe : Modèles d’administration de configuration ordinateur \>  \> **Windows Composants** \> **Antivirus Microsoft Defender** \> **Contrôle**  de périphérique : « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil ».

   Si vous ne trouvez pas l’UX de configuration de stratégie dans la stratégie de groupe, vous pouvez télécharger les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) en sélectionnant **Raw,** puis **Enregistrer** sous .

   - L’ordinateur cible doit pouvoir accéder au partage réseau pour avoir la stratégie. Toutefois, une fois la stratégie lue, la connexion de partage réseau n’est plus nécessaire, même après le redémarrage de l’ordinateur.

    :::image type="content" source="images/device-control.png" alt-text="Écran Contrôle d’appareil":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Déploiement et gestion d’une stratégie via Intune OMA-URI

La fonctionnalité Stockage contrôle d’accès amovible vous permet d’appliquer une stratégie via OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer avec le contrôle d’accès Stockage amovible, vous devez confirmer [votre abonnement Microsoft 365.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder au contrôle d’accès Stockage et l’utiliser, vous devez Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit être autorisé à créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser n’importe quel rôle intégré avec ces autorisations.

- Rôle gestionnaire de stratégies et de profils
- Rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lecture/Supprimer/Afficher les rapports pour les profils de configuration d’appareil
- Administrateur général

### <a name="deploying-policy-via-oma-uri"></a>Déploiement d’une stratégie via OMA-URI

**Microsoft Endpoint Manager admin center ( https://endpoint.microsoft.com/) -> Devices -> Configuration profiles -> Create profile -> Platform: Windows 10 and later & Profile: Custom**

1. Pour chaque groupe, créez une règle OMA-URI :
    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Par exemple, pour tout stockage amovible et groupe **CD/DVD** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Type de données : chaîne (fichier XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Fichier xml pour le type de données STRING":::

2. Pour chaque stratégie, créez également un OMA-URI :
    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bFA6BE102-0784-4A2A-B010-A0BEBEBF68E1%7d/RuleData`

      Par exemple, pour la règle Bloquer l’écriture et exécuter l’accès, mais autoriser les règles de base de données utilisateur **approuvées** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Type de données : chaîne (fichier XML)

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Déploiement et gestion d’une stratégie à l’aide de l’interface utilisateur Intune

Cette fonctionnalité (dans Microsoft Endpoint Manager admin center ( <https://endpoint.microsoft.com/> ) Devices Configuration profiles Create profile \> \> \> \> Platform: Windows 10 and later & Profile: Device Control) n’est pas encore disponible.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données de contrôle d’Stockage d’accès amovible dans Microsoft Defender pour le point de terminaison

Le portail Microsoft 365 de sécurité affiche le stockage amovible bloqué par le contrôle d’Stockage d’accès. Pour accéder à la sécurité Microsoft 365, vous devez avoir l’abonnement suivant :

- Microsoft 365 de rapports E5

```kusto
//events triggered by RemovableStoragePolicyTriggered
DeviceEvents
| where ActionType == &quot;RemovableStoragePolicyTriggered&quot;
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess) 
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict) 
| extend MediaBusType = tostring(parsed.BusType) 
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy) 
| extend MediaProductId = tostring(parsed.ProductId) 
| extend MediaVendorId = tostring(parsed.VendorId) 
| extend MediaSerialNumber = tostring(parsed.SerialNumber) 
| extend MediaVolume = tostring(parsed.Volume) 
| project Timestamp, DeviceId, DeviceName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber, MediaVolume
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="Écran illustrant le blocage du stockage amovible":::

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Quelle est la limite du support de stockage amovible pour le nombre maximal de objets de première utilisation ?

Nous avons validé un groupe USB avec 100 000 supports , jusqu’à 7 Mo. La stratégie fonctionne dans Intune et LPO sans problèmes de performances.

### <a name="why-does-the-policy-not-work"></a>Pourquoi la stratégie ne fonctionne-t-elle pas ?

La raison la plus courante est qu’il n’existe pas de version de [client anti-programme malveillant requise.](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints)

Une autre raison peut être que le fichier XML n’est pas correctement formaté, par exemple, si vous n’utilisez pas la mise en forme markdown correcte pour le caractère « & » dans le fichier XML, ou que l’éditeur de texte peut ajouter une 0xEF 0xBB 0xBF de marque d’ordre d’byte au début des fichiers, ce qui entraîne le non-bon de l’examen XML. Une solution simple consiste à télécharger [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (sélectionnez **Raw,** puis **Enregistrer sous),** puis à mettre à jour.

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Il n’existe aucune expérience d’expérience de configuration pour « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil » dans ma stratégie de groupe

Nous ne déportons pas l’UX de la stratégie de groupe, mais vous pouvez toujours obtenir les fichiers adml et admx associés en cliquant sur « Raw » et « Save as » dans les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx.](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx)

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Comment puis-je savoir quel ordinateur utilise la version du client anti-programme malveillant inaltérable dans l’organisation ?

Vous pouvez utiliser la requête suivante pour obtenir la version du client anti-programme malveillant sur le portail Microsoft 365 sécurité :

```kusto
//check the antimalware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```
