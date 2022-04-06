---
title: Guide pratique pour planifier des analyses avec Microsoft Defender pour point de terminaison (Linux)
description: Découvrez comment planifier un temps d’analyse automatique pour Microsoft Defender pour point de terminaison (Linux) afin de mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, analyses, antivirus, microsoft defender pour point de terminaison (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 706284ed0adf49c4da6357b6bb8217d5a14268e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663487"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Planifier des analyses avec Microsoft Defender pour point de terminaison (Linux)

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Pour exécuter une analyse pour Linux, consultez [Commandes prises en charge](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

Linux (et Unix) disposent d’un outil appelé **crontab** (similaire au planificateur de tâches) pour pouvoir exécuter des tâches planifiées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`<br>
> Exemples de fuseaux horaires :
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Pour définir le travail Cron

Utilisez les commandes suivantes :

### <a name="backup-crontab-entries"></a>Entrées crontab de sauvegarde

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Where 200919 == YRMMDD

> [!TIP]
> Effectuez cette opération avant de modifier ou de supprimer.

Pour modifier le crontab et ajouter un nouveau travail en tant qu’utilisateur racine :

```bash
sudo crontab -e
```

> [!NOTE]
> L’éditeur par défaut est VIM.

Vous pouvez voir :

```outbou
0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh
```

Appuyez sur « Insertion »

Ajoutez les entrées suivantes :

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> Dans cet exemple, nous l’avons défini sur 00 minutes, 2 heures du matin. (heure au format 24 heures), n’importe quel jour du mois, n’importe quel mois, le samedi. Ce qui signifie qu’il s’exécutera le samedi à 2h00. Pacifique (UTC -8).

Appuyez sur Échap

Tapez «`:wq` » sans guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="Page mdatp Linux" lightbox="../../media/linux-mdatp-1.png":::

#### <a name="to-inspect-cron-job-runs"></a>Pour inspecter les exécutions de travaux cron

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>Pour inspecter le mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour ceux qui utilisent Ansible, Chef ou Puppet

Utilisez les commandes suivantes :

### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux cron dans Ansible

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Si vous souhaitez plus d’informations, consultez <https://docs.chef.io/resources/cron/>.

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux cron dans Puppet

```bash
Resource Type: cron
```

Si vous souhaitez plus d’informations, consultez <https://puppet.com/docs/puppet/5.5/types/cron.html>.

Automatisation avec Puppet : tâches Cron et tâches planifiées

Pour plus d’informations, voir [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/).

## <a name="additional-information"></a>Informations supplémentaires

### <a name="to-get-help-with-crontab"></a>Pour obtenir de l’aide avec crontab

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Pour obtenir la liste du fichier crontab de l’utilisateur actuel

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Pour obtenir la liste du fichier crontab d’un autre utilisateur

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Pour sauvegarder des entrées crontab

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Effectuez cette opération avant de modifier ou de supprimer.

### <a name="to-restore-crontab-entries"></a>Pour restaurer des entrées crontab

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>Pour modifier le crontab et ajouter un nouveau travail en tant qu’utilisateur racine

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>Pour modifier le crontab et ajouter un nouveau travail

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>Pour modifier les entrées crontab d’un autre utilisateur

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Pour supprimer toutes les entrées crontab

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Pour supprimer les entrées crontab d’un autre utilisateur

```bash
crontab -u username -r
```

### <a name="explanation"></a>Explication

+—————- minute (valeurs : 0 à 59) (caractères spéciaux : , \- \* /)  <br>
| +————- heure (valeurs : 0 à 23) (caractères spéciaux : , \- \* /) <br>
| | +———- jour du mois (valeurs : 1 à 31) (caractères spéciaux : , \- \* / L W C)  <br>
| | | +——- mois (valeurs : 1 à 12) (caractères spéciaux : , \- \* / )  <br>
| | | | +— jour de la semaine (valeurs : 0 - 6) (Sunday=0 ou 7) (caractères spéciaux : , \- \* / L W C) <br>
commande | | | | |****** à exécuter
