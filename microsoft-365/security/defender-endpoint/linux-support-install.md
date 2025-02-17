---
title: Résoudre les problèmes d’installation pour Microsoft Defender pour point de terminaison sur Linux
ms.reviewer: ''
description: Résoudre les problèmes d’installation pour Microsoft Defender pour point de terminaison sur Linux
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation
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
ms.openlocfilehash: cc8198ad6ecd1a40d18d4f2b185d13481b8c0651
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68228161"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes d’installation pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-that-the-installation-succeeded"></a>Vérifier que l’installation a réussi

Une erreur lors de l’installation peut ou non entraîner un message d’erreur significatif par le gestionnaire de package. Pour vérifier si l’installation a réussi, obtenez et vérifiez les journaux d’installation à l’aide de :

```bash
 sudo journalctl --no-pager|grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

Une sortie de la commande précédente avec la date et l’heure d’installation correctes indique la réussite.

Vérifiez également la [configuration du client](linux-install-manually.md#client-configuration) pour vérifier l’intégrité du produit et détecter le fichier texte EICAR.

## <a name="make-sure-you-have-the-correct-package"></a>Vérifiez que vous disposez du package approprié

Vérifiez que le package que vous installez correspond à la distribution et à la version de l’hôte.

<br>

****

|package|Distribution|
|---|---|
|mdatp-rhel8. Linux.x86_64.rpm|Oracle, RHEL et CentOS 8.x|
|mdatp-sles12. Linux.x86_64.rpm|SUSE Linux Enterprise Server 12.x|
|mdatp-sles15. Linux.x86_64.rpm|SUSE Linux Enterprise Server 15.x|
|mdatp. Linux.x86_64.rpm|Oracle, RHEL et CentOS 7.x|
|mdatp. Linux.x86_64.deb|Debian et Ubuntu 16.04, 18.04 et 20.04|
|

Pour un [déploiement manuel](linux-install-manually.md), assurez-vous que la distribution et la version correctes ont été choisies.

## <a name="installation-failed"></a>Échec de l’installation

Vérifiez si le service Defender pour point de terminaison est en cours d’exécution :

```bash
service mdatp status
```

```Output
 ● mdatp.service - Microsoft Defender for Endpoint
   Loaded: loaded (/lib/systemd/system/mdatp.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-26 10:37:30 IST; 23h ago
 Main PID: 1966 (wdavdaemon)
    Tasks: 105 (limit: 4915)
   CGroup: /system.slice/mdatp.service
           ├─1966 /opt/microsoft/mdatp/sbin/wdavdaemon
           ├─1967 /opt/microsoft/mdatp/sbin/wdavdaemon
           └─1968 /opt/microsoft/mdatp/sbin/wdavdaemon
 ```

## <a name="steps-to-troubleshoot-if-the-mdatp-service-isnt-running"></a>Étapes de résolution des problèmes si le service mdatp n’est pas en cours d’exécution

1. Vérifiez si l’utilisateur « mdatp » existe :

    ```bash
    id "mdatp"
    ```

    S’il n’y a pas de sortie, exécutez

    ```bash
    sudo useradd --system --no-create-home --user-group --shell /usr/sbin/nologin mdatp
    ```

2. Essayez d’activer et de redémarrer le service à l’aide de :

    ```bash
    sudo service mdatp start
    ```

    ```bash
    sudo service mdatp restart
    ```

3. Si mdatp.service est introuvable lors de l’exécution de la commande précédente, exécutez :

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path> 
    ```

    où `<systemd_path>` se trouve `/lib/systemd/system` pour les distributions Ubuntu et Debian et /usr/lib/systemd/system' pour Rhel, CentOS, Oracle et SLES. Réexécutez ensuite l’étape 2.

4. Si les étapes ci-dessus ne fonctionnent pas, vérifiez si SELinux est installé et en mode d’application. Si c’est le cas, essayez de le définir sur le mode permissif (de préférence) ou désactivé. Pour ce faire, définissez le paramètre `SELINUX` sur « permissif » ou « désactivé » dans le `/etc/selinux/config` fichier, puis redémarrez. Pour plus d’informations, consultez la page homme de Selinux.
Essayez maintenant de redémarrer le service mdatp à l’aide de l’étape 2. Rétablissez immédiatement la modification de configuration pour des raisons de sécurité après l’avoir essayée et redémarrez.

5. Si `/opt` le répertoire est un lien symbolique, créez un montage de liaison pour `/opt/microsoft`.

6. Vérifiez que le démon dispose d’une autorisation exécutable.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    Si le démon ne dispose pas d’autorisations exécutables, rendez-le exécutable à l’aide de :

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    et réessayez d’exécuter l’étape 2.

7. Vérifiez que le système de fichiers contenant wdavdaemon n’est pas monté avec « noexec ».

## <a name="if-the-defender-for-endpoint-service-is-running-but-the-eicar-text-file-detection-doesnt-work"></a>Si le service Defender pour point de terminaison est en cours d’exécution, mais que la détection de fichier texte EICAR ne fonctionne pas

1. Vérifiez le type de système de fichiers à l’aide de :

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    Les systèmes de fichiers actuellement pris en charge pour l’activité d’accès sont répertoriés [ici](microsoft-defender-endpoint-linux.md#system-requirements). Les fichiers en dehors de ces systèmes de fichiers ne seront pas analysés.

## <a name="command-line-tool-mdatp-isnt-working"></a>L’outil en ligne de commande « mdatp » ne fonctionne pas

1. Si l’exécution de l’outil `mdatp` en ligne de commande génère une erreur `command not found`, exécutez la commande suivante :

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    et réessayez.

    Si aucune des étapes ci-dessus n’est utile, collectez les journaux de diagnostic :

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    Le chemin d’accès à un fichier zip qui contient les journaux s’affiche sous forme de sortie. Contactez notre support client avec ces journaux d’activité.
