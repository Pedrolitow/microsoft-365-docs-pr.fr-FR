---
title: Ressources Microsoft Defender ATP pour Linux
ms.reviewer: ''
description: Décrit les ressources pour Microsoft Defender ATP pour Linux, notamment comment le désinstaller, comment collecter les journaux de diagnostic, les commandes CLI et les problèmes connus avec le produit.
keywords: microsoft, defender, atp, linux, installation, déployer, désinstallation, casque, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a4f2324bc47bdee38e1cdeed1e21b5f9063e9a5c
ms.sourcegitcommit: 987f70e44e406ab6b1dd35f336a9d0c228032794
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2021
ms.locfileid: "51587063"
---
# <a name="resources"></a>Ressources

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-investigateip-abovefoldlink)

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

3. Exécutez la commande suivante pour back up Defender for Endpoint’s logs. Les fichiers sont stockés dans une archive .zip.

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

Le journal détaillé sera enregistré dans `/var/log/microsoft/mdatp_install.log` . Si vous avez des problèmes lors de l’installation, envoyez-nous ce fichier afin que nous aidions à diagnostiquer la cause.

## <a name="uninstall"></a>Uninstall

Il existe plusieurs façons de désinstaller Defender pour Endpoint pour Linux. Si vous utilisez un outil de configuration tel que l’Outil de configuration, suivez les instructions de désinstallation du package pour l’outil de configuration.

### <a name="manual-uninstallation"></a>Désinstallation manuelle

- `sudo yum remove mdatp` pour RHEL et ses variantes (CentOS et Oracle Linux).
- `sudo zypper remove mdatp` pour SLES et les variantes.
- `sudo apt-get purge mdatp` pour les systèmes Ubuntu et Debian.

## <a name="configure-from-the-command-line"></a>Configurer à partir de la ligne de commande

Des tâches importantes, telles que le contrôle des paramètres du produit et le déclenchement d’analyses à la demande, peuvent être réalisées à partir de la ligne de commande.

### <a name="global-options"></a>Options globales

Par défaut, l’outil en ligne de commande produit le résultat dans un format lisible par l’homme. En outre, l’outil prend également en charge la sortie du résultat en tant que JSON, ce qui est utile pour les scénarios d’automatisation. Pour modifier la sortie en JSON, passez `--output json` à l’une des commandes ci-dessous.

### <a name="supported-commands"></a>Commandes prise en charge

Le tableau suivant répertorie les commandes pour certains des scénarios les plus courants. Exécutez `mdatp help` à partir du Terminal pour afficher la liste complète des commandes prise en charge.

|Group                 |Scénario                                                |Commande                                                                |
|----------------------|--------------------------------------------------------|-----------------------------------------------------------------------|
|Configuration         |Activer/désactiver la protection en temps réel                        |`mdatp config real-time-protection --value [enabled\|disabled]`        |
|Configuration         |Activer/désactiver la surveillance du comportement                         |`mdatp config behavior-monitoring --value [enabled\|disabled]` 
|Configuration         |Activer/désactiver la protection cloud                            |`mdatp config cloud --value [enabled\|disabled]`                       |
|Configuration         |Activer/désactiver les diagnostics de produit                         |`mdatp config cloud-diagnostic --value [enabled\|disabled]`            |
|Configuration         |Activer/désactiver l’envoi automatique d’échantillons                 |`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`   |
|Configuration         |Activer/désactiver le mode passif antivirus                             |`mdatp config passive-mode --value [enabled\|disabled]`                |
|Configuration         |Ajouter/supprimer une exclusion antivirus pour une extension de fichier  |`mdatp exclusion extension [add\|remove] --name [extension]`           |
|Configuration         |Ajouter/supprimer une exclusion antivirus pour un fichier            |`mdatp exclusion file [add\|remove] --path [path-to-file]`             |
|Configuration         |Ajouter/supprimer une exclusion antivirus pour un répertoire       |`mdatp exclusion folder [add\|remove] --path [path-to-directory]`      |
|Configuration         |Ajouter/supprimer une exclusion antivirus pour un processus         |`mdatp exclusion process [add\|remove] --path [path-to-process]`<br/>`mdatp exclusion process [add\|remove] --name [process-name]` |
|Configuration         |Liste de toutes les exclusions antivirus                           |`mdatp exclusion list`                                                 |
|Configuration         |Ajouter un nom de menace à la liste autorisée                   |`mdatp threat allowed add --name [threat-name]`                        |
|Configuration         |Supprimer un nom de menace de la liste autorisée              |`mdatp threat allowed remove --name [threat-name]`                     |
|Configuration         |Liste de tous les noms de menace autorisés                           |`mdatp threat allowed list`                                            |
|Configuration         |Activer la protection PUA                                  |`mdatp threat policy set --type potentially_unwanted_application --action block` |
|Configuration         |Désactiver la protection PUA                                 |`mdatp threat policy set --type potentially_unwanted_application --action off` |
|Configuration         |Activer le mode audit pour la protection PUA                   |`mdatp threat policy set --type potentially_unwanted_application --action audit` |
|Diagnostics           |Modifier le niveau de journal                                    |`mdatp log level set --level verbose [error|warning|info|verbose]`     |
|Diagnostics           |Générer des journaux de diagnostic                                |`mdatp diagnostic create --path [directory]`                           |
|Intégrité                |Vérifier l’état du produit                              |`mdatp health`                                                         |
|Protection            |Analyser un chemin d’accès                                             |`mdatp scan custom --path [path] [--ignore-exclusions]`                |
|Protection            |Faire une analyse rapide                                         |`mdatp scan quick`                                                     |
|Protection            |Faire une analyse complète                                          |`mdatp scan full`                                                      |
|Protection            |Annuler une analyse à la demande en cours                        |`mdatp scan cancel`                                                    |
|Protection            |Demander une mise à jour de l’intelligence de la sécurité                  |`mdatp definitions update`                                             |
|Historique de la protection    |Imprimer l’historique complet de la protection                       |`mdatp threat list`                                                    |
|Historique de la protection    |Obtenir les détails sur les menaces                                      |`mdatp threat get --id [threat-id]`                                    |
|Gestion de la mise en quarantaine |Liste de tous les fichiers mis en quarantaine                              |`mdatp threat quarantine list`                                         |
|Gestion de la mise en quarantaine |Supprimer tous les fichiers de la quarantaine                    |`mdatp threat quarantine remove-all`                                   |
|Gestion de la mise en quarantaine |Ajouter un fichier détecté comme une menace en quarantaine       |`mdatp threat quarantine add --id [threat-id]`                         |
|Gestion de la mise en quarantaine |Supprimer de la quarantaine un fichier détecté comme une menace  |`mdatp threat quarantine remove --id [threat-id]`                      |
|Gestion de la mise en quarantaine |Restaurer un fichier de la quarantaine                      |`mdatp threat quarantine restore --id [threat-id]`                     |
|Détection et réponse des points de terminaison |Définir la prévisualisation (inutilisée)                    |`mdatp edr early-preview [enable|disable]`                             |
|Détection et réponse des points de terminaison |Définir l’ID de groupe                                  |`mdatp edr group-ids --group-id [group-id]`                            |
|Détection et réponse des points de terminaison |Balise Set/Remove uniquement `GROUP` prise en charge        |`mdatp edr tag set --name GROUP --value [tag]`                         |
|Détection et réponse des points de terminaison |exclusions de liste (racine)                        |`mdatp edr exclusion list [processes|paths|extensions|all]`            |

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Informations du portail Microsoft Defender pour les points de terminaison

Dans le portail Defender pour points de terminaison, deux catégories d’informations s’offrent à vous :

- Alertes antivirus, notamment :
  - Severity
  - Type d’analyse
  - Informations sur l’appareil (nom d’hôte, identificateur d’appareil, identificateur client, version de l’application et type de système d’exploitation)
  - Informations sur le fichier (nom, chemin d’accès, taille et hachage)
  - Informations sur les menaces (nom, type et état)
- Informations sur l’appareil, notamment :
  - Identificateur d’appareil
  - Identificateur de client
  - Version de l’application.
  - Nom d'hôte
  - Type de système d’exploitation
  - Version du système d’exploitation
  - Modèle ordinateur
  - Architecture du processeur
  - Si l’appareil est une machine virtuelle

### <a name="known-issues"></a>Problèmes connus

- Vous pouvez voir « Aucune donnée de capteur, communications altérées » dans la page d’informations de l’ordinateur du portail centre de sécurité Microsoft Defender, même si le produit fonctionne comme prévu. Nous travaillons à la résoudre.
- Les utilisateurs connectés n’apparaissent pas dans le portail centre de sécurité Microsoft Defender.
- Dans les distributions SUSE, si l’installation de *libatomic1* échoue, vous devez vérifier que votre système d’exploitation est enregistré :

   ```bash
   sudo SUSEConnect --status-text
   ```
