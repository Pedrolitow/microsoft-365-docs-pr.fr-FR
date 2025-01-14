---
title: Résoudre les problèmes de Microsoft Defender pour point de terminaison sur Linux RHEL6
ms.reviewer: ''
description: Résoudre les problèmes de connectivité cloud pour Microsoft Defender pour point de terminaison sur Linux
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, cloud, connectivité, communication
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 288588be3b9f519da5e123ef1a07e6c216702fdf
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633788"
---
# <a name="troubleshoot-issues-for-microsoft-defender-for-endpoint-on-linux-rhel6"></a>Résoudre les problèmes de Microsoft Defender pour point de terminaison sur Linux RHEL6

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Cet article fournit des conseils sur la résolution des problèmes que vous pouvez rencontrer avec Microsoft Defender pour Linux sur Red Hat Linux 6 (RHEL 6) ou version ultérieure. 

Une fois le package (mdatp_XXX.XX.XX.XX.x86_64.rpm) installé, effectuez les actions fournies pour vérifier que l’installation a réussi. 


## <a name="check-the-service-health"></a>Vérifier l’intégrité du service

Utilisez la commande suivante pour vérifier l’intégrité du service :

```bash
mdatp health 
```

## <a name="verify-that-the-service-is-running"></a>Vérifier que le service est en cours d’exécution

Utilisez la commande suivante pour vérifier que le service est en cours d’exécution :

```bash
service mdatp status 
```

Sortie attendue : `mdatp start/running, process 4517`

## <a name="verify-the-distribution-and-kernel-version"></a>Vérifier la distribution et la version du noyau
Les versions de distribution et de noyau doivent figurer dans la liste prise en charge.

Utilisez la commande suivante pour obtenir la version de distribution :

```bash
cat /etc/redhat-release (or /etc/system-release) 
```

Utilisez la commande suivante pour obtenir la version du noyau :

```bash
uname -r
```
## <a name="check-if-mdatp-audisp-process-is-running"></a>Vérifier si le processus audisp mdatp est en cours d’exécution 
La sortie attendue est que le processus est en cours d’exécution.

Utilisez la commande suivante pour vérifier :

```bash
pidof mdatp_audisp_plugin 
```

## <a name="check-talpa-modules"></a>Vérifier les modules TALPA
Neuf modules doivent être chargés. 

Utilisez la commande suivante pour vérifier :

```bash
lsmod | grep talpa
```

Sortie attendue : activée

```bash
talpa_pedconnector       878  0 

talpa_pedevice          5189  2 talpa_pedconnector 

talpa_vfshook          32300  1 

talpa_vcdevice          4947  1 

talpa_syscall           9127  0 

talpa_core             90699  4 talpa_vfshook,talpa_vcdevice,talpa_syscall 

talpa_linux            29424  5 talpa_vfshook,talpa_vcdevice,talpa_syscall,talpa_core 

talpa_syscallhookprobe      882  0 

talpa_syscallhook      14987  2 talpa_vfshook,talpa_syscallhookprobe 
```


```bash
lsmod | grep talpa | wc -l 
```

Sortie attendue : 9

## <a name="check-talpa-status"></a>Vérifier l’état TALPA

```bash
cat /proc/sys/talpa/interceptors/VFSHookInterceptor/status 
```

Déboguer les fichiers journaux (à l’exception de l’offre groupée « mdatp diagnostic create ») 

```bash
/var/log/audit/audit.log 

/var/log/messages 

semanage fcontext -l > selinux.log 
```
 

Performances et mémoire 

```bash
top -p <wdavdaemon pid>      

pmap -x <wdavdaemon pid> 
```

Où `<wdavdaemon pid>` trouver à l’aide de `pidof wdavdaemon`.

