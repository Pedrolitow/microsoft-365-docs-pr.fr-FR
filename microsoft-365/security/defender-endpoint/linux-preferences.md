---
title: Définir des préférences pour Microsoft Defender pour le point de terminaison sur Linux
ms.reviewer: null
description: Décrit comment configurer Microsoft Defender pour endpoint sur Linux dans les entreprises.
keywords: 'microsoft, defender, Microsoft Defender pour le point de terminaison, linux, installation, déployer, désinstallation, préinstallation, ansible, linux, redhat, ubuntu, debian, sles, suse, centos'
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
---

# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Définir des préférences pour Microsoft Defender pour le point de terminaison sur Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Cette rubrique contient des instructions sur la façon de définir des préférences pour Defender pour Endpoint sur Linux dans les environnements d’entreprise. Si vous souhaitez configurer le produit sur un appareil à partir de la ligne de commande, voir [Ressources](linux-resources.md#configure-from-the-command-line).

Dans les environnements d’entreprise, Defender pour Point de terminaison sur Linux peut être géré via un profil de configuration. Ce profil est déployé à partir de l’outil de gestion de votre choix. Les préférences gérées par l’entreprise prévalent sur les préférences définies localement sur l’appareil. En d’autres termes, les utilisateurs de votre entreprise ne peuvent pas modifier les préférences définies par le biais de ce profil de configuration.

Cet article décrit la structure de ce profil (y compris un profil recommandé que vous pouvez utiliser pour commencer) et des instructions sur la façon de déployer le profil.

## <a name="configuration-profile-structure"></a>Structure de profil de configuration

Le profil de configuration est un fichier .json qui se compose d’entrées identifiées par une clé (qui indique le nom de la préférence), suivi d’une valeur, qui dépend de la nature de la préférence. Les valeurs peuvent être simples, telles qu’une valeur numérique, ou complexes, telles qu’une liste imbriée de préférences.

En règle générale, vous utilisez un outil de gestion de la configuration pour pousser un fichier avec le nom ```mdatp_managed.json``` à l’emplacement ```/etc/opt/microsoft/mdatp/managed/```.

Le niveau supérieur du profil de configuration inclut les préférences et entrées à l’échelle du produit pour les sous-catégories du produit, qui sont expliquées plus en détail dans les sections suivantes.

### <a name="antivirus-engine-preferences"></a>Préférences du moteur antivirus

La *section antivirusEngine* du profil de configuration est utilisée pour gérer les préférences du composant antivirus du produit.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|antivirusEngine|
|**Type de données**|Dictionnaire (préférence imbriée)|
|**Comments**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

#### <a name="enforcement-level-for-antivirus-engine"></a>Niveau d’application pour le moteur antivirus

Spécifie la préférence d’application du moteur antivirus. Il existe trois valeurs pour définir le niveau d’application :

- En temps réel (`real_time`) : la protection en temps réel (analyser les fichiers à mesure qu’ils sont accessibles) est activée.
- À la demande (`on_demand`) : les fichiers sont analysés uniquement à la demande. Dans les cas ci-après :
  - La protection en temps réel est désactivée.
- Passive (`passive`) : exécute le moteur antivirus en mode passif. Dans les cas ci-après :
  - La protection en temps réel est désactivée.
  - L’analyse à la demande est désactivée.
  - La correction automatique des menaces est désactivée.
  - Les mises à jour de l’intelligence de la sécurité sont allumées.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|enforcementLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|real_time (par défaut) <p> on_demand <p> passive|
|**Comments**|Disponible dans Defender pour Endpoint version 101.10.72 ou supérieure.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Activer/désactiver la surveillance du comportement 

Détermine si la fonctionnalité de surveillance et de blocage du comportement est activée ou non sur l’appareil. Pour améliorer l’efficacité de la protection de la sécurité, nous vous recommandons de maintenir cette fonctionnalité allumée.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|behaviorMonitoring|
|**Type de données**|Chaîne|
|**Valeurs possibles**|désactivé <p> activé (par défaut)|
|**Comments**|Disponible dans Defender pour Endpoint version 101.45.00 ou supérieure.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Exécuter une analyse après la mise à jour des définitions

Spécifie s’il faut démarrer une analyse de processus après le téléchargement des nouvelles mises à jour de l’intelligence de sécurité sur l’appareil. L’activation de ce paramètre déclenche une analyse antivirus sur les processus en cours d’exécution de l’appareil.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|scanAfterDefinitionUpdate|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (par défaut) <p> false|
|**Comments**|Disponible dans Defender pour Endpoint version 101.45.00 ou supérieure.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Analyser les archives (analyses antivirus à la demande uniquement)

Spécifie s’il faut analyser les archives pendant les analyses antivirus à la demande.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|scanArchives|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (par défaut) <p> false|
|**Comments**|Disponible dans Microsoft Defender pour Endpoint version 101.45.00 ou supérieure.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Degré de parallélisme pour les analyses à la demande

Spécifie le degré de parallélisme pour les analyses à la demande. Cela correspond au nombre de threads utilisés pour effectuer l’analyse et a une incidence sur l’utilisation du processeur, ainsi que sur la durée de l’analyse à la demande.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|maximumOnDemandScanThreads|
|**Type de données**|Entier|
|**Valeurs possibles**|2 (par défaut). Les valeurs autorisées sont desgers entre 1 et 64.|
|**Comments**|Disponible dans Microsoft Defender pour Endpoint version 101.45.00 ou supérieure.|
|||
  

#### <a name="exclusion-merge-policy"></a>Stratégie de fusion d’exclusions

Spécifie la stratégie de fusion pour les exclusions. Il peut s’agit d’une combinaison d’exclusions définies par l’administrateur et d’exclusions définies par l’utilisateur (`merge`) ou uniquement d’exclusions définies par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres exclusions.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|exclusionsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Comments**|Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure.|
|

#### <a name="scan-exclusions"></a>Exclusions d’analyse

Entités exclues de l’analyse. Les exclusions peuvent être spécifiées par des chemins d’accès complets, des extensions ou des noms de fichiers.
(Les exclusions sont spécifiées en tant que tableau d’éléments, l’administrateur peut spécifier autant d’éléments que nécessaire, dans n’importe quel ordre.)

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|exclusions|
|**Type de données**|Dictionnaire (préférence imbriée)|
|**Comments**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

##### <a name="type-of-exclusion"></a>Type d’exclusion

Spécifie le type de contenu exclu de l’analyse.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|$type|
|**Type de données**|Chaîne|
|**Valeurs possibles**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Chemin d’accès au contenu exclu

Utilisé pour exclure le contenu de l’analyse par chemin d’accès complet au fichier.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|chemin|
|**Type de données**|Chaîne|
|**Valeurs possibles**|chemins d’accès valides|
|**Comments**|Applicable uniquement si *$type* est *excluPath*|
|

##### <a name="path-type-file--directory"></a>Type de chemin d’accès (fichier/répertoire)

Indique si la propriété *du chemin d’accès* fait référence à un fichier ou un répertoire.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|isDirectory|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|false (par défaut) <p> true|
|**Comments**|Applicable uniquement si *$type* est *excluPath*|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Extension de fichier exclue de l’analyse

Utilisé pour exclure le contenu de l’analyse par extension de fichier.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|extension|
|**Type de données**|Chaîne|
|**Valeurs possibles**|extensions de fichier valides|
|**Comments**|Applicable uniquement si *$type* *est excluFileExtension*|
|

##### <a name="process-excluded-from-the-scan"></a>Processus exclu de l’analyse*

Spécifie un processus pour lequel toute l’activité de fichier est exclue de l’analyse. Le processus peut être spécifié par son nom (par exemple) `cat`ou son chemin d’accès complet (par exemple, `/bin/cat`).

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|nom|
|**Type de données**|Chaîne|
|**Valeurs possibles**|n’importe quelle chaîne|
|**Comments**|Applicable uniquement *si $type* est *excluFileName*|
|

#### <a name="allowed-threats"></a>Menaces autorisées

Liste des menaces (identifiées par leur nom) qui ne sont pas bloquées par le produit et sont autorisées à s’exécuter.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|allowedThreats|
|**Type de données**|Tableau de chaînes|
|

#### <a name="disallowed-threat-actions"></a>Actions de menace non autorisées

Limite les actions que l’utilisateur local d’un appareil peut prendre lorsque des menaces sont détectées. Les actions incluses dans cette liste ne sont pas affichées dans l’interface utilisateur.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|disallowedThreatActions|
|**Type de données**|Tableau de chaînes|
|**Valeurs possibles**|autoriser (empêche les utilisateurs d’autoriser les menaces) <p> restaurer (empêche les utilisateurs de restaurer les menaces de la quarantaine)|
|**Comments**|Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure.|
|

#### <a name="threat-type-settings"></a>Paramètres des types de menaces

La *préférence threatTypeSettings dans* le moteur antivirus est utilisée pour contrôler la façon dont certains types de menaces sont gérés par le produit.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|threatTypeSettings|
|**Type de données**|Dictionnaire (préférence imbriée)|
|**Comments**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

##### <a name="threat-type"></a>Type de menace

Type de menace pour lequel le comportement est configuré.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|clé|
|**Type de données**|Chaîne|
|**Valeurs possibles**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Action

Action à prendre en cas de menace du type spécifié dans la section précédente. Peut être :

- **Audit** : l’appareil n’est pas protégé contre ce type de menace, mais une entrée sur la menace est enregistrée.
- **Bloc** : l’appareil est protégé contre ce type de menace et vous êtes averti dans la console de sécurité.
- **Off** : l’appareil n’est pas protégé contre ce type de menace et rien n’est enregistré.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|valeur|
|**Type de données**|Chaîne|
|**Valeurs possibles**|audit (par défaut) <p> block <p> off|
|

#### <a name="threat-type-settings-merge-policy"></a>Stratégie de fusion des paramètres du type de menace

Spécifie la stratégie de fusion pour les paramètres de type de menace. Il peut s’agit d’une combinaison de paramètres définis par l’administrateur et de paramètres définis par l’utilisateur (`merge`) ou uniquement de paramètres définis par l’administrateur (`admin_only`). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres paramètres pour différents types de menaces.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|threatTypeSettingsMergePolicy|
|**Type de données**|Chaîne|
|**Valeurs possibles**|merge (par défaut) <p> admin_only|
|**Comments**|Disponible dans Defender pour Endpoint version 100.83.73 ou supérieure.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Conservation de l’historique d’analyse antivirus (en jours)

Spécifiez le nombre de jours pendant combien de jours les résultats sont conservés dans l’historique d’analyse sur l’appareil. Les anciens résultats d’analyse sont supprimés de l’historique. Anciens fichiers mis en quarantaine qui sont également supprimés du disque.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|scanResultsRetentionDays|
|**Type de données**|Chaîne|
|**Valeurs possibles**|90 (valeur par défaut). Les valeurs autorisées sont de 1 jour à 180 jours.|
|**Comments**|Disponible dans Defender pour Endpoint version 101.04.76 ou supérieure.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Nombre maximal d’éléments dans l’historique d’analyse antivirus

Spécifiez le nombre maximal d’entrées à conserver dans l’historique d’analyse. Les entrées incluent toutes les analyses à la demande effectuées dans le passé et toutes les détections antivirus.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|scanHistoryMaximumItems|
|**Type de données**|Chaîne|
|**Valeurs possibles**|10000 (valeur par défaut). Les valeurs autorisées sont de 5 000 à 1 5 000 éléments.|
|**Comments**|Disponible dans Defender pour Endpoint version 101.04.76 ou supérieure.|
|

### <a name="cloud-delivered-protection-preferences"></a>Préférences de protection dans le cloud

*L’entrée cloudService* dans le profil de configuration est utilisée pour configurer la fonctionnalité de protection pilotée par le cloud du produit.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|cloudService|
|**Type de données**|Dictionnaire (préférence imbriée)|
|**Comments**|Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Activer/désactiver la protection cloud

Détermine si la protection cloud est activée ou non sur l’appareil. Pour améliorer la sécurité de vos services, nous vous recommandons de maintenir cette fonctionnalité allumée.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|activé|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (par défaut) <p> false|
|

#### <a name="diagnostic-collection-level"></a>Niveau de collecte de diagnostics

Les données de diagnostic sont utilisées pour sécuriser et mettre à jour Defender for Endpoint, détecter, diagnostiquer et résoudre les problèmes, ainsi que pour améliorer les produits. Ce paramètre détermine le niveau de diagnostics envoyés par le produit à Microsoft.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|diagnosticLevel|
|**Type de données**|Chaîne|
|**Valeurs possibles**|facultatif (par défaut) <p> obligatoire|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Activer/désactiver les envois automatiques d’échantillons

Détermine si des échantillons suspects (susceptibles de contenir des menaces) sont envoyés à Microsoft. Il existe trois niveaux pour contrôler l’envoi d’échantillons :

- **Aucun** : aucun échantillon suspect n’est envoyé à Microsoft.
- **Coffre** : seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut pour ce paramètre.
- **Tous** : tous les échantillons suspects sont envoyés à Microsoft.

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|automaticSampleSubmissionConsent|
|**Type de données**|Chaîne|
|**Valeurs possibles**|none <p> safe (par défaut) <p> all|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Activer/désactiver les mises à jour automatiques de l’intelligence de sécurité

Détermine si les mises à jour d’informations de sécurité sont installées automatiquement :

<br>

****

|Description|Valeur|
|---|---|
|**Clé**|automaticDefinitionUpdateEnabled|
|**Type de données**|Valeur booléenne|
|**Valeurs possibles**|true (par défaut) <p> false|
|

## <a name="recommended-configuration-profile"></a>Profil de configuration recommandé

Pour commencer, nous recommandons le profil de configuration suivant pour votre entreprise afin de tirer parti de toutes les fonctionnalités de protection que Defender pour Endpoint fournit.

Le profil de configuration suivant :

- Activer la protection en temps réel (RTP)
- Spécifiez la façon dont les types de menaces suivants sont gérés :
  - **Les applications potentiellement indésirables (PUA) sont** bloquées
  - **Les archives** archivées (fichier avec un taux de compression élevé) sont auditées dans les journaux du produit
- Activer les mises à jour automatiques des informations de sécurité
- Protection fournie par le cloud
- Activer l’envoi automatique d’échantillons au `safe` niveau
- Activer la surveillance du comportement

### <a name="sample-profile"></a>Exemple de profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
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

## <a name="full-configuration-profile-example"></a>Exemple de profil de configuration complète

Le profil de configuration suivant contient des entrées pour tous les paramètres décrits dans ce document et peut être utilisé pour des scénarios plus avancés où vous souhaitez contrôler davantage le produit.

### <a name="full-profile"></a>Profil complet

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
      "enforcementLevel":"real_time",
      "scanAfterDefinitionUpdate":true,
      "scanArchives":true,
      "maximumOnDemandScanThreads":2,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/run"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home/*/git"
         },
         {
            "$type":"excludedFileExtension",
            "extension":".pdf"
         },
         {
            "$type":"excludedFileName",
            "name":"cat"
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

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Ajouter une balise ou un ID de groupe au profil de configuration

Lorsque vous exécutez la `mdatp health` commande pour la première fois, la valeur de la balise et de l’ID de groupe est vide. Pour ajouter une balise ou un ID de groupe au `mdatp_managed.json` fichier, suivez les étapes ci-dessous :
  
  1. Ouvrez le profil de configuration à partir du chemin d’accès `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Descendez jusqu’au bas du fichier, où se `cloudService` trouve le bloc.
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
  > N’oubliez pas d’ajouter la virgule après le crochet fermant à la fin du `cloudService` bloc. Assurez-vous également qu’il existe deux crochets fermants après l’ajout d’un bloc Balise ou ID de groupe (voir l’exemple ci-dessus). Pour le moment, le seul nom de clé pris en charge pour les balises est `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Validation du profil de configuration

Le profil de configuration doit être un fichier au format JSON valide. Il existe un certain nombre d’outils qui peuvent être utilisés pour vérifier cela. Par exemple, si vous avez `python` installé sur votre appareil :

```bash
python -m json.tool mdatp_managed.json
```

Si le JSON est bien formé, la commande ci-dessus le renvoie au Terminal et renvoie un code de sortie de `0`. Sinon, une erreur qui décrit le problème s’affiche et la commande renvoie un code de sortie de `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>Vérifier que le fichier mdatp_managed.json fonctionne comme prévu

Pour vérifier que votre /etc/opt/microsoft/mdatp/managed/mdatp_managed.json fonctionne correctement, vous devez voir « [géré] » en regard de ces paramètres :

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> Pour que le mdatp_managed.json prenne effet, aucun redémarrage `mdatp` du deamon n’est requis.

## <a name="configuration-profile-deployment"></a>Déploiement de profil de configuration

Une fois que vous avez créé le profil de configuration pour votre entreprise, vous pouvez le déployer via l’outil de gestion que votre entreprise utilise. Defender for Endpoint sur Linux lit la configuration gérée à partir du *fichier /etc/opt/microsoft/mdatp/managed/mdatp_managed.json* .
