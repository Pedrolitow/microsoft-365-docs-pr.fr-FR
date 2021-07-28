---
title: Planifier des analyses avec Microsoft Defender pour Endpoint (Linux)
description: Découvrez comment planifier un temps d’analyse automatique pour Microsoft Defender pour Endpoint (Linux) afin de mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, analyses, antivirus, microsoft defender pour point de terminaison (linux)
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
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d8b7bbd2a5f1050b7897af3b208346330172ef94
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53623203"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Planifier des analyses avec Microsoft Defender pour Endpoint (Linux)

Pour exécuter une analyse pour Linux, voir [Commandes pris en charge.](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands)

Linux (et Unix) ont un outil appelé **crontab** (semblable au Programmeur des tâches) pour pouvoir exécuter des tâches programmées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`<br>
> Exemples pour les fuseaux horaires :
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Pour définir le travail Cron

Utilisez les commandes suivantes :

### <a name="backup-crontab-entries"></a>Entrées de crontab de sauvegarde

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Où 200919 == YRMMDD

> [!TIP]
> Faites-le avant de modifier ou de supprimer.

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

Appuyez sur « Insérer »

Ajoutez les entrées suivantes :

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> Dans cet exemple, nous l’avons définie sur 00 minutes, 2 heures du matin. (heure au format 24 heures), tous les jours du mois, tous les mois, le samedi. Ce qui signifie qu’il sera exécuté le samedi à 2 h 00. Pacifique (UTC -8).

Appuyez sur « Échap »

Type " `:wq` " sans guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="/microsoft-365/security/defender-endpoint/images/linux-mdatp-1" alt-text="linux mdatp":::

#### <a name="to-inspect-cron-job-runs"></a>Pour inspecter les séries de travail de cron

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>Pour inspecter le fichier mdatp_cron_job.log*

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour les personnes qui utilisent Ansible, Chef ou Autres

Utilisez les commandes suivantes :

### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux de cron dans Ansible

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Si vous souhaitez plus d’informations, consultez <https://docs.chef.io/resources/cron/>.

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux de cron dans l’ombre

```bash
Resource Type: cron
```

Si vous souhaitez plus d’informations, consultez <https://puppet.com/docs/puppet/5.5/types/cron.html>.

Automatisation avec l’annexe : tâches Cron et tâches programmées

Pour plus d’informations, voir [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/).

## <a name="additional-information"></a>Informations supplémentaires

### <a name="to-get-help-with-crontab"></a>Pour obtenir de l’aide sur crontab

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

### <a name="to-backup-crontab-entries"></a>Pour sauvegarder les entrées de crontab

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Faites-le avant de modifier ou de supprimer.

### <a name="to-restore-crontab-entries"></a>Pour restaurer des entrées de crontab

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

### <a name="to-edit-other-users-crontab-entries"></a>Pour modifier les entrées de crontab d’autres utilisateurs

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Pour supprimer toutes les entrées crontab

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Pour supprimer les entrées de crontab d’autres utilisateurs

```bash
crontab -u username -r
```

### <a name="explanation"></a>Explication

+—————- minute (valeurs : 0 - 59) (caractères spéciaux : , - * /)  <br>
| +————- heure (valeurs : 0 - 23) (caractères spéciaux : , - * /) <br>
| | +———- jour du mois (valeurs : 1 - 31) (caractères spéciaux : , - * / L W C)  <br>
| | | +——- mois (valeurs : 1 - 12) (caractères spéciaux : ,- * / )  <br>
| | | | +— jour de la semaine (valeurs : 0 - 6) (Sunday=0 ou 7) (caractères spéciaux : , - * / L W C) <br>
| | | | | commande ****** à exécuter
