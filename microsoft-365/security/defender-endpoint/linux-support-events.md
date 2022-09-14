---
title: Résoudre les problèmes d’événements ou d’alertes manquants pour Microsoft Defender pour point de terminaison sur Linux
description: Résoudre les problèmes d’événements ou d’alertes manquants dans Microsoft Defender pour point de terminaison sur Linux.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, événements
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
- m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6ea07b089233217852b684009d8fea1280367e23
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687128"
---
# <a name="troubleshoot-missing-events-or-alerts-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Résoudre les problèmes d’événements ou d’alertes manquants pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article fournit des étapes générales pour atténuer les événements manquants ou les alertes dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

Une fois **que Microsoft Defender pour point de terminaison** a été correctement installé sur un appareil, une _page d’appareil_ est générée dans le portail. Vous pouvez passer en revue tous les événements enregistrés sous l’onglet Chronologie de la page de l’appareil ou dans la page de repérage avancé. Cette section résolvent le cas de certains événements ou de tous les événements attendus manquants.
Par exemple, si tous les événements _CreatedFile_ sont manquants.

## <a name="missing-network-and-login-events"></a>Événements réseau et de connexion manquants

Microsoft Defender pour point de terminaison l’infrastructure utilisée `audit` à partir de Linux pour suivre l’activité de connexion et de réseau.

1. Vérifiez que l’infrastructure d’audit fonctionne.

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

Sur les systèmes **SLES**, l’audit SYSCALL peut être désactivé par défaut et être pris en `auditd` compte pour les événements manquants.

1. Pour vérifier que l’audit SYSCALL n’est pas désactivé, répertoriez les règles d’audit actuelles :

    ```bash
    sudo auditctl -l
    ```

    si la ligne suivante est présente, supprimez-la ou modifiez-la pour permettre à Microsoft Defender pour point de terminaison de suivre des SYSCALL spécifiques.

    ```output
    -a task, never
    ```

    les règles d’audit se trouvent à `/etc/audit/rules.d/audit.rules`.

## <a name="missing-file-events"></a>Événements de fichier manquants

Les événements de fichier sont collectés avec l’infrastructure `fanotify` . Si certains événements de fichier ou tous les événements de fichier sont manquants, assurez-vous qu’il `fanotify` est activé sur l’appareil et que le système de fichiers est [pris en charge](microsoft-defender-endpoint-linux.md#system-requirements).

Répertoriez les systèmes de fichiers sur l’ordinateur avec :

```bash
df -Th
```
