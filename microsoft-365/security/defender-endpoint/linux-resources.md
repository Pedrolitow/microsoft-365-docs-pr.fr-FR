---
title: Microsoft Defender pour point de terminaison sur les ressources Linux
ms.reviewer: ''
description: Décrit les ressources pour Microsoft Defender pour point de terminaison sur Linux, notamment comment la désinstaller, comment collecter des journaux de diagnostic, des commandes CLI et des problèmes connus avec le produit.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: 5e3f8cb9cc826894f816fcebf28ef73213548f22
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233329"
---
# <a name="resources"></a>Ressources

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Collecter des informations de diagnostic

Si vous pouvez reproduire un problème, augmentez d’abord le niveau de journalisation, exécutez le système pendant un certain temps, puis restaurez le niveau de journalisation à la valeur par défaut.

1. Augmenter le niveau de journalisation :

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Reproduisez le problème.

3. Exécutez la commande suivante pour sauvegarder les journaux de Defender pour point de terminaison. Les fichiers sont stockés à l’intérieur d’une archive .zip.

   ```bash
   sudo mdatp diagnostic create
   ```

    Cette commande affiche également le chemin d’accès du fichier à la sauvegarde une fois l’opération réussie :

   ```Output
   Diagnostic file created: <path to file>
   ```

4. Restaurer le niveau de journalisation :

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>Problèmes d’installation du journal

Si une erreur se produit pendant l’installation, le programme d’installation signale uniquement un échec général.

Le journal détaillé sera enregistré `/var/log/microsoft/mdatp/install.log`dans .
Si vous rencontrez des problèmes pendant l’installation, envoyez-nous ce fichier afin que nous puissions vous aider à diagnostiquer la cause.

## <a name="uninstall"></a>Désinstaller

Il existe plusieurs façons de désinstaller Defender pour point de terminaison sur Linux. Si vous utilisez un outil de configuration tel que Puppet, suivez les instructions de désinstallation du package pour l’outil de configuration.

### <a name="manual-uninstallation"></a>Désinstallation manuelle

- `sudo yum remove mdatp` pour RHEL et les variantes (CentOS et Oracle Linux).
- `sudo zypper remove mdatp` pour SLES et les variantes.
- `sudo apt-get purge mdatp` pour les systèmes Ubuntu et Debian.

## <a name="configure-from-the-command-line"></a>Configurer à partir de la ligne de commande

Des tâches importantes, telles que le contrôle des paramètres de produit et le déclenchement d’analyses à la demande, peuvent être effectuées à partir de la ligne de commande.

### <a name="global-options"></a>Options globales

Par défaut, l’outil en ligne de commande génère le résultat au format lisible par l’homme. En outre, l’outil prend également en charge la sortie du résultat en tant que JSON, ce qui est utile pour les scénarios d’automatisation. Pour remplacer la sortie par JSON, passez `--output json` à l’une des commandes ci-dessous.

### <a name="supported-commands"></a>Commandes prises en charge

Le tableau suivant répertorie les commandes pour certains des scénarios les plus courants. Exécutez `mdatp help` à partir du terminal pour afficher la liste complète des commandes prises en charge.

<br>

****

|Groupe|Scénario|Commande|
|---|---|---|
|Configuration|Activer/désactiver la protection en temps réel|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Configuration|Activer/désactiver la surveillance du comportement|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Configuration|Activer/désactiver la protection cloud|`mdatp config cloud --value [enabled\|disabled]`|
|Configuration|Activer/désactiver les diagnostics de produit|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Configuration|Activer/désactiver la soumission automatique d’exemples|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Configuration|Activer/désactiver le mode passif AV|`mdatp config passive-mode --value [enabled\|disabled]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour une extension de fichier|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un fichier|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un répertoire|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un processus|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Configuration|Répertorier toutes les exclusions antivirus|`mdatp exclusion list`|
|Configuration|Ajouter un nom de menace à la liste autorisée|`mdatp threat allowed add --name [threat-name]`|
|Configuration|Supprimer un nom de menace de la liste autorisée|`mdatp threat allowed remove --name [threat-name]`|
|Configuration|Répertorier tous les noms de menaces autorisés|`mdatp threat allowed list`|
|Configuration|Activer la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Configuration|Désactiver la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Configuration|Activer le mode audit pour la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Configuration|Configurer le degré de parallélisme pour les analyses à la demande|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Configuration|Activer/désactiver les analyses après les mises à jour du renseignement de sécurité|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Configuration|Activer/désactiver l’analyse des archives (analyses à la demande uniquement)|`mdatp config scan-archives --value [enabled/disabled]`|
|Configuration|Activer/désactiver le calcul de hachage de fichier|`mdatp config enable-file-hash-computation --value [enabled/disabled]`|
|Diagnostics|Modifier le niveau du journal|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Diagnostics|Générer des journaux de diagnostic|`mdatp diagnostic create --path [directory]`|
|Intégrité|Vérifier l’intégrité du produit|`mdatp health`|
|Protection|Analyser un chemin d’accès|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Protection|Effectuer une analyse rapide|`mdatp scan quick`|
|Protection|Effectuer une analyse complète|`mdatp scan full`|
|Protection|Annuler une analyse à la demande en cours|`mdatp scan cancel`|
|Protection|Demander une mise à jour du renseignement de sécurité|`mdatp definitions update`|
|Historique de protection|Imprimer l’historique de protection complet|`mdatp threat list`|
|Historique de protection|Obtenir les détails des menaces|`mdatp threat get --id [threat-id]`|
|Gestion de la quarantaine|Répertorier tous les fichiers mis en quarantaine|`mdatp threat quarantine list`|
|Gestion de la quarantaine|Supprimer tous les fichiers de la quarantaine|`mdatp threat quarantine remove-all`|
|Gestion de la quarantaine|Ajouter un fichier détecté comme une menace à la mise en quarantaine|`mdatp threat quarantine add --id [threat-id]`|
|Gestion de la quarantaine|Supprimer un fichier détecté comme une menace de la mise en quarantaine|`mdatp threat quarantine remove --id [threat-id]`|
|Gestion de la quarantaine|Restaurer un fichier à partir de la mise en quarantaine|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|Détection et réponse du point de terminaison|Définir la préversion anticipée (inutilisée)|`mdatp edr early-preview [enable|disable]`|
|Détection et réponse du point de terminaison|Définir l’ID de groupe|`mdatp edr group-ids --group-id [group-id]`|
|Détection et réponse du point de terminaison|Définir/supprimer une balise, uniquement `GROUP` prise en charge|`mdatp edr tag set --name GROUP --value [tag]`|
|Détection et réponse du point de terminaison|Exclusions de liste (racine)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
