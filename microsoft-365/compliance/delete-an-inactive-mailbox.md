---
title: Suppression d’une boîte aux lettres inactive
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: f5caf497-5e8d-4b7a-bfff-d02942f38150
ms.custom:
- seo-marvel-apr2020
description: Lorsque vous n’avez plus besoin de conserver le contenu d’Microsoft 365 boîte aux lettres inactive, vous pouvez supprimer définitivement la boîte aux lettres inactive.
ms.openlocfilehash: 929b3d8a01dd9c88bc12e6e13bf4477a07496b34
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2021
ms.locfileid: "60804628"
---
# <a name="delete-an-inactive-mailbox"></a>Suppression d’une boîte aux lettres inactive

Une boîte aux lettres inactive est utilisée pour conserver le courrier électronique d’un ancien employé après qu’il a quitté votre organisation. Si vous n'avez plus besoin du contenu d'une boîte aux lettres inactive, vous pouvez le supprimer de façon définitive en supprimant le blocage. En outre, il est possible que plusieurs blocages soient placés sur une boîte aux lettres inactive. Par exemple, une boîte aux lettres inactive peut être placée en suspension pour litige et sur une ou plusieurs blocages sur place. En outre, une stratégie de rétention (créée dans le centre de sécurité et conformité dans Office 365 ou Microsoft 365) peut être appliquée à la boîte aux lettres inactive. Vous devez supprimer toutes les conservations et stratégies de rétention d’une boîte aux lettres inactive pour la supprimer. Une fois que vous avez supprimé les stratégies de conservation et de rétention, la boîte aux lettres inactive est marquée pour suppression et définitivement supprimée après son traitement.
  
> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes façons pour conserver le contenu des boîtes aux lettres, nous annonceons le retrait des conservations In-Place dans le Centre d’administration Exchange gestion. Cela signifie que vous devez utiliser des conservations pour litige et des stratégies de rétention pour créer une boîte aux lettres inactive. À compter du 1er juillet 2020, vous ne pourrez plus créer de In-Place de Exchange Online. Toutefois, vous pourrez toujours modifier la durée d’une In-Place placée sur une boîte aux lettres inactive. Toutefois, à compter du 1er octobre 2020, vous ne pourrez pas modifier la durée de la durée de la durée de la période de attente. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont en conservation In-Place sont conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur le retrait des In-Place, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)
  
Consultez la section [Plus d'informations](#more-information) pour obtenir une description de ce qui se produit après la suppression des blocages d'une boîte aux lettres inactive.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Avant de supprimer une boîte aux lettres inactive

- Vous devez utiliser powershell Exchange Online pour supprimer une attente pour litige d’une boîte aux lettres inactive. Vous ne pouvez pas utiliser le Centre d'administration Exchange (CAE). Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous pouvez copier le contenu d'une boîte aux lettres inactive vers une autre boîte aux lettres avant de supprimer la conservation et de supprimer une boîte aux lettres inactive. Pour plus d’informations, voir [Restaurer une boîte aux lettres inactive dans Office 365](restore-an-inactive-mailbox.md).

- Si vous supprimez la stratégie de conservation ou de rétention d’une boîte aux lettres inactive et que la période de rétention de la boîte aux lettres supprimée (suppression temporaire) de la boîte aux lettres a expiré, la boîte aux lettres est définitivement supprimée. Après sa suppression, elle ne peut pas être récupérée. Avant de supprimer la conservation, vérifiez que vous n'avez plus besoin du contenu de la boîte aux lettres. Si vous souhaitez réactiver une boîte aux lettres inactive, vous pouvez la récupérer. Pour plus d’informations, [voir Récupérer une boîte aux lettres inactive dans Office 365](recover-an-inactive-mailbox.md).

- Pour plus d’informations sur les boîtes aux lettres inactives, consultez [la Office 365](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Comme indiqué précédemment, une conservation pour litige, une In-Place de rétention ou une stratégie de rétention peuvent être placées sur une boîte aux lettres inactive. La première étape consiste à identifier les blocages sur une boîte aux lettres inactive.
  
Exécutez la commande suivante pour afficher les informations de blocage pour toutes les boîtes aux lettres inactives dans votre organisation.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

La valeur de **True** pour la propriété **LitigationHoldEnabled** indique que la boîte aux lettres inactive est en suspension pour litige. Si un blocage sur place est placé sur une boîte aux lettres inactive, le GUID du blocage s'affiche comme valeur pour la propriété **InPlaceHolds**. Par exemple, les résultats suivants pour deux boîtes aux lettres inactives indiquent qu’une conservation pour litige est placée sur Ann Beebe et qu’une conservation In-Place et une stratégie de rétention sont placées sur Pilar Pinilla.
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491, mbxba6f4ba25b62490aaaa253eea27426ab}
```

> [!TIP]
> Si un grand nombre In-Place conservations ou stratégies de rétention sont placées sur une boîte aux lettres inactive, tous les In-Place de conservation ne seront pas affichés. Vous pouvez exécuter la commande suivante pour afficher tous les GUID dans la propriété InPlaceHolds :  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Pour plus d’informations sur l’identification des mises en attente, voir Comment identifier le type de mise en attente [placée sur une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>Étape 2 : Supprimer une blocage d'une boîte aux lettres inactive

Après avoir identifié le type de blocage placé sur la boîte aux lettres inactive (et s'il y a plusieurs blocages), l'étape suivante consiste à supprimer les blocages sur la boîte aux lettres. Comme indiqué précédemment, vous devez supprimer tous les blocages pour supprimer définitivement une boîte aux lettres inactive.
  
### <a name="remove-a-litigation-hold"></a>Supprimer une suspension pour litige

Comme indiqué précédemment, vous devez utiliser Windows PowerShell pour supprimer une suspension pour litige d'une boîte aux lettres inactive. Vous ne pouvez pas utiliser le CAE. Exécutez la commande suivante pour supprimer une suspension pour litige.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> La meilleure façon d'identifier une boîte aux lettres inactive est d'utiliser son nom unique ou sa valeur GUID Exchange. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Supprimer une boîte aux lettres inactive d’une stratégie de rétention

La procédure de suppression d’une boîte aux lettres inactive d’une stratégie Microsoft 365 de rétention dépend de la stratégie de rétention affectée à la boîte aux lettres inactive à l’échelle de l’organisation ou explicite. sur le type de stratégie de rétention qui est affecté à la boîte aux lettres inactive.

- Stratégies de rétention à l’échelle de l’organisation affectées à toutes les boîtes aux lettres de l’organisation. Utilisez la cmdlet **Get-OrganizationConfig** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation.

- Stratégies de rétention d’emplacement spécifiques affectées à des boîtes aux lettres spécifiques. Ce sont des stratégies qui sont affectées aux emplacements de contenu d’utilisateurs spécifiques. Utilisez la cmdlet **Get-Mailbox -IncludeInactiveMailbox** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention attribuées à des boîtes aux lettres inactives spécifiques.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Supprimer une boîte aux lettres inactive d’une stratégie de rétention à l’échelle de l’organisation

Exécutez la commande suivante dans Exchange Online PowerShell pour exclure une boîte aux lettres inactive d’une stratégie de rétention à l’échelle de l’organisation.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Pour plus d’informations sur l’identification des stratégies de rétention à l’échelle de l’organisation appliquées à une boîte aux lettres inactive et sur l’obtention du GUID d’une stratégie de rétention, consultez la section « Get-OrganizationConfig » dans comment identifier le [type](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig)de conservation placé sur une boîte aux lettres.

Vous pouvez également exécuter la commande suivante pour supprimer la boîte aux lettres inactive de toutes les stratégies à l’échelle de l’organisation :

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Supprimer une boîte aux lettres inactive d’une stratégie de rétention d’emplacement spécifique

Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell) pour supprimer une boîte aux lettres inactive d’une stratégie de rétention explicite.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -AddExchangeLocationException <identity of inactive mailbox>
```

Pour plus d’informations sur l’identification des stratégies de rétention d’emplacement spécifiques appliquées à une boîte aux lettres inactive et l’obtention du GUID d’une stratégie de rétention, consultez la section « Get-Mailbox » dans Comment identifier le [type](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox)de conservation placé sur une boîte aux lettres.

### <a name="remove-in-place-holds"></a>Supprimer des blocages sur place

 Il existe deux façons de supprimer un blocage sur place à partir d'une boîte aux lettres inactive :
  
- **Supprimez lIn-Place hold .** Si la boîte aux lettres inactive que vous souhaitez supprimer définitivement est la seule boîte aux lettres source pour une In-Place, vous pouvez simplement supprimer l’objet In-Place hold. 

    > [!NOTE]
    > Vous devez désactiver le blocage avant de pouvoir supprimer un objet de blocage sur place. Si vous essayez de supprimer un objet de blocage sur place ayant le blocage activé, vous recevrez un message d'erreur. 
  
- **Supprimez la boîte aux lettres inactive en tant que boîte aux lettres source d’une In-Place en attente.** Si vous souhaitez conserver d’autres boîtes aux lettres sources pour une In-Place, vous pouvez supprimer la boîte aux lettres inactive de la liste des boîtes aux lettres source et conserver l’objet In-Place Hold.

#### <a name="delete-an-in-place-hold"></a>Supprimer une In-Place en attente

1. Créez une variable qui contient les propriétés du blocage sur place à supprimer. Utilisez le GUID du blocage sur place obtenu à l'[Étape 1 : Identifier les blocages sur une boîte aux lettres inactive](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Désactivez le blocage sur le blocage sur place.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Supprimez le blocage sur place.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Supprimer une boîte aux lettres inactive d’une In-Place en attente

Si le blocage sur place contient un grand nombre de boîtes aux lettres source, il est possible que la boîte aux lettres inactive ne soit pas répertoriée sur la page **Sources** dans le CAE. Jusqu'à 3 000 boîtes aux lettres s'affichent sur la page **Sources** lorsque vous modifiez un blocage sur place. Si une boîte aux lettres inactive n’est pas répertoriée dans la page **Sources,** vous pouvez utiliser Exchange Online PowerShell pour la supprimer de la In-Place en attente. 
  
1. Créez une variable qui contient les propriétés du blocage sur place placé sur la boîte aux lettres inactive. Utilisez le GUID du blocage sur place obtenu à l'[Étape 1 : Identifier les blocages sur une boîte aux lettres inactive](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Vérifiez que la boîte aux lettres inactive est répertoriée comme une boîte aux lettres source pour le blocage sur place. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > La propriété *Sources* du blocage sur place identifie les boîtes aux lettres source par leurs propriétés *LegacyExchangeDN*. Étant donné que cette propriété identifie les boîtes aux lettres inactives de façon unique, l'utilisation de la propriété *Sources* du blocage sur place permet d'empêcher la suppression de la boîte aux lettres incorrecte. Cela permet également d'éviter les problèmes si deux boîtes aux lettres ont le même alias ou la même adresse SMTP. 

3. Supprimez la boîte aux lettres inactive dans la liste des boîtes aux lettres sources dans la variable. Veillez à utiliser le **LegacyExchangeDN** de la boîte aux lettres inactive qui est renvoyé par la commande à l'étape précédente. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Par exemple, la commande suivante supprime la boîte aux lettres inactive pour Pilar Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Vérifiez que la boîte aux lettres inactive est supprimée de la liste des boîtes aux lettres source dans la variable.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Modifiez le blocage sur place avec la liste mise à jour des boîtes aux lettres source, qui n'inclut pas la boîte aux lettres inactive.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Vérifiez que la boîte aux lettres inactive est supprimée de la liste des boîtes aux lettres source pour le blocage sur place.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Plus d’informations

- **Une boîte aux lettres inactive est un type de boîte aux lettres supprimée (récupérable).** Dans Exchange Online, une boîte aux lettres supprimée (récupérable) est une boîte aux lettres qui a été supprimée mais qui peut être récupérée pendant une période de rétention spécifique. Pour les boîtes aux lettres supprimées (récupérables) qui ne sont pas en attente, la boîte aux lettres est récupérable dans les 30 jours. Une boîte aux lettres inactive (une boîte aux lettres en attente avant sa suppression) reste dans un état de suppression (avec état de attente) jusqu’à ce que la boîte aux lettres soit supprimée. Une fois la boîte aux lettres inactive supprimée, la boîte aux lettres n’est plus dans un état inactif. Au lieu de cela, il devient supprimé (récupérable) et reste en Exchange Online pendant 183 jours à partir du jour où la période de la période de attente a été supprimée et récupérable pendant cette période. Après 183 jours, une boîte aux lettres supprimée (récupération) est marquée pour suppression définitive et ne peut pas être récupérée.

- **Que se passe-t-il après avoir supprimé la conservation sur une boîte aux lettres inactive ?** La boîte aux lettres est traitée comme d’autres boîtes aux lettres supprimées (suppression temporaire) et est marquée pour suppression définitive après l’expiration de la période de rétention de 183 jours. Cette période de rétention commence à la date à laquelle la conservation est supprimée de la boîte aux lettres inactive. La *propriété InactiveMailboxRetireTime* est définie lorsque la boîte aux lettres passe de l’état inactif (supprimé (supprimé de la boîte aux lettres) à l’état inactif (supprimé (supprimé de la boîte aux lettres sans mise en attente). À ce stade, la *propriété InactiveMailboxRetireTime* est définie sur la date actuelle à laquelle la transition s’est produite. Il existe un assistant qui s’exécute (appelé Assistant *MailboxLifeCycle)* qui recherche les boîtes aux lettres dont la propriété *InactiveMailboxRetireTime* est définie. Si « InactiveMailboxRetireTime + 183 jours » est inférieur à la date actuelle, la boîte aux lettres sera purgée.

- **Une boîte aux lettres inactive est-elle définitivement supprimée immédiatement après la suppression de la conservation ?** Une boîte aux lettres auparavant inactive sera disponible à l’état supprimé (suppression possible) pendant 183 jours. Après 183 jours, la boîte aux lettres est marquée pour suppression définitive.

- **Comment afficher des informations sur une boîte aux lettres inactive après la suppression de la conservation ?** Une fois qu’une boîte aux lettres inactive a été supprimée et que la boîte aux lettres inactive est revenir à une boîte aux lettres supprimée (suppression réverable), elle ne sera pas renvoyée à l’aide du paramètre *InactiveMailboxOnly* avec la cmdlet **Get-Mailbox.** Cependant, vous pouvez afficher des informations sur la boîte aux lettres à l'aide de la commande **Get-Mailbox -SoftDeletedMailbox**. Par exemple :

  ```text
  Get-Mailbox -SoftDeletedMailbox -Identity pilarp | FL Name,Identity,LitigationHoldEnabled,In
  Placeholds,WhenSoftDeleted,IsInactiveMailbox,WasInactiveMailbox,InactiveMailboxRetireTime
  Name                   : pilarp
  Identity               : Soft Deleted Objects\pilarp
  LitigationHoldEnabled  : False
  InPlaceHolds           : {}
  WhenSoftDeleted        : 6/16/2020 1:19:04 AM
  IsInactiveMailbox      : False
  WasInactiveMailbox     : True
  InactiveMailboxRetireTime : 9/30/2020 11:16:23 PM
  ```

  Dans l’exemple ci-dessus, la *propriété WhenSoftDeleted* identifie la date supprimée (supprimée (supprimé(s) (supprimé(s) (dans cet exemple) : 16 juin 2020. La *propriété WasInactiveMailbox est* répertoriée comme étant une boîte aux lettres `True` inactive. La boîte aux lettres sera définitivement supprimée 183 jours après le 30 septembre 2020.

