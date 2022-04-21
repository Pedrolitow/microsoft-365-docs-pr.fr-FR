---
title: Utiliser la recherche de contenu pour une liste d’utilisateurs sur la boîte aux lettres & OneDrive Entreprise site
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/3/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 5f4f8206-2d6a-4cb2-bbc6-7a0698703cc0
description: Utilisez la recherche de contenu et le script de cet article pour rechercher un groupe d’utilisateurs dans les boîtes aux lettres et les sites OneDrive Entreprise.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1bbfc26c2193c1bf31e081b8ded9e2e2baf56743
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998813"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>Utiliser la recherche de contenu pour rechercher une liste d’utilisateurs dans la boîte aux lettres et OneDrive Entreprise

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Security & Compliance Center PowerShell fournit un certain nombre d’applets de commande qui vous permettent d’automatiser des tâches liées à eDiscovery qui prennent beaucoup de temps. Actuellement, la création d’une recherche de contenu dans le portail de conformité Microsoft Purview pour effectuer une recherche dans un grand nombre d’emplacements de contenu de consignation prend du temps et de la préparation. Avant de créer une recherche, vous devez collecter l’URL de chaque site OneDrive Entreprise, puis ajouter chaque boîte aux lettres et OneDrive Entreprise site à la recherche. Dans les versions ultérieures, cela sera plus facile à faire dans le portail de conformité. En attendant, vous pouvez utiliser le script de cet article pour automatiser ce processus. Ce script vous invite à entrer le nom du domaine MySite de votre organisation (par exemple, **contoso** dans l’URL `https://contoso-my.sharepoint.com`), une liste d’adresses e-mail utilisateur, le nom de la nouvelle recherche de contenu et la requête de recherche à utiliser. Le script obtient l’URL OneDrive Entreprise pour chaque utilisateur de la liste, puis il crée et démarre une recherche de contenu qui recherche dans la boîte aux lettres et OneDrive Entreprise site pour chaque utilisateur de la liste, à l’aide de la requête de recherche que vous fournissez.
  
## <a name="permissions-and-script-information"></a>Autorisations et informations de script

- Vous devez être membre du groupe de rôles eDiscovery Manager dans le portail de conformité et un administrateur général SharePoint Online pour exécuter le script à l’étape 3.

- Veillez à enregistrer la liste des utilisateurs que vous créez à l’étape 2 et le script de l’étape 3 dans le même dossier. Cela facilite l’exécution du script.

- Le script inclut une gestion minimale des erreurs. Son objectif principal est de rechercher rapidement et facilement la boîte aux lettres et OneDrive Entreprise site de chaque utilisateur.

- Les exemples de script fournis dans cette rubrique ne sont pris en charge dans aucun programme de support ou service standard de Microsoft. Les exemples de scripts sont fournis en l’état, sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. Vous assumez tous les risques liés à l’utilisation ou à l’exécution des exemples de scripts et de la documentation. En aucun cas, Microsoft, ses auteurs ou toute personne impliquée dans la création, la production ou la livraison des scripts ne sont responsables de dommages quelconques (y compris, sans limitation, pertes de bénéfices, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Étape 1 : installer SharePoint Online Management Shell

La première étape consiste à installer le SharePoint Online Management Shell. Vous n’avez pas besoin d’utiliser l’interpréteur de commandes dans cette procédure, mais vous devez l’installer, car il contient les prérequis requis par le script que vous exécutez à l’étape 3. Ces conditions préalables permettent au script de communiquer avec SharePoint Online pour obtenir les URL des sites OneDrive Entreprise.
  
Accédez à [configurer l’environnement Windows PowerShell Windows PowerShell de l’interpréteur de commandes de gestion en ligne SharePoint](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) et effectuez les étapes 1 et 2 pour installer le SharePoint Online Management Shell.
  
## <a name="step-2-generate-a-list-of-users"></a>Étape 2 : Générer une liste d’utilisateurs

Le script de l’étape 3 crée une recherche de contenu pour rechercher une liste d’utilisateurs dans les boîtes aux lettres et OneDrive comptes. Vous pouvez simplement taper les adresses e-mail dans un fichier texte, ou exécuter une commande dans Windows PowerShell pour obtenir une liste d’adresses e-mail et les enregistrer dans un fichier (situé dans le même dossier que celui dans lequel vous allez enregistrer le script à l’étape 3).
  
Voici une [commande PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) que vous pouvez exécuter pour obtenir une liste d’adresses e-mail pour tous les utilisateurs de votre organisation et l’enregistrer dans un fichier texte nommé `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

Après avoir exécuté cette commande, veillez à ouvrir le fichier et à supprimer l’en-tête qui contient le nom de la propriété. `PrimarySmtpAddress` Le fichier texte doit simplement contenir une liste d’adresses e-mail et rien d’autre. Assurez-vous qu’il n’y a pas de lignes vides avant ou après la liste des adresses e-mail.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>Étape 3 : Exécuter le script pour créer et démarrer la recherche

Lorsque vous exécutez le script dans cette étape, il vous invite à fournir les informations suivantes. Veillez à disposer de ces informations avant d’exécuter le script.
  
- **Vos informations d’identification utilisateur** : le script utilise vos informations d’identification pour accéder à SharePoint Online afin d’obtenir les URL OneDrive Entreprise et de se connecter au Centre de sécurité & conformité PowerShell. 
    
- **Nom de votre domaine MySite** : le domaine MySite est le domaine qui contient tous les sites OneDrive Entreprise de votre organisation. Par exemple, si l’URL de votre domaine MySite est **https://contoso-my.sharepoint.com**, vous devez entrer  `contoso` lorsque le script vous demande le nom de votre domaine MySite. 
    
- **Nom du chemin d’accès du fichier texte de l’étape 2** : nom du chemin d’accès du fichier texte que vous avez créé à l’étape 2. Si le fichier texte et le script se trouvent dans le même dossier, entrez le nom du fichier texte. Sinon, entrez le nom de chemin complet du fichier texte. 
    
- **Nom de la recherche de contenu** : nom de la recherche de contenu qui sera créée par le script. 
    
- **Requête de** recherche : la requête de recherche qui sera utilisée avec la recherche de contenu est créée et exécutée. Pour plus d’informations sur les requêtes de recherche, consultez [les requêtes de mot clé et les conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).


**Pour exécuter le script :**
    
1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de .ps1 ; par exemple, `SearchEXOOD4B.ps1`. Enregistrez le fichier dans le dossier où vous avez enregistré la liste des utilisateurs à l’étape 2.
    
  ```powershell
  # This PowerShell script will prompt you for the following information:
  #    * Your user credentials 
  #    * The name of your organization's MySite domain                                              
  #    * The pathname for the text file that contains a list of user email addresses
  #    * The name of the Content Search that will be created
  #    * The search query string
  # The script will then:
  #    * Find the OneDrive for Business site for each user in the text file
  #    * Create and start a Content Search using the above information
  # Get user credentials
  if (!$credentials)
  {
      $credentials = Get-Credential
  }
  # Get the user's MySite domain name.  We use this to create the admin URL and root URL for OneDrive for Business
  $mySiteDomain = Read-Host "What is your organization's MySite domain?  For example,  'contoso' for 'https://contoso-my.sharepoint.com'"
  $AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
  $mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
  # Get other required information
  $inputfile = read-host "Enter the file name of the text file that contains the email addresses for the users you want to search"
  $searchName = Read-Host "Enter the name for the new search"
  $searchQuery = Read-Host "Enter the search query you want to use"
  $emailAddresses = Get-Content $inputfile | where {$_ -ne ""}  | foreach{ $_.Trim() }
  # Connect to Security & Compliance Center PowerShell
  if (!$s -or !$a)
  {
      Import-Module ExchangeOnlineManagement
      Connect-IPPSSession
  }
  
  # Load the SharePoint assemblies from the SharePoint Online Management Shell
  # To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
  if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
  {
      $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
      $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
      $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
      if (!$SharePointClient)
      {
          Write-Error "SharePoint Online Management Shell isn't installed, please install from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then run this script again"
          return;
      }
  }
  if (!$spCreds)
  {
      $spCreds = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($credentials.UserName, $credentials.Password)
  }
  # Add the path of the User Profile Service to the SPO admin URL, then create a new webservice proxy to access it
  $proxyaddr = "$AdminUrl/_vti_bin/UserProfileService.asmx?wsdl"
  $UserProfileService= New-WebServiceProxy -Uri $proxyaddr -UseDefaultCredential False
  $UserProfileService.Credentials = $credentials
  # Take care of auth cookies
  $strAuthCookie = $spCreds.GetAuthenticationCookie($AdminUrl)
  $uri = New-Object System.Uri($AdminUrl)
  $container = New-Object System.Net.CookieContainer
  $container.SetCookies($uri, $strAuthCookie)
  $UserProfileService.CookieContainer = $container
  Write-Host "Getting each user's OneDrive for Business URL"
  $urls = @()
  foreach($emailAddress in $emailAddresses)
  {
      try
      {
          $prop = $UserProfileService.GetUserProfileByName("i:0#.f|membership|$emailAddress") | Where-Object { $_.Name -eq "PersonalSpace" } 
          $url = $prop.values[0].value
          $furl = $mySiteUrlRoot + $url
          $urls += $furl
          Write-Host "-$emailAddress => $furl"
      }
      catch
      {
          Write-Warning "Could not locate OneDrive for $emailAddress"
      }
  }
  Write-Host "Creating and starting the search"
  $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $emailAddresses -SharePointLocation $urls -ContentMatchQuery $searchQuery
  # Finally, start the search and then display the status
  if($search)
  {
      Start-ComplianceSearch $search.Name
      Get-ComplianceSearch $search.Name
  }
  
  ```

2. Ouvrez Windows PowerShell et accédez au dossier dans lequel vous avez enregistré le script et la liste des utilisateurs de l’étape 2.
    
3. Démarrez le script ; par exemple :
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. Lorsque vous êtes invité à entrer vos informations d’identification, entrez votre adresse e-mail et votre mot de passe, puis cliquez sur **OK**. 
    
5. Entrez les informations suivantes lorsque vous y êtes invité par le script. Tapez chaque information, puis **appuyez sur Entrée**.
    
    - Nom de votre domaine MySite. 
    
    - Chemin d’accès du fichier texte qui contient la liste des utilisateurs.
    
    - Nom de la recherche de contenu.
    
    - Requête de recherche (laissez cette valeur vide pour renvoyer tous les éléments dans les emplacements de contenu).
    
    Le script obtient les URL de chaque site OneDrive Entreprise, puis crée et démarre la recherche. Vous pouvez exécuter l’applet de commande **Get-ComplianceSearch** dans Security & Compliance Center PowerShell pour afficher les statistiques et les résultats de recherche, ou vous pouvez accéder à la page **Recherche de contenu** dans le portail de conformité pour afficher des informations sur la recherche.
