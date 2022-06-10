---
title: Actualiser votre fichier de table source d’informations sensibles correspondant exactement aux données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Actualisez votre fichier de table source d’informations sensibles.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a846f22b866b4b8adf75c44e55fde4b9d56b8ac4
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008842"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>Actualiser votre fichier de table source d’informations sensibles correspondant exactement aux données 

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez actualiser votre base de données d’informations sensibles jusqu’à 5 fois toutes les 24 heures. Vous devrez resserrez et chargez votre table source d’informations sensibles.

1. Réexportez les données sensibles vers une application, telle que Microsoft Excel, et enregistrez le fichier au format .csv, au format .tsv ou au format délimité par canal (|). Conservez le même nom de fichier et le même emplacement que ceux que vous avez utilisés lors du hachage et du chargement précédents du fichier. Pour plus d’informations sur l’exportation de vos données sensibles et leur mise au format correct, consultez [Exporter les données sources pour obtenir des informations exactes sur la correspondance des données en fonction du type d’informations sensibles](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) .

      > [!NOTE]
      > Si aucune modification n’est apportée à la structure (noms de champs) du fichier de table source d’informations sensibles, vous n’avez pas besoin d’apporter des modifications à votre fichier de schéma de base de données lorsque vous actualisez les données. Si vous devez apporter des modifications, assurez-vous de modifier le schéma de base de données et votre package de règles en conséquence. Consultez, [Gérez votre schéma de correspondance de données exact](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) pour les étapes de modification ou de suppression d’un schéma. Consultez la page [Créer des données exactes correspondant au type d’informations sensibles/au package de règle](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) pour les étapes de modification ou de suppression de votre package sit/rule EDM.

2. Utilisez les procédures de [hachage et chargez la table source d’informations sensibles pour que les données exactes correspondent aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) pour charger votre fichier source de table d’informations sensibles.

3. Vous pouvez utiliser [le planificateur de tâches](/windows/desktop/TaskSchd/task-scheduler-start-page) pour automatiser le [hachage et charger la table source d’informations sensibles pour la procédure de correspondance exacte des données avec les types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . Vous pouvez planifier des tâches à l’aide de plusieurs méthodes :

   |Méthode|Procédure|
   |---|---|
   |PowerShell|Consultez la documentation[ScheduledTasks](/powershell/module/scheduledtasks/) et l’[exemple de script PowerShell](#example-powershell-script-for-task-scheduler) dans cet article|
   |API planificateur de tâches|Consultez la documentation relative au [planificateur de tâches](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |Interface utilisateur Windows|Dans Windows, cliquez sur **Démarrer**, puis tapez Planificateur de tâches. Dans la liste des résultats, cliquez avec le bouton droit sur **planificateur de tâches**, puis sélectionnez **exécuter en tant qu’administrateur**.|

## <a name="example-powershell-script-for-task-scheduler"></a>Exemple de script PowerShell pour le planificateur de tâches

Cette section inclut un exemple de script PowerShell que vous pouvez utiliser pour planifier vos tâches de hachage de données et de téléchargement des données hachées :

### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>Planifier le hachage et le chargement dans une étape combinée

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

### <a name="schedule-hashing-and-upload-as-separate-steps"></a>Planifier le hachage et le chargement en tant qu’étapes distinctes

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
