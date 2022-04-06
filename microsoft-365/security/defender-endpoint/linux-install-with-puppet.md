---
title: Déployer Microsoft Defender pour le point de terminaison sur Linux avec l’ment
ms.reviewer: ''
description: Décrit comment déployer Microsoft Defender pour le point de terminaison sur Linux à l’aide de L’Atelier.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, loi, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: adf58b3009c3feaafde389b91ddc64b441d49f40
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476006"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Déployer Microsoft Defender pour le point de terminaison sur Linux avec l’ment

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article explique comment déployer Defender pour point de terminaison sur Linux à l’aide de Latra. Un déploiement réussi nécessite l’exécution de toutes les tâches suivantes :

- [Télécharger le package d’intégration](#download-the-onboarding-package)
- [Créer un manifeste d’atelier](#create-a-puppet-manifest)
- [Déploiement](#deployment)
- [Vérifier l’état de l’intégration](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Conditions préalables et système requis

 Pour obtenir une description des conditions préalables et de la condition système requise pour la version logicielle actuelle, voir la page principale de [Defender for Endpoint sur Linux](microsoft-defender-endpoint-linux.md).

En outre, pour le déploiement de Manière générale, vous devez être familiarisé avec les tâches d’administration de l’équipe de sécurité, configurer la configuration de l’appareil et savoir comment déployer des packages. Il existe de nombreuses façons d’effectuer la même tâche. Ces instructions supposent la disponibilité des modules De jeu pris en charge, par exemple *pour* vous aider à déployer le package. Votre organisation peut utiliser un flux de travail différent. Pour plus d’informations [, reportez-vous](https://puppet.com/docs) à la documentation de Documentation.

## <a name="download-the-onboarding-package"></a>Télécharger le package d’intégration

Téléchargez le package d’intégration à partir Microsoft 365 Defender portail :

1. Dans Microsoft 365 Defender portail, go to **Paramètres > Endpoints > Device management > Onboarding**.
2. Dans le premier menu déroulant, sélectionnez **Linux Server comme** système d’exploitation. Dans le deuxième menu déroulant, sélectionnez Votre outil de gestion de **configuration Linux préféré** comme méthode de déploiement.
3. **Sélectionnez Télécharger le package d’intégration**. Enregistrez le fichier sous WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Option de téléchargement du package intégré" lightbox="images/portal-onboarding-linux-2.png":::

4. À partir d’une invite de commandes, vérifiez que vous avez le fichier. 

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
5. Extrayons le contenu de l’archive.
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Créer un manifeste de jeu

Vous devez créer un manifeste Pour déployer Defender pour Point de terminaison sur Linux sur des appareils gérés par un serveur De jeu. Cet exemple utilise les modules *apt* et *yumrepo* disponibles à partir delabs, et part du principe que les modules ont été installés sur votre serveur Dupont.

Créez les dossiers *install_mdatp/fichiers* et install_mdatp */manifestes* sous le dossier modules de votre installation de Latre. Ce dossier se trouve généralement dans */etc/spamlabs/code/environnements/production/modules* sur votre serveur Der. Copiez le mdatp_onboard.json créé ci-dessus dans le *dossier install_mdatp/fichiers* . Créer *un init.pp* qui contient les instructions de déploiement :

```bash
pwd
```
```Output
/etc/puppetlabs/code/environments/production/modules
```

```bash
tree install_mdatp
```
```Output
install_mdatp
├── files
│   └── mdatp_onboard.json
└── manifests
    └── init.pp
```

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>Contenu de `install_mdatp/manifests/init.pp`

Defender pour le point de terminaison sur Linux peut être déployé à partir de l’un des canaux suivants (indiqués ci-dessous sous *le nom [canal]*) : *insiders-fast*, *insiders-slow* ou *prod*. Chacun de ces canaux correspond à un référentiel de logiciels Linux.

Le choix du canal détermine le type et la fréquence des mises à jour proposées à votre appareil. Les appareils *internes rapides* sont les premiers à recevoir des mises à jour et de nouvelles fonctionnalités, suivis ultérieurement par les *insiders-slow* et enfin par *prod*.

Pour prévisualiser les nouvelles fonctionnalités et fournir des commentaires préliminaires, il est recommandé de configurer certains appareils de votre entreprise pour utiliser les *insiders-fast* ou *insider-slow*.

> [!WARNING]
> Le basculement du canal après l’installation initiale nécessite la réinstallation du produit. Pour basculer le canal de produit : désinstallez le package existant, configurez de nouveau votre appareil pour utiliser le nouveau canal et suivez les étapes de ce document pour installer le package à partir du nouvel emplacement.

Notez votre distribution et version et identifiez l’entrée la plus proche sous `https://packages.microsoft.com/config/[distro]/`.

Dans les commandes ci-dessous, *remplacez [distro]* et *[version]* par les informations que vous avez identifiées :

> [!NOTE]
> Dans le cas de RedHat, Oracle Linux, Amazon Linux 2 et CentOS 8, *remplacez [distro]* par « rhel ».

```puppet
# Puppet manifest to install Microsoft Defender for Endpoint on Linux.
# @param channel The release channel based on your environment, insider-fast or prod.
# @param distro The Linux distribution in lowercase. In case of RedHat, Oracle Linux, Amazon Linux 2, and CentOS 8, the distro variable should be 'rhel'.
# @param version The Linux distribution release number, e.g. 7.4.

class install_mdatp (
$channel = 'insiders-fast',
$distro = undef,
$version = undef
){
    case $::osfamily {
        'Debian' : {
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/config/${distro}/${version}/prod",
                release  => $channel,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/config/${distro}/${version}/${channel}",
                descr    => "packages-microsoft-com-prod-${channel}",
                enabled  => 1,
                gpgcheck => 1,
                gpgkey   => 'https://packages.microsoft.com/keys/microsoft.asc'
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }

    case $::osfamily {
        /(Debian|RedHat)/: {
            file { ['/etc/opt', '/etc/opt/microsoft', '/etc/opt/microsoft/mdatp']:
                ensure => directory,
                owner  => root,
                group  => root,
                mode   => '0755'
            }

            file { '/etc/opt/microsoft/mdatp/mdatp_onboard.json':
                source  => 'puppet:///modules/install_mdatp/mdatp_onboard.json',
                owner   => root,
                group   => root,
                mode    => '0600',
                require => File['/etc/opt/microsoft/mdatp']
            }

            package { 'mdatp':
                ensure  => 'installed',
                require => File['/etc/opt/microsoft/mdatp/mdatp_onboard.json']
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }
}
```

## <a name="deployment"></a>Déploiement

Inclure le manifeste ci-dessus dans votre site.pp fichier :

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```
```Output
node "default" {
    include install_mdatp
}
```

Les appareils d’agent inscrits sondent périodiquement le serveur de contrôle d’accès et installent de nouveaux profils et stratégies de configuration dès qu’ils sont détectés.

## <a name="monitor-puppet-deployment"></a>Surveiller le déploiement de l’écran de surveillance

Sur l’appareil de l’agent, vous pouvez également vérifier l’état d’intégration en exécutant :

```bash
mdatp health
```
```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **sous licence** : cela confirme que l’appareil est lié à votre organisation.

- **orgId :** il s’agit de votre identificateur d’organisation Defender pour le point de terminaison.

## <a name="check-onboarding-status"></a>Vérifier l’état de l’intégration

Vous pouvez vérifier que les appareils ont été correctement intégrés en créant un script. Par exemple, le script suivant vérifie l’état d’intégration des appareils inscrits :

```bash
mdatp health --field healthy
```

La commande ci-dessus imprime `1` si le produit est intégré et fonctionne comme prévu.

> [!IMPORTANT]
> Lorsque le produit démarre pour la première fois, il télécharge les dernières définitions de logiciel anti-programme malveillant. Selon votre connexion Internet, cela peut prendre jusqu’à quelques minutes. Pendant ce temps, la commande ci-dessus renvoie une valeur de `0`.

Si le produit n’est pas sain, le code de sortie ( `echo $?`qui peut être vérifié) indique le problème :

- 1 si l’appareil n’est pas encore intégré.
- 3 si la connexion au daemon ne peut pas être établie.

## <a name="log-installation-issues"></a>Journaux des problèmes d’installation

 Pour plus d’informations sur la recherche du journal généré automatiquement par le programme d’installation en cas d’erreur, voir [Problèmes d’installation du journal](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>Mises à niveau du système d’exploitation

Lors de la mise à niveau de votre système d’exploitation vers une nouvelle version majeure, vous devez d’abord désinstaller Defender pour Endpoint sur Linux, installer la mise à niveau, puis reconfigurer Defender pour Endpoint sur Linux sur votre appareil.

## <a name="uninstallation"></a>Désinstallation

Créer un module *remove_mdatp* similaire à *install_mdatp* avec le contenu suivant *dans init.pp* fichier :

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
