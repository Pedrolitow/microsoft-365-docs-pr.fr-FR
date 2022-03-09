---
title: Microsoft Defender for Endpoint Device Control Removable Stockage Access Control, removable storage media
description: Une présentation de Microsoft Defender pour point de terminaison
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
ms.date: 02/07/2022
ms.openlocfilehash: a0bca99258bd256797437cdc4756910fc713cf26
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63401177"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Contrôle d’appareil amovible Microsoft Defender for Endpoint Stockage Access Control

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion des stratégies de groupe et la gestion des stratégies personnalisées/OMA-URI Intune de ce produit sont désormais généralement disponibles (4.18.2106) : consultez le blog Tech Community : Protéger votre stockage amovible et votre imprimante avec [Microsoft Defender pour endpoint](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).


Microsoft Defender for Endpoint Device Control Removable Stockage Access Control vous permet d’accomplir la tâche suivante :

- audit, autoriser ou empêcher l’accès en lecture, écriture ou exécution au stockage amovible avec ou sans exclusion

<br/><br/>

|Privilège|Autorisation|
|---|---|
|Accès|Lecture, Écriture, Exécution|
|Action Mode|Auditer, autoriser, empêcher|
|Prise en charge du programme CSP|Oui|
|Prise en charge des GPO|Oui|
|Prise en charge basée sur l’utilisateur|Oui|
|Prise en charge basée sur l’ordinateur|Oui|

<br/><br/>

|Fonctionnalité|Description|Déployer via Intune|Déployer par le biais d’une stratégie de groupe|
|---|---|---|---|
|Création d’un groupe de médias amovibles|Vous permet de créer un groupe de médias amovible réutilisable|Étape 1 et étape 3 de la section Déploiement [d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 1 de la section Déploiement [d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy)|
|Création de stratégie|Permet de créer une stratégie pour appliquer chaque groupe de médias amovible|Étapes 2 et 3 de la section Déploiement [d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 2 de la section Déploiement [d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Application par défaut|Vous permet de définir l’accès par défaut (Refuser ou Autoriser) aux médias amovibles s’il n’existe aucune stratégie|Étape 4 de la section Déploiement [d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 3 de la section Déploiement [d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Activer ou désactiver le contrôle d’accès Stockage amovible|Si vous définissez Disable, la stratégie Demovable Stockage Access Control est désactivée sur cet ordinateur.| Étape 5 de la section Déploiement [d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 4 de la section Déploiement [d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Capturer les informations de fichier|Vous permet de créer une stratégie pour capturer des informations de fichier lorsque l’accès en écriture se produit| Étape 2 et 6 de la section Déploiement [d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 2 et 5 de la section Déploiement [d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez le contrôle d’Stockage amovible sur les appareils Windows 10 et Windows 11 qui ont un client anti-programme malveillant version **4.18.2103.3** ou ultérieure.

- **4.18.2104** ou version ultérieure : Ajouter SerialNumberId, VID_PID, prise en charge des GPO basés sur des chemins d’fichiers, ComputerSid

- **4.18.2105** ou version ultérieure : ajouter la prise en charge des caractères génériques pour HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, la combinaison d’un utilisateur spécifique sur un ordinateur spécifique, la prise en charge du SSD (Un SSD Extrême SanDisk)/USB Attached SCSI (UAS)

- **4.18.2107** ou ultérieure : ajouter la prise en charge de l’appareil portable Windows (WPD) (pour les appareils mobiles, tels que les tablettes) ; ajouter AccountName dans le recherche avancée [](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2111** ou version ultérieure : ajouter « Activer ou désactiver le contrôle d’accès Stockage amovible » , « Application par défaut » , heure de mise à jour de la stratégie de l’ordinateur client via PowerShell, informations sur les fichiers

:::image type="content" source="images/powershell.png" alt-text="Interface PowerShell.":::

> [!NOTE]
> Aucun des Sécurité Windows ne doit être actif, car vous pouvez exécuter le contrôle d’accès Stockage amovible indépendamment de l’état Sécurité Windows’accès.

## <a name="policy-properties"></a>Propriétés de stratégie

Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible :

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

### <a name="removable-storage-group"></a>Groupe de Stockage amovible

<br/><br/>

|Nom de la propriété|Description|Options|
|---|---|---|
|**GroupId**|GUID, un ID unique, représente le groupe et sera utilisé dans la stratégie.||
|**DescriptorIdList**|List the device properties you want to use to cover in the group. Pour chaque propriété d’appareil, voir [Propriétés de l’appareil](device-control-removable-storage-protection.md) pour plus d’informations. Toutes les propriétés sont sensibles à la cas. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId** : par exemple, USB, SCSI<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId** : InstancePathId est une chaîne qui identifie de manière unique l’appareil dans le système, par exemple, `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. Le numéro à la fin (par exemple, &0) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple : `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>0751_55E0 : correspondre à cette paire VID/PID exacte<p>55E0 : faire correspondre n’importe quel média avec PID=55E0 <p>0751 : faire correspondre n’importe quel média avec VID=0751|
|**MatchType**|Lorsqu’il existe plusieurs propriétés d’appareil utilisées dans `DescriptorIDList`le , MatchType définit la relation.|**MatchAll** : tous les attributs `DescriptorIdList` sous la relation **Will be And** ; par exemple, `DeviceID` `InstancePathID`si l’administrateur met et, pour chaque clé USB connectée, le système vérifie si la clé USB correspond aux deux valeurs. <p> **MatchAny :** les attributs sous la relation DescriptorIdList seront **Or** ; par exemple, si `DeviceID` `InstancePathID`l’administrateur met et, pour chaque clé USB connectée, le système fait l’application tant que la clé USB a une valeur **DeviceID** ou **InstanceID** identique. |

### <a name="access-control-policy"></a>Politique de contrôle d’accès

<br/><br/>

| Nom de la propriété | Description | Options |
|---|---|---|
| **PolicyRuleId** | GUID, un ID unique, représente la stratégie et sera utilisé dans le rapport et la résolution des problèmes. | |
| **IncludedIdList** | Groupe(s) à appliquer à la stratégie. Si plusieurs groupes sont ajoutés, la stratégie est appliquée à n’importe quel média de tous ces groupes.|L’ID de groupe/GUID doit être utilisé à cette instance. <p> L’exemple suivant illustre l’utilisation de GroupID : <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | Les groupes à qui la stratégie ne sera pas appliquée. | L’ID de groupe/GUID doit être utilisé à cette instance. |
| **ID d’entrée** | Un policyRule peut avoir plusieurs entrées ; chaque entrée avec un GUID unique indique à Device Control une restriction.| |
| **Type** | Définit l’action pour les groupes de stockage amovibles dans IncludedIDList. <p>Application : autoriser ou refuser <p>Audit : AuditAllowed ou AuditDenied<p> | Autoriser<p>Refuser <p>AuditAllowed : définit la notification et l’événement lorsque l’accès est autorisé <p>AuditDenied : définit la notification et l’événement lorsque l’accès est refusé ; doit fonctionner avec **l’entrée** de refus.<p> Lorsqu’il existe des types de conflit pour le même média, le système applique le premier de la stratégie. Allow et **Deny** sont un exemple de **type de conflit**. |
| **Sid** | Le sid d’utilisateur local ou le groupe sid d’utilisateur ou le sid de l’objet AD, définit s’il faut appliquer cette stratégie sur un utilisateur ou un groupe d’utilisateurs spécifique ; une entrée peut avoir un maximum d’un Sid et une entrée sans sid signifie appliquer la stratégie sur l’ordinateur. |  |
| **ComputerSid** | Le sid d’ordinateur local ou le groupe sid d’ordinateur ou le sid de l’objet AD, définit s’il faut appliquer cette stratégie sur un ordinateur ou un groupe d’ordinateurs spécifique ; une entrée peut avoir un maximum d’un ComputerSid et une entrée sans ComputerSid signifie appliquer la stratégie sur l’ordinateur. Si vous souhaitez appliquer une entrée à un utilisateur spécifique et à un ordinateur spécifique, ajoutez Sid et ComputerSid dans la même entrée. |  |
| **Options** | Définit s’il faut afficher la notification ou non |**Lorsque le type d’autoriser est sélectionné** : <p>0 : rien<p>4 : désactivez **AuditAllowed** et **AuditDenied** pour cette entrée. Même si **l’autoriser** se produit et que le paramètre AuditAllowed est configuré, le système n’envoie pas d’événement. <p>8 : capturer des informations de fichier et avoir une copie du fichier en tant que preuve de l’accès en écriture. <p>16 : capturer les informations de fichier pour l’accès en écriture. <p>**Lorsque le refus de type est sélectionné** : <p>0 : rien<p>4 : désactivez **AuditDenied** pour cette entrée. Même si **le blocage** se produit et que le paramètre AuditDenied est configuré, le système n’affiche pas de notification. <p>**Lorsque type **AuditAllowed est** sélectionné** : <p>0 : rien <p>1 : rien <p>2 : événement d’envoi<p>3 : événement d’envoi <p> **Lorsque type **AuditDenied** est sélectionné** : <p>0 : rien <p>1 : afficher la notification <p>2 : événement d’envoi<p>3 : afficher la notification et envoyer un événement |
|AccessMask|Définit l’accès. | **Accès au niveau du disque** : <p>1 : lecture <p>2 : Écriture <p>4 : Exécuter <p>**Accès au niveau du système de fichiers** : <p>8 : Lecture du système de fichiers <p>16 : Écriture du système de fichiers <p>32 : Exécution du système de fichiers <p><p>Vous pouvez avoir plusieurs accès en faisant une opération OR binaire, par exemple, AccessMask pour la lecture et l’écriture et l’exécution sera 7 ; AccessMask pour lecture et écriture est 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>Scénarios courants Stockage contrôle d’accès des périphériques amovibles

Pour vous aider à vous familiariser avec Microsoft Defender pour endpoint Removable Stockage Access Control, nous avons mis en place des scénarios courants que vous pouvez suivre.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scénario 1 : empêcher l’accès en écriture et en exécution à tous les utilisateurs approuvés spécifiques, mais autoriser

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible et CD/DVD. Un exemple de stockage amovible et de CD/DVD est le groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Stockage amovible et [de CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Groupe 2 : approbation de base de données américaines en fonction des propriétés de l’appareil. Voici un exemple de ce cas d’utilisation : ID d’instance - Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données approuvé.[](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples)

    > [!TIP]
    > Remplacez `&` par `&amp;` dans la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : bloquer l’écriture et exécuter l’accès, mais autoriser les usbs approuvés. Voici un exemple de ce cas d’utilisation : PolicyRule **c544a991-5786-4402-949e-a032cb790d0e dans** l’exemple Scénario 1 Bloquer l’écriture et exécuter l’accès, mais autoriser le fichier [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) approuvé.

    2. Stratégie 2 : auditer l’accès en écriture et en cours d’exécution aux usbs autorisés. Voici un exemple de ce cas d’utilisation : PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** dans l’exemple scénario [1 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et en exécution au fichier USBs.xmlapprouvé.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>Scénario 2 : Auditer l’accès en écriture et en exécution à tous les services de sécurité universels non désapprouvés, sauf bloquer

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible et CD/DVD. Voici un exemple de ce cas d’utilisation : Groupe **9b28fae8-72f7-4267-a1a5-685f747a7146** dans l’exemple de fichier de Stockage amovible et [de CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples).

    2. Groupe 2 : listes de contrôle d’appareil non désapprouvées en fonction des propriétés de l’appareil, par exemple, ID fournisseur/ID de produit, nom convivial – Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier Group.xmlde base de données des états- [Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) non accepté.

    > [!TIP]
    > Remplacez `&` par `&amp;` dans la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : bloquer l’accès en écriture et en exécution à tous les usbs non désapprouvés spécifiques, sauf à les bloquer. Voici un exemple de ce cas d’utilisation : PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’écriture et l’exécution de l’accès à tous les fichiers USBs.xmlnon acceptés, sauf bloquer.

    2. Stratégie 2 : auditer l’accès en écriture et exécuter l’accès à d’autres personnes. Voici un exemple de ce cas d’utilisation : PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** dans l’exemple Scénario [2 Auditer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) l’accès en écriture et en exécution au fichier others.xml.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion d’une stratégie via une stratégie de groupe

La fonctionnalité de contrôle d Stockage’accès amovible vous permet d’appliquer une stratégie via la stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

Avant de commencer avec le contrôle d’accès Stockage amovible, vous devez confirmer [votre abonnement Microsoft 365'accès.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder au contrôle d’accès Stockage et l’utiliser, vous devez Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Déploiement d’une stratégie via une stratégie de groupe

1. Combinez tous les groupes au sein `<Groups>` `</Groups>` d’un fichier xml.

    L’image suivante illustre l’exemple du scénario 1 : empêcher l’accès en écriture et en exécution à tous les [usbs](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs) approuvés mais autorisés.

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Écran affichant les paramètres de configuration qui autorisent des usbs approuvés spécifiques sur les appareils.":::

2. Combinez toutes les règles dans `<PolicyRules>` `</PolicyRules>` un fichier xml.

    Si vous souhaitez limiter un utilisateur spécifique, utilisez la propriété SID dans l’entrée. S’il n’existe aucun SID dans l’entrée de stratégie, l’entrée est appliquée à l’instance de connexion de tout le monde pour l’ordinateur.
    
    Si vous souhaitez surveiller les informations de fichier pour l’accès en écriture, utilisez le bon AccessMask avec l’option de droite (8 ou 16) ; voici l’exemple [d’informations de fichier de capture](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    L’image suivante illustre l’utilisation de la propriété SID et un exemple de scénario 1 : empêcher l’accès en écriture et en exécution à tous les [usbs](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs) approuvés, sauf autoriser.

    :::image type="content" source="images/usage-sid-property.png" alt-text="Écran affichant un code qui indique l’utilisation de l’attribut de propriété SID.":::

3. Enregistrez les fichiers XML  \> de règle et de groupe sur le dossier de partage réseau et placez le chemin d’accès du dossier de partage réseau dans le paramètre de stratégie de groupe : **Modèles** \> d’administration  de configuration ordinateur **Windows Composants** \> **Antivirus Microsoft Defender** \> **Contrôle de périphérique : « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil** ».

   Si vous ne trouvez pas l’UX de configuration de stratégie dans la stratégie de groupe, vous pouvez télécharger les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) en sélectionnant **Raw** , puis **Enregistrer** sous.

   - L’ordinateur cible doit pouvoir accéder au partage réseau pour avoir la stratégie. Toutefois, une fois la stratégie lue, la connexion de partage réseau n’est plus nécessaire, même après le redémarrage de l’ordinateur.

    :::image type="content" source="images/device-control.png" alt-text="Écran Contrôle d’appareil.":::

4. Application par défaut : vous permet de définir l’accès par défaut (Refuser ou Autoriser) aux médias amovibles s’il n’existe aucune stratégie. Par exemple, vous avez uniquement une stratégie (refuser ou autoriser) pour RemovableMediaDevices, mais vous n’avez pas de stratégie pour CdRomDevices ou WpdDevices, et vous définissez refuser par défaut via cette stratégie, l’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices sera bloqué.

   - Une fois ce paramètre déployé, vous verrez **l’option Autoriser ou** **Refuser par défaut**.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Code PowerShell autoriser ou refuser par défaut":::

5. Activez ou désactivez le contrôle d Stockage’accès amovible : vous pouvez définir cette valeur pour désactiver temporairement le contrôle d’Stockage’accès amovible.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Paramètres de contrôle d’appareil":::

   - Une fois ce paramètre déployé, vous verrez « Activé » ou « Désactivé » : « Désactivé » signifie que cette machine n’a pas de stratégie de contrôle d’accès Stockage amovible en cours d’exécution.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Contrôle d’appareil activé ou désactivé dans le code PowerShell":::

6. Définissez l’emplacement d’une copie du fichier : si vous souhaitez obtenir une copie du fichier lors de l’accès en écriture, vous devez définir l’emplacement où le système peut enregistrer la copie.
    
    Vous devez déployer cette option en même temps que accessMask et Option , voir l’étape 2 ci-dessus.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="Stratégie de groupe : définir locaiton pour les preuves de fichier":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Déploiement et gestion d’une stratégie via Intune OMA-URI

La fonctionnalité Stockage contrôle d’accès amovible vous permet d’appliquer une stratégie via OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer avec le contrôle d’accès Stockage amovible, vous devez confirmer [votre abonnement Microsoft 365'accès.](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder au contrôle d’accès Stockage et l’utiliser, vous devez Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit être autorisé à créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser n’importe quel rôle intégré avec ces autorisations.

- Rôle gestionnaire de stratégies et de profils

- Rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lecture/Supprimer/Afficher les rapports pour les profils de configuration d’appareil

- Administrateur général

### <a name="deploying-policy-via-oma-uri"></a>Déploiement d’une stratégie via OMA-URI

Microsoft Endpoint Manager centre d’administration  **des appareils (**<https://endpoint.microsoft.com/>) \> \> Profils de **configuration** \> \> des appareils Créer une plateforme de profil **: Windows 10 profil et & profil : personnalisé**

1. Pour chaque groupe, créez une règle OMA-URI :

    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Par exemple, pour tout **stockage amovible et groupe CD/DVD** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Type de données : chaîne (fichier XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Fichier xml pour le type de données STRING.":::

2. Pour chaque stratégie, créez également un OMA-URI :

    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Par exemple, pour la règle Bloquer l’écriture et exécuter l’accès, mais autoriser les règles de base de données utilisateur **approuvées** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Type de données : chaîne (fichier XML)
       
    Si vous souhaitez surveiller les informations de fichier pour l’accès en écriture, utilisez le bon AccessMask avec l’option de droite (8 ou 16) ; voici l’exemple [d’informations de fichier de capture](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Application par défaut : vous permet de définir l’accès par défaut (Refuser ou Autoriser) aux médias amovibles s’il n’existe aucune stratégie. Par exemple, vous avez uniquement une stratégie (refuser ou autoriser) pour RemovableMediaDevices, mais vous n’avez pas de stratégie pour CdRomDevices ou WpdDevices, et vous définissez refuser par défaut via cette stratégie, l’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices sera bloqué.

    - OMA-URI : `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Type de données : Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Une fois ce paramètre déployé, vous verrez **l’option Autoriser ou** **Refuser par défaut**.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Code PowerShell d’application par défaut":::

4. Activez ou désactivez le contrôle d Stockage’accès amovible : vous pouvez définir cette valeur pour désactiver temporairement le contrôle d’Stockage’accès amovible.

   - OMA-URI : `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Type de données : Int `Disable: 0`
     `Enable: 1`

   - Une fois ce paramètre déployé, l’effet **Activé** ou **Désactivé s’active.**

    **Désactivée signifie** que la stratégie de contrôle d’accès Stockage’est pas en cours d’exécution sur cet ordinateur

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Contrôle d’accès Stockage dans le code PowerShell":::

5. Définissez l’emplacement d’une copie du fichier : si vous souhaitez obtenir une copie du fichier lors de l’accès en écriture, vous devez définir l’emplacement où le système peut enregistrer la copie.
    
    - OMA-URI : `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation`

    - Type de données : String
    
    Vous devez déployer cette option avec accessMask et l’option de votre choix ( voir l’étape 2 ci-dessus).

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Définir locaiton pour la preuve de fichier":::
    
## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Déploiement et gestion d’une stratégie à l’aide de l’interface utilisateur Intune

Cette fonctionnalité est disponible dans le Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). Go to **Endpoint SecurityAttack** >  **Surface** **ReductionCreate** >  Policy. Choose **Platform: Windows 10 and later** with **Profile: Device Control**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données de contrôle d’Stockage d’accès amovible dans Microsoft Defender pour le point de terminaison

Le [portail Microsoft 365 Defender affiche](https://security.microsoft.com/advanced-hunting) les événements déclenchés par le contrôle d’Stockage d’accès. Pour accéder à la sécurité Microsoft 365, vous devez avoir l’abonnement suivant :

- Microsoft 365 de rapports E5

```kusto
//events triggered by RemovableStoragePolicyTriggered
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

:::image type="content" source="images/block-removable-storage.png" alt-text="Écran illustrant le blocage du stockage amovible.":::

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>Quelle est la limite du support de stockage amovible pour le nombre maximal de objets de première utilisation ?

Nous avons validé un groupe USB avec 100 000 supports , jusqu’à 7 Mo. La stratégie fonctionne dans Intune et LPO sans problèmes de performances.

### <a name="why-does-the-policy-not-work"></a>Pourquoi la stratégie ne fonctionne-t-elle pas ?

La raison la plus courante est qu’il n’existe pas de [version requise du client anti-programme malveillant](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

Une autre raison peut être que le fichier XML n’est pas correctement formaté, par exemple, en n’utilisant pas la mise en forme markdown correcte pour le caractère « & » dans le fichier XML, ou que l’éditeur de texte peut ajouter une 0xEF 0xBB 0xBF d’ordre d’byte au début des fichiers, ce qui entraîne le non-bon de l’examen XML. Une solution simple consiste à télécharger [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (sélectionnez **Raw** , puis **Enregistrer sous**), puis à mettre à jour.

Si vous déployez et gérez la stratégie via la stratégie de groupe, veillez à combiner toutes les stratégies PolicyRule dans un fichier XML au sein d’un nœud parent appelé PolicyRules et tous les groupes dans un fichier XML au sein d’un nœud parent appelé Groupes ; si vous gérez par le biais d’Intune, conservez un seul fichier XML PolicyRule, la même chose, un fichier XML de groupe 1.

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Il n’existe aucune expérience d’expérience de configuration pour « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil » dans ma stratégie de groupe

Nous ne déportons pas l’UX de configuration de la stratégie de groupe, mais vous pouvez toujours obtenir les fichiers adml et admx associés en cliquant sur « Raw » et « Save as » dans les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) .

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>Comment savoir si la dernière stratégie a été déployée sur l’ordinateur cible ?

Vous pouvez exécuter « Get-MpComputerStatus » sur PowerShell en tant qu’administrateur. La valeur suivante indique si la dernière stratégie a été appliquée à l’ordinateur cible.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

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
