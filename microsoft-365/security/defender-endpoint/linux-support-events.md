---
title: Résoudre les problèmes d'événements ou d'alertes manquants pour Microsoft Defender ATP pour Linux
description: Résoudre les problèmes d'événements ou d'alertes manquants dans Microsoft Defender ATP pour Linux.
keywords: microsoft, defender, atp, linux, événements
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
mms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5981cb75b4c835390e27d902b5950e3c68305200
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51687453"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes d'événements ou d'alertes manquants pour Microsoft Defender pour Endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison sur Linux](microsoft-defender-endpoint-linux.md)

Cet article fournit quelques étapes générales pour atténuer les événements ou alertes manquants dans le portail [du centre de](https://securitycenter.windows.com/) sécurité.

Une **fois que Microsoft Defender pour le point** de terminaison a été correctement installé sur un appareil, une _page_ d'appareil est générée dans le portail. Vous pouvez passer en revue tous les événements enregistrés dans l'onglet Chronologie de la page de l'appareil ou dans la page de recherche avancée. Cette section permet de résoudre les problèmes de certains événements attendus ou de tous.
Par exemple, si tous _les événements CreatedFile_ sont manquants.

## <a name="missing-network-and-login-events"></a>Événements réseau et de connexion manquants

Microsoft Defender pour le point de terminaison a utilisé `audit` l'infrastructure linux pour suivre l'activité réseau et de connexion.

1. Assurez-vous que l'infrastructure d'audit fonctionne.

    ```bash
    service auditd status
    ```

    sortie attendue :

    ```output
    ● auditd.service - Security Auditing Service
    Loaded: loaded (/usr/lib/systemd/system/auditd.service; enabled; vendor preset: enabled)
    Active: active (running) since Mon 2020-12-21 10:48:02 IST; 2 weeks 0 days ago
        Docs: man:auditd(8)
            https://github.com/linux-audit/audit-documentation
    Process: 16689 ExecStartPost=/sbin/augenrules --load (code=exited, status=1/FAILURE)
    Process: 16665 ExecStart=/sbin/auditd (code=exited, status=0/SUCCESS)
    Main PID: 16666 (auditd)
        Tasks: 25
    CGroup: /system.slice/auditd.service
            ├─16666 /sbin/auditd
            ├─16668 /sbin/audispd
            ├─16670 /usr/sbin/sedispatch
            └─16671 /opt/microsoft/mdatp/sbin/mdatp_audisp_plugin -d
    ```

2. Si `auditd` elle est marquée comme arrêtée, démarrez-la.

    ```bash
    service auditd start
    ```

**Sur les systèmes SLES,** l'audit SYSCALL peut être désactivé par défaut et peut être tenu compte des `auditd` événements manquants.

1. Pour vérifier que l'audit SYSCALL n'est pas désactivé, listez les règles d'audit actuelles :

    ```bash
    sudo auditctl -l
    ```

    si la ligne suivante est présente, supprimez-la ou modifiez-la pour permettre à Microsoft Defender for Endpoint de suivre des SYSCALL spécifiques.

    ```output
    -a task, never
    ```

    les règles d'audit se trouvent à `/etc/audit/rules.d/audit.rules` l'emplacement .

## <a name="missing-file-events"></a>Événements de fichier manquants

Les événements de fichier sont collectés avec `fanotify` l'infrastructure. Si certains événements de fichier ou tous sont manquants, assurez-vous qu'il est activé sur l'appareil et que le système `fanotify` de fichiers est pris en [charge.](microsoft-defender-endpoint-linux.md#system-requirements)

List the filesystems on the machine with:

```bash
df -Th
```
