---
title: Collecter les données de diagnostic de Antivirus Microsoft Defender
description: Utiliser un outil pour collecter des données pour résoudre les problèmes liés à l’Antivirus Microsoft Defender
keywords: résolution des problèmes, erreur, correctif, conformité des mises à jour, oms, surveiller, rapport, Microsoft Defender av, objet de stratégie de groupe, paramètre, données de diagnostic, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/29/2020
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 02225524e2b0c38e652fa2567564b086e412a2e8
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679458"
---
# <a name="collect-microsoft-defender-antivirus-diagnostic-data"></a>Collecter les données de diagnostic de l’Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article explique comment collecter des données de diagnostic qui peuvent être utilisées par les équipes de support et d’ingénierie microsoft pour aider à résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation de l’antivirus Microsoft Defender.

> [!NOTE]
> Dans le cadre du processus d’investigation ou de réponse, vous pouvez collecter un package d’investigation à partir d’un appareil. Voici comment : [collecter un package d’investigation à partir d’appareils](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices).

Sur au moins deux appareils qui rencontrent le même problème, obtenez le fichier de diagnostic .cab en effectuant les étapes suivantes :

1. Ouvrez une version de niveau administrateur de l’invite de commandes comme suit :

    a. Ouvrez le menu **Démarrer** .

    b. Tapez **cmd**. Cliquez avec le bouton droit sur **l’invite de commandes** , puis **sélectionnez Exécuter en tant qu’administrateur**.

    c. Spécifiez les informations d’identification de l’administrateur ou approuvez l’invite.

2. Accédez au répertoire de l’antivirus Microsoft Defender. Par défaut, cette valeur est `C:\Program Files\Windows Defender`.

   > [!NOTE]
   > Si vous exécutez une [version mise à jour de la plateforme anti-programme malveillant Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform), exécutez-la `MpCmdRun` à l’emplacement suivant : `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`.

3. Tapez la commande suivante, puis **appuyez sur Entrée**

    ```Dos
    mpcmdrun.exe -GetFiles
    ```

4. Un fichier .cab est généré et contient différents journaux de diagnostic. L’emplacement du fichier est spécifié dans la sortie de l’invite de commandes. Par défaut, l’emplacement est `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

   > [!NOTE]
   > Pour rediriger le fichier cab vers un autre chemin d’accès ou un partage UNC, utilisez la commande suivante :
   >
   > `mpcmdrun.exe -GetFiles -SupportLogLocation <path>`
   >
   > Pour plus d’informations, consultez [Rediriger les données de diagnostic vers un partage UNC](#redirect-diagnostic-data-to-a-unc-share).

5. Copiez ces fichiers .cab à un emplacement accessible par le support Microsoft. Par exemple, un dossier OneDrive protégé par mot de passe que vous pouvez partager avec nous.

> [!NOTE]
> Si vous rencontrez un problème de conformité à la mise à jour, envoyez un e-mail à l’aide du <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">modèle de courrier de support update compliance</a> et renseignez le modèle avec les informations suivantes :
>
> Je rencontre le problème suivant lors de l’utilisation de l’Antivirus Microsoft Defender dans Update Compliance :
>
> J’ai fourni au moins 2 fichiers de support .cab à l’emplacement suivant :
>
> \<accessible share, including access details such as password\>
>
> Mon ID d’espace de travail OMS est le suivant :
>
> Veuillez me contacter à l’adresse suivante :

## <a name="redirect-diagnostic-data-to-a-unc-share"></a>Rediriger les données de diagnostic vers un partage UNC

Pour collecter des données de diagnostic sur un référentiel central, vous pouvez spécifier le paramètre SupportLogLocation.

```Dos
mpcmdrun.exe -GetFiles -SupportLogLocation <path>
```

Copie les données de diagnostic dans le chemin d’accès spécifié. Si le chemin d’accès n’est pas spécifié, les données de diagnostic sont copiées vers l’emplacement spécifié dans la configuration de l’emplacement du journal de support.

Lorsque le paramètre SupportLogLocation est utilisé, une structure de dossiers comme suit est créée dans le chemin d’accès de destination :

```Dos
<path>\<MMDD>\MpSupport-<hostname>-<HHMM>.cab
```

<br>

****

|champ|Description|
|---|---|
|chemin|Chemin d’accès tel que spécifié sur la ligne de commande ou récupéré à partir de la configuration|
|MMDD|Mois et jour où les données de diagnostic ont été collectées (par exemple, 0530)|
|Hostname|Nom d’hôte de l’appareil sur lequel les données de diagnostic ont été collectées|
|HHMM|Heures et minutes de collecte des données de diagnostic (par exemple, 1422)|
|

> [!NOTE]
> Lorsque vous utilisez un partage de fichiers, assurez-vous que le compte utilisé pour collecter le package de diagnostic dispose d’un accès en écriture au partage.

## <a name="specify-location-where-diagnostic-data-is-created"></a>Spécifier l’emplacement où les données de diagnostic sont créées

Vous pouvez également spécifier l’emplacement de création du fichier de .cab de diagnostic à l’aide d’un objet stratégie de groupe (GPO).

1. Ouvrez l’éditeur de stratégie de groupe local et recherchez l’objet de stratégie de groupe SupportLogLocation à l’adresse : `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\SupportLogLocation`.

2. Sélectionnez **Définir le chemin d’accès au répertoire pour copier les fichiers journaux de prise en charge**.

   :::image type="content" source="images/GPO1-SupportLogLocationDefender.png" alt-text="Éditeur de stratégie de groupe local" lightbox="images/GPO1-SupportLogLocationDefender.png":::

   :::image type="content" source="images/GPO2-SupportLogLocationGPPage.png" alt-text="Définition du chemin d’accès pour le paramètre fichiers journaux" lightbox="images/GPO2-SupportLogLocationGPPage.png":::

   :::image type="content" source="images/GPO1-SupportLogLocationDefender.png" alt-text="Éditeur de stratégie de groupe local" lightbox="images/GPO1-SupportLogLocationDefender.png"::: 
        
   :::image type="content" source="images/GPO2-SupportLogLocationGPPage.png" alt-text="Chemin d’accès de définition pour la configuration du paramètre fichiers journaux" lightbox="images/GPO2-SupportLogLocationGPPage.png":::
 
3. Dans l’éditeur de stratégie, **sélectionnez Activé**.

4. Spécifiez le chemin d’accès au répertoire dans lequel vous souhaitez copier les fichiers journaux de support dans le champ **Options** .
   :::image type="content" source="images/GPO3-SupportLogLocationGPPageEnabledExample.png" alt-text="Paramètre personnalisé du chemin d’accès au répertoire activé" lightbox="images/GPO3-SupportLogLocationGPPageEnabledExample.png":::
5. Sélectionnez **OK** ou **Appliquer**.

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de création de rapports sur l’antivirus Microsoft Defender](troubleshoot-reporting.md)
