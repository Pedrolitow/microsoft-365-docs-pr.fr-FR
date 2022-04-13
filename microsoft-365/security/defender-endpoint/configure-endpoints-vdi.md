---
title: Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.
description: Déployez le package de configuration sur l’appareil VDI (Virtual Desktop Infrastructure) afin qu’il soit intégré à Microsoft Defender pour point de terminaison service.
keywords: configurer un appareil d’infrastructure de bureau virtuel (VDI), vdi, gestion des appareils, configurer Microsoft Defender pour point de terminaison, points de terminaison
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
ms.openlocfilehash: fe86b09588f08a05183de146092b50b5cb530d0e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825011"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>Intégrer des appareils d’infrastructure de bureau virtuel (VDI) non persistants dans Microsoft 365 Defender

L’infrastructure de bureau virtuel (VDI) est un concept d’infrastructure informatique qui permet aux utilisateurs finaux d’accéder aux instances de bureaux virtuels d’entreprise à partir de presque n’importe quel appareil (par exemple, votre ordinateur personnel, smartphone ou tablette), ce qui élimine la nécessité pour l’organisation de fournir aux utilisateurs des ordinateurs physiques. L’utilisation d’appareils VDI réduit les coûts, car les services informatiques ne sont plus responsables de la gestion, de la réparation et du remplacement des points de terminaison physiques. Les utilisateurs autorisés peuvent accéder aux mêmes serveurs d’entreprise, fichiers, applications et services à partir de n’importe quel appareil approuvé via un client de bureau sécurisé ou un navigateur.

Comme tout autre système dans un environnement informatique, ceux-ci doivent également avoir une solution endpoint Detection and Response (PEPT) et antivirus pour se protéger contre les menaces et les attaques avancées.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Appareils vDI (Virtual Desktop Infrastructure)
- Windows 10, Windows 11, Windows Server 2019, Windows Server 2022, Windows Server 2008R2/2012R2/2016

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **VDI persistants** -  [L’intégration d’un ordinateur VDI persistant](configure-endpoints.md) dans Microsoft Defender pour point de terminaison est gérée de la même façon que vous intégreriez une machine physique, telle qu’un ordinateur de bureau ou un ordinateur portable. La stratégie de groupe, Microsoft Endpoint Manager et d’autres méthodes peuvent être utilisées pour intégrer une machine persistante. Dans le portail Microsoft 365 Defender (https://security.microsoft.com) sous intégration, sélectionnez votre méthode d’intégration préférée et suivez les instructions pour ce type. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Intégration d’appareils d’infrastructure de bureau virtuel (VDI) non persistants

Defender pour point de terminaison prend en charge l’intégration de session VDI non persistante.

Il peut y avoir des problèmes associés lors de l’intégration d’instances VDI. Voici les défis classiques de ce scénario :

- Intégration anticipée instantanée d’une session de courte durée, qui doit être intégrée à Defender pour point de terminaison avant l’approvisionnement réel.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Dans un environnement VDI, les instances VDI peuvent avoir une durée de vie courte. Les appareils VDI peuvent apparaître dans le portail Defender pour point de terminaison comme suit :


- Entrée de portail unique pour chaque instance VDI. Si l’instance VDI a déjà été intégrée à Microsoft Defender pour point de terminaison et qu’elle a été supprimée à un moment donné, puis recréée avec le même nom d’hôte, un nouvel objet représentant cette instance VDI ne sera PAS créé dans le portail. 


  > [!NOTE]
  > Dans ce cas, le *même* nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans assistance.

- Plusieurs entrées pour chaque appareil , une pour chaque instance VDI.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en surbrillance les étapes pour les entrées uniques et multiples.

> [!WARNING]
> Pour les environnements où les configurations de ressources sont faibles, la procédure de démarrage VDI peut ralentir l’intégration du capteur Defender pour point de terminaison.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>Pour Windows 10, ou Windows 11, ou Windows Server 2012 R2 et versions ultérieures

> [!NOTE]
> Windows Server 2016 et Windows Server 2012 R2 doivent être préparés en appliquant d’abord le package d’installation à l’aide des instructions fournies dans [les serveurs d’intégration Windows](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne.

1.  Ouvrez le fichier de configuration VDI .zip (*WindowsDefenderATPOnboardingPackage.zip*) que vous avez téléchargé à partir de l’Assistant Intégration de service. Vous pouvez également obtenir le package à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> :

    1. Dans le volet de navigation, sélectionnez **Paramètres** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. Sélectionnez le système d’exploitation.

    1.  Dans le champ **Méthode de déploiement** , sélectionnez les **scripts d’intégration VDI pour les points de terminaison non persistants**.

    1. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

2. Copiez les fichiers du dossier WindowsDefenderATPOnboardingPackage extrait du fichier .zip dans l’image d’or/maître sous le chemin d’accès `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. Si vous implémentez plusieurs entrées pour chaque appareil , une pour chaque session, copiez WindowsDefenderATPOnboardingScript.cmd.
    2. Si vous implémentez une entrée unique pour chaque appareil, copiez Onboard-NonPersistentMachine.ps1 et WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > Si vous ne voyez pas le `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` dossier, il peut être masqué. Vous devez choisir l’option **Afficher les fichiers et dossiers masqués** dans Explorateur de fichiers.

3. Ouvrez une fenêtre d’éditeur de stratégie de groupe local et accédez à **Configuration** \> de l’ordinateur **Windows Paramètres** \> **Démarrage des scripts**\>.

   > [!NOTE]
   > Les stratégie de groupe de domaine peuvent également être utilisées pour intégrer des appareils VDI non persistants.

4. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
    - Pour une entrée unique pour chaque appareil :

         Sélectionnez l’onglet **Scripts PowerShell**, puis cliquez sur **Ajouter** (Windows’Explorateur s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script `Onboard-NonPersistentMachine.ps1`PowerShell d’intégration. Il n’est pas nécessaire de spécifier l’autre fichier, car il sera déclenché automatiquement.

    - Pour plusieurs entrées pour chaque appareil :

         Sélectionnez l’onglet **Scripts**, puis cliquez sur **Ajouter** (Windows’Explorateur s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script `WindowsDefenderATPOnboardingScript.cmd`Bash d’intégration.

5. Testez votre solution :
   1. Créez un pool avec un seul appareil.
   2. Connectez-vous à l’appareil.
   3. Déconnectez-vous de l’appareil.
   4. Connectez-vous à l’appareil avec un autre utilisateur.
   5. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :
      - Pour une entrée unique pour chaque appareil : vérifiez une seule entrée dans Microsoft 365 Defender portail.
      - Pour plusieurs entrées pour chaque appareil : vérifiez plusieurs entrées dans Microsoft 365 Defender portail.

6. Cliquez sur **La liste Appareils** dans le volet de navigation.

7. Utilisez la fonction de recherche en entrant le nom de l’appareil et en sélectionnant **Appareil** comme type de recherche.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>Pour les références SKU de niveau inférieur (Windows Server 2008 R2)

> [!NOTE]
> Ces instructions pour les autres versions de serveur Windows s’appliquent également si vous exécutez les Microsoft Defender pour point de terminaison précédentes pour Windows Server 2016 et Windows Server 2012 R2 qui nécessite le MMA. Les instructions pour migrer vers la nouvelle solution unifiée se trouvent [dans les scénarios de migration de serveur dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Le registre suivant n’est pertinent que lorsque l’objectif est d’obtenir une « entrée unique pour chaque appareil ».

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

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images d’infrastructure de bureau virtuel (VDI) non persistantes

Avec la possibilité de déployer facilement des mises à jour sur des machines virtuelles s’exécutant dans des VM, nous avons raccourci ce guide pour vous concentrer sur la façon dont vous pouvez obtenir des mises à jour sur vos machines rapidement et facilement. Vous n’avez plus besoin de créer et de sceller régulièrement des images d’or, car les mises à jour sont développées dans leurs bits de composant sur le serveur hôte, puis téléchargées directement sur la machine virtuelle lorsqu’elle est activée.

Pour plus d’informations, suivez les instructions du [guide de déploiement pour Antivirus Microsoft Defender dans un environnement d’infrastructure de bureau virtuel (VDI](/security/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)).


## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer les appareils Windows à l’aide des outils de gestion des appareils mobiles](configure-endpoints-mdm.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Résoudre les problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
