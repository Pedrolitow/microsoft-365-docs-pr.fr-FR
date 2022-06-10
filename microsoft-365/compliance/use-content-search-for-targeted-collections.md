---
title: Utiliser la recherche de contenu pour les collections ciblées
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
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
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Utilisez la recherche de contenu dans le portail de conformité Microsoft Purview pour effectuer une collection ciblée, qui recherche des éléments dans une boîte aux lettres ou un dossier de site spécifique.
ms.openlocfilehash: 224da8e651599d1d007684a069b0dbb9d30a6119
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015537"
---
# <a name="use-content-search-for-targeted-collections"></a>Utiliser la recherche de contenu pour les collections ciblées

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

L’outil de recherche de contenu dans le portail de conformité Microsoft Purview ne fournit pas de moyen direct dans l’interface utilisateur de rechercher des dossiers spécifiques dans Exchange boîtes aux lettres ou SharePoint et OneDrive Entreprise sites. Toutefois, il est possible de rechercher des dossiers spécifiques ( *appelés regroupements ciblés*) en spécifiant la propriété d’ID de dossier pour la propriété e-mail ou chemin d’accès (DocumentLink) pour les sites dans la syntaxe de requête de recherche réelle. L’utilisation de la recherche de contenu pour effectuer une collection ciblée est utile lorsque vous êtes certain que les éléments sensibles à un cas ou à des éléments privilégiés se trouvent dans une boîte aux lettres ou un dossier de site spécifique. Vous pouvez utiliser le script de cet article pour obtenir l’ID de dossier des dossiers de boîte aux lettres ou le chemin d’accès (DocumentLink) pour les dossiers d’un SharePoint et d’un site OneDrive Entreprise. Vous pouvez ensuite utiliser l’ID de dossier ou le chemin d’accès dans une requête de recherche pour renvoyer les éléments situés dans le dossier.

> [!NOTE]
> Pour renvoyer du contenu situé dans un dossier d’un SharePoint ou d’un site OneDrive Entreprise, le script de cette rubrique utilise la propriété gérée DocumentLink au lieu de la propriété Path. La propriété DocumentLink est plus robuste que la propriété Path, car elle retourne tout le contenu d’un dossier, tandis que la propriété Path ne retourne pas certains fichiers multimédias.

## <a name="before-you-run-a-targeted-collection"></a>Avant d’exécuter une collection ciblée

- Vous devez être membre du groupe de rôles gestionnaire eDiscovery dans le portail de conformité pour exécuter le script à l’étape 1. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- Vous devez également disposer du rôle Destinataires du courrier dans votre organisation Exchange Online. Cela est nécessaire pour exécuter l’applet de commande **Get-MailboxFolderStatistics** , qui est incluse dans le script. Par défaut, le rôle Destinataires du courrier est attribué aux groupes de rôles Gestion de l’organisation et Gestion des destinataires dans Exchange Online. Pour plus d’informations sur l’attribution d’autorisations dans Exchange Online, consultez [Gérer les membres du groupe de rôles](/exchange/manage-role-group-members-exchange-2013-help). Vous pouvez également créer un groupe de rôles personnalisé, lui attribuer le rôle Destinataires du courrier, puis ajouter les membres qui doivent exécuter le script à l’étape 1. Pour plus d'informations, consultez la rubrique [Gérer des groupes de rôles](/Exchange/permissions-exo/role-groups).

- Le script de cet article prend en charge l’authentification moderne. Vous pouvez utiliser le script tel qu’il est si vous êtes un Microsoft 365 ou une organisation Microsoft 365 Cloud de la communauté du secteur public. Si vous êtes une organisation Office 365 Allemagne, une organisation Microsoft 365 Cloud de la communauté du secteur public High ou une organisation DoD Microsoft 365, vous devrez modifier le script pour l’exécuter correctement. Plus précisément, vous devez modifier la ligne `Connect-ExchangeOnline` et utiliser le paramètre *ExchangeEnvironmentName* (et la valeur appropriée pour votre type d’organisation) pour vous connecter à Exchange Online PowerShell.  En outre, vous devez modifier la ligne `Connect-IPPSSession` et utiliser les paramètres *ConnectionUri* et *AzureADAuthorizationEndpointUri* (et les valeurs appropriées pour votre type d’organisation) pour vous connecter à Security & Compliance PowerShell. Pour plus d’informations, consultez les exemples de [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) et [Connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Chaque fois que vous exécutez le script, une nouvelle session PowerShell distante est créée. Cela signifie que vous pouvez utiliser toutes les sessions PowerShell distantes disponibles. Pour éviter cela, exécutez les commandes suivantes pour déconnecter vos sessions PowerShell distantes actives.

  ```powershell
  Get-PSSession | Remove-PSSession; Disconnect-ExchangeOnline
  ```

    Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

- Le script inclut une gestion minimale des erreurs. L’objectif principal du script est d’afficher rapidement une liste d’ID de dossier de boîte aux lettres ou de chemins d’accès de site qui peuvent être utilisés dans la syntaxe de requête de recherche d’une recherche de contenu pour effectuer une collection ciblée.

- L’exemple de script fourni dans cette rubrique n’est pris en charge par aucun service ou programme de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Étape 1 : Exécuter le script pour obtenir la liste des dossiers d’une boîte aux lettres ou d’un site

Le script que vous exécutez dans cette première étape retourne une liste de dossiers de boîte aux lettres ou SharePoint et OneDrive Entreprise dossiers, ainsi que l’ID de dossier ou le chemin correspondant pour chaque dossier. Lorsque vous exécutez ce script, il vous invite à fournir les informations suivantes.

- **Adresse e-mail ou URL du site** : tapez une adresse e-mail du consignateur pour renvoyer une liste de dossiers de boîte aux lettres et d’ID de dossier Exchange. Ou tapez l’URL d’un site SharePoint ou d’un site OneDrive Entreprise pour retourner une liste de chemins d’accès pour le site spécifié. Voici quelques exemples :

  - **Exchange** :`stacig@contoso.onmicrosoft.com`

  - **SharePoint** :`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive Entreprise** :`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **Vos informations d’identification d’utilisateur** : le script utilise vos informations d’identification pour se connecter à Exchange Online PowerShell ou à Security & Compliance PowerShell à l’aide de l’authentification moderne. Comme expliqué précédemment, vous devez disposer des autorisations appropriées pour exécuter correctement ce script.

Pour afficher la liste des dossiers de boîte aux lettres ou des noms de liens de document de site (chemin d’accès) :

1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de .ps1 ; par exemple, `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the compliance portal.            #
   # The script will then:                                            #
   #    * If an email address is supplied: list the folders for the target mailbox.            #
   #    * If a SharePoint or OneDrive for Business site is supplied: list the documentlinks (folder paths) #
   #    * for the site.                                                                                    #
   #    * In both cases, the script supplies the correct search properties (folderid: or documentlink:)    #
   #      appended to the folder ID or documentlink to use in a Content Search.                #
   # Notes:                                                #
   #    * For SharePoint and OneDrive for Business, the paths are searched recursively; this means the     #
   #      the current folder and all sub-folders are searched.                        #
   #    * For Exchange, only the specified folder will be searched; this means sub-folders in the folder    #
   #      will not be searched.  To search sub-folders, you need to use the specify the folder ID for    #
   #      each sub-folder that you want to search.                                #
   #    * For Exchange, only folders in the user's primary mailbox will be returned by the script.        #
   #########################################################################################################
   # Collect the target email address or SharePoint Url
   $addressOrSite = Read-Host "Enter an email address or a URL for a SharePoint or OneDrive for Business site"
   # Authenticate with Exchange Online and the compliance portal (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline -ShowBanner:$false -CommandName Get-MailboxFolderStatistics
      }
      $folderQueries = @()
      $folderStatistics = Get-MailboxFolderStatistics $emailAddress
      foreach ($folderStatistic in $folderStatistics)
      {
          $folderId = $folderStatistic.FolderId;
          $folderPath = $folderStatistic.FolderPath;
          $encoding= [System.Text.Encoding]::GetEncoding("us-ascii")
          $nibbler= $encoding.GetBytes("0123456789ABCDEF");
          $folderIdBytes = [Convert]::FromBase64String($folderId);
          $indexIdBytes = New-Object byte[] 48;
          $indexIdIdx=0;
          $folderIdBytes | select -skip 23 -First 24 | %{$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -shr 4];$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -band 0xF]}
          $folderQuery = "folderid:$($encoding.GetString($indexIdBytes))";
          $folderStat = New-Object PSObject
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderPath -Value $folderPath
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderQuery -Value $folderQuery
          $folderQueries += $folderStat
      }
      Write-Host "-----Exchange Folders-----"
      $folderQueries |ft
   }
   elseif ($addressOrSite.IndexOf("http") -ige 0)
   {
      $searchName = "SPFoldersSearch"
      $searchActionName = "SPFoldersSearch_Preview"
      # List the folders for the SharePoint or OneDrive for Business Site
      $siteUrl = $addressOrSite
      # Connect to Security & Compliance PowerShell
      if (!$SccSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-IPPSSession
      }
      # Clean-up, if the script was aborted, the search we created might not have been deleted.  Try to do so now.
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
      # Create a Content Search against the SharePoint Site or OneDrive for Business site and only search for folders; wait for the search to complete
      $complianceSearch = New-ComplianceSearch -Name $searchName -ContentMatchQuery "contenttype:folder" -SharePointLocation $siteUrl
      Start-ComplianceSearch $searchName
      do{
          Write-host "Waiting for search to complete..."
          Start-Sleep -s 5
          $complianceSearch = Get-ComplianceSearch $searchName
      }while ($complianceSearch.Status -ne 'Completed')
      if ($complianceSearch.Items -gt 0)
      {
          # Create a Compliance Search Action and wait for it to complete. The folders will be listed in the .Results parameter
          $complianceSearchAction = New-ComplianceSearchAction -SearchName $searchName -Preview
          do
          {
              Write-host "Waiting for search action to complete..."
              Start-Sleep -s 5
              $complianceSearchAction = Get-ComplianceSearchAction $searchActionName
          }while ($complianceSearchAction.Status -ne 'Completed')
          # Get the results and print out the folders
          $results = $complianceSearchAction.Results
          $matches = Select-String "Data Link:.+[,}]" -Input $results -AllMatches
          foreach ($match in $matches.Matches)
          {
              $rawUrl = $match.Value
              $rawUrl = $rawUrl -replace "Data Link: " -replace "," -replace "}"
              Write-Host "DocumentLink:""$rawUrl"""
          }
      }
      else
      {
          Write-Host "No folders were found for $siteUrl"
      }
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
   }
   else
   {
      Write-Error "Couldn't recognize $addressOrSite as an email address or a site URL"
   }
   ```

2. Sur votre ordinateur local, ouvrez Windows PowerShell et accédez au dossier où vous avez enregistré le script.

3. Exécutez le script ; par exemple :

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Entrez les informations que le script vous invite à entrer.

    Le script affiche la liste des dossiers de boîte aux lettres ou des dossiers de site pour l’utilisateur spécifié. Laissez cette fenêtre ouverte pour pouvoir copier un ID de dossier ou un nom de lien de document et le coller dans une requête de recherche à l’étape 2.

    > [!TIP]
    > Au lieu d’afficher une liste de dossiers sur l’écran de l’ordinateur, vous pouvez rediriger la sortie du script vers un fichier texte. Ce fichier est enregistré dans le dossier où se trouve le script. Par exemple, pour rediriger la sortie du script vers un fichier texte, exécutez la commande suivante à l’étape 3 :  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` vous pouvez ensuite copier un ID de dossier ou un lien de document à partir du fichier à utiliser dans une requête de recherche.

### <a name="script-output-for-mailbox-folders"></a>Sortie de script pour les dossiers de boîte aux lettres

Si vous obtenez des ID de dossier de boîte aux lettres, le script se connecte à Exchange Online PowerShell, exécute l’applet de commande **Get-MailboxFolderStatisics**, puis affiche la liste des dossiers de la boîte aux lettres spécifiée. Pour chaque dossier de la boîte aux lettres, le script affiche le nom du dossier dans la colonne **FolderPath** et l’ID de dossier dans la colonne **FolderQuery** . En outre, le script ajoute le préfixe de **folderId** (qui est le nom de la propriété de boîte aux lettres) à l’ID de dossier. Étant donné que la propriété **folderid** est une propriété pouvant faire l’objet d’une recherche, vous allez l’utiliser  `folderid:<folderid>` dans une requête de recherche à l’étape 2 pour rechercher dans ce dossier. 

> [!IMPORTANT]
> Le script de cet article inclut une logique d’encodage qui convertit les valeurs d’ID de dossier de 64 caractères retournées par **Get-MailboxFolderStatistics** au même format de 48 caractères indexé pour la recherche. Si vous exécutez simplement l’applet de commande **Get-MailboxFolderStatistics** dans PowerShell pour obtenir un ID de dossier (au lieu d’exécuter le script dans cet article), une requête de recherche qui utilise cette valeur d’ID de dossier échoue. Vous devez exécuter le script pour obtenir les ID de dossier correctement mis en forme qui peuvent être utilisés dans une recherche de contenu.

Voici un exemple de la sortie retournée par le script pour les dossiers de boîte aux lettres.

![Exemple de la liste des dossiers de boîte aux lettres et des ID de dossier retournés par le script.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

L’exemple de l’étape 2 montre la requête utilisée pour rechercher le sous-dossier Purges dans le dossier Éléments récupérables de l’utilisateur.

### <a name="script-output-for-site-folders"></a>Sortie de script pour les dossiers de site

Si vous obtenez le chemin de la propriété **documentlink** à partir de sites SharePoint ou OneDrive Entreprise, le script se connecte à Security & Compliance PowerShell, crée une recherche de contenu qui recherche des dossiers sur le site, puis affiche une liste des dossiers situés dans le site spécifié. Le script affiche le nom de chaque dossier et ajoute le préfixe de **documentlink** à l’URL du dossier. Étant donné que la propriété **documentlink** est une propriété pouvant faire l’objet d’une recherche, vous allez utiliser `documentlink:<path>` la paire property:value dans une requête de recherche à l’étape 2 pour rechercher ce dossier. Le script affiche un maximum de 100 dossiers de site. S’il existe plus de 100 dossiers de site, les dossiers les plus récents sont affichés.

Voici un exemple de la sortie retournée par le script pour les dossiers de site.

![Exemple de liste de noms de liens de document pour les dossiers de site retournés par le script.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Étape 2 : Utiliser un ID de dossier ou un lien de document pour effectuer une collection ciblée

Une fois que vous avez exécuté le script pour collecter une liste d’ID de dossier ou de liens de document pour un utilisateur spécifique, l’étape suivante consiste à accéder au portail de conformité et à créer une recherche de contenu pour rechercher un dossier spécifique. Vous allez utiliser la  `folderid:<folderid>` paire propriété  `documentlink:<path>` :valeur dans la requête de recherche que vous configurez dans la zone de mot clé Recherche de contenu (ou comme valeur du paramètre  *ContentMatchQuery*  si vous utilisez l’applet de commande **New-ComplianceSearch** ). Vous pouvez combiner la ou `documentlink` la `folderid` propriété avec d’autres paramètres de recherche ou conditions de recherche. Si vous incluez uniquement la ou `documentlink` la `folderid` propriété dans la requête, la recherche retourne tous les éléments situés dans le dossier spécifié.

1. Accédez et <https://compliance.microsoft.com> connectez-vous à l’aide du compte et des informations d’identification que vous avez utilisés pour exécuter le script à l’étape 1.

2. Dans le volet gauche du centre de conformité, cliquez sur **Afficher toutes les** > **recherches de contenu**, puis sur **Nouvelle recherche**.

3. Dans la zone **Mots clés**, collez la ou `documentlink:<path>/*` la `folderid:<folderid>` valeur retournée par le script à l’étape 1.

    Par exemple, la requête de la capture d’écran suivante recherche n’importe quel élément du sous-dossier Purges dans le dossier Éléments récupérables de l’utilisateur (la valeur de la `folderid` propriété du sous-dossier Purges apparaît dans la capture d’écran de l’étape 1) :

    ![Collez le folderid ou le lien de document dans la zone de mot clé de la requête de recherche.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > Les recherches de liens de document nécessitent l’utilisation d’une liste de  `asterisk '/*'`fin.  

4. Sous **Emplacements**, sélectionnez **Emplacements spécifiques** , puis cliquez sur **Modifier**.

5. Effectuez l’une des opérations suivantes, selon que vous effectuez une recherche dans un dossier de boîte aux lettres ou un dossier de site :

    - En regard **de Exchange courrier électronique**, cliquez sur **Choisir des utilisateurs, des groupes ou des équipes,** puis ajoutez la même boîte aux lettres que celle que vous avez spécifiée lorsque vous avez exécuté le script à l’étape 1.

      Ou

    - En regard **de SharePoint sites**, cliquez sur **Choisir des sites**, puis ajoutez la même URL de site que celle que vous avez spécifiée lorsque vous avez exécuté le script à l’étape 1.

6. Après avoir enregistré l’emplacement de contenu à rechercher, cliquez sur **Enregistrer & exécuter**, tapez un nom pour la recherche de contenu, puis cliquez sur **Enregistrer** pour démarrer la recherche de collection ciblée.

### <a name="examples-of-search-queries-for-targeted-collections"></a>Exemples de requêtes de recherche pour les collections ciblées

Voici quelques exemples d’utilisation des propriétés et `documentlink` des `folderid` propriétés dans une requête de recherche pour effectuer une collection ciblée. Les espaces réservés sont utilisés pour et `documentlink:<path>` pour `folderid:<folderid>` économiser de l’espace.

- Cet exemple recherche trois dossiers de boîte aux lettres différents. Vous pouvez utiliser une syntaxe de requête similaire pour rechercher les dossiers masqués dans le dossier Éléments récupérables d’un utilisateur.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- Cet exemple recherche dans un dossier de boîte aux lettres les éléments qui contiennent une expression exacte.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- Cet exemple recherche dans un dossier de site (et tous les sous-dossiers) les documents qui contiennent les lettres « NDA » dans le titre.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- Cet exemple recherche dans un dossier de site (et tout sous-dossier) les documents qui ont été modifiés dans une plage de dates.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Plus d’informations

Gardez à l’esprit les éléments suivants lorsque vous utilisez le script de cet article pour effectuer des collections ciblées.

- Le script ne supprime aucun dossier des résultats. Par conséquent, certains dossiers répertoriés dans les résultats peuvent être introuvables (ou renvoyer zéro élément) parce qu’ils contiennent du contenu généré par le système ou parce qu’ils contiennent uniquement des sous-dossiers et non des éléments de boîte aux lettres.

- Ce script retourne uniquement les informations de dossier pour la boîte aux lettres principale de l’utilisateur. Il ne retourne pas d’informations sur les dossiers dans la boîte aux lettres d’archivage de l’utilisateur. Pour retourner des informations sur les dossiers dans la boîte aux lettres d’archivage de l’utilisateur, vous pouvez modifier le script. Pour ce faire, remplacez la ligne `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` par, puis enregistrez et exécutez le script modifié. Cette modification renvoie les ID de dossier pour les dossiers et les sous-dossiers dans la boîte aux lettres d’archivage de l’utilisateur. Pour effectuer une recherche dans l’intégralité de la boîte aux lettres d’archive, vous pouvez connecter toutes les paires property:value d’ID de dossier avec un `OR` opérateur dans une requête de recherche.

- Lors de la recherche dans les dossiers de boîte aux lettres, seul le dossier spécifié (identifié par sa `folderid` propriété) est recherché ; les sous-dossiers ne sont pas recherchés. Pour rechercher des sous-dossiers, vous devez utiliser l’ID de dossier du sous-dossier que vous souhaitez rechercher.

- Lors de la recherche dans les dossiers de site, le dossier (identifié par sa `documentlink` propriété) et tous les sous-dossiers sont recherchés.

- Lors de l’exportation des résultats d’une recherche dans laquelle vous avez spécifié uniquement la `folderid` propriété dans la requête de recherche, vous pouvez choisir la première option d’exportation, « Tous les éléments, à l’exclusion de celles qui ont un format non reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons ». Tous les éléments du dossier sont toujours exportés, quel que soit leur état d’indexation, car l’ID du dossier est toujours indexé.
