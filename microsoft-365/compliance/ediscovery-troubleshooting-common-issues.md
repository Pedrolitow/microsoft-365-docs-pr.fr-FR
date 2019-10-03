---
title: Dépannage des problèmes eDiscovery courants
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Examinez, dépannez et résolvez les problèmes courants dans Office 365 eDiscovery.
siblings_only: true
ms.openlocfilehash: 0d411976ecf6adba9df1f75eb8a45409647b3e1a
ms.sourcegitcommit: c7f7ff463141f7d7f0970b64e5a04341db7e4fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "37378636"
---
# <a name="investigate-troubleshoot-and-resolve-common-ediscovery-issues"></a>Examiner, dépanner et résoudre les problèmes eDiscovery courants

Cette rubrique décrit les étapes de résolution des problèmes que vous pouvez effectuer pour identifier et résoudre les problèmes que vous pouvez rencontrer lors d’une recherche de découverte électronique ou ailleurs dans le processus de découverte électronique. La résolution de certains de ces scénarios nécessite de l’aide du support Microsoft. Vous trouverez des informations sur le moment auquel contacter le support Microsoft dans la procédure de résolution.

## <a name="errorissue-ambiguous-location"></a>Erreur/problème : emplacement ambigu

Si vous essayez d’ajouter l’emplacement de la boîte aux lettres de l’utilisateur à rechercher et qu’il existe des objets en double ou en conflit avec le même ID utilisateur dans le répertoire Exchange Online Protection `The compliance search contains the following invalid location(s):useralias@contoso.com. The location "useralias@contoso.com" is ambiguous`(EoP), vous recevrez le message d’erreur suivant :. 

### <a name="resolution"></a>Résolution

Recherchez les utilisateurs en double ou la liste de distribution avec le même ID d’utilisateur.

1. Connectez-vous au [Centre de sécurité & conformité d’Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Récupérez toutes les instances du nom d’utilisateur, tapez :

    ```powershell
    Get-Recipient <username>
    ```

La sortie de « useralias@contoso.com » est semblable à ce qui suit :

> 
> |Name  |RecipientType  |
> |---------|---------|
> |Alias, User     |MailUser         |
> |Alias, User     |Utilisateur         |

3. Si plusieurs utilisateurs sont renvoyés, recherchez et corrigez l’objet en conflit.

## <a name="errorissue-search-fails-on-specific-locations"></a>Erreur/problème : la recherche échoue sur des emplacements spécifiques

Une recherche de contenu ou eDiscovery peut produire l’erreur suivante :
>Cette recherche s’est terminée avec les erreurs (#).  Voulez-vous relancer la recherche sur les emplacements ayant échoué ?

![Capture d’écran des erreurs d’emplacement spécifique à la recherche]( media/edisc-tshoot-specific-location-search-fails.png)

### <a name="resolution"></a>Résolution

Si vous recevez cette erreur, nous vous recommandons de vérifier les emplacements qui ont échoué dans la recherche, puis de réexécuter la recherche uniquement sur les emplacements ayant échoué.

1. Connectez-vous au [Centre de sécurité & conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) , puis entrez la commande suivante :

    ```powershell
    Get-ComplianceSearch <searchname> | FL 
    ```

2. À partir de la sortie PowerShell, affichez les emplacements en échec dans le champ erreurs ou à partir des informations d’État dans l’erreur du résultat de la recherche.

3. Renouvelez la recherche de découverte électronique aux emplacements ayant échoué uniquement.

4. Si vous continuez à recevoir ces erreurs, reportez-vous à la rubrique [Retry failed locations](https://docs.microsoft.com/en-us/Office365/SecurityCompliance/retry-failed-content-search) pour obtenir d’autres étapes de dépannage.

## <a name="errorissue-file-not-found"></a>Erreur/problème : fichier introuvable

Lors de l’exécution d’une recherche de découverte électronique incluant SharePoint Online et un lecteur pour les emplacements d’entreprise `File Not Found` , vous pouvez recevoir le message d’erreur même si le fichier se trouve sur le site. Cette erreur se produira dans les avertissements et les erreurs d’exportation. csv ou éléments ignorés. csv. Cela peut se produire si le fichier est introuvable sur le site ou si l’index est obsolète. Voici le texte d’une erreur réelle, avec l’accentuation ajoutée.
  
> 28.06.2019 10:02:19_FailedToExportItem_Failed pour télécharger du contenu. Informations de diagnostic supplémentaires : Microsoft. Office. Compliance. EDiscovery. ExportWorker. exceptions. ContentDownloadTemporaryFailure : échec de téléchargement à partir du contenu 6ea52149-91cd-4965-b5bb-82ca6a3ec9be de type document. ID de corrélation : 3bd84722-937b-4c23-B61B-08d6fba9ec32. ServerErrorCode :-2147024894---> Microsoft. SharePoint. client. ServerException : ***fichier introuvable***. at Microsoft. SharePoint. client. ClientRequest. ProcessResponseStream (Stream responseStream) à Microsoft. SharePoint. client. ClientRequest. ProcessResponse ()---fin de la trace de la pile d’exception interne---

### <a name="resolution"></a>Résolution

1. Vérifiez l’emplacement identifié dans la recherche pour vous assurer que l’emplacement du fichier est correct et ajouté aux emplacements de recherche.

2. Utilisez les procédures pour [demander manuellement l’analyse et la réindexation d’un site, d’une bibliothèque ou d’une liste](https://docs.microsoft.com/en-us/sharepoint/crawl-site-content) pour réindexer le site.

## <a name="errorissue-search-fails-because-recipient-is-not-found"></a>Erreur/problème : la recherche échoue, car le destinataire est introuvable

Une recherche de découverte électronique échoue avec `recipient not found`l’erreur. Cette erreur peut se produire si l’objet utilisateur est introuvable dans Exchange Online Protection (EOP) car l’objet n’a pas été synchronisé.

### <a name="resolution"></a>Résolution

1. Connectez-vous à [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

2. Vérifiez si l’objet utilisateur est synchronisé avec le type de protection Exchange Online :

    ```powershell
    Get-Recipient <userId> | FL
    ```

3. Il doit y avoir un objet utilisateur de messagerie pour la question de l’utilisateur. Si aucune valeur n’est renvoyée, examinez l’objet User. Contactez le support Microsoft si l’objet ne peut pas être synchronisé.

## <a name="errorissue-exporting-search-results-is-slow"></a>Erreur/problème : l’exportation des résultats de la recherche est lente

Lors de l’exportation des résultats de recherche à partir de eDiscovery ou de la recherche de contenu dans le centre de sécurité et conformité, le téléchargement prend plus de temps que prévu.  Vous pouvez vérifier la quantité de données à télécharger et augmenter éventuellement la vitesse d’exportation.

### <a name="resolution"></a>Résolution

1.  Essayez d’utiliser les étapes indiquées dans l’article [augmenter les vitesses de téléchargement](https://docs.microsoft.com/en-us/office365/securitycompliance/increase-download-speeds-when-exporting-ediscovery-results).

2.  Si vous rencontrez toujours des problèmes, connectez-vous à [Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) , puis entrez la commande suivante :

    ```powershell
    Get-ComplianceSearch <searchname> | FL
    ```

4. Recherchez la quantité de données à télécharger dans les paramètres SearchResults et SearchStatistics.

5. Entrez la commande suivante :

   ```powershell
   Get-ComplianceSearchAction | FL
   ```

6. Dans le champ résultats, recherchez les données qui ont été exportées et affichez les erreurs rencontrées.

7. Vérifiez le fichier trace. log situé dans le répertoire dans lequel vous avez exporté le contenu pour détecter d’éventuelles erreurs.

## <a name="errorissue-internal-server-error-500-occurred"></a>Erreur/problème : « erreur interne du serveur (500) » s’est produite»

Lors de l’exécution d’une recherche de découverte électronique, si la recherche continue de se produire avec une erreur semblable à « erreur interne du serveur (500) », vous pouvez être amené à relancer la recherche uniquement sur des emplacements de boîte aux lettres spécifiques.

![Capture d’écran de l’erreur de serveur interne 500](media/edisc-tshoot-error-500.png)

### <a name="resolution"></a>Résolution

1. Fractionnez la recherche en petites recherches et réexécutez la recherche.  Essayez d’utiliser une plage de dates plus petite ou limitez le nombre d’emplacements recherchés.

2. Connectez-vous au [Centre de sécurité & conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) , puis entrez la commande suivante :

    ```powershell
    Get-ComplianceSearch <searchname> | FL
    ```

3. Examinez la sortie pour les résultats et les erreurs.

4. Examinez le fichier trace. log. Il se trouve dans le dossier vers lequel vous avez envoyé l’exportation.

5. Contactez le support technique Microsoft.

## <a name="errorissue-holds-dont-sync"></a>Erreur/problème : conservation ne pas synchroniser

erreur de distribution de la stratégie de conservation de cas eDiscovery. L’erreur indique :

> «Ressources : le déploiement de la stratégie prend plus de temps que prévu. La mise à jour de l’état final du déploiement peut prendre deux heures supplémentaires, vous pouvez donc vérifier en quelques heures.

### <a name="resolution"></a>Résolution

1.  Connectez-vous au [Centre de sécurité & conformité Office 365 PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell) , puis entrez la commande suivante :

    ```powershell
    Get-RetentionCompliancePolicy  <policyname> - DistributionDetail | FL
    ```

2. Examinez la valeur du paramètre DistributionDetail pour rechercher les erreurs suivantes :

   > Si une erreur existe, créez une escalade à PG pour forcer une resynchronisation manuelle sur la stratégie.

3. Contactez le support technique Microsoft.

## <a name="see-also"></a>Voir aussi

- [Conseils pour éviter les erreurs d’emplacement de contenu](retry-failed-content-search.md#tips-to-avoid-content-location-errors)