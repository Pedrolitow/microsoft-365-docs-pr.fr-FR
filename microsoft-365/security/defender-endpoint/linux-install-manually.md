---
title: Déployer Microsoft Defender pour point de terminaison manuellement sur Linux
ms.reviewer: ''
description: Décrit comment déployer manuellement Microsoft Defender pour point de terminaison sur Linux à partir de la ligne de commande.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
ms.service: microsoft-365-security
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
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 33f3931bca1f2888948043f05f6f3f02c80a2c18
ms.sourcegitcommit: a250d043a2e42ecbc7b86147468d1660af5a6ba7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68673104"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Déployer Microsoft Defender pour point de terminaison manuellement sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article explique comment déployer manuellement Microsoft Defender pour point de terminaison sur Linux. Un déploiement réussi nécessite l’exécution de toutes les tâches suivantes :

- [Conditions préalables et configuration système requise](#prerequisites-and-system-requirements)
- [Configurer le référentiel de logiciels Linux](#configure-the-linux-software-repository)
  - [RHEL et variantes (CentOS, Fedora, Oracle Linux et Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
  - [SLES et variantes](#sles-and-variants)
  - [Systèmes Ubuntu et Debian](#ubuntu-and-debian-systems)
- [Installation d’application](#application-installation)
- [Télécharger le package d’intégration](#download-the-onboarding-package)
- [Configuration du client](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Conditions préalables et configuration système requise

Avant de commencer, consultez [Microsoft Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.

> [!WARNING]
> La mise à niveau de votre système d’exploitation vers une nouvelle version majeure après l’installation du produit nécessite la réinstallation du produit. Vous devez [désinstaller](linux-resources.md#uninstall) defender pour point de terminaison existant sur Linux, mettre à niveau le système d’exploitation, puis reconfigurer Defender pour point de terminaison sur Linux en suivant les étapes ci-dessous.

## <a name="configure-the-linux-software-repository"></a>Configurer le référentiel de logiciels Linux

Defender pour point de terminaison sur Linux peut être déployé à partir de l’un des canaux suivants (désigné ci-dessous comme *[canal]*) : *insiders-fast*, *insiders-slow* ou *prod*. Chacun de ces canaux correspond à un référentiel de logiciels Linux. Les instructions de configuration de votre appareil pour utiliser l’un de ces référentiels sont fournies ci-dessous.

Le choix du canal détermine le type et la fréquence des mises à jour proposées à votre appareil. Les appareils *dans insiders-fast* sont les premiers à recevoir des mises à jour et de nouvelles fonctionnalités, suivis ultérieurement par *les insiders - lents* et enfin par *prod*.

Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires précoces, il est recommandé de configurer certains appareils de votre entreprise pour qu’ils utilisent *des insiders rapides* ou *des insiders lents*.

> [!WARNING]
> Le basculement du canal après l’installation initiale nécessite la réinstallation du produit. Pour changer de canal de produit : désinstallez le package existant, reconfigurez votre appareil pour utiliser le nouveau canal et suivez les étapes décrites dans ce document pour installer le package à partir du nouvel emplacement.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL et variantes (CentOS, Fedora, Oracle Linux et Amazon Linux 2)

- Installez `yum-utils` s’il n’est pas encore installé :

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Votre distribution et votre version, et identifiez l’entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config/rhel/`.

    Utilisez le tableau suivant pour vous aider à localiser le package :

    |Distribution & version|Paquet|
    |---|---|
    |Pour RHEL/Centos/Oracle 8.0-8.5|<https://packages.microsoft.com/config/rhel/8/prod.repo>|
    |Pour RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 |<https://packages.microsoft.com/config/rhel/7.2/prod.repo>|
    |Pour Fedora 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Pour Fedora 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    <!--|For RHEL/Centos 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|-->

    Dans les commandes suivantes, remplacez *[version]* et *[canal]* par les informations que vous avez identifiées :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Utilisez la commande hostnamectl pour identifier les informations relatives au système, notamment la version *[version]*.

    Par exemple, si vous exécutez CentOS 7 et que vous souhaitez déployer Defender pour point de terminaison sur Linux à partir du canal *prod* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Ou si vous souhaitez explorer de nouvelles fonctionnalités sur des appareils sélectionnés, vous pouvez déployer Microsoft Defender pour point de terminaison sur Linux sur le canal *insider-fast* :

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Installez la clé publique Microsoft GPG :

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES et variantes

> [!NOTE]
> Votre distribution et votre version, et identifiez l’entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config/sles/`.

   Dans les commandes suivantes, remplacez *[distribution]* et *[version]* par les informations que vous avez identifiées :

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Utilisez la commande SPident pour identifier les informations relatives au système, notamment la version *[version]*.

   Par exemple, si vous exécutez SLES 12 et que vous souhaitez déployer Microsoft Defender pour point de terminaison sur Linux à partir du canal *prod* :

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Installez la clé publique Microsoft GPG :

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Systèmes Ubuntu et Debian

- Installez `curl` s’il n’est pas encore installé :

    ```bash
    sudo apt-get install curl
    ```

- Installez `libplist-utils` s’il n’est pas encore installé :

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Votre distribution et votre version, et identifiez l’entrée la plus proche (par majeure, puis mineure) sous `https://packages.microsoft.com/config/[distro]/`.

   Dans la commande ci-dessous, remplacez *[distribution]* et *[version]* par les informations que vous avez identifiées :

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Utilisez la commande hostnamectl pour identifier les informations relatives au système, notamment la version *[version]*.

   Par exemple, si vous exécutez Ubuntu 18.04 et que vous souhaitez déployer Microsoft Defender pour point de terminaison sur Linux à partir du canal *prod* :

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Installez la configuration du dépôt :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Par exemple, si vous avez choisi *le canal prod* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- Installez le `gpg` package s’il n’est pas déjà installé :

    ```bash
    sudo apt-get install gpg
    ```

  Si `gpg` n’est pas disponible, installez `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Installez la clé publique Microsoft GPG :

    ```bash
    curl -sSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /usr/share/keyrings/microsoft.gpg > /dev/null
    ```

- Installez le pilote HTTPS s’il n’est pas déjà installé :

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Mettez à jour les métadonnées du dépôt :

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Installation d’application

- RHEL et variantes (CentOS et Oracle Linux) :

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Si vous avez plusieurs référentiels Microsoft configurés sur votre appareil, vous pouvez être précis sur le dépôt à partir duquel installer le package. L’exemple suivant montre comment installer le package à partir du `production` canal si le canal de `insiders-fast` dépôt est également configuré sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil. Selon la distribution et la version de votre serveur, l’alias de dépôt peut être différent de celui de l’exemple suivant.

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

    > [!NOTE]
    > Si vous avez plusieurs référentiels Microsoft configurés sur votre appareil, vous pouvez être précis sur le dépôt à partir duquel installer le package. L’exemple suivant montre comment installer le package à partir du `production` canal si le canal de `insiders-fast` dépôt est également configuré sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil.

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

    > [!NOTE]
    > Si vous avez plusieurs référentiels Microsoft configurés sur votre appareil, vous pouvez être précis sur le dépôt à partir duquel installer le package. L’exemple suivant montre comment installer le package à partir du `production` canal si le canal de `insiders-fast` dépôt est également configuré sur cet appareil. Cette situation peut se produire si vous utilisez plusieurs produits Microsoft sur votre appareil.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```

    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
    ```

    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>Télécharger le package d’intégration

Téléchargez le package d’intégration à partir de Microsoft 365 Defender portail.

> [!IMPORTANT]
> Si vous manquez cette étape, toute commande exécutée affiche un message d’avertissement indiquant que le produit n’a pas de licence. `mdatp health` La commande retourne également une valeur de `false`.

1. Dans le portail Microsoft 365 Defender, accédez à **Paramètres > Points de terminaison > Gestion des appareils > Intégration**.
2. Dans le premier menu déroulant, sélectionnez **Serveur Linux** comme système d’exploitation. Dans le deuxième menu déroulant, sélectionnez **Script local** comme méthode de déploiement.
3. Sélectionnez **Télécharger le package d’intégration**. Enregistrez le fichier en tant que WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="Téléchargement d’un package d’intégration dans le portail Microsoft 365 Defender" lightbox="images/portal-onboarding-linux.png":::

4. À partir d’une invite de commandes, vérifiez que vous disposez du fichier et extrayez le contenu de l’archive :

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

1. Copiez MicrosoftDefenderATPOnboardingLinuxServer.py sur l’appareil cible.

    > [!NOTE]
    > Initialement, l’appareil client n’est pas associé à une organisation et l’attribut *orgId* est vide.

    ```bash
    mdatp health --field org_id
    ```

2. Exécutez MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > Pour exécuter cette commande, vous devez disposer de ou `python3` être `python` installé sur l’appareil en fonction du disto et de la version. Si nécessaire, consultez [Instructions pas à pas pour l’installation de Python sur Linux](https://opensource.com/article/20/4/install-python-linux).

    Si vous exécutez RHEL 8.x ou Ubuntu 20.04 ou version ultérieure, vous devez utiliser `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    Pour le reste des distributions et versions, vous devez utiliser `python`.

    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

3. Vérifiez que l’appareil est maintenant associé à votre organisation et qu’il signale un identificateur d’organisation valide :

    ```bash
    mdatp health --field org_id
    ```

4. Vérifiez l’état d’intégrité du produit en exécutant la commande suivante. Une valeur de retour de `1` indique que le produit fonctionne comme prévu :

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Lorsque le produit démarre pour la première fois, il télécharge les dernières définitions de logiciel anti-programme malveillant. Cela peut prendre jusqu’à quelques minutes en fonction de la connectivité réseau. Pendant ce temps, la commande ci-dessus retourne une valeur de `false`. Vous pouvez vérifier l’état de la mise à jour de définition à l’aide de la commande suivante :
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > Notez que vous devrez peut-être également configurer un proxy après l’installation initiale. Consultez [Configurer Defender pour point de terminaison sur Linux pour la découverte de proxy statique : configuration post-installation](linux-static-proxy-configuration.md#post-installation-configuration).

5. Exécutez un test de détection av pour vérifier que l’appareil est correctement intégré et qu’il signale au service. Effectuez les étapes suivantes sur l’appareil nouvellement intégré :

    - Assurez-vous que la protection en temps réel est activée (indiqué par le résultat de l’exécution de `1` la commande suivante) :

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

      S’il n’est pas activé, exécutez la commande suivante :

       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Ouvrez une fenêtre Terminal et exécutez la commande suivante :

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Le fichier doit avoir été mis en quarantaine par Defender pour point de terminaison sur Linux. Utilisez la commande suivante pour répertorier toutes les menaces détectées :

        ```bash
        mdatp threat list
        ```

6. Exécutez un test de détection EDR et simulez une détection pour vérifier que l’appareil est correctement intégré et qu’il signale au service. Effectuez les étapes suivantes sur l’appareil nouvellement intégré :

    - Vérifiez que le serveur Linux intégré apparaît dans Microsoft 365 Defender. S’il s’agit de la première intégration de la machine, l’affichage peut prendre jusqu’à 20 minutes.

    - Téléchargez et extrayez le [fichier de script](https://aka.ms/LinuxDIY) sur un serveur Linux intégré, puis exécutez la commande suivante : `./mde_linux_edr_diy.sh`

    - Après quelques minutes, une détection doit être déclenchée dans Microsoft 365 Defender.

    - Examinez les détails de l’alerte, la chronologie de l’ordinateur et effectuez vos étapes d’investigation classiques.

## <a name="installer-script"></a>Script du programme d’installation

Vous pouvez également utiliser un [script bash du programme d’installation](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) automatisé fourni dans notre [dépôt GitHub public](https://github.com/microsoft/mdatp-xplat/).
Le script identifie la distribution et la version, simplifie la sélection du référentiel approprié, configure l’appareil pour extraire le package le plus récent et combine les étapes d’installation et d’intégration du produit.

```bash
> ./mde_installer.sh --help
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

En savoir plus [ici](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Problèmes d’installation des journaux

Consultez [Problèmes d’installation des journaux](linux-resources.md#log-installation-issues) pour plus d’informations sur la recherche du journal généré automatiquement par le programme d’installation lorsqu’une erreur se produit.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Comment migrer du canal Insiders-Fast vers le canal de production

1. Désinstallez la version « Canal Insiders-Fast » de Defender pour point de terminaison sur Linux.

    ```bash
    sudo yum remove mdatp
    ```

1. Désactiver le référentiel Defender pour point de terminaison sur Linux Insiders-Fast

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > La sortie doit afficher « packages-microsoft-com-fast-prod ».

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. Redéployez Microsoft Defender pour point de terminaison sur Linux à l’aide du « canal de production ».

## <a name="uninstallation"></a>Désinstallation

Pour plus d’informations sur la suppression de Defender pour point de terminaison sur Linux des appareils clients, consultez [Désinstaller](linux-resources.md#uninstall) .

## <a name="see-also"></a>Voir aussi

- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
