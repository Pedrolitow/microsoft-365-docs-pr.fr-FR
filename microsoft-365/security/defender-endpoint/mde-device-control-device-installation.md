---
title: Microsoft Defender for Endpoint Device Control Device Installation
description: Cette rubrique fournit une présentation de Microsoft Defender pour l’installation de périphériques de contrôle d’appareil de point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-lsaldanha
author: lovina-saldanha
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1405d2b2c40f208ebe09a8be29fa1a7f5f8a03ef
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204714"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Microsoft Defender for Endpoint Device Control Device Installation 

Microsoft Defender for Endpoint Device Control Removable Stockage Access Control vous permet d’accomplir la tâche suivante :

- Empêcher les personnes d’installer des appareils spécifiques.
- Autoriser les utilisateurs à installer des appareils spécifiques, mais en empêcher d’autres.

> [!NOTE]
> Pour trouver la différence entre l’installation de l’appareil et le contrôle d’accès au stockage amovible, voir [Microsoft Defender for Endpoint Device Control Removable Stockage Protection](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Privilège|Autorisation|
|---|---|
|Accès|Installation de l’appareil |
|Action Mode|Autoriser, Empêcher |
|Prise en charge du programme CSP|Oui|
|Prise en charge des GPO|Oui|
|Prise en charge basée sur l’utilisateur|Non|
|Prise en charge basée sur l’ordinateur|Oui|
|||

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployez l’installation de Windows 10 sur Windows Server 2022.

## <a name="device-properties"></a>Propriétés du périphérique

Les propriétés d’appareil suivantes sont pris en charge par la prise en charge de l’installation de périphériques :

- ID d’appareil 
- ID matériel 
- Compatible ID 
- Classe Device 
- Type de périphérique « Appareil amovible » : certains appareils peuvent être classés comme périphériques amovibles. Un appareil est considéré comme amovible lorsque le pilote de l’appareil auquel il est connecté indique que l’appareil est amovible. Par exemple, un périphérique USB est signalé comme amovible par les pilotes du concentrateur USB auquel l’appareil est connecté. Pour plus d’informations, [voir Installation de l’appareil dans Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>Stratégies

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Autoriser l’installation d’appareils qui correspondent à l’un de ces ID d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’ID matériels Plug-and-Play et d’ID compatibles pour les appareils que Windows est autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque l’ordre d’évaluation Appliquer une couche d’évaluation pour les stratégies **d’installation** d’appareil Autoriser et Empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil est activé.

Lorsque ce paramètre de stratégie est activé avec l’ordre d’évaluation Appliqué en couches pour les stratégies **d’installation** d’appareil Autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance de périphérique, Windows est autorisé à installer ou mettre à jour tout appareil dont l’ID matériel plug-and-play ou l’ID compatible apparaît dans la liste que vous créez, sauf si un autre paramètre de stratégie de la même couche ou d’une couche supérieure de la hiérarchie empêche spécifiquement cette installation, comme les paramètres de stratégie suivants :

- Empêcher l’installation d’appareils qui correspondent à ces ID d’appareil.
- Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil.

Si l’ordre d’évaluation Appliquer en couches pour les stratégies **d’installation** d’appareil autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie empêchant spécifiquement l’installation seront prioritaires. 

> [!NOTE]
> La stratégie Empêcher l’installation d’appareils non décrits par d’autres **paramètres** de stratégie a été remplacée par l’ordre d’évaluation appliquer en couches pour les stratégies **d’installation** d’appareils autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance des appareils pour les versions de Windows 10 cibles pris en charge. Il est recommandé d’utiliser l’ordre d’évaluation appliqué en couches pour autoriser et empêcher les stratégies **d’installation** d’appareils dans tous les paramètres de stratégie de correspondance des critères d’appareil lorsque cela est possible.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Autoriser l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil 

Ce paramètre de stratégie vous permet de spécifier une liste d’ID d’instance d’appareil Plug-and-Play pour les Windows que vous êtes autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque l’ordre d’évaluation Appliquer une couche d’évaluation pour les stratégies **d’installation** d’appareil Autoriser et Empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil est activé. 

Lorsque ce paramètre de stratégie est activé avec l’ordre d’évaluation Appliquer en couches pour les stratégies **d’installation** d’appareil autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil, Windows est autorisé à installer ou mettre à jour tout appareil dont l’ID d’instance plug-and-play apparaît dans la liste que vous créez, sauf si un autre paramètre de stratégie de la même couche ou d’une couche supérieure de la hiérarchie empêche spécifiquement cette installation, comme les paramètres de stratégie suivants :

- Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil 

Si l’ordre d’évaluation Appliquer en couches pour les stratégies **d’installation** d’appareil autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie empêchant spécifiquement l’installation seront prioritaires. 

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil 

Ce paramètre de stratégie vous permet de spécifier une liste d’identificateurs globaux uniques (GUID) de la classe d’installation d’appareil pour les packages de pilotes que Windows est autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque l’ordre d’évaluation Appliquer une couche d’évaluation pour les stratégies **d’installation** d’appareil Autoriser et Empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil est activé.

Lorsque ce paramètre de stratégie est activé avec l’ordre d’évaluation en couches Appliquer pour les stratégies **d’installation** d’appareil autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance de périphérique, Windows est autorisé à installer ou mettre à jour les packages de pilotes dont les GUI de classe d’installation d’appareil apparaissent dans la liste que vous créez, sauf si un autre paramètre de stratégie de la même couche ou d’une couche supérieure de la hiérarchie empêche spécifiquement cette installation, comme les paramètres de stratégie suivants : 

- Empêcher l’installation d’appareils pour ces classes d’appareils 
- Empêcher l’installation d’appareils qui correspondent à ces ID d’appareil 
- Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil 

Si l’ordre d’évaluation Appliquer en couches pour les stratégies **d’installation** d’appareil autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie empêchant spécifiquement l’installation seront prioritaires.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Appliquer l’ordre d’évaluation en couches pour les stratégies d’installation d’appareil autoriser et empêcher l’installation sur tous les critères de correspondance d’appareil 

Ce paramètre de stratégie modifie l’ordre d’évaluation dans lequel les paramètres de stratégie Autoriser et Empêcher sont appliqués lorsque plusieurs paramètres de stratégie d’installation sont applicables pour un appareil donné. Activez ce paramètre de stratégie pour vous assurer que les critères de correspondance d’appareil qui se chevauchent sont appliqués en fonction d’une hiérarchie établie où des critères de correspondance plus spécifiques ont lieu sur des critères de correspondance moins spécifiques. L’ordre hiérarchique d’évaluation pour les paramètres de stratégie qui spécifient les critères de correspondance d’appareil est le suivant :

**ID d’instance d’appareil > ID d’appareil > la classe d’installation > appareils amovibles**

#### <a name="device-instance-ids"></a>ID d’instance d’appareil 

1. Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’instance d’appareil.
2. Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’instance d’appareil.

#### <a name="device-ids"></a>ID d’appareil 

1. Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’appareil.
2. Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’appareil.

#### <a name="device-setup-class"></a>Classe d’installation d’appareil 

1. Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil.
2. Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil.

#### <a name="removable-devices"></a>Appareils amovibles 

Empêcher l’installation d’appareils amovibles 

> [!NOTE]
> Ce paramètre de stratégie offre un contrôle plus granulaire que l’installation d’appareils non décrits par d’autres **paramètres** de stratégie. Si ces paramètres de stratégie conflictuelles sont activés en même temps, l’ordre d’évaluation Appliquer en couches pour les stratégies **d’installation** d’appareil Autoriser et Empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil sera activé et l’autre paramètre de stratégie sera ignoré. 

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’appareil 

Ce paramètre de stratégie vous permet de spécifier une liste d’ID matériels Plug-and-Play et d’ID compatibles pour les appareils dont l’installation est Windows’est pas installée. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet Windows installer un appareil.

> [!NOTE]
> Pour permettre à l’installation d’appareils qui correspondent à l’un de ces **paramètres** de stratégie d’instance d’appareil de prendre le pas sur ce paramètre de stratégie pour les appareils applicables, activez l’ordre d’évaluation en couches pour les stratégies **d’installation** d’appareil Autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance d’appareil. 

Si vous activez ce paramètre de stratégie, Windows ne peut pas installer un appareil dont l’ID matériel ou l’ID compatible apparaît dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur bureau à distance, le paramètre de stratégie affecte la redirection des appareils spécifiés d’un client bureau à distance vers le serveur de bureau à distance.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les appareils peuvent être installés et mis à jour comme autorisé ou interdit par d’autres paramètres de stratégie. 

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil 

Ce paramètre de stratégie vous permet de spécifier une liste d’ID d’instance d’appareil Plug-and-Play pour les appareils dont l Windows’installation est empêchée. Ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet Windows installer un appareil. 

Si vous activez ce paramètre de stratégie, Windows ne peut pas installer un appareil dont l’ID d’instance d’appareil apparaît dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur bureau à distance, le paramètre de stratégie affecte la redirection des appareils spécifiés d’un client bureau à distance vers le serveur de bureau à distance. 

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les appareils peuvent être installés et mis à jour comme autorisé ou interdit par d’autres paramètres de stratégie. 

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil 

Ce paramètre de stratégie vous permet de spécifier une liste d’identificateurs globaux uniques (GUID) de la classe d’installation d’appareil pour les packages de pilotes dont l’installation Windows est empêchée. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet Windows installer un appareil.

> [!NOTE]
> Pour activer l’installation autoriser l’installation d’appareils qui correspondent à l’un de ces **ID** d’appareil et autoriser l’installation d’appareils qui correspondent à l’un de ces **paramètres** de stratégie d’instance d’appareil afin de passer outre ce paramètre de stratégie pour les appareils applicables, activez l’ordre d’évaluation en couches pour les stratégies **d’installation** d’appareil Autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance de périphérique.

Si vous activez ce paramètre de stratégie, Windows ne peut pas installer ou mettre à jour les packages de pilotes dont les GUID de classe d’installation d’appareil apparaissent dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur bureau à distance, le paramètre de stratégie affecte la redirection des appareils spécifiés d’un client bureau à distance vers le serveur de bureau à distance. 

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Windows pouvez installer et mettre à jour des appareils comme cela est autorisé ou interdit par d’autres paramètres de stratégie. 

### <a name="prevent-installation-of-removable-devices"></a>Empêcher l’installation d’appareils amovibles 

Ce paramètre de stratégie vous permet d’empêcher les Windows d’installer des appareils amovibles. Un appareil est considéré comme amovible lorsque le pilote de l’appareil auquel il est connecté indique que l’appareil est amovible. Par exemple, un périphérique USB (Universal Serial Bus) est signalé comme amovible par les pilotes du concentrateur USB auquel l’appareil est connecté. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet Windows installer un appareil. 

> [!NOTE]
> Pour activer l’installation d’appareils à l’aide de pilotes qui correspondent à ces **classes** d’installation d’appareil, autoriser l’installation d’appareils qui correspondent à l’un de ces **ID** d’appareil et autoriser l’installation d’appareils qui correspondent à l’un de ces **paramètres** de stratégie d’instance d’appareil pour prendre le pas sur ce paramètre de stratégie pour les appareils applicables, activez l’ordre d’évaluation en couches des stratégies **d’installation** d’appareils autoriser et empêcher l’installation sur tous les paramètres de stratégie de correspondance de périphérique.

Si vous activez ce paramètre de stratégie, Windows l’installation de périphériques amovibles est empêchée et les pilotes des appareils amovibles existants ne peuvent pas être mis à jour. Si vous activez ce paramètre de stratégie sur un serveur bureau à distance, le paramètre de stratégie affecte la redirection des appareils amovibles d’un client bureau à distance vers le serveur de bureau à distance.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Windows peut installer et mettre à jour des packages de pilotes pour les appareils amovibles comme cela est autorisé ou interdit par d’autres paramètres de stratégie.

## <a name="common-removable-storage-access-control-scenarios"></a>Scénarios courants Stockage contrôle d’accès des périphériques amovibles

Pour vous aider à vous familiariser avec Microsoft Defender pour endpoint Removable Stockage Access Control, nous avons mis en place des scénarios courants que vous pouvez suivre.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scénario 1 : empêcher l’installation de tous les périphériques USB tout en autorisant l’installation d’une seule clé USB autorisée 

Pour ce scénario, les stratégies suivantes seront utilisées :

- Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil.
- Appliquer l’ordre d’évaluation en couches pour les stratégies d’installation d’appareil Autoriser et empêcher sur tous les critères de correspondance d’appareil.
- Autorisez l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil ou autorisez l’installation d’appareils qui correspondent à l’un de ces ID d’appareil.

#### <a name="deploying-and-managing-policy-via-intune"></a>Déploiement et gestion d’une stratégie via Intune 

La fonctionnalité d’installation de l’appareil vous permet d’appliquer une stratégie via Intune à l’appareil.

#### <a name="licensing"></a>Licences 

Avant de commencer l’installation de l’appareil, vous devez confirmer [votre abonnement Microsoft 365.](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2) Pour accéder à l’installation de l’appareil et l’utiliser, vous devez Microsoft 365 E3.

#### <a name="permission"></a>Autorisation 

Pour le déploiement de stratégie dans Intune, le compte doit être autorisé à créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser n’importe quel rôle intégré avec les autorisations ci-après :  

- Rôle gestionnaire de stratégies et de profils
- Ou rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lecture/Supprimer/Afficher les rapports pour les profils de configuration d’appareil
- Ou administrateur global

#### <a name="deploying-policy"></a>Déploiement d’une stratégie 

Dans Microsoft Endpoint Manager[https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)  

1. Configurez Empêcher **l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes de configuration d’appareil.**

    - Ouvrez endpoint security > Attack surface reduction > Create Policy > Platform: Windows 10 (and later) & Profile: Device control.
    
      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="modifier le profil":::
    
2. Branchez un périphérique USB et vous verrez le message d’erreur suivant :

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="message d’erreur":::

3. Activez l’application d’un ordre d’évaluation en couches pour les stratégies d’installation d’appareil autoriser et empêcher **l’installation sur tous les critères de correspondance d’appareil.**

    - ne prise en charge que pour l’instant **OMA-URI**: profils de configuration > appareils > Créer un profil > Plateforme : Windows 10 (et & profil : personnalisé
    
      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="modifier la ligne":::

4. Activer et ajouter un ID d’instance USB autorisé : autoriser l’installation d’appareils qui correspondent à l’un de **ces ID d’appareil.**

    - Mettre à jour le profil de contrôle d’appareil de l’étape 1
    
      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="devicecontrol":::
       
    Ajout de PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1 &HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; Usb\USB20_HUB capture d’écran ci-dessus est dû au fait qu’il ne suffit pas d’activer un seul ID matériel pour activer une seule clé USB. Vous devez vous assurer que tous les périphériques USB précédant la cible ne sont pas bloqués (autorisés). Vous pouvez ouvrir le Gestionnaire de périphériques et afficher « Appareils par connexion » pour voir la façon dont les appareils sont installés dans l’arborescence PnP. Dans notre cas, les appareils suivants doivent être autorisés afin que le lecteur usb cible puisse également être autorisé : 

    - « Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft) » -> PCI\CC_0C03 
    - « Concentrateur racine USB (USB 3.0) » -> USB\ROOT_HUB30 
    - « Hub USB générique » : > USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="contrôle d’appareil":::

    > [!NOTE]
    > Certains appareils du système ont plusieurs couches de connectivité pour définir leur installation sur le système. Les lecteurs USB sont de tels périphériques. Par conséquent, lorsque vous cherchez à les bloquer ou les autoriser sur un système, il est important de comprendre le chemin de connectivité de chaque appareil. Il existe plusieurs ID d’appareil génériques qui sont couramment utilisés dans les systèmes et peuvent fournir un bon démarrage pour créer une « liste d’appareils acceptés » dans de tels cas. Voir ci-dessous pour obtenir la liste :
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (pour les contrôleurs d’hôte)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (pour les concentrateurs racine USB)/ USB\USB20_HUB (pour les concentrateurs USB génériques)/ 
    >
    > Plus précisément pour les ordinateurs de bureau, il est important de lister tous les périphériques USB connectés par vos claviers et souris dans la liste ci-dessus. Si vous ne le faites pas, un utilisateur peut accéder à son ordinateur via des périphériques HID. 
    >
    > Les différents fabricants de PC ont parfois différentes façons d’imbribrier des périphériques USB dans l’arborescence PnP, mais en général, c’est comme cela que l’on fait. 

5. Branchez de nouveau la clé USB autorisée. Vous verrez qu’il est désormais autorisé et disponible.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="supprimer un lecteur":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion d’une stratégie via une stratégie de groupe

La fonctionnalité d’installation de l’appareil vous permet d’appliquer une stratégie par le biais de la stratégie de groupe.

#### <a name="licensing"></a>Licences

Pour accéder à l’installation de l’appareil et l’utiliser, vous devez Windows E3.

#### <a name="deploying-policy"></a>Déploiement d’une stratégie

Vous trouverez les détails du déploiement ici : Gérer l’installation de l’appareil avec la stratégie de groupe [(Windows 10) - Windows client](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données de contrôle d’Stockage d’accès amovible dans Microsoft Defender pour le point de terminaison

Le [portail Microsoft 365 sécurité](https://sip.security.microsoft.com/homepage) affiche le stockage amovible bloqué par l’installation de l’appareil de contrôle d’appareil. Pour accéder à la sécurité Microsoft 365, vous devez avoir l’abonnement suivant :

- Microsoft 365 de rapports E5

```kusto
//events triggered by Device Installation policies 
DeviceEvents 
| where ActionType == "PnpDeviceBlocked" or ActionType == "PnpDeviceAllowed" 
| extend parsed=parse_json(AdditionalFields) 
| extend MediaClassGuid = tostring(parsed.ClassGuid)  
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId) 
| extend MediaDeviceId = tostring(parsed.MatchingDeviceId) 
| project Timestamp , DeviceId, DeviceName, ActionType, MediaClassGuid, MediaDeviceId, MediaInstanceId, AdditionalFields 
| order by Timestamp desc 
```

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="bloquer le stockage":::

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Comment savoir si l’ordinateur cible obtient la stratégie déployée ? 
Vous pouvez utiliser la requête suivante pour obtenir la version du client anti-programme malveillant sur le portail Microsoft 365 sécurité :

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens   
DeviceRegistryEvents 
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\" 
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>Pourquoi la stratégie Autoriser ne fonctionne pas ?
Il ne suffit pas d’activer un seul ID matériel pour activer une seule clé USB. Assurez-vous que tous les périphériques USB qui précèdent la cible ne sont pas bloqués (autorisés).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Faq sur l’installation des appareils":::

