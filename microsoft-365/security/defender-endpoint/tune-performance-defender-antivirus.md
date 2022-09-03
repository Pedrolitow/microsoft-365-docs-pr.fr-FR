---
title: Analyseur de performances pour l’antivirus Microsoft Defender
description: Décrit la procédure permettant d’optimiser les performances de l’antivirus Microsoft Defender.
keywords: tune, performances, microsoft defender pour point de terminaison, antivirus defender
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.date: 08/13/2022
manager: dansimp
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 155a335dc0d3a744b226e59551bfd0da732366ca
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67577847"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Analyseur de performances pour l’antivirus Microsoft Defender

**S’applique à**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**

- Windows

## <a name="what-is-microsoft-defender-antivirus-performance-analyzer"></a>Qu’est-ce que l’analyseur de performances de l’Antivirus Microsoft Defender ?

Dans certains cas, vous devrez peut-être optimiser les performances de l’Antivirus Microsoft Defender lors de l’analyse de fichiers et de dossiers spécifiques. L’analyseur de performances est un outil en ligne de commande PowerShell qui permet de déterminer quels fichiers, extensions de fichiers et processus peuvent entraîner des problèmes de performances sur des points de terminaison individuels. Ces informations peuvent être utilisées pour mieux évaluer les problèmes de performances et appliquer des actions de correction.

Voici quelques options à analyser :

- Principaux chemins qui impactent le temps d’analyse
- Principaux fichiers ayant un impact sur le temps d’analyse
- Principaux processus ayant un impact sur le temps d’analyse
- Principales extensions de fichier ayant un impact sur le temps d’analyse
- Combinaisons , par exemple :
  - fichiers supérieurs par extension
  - chemins supérieurs par extension
  - processus supérieurs par chemin d’accès
  - principales analyses par fichier
  - top scans per file per process
  
## <a name="running-performance-analyzer"></a>Exécution de l’analyseur de performances

Le processus général d’exécution de l’analyseur de performances implique les étapes suivantes :

1. Exécutez l’analyseur de performances pour collecter un enregistrement des performances des événements antivirus Microsoft Defender sur le point de terminaison.

   > [!NOTE]
   > Les performances des événements antivirus Microsoft Defender de type **Microsoft-Antimalware-Engine** sont enregistrées via l’analyseur de performances.

2. Analysez les résultats de l’analyse à l’aide de différents rapports d’enregistrement.

## <a name="using-performance-analyzer"></a>Utilisation de l’analyseur de performances

Pour démarrer l’enregistrement des événements système, ouvrez PowerShell en mode administratif et effectuez les étapes suivantes :

1. Exécutez la commande suivante pour démarrer l’enregistrement :

   `New-MpPerformanceRecording -RecordTo <recording.etl>`

    où `-RecordTo` le paramètre spécifie l’emplacement de chemin d’accès complet dans lequel le fichier de trace est enregistré. Pour plus d’informations sur les applets de commande, consultez les [applets de commande antivirus Microsoft Defender](/powershell/module/defender).

2. Si des processus ou des services sont considérés comme affectant les performances, reproduisez la situation en effectuant les tâches pertinentes.

3. Appuyez sur **Entrée** pour arrêter et enregistrer l’enregistrement, ou **sur Ctrl+C** pour annuler l’enregistrement.

4. Analysez les résultats à l’aide du paramètre de l’analyseur de `Get-MpPerformanceReport`performances. Par exemple, lors de l’exécution de la commande `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`, l’utilisateur reçoit une liste des dix premières analyses pour les 3 principaux fichiers affectant les performances.

Pour plus d’informations sur les paramètres et les options de ligne de commande, consultez [New-MpPerformanceRecording](#new-mpperformancerecording) et [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> Lors de l’exécution d’un enregistrement, si vous obtenez l’erreur « Impossible de démarrer l’enregistrement des performances, car l’enregistreur de performances Windows est déjà en cours d’enregistrement », exécutez la commande suivante pour arrêter la trace existante avec la nouvelle commande : **wpr -cancel -instancename MSFT_MpPerformanceRecording**

## <a name="performance-tuning-data-and-information"></a>Données et informations sur l’optimisation des performances

En fonction de la requête, l’utilisateur peut afficher les données pour le nombre d’analyses, la durée (total/min/moyenne/max/médiane), le chemin d’accès, le processus et **la raison de l’analyse**. L’image ci-dessous montre l’exemple de sortie d’une requête simple des 10 premiers fichiers pour l’impact de l’analyse.

:::image type="content" source="images/example-output.png" alt-text="Exemple de sortie pour une requête TopFiles de base" lightbox="images/example-output.png":::

## <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Fonctionnalités supplémentaires : exportation et conversion en CSV et JSON

Les résultats de l’analyseur de performances peuvent également être exportés et convertis dans un fichier CSV ou JSON.
Pour obtenir des exemples décrivant le processus d'« exportation » et de « conversion » par le biais d’exemples de codes, voir ci-dessous.

À compter de Defender version 4.18.2206.X, les utilisateurs pourront afficher les informations de raison de l’analyse ignorée sous la colonne « SkipReason ». Les valeurs possibles sont les suivantes :

1. Non ignoré
1. Optimisation (généralement pour des raisons de performances)
1. Utilisateur ignoré (généralement en raison d’exclusions de jeu d’utilisateurs)

### <a name="for-csv"></a>Pour CSV

- **Pour exporter** : `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Pour convertir** : `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

### <a name="for-json"></a>Pour JSON

- **Pour convertir** : `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

Pour garantir une sortie lisible par l’ordinateur pour l’exportation avec d’autres systèmes de traitement des données, il est recommandé d’utiliser le paramètre -Raw pour Get-MpPerformanceReport. Voir ci-dessous pour plus d’informations

## <a name="requirements"></a>Conditions requises

L’analyseur de performances de l’Antivirus Microsoft Defender présente les prérequis suivants :

- Versions windows prises en charge : Windows 10, Windows 11 et Windows Server 2016 et versions ultérieures
- Version de la plateforme : 4.18.2108.7+
- Version de PowerShell : PowerShell version 5.1, PowerShell ISE, Remote PowerShell (4.18.2201.10+), PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>Informations de référence sur PowerShell

Deux nouvelles applets de commande PowerShell sont utilisées pour optimiser les performances de l’antivirus Microsoft Defender :

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)

### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

La section suivante décrit la référence de la nouvelle applet de commande PowerShell New-MpPerformanceRecording. Cette applet de commande collecte un enregistrement des performances des analyses de l’Antivirus Microsoft Defender.

#### <a name="syntax-new-mpperformancerecording"></a>Syntaxe : New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Description : New-MpPerformanceRecording

L’applet `New-MpPerformanceRecording` de commande collecte un enregistrement des performances des analyses de l’Antivirus Microsoft Defender. Ces enregistrements de performances contiennent des événements de processus du noyau Microsoft-Antimalware-Engine et NT et peuvent être analysés après la collecte à l’aide de l’applet de commande [Get-MpPerformanceReport](#get-mpperformancereport) .

Cette `New-MpPerformanceRecording` applet de commande fournit un aperçu des fichiers problématiques susceptibles de provoquer une dégradation des performances de l’antivirus Microsoft Defender. Cet outil est fourni « AS IS » et n’est pas destiné à fournir des suggestions sur les exclusions. Les exclusions peuvent réduire le niveau de protection sur vos points de terminaison. Les exclusions, le cas échéant, doivent être définies avec précaution.

Pour plus d’informations sur l’analyseur de performances, consultez [Analyseur de performances](/windows-hardware/test/wpt/windows-performance-analyzer) documentation.

> [!IMPORTANT]
> Cette applet de commande nécessite des privilèges d’administrateur élevés.

**Versions de système d’exploitation prises en charge** :

Windows version 10 et ultérieure.

> [!NOTE]
> Cette fonctionnalité est disponible à partir de la plateforme version 4.18.2108.X et ultérieure.

#### <a name="examples-new-mpperformancerecording"></a>Exemples : New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Exemple 1 : Collecter un enregistrement de performances et l’enregistrer

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

La commande ci-dessus collecte un enregistrement de performances et l’enregistre dans le chemin d’accès spécifié : **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>Exemple 2 : Collecter un enregistrement des performances pour une session PowerShell distante

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

La commande ci-dessus collecte un enregistrement des performances sur Server02 (comme spécifié par l’argument $s de session de paramètre) et l’enregistre dans le chemin d’accès spécifié : **C:\LocalPathOnServer02\trace.etl** sur Server02.

##### <a name="example-3-collect-a-performance-recording-in-non-interactive-mode"></a>Exemple 3 : Collecter un enregistrement de performances en mode non interactif

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl -Seconds 60
```

La commande ci-dessus collecte un enregistrement des performances pour la durée en secondes spécifiée par le paramètre -Seconds. Ceci est recommandé pour les utilisateurs qui effectuent des regroupements par lots qui ne nécessitent aucune interaction ou invite.

#### <a name="parameters-new-mpperformancerecording"></a>Paramètres : New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo

Spécifie l’emplacement dans lequel enregistrer l’enregistrement des performances de Microsoft Defender Antimalware.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session

Spécifie l’objet PSSession dans lequel créer et enregistrer l’enregistrement des performances de l’Antivirus Microsoft Defender. Lorsque vous utilisez ce paramètre, le paramètre RecordTo fait référence au chemin d’accès local sur l’ordinateur distant. Disponible avec la plateforme Defender version 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-seconds"></a>-Secondes

Spécifie la durée de l’enregistrement des performances en secondes. Ceci est recommandé pour les utilisateurs qui effectuent des regroupements par lots qui ne nécessitent aucune interaction ou invite.

```yaml
Type: Int32
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

La section suivante décrit la Get-MpPerformanceReport cmdlet PowerShell. Analyse et signale l’enregistrement des performances de l’Antivirus Microsoft Defender.

#### <a name="syntax-get-mpperformancereport"></a>Syntaxe : Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
    [-TopScans [<Int32>]]
    [-TopPaths [<Int32>] [-TopPathsDepth [<Int32>]]]
            [-TopScansPerPath [<Int32>]]
            [-TopFilesPerPath [<Int32>]
                    [-TopScansPerFilePerPath [<Int32>]]
                    ]
            [-TopExtensionsPerPath [<Int32>]
                    [-TopScansPerExtensionPerPath [<Int32>]]
                    ]
            [-TopProcessesPerPath [<Int32>]
                    [-TopScansPerProcessPerPath [<Int32>]]
                    ]
            ]
    [-TopFiles [<Int32>]
            [-TopScansPerFile [<Int32>]]
            [-TopProcessesPerFile [<Int32>]
                    [-TopScansPerProcessPerFile [<Int32>]]
                    ]
            ]
    [-TopExtensions [<Int32>]
            [-TopScansPerExtension [<Int32>]
            [-TopPathsPerExtension [<Int32>] [-TopPathsDepth [<Int32>]]
                    [-TopScansPerPathPerExtension [<Int32>]]
                    ]
            [-TopProcessesPerExtension [<Int32>]
                    [-TopScansPerProcessPerExtension [<Int32>]]
                    ]
            [-TopFilesPerExtension [<Int32>]
                    [-TopScansPerFilePerExtension [<Int32>]]
                    ]
            ]
    [-TopProcesses [<Int32>]
            [-TopScansPerProcess [<Int32>]]
            [-TopExtensionsPerProcess [<Int32>]
                    [-TopScansPerExtensionPerProcess [<Int32>]]
                    ]
            [-TopPathsPerProcess [<Int32>] [-TopPathsDepth [<Int32>]]
                    [-TopScansPerPathPerProcess [<Int32>]]
                    ]
            [-TopFilesPerProcess [<Int32>]
                    [-TopScansPerFilePerProcess [<Int32>]]
                    ]
            ]
    [-MinDuration <String>]
    [-Raw]

```

#### <a name="description-get-mpperformancereport"></a>Description : Get-MpPerformanceReport

L’applet `Get-MpPerformanceReport` de commande analyse un enregistrement des performances de l’Antivirus Microsoft Defender précédemment collecté ([New-MpPerformanceRecording](#new-mpperformancerecording)) et signale les chemins d’accès aux fichiers, les extensions de fichier et les processus qui ont le plus d’impact sur les analyses antivirus Microsoft Defender.

L’analyseur de performances fournit un aperçu des fichiers problématiques qui peuvent entraîner une dégradation des performances de l’antivirus Microsoft Defender. Cet outil est fourni « AS IS » et n’est pas destiné à fournir des suggestions sur les exclusions. Les exclusions peuvent réduire le niveau de protection sur vos points de terminaison. Les exclusions, le cas échéant, doivent être définies avec précaution.

Pour plus d’informations sur l’analyseur de performances, consultez [Analyseur de performances](/windows-hardware/test/wpt/windows-performance-analyzer) documentation.

**Versions de système d’exploitation prises en charge** :

Windows version 10 et ultérieure.

> [!NOTE]
> Cette fonctionnalité est disponible à partir de la plateforme version 4.18.2108.X et ultérieure.

#### <a name="examples-get-mpperformancereport"></a>Exemples : Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Exemple 1 : requête unique

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Exemple 2 : Plusieurs requêtes

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Exemple 3 : Requêtes imbriqués

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Exemple 4 : Utilisation du paramètre -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

##### <a name="example-5-using--raw-parameter"></a>Exemple 5 : Utilisation du paramètre -Raw

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10 -Raw | ConvertTo-Json
```

L’utilisation \-de Raw dans la commande ci-dessus spécifie que la sortie doit être lisible par l’ordinateur et facilement convertible en formats de sérialisation tels que JSON

#### <a name="parameters-get-mpperformancereport"></a>Paramètres : Get-MpPerformanceReport

##### <a name="-toppaths"></a>-TopPaths

Demande un rapport de chemins d’accès supérieurs et spécifie le nombre de chemins supérieurs à générer, triés par « Durée ». Agrège les analyses en fonction de leur chemin d’accès et de leur répertoire. L’utilisateur peut spécifier le nombre de répertoires à afficher sur chaque niveau et la profondeur de la sélection.

- Type : Int32
- Position : Nommée
- Valeur par défaut : Aucun
- Accepter l’entrée de pipeline : False
- Accepter les caractères génériques : False

##### <a name="-toppathsdepth"></a>-TopPathsDepth

Spécifie la profondeur récursive qui sera utilisée pour regrouper et afficher les résultats agrégés du chemin d’accès. Par exemple, « C :\" correspond à une profondeur de 1 , « C:\Users\Foo » correspond à une profondeur de 3.

Cet indicateur peut accompagner toutes les autres options de chemin d’accès supérieur. En cas d’absence, la valeur par défaut 3 est supposée. La valeur ne peut pas être 0.

- Type : Int32
- Position : Nommée
- Valeur par défaut : 3
- Accepter l’entrée de pipeline : False
- Accepter les caractères génériques : False

| flag | Définition |
|:---|:---|  
|  -**TopScansPerPath** | Spécifie comment les analyses supérieures peuvent être spécifiées pour chaque chemin d’accès supérieur. |
|  -**TopFilesPerPath** | Spécifie comment les fichiers supérieurs peuvent être spécifiés pour chaque chemin d’accès supérieur. |
|  -**TopScansPerFilePerPath** | Spécifie le nombre d’analyses principales à générer pour chaque fichier supérieur pour chaque chemin d’accès supérieur, trié par « Durée ». |
|  -**TopExtensionsPerPath** | Spécifie le nombre d’extensions principales à générer pour chaque chemin d’accès supérieur |
|  -**TopScansPerExtensionPerPath** | Spécifie le nombre d’analyses principales à générer pour chaque extension supérieure pour chaque chemin d’accès supérieur |
|  -**TopProcessesPerPath** | Spécifie le nombre de processus principaux à générer pour chaque chemin d’accès supérieur |
|  -**TopScansPerProcessPerPath** | Spécifie le nombre d’analyses principales à générer pour chaque processus supérieur pour chaque chemin d’accès supérieur |
|  -**TopPathsPerExtension** | Spécifie le nombre de chemins supérieurs à générer pour chaque extension supérieure |
|  -**TopScansPerPathPerExtension** | Spécifie le nombre d’analyses principales à générer pour chaque chemin d’accès supérieur pour chaque extension supérieure |
|  -**TopPathsPerProcess** | Spécifie le nombre de chemins supérieurs à générer pour chaque processus supérieur |
|  -**TopScansPerPathPerProcess** | Spécifie le nombre d’analyses principales à générer pour chaque chemin d’accès supérieur pour chaque processus supérieur |

##### <a name="-minduration"></a>-MinDuration

Spécifie la durée minimale de toute analyse ou durée totale d’analyse des fichiers, extensions et processus inclus dans le rapport ; accepte des valeurs telles que  **0,1234567sec**, **0,1234ms**, **0,1us** ou un timeSpan valide.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-path"></a>-Chemin d’accès

Spécifie le ou les chemins d’accès à un ou plusieurs emplacements.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

##### <a name="-raw"></a>-Brut

Spécifie que la sortie de l’enregistrement des performances doit être lisible par l’ordinateur et facilement convertible en formats de sérialisation tels que JSON (par exemple, via la commande Convert-to-JSON). Ceci est recommandé pour les utilisateurs intéressés par le traitement par lots avec d’autres systèmes de traitement des données.

```yaml
Type: <SwitchParameter>
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensions"></a>-TopExtensions

Spécifie le nombre d’extensions principales à générer, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess

Spécifie le nombre d’extensions principales à générer pour chaque processus supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfiles"></a>-TopFiles

Demande un rapport top-files et spécifie le nombre de fichiers principaux à générer, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperextension"></a>-TopFilesPerExtension

Spécifie le nombre de fichiers principaux à générer pour chaque extension supérieure, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperprocess"></a>-TopFilesPerProcess

Spécifie le nombre de fichiers principaux à générer pour chaque processus supérieur, trié par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocesses"></a>-TopProcesses

Demande un rapport de processus supérieurs et spécifie le nombre de processus principaux à générer, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension

Spécifie le nombre de processus principaux à générer pour chaque extension supérieure, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperfile"></a>-TopProcessesPerFile

Spécifie le nombre de processus principaux à générer pour chaque fichier supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscans"></a>-TopScans

Demande un rapport d’analyses supérieures et spécifie le nombre d’analyses principales à générer, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextension"></a>-TopScansPerExtension

Spécifie le nombre d’analyses principales à générer pour chaque extension supérieure, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess

Spécifie le nombre d’analyses principales à générer pour chaque extension supérieure pour chaque processus supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfile"></a>-TopScansPerFile

Spécifie le nombre d’analyses principales à générer pour chaque fichier supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension

Spécifie le nombre d’analyses principales à générer pour chaque fichier supérieur pour chaque extension supérieure, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess

Spécifie le nombre d’analyses principales de sortie pour chaque fichier supérieur pour chaque processus supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocess"></a>-TopScansPerProcess

Spécifie le nombre d’analyses principales à générer pour chaque processus supérieur dans le rapport Processus principaux, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension

Spécifie le nombre d’analyses principales de sortie pour chaque processus supérieur pour chaque extension supérieure, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile

Spécifie le nombre d’analyses principales de sortie pour chaque processus supérieur pour chaque fichier supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## <a name="additional-resources"></a>Ressources supplémentaires

Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :

- [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
- [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
- [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
- [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
- [Configurer Defender pour point de terminaison sur les fonctionnalités](android-configure.md)-  Android [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
