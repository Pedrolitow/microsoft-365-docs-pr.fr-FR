---
title: Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser PowerShell pour intégrer Shifts à Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 64a5e8a8cede1481c42add9383239ae6b4ad4f06
ms.sourcegitcommit: 99b174a8d431092b3cf7d650593248671297fd91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68300059"
---
# <a name="use-powershell-to-connect-shifts-to-blue-yonder-workforce-management"></a>Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management

## <a name="overview"></a>Vue d’ensemble

Utilisez le [connecteur Microsoft Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) pour intégrer l'application Shifts dans Microsoft Teams avec Blue Yonder Workforce Management (Blue Yonder WFM). Une fois la connexion établie, vos employés de première ligne peuvent afficher et gérer leurs horaires de manière transparente dans Blue Yonder WFM à partir de Shifts.

Dans cet article, nous vous expliquons comment utiliser PowerShell pour installer et configurer le connecteur afin d'intégrer Shifts à Blue Yonder WFM..

Pour configurer la connexion, vous exécutez un script PowerShell. Le script configure le connecteur, applique les paramètres de synchronisation, crée la connexion et mappe les instances Blue Yonder WFM aux équipes. Les paramètres de synchronisation déterminent les fonctionnalités activées dans Shifts et les informations de planification synchronisées entre Blue Yonder WFM et Shifts.. Les mappages définissent la relation de synchronisation entre vos instances Blue Yonder WFM et les équipes dans Teams.. Vous pouvez mapper aux équipes existantes et aux nouvelles équipes.

Nous fournissons deux scripts. Vous pouvez utiliser l'un ou l'autre des scripts, selon que vous souhaitez mapper sur des équipes existantes ou créer de nouvelles équipes à mapper..

Vous pouvez configurer plusieurs connexions, chacune avec des paramètres de synchronisation différents. Par exemple, si votre organisation possède plusieurs emplacements avec des exigences de planification différentes, créez une connexion avec des paramètres de synchronisation uniques pour chaque emplacement. Gardez à l'esprit qu'une instance Blue Yonder WFM ne peut être associée qu'à une seule équipe à la fois.. Si une instance est déjà mappée à une équipe, elle ne peut pas être mappée à une autre équipe.

Avec Blue Yonder WFM comme système d’enregistrement, vos employés de première ligne peuvent gérer efficacement leurs horaires et leur disponibilité dans Shifts sur leurs appareils. Les responsables de première ligne peuvent continuer à utiliser Blue Yonder WFM pour établir des horaires.

> [!NOTE]
> Vous pouvez également utiliser l’[Assistant connecteur Shifts](shifts-connector-wizard.md) dans le centre d'administration Microsoft 365 pour connecter Shifts à Blue Yonder WFM.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="prerequisites"></a>Configuration requise

[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

### <a name="admin-role-to-manage-the-connector-using-powershell"></a>Rôle d’administrateur pour gérer le connecteur à l’aide de PowerShell

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>Configuration de votre environnement

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

## <a name="connect-to-teams"></a>Se connecter à Teams

Exécutez ce qui suit pour vous connecter à Teams.

```powershell
Connect-MicrosoftTeams
```

Lorsque vous y êtes invité, connectez-vous à l’aide de vos informations d’identification d’administrateur. Vous êtes maintenant configuré pour exécuter les scripts de cet article et les applets de commande du connecteur Shifts.

## <a name="identify-the-teams-you-want-to-map"></a>Identifier les équipes que vous souhaitez mapper

> [!NOTE]
> Effectuez cette étape si vous mappez des instances Blue Yonder WFM à des équipes existantes. Si vous créez des équipes à mapper, vous pouvez ignorer cette étape.

Dans le portail Azure, accédez à la page [Tous les groupes](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) pour obtenir une liste des ID d’équipes de votre organisation.

Prenez note des ID d’équipes que vous souhaitez mapper. Le script vous invitera à entrer ces informations.

> [!NOTE]
> Si une ou plusieurs équipes ont une planification existante, le script supprime les horaires de ces équipes. Sinon, vous verrez des shifts en double.

## <a name="run-the-script"></a>Exécutez le script

Exécutez le script :

- Pour configurer une connexion et créer des équipes à mapper, [exécuter ce script](#set-up-a-connection-and-create-new-teams-to-map).
- Pour configurer une connexion et mapper à des équipes existantes, [exécuter ce script](#set-up-a-connection-and-map-to-existing-teams).

Le script effectue les opérations suivantes. Vous serez invité à entrer les détails de l’installation et de la configuration.

1. Teste et vérifie la connexion à Blue Yonder WFM à l'aide des informations d'identification du compte de service Blue Yonder WFM et des URL de service que vous entrez.
1. Configure le connecteur Shifts.
1. Applique les paramètres de synchronisation. Ces paramètres incluent la fréquence de synchronisation (en minutes) et les données de planification synchronisées entre Blue Yonder WFM et Shifts. Les données de planification sont définies dans les paramètres suivants :

    - Le paramètre **enabledConnectorScenarios** définit les données synchronisées de Blue Yonder WFM vers Shifts. Les options sont `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift`, `OpenShiftRequest`, `TimeOff`, `TimeOffRequest`.
    - Le paramètre **enabledWfiScenarios** définit les données synchronisées de Shifts vers Blue Yonder WFM. Les options sont `SwapRequest`, `OpenShiftRequest`, `TimeOffRequest`, `UserShiftPreferences`.

    Pour en savoir plus, consultez [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance). Pour voir la liste des options de synchronisation prises en charge pour chaque paramètre, exécutez [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

    > [!IMPORTANT]
    > Le script active la synchronisation pour toutes ces options. Si vous souhaitez modifier les paramètres de synchronisation, vous pouvez le faire une fois la connexion configurée. Pour en savoir plus, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

1. Crée la connexion.
1. Mappe les instances WFM Blue Yonder WFM aux équipes. Les mappages sont basés sur les ID d'instance Blue Yonder WFM et les ID d’équipes que vous entrez ou sur les nouvelles équipes que vous créez, selon le script que vous exécutez. Si une équipe a un planification existante, le script supprime les données de planification pour la plage de dates et d'heures que vous spécifiez.

Un message de réussite à l’écran indique que votre connexion est correctement configurée.

## <a name="manage-your-connection"></a>Gérer votre connexion

Une fois la connexion configurée, vous pouvez la gérer et y apporter des modifications dans le Centre d'administration Microsoft 365 ou à l’aide de PowerShell.

### <a name="use-the-microsoft-365-admin-center"></a>Utiliser le Centre d'administration Microsoft 365

La page Gestion des connecteurs répertorie chaque connexion que vous avez configurée, ainsi que des informations telles que l’état d’intégrité et les détails de l’intervalle de synchronisation. Vous pouvez également accéder à l’Assistant pour apporter des modifications à l’une de vos connexions. Par exemple, vous pouvez mettre à jour les paramètres de synchronisation et les mappages d’équipe.

Pour plus d’informations, consultez [Utiliser le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-admin-center-manage.md).

### <a name="use-powershell"></a>Utiliser PowerShell

Vous pouvez utiliser PowerShell pour afficher un rapport d’erreurs, modifier les paramètres de connexion, désactiver la synchronisation, etc. Pour obtenir des instructions pas à pas, consultez [Utiliser PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

## <a name="scripts"></a>Scripts

### <a name="set-up-a-connection-and-create-new-teams-to-map"></a>Configurer une connexion et créer des équipes à mapper

```powershell
#Map WFM instances to teams script
Write-Host "Map WFM sites to teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.7.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate `
    -Name $InstanceName `
    -ConnectorId $BlueYonderId `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificBlueYonderSettingsRequest `
        -Property @{
            AdminApiUrl = $adminApiUrl
            SiteManagerUrl = $siteManagerUrl
            EssApiUrl = $essApiUrl
            RetailWebApiUrl = $retailWebApiUrl
            CookieAuthUrl = $cookieAuthUrl
            FederatedAuthUrl = $federatedAuthUrl
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
        })
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create a connection instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency"

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$InstanceResponse = New-CsTeamsShiftsConnectionInstance `
    -ConnectorId $BlueYonderId `
    -ConnectorAdminEmail $AdminEmailList `
    -DesignatedActorId $teamsUserId `
    -EnabledConnectorScenario $enabledConnectorScenario `
    -EnabledWfiScenario $wfiSupportedScenario `
    -Name $InstanceName `
    -SyncFrequencyInMin $syncFreq `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificBlueYonderSettingsRequest `
        -Property @{
            AdminApiUrl = $adminApiUrl
            SiteManagerUrl = $siteManagerUrl
            EssApiUrl = $essApiUrl
            RetailWebApiUrl = $retailWebApiUrl
            CookieAuthUrl = $cookieAuthUrl
            FederatedAuthUrl = $federatedAuthUrl
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
        })
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if (($WfmTeamIds -ne $NULL) -and ($WfmTeamIds.Count -gt 0)){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

#Create a new Teams team with owner set to system account and name set to the site name
Write-Host "Creating a Teams team"
$teamsTeamName = Read-Host -Prompt "Input the Teams team name"
$Team = New-Team -DisplayName $teamsTeamName -Visibility "Public" -Owner $teamsUserId
Write-Host "Success"
$TeamsTeamId=$Team.GroupId

#Add users to the Team for Shifts
Write-Host "Adding users to Teams team"
$currentUser = Read-Host -Prompt "Input the current user's user name or ID"
Add-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
$failedWfmUsers=@()
foreach ($user in $WFMUsers) {
    try {
    $userEmail = $user.Name + "@" +$domain
    Add-TeamUser -GroupId $TeamsTeamId -User $userEmail
    } catch {
        $failedWfmUsers+=$user
    }
}
if($failedWfmUsers.Count -gt 0){
    Write-Host "There are WFM users not existed in Teams tenant:"
    write $failedWfmUsers
}

#Enable scheduling in the group
$RequestBody = @{
    Enabled = $true
    TimeZone = "America/Los_Angeles"
}
$teamUpdateUrl="https://graph.microsoft.com/v1.0/teams/"+$TeamsTeamId+"/schedule"
$Schedule = Invoke-MgGraphRequest -Uri $teamUpdateUrl -Method PUT -Body $RequestBody

#Create a mapping of the new team to the instance
Write-Host "Create a mapping of the new team to the site"
$TimeZone = Read-Host -Prompt "Input the time zone of team mapping"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone $TimeZone -WfmTeamId $WfmTeamId
Write-Host "Success"

$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Remove-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
Disconnect-MgGraph
```

### <a name="set-up-a-connection-and-map-to-existing-teams"></a>Configurer une connexion et mapper aux équipes existantes

```powershell
#Map WFM sites to existing teams script
Write-Host "Map WFM sites to existing teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.7.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate `
    -Name $InstanceName `
    -ConnectorId $BlueYonderId `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificBlueYonderSettingsRequest `
        -Property @{
            AdminApiUrl = $adminApiUrl
            SiteManagerUrl = $siteManagerUrl
            EssApiUrl = $essApiUrl
            RetailWebApiUrl = $retailWebApiUrl
            CookieAuthUrl = $cookieAuthUrl
            FederatedAuthUrl = $federatedAuthUrl
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
        })
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create an instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency. Value should be equal to or more than 10."

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}

$InstanceResponse = New-CsTeamsShiftsConnectionInstance `
    -ConnectorId $BlueYonderId `
    -ConnectorAdminEmail $AdminEmailList `
    -DesignatedActorId $teamsUserId `
    -EnabledConnectorScenario $enabledConnectorScenario `
    -EnabledWfiScenario $wfiSupportedScenario `
    -Name $InstanceName `
    -SyncFrequencyInMin $syncFreq `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificBlueYonderSettingsRequest `
        -Property @{
            AdminApiUrl = $adminApiUrl
            SiteManagerUrl = $siteManagerUrl
            EssApiUrl = $essApiUrl
            RetailWebApiUrl = $retailWebApiUrl
            CookieAuthUrl = $cookieAuthUrl
            FederatedAuthUrl = $federatedAuthUrl
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
    })
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if (($WfmTeamIds -ne $NULL) -and ($WfmTeamIds.Count -gt 0)){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

$TeamsTeamId = Read-Host -Prompt "Input the ID of the Teams team to be mapped"
#Clear schedule of the Teams team
Write-Host "Clear schedule of the existing team"
$startTime = Read-Host -Prompt "Input the start time of clear schedule"
$endTime = Read-Host -Prompt "Input the end time of clear schedule"

$entityTypeString = Read-Host -Prompt 'Input the entity types of clear schedule'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$entityType = $entityTypeString -Split {$Delimiters -contains $_}
$entityType = $entityType.Trim()
$entityType = $entityType.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
Remove-CsTeamsShiftsScheduleRecord -TeamId $TeamsTeamId -DateRangeStartDate $startTime -DateRangeEndDate $endTime -ClearSchedulingGroup:$True -EntityType $entityType -DesignatedActorId $teamsUserId

#Create a mapping of the existing team to the instance
Write-Host "Create a mapping of the existing team to the site"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"


$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Disconnect-MgGraph
```

## <a name="shifts-connector-cmdlets"></a>Applets de commande du connecteur Shifts

Pour obtenir de l'aide sur les applets de commande du connecteur Shifts, y compris les applets de commande utilisées dans les scripts, recherchez **CsTeamsShiftsConnection** dans la [référence de l'applet de commande Teams PowerShell](/powershell/teams/intro). Voici des liens vers certaines applets de commande couramment utilisées.

- [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation)
- [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance)
- [Get-CsTeamsShiftsConnectionInstance](/powershell/module/teams/get-csteamsshiftsconnectioninstance)
- [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance)
- [Remove-CsTeamsShiftsConnectionInstance](/powershell/module/teams/remove-csteamsshiftsconnectioninstance)
- [Test-CsTeamsShiftsConnectionValidate](/powershell/module/teams/test-csteamsshiftsconnectionvalidate)
- [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap)
- [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector)
- [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult)
- [Get-CsTeamsShiftsConnectionWfmUser](/powershell/module/teams/get-csteamsshiftsconnectionwfmuser)
- [Get-CsTeamsShiftsConnectionWfmTeam](/powershell/module/teams/get-csteamsshiftsconnectionwfmteam)
- [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport)
- [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord)

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)
- [Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-admin-center-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Présentation de Teams PowerShell](/microsoftteams/teams-powershell-overview)
- [Référence de l'applet de commande Teams PowerShell](/powershell/teams/intro)
