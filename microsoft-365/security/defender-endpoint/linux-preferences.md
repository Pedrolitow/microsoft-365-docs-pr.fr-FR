---
title: Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux
ms.reviewer: ''
description: Décrit comment configurer Microsoft Defender pour point de terminaison sur Linux dans les entreprises.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, linux, installation, déployer, désinstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 08/10/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 8a04c1720585d8b17c95a0bd4e02ace62bcd1f26
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68803960"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Cette rubrique contient des instructions pour définir des préférences pour Defender pour point de terminaison sur Linux dans les environnements d’entreprise. Si vous souhaitez configurer le produit sur un appareil à partir de la ligne de commande, consultez [Ressources](linux-resources.md#configure-from-the-command-line).

Dans les environnements d’entreprise, Defender pour point de terminaison sur Linux peut être géré via un profil de configuration. Ce profil est déployé à partir de l’outil de gestion de votre choix. Les préférences gérées par l’entreprise sont prioritaires sur celles définies localement sur l’appareil. En d’autres termes, les utilisateurs de votre entreprise ne peuvent pas modifier les préférences définies par le biais de ce profil de configuration. Si des exclusions ont été ajoutées via le profil de configuration managé, elles ne peuvent être supprimées que via le profil de configuration managé. La ligne de commande fonctionne pour les exclusions qui ont été ajoutées localement.

Cet article décrit la structure de ce profil (y compris un profil recommandé que vous pouvez utiliser pour commencer) et des instructions sur la façon de déployer le profil.

## <a name="configuration-profile-structure"></a>Structure du profil de configuration

Le profil de configuration est un fichier .json qui se compose d’entrées identifiées par une clé (qui indique le nom de la préférence), suivie d’une valeur, qui dépend de la nature de la préférence. Les valeurs peuvent être simples, telles qu’une valeur numérique, ou complexes, comme une liste imbriquée de préférences.

En règle générale, vous devez utiliser un outil de gestion de la configuration pour envoyer (push) un fichier portant le nom ```mdatp_managed.json``` à l’emplacement ```/etc/opt/microsoft/mdatp/managed/```.

Le niveau supérieur du profil de configuration inclut les préférences et les entrées à l’échelle du produit pour les sous-zones du produit, qui sont expliquées plus en détail dans les sections suivantes.

### <a name="antivirus-engine-preferences"></a>Préférences du moteur antivirus

La section *antivirusEngine* du profil de configuration est utilisée pour gérer les préférences du composant antivirus du produit.

|Description|Valeur|
|---|---|
|**Clé**|antivirusEngine|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|

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

|Description|Valeur|
|---|---|
|**Clé**|enforcementLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|real_time (par défaut) <p> on_demand <p> Passif|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.10.72 ou ultérieure.|

#### <a name="enabledisable-behavior-monitoring"></a>Activer/désactiver la surveillance du comportement 

Détermine si la fonctionnalité de surveillance et de blocage du comportement est activée sur l’appareil ou non. 

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|behaviorMonitoring|
|**Type de données**|Chaîne|
|**Valeurs possibles**|disabled (par défaut) <p> activé|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.45.00 ou ultérieure.|

#### <a name="configure-file-hash-computation-feature"></a>Configurer la fonctionnalité de calcul de hachage de fichier

Active ou désactive la fonctionnalité de calcul de hachage de fichier. Lorsque cette fonctionnalité est activée, Defender pour point de terminaison calcule les hachages pour les fichiers qu’il analyse. Notez que l’activation de cette fonctionnalité peut avoir un impact sur les performances de l’appareil. Pour plus d’informations, reportez-vous à : [Créer des indicateurs pour les fichiers](indicator-file.md).

|Description|Valeur|
|---|---|
|**Clé**|enableFileHashComputation|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.73.77 ou ultérieure.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Exécuter une analyse après la mise à jour des définitions

Spécifie s’il faut démarrer une analyse de processus après le téléchargement de nouvelles mises à jour du renseignement de sécurité sur l’appareil. L’activation de ce paramètre déclenche une analyse antivirus sur les processus en cours d’exécution de l’appareil.

|Description|Valeur|
|---|---|
|**Clé**|scanAfterDefinitionUpdate|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.45.00 ou ultérieure.|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Archives d’analyse (analyses antivirus à la demande uniquement)

Spécifie s’il faut analyser les archives pendant les analyses antivirus à la demande.

|Description|Valeur|
|---|---|
|**Clé**|scanArchives|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.45.00 ou ultérieure.|

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Degré de parallélisme pour les analyses à la demande

Spécifie le degré de parallélisme pour les analyses à la demande. Cela correspond au nombre de threads utilisés pour effectuer l’analyse et a un impact sur l’utilisation du processeur, ainsi que sur la durée de l’analyse à la demande.

|Description|Valeur|
|---|---|
|**Clé**|maximumOnDemandScanThreads|
|**Type de données**|Entier|
|**Valeurs possibles**|2 (valeur par défaut). Les valeurs autorisées sont des entiers compris entre 1 et 64.|
|**Commentaires**|Disponible dans Microsoft Defender pour point de terminaison version 101.45.00 ou ultérieure.|

#### <a name="exclusion-merge-policy"></a>Stratégie de fusion d’exclusion

Spécifie la stratégie de fusion pour les exclusions. Il peut s’agir d’une combinaison d’exclusions définies par l’administrateur et définies par l’utilisateur (`merge`) ou uniquement d’exclusions définies par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres exclusions.

|Description|Valeur|
|---|---|
|**Clé**|exclusionsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 100.83.73 ou ultérieure.|

#### <a name="scan-exclusions"></a>Exclusions d’analyse

Entités qui ont été exclues de l’analyse. Les exclusions peuvent être spécifiées par des chemins d’accès complets, des extensions ou des noms de fichiers.
(Les exclusions sont spécifiées sous la forme d’un tableau d’éléments, l’administrateur peut spécifier autant d’éléments que nécessaire, dans n’importe quel ordre.)

|Description|Valeur|
|---|---|
|**Clé**|Exclusions|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|

##### <a name="type-of-exclusion"></a>Type d’exclusion

Spécifie le type de contenu exclu de l’analyse.

|Description|Valeur|
|---|---|
|**Clé**|$type|
|**Type de données**|Chaîne|
|**Valeurs possibles**|excludedPath <p> excludedFileExtension <p> excludedFileName|

##### <a name="path-to-excluded-content"></a>Chemin d’accès au contenu exclu

Permet d’exclure le contenu de l’analyse par chemin d’accès de fichier complet.

|Description|Valeur|
|---|---|
|**Clé**|chemin|
|**Type de données**|Chaîne|
|**Valeurs possibles**|chemins d’accès valides|
|**Commentaires**|Applicable uniquement si *$type* est *excluPath*|

##### <a name="path-type-file--directory"></a>Type de chemin d’accès (fichier/répertoire)

Indique si la propriété *path* fait référence à un fichier ou un répertoire.

|Description|Valeur|
|---|---|
|**Clé**|isDirectory|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|**Commentaires**|Applicable uniquement si *$type* est *excluPath*|

##### <a name="file-extension-excluded-from-the-scan"></a>Extension de fichier exclue de l’analyse

Permet d’exclure le contenu de l’analyse par extension de fichier.

|Description|Valeur|
|---|---|
|**Clé**|Extension|
|**Type de données**|Chaîne|
|**Valeurs possibles**|extensions de fichier valides|
|**Commentaires**|Applicable uniquement si *$type* est *excluFileExtension*|

##### <a name="process-excluded-from-the-scan"></a>Processus exclu de l’analyse*

Spécifie un processus pour lequel toute l’activité de fichier est exclue de l’analyse. Le processus peut être spécifié par son nom (par exemple, `cat`) ou par son chemin d’accès complet (par exemple, `/bin/cat`).

|Description|Valeur|
|---|---|
|**Clé**|nom|
|**Type de données**|Chaîne|
|**Valeurs possibles**|n’importe quelle chaîne|
|**Commentaires**|Applicable uniquement si *$type* est *excluFileName*|

#### <a name="allowed-threats"></a>Menaces autorisées

Liste des menaces (identifiées par leur nom) qui ne sont pas bloquées par le produit et qui sont à la place autorisées à s’exécuter.

|Description|Valeur|
|---|---|
|**Clé**|allowedThreats|
|**Type de données**|Tableau de chaînes|

#### <a name="disallowed-threat-actions"></a>Actions de menace non autorisées

Limite les actions que l’utilisateur local d’un appareil peut effectuer lorsque des menaces sont détectées. Les actions incluses dans cette liste ne sont pas affichées dans l’interface utilisateur.

|Description|Valeur|
|---|---|
|**Clé**|disallowedThreatActions|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|autoriser (empêche les utilisateurs d’autoriser les menaces) <p> restore (empêche les utilisateurs de restaurer les menaces à partir de la quarantaine)|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 100.83.73 ou ultérieure.|

#### <a name="threat-type-settings"></a>Paramètres des types de menaces

La préférence *threatTypeSettings* dans le moteur antivirus est utilisée pour contrôler la façon dont certains types de menaces sont gérés par le produit.

|Description|Valeur|
|---|---|
|**Clé**|threatTypeSettings|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|

##### <a name="threat-type"></a>Type de menace

Type de menace pour lequel le comportement est configuré.

|Description|Valeur|
|---|---|
|**Clé**|clé|
|**Type de données**|Chaîne|
|**Valeurs possibles**|potentially_unwanted_application <p> archive_bomb|

##### <a name="action-to-take"></a>Mesures à prendre

Action à entreprendre en cas de détection d’une menace du type spécifié dans la section précédente. Peut être :

- **Audit** : l’appareil n’est pas protégé contre ce type de menace, mais une entrée concernant la menace est journalisée.
- **Bloquer** : l’appareil est protégé contre ce type de menace et vous êtes averti dans la console de sécurité.
- **Désactivé** : l’appareil n’est pas protégé contre ce type de menace et rien n’est journalisé.

|Description|Valeur|
|---|---|
|**Clé**|valeur|
|**Type de données**|Chaîne|
|**Valeurs possibles**|audit (par défaut) <p> Bloc <p> inactif|

#### <a name="threat-type-settings-merge-policy"></a>Stratégie de fusion des paramètres de type de menace

Spécifie la stratégie de fusion pour les paramètres de type de menace. Il peut s’agir d’une combinaison de paramètres définis par l’administrateur et définis par l’utilisateur (`merge`) ou uniquement de paramètres définis par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres paramètres pour différents types de menaces.

|Description|Valeur|
|---|---|
|**Clé**|threatTypeSettingsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 100.83.73 ou ultérieure.|

#### <a name="antivirus-scan-history-retention-in-days"></a>Rétention de l’historique d’analyse antivirus (en jours)

Spécifiez le nombre de jours pendant lesquels les résultats sont conservés dans l’historique d’analyse sur l’appareil. Les anciens résultats de l’analyse sont supprimés de l’historique. Anciens fichiers mis en quarantaine qui sont également supprimés du disque.

|Description|Valeur|
|---|---|
|**Clé**|scanResultsRetentionDays|
|**Type de données**|Chaîne|
|**Valeurs possibles**|90 (valeur par défaut). Les valeurs autorisées sont comprises entre 1 et 180 jours.|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.04.76 ou ultérieure.|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Nombre maximal d’éléments dans l’historique d’analyse antivirus

Spécifiez le nombre maximal d’entrées à conserver dans l’historique d’analyse. Les entrées incluent toutes les analyses à la demande effectuées dans le passé et toutes les détections antivirus.

|Description|Valeur|
|---|---|
|**Clé**|scanHistoryMaximumItems|
|**Type de données**|Chaîne|
|**Valeurs possibles**|10000 (valeur par défaut). Les valeurs autorisées sont comprises entre 5 000 éléments et 1 5 000 éléments.|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.04.76 ou ultérieure.|

### <a name="cloud-delivered-protection-preferences"></a>Préférences de protection fournies par le cloud

L’entrée *cloudService* dans le profil de configuration est utilisée pour configurer la fonctionnalité de protection pilotée par le cloud du produit.

|Description|Valeur|
|---|---|
|**Clé**|cloudService|
|**Type de données**|Dictionnaire (préférence imbriquée)|
|**Commentaires**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|

#### <a name="enable--disable-cloud-delivered-protection"></a>Activer/désactiver la protection fournie par le cloud

Détermine si la protection fournie par le cloud est activée sur l’appareil ou non. Pour améliorer la sécurité de vos services, nous vous recommandons de garder cette fonctionnalité activée.

|Description|Valeur|
|---|---|
|**Clé**|activé|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|

#### <a name="diagnostic-collection-level"></a>Niveau de collecte de diagnostics

Les données de diagnostic sont utilisées pour assurer la sécurité et la mise à jour de Defender pour point de terminaison, détecter, diagnostiquer et résoudre les problèmes, et apporter des améliorations au produit. Ce paramètre détermine le niveau des diagnostics envoyés par le produit à Microsoft.

|Description|Valeur|
|---|---|
|**Clé**|diagnosticLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|facultatif <p> obligatoire (par défaut)|
|

#### <a name="configure-cloud-block-level"></a>Configurer le niveau de bloc cloud

Ce paramètre détermine l’agressivité de Defender pour point de terminaison dans le blocage et l’analyse des fichiers suspects. Si ce paramètre est activé, Defender pour point de terminaison sera plus agressif lors de l’identification des fichiers suspects à bloquer et analyser ; sinon, il sera moins agressif et donc bloquer et analyser avec moins de fréquence. Il existe cinq valeurs pour définir le niveau de bloc cloud :

- Normal (`normal`) : niveau de blocage par défaut.
- Modéré (`moderate`) : fournit un verdict uniquement pour les détections à haut niveau de confiance.
- Élevé (`high`) : bloque de manière agressive les fichiers inconnus tout en optimisant les performances (plus de chances de bloquer les fichiers non dangereux).
- Plus élevé (`high_plus`) : bloque de manière agressive les fichiers inconnus et applique des mesures de protection supplémentaires (susceptibles d’avoir un impact sur les performances des appareils clients).
- Tolérance zéro (`zero_tolerance`) : bloque tous les programmes inconnus.

|Description|Valeur|
|---|---|
|**Clé**|cloudBlockLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|normal (par défaut) <p> Modérée <p> Haute <p> high_plus <p> zero_tolerance|
|**Commentaires**|Disponible dans Defender pour point de terminaison version 101.56.62 ou ultérieure.|
  
#### <a name="enable--disable-automatic-sample-submissions"></a>Activer/désactiver les envois automatiques d’exemples

Détermine si des échantillons suspects (susceptibles de contenir des menaces) sont envoyés à Microsoft. Il existe trois niveaux pour contrôler l’envoi d’exemples :

- **Aucun** : aucun échantillon suspect n’est envoyé à Microsoft.
- **Sécurisé** : seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut de ce paramètre.
- **Tout** : tous les échantillons suspects sont envoyés à Microsoft.

|Description|Valeur|
|---|---|
|**Clé**|automaticSampleSubmissionConsent|
|**Type de données**|Chaîne|
|**Valeurs possibles**|none <p> safe (valeur par défaut) <p> tout|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Activer/désactiver les mises à jour automatiques du renseignement de sécurité

Détermine si les mises à jour du renseignement de sécurité sont installées automatiquement :

|Description|Valeur|
|---|---|
|**Clé**|automaticDefinitionUpdateEnabled|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (valeur par défaut) <p> false|

## <a name="recommended-configuration-profile"></a>Profil de configuration recommandé

Pour commencer, nous vous recommandons d’utiliser le profil de configuration suivant pour votre entreprise afin de tirer parti de toutes les fonctionnalités de protection fournies par Defender pour point de terminaison.

Le profil de configuration suivant :

- Activer la protection en temps réel (RTP)
- Spécifiez la façon dont les types de menaces suivants sont gérés :
  - **Les applications potentiellement indésirables (PUA)** sont bloquées
  - **Les bombes d’archivage** (fichier avec un taux de compression élevé) sont auditées dans les journaux du produit
- Activer les mises à jour automatiques du renseignement de sécurité
- Protection fournie par le cloud
- Activer l’envoi automatique d’exemples au `safe` niveau

### <a name="sample-profile"></a>Exemple de profil

```JSON
{
   "antivirusEngine":{
      "enforcementLevel":"real_time",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "automaticDefinitionUpdateEnabled":true,
      "automaticSampleSubmissionConsent":"safe",
      "enabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="full-configuration-profile-example"></a>Exemple de profil de configuration complet

Le profil de configuration suivant contient des entrées pour tous les paramètres décrits dans ce document et peut être utilisé pour des scénarios plus avancés où vous souhaitez davantage de contrôle sur le produit.
  
> [!NOTE]
> Il n’est pas possible de contrôler toutes les communications Microsoft Defender pour point de terminaison avec uniquement un paramètre proxy dans ce json.

### <a name="full-profile"></a>Profil complet

```JSON
{
   "antivirusEngine":{
      "enforcementLevel":"real_time",
      "scanAfterDefinitionUpdate":true,
      "scanArchives":true,
      "maximumOnDemandScanThreads":2,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log<EXAMPLE DO NOT USE>"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/run<EXAMPLE DO NOT USE>"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home/*/git<EXAMPLE DO NOT USE>"
         },
         {
            "$type":"excludedFileExtension",
            "extension":".pdf<EXAMPLE DO NOT USE>"
         },
         {
            "$type":"excludedFileName",
            "name":"cat<EXAMPLE DO NOT USE>"
         }
      ],
      "allowedThreats":[
         "<EXAMPLE DO NOT USE>EICAR-Test-File (not a virus)"
      ],
      "disallowedThreatActions":[
         "allow",
         "restore"
      ],
      "threatTypeSettingsMergePolicy":"merge",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "enabled":true,
      "diagnosticLevel":"optional",
      "automaticSampleSubmissionConsent":"safe",
      "automaticDefinitionUpdateEnabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Ajouter une étiquette ou un ID de groupe au profil de configuration

Lorsque vous exécutez la `mdatp health` commande pour la première fois, la valeur de la balise et de l’ID de groupe est vide. Pour ajouter une balise ou un ID de groupe au `mdatp_managed.json` fichier, procédez comme suit :
  
  1. Ouvrez le profil de configuration à partir du chemin d’accès `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Descendez en bas du fichier, où se trouve le `cloudService` bloc.
  3. Ajoutez la balise ou l’ID de groupe requis comme exemple suivant à la fin du crochet fermant pour le `cloudService`.

  ```JSON
    },
    "cloudService": {
      "enabled": true,
      "diagnosticLevel": "optional",
      "automaticSampleSubmissionConsent": "safe",
      "automaticDefinitionUpdateEnabled": true,
      "proxy": "http://proxy.server:port/"
  },
  "edr": {
    "groupIds":"GroupIdExample",
    "tags": [
              {
              "key": "GROUP",
              "value": "Tag"
              }
            ]
        }
  }
  ```

  > [!NOTE]
  > N’oubliez pas d’ajouter la virgule après le crochet fermant à la fin du `cloudService` bloc. Assurez-vous également qu’il existe deux accolades fermants après l’ajout d’une balise ou d’un bloc d’ID de groupe (consultez l’exemple ci-dessus). Pour le moment, le seul nom de clé pris en charge pour les balises est `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Validation du profil de configuration

Le profil de configuration doit être un fichier au format JSON valide. Il existe un certain nombre d’outils qui peuvent être utilisés pour vérifier cela. Par exemple, si vous avez `python` installé sur votre appareil :

```bash
python -m json.tool mdatp_managed.json
```

Si le json est correctement formé, la commande ci-dessus le renvoie au terminal et retourne un code de sortie de `0`. Sinon, une erreur décrivant le problème s’affiche et la commande retourne un code de sortie de `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Vérification que le fichier mdatp_managed.json fonctionne comme prévu

Pour vérifier que votre fichier /etc/opt/microsoft/mdatp/managed/mdatp_managed.json fonctionne correctement, vous devez voir « [géré] » en regard de ces paramètres :

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> Pour que le mdatp_managed.json prenne effet, aucun redémarrage du `mdatp` démon n’est nécessaire.
  

## <a name="configuration-profile-deployment"></a>Déploiement du profil de configuration

Une fois que vous avez créé le profil de configuration pour votre entreprise, vous pouvez le déployer via l’outil de gestion que votre entreprise utilise. Defender pour point de terminaison sur Linux lit la configuration managée à partir du fichier */etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
