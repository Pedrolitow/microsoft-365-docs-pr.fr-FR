---
title: Planifier des analyses avec Microsoft Defender pour Endpoint (Linux)
description: Découvrez comment planifier un temps d'analyse automatique pour Microsoft Defender pour Endpoint (Linux) afin de mieux protéger les ressources de votre organisation.
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
ms.openlocfilehash: f868570fccf9b30cde5f16aa8e71292fb8b09497
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933132"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Planifier des analyses avec Microsoft Defender pour Endpoint (Linux)

Pour exécuter une analyse pour Linux, voir [Commandes pris en charge.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/linux-resources#supported-commands)

Linux (et Unix) ont un outil appelé **crontab** (semblable au Programmeur des tâches) pour pouvoir exécuter des tâches programmées.

## <a name="pre-requisite"></a>Conditions préalables

> [!NOTE]
> Pour obtenir la liste de tous les fuseaux horaires, exécutez la commande suivante : `timedatectl list-timezones`<br>
> Exemples pour les fuseaux horaires :
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Pour définir le travail Cron
Utilisez les commandes suivantes :

**Pour sauvegarder les entrées de crontab**

`sudo crontab -l > /var/tmp/cron_backup_200919.dat`

> [!NOTE]
> Where 200919 == YRMMDD

> [!TIP]
> Faites-le avant de modifier ou de supprimer. <br>

Pour modifier le crontab et ajouter un nouveau travail en tant qu'utilisateur racine : <br>
`sudo crontab -e`

> [!NOTE]
> L'éditeur par défaut est VIM.

Vous pouvez voir :

0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh

Appuyez sur « Insérer »

Ajoutez les entrées suivantes :

CRON_TZ=Amérique/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log

> [!NOTE]
>Dans cet exemple, nous l'avons définie sur 00 minutes, 2 heures du matin. (heure au format 24 heures), tous les jours du mois, tous les mois, le samedi. Ce qui signifie qu'il sera exécuté le samedi à 2 h 00. Pacifique (UTC –8).

Appuyez sur « Échap »

Tapez « :wq » sans guillemets doubles.

> [!NOTE]
> w == write, q == quit

Pour afficher vos travaux cron, tapez `sudo crontab -l`

:::image type="content" source="/microsoft-365/security/defender-endpoint/images/linux-mdatp-1" alt-text="linux mdatp":::

**Pour inspecter les séries de travail de cron**

`sudo grep mdatp /var/log/cron`

**Pour inspecter le fichier mdatp_cron_job.log**

`sudo nano mdatp_cron_job.log`

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Pour les personnes qui utilisent Ansible, Chef ou Autres

Utilisez les commandes suivantes :
### <a name="to-set-cron-jobs-in-ansible"></a>Pour définir des travaux de cron dans Ansible

`cron – Manage cron.d and crontab entries`

Pour plus d’informations, voir [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html).

### <a name="to-set-crontabs-in-chef"></a>Pour définir des crontabs dans chef
`cron resource`

Pour plus d’informations, voir [https://docs.chef.io/resources/cron/](https://docs.chef.io/resources/cron/).

### <a name="to-set-cron-jobs-in-puppet"></a>Pour définir des travaux de cron dans l'ombre
Type de ressource : cron

Pour plus d’informations, voir [https://puppet.com/docs/puppet/5.5/types/cron.html](https://puppet.com/docs/puppet/5.5/types/cron.html).

Automatisation avec l'annexe : tâches Cron et tâches programmées

Pour plus d’informations, voir [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/).

## <a name="additional-information"></a>Informations supplémentaires

**Pour obtenir de l'aide sur crontab**

`man crontab`

**Pour obtenir la liste du fichier crontab de l'utilisateur actuel**

`crontab -l`

**Pour obtenir la liste du fichier crontab d'un autre utilisateur**

`crontab -u username -l`

**Pour sauvegarder les entrées de crontab**

`crontab -l > /var/tmp/cron_backup.dat`

> [!TIP]
> Faites-le avant de modifier ou de supprimer. <br>

**Pour restaurer des entrées de crontab**

`crontab /var/tmp/cron_backup.dat`

**Pour modifier le crontab et ajouter un nouveau travail en tant qu'utilisateur racine**

`sudo crontab -e`

**Pour modifier le crontab et ajouter un nouveau travail**

`crontab -e`

**Pour modifier les entrées de crontab d'autres utilisateurs**

`crontab -u username -e`

**Pour supprimer toutes les entrées crontab**

`crontab -r`

**Pour supprimer les entrées de crontab d'autres utilisateurs**

`crontab -u username -r`

**Explication**

+—————- minute (valeurs : 0 – 59) (caractères spéciaux : , – * /)  <br>
| +————- heure (valeurs : 0 – 23) (caractères spéciaux : , – * /) <br>
| | +———- jour du mois (valeurs : 1 – 31) (caractères spéciaux : , – * / L W C)  <br>
| | | +——- mois (valeurs : 1 – 12) (caractères spéciaux : ,- * / )  <br>
| | | | +— jour de la semaine (valeurs : 0 – 6) (Sunday=0 ou 7) (caractères spéciaux : , – * / L W C) <br>
| | | | | commande ****** à exécuter


