---
title: Utiliser la recherche de contenu pour les collections ciblées
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
- M365-security-compliance
- SPO_Content
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: Utilisez la recherche de contenu dans le centre Microsoft 365 conformité pour effectuer une collection ciblée, qui recherche des éléments dans une boîte aux lettres ou un dossier de site spécifique.
ms.openlocfilehash: cf0364d39a78e1bbbc062d85ce750d190fbbda5a
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311896"
---
# <a name="use-content-search-for-targeted-collections"></a>Utiliser la recherche de contenu pour les collections ciblées

L’outil de recherche de contenu dans le Centre de conformité Microsoft 365 ne fournit pas un moyen direct dans l’interface utilisateur de rechercher des dossiers spécifiques dans des boîtes aux lettres Exchange ou des sites SharePoint et OneDrive Entreprise web. Toutefois, il est possible de rechercher des dossiers spécifiques (appelés une *collection* ciblée) en spécifiant la propriété d’ID de dossier pour la propriété de messagerie ou de chemin d’accès (DocumentLink) pour les sites dans la syntaxe de requête de recherche réelle. L’utilisation de la recherche de contenu pour effectuer une collection ciblée est utile lorsque vous êtes certain que les éléments qui répondent à un cas ou des éléments privilégiés se trouvent dans une boîte aux lettres ou un dossier de site spécifique. Vous pouvez utiliser le script de cet article pour obtenir l’ID de dossier pour les dossiers de boîte aux lettres ou le chemin d’accès (DocumentLink) pour les dossiers sur un site SharePoint et OneDrive Entreprise site. Ensuite, vous pouvez utiliser l’ID de dossier ou le chemin d’accès dans une requête de recherche pour renvoyer les éléments situés dans le dossier.

> [!NOTE]
> Pour renvoyer le contenu situé dans un dossier d’un site SharePoint ou OneDrive Entreprise, le script de cette rubrique utilise la propriété gérée DocumentLink au lieu de la propriété Path. La propriété DocumentLink est plus robuste que la propriété Path, car elle retourne tout le contenu d’un dossier, alors que la propriété Path ne retourne pas certains fichiers multimédias.

## <a name="before-you-run-a-targeted-collection"></a>Avant d’exécuter une collection ciblée

- Vous devez être membre du groupe de rôles Gestionnaire eDiscovery dans le Centre de sécurité & conformité pour exécuter le script à l’étape 1. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- Le rôle Destinataires de courrier doit également vous être attribué dans votre Exchange Online organisation. Cela est nécessaire pour exécuter la cmdlet **Get-MailboxFolderStatistics,** qui est incluse dans le script. Par défaut, le rôle Destinataires de courrier est attribué aux groupes de rôles Gestion de l’organisation et Gestion des destinataires dans Exchange Online. Pour plus d’informations sur l’attribution d’autorisations dans Exchange Online, voir [Gérer les membres du groupe de rôles.](/exchange/manage-role-group-members-exchange-2013-help) Vous pouvez également créer un groupe de rôles personnalisé, lui attribuer le rôle Destinataires de messagerie, puis ajouter les membres qui doivent exécuter le script à l’étape 1. Pour plus d'informations, consultez la rubrique [Gérer des groupes de rôles](/Exchange/permissions-exo/role-groups).

- Le script de cet article prend en charge l’authentification moderne. Vous pouvez utiliser le script tel qu’il est si vous êtes un Microsoft 365 ou une Microsoft 365 Cloud de la communauté du secteur public organisation. Si vous êtes une organisation Office 365 Germany, une organisation Microsoft 365 Cloud de la communauté du secteur public High ou une organisation DoD Microsoft 365, vous devez modifier le script pour l’exécuter correctement. Plus précisément, vous devez modifier la ligne et utiliser le paramètre `Connect-ExchangeOnline` *ExchangeEnvironmentName* (et la valeur appropriée pour le type de votre organisation) pour vous connecter à Exchange Online PowerShell.  En outre, vous devez modifier la ligne et utiliser les `Connect-IPPSSession` paramètres *ConnectionUri* et *AzureADAuthorizationEndpointUri* (et les valeurs appropriées pour le type de votre organisation) pour vous connecter au Centre de sécurité & conformité PowerShell. Pour plus d’informations, voir les exemples dans Connecter pour Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) et Connecter au Centre de sécurité & conformité [PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- Chaque fois que vous exécutez le script, une nouvelle session PowerShell distante est créée. Cela signifie que vous pouvez utiliser toutes les sessions PowerShell distantes à votre disposition. Pour éviter que cela ne se produise, exécutez la commande suivante pour déconnecter vos sessions PowerShell distantes actives.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

- Le script inclut une gestion minimale des erreurs. L’objectif principal du script est d’afficher rapidement une liste d’ID de dossier de boîte aux lettres ou de chemins d’accès au site qui peuvent être utilisés dans la syntaxe de requête de recherche d’une recherche de contenu pour effectuer une collection ciblée.

- L’exemple de script fourni dans cette rubrique n’est pas pris en charge dans le cadre d’un programme ou d’un service de support standard Microsoft. L’exemple de script est fourni tel quel, sans garantie d’aucune sorte. Microsoft Corporation décline aussi toute garantie implicite, y compris et sans limitation, les garanties implicites de qualité marchande ou d’adéquation à un usage particulier. La totalité des risques découlant de l’utilisation ou de la performance de l’exemple de script et de la documentation repose sur vous. En aucun cas Microsoft, ses auteurs ou quiconque impliqué dans la création, la production ou la livraison des scripts ne sera responsable de tous dommages quels qu’ils soient (y compris, sans limitation, les dommages pour perte de profits, interruption d’activité, perte d’informations commerciales ou toute autre perte pécuniaire) découlant de l’utilisation ou de l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été informé de la possibilité de tels dommages.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>Étape 1 : Exécuter le script pour obtenir la liste des dossiers d’une boîte aux lettres ou d’un site

Le script que vous exécutez lors de cette première étape retourne une liste de dossiers de boîtes aux lettres ou de dossiers SharePoint et OneDrive Entreprise, ainsi que l’ID ou le chemin d’accès correspondant pour chaque dossier. Lorsque vous exécutez ce script, il vous invite à fournir les informations suivantes.

- **Adresse de messagerie ou URL du site**: tapez l’adresse e-mail du dépositaire pour renvoyer la liste Exchange dossiers de boîte aux lettres et les ID de dossier. Ou tapez l’URL d’un site SharePoint ou d’un site OneDrive Entreprise pour renvoyer la liste des chemins d’accès pour le site spécifié. Voici quelques exemples :

  - **Exchange**: stacig@contoso.onmicrosoft <spam> <spam> .com

  - **SharePoint**: https <span>://</span>contoso.sharepoint.com/sites/marketing

  - **OneDrive Entreprise**: https <span>://</span>contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com

- **Vos informations d’identification** utilisateur : le script utilisera vos informations d’identification pour se connecter à Exchange Online PowerShell ou au Centre de sécurité & conformité PowerShell à l’aide de l’authentification moderne. Comme indiqué précédemment, les autorisations appropriées doivent vous être attribuées pour exécuter correctement ce script.

Pour afficher une liste de dossiers de boîtes aux lettres ou de noms de lien de document de site (chemin d’accès) :

1. Enregistrez le texte suivant dans un fichier Windows PowerShell script à l’aide d’un suffixe de nom de fichier .ps1 ; par exemple, `GetFolderSearchParameters.ps1` .

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the Security & Compliance Center.            #
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
   # Authenticate with Exchange Online and the Security & Compliance Center (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline
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
      # Connect to Security & Compliance Center PowerShell
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

2. Sur votre ordinateur local, ouvrez Windows PowerShell et allez dans le dossier où vous avez enregistré le script.

3. Exécutez le script . par exemple :

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. Entrez les informations que vous invite le script.

    Le script affiche la liste des dossiers de boîte aux lettres ou des dossiers de site pour l’utilisateur spécifié. Laissez cette fenêtre ouverte pour pouvoir copier un ID de dossier ou un nom de lien de document et le coller dans une requête de recherche à l’étape 2.

    > [!TIP]
    > Au lieu d’afficher une liste de dossiers sur l’écran de l’ordinateur, vous pouvez ré-diriger la sortie du script vers un fichier texte. Ce fichier est enregistré dans le dossier où se trouve le script. Par exemple, pour rediriger la sortie du script vers un fichier texte, exécutez la commande suivante à l’étape 3 : vous pouvez ensuite copier un ID de dossier ou un lien de document à partir du fichier à utiliser dans une requête de  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` recherche.

### <a name="script-output-for-mailbox-folders"></a>Sortie de script pour les dossiers de boîte aux lettres

Si vous obtenez des ID de dossier de boîte aux lettres, le script se connecte à Exchange Online PowerShell, exécute la cmdlet **Get-MailboxFolderStatisics,** puis affiche la liste des dossiers de la boîte aux lettres spécifiée. Pour chaque dossier de la boîte aux lettres, le script affiche le nom du dossier dans la colonne **FolderPath** et l’ID de dossier dans la **colonne FolderQuery.** En outre, le script ajoute le préfixe **folderId** (qui est le nom de la propriété de boîte aux lettres) à l’ID de dossier. Étant donné que **la propriété folderid** est une propriété utilisable dans une recherche, vous l’utiliserez dans une requête de recherche à l’étape 2 pour rechercher  `folderid:<folderid>` ce dossier. Le script affiche un maximum de 100 dossiers de boîte aux lettres.

> [!IMPORTANT]
> Le script de cet article inclut une logique de codage qui convertit les valeurs d’ID de dossier de 64 caractères renvoyées par **Get-MailboxFolderStatistics** au même format de 48 caractères qui est indexé pour la recherche. Si vous exécutez simplement la cmdlet **Get-MailboxFolderStatistics** dans PowerShell pour obtenir un ID de dossier (au lieu d’exécuter le script dans cet article), une requête de recherche qui utilise cette valeur d’ID de dossier échoue. Vous devez exécuter le script pour obtenir les ID de dossier correctement formatés qui peuvent être utilisés dans une recherche de contenu.

Voici un exemple de sortie renvoyée par le script pour les dossiers de boîte aux lettres.

![Exemple de liste des dossiers de boîte aux lettres et des ID de dossier renvoyés par le script](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

L’exemple de l’étape 2 montre la requête utilisée pour rechercher le sous-dossier Purges dans le dossier Éléments récupérables de l’utilisateur.

### <a name="script-output-for-site-folders"></a>Sortie de script pour les dossiers de site

Si vous recherchez le chemin d’accès de la propriété **documentlink** à partir de sites SharePoint ou OneDrive Entreprise, le script se connecte à Security & Compliance PowerShell, crée une recherche de contenu qui recherche des dossiers dans le site, puis affiche la liste des dossiers situés dans le site spécifié. Le script affiche le nom de chaque dossier et ajoute le préfixe **de documentlink** à l’URL du dossier. Étant donné que la propriété **documentlink** est une propriété utilisable dans une recherche, vous utiliserez la paire propriété:valeur dans une requête de recherche à l’étape 2 pour rechercher `documentlink:<path>` ce dossier. Le script affiche un maximum de 200 dossiers de site. S’il y a plus de 200 dossiers de site, les plus récents sont affichés.

Voici un exemple de sortie renvoyée par le script pour les dossiers de site.

![Exemple de liste de noms de liens de documents pour les dossiers de site renvoyés par le script](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>Étape 2 : Utiliser un ID de dossier ou un lien de document pour effectuer une collection ciblée

Après avoir exécuté le script pour collecter une liste d’ID de dossier ou de liens de documents pour un utilisateur spécifique, l’étape suivante vous permet d’aller au Centre de conformité Microsoft 365 et de créer une recherche de contenu pour rechercher un dossier spécifique. Vous utiliserez la paire ou property:value dans la requête de recherche que vous configurez dans la zone de mot clé de recherche de contenu (ou comme valeur pour le paramètre ContentMatchQuery si vous utilisez la `folderid:<folderid>` `documentlink:<path>` cmdlet **New-ComplianceSearch).**  Vous pouvez combiner la ou la  `folderid`  `documentlink` propriété avec d’autres paramètres de recherche ou conditions de recherche. Si vous incluez uniquement la ou la propriété dans la requête, la recherche retourne tous les éléments situés  `folderid`  `documentlink` dans le dossier spécifié.

1. Go to <https://compliance.microsoft.com> and sign in using the account and credentials that you used to run the script in Step 1.

2. Dans le volet gauche du centre de conformité, cliquez sur Afficher la recherche de contenu, puis  >  sur **Nouvelle recherche.**

3. Dans la **zone Mots clés,** collez la ou la valeur renvoyée par le script à `folderid:<folderid>`  `documentlink:<path>` l’étape 1.

    Par exemple, la requête de la capture d’écran suivante recherchera n’importe quel élément du sous-dossier Purges du dossier Éléments récupérables de l’utilisateur (la valeur de la propriété du sous-dossier Purges est indiquée dans la capture d’écran de l’étape `folderid` 1) :

    ![Coller le folderid ou le documentlink dans la zone de mot clé de la requête de recherche](../media/FolderIDSearchQuery.png)

4. Sous **Emplacements,** **sélectionnez Des emplacements spécifiques,** puis cliquez sur **Modifier.**

5. Faites l’une des choses suivantes, selon que vous recherchez un dossier de boîte aux lettres ou un dossier de site :

    - En **Exchange,** cliquez sur Choisir des utilisateurs, des groupes ou des **équipes,** puis ajoutez la boîte aux lettres que vous avez spécifiée lorsque vous avez lancé le script à l’étape 1.

      Ou

    - En SharePoint **sites,** cliquez sur Choisir des **sites,** puis ajoutez la même URL de site que celle que vous avez spécifiée lorsque vous avez lancé le script à l’étape 1.

6. Après avoir enregistrez l’emplacement de contenu à rechercher, cliquez sur Enregistrer **&** exécuter, tapez un nom pour la recherche de contenu, puis cliquez sur Enregistrer pour démarrer la recherche de collection ciblée. 

### <a name="examples-of-search-queries-for-targeted-collections"></a>Exemples de requêtes de recherche pour des collections ciblées

Voici quelques exemples d’utilisation des propriétés dans une requête de recherche pour  `folderid`  `documentlink` effectuer une collection ciblée. Les espaces réservé sont utilisés pour  `folderid:<folderid>` et pour économiser de  `documentlink:<path>` l’espace.

- Cet exemple recherche trois dossiers de boîtes aux lettres différents. Vous pouvez utiliser une syntaxe de requête similaire pour rechercher les dossiers masqués dans le dossier Éléments récupérables d’un utilisateur.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- Cet exemple recherche dans un dossier de boîte aux lettres les éléments qui contiennent une expression exacte.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- Cet exemple recherche dans un dossier de site (et tous les sous-dossiers) les documents qui contiennent les lettres « NDA » dans le titre.

  ```powershell
  documentlink:<path> AND filename:nda
  ```

- Cet exemple recherche dans un dossier de site (et tout sous-dossier) les documents qui ont été modifiés dans une plage de dates.

  ```powershell
  documentlink:<path> AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>Plus d’informations

Gardez les points suivants à l’esprit lorsque vous utilisez le script de cet article pour effectuer des collections ciblées.

- Le script ne supprime aucun dossier des résultats. Par exemple, certains dossiers répertoriés dans les résultats peuvent ne pas être accessibles à la recherche (ou renvoyer zéro éléments) car ils contiennent du contenu généré par le système ou parce qu’ils contiennent uniquement des sous-dossiers et non des éléments de boîte aux lettres.

- Ce script renvoie uniquement les informations de dossier pour la boîte aux lettres principale de l’utilisateur. Il ne retourne pas d’informations sur les dossiers de la boîte aux lettres d’archivage de l’utilisateur. Pour renvoyer des informations sur les dossiers de la boîte aux lettres d’archivage de l’utilisateur, vous pouvez modifier le script. Pour ce faire, modifiez la ligne, `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` puis `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` enregistrez et exécutez le script modifié. Cette modification retourne les ID de dossier pour les dossiers et les sous-dossiers de la boîte aux lettres d’archivage de l’utilisateur. Pour effectuer une recherche dans l’ensemble de la boîte aux lettres d’archivage, vous pouvez connecter toutes les paires propriété:valeur de l’ID de dossier avec un opérateur `OR` dans une requête de recherche.

- Lorsque vous recherchez des dossiers de boîte aux lettres, seul le dossier spécifié (identifié par sa propriété) est recherché ; les sous-dossiers ne sont `folderid` pas recherchés. Pour rechercher des sous-dossiers, vous devez utiliser l’ID de dossier du sous-dossier que vous souhaitez rechercher.

- Lorsque vous recherchez des dossiers de site, le dossier (identifié par sa propriété) et tous les `documentlink` sous-dossiers sont recherchés.

- Lors de l’exportation des résultats d’une recherche dans laquelle vous avez uniquement spécifié la propriété dans la requête de recherche, vous pouvez choisir la première option d’exportation , « Tous les éléments, à l’exception de ceux qui ont un format non reconnu, sont chiffrés ou n’ont pas été indexés pour `folderid` d’autres raisons. » Tous les éléments du dossier sont toujours exportés quel que soit leur état d’indexation, car l’ID de dossier est toujours indexé.
