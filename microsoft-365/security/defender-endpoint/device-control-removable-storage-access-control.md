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
ms.author: v-smandalika
author: v-smandalika
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cf8e74a6886d7086da062d6258e3e1e1a1cbd730
ms.sourcegitcommit: 3e971b31435d17ceeaa9871c01e88e25ead560fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "52861718"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Microsoft Defender for Endpoint Device Control Removable Stockage Access Control vous permet d’accomplir la tâche suivante :
- audit, autoriser ou empêcher l’accès en lecture, écriture ou exécution au stockage amovible avec ou sans exclusion

|Privilège |Autorisation  |
|---------|---------|
|Accès    |  Lecture, Écriture, Exécution       |
|Action Mode    |    Auditer, autoriser, empêcher     |
|Prise en charge du programme CSP   |   Oui      |
|Prise en charge des GPO    |   Oui      |
|Prise en charge basée sur l’utilisateur     |   Oui      |
|Prise en charge basée sur l’ordinateur    |    Oui     |

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez le contrôle d Stockage d’accès amovible sur Windows 10 qui ont un client anti-programme malveillant version **4.18.2103.3** ou ultérieure.
1. **4.18.2104** ou version ultérieure : Ajouter SerialNumberId, VID_PID, prise en charge des GPO basés sur des chemins d’fichiers, ComputerSid

2. **4.18.2105** ou version ultérieure : ajouter la prise en charge des caractères génériques pour HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, la combinaison d’un utilisateur spécifique sur un ordinateur spécifique, la prise en charge du SSD (Un SSD Extrême SanDisk)/USB Attached SCSI (UAS)

:::image type="content" source="images/powershell.png" alt-text="Interface PowerShell":::

   > [!NOTE]
   > Aucun des Sécurité Windows n’a besoin d’être actif, vous pouvez exécuter le contrôle d’accès Stockage amovible indépendamment de l’état Sécurité Windows’utilisateur.

## <a name="policy-properties"></a>Propriétés de stratégie


Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible :

**Nom de la propriété : ID de groupe**

1. Description : [GUID](https://en.wikipedia.org/wiki/Universally_unique_identifier), un ID unique, représente le groupe et sera utilisé dans la stratégie.

**Nom de la propriété : DescriptorIdList**

1. Description : liste des propriétés d’appareil que vous souhaitez utiliser pour couvrir dans le groupe.
List the device properties you want to use to cover in the group.
Pour chaque propriété d’appareil, voir la section **Propriétés de** l’appareil ci-dessus pour plus d’informations.

1. Options :
    - ID principal
        - RemovableMediaDevices
        - CdRomDevices
    - DeviceId
    - HardwareId
    - InstancePathId : InstancePathId est une chaîne qui identifie de manière unique l’appareil dans le système, par exemple USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0. Le numéro à la fin (par **exemple,&0**) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple, USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*
    - FriendlyNameId
    - SerialNumberId
    - VID
    - PID
    - VID_PID
        - 0751_55E0 : correspondre à cette paire VID/PID exacte
        - _55E0 : faire correspondre n’importe quel média avec PID=55E0
        - 0751_: faire correspondre n’importe quel média avec VID=0751
        
**Nom de la propriété : MatchType** 

1. Description : lorsque plusieurs propriétés d’appareil sont utilisées dans DescriptorIDList, MatchType définit la relation.

1. Options :
    - MatchAll : tous les attributs sous la relation DescriptorIdList seront **And** ; par exemple, si l’administrateur place DeviceID et InstancePathID, pour chaque clé USB connectée, le système vérifie si la clé USB répond aux deux valeurs.

    - MatchAny : les attributs sous la relation DescriptorIdList seront **Or** ; par exemple, si l’administrateur place DeviceID et InstancePathID, pour chaque clé USB connectée, le système appliquera l’application tant que la clé USB aura une valeur **DeviceID** ou **InstanceID** identique.



Voici les propriétés de stratégie de contrôle d’accès :

**Nom de la propriété : PolicyRuleId**

1. Description : [GUID](https://en.wikipedia.org/wiki/Universally_unique_identifier), un ID unique, représente la stratégie et sera utilisé dans le rapport et la résolution des problèmes.

**Nom de la propriété : IncludedIdList**

1. Description : groupe(s) à appliquer à la stratégie. Si plusieurs groupes sont ajoutés, la stratégie est appliquée à n’importe quel média de tous ces groupes.

1. Options : l’ID de groupe/GUID doit être utilisé à cette instance.

L’exemple suivant illustre l’utilisation de GroupID :

`<IncludedIdList> <GroupId>{EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>`

**Nom de la propriété : ExcludedIDList**

1. Description : groupe(s) à qui la stratégie ne sera pas appliquée.
1. Options : l’ID de groupe/GUID doit être utilisé à cette instance.

**Nom de la propriété : ID d’entrée**

1. Description : un policyRule peut avoir plusieurs entrées ; chaque entrée avec un GUID unique indique à Device Control une restriction.

**Nom de la propriété : Type**

1. Description : définit l’action pour les groupes de stockage amovibles dans IncludedIDList.
    - Application : autoriser ou refuser
    - Audit : AuditAllowed ou AuditDenied 
1. Options :
    - Autoriser
    - Refuser
    - AuditAllowed : définit la notification et l’événement lorsque l’accès est autorisé
    - AuditDenied : définit la notification et l’événement lorsque l’accès est refusé ; doit fonctionner avec **l’entrée** de refus.

Lorsqu’il existe des types de conflit pour le même média, le système applique le premier de la stratégie. Un exemple de type de conflit est **Allow** et **Deny**.

**Nom de la propriété : Sid**

1. Description : définit si cette stratégie est appliquée à un utilisateur ou à un groupe d’utilisateurs spécifique ; une entrée peut avoir un sid et une entrée sans sid signifie appliquer la stratégie sur l’ordinateur.

**Nom de la propriété : ComputerSid**

1. Description : définit si cette stratégie est appliquée sur un ordinateur ou un groupe d’ordinateurs spécifique ; Une entrée peut avoir un maximum d’un ComputerSid et une entrée sans ComputerSid signifie appliquer la stratégie sur l’ordinateur. Si vous souhaitez appliquer une entrée à un utilisateur spécifique et à un ordinateur spécifique, ajoutez Sid et ComputerSid dans la même entrée.

**Nom de la propriété : Options**

1. Description : définit s’il faut afficher la notification ou non.

   :::image type="content" source="images/device-status.png" alt-text="Écran sur lequel l’état de l’appareil est visible":::

1. Options : 0-4. Lorsque le type Autoriser ou Refuser est sélectionné :

   - 0 : rien
   - 4 : désactivez **AuditAllowed** et **AuditDenied** pour cette entrée. Même si **le blocage** se produit et que le paramètre **AuditDenied** est configuré, le système n’affiche pas de notification.

   Lorsque type **AuditAllowed ou** **AuditDenied** est sélectionné :

   - 0 : rien
   - 1 : afficher la notification
   - 2 : événement d’envoi
   - 3 : afficher la notification et envoyer un événement

**Nom de la propriété : AccessMask**

1. Description : définit l’accès.

1. Options : 1-7 :
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
    1. Groupe 1 : Tout stockage amovible et CD/DVD. Un exemple de stockage amovible et de CD/DVD est le groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Group.xmlany [Removable Stockage et CD-DVD.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)
    
    2. Groupe 2 : approbation de base de données américaines en fonction des propriétés de l’appareil. Exemple de ce cas d’utilisation : ID d’instance – Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données approuvé. [](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    > [!NOTE]
    > Vous devez remplacer `&` par `&amp;` dans la valeur.

2. Création d’une stratégie
    1. Stratégie 1 : bloquer l’écriture et exécuter l’accès, mais autoriser les usbs approuvés. Voici un exemple de ce cas d’utilisation : PolicyRule **c544a991-5786-4402-949e-a032cb790d0e dans** l’exemple Scénario [1](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) Bloquer l’écriture et exécuter l’accès, mais autoriser le fichier .xmlapprouvé.
    
    2. Stratégie 2 : auditer l’accès en écriture et en cours d’exécution aux usbs autorisés. Voici un exemple de ce cas d’utilisation : PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** dans l’exemple scénario [1 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et en exécution au fichier USBs.xmlapprouvé.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scénario 2 : Auditer l’accès en écriture et en exécution à tous les services de sécurité universels non désapprouvés, sauf bloquer

1. Créer des groupes
    1. Groupe 1 : Tout stockage amovible et CD/DVD. Voici un exemple de ce cas d’utilisation : Groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Stockage amovible et [de CD-DVD Group.xml.](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)
    
    2. Groupe 2 : listes de contrôle d’appareil non désapprouvées en fonction des propriétés de l’appareil, par exemple, ID fournisseur/ID de produit, nom convivial – Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données des [états-Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) non accepté. 

    > [!NOTE]
    > Vous devez remplacer `&` par `&amp;` dans la valeur.

2. Création d’une stratégie
    1. Stratégie 1 : bloquer l’accès en écriture et en exécution à tous les usbs non désapprouvés spécifiques, sauf à les bloquer. Voici un exemple de ce cas d’utilisation : PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’écriture et l’exécution de l’accès à tous les fichiers USBs.xmlnon acceptés, sauf bloquer.
    
    2. Stratégie 2 : auditer l’accès en écriture et exécuter l’accès à d’autres personnes. Voici un exemple de ce cas d’utilisation : PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et en exécution au fichier others.xml.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion d’une stratégie via une stratégie de groupe

La fonctionnalité de contrôle d Stockage’accès amovible vous permet d’appliquer une stratégie via la stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

Avant de commencer avec le contrôle d’accès Stockage amovible, vous devez confirmer [votre abonnement Microsoft 365.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder au contrôle d’accès Stockage et l’utiliser, vous devez Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Déploiement d’une stratégie via une stratégie de groupe

1. Combinez tous les groupes `<Groups>` `</Groups>` au sein d’un fichier xml. 

    L’image suivante illustre l’exemple du scénario 1 : empêcher l’accès en écriture et en exécution à tous les [usbs approuvés spécifiques,](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)sauf autoriser.
    
    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Écran affichant les paramètres de configuration qui autorisent des usbs approuvés spécifiques sur les appareils":::
    
2. Combinez toutes les règles `<PolicyRules>` `</PolicyRules>` dans un fichier xml. 

    Si vous souhaitez limiter un utilisateur spécifique, utilisez la propriété SID dans l’entrée. S’il n’existe aucun SID dans l’entrée de stratégie, l’entrée est appliquée à l’instance de connexion de tout le monde pour l’ordinateur.
    
    L’image suivante illustre l’utilisation de la propriété SID et un exemple de scénario 1 : empêcher l’accès en écriture et en exécution à tous les [usbs approuvés spécifiques,](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs)sauf autoriser.
    
    :::image type="content" source="images/usage-sid-property.png" alt-text="Écran affichant un code qui indique l’utilisation de l’attribut de propriété SID":::

3. Enregistrez les fichiers XML de règle et de groupe sur le dossier de partage réseau et placez le chemin d’accès du dossier de partage réseau dans le paramètre de stratégie de groupe : Configuration ordinateur -> Modèles d’administration **-> Windows Composants -> Antivirus Microsoft Defender -> Contrôle** d’appareil : « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil ».

    - L’ordinateur cible doit pouvoir accéder au partage réseau pour avoir la stratégie. Toutefois, une fois la stratégie lue, la connexion de partage réseau n’est plus nécessaire, même après le redémarrage de l’ordinateur.

    :::image type="content" source="images/device-control.png" alt-text="Écran Contrôle d’appareil":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Déploiement et gestion d’une stratégie via Intune OMA-URI

La fonctionnalité Stockage contrôle d’accès amovible vous permet d’appliquer une stratégie via OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

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

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b **GroupGUID**%7d/GroupData

      Par exemple, pour tout stockage amovible et groupe **CD/DVD** dans l’exemple, le lien doit être :

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData

    - Type de données : chaîne (fichier XML)
    
      :::image type="content" source="images/xml-data-type-string.png" alt-text="Fichier xml pour le type de données STRING":::

2. Pour chaque stratégie, créez également un OMA-URI :

    - OMA-URI : 

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bFA6BE102-0784-4A2A-B010-A0BEBEBF68E1%7d/RuleData

      Par exemple, pour la règle Bloquer l’écriture et exécuter l’accès, mais autoriser les règles de base de données utilisateur **approuvées** dans l’exemple, le lien doit être : 

      ./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData.

    - Type de données : chaîne (fichier XML)

      :::image type="content" source="images/xml-data-type-string-2.png" lightbox="images/xml-data-type-string-2.png" alt-text="Affichage du fichier XML pour le type de données STRING":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Déploiement et gestion d’une stratégie à l’aide de l’interface utilisateur Intune

Cette fonctionnalité (dans le Centre d’administration Microsoft Endpoint Manager ( profils de configuration > Périphériques > > Créer un profil https://endpoint.microsoft.com/) > Platform: Windows 10 and later & Profile: Device Control) n’est pas encore disponible. 

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
