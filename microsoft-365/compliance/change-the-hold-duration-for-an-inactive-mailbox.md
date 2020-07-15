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
description: Une fois qu’une boîte aux lettres Office 365 est rendue inactive, modifiez la durée de la conservation ou de la stratégie de rétention d’Office 365 affectée à la boîte aux lettres inactive.
ms.openlocfilehash: 675e6eb36f762a50c3caafce07d09fda9ba9d98e
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45126375"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une boîte aux lettres inactive est utilisée pour conserver l'e-mail d'un ancien employé une fois qu'il quitte votre organisation. Une boîte aux lettres devient inactive lorsqu’une suspension pour litige, une conservation inaltérable, une stratégie de rétention Microsoft 365 ou une conservation associée à un cas eDiscovery est placée sur la boîte aux lettres et le compte d’utilisateur correspondant est supprimé. Le contenu d'une boîte aux lettres inactive est conservé pendant la durée de la conservation appliquée à la boîte aux lettres avant qu'elle ne soit définie comme inactive. La durée de la conservation définit la durée de conservation des éléments dans le dossier Éléments récupérables. Lorsque la durée de conservation expire pour un élément du dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. Une fois qu’une boîte aux lettres est devenue inactive, vous pouvez modifier la durée de la conservation ou de la stratégie de rétention 365 affectée à la boîte aux lettres inactive.
  
> [!IMPORTANT]
> À mesure que nous continuons à investir de différentes manières pour conserver le contenu de la boîte aux lettres, nous annonçaons le retrait des conservations inaltérables dans le centre d’administration Exchange. Cela signifie que vous devez utiliser des conservations pour litige et des stratégies de rétention Microsoft 365 pour créer une boîte aux lettres inactive. À partir du 1er avril 2020 vous ne pourrez pas créer de nouvelles conservations inaltérables dans Exchange Online. Toutefois, vous pourrez toujours modifier la durée de conservation d’un blocage sur place placé sur une boîte aux lettres inactive. Toutefois, à partir du 1er juillet 2020, vous ne pourrez pas modifier la durée de la conservation. Vous ne pourrez supprimer une boîte aux lettres inactive qu’en supprimant la conservation inaltérable. Les boîtes aux lettres inactives existantes qui sont en conservation inaltérable resteront conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur le retrait des conservations inaltérables, consultez la rubrique [déclassement des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
  
## <a name="connect-to-powershell"></a>Se connecter à PowerShell

- You have to use Exchange Online PowerShell to change the hold duration for a Litigation Hold on an inactive mailbox. You can't use the Exchange admin center (EAC). But you can use Exchange Online PowerShell or the EAC to change the hold duration for an In-Place Hold. Vous pouvez utiliser le centre de sécurité et de conformité ou le centre de sécurité & conformité PowerShell pour modifier la durée de la conservation pour une stratégie de rétention 365 de Microsoft.
    
- Pour vous connecter à Exchange Online PowerShell ou Security & Compliance Center PowerShell, consultez l’une des rubriques suivantes :
    
  - [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554)
    
  - [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](https://go.microsoft.com/fwlink/?linkid=799771)
    
- Les suspensions associées à des cas eDiscovery sont des suspensions infinies, ce qui signifie qu’il n’est pas possible de modifier la durée de la conservation. Les éléments sont mis en conservation indéfiniment ou jusqu'à ce que la conservation et la boîte aux lettres inactive soient supprimées.
    
- Pour plus d’informations sur les boîtes aux lettres inactives, consultez la rubrique [inactive mailboxes dans Microsoft 365](inactive-mailboxes-in-office-365.md).
    
## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Étant donné que différents types de conservation ou une ou plusieurs stratégies de rétention de Microsoft 365 peuvent être placées sur une boîte aux lettres inactive, la première étape consiste à identifier les suspensions sur une boîte aux lettres inactive.
  
Exécutez la commande suivante dans Exchange Online PowerShell pour afficher les informations de conservation pour toutes les boîtes aux lettres inactives dans votre organisation.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,InPlaceHolds
```

La valeur de **True** pour la propriété **LitigationHoldEnabled** indique que la boîte aux lettres inactive est en conservation pour litige. Si une conservation inaltérable, un blocage eDiscovery ou une stratégie de rétention Microsoft 365 est placée sur une boîte aux lettres inactive, un GUID pour la stratégie de conservation ou de rétention est affiché comme valeur de la propriété **InPlaceHolds** . Par exemple, le code suivant montre les résultats de cinq boîtes aux lettres inactives. 
  
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
|Pilar Pinilla  <br/> |Conservation inaltérable  <br/> |The  *InPlaceHolds*  property contains the GUID of the In-Place Hold that's placed on the inactive mailbox. You can tell this is an In-Place Hold because the ID doesn't start with a prefix.  <br/> Vous pouvez utiliser la commande  `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` dans Exchange Online PowerShell pour obtenir des informations sur la conservation inaltérable dans la boîte aux lettres inactive.  <br/> |
|Mario Necaise  <br/> |Stratégie de rétention Microsoft 365 à l’échelle de l’organisation dans le centre de sécurité & conformité  <br/> |La propriété  *InPlaceHolds*  est vide. Cela indique qu’une ou plusieurs stratégies de rétention Microsoft 365 à l’échelle de l’organisation ou (Exchange) sont appliquées à la boîte aux lettres inactive. Dans ce cas, vous pouvez exécuter la `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` commande dans Exchange Online PowerShell pour obtenir la liste des GUID pour les stratégies de rétention Microsoft 365 à l’échelle de l’organisation. Le GUID des stratégies de rétention à l’échelle de l’organisation appliquées aux boîtes aux lettres Exchange commence par le `mbx` préfixe ; par exemple, `mbxa3056bb15562480fadb46ce523ff7b02` .  <br/> <br/>Pour identifier la stratégie de rétention de Microsoft 365 qui est appliquée à la boîte aux lettres inactive, exécutez la commande suivante dans sécurité & Centre de conformité PowerShell.  <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>
|Carol Olson  <br/> |Stratégie de rétention de Microsoft 365 dans le centre de sécurité & conformité appliquée à des boîtes aux lettres spécifiques  <br/> |La propriété *InPlaceHolds* contient le GUID de la stratégie de rétention Microsoft 365 qui est appliquée à la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une stratégie de rétention qui est appliquée à des boîtes aux lettres spécifiques, car le GUID commence par le préfixe  `mbx`. Si le GUID de la stratégie de rétention appliquée à la boîte aux lettres inactive a démarré avec le `skp` préfixe, cela signifie que la stratégie de rétention est appliquée aux conversations Skype entreprise.  <br/><br/> Pour identifier la stratégie de rétention de Microsoft 365 qui est appliquée à la boîte aux lettres inactive, exécutez la commande suivante dans sécurité & Centre de conformité PowerShell.<br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name` <br/><br/>N'oubliez pas de supprimer le préfixe  `mbx` ou  `skp` lorsque vous exécutez cette commande.  <br/> |
|Abraham McMahon  <br/> |conservation des cas eDiscovery dans le centre de sécurité & conformité  <br/> |The  *InPlaceHolds*  property contains the GUID of the eDiscovery case hold that's placed on the inactive mailbox. You can tell this is an eDiscovery case hold because the GUID starts with the  `UniH` prefix.  <br/> Vous pouvez utiliser l' `Get-CaseHoldPolicy` applet de commande dans Security & Compliance Center PowerShell pour obtenir des informations sur le cas eDiscovery auquel est associée la conservation de la boîte aux lettres inactive. For example, you can run the command  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` to display the name of the case hold that's on the inactive mailbox. Be sure to remove the  `UniH` lorsque vous exécutez cette commande.  <br/><br/> Pour identifier le cas eDiscovery associé à la conservation dans la boîte aux lettres inactive, exécutez les commandes suivantes.  <br/><br/> `$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/> `Get-ComplianceCase $CaseHold.CaseId | FL Name`<br/><br/><br/> **Remarque :** Il n’est pas recommandé d’utiliser des suspensions eDiscovery pour les boîtes aux lettres inactives. En effet, les cas eDiscovery sont destinés à cas spécifiques, limités dans le temps et liés à un problème juridique. À un moment ou un autre, un dossier juridique se terminera probablement, et les conservations associées au cas seront supprimées et le cas eDiscovery sera fermé (ou supprimé). En fait, si une conservation figurant dans une boîte aux lettres inactive est associée à un cas eDiscovery et que la conservation est libérée, ou le cas eDiscovery est fermé ou supprimé, la boîte aux lettres inactive est définitivement supprimée. 

Pour plus d’informations sur les stratégies de rétention de Microsoft 365, voir [en savoir plus sur les stratégies de rétention et les étiquettes de conservation](retention.md)
  
## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Étape 2 : Modifier la durée de la conservation pour une boîte aux lettres inactive

Après avoir identifié le type de conservation placé sur la boîte aux lettres inactive (et s'il y a plusieurs conservations), l'étape suivante consiste à modifier la durée de la conservation. 
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Modifier la durée pour une conservation pour litige

Here's how to use Exchange Online PowerShell to change the hold duration for a Litigation Hold that is placed on an inactive mailbox. You can't use the EAC. Run the following command to change the hold duration. In this example, the hold duration is changed to an unlimited period of time.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Les éléments de la boîte aux lettres inactive sont alors conservés indéfiniment ou jusqu'à ce que la conservation soit supprimée ou que la durée de la conservation soit remplacée par une autre valeur.
  
> [!TIP]
> The best way to identify an inactive mailbox is by using its **Distinguished Name** or **Exchange GUID** value. Using one of these values helps prevent accidentally specifying the wrong mailbox. 
  
### <a name="change-the-duration-for-an-in-place-hold"></a>Modifier la durée pour une conservation inaltérable

 Vous pouvez utiliser le CAE ou Exchange Online PowerShell pour modifier la durée d'une conservation inaltérable. 
  
#### <a name="use-the-eac-to-change-the-hold-duration"></a>Utiliser le CAE pour modifier la durée de la conservation

1. Si vous connaissez le nom de la conservation inaltérable que vous souhaitez modifier, passez à l'étape suivante. Sinon, exécutez la commande suivante pour obtenir le nom de la conservation inaltérable placée sur la boîte aux lettres inactive. Utilisez le GUID de conservation inaltérable que vous avez obtenu à l' [étape 1](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID> | FL Name
    ```

2. In the EAC, go to **Compliance management** \> **In-Place eDiscovery &amp; Hold**.
    
3. Sélectionnez la conservation inaltérable à modifier, puis sélectionnez **modifier** l' ![ icône modifier ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) .
    
4. Sur la page Propriétés **de la &amp; découverte électronique** inaltérable, sélectionnez **conservation**inaltérable. 
    
5. Effectuez l'une des opérations suivantes sur la durée de la conservation actuelle :
    
    1. Sélectionnez **bloquer indéfiniment** pour conserver les éléments pendant une période illimitée. 
    
    2. Sélectionnez **spécifier le nombre de jours de conservation des éléments par rapport à leur date de réception** pour conserver les éléments d’une période donnée. Type the number of days that you want to hold items for. 
    
    ![Capture d'écran de la modification de la durée d'une conservation inaltérable](../media/cfcfd92a-9d65-40c0-90ef-ab72697b0166.png)
  
6. Sélectionnez **Enregistrer**.
    
#### <a name="use-exchange-online-powershell-to-change-the-hold-duration"></a>Utiliser Exchange Online PowerShell pour modifier la durée de conservation

1. Si vous connaissez le nom de la conservation inaltérable que vous souhaitez modifier, passez à l’étape suivante. Sinon, exécutez la commande suivante pour obtenir le nom de la conservation inaltérable placée sur la boîte aux lettres inactive. Utilisez le GUID de conservation inaltérable que vous avez obtenu à l' [étape 1](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID> | FL Name
    ```

2. Exécutez la commande suivante pour modifier la durée du blocage. Dans cet exemple, la durée de la conservation est passée à 2 555 jours (sept ans environ). 
    
    ```powershell
    Set-MailboxSearch <identity of In-Place Hold> -ItemHoldPeriod 2555
    ```

     Pour modifier la durée de la conservation sur une période illimitée, utilisez  _-ItemHoldPeriod unlimited_.
  
## <a name="more-information"></a>Plus d’informations

- **How is the hold duration calculated for an item in an inactive mailbox?** The duration is calculated from the original date a mailbox item was received or created. 
    
- **Que se passe-t-il lorsque la durée de la conservation arrive à expiration ?** Lorsque la durée de la conservation arrive à expiration pour un élément de boîte aux lettres dans le dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. Si aucune durée n’est spécifiée pour la suspension placée sur la boîte aux lettres inactive, les éléments du dossier éléments récupérables ne sont jamais purgés (sauf si la durée de la conservation de la boîte aux lettres inactive est modifiée). 
    
- **Is an Exchange retention policy still processed on inactive mailboxes?** If an Exchange retention policy (the messaging records management, or MRM, feature in Exchange Online) was applied to a mailbox when it was made inactive, the deletion policies (which are retention tags configured with a **Delete** retention action) will continue to be processed on the inactive mailbox. That means items that are tagged with a deletion policy are moved to the Recoverable Items folder when the retention period expires. Those items are then purged from the inactive mailbox when the hold duration for an item expires. 
    
    Conversely, any archive policies (which are retention tags configured with a **MoveToArchive** retention action) that are included in the retention policy assigned to an inactive mailbox are ignored. That means items in an inactive mailbox that are tagged with an archive policy remain in the primary mailbox when the retention period expires. They're not moved to the archive mailbox or to the Recoverable Items folder in the archive mailbox. Because a user can't sign in to an inactive mailbox, there's no reason to consume datacenter resources to process archive policies. 
    
- **To check the new hold duration, run one of the following commands.** The first command is for Litigation Hold; the second is for In-Place Hold. 

    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | FL LitigationHoldDuration
    ```

    ```powershell
    Get-MailboxSearch <identity of In-Place Hold> | FL ItemHoldPeriod
    ```

- **Comme les boîtes aux lettres ordinaires, l'Assistant Dossier géré traite également les boîtes aux lettres inactives.** Dans Exchange Online, le MFA traite les boîtes aux lettres approximativement une fois tous les sept jours. Après avoir modifié la durée de la conservation pour une boîte aux lettres inactive, vous pouvez utiliser la cmdlet **Start-ManagedFolderAssistant** pour démarrer immédiatement le traitement de la nouvelle durée de la conservation pour la boîte aux lettres inactive. Exécutez la commande suivante. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Si de nombreuses suspensions sont placées sur une boîte aux lettres inactive, tous les GUID de conservation ne seront pas affichés.** Vous pouvez exécuter la commande suivante pour afficher les GUID pour toutes les conservations (sauf pour les conservations pour litige) qui figurent dans une boîte aux lettres inactive. 
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
