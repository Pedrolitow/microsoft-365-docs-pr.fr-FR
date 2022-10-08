---
title: Déployer Microsoft Defender pour point de terminaison sur Linux avec Ansible
ms.reviewer: ''
description: Décrit comment déployer Microsoft Defender pour point de terminaison sur Linux à l’aide d’Ansible.
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
ms.openlocfilehash: 5c0c5e4eea9a639364f1750c960102740d071163
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68229479"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>Déployer Microsoft Defender pour point de terminaison sur Linux avec Ansible

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article explique comment déployer Defender pour point de terminaison sur Linux à l’aide d’Ansible. Un déploiement réussi nécessite l’achèvement de toutes les tâches suivantes :

- [Télécharger le package d’intégration](#download-the-onboarding-package)
- [Créer des fichiers YAML Ansible](#create-ansible-yaml-files)
- [Déploiement](#deployment)
- [Références](#references)

## <a name="prerequisites-and-system-requirements"></a>Prérequis et configuration requise

Avant de commencer, consultez [la page principale de Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.

En outre, pour le déploiement Ansible, vous devez connaître les tâches d’administration Ansible, configurer Ansible et savoir comment déployer des playbooks et des tâches. Ansible a de nombreuses façons d’effectuer la même tâche. Ces instructions supposent la disponibilité des modules Ansible pris en charge, tels que *apt* et *unarchive* pour aider à déployer le package. Votre organisation peut utiliser un flux de travail différent. Pour plus d’informations, consultez la [documentation Ansible](https://docs.ansible.com/) .

- Ansible doit être installé sur au moins un ordinateur (Ansible appelle cela le nœud de contrôle).
- SSH doit être configuré pour un compte d’administrateur entre le nœud de contrôle et tous les nœuds managés (appareils sur lesquels Defender pour point de terminaison sera installé), et il est recommandé d’être configuré avec l’authentification par clé publique.
- Les logiciels suivants doivent être installés sur tous les nœuds managés :
  - Curl
  - python-apt (si vous déployez sur des distributions à l’aide d’apt en tant que gestionnaire de package)

- Tous les nœuds managés doivent être répertoriés au format suivant dans le fichier ou le `/etc/ansible/hosts` fichier approprié :

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- Test ping :

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>Télécharger le package d’intégration

Téléchargez le package d’intégration à partir du portail Microsoft 365 Defender :

1. Dans Microsoft 365 Defender portail, accédez à **Paramètres > Points de terminaison > gestion des appareils > Intégration**.
2. Dans le premier menu déroulant, sélectionnez **Serveur Linux** comme système d’exploitation. Dans le deuxième menu déroulant, sélectionnez **votre outil de gestion de configuration Linux préféré** comme méthode de déploiement.
3. Sélectionnez **Télécharger le package d’intégration**. Enregistrez le fichier en tant que WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Option Télécharger le package d’intégration" lightbox="images/portal-onboarding-linux-2.png":::

4. À partir d’une invite de commandes, vérifiez que vous disposez du fichier. Extrayez le contenu de l’archive :

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-ansible-yaml-files"></a>Créer des fichiers YAML Ansible

Créez un sous-masque ou des fichiers de rôle qui contribuent à un playbook ou à une tâche.

- Créez la tâche d’intégration : `onboarding_setup.yml`

    ```bash
    - name: Create MDATP directories
      file:
        path: /etc/opt/microsoft/mdatp/
        recurse: true
        state: directory
        mode: 0755
        owner: root
        group: root

    - name: Register mdatp_onboard.json
      stat:
        path: /etc/opt/microsoft/mdatp/mdatp_onboard.json
      register: mdatp_onboard

    - name: Extract WindowsDefenderATPOnboardingPackage.zip into /etc/opt/microsoft/mdatp
      unarchive:
        src: WindowsDefenderATPOnboardingPackage.zip
        dest: /etc/opt/microsoft/mdatp
        mode: 0600
        owner: root
        group: root
      when: not mdatp_onboard.stat.exists
    ```

- Ajoutez le référentiel et la clé Defender pour point de terminaison : `add_apt_repo.yml`

    Defender pour point de terminaison sur Linux peut être déployé à partir de l’un des canaux suivants (indiqué ci-dessous comme *[canal])* : *insiders-fast*, *insiders-slow* ou *prod*. Chacun de ces canaux correspond à un référentiel logiciel Linux.

    Le choix du canal détermine le type et la fréquence des mises à jour proposées à votre appareil. Les appareils dans *insiders-fast* sont les premiers à recevoir des mises à jour et de nouvelles fonctionnalités, suivis ultérieurement par *des insiders lents* et enfin par *prod*.

    Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires précoces, il est recommandé de configurer certains appareils de votre entreprise pour qu’ils utilisent des *insiders rapides* ou *des insiders lents*.

    > [!WARNING]
    > Le changement de canal après l’installation initiale nécessite la réinstallation du produit. Pour changer de canal de produit : désinstallez le package existant, reconfigurez votre appareil pour utiliser le nouveau canal et suivez les étapes décrites dans ce document pour installer le package à partir du nouvel emplacement.

    Notez votre distribution et votre version et identifiez l’entrée la plus proche sous `https://packages.microsoft.com/config/[distro]/`.

    Dans les commandes suivantes, remplacez *[distribution]* et *[version]* par les informations que vous avez identifiées.

    > [!NOTE]
    > Dans le cas d’Oracle Linux et d’Amazon Linux 2, remplacez *[distro]* par « rhel ». Pour Amazon Linux 2, remplacez *[version]* par « 7 ». Pour Oracle, remplacez *[version]* par la version d’Oracle Linux.

  ```bash
  - name: Add Microsoft APT key
    apt_key:
      url: https://packages.microsoft.com/keys/microsoft.asc
      state: present
    when: ansible_os_family == "Debian"

  - name: Add Microsoft apt repository for MDATP
    apt_repository:
      repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [codename] main
      update_cache: yes
      state: present
      filename: microsoft-[channel]
    when: ansible_os_family == "Debian"

  - name: Add Microsoft DNF/YUM key
    rpm_key:
      state: present
      key: https://packages.microsoft.com/keys/microsoft.asc
    when: ansible_os_family == "RedHat"

  - name: Add  Microsoft yum repository for MDATP
    yum_repository:
      name: packages-microsoft-[channel]
      description: Microsoft Defender for Endpoint
      file: microsoft-[channel]
      baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/ 
      gpgcheck: yes
      enabled: Yes
    when: ansible_os_family == "RedHat"
  ```

- Créez les fichiers YAML d’installation et de désinstallation Ansible.

    - Pour les distributions basées sur apt, utilisez le fichier YAML suivant :

        ```bash
        cat install_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_apt_repo.yml
            - name: Install MDATP
              apt:
                name: mdatp
                state: latest
                update_cache: yes
        ```

        ```bash
        cat uninstall_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              apt:
                name: mdatp
                state: absent
        ```

    - Pour les distributions basées sur dnf, utilisez le fichier YAML suivant :

        ```bash
        cat install_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_yum_repo.yml
            - name: Install MDATP
              dnf:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-[channel]
        ```

        ```bash
        cat uninstall_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              dnf:
                name: mdatp
                state: absent
        ```

## <a name="deployment"></a>Déploiement

À présent, exécutez les fichiers de tâches sous `/etc/ansible/playbooks/` ou le répertoire approprié.

- Installation:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> Lorsque le produit démarre pour la première fois, il télécharge les dernières définitions de logiciel anti-programme malveillant. En fonction de votre connexion Internet, cela peut prendre jusqu’à quelques minutes.

- Validation/configuration :

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- Désinstallation:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>Problèmes d’installation du journal

Consultez [les problèmes d’installation](linux-resources.md#log-installation-issues) du journal pour plus d’informations sur la façon de trouver le journal généré automatiquement qui est créé par le programme d’installation en cas d’erreur.

## <a name="operating-system-upgrades"></a>Mises à niveau du système d’exploitation

Lors de la mise à niveau de votre système d’exploitation vers une nouvelle version majeure, vous devez d’abord désinstaller Defender pour point de terminaison sur Linux, installer la mise à niveau, puis reconfigurer Defender pour point de terminaison sur Linux sur votre appareil.

## <a name="references"></a>References

- [Ajouter ou supprimer des référentiels YUM](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [Gérer les packages avec le gestionnaire de packages dnf](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [Ajouter et supprimer des référentiels APT](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [Gérer apt-packages](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>Voir aussi
- [Rechercher les problèmes d’état d’intégrité de l’agent](health-status.md)
