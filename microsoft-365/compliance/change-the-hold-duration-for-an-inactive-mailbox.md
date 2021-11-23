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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: Une fois Office 365 boîte aux lettres inactive, modifiez la durée de la conservation ou de la stratégie de rétention Office 365 affectée à la boîte aux lettres inactive.
ms.openlocfilehash: 1698a252cad4cebcb09b7c3695b2cecf3184ba1f
ms.sourcegitcommit: a15ea6bc8f60895e791a08a5a88d346c6581ea38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2021
ms.locfileid: "61144973"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) est l’état de boîte aux lettres utilisé pour conserver le courrier électronique d’un ancien employé après son départ de votre organisation. Une boîte aux lettres devient inactive lorsqu’une attente applicable lui est appliquée avant Microsoft 365'objet utilisateur est supprimé.  Les types de mise en place suivants lancent la création d’une boîte aux lettres inactive lors de la suppression d’un compte d’utilisateur :

- [Microsoft 365 stratégies et étiquettes de](retention.md) rétention avec des paramètres de rétention ou de rétention et de suppression

- Une attente associée à un [cas eDiscovery](ediscovery.md)

- [Conservation pour litige](create-a-litigation-hold.md)

- Une In-Place existante.

> [!IMPORTANT]
> Bien que l’une des conservations ci-dessus force l’inactivité d’une boîte aux lettres lors de la suppression d’un compte d’utilisateur Microsoft 365, il est vivement recommandé d’utiliser la rétention Microsoft 365 lors de la planification proactive de l’utilisation de boîtes aux lettres inactives.
>
> - Les obligations de découverte électronique sont destinées à des cas spécifiques, liés à un problème juridique. À un moment ou un autre, un dossier juridique se terminera probablement, et les conservations associées au cas seront supprimées et le cas eDiscovery sera fermé (ou supprimé). Si une mise en attente placée sur une boîte aux lettres inactive est associée à un cas eDiscovery et que la mise en attente est libérée ou si le cas eDiscovery est fermé ou supprimé, la boîte aux lettres inactive est définitivement supprimée.
>
> - In-Place les Exchange du centre d’administration sont désormais retirés. Depuis le 1er juillet 2020, les nouvelles In-Place de la Exchange Online. À compter du 1er octobre 2020, la durée de la durée des attentes in place n’a plus pu être modifiée. Toute boîte aux lettres inactive dont la In-Place est appliquée ne peut être supprimée qu’en supprimant la In-Place de la boîte aux lettres. Les boîtes aux lettres inactives existantes qui sont In-Place conservation continueront d’être conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur In-Place retrait de la découverte électronique héritée, voir Retrait des [outils eDiscovery hérités.](legacy-ediscovery-retirement.md)
>
> - [La rétention pour](create-a-litigation-hold.md) litige reste prise en charge en tant que méthode alternative pour conserver le contenu d’une boîte aux lettres et le rendre inactif après la suppression d’un compte d’utilisateur. Toutefois, en tant qu’ancienne technologie, nous vous recommandons d’utiliser Microsoft 365 rétention à la place.

Une fois inactif, le contenu de la boîte aux lettres, y compris le dossier Éléments [récupérables,](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) est conservé jusqu’à ce que la mise en attente qui a été placée sur la boîte aux lettres avant qu’elle ne soit inactive ne s’applique plus.  

Si la conservation applicable n’est pas basée sur le temps, par exemple une conservation associée à une stratégie ou une étiquette de rétention Microsoft 365 indéfinie, à un cas eDiscovery ou à une conservation pour litige (sans configuration), le contenu de la boîte aux lettres est conservé indéfiniment jusqu’à ce que la conservation soit ```LitigationHoldDuration``` supprimée.  

Toutefois, si la rétention est basée sur le temps, le contenu de la boîte aux lettres est conservé jusqu’à l’expiration de la durée de la rétention, auquel moment tous les éléments du dossier Éléments récupérables sont supprimés définitivement (purgés) de la boîte aux lettres inactive.

> [!NOTE]
> Pour les boîtes aux lettres inactives, nous vous recommandons d’utiliser un paramètre de rétention et de suppression pour Microsoft 365 stratégie ou étiquettes de rétention.  Si vous choisissez un paramètre de rétention uniquement, le dossier Éléments récupérables sera purgé à la fin de la durée de la mise en attente, mais tous les autres éléments non supprimés resteront indéfiniment dans la boîte aux lettres inactive.

Au fil de l’évolution des réglementations et des stratégies, vous devrez peut-être modifier la durée de la durée de la boîte aux lettres inactive.  Les étapes suivantes décrivent comment faire.

## <a name="connect-to-powershell"></a>Connecter à PowerShell

Comme nous l’avons mentionné précédemment, de nombreux types de mise en veille peuvent déclencher la création d’une boîte aux lettres inactive.  Pour cette raison, pour modifier la durée de la mise en attente appliquée à la boîte aux lettres inactive, vous devez d’abord identifier le type de mise en attente qui l’affecte.  Pour ce faire, vous devez utiliser Exchange Online PowerShell pour identifier les types de conservations et, si la boîte aux lettres inactive est affectée par des stratégies ou des étiquettes de rétention Microsoft 365, vous devez également utiliser le Centre de sécurité et conformité PowerShell pour identifier les stratégies spécifiques.

- Pour vous connecter à Exchange Online PowerShell ou au Centre de sécurité & conformité PowerShell, consultez l’une des rubriques suivantes :

  - [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Étant donné que différents types de conservations ou une ou plusieurs stratégies de rétention Microsoft 365 peuvent être placées sur une boîte aux lettres inactive, la première étape consiste à identifier les conservations sur une boîte aux lettres inactive.
  
Exécutez la commande suivante dans Exchange Online PowerShell pour afficher les informations de la boîte aux lettres inactive spécifique dans votre organisation.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Si vous devez identifier le type de blocage pour plusieurs boîtes aux lettres inactives et que votre organisation en possède un grand nombre, l’affichage à l’aide de PowerShell peut devenir ingérable. Dans ce cas, vous pouvez exporter toutes les informations applicables dans un fichier CSV à l’aide de la commande suivante et en modifiant les informations nécessaires ```Path``` pour votre environnement :

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Pour les besoins de cet exemple, l’exemple suivant présente les résultats pour six boîtes aux lettres inactives avec différents types de conserver possibles.

> [!NOTE]
> Plusieurs boîtes aux lettres inactives, y compris plusieurs types de boîtes aux lettres inactives, peuvent être appliquées.
  
```text
DisplayName              : Ann Beebe
Name                     : annb
DistinguishedName        : CN=annb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 664ef44e-c1a0-47b0-9553-2ecdfc6ef840
IsInactiveMailbox        : True
LitigationHoldEnabled    : True
LitigationHoldDuration   : 365.00:00:00
LitigationHoldDate       : 10/25/2021 6:54:57 PM
LitigationHoldOwner      : admin@contoso.com
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Carol Olson
Name                     : carolo
DistinguishedName        : CN=carolo,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : e646a369-00bf-43d3-837a-8eae8b301d44
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbxcdbbb86ce60342489bff371876e7f224:3}
ComplianceTagHoldApplied : False
...
DisplayName              : Megan Bowen
Name                     : meganb
DistinguishedName        : CN=meganb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 36ec77cb-c524-468a-a8e8-bfb75e01a176
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbx6fe063689d404a5bb9940eed0f0bf5d2:1}
ComplianceTagHoldApplied : True
...
DisplayName              : Mario Necaise
Name                     : marion
DistinguishedName        : CN=marion,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 0579e039-a695-40d5-8f0a-0dc04f4b4c8f
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Abraham McMahon
Name                     : abrahamm
DistinguishedName        : CN=abrahamm,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 55ad8905-4e68-4c8d-940d-e068ec6b51fc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
ComplianceTagHoldApplied : False
...
DisplayName              : Pilar Pinilla
Name                     : pilarp
DistinguishedName        : CN=pilarp,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 8d7867d6-bb6d-4cd8-a51f-09d208f97fcc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {c0ba3ce811b6432a8751430937152491}
ComplianceTagHoldApplied : False
```

Le tableau suivant identifie les six types de conserver différents qui ont été utilisés pour rendre chaque boîte aux lettres inactive par rapport à l’exemple ci-dessus.
  
|**Boîte aux lettres inactive**|**Type de conservation**|**Comment identifier la conservation dans la boîte aux lettres inactive**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Conservation pour litige  <br/> | La propriété indique que la boîte aux lettres est  `LitigationHoldEnabled`  `True` en attente pour litige. <br/><br/> En outre, la valeur est définie pour indiquer que les éléments de boîte aux lettres ne seront plus soumis à une mise en attente pour litige 365 jours après leur date de création `LitigationHoldDuration` `365.00:00:00` (envoyée/reçue).  <br/><br/> Indique la date à laquelle LitigationHold a été activé et identifie la personne qui a initié `LitigationHoldDate` la mise en attente pour `LitigationHoldOwner` litige. <br/> |
|Carol Olson  <br/> |Microsoft 365 de rétention à partir du Centre de conformité Microsoft 365 qui est appliqué à des boîtes aux lettres spécifiques  <br/> |La propriété contient le GUID de la stratégie Microsoft 365 rétention appliquée à la boîte aux lettres `InPlaceHolds` inactive. Vous pouvez savoir qu’il s’agit d’une stratégie de rétention qui s’applique à des boîtes aux lettres spécifiques, car le GUID commence par le préfixe et se termine `mbx` par un `:2` ou `:3` . <br/><br/> Pour plus d’informations, voir [Présentation du format de la valeur InPlaceHolds pour les stratégies de rétention.](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies)  <br/> |
|Megan Bowen <br/> | Microsoft 365 étiquette de rétention avec une action de rétention ou de rétention et de suppression est appliquée à au moins un élément de la boîte aux lettres  <br/> |La propriété indique qu’un élément a été étiqueté avec une étiquette de rétention `ComplianceTagHoldApplied` ou de rétention et de `True` suppression.  <br/><br/> En outre, la propriété contient le GUID de la stratégie Microsoft 365 d’étiquette de rétention appliquée à `InPlaceHolds` la boîte aux lettres inactive.  <br/><br/> Pour plus d’informations, voir Identification des boîtes aux lettres en attente car une étiquette de rétention a été appliquée à un dossier [ou à un élément](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Stratégie de rétention Microsoft 365 à l’échelle de l’Centre de conformité Microsoft 365  <br/> |La  `InPlaceHolds`  propriété est vide, est et `LitigationHoldEnabled` est `False` `ComplianceTagHoldApplied` `False` . Cela indique qu’un ou plusieurs emplacements (Exchange) sont Microsoft 365 de rétention appliquées à l’organisation dont hérite la boîte aux lettres inactive. <br/><br/> Pour plus d’informations, voir Comment vérifier qu’une stratégie de rétention à l’échelle de [l’organisation est appliquée à une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |Cas eDiscovery dans la Centre de conformité Microsoft 365  <br/> |La propriété contient le GUID de la mise en attente du cas  `InPlaceHolds`  eDiscovery qui est placé sur la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une mise en conservation de cas eDiscovery, car le GUID commence par le préfixe  `UniH`.  <br/><br/> Pour plus d’informations, [voir les holds eDiscovery.](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds) <br/> |
|Pilar Pinilla  <br/> |Conservation inaltérable  <br/> |La  `InPlaceHolds`  propriété contient le GUID de la In-Place qui est placée sur la boîte aux lettres inactive. Vous pouvez savoir qu’il s’agit d’une In-Place car le GUID ne commence pas par un préfixe.  <br/><br/> **REMARQUE**: à compter du 1er octobre 2020, la durée de la période de attente sur place ne peut plus être modifiée. Vous pouvez uniquement supprimer une In-Place qui entraîne la suppression de la boîte aux lettres inactive. <br/><br/> Pour plus d’informations, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md) <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Étape 2 : Modifier la durée de la conservation pour une boîte aux lettres inactive

Après avoir identifié le type de conservation placé sur la boîte aux lettres inactive (et s'il y a plusieurs conservations), l'étape suivante consiste à modifier la durée de la conservation.  Le processus varie en fonction du type d’attente appliqué.

- [Modifier la durée d’une stratégie Microsoft 365 rétention](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Modifier la durée d’une étiquette Microsoft 365 rétention](#change-the-duration-for-a-microsoft-365-retention-label)

- [Modifier la durée d’une attente eDiscovery](#change-the-duration-for-an-ediscovery-hold)

- [Modifier la durée d’une attente pour litige](#change-the-duration-for-a-litigation-hold)

- [Modifier la durée d’une In-Place en attente](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Modifier la durée d’une stratégie Microsoft 365 rétention

Pour modifier la durée de la conservation pour une stratégie de rétention Microsoft 365, vous devez d’abord identifier la stratégie affectant la boîte aux lettres inactive en exécutant le GUID associé à partir de la propriété de la boîte aux lettres dans le Centre de sécurité et conformité `Get-RetentionCompliancePolicy` `InPlaceHolds` PowerShell.

N’oubliez pas de supprimer le préfixe et le suffixe du GUID lors de l’exécution de cette commande.  Par exemple, à l’aide de l’exemple d’informations ci-dessus, vous devez prendre la valeur de supprimer puis obtenir un GUID de `InPlaceHolds` `mbxcdbbb86ce60342489bff371876e7f224:3` stratégie de `mbx` `:3` `cdbbb86ce60342489bff371876e7f224` .  Dans cet exemple, vous souhaitez exécuter :

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Une fois que vous connaissez le nom de la stratégie, vous pouvez simplement modifier la stratégie de rétention dans le centre Microsoft 365 conformité.  N’ignorez pas que les stratégies de rétention sont généralement appliquées à plusieurs emplacements, de sorte que la modification de la stratégie affecte tous les emplacements appliqués , inactifs et actifs, qui peuvent également inclure des emplacements autres que Exchange.  Pour plus d’informations, voir [Créer et configurer des stratégies de rétention.](create-retention-policies.md)  

> [!IMPORTANT]
> La période [](retention-preservation-lock.md) de rétention des stratégies de rétention avec verrouillage de conservation activé peut être prolongée, mais pas diminuée ou supprimée.

Si l’intention est de modifier la période de rétention pour les boîtes aux lettres inactives uniquement ou uniquement les boîtes aux lettres [inactives spécifiques,](retention.md#adaptive-or-static-policy-scopes-for-retention)vous pouvez envisager de déployer des étendues de stratégie adaptative, qui peuvent être utilisées pour cibler individuellement des boîtes aux lettres spécifiques (ou des types de boîtes aux lettres, tels que des boîtes aux lettres inactives) à l’aide des attributs et propriétés Azure AD et Exchange.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Modifier la durée d’une étiquette Microsoft 365 rétention

Comme pour les stratégies de rétention, lorsque vous modifiez la durée de conservation d’une étiquette de rétention Microsoft 365, vous devez d’abord identifier la stratégie qui publie l’étiquette affectant le contenu de la boîte aux lettres inactive en exécutant le GUID associé à partir de la propriété sur la boîte aux lettres dans le Centre de sécurité et conformité `Get-RetentionCompliancePolicy` `InPlaceHolds` PowerShell.

N’oubliez pas de supprimer le préfixe et le suffixe du GUID lors de l’exécution de cette commande.  Par exemple, à l’aide de l’exemple d’informations ci-dessus, vous devez prendre la valeur de supprimer puis obtenir un GUID de `InPlaceHolds` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` stratégie de `mbx` `:1` `6fe063689d404a5bb9940eed0f0bf5d2` .  Dans cet exemple, vous souhaitez exécuter :

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Une fois que vous avez identifié la stratégie, vous savez quelles étiquettes ont été publiées et leurs paramètres.  Étant donné que les étiquettes s’appliquent à des éléments individuels, en fonction du nombre d’étiquettes publiées avec la stratégie et de leurs paramètres, vous ne pourrez peut-être pas identifier directement l’étiquette qui affecte le contenu.  

Une méthode que vous pouvez utiliser pour identifier le contenu que chaque étiquette s’applique consiste à utiliser [la recherche de contenu.](content-search.md)  Par exemple, à l’aide des exemples d’informations ci-dessus, supposons que la stratégie publie plusieurs étiquettes, dont l’une est nommée « HR-Content ».  Avec les [autorisations correctes,](microsoft-365-compliance-center-permissions.md)une recherche de contenu peut être exécuté avec la commande [PowerShell New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch), en spécifiant l’adresse SMTP principale de la boîte aux lettres inactive, pré-pendée avec un point ( ), et le paramètre pour ignorer la `.` validation `-AllowNotFoundExchangeLocationsEnabled $true` :

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Une fois la recherche créée, vous la lancez à l’aide de la commande suivante :

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

À l’aide de cette méthode, vous pouvez ensuite identifier les étiquettes de la stratégie d’étiquette identifiée qui s’appliquent au contenu de la boîte aux lettres inactive afin de pouvoir modifier leurs périodes de rétention. Comme les étiquettes de rétention sont généralement appliquées à plusieurs emplacements, la modification d’une étiquette affecte tous les emplacements appliqués et le contenu étiqueté, ce qui peut également inclure des emplacements et du contenu autres que Exchange. Pour plus d’informations, voir [Créer des étiquettes de rétention et les appliquer dans les applications.](create-apply-retention-labels.md)

> [!NOTE]
> Tous les types d’étiquettes de rétention ne peuvent pas être modifiés.  Pour certaines étiquettes, il se peut que vous ne soyez en mesure d’augmenter le temps de rétention, et pour d’autres, que vous ne soyez pas en mesure de modifier la période de rétention du tout.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Modifier la durée d’une attente eDiscovery

Les suspensions associées aux cas eDiscovery sont des suspensions indéfinies, ce qui signifie qu’aucune durée de suspension ne peut être modifiée. Les éléments sont placés en attente indéfiniment [ou](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) jusqu’à la suppression ou la fermeture du dossier.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Modifier la durée pour une conservation pour litige

Vous devez utiliser Exchange Online PowerShell pour modifier la durée de la mise en attente pour litige qui est placée sur une boîte aux lettres inactive. Vous ne pouvez pas utiliser le CAE. Exécutez la commande suivante pour modifier la durée de la conservation. Dans cet exemple, la durée de la durée de la période de la durée de la période est illimitée :
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Les éléments de la boîte aux lettres inactive sont alors conservés indéfiniment ou jusqu'à ce que la conservation soit supprimée ou que la durée de la conservation soit remplacée par une autre valeur.
  
> [!TIP]
> La meilleure façon d'identifier une boîte aux lettres inactive est d'utiliser sa valeur **Distinguished Name** ou **Exchange GUID**. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres.

### <a name="change-the-duration-for-an-in-place-hold"></a>Modifier la durée pour une conservation inaltérable

In-Place les In-Place ont été retirées et ne peuvent plus être modifiées. Si une boîte aux lettres inactive dispose d’une In-Place en attente, vous ne pouvez pas modifier la durée de la durée de la boîte aux lettres inactive. Vous pouvez uniquement supprimer la In-Place, ce qui entraîne la suppression de la boîte aux lettres inactive. Pour plus d’informations, voir [Supprimer une boîte aux lettres inactive.](delete-an-inactive-mailbox.md#remove-in-place-holds)
  
## <a name="more-information"></a>Plus d’informations

- **Comment la durée de la conservation est-elle calculée pour un élément dans une boîte aux lettres inactive ?** La durée est calculée à partir de la date de réception ou de création d’origine d’un élément de boîte aux lettres.
    
- **Que se passe-t-il lorsque la durée de la conservation arrive à expiration ?** Lorsque la durée de la conservation arrive à expiration pour un élément de boîte aux lettres dans le dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. Si aucune durée n’est spécifiée pour la mise en attente sur la boîte aux lettres inactive, les éléments du dossier Éléments récupérables ne sont jamais purgés (sauf si la durée de la mise en attente de la boîte aux lettres inactive est modifiée). 
    
- **Une stratégie mrm Exchange est-elle toujours traitée sur les boîtes aux lettres inactives ?**  Si une stratégie de rétention MRM **a** été appliquée à une boîte aux lettres avant qu’elle ne soit inactive, toutes les stratégies de suppression (balises de rétention MRM configurées avec une action de suppression) continueront d’être traitées sur la boîte aux lettres inactive. Cela signifie que les éléments marqués avec une stratégie de suppression MRM sont déplacés vers le dossier Éléments récupérables à l’expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation. Si aucune durée de conservation n'est spécifiée pour la boîte aux lettres inactive, les éléments du dossier Éléments récupérables seront conservés indéfiniment.

    À l’inverse, toutes les stratégies d’archivage (balises de rétention MRM configurées avec une action **MoveToArchive)** incluses dans la stratégie de rétention MRM affectée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Ils seront conservés indéfiniment.
    > [!NOTE]
    > L’application d’une stratégie de rétention Exchange (fonctionnalité de gestion des enregistrements de messagerie ou MRM dans Exchange Online) ne crée pas de boîte aux lettres inactive lorsque le compte d’utilisateur est supprimé.

- **Comme pour les boîtes aux lettres normales, l’Assistant Dossier géré traite également les boîtes aux lettres inactives.** Dans Exchange Online, le MFA traite les boîtes aux lettres environ tous les sept jours. Après avoir modifié la durée de la conservation pour une boîte aux lettres inactive, vous pouvez utiliser la cmdlet **Start-ManagedFolderAssistant** pour démarrer immédiatement le traitement de la nouvelle durée de la conservation pour la boîte aux lettres inactive. Exécutez la commande suivante. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Si de nombreuses boîtes aux lettres sont placées sur une boîte aux lettres inactive, tous les GUID de mise en attente ne `InPlaceHolds` sont pas affichés.** Vous pouvez exécuter la commande suivante pour afficher les GUID de tous les utilisateurs placés `InPlaceHolds` sur une boîte aux lettres inactive.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
