---
title: Définir des préférences pour Microsoft Defender pour le point de terminaison sur Mac
description: Configurez MMicrosoft Defender pour endpoint sur Mac dans les organisations d’entreprise.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, gestion, préférences, entreprise, intune, jamf, macos,pératin, mojave, high sierra
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
ms.openlocfilehash: b706cb8dbd43d545768c1c573021b5ef401e3c09
ms.sourcegitcommit: 94e64afaf12f3d8813099d8ffa46baba65772763
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52346401"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>Définir des préférences pour Microsoft Defender pour le point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison macOS](microsoft-defender-endpoint-mac.md)

>[!IMPORTANT]
>Cet article contient des instructions sur la façon de définir des préférences pour Microsoft Defender pour Endpoint sur macOS dans les organisations d’entreprise. Pour configurer Microsoft Defender pour endpoint sur macOS à l’aide de l’interface de ligne de commande, voir [Resources](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Résumé

Dans les organisations d’entreprise, Microsoft Defender pour Endpoint sur macOS peut être géré via un profil de configuration déployé à l’aide de l’un des outils de gestion. Les préférences gérées par votre équipe en charge des opérations de sécurité prévalent sur les préférences définies localement sur l’appareil. La modification des préférences définies par le biais du profil de configuration nécessite des privilèges escalades et n’est pas disponible pour les utilisateurs sans autorisations administratives.

Cet article décrit la structure du profil de configuration, inclut un profil recommandé que vous pouvez utiliser pour commencer et fournit des instructions sur la façon de déployer le profil.

## <a name="configuration-profile-structure"></a>Structure de profil de configuration

Le profil de configuration est un fichier *.plist* qui se compose d’entrées identifiées par une clé (qui indique le nom de la préférence), suivi d’une valeur, qui dépend de la nature de la préférence. Les valeurs peuvent être simples (par exemple, une valeur numérique) ou complexes, telles qu’une liste imbriée de préférences.

>[!CAUTION]
>La disposition du profil de configuration dépend de la console de gestion que vous utilisez. Les sections suivantes contiennent des exemples de profils de configuration pour JAMF et Intune.

Le niveau supérieur du profil de configuration inclut les préférences et entrées à l’échelle du produit pour les sous-catégories de Microsoft Defender pour le point de terminaison, qui sont expliquées plus en détail dans les sections suivantes.

### <a name="antivirus-engine-preferences"></a>Préférences du moteur antivirus

La *section antivirusEngine* du profil de configuration est utilisée pour gérer les préférences du composant antivirus de Microsoft Defender for Endpoint.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | antivirusEngine |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="enable--disable-real-time-protection"></a>Activer/désactiver la protection en temps réel

Spécifiez s’il faut activer la protection en temps réel, qui analyse les fichiers à mesure qu’ils sont accessibles.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | enableRealTimeProtection |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

#### <a name="enable--disable-passive-mode"></a>Activer/désactiver le mode passif

Spécifiez si le moteur antivirus s’exécute en mode passif. Le mode passif a les implications suivantes : 
- La protection en temps réel est désactivée
- L’analyse à la demande est désactivée
- La correction automatique des menaces est désactivée
- Les mises à jour de l’intelligence de la sécurité sont allumées
- L’icône du menu État est masquée

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | passiveMode |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | false (par défaut) <br/> true |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 100.67.60 ou supérieure. |

#### <a name="exclusion-merge-policy"></a>Stratégie de fusion d’exclusions

Spécifiez la stratégie de fusion pour les exclusions. Il peut s’agit d’une combinaison d’exclusions définies par l’administrateur et d’exclusions définies par l’utilisateur ( ) ou uniquement `merge` d’exclusions définies par l’administrateur ( `admin_only` ). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres exclusions.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | exclusionsMergePolicy |
| **Type de données** | Chaîne |
| **Valeurs possibles** | merge (par défaut) <br/> admin_only |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="scan-exclusions"></a>Analyser les exclusions

Spécifiez les entités exclues de l’analyse. Les exclusions peuvent être spécifiées par des chemins d’accès complets, des extensions ou des noms de fichiers.
(Les exclusions sont spécifiées en tant que tableau d’éléments, l’administrateur peut spécifier autant d’éléments que nécessaire, dans n’importe quel ordre.)

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | exclusions |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

##### <a name="type-of-exclusion"></a>Type d’exclusion

Spécifiez le contenu exclu de l’analyse par type.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | $type |
| **Type de données** | Chaîne |
| **Valeurs possibles** | excludedPath <br/> excludedFileExtension <br/> excludedFileName |

##### <a name="path-to-excluded-content"></a>Chemin d’accès au contenu exclu

Spécifiez le contenu exclu de l’analyse par le chemin d’accès complet du fichier.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | chemin |
| **Type de données** | Chaîne |
| **Valeurs possibles** | chemins d’accès valides |
| **Comments** | Applicable uniquement si *$type* est *excluPath* |

## <a name="supported-exclusion-types"></a>Types d’exclusion pris en charge

Le tableau suivant indique les types d’exclusion pris en charge par Defender pour Endpoint sur Mac.

Exclusion | Définition | Exemples
---|---|---
Extension de fichier | Tous les fichiers avec l’extension, n’importe où sur l’appareil | `.test`
Fichier | Un fichier spécifique identifié par le chemin d’accès complet | `/var/log/test.log`<br/>`/var/log/*.log`<br/>`/var/log/install.?.log`
Dossier | Tous les fichiers sous le dossier spécifié (de manière récursive) | `/var/log/`<br/>`/var/*/`
Processus | Un processus spécifique (spécifié par le chemin d’accès complet ou le nom de fichier) et tous les fichiers ouverts par celui-ci | `/bin/cat`<br/>`cat`<br/>`c?t`

> [!IMPORTANT]
> Les chemins ci-dessus doivent être des liens durs, et non symboliques, pour être correctement exclus. Vous pouvez vérifier si un chemin d’accès est un lien symbolique en exécutant `file <path-name>` .

Les exclusions de fichiers, de dossiers et de processus prisent en charge les caractères génériques suivants :

Caractère générique | Description | Exemple | Correspondances | Ne correspond pas
---|---|---|---|---
\* |    Correspond à n’importe quel nombre de caractères, y compris aucun (notez que lorsque ce caractère générique est utilisé à l’intérieur d’un chemin d’accès, il ne remplace qu’un seul dossier) | `/var/\*/\*.log` | `/var/log/system.log` | `/var/log/nested/system.log`
? | Correspond à n’importe quel caractère | `file?.log` | `file1.log`<br/>`file2.log` | `file123.log`

##### <a name="path-type-file--directory"></a>Type de chemin d’accès (fichier/répertoire)

Indiquez si la *propriété du* chemin d’accès fait référence à un fichier ou un répertoire. 

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | isDirectory |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | false (par défaut) <br/> true |
| **Comments** | Applicable uniquement si *$type* est *excluPath* |

##### <a name="file-extension-excluded-from-the-scan"></a>Extension de fichier exclue de l’analyse

Spécifiez le contenu exclu de l’analyse par extension de fichier.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | extension |
| **Type de données** | Chaîne |
| **Valeurs possibles** | extensions de fichier valides |
| **Comments** | Applicable uniquement si *$type* est *excluFileExtension* |

##### <a name="process-excluded-from-the-scan"></a>Processus exclu de l’analyse

Spécifiez un processus pour lequel toute l’activité de fichier est exclue de l’analyse. Le processus peut être spécifié par son nom (par exemple) ou son chemin d’accès complet `cat` (par exemple, `/bin/cat` ).

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | name |
| **Type de données** | Chaîne |
| **Valeurs possibles** | n’importe quelle chaîne |
| **Comments** | Applicable uniquement *si $type* est *excluFileName* |

#### <a name="allowed-threats"></a>Menaces autorisées

Spécifiez les menaces par nom qui ne sont pas bloquées par Defender pour endpoint sur Mac. Ces menaces seront autorisées à s’exécuter.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | allowedThreats |
| **Type de données** | Tableau de chaînes |

#### <a name="disallowed-threat-actions"></a>Actions contre les menaces nonallées

Limite les actions que l’utilisateur local d’un appareil peut prendre lorsque des menaces sont détectées. Les actions incluses dans cette liste ne sont pas affichées dans l’interface utilisateur.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | disallowedThreatActions |
| **Type de données** | Tableau de chaînes |
| **Valeurs possibles** | autoriser (empêche les utilisateurs d’autoriser les menaces) <br/> restaurer (empêche les utilisateurs de restaurer les menaces de la quarantaine) |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="threat-type-settings"></a>Paramètres du type de menace

Spécifiez comment certains types de menaces sont gérés par Microsoft Defender pour point de terminaison sur macOS.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | threatTypeSettings |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

##### <a name="threat-type"></a>Type de menace

Spécifiez les types de menaces.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | clé |
| **Type de données** | Chaîne |
| **Valeurs possibles** | potentially_unwanted_application <br/> archive_bomb |

##### <a name="action-to-take"></a>Mesures à prendre

Spécifiez l’action à prendre lorsqu’une menace du type spécifié dans la section précédente est détectée. Choisissez l'une des options suivantes :

- **Audit**: votre appareil n’est pas protégé contre ce type de menace, mais une entrée sur la menace est enregistrée.
- **Bloquer**: votre appareil est protégé contre ce type de menace et vous êtes averti dans l’interface utilisateur et la console de sécurité.
- **Off**: votre appareil n’est pas protégé contre ce type de menace et rien n’est enregistré.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | valeur |
| **Type de données** | Chaîne |
| **Valeurs possibles** | audit (par défaut) <br/> block <br/> off |

#### <a name="threat-type-settings-merge-policy"></a>Stratégie de fusion des paramètres du type de menace

Spécifiez la stratégie de fusion pour les paramètres de type de menace. Il peut s’agit d’une combinaison de paramètres définis par l’administrateur et de paramètres définis par l’utilisateur ( ) ou uniquement de `merge` paramètres définis par l’administrateur ( `admin_only` ). Ce paramètre peut être utilisé pour empêcher les utilisateurs locaux de définir leurs propres paramètres pour différents types de menaces.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | threatTypeSettingsMergePolicy |
| **Type de données** | Chaîne |
| **Valeurs possibles** | merge (valeur par défaut) <br/> admin_only |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 100.83.73 ou supérieure. |

#### <a name="antivirus-scan-history-retention-in-days"></a>Conservation de l’historique d’analyse antivirus (en jours)

Spécifiez le nombre de jours pendant combien de jours les résultats sont conservés dans l’historique d’analyse sur l’appareil. Les anciens résultats d’analyse sont supprimés de l’historique. Anciens fichiers mis en quarantaine qui sont également supprimés du disque.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | scanResultsRetentionDays |
| **Type de données** | Chaîne |
| **Valeurs possibles** | 90 (valeur par défaut). Les valeurs autorisées sont de 1 jour à 180 jours. |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 101.07.23 ou supérieure. |

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Nombre maximal d’éléments dans l’historique d’analyse antivirus

Spécifiez le nombre maximal d’entrées à conserver dans l’historique d’analyse. Les entrées incluent toutes les analyses à la demande effectuées dans le passé et toutes les détections antivirus.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | scanHistoryMaximumItems |
| **Type de données** | Chaîne |
| **Valeurs possibles** | 10000 (valeur par défaut). Les valeurs autorisées sont de 5 000 à 15 000 éléments. |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 101.07.23 ou supérieure. |

### <a name="cloud-delivered-protection-preferences"></a>Préférences de protection dans le cloud

Configurez les fonctionnalités de protection informatique de Microsoft Defender pour Endpoint sur macOS.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | cloudService |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="enable--disable-cloud-delivered-protection"></a>Activer/désactiver la protection cloud

Spécifiez s’il faut activer ou non la protection de l’appareil livrée par le cloud. Pour améliorer la sécurité de vos services, nous vous recommandons de maintenir cette fonctionnalité allumée.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | activé |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

#### <a name="diagnostic-collection-level"></a>Niveau de collection de diagnostics

Les données de diagnostic sont utilisées pour sécuriser et mettre à jour Microsoft Defender for Endpoint, détecter, diagnostiquer et résoudre les problèmes, ainsi que pour améliorer les produits. Ce paramètre détermine le niveau de diagnostics envoyés par Microsoft Defender pour endpoint à Microsoft.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | diagnosticLevel |
| **Type de données** | Chaîne |
| **Valeurs possibles** | facultatif (par défaut) <br/> obligatoire |

#### <a name="enable--disable-automatic-sample-submissions"></a>Activer/désactiver les envois automatiques d’échantillons

Détermine si des échantillons suspects (susceptibles de contenir des menaces) sont envoyés à Microsoft. Vous êtes invité à vous demander si le fichier envoyé est susceptible de contenir des informations personnelles.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | automaticSampleSubmission |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Activer/désactiver les mises à jour automatiques de l’intelligence de sécurité

Détermine si les mises à jour d’informations de sécurité sont installées automatiquement :

|Section|Valeur|
|:---|:---|
| **Clé** | automaticDefinitionUpdateEnabled |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | true (par défaut) <br/> false |

### <a name="user-interface-preferences"></a>Préférences de l’interface utilisateur

Gérez les préférences pour l’interface utilisateur de Microsoft Defender pour Endpoint sur macOS.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | userInterface |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="show--hide-status-menu-icon"></a>Afficher/masquer l’icône du menu d’état

Spécifiez s’il faut afficher ou masquer l’icône du menu d’état dans le coin supérieur droit de l’écran.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | hideStatusMenuIcon |
| **Type de données** | Valeur booléenne |
| **Valeurs possibles** | false (par défaut) <br/> true |

#### <a name="show--hide-option-to-send-feedback"></a>Afficher /masquer l’option d’envoi de commentaires

Spécifiez si les utilisateurs peuvent envoyer des commentaires à Microsoft en allant à `Help`  >  `Send Feedback` .

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | userInitiatedFeedback |
| **Type de données** | Chaîne |
| **Valeurs possibles** | activé (par défaut) <br/> désactivé |
| **Comments** | Disponible dans Microsoft Defender pour Endpoint version 101.19.61 ou supérieure. |

### <a name="endpoint-detection-and-response-preferences"></a>Préférences de détection et de réponse des points de terminaison

Gérez les préférences du composant protection évolutive des points de terminaison (PEPT) de Microsoft Defender pour Endpoint sur macOS.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | edr |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

#### <a name="device-tags"></a>Balises d’appareil

Spécifiez un nom de balise et sa valeur. 

- La balise GROUP balise l’appareil avec la valeur spécifiée. La balise est reflétée dans le portail sous la page de l’appareil et peut être utilisée pour le filtrage et le regroupement des appareils.

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | étiquettes |
| **Type de données** | Dictionnaire (préférence imbriée) |
| **Comments** | Consultez les sections suivantes pour obtenir une description du contenu du dictionnaire. |

##### <a name="type-of-tag"></a>Type de balise

Spécifie le type de balise

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | clé |
| **Type de données** | Chaîne |
| **Valeurs possibles** | `GROUP` |

##### <a name="value-of-tag"></a>Valeur de la balise

Spécifie la valeur de la balise

|Section|Valeur|
|:---|:---|
| **Domaine** | `com.microsoft.wdav` |
| **Clé** | valeur |
| **Type de données** | Chaîne |
| **Valeurs possibles** | n’importe quelle chaîne |

> [!IMPORTANT]  
> - Une seule valeur par type de balise peut être définie.
> - Le type de balises est unique et ne doit pas être répété dans le même profil de configuration.

## <a name="recommended-configuration-profile"></a>Profil de configuration recommandé

Pour commencer, nous recommandons la configuration suivante pour votre entreprise afin de tirer parti de toutes les fonctionnalités de protection que Microsoft Defender pour Endpoint fournit.

Le profil de configuration suivant (ou, dans le cas de JAMF, une liste de propriétés qui peut être téléchargée dans le profil de configuration des paramètres personnalisés) sera :
- Activer la protection en temps réel (RTP)
- Spécifiez la façon dont les types de menaces suivants sont gérés :
  - **Les applications potentiellement indésirables (PUA) sont** bloquées
  - **Les archives** archivées (fichier avec un taux de compression élevé) sont auditées dans Microsoft Defender pour les journaux de point de terminaison
- Activer les mises à jour automatiques des informations de sécurité
- Protection fournie par le cloud
- Activer l’envoi automatique d’échantillons

### <a name="property-list-for-jamf-configuration-profile"></a>Liste de propriétés pour le profil de configuration JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enableRealTimeProtection</key>
        <true/>
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

### <a name="intune-profile"></a>Profil Intune

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
                    <key>enableRealTimeProtection</key>
                    <true/>
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

## <a name="full-configuration-profile-example"></a>Exemple de profil de configuration complète

Les modèles suivants contiennent des entrées pour tous les paramètres décrits dans ce document et peuvent être utilisés pour des scénarios plus avancés dans lequel vous souhaitez mieux contrôler Microsoft Defender pour Endpoint sur macOS.

### <a name="property-list-for-jamf-configuration-profile"></a>Liste de propriétés pour le profil de configuration JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enableRealTimeProtection</key>
        <true/>
        <key>passiveMode</key>
        <false/>
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

### <a name="intune-profile"></a>Profil Intune

```XML
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
                    <key>enableRealTimeProtection</key>
                    <true/>
                    <key>passiveMode</key>
                    <false/>
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
```

## <a name="property-list-validation"></a>Validation de liste de propriétés

La liste des propriétés doit être un fichier *.plist* valide. Pour ce faire, exécutez :

```bash
plutil -lint com.microsoft.wdav.plist
```
```Output
com.microsoft.wdav.plist: OK
```

Si le fichier est bien formé, la commande ci-dessus produit `OK` et renvoie un code de sortie de `0` . Sinon, une erreur qui décrit le problème s’affiche et la commande renvoie un code de sortie de `1` .

## <a name="configuration-profile-deployment"></a>Déploiement de profil de configuration

Une fois que vous avez créé le profil de configuration pour votre entreprise, vous pouvez le déployer via la console de gestion que votre entreprise utilise. Les sections suivantes fournissent des instructions sur la façon de déployer ce profil à l’aide de JAMF et Intune.

### <a name="jamf-deployment"></a>Déploiement JAMF

À partir de la console JAMF, **ouvrez** profils de configuration ordinateurs, accédez au profil de configuration que vous souhaitez utiliser, puis sélectionnez Custom  >   **Paramètres**. Créez une entrée avec comme domaine de préférence `com.microsoft.wdav` et téléchargez *le .plist* produit précédemment.

>[!CAUTION]
>Vous devez entrer le domaine de préférence correct ( ) ; sinon, les préférences ne seront pas reconnues par `com.microsoft.wdav` Microsoft Defender pour le point de terminaison.

### <a name="intune-deployment"></a>Déploiement d’Intune

1. Ouvrez **Gérer**  >  **la configuration de l’appareil.** Sélectionnez **Gérer**  >  **les profils**  >  **créer un profil.**

2. Choisissez un nom pour le profil. Change **Platform=macOS** to **Profile type=Custom**. Sélectionnez Configurer.

3. Enregistrez le .plist produit précédemment sous `com.microsoft.wdav.xml` .

4. Entrez `com.microsoft.wdav` comme nom de profil de configuration **personnalisé.**

5. Ouvrez le profil de configuration et téléchargez le `com.microsoft.wdav.xml` fichier. (Ce fichier a été créé à l’étape 3.)

6. Sélectionnez **OK**.

7. Sélectionnez   >  **Gérer les affectations.** Dans **l’onglet** Inclure, sélectionnez Affecter à tous **les utilisateurs & tous les appareils.**

>[!CAUTION]
>Vous devez entrer le nom de profil de configuration personnalisé correct . Dans le cas contraire, ces préférences ne seront pas reconnues par Microsoft Defender pour endpoint.

## <a name="resources"></a>Ressources

- [Référence du profil de configuration (documentation Apple pour les développeurs)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
