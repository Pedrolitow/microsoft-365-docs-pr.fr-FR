---
title: Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser PowerShell pour gérer votre connexion Shifts à Gestion de la main-d’œuvre Blue Yonder.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 1064401dee3a25a7d1749db6e4a36a110f21da0b
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66992244"
---
# <a name="use-powershell-to-manage-your-shifts-connection-to-blue-yonder-workforce-management"></a>Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management

## <a name="overview"></a>Vue d’ensemble

Le [connecteur Microsoft Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) vous permet d’intégrer l'application Shifts dans Microsoft Teams avec Blue Yonder Workforce Management (Blue Yonder WFM). Une fois que vous avez configuré une connexion, vos employés de première ligne peuvent afficher et gérer en toute transparence leurs plannings dans le WFM Blue Yonder à partir de Shifts.

Vous pouvez utiliser [l’Assistant Connecteur Shifts](shifts-connector-wizard.md) dans le Centre d’administration Microsoft 365 ou [PowerShell](shifts-connector-blue-yonder-powershell-setup.md) pour configurer une connexion. Une fois qu’une connexion est configurée, vous la gérez à l’aide des [applets de commande PowerShell du connecteur Shifts](#shifts-connector-cmdlets).

Cet article explique comment utiliser PowerShell pour effectuer les opérations suivantes :

- [Vérifier l’état de l’installation de la connexion](#check-connection-setup-status)
- [Afficher un rapport d’erreurs pour une connexion](#view-an-error-report-for-a-connection)
- [Résoudre les erreurs de connexion](#resolve-connection-errors)
- [Modifier les paramètres de connexion](#change-connection-settings)
- [Annuler le mappage d’une équipe d’une connexion et la mapper à une autre connexion](#unmap-a-team-from-one-connection-and-map-it-to-another-connection)
- [Désactiver la synchronisation pour une connexion](#disable-sync-for-a-connection)

> [!NOTE]
> Cet article part du principe que vous avez déjà configuré une connexion à Blue Yonder WFM, à l’aide de l’Assistant ou de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>Configuration de votre environnement

> [!NOTE]
> Veillez à suivre ces étapes pour configurer votre environnement avant d’exécuter l’une des commandes ou scripts de cet article.

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

7. Se connecter à Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    Lorsque vous y êtes invité, connectez-vous à l’aide de vos informations d’identification d’administrateur. Vous êtes maintenant configuré pour exécuter les scripts de cet article et les applets de commande du connecteur Shifts.

## <a name="check-connection-setup-status"></a>Vérifier l’état de l’installation de la connexion

<a name="setup_status"> </a>

Pour vérifier l’état de la connexion que vous avez configurée à l’aide de l’ID d’opération que vous avez reçu par e-mail :

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Exécutez la commande suivante : Cette commande vous donne l’état global des mappages d’équipe pour la connexion.

    ``` powershell
    Get-CsTeamsShiftsConnectionOperation -OperationId <YourOperationId>
    ```

Pour en savoir plus, consultez [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation).

## <a name="view-an-error-report-for-a-connection"></a>Afficher un rapport d’erreurs pour une connexion

<a name="error_report"> </a>

Vous pouvez exécuter un rapport qui affiche les détails de l’erreur pour une connexion. Le rapport répertorie les mappages d’équipe et d’utilisateur qui ont réussi et échoué. Il fournit également des informations sur les problèmes liés aux comptes associés à la connexion.

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Obtenez la liste des rapports d’erreurs pour une connexion.

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Pour afficher un rapport d’erreurs spécifique, exécutez la commande suivante :

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ErrorReportId <ErrorReportId>
    ```

Pour en savoir plus, consultez [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport).

## <a name="resolve-connection-errors"></a>Résoudre les erreurs de connexion

### <a name="user-mapping-errors"></a>Erreurs de mappage d’utilisateurs

Des erreurs de mappage d’utilisateurs peuvent se produire si un ou plusieurs utilisateurs d’une instance Blue Yonder WFM ne sont pas membres de l’équipe mappée dans Teams. Pour résoudre ce problème, assurez-vous que les utilisateurs de l’équipe mappée correspondent aux utilisateurs de l’instance Blue Yonder WFM.

Pour afficher les détails des utilisateurs non mappés, [configurez votre environnement](#set-up-your-environment) (si ce n’est pas déjà fait), puis exécutez le script suivant.

```powershell
#View sync errors script
Write-Host "View sync errors"
Start-Sleep 1

#Ensure Teams module is of version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to retrieve user sync results from'
}
else {
    throw "Instance list is empty"
}

#Get a list of the mappings
Write-Host "Listing team mappings"
$mappings = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $mappings

#For each mapping, retrieve the failed mappings
ForEach ($mapping in $mappings){
    $teamsTeamId = $mapping.TeamId
    $wfmTeamId = $mapping.WfmTeamId
    Write-Host "Failed mapped users in the mapping of ${teamsTeamId} and ${wfmTeamId}:"
    $userSyncResult = Get-CsTeamsShiftsConnectionSyncResult -ConnectorInstanceId $InstanceId -TeamId $teamsTeamId
    Write-Host "Failed AAD users:"
    write $userSyncResult.FailedAadUser
    Write-Host "Failed WFM users:"
    write $userSyncResult.FailedWfmUser
}
```

### <a name="account-authorization-errors"></a>Erreurs d’autorisation de compte

Des erreurs d'autorisation de compte peuvent se produire si le compte de service Blue Yonder WFM ou les informations d'identification du compte système Microsoft 365 sont incorrects ou ne disposent pas des autorisations requises.

Pour modifier vos informations d’identification de compte de service Blue Yonder WFM ou de compte système Microsoft 365 pour la connexion, vous pouvez exécuter l’applet de commande [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) ou utiliser le script PowerShell dans la section [Modifier les paramètres de connexion](#change-connection-settings) de cet article.

## <a name="change-connection-settings"></a>Modifier les paramètres de connexion
<a name="change_settings"> </a>

Utilisez ce script pour modifier les paramètres de connexion. Les paramètres que vous pouvez modifier incluent votre compte de service Blue Yonder WFM et votre mot de passe, le compte système Microsoft 365, les mappages d’équipe et les paramètres de synchronisation.

Ces paramètres incluent la fréquence de synchronisation (en minutes) et les données de planification synchronisées entre Blue Yonder WFM et Shifts. Les données de planification sont définies dans les paramètres suivants, que vous pouvez afficher en exécutant [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

- Le paramètre **enabledConnectorScenarios** définit les données synchronisées de Blue Yonder WFM vers Shifts. Les options sont `Shift`, `SwapRequest`, `UserShiftPreferences`, `OpenShift`, `OpenShiftRequest`, `TimeOff`, `TimeOffRequest`.
- Le paramètre **enabledWfiScenarios** définit les données synchronisées de Shifts vers Blue Yonder WFM. Les options sont `SwapRequest`, `OpenShiftRequest`, `TimeOffRequest`, `UserShiftPreferences`.

    > [!NOTE]
    > Si vous choisissez de ne pas synchroniser les shifts ouvertes, les demandes de changement d'équipe, les demandes d'échange ou les demandes de congés entre les équipes et Blue Yonder WFM, vous devez effectuer une autre étape pour masquer cette capacité dans les équipes. Après avoir exécuté ce script, assurez-vous de suivre les étapes de la section [Désactiver les équipes ouvertes, les demandes d'équipes ouvertes, les demandes de permutation et les demandes de congés](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) plus loin dans cet article.

> [!IMPORTANT]
> Pour les paramètres que vous ne souhaitez pas modifier, vous devez entrer à nouveau les paramètres d’origine lorsque le script vous y invite.

[Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait), puis exécutez le script suivant.

```powershell
#Update connector instance and mapping script
Write-Host "Update connector instance and mapping"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
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

#List connection instances available
Write-Host "Listing connection instances available"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Prompt for the WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Get the instance ID
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$InstanceId = Read-Host -Prompt 'Input the instance ID that you want to update'
$Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
$Etag = $Instance.etag

#Change sync setting
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$UpdatedInstanceName = Read-Host -Prompt 'Input new connection instance name'
$updatedConnectorScenarioString = Read-Host -Prompt 'Input new enabled connector scenarios'
$updatedWfiScenarioString = Read-Host -Prompt 'Input new enabled WFI scenarios'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$updatedConnectorScenario = $updatedConnectorScenarioString -Split {$Delimiters -contains $_}
$updatedConnectorScenario = $updatedConnectorScenario.Trim()
$updatedConnectorScenario = $updatedConnectorScenario.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
$updatedWfiScenario = $updatedWfiScenarioString -Split {$Delimiters -contains $_}
$updatedWfiScenario = $updatedWfiScenario.Trim()
$updatedWfiScenario = $updatedWfiScenario.Split('', [System.StringSplitOptions]::RemoveEmptyEntries)
$adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
$cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
$essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
$federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
$retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
$siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
$syncFreq = Read-Host -Prompt 'Input new sync frequency'

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
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $teamsUserId -EnabledConnectorScenario $updatedConnectorScenario -EnabledWfiScenario $updatedWfiScenario -Name $UpdatedInstanceName -SyncFrequencyInMin $syncFreq -IfMatch $Etag -ConnectorAdminEmail $AdminEmailList

#Get a list of the mappings
Write-Host "Listing mappings"
$TeamMaps = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $TeamMaps

#Modify a mapping
#Remove a mapping
Write-Host "Removing a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to unlink'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to unlink'
Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId
Write-Host "Success"

#Add a mapping
Write-Host "Adding a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to link'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to link'
New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"
```

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>Désactiver les shifts ouverts, les demandes de shifts ouverts, les demandes de permutation et les demandes de congés.

> [!IMPORTANT]
> Suivez ces étapes uniquement si vous avez choisi de désactiver les équipes ouvertes, les demandes d’équipes ouvertes, les demandes de permutation ou les demandes de congés à l’aide du script de la section [Modifier les paramètres de connexion](#change-connection-settings) plus haut dans cet article ou à l’aide du cmdlet [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance). L’exécution de cette étape masque la fonctionnalité dans Shifts. Sans cette deuxième étape, les utilisateurs verront toujours la fonctionnalité dans Shifts et recevront un message d’erreur « opération non prise en charge » s’ils essaient de l’utiliser.

Pour masquer les équipes ouvertes, les demandes de permutation et les demandes de congés dans les équipes, utilisez le [type de ressource de planification](/graph/api/resources/schedule) de l’API graphique pour définir les paramètres suivants pour```false``` chaque équipe que vous avez associée à une instance WFM Blue Yonder :

- Ouvrir les shifts : ```openShiftsEnabled```
- Demandes d’échange :  ```swapShiftsRequestsEnabled```
- Demandes de congé : ```timeOffRequestsEnabled```

Pour masquer les demandes de shifts ouverts dans Shifts, accédez à **Paramètres** dans Shifts, puis désactivez le paramètre **Ouvrir les shifts** .

## <a name="unmap-a-team-from-one-connection-and-map-it-to-another-connection"></a>Annuler le mappage d’une équipe d’une connexion et la mapper à une autre connexion

> [!NOTE]
> Le compte système Microsoft 365 doit être le même pour les deux connexions. Si ce n’est pas le cas, le message d’erreur « Ce profil d’acteur désigné n’a pas de privilèges de propriété d’équipe » s’affiche.

Si vous souhaitez dissocier une équipe d’une connexion et la mapper à une autre connexion :

1. [Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait).
1. Affichez la liste de tous les mappages d’équipe pour une connexion.

    ```powershell
    Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. Supprimez un mappage d’équipe de la connexion.

    ```powershell
    Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId>
    ```

1. Mappez l’équipe à une autre connexion.

    ```powershell
    New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId> -WfmTeamId <SiteId> -TimeZone <TimeZone>
    ```

Pour plus d’informations, consultez [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap), [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) et [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap).

## <a name="disable-sync-for-a-connection"></a>Désactiver la synchronisation pour une connexion

Utilisez ce script pour désactiver la synchronisation d’une connexion. Gardez à l’esprit que ce script ne supprime pas une connexion. Il désactive la synchronisation afin qu’aucune donnée ne soit synchronisée entre Shifts et Blue Yonder WFM pour la connexion que vous spécifiez.

[Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait), puis exécutez le script suivant.

```powershell
#Disable sync script
Write-Host "Disable sync"
#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to disable sync'
    $Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
    $Etag = $Instance.etag
    $InstanceName = $Instance.Name
    $DesignatedActorId = $Instance.designatedActorId
    $adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
    $cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
    $essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
    $federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
    $retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
    $siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
    $ConnectorAdminEmail = $Instance.ConnectorAdminEmail
}
else {
    throw "Instance list is empty"
}

#Remove scenarios in the mapping
Write-Host "Disabling scenarios in the team mapping"
$UpdatedInstanceName = $InstanceName + " - Disabled"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $DesignatedActorId -EnabledConnectorScenario @() -EnabledWfiScenario @() -Name $UpdatedInstanceName -SyncFrequencyInMin 60 -IfMatch $Etag -ConnectorAdminEmail $ConnectorAdminEmail

if ($UpdatedInstance.Id -ne $null) {
    Write-Host "Success"
}
else {
    throw "Update instance failed"
}
```

## <a name="shifts-connector-cmdlets"></a>Applets de commande du connecteur Shifts

Pour obtenir de l’aide sur les applets de commande du connecteur Shifts, recherchez **CsTeamsShiftsConnection** dans la [référence de l’applet de commande Teams PowerShell](/powershell/teams/intro). Voici des liens vers certaines applets de commande couramment utilisées.

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
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Présentation de Teams PowerShell](/microsoftteams/teams-powershell-overview)
