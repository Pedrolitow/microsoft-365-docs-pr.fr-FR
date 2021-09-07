---
title: Analyseur de performances pour les Antivirus Microsoft Defender
description: Décrit la procédure à suivre pour régler les performances des Antivirus Microsoft Defender.
keywords: régler, performances, microsoft defender pour le point de terminaison, antivirus defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-smandalika
author: v-smandalika
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d38fe9f7c3bb19c946f97d00720cd8bf60c18f4c
ms.sourcegitcommit: a4e6a5a92ea527461a7835ddc83e2b01986e566b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2021
ms.locfileid: "58918367"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>Analyseur de performances pour les Antivirus Microsoft Defender

**Qu’est-ce Antivirus Microsoft Defender’analyseur de performances ?**

Dans certains cas, vous devrez peut-être régler les performances des Antivirus Microsoft Defender lors de l’analyse de fichiers et de dossiers spécifiques. L’analyseur de performances est un outil en ligne de commande PowerShell qui permet de déterminer quels fichiers, extensions de fichiers et processus peuvent être à l’origine de problèmes de performances sur des points de terminaison individuels. Ces informations peuvent être utilisées pour mieux évaluer les problèmes de performances et appliquer des actions de correction.

Voici quelques options à analyser :

- Fichiers principaux qui ont un impact sur le temps d’analyse
- Principaux processus qui ont un impact sur le temps d’analyse
- Principales extensions de fichier qui ont un impact sur le temps d’analyse
- Combinaisons : par exemple, les principaux fichiers par extension, les analyses les plus hautes par fichier, les analyses les plus hautes par fichier par processus

## <a name="running-performance-analyzer"></a>Exécution de l’analyseur de performances

Le processus de haut niveau pour l’exécution de l’analyseur de performances implique les étapes suivantes :

1. Exécutez l’analyseur de performances pour collecter un enregistrement des performances Antivirus Microsoft Defender événements sur le point de terminaison.

> [!NOTE]
> Les performances de Antivirus Microsoft Defender événements de type **Microsoft-Antimalware-Engine** sont enregistrées via l’analyseur de performances.

2. Analysez les résultats de l’analyse à l’aide de différents rapports d’enregistrement.

## <a name="using-performance-analyzer"></a>Utilisation de l’analyseur de performances

Pour commencer à enregistrer les événements système, ouvrez PowerShell en mode d’administration et effectuez les étapes suivantes :

1. Exécutez la commande suivante pour démarrer l’enregistrement :

`New-MpPerformanceRecording -RecordTo <recording.etl>`
 
 où `-RecordTo` le paramètre spécifie l’emplacement du chemin d’accès complet dans lequel le fichier de suivi est enregistré. Pour plus d’informations sur les cmdlet, voir [Defender.](/powershell/module/defender)

2. S’il existe des processus ou des services qui semblent affecter les performances, reproduisez la situation en réalisation des tâches pertinentes.
3. Appuyez **sur Entrée** pour arrêter et enregistrer l’enregistrement, ou **sur Ctrl+C** pour annuler l’enregistrement.
4. Analysez les résultats à l’aide du paramètre de l’analyseur de `Get-MpPerformanceReport` performances. Par exemple, lors de l’exécution de la commande, l’utilisateur est fourni avec une liste des dix premières analyses pour les 3 premiers fichiers affectant `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10` les performances. 

Pour plus d’informations sur les paramètres de ligne de commande et les options, voir [New-MpPerformanceRecording](#new-mpperformancerecording) et [Get-MpPerformanceReport](#get-mpperformancereport).

### <a name="performance-tuning-data-and-information"></a>Informations et données d’optimisation des performances

En fonction de la requête, l’utilisateur peut afficher les données pour le nombre d’analyses, la durée (total/min/average/max/median), le chemin d’accès, le processus et le motif de l’analyse. L’image ci-dessous montre un exemple de sortie pour une requête simple des 10 premiers fichiers pour l’impact de l’analyse. 

:::image type="content" source="images/example-output.png" alt-text="Exemple de sortie pour une requête TopFiles de base":::

### <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>Fonctionnalités supplémentaires : exportation et conversion en CSV et JSON

Les résultats de l’analyseur de perfomance peuvent également être exportés et convertis en fichier CSV ou JSON.
Pour obtenir des exemples qui décrivent le processus d’exportation et de conversion par le biais d’exemples de codes, voir ci-dessous.

#### <a name="for-csv"></a>Pour CSV

- **Pour exporter**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **Pour convertir**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

#### <a name="for-json"></a>Pour JSON

- **Pour convertir**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

### <a name="requirements"></a>Configuration requise
Antivirus Microsoft Defender’analyseur de performances présente les conditions préalables suivantes :

- Versions Windows prise en charge : Windows 10, Windows 11 et versions Windows Server 2016 versions ultérieures
- Version de la plateforme : 4.18.2108.X+
- Version PowerShell : PowerShell Version 5.1

## <a name="powershell-reference"></a>Référence PowerShell
Deux nouvelles cmdlets PowerShell sont utilisées pour régler les performances des Antivirus Microsoft Defender : 

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)


### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

La section suivante décrit la référence pour la nouvelle cmdlet PowerShell New-MpPerformanceRecording. Cette cmdlet collecte un enregistrement des performances de Antivirus Microsoft Defender analyses.

#### <a name="syntax-new-mpperformancerecording"></a>Syntaxe : New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>Description : New-MpPerformanceRecording
`New-MpPerformanceRecording`L’cmdlet collecte un enregistrement des performances de Antivirus Microsoft Defender analyses. Ces enregistrements de performances contiennent des événements de processus de noyau Microsoft-Antimalware-Engine et NT et peuvent être analysés après la collecte à l’aide de l’cmdlet [Get-MpPerformanceReport.](#get-mpperformancereport)

Cette cmdlet fournit un aperçu des fichiers problématiques qui peuvent entraîner une dégradation des `New-MpPerformanceRecording` performances de Antivirus Microsoft Defender. Cet outil est fourni « TEL QU’IL EST » et n’est pas destiné à fournir des suggestions sur les exclusions. Les exclusions peuvent réduire le niveau de protection sur vos points de terminaison. Les exclusions, le cas besoin, doivent être définies avec précaution.

Pour plus d’informations sur l’analyseur de performances, voir la documentation [de l’analyseur](/windows-hardware/test/wpt/windows-performance-analyzer) de performances.

> [!IMPORTANT]
> Cette cmdlet nécessite des privilèges d’administrateur élevés.

**Versions de système d’exploitation prise en charge**

Windows Version 10 et ultérieures.

> [!NOTE]
> Cette fonctionnalité est disponible à partir de la version de plateforme 4.18.2108.X et versions ultérieures.

#### <a name="examples-new-mpperformancerecording"></a>Exemples : New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>Exemple 1 : Collecter un enregistrement des performances et l’enregistrer

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

La commande ci-dessus collecte un enregistrement des performances et l’enregistre dans le chemin d’accès spécifié **: .\Defender-scans.etl**.

#### <a name="parameters-new-mpperformancerecording"></a>Paramètres : New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo
Spécifie l’emplacement dans lequel enregistrer l’enregistrement des performances du logiciel anti-programme malveillant Microsoft Defender.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

La section suivante décrit l'Get-MpPerformanceReport cmdlet PowerShell. Analyse et signale l’enregistrement des performances Antivirus Microsoft Defender (MDAV).

#### <a name="syntax-get-mpperformancereport"></a>Syntaxe : Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
[-TopScans <Int32>]
[-TopFiles  <Int32>
    [-TopScansPerFile <Int32>]
    [-TopProcessesPerFile  <Int32>  
        [-TopScansPerProcessPerFile <Int32>]
    ]
] 
[-TopExtensions  <Int32>
    [-TopScansPerExtension <Int32>]
    [-TopProcessesPerExtension <Int32>
        [-TopScansPerProcessPerExtension <Int32>]
        ]
    [-TopFilesPerExtension  <Int32>
        [-TopScansPerFilePerExtension <Int32>]
        ]
    ] 
]
[-TopProcesses  <Int32>
    [-TopScansPerProcess <Int32>]
    [-TopExtensionsPerProcess <Int32>
        [-TopScansPerExtensionPerProcess <Int32>]
    ]
]
[-TopFilesPerProcess  <Int32>
    [-TopScansPerFilePerProcess <Int32>]
]
[-MinDuration <String>]
```

#### <a name="description-get-mpperformancereport"></a>Description : Get-MpPerformanceReport
L’cmdlet analyse un enregistrement des performances Antivirus Microsoft Defender précédemment collecté `Get-MpPerformanceReport` ([New-MpPerformanceRecording](#new-mpperformancerecording)) et signale les chemins d’accès aux fichiers, extensions de fichiers et processus qui ont le plus d’impact sur Antivirus Microsoft Defender analyses.

L’analyseur de performances fournit un aperçu des fichiers problématiques qui peuvent entraîner une dégradation des performances des Antivirus Microsoft Defender. Cet outil est fourni « TEL QU’IL EST » et n’est pas destiné à fournir des suggestions sur les exclusions. Les exclusions peuvent réduire le niveau de protection sur vos points de terminaison. Les exclusions, le cas besoin, doivent être définies avec précaution.

Pour plus d’informations sur l’analyseur de performances, voir la documentation [de l’analyseur](/windows-hardware/test/wpt/windows-performance-analyzer) de performances.

**Versions de système d’exploitation prise en charge**

Windows Version 10 et ultérieures.

> [!NOTE]
> Cette fonctionnalité est disponible à partir de la version de plateforme 4.18.2108.X et versions ultérieures.

#### <a name="examples-get-mpperformancereport"></a>Exemples : Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>Exemple 1 : requête unique 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>Exemple 2 : requêtes multiples 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>Exemple 3 : requêtes imbrmbrées 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>Exemple 4 : Utilisation du paramètre -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

#### <a name="parameters-get-mpperformancereport"></a>Paramètres : Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration
Spécifie la durée minimale d’une analyse ou d’un nombre total de durées d’analyse des fichiers, des extensions et des processus inclus dans le rapport ; accepte des valeurs telles que  **0,1234567sec,** **0,1234 ms,** **0,1us** ou un timeSpan valide.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-path"></a>-Path
Spécifie le ou les chemins d’accès à un ou plusieurs emplacements.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### <a name="-topextensions"></a>-TopExtensions 
Spécifie le nombre d’extensions principales à sortie, triées par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess 
Spécifie le nombre d’extensions principales à obtenir pour chaque processus supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfiles"></a>-TopFiles
Demande un rapport de fichiers principaux et spécifie le nombre de fichiers principaux à sortie, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperextension"></a>-TopFilesPerExtension 
Spécifie le nombre de fichiers principaux à sortier pour chaque extension supérieure, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperprocess"></a>-TopFilesPerProcess
Spécifie le nombre de fichiers principaux à obtenir pour chaque processus supérieur, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocesses"></a>-TopProcesses
Demande un rapport des principaux processus et spécifie le nombre de processus principaux à sortie, triés par « Durée ».

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension 
Spécifie le nombre de processus principaux à obtenir pour chaque extension supérieure, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topprocessesperfile"></a>-TopProcessesPerFile
Spécifie le nombre de processus principaux à produire pour chaque fichier supérieur, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscans"></a>-TopScans
Demande un rapport d’analyse supérieure et spécifie le nombre d’analyses principales à sortie, triées par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextension"></a>-TopScansPerExtension
Spécifie le nombre d’analyses principales à obtenir pour chaque extension supérieure, triées par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess 
Spécifie le nombre d’analyses principales à obtenir pour chaque extension supérieure pour chaque processus supérieur, trié par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfile"></a>-TopScansPerFile
Spécifie le nombre d’analyses principales à produire pour chaque fichier supérieur, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension 
Spécifie le nombre d’analyses principales à produire pour chaque fichier supérieur pour chaque extension supérieure, triées par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess 
Spécifie le nombre d’analyses principales pour la sortie de chaque fichier supérieur pour chaque processus supérieur, trié par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperprocess"></a>-TopScansPerProcess 
Spécifie le nombre d’analyses principales à obtenir pour chaque processus supérieur dans le rapport Processus principaux, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension
Spécifie le nombre d’analyses principales pour la sortie de chaque processus supérieur pour chaque extension supérieure, triée par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile
Spécifie le nombre d’analyses principales de sortie pour chaque processus supérieur pour chaque fichier supérieur, triés par « Durée ».


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

