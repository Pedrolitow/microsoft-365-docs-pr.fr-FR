---
title: Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment utiliser PowerShell pour gérer votre connexion Shifts à UKG Dimensions.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 411af2e33537cebd1325dc3d4e1f2f29b130a16d
ms.sourcegitcommit: 3d7dd25abcbf923b45eae84ff4d9d2bb95ef4ca4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68777726"
---
# <a name="use-powershell-to-manage-your-shifts-connection-to-ukg-dimensions"></a>Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG

[!INCLUDE [preview-feature](includes/preview-feature.md)]

## <a name="overview"></a>Vue d’ensemble

Le [connecteur Microsoft Teams Shifts pour UKG Dimensions](shifts-connectors.md#microsoft-teams-shifts-connector-for-ukg-dimensions) vous permet d’intégrer l’application Shifts dans Microsoft Teams avec UKG Dimensions. Une fois que vous avez configuré une connexion, vos employés de première ligne peuvent afficher et gérer en toute transparence leurs planifications dans ukG Dimensions à partir de Shifts.

Vous pouvez utiliser [l’Assistant Connecteur Shifts](shifts-connector-wizard-ukg.md) dans le Centre d’administration Microsoft 365 ou [PowerShell](shifts-connector-ukg-powershell-setup.md) pour configurer une connexion. Une fois la connexion configurée, vous pouvez la gérer à l’aide [des applets de commande PowerShell du connecteur Shifts](#shifts-connector-cmdlets).

Cet article explique comment utiliser PowerShell pour effectuer les opérations suivantes :

- [Vérifier l’état de l’installation de la connexion](#check-connection-setup-status)
- [Afficher un rapport d’erreurs pour une connexion](#view-an-error-report-for-a-connection)
- [Résoudre les erreurs de connexion](#resolve-connection-errors)
- [Modifier les paramètres de connexion](#change-connection-settings)
- [Annuler le mappage d’une équipe d’une connexion et la mapper à une autre connexion](#unmap-a-team-from-one-connection-and-map-it-to-another-connection)
- [Désactiver la synchronisation pour une connexion](#disable-sync-for-a-connection)

Cet article part du principe que vous avez déjà configuré une connexion à UKG Dimensions, à l’aide de l’Assistant ou de PowerShell.

> [!NOTE]
> Vous pouvez également gérer votre connexion dans le Centre d'administration Microsoft 365. Par exemple, vous pouvez vérifier l’état d’intégrité et accéder à l’Assistant pour modifier les paramètres de connexion. Pour plus d’informations, consultez [Utiliser la Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-admin-center-manage.md).

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

[!INCLUDE [shifts-connector-check-setup-status](includes/shifts-connector-check-setup-status.md)]

## <a name="view-an-error-report-for-a-connection"></a>Afficher un rapport d’erreurs pour une connexion

[!INCLUDE [shifts-connector-view-error-report](includes/shifts-connector-view-error-report.md)]

> [!NOTE]
> Pour obtenir la liste complète des messages d’erreur, consultez [Liste des messages d’erreur](#list-of-error-messages) plus loin dans cet article.

## <a name="resolve-connection-errors"></a>Résoudre les erreurs de connexion

### <a name="user-mapping-errors"></a>Erreurs de mappage d’utilisateurs

Des erreurs de mappage d’utilisateurs peuvent se produire si un ou plusieurs utilisateurs d’une instance WFM ne sont pas membres de l’équipe mappée dans Teams. Pour résoudre ce problème, assurez-vous que les utilisateurs de l’équipe mappée correspondent aux utilisateurs de l’instance WFM.

Pour afficher les détails des utilisateurs non mappés, [configurez votre environnement](#set-up-your-environment) (si ce n’est pas déjà fait), puis exécutez le script suivant.

```powershell
#View sync errors script
Write-Host "View sync errors"
Start-Sleep 1

#Ensure Teams module is of version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.7.0
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

[!INCLUDE [shifts-connector-account-authorization-errors](includes/shifts-connector-account-authorization-errors.md)]

## <a name="change-connection-settings"></a>Modifier les paramètres de connexion

[!INCLUDE [shifts-connector-change-connection-settings](includes/shifts-connector-change-connection-settings.md)]

[Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait), puis exécutez le script suivant.

```powershell
#Update connector instance and mapping script
Write-Host "Update Connector instance and mapping"
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
$UkgId = "95BF2848-2DDA-4425-B0EE-D62AEED4C0A0"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$Ukg = $connectors | where {$_.Id -match $UkgId}

#List connection instances available
Write-Host "Listing connection instances available"
$InstanceList = Get-CsTeamsShiftsConnectionInstance | where {$_.ConnectorId -match $UkgId}
write $InstanceList

#Prompt for the WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Get the instance ID
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
$apiUrl = $Instance.ConnectorSpecificSettingApiUrl
$ssoUrl = $Instance.ConnectorSpecificSettingSsoUrl
$clientId = $Instance.ConnectorSpecificSettingClientId
$syncFreq = Read-Host -Prompt 'Input new sync frequency'
$AppKey = Read-Host -Prompt 'Input your app key' -AsSecureString
$plainKey =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($AppKey))
$ClientSecret = Read-Host -Prompt 'Input your client secret' -AsSecureString
$plainSecret =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($ClientSecret))

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
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance `
    -ConnectorInstanceId $InstanceId `
    -ConnectorId $UkgId `
    -ConnectorAdminEmail $AdminEmailList `
    -DesignatedActorId $teamsUserId `
    -EnabledConnectorScenario $updatedConnectorScenario `
    -EnabledWfiScenario $updatedWfiScenario `
    -Name $UpdatedInstanceName `
    -SyncFrequencyInMin $syncFreq `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificUkgDimensionsSettingsRequest `
        -Property @{
            apiUrl = $apiUrl
            ssoUrl = $ssoUrl
            appKey = $plainKey
            clientId = $clientId
            clientSecret = $plainSecret
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
        }) `
    -IfMatch $Etag
if ($UpdatedInstance.Id -ne $null) {
    Write-Host "Success"
}
else {
    throw "Update instance failed"
}
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

[!INCLUDE [shifts-connector-disable-shifts-requests](includes/shifts-connector-disable-shifts-requests.md)]

## <a name="unmap-a-team-from-one-connection-and-map-it-to-another-connection"></a>Annuler le mappage d’une équipe d’une connexion et la mapper à une autre connexion

[!INCLUDE [shifts-connector-unmap-a-team](includes/shifts-connector-unmap-a-team.md)]

## <a name="disable-sync-for-a-connection"></a>Désactiver la synchronisation pour une connexion

Utilisez ce script pour désactiver la synchronisation d’une connexion. Gardez à l’esprit que ce script ne supprime pas une connexion. Il désactive la synchronisation afin qu’aucune donnée ne soit synchronisée entre Shifts et votre système WFM pour la connexion que vous spécifiez.

[Configurez votre environnement](#set-up-your-environment) (si vous ne l’avez pas déjà fait), puis exécutez le script suivant.

```powershell
#Disable sync script
Write-Host "Disable sync"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.7.0
} catch {
    throw
}

#List connection instances available
$UkgId = "95BF2848-2DDA-4425-B0EE-D62AEED4C0A0"
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance | where {$_.ConnectorId -match $UkgId}
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to disable sync'
    $Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
    $Etag = $Instance.etag
    $InstanceName = $Instance.Name
    $DesignatedActorId = $Instance.designatedActorId
    $apiUrl = $Instance.ConnectorSpecificSettingApiUrl
    $ssoUrl = $Instance.ConnectorSpecificSettingSsoUrl
    $clientId = $Instance.ConnectorSpecificSettingClientId
    $ConnectorAdminEmail = $Instance.ConnectorAdminEmail
}
else {
    throw "Instance list is empty"
}

#Remove scenarios in the mapping
Write-Host "Disabling scenarios in the team mapping"
$UpdatedInstanceName = $InstanceName + " - Disabled"
$UkgId = "95BF2848-2DDA-4425-B0EE-D62AEED4C0A0"
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))
$AppKey = Read-Host -Prompt 'Input your app key' -AsSecureString
$plainKey =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($AppKey))
$ClientSecret = Read-Host -Prompt 'Input your client secret' -AsSecureString
$plainSecret =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($ClientSecret))

$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance `
    -ConnectorInstanceId $InstanceId `
    -ConnectorId $UkgId `
    -ConnectorAdminEmail $ConnectorAdminEmail `
    -DesignatedActorId $DesignatedActorId `
    -EnabledConnectorScenario @() `
    -EnabledWfiScenario @() `
    -Name $UpdatedInstanceName `
    -SyncFrequencyInMin 10 `
    -ConnectorSpecificSettings (New-Object Microsoft.Teams.ConfigAPI.Cmdlets.Generated.Models.ConnectorSpecificUkgDimensionsSettingsRequest `
        -Property @{
            apiUrl = $apiUrl
            ssoUrl = $ssoUrl
            appKey = $plainKey
            clientId = $clientId
            clientSecret = $plainSecret
            LoginUserName = $WfmUserName
            LoginPwd = $plainPwd
        }) `
    -IfMatch $Etag

if ($UpdatedInstance.Id -ne $null) {
    Write-Host "Success"
}
else {
    throw "Update instance failed"
}
```

## <a name="list-of-error-messages"></a>Liste des messages d’erreur

Voici la liste des messages d’erreur que vous pouvez rencontrer et des informations pour vous aider à les résoudre.

|Type d’erreur |Détails de l’erreur |Résolution |
|---------|---------|---------|
|Impossible d’authentifier le système de gestion du personnel.|Les informations d’identification du compte système de gestion de la main-d’œuvre que vous avez fournies ne sont pas valides ou ce compte ne dispose pas des autorisations requises.|Mettez à jour les informations d’identification de votre compte de service WFM dans les paramètres de connexion. Pour cela, appliquez l’une des méthodes suivantes :<ul><li>Dans la Centre d'administration Microsoft 365, choisissez **Modifier** dans la page Gestion des connecteurs ou dans la page des détails de connexion pour accéder à l’Assistant Connecteur Shifts.</li><li>Utilisez l’applet de [commande Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) ou [Update-CsTeamsShiftsConnectionInstance](/powershell/module/teams/update-csteamsshiftsconnectioninstance) .</li><li>Utilisez [ce script PowerShell](#change-connection-settings).</li></ul>|
|Impossible d’authentifier Graph. |Échec de l’authentification. Vérifiez que vous avez entré des informations d’identification valides pour l’acteur désigné et que vous disposez des autorisations requises.|Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br> Vous pouvez également mettre à jour les informations d’identification de votre compte système Microsoft 365 dans les paramètres de connexion.|
|Certains utilisateurs n’ont pas pu mapper correctement|Le mappage a échoué pour certains utilisateurs : \<X\> réussite, \<X\> échec des utilisateurs AAD et \<X\> échec du ou des utilisateurs du système de gestion de la main-d’œuvre.|Utilisez l’applet de commande [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult) ou [ce script PowerShell](#user-mapping-errors) pour identifier les utilisateurs pour lesquels le mappage a échoué. Assurez-vous que les utilisateurs de l’équipe mappée correspondent aux utilisateurs de l’instance WFM.|
|Impossible de mapper une équipe ou des équipes dans ce lot. |Ce profil d’acteur désigné n’a pas de privilèges de propriété d’équipe. |Assurez-vous que votre compte système Microsoft 365 (également appelé acteur désigné) est ajouté en tant que propriétaire d’équipe.<br>Si vous avez modifié votre compte système Microsoft 365, ajoutez ce compte en tant que propriétaire d’équipe et mettez à jour les paramètres de connexion pour utiliser ce compte.|
|    |Cette équipe est déjà mappée à une instance de connecteur existante. |Annulez le mappage de l’équipe de la connexion existante à l’aide de l’applet de commande [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) . Vous pouvez également créer une connexion pour remapper l’équipe.|
|    |Ce fuseau horaire n’est pas valide. Le fuseau horaire passé n’utilise pas le format de base de données tz.|Vérifiez que le fuseau horaire est correct, puis remapper l’équipe.|
|    |Nous ne trouvons pas cette instance de connecteur.|Mappez l’équipe à une connexion existante.|
|    |Cette équipe AAD est introuvable.|Assurez-vous que l’équipe existe ou créez-en une.|

## <a name="shifts-connector-cmdlets"></a>Applets de commande du connecteur Shifts

Pour obtenir de l’aide sur les applets de commande du connecteur Shifts, recherchez **CsTeamsShiftsConnection** dans la [référence de l’applet de commande Teams PowerShell](/powershell/teams/intro). Voici des liens vers certaines applets de commande couramment utilisées.

- [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation)
- [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance)
- [Get-CsTeamsShiftsConnectionInstance](/powershell/module/teams/get-csteamsshiftsconnectioninstance)
- [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance)
- [Update-CsTeamsShiftsConnectionInstance](/powershell/module/teams/update-csteamsshiftsconnectioninstance)
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
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à UKG Dimensions](shifts-connector-wizard-ukg.md)
- [Utiliser PowerShell pour connecter Shifts à UKG Dimensions](shifts-connector-ukg-powershell-setup.md)
- [Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-admin-center-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Présentation de Teams PowerShell](/microsoftteams/teams-powershell-overview)
