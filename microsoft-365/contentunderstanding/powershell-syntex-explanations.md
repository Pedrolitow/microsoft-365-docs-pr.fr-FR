---
title: Travailler avec des explications de modèle de présentation de document dans PowerShell
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: normal
description: Découvrez comment travailler avec SharePoint Syntex des explications de modèle dans PowerShell.
ms.openlocfilehash: 06f0eb7314b85f9463689fea32667666e5e167fd
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2022
ms.locfileid: "62159708"
---
# <a name="work-with-document-understanding-model-explanations-in-powershell"></a>Travailler avec des explications de modèle de présentation de document dans PowerShell

> [!IMPORTANT]
> Les SharePoint Syntex PowerShell et tous les autres composants PnP sont des outils open source soutenus par une communauté active qui les aide. Il n’existe aucun contrat de niveau de service pour la prise en charge des outils open source des canaux de support Microsoft officiels.

Les modèles d’explication personnalisés sont stockés dans une liste dans un centre de contenu. Étant donné que ces explications sont stockées en tant qu’éléments de liste, PowerShell peut être utilisé pour interagir avec eux.

## <a name="list-saved-explanations"></a>Liste des explications enregistrées

Cet exemple montre comment afficher tous les modèles d’explication personnalisés qui ont été enregistrés dans un centre de contenu spécifique.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list and items
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"
$explanations = Get-PnPListItem -List $explanationTemplatesList -Fields "Id", "Title", "ExplanationName", "ExplanationType", "ExplanationDescription","ExplanationContent"

# Extract explanation components
$explanationValues = $explanations.fieldvalues 
$explanationOutput = @()

foreach ($explanation in $explanationValues) {
    $content = $explanation.ExplanationContent
    $content = $content.replace('false','"false"')
    $content = $content.replace('true','"true"')
    $contentArray = $content | ConvertFrom-Json

    $output = New-Object -TypeName PSObject
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Name" -Value $explanation.ExplanationName
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Description" -Value $explanation.ExplanationDescription
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Type" -Value $contentArray.kind
    Add-Member -InputObject $output -MemberType NoteProperty -Name "RegEx Pattern" -Value $contentArray.pattern
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Phrase List" -Value $contentArray.ngrams
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Case Sensitive" -Value $contentArray.caseSensitive
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Ignore Digit Identity" -Value $contentArray.ignoreDigitIdentity
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Ignore Letter Identity" -Value $contentArray.ignoreLetterIdentity

    $explanationOutput += $output
}

$explanationOutput
```

## <a name="create-a-phrase-list-explanation"></a>Créer une explication de liste d’expressions

Cet exemple montre comment créer un modèle d’explication de liste d’expressions personnalisée.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$explanationName = "Phrase Explanation A"
$explanationDescription = "This is my explanation"
$phrases = "Phrase 1", "Phrase 2"
$caseSensitive = $false
$ignoreDigitIdentity= $false
$ignoreLetterIdentity = $false

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

#Format phrase list
$phrases = $phrases -join "`",`""

#Convert booleans to lower case strings
$caseSensitive = ($caseSensitive.ToString()).ToLower()
$ignoreDigitIdentity= ($ignoreDigitIdentity.ToString()).ToLower()
$ignoreLetterIdentity = ($ignoreLetterIdentity.ToString()).ToLower()

# Build explanation content
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"dictionaryFeature`",`"name`":`"$explanationName`",`"active`":true,`"nGrams`":[`"$phrases`"],`"caseSensitive`":$caseSensitive,`"ignoreDigitIdentity`":$ignoreDigitIdentity,`"ignoreLetterIdentity`":$ignoreLetterIdentity}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```

## <a name="create-a-regular-expression-explanation"></a>Créer une explication d’expression régulière

Cet exemple montre comment créer un modèle d’explication d’expression régulière personnalisé.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$explanationName = "RegEx Explanation A"
$explanationDescription = "This is my explanation"
$pattern = "\b(https?):\/\/\S+"

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

# Build explanation content
$pattern = $pattern.Replace('\','\\')
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"regexFeature`",`"name`":`"$explanationName`",`"active`":true,`"pattern`":`"$pattern`"}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```

## <a name="create-a-phrase-list-explanation-based-on-a-term-set"></a>Créer une explication de liste d’expressions basée sur un ensemble de termes

Cet exemple montre comment créer un modèle d’explication de liste d’expressions personnalisée en prenant les valeurs d’un ensemble de termes. Cela inclut les noms de termes préférés et tous les synonymes.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$termSetName = "Terms"
$termGroupName = "GroupA"
$explanationName = "MMS Explanation A"
$explanationDescription = "This is my explanation"
$caseSensitive = $false
$ignoreDigitIdentity= $false
$ignoreLetterIdentity = $false

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

#Get term set, including preferred labels and synonyms
$terms = Get-PnPTerm -TermGroup $termGroupName -TermSet $termSetName -Includes Labels
$phrases = $terms.labels.value

#Format phrase list
$phrases = $phrases -join "`",`""

#Convert booleans to lower case strings
$caseSensitive = ($caseSensitive.ToString()).ToLower()
$ignoreDigitIdentity= ($ignoreDigitIdentity.ToString()).ToLower()
$ignoreLetterIdentity = ($ignoreLetterIdentity.ToString()).ToLower()

# Build explanation content
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"dictionaryFeature`",`"name`":`"$explanationName`",`"active`":true,`"nGrams`":[`"$phrases`"],`"caseSensitive`":$caseSensitive,`"ignoreDigitIdentity`":$ignoreDigitIdentity,`"ignoreLetterIdentity`":$ignoreLetterIdentity}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```
