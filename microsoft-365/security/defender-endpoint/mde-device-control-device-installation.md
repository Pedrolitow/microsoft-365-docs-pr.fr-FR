---
title: Microsoft Defender pour point de terminaison installation de l’appareil Device Control
description: Cette rubrique présente Microsoft Defender pour point de terminaison’installation de l’appareil Device Control
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 08/11/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5b336a0650bc30eb1ebf23f8356b6c3c1ebb4e79
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67324164"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Microsoft Defender pour point de terminaison installation de l’appareil Device Control

**S’applique à**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> [!NOTE]
> Si vous souhaitez gérer le stockage amovible, consultez Microsoft Defender pour point de terminaison Access Control de [stockage amovible Device Control](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control).

Microsoft Defender pour point de terminaison’installation de l’appareil Device Control vous permet d’effectuer la tâche suivante :

- Empêcher les utilisateurs d’installer des appareils spécifiques.
- Autoriser les utilisateurs à installer des appareils spécifiques, mais empêcher d’autres appareils.

> [!NOTE]
> Pour trouver la différence entre l’installation de l’appareil et le contrôle d’accès au stockage amovible, consultez [Microsoft Defender pour point de terminaison Protection du stockage amovible du contrôle d’appareil](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Privilège|Autorisation|
|:---|:---|
|Access|Installation de l’appareil |
|Action Mode|Autoriser, Empêcher |
|Prise en charge du fournisseur de solutions Cloud|Oui|
|Prise en charge de l’objet de stratégie de groupe|Oui|
|Prise en charge basée sur l’utilisateur|Non|
|Prise en charge basée sur l’ordinateur|Oui|

## <a name="prepare-your-endpoints"></a>Préparer vos points de terminaison

Déployer l’installation des appareils sur Windows 10, Windows 11 appareils, Windows Server 2022.

## <a name="device-properties"></a>Propriétés du périphérique

Les propriétés d’appareil suivantes sont prises en charge par la prise en charge de l’installation de l’appareil :

- ID d'appareil
- ID matériel
- Compatible ID
- Classe d’appareil
- Type d’appareil amovible : certains appareils peuvent être classés en tant qu’appareil amovible. Un appareil est considéré comme amovible lorsque le pilote de l’appareil auquel il est connecté indique que l’appareil est amovible. Par exemple, un périphérique USB est signalé comme amovible par les pilotes du hub USB auquel l’appareil est connecté.

Pour plus d’informations, consultez [Installation de l’appareil dans Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>Politiques

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Autoriser l’installation d’appareils qui correspondent à l’un de ces ID d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’ID matériels Plug-and-Play et d’ID compatibles pour les appareils que Windows est autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les paramètres de stratégie de critères de correspondance d’appareil** est activé.

Lorsque ce paramètre de stratégie est activé avec **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher l’installation de l’appareil dans tous les paramètres de stratégie de critères de correspondance d’appareil**, Windows est autorisé à installer ou mettre à jour tout appareil dont l’ID matériel ou l’ID compatible Plug-and-Play apparaît dans la liste que vous créez, sauf si un autre paramètre de stratégie situé dans la même couche ou une couche supérieure de la hiérarchie empêche spécifiquement cette installation,  tels que les paramètres de stratégie suivants :

- Empêchez l’installation d’appareils qui correspondent à ces ID d’appareil.
- Empêchez l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil.

Si **l’ordre appliquer l’évaluation en couches pour autoriser et empêcher les stratégies d’installation d’appareil dans tous les paramètres de stratégie de critères de correspondance d’appareil** n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie qui empêchent spécifiquement l’installation sont prioritaires.

> [!NOTE]
> **L’option Empêcher l’installation d’appareils non décrits par d’autres paramètres** de stratégie a été remplacée par **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils dans tous les paramètres de stratégie de critères de correspondance d’appareil** pour les versions Windows 10 et Windows 11 cibles prises en charge. Dans la mesure du possible, utilisez **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher l’installation des appareils dans tous les paramètres de stratégie de critères de correspondance de l’appareil** .

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Autoriser l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’ID d’instance d’appareil Plug-and-Play pour les appareils que Windows est autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les paramètres de stratégie de critères de correspondance d’appareil** est activé.

Lorsque ce paramètre de stratégie est activé avec **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation d’appareil sur tous les paramètres de stratégie de critères de correspondance d’appareil**, Windows est autorisé à installer ou mettre à jour tout appareil dont l’ID d’instance d’appareil Plug-and-Play apparaît dans la liste que vous créez, sauf si un autre paramètre de stratégie de la même couche ou supérieure de la hiérarchie empêche spécifiquement cette installation,  tels que les paramètres de stratégie suivants :

- Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil

Si **l’ordre appliquer l’évaluation en couches pour autoriser et empêcher les stratégies d’installation d’appareil dans tous les paramètres de stratégie de critères de correspondance d’appareil** n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie qui empêchent spécifiquement l’installation sont prioritaires.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’identificateurs globalement uniques de la classe d’installation d’appareil pour les packages de pilotes que Windows est autorisé à installer. Ce paramètre de stratégie est destiné à être utilisé uniquement lorsque **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les paramètres de stratégie de critères de correspondance d’appareil** est activé.

Lorsque ce paramètre de stratégie est activé avec **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher les stratégies d’installation d’appareil dans tous les paramètres de stratégie de critères de correspondance d’appareil** , Windows est autorisé à installer ou mettre à jour les packages de pilotes dont les GUID de classe d’installation d’appareil apparaissent dans la liste que vous créez, sauf si un autre paramètre de stratégie de la même couche ou supérieure de la hiérarchie empêche spécifiquement cette installation,  tels que les paramètres de stratégie suivants :

- Empêcher l’installation d’appareils pour ces classes d’appareils
- Empêcher l’installation d’appareils qui correspondent à ces ID d’appareil
- Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil

Si **l’ordre appliquer l’évaluation en couches pour autoriser et empêcher les stratégies d’installation d’appareil dans tous les paramètres de stratégie de critères de correspondance d’appareil** n’est pas activé avec ce paramètre de stratégie, tous les autres paramètres de stratégie qui empêchent spécifiquement l’installation sont prioritaires.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Appliquer l’ordre d’évaluation en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les critères de correspondance des appareils

Ce paramètre de stratégie modifie l’ordre d’évaluation dans lequel les paramètres de stratégie Autoriser et Empêcher sont appliqués lorsque plusieurs paramètres de stratégie d’installation sont applicables pour un appareil donné. Activez ce paramètre de stratégie pour vous assurer que les critères de correspondance d’appareil qui se chevauchent sont appliqués en fonction d’une hiérarchie établie où des critères de correspondance plus spécifiques remplacent des critères de correspondance moins spécifiques. L’ordre hiérarchique d’évaluation des paramètres de stratégie qui spécifient des critères de correspondance d’appareil est le suivant :

**ID d’instance d’appareil** \> **ID d’appareil** \> Classe \> **d’installation de l’appareil** **Appareils amovibles**

#### <a name="device-instance-ids"></a>ID d’instance d’appareil

1. Empêchez l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’instance d’appareil.
2. Autorisez l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’instance d’appareil.

#### <a name="device-ids"></a>ID d’appareil

1. Empêchez l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’appareil.
2. Autorisez l’installation d’appareils à l’aide de pilotes qui correspondent à ces ID d’appareil.

#### <a name="device-setup-class"></a>Classe d’installation de l’appareil

1. Empêchez l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil.
2. Autorisez l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil.

#### <a name="removable-devices"></a>Appareils amovibles

Empêcher l’installation d’appareils amovibles

> [!NOTE]
> Ce paramètre de stratégie fournit un contrôle plus précis que **l’option Empêcher l’installation d’appareils non décrits par d’autres paramètres** de stratégie. Si ces paramètres de stratégie en conflit sont activés en même temps, **l’ordre d’évaluation Appliquer en couches pour autoriser et empêcher l’installation des appareils sur tous les paramètres de stratégie de critères de correspondance d’appareil** est activé et l’autre paramètre de stratégie est ignoré.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’ID matériels Plug-and-Play et d’ID compatibles pour les appareils que Windows n’est pas autorisé à installer. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet à Windows d’installer un appareil.

> [!NOTE]
> Pour activer **l’option Autoriser l’installation d’appareils qui correspondent à l’un de ces paramètres de stratégie d’ID d’instance d’appareil** pour remplacer ce paramètre de stratégie pour les appareils applicables, **activez l’ordre d’évaluation appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les paramètres de stratégie de correspondance d’appareil** .

Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer un appareil dont l’ID matériel ou l’ID compatible apparaît dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur de bureau distant, le paramètre de stratégie affecte la redirection des appareils spécifiés à partir d’un client bureau à distance vers le serveur bureau à distance.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les appareils peuvent être installés et mis à jour comme autorisés ou empêchés par d’autres paramètres de stratégie.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Empêcher l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’ID d’instance d’appareil Plug-and-Play pour les appareils que Windows n’est pas autorisé à installer. Ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet à Windows d’installer un appareil.

Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer un appareil dont l’ID d’instance d’appareil apparaît dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur de bureau distant, le paramètre de stratégie affecte la redirection des appareils spécifiés à partir d’un client bureau à distance vers le serveur bureau à distance.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, les appareils peuvent être installés et mis à jour comme autorisés ou empêchés par d’autres paramètres de stratégie.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil

Ce paramètre de stratégie vous permet de spécifier une liste d’identificateurs globalement uniques de la classe d’installation d’appareil pour les packages de pilotes que Windows n’est pas autorisé à installer. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet à Windows d’installer un appareil.

> [!NOTE]
> Pour activer **l’option Autoriser l’installation des appareils qui correspondent à l’un de ces ID d’appareil** et **autoriser l’installation d’appareils qui correspondent à l’un de ces paramètres de stratégie d’ID d’instance d’appareil** pour remplacer ce paramètre de stratégie pour les appareils applicables, **activez l’ordre d’évaluation en couches Appliquer pour autoriser et empêcher les stratégies d’installation des appareils dans tous les paramètres de stratégie de correspondance d’appareil** .

Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer ou mettre à jour des packages de pilotes dont les GUID de classe d’installation d’appareil apparaissent dans la liste que vous créez. Si vous activez ce paramètre de stratégie sur un serveur de bureau distant, le paramètre de stratégie affecte la redirection des appareils spécifiés à partir d’un client bureau à distance vers le serveur bureau à distance.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Windows peut installer et mettre à jour des appareils comme autorisé ou empêché par d’autres paramètres de stratégie.

### <a name="prevent-installation-of-removable-devices"></a>Empêcher l’installation d’appareils amovibles

Ce paramètre de stratégie vous permet d’empêcher Windows d’installer des appareils amovibles. Un appareil est considéré comme amovible lorsque le pilote de l’appareil auquel il est connecté indique que l’appareil est amovible. Par exemple, un périphérique USB (Universal Serial Bus) est signalé comme amovible par les pilotes du hub USB auquel l’appareil est connecté. Par défaut, ce paramètre de stratégie est prioritaire sur tout autre paramètre de stratégie qui permet à Windows d’installer un appareil.

> [!NOTE]
> Pour activer **l’option Autoriser l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil**, **autoriser l’installation d’appareils correspondant** à l’un de ces paramètres de stratégie d’ID d’instance d’appareil pour remplacer ce paramètre de stratégie pour les appareils applicables,  **activez l’ordre d’évaluation appliquer en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les** paramètres de stratégie de correspondance d’appareil.

Si vous activez ce paramètre de stratégie, Windows n’est pas autorisé à installer des appareils amovibles et les appareils amovibles existants ne peuvent pas être mis à jour. Si vous activez ce paramètre de stratégie sur un serveur de bureau distant, le paramètre de stratégie affecte la redirection d’appareils amovibles d’un client bureau à distance vers le serveur de bureau distant.

Si vous désactivez ou ne configurez pas ce paramètre de stratégie, Windows peut installer et mettre à jour les packages de pilotes pour les appareils amovibles, comme autorisé ou empêché par d’autres paramètres de stratégie.

## <a name="common-removable-storage-access-control-scenarios"></a>Scénarios courants de Access Control de stockage amovible

Pour vous aider à vous familiariser avec Microsoft Defender pour point de terminaison Access Control de stockage amovible, nous avons mis en place des scénarios courants à suivre.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scénario 1 : Empêcher l’installation de tous les périphériques USB tout en autorisant l’installation d’un lecteur usb autorisé

Pour ce scénario, les stratégies suivantes seront utilisées :

- Empêchez l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil.
- Appliquez l’ordre d’évaluation en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les critères de correspondance d’appareil.
- Autorisez l’installation d’appareils qui correspondent à l’un de ces ID d’instance d’appareil ou autorisez l’installation d’appareils qui correspondent à l’un de ces ID d’appareil.

#### <a name="deploying-and-managing-policy-via-intune"></a>Déploiement et gestion de la stratégie via Intune

La fonctionnalité d’installation de l’appareil vous permet d’appliquer une stratégie via Intune à l’appareil.

#### <a name="licensing"></a>Licences

Avant de commencer l’installation de l’appareil, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder à l’installation de l’appareil et l’utiliser, vous devez disposer de Microsoft 365 E3.

#### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit disposer des autorisations nécessaires pour créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser l’un des rôles intégrés avec les autorisations suivantes :

- Rôle gestionnaire de stratégies et de profils
- Ou un rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lire/Supprimer/Afficher les rapports activées pour les profils de configuration d’appareil
- Ou administrateur général

#### <a name="deploying-policy"></a>Déploiement d’une stratégie

Dans Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. Configurez **Empêcher l’installation d’appareils à l’aide de pilotes qui correspondent à ces classes d’installation d’appareil**.

    Ouvrir la **réduction de la surface d’attaque** >  de **sécurité** >  des points de terminaison **Créer** >  une **plateforme de stratégie : Windows 10 (et versions ultérieures) & Profil : Contrôle de l’appareil**.

      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Page Modifier le profil" lightbox="../../media/devicepolicy-editprofile.png":::

2. Connectez un périphérique USB et vous verrez le message d’erreur suivant :

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Message d’erreur" lightbox="../../media/devicepolicy-errormsg.png":::

3. **Activez Appliquer l’ordre d’évaluation en couches pour autoriser et empêcher les stratégies d’installation des appareils sur tous les critères de correspondance d’appareil**.

    **prend uniquement en charge OMA-URI pour le moment** :**Profils** >  de configuration **des appareils** >  Créer une plateforme de **profil** > **: Windows 10 (et versions ultérieures) & Profil : Personnalisé**

      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Page Modifier la ligne" lightbox="../../media/devicepolicy-editrow.png":::

4. Activer et ajouter l’ID d’instance USB autorisé : **autoriser l’installation d’appareils qui correspondent à l’un de ces ID d’appareil**.

    Mettez à jour le profil de contrôle d’appareil à partir de l’étape 1.

      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Identificateur dans la page Contrôle d’appareil" lightbox="../../media/devicepolicy-devicecontrol.png":::

    Nous l’avons ajouté `PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB` comme indiqué dans l’image précédente, car il ne suffit pas d’activer un seul ID matériel pour activer un lecteur USB unique. Vous devez également vous assurer que tous les périphériques USB qui précèdent la cible ne sont pas bloqués (autorisés). Vous pouvez ouvrir Gestionnaire de périphériques et modifier la vue **sur Appareils par connexions** pour voir comment les appareils sont installés dans l’arborescence PnP. Dans ce cas, les appareils suivants doivent être autorisés afin que le lecteur usb cible puisse également être autorisé :

    - « Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft) » -> PCI\CC_0C03
    - « USB Root Hub (USB 3.0) » -> USB\ROOT_HUB30
    - « Hub USB générique » -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Élément de menu Affichage dans la page Gestionnaire de périphériques" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Certains appareils du système disposent de plusieurs couches de connectivité pour définir leur installation sur le système. Les lecteurs USB sont de tels appareils. Par conséquent, lorsque vous cherchez à les bloquer ou à les autoriser sur un système, il est important de comprendre le chemin de connectivité pour chaque appareil. Il existe plusieurs ID d’appareil génériques qui sont couramment utilisés dans les systèmes et qui peuvent fournir un bon point de départ pour créer une « liste verte » dans de tels cas. Voici un exemple (il n’est pas toujours le même pour tous les objets usuels ; vous devez comprendre l’arborescence PnP de l’appareil que vous souhaitez gérer via le Gestionnaire de périphériques) :
    >
    > `PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (for Host Controllers)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (for USB Root Hubs)/ USB\USB20_HUB (for Generic USB Hubs)/`
    >
    > Plus précisément pour les ordinateurs de bureau, il est important de répertorier tous les périphériques USB auxquels vos claviers et souris sont connectés dans la liste ci-dessus. Si vous ne le faites pas, un utilisateur peut empêcher l’utilisateur d’accéder à son ordinateur via des appareils HID.
    >
    > Différents fabricants de PC ont parfois différentes façons d’imbriquer des périphériques USB dans l’arborescence PnP, mais en général, c’est comme cela qu’il est fait.

5. Branchez à nouveau l’USB autorisé. Vous verrez qu’il est désormais autorisé et disponible.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Page Supprimer les détails du lecteur" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Déploiement et gestion de la stratégie via stratégie de groupe

La fonctionnalité d’installation de l’appareil vous permet d’appliquer une stratégie via stratégie de groupe.

#### <a name="deploying-policy"></a>Déploiement d’une stratégie

Consultez [Gérer l’installation de l’appareil avec stratégie de groupe (Windows 10) - Client Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Afficher les données de Access Control de stockage amovibles du contrôle d’appareil dans Microsoft Defender pour point de terminaison

Le [portail Microsoft 365 Defender](https://sip.security.microsoft.com/homepage) affiche le stockage amovible bloqué par l’installation de l’appareil Device Control.

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

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="Stockage de blocs" lightbox="../../media/block-removable-storage2.png":::

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="how-do-i-confirm-that-a-device-gets-a-deployed-policy"></a>Comment faire confirmer qu’un appareil obtient une stratégie déployée ?

Vous pouvez utiliser la requête suivante pour obtenir la version du client anti-programme malveillant sur le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) :

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-doesnt-the-allow-policy-work"></a>Pourquoi la stratégie Autoriser ne fonctionne-t-elle pas ?

Il ne suffit pas d’activer un seul ID matériel pour activer un lecteur USB unique. Assurez-vous que tous les périphériques USB qui précèdent la cible ne sont pas non plus bloqués (autorisés).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Faq sur l’installation de l’appareil" lightbox="../../media/devicemgrscrnshot.png":::
