---
title: Utiliser un script pour ajouter des utilisateurs à une conservation dans un cas core eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: bad352ff-d5d2-45d8-ac2a-6cb832f10e73
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Découvrez comment exécuter un script pour ajouter des boîtes aux lettres & OneDrive Entreprise sites à une nouvelle conservation associée à un cas eDiscovery dans le Centre de conformité Microsoft 365.
ms.openlocfilehash: a678649ebd15a34bdfe5765449d41feae1b14901
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761238"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>Utiliser un script pour ajouter des utilisateurs à une conservation dans un cas core eDiscovery

Le Centre de sécurité & conformité PowerShell fournit des applets de commande qui vous permettent d’automatiser les tâches fastidieuses liées à la création et à la gestion des cas eDiscovery. Actuellement, l’utilisation du cas core eDiscovery dans le Centre de conformité Microsoft 365 pour mettre en attente un grand nombre d’emplacements de contenu de consignation prend du temps et de la préparation. Par exemple, avant de créer une conservation, vous devez collecter l’URL de chaque site OneDrive Entreprise que vous souhaitez mettre en attente. Ensuite, pour chaque utilisateur que vous souhaitez mettre en attente, vous devez ajouter sa boîte aux lettres et son site OneDrive Entreprise à la conservation. Vous pouvez utiliser le script de cet article pour automatiser ce processus.
  
Le script vous invite à entrer le nom du domaine Mon site de votre organisation (par exemple, `contoso` dans l’URL https://contoso-my.sharepoint.com), le nom d’un cas eDiscovery existant, le nom de la nouvelle conservation associée au cas, une liste d’adresses e-mail des utilisateurs que vous souhaitez mettre en attente et une requête de recherche à utiliser si vous souhaitez créer une conservation basée sur une requête. Le script obtient ensuite l’URL du site OneDrive Entreprise pour chaque utilisateur de la liste, crée la nouvelle conservation, puis ajoute la boîte aux lettres et OneDrive Entreprise site pour chaque utilisateur de la liste à la conservation. Le script génère également des fichiers journaux qui contiennent des informations sur la nouvelle conservation.
  
Voici les étapes à suivre pour y parvenir :
  
[Étape 1 : installer SharePoint Online Management Shell](#step-1-install-the-sharepoint-online-management-shell)
  
[Étape 2 : Générer une liste d’utilisateurs](#step-2-generate-a-list-of-users)
  
[Étape 3 : Exécuter le script pour créer une conservation et ajouter des utilisateurs](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>Avant d’ajouter des utilisateurs à une conservation

- Vous devez être membre du groupe de rôles eDiscovery Manager dans le Centre de conformité Microsoft 365 et administrateur SharePoint Online pour exécuter le script à l’étape 3. Pour plus d’informations, consultez [Attribuer des autorisations eDiscovery dans le Centre de sécurité & conformité Office 365](assign-ediscovery-permissions.md).

- Un maximum de 1 000 boîtes aux lettres et 100 sites peuvent être ajoutés à une conservation associée à un cas eDiscovery dans le Centre de conformité Microsoft 365. En supposant que chaque utilisateur que vous souhaitez mettre en attente dispose d’un site OneDrive Entreprise, vous pouvez ajouter un maximum de 100 utilisateurs à une conservation à l’aide du script de cet article.

- Veillez à enregistrer la liste des utilisateurs que vous créez à l’étape 2 et le script de l’étape 3 dans le même dossier. Cela facilite l’exécution du script.

- Le script ajoute la liste des utilisateurs à une nouvelle conservation associée à un cas existant. Assurez-vous que le cas auquel vous souhaitez associer la conservation est créé avant d’exécuter le script.

- Le script de cet article prend en charge l’authentification moderne lors de la connexion à Security & Compliance Center PowerShell et SharePoint Online Management Shell. Vous pouvez utiliser le script tel qu’il est si vous êtes un Microsoft 365 ou une organisation Microsoft 365 Cloud de la communauté du secteur public. Si vous êtes une organisation Office 365 Allemagne, une organisation Microsoft 365 Cloud de la communauté du secteur public High ou une organisation DoD Microsoft 365, vous devrez modifier le script pour l’exécuter correctement. Plus précisément, vous devez modifier la ligne `Connect-IPPSSession` et utiliser les paramètres *ConnectionUri* et *AzureADAuthorizationEndpointUri* (et les valeurs appropriées pour votre type d’organisation) pour vous connecter à Security & Compliance Center PowerShell. Pour plus d’informations, consultez les exemples de [Connecter à Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Le script se déconnecte automatiquement de Security & Compliance Center PowerShell et SharePoint Online Management Shell.

- Le script inclut une gestion minimale des erreurs. Son objectif principal est de mettre rapidement et facilement la boîte aux lettres et OneDrive Entreprise site de chaque utilisateur en attente.

- Les exemples de script fournis dans cette rubrique ne sont pris en charge dans aucun programme de support ou service standard de Microsoft. Les exemples de scripts sont fournis en l’état, sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. Vous assumez tous les risques liés à l’utilisation ou à l’exécution des exemples de scripts et de la documentation. En aucun cas, Microsoft, ses auteurs ou toute personne impliquée dans la création, la production ou la livraison des scripts ne sont responsables de dommages quelconques (y compris, sans limitation, pertes de bénéfices, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>Étape 1 : installer SharePoint Online Management Shell

La première étape consiste à installer le SharePoint Online Management Shell s’il n’est pas déjà installé sur votre ordinateur local. Vous n’avez pas besoin d’utiliser l’interpréteur de commandes dans cette procédure, mais vous devez l’installer, car il contient les prérequis requis par le script que vous exécutez à l’étape 3. Ces conditions préalables permettent au script de communiquer avec SharePoint Online pour obtenir les URL des sites OneDrive Entreprise.
  
Accédez à [configurer l’environnement SharePoint Online Management Shell Windows PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) et effectuez les étapes 1 et 2 pour installer le SharePoint Online Management Shell sur votre ordinateur local.

## <a name="step-2-generate-a-list-of-users"></a>Étape 2 : Générer une liste d’utilisateurs

Le script de l’étape 3 crée une conservation associée à un cas eDiscovery, et l’ajout des boîtes aux lettres et des sites OneDrive Entreprise d’une liste d’utilisateurs à la conservation. Vous pouvez simplement taper les adresses e-mail dans un fichier texte, ou exécuter une commande dans Windows PowerShell pour obtenir une liste d’adresses e-mail et les enregistrer dans un fichier (situé dans le même dossier que celui dans lequel vous allez enregistrer le script à l’étape 3).
  
Voici une commande PowerShell (que vous exécutez à l’aide de PowerShell distant connecté à votre organisation Exchange Online) pour obtenir une liste d’adresses e-mail pour tous les utilisateurs de votre organisation et l’enregistrer dans un fichier texte nommé HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

Après avoir exécuté cette commande, ouvrez le fichier texte et supprimez l’en-tête qui contient le nom de la propriété. `PrimarySmtpAddress` Supprimez ensuite toutes les adresses e-mail, à l’exception de celles des utilisateurs que vous souhaitez ajouter à la conservation que vous allez créer à l’étape 3. Assurez-vous qu’il n’y a pas de lignes vides avant ou après la liste des adresses e-mail.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>Étape 3 : Exécuter le script pour créer une conservation et ajouter des utilisateurs

Lorsque vous exécutez le script dans cette étape, il vous invite à fournir les informations suivantes. Veillez à disposer de ces informations avant d’exécuter le script.
  
- **Vos informations d’identification d’utilisateur :** Le script utilise vos informations d’identification pour se connecter au Centre de sécurité & conformité avec PowerShell. Il utilisera également ces informations d’identification pour accéder à SharePoint Online afin d’obtenir les URL OneDrive Entreprise pour la liste des utilisateurs.

- **Nom de votre domaine SharePoint :** le script vous invite à entrer ce nom pour qu’il puisse se connecter au <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">centre d’administration SharePoint</a>. Il utilise également le nom de domaine pour les URL OneDrive de votre organisation. Par exemple, si l’URL de votre centre d’administration est `https://contoso-admin.sharepoint.com` et que l’URL de OneDrive est`https://contoso-my.sharepoint.com`, vous devez entrer `contoso` lorsque le script vous demande votre nom de domaine.

- **Nom du cas :** Nom d’un cas existant. Le script crée une conservation associée à ce cas.

- **Nom de la conservation :** Nom de la conservation que le script crée et associe au cas spécifié.

- **Recherchez une requête pour une conservation basée sur une requête :** Vous pouvez créer une conservation basée sur une requête afin que seul le contenu qui répond aux critères de recherche spécifiés soit mis en attente. Pour mettre tout le contenu en attente, appuyez simplement sur **Entrée** lorsque vous êtes invité à effectuer une requête de recherche.

- **Activation ou non de la conservation :** Le script peut être activé après sa création ou le script peut créer la conservation sans l’activer. Si le script n’est pas activé, vous pouvez l’activer ultérieurement dans le Centre de conformité Microsoft 365 ou en exécutant les commandes PowerShell suivantes :

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **Nom du fichier texte avec la liste des utilisateurs** : nom du fichier texte de l’étape 2 qui contient la liste des utilisateurs à ajouter à la conservation. Si ce fichier se trouve dans le même dossier que le script, tapez simplement le nom du fichier (par exemple, HoldUsers.txt). Si le fichier texte se trouve dans un autre dossier, tapez le chemin d’accès complet du fichier.

Une fois que vous avez collecté les informations que le script vous invitera, la dernière étape consiste à exécuter le script pour créer la nouvelle conservation et y ajouter des utilisateurs.
  
1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier .`.ps1` Par exemple : `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   Core eDiscovery cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
write-host "***********************************************"
" "
# Connect to SCC PowerShell using modern authentication
if (!$SccSession)
{
  Import-Module ExchangeOnlineManagement
  Connect-IPPSSession
}

# Get the organization's domain name. We use this to create the SharePoint admin URL and root URL for OneDrive for Business.
""
$mySiteDomain = Read-Host "Enter the domain name for your SharePoint organization. We use this name to connect to SharePoint admin center and for the OneDrive URLs in your organization. For example, 'contoso' in 'https://contoso-admin.sharepoint.com' and 'https://contoso-my.sharepoint.com'"
""

# Connect to PnP Online using modern authentication
Import-Module PnP.PowerShell
Connect-PnPOnline -Url https://$mySiteDomain-admin.sharepoint.com -UseWebLogin

# Load the SharePoint assemblies from the SharePoint Online Management Shell
# To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
{
    $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
    $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
    $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
    if (!$SharePointClient)
    {
        Write-Error "The SharePoint Online Management Shell isn't installed. Please install it from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then re-run this script."
        return;
    }
}

# Get other required information
do{
$casename = Read-Host "Enter the name of the case"
$caseexists = (get-compliancecase -identity "$casename" -erroraction SilentlyContinue).isvalid
if($caseexists -ne 'True')
{""
write-host "A case named '$casename' doesn't exist. Please specify the name of an existing case, or create a new case and then re-run the script." -foregroundColor Yellow
""}
}While($caseexists -ne 'True')
""
do{
$holdName = Read-Host "Enter the name of the new hold"
$holdexists=(get-caseholdpolicy -identity "$holdname" -case "$casename" -erroraction SilentlyContinue).isvalid
if($holdexists -eq 'True')
{""
write-host "A hold named '$holdname' already exists. Please specify a new hold name." -foregroundColor Yellow
""}
}While($holdexists -eq 'True')
""
$holdQuery = Read-Host "Enter a search query to create a query-based hold, or press Enter to hold all content"
""
$holdstatus = read-host "Do you want the hold enabled after it's created? (Yes/No)"
do{
""
$inputfile = read-host "Enter the name of the text file that contains the email addresses of the users to add to the hold"
""
$fileexists = test-path -path $inputfile
if($fileexists -ne 'True'){write-host "$inputfile doesn't exist. Please enter a valid file name." -foregroundcolor Yellow}
}while($fileexists -ne 'True')
#Import the list of addresses from the txt file.  Trim any excess spaces and make sure all addresses 
    #in the list are unique.
  [array]$emailAddresses = Get-Content $inputfile -ErrorAction SilentlyContinue | where {$_.trim() -ne ""}  | foreach{ $_.Trim() }
  [int]$dupl = $emailAddresses.count
  [array]$emailAddresses = $emailAddresses | select-object -unique
  $dupl -= $emailAddresses.count
#Validate email addresses so the hold creation does not run in to an error.
if($emailaddresses.count -gt 0){
write-host ($emailAddresses).count "addresses were found in the text file. There were $dupl duplicate entries in the file." -foregroundColor Yellow
""
Write-host "Validating the email addresses. Please wait..." -foregroundColor Yellow
""
$finallist =@()
foreach($emailAddress in $emailAddresses)
{
if((get-recipient $emailaddress -erroraction SilentlyContinue).isvalid -eq 'True')
{$finallist += $emailaddress}
else {"Unable to find the user $emailaddress"
[array]$excludedlist += $emailaddress}
}
""
#Find user's OneDrive account URL using email address
Write-Host "Getting the URL for each user's OneDrive for Business site." -foregroundColor Yellow 
""
$AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
$mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
$urls = @()
foreach($emailAddress in $finallist)
{
try
{
$url=Get-PnPUserProfileProperty -Account $emailAddress | Select PersonalUrl
$urls += $url.PersonalUrl
       Write-Host "- $emailAddress => $url"
       [array]$ODadded += $url.PersonalUrl
       }catch { 
 Write-Warning "Could not locate OneDrive for $emailAddress"
 [array]$ODExluded += $emailAddress
 Continue }
}
$urls | FL
if(($finallist.count -gt 0) -or ($urls.count -gt 0)){
""
Write-Host "Creating the hold named $holdname. Please wait..." -foregroundColor Yellow
if(($holdstatus -eq "Y") -or ($holdstatus -eq  "y") -or ($holdstatus -eq "yes") -or ($holdstatus -eq "YES")){
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $True | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery | out-null
}
else{
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $false | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery -disabled $false | out-null
}
""
}
else {"No valid locations were identified. Therefore, the hold wasn't created."}
#write log files (if needed)
$newhold=Get-CaseHoldPolicy -Identity "$holdname" -Case "$casename" -erroraction SilentlyContinue
$newholdrule=Get-CaseHoldRule -Identity "$holdName" -erroraction SilentlyContinue
if(($ODAdded.count -gt 0) -or ($ODExluded.count -gt 0) -or ($finallist.count -gt 0) -or ($excludedlist.count -gt 0) -or ($newhold.isvalid -eq 'True') -or ($newholdrule.isvalid -eq 'True'))
{
Write-Host "Generating output files..." -foregroundColor Yellow
if($ODAdded.count -gt 0){
"OneDrive Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.SharePointLocation.name | add-content .\LocationsOnHold.txt}
if($ODExluded.count -gt 0){ 
"Users without OneDrive locations" | add-content .\LocationsNotOnHold.txt
"================================" | add-content .\LocationsNotOnHold.txt
$ODExluded | add-content .\LocationsNotOnHold.txt}
if($finallist.count -gt 0){
" " | add-content .\LocationsOnHold.txt
"Exchange Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.ExchangeLocation.name | add-content .\LocationsOnHold.txt}
if($excludedlist.count -gt 0){
" "| add-content .\LocationsNotOnHold.txt
"Mailboxes not added to the hold" | add-content .\LocationsNotOnHold.txt
"===============================" | add-content .\LocationsNotOnHold.txt
$excludedlist | add-content .\LocationsNotOnHold.txt}
$FormatEnumerationLimit=-1
if($newhold.isvalid -eq 'True'){$newhold|fl >.\GetCaseHoldPolicy.txt}
if($newholdrule.isvalid -eq 'True'){$newholdrule|Fl >.\GetCaseHoldRule.txt}
}
}
else {"The hold wasn't created because no valid entries were found in the text file."}
""
#Disconnect from SCC PowerShell and PnPOnline

Write-host "Disconnecting from SCC PowerShell and PnP Online" -foregroundColor Yellow
Get-PSSession | Remove-PSSession
Disconnect-PnPOnline

Write-host "Script complete!" -foregroundColor Yellow
""
#script end
```

2. Sur votre ordinateur local, ouvrez Windows PowerShell et accédez au dossier où vous avez enregistré le script.

3. Exécutez le script ; par exemple :

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. Entrez les informations que le script vous invite à entrer.

   Le script se connecte à Security & Compliance Center PowerShell, puis crée la nouvelle conservation dans le cas eDiscovery et ajoute les boîtes aux lettres et les OneDrive Entreprise pour les utilisateurs dans la liste. Vous pouvez accéder au cas sur la page **eDiscovery** dans le Centre de conformité Microsoft 365 pour afficher la nouvelle conservation.

Une fois l’exécution du script terminée, il crée les fichiers journaux suivants et les enregistre dans le dossier où se trouve le script.
  
- **LocationsOnHold.txt :** Contient la liste des boîtes aux lettres et des sites OneDrive Entreprise que le script a correctement mis en attente.

- **LocationsNotOnHold.txt :** Contient une liste de boîtes aux lettres et de sites OneDrive Entreprise que le script n’a pas mis en attente. Si un utilisateur a une boîte aux lettres, mais pas un site OneDrive Entreprise, il est inclus dans la liste des sites OneDrive Entreprise qui n’ont pas été mis en attente.

- **GetCaseHoldPolicy.txt :** Contient la sortie de l’applet de commande **Get-CaseHoldPolicy** pour la nouvelle conservation, que le script a exécutée après la création de la nouvelle conservation. Les informations retournées par cette applet de commande incluent une liste d’utilisateurs dont les boîtes aux lettres et les sites OneDrive Entreprise ont été mis en attente et si la conservation est activée ou désactivée. 

- **GetCaseHoldRule.txt :** Contient la sortie de l’applet de commande **Get-CaseHoldRule** pour la nouvelle conservation, que le script a exécutée après la création de la nouvelle conservation. Les informations retournées par cette applet de commande incluent la requête de recherche si vous avez utilisé le script pour créer une conservation basée sur une requête.
