---
title: Pertahanan Microsoft untuk Titik Akhir questions fréquentes sur le stockage amovible de contrôle d’appareil
description: Répond aux questions fréquemment posées sur le stockage amovible du contrôle d’appareil MDE.
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
ms.date: 08/25/2022
ms.reviewer: tewchen
search.appverid: met150
ms.openlocfilehash: 89b4b0f3712132b40050205a38fb761b0ba1db1d
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736049"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-frequently-asked-questions"></a>Pertahanan Microsoft untuk Titik Akhir questions fréquentes sur le stockage amovible de contrôle d’appareil

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="how-do-i-generate-guid-for-group-idpolicyrule-identry-id"></a>如何实现 générer le GUID pour l’ID de groupe/ID PolicyRule/ID d’entrée ?

Vous pouvez générer le GUID par le biais de Open Source en ligne ou de PowerShell. Pour plus d’informations, consultez [Comment générer un GUID via PowerShell](/powershell/module/microsoft.powershell.utility/new-guid).

![Capture d’écran du GUID dans PowerShell.](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

## <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>Quelles sont les limitations de stratégie et de média de stockage amovibles ?

L’appel principal est effectué via OMA-URI (GET to read ou PATCH to update) à partir du Centre d’administration Microsoft Endpoint Manager (Intune) ou via Microsoft Graph API. La limitation est identique à n’importe quel profil de configuration personnalisé OMA-URI chez Microsoft, qui est officiellement de 350 000 caractères pour les fichiers XML.

Par exemple, si vous avez besoin de deux blocs d’entrées par SID utilisateur pour « Autoriser » / « Auditer les utilisateurs autorisés », puis de deux blocs d’entrées à la fin de « Refuser », vous serez en mesure de gérer 2 276 utilisateurs.

## <a name="why-doesnt-the-policy-work"></a>Pourquoi la stratégie ne fonctionne-t-elle pas ?

1. La raison la plus courante est qu’il n’existe aucune version requise du [client anti-programme malveillant](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

2. Une autre raison peut être que le fichier XML n’est pas correctement mis en forme. Par exemple, si vous n’utilisez pas la mise en forme markdown correcte pour le caractère « & » dans le fichier XML ou que l’éditeur de texte peut ajouter une marque d’ordre d’octet (BOM) 0xEF 0xBB 0xBF au début des fichiers, ce qui entraîne l’échec de l’analyse XML. Une solution simple consiste à télécharger [l’exemple de fichier](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (sélectionnez **Raw** , puis **Enregistrer sous**), puis mettez à jour.

3. Si vous déployez et gérez la stratégie à l’aide de نهج المجموعة, veillez à combiner tous les PolicyRule dans un fichier XML au sein d’un nœud parent appelé PolicyRules. Combinez également tous les groupes dans un fichier XML au sein d’un nœud parent appelé Groupes. Si vous gérez via Intune, conservez un PolicyRule un fichier XML et un fichier XML de groupe.

Si cela ne fonctionne toujours pas, contactez le support technique et partagez votre cabine de support. Pour obtenir ce fichier, utilisez l’invite de commandes en tant qu’administrateur : 

`"%programfiles%\Windows Defender\MpCmdRun.exe" -GetFiles`

## <a name="why-is-there-no-configuration-ux-for-some-policy-groups"></a>Pourquoi n’existe-t-il pas d’expérience utilisateur de configuration pour certains groupes de stratégies ? 

Il n’existe aucune expérience utilisateur de configuration pour **définir des groupes de stratégies de contrôle d’appareil** et **définir des règles de stratégie de contrôle d’appareil** sur votre نهج المجموعة. Toutefois, vous pouvez toujours obtenir les fichiers .adml et .admx associés en sélectionnant **Raw** et **Save as** at the [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) and [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) files.

## <a name="how-do-i-confirm-that-the-latest-policy-has-been-deployed-to-the-target-machine"></a>如何实现 confirmer que la dernière stratégie a été déployée sur l’ordinateur cible ?

Vous pouvez exécuter l’applet `Get-MpComputerStatus` de commande PowerShell en tant qu’administrateur. La valeur suivante indique si la dernière stratégie a été appliquée à l’ordinateur cible.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

## <a name="how-can-i-know-which-machine-is-using-out-of-date-anti-malware-client-version-in-the-organization"></a>Comment savoir quel ordinateur utilise une version obsolète du client anti-programme malveillant dans l’organisation ?

Vous pouvez utiliser la requête suivante pour obtenir la version du client anti-programme malveillant sur le portail de sécurité Microsoft 365 :

```kusto
//check the anti-malware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```

## <a name="how-do-i-find-the-media-property-in-the-device-manager"></a>如何实现 trouver la propriété multimédia dans le Enhedshåndtering ?

1. Branchez le média.

2. Ouvrez le Gestionnaire de périphériques. 

   ![Capture d’écran de Enhedshåndtering.](https://user-images.githubusercontent.com/81826151/181859412-affd6aa1-09ad-44bf-9541-330499cc2c87.png)

3. Recherchez le média dans le Enhedshåndtering, cliquez avec le bouton droit, puis sélectionnez **Propriétés**.

   :::image type="content" alt-text="Capture d’écran du média dans le Enhedshåndtering." source="https://user-images.githubusercontent.com/81826151/181859700-62a6f704-b12e-41e3-a048-7d63432654a4.png":::

4. Ouvrez **Détails**, puis sélectionnez **Propriétés**.

   :::image type="content" alt-text="Capture d’écran de la propriété de l’appareil dans Enhedshåndtering." source="https://user-images.githubusercontent.com/81826151/181859852-00bc8b11-8ee5-4d46-9770-fa29f894d13f.png":::
    