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
ms.openlocfilehash: 9b7699b1a24e7e1d74a48389d02518e814911ecc
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52730869"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Planifier une mise à jour de Microsoft Defender pour point de terminaison (Linux)

Pour exécuter une mise à jour sur Microsoft Defender pour endpoint sur Linux, voir Déployer les mises à jour [de Microsoft Defender pour Endpoint sur Linux.](/microsoft-365/security/defender-endpoint/linux-updates)

Linux (et Unix) ont un outil appelé **crontab** (semblable au Programmeur des tâches) pour pouvoir exécuter des tâches programmées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`<br>
> Exemples pour les fuseaux horaires : <br>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Pour définir le travail Cron
Utilisez les commandes suivantes :

**Pour sauvegarder les entrées de crontab**

`sudo crontab -l > /var/tmp/cron_backup_201118.dat`

> [!NOTE]
> Where 201118 == YYMMDD

> [!TIP]
> Faites-le avant de modifier ou de supprimer. <br>

Pour modifier le crontab et ajouter un nouveau travail en tant qu’utilisateur racine : <br>
`sudo crontab -e`

> [!NOTE]
> L’éditeur par défaut est VIM.

Vous pouvez voir :

0****/etc/opt/microsoft/mdatp/logrorate.sh

And

02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log

Voir [Analyses de planification avec Microsoft Defender pour Endpoint (Linux)](linux-schedule-scan-atp.md)

Appuyez sur « Insérer »

Ajoutez les entrées suivantes :

CRON_TZ=Amérique/Los_Angeles

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL et variantes (CentOS et Oracle Linux)

`06**sun[$(date +\%d) -le 15] sudo yum update mdatp>>~/mdatp_cron_job.log`

> #<a name="sles-and-variants"></a>! SLES et variantes

`06**sun[$(date +\%d) -le 15] sudo zypper update mdatp>>~/mdatp_cron_job.log`

> #<a name="ubuntu-and-debian-systems"></a>! Systèmes Ubuntu et Debian

`0 6 * * sun [$(date +\%d) -le 15] sudo apt-get install --only-upgrade mdatp>>~/mdatp_cron_job.log`

> [!NOTE]
> Dans les exemples ci-dessus, nous la fixons à 00 minutes, 6 heures (heure au format 24 heures), n’importe quel jour du mois, tous les mois, le dimanche. [$(date + d) -le 15] == Ne s’exécute pas, sauf s’il est égal ou inférieur au \% 15e jour (3e semaine). Cela signifie qu’il s’exécutera tous les 3e dimanche (7) du mois à 6 h 00. Pacifique (UTC -8).

Appuyez sur « Échap »

Tapez « :wq » avec les guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="mettre à jour MDE linux":::

Pour inspecter les séries de travail de recherche : `sudo grep mdatp /var/log/cron`

Pour inspecter le fichier mdatp_cron_job.log `sudo nano mdatp_cron_job.log`

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour les personnes qui utilisent Ansible, Chef ou Autres

Utilisez les commandes suivantes :
### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux de cron dans Ansible

`cron – Manage cron.d and crontab entries`

Pour plus d’informations, voir [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html).

### <a name="to-set-crontabs-in-chef"></a>Pour définir des crontabs dans chef
`cron resource`

Pour plus d’informations, voir [https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/).

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux de cron dans l’ombre
Type de ressource : cron

Pour plus d’informations, voir [https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html).

Automatisation avec l’annexe : tâches Cron et tâches programmées

Pour plus d’informations, voir [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/).

## <a name="additional-information"></a>Informations supplémentaires

**Pour obtenir de l’aide sur crontab**

`man crontab`

**Pour obtenir la liste du fichier crontab de l’utilisateur actuel**

`crontab -l`

**Pour obtenir la liste du fichier crontab d’un autre utilisateur**

`crontab -u username -l`

**Pour sauvegarder les entrées de crontab**

`crontab -l > /var/tmp/cron_backup.dat`

> [!TIP]
> Faites-le avant de modifier ou de supprimer. <br>

**Pour restaurer des entrées de crontab**

`crontab /var/tmp/cron_backup.dat`

**Pour modifier le crontab et ajouter un nouveau travail en tant qu’utilisateur racine**

`sudo crontab -e`

**Pour modifier le crontab et ajouter un nouveau travail**

`crontab -e`

**Pour modifier les entrées de crontab d’autres utilisateurs**

`crontab -u username -e`

**Pour supprimer toutes les entrées crontab**

`crontab -r`

**Pour supprimer les entrées de crontab d’autres utilisateurs**

`crontab -u username -r`

**Explication**

<pre>
+—————- minute (values: 0 – 59) (special characters: , – * /)  <br>
| +————- hour (values: 0 – 23) (special characters: , – * /) <br>
| | +———- day of month (values: 1 – 31) (special characters: , – * / L W C)  <br>
| | | +——- month (values: 1 – 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 – 6) (Sunday=0 or 7) (special characters: , – * / L W C) <br>
| | | | |*****command to be executed
</pre>

