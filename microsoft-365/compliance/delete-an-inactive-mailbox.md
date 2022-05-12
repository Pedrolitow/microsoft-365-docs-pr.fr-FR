---
title: Suppression d’une boîte aux lettres inactive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
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
description: Lorsque vous n’avez plus besoin de conserver le contenu d’une boîte aux lettres inactive Microsoft 365, vous pouvez supprimer définitivement la boîte aux lettres inactive.
ms.openlocfilehash: 1e518bda3d11ff17c4ce5aa1ebb6997f8bc09c4d
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363130"
---
# <a name="delete-an-inactive-mailbox"></a>Suppression d’une boîte aux lettres inactive

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une boîte aux lettres inactive est utilisée pour conserver l’adresse e-mail d’un ancien employé après son départ de votre organisation. Si vous n'avez plus besoin du contenu d'une boîte aux lettres inactive, vous pouvez le supprimer de façon définitive en supprimant le blocage. En outre, il est possible que plusieurs blocages soient placés sur une boîte aux lettres inactive. Par exemple, une boîte aux lettres inactive peut être placée en suspension pour litige et sur une ou plusieurs blocages sur place. En outre, Microsoft 365 rétention peut être appliquée à la boîte aux lettres inactive. Vous devez supprimer toutes les conservations et stratégies de rétention d’une boîte aux lettres inactive pour la supprimer. Après avoir supprimé les stratégies de conservation et de rétention, la boîte aux lettres inactive est marquée pour suppression et est définitivement supprimée après son traitement.
  
> [!IMPORTANT]
> Alors que nous continuons d’investir de différentes façons pour préserver le contenu de la boîte aux lettres, nous annoncions le retrait de In-Place Conservations dans le centre d’administration Exchange. Cela signifie que vous devez utiliser des stratégies de conservation et de rétention pour créer une boîte aux lettres inactive. À compter du 1er juillet 2020, vous ne pourrez pas créer de In-Place Conservations dans Exchange Online. Toutefois, vous pourrez toujours modifier la durée de conservation d’une In-Place mise en attente sur une boîte aux lettres inactive. Toutefois, à compter du 1er octobre 2020, vous ne pourrez pas modifier la durée de conservation. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant le In-Place Hold. Les boîtes aux lettres inactives existantes qui sont en attente In-Place sont conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur la mise hors service de In-Place Conservations, consultez [La mise hors service des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
  
Consultez la section [Plus d'informations](#more-information) pour obtenir une description de ce qui se produit après la suppression des blocages d'une boîte aux lettres inactive.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Avant de supprimer une boîte aux lettres inactive

- Vous devez utiliser Exchange Online PowerShell pour supprimer une conservation des litiges d’une boîte aux lettres inactive. Vous ne pouvez pas utiliser le Centre d'administration Exchange (CAE). Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous pouvez copier le contenu d'une boîte aux lettres inactive vers une autre boîte aux lettres avant de supprimer la conservation et de supprimer une boîte aux lettres inactive. Pour plus d’informations, consultez [Restaurer une boîte aux lettres inactive dans Office 365](restore-an-inactive-mailbox.md).

- Si vous supprimez la stratégie de conservation ou de rétention d’une boîte aux lettres inactive et que la période de rétention de boîte aux lettres supprimée de manière réversible pour la boîte aux lettres a expiré, la boîte aux lettres sera définitivement supprimée après l’expiration de la période de rétention de boîte aux lettres supprimée de manière réversible de 183 jours. Pour plus d’informations sur la période de rétention des boîtes aux lettres supprimées de manière réversible, consultez la section [Plus d’informations](#more-information) de cet article. Une fois la boîte aux lettres inactive supprimée définitivement, elle ne peut pas être récupérée. Avant de supprimer la conservation, vérifiez que vous n'avez plus besoin du contenu de la boîte aux lettres. Si vous souhaitez réactiver une boîte aux lettres inactive, vous pouvez la récupérer. Pour plus d’informations, consultez [Récupérer une boîte aux lettres inactive dans Office 365](recover-an-inactive-mailbox.md).

- Pour plus d’informations sur les boîtes aux lettres inactives, voir [En savoir plus sur les boîtes aux lettres inactives.](inactive-mailboxes-in-office-365.md)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Comme indiqué précédemment, une stratégie de conservation des litiges, de conservation In-Place ou de rétention peut être placée sur une boîte aux lettres inactive. La première étape consiste à identifier les blocages sur une boîte aux lettres inactive.
  
Exécutez la commande suivante pour afficher les informations de blocage pour toutes les boîtes aux lettres inactives dans votre organisation.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

La valeur de **True** pour la propriété **LitigationHoldEnabled** indique que la boîte aux lettres inactive est en suspension pour litige. Si un blocage sur place est placé sur une boîte aux lettres inactive, le GUID du blocage s'affiche comme valeur pour la propriété **InPlaceHolds**. Par exemple, les résultats suivants pour deux boîtes aux lettres inactives montrent qu’une conservation du litige est placée sur Ann Beebe et qu’une stratégie de conservation et de conservation In-Place sont placées sur Pilar Pinilla.
  
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
> Si un grand nombre de stratégies de conservation ou de rétention In-Place sont placées sur une boîte aux lettres inactive, tous les guidons de conservation In-Place ne sont pas affichés. Vous pouvez exécuter la commande suivante pour afficher tous les GUID dans la propriété InPlaceHolds :  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Pour plus d’informations sur l’identification des conservations, consultez [Comment identifier le type de conservation placé sur une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md).

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

La procédure de suppression d’une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365 varie selon que la stratégie de rétention affectée à la boîte aux lettres inactive est explicite ou à l’échelle de l’organisation. sur le type de stratégie de rétention affecté à la boîte aux lettres inactive.

- Stratégies de rétention à l’échelle de l’organisation affectées à toutes les boîtes aux lettres de l’organisation. Utilisez l’applet de commande **Get-OrganizationConfig** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation.

- Stratégies de rétention d’emplacement spécifiques affectées à des boîtes aux lettres spécifiques. Il s’agit de stratégies qui sont affectées aux emplacements de contenu de certains utilisateurs. Utilisez l’applet de commande **Get-Mailbox -IncludeInactiveMailbox** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention affectées à des boîtes aux lettres inactives spécifiques.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Supprimer une boîte aux lettres inactive d’une stratégie de rétention à l’échelle de l’organisation

Exécutez la commande suivante dans Exchange Online PowerShell pour exclure une boîte aux lettres inactive d’une stratégie de rétention à l’échelle de l’organisation.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Pour plus d’informations sur l’identification des stratégies de rétention à l’échelle de l’organisation appliquées à une boîte aux lettres inactive et l’obtention du GUID pour une stratégie de rétention, consultez la section « Get-OrganizationConfig » dans [Comment identifier le type de conservation placé sur une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig).

Vous pouvez également exécuter la commande suivante pour supprimer la boîte aux lettres inactive de toutes les stratégies à l’échelle de l’organisation :

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Supprimer une boîte aux lettres inactive d’une stratégie de rétention d’emplacement spécifique

Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell) pour supprimer une boîte aux lettres inactive d’une stratégie de rétention explicite.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -RemoveExchangeLocation <identity of inactive mailbox>
```

Pour plus d’informations sur l’identification des stratégies de rétention d’emplacement spécifiques appliquées à une boîte aux lettres inactive et l’obtention du GUID pour une stratégie de rétention, consultez la section « Get-Mailbox » dans [Comment identifier le type de conservation placé sur une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>Supprimer des blocages sur place

 Il existe deux façons de supprimer un blocage sur place à partir d'une boîte aux lettres inactive :
  
- **Supprimez l’objet In-Place Hold**. Si la boîte aux lettres inactive que vous souhaitez supprimer définitivement est la seule boîte aux lettres source pour une In-Place Hold, vous pouvez simplement supprimer l’objet In-Place Hold. 

    > [!NOTE]
    > Vous devez désactiver le blocage avant de pouvoir supprimer un objet de blocage sur place. Si vous essayez de supprimer un objet de blocage sur place ayant le blocage activé, vous recevrez un message d'erreur. 
  
- **Supprimez la boîte aux lettres inactive en tant que boîte aux lettres source d’une In-Place Hold**. Si vous souhaitez conserver d’autres boîtes aux lettres sources pour une In-Place Conservation, vous pouvez supprimer la boîte aux lettres inactive de la liste des boîtes aux lettres sources et conserver l’objet In-Place Hold.

#### <a name="delete-an-in-place-hold"></a>Supprimer une conservation In-Place

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

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Supprimer une boîte aux lettres inactive d’une In-Place Hold

Si le blocage sur place contient un grand nombre de boîtes aux lettres source, il est possible que la boîte aux lettres inactive ne soit pas répertoriée sur la page **Sources** dans le CAE. Jusqu'à 3 000 boîtes aux lettres s'affichent sur la page **Sources** lorsque vous modifiez un blocage sur place. Si une boîte aux lettres inactive n’est pas répertoriée dans la page **Sources**, vous pouvez utiliser Exchange Online PowerShell pour la supprimer du In-Place Hold. 
  
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

- **Une boîte aux lettres inactive est un type de boîte aux lettres supprimée (récupérable).** Dans Exchange Online, une boîte aux lettres supprimée (récupérable) est une boîte aux lettres qui a été supprimée mais qui peut être récupérée pendant une période de rétention spécifique. Pour les boîtes aux lettres supprimées de manière réversible qui ne sont pas en attente, la boîte aux lettres est récupérable dans les 30 jours. Une boîte aux lettres inactive (boîte aux lettres en attente avant sa suppression) reste supprimée de manière réversible avec l’état de conservation jusqu’à ce que la conservation soit supprimée. Une fois la conservation supprimée d’une boîte aux lettres inactive, la boîte aux lettres ne sera plus inactive. Au lieu de cela, il sera supprimé de manière réversible et restera en Exchange Online pendant 183 jours à partir du jour où la conservation a été supprimée et récupérable pendant cette période. Après 183 jours, une boîte aux lettres supprimée de manière réversible est marquée pour suppression définitive et ne peut pas être récupérée.

- **Que se passe-t-il après avoir supprimé la conservation sur une boîte aux lettres inactive ?** La boîte aux lettres est traitée comme d’autres boîtes aux lettres supprimées de manière réversible et est marquée pour suppression définitive après l’expiration de la période de rétention de boîte aux lettres supprimée de manière réversible de 183 jours. Cette période de rétention commence à la date à laquelle la conservation est supprimée de la boîte aux lettres inactive. La propriété *InactiveMailboxRetireTime* est définie lorsque la boîte aux lettres passe de inactive (supprimée de manière réversible en attente) à inactive (supprimée de manière réversible sans conservation). À ce stade, la propriété *InactiveMailboxRetireTime* est définie sur la date actuelle à laquelle la transition s’est produite. Il existe un assistant qui s’exécute (appelé Assistant *MailboxLifeCycle* ) qui recherche les boîtes aux lettres dont la propriété *InactiveMailboxRetireTime* est définie. Si « InactiveMailboxRetireTime + 183 jours » est inférieur à la date actuelle, la boîte aux lettres est vidée.

- **Une boîte aux lettres inactive est-elle définitivement supprimée immédiatement après la suppression de la conservation ?** Une boîte aux lettres anciennement inactive sera disponible dans l’état supprimé de manière réversible pendant 183 jours. Après 183 jours, la boîte aux lettres est marquée pour suppression définitive.

- **Comment afficher des informations sur une boîte aux lettres inactive après la suppression de la conservation ?** Une fois qu’une conservation est supprimée et que la boîte aux lettres inactive est rétablie dans une boîte aux lettres supprimée de manière réversible, elle ne sera pas retournée à l’aide du paramètre  *InactiveMailboxOnly*  avec l’applet **de commande Get-Mailbox** . Cependant, vous pouvez afficher des informations sur la boîte aux lettres à l'aide de la commande **Get-Mailbox -SoftDeletedMailbox**. Par exemple :

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

  Dans l’exemple ci-dessus, la propriété *WhenSoftDeleted* identifie la date de suppression réversible, qui dans cet exemple est le 16 juin 2020. La propriété *WasInactiveMailbox* est répertoriée comme étant une `True` boîte aux lettres inactive. La boîte aux lettres sera définitivement supprimée 183 jours après le 30 septembre 2020.
