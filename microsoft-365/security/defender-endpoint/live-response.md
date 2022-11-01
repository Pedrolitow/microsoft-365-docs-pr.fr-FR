---
title: Examiner les entités sur les appareils à l’aide de la réponse en direct dans Microsoft Defender pour point de terminaison
description: Accédez à un appareil à l’aide d’une connexion shell à distance sécurisée pour effectuer un travail d’investigation et prendre des mesures de réponse immédiates sur un appareil en temps réel.
keywords: remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 075d32e8a7e24bf688902f919ec926edcd26344b
ms.sourcegitcommit: 4bae15909267a70c8842bd0cd3dceb8459b4cc29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68798384"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Examiner les entités sur les appareils à l’aide de la réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

La réponse en direct permet aux équipes des opérations de sécurité d’accéder instantanément à un appareil (également appelé machine) à l’aide d’une connexion shell à distance. Cela vous donne le pouvoir d’effectuer un travail d’investigation approfondi et de prendre des mesures d’intervention immédiates pour contenir rapidement les menaces identifiées en temps réel.

La réponse en direct est conçue pour améliorer les enquêtes en permettant à votre équipe des opérations de sécurité de collecter des données d’investigation, d’exécuter des scripts, d’envoyer des entités suspectes à des fins d’analyse, de corriger les menaces et de rechercher de manière proactive les menaces émergentes.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Avec la réponse en direct, les analystes peuvent effectuer toutes les tâches suivantes :

- Exécutez des commandes de base et avancées pour effectuer un travail d’investigation sur un appareil.
- Téléchargez des fichiers tels que des exemples de programmes malveillants et les résultats des scripts PowerShell.
- Téléchargez les fichiers en arrière-plan (nouveau !).
- Chargez un script PowerShell ou un exécutable dans la bibliothèque et exécutez-le sur un appareil à partir d’un niveau client.
- Effectuer ou annuler des actions de correction.

## <a name="before-you-begin"></a>Avant de commencer

Avant de pouvoir lancer une session sur un appareil, vérifiez que vous remplissez les conditions suivantes :

- **Vérifiez que vous exécutez une version prise en charge de Windows**.

  Les appareils doivent exécuter l’une des versions suivantes de Windows

  - **11 Windows 10 &**
    - [Version 1909](/windows/whats-new/whats-new-windows-10-version-1909) ou ultérieure
    - [Version 1903](/windows/whats-new/whats-new-windows-10-version-1903) avec [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) avec [kb4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) avec [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) avec [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** : applicable uniquement pour la préversion publique, version minimale requise : 101.43.84. Pris en charge pour les appareils MacOS Basés sur Intel et ARM

  - **Linux** - Applicable uniquement pour la préversion publique, version minimale requise : 101.45.13

  - **Windows Server 2012 R2** - avec [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2016** - avec [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Version 1903 ou (avec [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) ultérieure
    - Version 1809 (avec [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))

  - **Windows Server 2022**

- **Activez la réponse en direct à partir de la page des paramètres avancés**.

  Vous devez activer la fonctionnalité de réponse en direct dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

  > [!NOTE]
  > Seuls les administrateurs et les utilisateurs disposant des autorisations « Gérer les paramètres du portail » peuvent activer la réponse en direct. 
  >
  > L’investigation automatisée doit être activée dans les [paramètres Fonctionnalités avancées](advanced-features.md) avant d’activer la réponse en direct.

- **Activez la réponse en direct pour les serveurs à partir de la page des paramètres avancés** (recommandé).

  > [!NOTE]
  > Seuls les administrateurs et les utilisateurs disposant des autorisations « Gérer les paramètres du portail » peuvent activer la réponse en direct.

- **Vérifiez qu’un niveau de correction Automation est affecté à l’appareil**.

  Vous devez activer au moins le niveau de correction minimal pour un groupe d’appareils donné. Sinon, vous ne serez pas en mesure d’établir une session De réponse dynamique à un membre de ce groupe.
  > [!NOTE]
  > La création d’un groupe d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2. 

  Vous recevez l’erreur suivante :

  :::image type="content" source="images/live-response-error.png" alt-text="Message d’erreur" lightbox="images/live-response-error.png":::

- **Activer l’exécution de script non signé de réponse en direct** (facultatif).

  >[!IMPORTANT]
  >La vérification de signature s’applique uniquement aux scripts PowerShell.

  > [!WARNING]
  > Autoriser l’utilisation de scripts non signés peut augmenter votre exposition aux menaces.

  L’exécution de scripts non signés n’est pas recommandée, car cela peut augmenter votre exposition aux menaces. Toutefois, si vous devez les utiliser, vous devez activer le paramètre dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

- **Vérifiez que vous disposez des autorisations appropriées**.

  Seuls les utilisateurs qui ont été approvisionnés avec les autorisations appropriées peuvent lancer une session. Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

  > [!IMPORTANT]
  > L’option de chargement d’un fichier dans la bibliothèque est disponible uniquement pour les utilisateurs disposant de l’autorisation « Gérer les paramètres de sécurité ».
  > Le bouton est grisé pour les utilisateurs disposant uniquement d’autorisations déléguées.

  Selon le rôle qui vous a été accordé, vous pouvez exécuter des commandes de réponse en direct de base ou avancées. Les autorisations des utilisateurs sont contrôlées par le rôle personnalisé RBAC.

## <a name="live-response-dashboard-overview"></a>Vue d’ensemble du tableau de bord des réponses en direct

Lorsque vous lancez une session de réponse en direct sur un appareil, un tableau de bord s’ouvre. Le tableau de bord fournit des informations sur la session, telles que les suivantes :

- Qui a créé la session
- Quand la session a démarré
- Durée de la session

Le tableau de bord vous donne également accès aux éléments suivants :

- Inscription de l’application dans Azure Active Directory
- Charger des fichiers dans la bibliothèque
- Console de commandes
- Journal des commandes

## <a name="initiate-a-live-response-session-on-a-device"></a>Lancer une session de réponse en direct sur un appareil

1. Connectez-vous à Microsoft 365 Defender portail.

2. Accédez à **Points de terminaison > Inventaire des appareils** et sélectionnez un appareil à examiner. La page appareils s’ouvre.

3. Lancez la session de réponse en direct en sélectionnant **Lancer la session de réponse en direct**. Une console de commande s’affiche. Attendez que la session se connecte à l’appareil.

4. Utilisez les commandes intégrées pour effectuer un travail d’investigation. Pour plus d’informations, consultez [Commandes de réponse en direct](#live-response-commands).

5. Une fois votre investigation terminée, sélectionnez **Déconnecter la session**, puis **sélectionnez Confirmer**.

## <a name="live-response-commands"></a>Commandes de réponse en direct

Selon le rôle qui vous a été accordé, vous pouvez exécuter des commandes de réponse en direct de base ou avancées. Les autorisations utilisateur sont contrôlées par les rôles personnalisés RBAC. Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

> [!NOTE]
> La réponse en direct est un interpréteur de commandes interactif basé sur le cloud. Par conséquent, l’expérience de commande spécifique peut varier en fonction de la qualité du réseau et de la charge du système entre l’utilisateur final et l’appareil cible.

### <a name="basic-commands"></a>Commandes de base

Les commandes suivantes sont disponibles pour les rôles d’utilisateur qui ont la possibilité d’exécuter des commandes de réponse dynamique **de base** . Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

| Command  | Description  | Windows et Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| Cd  | Modifie le répertoire actif.  | v  | v  | v  |
| Cls  | Efface l’écran de la console.  | v  | v  | v  |
| connect  | Lance une session de réponse en direct sur l’appareil.  | v  | v  | v  |
| Connexions  | Affiche toutes les connexions actives.  | v  | N  | N  |
| Dir  | Affiche une liste de fichiers et de sous-répertoires dans un répertoire.  | v  | v  | v  |
| Pilotes  | Affiche tous les pilotes installés sur l’appareil.  | v  | N  | N  |
| Fg `<command ID>`  | Placez le travail spécifié au premier plan, ce qui en fait le travail actuel.  REMARQUE : fg prend un « ID de commande » disponible à partir des travaux, et non un PID  | v  | v  | v  |
| Fileinfo  | Récupération d’informations sur un fichier.  | v  | v  | v  |
| findfile  | Localise les fichiers par un nom donné sur l’appareil.  | v  | v  | v  |
| <file_path> getfile  | Télécharge un fichier.  | v  | v  | v  |
| Aide  | Fournit des informations d’aide pour les commandes de réponse en direct.  | v  | v  | v  |
| tâches  | Affiche les travaux en cours d’exécution, leur ID et leur état.  | v  | v  | v  |
| Persistance  | Affiche toutes les méthodes de persistance connues sur l’appareil.  | v  | N  | N  |
| Processus  | Affiche tous les processus en cours d’exécution sur l’appareil.  | v  | v  | v  |
| registre  | Affiche les valeurs de Registre.  | v  | N  | N  |
| scheduledtasks  | Affiche toutes les tâches planifiées sur l’appareil.  | v  | N  | N  |
| Services  | Affiche tous les services sur l’appareil.  | v  | N  | N  |
| startupfolders  | Affiche tous les fichiers connus dans les dossiers de démarrage sur l’appareil.  | v  | N  | N  |
| status  | Affiche l’état et la sortie d’une commande spécifique.  | v  | N  | N  |
| Trace  | Définit le mode de journalisation du terminal pour déboguer.  | v  | v  | v  |

### <a name="advanced-commands"></a>Commandes avancées

Les commandes suivantes sont disponibles pour les rôles d’utilisateur qui ont la possibilité d’exécuter des commandes de réponse dynamique **avancées** . Pour plus d’informations sur les attributions de rôles, consultez [Créer et gérer des rôles](user-roles.md).

| Command  | Description  | Windows et Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| Analyser  | Analyse l’entité avec différents moteurs d’incrimination pour parvenir à un verdict.  | v  | N  | N  |
| Recueillir  | Collecte le package d’investigation à partir de la machine  | N  | v  | v  |
| Isoler  | Déconnecte l’appareil du réseau tout en conservant la connectivité au service Defender pour point de terminaison  | N  | v  | N  |
| Libération  | Libère un appareil de l’isolement réseau  | N  | v  | N  |
| Courir  | Exécute un script PowerShell à partir de la bibliothèque sur l’appareil.  | v  | v  | v  |
| Bibliothèque  | Répertorie les fichiers qui ont été chargés dans la bibliothèque de réponses en direct.  | v  | v  | v  |
| Putfile  | Place un fichier de la bibliothèque sur l’appareil. Les fichiers sont enregistrés dans un dossier de travail et sont supprimés lorsque l’appareil redémarre par défaut.  | v  | v  | v  |
| corriger  | Corrige une entité sur l’appareil. L’action de correction varie en fonction du type d’entité : Fichier : supprimer Processus : arrêter, supprimer le fichier image Service : arrêter, supprimer le fichier image Entrée du registre : supprimer tâche planifiée : supprimer l’élément dossier de démarrage : supprimer le fichier REMARQUE : cette commande a une commande prérequise. Vous pouvez utiliser la commande -auto conjointement avec remediate pour exécuter automatiquement la commande requise.  | v  | v  | v  |
| numériser | Exécute une analyse antivirus pour aider à identifier et corriger les programmes malveillants. | N | v | v |
| Annuler  | Restaure une entité qui a été corrigée.  | v  | v  | v  |

## <a name="use-live-response-commands"></a>Utiliser des commandes de réponse dynamique

Les commandes que vous pouvez utiliser dans la console suivent des principes similaires à ceux [des commandes Windows](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

Les commandes avancées offrent un ensemble plus robuste d’actions qui vous permettent d’effectuer des actions plus puissantes telles que télécharger et charger un fichier, exécuter des scripts sur l’appareil et effectuer des actions de correction sur une entité.

### <a name="get-a-file-from-the-device"></a>Obtenir un fichier à partir de l’appareil

Pour les scénarios où vous souhaitez obtenir un fichier à partir d’un appareil que vous examinez, vous pouvez utiliser la `getfile` commande . Cela vous permet d’enregistrer le fichier à partir de l’appareil pour une investigation plus approfondie.

> [!NOTE]
> Les limites de taille de fichier suivantes s’appliquent :
>
> - `getfile` limite : 3 Go
> - `fileinfo` limite : 30 Go
> - `library` limite : 250 Mo

### <a name="download-a-file-in-the-background"></a>Télécharger un fichier en arrière-plan

Pour permettre à votre équipe des opérations de sécurité de continuer à examiner un appareil affecté, les fichiers peuvent désormais être téléchargés en arrière-plan.

- Pour télécharger un fichier en arrière-plan, dans la console de commande de réponse dynamique, tapez `download <file_path> &`.
- Si vous attendez qu’un fichier soit téléchargé, vous pouvez le déplacer en arrière-plan à l’aide de Ctrl + Z.
- Pour mettre un fichier téléchargé au premier plan, dans la console de commande de réponse en direct, tapez `fg <command_id>`.

Voici quelques exemples :

<br>

****

|Commande|Ce qu'il fait|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Démarre le téléchargement d’un fichier nommé *some_file.exe* en arrière-plan.|
|`fg 1234`|Retourne un téléchargement avec l’ID de commande *1234* au premier plan.|
|

### <a name="put-a-file-in-the-library"></a>Placer un fichier dans la bibliothèque

La réponse en direct dispose d’une bibliothèque dans laquelle vous pouvez placer des fichiers. La bibliothèque stocke les fichiers (tels que les scripts) qui peuvent être exécutés dans une session de réponse dynamique au niveau du locataire.

La réponse dynamique permet aux scripts PowerShell de s’exécuter, mais vous devez d’abord placer les fichiers dans la bibliothèque avant de pouvoir les exécuter.

Vous pouvez disposer d’une collection de scripts PowerShell qui peuvent s’exécuter sur les appareils avec lesquels vous lancez des sessions de réponse en direct.

#### <a name="to-upload-a-file-in-the-library"></a>Pour charger un fichier dans la bibliothèque

1. Cliquez sur **Charger le fichier dans la bibliothèque**.

2. Cliquez sur **Parcourir** et sélectionnez le fichier.

3. Fournissez une brève description.

4. Spécifiez si vous souhaitez remplacer un fichier portant le même nom.

5. Si vous le souhaitez, sachez quels paramètres sont nécessaires pour le script, cochez la case Paramètres du script. Dans le champ de texte, entrez un exemple et une description.

6. Cliquez sur **Confirmer**.

7. (Facultatif) Pour vérifier que le fichier a été chargé dans la bibliothèque, exécutez la `library` commande .

### <a name="cancel-a-command"></a>Annuler une commande

À tout moment pendant une session, vous pouvez annuler une commande en appuyant sur Ctrl +C.

> [!WARNING]
> L’utilisation de ce raccourci n’arrête pas la commande côté agent. Elle annule uniquement la commande dans le portail. Par conséquent, la modification des opérations telles que « corriger » peut continuer, pendant que la commande est annulée.

## <a name="run-a-script"></a>Exécuter un script

Avant de pouvoir exécuter un script PowerShell/Bash, vous devez d’abord le charger dans la bibliothèque.

Après avoir chargé le script dans la bibliothèque, utilisez la `run` commande pour exécuter le script.

Si vous envisagez d’utiliser un script PowerShell non signé dans la session, vous devez activer le paramètre dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

> [!WARNING]
> Autoriser l’utilisation de scripts non signés peut augmenter votre exposition aux menaces.

## <a name="apply-command-parameters"></a>Appliquer des paramètres de commande

- Consultez l’aide de la console pour en savoir plus sur les paramètres de commande. Pour en savoir plus sur une commande individuelle, exécutez :

  ```powershell
  help <command name>
  ```

- Lorsque vous appliquez des paramètres à des commandes, notez que les paramètres sont gérés selon un ordre fixe :

  ```powershell
  <command name> param1 param2
  ```

- Lorsque vous spécifiez des paramètres en dehors de l’ordre fixe, spécifiez le nom du paramètre avec un trait d’union avant de fournir la valeur :

  ```powershell
  <command name> -param2_name param2
  ```

- Lorsque vous utilisez des commandes qui ont des commandes requises, vous pouvez utiliser des indicateurs :

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  ou

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Types de sortie pris en charge

La réponse en direct prend en charge les types de sortie au format table et JSON. Pour chaque commande, il existe un comportement de sortie par défaut. Vous pouvez modifier la sortie dans votre format de sortie préféré à l’aide des commandes suivantes :

- `-output json`
- `-output table`

> [!NOTE]
> Moins de champs sont affichés au format tableau en raison de l’espace limité. Pour afficher plus de détails dans la sortie, vous pouvez utiliser la commande de sortie JSON afin que d’autres détails soient affichés.

## <a name="supported-output-pipes"></a>Canaux de sortie pris en charge

La réponse en direct prend en charge le piping de sortie vers l’interface CLI et le fichier. L’interface CLI est le comportement de sortie par défaut. Vous pouvez diriger la sortie vers un fichier à l’aide de la commande suivante : [command] > [filename].txt.

Exemple :

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Afficher le journal des commandes

Sélectionnez l’onglet **Journal des** commandes pour afficher les commandes utilisées sur l’appareil pendant une session. Chaque commande fait l’objet d’un suivi avec des détails complets tels que :

- ID
- Ligne de commande
- Durée
- État et barre latérale d’entrée ou de sortie

## <a name="limitations"></a>Limites

- Les sessions de réponse en direct sont limitées à 25 sessions de réponse en direct à la fois.
- La valeur du délai d’expiration inactif de la session de réponse en direct est de 30 minutes.
- Les commandes de réponse en direct individuelles ont une limite de temps de 10 minutes, à l’exception de `getfile`, `findfile`et `run`, qui ont une limite de 30 minutes.
- Un utilisateur peut lancer jusqu’à 10 sessions simultanées.
- Un appareil ne peut se trouver que dans une seule session à la fois.
- Les limites de taille de fichier suivantes s’appliquent :
  - `getfile` limite : 3 Go
  - `fileinfo` limite : 30 Go
  - `library` limite : 250 Mo

## <a name="related-article"></a>Article connexe

- [Exemples de commande Live response](live-response-command-examples.md)
