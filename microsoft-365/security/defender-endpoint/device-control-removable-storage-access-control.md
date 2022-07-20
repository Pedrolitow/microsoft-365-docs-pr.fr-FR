---
title: Microsoft Defender pour point de terminaison Access Control de stockage amovible du contrôle d’appareil, support de stockage amovible
description: Une procédure pas à pas sur Microsoft Defender pour point de terminaison
ms.prod: m365-security
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
ms.technology: mde
ms.date: 06/24/2022
ms.openlocfilehash: 1900487e4249c344981630d7a11aafd02862f863
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882116"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Microsoft Defender pour point de terminaison Access Control de stockage amovible du contrôle d’appareil

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion stratégie de groupe et Intune gestion OMA-URI/Custom Policy de ce produit sont désormais en disponibilité générale (4.18.2106) : consultez le [blog Tech Community : Protéger votre stockage amovible et votre imprimante avec Microsoft Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="device-control-removable-storage-access-control-overview"></a>Vue d’ensemble de l’Access Control de stockage amovible du contrôle d’appareil

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

|Fonctionnalité|Description|Déployer via Intune|Déployer via stratégie de groupe|
|---|---|---|---|
|Création de groupes multimédias amovibles|Vous permet de créer un groupe de supports amovibles réutilisable|Étape 4 et 6 de la section [, déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Étape 4 et 6 de la section [, déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](#deploying-removable-storage-access-control-by-using-group-policy)|
|Création de stratégie|Vous permet de créer une stratégie pour appliquer chaque groupe de supports amovibles|Étape 5 et 7 de la section [, déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Étapes 5 et 7 de la section [Déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](#deploying-removable-storage-access-control-by-using-group-policy)|
|Application par défaut|Vous permet de définir l’accès par défaut (Refuser ou Autoriser) sur un média amovible s’il n’existe aucune stratégie|Étape 2 de la section [, déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri) | Étape 2 de la section [, déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](#deploying-removable-storage-access-control-by-using-group-policy)|
|Activer ou désactiver les Access Control de stockage amovibles|Si vous définissez Désactiver, il désactive la stratégie de Access Control de stockage amovible sur cet ordinateur| Étape 1 de la section [, déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| Étape 1 de la section [, déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](#deploying-removable-storage-access-control-by-using-group-policy)|
|Capturer des informations sur le fichier|Vous permet de créer une stratégie pour capturer les informations de fichier lorsque l’accès en écriture se produit|  | Étape 10 de la section [, déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe](#deploying-removable-storage-access-control-by-using-group-policy) |

### <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez des Access Control de stockage amovibles sur des appareils Windows 10 et Windows 11 qui ont un client anti-programme malveillant version **4.18.2103.3 ou ultérieure**.

- **4.18.2104 ou version ultérieure** : Ajouter `SerialNumberId`, `VID_PID`, prise en charge de l’objet de stratégie de groupe basée sur filepath, et `ComputerSid`

- **4.18.2105 ou version ultérieure** : ajout de la prise en charge des caractères génériques pour `HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId`la combinaison d’un utilisateur spécifique sur un ordinateur spécifique, d’un disque SSD amovible (SSD SanDisk Extreme)/d’une prise en charge DESI (USB Attached SCSI)

- **4.18.2107 ou version ultérieure** : Ajout de la prise en charge de l’appareil portable Windows (WPD) (pour les appareils mobiles, tels que les tablettes) ; ajouter `AccountName` à la [chasse avancée](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2205 ou version ultérieure** : développez l’application par défaut de **l’imprimante**. Si vous le définissez sur **Refuser**, il bloque également l’imprimante. Par conséquent, si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie personnalisée pour autoriser l’imprimante.

:::image type="content" source="images/powershell.png" alt-text="Interface PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Aucun composant Sécurité Windows n’a besoin d’être actif, car vous pouvez exécuter le stockage amovible Access Control indépendamment de l’état Sécurité Windows.

## <a name="device-control-removable-storage-access-control-policies"></a>Stratégies de Access Control de stockage amovibles du contrôle d’appareil

Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible :

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

### <a name="removable-storage-group"></a>Groupe de stockage amovible

|Nom de la propriété|Description|Options|
|---|---|---|
|**GroupId**|GUID, un ID unique, représente le groupe et sera utilisé dans la stratégie.||
|**DescriptorIdList**|Répertoriez les propriétés de l’appareil que vous souhaitez utiliser pour couvrir le groupe. Pour chaque propriété d’appareil, consultez [Propriétés de l’appareil](device-control-removable-storage-protection.md) pour plus d’informations. Toutes les propriétés respectent la casse. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices``WpdDevices`<p>**BusId** : Par exemple, USB, SCSI<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId** : InstancePathId est une chaîne qui identifie de façon unique l’appareil dans le système, par exemple. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0` Le nombre à la fin (par exemple &0) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple : `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: correspond à cette paire exacte VID/PID<p>`_55E0`: faire correspondre n’importe quel média avec PID=55E0 <p>`0751_`: faire correspondre n’importe quel média avec VID=0751|
|**Matchtype**|Quand plusieurs propriétés d’appareil sont utilisées dans le `DescriptorIDList`, MatchType définit la relation.|**MatchAll** : tous les attributs sous la `DescriptorIdList` relation will be **And** ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système vérifie si l’USB répond aux deux valeurs. <p> **MatchAny** : les attributs sous DescriptorIdList seront **ou** la relation ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système effectue l’application tant que l’USB a une valeur **DeviceID** ou **InstanceID** identique.|

### <a name="access-control-policy"></a>Politique de contrôle d’accès
Vous pouvez utiliser les propriétés suivantes pour créer la stratégie de contrôle d’accès :

| Nom de la propriété | Description | Options |
|---|---|---|
| **PolicyRule Id** | GUID, un ID unique, représente la stratégie et sera utilisé dans les rapports et la résolution des problèmes. | |
| **IncludedIdList** | Les groupes auxquels la stratégie sera appliquée. Si plusieurs groupes sont ajoutés, la stratégie est appliquée à n’importe quel média de tous ces groupes.|L’ID/GUID de groupe doit être utilisé dans cette instance. <p> L’exemple suivant illustre l’utilisation de GroupID : <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Groupe auquel la stratégie ne sera pas appliquée. | L’ID/GUID de groupe doit être utilisé dans cette instance. |
| **ID d’entrée** | Une policyRule peut avoir plusieurs entrées ; chaque entrée avec un GUID unique indique à Device Control une restriction.| |
| **Type (Type)** | Définit l’action pour les groupes de stockage amovibles dans IncludedIDList. <p>Application : Autoriser ou refuser <p>Audit : AuditAllowed ou AuditDenied<p> | Autoriser<p>Refuser <p>AuditAllowed : définit la notification et l’événement lorsque l’accès est autorisé <p>Audit refusé : définit la notification et l’événement lorsque l’accès est refusé ; doit fonctionner avec l’entrée **Deny** .<p> Lorsqu’il existe des types de conflit pour le même média, le système applique le premier type de stratégie. **Autoriser** et **refuser** est un exemple de type de conflit. |
| **Sid** | Sid de l’utilisateur local ou groupe Sid utilisateur ou Sid de l’objet AD, définit s’il faut appliquer cette stratégie à un utilisateur ou à un groupe d’utilisateurs spécifique ; une entrée peut avoir un maximum d’un Sid et une entrée sans sid signifie appliquer la stratégie sur l’ordinateur. |  |
| **ComputerSid** | Sid d’ordinateur local ou groupe Sid d’ordinateur ou Sid de l’objet AD, définit s’il faut appliquer cette stratégie sur un ordinateur ou un groupe d’ordinateurs spécifique ; une entrée peut avoir un maximum d’un ComputerSid et une entrée sans ComputerSid signifie appliquer la stratégie sur l’ordinateur. Si vous souhaitez appliquer une entrée à un utilisateur spécifique et à un ordinateur spécifique, ajoutez Sid et ComputerSid dans la même entrée. |  |
| **Options** | Définit s’il faut afficher ou non une notification |**Lorsque l’option Type Allow est sélectionnée** : <p>0 : rien<p>4 : désactivez **AuditAllowed** et **AuditDenied** pour cette entrée. Même si **Allow** se produit et que le paramètre AuditAllowed est configuré, le système n’envoie pas d’événement. <p>8 : capturez les informations du fichier et disposez d’une copie du fichier comme preuve de l’accès en écriture. <p>16 : capturer les informations de fichier pour l’accès en écriture. <p>**Lorsque le refus de type est sélectionné** : <p>0 : rien<p>4 : désactiver **l’audit refusé** pour cette entrée. Même si **le blocage** se produit et que le paramètre AuditDenied est configuré, le système n’affiche pas de notification. <p>**Quand type **AuditAllowed** est sélectionné** : <p>0 : rien <p>1 : rien <p>2 : événement d’envoi<p> **Lorsque **l’audit** de type refusé est sélectionné** : <p>0 : rien <p>1 : afficher la notification <p>2 : événement d’envoi<p>3 : afficher l’événement de notification et d’envoi |
|AccessMask|Définit l’accès. | **Accès au niveau du disque** : <p>1 : Lecture <p>2 : Écrire <p>4 : Exécuter <p>**Accès au niveau du système de fichiers** : <p>8 : Lecture du système de fichiers <p>16 : Écriture du système de fichiers <p>32 : Exécution du système de fichiers <p><p>Vous pouvez avoir plusieurs accès en effectuant une opération OR binaire. Par exemple, accessMask pour lecture et écriture et exécution est égal à 7 ; AccessMask pour lecture et écriture est 3.|

## <a name="device-control-removable-storage-access-control-scenarios"></a>Scénarios de Access Control de stockage amovibles de contrôle d’appareil

Pour vous aider à vous familiariser avec Microsoft Defender pour point de terminaison Access Control de stockage amovible, nous avons mis en place des scénarios courants à suivre.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scénario 1 : Empêcher l’accès en écriture et en exécution à tous, mais autoriser des bases de données approuvées spécifiques

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible et CD/DVD. Un exemple de stockage amovible et de CD/DVD est le suivant : Groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier [Any Removable Storage and CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Groupe 2 : Bases de données américaines approuvées en fonction des propriétés de l’appareil. Voici un exemple de cas d’usage : ID d’instance - Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier [Group.xmlusbs approuvés](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : Bloquer l’écriture et l’exécution de l’accès, mais autoriser les objets USB approuvés. Voici un exemple de cas d’usage : PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** dans l’exemple [scénario 1 Bloquer l’écriture et l’exécution d’accès, mais autoriser le fichier approuvé USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Stratégie 2 : Auditer l’accès à l’écriture et à l’exécution aux objets usb autorisés. Voici un exemple de cas d’usage : PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** dans l’exemple [de scénario 1 Auditer et exécuter l’accès au fichier USBs.xmlapprouvé](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scénario 2 : Auditer l’accès en écriture et en exécution à tous les objets usb non approuvés spécifiques, sauf bloquer

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible et CD/DVD. Voici un exemple de cas d’usage : Groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier [De stockage amovible et cd-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Groupe 2 : objets usb non approuvés basés sur les propriétés de l’appareil, par exemple, ID de fournisseur/ID de produit, nom convivial - Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichiers [usBs non approuvés Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : bloquer l’accès à l’écriture et à l’exécution à tous les objets usb non approuvés spécifiques, sauf à bloquer. Voici un exemple de cas d’usage : PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** dans l’exemple [scénario 2 Auditer et exécuter l’accès à tous les fichiers USBs.xmlnon approuvés, sauf bloquer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Stratégie 2 : Auditer l’accès en écriture et en exécution à d’autres personnes. Voici un exemple de cas d’usage : PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** dans l’exemple [scénario 2 Auditer et exécuter l’accès à others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fichier.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-intune-oma-uri"></a>Déploiement et gestion des Access Control de stockage amovibles à l’aide de Intune OMA-URI

La fonctionnalité De stockage amovible Access Control vous permet d’appliquer une stratégie à l’aide d’OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer à utiliser les Access Control de stockage amovibles, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder aux Access Control de stockage amovibles et les utiliser, vous devez disposer d’Microsoft 365 E3 ou de Microsoft 365 E5.

### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit disposer des autorisations nécessaires pour créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser l’un des rôles intégrés avec ces autorisations.

- Rôle gestionnaire de stratégies et de profils
- Rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lire/Supprimer/Afficher les rapports activées pour les profils de configuration d’appareil
- Administrateur général

### <a name="deploying-removable-storage-access-control-by-using-intune-oma-uri"></a>Déploiement de Access Control de stockage amovible à l’aide de Intune OMA-URI

Pour bloquer une classe de stockage amovible spécifique, mais autoriser un média spécifique, vous pouvez utiliser « IncludedIdList a group through PrimaryId and ExcludedIDList a group through DeviceId/HardwareId/etc. ».

Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>) **> Appareils > Créer un profil > Platform : Windows 10 et versions ultérieures, Type de profil : Modèles > Personnalisé**

1. Activez ou désactivez le contrôle d’appareil comme suit :

   - Sous **Paramètres de configuration > personnalisés**, cliquez sur **Ajouter**.
   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** **en tant qu’activer le contrôle d’appareil**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **Type de données** **en tant qu’entier**
     - **Valeur** **1**

       `Disable: 0`
       `Enable: 1`

     - Cliquez sur **Save (Enregistrer)**.

   :::image type="content" source="images/enable-rsac.png" alt-text="Capture d’écran de l’activation de la stratégie de Access Control de stockage amovible" lightbox="images/enable-rsac.png":::

2. Définir l’application par défaut :

   Vous pouvez définir l’accès par défaut (Refuser ou Autoriser) pour toutes les fonctionnalités de contrôle d’appareil (`RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`). `PrinterDevices`

   Par exemple, vous avez une **stratégie Refuser** ou **Autoriser** pour `RemovableMediaDevices`, mais vous n’avez pas de stratégie pour `CdRomDevices` ou `WpdDevices`. Vous pouvez définir le **refus par défaut** via cette stratégie, puis l’accès en lecture/écriture/exécution à `CdRomDevices` ou `WpdDevices` sera bloqué. Si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie **Autoriser** pour votre imprimante ; Sinon, cette mise en œuvre par défaut sera également appliquée aux imprimantes.

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** en tant que **refus par défaut**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **Type de données** **en tant qu’entier**
     - **Valeur** **1** ou **2**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - Cliquez sur **Save (Enregistrer)**.

   :::image type="content" source="images/default-deny.png" alt-text="Capture d’écran de la définition de l’application par défaut en tant que refus" lightbox="images/default-deny.png":::

3. Auditer le refus par défaut :

   Vous pouvez créer une stratégie d’audit pour le refus par défaut comme suit :

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** en tant que **refus par défaut d’audit**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf3520ea7-fd1b-4237-8ebc-96911db44f8e%7d/RuleData`

       :::image type="content" source="images/audit-default-deny-1.png" alt-text="Capture d’écran de la création d’une stratégie d’audit de refus par défaut" lightbox="images/audit-default-deny-1.png":::

     - **Type de données** **sous forme de chaîne (fichier XML)**
     - **Fichier XML personnalisé** en tant que **fichier audit par défaut Deny.xml** .

       Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20Default%20Deny.xml>

       Utilisez les données XML suivantes pour créer votre stratégie d’audit pour le refus par défaut :

       :::image type="content" source="images/audit-default-deny-xml-file-1.png" alt-text="Capture d’écran du fichier xml de refus par défaut d’audit":::

4. ReadOnly - Groupe :

   Vous pouvez créer un groupe de stockage amovible avec un accès ReadOnly comme suit :

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** **de n’importe quel groupe de stockage amovible**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="Capture d’écran de la création d’un groupe de stockage amovible" lightbox="images/any-removable-storage-group.png":::

     - **Type de données** **sous forme de chaîne (fichier XML)**
       - **XML personnalisé** en tant que **stockage amovible et cd-DVD et fichier Group.xmlWPD**

         Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

         Utilisez les données XML suivantes pour créer « Tout stockage amovible et CD-DVD et groupe WPD » avec accès En lecture seule :

         :::image type="content" source="images/read-only-group-xml-file.png" alt-text="Capture d’écran du fichier xml de groupe en lecture seule":::

5. ReadOnly - Stratégie :

   Vous pouvez créer une stratégie ReadOnly et l’appliquer au groupe de stockage amovible ReadOnly pour autoriser l’activité de lecture comme suit :

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** comme **autoriser l’activité de lecture**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf7e75634-7eec-4e67-bec5-5e7750cb9e02%7d/RuleData`

       :::image type="content" source="images/allow-read-activity.png" alt-text="Capture d’écran de la stratégie Autoriser l’activité de lecture" lightbox= "images/allow-read-activity.png":::

     - **Type de données** **sous forme de chaîne (fichier XML)**
     - **Fichier XML personnalisé** en tant **qu’autorisation Read.xml**

       Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       Utilisez les données XML suivantes pour créer une stratégie ReadOnly et l’appliquer au groupe de stockage amovible ReadOnly :

       :::image type="content" source="images/read-only-policy-xml-file.png" alt-text="Capture d’écran du fichier xml de stratégie en lecture seule":::

6. Créer un groupe pour le média autorisé : vous pouvez créer votre groupe de supports autorisé comme suit :
   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** en tant que **groupe USB approuvé**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b65fa649a-a111-4912-9294-fb6337a25038%7d/GroupData`

       :::image type="content" source="images/create-group-allowed-medias.png" alt-text="Capture d’écran de la création d’un groupe usb approuvé" lightbox="images/create-group-allowed-medias.png":::

     - **Type de données** **sous forme de chaîne (fichier XML)**
     - **XML personnalisé** en tant que fichier **Group.xmlusb approuvé**

       Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml>

       Utilisez les données XML suivantes pour créer un groupe de supports autorisé :

       :::image type="content" source="images/create-group-allowed-medias-xml-file.png" alt-text="Capture d’écran de la création d’un groupe pour un fichier xml multimédia autorisé":::

7. Créez une stratégie pour autoriser le groupe USB approuvé : vous pouvez créer une stratégie pour autoriser le groupe USB approuvé comme suit :
   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** **en tant qu’autorisation d’accès et informations de fichier d’audit**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bb2061588-029e-427d-8404-6dfec096a571%7d/RuleData`

       :::image type="content" source="images/allow-access-audit-file-information-1.png" alt-text="Capture d’écran des informations autoriser l’accès et le fichier d’audit" lightbox= "images/allow-access-audit-file-information-1.png":::

     - **Type de données** **sous forme de chaîne (fichier XML)**
     - **XML personnalisé** en tant **qu’autorisation d’accès complet et d’audit file.xml**  fichier

       Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20full%20access%20and%20audit%20file.xml>

       Utilisez les données XML suivantes pour créer une stratégie pour autoriser le groupe USB approuvé :

       :::image type="content" source="images/create-policy-allow-approved-usb-group-xml-intune.png" alt-text="Capture d’écran de la création d’une stratégie pour autoriser le fichier XML du groupe USB approuvé":::

       Que signifie « 47 » dans la stratégie ? C’est 9 + 2 + 36 = 47 :

       - Accès en lecture : 1 + 8 = 9.
       - Accès en écriture : niveau disque 2.
       - Exécution : 4 + 32 = 36.

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Déploiement et gestion d’une stratégie à l’aide de Intune’interface utilisateur

Cette fonctionnalité est disponible dans le Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). Accédez à la stratégie de création **de la surface d’attaque** >  de **sécurité** >  du point de **terminaison**. Choisissez **Plateforme : Windows 10 et versions ultérieures** avec **Profil : Contrôle d’appareil**.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-group-policy"></a>Déploiement et gestion des Access Control de stockage amovibles à l’aide de stratégie de groupe

La fonctionnalité de Access Control de stockage amovible vous permet d’appliquer une stratégie à l’aide de stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

Avant de commencer à utiliser les Access Control de stockage amovibles, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder aux Access Control de stockage amovibles et les utiliser, vous devez disposer d’Microsoft 365 E3 ou de Microsoft 365 E5.

### <a name="deploying-removable-storage-access-control-by-using-group-policy"></a>Déploiement de Access Control de stockage amovible à l’aide de stratégie de groupe

1. Activez ou désactivez les Access Control de stockage amovibles :

   Vous pouvez activer le contrôle d’appareil comme suit :

   - Accédez à **Configuration de l’ordinateur > modèles d’administration > composants Windows > fonctionnalités > antivirus Microsoft Defender > le contrôle d’appareil**
   - Dans la fenêtre **Contrôle d’appareil** , sélectionnez **Activé**.

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="Capture d’écran de l’activation de RSAC à l’aide de stratégie de groupe " lightbox="images/enable-rsac-gp.png":::

2. Définir l’application par défaut :

   Vous pouvez définir l’accès par défaut (Refuser ou Autoriser) pour toutes les fonctionnalités de contrôle d’appareil (RemovableMediaDevices, CdRomDevices, WpdDevices, PrinterDevices).

   Par exemple, vous disposez d’une stratégie Deny ou Allow pour RemovableMediaDevices, mais vous n’avez pas de stratégie pour CdRomDevices ou WpdDevices. Vous définissez le refus par défaut via cette stratégie, puis l’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices est bloqué. Si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie d’autorisation pour l’imprimante. Sinon, cette application par défaut sera également appliquée à l’imprimante.

   - Accédez à **Configuration de l’ordinateur > modèles d’administration > composants Windows > fonctionnalités de > antivirus Microsoft Defender > contrôle d’appareil > sélectionner l’application par défaut du contrôle d’appareil**

   - Dans la fenêtre **Sélectionner l’application par défaut du contrôle d’appareil** , sélectionnez **Refuser par défaut** :

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="Capture d’écran de la définition de l’application par défaut = Refuser à l’aide de stratégie de groupe" lightbox="images/set-default-enforcement-deny-gp.png":::

3. Auditer le refus par défaut :

   Utilisez les données XML suivantes pour créer une stratégie d’audit pour le refus par défaut :

   :::image type="content" source="images/audit-default-deny-gp.png" alt-text="Capture d’écran de l’audit des données xml de refus par défaut":::

4. ReadOnly - Groupe :

   Utilisez les données XML suivantes pour créer un groupe de stockage amovible avec accès ReadOnly :

   :::image type="content" source="images/read-only-group-gp.png" alt-text="Capture d’écran des données xml de groupe de stockage amovible en lecture seule":::

5. ReadOnly - Stratégie :

   Utilisez les données XML suivantes pour créer une stratégie ReadOnly et appliquer au groupe de stockage amovible ReadOnly pour autoriser l’activité de lecture :

    :::image type="content" source="images/read-only-policy-gp.png" alt-text="Capture d’écran des données XML de stratégie en lecture seule" lightbox="images/read-only-policy-gp.png":::

6. Créer un groupe pour les supports autorisés :

   Utilisez les données XML suivantes pour créer un groupe de supports de stockage amovible autorisé :

   :::image type="content" source="images/create-group-allowed-medias-gp.png" alt-text="Capture d’écran des données xml permettant de créer un groupe pour les supports autorisés" lightbox="images/create-group-allowed-medias-gp.png":::

7. Créez une stratégie pour autoriser le groupe USB approuvé :

   Utilisez les données XML suivantes pour créer une stratégie pour autoriser le groupe USB approuvé :

   :::image type="content" source="images/create-policy-allow-approved-usb-group-xml.png" alt-text="Capture d’écran des données XML permettant de créer une stratégie pour autoriser le groupe USB approuvé à l’aide de stratégie de groupe" lightbox="images/create-policy-allow-approved-usb-group-xml.png":::

   Que signifie « 47 » dans la stratégie ? C’est 9 + 2 + 36 = 47 :

   - Accès en lecture : 1+8 = 9.
   - Accès en écriture : niveau disque 2.
   - Exécution : 4 + 32 = 36.

8. Combinez des groupes en un seul fichier XML :

   Vous pouvez combiner des groupes de stratégies de contrôle d’appareil dans un fichier XML comme suit :

   - Accédez à **Modèles d’administration** **de configuration** \> ordinateur **Composants** \> \> Windows Microsoft **Defender Antivirus** \> **Device Control** \> **Définir des groupes de stratégies de contrôle d’appareil**.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="Capture d’écran de définir des groupes de stratégies de contrôle d’appareil" lightbox="images/define-device-control-policy-grps-gp.png":::

   - Dans la fenêtre **Définir des groupes de stratégies de contrôle d’appareil** , entrez le chemin d’accès du fichier contenant les données des groupes XML.

     Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml>

     Voici le schéma xml des groupes de stratégies de contrôle d’appareil :

     :::image type="content" source="images/combine-grps-xml-file-gp.png" alt-text="Capture d’écran de la combinaison de groupes dans un fichier XML":::

9. Combinez les stratégies en un seul fichier XML :

   Vous pouvez combiner des règles de stratégie de contrôle d’appareil dans un fichier XML comme suit :

   - Accédez à **Configuration de l’ordinateur > modèles d’administration > composants Windows > microsoft Defender Antivirus > Device Control > Définir des règles de stratégie de contrôle d’appareil**

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="Capture d’écran de la définition des règles de stratégie de contrôle d’appareil" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - Dans la fenêtre **Définir les règles de stratégie de contrôle d’appareil** , sélectionnez **Activé**, puis entrez le chemin d’accès du fichier contenant les données de règles XML.

     Chemin du fichier XML : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Policies.xml>

     Voici le schéma xml des règles de stratégie de contrôle d’appareil :

    :::image type="content" source="images/combine-policies-xml-gp.png" alt-text="Capture d’écran de la combinaison de stratégies dans un fichier XML":::

10. Définir l’emplacement d’une copie du fichier (preuve) :

    Si vous souhaitez avoir une copie du fichier (preuve) lorsque l’accès en écriture se produit, vous devez définir l’emplacement où le système peut enregistrer la copie.

    - Accédez à **Configuration de l’ordinateur > modèles d’administration > composants Windows > l’antivirus Microsoft Defender > le contrôle d’appareil > définir l’emplacement distant des données de preuve de contrôle d’appareil**.

    - Dans la fenêtre **Définir l’emplacement distant des données de preuve de Contrôle d’appareil** , **sélectionnez Activé** et entrez le chemin d’accès du dossier de partage local ou réseau.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="Capture d’écran de l’emplacement distant des données de preuve Définir le contrôle d’appareil" lightbox="images/evidence-data-remote-location-gp.png":::

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données de Access Control de stockage amovibles du contrôle d’appareil dans Microsoft Defender pour point de terminaison

Le [portail Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) affiche les événements déclenchés par le Access Control de stockage amovible Device Control. Pour accéder à la sécurité Microsoft 365, vous devez disposer de l’abonnement suivant :

- Rapports Microsoft 365 pour E5

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

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Comment générer un GUID pour l’ID de groupe/ID PolicyRule/ID d’entrée ?

Vous pouvez générer un GUID via des open source en ligne ou via PowerShell - [Guide pratique pour générer un GUID via PowerShell](/powershell/module/microsoft.powershell.utility/new-guid)

![image](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Quelles sont les limitations de stratégie et de média de stockage amovibles ?

À partir du Centre d’administration Microsoft Endpoint Manager (Intune) ou par le biais de Microsoft API Graph, l’appel principal est effectué via OMA-URI (GET to read ou PATCH to update), et par conséquent, la limitation est la même que n’importe quel profil de configuration personnalisé OMA-URI dans Microsoft, qui est officiellement de 350 000 caractères pour les fichiers XML.

Par exemple, si vous avez besoin de deux blocs d’entrées par SID utilisateur pour « Autoriser » /« Auditer autorisé » des utilisateurs spécifiques et de deux blocs d’entrées à la fin de « Refuser », vous serez en mesure de gérer 2 276 utilisateurs.

### <a name="why-does-the-policy-not-work"></a>Pourquoi la stratégie ne fonctionne-t-elle pas ?

1. La raison la plus courante est qu’il n’existe aucune version requise du [client anti-programme malveillant](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. Une autre raison peut être que le fichier XML n’est pas correctement mis en forme, par exemple, ne pas utiliser la mise en forme markdown correcte pour le caractère « & » dans le fichier XML, ou que l’éditeur de texte peut ajouter une marque d’ordre d’octet (BOM) 0xEF 0xBB 0xBF au début des fichiers, ce qui entraîne le non-fonctionnement de l’analyse XML. Une solution simple consiste à télécharger [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (sélectionnez **Raw** , puis **Enregistrer sous**), puis mettez à jour.

3. Si vous déployez et gérez la stratégie à l’aide de stratégie de groupe, veillez à combiner tous les PolicyRule dans un fichier XML au sein d’un nœud parent appelé PolicyRules et tous les groupes dans un fichier XML dans un nœud parent appelé Groupes ; si vous gérez via Intune, conservez un seul fichier XML PolicyRule, la même chose, un seul fichier XML de groupe.

Si cela ne fonctionne toujours pas, vous pouvez nous contacter et partager la cabine de support en exécutant cmd avec l’administrateur : « %programfiles%\Windows Defender\MpCmdRun.exe » -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Il n’existe aucune expérience utilisateur de configuration pour « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil » sur mon stratégie de groupe

Nous ne réportons pas l’expérience utilisateur de configuration stratégie de groupe, mais vous pouvez toujours obtenir les fichiers adml et admx associés en cliquant sur « Raw » et « Enregistrer sous » dans les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Comment savoir si la dernière stratégie a été déployée sur l’ordinateur cible ?

Vous pouvez exécuter « Get-MpComputerStatus » sur PowerShell en tant qu’administrateur. La valeur suivante indique si la dernière stratégie a été appliquée à l’ordinateur cible.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>Comment savoir quel ordinateur utilise une version obsolète du client anti-programme malveillant dans l’organisation ?

Vous pouvez utiliser la requête suivante pour obtenir la version du client anti-programme malveillant sur le portail de sécurité Microsoft 365 :

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
