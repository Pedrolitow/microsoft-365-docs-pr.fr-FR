---
title: Résoudre les erreurs de mise en suspens de la découverte électronique
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Résoudre les erreurs liées aux conservations légales appliquées aux dépositaires et aux sources de données qui ne sont pas en conservation dans core eDiscovery.
ms.openlocfilehash: 3e5cc6351d5026feda560bee646a1e6a03475ee2
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182296"
---
# <a name="troubleshoot-ediscovery-hold-errors"></a>Résoudre les erreurs de mise en suspens de la découverte électronique

Cet article traite des problèmes courants qui peuvent se produire avec les conserves eDiscovery et explique comment les résoudre. L’article inclut également des pratiques recommandées pour vous aider à atténuer ou à éviter ces problèmes.

## <a name="recommended-practices"></a>Pratiques recommandées

Pour réduire le nombre d’erreurs liées aux conserves eDiscovery, nous vous recommandons les pratiques suivantes :

- Si une distribution de la mise en attente est toujours en attente, avec l’un ou l’autre état, patientez jusqu’à ce que la distribution de la mise en attente soit `On (Pending)` terminée avant d’effectuer d’autres mises à `Off (Pending)` jour.

- Vérifiez si une stratégie de mise en attente est en attente avant d’y apporter d’autres mises à jour. Exécutez les commandes suivantes ou enregistrez-les dans un script PowerShell.

    ```powershell
    $status = Get-CaseHoldPolicy -Identity <policyname> -DistributionDetail
    if($status.DistributionStatus -ne "Pending"){
        # policy no longer pending
        Set-CaseHoldPolicy -Identity <policyname> -AddExchangeLocation $user1
    }else{
        # policy still pending
        Write-Host "Hold policy still pending."
    }
   ```

- Fusionnez vos mises à jour dans une mise en attente eDiscovery dans une seule demande en bloc au lieu de mettre à jour la stratégie de mise à jour à plusieurs reprises pour chaque transaction. Par exemple, pour ajouter plusieurs boîtes aux lettres utilisateur à une stratégie de blocage existante à l’aide de la cmdlet [Set-CaseHoldPolicy,](/powershell/module/exchange/set-caseholdpolicy) exécutez la commande (ou ajoutez-la en tant que bloc de code à un script) afin qu’elle ne s’exécute qu’une seule fois pour ajouter plusieurs utilisateurs.

  **Correct**

    ```powershell
    Set-CaseHoldPolicy -Identity <policyname> -AddExchangeLocation {$user1, $user2, $user3, $user4, $user5}
    ```

   **Incorrect**

    ```powershell
    $users = {$user1, $user2, $user3, $user4, $user5}
    ForEach($user in $users)
    {
        Set-CaseHoldPolicy -Identity <policyname> -AddExchangeLocation $user
    }
    ```

   Dans l’exemple incorrect précédent, la cmdlet est exécuté cinq fois distinctement pour effectuer la tâche. Pour plus d’informations sur les pratiques recommandées pour ajouter des utilisateurs à une stratégie de attente, consultez la section [Plus d’informations.](#more-information)

- Avant de contacter le Support Microsoft concernant les problèmes de la découverte électronique, suivez les étapes de la section [Erreur/problème](#errorissue-holds-dont-sync) : Les attentes ne sont pas synchronisées pour réessayer la distribution de la attente. Ce processus résout souvent des problèmes temporaires, notamment des erreurs de serveur interne.

## <a name="errorissue-holds-dont-sync"></a>Erreur/problème : les holds ne sont pas synchronisés

Si vous voyez l’un des messages d’erreur suivants lors de la mise en attente des dépositaires et des sources de données, utilisez les étapes de résolution pour résoudre le problème.

> Ressources : le déploiement de la stratégie prend plus de temps que prévu. La mise à jour de l’état de déploiement final peut prendre 2 heures supplémentaires. Vérifiez-le dans quelques heures.

> La stratégie ne peut pas être déployée sur la source de contenu en raison d’un problème Office 365 de centre de données temporaire. La stratégie actuelle n’est appliquée à aucun contenu de la source, donc le déploiement bloqué n’a aucun impact. Pour résoudre ce problème, essayez de redéployer la stratégie.

> Désolé, nous n’avons pas pu effectuer les modifications demandées à la stratégie en raison d’une erreur temporaire du serveur interne. Veuillez essayer à nouveau dans 30 minutes.

### <a name="resolution"></a>Résolution

1. Connecter [au Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante pour une mise en attente eDiscovery :

   ```powershell
   Get-CaseHoldPolicy <policyname> -DistributionDetail | FL
   ```

2. Examinez la valeur dans le *paramètre DistributionDetail.* Recherchez les erreurs suivantes :

   > Erreur : Ressources : le déploiement de la stratégie prend plus de temps que prévu. La mise à jour de l’état de déploiement final peut prendre 2 heures supplémentaires. Vérifiez-le dans quelques heures.

3. Essayez d’exécution de la commande **Set-CaseHoldPolicy -RetryDistribution** sur la stratégie de mise en attente en question ; par exemple :

   ```powershell
   Set-CaseHoldPolicy <policyname> -RetryDistribution
   ```

## <a name="error-the-sharepoint-site-is-read-only-or-not-accessible"></a>Erreur : le site SharePoint est en lecture seule ou inaccessible

Si vous voyez le message d’erreur suivant lors de la mise en attente des dépositaires et des sources de données, cela signifie que l’administrateur global de votre organisation ou l’administrateur [SharePoint a](/sharepoint/sharepoint-admin-role) verrouillé le site. Un site verrouillé empêche eDiscovery de placer le site en attente.

> Le site SharePoint est accessible en lecture seule ou inaccessible. Veuillez contacter l’administrateur du site pour rendre le site accessible en ligne, puis redéployer cette stratégie.

### <a name="resolution"></a>Résolution

Déverrouillez le site (ou demandez à un administrateur de le déverrouiller) pour résoudre ce problème. Pour en savoir plus sur la modification de l’état de verrouillage d’un site, voir [Verrouiller et déverrouiller des sites.](/sharepoint/manage-lock-status)

## <a name="error-the-mailbox-or-sharepoint-site-may-not-exist"></a>Erreur : la boîte aux lettres ou SharePoint site n’existe peut-être pas

Si vous voyez le message d’erreur suivant lors de la mise en attente des dépositaires et des sources de données, utilisez les étapes de résolution pour résoudre le problème.

> La boîte aux lettres ou SharePoint site web n’existe peut-être pas.  Si ce n’est pas le cas, contactez le support Microsoft.  Dans le cas contraire, supprimez-la de cette stratégie.

### <a name="resolution"></a>Résolution

- Exécutez [Get-Mailbox](/powershell/module/exchange/get-mailbox) dans Exchange Online PowerShell pour vérifier si la boîte aux lettres utilisateur existe dans votre organisation.

- Exécutez la cmdlet [Get-SPOSite](/powershell/module/sharepoint-online/get-sposite) dans SharePoint Online PowerShell pour vérifier si le site existe dans votre organisation.

- Vérifiez si l’URL du site a changé.

## <a name="more-information"></a>Plus d’informations

Les instructions sur la mise à jour des stratégies de blocage pour plusieurs utilisateurs dans la section « Pratiques recommandées » résultent du fait que le système bloque les mises à jour simultanées d’une stratégie de blocage. Cela signifie que lorsqu’une stratégie de mise à jour de mise en attente est appliquée aux nouveaux emplacements de contenu et que la stratégie de mise en attente est dans un état en attente, des emplacements de contenu supplémentaires ne peuvent pas être ajoutés à la stratégie de mise en attente. Voici quelques éléments à garder à l’esprit pour vous aider à atténuer ce problème :
  
- Chaque fois qu’une mise à jour de la mise à jour d’une mise en attente est mise à jour, elle passe immédiatement à l’état en attente. L’état d’état en attente signifie que la attente est appliquée aux emplacements de contenu.
  
- Si vous avez un script qui exécute une boucle et ajoute des emplacements à la stratégie un par un (semblable à l’exemple incorrect présenté dans la section « Pratiques recommandées », le premier emplacement de contenu (par exemple, une boîte aux lettres utilisateur) lance le processus de synchronisation qui déclenche l’état en attente. Cela signifie que les autres utilisateurs ajoutés à la stratégie dans les boucles suivantes entraînent une erreur.
  
- Si votre organisation utilise un script qui exécute une boucle pour mettre à jour les emplacements de contenu pour une stratégie de mise en attente, vous devez mettre à jour le script afin qu’il met à jour les emplacements en une seule opération en bloc (comme illustré dans l’exemple correct dans la section « Pratiques recommandées »).
