---
title: Actualiser votre fichier exact de table source d’informations sensible aux correspondances de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Actualisez votre fichier de table source d’informations sensibles.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 79442356066263485c70bf455af5a6a44a0355d4
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62903709"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Actualiser votre fichier de table source d’informations sensibles de correspondance exacte 

Vous pouvez actualiser votre base de données d’informations sensibles deux fois par période de 24 heures. Vous devez resserrez et téléchargez votre table de sources d’informations sensibles.

1. Réexportez les données sensibles vers une application, telle que Microsoft Excel, et enregistrez le fichier au format .csv, au format .tsv ou au format de canal (|). Conservez le nom de fichier et l’emplacement que vous avez utilisés lorsque vous avez précédemment haché et chargé le fichier. Voir, [Export source data for exact data match based sensitive information type](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) for details on exporting your sensitive data and getting it into the correct format.

      > [!NOTE]
      > Si aucune modification n’est apportée à la structure (noms de champs) du fichier de table de sources d’informations sensibles, vous n’avez pas besoin d’apporter de modifications à votre fichier de schéma de base de données lorsque vous actualisez les données. Si vous devez apporter des modifications, assurez-vous de modifier le schéma de base de données et votre package de règles en conséquence. Consultez [la procédure de modification](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) ou de suppression d’un schéma exact de correspondance de données. See, [Create exact data match sensitive information type/rule package](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) for the steps to edit or remove your EDM SIT/rule package.

2. Utilisez les procédures du hachage et téléchargez la [table des sources](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) d’informations sensibles pour obtenir des types d’informations sensibles de correspondance exacte pour télécharger votre fichier source de table d’informations sensibles.

2. Vous pouvez utiliser le [Programmeur des](/windows/desktop/TaskSchd/task-scheduler-start-page) tâches pour automatiser le hachage et charger la table des sources d’informations sensibles pour la procédure exacte des [types d’informations](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) sensibles de correspondance de données. Vous pouvez planifier des tâches à l’aide de plusieurs méthodes :

   |Méthode|Procédure|
   |---|---|
   |Windows PowerShell|Consultez la documentation[ScheduledTasks](/powershell/module/scheduledtasks/) et l’[exemple de script PowerShell](#example-powershell-script-for-task-scheduler) dans cet article|
   |API planificateur de tâches|Consultez la documentation relative au [planificateur de tâches](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |Interface utilisateur Windows|Dans Windows, cliquez sur **Démarrer**, puis tapez Planificateur de tâches. Dans la liste des résultats, cliquez avec le bouton droit sur **planificateur de tâches**, puis sélectionnez **exécuter en tant qu’administrateur**.|

### <a name="example-powershell-script-for-task-scheduler"></a>Exemple de script PowerShell pour le planificateur de tâches 

Cette section inclut un exemple de script PowerShell que vous pouvez utiliser pour planifier vos tâches de hachage de données et de téléchargement des données hachées :

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planifier le hachage et le chargement dans une étape combinée

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planifier le hachage et le chargement en tant qu’étapes distinctes

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
