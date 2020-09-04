---
title: Cloner une recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: Utilisez le script PowerShell dans cet article pour cloner rapidement une recherche de contenu existante dans le centre de conformité dans Office 365 ou Microsoft 365.
ms.openlocfilehash: 9bc9329d31ae27736bdcd399c555f5d70bb9c761
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47357902"
---
# <a name="clone-a-content-search"></a>Cloner une recherche de contenu

La création d’une recherche de contenu dans le centre de conformité dans Office 365 ou Microsoft 365 recherche plusieurs boîtes aux lettres ou sites SharePoint et OneDrive entreprise peut prendre un certain temps. La spécification des sites à rechercher peut également être sujette à des erreurs si vous entrez une URL erronée. Pour éviter ces problèmes, vous pouvez utiliser le script Windows PowerShell dans cet article pour cloner rapidement une recherche de contenu existante. Lorsque vous clonez une recherche, une nouvelle recherche (avec un nom différent) est créée, qui contient les mêmes propriétés (telles que les emplacements de contenu et la requête de recherche) en tant que recherche d’origine. Ensuite, vous pouvez modifier la nouvelle recherche en changeant la requête par mot clé ou la plage de dates, puis l’exécuter.
  
Pourquoi le clonage du contenu effectue des recherches ?
  
- Pour comparer les résultats de différentes requêtes de recherche par mot clé exécutées sur les mêmes emplacements de contenu.
    
- Pour éviter de devoir entrer un grand nombre d’emplacements de contenu lors de la création d’une recherche.
    
- Pour réduire la taille des résultats de la recherche. Par exemple, si vous avez une recherche qui renvoie un trop grand nombre de résultats à exporter, vous pouvez cloner la recherche, puis ajouter une condition de recherche basée sur une plage de dates pour réduire le nombre de résultats de recherche.
  
## <a name="script-information"></a>Informations sur le script

- Pour exécuter le script décrit dans cette rubrique, vous devez être membre du groupe de rôles gestionnaire eDiscovery dans le centre de sécurité & conformité.
    
- Le script inclut une gestion des erreurs minimale. Le principal objectif du script est de cloner rapidement une recherche de contenu.
    
- Le script crée une recherche de contenu, mais ne le démarre pas.
    
- Ce script prend en compte si la recherche de contenu que vous clonez est associée à un cas de découverte électronique. Si la recherche est associée à un cas, la nouvelle recherche est également associée à la même casse. Si la recherche existante n’est pas associée à un cas, la nouvelle recherche est indiquée sur la page **recherche de contenu** dans le centre de conformité. 
    
- L’exemple de script fourni dans cette rubrique n’est pas pris en charge dans le cadre d’un service ou d’un programme de support standard Microsoft. L’exemple de script est fourni en l’État sans aucune garantie. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. L’ensemble des risques liés à l’utilisation ou aux performances de l’exemple de script et de la documentation reste avec vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.
  
## <a name="step-1-run-the-script-to-clone-a-search"></a>Étape 1 : exécuter le script pour cloner une recherche

Le script de cette étape crée une recherche de contenu en clonant une recherche existante. Lorsque vous exécutez ce script, vous êtes invité à fournir les informations suivantes :
  
- **Vos informations d’identification utilisateur** : le script utilisera vos informations d’identification pour vous connecter au centre de sécurité & conformité de votre organisation avec Windows PowerShell. Comme indiqué précédemment, vous devez être membre du groupe de rôles gestionnaire de découverte électronique dans le centre de sécurité & compCompliance pour exécuter le script. 
    
- **Nom de la recherche existante** : il s’agit de la recherche de contenu que vous souhaitez Cloner. 
    
- **Nom de la nouvelle recherche qui sera créée** : Si vous laissez cette valeur vide, le script crée un nom pour la nouvelle recherche basée sur le nom de la recherche que vous clonez. 
    
Pour cloner une recherche :
  
1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier. ps1 ; par exemple, `CloneSearch.ps1` .
    
  ```powershell
  # This PowerShell script clones an existing content search in the Security &amp; Compliance Center.
  # Get login credentials from the user
  if(!$UserCredential)
  {
      $UserCredential = Get-Credential
      $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
      if (!$Session)
      {
          Write-Error "Couldn't create a remote PowerShell session."
          return
      }
      Import-PSSession $Session -AllowClobber -DisableNameChecking
      $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Security & Compliance Center)"
  }
  # Ask for the name of the search you want to clone
  $searchName = Read-Host 'Enter the name of the search that you want to clone'
  # Ask for the name of the new search
  $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
  $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
  # Make sure we have a valid search before continuing
  if(!$originalSearch)
  {
      Write-Error "Couldn't find search: $searchName"
      return
  }
  $searchNameCounter = 1
  # Find a suitable name for the new search
  while(!$newSearchName)
  {
      $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
      $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
      if ($tempSearch)
      {
          $newSearchName = $null
          $searchNameCounter++
      }
  }
  $caseName
  # Determine if the search is part of a case; if so get the case name
  if ($originalSearch.CaseId)
  {
      $searchCase = Get-ComplianceCase $originalSearch.CaseId
      $caseName = $searchCase.Name
  }
  # Need to cast this value as a Boolean the old fashion way
  $allowNotFoundExchangeLocationsEnabled = $false
  if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
  {
      $allowNotFoundExchangeLocationsEnabled = $true
  }
  $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
  if ($newSearch)
  {
      Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
  }
  ```

2. Ouvrez Windows PowerShell et accédez au dossier où vous avez enregistré le script.
    
3. Exécutez le script ; par exemple :
    
    ```powershell
    .\CloneSearch.ps1
    ```

4. Lorsque vous êtes invité à entrer vos informations d’identification, entrez votre adresse de messagerie et votre mot de passe, puis cliquez sur **OK**.
    
5. Entrez les informations suivantes lorsque le script vous y invite. Tapez chaque information, puis appuyez sur **entrée**.
    
    - Nom de la recherche existante.
    
    - Nom de la nouvelle recherche.
    
    Le script crée la recherche de contenu, mais ne le démarre pas. Cela vous permet de modifier et d’exécuter la recherche à l’étape suivante. Vous pouvez afficher les propriétés de la nouvelle recherche en exécutant la cmdlet **Get-ComplianceSearch** ou en accédant à la page **recherche de contenu** ou **découverte électronique** dans le centre de conformité, selon que la nouvelle recherche est associée ou non à un cas. 
  
## <a name="step-2-edit-and-run-the-cloned-search-in-the-compliance-center"></a>Étape 2 : modifier et exécuter la recherche clonée dans le centre de conformité

Une fois que vous avez exécuté le script pour cloner une recherche de contenu existante, l’étape suivante consiste à accéder au centre de conformité pour modifier et exécuter la nouvelle recherche. Comme indiqué précédemment, vous pouvez modifier une recherche en modifiant la requête de recherche par mot clé et en ajoutant ou supprimant des conditions de recherche. Pour plus d’informations, reportez-vous aux rubriques suivantes :
  
- [Recherche de contenu dans Office 365](content-search.md)
    
- [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)
    
- [cas eDiscovery](ediscovery-cases.md)
