---
title: Résoudre les problèmes d’événements ou d’alertes manquants pour Microsoft Defender pour Endpoint sur Linux
description: Résoudre les problèmes d’événements ou d’alertes manquants dans Microsoft Defender pour Endpoint sur Linux.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, événements
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
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 82c1418d58679fef1b59e51b41052e4dfe584635
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61168537"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes d’événements ou d’alertes manquants pour Microsoft Defender pour Endpoint sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article fournit quelques étapes générales pour atténuer les événements ou alertes manquants dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le portail Microsoft 365 Defender.</a>

Une **fois que Microsoft Defender pour le point** de terminaison a été correctement installé sur un appareil, une _page_ d’appareil est générée dans le portail. Vous pouvez passer en revue tous les événements enregistrés dans l’onglet Chronologie de la page de l’appareil ou dans la page de recherche avancée. Cette section permet de résoudre les problèmes de certains événements attendus ou de tous.
Par exemple, si tous _les événements CreatedFile_ sont manquants.

## <a name="missing-network-and-login-events"></a>Événements réseau et de connexion manquants

Microsoft Defender pour le point de terminaison a utilisé `audit` l’infrastructure linux pour suivre l’activité réseau et de connexion.

1. Assurez-vous que l’infrastructure d’audit fonctionne.

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

**Sur les systèmes SLES,** l’audit SYSCALL peut être désactivé par défaut et peut être tenu compte des `auditd` événements manquants.

1. Pour vérifier que l’audit SYSCALL n’est pas désactivé, listez les règles d’audit actuelles :

    ```bash
    sudo auditctl -l
    ```

    si la ligne suivante est présente, supprimez-la ou modifiez-la pour permettre à Microsoft Defender for Endpoint de suivre des SYSCALL spécifiques.

    ```output
    -a task, never
    ```

    les règles d’audit se trouvent à `/etc/audit/rules.d/audit.rules` l’emplacement .

## <a name="missing-file-events"></a>Événements de fichier manquants

Les événements de fichier sont collectés avec `fanotify` l’infrastructure. Si certains événements de fichier ou tous sont manquants, assurez-vous qu’il est activé sur l’appareil et que le système `fanotify` de fichiers est pris en [charge.](microsoft-defender-endpoint-linux.md#system-requirements)

List the filesystems on the machine with:

```bash
df -Th
```
