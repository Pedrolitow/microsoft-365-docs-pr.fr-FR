---
title: 'Créer un rapport sur les conservations définies dans les cas eDiscovery '
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/11/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment générer un rapport qui contient des informations sur toutes les conservations associées à des cas eDiscovery.
ms.openlocfilehash: 35e432104e7c1358887eb89ae96b9bb0d1d12a0f
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546976"
---
# <a name="create-a-report-on-holds-in-ediscovery-cases"></a>Créer un rapport sur les conservations définies dans les cas eDiscovery 

Le script de cet article permet aux administrateurs eDiscovery et aux gestionnaires eDiscovery de générer un rapport contenant des informations sur toutes les suspensions associées à des cas eDiscovery dans le centre de conformité dans Office 365 ou Microsoft 365. Le rapport contient des informations telles que le nom du cas dans lequel une conservation est associée, les emplacements de contenu placés en conservation et si la suspension est basée sur une requête. S’il existe des cas qui n’ont aucune conservation, le script crée un rapport supplémentaire avec une liste de cas sans conservation.

Consultez la section [plus d’informations](#more-information) pour obtenir une description détaillée des informations incluses dans le rapport.

## <a name="admin-requirements-and-script-information"></a>Exigences en matière d’administration et informations sur les scripts

- Pour générer un rapport sur tous les cas de découverte électronique dans votre organisation, vous devez être un administrateur de découverte électronique dans votre organisation. Si vous êtes un gestionnaire eDiscovery, le rapport n’inclut que les informations sur les cas accessibles. Pour plus d’informations sur les autorisations de découverte électronique, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md).

- Le script de cet article a une gestion des erreurs minimale. L’objectif principal est de créer rapidement un rapport sur les conservations associées aux cas eDiscovery dans votre organisation.

- Les exemples de script fournis dans cette rubrique ne sont pris en charge dans aucun programme de support ou service standard de Microsoft. Les exemples de scripts sont fournis en l’état, sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. Vous assumez tous les risques liés à l’utilisation ou à l’exécution des exemples de scripts et de la documentation. En aucun cas, Microsoft, ses auteurs ou toute personne impliquée dans la création, la production ou la livraison des scripts ne sont responsables de dommages quelconques (y compris, sans limitation, pertes de bénéfices, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-connect-to-the-security--compliance-center-powershell"></a>Étape 1 : Connectez-vous au centre de sécurité & conformité PowerShell

La première étape consiste à vous connecter à la sécurité & Centre de conformité PowerShell pour votre organisation. Pour consulter des instructions détaillées, voir [Se connecter au Centre de sécurité et conformité PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>Étape 2 : exécuter le script pour signaler les suspensions associées à des cas de découverte électronique

Une fois que vous êtes connecté à la sécurité & Centre de conformité PowerShell, l’étape suivante consiste à créer et exécuter le script qui collecte des informations sur les cas eDiscovery dans votre organisation.

1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier. ps1 ; par exemple, CaseHoldsReport.ps1.

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
   $Path = Read-Host 'Enter a file path to save the report to a .csv file'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
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
   $allholdreport = $addRow | Select-Object "Case name","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
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

2. Dans la session Windows PowerShell qui s’est ouverte à l’étape 1, accédez au dossier où vous avez enregistré le script.

3. Exécutez le script ; par exemple :

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   Le script vous invite à entrer un dossier cible dans lequel enregistrer le rapport.

4. Tapez le chemin d’accès complet du dossier dans lequel le rapport doit être enregistré, puis appuyez sur **entrée**.

   > [!TIP]
   > Pour enregistrer le rapport dans le dossier dans lequel se trouve le script, tapez un point (« . ») lorsque vous êtes invité à indiquer un dossier cible. Pour enregistrer le rapport dans un sous-dossier du dossier où se trouve le script, tapez simplement le nom du sous-dossier.

   Le script commence à collecter des informations sur tous les cas de découverte électronique dans votre organisation. N’accédez pas au fichier de rapport pendant l’exécution du script. Une fois le script terminé, un message de confirmation s’affiche dans la session Windows PowerShell. Une fois ce message affiché, vous pouvez accéder au rapport dans le dossier que vous avez spécifié à l’étape 4. Le nom de fichier du rapport est `CaseHoldsReport<DateTimeStamp>.csv` .

   Plus, le script crée également un rapport avec une liste de cas qui n’ont aucune conservation. Le nom de fichier de ce rapport est `CaseswithNoHolds<DateTimeStamp>.csv` .

   Voici un exemple d’exécution du script CaseHoldsReport.ps1.

   ![Sortie après l’exécution du script CaseHoldsReport.ps1](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>Plus d’informations

Le rapport de suspension de cas qui est créé lorsque vous exécutez le script dans cet article contient les informations suivantes sur chaque blocage. Comme expliqué précédemment, vous devez être un administrateur eDiscovery pour renvoyer des informations pour toutes les suspensions de votre organisation. Pour plus d’informations sur les conservations d’incidents, consultez la rubrique [cas eDiscovery](ediscovery-cases.md).

- Nom de la conservation et nom du cas eDiscovery auquel la conservation est associée.

- Indique si le cas de découverte électronique est actif ou fermé.

- Indique si la conservation est activée ou désactivée.

- Membres du cas eDiscovery auquel est associée la conservation. Les membres de cas peuvent afficher ou gérer un cas, en fonction des autorisations eDiscovery auxquelles ils ont été affectés.

- Date et heure de création de la demande de devis.

- Si une demande de devis est fermée, la personne qui l’a fermée et l’heure et la date de clôture.

- Les emplacements des boîtes aux lettres Exchange et des sites SharePoint en conservation.

- Si la suspension est basée sur une requête, la syntaxe de requête.

- L’heure et la date de création de la conservation et la personne qui l’a créée.

- Date et heure de la dernière modification de la conservation et de la personne qui l’a modifiée.
