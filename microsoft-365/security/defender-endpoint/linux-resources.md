---
title: Microsoft Defender pour point de terminaison sur les ressources Linux
ms.reviewer: ''
description: Décrit les ressources de Microsoft Defender pour Endpoint sur Linux, notamment comment le désinstaller, comment collecter les journaux de diagnostic, les commandes CLI et les problèmes connus avec le produit.
keywords: microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, préinstallation, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: e20b993d577f144e80c99479bac7bf70e484f785
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61168881"
---
# <a name="resources"></a>Ressources

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>Collecter des informations de diagnostic

Si vous pouvez reproduire un problème, augmentez d’abord le niveau de journalisation, exécutez le système pendant un certain temps, puis rétablissez le niveau de journalisation par défaut.

1. Augmenter le niveau de journalisation :

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Reproduisez le problème.

3. Exécutez la commande suivante pour back up Defender for Endpoint’s logs. Les fichiers sont stockés dans une archive .zip de données.

   ```bash
   sudo mdatp diagnostic create
   ```

    Cette commande imprime également le chemin d’accès du fichier à la sauvegarde une fois l’opération réussie :

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

## <a name="log-installation-issues"></a>Journaux des problèmes d’installation

Si une erreur se produit lors de l’installation, le programme d’installation signale uniquement un échec général.

Le journal détaillé sera enregistré dans `/var/log/microsoft/mdatp/install.log` .
Si vous avez des problèmes lors de l’installation, envoyez-nous ce fichier afin que nous aidions à diagnostiquer la cause.

## <a name="uninstall"></a>Désinstaller

Il existe plusieurs façons de désinstaller Defender pour Endpoint sur Linux. Si vous utilisez un outil de configuration tel que l’Outil de configuration, suivez les instructions de désinstallation du package pour l’outil de configuration.

### <a name="manual-uninstallation"></a>Désinstallation manuelle

- `sudo yum remove mdatp` pour RHEL et les variantes (CentOS et Oracle Linux).
- `sudo zypper remove mdatp` pour SLES et les variantes.
- `sudo apt-get purge mdatp` pour les systèmes Ubuntu et Debian.

## <a name="configure-from-the-command-line"></a>Configurer à partir de la ligne de commande

Des tâches importantes, telles que le contrôle des paramètres du produit et le déclenchement d’analyses à la demande, peuvent être réalisées à partir de la ligne de commande.

### <a name="global-options"></a>Options globales

Par défaut, l’outil en ligne de commande produit le résultat dans un format lisible par l’homme. En outre, l’outil prend également en charge la sortie du résultat en tant que JSON, ce qui est utile pour les scénarios d’automatisation. Pour modifier la sortie en JSON, passez `--output json` à l’une des commandes ci-dessous.

### <a name="supported-commands"></a>Commandes prises en charge

Le tableau suivant répertorie les commandes pour certains des scénarios les plus courants. Exécutez `mdatp help` à partir du Terminal pour afficher la liste complète des commandes prise en charge.

<br>

****

|Group|Scénario|Commande|
|---|---|---|
|Configuration|Activer/désactiver la protection en temps réel|`mdatp config real-time-protection --value [enabled\|disabled]`|
|Configuration|Activer/désactiver la surveillance du comportement|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|Configuration|Activer/désactiver la protection cloud|`mdatp config cloud --value [enabled\|disabled]`|
|Configuration|Activer/désactiver les diagnostics de produit|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|Configuration|Activer/désactiver l’envoi automatique d’échantillons|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|Configuration|Activer/désactiver le mode passif antivirus|`mdatp config passive-mode --value [enabled\|disabled]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour une extension de fichier|`mdatp exclusion extension [add\|remove] --name [extension]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un fichier|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un répertoire|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|Configuration|Ajouter/supprimer une exclusion antivirus pour un processus|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|Configuration|Liste de toutes les exclusions antivirus|`mdatp exclusion list`|
|Configuration|Ajouter un nom de menace à la liste autorisée|`mdatp threat allowed add --name [threat-name]`|
|Configuration|Supprimer un nom de menace de la liste autorisée|`mdatp threat allowed remove --name [threat-name]`|
|Configuration|Liste de tous les noms de menaces autorisés|`mdatp threat allowed list`|
|Configuration|Activer la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|Configuration|Désactiver la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|Configuration|Activer le mode audit pour la protection PUA|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|Configuration|Configurer le degré de parallélisme pour les analyses à la demande|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Configuration|Activer/désactiver les analyses après les mises à jour des informations de sécurité|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Configuration|Activer/désactiver l’analyse d’archivage (analyses à la demande uniquement)|`mdatp config scan-archives --value [enabled/disabled]`|
|Diagnostics|Modifier le niveau de journal|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|Diagnostics|Générer des journaux de diagnostic|`mdatp diagnostic create --path [directory]`|
|Intégrité|Vérifier l’état du produit|`mdatp health`|
|Protection|Analyser un chemin d’accès|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Protection|Faire une analyse rapide|`mdatp scan quick`|
|Protection|Faire une analyse complète|`mdatp scan full`|
|Protection|Annuler une analyse à la demande en cours|`mdatp scan cancel`|
|Protection|Demander une mise à jour des informations de sécurité|`mdatp definitions update`|
|Historique de la protection|Imprimer l’historique complet de la protection|`mdatp threat list`|
|Historique de la protection|Obtenir les détails sur les menaces|`mdatp threat get --id [threat-id]`|
|Gestion de la mise en quarantaine|Liste de tous les fichiers mis en quarantaine|`mdatp threat quarantine list`|
|Gestion de la mise en quarantaine|Supprimer tous les fichiers de la quarantaine|`mdatp threat quarantine remove-all`|
|Gestion de la mise en quarantaine|Ajouter un fichier détecté comme une menace en quarantaine|`mdatp threat quarantine add --id [threat-id]`|
|Gestion de la mise en quarantaine|Supprimer de la quarantaine un fichier détecté comme une menace|`mdatp threat quarantine remove --id [threat-id]`|
|Gestion de la mise en quarantaine|Restaurer un fichier de la quarantaine|`mdatp threat quarantine restore --id [threat-id]`|
|Détection et réponse des points de terminaison|Définir la prévisualisation (inutilisée)|`mdatp edr early-preview [enable|disable]`|
|Détection et réponse des points de terminaison|Définir l’ID de groupe|`mdatp edr group-ids --group-id [group-id]`|
|Détection et réponse des points de terminaison|Définir/supprimer une balise, uniquement `GROUP` prise en charge|`mdatp edr tag set --name GROUP --value [tag]`|
|Détection et réponse des points de terminaison|Exclusions de listes (racine)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
