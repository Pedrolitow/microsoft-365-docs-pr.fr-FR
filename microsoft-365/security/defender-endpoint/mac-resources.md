---
title: Ressources pour Microsoft Defender pour point de terminaison sur Mac
description: Ressources pour Microsoft Defender pour point de terminaison sur Mac, notamment comment le désinstaller, comment collecter les journaux de diagnostic, les commandes CLI et les problèmes connus liés au produit.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, déployer, désinstallation, intune, jamf, macos, catalina, big sur, monterey, ventura, mde pour mac
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
ms.openlocfilehash: a9c853b2a4728a0174f4831ccff965021b1e279b
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68767807"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>Ressources pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>Collecte des informations de diagnostic

Si vous pouvez reproduire un problème, augmentez le niveau de journalisation, exécutez le système pendant un certain temps et restaurez le niveau de journalisation par défaut.

1. Augmenter le niveau de journalisation :

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. Reproduire le problème

3. Exécutez `sudo mdatp diagnostic create` pour sauvegarder les journaux Microsoft Defender pour point de terminaison. Les fichiers seront stockés dans une archive .zip. Cette commande affiche également le chemin d’accès du fichier à la sauvegarde une fois l’opération réussie.

   > [!TIP]
   > Par défaut, les journaux de diagnostic sont enregistrés dans `/Library/Application Support/Microsoft/Defender/wdavdiag/`. Pour modifier le répertoire dans lequel les journaux de diagnostic sont enregistrés `--path [directory]` , passez à la commande ci-dessous, en remplaçant par `[directory]` le répertoire souhaité.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. Niveau de journalisation de restauration :

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>Problèmes d’installation de journalisation

Si une erreur se produit pendant l’installation, le programme d’installation signale uniquement une défaillance générale.

Le journal détaillé sera enregistré dans `/Library/Logs/Microsoft/mdatp/install.log`. Si vous rencontrez des problèmes lors de l’installation, envoyez-nous ce fichier afin que nous puissions vous aider à diagnostiquer la cause.

## <a name="uninstalling"></a>Désinstallation

Il existe plusieurs façons de désinstaller Microsoft Defender pour point de terminaison sur macOS. Notez que si la désinstallation gérée de manière centralisée est disponible sur JAMF, elle n’est pas encore disponible pour Microsoft Intune.

### <a name="interactive-uninstallation"></a>Désinstallation interactive

- Ouvrez **Finder > Applications**. Cliquez avec le bouton droit sur **Microsoft Defender pour point de terminaison > Déplacer vers la Corbeille**.

### <a name="supported-output-types"></a>Types de sortie pris en charge

Prend en charge les types de sortie au format table et JSON. Pour chaque commande, il existe un comportement de sortie par défaut. Vous pouvez modifier la sortie dans votre format de sortie préféré à l’aide des commandes suivantes :

`-output json`

`-output table`

### <a name="from-the-command-line"></a>À partir de la ligne de commande

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>Configuration à partir de la ligne de commande

Les tâches importantes, telles que le contrôle des paramètres du produit et le déclenchement d’analyses à la demande, peuvent être effectuées à partir de la ligne de commande :

|Group|Scénario|Commande|
|---|---|---|
|Configuration|Activer/désactiver la protection en temps réel|`mdatp config real-time-protection --value [enabled/disabled]`|
|Configuration|Activer/désactiver la protection cloud|`mdatp config cloud --value [enabled/disabled]`|
|Configuration|Activer/désactiver les diagnostics de produit|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|Configuration|Activer/désactiver l’envoi automatique d’exemples|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|Configuration|Ajouter un nom de menace à la liste autorisée|`mdatp threat allowed add --name [threat-name]`|
|Configuration|Supprimer un nom de menace de la liste autorisée|`mdatp threat allowed remove --name [threat-name]`|
|Configuration|Répertorier tous les noms de menaces autorisés|`mdatp threat allowed list`|
|Configuration|Activer la protection puA|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|Configuration|Désactiver la protection puA|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|Configuration|Activer le mode d’audit pour la protection puA|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|Configuration|Activer/désactiver le mode passif antivirus|`mdatp config passive-mode --value [enabled/disabled]`|
|Configuration|Configurer le degré de parallélisme pour les analyses à la demande|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|Configuration|Activer/désactiver les analyses après les mises à jour du renseignement de sécurité|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|Configuration|Activer/désactiver l’analyse des archives (analyses à la demande uniquement)|`mdatp config scan-archives --value [enabled/disabled]`|
|Configuration|Activer/désactiver le calcul de hachage de fichier|`mdatp config enable-file-hash-computation --value [enabled/disabled]`|
|Configuration|Activer/désactiver data_loss_prevention|`mdatp config data_loss_prevention --value [enabled/disabled]`|
|Diagnostics|Modifier le niveau du journal|`mdatp log level set --level [error/warning/info/verbose]`|
|Diagnostics|Générer des journaux de diagnostic|`mdatp diagnostic create --path [directory]`|
|Intégrité|Vérifier l’intégrité du produit|`mdatp health`|
|Intégrité|Rechercher un attribut de produit spefic|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|Protection|Analyser un chemin d’accès|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|Protection|Effectuer une analyse rapide|`mdatp scan quick`|
|Protection|Effectuer une analyse complète|`mdatp scan full`|
|Protection|Annuler une analyse à la demande en cours|`mdatp scan cancel`|
|Protection|Demander une mise à jour du renseignement de sécurité|`mdatp definitions update`|
|EDR|Définir/supprimer une balise, uniquement GROUP pris en charge|`mdatp edr tag set --name GROUP --value [name]`|
|EDR|Supprimer l’étiquette de groupe de l’appareil|`mdatp edr tag remove --tag-name [name]`|
|EDR|Ajouter un ID de groupe|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>Comment activer l’autocompletion

Pour activer la saisie semi-automatique dans bash, exécutez la commande suivante et redémarrez la session Terminal :

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

Pour activer la saisie semi-automatique dans zsh :

- Vérifiez si l’autocomplétion est activée sur votre appareil :

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- Si la commande précédente ne produit aucune sortie, vous pouvez activer la saisie semi-automatique à l’aide de la commande suivante :

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- Exécutez les commandes suivantes pour activer la saisie automatique pour Microsoft Defender pour point de terminaison sur macOS et redémarrez la session Terminal :

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>Répertoire de mise en quarantaine du client Microsoft Defender pour point de terminaison

`/Library/Application Support/Microsoft/Defender/quarantine/` contient les fichiers mis en quarantaine par `mdatp`. Les fichiers sont nommés d’après l’Id de suivi des menaces. Les trackingIds actuels sont affichés avec `mdatp threat list`.

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Microsoft Defender pour point de terminaison les informations du portail

Les [fonctionnalités EDR pour macOS sont maintenant arrivées](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801), sur le blog Microsoft Defender pour point de terminaison, fournit des instructions détaillées sur ce à quoi s’attendre dans Microsoft Defender pour point de terminaison Security Center.
