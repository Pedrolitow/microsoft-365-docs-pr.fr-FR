---
title: Contrôle d’accès au stockage amovible microsoft Defender pour point de terminaison, support de stockage amovible
description: Présentation pas à pas de Microsoft Defender pour point de terminaison
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
ms.date: 06/06/2022
ms.openlocfilehash: 68beef5a01206ef08a87f74d53767fdd74d37a14
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923497"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>Contrôle d’accès au stockage amovible microsoft Defender pour le contrôle d’appareil de point de terminaison

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion des stratégies de groupe et la gestion OMA-URI/Custom Policy Intune de ce produit sont désormais en disponibilité générale (4.18.2106) : consultez le [blog Tech Community : Protéger votre stockage et votre imprimante amovibles avec Microsoft Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

Le contrôle d’accès au stockage amovible microsoft Defender pour le contrôle d’appareil de point de terminaison vous permet d’effectuer la tâche suivante :

- audit, autorisation ou prévention de l’accès en lecture, en écriture ou en exécution au stockage amovible avec ou sans exclusion

|Privilège|Autorisation|
|---|---|
|Access|Lecture, Écriture, Exécution|
|Action Mode|Auditer, autoriser, empêcher|
|Prise en charge du fournisseur de solutions Cloud|Oui|
|Prise en charge de l’objet de stratégie de groupe|Oui|
|Prise en charge basée sur l’utilisateur|Oui|
|Prise en charge basée sur l’ordinateur|Oui|

|Fonctionnalité|Description|Déployer via Intune|Déployer via une stratégie de groupe|
|---|---|---|---|
|Création de groupes multimédias amovibles|Vous permet de créer un groupe de supports amovibles réutilisable|Étape 1 de la section [Déploiement d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 1 de la section [Déploiement d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy)|
|Création de stratégie|Vous permet de créer une stratégie pour appliquer chaque groupe de supports amovibles|Étape 2 de la section [Déploiement d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étapes 2 et 3 de la section [Déploiement d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Application par défaut|Vous permet de définir l’accès par défaut (Refuser ou Autoriser) sur un média amovible s’il n’existe aucune stratégie|Étape 3 de la section [Déploiement d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 4 de la section [Déploiement d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Activer ou désactiver le contrôle d’accès au stockage amovible|Si vous définissez Désactiver, la stratégie de contrôle d’accès au stockage amovible est désactivée sur cet ordinateur.| Étape 4 de la section [Déploiement d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 5 de la section [Déploiement d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |
|Capturer des informations sur le fichier|Vous permet de créer une stratégie pour capturer les informations de fichier lorsque l’accès en écriture se produit| Étapes 2 et 5 de la section [Déploiement d’une stratégie via OMA-URI](#deploying-policy-via-oma-uri) | Étape 2 et 6 de la section [Déploiement d’une stratégie via une stratégie de groupe](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez le contrôle d’accès au stockage amovible sur les appareils Windows 10 et Windows 11 qui ont un client anti-programme malveillant version **4.18.2103.3 ou ultérieure**.

- **4.18.2104 ou version ultérieure** : Ajouter SerialNumberId, VID_PID, prise en charge de l’objet de stratégie de groupe basé sur filepath, ComputerSid

- **4.18.2105 ou version ultérieure** : Ajout d’une prise en charge générique pour HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId, combinaison d’utilisateurs spécifiques sur un ordinateur spécifique, DSD amovible (SSD SanDisk Extreme)/USB Attached SCSI (UAS)

- **4.18.2107 ou version ultérieure** : Ajout de la prise en charge de l’appareil portable Windows (WPD) (pour les appareils mobiles, tels que les tablettes) ; ajouter AccountName à la [chasse avancée](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="Interface PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> Aucun composant de sécurité Windows n’a besoin d’être actif, car vous pouvez exécuter le contrôle d’accès au stockage amovible indépendamment de l’état de sécurité Windows.

## <a name="policy-properties"></a>Propriétés de la stratégie

Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible :

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

### <a name="removable-storage-group"></a>Groupe de stockage amovible

|Nom de la propriété|Description|Options|
|---|---|---|
|**ID de groupe**|GUID, un ID unique, représente le groupe et sera utilisé dans la stratégie en tant qu’ID de groupe||
|**DescriptorIdList**|Répertoriez les propriétés de l’appareil que vous souhaitez utiliser pour couvrir le groupe. Pour chaque propriété d’appareil, consultez [Propriétés de l’appareil](device-control-removable-storage-protection.md) pour plus d’informations. Toutes les propriétés respectent la casse. |**PrimaryId**: `RemovableMediaDevices`, `CdRomDevices``WpdDevices`<p>**BusId** : Par exemple, USB, SCSI<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId** : InstancePathId est une chaîne qui identifie de façon unique l’appareil dans le système, par exemple. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0` Le nombre à la fin (par exemple &0) représente l’emplacement disponible et peut changer d’appareil à appareil. Pour de meilleurs résultats, utilisez un caractère générique à la fin. Par exemple : `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: correspond à cette paire exacte VID/PID<p>`_55E0`: faire correspondre n’importe quel média avec PID=55E0 <p>`0751_`: faire correspondre n’importe quel média avec VID=0751|
|**Matchtype**|Quand plusieurs propriétés d’appareil sont utilisées dans le `DescriptorIDList`, MatchType définit la relation.|**MatchAll** : tous les attributs sous la `DescriptorIdList` relation will be **And** ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système vérifie si l’USB répond aux deux valeurs. <p> **MatchAny** : les attributs sous DescriptorIdList seront **ou** la relation ; par exemple, si l’administrateur place `DeviceID` et `InstancePathID`, pour chaque USB connecté, le système effectue l’application tant que l’USB a une valeur **DeviceID** ou **InstanceID** identique. |

### <a name="access-control-policy"></a>Politique de contrôle d’accès

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

## <a name="common-removable-storage-access-control-scenarios"></a>Scénarios courants de contrôle d’accès au stockage amovible

Pour vous aider à vous familiariser avec le contrôle d’accès au stockage amovible Microsoft Defender pour point de terminaison, nous avons mis en place des scénarios courants à suivre.

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

    2. Groupe 2 : objets usb non approuvés basés sur les propriétés de l’appareil, par exemple, ID de fournisseur/ID de produit, nom convivial – Groupe **65fa649a-a111-4912-9294-fb6337a25038** dans l’exemple de fichier [de Group.xmlusbs non approuvés](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : bloquer l’accès à l’écriture et à l’exécution à tous les objets usb non approuvés spécifiques, sauf à bloquer. Voici un exemple de cas d’usage : PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** dans l’exemple [scénario 2 Auditer et exécuter l’accès à tous les fichiers USBs.xmlnon approuvés, sauf bloquer](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. Stratégie 2 : Auditer l’accès en écriture et en exécution à d’autres personnes. Voici un exemple de cas d’usage : PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** dans l’exemple [scénario 2 Auditer et exécuter l’accès à others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) fichier.

## <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion d’une stratégie via une stratégie de groupe

La fonctionnalité de contrôle d’accès au stockage amovible vous permet d’appliquer une stratégie via une stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing"></a>Licences

Avant de commencer à utiliser le contrôle d’accès au stockage amovible, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder au contrôle d’accès au stockage amovible et l’utiliser, vous devez disposer de Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>Déploiement d’une stratégie via une stratégie de groupe

1. Combinez tous les groupes au sein `<Groups>` `</Groups>` d’un fichier xml.

    L’image suivante illustre l’exemple du [scénario 1 : Empêcher l’accès à l’écriture et à l’exécution à tous, mais autoriser des bases de données approuvées spécifiques](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="Paramètres de configuration qui autorisent des bases de données approuvées spécifiques sur les appareils" lightbox="images/prevent-write-access-allow-usb.png":::

2. Combinez toutes les règles à l’intérieur `<PolicyRules>` `</PolicyRules>` en un seul fichier xml.

    Si vous souhaitez restreindre un utilisateur spécifique, utilisez la propriété SID dans l’entrée. S’il n’y a pas de SID dans l’entrée de stratégie, l’entrée est appliquée à toutes les instances de connexion de l’ordinateur.

    Si vous souhaitez surveiller les informations de fichier pour l’accès en écriture, utilisez le masque AccessMask approprié avec l’option appropriée (16) ; Voici l’exemple d’informations sur le [fichier Capture](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    L’image suivante illustre l’utilisation de la propriété SID, et un exemple de [scénario 1 : Empêcher l’accès à l’écriture et à l’exécution à tous, mais à autoriser des bases de données approuvées spécifiques](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="Code qui indique l’utilisation de l’attribut de propriété SID" lightbox="images/usage-sid-property.png":::

3. Enregistrez les fichiers XML de règle et de groupe dans le dossier de partage réseau et placez le chemin d’accès au dossier de partage réseau dans le paramètre de stratégie de groupe : Modèles **d’administration** de **configuration** \> par ordinateur **Composants** \> Windows Composants \> **Microsoft Defender Antivirus** \> **Device Control** : **« Définir des groupes de stratégies de contrôle d’appareil »** et **« Définir des règles de stratégie de contrôle d’appareil** ».

   Si vous ne trouvez pas l’expérience utilisateur de configuration de stratégie dans la stratégie de groupe, vous pouvez télécharger les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) en sélectionnant **Raw** , puis **Enregistrer sous**.

   - L’ordinateur cible doit être en mesure d’accéder au partage réseau pour disposer de la stratégie. Toutefois, une fois la stratégie lue, la connexion de partage réseau n’est plus nécessaire, même après le redémarrage de l’ordinateur.

    :::image type="content" source="images/device-control.png" alt-text="Écran Contrôle d’appareil" lightbox="images/device-control.png":::

4. Application par défaut : vous permet de définir l’accès par défaut (Refuser ou Autoriser) sur un média amovible s’il n’existe aucune stratégie. Par exemple, vous avez uniquement une stratégie (Refuser ou Autoriser) pour RemovableMediaDevices, mais vous n’avez pas de stratégie pour CdRomDevices ou WpdDevices, et vous définissez refuser par défaut via cette stratégie. L’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices est bloqué.

   - Une fois ce paramètre déployé, vous **verrez l’option Autoriser par défaut** ou **Refuser par défaut**.
   - Considérez le niveau disque et le masque d’accès au niveau du système de fichiers lors de la configuration de ce paramètre. Par exemple, si vous souhaitez refuser par défaut, mais autoriser un stockage spécifique, vous devez autoriser à la fois l’accès au niveau du disque et au niveau du système de fichiers, vous devez définir AccessMask sur 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="Autoriser ou refuser le code PowerShell par défaut":::

5. Activer ou désactiver le contrôle d’accès au stockage amovible : vous pouvez définir cette valeur pour désactiver temporairement le contrôle d’accès au stockage amovible.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="Paramètres de contrôle d’appareil":::

   - Une fois ce paramètre déployé, vous **verrez Activé** ou **Désactivé**. Désactivé signifie que cette machine n’a pas de stratégie de contrôle d’accès au stockage amovible en cours d’exécution.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="Contrôle d’appareil activé ou désactivé dans le code PowerShell":::

6. Définissez l’emplacement d’une copie du fichier : si vous souhaitez avoir une copie du fichier lorsque l’accès en écriture se produit, vous devez définir l’emplacement où le système peut enregistrer la copie.

    Déployez ceci avec accessMask et option appropriés . Consultez l’étape 2 ci-dessus.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="Stratégie de groupe - Définir locaiton pour la preuve de fichier":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>Déploiement et gestion de la stratégie via Intune OMA-URI

La fonctionnalité de contrôle d’accès au stockage amovible vous permet d’appliquer une stratégie via OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

### <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer à utiliser le contrôle d’accès au stockage amovible, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder au contrôle d’accès au stockage amovible et l’utiliser, vous devez disposer de Microsoft 365 E3 ou Microsoft 365 E5.

### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit disposer des autorisations nécessaires pour créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser l’un des rôles intégrés avec ces autorisations.

- Rôle gestionnaire de stratégies et de profils

- Rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lire/Supprimer/Afficher les rapports activées pour les profils de configuration d’appareil

- Administrateur général

### <a name="deploying-policy-via-oma-uri"></a>Déploiement d’une stratégie via OMA-URI

Microsoft Endpoint Manager admin center (<https://endpoint.microsoft.com/>) \> **Devices** \> **Configuration profiles** \> **Create profile** \> **Platform: Windows 10 and later & Profile: Custom**

1. Pour chaque groupe, créez une règle OMA-URI :

    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      Par exemple, pour **tout stockage amovible et groupe CD/DVD** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - Type de données : Chaîne (fichier XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="Champ Type de données dans la page Ajouter une ligne" lightbox="images/xml-data-type-string.png":::

2. Pour chaque stratégie, créez également un OMA-URI :

    - OMA-URI : 

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      Par exemple, pour la règle **Bloquer l’écriture et l’exécution de l’accès, mais autoriser la règle usb approuvée** dans l’exemple, le lien doit être :

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - Type de données : Chaîne (fichier XML)

    Si vous souhaitez surveiller les informations de fichier pour l’accès en écriture, utilisez le masque AccessMask approprié avec l’option appropriée (16) ; Voici l’exemple d’informations sur le [fichier Capture](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. Application par défaut : vous permet de définir l’accès par défaut (Refuser ou Autoriser) sur un média amovible s’il n’existe aucune stratégie. Par exemple, vous avez uniquement une stratégie (Refuser ou Autoriser) pour RemovableMediaDevices, mais vous n’avez pas de stratégie pour CdRomDevices ou WpdDevices, et vous définissez refuser par défaut via cette stratégie. L’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices est bloqué.

    - OMA-URI : `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - Type de données : Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - Une fois que vous avez déployé ce paramètre, vous **verrez l’option Autoriser par défaut** ou **Refuser par défaut**
    - Considérez le niveau disque et le masque d’accès au niveau du système de fichiers lors de la configuration de ce paramètre. Par exemple, si vous souhaitez refuser par défaut, mais autoriser un stockage spécifique, vous devez autoriser à la fois l’accès au niveau du disque et au niveau du système de fichiers, vous devez définir AccessMask sur 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="Application par défaut Autoriser le code PowerShell":::

4. Activer ou désactiver le contrôle d’accès au stockage amovible : vous pouvez définir cette valeur pour désactiver temporairement le contrôle d’accès au stockage amovible.

   - OMA-URI : `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - Type de données : Int `Disable: 0`
     `Enable: 1`

   - Une fois ce paramètre déployé, vous **verrez Activé** ou **Désactivé**

    **Désactivé** signifie que cette machine n’a pas de stratégie de contrôle d’accès au stockage amovible en cours d’exécution

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="Contrôle d’accès au stockage amovible dans le code PowerShell":::

5. Définissez l’emplacement d’une copie du fichier : si vous souhaitez avoir une copie du fichier lorsque l’accès en écriture se produit, vous devez définir l’emplacement où le système peut enregistrer la copie.

    - OMA-URI : './Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation

    - Type de données : String

    Vous devez déployer cela avec le masque AccessMask approprié et l’option appropriée . Voir l’étape 2 ci-dessus.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Définir locaiton pour la preuve de fichier":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>Déploiement et gestion d’une stratégie à l’aide de l’interface utilisateur Intune

(*Bientôt disponible!*) Cette fonctionnalité sera disponible dans le Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). Accédez à la stratégie de création **de la surface d’attaque** >  de **sécurité** >  du point de **terminaison**. Choisissez **Plateforme : Windows 10 et versions ultérieures** avec **Profil : Contrôle d’appareil**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données du contrôle d’accès au stockage amovible du contrôle d’appareil dans Microsoft Defender pour point de terminaison

Le [portail Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) affiche les événements déclenchés par le contrôle d’accès au stockage amovible Device Control. Pour accéder à la sécurité Microsoft 365, vous devez disposer de l’abonnement suivant :

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

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>Comment générer un GUID pour l’ID de groupe/ID PolicyRule/ID d’entrée ?

Vous pouvez générer un GUID via l’open source en ligne ou via PowerShell - [Guide pratique pour générer un GUID via PowerShell](/powershell/module/microsoft.powershell.utility/new-guid)

![image](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Quelles sont les limitations de stratégie et de média de stockage amovibles ?

À partir du Centre d’administration Microsoft Endpoint Manager (Intune) ou de l’API Microsoft Graph, l’appel principal est effectué via OMA-URI (GET to read ou PATCH to update), et par conséquent, la limitation est la même que n’importe quel profil de configuration personnalisé OMA-URI dans Microsoft, qui est officiellement de 350 000 caractères pour les fichiers XML. 
    
Par exemple, si vous avez besoin de deux blocs d’entrées par SID utilisateur pour « Autoriser » /« Auditer autorisé » des utilisateurs spécifiques et de deux blocs d’entrées à la fin de « Refuser », vous serez en mesure de gérer 2 276 utilisateurs. 

### <a name="why-does-the-policy-not-work"></a>Pourquoi la stratégie ne fonctionne-t-elle pas ?

1. La raison la plus courante est qu’il n’existe aucune version requise du [client anti-programme malveillant](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. Une autre raison peut être que le fichier XML n’est pas correctement mis en forme, par exemple, ne pas utiliser la mise en forme markdown correcte pour le caractère « & » dans le fichier XML, ou que l’éditeur de texte peut ajouter une marque d’ordre d’octet (BOM) 0xEF 0xBB 0xBF au début des fichiers, ce qui entraîne le non-fonctionnement de l’analyse XML. Une solution simple consiste à télécharger [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (sélectionnez **Raw** , puis **Enregistrer sous**), puis mettez à jour.

3. Si vous déployez et gérez la stratégie via une stratégie de groupe, veillez à combiner tous les PolicyRule dans un fichier XML au sein d’un nœud parent appelé PolicyRules et tous les groupes dans un fichier XML au sein d’un nœud parent appelé Groupes ; si vous gérez via Intune, conservez un fichier PolicyRule un fichier XML, la même chose, un seul fichier XML de groupe.

Si vous ne fonctionnez toujours pas, vous pouvez nous contacter et partager la cabine de support en exécutant cmd avec l’administrateur : « %programfiles%\Windows Defender\MpCmdRun.exe » -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>Il n’existe aucune expérience utilisateur de configuration pour « Définir des groupes de stratégies de contrôle d’appareil » et « Définir des règles de stratégie de contrôle d’appareil » dans ma stratégie de groupe

Nous ne réportons pas l’expérience utilisateur de configuration de la stratégie de groupe, mais vous pouvez toujours obtenir les fichiers adml et admx associés en cliquant sur « Brut » et « Enregistrer sous » dans les fichiers [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) et [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) .

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
