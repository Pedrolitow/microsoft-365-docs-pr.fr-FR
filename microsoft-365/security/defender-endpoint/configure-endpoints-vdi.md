---
title: Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.
description: Déployez le package de configuration sur un appareil VDI (Virtual Desktop Infrastructure) afin qu’il soit intégré au service Microsoft Defender for Endpoint.
keywords: configurer l’infrastructure VDI (Virtual Desktop Infrastructure), vdi, gestion des appareils, configurer Microsoft Defender pour les points de terminaison, points de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 09/22/2021
ms.technology: mde
ms.openlocfilehash: 57d029e55759a08d84efe1eb684b67caf3e8653a
ms.sourcegitcommit: d78553deeba23d2f8238f10e64c2e27f235dc37f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2021
ms.locfileid: "60124684"
---
# <a name="onboarding-non-persistent-virtual-desktop-infrastructure-devices"></a>Intégration d’appareils d’infrastructure de bureau virtuel non persistants


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Périphériques VDI (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

## <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

Defender pour le point de terminaison prend en charge l’intégration de session VDI non persistante.

Il peut y avoir des difficultés associées lors de l’intégration des VDIs. Les défis classiques de ce scénario sont les suivants :

- Intégration anticipée instantanée d’une session à durée de vie courte, qui doit être intégré à Defender for Endpoint avant la mise en service réelle.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Les appareils VDI peuvent apparaître dans le portail Defender for Endpoint sous la forme :

- Entrée unique pour chaque appareil.

  > [!NOTE]
  > Dans ce cas, le *même* nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans surveillance.

- Plusieurs entrées pour chaque appareil - une pour chaque session.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en évidence les étapes pour les entrées simples et multiples.

> [!WARNING]
> Pour les environnements dans lequel il existe des configurations de ressources faibles, la procédure de démarrage VDI peut ralentir l’intégration du capteur Defender for Endpoint.

### <a name="for-windows-10-or-windows-11-or-windows-server-2019-or-windows-server-2022"></a>Pour Windows 10, Windows 11, Windows Server 2019 ou Windows Server 2022

1. Ouvrez le fichier de package de configuration VDI .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du [portail Microsoft 365 Defender :](https://security.microsoft.com/)
   1. Dans le volet de navigation, sélectionnez **Paramètres** \> **Endpoints** \> **Device Management** \> **Onboarding**.
   2. Sélectionnez Windows 10 ou Windows 11 comme système d’exploitation.
   3. Dans le **champ Méthode de** déploiement, sélectionnez les **scripts d’intégration VDI pour les** points de terminaison non persistants.
   4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Copiez les fichiers du dossier WindowsDefenderATPOnboardingPackage extraits du fichier .zip dans l’image de premier plan sous le chemin `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` d’accès.
    1. Si vous implémentez plusieurs entrées pour chaque appareil - une pour chaque session, copiez WindowsDefenderATPOnboardingScript.cmd.
    2. Si vous implémentez une entrée unique pour chaque appareil, copiez les fichiers Onboard-NonPersistentMachine.ps1 et WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Si vous ne voyez pas le `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` dossier, il peut être masqué. Vous devez choisir l’option Afficher les fichiers **et dossiers masqués** dans l’Explorateur de fichiers.

3. Ouvrez une fenêtre Éditeur de stratégie de groupe locale et accédez à **Configuration** ordinateur \> **Windows Paramètres** \> **scripts de** \> **démarrage.**

   > [!NOTE]
   > La stratégie de groupe de domaine peut également être utilisée pour l’intégration d’appareils VDI non persistants.

4. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
    - Pour une entrée unique pour chaque appareil :

         Sélectionnez **l’onglet Scripts PowerShell,** puis cliquez sur Ajouter **(Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script PowerShell `Onboard-NonPersistentMachine.ps1` d’intégration. Il n’est pas nécessaire de spécifier l’autre fichier, car il sera déclenché automatiquement.

    - Pour plusieurs entrées pour chaque appareil :

         Sélectionnez **l’onglet Scripts,** puis cliquez sur Ajouter **(Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script Bash `WindowsDefenderATPOnboardingScript.cmd` d’intégration.

5. Testez votre solution :
   1. Créez un pool avec un seul appareil.
   2. Connectez-vous à l’appareil.
   3. Déconnectez-vous de l’appareil.
   4. Connectez-vous à l’appareil avec un autre utilisateur.
   5. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
      - Pour une entrée unique pour chaque appareil : vérifiez une seule entrée dans Microsoft 365 Defender portail.
      - Pour plusieurs entrées pour chaque appareil : vérifiez plusieurs entrées dans Microsoft 365 Defender portail.

6. Cliquez **sur La liste Appareils** dans le volet de navigation.

7. Utilisez la fonction de recherche en entrant le nom de l’appareil et **sélectionnez Appareil** comme type de recherche.

## <a name="for-downlevel-skus-windows-server-2008-r22012-r22016"></a>Pour les S SKUs de niveau bas (Windows Server 2008 R2/2012 R2/2016)

> [!NOTE]
> Le Registre suivant n’est pertinent que lorsque l’objectif est d’obtenir une entrée unique pour chaque appareil.

1. Définissez la valeur de Registre sur :

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    ou à l’aide de la ligne de commande :

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. Suivez le [processus d’intégration du serveur.](configure-server-endpoints.md#windows-server-2008-r2-sp1-windows-server-2012-r2-and-windows-server-2016)

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images VDI (Virtual Desktop Infrastructure) non persistantes

En tant que meilleure pratique, nous vous recommandons d’utiliser des outils de maintenance hors connexion pour mettre à jour les images de base/de base.

Par exemple, vous pouvez utiliser les commandes ci-dessous pour installer une mise à jour pendant que l’image reste hors connexion :

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Pour plus d’informations sur les commandes DISM et la maintenance hors connexion, consultez les articles ci-dessous :

- [Modifier une image Windows à l’aide de DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Options de gestion des images DISM Command-Line d’images](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Réduire la taille du magasin de composants dans une image de Windows hors connexion](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Si la maintenance hors connexion n’est pas une option viable pour votre environnement VDI non persistant, les étapes suivantes doivent être prises pour garantir la cohérence et l’état du capteur :

1. Après avoir démarré l’image maître pour la maintenance en ligne ou la correction, exécutez un script de mise hors service pour désactiver le capteur Defender pour point de terminaison. Pour plus d’informations, voir [Les appareils hors-carte à l’aide d’un script local.](configure-endpoints-script.md#offboard-devices-using-a-local-script)

2. Assurez-vous que le capteur est arrêté en exécutant la commande ci-dessous dans une fenêtre CMD :

   ```console
   sc query sense
   ```

3. Service de l’image selon les besoins.

4. Exécutez les commandes ci-dessous à l’aide PsExec.exe (qui peut être téléchargé à partir de pour nettoyer le contenu du dossier cyber que le capteur a peut-être cumulé https://download.sysinternals.com/files/PSTools.zip) depuis le démarrage :

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Resealez l’image de l’or/maître comme vous le feriez normalement.

## <a name="related-topics"></a>Rubriques connexes

- [Intégrer des Windows à l’aide de la stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer Windows appareils à l’aide Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer des Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer Windows appareils à l’aide d’un script local](configure-endpoints-script.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
