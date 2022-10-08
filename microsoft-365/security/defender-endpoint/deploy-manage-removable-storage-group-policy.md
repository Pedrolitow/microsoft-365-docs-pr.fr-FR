---
title: Déployer et gérer des Access Control de stockage amovibles à l’aide d’une stratégie de groupe
description: Utilisez la stratégie de groupe pour déployer et gérer le contrôle d’accès au stockage amovible.
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
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.date: 09/09/2022
ms.reviewer: tewchen
search.appverid: met150
ms.openlocfilehash: 947388cd2840c94e7faeb956d3fcaac309303307
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68174927"
---
# <a name="deploy-and-manage-removable-storage-access-control-using-group-policy"></a>Déployer et gérer des Access Control de stockage amovibles à l’aide d’une stratégie de groupe

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> La gestion stratégie de groupe et Intune gestion OMA-URI/Custom Policy de ce produit sont désormais en disponibilité générale (4.18.2106) : consultez le [blog Tech Community : Protéger votre stockage amovible et votre imprimante avec Microsoft Defender pour point de terminaison](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

La fonctionnalité De stockage amovible Access Control vous permet d’appliquer une stratégie à l’aide d’une stratégie de groupe à l’utilisateur ou à l’appareil, ou aux deux.

## <a name="device-control-removable-storage-access-control-policies"></a>Stratégies de Access Control de stockage amovibles device control

Vous pouvez utiliser les propriétés suivantes pour créer un groupe de stockage amovible.

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Avant de commencer à utiliser les Access Control de stockage amovibles, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Pour accéder aux Access Control de stockage amovibles et les utiliser par le biais d’une stratégie de groupe, vous devez disposer de Microsoft 365 E5.

## <a name="deploy-using-group-policy"></a>Déployer à l’aide d’une stratégie de groupe

1. Activez ou désactivez les Access Control de stockage amovibles :

   Vous pouvez activer ou désactiver le contrôle d’appareil comme suit :

   - Accédez à Computer **Configuration** > **Administrative Templates** > **Windows Components** >  **Microsoft Defender Antivirus** > **Features** > **Device Control**.
   - Dans la fenêtre **Contrôle d’appareil** , sélectionnez **Activé**.

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="Capture d’écran de l’activation de RSAC à l’aide de stratégie de groupe " lightbox="images/enable-rsac-gp.png":::

> [!NOTE]
> Si vous ne voyez pas ces objets de stratégie de groupe, vous devez ajouter le modèle d’administration de stratégie de groupe. Vous pouvez télécharger le modèle d’administration (WindowsDefender.adml et WindowsDefender.admx) à partir de https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples.

2. Définir l’application par défaut :

   Vous pouvez définir l’accès par défaut (Refuser ou Autoriser) pour toutes les fonctionnalités de contrôle d’appareil (RemovableMediaDevices, CdRomDevices, WpdDevices, PrinterDevices).

   Par exemple, vous pouvez avoir une stratégie Deny ou Allow pour RemovableMediaDevices, mais pas pour CdRomDevices ou WpdDevices. Vous définissez le refus par défaut via cette stratégie, puis l’accès en lecture/écriture/exécution à CdRomDevices ou WpdDevices est bloqué. Si vous souhaitez uniquement gérer le stockage, veillez à créer une stratégie Autoriser pour l’imprimante. Sinon, cette application par défaut sera également appliquée à l’imprimante.

   - Accédez aux modèles **d’administration** de **configuration** >  d’ordinateur **composants** >  Windows Microsoft Defender Contrôle **d’appareil** > **des fonctionnalités** >  >  **antivirus** > **Sélectionner l’application par défaut du contrôle d’appareil**

   - Dans le volet **Sélectionner l’application par défaut du contrôle d’appareil** , sélectionnez **Refuser par défaut** :

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="Capture d’écran de la définition de l’application par défaut = Refuser à l’aide de stratégie de groupe" lightbox="images/set-default-enforcement-deny-gp.png":::

3. Créez un fichier XML pour les groupes de stockage amovibles :

   Utilisez les propriétés du groupe de stockage amovible pour créer un fichier XML pour le ou les groupes de stockage amovibles, enregistrez le fichier XML dans le partage réseau et définissez le paramètre comme suit :

   - Accédez aux modèles **d’administration** de **configuration** \> d’ordinateur **composants** \> \> Windows Microsoft Defender **Contrôle** \> **d’appareil antivirus** \> **Définir des groupes de stratégies de contrôle d’appareil**.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="Capture d’écran de définir des groupes de stratégies de contrôle d’appareil" lightbox="images/define-device-control-policy-grps-gp.png":::

   - Dans la fenêtre **Définir des groupes de stratégies de contrôle d’appareil** , spécifiez le chemin d’accès du fichier de partage réseau contenant les données des groupes XML.

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

4. Créez un fichier XML pour les règles de stratégie d’accès :

   Utilisez les propriétés dans les règles de stratégie d’accès au stockage amovible pour créer un code XML pour la règle de stratégie d’accès au stockage amovible de chaque groupe, enregistrez le fichier XML dans le partage réseau et devlier le paramètre comme suit :

   - Accédez à Computer **Configuration** > **Administrative Templates** > **Windows Components** >  **Microsoft Defender Antivirus** > **Device Control** > **Define device control policy rules**.

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="Capture d’écran de la définition des règles de stratégie de contrôle d’appareil" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - Dans la fenêtre **Définir les règles de stratégie de contrôle d’appareil** , sélectionnez **Activé**, puis entrez le chemin d’accès du fichier de partage réseau contenant les données de règles XML.

> [!NOTE]
> Les commentaires utilisant la notation `<!-- COMMENT -->` de commentaire XML peuvent être utilisés dans les fichiers XML de règle et de groupe, mais ils doivent se trouver à l’intérieur de la première balise XML, et non de la première ligne du fichier XML.

5. Définir l’emplacement d’une copie du fichier (preuve) :

    Si vous souhaitez avoir une copie du fichier (preuve) lorsque l’accès en écriture se produit, définissez **les options** appropriées dans votre règle de stratégie d’accès au stockage amovible dans le fichier XML, puis spécifiez l’emplacement où le système peut enregistrer la copie.

    - Accédez à Computer **Configuration** > **Administrative Templates** > **Windows Components** >  **Microsoft Defender Antivirus** > **Device Control** > **Define Device Control evidence data remote location**.

    - Dans le volet **Définir l’emplacement distant des données de preuve de Contrôle d’appareil** , sélectionnez **Activé**, puis spécifiez le chemin du dossier de partage local ou réseau.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="Capture d’écran de l’emplacement distant des données de preuve Définir le contrôle d’appareil." lightbox="images/evidence-data-remote-location-gp.png":::

## <a name="scenarios"></a>Scénarios

Voici quelques scénarios courants pour vous aider à vous familiariser avec Microsoft Defender pour point de terminaison Access Control de stockage amovible. Notez que dans les exemples suivants, « Application par défaut » n’a pas été utilisé, car l’application par défaut s’applique à la fois au stockage amovible et à l’imprimante.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>Scénario 1 : Empêcher l’accès en écriture et en exécution à tous, mais autoriser des bases de données approuvées spécifiques

Pour ce scénario, vous devez créer deux groupes : un groupe pour tout stockage amovible et un autre pour les objets USB approuvés. Vous devez également créer deux stratégies : une stratégie pour refuser l’accès En écriture et exécution pour tout groupe de stockage amovible, et l’autre pour auditer le groupe usBs approuvé.

1. Créer des groupes

    1. Groupe 1 : Tout stockage amovible, CD/DVD et appareils portables Windows.

    ![Capture d’écran du stockage amovible](https://user-images.githubusercontent.com/81826151/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png)

    2. Groupe 2 : Bases de données américaines approuvées en fonction des propriétés de l’appareil.

    ![Capture d’écran des objets usb approuvés](https://user-images.githubusercontent.com/81826151/188234372-526d20b3-cfea-4f1d-8d63-b513497ada52.png)
    
    Combinez ces deux groupes en [un seul fichier XML](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml). Pour déployer cette configuration, consultez l’étape 3 de la section [Déployer à l’aide](deploy-manage-removable-storage-group-policy.md#deploy-using-group-policy) d’une stratégie de groupe.

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : Bloquer l’accès à l’écriture et à l’exécution pour tout groupe de stockage amovible, mais autoriser les objets usb approuvés.

    ![Capture d’écran de l’accès d’écriture et d’exécution de blocs](https://user-images.githubusercontent.com/81826151/188237490-d736ace1-4912-4788-9e94-3fc506692a41.png)


    2. Stratégie 2 : Auditer l’accès en écriture et en exécution pour les objets usb autorisés.

    ![Capture d’écran de l’écriture d’audit et de l’exécution de l’accès](https://user-images.githubusercontent.com/81826151/188237598-b28dd534-9ea4-4cdd-832b-afff50f9897b.png)

    Que signifie « 54 » dans la stratégie ? C’est 18 + 36 = 54 :

    - Accès en écriture : niveau disque 2 + niveau système de fichiers 16 = 18.
    - Exécution : niveau disque 4 + niveau système de fichiers 32 = 36.

    Combinez ces deux règles de stratégie dans [un fichier XML](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Scenario%201%20GPO%20Policy%20-%20Prevent%20Write%20and%20Execute%20access%20to%20all%20but%20allow%20specific%20approved%20USBs.xml). Pour déployer cette configuration, consultez l’étape 4 de la section [Déployer à l’aide](deploy-manage-removable-storage-group-policy.md#deploy-using-group-policy) d’une stratégie de groupe.

### <a name="scenario-2-audit-write-and-execute-access-for-all-but-block-specific-blocked-usbs"></a>Scénario 2 : Auditer l’accès à l’écriture et à l’exécution pour tous les objets usb bloqués, à l’exception d’un bloc spécifique

Pour ce scénario, vous devez créer deux groupes : un groupe pour tout stockage amovible et un autre pour les objets usb bloqués. Vous devez également créer deux stratégies : une stratégie pour auditer l’accès en écriture et en exécution pour n’importe quel groupe de stockage amovible et l’autre stratégie pour refuser le groupe usb bloqué.

1. Créer des groupes

    1. Groupe 1 : Tous les périphériques portables amovibles, CD/DVD et windows.

    ![Capture d’écran du stockage amovible dans les groupes](https://user-images.githubusercontent.com/81826151/188234308-4db09787-b14e-446a-b9e0-93c99b08748f.png)

    2. Groupe 2 : Bases de données usuelles bloquées en fonction des propriétés de l’appareil.

    ![Capture d’écran des objets usb bloqués](https://user-images.githubusercontent.com/81826151/188234372-526d20b3-cfea-4f1d-8d63-b513497ada52.png)
    
    Combinez ces deux groupes en [un seul fichier XML](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml). Pour déployer cette configuration, consultez l’étape 3 de la section [Déployer à l’aide](deploy-manage-removable-storage-group-policy.md#deploy-using-group-policy) d’une stratégie de groupe.

    > [!TIP]
    > `&amp;` Remplacez `&` par la valeur.

2. Création d’une stratégie

    1. Stratégie 1 : Bloquer l’accès à l’écriture et à l’exécution pour tous les objets usb non approuvés spécifiques, sauf bloquer.

    ![Capture d’écran de bases de données non approuvées spécifiques](https://user-images.githubusercontent.com/81826151/188239025-218a1985-b198-4f7e-b323-b4b6fb7e274e.png)

    2. Stratégie 2 : Auditer l’accès en écriture et en exécution pour d’autres utilisateurs. 

    ![Capture d’écran de l’écriture d’audit et de l’exécution de l’accès dans la stratégie de groupe](https://user-images.githubusercontent.com/81826151/188239144-3e6a2781-6927-487a-aa01-498a0904ad98.png)

    Que signifie « 54 » dans la stratégie ? C’est 18 + 36 = 54 :

    - Accès en écriture : niveau disque 2 + niveau système de fichiers 16 = 18.
    - Exécution : niveau disque 4 + niveau système de fichiers 32 = 36.

    Combinez ces deux règles de stratégie dans [un fichier XML](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Scenario%202%20GPO%20Policy%20-%20Audit%20Write%20and%20Execute%20access%20to%20all%20but%20block%20specific%20unapproved%20USBs.xml). Pour déployer cette configuration, consultez l’étape 4 de la section [Déployer à l’aide](deploy-manage-removable-storage-group-policy.md#deploy-using-group-policy) d’une stratégie de groupe.

