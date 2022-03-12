---
title: Examiner les entités sur les appareils à l’aide de la réponse en direct dans Microsoft Defender pour le point de terminaison
description: Accéder à un appareil à l’aide d’une connexion shell distante sécurisée pour faire des enquêtes et prendre des mesures de réponse immédiates sur un appareil en temps réel.
keywords: remote, shell, connection, live, response, real-time, command, script, remediate, hunt, export, log, drop, download, file,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 882454e00517624c3bc43e87308007b00ece9507
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63449717"
---
# <a name="investigate-entities-on-devices-using-live-response"></a>Examiner les entités sur les appareils à l’aide de la réponse en direct

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

La réponse en direct permet aux équipes d’opérations de sécurité d’accéder instantanément à un appareil (également appelé ordinateur) à l’aide d’une connexion Shell distante. Cela vous donne la puissance d’un travail d’examen approfondi et d’actions de réponse immédiates pour contenir rapidement les menaces identifiées en temps réel.

La réponse dynamique est conçue pour améliorer les enquêtes en permettant à votre équipe des opérations de sécurité de collecter des données d’investigation, d’exécuter des scripts, d’envoyer des entités suspectes pour analyse, de corriger les menaces et de chercher de manière proactive les menaces émergentes.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUW]

Avec la réponse en direct, les analystes peuvent effectuer toutes les tâches suivantes :

- Exécutez des commandes de base et avancées pour faire des investigations sur un appareil.
- Téléchargez des fichiers tels que des exemples de programmes malveillants et les résultats des scripts PowerShell.
- Téléchargez des fichiers en arrière-plan (nouveau !).
- Télécharger script PowerShell ou exécutable dans la bibliothèque et exécutez-le sur un appareil à partir d’un niveau client.
- Prendre ou annuler des actions de correction.

## <a name="before-you-begin"></a>Avant de commencer

Avant de lancer une session sur un appareil, veillez à respecter les conditions suivantes :

- **Vérifiez que vous exécutez une version prise en charge de Windows**.

  Les appareils doivent être en cours d’exécution dans l’une des versions suivantes Windows

  - **Windows 10 & 11**
    - [Version 1909 ou](/windows/whats-new/whats-new-windows-10-version-1909) ultérieure
    - [Version 1903 avec](/windows/whats-new/whats-new-windows-10-version-1903) [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) avec [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) avec [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) avec [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **macOS** : applicable uniquement pour la prévisualisation publique, version minimale requise : 101.43.84 
  
   > [!NOTE]
   > Actuellement, seuls les systèmes MacOS Intel sont pris en charge.
    

  - **Linux** : applicable uniquement pour la prévisualisation publique, version minimale requise : 101.45.13 
    
  - **Windows Server 2012 R2** - avec [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)
  
  - **Windows Server 2016** - avec [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac)

  - **Windows Server 2019**
    - Version 1903 ou (avec [KB4515384) ultérieure](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - Version 1809 ( [avec KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

       

- **Activez la réponse en direct à partir de la page paramètres avancés**.

  Vous devez activer la fonctionnalité de réponse en direct dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

  > [!NOTE]
  > Seuls les utilisateurs  ayant des rôles d’administrateur global ou de sécurité peuvent modifier ces paramètres.
  > 
  > L’examen automatisé doit être activé dans les [paramètres des fonctionnalités](advanced-features.md) avancées avant d’activer la réponse en direct.

- **Activez la réponse en direct pour les serveurs à partir de la page paramètres avancés** (recommandé).

  > [!NOTE]
  > Seuls les utilisateurs  ayant des rôles d’administrateur global ou de sécurité peuvent modifier ces paramètres.

- **Assurez-vous qu’un niveau de correction Automation est affecté à l’appareil**.

  Vous devez activer, au moins, le niveau de correction minimal pour un groupe d’appareils donné. Sinon, vous ne pourrez pas établir une session Live Response à un membre de ce groupe.

  Vous recevrez l’erreur suivante :

  ![Image du message d’erreur.](images/live-response-error.png)

- **Activer l’exécution de scripts non signés de réponse en** direct (facultatif).

  >[!IMPORTANT]
  >La vérification des signatures s’applique uniquement aux scripts PowerShell. 

  > [!WARNING]
  > Autoriser l’utilisation de scripts non signés peut augmenter votre exposition aux menaces.

  L’exécution de scripts non signés n’est pas recommandée, car elle peut augmenter votre exposition aux menaces. Si vous devez toutefois les utiliser, vous devez activer le paramètre dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

- **Assurez-vous que vous avez les autorisations appropriées**.

  Seuls les utilisateurs qui ont été mis en service avec les autorisations appropriées peuvent lancer une session. Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles](user-roles.md).

  > [!IMPORTANT]
  > L’option de téléchargement d’un fichier dans la bibliothèque est uniquement disponible pour les utilisateurs  ayant l’autorisation « Gérer Paramètres sécurité ».
  > Le bouton est grisé pour les utilisateurs qui n’ont que des autorisations déléguées.

  Selon le rôle qui vous a été accordé, vous pouvez exécuter des commandes de réponse en direct de base ou avancées. Les autorisations des utilisateurs sont contrôlées par le rôle personnalisé RBAC.

## <a name="live-response-dashboard-overview"></a>Vue d’ensemble du tableau de bord de réponse en direct

Lorsque vous lancez une session de réponse en direct sur un appareil, un tableau de bord s’ouvre. Le tableau de bord fournit des informations sur la session, telles que les suivantes :

- Qui créé la session
- Au début de la session
- Durée de la session

Le tableau de bord vous donne également accès à :

- Inscription de l’application dans Azure Active Directory
- Télécharger fichiers dans la bibliothèque
- Console de commande
- Journal de commandes

## <a name="initiate-a-live-response-session-on-a-device"></a>Lancer une session de réponse en direct sur un appareil

1. Connectez-vous Microsoft 365 Defender portail.

2. Accédez aux **points de terminaison >'inventaire** des appareils et sélectionnez un appareil à examiner. La page appareils s’ouvre.

3. Lancez la session de réponse en direct en sélectionnant **Lancer la session de réponse en direct**. Une console de commande s’affiche. Patientez pendant que la session se connecte à l’appareil.

4. Utilisez les commandes intégrées pour faire des enquêtes. Pour plus d’informations, voir [commandes de réponse En direct](#live-response-commands).

5. Après avoir terminé votre enquête, sélectionnez **Déconnecter la session**, puis **confirmez**.

## <a name="live-response-commands"></a>Commandes de réponse en direct

Selon le rôle qui vous a été accordé, vous pouvez exécuter des commandes de réponse en direct de base ou avancées. Les autorisations utilisateur sont contrôlées par des rôles personnalisés RBAC. Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles](user-roles.md).

> [!NOTE]
> La réponse en direct est un environnement de ligne de commande interactif basé sur le cloud, de ce fait, une expérience de commande spécifique peut varier en temps de réponse en fonction de la qualité du réseau et de la charge système entre l’utilisateur final et l’appareil cible.

### <a name="basic-commands"></a>Commandes de base

Les commandes suivantes sont disponibles pour les rôles d’utilisateur qui ont la possibilité d’exécuter des commandes de **réponse en direct** de base. Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles](user-roles.md).

<br>

****
| Command  | Description  | Windows et Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| cd  | Modifie le répertoire actuel.  | v  | v  | v  |
| cls  | Cette commande permet d’effacer l’écran de la console.  | v  | v  | v  |
| connect  | Lance une session de réponse en direct sur l’appareil.  | v  | v  | v  |
| connexions  | Affiche toutes les connexions actives.  | v  | N  | N  |
| dir  | Affiche une liste de fichiers et de sous-répertoires dans un répertoire.  | v  | v  | v  |
| drivers  | Affiche tous les pilotes installés sur l’appareil.  | v  | N  | N  |
| fg `<command ID>`  | Placez le travail spécifié au premier plan au premier plan, ce qui en fait le travail actuel.  REMARQUE : fg prend un « ID de commande » disponible à partir des travaux, et non un piD  | v  | v  | v  |
| fileinfo  | Récupération d’informations sur un fichier.  | v  | v  | v  |
| findfile  | Localise les fichiers sous un nom donné sur l’appareil.  | v  | v  | v  |
| getfile <file_path>  | Télécharge un fichier.  | v  | v  | v  |
| Aide  | Fournit des informations d’aide pour les commandes de réponse en direct.  | v  | v  | v  |
| tâches  | Indique les travaux en cours d’exécution, leur ID et leur état.  | v  | v  | v  |
| persistance  | Affiche toutes les méthodes de persistance connues sur l’appareil.  | v  | N  | N  |
| Processus  | Affiche tous les processus en cours d’exécution sur l’appareil.  | v  | v  | v  |
| registre  | Affiche les valeurs du Registre.  | v  | N  | N  |
| scheduledtasks  | Affiche toutes les tâches programmées sur l’appareil.  | v  | N  | N  |
| services  | Affiche tous les services sur l’appareil.  | v  | N  | N  |
| startupfolders  | Affiche tous les fichiers connus dans les dossiers de démarrage sur l’appareil.  | v  | N  | N  |
| status  | Indique l’état et la sortie d’une commande spécifique.  | v  | N  | N  |
| trace  | Définit le mode de journalisation du terminal pour le débogage.  | v  | v  | v  |

### <a name="advanced-commands"></a>Commandes avancées

Les commandes suivantes sont disponibles pour les rôles d’utilisateur qui ont la possibilité d’exécuter des **commandes** de réponse en direct avancées. Pour plus d’informations sur les attributions de rôles, voir [Créer et gérer des rôles](user-roles.md).

<br>

****

| Command  | Description  | Windows et Windows Server  | macOS  | Linux  |
|---|---|---|---|---|
| analyser  | Analyse l’entité avec différents moteurs d’incrimination pour parvenir à un verdict.  | v  | N  | N  |
| collect  | Collecte le package d’investigation à partir de l’ordinateur  | N  | v  | v  |
| isolate  | Déconnecte l’appareil du réseau tout en conservant la connectivité au service Defender for Endpoint  | N  | v  | N  |
| release  | Libère un appareil de l’isolation réseau  | N  | v  | N  |
| run  | Exécute un script PowerShell à partir de la bibliothèque sur l’appareil.  | v  | v  | v  |
| library  | Répertorie les fichiers qui ont été chargés dans la bibliothèque de réponses en direct.  | v  | v  | v  |
| putfile  | Place un fichier de la bibliothèque sur l’appareil. Les fichiers sont enregistrés dans un dossier de travail et supprimés lorsque l’appareil redémarre par défaut.  | v  | v  | v  |
| corriger  | Remédie à une entité sur l’appareil. L’action de correction varie en fonction du type d’entité : File: delete Process: stop, delete image file Service: stop, delete image file Registry entry: delete Scheduled task: remove Startup folder item: delete file NOTE: This command has a prerequisite command. Vous pouvez utiliser la commande -auto conjointement avec la correction pour exécuter automatiquement la commande prérequise.  | v  | v  | v  |
| analyse | Exécute une analyse antivirus pour identifier et corriger les programmes malveillants. | N | v | v |
| undo  | Restaure une entité qui a été corrigé.  | v  | v  | v  |


## <a name="use-live-response-commands"></a>Utiliser des commandes de réponse en direct

Les commandes que vous pouvez utiliser dans la console suivent les mêmes principes que [Windows commands](/windows-server/administration/windows-commands/windows-commands#BKMK_c).

Les commandes avancées offrent un ensemble plus robuste d’actions qui vous permettent d’exécuter des actions plus puissantes telles que télécharger et télécharger un fichier, exécuter des scripts sur l’appareil et prendre des mesures correctives sur une entité.

### <a name="get-a-file-from-the-device"></a>Obtenir un fichier à partir de l’appareil

Pour les scénarios où vous souhaitez obtenir un fichier à partir d’un appareil que vous examinez, vous pouvez utiliser la `getfile` commande. Cela vous permet d’enregistrer le fichier à partir de l’appareil pour une investigation plus approfondie.

> [!NOTE]
> Les limites de taille de fichier suivantes s’appliquent :
>
> - `getfile` limite : 3 Go
> - `fileinfo` limite : 30 Go
> - `library` limite : 250 Mo

### <a name="download-a-file-in-the-background"></a>Télécharger un fichier en arrière-plan

Pour permettre à votre équipe des opérations de sécurité de continuer à examiner un appareil touché, les fichiers peuvent désormais être téléchargés en arrière-plan.

- Pour télécharger un fichier en arrière-plan, dans la console de commande de réponse en direct, tapez `download <file_path> &`.
- Si vous attendez le téléchargement d’un fichier, vous pouvez le déplacer vers l’arrière-plan à l’aide de Ctrl + Z.
- Pour mettre un téléchargement de fichier au premier plan, dans la console de commande de réponse en direct, tapez `fg <command_id>`.

Voici quelques exemples :

<br>

****

|Commande|Comportement|
|---|---|
|`getfile "C:\windows\some_file.exe" &`|Commence à télécharger un fichier nommé *some_file.exe* en arrière-plan.|
|`fg 1234`|Renvoie un téléchargement avec l’ID *de commande 1234* au premier plan.|
|

### <a name="put-a-file-in-the-library"></a>Placer un fichier dans la bibliothèque

La réponse en direct dispose d’une bibliothèque dans laquelle vous pouvez placer des fichiers. La bibliothèque stocke les fichiers (tels que les scripts) qui peuvent être exécutés dans une session de réponse en direct au niveau du client.

La réponse en direct permet aux scripts PowerShell de s’exécuter, mais vous devez d’abord placer les fichiers dans la bibliothèque avant de pouvoir les exécuter.

Vous pouvez avoir une collection de scripts PowerShell qui peuvent s’exécuter sur les appareils avec qui vous lancez des sessions de réponse en direct.

#### <a name="to-upload-a-file-in-the-library"></a>Pour télécharger un fichier dans la bibliothèque

1. Cliquez **Télécharger fichier vers la bibliothèque**.

2. Cliquez **sur Parcourir** et sélectionnez le fichier.

3. Fournissez une brève description.

4. Spécifiez si vous souhaitez réécrire un fichier du même nom.

5. Si vous le souhaitez, connaissez les paramètres nécessaires pour le script, cochez la case des paramètres de script. Dans le champ de texte, entrez un exemple et une description.

6. Cliquez sur **Confirmer**.

7. (Facultatif) Pour vérifier que le fichier a été téléchargé vers la bibliothèque, exécutez la `library` commande.

### <a name="cancel-a-command"></a>Annuler une commande

À tout moment pendant une session, vous pouvez annuler une commande en appuyant sur Ctrl + C.

> [!WARNING]
> L’utilisation de ce raccourci n’arrête pas la commande côté agent. Il annule uniquement la commande dans le portail. Ainsi, la modification des opérations telles que la « correction » peut se poursuivre, pendant l’annulation de la commande.

## <a name="run-a-script"></a>Exécuter un script

Avant de pouvoir exécuter un script PowerShell/Bash, vous devez d’abord le télécharger dans la bibliothèque.

Après avoir téléchargé le script dans la bibliothèque, utilisez la commande `run` pour exécuter le script.

Si vous prévoyez d’utiliser un script PowerShell non signé dans la session, vous devez activer le paramètre dans la page [Paramètres des fonctionnalités avancées](advanced-features.md) .

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

- Lorsque vous spécifiez des paramètres en dehors de l’ordre fixe, spécifiez le nom du paramètre avec un tiret avant de fournir la valeur :

  ```powershell
  <command name> -param2_name param2
  ```

- Lorsque vous utilisez des commandes qui ont des commandes prérequises, vous pouvez utiliser des indicateurs :

  ```powershell
  <command name> -type file -id <file path> - auto
  ```

  ou

  ```powershell
  remediate file <file path> - auto`
  ```

## <a name="supported-output-types"></a>Types de sortie pris en charge

La réponse en direct prend en charge les types de sortie au format JSON et tableau. Pour chaque commande, il existe un comportement de sortie par défaut. Vous pouvez modifier la sortie dans votre format de sortie préféré à l’aide des commandes suivantes :

- `-output json`
- `-output table`

> [!NOTE]
> Moins de champs sont affichés au format tableau en raison de l’espace limité. Pour voir plus de détails dans la sortie, vous pouvez utiliser la commande de sortie JSON afin que d’autres détails soient affichés.

## <a name="supported-output-pipes"></a>Canaux de sortie pris en charge

La réponse en direct prend en charge le système de sortie vers l’CLI et le fichier. L’CLI est le comportement de sortie par défaut. Vous pouvez canaliser la sortie vers un fichier à l’aide de la commande suivante : [command] > [filename].txt.

Exemple :

```console
processes > output.txt
```

## <a name="view-the-command-log"></a>Afficher le journal de commandes

Sélectionnez **l’onglet Journal** de commandes pour voir les commandes utilisées sur l’appareil au cours d’une session. Chaque commande est suivi avec des détails complets tels que :

- ID
- Ligne de commande
- Durée
- Barre d’état et d’entrée ou de sortie

## <a name="limitations"></a>Limites

- Les sessions de réponse en direct sont limitées à 25 sessions de réponse en direct à la fois.
- La valeur du délai d’inactivité de la session de réponse active est de 30 minutes.
- Les commandes de réponse en direct individuelles ont une limite de temps de 10 minutes, à l’exception `getfile`de , `findfile``run`et , qui ont une limite de 30 minutes.
- Un utilisateur peut démarrer jusqu’à 10 sessions simultanées.
- Un appareil ne peut être connecté qu’à une seule session à la fois.
- Les limites de taille de fichier suivantes s’appliquent :
  - `getfile` limite : 3 Go
  - `fileinfo` limite : 10 Go
  - `library` limite : 250 Mo

## <a name="related-article"></a>Article connexe

- [Exemples de commande Live response](live-response-command-examples.md)
