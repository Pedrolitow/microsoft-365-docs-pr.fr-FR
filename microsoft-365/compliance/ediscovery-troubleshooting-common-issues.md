---
title: Résolution des problèmes eDiscovery courants
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez les étapes de résolution des problèmes de base que vous pouvez suivre pour résoudre les problèmes courants dans Office 365 eDiscovery.
siblings_only: true
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b562e3d22557133630fa8c7c7d343432736b9f4f
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58569608"
---
# <a name="investigate-troubleshoot-and-resolve-common-ediscovery-issues"></a>Examiner, résoudre et résoudre les problèmes eDiscovery courants

Cette rubrique traite des étapes de résolution des problèmes de base que vous pouvez effectuer pour identifier et résoudre les problèmes que vous pouvez rencontrer lors d’une recherche de découverte électronique ou ailleurs dans le processus eDiscovery. La résolution de certains de ces scénarios nécessite l’aide du Support Microsoft. Les informations sur le moment où contacter le Support Microsoft sont incluses dans les étapes de résolution.

## <a name="errorissue-ambiguous-location"></a>Erreur/problème : emplacement ambigu

Si vous essayez d’ajouter l’emplacement de la boîte aux lettres de l’utilisateur à rechercher et qu’il existe des objets en double ou en conflit avec le même userID dans l’annuaire Exchange Online Protection (EOP), vous recevez cette erreur : `The compliance search contains the following invalid location(s):useralias@contoso.com. The location "useralias@contoso.com" is ambiguous` .

### <a name="resolution"></a>Résolution

Recherchez des utilisateurs en double ou une liste de distribution avec le même ID d’utilisateur.

1. Connecter au [Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande suivante pour récupérer toutes les instances du nom d’utilisateur :

    ```powershell
    Get-Recipient <username>
    ```

   La sortie de « useralias@contoso.com » serait similaire à ce qui suit :

   > 
   > |Nom|RecipientType|
   > |---|---|
   > |Alias, Utilisateur|MailUser|
   > |Alias, Utilisateur|Utilisateur|

3. Si plusieurs utilisateurs sont renvoyés, recherchez et corrigez l’objet en conflit.

## <a name="errorissue-search-fails-on-specific-locations"></a>Erreur/problème : la recherche échoue sur des emplacements spécifiques

Une recherche de contenu ou eDiscovery peut produire l’erreur suivante : `This search completed with (#) errors.  Would you like to retry the search on the failed locations?`

![Capture d’écran d’erreur d’erreur d’un emplacement spécifique à la recherche.](../media/edisc-tshoot-specific-location-search-fails.png)

### <a name="resolution"></a>Résolution

Si vous recevez cette erreur, nous vous recommandons de vérifier les emplacements qui ont échoué dans la recherche, puis de réexécuter la recherche uniquement sur les emplacements qui ont échoué.

1. Connecter [au Centre de sécurité & conformité PowerShell,](/powershell/exchange/connect-to-scc-powershell) puis exécutez la commande suivante :

   ```powershell
   Get-ComplianceSearch <searchname> | FL
   ```

2. À partir de la sortie PowerShell, affichez les emplacements qui ont échoué dans le champ erreurs ou à partir des détails d’état dans l’erreur à partir de la sortie de recherche.

3. Réessayez la recherche eDiscovery uniquement sur les emplacements qui ont échoué.

4. Si vous continuez à recevoir ces erreurs, consultez Réessayer les emplacements d’échec [pour](/Office365/SecurityCompliance/retry-failed-content-search) plus d’étapes de résolution des problèmes.

## <a name="errorissue-file-not-found"></a>Erreur/problème : fichier in trouvé

Lors de l’exécution d’une recherche de découverte électronique qui inclut des emplacements SharePoint Online et OneDrive Entreprise, vous pouvez recevoir l’erreur même si le fichier se trouve `File Not Found` sur le site. Cette erreur sera dans les avertissements d’exportation et errors.csv ou ignorée items.csv. Cela peut se produire si le fichier n’est pas trouvé sur le site ou si l’index n’est pas à jour. Voici le texte d’une erreur réelle (avec une accentuation ajoutée).

> 28.06.2019 10:02:19_FailedToExportItem_Failed télécharger du contenu. Informations de diagnostic supplémentaires : Microsoft. Office. Compliance.EDiscovery.ExportWorker.Exceptions.ContentDownloadTemporaryFailure: Failed to download from content 6ea52149-91cd-4965-b5bb-82ca6a3ec9be of type Document. ID de corrélation : 3bd84722-937b-4c23-b61b-08d6fba9ec32. ServerErrorCode : -2147024894 ---> Microsoft. SharePoint. Client.ServerException : ***fichier in trouvé.*** chez Microsoft. SharePoint. Client.ClientRequest.ProcessResponseStream(Stream responseStream) chez Microsoft. SharePoint. Client.ClientRequest.ProcessResponse() --- fin de la trace de pile des exceptions internes ---

### <a name="resolution"></a>Résolution

1. Vérifiez l’emplacement identifié dans la recherche pour vous assurer que l’emplacement du fichier est correct et ajouté aux emplacements de recherche.

2. Utilisez les procédures de demande manuelle d’analyse et [de réindexation](/sharepoint/crawl-site-content) d’un site, d’une bibliothèque ou d’une liste pour réindexer le site.

## <a name="errorissue-this-file-wasnt-exported-because-it-doesnt-exist-anymore-the-file-was-included-in-the-count-of-estimated-search-results-because-its-still-listed-in-the-index-the-file-will-eventually-be-removed-from-the-index-and-wont-cause-an-error-in-the-future"></a>Erreur/problème : ce fichier n’a pas été exporté car il n’existe plus. Le fichier a été inclus dans le nombre de résultats de recherche estimés, car il est toujours répertorié dans l’index. Le fichier sera finalement supprimé de l’index et ne provoquera pas d’erreur à l’avenir.

Vous pouvez voir cette erreur lors de l’exécution d’une recherche eDiscovery qui inclut SharePoint Online et OneDrive Entreprise sites. eDiscovery s’appuie sur l’index SPO pour identifier les emplacements de fichiers. Si le fichier a été supprimé mais que l’index SPO n’a pas encore été mis à jour, cette erreur peut se produire.

### <a name="resolution"></a>Résolution 
Ouvrez l’emplacement SPO et vérifiez que ce fichier n’y est pas.
La solution suggérée consiste à réindexer manuellement le site ou à attendre la réindexation du site par le processus en arrière-plan automatique.


## <a name="errorissue-this-search-result-was-not-downloaded-as-it-is-a-folder-or-other-artifact-that-cant-be-downloaded-by-itself-any-items-inside-the-folder-or-library-will-be-downloaded"></a>Erreur/problème : ce résultat de recherche n’a pas été téléchargé car il s’agit d’un dossier ou d’un autre artefact qui ne peut pas être téléchargé seul, tous les éléments du dossier ou de la bibliothèque seront téléchargés.

Vous pouvez voir cette erreur lors de l’exécution d’une recherche eDiscovery qui inclut SharePoint Online et OneDrive Entreprise sites. Cela signifie que nous allions essayer d’exporter l’élément signalé dans l’index, mais qu’il s’est traduit par un dossier afin de ne pas l’exporter. Comme mentionné dans l’erreur, nous n’exportons pas les éléments de dossier, mais nous exportons leur contenu.

## <a name="errorissue-search-fails-because-recipient-is-not-found"></a>Erreur/problème : la recherche échoue car le destinataire est in trouvé

Une recherche eDiscovery échoue avec l’erreur . `recipient not found` Cette erreur peut se produire si l’objet utilisateur est in Exchange Online Protection (EOP) car l’objet n’a pas été synchronisé.

### <a name="resolution"></a>Résolution

1. Connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande suivante pour vérifier si l’utilisateur est synchronisé avec Exchange Online Protection :

   ```powershell
   Get-Recipient <userId> | FL
   ```

3. Il doit y avoir un objet utilisateur de messagerie pour la question de l’utilisateur. Si rien n’est renvoyé, examinez l’objet utilisateur. Contactez le Support Microsoft si l’objet ne peut pas être synchronisé.

## <a name="errorissue-exporting-search-results-is-slow"></a>Erreur/problème : l’exportation des résultats de recherche est lente

Lors de l’exportation des résultats de recherche à partir de core eDiscovery ou de recherche de contenu dans le Centre de conformité Microsoft 365, le téléchargement prend plus de temps que prévu.  Vous pouvez vérifier la quantité de données à télécharger et éventuellement augmenter la vitesse d’exportation.

### <a name="resolution"></a>Résolution

1. Connecter [au Centre de sécurité & conformité PowerShell,](/powershell/exchange/connect-to-scc-powershell) puis exécutez la commande suivante :

   ```powershell
   Get-ComplianceSearch <searchname> | FL
   ```

2. Recherchez la quantité de données à télécharger dans les paramètres SearchResults et SearchStatistics.

3. Exécutez la commande suivante :

   ```powershell
   Get-ComplianceSearchAction | FL
   ```

4. Dans le champ résultats, recherchez les données qui ont été exportées et affichez les erreurs rencontrées.

5. Recherchez les erreurs éventuelles dans le fichier trace.log situé dans le répertoire vers qui vous avez exporté le contenu.

6. Si vous avez encore des problèmes, envisagez de diviser les recherches qui retournent un grand ensemble de résultats en recherches plus petites. Par exemple, vous pouvez utiliser des plages de dates dans les requêtes de recherche pour renvoyer un ensemble de résultats plus petit qui peut être téléchargé plus rapidement.

## <a name="errorissue-export-process-not-progressing-or-is-stuck"></a>Erreur/problème : le processus d’exportation n’est pas en cours ou est bloqué

Lors de l’exportation des résultats de recherche à partir de core eDiscovery ou de recherche de contenu dans le Centre de conformité Microsoft 365, le processus d’exportation n’est pas en cours ou semble bloqué.

### <a name="resolution"></a>Résolution

1. Si nécessaire, réexécutez la recherche. Si la recherche a été réexécutée pour la dernière fois il y a plus de sept jours, vous devez réexécuter la recherche.

2. Redémarrez l’exportation.

## <a name="errorissue-internal-server-error-500-occurred"></a>Erreur/problème : « Une erreur de serveur interne (500) s’est produite »

Lors de l’exécution d’une recherche de découverte électronique, si la recherche échoue continuellement avec une erreur semblable à « Erreur interne du serveur (500) s’est produite », vous devrez peut-être réexécuter la recherche uniquement sur des emplacements de boîtes aux lettres spécifiques.

![Capture d’écran de l’erreur du serveur interne 500.](../media/edisc-tshoot-error-500.png)

### <a name="resolution"></a>Résolution

1. Décomposez la recherche en recherches plus petites et exécutez à nouveau la recherche.  Essayez d’utiliser une plage de dates plus petite ou limitez le nombre d’emplacements recherchés.

2. Connecter [au Centre de sécurité & conformité PowerShell,](/powershell/exchange/connect-to-scc-powershell) puis exécutez la commande suivante :

   ```powershell Set-CaseHoldPolicy <policyname> -RetryDistribution
   Get-ComplianceSearch <searchname> | FL
   ```

3. Examinez la sortie pour les résultats et les erreurs.

4. Examinez le fichier trace.log. Il se trouve dans le même dossier que celui vers qui vous avez exporté les résultats de la recherche.

5. Contactez le support technique Microsoft.

## <a name="errorissue-holds-dont-sync"></a>Erreur/problème : les holds ne sont pas synchronisés

Erreur de distribution de synchronisation de stratégie de la stratégie de prise en main eDiscovery. L’erreur se lit comme ci-après :

> « Ressources : le déploiement de la stratégie prend plus de temps que prévu. La mise à jour de l’état de déploiement final peut prendre 2 heures supplémentaires, donc vérifiez-la dans quelques heures. »

### <a name="resolution"></a>Résolution

1. Connecter au Centre de sécurité & conformité [PowerShell,](/powershell/exchange/connect-to-scc-powershell) puis exécutez la commande suivante pour une mise en attente de cas eDiscovery :

   ```powershell
   Get-CaseHoldPolicy <policyname> - DistributionDetail | FL
   ```

    Pour une stratégie de rétention, exécutez la commande suivante :

   ```powershell
   Get-RetentionCompliancePolicy <policyname> - DistributionDetail | FL
   ```

2. Examinez la valeur dans le paramètre DistributionDetail pour les erreurs suivantes :

   > Erreur : Ressources : le déploiement de la stratégie prend plus de temps que prévu. La mise à jour de l’état de déploiement final peut prendre 2 heures supplémentaires, donc vérifiez-la dans quelques heures. »

3. Essayez d’exécutez le paramètre RetryDistribution sur la stratégie en question :

   Pour les cas eDiscovery :

   ```powershell
   Set-CaseHoldPolicy <policyname> -RetryDistribution
   ```

   Pour les stratégies de rétention :

   ```powershell
   Set-RetentionCompliancePolicy <policyname> -RetryDistribution
   ```

4. Contactez le support technique Microsoft.

## <a name="error-the-condition-specified-using-http-conditional-headers-is-not-met"></a>Erreur : « La condition spécifiée à l’aide d’en-têtes conditionnels HTTP n’est pas remplie »

Lorsque vous téléchargez des résultats de recherche à l’aide de l’outil d’exportation eDiscovery, il est possible que vous receviez l’erreur suivante : Il s’agit d’une erreur passagère, qui se produit généralement à `System.Net.WebException: The remote server returned an error: (412) The condition specified using HTTP conditional header(s) is not met.` l’emplacement stockage Azure.

### <a name="resolution"></a>Résolution

Pour résoudre ce problème, réessayez de [télécharger](export-search-results.md#step-2-download-the-search-results)les résultats de la recherche, ce qui redémarrera l’outil d’exportation eDiscovery.

## <a name="errorissue-downloaded-export-shows-no-results"></a>Erreur/problème : l’exportation téléchargée n’affiche aucun résultat

Une fois l’exportation réussie, le téléchargement terminé via l’outil d’exportation affiche zéro fichier dans les résultats.

### <a name="resolution"></a>Résolution

Il s’agit d’un problème côté client. Pour y remédier, suivez les étapes suivantes :

1. Essayez d’utiliser un autre client/ordinateur pour télécharger.

2. Supprimez les anciennes recherches qui ne sont plus nécessaires à l’aide de la cmdlet [Remove-ComplianceSearch.](/powershell/module/exchange/remove-compliancesearch)

3. Veillez à effectuer le téléchargement sur un lecteur local.

4. Assurez-vous que le scanneur antivirus n’est pas en cours d’exécution.

5. Assurez-vous qu’aucune autre exportation n’est téléchargée vers le même dossier ou n’importe quel dossier parent.

6. Si les étapes précédentes ne fonctionnent pas, désactivez la fermeture à la tiret et la déplication.

7. Si cela fonctionne, le problème est dû à un scanneur antivirus local ou à un problème de disque.

## <a name="error-your-request-cant-be-started-because-the-maximum-number-of-jobs-for-your-organization-are-currently-running"></a>Erreur : « Votre demande ne peut pas être démarrée car le nombre maximal de travaux de votre organisation est en cours d’exécution »

Votre organisation a atteint la limite du nombre maximal de travaux d’exportation simultanés. Toutes les nouvelles tâches d’exportation sont limitées.

### <a name="resolution"></a>Résolution

Exécutez le script suivant pour découvrir combien de travaux d’exportation qui ont été démarrés au cours des sept derniers jours sont toujours en cours d’exécution.

1. Connecter au [Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez le script suivant pour collectionr des informations sur les tâches d’exportation en cours qui déclenchent la limitation :

   ```powershell
   $date = Get-Date;
   $exports = Get-ComplianceSearchAction -Export -ResultSize Unlimited;
   $inprogressExports = $exports | ?{$_.Results -eq $null -or (!$_.Results.Contains("Export status: Completed") -and !$_.Results.Contains("Export status: none"))};
   $exportJobsRunning = $inprogressExports | ?{$_.JobStartTime -ge $date.AddDays(-7)} | Sort-Object JobStartTime -Descending;
   ```

3. Exécutez la commande suivante pour afficher la liste des travaux d’exportation en cours d’exécution :

   ```powershell
   $exportJobsRunning | Format-Table Name, JobStartTime, JobEndTime, Status | More;
   ```

   Si la commande précédente renvoie au moins 10 travaux d’exportation, votre organisation a atteint la limite du nombre de travaux d’exportation simultanés. Pour plus d’informations, voir [Limites pour la recherche eDiscovery.](limits-for-content-search.md)

4. Attendez que les travaux d’exportation existants terminent ou suppriment les travaux d’exportation qui ne sont plus nécessaires à l’aide de la cmdlet [Remove-ComplianceSearchAction.](/powershell/module/exchange/remove-compliancesearchaction)
