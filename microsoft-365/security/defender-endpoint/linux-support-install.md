---
title: Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur Linux
ms.reviewer: ''
description: Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur Linux
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dc1e8707dc0810c0986698674a64e969792b5fb8
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311231"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes d’installation de Microsoft Defender pour endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-if-installation-succeeded"></a>Vérifier si l’installation a réussi

Une erreur d’installation peut ou non entraîner un message d’erreur significatif de la part du gestionnaire de package. Pour vérifier si l’installation a réussi, obtenez et vérifiez les journaux d’installation en utilisant :

```bash
 sudo journalctl --no-pager | grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

Une sortie de la commande précédente avec la date et l’heure correctes de l’installation indique la réussite.

Vérifiez également la [configuration du client](linux-install-manually.md#client-configuration) pour vérifier l’état du produit et détecter le fichier texte EICAR.

## <a name="make-sure-you-have-the-correct-package"></a>Assurez-vous que vous avez le package correct

N’oubliez pas que le package que vous installez correspond à la distribution et à la version de l’hôte.

| package                       | distribution                             |
|-------------------------------|------------------------------------------|
| mdatp-rhel8. Linux.x86_64.rpm  | Oracle, RHEL et CentOS 8.x              |
| mdatp-sles12. Linux.x86_64.rpm | SuSE Linux Enterprise Server 12.x        |
| mdatp-sles15. Linux.x86_64.rpm | SuSE Linux Enterprise Server 15.x        |
| mdatp. Linux.x86_64.rpm        | Oracle, RHEL et CentOS 7.x              |
| mdatp. Linux.x86_64.deb        | Debian et Ubuntu 16.04, 18.04 et 20.04 |

Pour [un déploiement](linux-install-manually.md)manuel, assurez-vous que la version et la version correctes ont été choisies.

## <a name="installation-failed"></a>Échec de l’installation

Vérifiez si le service mdatp est en cours d’exécution :

```bash
systemctl status mdatp
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

## <a name="steps-to-troubleshoot-if-mdatp-service-isnt-running"></a>Étapes à suivre pour résoudre les problèmes si le service mdatp n’est pas en cours d’exécution

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
    sudo systemctl enable mdatp
    ```

    ```bash
    sudo systemctl restart mdatp
    ```

3. Si mdatp.service n’est pas trouvé lors de l’exécution de la commande précédente, exécutez :

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path>
    ```

    où `<systemd_path>` est pour les distributions Ubuntu et Debian et pour `/lib/systemd/system` `/usr/lib/systemd/system` Rhel, CentOS, Oracle et SLES.
   Réexécutez ensuite l’étape 2.

4. Si les étapes ci-dessus ne fonctionnent pas, vérifiez si SELinux est installé et en mode d’application. Si c’est le cas, essayez de le définir sur le mode permissif (de préférence) ou désactivé. Pour ce faire, vous pouvez définir le paramètre sur « permissif » ou « désactivé » dans le fichier, puis par `SELINUX` `/etc/selinux/config` redémarrage. Pour plus d’informations, consultez la page de l’homme du sélinux.
Essayez maintenant de redémarrer le service mdatp à l’aide de l’étape 2. Revert the configuration change immediately though for security reasons after trying it andboot.

5. Si `/opt` le répertoire est un lien symbolique, créez un montage de liaison pour `/opt/microsoft` .

6. Assurez-vous que le daemon dispose de l’autorisation exécutable.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    Si le daemon n’a pas d’autorisations exécutables, rendez-le exécutable à l’aide de :

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    et réessayez d’exécution de l’étape 2.

7. Assurez-vous que le système de fichiers contenant wdavdaemon n’est pas monté avec « noexec ».

## <a name="if-mdatp-service-is-running-but-eicar-text-file-detection-doesnt-work"></a>Si le service mdatp est en cours d’exécution, mais que la détection de fichier texte EICAR ne fonctionne pas

1. Vérifiez le type de système de fichiers en utilisant :

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    Les systèmes de fichiers actuellement pris en charge pour l’activité d’accès sont répertoriés [ici.](microsoft-defender-endpoint-linux.md#system-requirements) Les fichiers en dehors de ces systèmes de fichiers ne seront pas analysés.

## <a name="command-line-tool-mdatp-isnt-working"></a>L’outil de ligne de commande « mdatp » ne fonctionne pas

1. Si l’exécution de l’outil en ligne de `mdatp` commande donne une `command not found` erreur, exécutez la commande suivante :

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    et essayez à nouveau.

    Si aucune des étapes ci-dessus ne vous aide, collectez les journaux de diagnostic :

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    Le chemin d’accès à un fichier zip qui contient les journaux s’affiche en tant que sortie. À l’aide de ces journaux, connectez-vous au support technique.
