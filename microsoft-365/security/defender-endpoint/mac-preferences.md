---
title: Définir les préférences pour Microsoft Defender pour point de terminaison sur Mac
description: Configurez Microsoft Defender pour point de terminaison sur Mac dans les organisations d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, gestion, préférences, entreprise, intune, jamf, macos, catalina, big sur, monterey, ventura, mde pour mac
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
ms.openlocfilehash: cc9b76c30bbf44fb19308790bb61a30145c8774b
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68767805"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Cet article contient des instructions pour définir des préférences pour Microsoft Defender pour point de terminaison sur macOS dans les organisations d’entreprise. Pour configurer Microsoft Defender pour point de terminaison sur macOS à l’aide de l’interface de ligne de commande, consultez [Ressources](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Résumé

Dans les organisations d’entreprise, les Microsoft Defender pour point de terminaison sur macOS peuvent être gérés via un profil de configuration déployé à l’aide de l’un des outils de gestion. Les préférences gérées par votre équipe des opérations de sécurité sont prioritaires sur les préférences définies localement sur l’appareil. La modification des préférences définies par le biais du profil de configuration nécessite des privilèges réaffectés et n’est pas disponible pour les utilisateurs sans autorisations d’administration.

Cet article décrit la structure du profil de configuration, inclut un profil recommandé que vous pouvez utiliser pour commencer et fournit des instructions sur le déploiement du profil.

## <a name="configuration-profile-structure"></a>Structure du profil de configuration

Le profil de configuration est un fichier *.plist* qui se compose d’entrées identifiées par une clé (qui indique le nom de la préférence), suivie d’une valeur, qui dépend de la nature de la préférence. Les valeurs peuvent être simples (par exemple, une valeur numérique) ou complexes, comme une liste imbriquée de préférences.

> [!CAUTION]
>La disposition du profil de configuration dépend de la console de gestion que vous utilisez. Les sections suivantes contiennent des exemples de profils de configuration pour JAMF et Intune.

Le niveau supérieur du profil de configuration inclut les préférences et les entrées à l’échelle du produit pour les sous-zones de Microsoft Defender pour point de terminaison, qui sont expliquées plus en détail dans les sections suivantes.

### <a name="antivirus-engine-preferences"></a>Préférences du moteur antivirus

La section *antivirusEngine* du profil de configuration est utilisée pour gérer les préférences du composant antivirus de Microsoft Defender pour point de terminaison.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|antivirusEngine|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

#### <a name="enforcement-level-for-antivirus-engine"></a>Niveau d’application pour le moteur antivirus

Spécifie la préférence d’application du moteur antivirus. Il existe trois valeurs pour définir le niveau d’application :

- En temps réel (`real_time`) : la protection en temps réel (analyser les fichiers au fur et à mesure qu’ils sont accessibles) est activée.
- À la demande (`on_demand`) : les fichiers sont analysés uniquement à la demande. Dans ce cas :
  - La protection en temps réel est désactivée.
- Passif (`passive`) : exécute le moteur antivirus en mode passif. Dans ce cas :
  - La protection en temps réel est désactivée.
  - L’analyse à la demande est activée.
  - La correction automatique des menaces est désactivée.
  - Les mises à jour du renseignement de sécurité sont activées.
  - L’icône du menu État est masquée.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|enforcementLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|real_time (par défaut) <p> on_demand <p> Passif|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.10.72 ou ultérieure.|
|||

#### <a name="configure-file-hash-computation-feature"></a>Configurer la fonctionnalité de calcul de hachage de fichier

Active ou désactive la fonctionnalité de calcul de hachage de fichier. Lorsque cette fonctionnalité est activée, Defender pour point de terminaison calcule les hachages pour les fichiers qu’il analyse. Notez que l’activation de cette fonctionnalité peut avoir un impact sur les performances de l’appareil. Pour plus d’informations, reportez-vous à : [Créer des indicateurs pour les fichiers](indicator-file.md).

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|enableFileHashComputation|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.73.77 ou ultérieure.|

#### <a name="run-a-scan-after-definitions-are-updated"></a>Exécuter une analyse après la mise à jour des définitions

Spécifie s’il faut démarrer une analyse de processus après le téléchargement de nouvelles mises à jour du renseignement de sécurité sur l’appareil. L’activation de ce paramètre déclenche une analyse antivirus sur les processus en cours d’exécution de l’appareil.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|scanAfterDefinitionUpdate|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.41.10 ou ultérieure.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Archives d’analyse (analyses antivirus à la demande uniquement)

Spécifie s’il faut analyser les archives pendant les analyses antivirus à la demande.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|scanArchives|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.41.10 ou ultérieure.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Degré de parallélisme pour les analyses à la demande

Spécifie le degré de parallélisme pour les analyses à la demande. Cela correspond au nombre de threads utilisés pour effectuer l’analyse et a un impact sur l’utilisation du processeur, ainsi que sur la durée de l’analyse à la demande.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|maximumOnDemandScanThreads|
|**Type de données**|Entier|
|**Valeurs possibles**|2 (valeur par défaut). Les valeurs autorisées sont des entiers compris entre 1 et 64.|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.41.10 ou ultérieure.|
|||

#### <a name="exclusion-merge-policy"></a>Stratégie de fusion d’exclusion

Spécifiez la stratégie de fusion pour les exclusions. Il peut s’agir d’une combinaison d’exclusions définies par l’administrateur et définies par l’utilisateur (`merge`), ou uniquement d’exclusions définies par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres exclusions.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|exclusionsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 100.83.73 ou ultérieure.|
|||

#### <a name="scan-exclusions"></a>Exclusions d’analyse

Spécifiez les entités exclues de l’analyse. Les exclusions peuvent être spécifiées par des chemins d’accès complets, des extensions ou des noms de fichiers.
(Les exclusions sont spécifiées sous la forme d’un tableau d’éléments, l’administrateur peut spécifier autant d’éléments que nécessaire, dans n’importe quel ordre.)

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|Exclusions|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

##### <a name="type-of-exclusion"></a>Type d’exclusion

Spécifiez le contenu exclu de l’analyse par type.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|$type|
|**Type de données**|Chaîne|
|**Valeurs possibles**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>Chemin d’accès au contenu exclu

Spécifiez le contenu exclu de l’analyse par chemin d’accès de fichier complet.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|chemin|
|**Type de données**|Chaîne|
|**Valeurs possibles**|chemins d’accès valides|
|**Commentaires**|Applicable uniquement si *$type* est *excluPath*|
|||

## <a name="supported-exclusion-types"></a>Types d’exclusion pris en charge

Le tableau suivant présente les types d’exclusion pris en charge par Defender pour point de terminaison sur Mac.

<br>

****

|Exclusion|Définition|Exemples|
|---|---|---|
|Extension de fichier|Tous les fichiers avec l’extension, n’importe où sur l’appareil|`.test`|
|File|Fichier spécifique identifié par le chemin d’accès complet|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|Folder|Tous les fichiers sous le dossier spécifié (de manière récursive)|`/var/log/` <p> `/var/*/`|
|Processus|Un processus spécifique (spécifié par le chemin d’accès complet ou le nom de fichier) et tous les fichiers ouverts par celui-ci|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> Les chemins ci-dessus doivent être des liens physiques, et non des liens symboliques, afin d’être correctement exclus. Vous pouvez vérifier si un chemin d’accès est un lien symbolique en exécutant `file <path-name>`.

Les exclusions de fichiers, de dossiers et de processus prennent en charge les caractères génériques suivants :

<br>

****

|Caractère générique|Description|Exemple|Matchs|Ne correspond pas|
|---|---|---|---|---|
|\*|Correspond à n’importe quel nombre de caractères, y compris aucun (notez que lorsque ce caractère générique est utilisé à l’intérieur d’un chemin d’accès, il ne remplace qu’un seul dossier)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|Correspond à n’importe quel caractère unique|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>Type de chemin d’accès (fichier/répertoire)

Indique si la propriété *path* fait référence à un fichier ou un répertoire.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|isDirectory|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|**Commentaires**|Applicable uniquement si *$type* est *excluPath*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>Extension de fichier exclue de l’analyse

Spécifiez le contenu exclu de l’analyse par extension de fichier.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|Extension|
|**Type de données**|Chaîne|
|**Valeurs possibles**|extensions de fichier valides|
|**Commentaires**|Applicable uniquement si *$type* est *excluFileExtension*|
|||

### <a name="process-excluded-from-the-scan"></a>Processus exclu de l’analyse

Spécifiez un processus pour lequel toute l’activité de fichier est exclue de l’analyse. Le processus peut être spécifié par son nom (par exemple, `cat`) ou par son chemin d’accès complet (par exemple, `/bin/cat`).

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|nom|
|**Type de données**|Chaîne|
|**Valeurs possibles**|n’importe quelle chaîne|
|**Commentaires**|Applicable uniquement si *$type* est *excluFileName*|
|||

#### <a name="allowed-threats"></a>Menaces autorisées

Spécifiez les menaces par nom qui ne sont pas bloquées par Defender pour point de terminaison sur Mac. Ces menaces seront autorisées à s’exécuter.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|allowedThreats|
|**Type de données**|Tableau de chaînes|
|||

#### <a name="disallowed-threat-actions"></a>Actions de menace non autorisées

Limite les actions que l’utilisateur local d’un appareil peut effectuer lorsque des menaces sont détectées. Les actions incluses dans cette liste ne sont pas affichées dans l’interface utilisateur.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|disallowedThreatActions|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|autoriser (empêche les utilisateurs d’autoriser les menaces) <p> restore (empêche les utilisateurs de restaurer les menaces à partir de la quarantaine)|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 100.83.73 ou ultérieure.|
|||

#### <a name="threat-type-settings"></a>Paramètres des types de menaces

Spécifiez comment certains types de menaces sont gérés par Microsoft Defender pour point de terminaison sur macOS.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|threatTypeSettings|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

##### <a name="threat-type"></a>Type de menace

Spécifiez les types de menaces.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|clé|
|**Type de données**|Chaîne|
|**Valeurs possibles**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>Mesures à prendre

Spécifiez l’action à entreprendre lorsqu’une menace du type spécifié dans la section précédente est détectée. Choisissez l'une des options suivantes :

- **Audit** : votre appareil n’est pas protégé contre ce type de menace, mais une entrée concernant la menace est journalisée.
- **Bloquer** : votre appareil est protégé contre ce type de menace et vous êtes averti dans l’interface utilisateur et la console de sécurité.
- **Désactivé** : votre appareil n’est pas protégé contre ce type de menace et rien n’est journalisé.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|valeur|
|**Type de données**|Chaîne|
|**Valeurs possibles**|audit (par défaut) <p> Bloc <p> inactif|
|||

#### <a name="threat-type-settings-merge-policy"></a>Stratégie de fusion des paramètres de type de menace

Spécifiez la stratégie de fusion pour les paramètres de type de menace. Il peut s’agir d’une combinaison de paramètres définis par l’administrateur et définis par l’utilisateur (`merge`) ou uniquement de paramètres définis par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres paramètres pour différents types de menaces.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|threatTypeSettingsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 100.83.73 ou ultérieure.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>Rétention de l’historique d’analyse antivirus (en jours)

Spécifiez le nombre de jours pendant lesquels les résultats sont conservés dans l’historique d’analyse sur l’appareil. Les anciens résultats de l’analyse sont supprimés de l’historique. Anciens fichiers mis en quarantaine qui sont également supprimés du disque.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|scanResultsRetentionDays|
|**Type de données**|Chaîne|
|**Valeurs possibles**|90 (valeur par défaut). Les valeurs autorisées sont comprises entre 1 et 180 jours.|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.07.23 ou ultérieure.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Nombre maximal d’éléments dans l’historique d’analyse antivirus

Spécifiez le nombre maximal d’entrées à conserver dans l’historique d’analyse. Les entrées incluent toutes les analyses à la demande effectuées dans le passé et toutes les détections antivirus.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|scanHistoryMaximumItems|
|**Type de données**|Chaîne|
|**Valeurs possibles**|10000 (valeur par défaut). Les valeurs autorisées sont comprises entre 5 000 éléments et 1 5 000 éléments.|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.07.23 ou ultérieure.|
|||

### <a name="cloud-delivered-protection-preferences"></a>Préférences de protection fournies par le cloud

Configurez les fonctionnalités de protection cloud de Microsoft Defender pour point de terminaison sur macOS.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|cloudService|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>Activer/désactiver la protection fournie par le cloud

Spécifiez s’il faut activer la protection fournie par le cloud sur l’appareil ou non. Pour améliorer la sécurité de vos services, nous vous recommandons de garder cette fonctionnalité activée.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|activé|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|||

#### <a name="diagnostic-collection-level"></a>Niveau de collecte de diagnostics

Les données de diagnostic sont utilisées pour maintenir Microsoft Defender pour point de terminaison sécurité et à jour, détecter, diagnostiquer et résoudre les problèmes, et apporter des améliorations au produit. Ce paramètre détermine le niveau des diagnostics envoyés par Microsoft Defender pour point de terminaison à Microsoft.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|diagnosticLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|facultatif (par défaut) <p> obligatoire|
|||

#### <a name="configure-cloud-block-level"></a>Configurer le niveau de bloc cloud

Ce paramètre détermine l’agressivité de Defender pour point de terminaison dans le blocage et l’analyse des fichiers suspects. Si ce paramètre est activé, Defender pour point de terminaison sera plus agressif lors de l’identification des fichiers suspects à bloquer et analyser ; sinon, il sera moins agressif et donc bloquer et analyser avec moins de fréquence. Il existe cinq valeurs pour définir le niveau de bloc cloud :

- Normal (`normal`) : niveau de blocage par défaut.
- Modéré (`moderate`) : fournit un verdict uniquement pour les détections à haut niveau de confiance.
- Élevé (`high`) : bloque de manière agressive les fichiers inconnus tout en optimisant les performances (plus de chances de bloquer les fichiers non dangereux).
- Plus élevé (`high_plus`) : bloque de manière agressive les fichiers inconnus et applique des mesures de protection supplémentaires (susceptibles d’avoir un impact sur les performances des appareils clients).
- Tolérance zéro (`zero_tolerance`) : bloque tous les programmes inconnus.

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|cloudBlockLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|normal (par défaut) <p> Modérée <p> Haute <p> high_plus <p> zero_tolerance|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.56.62 ou ultérieure.|

#### <a name="enable--disable-automatic-sample-submissions"></a>Activer/désactiver les envois automatiques d’exemples

Détermine si des échantillons suspects (susceptibles de contenir des menaces) sont envoyés à Microsoft. Vous êtes invité à indiquer si le fichier soumis est susceptible de contenir des informations personnelles.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|automaticSampleSubmission|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Activer/désactiver les mises à jour automatiques du renseignement de sécurité

Détermine si les mises à jour du renseignement de sécurité sont installées automatiquement :

<br>

****

|Section|Valeur|
|---|---|
|**Clé**|automaticDefinitionUpdateEnabled|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|||

### <a name="user-interface-preferences"></a>Préférences de l’interface utilisateur

Gérez les préférences pour l’interface utilisateur de Microsoft Defender pour point de terminaison sur macOS.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|userInterface|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

#### <a name="show--hide-status-menu-icon"></a>Icône afficher/masquer le menu d’état

Indiquez s’il faut afficher ou masquer l’icône du menu d’état dans le coin supérieur droit de l’écran.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|hideStatusMenuIcon|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|||

#### <a name="show--hide-option-to-send-feedback"></a>Option Afficher/masquer pour envoyer des commentaires

Spécifiez si les utilisateurs peuvent envoyer des commentaires à Microsoft en accédant à `Help` > `Send Feedback`.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|userInitiatedFeedback|
|**Type de données**|Chaîne|
|**Valeurs possibles**|enabled (valeur par défaut) <p> désactivé|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.19.61 ou ultérieure.|
|||



#### <a name="control-sign-in-to-consumer-version-of-microsoft-defender"></a>Contrôler la connexion à la version consommateur de Microsoft Defender

Spécifiez si les utilisateurs peuvent se connecter à la version consommateur de Microsoft Defender.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|consumerExperience|
|**Type de données**|Chaîne|
|**Valeurs possibles**|enabled (valeur par défaut) <p> désactivé|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.60.18 ou ultérieure.|
|||


### <a name="endpoint-detection-and-response-preferences"></a>Détection des points de terminaison et préférences de réponse

Gérez les préférences du composant EDR (Endpoint Detection and Response) de Microsoft Defender pour point de terminaison sur macOS.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|edr|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

#### <a name="device-tags"></a>Balises d’appareil

Spécifiez un nom de balise et sa valeur.

- La balise GROUP marque l’appareil avec la valeur spécifiée. La balise est reflétée dans le portail sous la page de l’appareil et peut être utilisée pour le filtrage et le regroupement d’appareils.

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|étiquettes|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|||

##### <a name="type-of-tag"></a>Type de balise

Spécifie le type de balise

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|clé|
|**Type de données**|Chaîne|
|**Valeurs possibles**|`GROUP`|
|||

##### <a name="value-of-tag"></a>Valeur de la balise

Spécifie la valeur de balise

<br>

****

|Section|Valeur|
|---|---|
|**Domaine**|`com.microsoft.wdav`|
|**Clé**|valeur|
|**Type de données**|Chaîne|
|**Valeurs possibles**|n’importe quelle chaîne|
|||

> [!IMPORTANT]
>
> - Une seule valeur par type de balise peut être définie.
> - Les types de balises sont uniques et ne doivent pas être répétés dans le même profil de configuration.

## <a name="recommended-configuration-profile"></a>Profil de configuration recommandé

Pour commencer, nous vous recommandons la configuration suivante pour votre entreprise afin de tirer parti de toutes les fonctionnalités de protection fournies par Microsoft Defender pour point de terminaison.

Le profil de configuration suivant (ou, dans le cas de JAMF, une liste de propriétés qui peut être chargée dans le profil de configuration des paramètres personnalisés) :

- Activer la protection en temps réel (RTP)
- Spécifiez la façon dont les types de menaces suivants sont gérés :
  - **Les applications potentiellement indésirables (PUA)** sont bloquées
  - **Les bombes d’archivage** (fichier avec un taux de compression élevé) sont auditées pour Microsoft Defender pour point de terminaison journaux
- Activer les mises à jour automatiques du renseignement de sécurité
- Protection fournie par le cloud
- Activer l’envoi automatique d’exemples

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>Liste de propriétés pour le profil de configuration recommandé JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-recommended-profile"></a>Intune profil recommandé

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>Exemple de profil de configuration complet

Les modèles suivants contiennent des entrées pour tous les paramètres décrits dans ce document et peuvent être utilisés pour des scénarios plus avancés où vous souhaitez mieux contrôler Microsoft Defender pour point de terminaison sur macOS.

### <a name="property-list-for-jamf-full-configuration-profile"></a>Liste de propriétés pour le profil de configuration complet JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>scanAfterDefinitionUpdate</key>
        <true/>
        <key>scanArchives</key>
        <true/>
        <key>maximumOnDemandScanThreads</key>
        <integer>2</integer>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-full-profile"></a>Intune profil complet

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>scanAfterDefinitionUpdate</key>
                    <true/>
                    <key>scanArchives</key>
                    <true/>
                    <key>maximumOnDemandScanThreads</key>
                    <integer>1</integer>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="property-list-validation"></a>Validation de la liste de propriétés

La liste de propriétés doit être un fichier *.plist* valide. Cela peut être vérifié en exécutant :

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

Si le fichier est correctement formé, la commande ci-dessus génère `OK` et retourne un code de sortie de `0`. Sinon, une erreur décrivant le problème s’affiche et la commande retourne un code de sortie de `1`.

## <a name="configuration-profile-deployment"></a>Déploiement du profil de configuration

Une fois que vous avez créé le profil de configuration pour votre entreprise, vous pouvez le déployer via la console de gestion que votre entreprise utilise. Les sections suivantes fournissent des instructions sur la façon de déployer ce profil à l’aide de JAMF et de Intune.

### <a name="jamf-deployment"></a>Déploiement JAMF

À partir de la console JAMF, ouvrez **Profils de configuration** **ordinateurs**\>, accédez au profil de configuration que vous souhaitez utiliser, puis sélectionnez **Paramètres personnalisés**. Créez une entrée avec `com.microsoft.wdav` comme domaine de préférence et *chargez le fichier .plist* produit précédemment.

> [!CAUTION]
> Vous devez entrer le domaine de préférence approprié (`com.microsoft.wdav`) ; sinon, les préférences ne seront pas reconnues par Microsoft Defender pour point de terminaison.

### <a name="intune-deployment"></a>déploiement Intune

1. Ouvrez **Gérer la** \> **configuration de l’appareil**. Sélectionnez **Gérer les** \> **profils** \> **Créer un profil**.

2. Choisissez un nom pour le profil. Remplacez **Platform=macOS par** **Type de profil=Personnalisé**. Sélectionnez Configurer.

3. Enregistrez le fichier .plist produit précédemment en tant que `com.microsoft.wdav.xml`.

4. Entrez `com.microsoft.wdav` comme **nom de profil de configuration personnalisé**.

5. Ouvrez le profil de configuration et chargez le `com.microsoft.wdav.xml` fichier. (Ce fichier a été créé à l’étape 3.)

6. Sélectionnez **OK**.

7. Sélectionnez **Gérer les** \> **affectations**. Sous l’onglet **Inclure** , sélectionnez **Affecter à tous les utilisateurs & Tous les appareils**.

> [!CAUTION]
> Vous devez entrer le nom de profil de configuration personnalisé correct. dans le cas contraire, ces préférences ne seront pas reconnues par Microsoft Defender pour point de terminaison.

## <a name="resources"></a>Ressources

- [Référence du profil de configuration (documentation Apple pour les développeurs)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
