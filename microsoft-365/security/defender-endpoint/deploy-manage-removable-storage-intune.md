---
title: Déployer et gérer des 存取控制 de stockage amovibles à l’aide d’Intune
description: Utilisez Intune OMA-URI et l’interface utilisateur Intune pour déployer et gérer le contrôle d’accès au stockage amovible.
ms.service: microsoft-365-security
ms.subservice: mde
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
ms.date: 09/09/2022
ms.reviewer: tewchen
search.appverid: met150
ms.openlocfilehash: d06d36f8b9fb3451f70b646c3969fa2bb7487f9f
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736843"
---
# <a name="deploy-and-manage-removable-storage-access-control-using-intune"></a>Déployer et gérer des 存取控制 de stockage amovibles à l’aide d’Intune

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion نهج المجموعة et la gestion intune OMA-URI/Custom Policy de ce produit sont désormais en disponibilité générale (4.18.2106) : consultez le [blog Tech Community : Protéger votre stockage amovible et votre imprimante avec Pertahanan Microsoft untuk Titik Akhir](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

La fonctionnalité de 存取控制 de stockage amovible vous permet d’appliquer une stratégie à l’aide d’OMA-URI à l’utilisateur ou à l’appareil, ou aux deux.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer à utiliser les 存取控制 de stockage amovibles, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder aux 存取控制 de stockage amovibles et les utiliser, vous devez disposer d’Microsoft 365 E3.

### <a name="permission"></a>Autorisation

Pour le déploiement de stratégie dans Intune, le compte doit disposer des autorisations nécessaires pour créer, modifier, mettre à jour ou supprimer des profils de configuration d’appareil. Vous pouvez créer des rôles personnalisés ou utiliser l’un des rôles intégrés avec ces autorisations.

- Rôle gestionnaire de stratégies et de profils
- Rôle personnalisé avec les autorisations Créer/Modifier/Mettre à jour/Lire/Supprimer/Afficher les rapports activées pour les profils de configuration d’appareil
- Administrateur général

## <a name="deploy-removable-storage-access-control-by-using-intune-oma-uri"></a>Déployer des 存取控制 de stockage amovibles à l’aide d’Intune OMA-URI

Accédez au Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>) > **Les appareils** > **créent une** plateforme de profil  > **: Windows 10 et versions ultérieures, Type de profil : Modèles** > Personnalisé**.

1. Activez ou désactivez le contrôle d’appareil comme suit :

   - Sous **Paramètres de configuration personnalisés** > , sélectionnez **Ajouter**.
   - Dans le volet **Ajouter une ligne** , spécifiez les paramètres suivants :
     - **Nom** **en tant qu’activer le contrôle d’appareil**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **Type de données** **en tant qu’entier**
     - **Valeur** **1**

       `Disable: 0`
       `Enable: 1`

     - Sélectionnez **Enregistrer**.

   :::image type="content" source="images/enable-rsac.png" alt-text="Capture d’écran de l’activation de la stratégie de 存取控制 de stockage amovible" lightbox="images/enable-rsac.png":::

2. Définir l’application par défaut :

   Vous pouvez définir l’accès par défaut (Refuser ou Autoriser) pour toutes les fonctionnalités de contrôle d’appareil (`RemovableMediaDevices`, `CdRomDevices`, `WpdDevices`). `PrinterDevices`

   Par exemple, vous pouvez avoir une **stratégie Deny** ou **Allow** pour `RemovableMediaDevices`, mais pas pour `CdRomDevices` ou `WpdDevices`. Vous pouvez définir le **refus par défaut** via cette stratégie, puis l’accès en lecture/écriture/exécution à `CdRomDevices` ou `WpdDevices` sera bloqué. Si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie **Autoriser** pour votre imprimante ; Sinon, cette mise en œuvre par défaut sera également appliquée aux imprimantes.

   - Dans le volet **Ajouter une ligne** , spécifiez les paramètres suivants :
     - **Nom** en tant que **refus par défaut**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **Type de données** **en tant qu’entier**
     - **Valeur** **1** ou **2**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - Sélectionnez **Enregistrer**.

   :::image type="content" source="images/default-deny.png" alt-text="Capture d’écran de la définition de l’application par défaut en tant que refus" lightbox="images/default-deny.png":::

3. Créez un fichier XML pour chaque groupe :

   Vous pouvez créer un groupe de stockage amovible pour chaque groupe comme suit :

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** **de n’importe quel groupe de stockage amovible**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**[GroupId]**%7d/GroupData`
     - **Type de données** **sous forme de chaîne (fichier XML)**
       - **XML personnalisé** en tant que fichier XML sélectionné

         Voici un exemple de fichier XML de groupe pour tout stockage amovible et cdROM et appareils portables Windows : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="Capture d’écran de la création d’un groupe de stockage amovible." lightbox="images/any-removable-storage-group.png":::

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

4. Créez un fichier XML pour chaque contrôle d’accès ou règle de stratégie :

   Vous pouvez créer une stratégie et l’appliquer au groupe de stockage amovible associé comme suit :

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** comme **autoriser l’activité de lecture**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**[PolicyRule Id]**%7d/RuleData`
     - **Type de données** **sous forme de chaîne (fichier XML)**
     - **Fichier XML personnalisé** en tant **qu’autorisation Read.xml**

       Voici un exemple de fichier XML de groupe pour autoriser l’accès en lecture pour chaque stockage amovible : <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       :::image type="content" source="images/allow-read-activity.png" alt-text="Capture d’écran de la stratégie Autoriser l’activité de lecture" lightbox= "images/allow-read-activity.png":::

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

5. Définir l’emplacement d’une copie du fichier (preuve) :
   
   Si vous souhaitez avoir une copie du fichier (preuve) lorsque l’accès en écriture se produit, définissez **les options** appropriées dans votre règle de stratégie d’accès au stockage amovible dans le fichier XML, puis spécifiez l’emplacement où le système peut enregistrer la copie.

   - Dans le volet **Ajouter une ligne** , entrez :
     - **Nom** en tant **qu’emplacement du dossier Preuve**
     - **OMA-URI** en tant que `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation`
     - **Type de données** sous **forme de chaîne**

       :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="Définir l’emplacement de la preuve de fichier":::

## <a name="scenarios"></a>Scénarios

Voici quelques scénarios courants pour vous aider à vous familiariser avec Pertahanan Microsoft untuk Titik Akhir 存取控制 de stockage amovible.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scénario 1 : Empêcher l’accès en écriture et en exécution à tous, mais autoriser des bases de données approuvées spécifiques

Pour ce scénario, vous devez créer deux groupes : un groupe pour tout stockage amovible et un autre pour les objets USB approuvés. Vous devez également créer deux stratégies : une stratégie pour refuser l’accès En écriture et exécution pour tout groupe de stockage amovible, et l’autre pour auditer le groupe usBs approuvé.

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible, CD/DVD et appareils portables Windows.

       :::image type="content" source="media/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png" alt-text="Capture d’écran montrant le stockage amovible" lightbox= "media/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png":::

    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml). Consultez l’étape 3 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

    2. Groupe 2 : Bases de données américaines approuvées en fonction des propriétés de l’appareil.

        :::image type="content" source="media/188234372-526d20b3-cfea-4f1d-8d63-b513497ada52.png" alt-text="Capture d’écran des objets usb approuvés" lightbox= "media/188234372-526d20b3-cfea-4f1d-8d63-b513497ada52.png":::

    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml). Consultez l’étape 3 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur dans le fichier XML.

2. Création d’une stratégie

    1. Stratégie 1 : Bloquer l’accès à l’écriture et à l’exécution pour tout groupe de stockage amovible, mais autoriser les objets usb approuvés.

        :::image type="content" source="media/188243425-c0772ed4-6537-4c6a-9a1d-1dbb48018578.png" alt-text="Capture d’écran de la stratégie 1" lightbox= "media/188243425-c0772ed4-6537-4c6a-9a1d-1dbb48018578.png":::

    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Scenario%201%20Block%20Write%20and%20Execute%20Access%20but%20allow%20approved%20USBs.xml). Consultez l’étape 4 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

    2. Stratégie 2 : Auditer l’accès en écriture et en exécution pour les objets usb autorisés.

        :::image type="content" source="media/188243552-5d2a90ab-dba6-450f-ad8f-86a862f6e739.png" alt-text="Capture d’écran de la stratégie 2" lightbox= "media/188243552-5d2a90ab-dba6-450f-ad8f-86a862f6e739.png":::

    Que signifie « 54 » dans la stratégie ? C’est 18 + 36 = 54 :

    - Accès en écriture : niveau disque 2 + niveau système de fichiers 16 = 18.
    - Exécution : niveau disque 4 + niveau système de fichiers 32 = 36.

    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Scenario%201%20Audit%20Write%20and%20Execute%20access%20to%20aproved%20USBs.xml). Consultez l’étape 4 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

### <a name="scenario-2-audit-write-and-execute-access-for-all-but-block-specific-blocked-usbs"></a>Scénario 2 : Auditer l’accès à l’écriture et à l’exécution pour tous les objets usb bloqués, à l’exception d’un bloc spécifique

Pour ce scénario, vous devez créer deux groupes : un groupe pour tout stockage amovible et un autre pour les objets usb bloqués. Vous devez également créer deux stratégies : une stratégie pour auditer l’accès en écriture et en exécution pour n’importe quel groupe de stockage amovible et l’autre stratégie pour refuser le groupe usb bloqué.

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible, CD/DVD et appareils portables Windows.

        :::image type="content" source="media/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png" alt-text="Capture d’écran du groupe 1" lightbox="media/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png":::
    
    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml). Consultez l’étape 3 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

    2. Groupe 2 : Bases de données non approuvées en fonction des propriétés de l’appareil.

        :::image type="content" source="media/188243875-0693ebcf-00c3-45bd-afd3-57a79df9dce6.png" alt-text="Capture d’écran du groupe 2" lightbox= "media/188243875-0693ebcf-00c3-45bd-afd3-57a79df9dce6.png":::
     
    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Unapproved%20USBs%20Group.xml). Consultez l’étape 3 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.


    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur dans le fichier XML.

2. Création d’une stratégie

    1. Stratégie 1 : Bloquer l’accès à l’écriture et à l’exécution pour tous les objets usb non approuvés spécifiques, sauf bloquer.

        :::image type="content" source="media/188244024-62355ded-353c-4d3a-ba61-4520d48f5a18.png" alt-text="Capture d’écran de la stratégie de blocage des objets usb non approuvés" lightbox= "media/188244024-62355ded-353c-4d3a-ba61-4520d48f5a18.png":::
    
    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Scenario%202%20Audit%20Write%20and%20Execute%20access%20to%20all%20but%20block%20specific%20unapproved%20USBs.xml). Consultez l’étape 4 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

    2. Stratégie 2 : Auditer l’accès en écriture et en exécution pour d’autres utilisateurs.

        :::image type="content" source="media/188244203-36c869b6-9330-4e2a-854b-494c342bb77d.png" alt-text="Capture d’écran de l’écriture d’audit et de l’exécution de l’accès" lightbox= "media/188244203-36c869b6-9330-4e2a-854b-494c342bb77d.png":::
    
    Que signifie « 54 » dans la stratégie ? C’est 18 + 36 = 54 :

    - Accès en écriture : niveau disque 2 + niveau système de fichiers 16 = 18.
    - Exécution : niveau disque 4 + niveau système de fichiers 32 = 36.
    
    Voici [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Scenario%202%20Audit%20Write%20and%20Execute%20access%20to%20others.xml). Consultez l’étape 4 de la section [Déployer le stockage amovible 存取控制](deploy-manage-removable-storage-intune.md#deploy-removable-storage-access-control-by-using-intune-oma-uri) pour déployer la configuration.

## <a name="use-intune-user-interface"></a>Utiliser l’interface utilisateur Intune

Cette fonctionnalité est disponible dans le Centre d’administration Microsoft Endpoint Manager (<https://endpoint.microsoft.com/>). 

Accédez à la stratégie de création **de la surface d’attaque** >  de **sécurité** >  du point de **terminaison**. Choisissez **Plateforme : Windows 10 et versions ultérieures** avec **Profil : Contrôle d’appareil**.
