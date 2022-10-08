---
title: Comment planifier une mise à jour du Microsoft Defender pour point de terminaison (Linux)
description: Découvrez comment planifier une mise à jour des Microsoft Defender pour point de terminaison (Linux) pour mieux protéger les ressources de votre organisation.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, analyses, antivirus, microsoft defender pour point de terminaison (linux)
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
ms.openlocfilehash: f1d0716f36e274ee5445304a73f3ab76f0686123
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68224863"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Planifier une mise à jour de Microsoft Defender pour point de terminaison (Linux)

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Pour exécuter une mise à jour sur Microsoft Defender pour point de terminaison sur Linux, consultez [Déployer des mises à jour pour Microsoft Defender pour point de terminaison sur Linux](/microsoft-365/security/defender-endpoint/linux-updates).

Linux (et Unix) disposent d’un outil appelé **crontab** (similaire au planificateur de tâches) pour pouvoir exécuter des tâches planifiées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`
>
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
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> Where 201118 == YYMMDD

> [!TIP]
> Effectuez cette opération avant de modifier ou de supprimer.

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

Voir [Les analyses de planification avec Microsoft Defender pour point de terminaison (Linux)](linux-schedule-scan-mde.md)

Appuyez sur « Insertion »

Ajoutez les entrées suivantes :

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL et variantes (CentOS et Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp -y >> ~/mdatp_cron_job.log
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
> Dans les exemples ci-dessus, nous le définissons sur 00 minutes, 6 heures (heure au format 24 heures), n’importe quel jour du mois, n’importe quel mois, le dimanche. [$(date +\%d) -le 15] == Ne s’exécute pas sauf s’il est égal ou inférieur au 15e jour (3e semaine). Ce qui signifie qu’il s’exécutera tous les 3 dimanches(7) du mois à 6h00. Pacifique (UTC -8).

Appuyez sur Échap

Tapez «`:wq` » w/o les guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="mettre à jour Defender pour point de terminaison sur Linux.":::

Pour inspecter les exécutions de travaux cron :

```bash
sudo grep mdatp /var/log/cron
```

Pour inspecter le fichier mdatp_cron_job.log

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour ceux qui utilisent Ansible, Chef ou Puppet

Utilisez les commandes suivantes :

### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux cron dans Ansible

```bash
cron - Manage cron.d and crontab entries
```

Si vous souhaitez plus d’informations, consultez <https://docs.ansible.com/ansible/latest/modules/cron_module.html>.

### <a name="to-set-crontabs-in-chef"></a>Pour définir des crontabs dans Chef

```bash
cron resource
```

Si vous souhaitez plus d’informations, consultez <https://docs.chef.io/resources/cron/>.

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux cron dans Puppet

Type de ressource : cron

Si vous souhaitez plus d’informations, consultez <https://puppet.com/docs/puppet/5.5/types/cron.html>.

Automatisation avec Puppet : tâches Cron et tâches planifiées

Si vous souhaitez plus d’informations, consultez <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/>.

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

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
