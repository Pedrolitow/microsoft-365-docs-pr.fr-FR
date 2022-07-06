---
title: Utiliser un script pour créer un rapport de conservation eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 05/10/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment générer un rapport qui contient des informations sur toutes les conservations associées aux cas eDiscovery.
ms.openlocfilehash: 9820eba0e29a510a1881a9349f63c7e2d9650728
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625476"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>Utiliser un script pour créer un rapport sur les conservations dans les cas eDiscovery

Le script de cet article permet aux administrateurs eDiscovery et aux responsables eDiscovery de générer un rapport qui contient des informations sur toutes les conservations associées aux cas eDiscovery (Standard) et eDiscovery (Premium) dans le portail de conformité Microsoft Purview. Le rapport contient des informations telles que le nom du cas auquel une conservation est associée, les emplacements de contenu mis en attente et la question de savoir si la conservation est basée sur une requête. S’il existe des cas qui n’ont pas de conservations, le script crée un rapport supplémentaire avec une liste de cas sans conservation.

Consultez la section [Plus d’informations](#more-information) pour obtenir une description détaillée des informations incluses dans le rapport.

## <a name="admin-requirements-and-script-information"></a>Administration exigences et informations de script

- Pour générer un rapport sur tous les cas eDiscovery de votre organisation, vous devez être administrateur eDiscovery dans votre organisation. Si vous êtes gestionnaire eDiscovery, le rapport inclut uniquement des informations sur les cas auxquels vous pouvez accéder. Pour plus d’informations sur les autorisations eDiscovery, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md).

- Le script de cet article dispose d’une gestion minimale des erreurs. L’objectif principal est de créer rapidement un rapport sur les conservations associées aux cas eDiscovery dans votre organisation.

- Les exemples de script fournis dans cette rubrique ne sont pris en charge dans aucun programme de support ou service standard de Microsoft. Les exemples de scripts sont fournis en l’état, sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. Vous assumez tous les risques liés à l’utilisation ou à l’exécution des exemples de scripts et de la documentation. En aucun cas, Microsoft, ses auteurs ou toute personne impliquée dans la création, la production ou la livraison des scripts ne sont responsables de dommages quelconques (y compris, sans limitation, pertes de bénéfices, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-connect-to-security--compliance-powershell"></a>Étape 1 : Connectez-vous à Security & Compliance PowerShell

La première étape consiste à se connecter à Security & Compliance PowerShell pour votre organisation. Pour consulter des instructions détaillées, consultez [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Étape 2 : Exécuter le script pour signaler les conservations associées aux cas eDiscovery

Une fois que vous êtes connecté à Security & Compliance PowerShell, l’étape suivante consiste à créer et exécuter le script qui collecte des informations sur les cas eDiscovery dans votre organisation.

1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de .ps1 ; par exemple, CaseHoldsReport.ps1.

   ```powershell
   #script begin
   " "
   write-host "***********************************************"
   write-host "   Security & Compliance Center   " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "        eDiscovery cases - Holds report         " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "***********************************************"
   " "
   #prompt users to specify a path to store the output files
   $time=get-date
   $Path = Read-Host 'Enter a folder path to save the report to a .csv file (filename is created automatically)'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casetype,
   [String]$casestatus,
   [datetime]$casecreatedtime,
   [string]$casemembers,
   [datetime]$caseClosedDateTime,
   [string]$caseclosedby,
   [string]$holdname,
   [String]$Holdenabled,
   [string]$holdcreatedby,
   [string]$holdlastmodifiedby,
   [string]$ExchangeLocation,
   [string]$sharePointlocation,
   [string]$ContentMatchQuery,
   [datetime]$holdcreatedtime,
   [datetime]$holdchangedtime
   )
   $addRow = New-Object PSObject
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case name" -Value $casename
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case type" -Value $casetype
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case status" -Value $casestatus
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case members" -Value $casemembers
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case created time" -Value $casecreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed time" -Value $caseClosedDateTime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed by" -Value $caseclosedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold name" -Value $holdname
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold enabled" -Value $Holdenabled
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created by" -Value $holdcreatedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold last changed by" -Value $holdlastmodifiedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Exchange locations" -Value  $ExchangeLocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "SharePoint locations" -Value $sharePointlocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold query" -Value $ContentMatchQuery
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created time (UTC)" -Value $holdcreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold changed time (UTC)" -Value $holdchangedtime
   $allholdreport = $addRow | Select-Object "Case name","Case type","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Standard) cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Premium) cases and holds..."
   " "
   $edc =Get-ComplianceCase -CaseType Advanced -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus -casetype $cc.casetype $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }

   " "
   Write-host "Script complete! Report files saved to this folder: '$Path'"
   " "
   #script end
   ```

2. Dans la session Windows PowerShell qui s’est ouverte à l’étape 1, accédez au dossier dans lequel vous avez enregistré le script.

3. Exécutez le script ; par exemple :

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Le script demande un dossier cible dans lequel enregistrer le rapport.

4. Tapez le nom complet du chemin d’accès du dossier dans lequel enregistrer le rapport, puis **appuyez sur Entrée**.

   > [!TIP]
   > Pour enregistrer le rapport dans le même dossier que celui où se trouve le script, tapez un point (« . ») quand vous êtes invité à entrer un dossier cible. Pour enregistrer le rapport dans un sous-dossier dans le dossier où se trouve le script, tapez simplement le nom du sous-dossier.

   Le script commence à collecter des informations sur tous les cas eDiscovery dans votre organisation. N’accédez pas au fichier de rapport pendant l’exécution du script. Une fois le script terminé, un message de confirmation s’affiche dans la session Windows PowerShell. Une fois ce message affiché, vous pouvez accéder au rapport dans le dossier que vous avez spécifié à l’étape 4. Le nom de fichier du rapport est `CaseHoldsReport<DateTimeStamp>.csv`.

   En outre, le script crée également un rapport avec une liste de cas qui n’ont aucune conservation. Le nom de fichier de ce rapport est `CaseswithNoHolds<DateTimeStamp>.csv`.

   Voici un exemple d’exécution du script CaseHoldsReport.ps1.

   ![Sortie après l’exécution du script CaseHoldsReport.ps1.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Plus d’informations

Le cas contient le rapport créé lorsque vous exécutez le script dans cet article contient les informations suivantes sur chaque conservation. Comme expliqué précédemment, vous devez être administrateur eDiscovery pour retourner des informations sur toutes les conservations de votre organisation. Pour plus d’informations sur les conservations de cas, consultez [les cas eDiscovery](./get-started-core-ediscovery.md).

- Nom de la conservation et nom du cas eDiscovery auquel la conservation est associée.

- Indique si la conservation est associée à un cas eDiscovery (Standard) ou eDiscovery (Premium).

- Indique si le cas eDiscovery est actif ou fermé.

- Indique si la conservation est activée ou désactivée.

- Membres du cas eDiscovery auquel la conservation est associée. Les membres de cas peuvent afficher ou gérer un cas, en fonction des autorisations eDiscovery qui leur ont été attribuées.

- Heure et date de création du cas.

- Si une affaire est classée, la personne qui l’a fermée et l’heure et la date à laquelle elle a été fermée.

- Emplacements des boîtes aux lettres Exchange et des sites SharePoint en attente.

- Si la conservation est basée sur une requête, la syntaxe de requête.

- Heure et date de création de la conservation et de la personne qui l’a créée.

- Heure et date à laquelle la conservation a été modifiée pour la dernière fois et la personne qui l’a modifiée.
