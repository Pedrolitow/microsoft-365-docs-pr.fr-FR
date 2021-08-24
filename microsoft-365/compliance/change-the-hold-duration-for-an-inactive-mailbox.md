---
title: Modifier la durée de la conservation pour une boîte aux lettres inactive
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 8/29/2017
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
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: Une fois qu Office 365 boîte aux lettres est inactive, modifiez la durée de la conservation ou Office 365 stratégie de rétention attribuée à la boîte aux lettres inactive.
ms.openlocfilehash: 02fb0ab1f598db3532f1544c041dfcffd3a2224a
ms.sourcegitcommit: 4582873483bd52bc790bf75b838cc505dc4bbeb4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58502890"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une boîte aux lettres inactive est utilisée pour conserver l'e-mail d'un ancien employé une fois qu'il quitte votre organisation. Une boîte aux lettres devient inactive lorsqu’une conservation pour litige, une conservation In-Place, une stratégie de rétention Microsoft 365 ou une conservation associée à un cas eDiscovery est placée sur la boîte aux lettres et que le compte d’utilisateur correspondant est supprimé. Le contenu d'une boîte aux lettres inactive est conservé pendant la durée de la conservation appliquée à la boîte aux lettres avant qu'elle ne soit définie comme inactive. La durée de la conservation définit la durée de conservation des éléments dans le dossier Éléments récupérables. Lorsque la durée de conservation expire pour un élément du dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. Une fois qu’une boîte aux lettres est inactive, vous pouvez modifier la durée de la conservation ou Microsoft 365 stratégie de rétention attribuée à la boîte aux lettres inactive.
  
> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes façons pour conserver le contenu des boîtes aux lettres, nous annonceons le retrait des conservations In-Place dans le Centre d’administration Exchange gestion. Cela signifie que vous devez utiliser les conservations pour litige et Microsoft 365 rétention pour créer une boîte aux lettres inactive. À compter du 1er avril 2020, vous ne pourrez plus créer de In-Place de Exchange Online. Toutefois, vous pourrez toujours modifier la durée d’une In-Place placée sur une boîte aux lettres inactive. Toutefois, à compter du 1er juillet 2020, vous ne pourrez pas modifier la durée de la durée de la durée de la période de attente. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont en conservation In-Place sont conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur le retrait des In-Place, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)
  
## <a name="connect-to-powershell"></a>Connecter à PowerShell

- You have to use Exchange Online PowerShell to change the hold duration for a Litigation Hold on an inactive mailbox. You can't use the Exchange admin center (EAC). But you can use Exchange Online PowerShell or the EAC to change the hold duration for an In-Place Hold. Vous pouvez utiliser le Centre de sécurité et conformité ou le Centre de sécurité & conformité PowerShell pour modifier la durée de la conservation pour une stratégie Microsoft 365 rétention.
    
- Pour vous connecter à Exchange Online PowerShell ou au Centre de sécurité & conformité PowerShell, consultez l’une des rubriques suivantes :
    
  - [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
  - [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell)
    
- Les attentes associées aux cas eDiscovery sont des attentes infinies, ce qui signifie qu’il n’existe aucune durée de la durée de la période de attente qui peut être modifiée. Les éléments sont mis en conservation indéfiniment ou jusqu'à ce que la conservation et la boîte aux lettres inactive soient supprimées.
    
- Pour plus d’informations sur les boîtes aux lettres inactives, consultez [la Microsoft 365](inactive-mailboxes-in-office-365.md).
    
## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Étant donné que différents types de conservations ou une ou plusieurs stratégies de rétention Microsoft 365 peuvent être placées sur une boîte aux lettres inactive, la première étape consiste à identifier les conservations sur une boîte aux lettres inactive.
  
Exécutez la commande suivante dans Exchange Online PowerShell pour afficher les informations de conservation pour toutes les boîtes aux lettres inactives dans votre organisation.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,InPlaceHolds
```

La valeur de **True** pour la propriété **LitigationHoldEnabled** indique que la boîte aux lettres inactive est en conservation pour litige. Si une conservation In-Place, une conservation eDiscovery ou une stratégie de rétention Microsoft 365 est placée sur une boîte aux lettres inactive, un GUID pour la conservation ou la stratégie de rétention s’affiche en tant que valeur pour la propriété **InPlaceHolds.** Par exemple, l’exemple suivant montre les résultats pour cinq boîtes aux lettres inactives. 
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
LitigationHoldDuration: 365.00:00:00
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
LitigationHoldDuration: Unlimited
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491}
...
DisplayName           : Mario Necaise
Name                  : marion
IsInactiveMailbox     : True
LitigationHoldEnabled : False
LitigationHoldDuration: Unlimited
InPlaceHolds          : {}
...
DisplayName           : Carol Olson
Name                  : carolo
IsInactiveMailbox     : True
LitigationHoldEnabled : False
LitigationHoldDuration: Unlimited
InPlaceHolds          : {mbxcdbbb86ce60342489bff371876e7f224}
...
DisplayName           : Abraham McMahon
Name                  : abrahamm
IsInactiveMailbox     : True
LitigationHoldEnabled : False
LitigationHoldDuration: Unlimited
InPlaceHolds          : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
```

Le tableau suivant indique les cinq différents types de conservations qui ont été utilisés pour chaque boîte aux lettres inactive.
  
|**Boîte aux lettres inactive**|**Type de conservation**|**Comment identifier la conservation dans la boîte aux lettres inactive**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Conservation pour litige  <br/> |La propriété  *LitigationHoldEnabled*  est définie sur  `True`.  <br/> |
|Pilar Pinilla  <br/> |Conservation inaltérable  <br/> |La propriété  *InPlaceHolds*  contient le GUID de la conservation inaltérable appliquée à la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une conservation inaltérable, car l'ID ne commence pas par un préfixe.  <br/> Vous pouvez utiliser la commande  `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` dans Exchange Online PowerShell pour obtenir des informations sur la conservation inaltérable dans la boîte aux lettres inactive.  <br/> |
|Mario Necaise  <br/> |Stratégie de rétention Microsoft 365 à l’échelle de l’organisation dans le Centre de conformité Microsoft 365  <br/> |La propriété  *InPlaceHolds*  est vide. Cela indique qu’une ou plusieurs stratégies de rétention Microsoft 365 à l’échelle de l’organisation ou (Exchange à l’échelle de l’organisation) sont appliquées à la boîte aux lettres inactive. Dans ce cas, vous pouvez exécuter la commande dans Exchange Online PowerShell pour obtenir la liste des GUID pour les stratégies de rétention Microsoft 365 à l’échelle de `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` l’organisation. Le GUID des stratégies de rétention à l’échelle de l’organisation qui sont appliquées Exchange boîtes aux lettres commence par le `mbx` préfixe ; par exemple, `mbxa3056bb15562480fadb46ce523ff7b02` .  <br/> <br/>Pour identifier la stratégie Microsoft 365 rétention appliquée à la boîte aux lettres inactive, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell.  <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>
|Carol Olson  <br/> |Microsoft 365 rétention dans le Centre de sécurité & conformité appliqué à des boîtes aux lettres spécifiques  <br/> |La *propriété InPlaceHolds contient* le GUID de la stratégie Microsoft 365 rétention appliquée à la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une stratégie de rétention qui est appliquée à des boîtes aux lettres spécifiques, car le GUID commence par le préfixe  `mbx`. Si le GUID de la stratégie de rétention appliquée à la boîte aux lettres inactive a démarré avec le préfixe, il indique que la stratégie de rétention est appliquée à Skype Entreprise `skp` conversations.  <br/><br/> Pour identifier la stratégie Microsoft 365 rétention appliquée à la boîte aux lettres inactive, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell.<br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name` <br/><br/>N'oubliez pas de supprimer le préfixe  `mbx` ou  `skp` lorsque vous exécutez cette commande.  <br/> |
|Abraham McMahon  <br/> |Cas eDiscovery dans la Centre de conformité Microsoft 365  <br/> |La propriété  *InPlaceHolds*  contient le GUID de la conservation du cas eDiscovery qui figure dans la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une mise en conservation de cas eDiscovery, car le GUID commence par le préfixe  `UniH`.  <br/> Vous pouvez utiliser la cmdlet dans le Centre de sécurité & conformité PowerShell pour obtenir des informations sur le cas eDiscovery associé à la mise en attente sur la boîte aux lettres  `Get-CaseHoldPolicy` inactive. For example, you can run the command  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` to display the name of the case hold that's on the inactive mailbox. Be sure to remove the  `UniH` lorsque vous exécutez cette commande.  <br/><br/> Pour identifier le cas eDiscovery associé à la conservation dans la boîte aux lettres inactive, exécutez les commandes suivantes.  <br/><br/> `$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/> `Get-ComplianceCase $CaseHold.CaseId | FL Name`<br/><br/><br/> **Remarque :** Nous vous déconseillons d’utiliser des boîtes aux lettres inactives à l’aide de la découverte électronique. En effet, les cas eDiscovery sont destinés à cas spécifiques, limités dans le temps et liés à un problème juridique. À un moment ou un autre, un dossier juridique se terminera probablement, et les conservations associées au cas seront supprimées et le cas eDiscovery sera fermé (ou supprimé). En fait, si une conservation figurant dans une boîte aux lettres inactive est associée à un cas eDiscovery et que la conservation est libérée, ou le cas eDiscovery est fermé ou supprimé, la boîte aux lettres inactive est définitivement supprimée. 

Pour plus d’informations sur Microsoft 365 stratégies de rétention, voir En savoir plus sur les stratégies [de rétention et les étiquettes de rétention.](retention.md)
  
## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Étape 2 : Modifier la durée de la conservation pour une boîte aux lettres inactive

Après avoir identifié le type de conservation placé sur la boîte aux lettres inactive (et s'il y a plusieurs conservations), l'étape suivante consiste à modifier la durée de la conservation. 
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Modifier la durée pour une conservation pour litige

Voici comment utiliser Exchange Online PowerShell pour modifier la durée de la conservation pour litige appliquée à une boîte aux lettres inactive. Vous ne pouvez pas utiliser le CAE. Exécutez la commande suivante pour modifier la durée de la conservation. Dans cet exemple, la durée de la conservation est modifiée pendant une période illimitée.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Les éléments de la boîte aux lettres inactive sont alors conservés indéfiniment ou jusqu'à ce que la conservation soit supprimée ou que la durée de la conservation soit remplacée par une autre valeur.
  
> [!TIP]
> La meilleure façon d'identifier une boîte aux lettres inactive est d'utiliser sa valeur **Distinguished Name** ou **Exchange GUID**. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres. 
  
### <a name="change-the-duration-for-an-in-place-hold"></a>Modifier la durée pour une conservation inaltérable

 In-Place les In-Place ont été retirées et ne peuvent plus être modifiées. Si une boîte aux lettres inactive dispose d’une In-Place de la boîte aux lettres inactive, vous ne pouvez pas modifier la durée de la durée de la boîte aux lettres. Vous pouvez uniquement supprimer la In-Place, ce qui entraîne la suppression de la boîte aux lettres inactive. Pour plus d’informations, voir [Supprimer une boîte aux lettres inactive.](delete-an-inactive-mailbox.md#remove-in-place-holds)
  
## <a name="more-information"></a>Plus d’informations

- **Comment la durée de la conservation est-elle calculée pour un élément dans une boîte aux lettres inactive ?** La durée est calculée à partir de la date de réception ou de création d’origine d’un élément de boîte aux lettres. 
    
- **Que se passe-t-il lorsque la durée de la conservation arrive à expiration ?** Lorsque la durée de la conservation arrive à expiration pour un élément de boîte aux lettres dans le dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. Si aucune durée n’est spécifiée pour la mise en attente sur la boîte aux lettres inactive, les éléments du dossier Éléments récupérables ne sont jamais purgés (sauf si la durée de la mise en attente de la boîte aux lettres inactive est modifiée). 
    
- **Une stratégie de rétention Exchange est-elle toujours traitée sur les boîtes aux lettres inactives ?** Si une stratégie de rétention Exchange (la fonctionnalité de gestion des enregistrements de messagerie, ou MRM, dans Exchange Online) a été appliquée à une boîte aux lettres lorsqu'elle est devenue inactive, les stratégies de suppression (qui sont des balises de rétention configurées avec une action de rétention **Delete** ) continueront à être traitées sur la boîte aux lettres inactive. Cela signifie que les éléments marqués avec une stratégie de suppression sont déplacés vers le dossier Éléments récupérables à l'expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation d'un élément. 
    
    À l'inverse, les stratégies d'archivage (qui sont des balises de rétention configurées avec une action de rétention **MoveToArchive** ) incluses dans la stratégie de rétention attribuée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Étant donné qu'un utilisateur ne peut pas se connecter à une boîte aux lettres inactive, il est inutile d'utiliser des ressources du centre de données pour traiter des stratégies d'archivage. 

- **Pour vérifier la nouvelle durée de la attente pour litige, exécutez les commandes suivantes :** 

   ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | FL LitigationHoldDuration
    ```

- **Comme les boîtes aux lettres ordinaires, l'Assistant Dossier géré traite également les boîtes aux lettres inactives.** Dans Exchange Online, le MFA traite les boîtes aux lettres environ tous les sept jours. Après avoir modifié la durée de la conservation pour une boîte aux lettres inactive, vous pouvez utiliser la cmdlet **Start-ManagedFolderAssistant** pour démarrer immédiatement le traitement de la nouvelle durée de la conservation pour la boîte aux lettres inactive. Exécutez la commande suivante. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Si de nombreuses mises en attente sont placées sur une boîte aux lettres inactive, tous les GUID de mise en attente ne sont pas affichés.** Vous pouvez exécuter la commande suivante pour afficher les GUID pour toutes les conservations (sauf pour les conservations pour litige) qui figurent dans une boîte aux lettres inactive. 
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```