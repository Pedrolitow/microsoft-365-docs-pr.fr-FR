---
title: Déployer Microsoft Defender pour le point de terminaison sur Linux manuellement
ms.reviewer: ''
description: Décrit comment déployer Microsoft Defender pour Endpoint sur Linux manuellement à partir de la ligne de commande.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, préinstallation, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 0374c1a44a4d942ea631d97f51fa48df15d3ec13
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51929084"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Déployer Microsoft Defender pour le point de terminaison sur Linux manuellement

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l'expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article explique comment déployer Microsoft Defender pour Endpoint sur Linux manuellement. Un déploiement réussi nécessite l'exécution de toutes les tâches suivantes :

- [Déployer Microsoft Defender pour le point de terminaison sur Linux manuellement](#deploy-microsoft-defender-for-endpoint-on-linux-manually)
  - [Conditions préalables et système requis](#prerequisites-and-system-requirements)
  - [Configurer le référentiel de logiciels Linux](#configure-the-linux-software-repository)
    - [RHEL et variantes (CentOS et Oracle Linux)](#rhel-and-variants-centos-and-oracle-linux)
    - [SLES et variantes](#sles-and-variants)
    - [Systèmes Ubuntu et Debian](#ubuntu-and-debian-systems)
  - [Installation de l'application](#application-installation)
  - [Télécharger le package d'intégration](#download-the-onboarding-package)
  - [Configuration du client](#client-configuration)
  - [Script du programme d'installation](#installer-script)
  - [Journal des problèmes d'installation](#log-installation-issues)
  - [Mises à niveau du système d'exploitation](#operating-system-upgrades)
  - [Désinstallation](#uninstallation)

## <a name="prerequisites-and-system-requirements"></a>Conditions préalables et système requis

Avant de commencer, consultez [Microsoft Defender pour Endpoint sur Linux](microsoft-defender-endpoint-linux.md) pour obtenir une description des conditions préalables et de la requise pour la version logicielle actuelle.

## <a name="configure-the-linux-software-repository"></a>Configurer le référentiel de logiciels Linux

Defender for Endpoint sur Linux peut être déployé à partir de l'un des canaux suivants (indiqués ci-dessous sous le nom *[canal]*) : *insiders-fast,* *insiders-slow* ou *prod*. Chacun de ces canaux correspond à un référentiel de logiciels Linux. Les instructions de configuration de votre appareil pour utiliser l'un de ces référentiels sont fournies ci-dessous.

Le choix du canal détermine le type et la fréquence des mises à jour proposées à votre appareil. Les appareils *internes rapides* sont les premiers à recevoir des mises à jour et de nouvelles fonctionnalités, suivis ultérieurement par les *insiders-slow* et enfin par *prod*.

Afin d'afficher un aperçu des nouvelles fonctionnalités et de fournir des commentaires préliminaires, il est recommandé de configurer certains appareils dans votre entreprise pour utiliser les *insiders-fast* ou *insider-slow*.

> [!WARNING]
> Le basculement du canal après l'installation initiale nécessite la réinstallation du produit. Pour basculer le canal de produit : désinstallez le package existant, configurez de nouveau votre appareil pour utiliser le nouveau canal et suivez les étapes de ce document pour installer le package à partir du nouvel emplacement.

### <a name="rhel-and-variants-centos-and-oracle-linux"></a>RHEL et variantes (CentOS et Oracle Linux)

- Installez `yum-utils` s'il n'est pas encore installé :

    ```bash
    sudo yum install yum-utils
    ```

- Notez votre distribution et version, et identifiez l'entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config/` . Par exemple, RHEL 7.9 est plus proche de 7,4 que de 8.

    Dans les commandes ci-dessous, *remplacez [distro]* et *[version]* par les informations que vous avez identifiées :

    > [!NOTE]
    > Dans le cas d'Oracle Linux, *remplacez [distro]* par « rhel ».

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
    ```

    Par exemple, si vous exécutez CentOS 7 et que vous souhaitez déployer Defender pour Endpoint sur Linux à partir du *canal prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/prod.repo
    ```

    Ou si vous souhaitez explorer de nouvelles fonctionnalités sur des appareils sélectionnés, vous pouvez déployer MDE pour Linux sur un canal rapide pour les *insiders* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/centos/7/insiders-fast.repo
    ```

- Installez la clé publique Microsoft GPG :

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

- Téléchargez et rendez utilisables toutes les métadonnées pour les référentiels yum actuellement activés :

    ```bash
    yum makecache
    ```

### <a name="sles-and-variants"></a>SLES et variantes

- Notez votre distribution et version, et identifiez l'entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config/` .

    Dans les commandes suivantes, *remplacez [distro]* et *[version]* par les informations que vous avez identifiées :

    ```bash
    sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
    ```

    Par exemple, si vous exécutez SLES 12 et que vous souhaitez déployer MDE pour Linux à partir du *canal prod* :

    ```bash
    sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
    ```

- Installez la clé publique Microsoft GPG :

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Systèmes Ubuntu et Debian

- Installez `curl` s'il n'est pas encore installé :

    ```bash
    sudo apt-get install curl
    ```

- Installez `libplist-utils` s'il n'est pas encore installé :

    ```bash
    sudo apt-get install libplist-utils
    ```

- Notez votre distribution et version, et identifiez l'entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config` .

    Dans la commande ci-dessous, *remplacez [distro]* et *[version]* par les informations que vous avez identifiées :

    ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
    ```

    Par exemple, si vous exécutez Ubuntu 18.04 et que vous souhaitez déployer MDE pour Linux à partir du *canal prod* :

    ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
    ```

- Installez la configuration du référentiel :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```
    Par exemple, si vous avez choisi *le canal prod* :
    
    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```   

- Installez le `gpg` package s'il n'est pas déjà installé :

    ```bash
    sudo apt-get install gpg
    ```

  Si `gpg` ce n'est pas le cas, `gnupg` installez.

- Installez la clé publique Microsoft GPG :

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- Installez le pilote https s'il n'est pas déjà présent :

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Mettez à jour les métadonnées du référentiel :

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Installation de l'application

- RHEL et variantes (CentOS et Oracle Linux) :

    ```bash
    sudo yum install mdatp
    ```

    Si plusieurs référentiels Microsoft sont configurés sur votre appareil, vous pouvez être spécifique au référentiel à partir duquel installer le package. L'exemple suivant montre comment installer le package à partir du canal si vous avez également configuré le canal de référentiel `production` `insiders-fast` sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil. Selon la distribution et la version de votre serveur, l'alias du référentiel peut être différent de celui de l'exemple suivant.

    ```bash
    # list all repositories
    yum repolist
    ```
    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```
    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- SLES et variantes :

    ```bash
    sudo zypper install mdatp
    ```

    Si plusieurs référentiels Microsoft sont configurés sur votre appareil, vous pouvez être spécifique au référentiel à partir duquel installer le package. L'exemple suivant montre comment installer le package à partir du canal si vous avez également configuré le canal de référentiel `production` `insiders-fast` sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil.

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...
    ```
    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- Système Ubuntu et Debian :

    ```bash
    sudo apt-get install mdatp
    ```

    Si plusieurs référentiels Microsoft sont configurés sur votre appareil, vous pouvez être spécifique au référentiel à partir duquel installer le package. L'exemple suivant montre comment installer le package à partir du canal si vous avez également configuré le canal de référentiel `production` `insiders-fast` sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```
    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/ubuntu/18.04/prod bionic main
    ```
    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>Télécharger le package d'intégration

Téléchargez le package d'intégration à partir du Centre de sécurité Microsoft Defender :

1. Dans le Centre de sécurité Microsoft Defender, go to **Settings > Device Management > Onboarding**.
2. Dans le premier menu déroulant, sélectionnez **Linux Server comme** système d'exploitation. Dans le deuxième menu déroulant, sélectionnez **Script local (pour 10** appareils au plus) comme méthode de déploiement.
3. Sélectionnez **Télécharger le package d'intégration.** Enregistrez le fichier sous WindowsDefenderATPOnboardingPackage.zip.

    ![Capture d'écran du Centre de sécurité Microsoft Defender](images/atp-portal-onboarding-linux.png)

4. À partir d'une invite de commandes, vérifiez que vous avez le fichier.
    Extrayons le contenu de l'archive :

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```


## <a name="client-configuration"></a>Configuration du client

1. Copiez MicrosoftDefenderATPOnboardingLinuxServer.py vers l'appareil cible.

    Initialement, l'appareil client n'est pas associé à une organisation. Notez que *l'attribut orgId* est vide :

    ```bash
    mdatp health --field org_id
    ```

2. Exécutez MicrosoftDefenderATPOnboardingLinuxServer.py et notez que, pour exécuter cette commande, vous devez avoir `python` installé sur l'appareil :

    ```bash
    python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

3. Vérifiez que l'appareil est désormais associé à votre organisation et signale un identificateur d'organisation valide :

    ```bash
    mdatp health --field org_id
    ```

4. Quelques minutes après avoir terminé l'installation, vous pouvez voir l'état en exécutant la commande suivante. Une valeur de retour `1` de indique que le produit fonctionne comme prévu :

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Lorsque le produit démarre pour la première fois, il télécharge les dernières définitions de logiciel anti-programme malveillant. Selon votre connexion Internet, cela peut prendre jusqu'à quelques minutes. Pendant ce temps, la commande ci-dessus renvoie une valeur de `false` . Vous pouvez vérifier l'état de la mise à jour des définitions à l'aide de la commande suivante :
    > ```bash
    > mdatp health --field definitions_status
    > ```
    > Notez que vous devrez peut-être également configurer un proxy après avoir terminé l'installation initiale. Voir Configurer Defender pour endpoint sur Linux pour [la découverte de proxy statique : configuration post-installation.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-static-proxy-configuration#post-installation-configuration)

5. Exécutez un test de détection pour vérifier que l'appareil est correctement intégré et signaler au service. Effectuez les étapes suivantes sur l'appareil nouvellement intégré :

    - Assurez-vous que la protection en temps réel est activée (en raison de l'exécution de `1` la commande suivante) :

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    - Ouvrez une fenêtre Terminal. Copiez et exécutez la commande suivante :

        ``` bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Le fichier doit avoir été mis en quarantaine par Defender for Endpoint sur Linux. Utilisez la commande suivante pour lister toutes les menaces détectées :

        ```bash
        mdatp threat list
        ```

## <a name="installer-script"></a>Script du programme d'installation

Vous pouvez également utiliser un script bash de [programme](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) d'installation automatisé fourni dans notre référentiel [GitHub public.](https://github.com/microsoft/mdatp-xplat/)
Le script identifie la distribution et la version, et définit l'appareil pour qu'il tire le dernier package et l'installe.
Vous pouvez également intégrer un script fourni.

```bash
❯ ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

En savoir plus [ici.](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation)

## <a name="log-installation-issues"></a>Journal des problèmes d'installation

Pour [plus d'informations](linux-resources.md#log-installation-issues) sur la recherche du journal généré automatiquement par le programme d'installation en cas d'erreur, voir problèmes d'installation des journaux.

## <a name="operating-system-upgrades"></a>Mises à niveau du système d'exploitation

Lors de la mise à niveau de votre système d'exploitation vers une nouvelle version majeure, vous devez d'abord désinstaller Defender pour Endpoint sur Linux, installer la mise à niveau, puis reconfigurer Defender pour Endpoint sur Linux sur votre appareil.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Comment migrer de Insiders-Fast canal de production

1. Désinstallez la version « Insiders-Fast channel » de MDE pour Linux.

    ``
    sudo yum remove mdatp
    ``

1. Désactiver le MDE pour le Insiders-Fast Linux  ``
    sudo yum repolist
    ``

    > [!NOTE]
    > La sortie doit afficher « packages-microsoft-com-fast-prod ».

    ``
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ``
1. Redéployer MDE pour Linux à l'aide du « canal de production ».


## <a name="uninstallation"></a>Désinstallation

Voir [Désinstaller](linux-resources.md#uninstall) pour plus d'informations sur la suppression de Defender for Endpoint sur Linux des appareils clients.
