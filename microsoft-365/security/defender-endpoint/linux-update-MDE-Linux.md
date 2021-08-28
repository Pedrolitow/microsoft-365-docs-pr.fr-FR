---
title: Planification d’une mise à jour de Microsoft Defender pour Endpoint (Linux)
description: Découvrez comment planifier une mise à jour de Microsoft Defender pour Endpoint (Linux) pour mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, analyses, antivirus, microsoft defender pour point de terminaison (linux)
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
ms.openlocfilehash: 05747374e2a28331ec0742fe11ca2dbc660771c5
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58570016"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Planifier une mise à jour de Microsoft Defender pour point de terminaison (Linux)

Pour exécuter une mise à jour sur Microsoft Defender pour endpoint sur Linux, voir Déployer les mises à jour [de Microsoft Defender pour Endpoint sur Linux.](/microsoft-365/security/defender-endpoint/linux-updates)

Linux (et Unix) ont un outil appelé **crontab** (semblable au Programmeur des tâches) pour pouvoir exécuter des tâches programmées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`
>
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
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> Où 201118 == AAMMMMDD

> [!TIP]
> Faites-le avant de modifier ou de supprimer.

Pour modifier le crontab et ajouter un nouveau travail en tant qu’utilisateur racine :

```bash
sudo crontab -e
```

> [!NOTE]
> L’éditeur par défaut est VIM.

Vous pouvez voir :

```output
0****/etc/opt/microsoft/mdatp/logrorate.sh
```

And

```output
02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log
```

Voir [Analyses de planification avec Microsoft Defender pour Endpoint (Linux)](linux-schedule-scan-atp.md)

Appuyez sur « Insérer »

Ajoutez les entrées suivantes :

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL et variantes (CentOS et Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="sles-and-variants"></a>! SLES et variantes
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo zypper update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="ubuntu-and-debian-systems"></a>! Systèmes Ubuntu et Debian
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo apt-get install --only-upgrade mdatp >> ~/mdatp_cron_job.log
> ```

> [!NOTE]
> Dans les exemples ci-dessus, nous la fixons à 00 minutes, 6 heures (heure au format 24 heures), n’importe quel jour du mois, tous les mois, le dimanche. [$(date + d) -le 15] == Ne s’exécute pas, sauf s’il est égal ou inférieur au \% 15e jour (3e semaine). Cela signifie qu’il s’exécutera tous les 3e dimanche (7) du mois à 6 h 00. Pacifique (UTC -8).

Appuyez sur « Échap »

Tapez `:wq` " w/o les guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="mettez à jour Defender pour endpoint sur Linux.":::

Pour inspecter les séries de travail de recherche :

```bash
sudo grep mdatp /var/log/cron
```

Pour inspecter le fichier mdatp_cron_job.log

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour les personnes qui utilisent Ansible, Chef ou Autres

Utilisez les commandes suivantes :

### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux de cron dans Ansible

```bash
cron - Manage cron.d and crontab entries
```

Si vous souhaitez plus d’informations, consultez <https://docs.ansible.com/ansible/latest/modules/cron_module.html>.

### <a name="to-set-crontabs-in-chef"></a>Pour définir des crontabs dans chef

```bash
cron resource
```

Si vous souhaitez plus d’informations, consultez <https://docs.chef.io/resources/cron/>.

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux de cron dans l’ombre

Type de ressource : cron

Si vous souhaitez plus d’informations, consultez <https://puppet.com/docs/puppet/5.5/types/cron.html>.

Automatisation avec l’annexe : tâches Cron et tâches programmées

Si vous souhaitez plus d’informations, consultez <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/>.

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

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
