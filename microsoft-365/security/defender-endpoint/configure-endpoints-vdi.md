---
title: Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.
description: Déployez le package de configuration sur un appareil VDI (Virtual Desktop Infrastructure) afin qu’il soit intégré au service Microsoft Defender pour point de terminaison service.
keywords: configurer l’infrastructure VDI (Virtual Desktop Infrastructure), vdi, gestion des appareils, configurer Microsoft Defender pour point de terminaison, points de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: e292c2f1e0d01e51e3962b71a940927078ab95ad
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634710"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Intégrer des appareils VDI (Virtual Desktop Infrastructure) non persistants dans Microsoft 365 Defender

L’infrastructure VDI (Virtual Desktop Infrastructure) est un concept d’infrastructure informatique qui permet aux utilisateurs finaux d’accéder aux instances de bureau virtuel d’entreprise à partir de presque n’importe quel appareil (par exemple, votre ordinateur personnel, votre smartphone ou votre tablette), ce qui élimine la nécessité pour l’organisation de fournir aux utilisateurs des ordinateurs physiques. L’utilisation d’appareils VDI réduit les coûts, car les services informatiques ne sont plus responsables de la gestion, de la réparation et du remplacement des points de terminaison physiques. Les utilisateurs autorisés peuvent accéder aux mêmes serveurs, fichiers, applications et services d’entreprise à partir de n’importe quel appareil approuvé via un client de bureau ou un navigateur sécurisé.

Comme tout autre système dans un environnement informatique, ces systèmes doivent également avoir une solution endpoint Detection and Response (PEPT) et antivirus pour se protéger contre les menaces et attaques avancées.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Périphériques VDI (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **Les VDI persistants** -  [L’intégration d’un ordinateur VDI](configure-endpoints.md) persistant dans Microsoft Defender pour point de terminaison est gérée de la même manière que pour un ordinateur physique, tel qu’un ordinateur de bureau ou un ordinateur portable. La stratégie de groupe, Microsoft Endpoint Manager et d’autres méthodes peuvent être utilisées pour intégrer un ordinateur persistant. Dans le portail Microsoft 365 Defender, (https://security.microsoft.com) sous intégration, sélectionnez votre méthode d’intégration préférée et suivez les instructions pour ce type. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Intégration d’appareils VDI (Virtual Desktop Infrastructure) non persistants

Defender pour le point de terminaison prend en charge l’intégration de session VDI non persistante.

Il peut y avoir des difficultés associées lors de l’intégration d’instances VDI. Voici quelques défis classiques pour ce scénario :

- Intégration anticipée instantanée d’une session à durée de vie courte, qui doit être intégré à Defender for Endpoint avant la mise en service réelle.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Dans un environnement VDI, les instances VDI peuvent avoir une durée de vie courte. Les appareils VDI peuvent apparaître dans le portail Defender for Endpoint sous la forme :


- Entrée de portail unique pour chaque instance VDI. Si l’instance VDI était déjà intégré à Microsoft Defender pour point de terminaison et à un moment donné supprimé, puis recréé avec le même nom d’hôte, un nouvel objet représentant cette instance VDI ne sera PAS créé dans le portail. 


  > [!NOTE]
  > Dans ce cas, le *même* nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans surveillance.

- Plusieurs entrées pour chaque appareil - une pour chaque instance VDI.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en évidence les étapes pour les entrées simples et multiples.

> [!WARNING]
> Pour les environnements où il existe des configurations de ressources faibles, la procédure de démarrage VDI peut ralentir l’intégration du capteur Defender for Endpoint.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>Pour Windows 10, Windows 11, ou Windows Server 2012 R2 et ultérieures

> [!NOTE]
> Windows Server 2016 et Windows Server 2012 R2 doivent être préparés en appliquant d’abord le package d’installation à l’aide des instructions des serveurs [Windows](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) intégrés pour que cette fonctionnalité fonctionne.

1.  Ouvrez le fichier de package de configuration VDI .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service. Vous pouvez également obtenir le package à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender:</a>

    1. Dans le volet de navigation, sélectionnez **Paramètres** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Sélectionnez le système d’exploitation.

    1.  Dans le **champ Méthode de** déploiement, sélectionnez **les scripts d’intégration VDI pour les points de terminaison non persistants**.

    1. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

2. Copiez les fichiers du dossier WindowsDefenderATPOnboardingPackage extraits du fichier .zip dans l’image de premier plan sous le chemin d’accès `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Si vous implémentez plusieurs entrées pour chaque appareil - une pour chaque session, copiez WindowsDefenderATPOnboardingScript.cmd.
    2. Si vous implémentez une entrée unique pour chaque appareil, copiez les fichiers Onboard-NonPersistentMachine.ps1 et WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Si vous ne voyez pas le dossier `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , il peut être masqué. Vous devez choisir l’option Afficher les **fichiers et dossiers masqués** dans Explorateur de fichiers.

3. Ouvrez une fenêtre Éditeur stratégie de groupe local et accédez à **Configuration** \> ordinateur **Windows Paramètres** \> **scripts** \> **de démarrage**.

   > [!NOTE]
   > Les stratégie de groupe domaine peuvent également être utilisés pour l’intégration d’appareils VDI non persistants.

4. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
    - Pour une entrée unique pour chaque appareil :

         Sélectionnez **l’onglet Scripts PowerShell**, puis cliquez sur **Ajouter (Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script `Onboard-NonPersistentMachine.ps1`PowerShell d’intégration. Il n’est pas nécessaire de spécifier l’autre fichier, car il sera déclenché automatiquement.

    - Pour plusieurs entrées pour chaque appareil :

         Sélectionnez **l’onglet Scripts**, puis cliquez sur **Ajouter (Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script Bash d’intégration `WindowsDefenderATPOnboardingScript.cmd`.

5. Testez votre solution :
   1. Créez un pool avec un seul appareil.
   2. Connectez-vous à l’appareil.
   3. Déconnectez-vous de l’appareil.
   4. Connectez-vous à l’appareil avec un autre utilisateur.
   5. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
      - Pour une entrée unique pour chaque appareil : vérifiez une seule entrée dans Microsoft 365 Defender portail.
      - Pour plusieurs entrées pour chaque appareil : vérifiez plusieurs entrées dans Microsoft 365 Defender portail.

6. Cliquez **sur La liste Appareils** dans le volet de navigation.

7. Utilisez la fonction de recherche en entrant le nom de l’appareil et sélectionnez **Appareil** comme type de recherche.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>Pour les SSO de niveau bas (Windows Server 2008 R2)

> [!NOTE]
> Ces instructions pour les autres versions Windows server s’appliquent également si vous exécutez la Microsoft Defender pour point de terminaison précédente pour Windows Server 2016 et Windows Server 2012 R2 qui nécessite le MMA. Les instructions de migration vers la nouvelle solution unifiée se font dans les [scénarios de migration de serveur Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/server-migration).

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

2. Suivez le [processus d’intégration du serveur](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images DDI (Virtual Desktop Infrastructure) non persistantes

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

1. Après avoir démarré l’image maître pour la maintenance en ligne ou la correction, exécutez un script de mise hors service pour désactiver le capteur Defender pour point de terminaison. Pour plus d’informations, voir [Les appareils hors-carte à l’aide d’un script local](configure-endpoints-script.md#offboard-devices-using-a-local-script).

2. Assurez-vous que le capteur est arrêté en exécutant la commande ci-dessous dans une fenêtre CMD :

   ```console
   sc query sense
   ```

3. Service de l’image selon les besoins.

4. Exécutez les commandes ci-dessous à l’aide PsExec.exe ( https://download.sysinternals.com/files/PSTools.zip) qui peut être téléchargé à partir de pour nettoyer le contenu du dossier cyber que le capteur a peut-être cumulé depuis le démarrage :

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Resealez l’image de premier plan comme vous le feriez normalement.

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Résoudre les problèmes Microsoft Defender pour point de terminaison’intégration](troubleshoot-onboarding.md)
