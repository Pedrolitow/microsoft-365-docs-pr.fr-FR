---
title: Ressources pour Microsoft Defender pour point de terminaison sur Mac
description: Ressources pour Microsoft Defender pour point de terminaison sur Mac, notamment comment le désinstaller, comment collecter des journaux de diagnostic, des commandes CLI et des problèmes connus avec le produit.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, déployer, désinstallation, intune, jamf, macos,pératin, mojave, high sierra
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
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2a4d588e869fed684c4424578025a50d36a2280e
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53650414"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>Ressources pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>Collecte d’informations de diagnostic

Si vous pouvez reproduire un problème, augmentez le niveau de journalisation, exécutez le système pendant un certain temps et rétablissez le niveau de journalisation par défaut.

1. Augmenter le niveau de journalisation :

   ```bash
   mdatp log level set --level verbose
   ```

   ```Output
   Log level configured successfully
   ```

2. Reproduire le problème

3. Exécutez `sudo mdatp diagnostic create` cette session pour enregistrer les journaux microsoft Defender pour les points de terminaison. Les fichiers sont stockés dans une archive .zip de données. Cette commande imprime également le chemin d’accès du fichier à la sauvegarde une fois l’opération réussie.

   > [!TIP]
   > Par défaut, les journaux de diagnostic sont enregistrés dans `/Library/Application Support/Microsoft/Defender/wdavdiag/` . Pour modifier le répertoire dans lequel les journaux de diagnostic sont enregistrés, passez à la commande ci-dessous, en remplaçant par le `--path [directory]` `[directory]` répertoire souhaité.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. Restaurer le niveau de journalisation :

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>Journalisation des problèmes d’installation

Si une erreur se produit lors de l’installation, le programme d’installation signale uniquement un échec général.

Le journal détaillé sera enregistré dans `/Library/Logs/Microsoft/mdatp/install.log` . Si vous avez des problèmes lors de l’installation, envoyez-nous ce fichier afin que nous aidions à diagnostiquer la cause.

## <a name="uninstalling"></a>Désinstallation

Il existe plusieurs façons de désinstaller Microsoft Defender pour Endpoint sur macOS. Notez que bien que la désinstallation gérée de manière centralisée soit disponible sur JAMF, elle n’est pas encore disponible pour les Microsoft Intune.

### <a name="interactive-uninstallation"></a>Désinstallation interactive

- Ouvrez **Finder > Applications.** Cliquez avec le bouton **droit sur Microsoft Defender pour le point de terminaison > déplacer vers la corbeille.**

### <a name="from-the-command-line"></a>À partir de la ligne de commande

- ```sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'```

## <a name="configuring-from-the-command-line"></a>Configuration à partir de la ligne de commande

Les tâches importantes, telles que le contrôle des paramètres du produit et le déclenchement d’analyses à la demande, peuvent être réalisées à partir de la ligne de commande :

|Group        |Scénario                                   |Commande                                                                           |
|-------------|-------------------------------------------|----------------------------------------------------------------------------------|
|Configuration|Activer/désactiver la protection en temps réel           |`mdatp config real-time-protection --value [enabled/disabled]`                    |
|Configuration|Activer/désactiver la protection cloud               |`mdatp config cloud --value [enabled/disabled]`                                   |
|Configuration|Activer/désactiver les diagnostics de produit            |`mdatp config cloud-diagnostic --value [enabled/disabled]`                        |
|Configuration|Activer/désactiver l’envoi automatique d’échantillons    |`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`       |
|Configuration|Ajouter un nom de menace à la liste autorisée      |`mdatp threat allowed add --name [threat-name]`                                   |
|Configuration|Supprimer un nom de menace de la liste autorisée |`mdatp threat allowed remove --name [threat-name]`                                |
|Configuration|Liste de tous les noms de menace autorisés              |`mdatp threat allowed list`                                                       |
|Configuration|Activer la protection PUA                     |`mdatp threat policy set --type potentially_unwanted_application -- action block` |
|Configuration|Désactiver la protection PUA                    |`mdatp threat policy set --type potentially_unwanted_application -- action off`   |
|Configuration|Activer le mode audit pour la protection PUA      |`mdatp threat policy set --type potentially_unwanted_application -- action audit` |
|Configuration|Activer/désactiver passiveMode                    |`mdatp config passive-mode --value enabled [enabled/disabled]`                    |
|Diagnostics  |Modifier le niveau de journal                       |`mdatp log level set --level [error/warning/info/verbose]`                        |
|Diagnostics  |Générer des journaux de diagnostic                   |`mdatp diagnostic create --path [directory]`                                      |
|Intégrité       |Vérifier l’état du produit                 |`mdatp health`                                                                    |
|Intégrité       |Vérifier l’attribut d’un produit de harpon       |`mdatp health --field [attribute: healthy/licensed/engine_version...]`            |
|Protection   |Analyser un chemin d’accès                                |`mdatp scan custom --path [path] [--ignore-exclusions]`                           |
|Protection   |Faire une analyse rapide                            |`mdatp scan quick`                                                                |
|Protection   |Faire une analyse complète                             |`mdatp scan full`                                                                 |
|Protection   |Annuler une analyse à la demande en cours           |`mdatp scan cancel`                                                               |
|Protection   |Demander une mise à jour de l’intelligence de la sécurité     |`mdatp definitions update`                                                        |
|PEPT          |Ajouter une balise de groupe à l’appareil. PEPT balises sont utilisées pour gérer les groupes d’appareils. Pour plus d’informations, visitez /microsoft-365/security/defender-endpoint/machine-groups |`mdatp edr tag set --name GROUP --value [name]` |
|PEPT          |Supprimer une balise de groupe de l’appareil               |`mdatp edr tag remove --tag-name [name]`                                          |
|PEPT          |Ajouter un ID de groupe                               |`mdatp edr group-ids --group-id [group]`                                          |

### <a name="how-to-enable-autocompletion"></a>Comment activer lacompletion automatique

Pour activer lacompletion automatique dans Bash, exécutez la commande suivante et redémarrez la session Terminal :

```bash
echo "source /Applications/Microsoft\ Defender\ ATP.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

Pour activer lacompletion automatique dans zsh :

- Vérifiez si lacompletion automatique est activée sur votre appareil :

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- Si la commande précédente ne produit aucune sortie, vous pouvez activer lacomplémentation automatique à l’aide de la commande suivante :

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- Exécutez les commandes suivantes pour activer lacompletion automatique pour Microsoft Defender pour Endpoint sur macOS et redémarrez la session Terminal :

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions
   ```
   ```zsh
   sudo ln -svf "/Applications/Microsoft Defender ATP.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>Répertoire de mise en quarantaine du client Microsoft Defender pour point de terminaison

`/Library/Application Support/Microsoft/Defender/quarantine/` contient les fichiers mis en quarantaine par `mdatp` . Les fichiers sont nommés d’après l’threat trackingId. Le trackingIds actuel est affiché avec `mdatp threat list` .

## <a name="microsoft-defender-for-endpoint-portal-information"></a>Informations du portail Microsoft Defender pour les points de terminaison

PEPT fonctionnalités pour [macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801)sont désormais arrivées, sur le blog Microsoft Defender pour endpoint, fournit des instructions détaillées sur ce à quoi vous devez vous attendre dans le Centre de sécurité Microsoft Defender pour Endpoint.
