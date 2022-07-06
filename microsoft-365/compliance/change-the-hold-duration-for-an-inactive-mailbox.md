---
title: Modifier la durée de la conservation pour une boîte aux lettres inactive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
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
description: Une fois qu’une boîte aux lettres Office 365 est inactive, modifiez la durée de conservation ou Office 365 stratégie de rétention affectée à la boîte aux lettres inactive.
ms.openlocfilehash: 6fdb3993fd6b6503ab672a0c6465a394f3824c4b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628878"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Modifier la durée de la conservation pour une boîte aux lettres inactive

Une [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md) est l’état de boîte aux lettres qui est utilisé pour conserver l’adresse e-mail d’un ancien employé après qu’il a quitté votre organisation. Une boîte aux lettres devient inactive lorsqu’une conservation applicable lui est appliquée avant la suppression de l’objet utilisateur Microsoft 365.  Les types de conservation suivants lancent la création d’une boîte aux lettres inactive lors de la suppression du compte d’utilisateur :

- [Stratégies et étiquettes de rétention Microsoft 365 avec des](retention.md) paramètres de conservation, de conservation et de suppression

- Conservation associée à un cas [eDiscovery](ediscovery.md)

- [Conservation des litiges](create-a-litigation-hold.md)

- Une In-Place hold existante.

> [!IMPORTANT]
> Bien que l’une des conservations ci-dessus force une boîte aux lettres à devenir inactive lors de la suppression du compte d’utilisateur Microsoft 365, il est vivement recommandé d’utiliser la rétention De Microsoft 365 lorsque vous planifiez de manière proactive d’utiliser des boîtes aux lettres inactives.
>
> - Les conservations eDiscovery sont destinées à des cas spécifiques et limités dans le temps liés à une question juridique. À un moment ou un autre, un dossier juridique se terminera probablement, et les conservations associées au cas seront supprimées et le cas eDiscovery sera fermé (ou supprimé). Si une conservation placée sur une boîte aux lettres inactive est associée à un cas eDiscovery et que la conservation est libérée ou que le cas eDiscovery est fermé ou supprimé, la boîte aux lettres inactive est définitivement supprimée.
>
> - In-Place conservations dans le Centre d’administration Exchange sont désormais mises hors service. Depuis le 1er juillet 2020, les nouvelles In-Place conservations n’ont pas pu être créées dans Exchange Online. À compter du 1er octobre 2020, la durée de conservation des conservations en place ne pouvait plus être modifiée. Toute boîte aux lettres inactive dont la conservation In-Place est appliquée ne peut être supprimée qu’en supprimant le In-Place Hold. Les boîtes aux lettres inactives existantes qui sont en attente In-Place continueront d’être conservées jusqu’à ce que la conservation soit supprimée. Pour plus d’informations sur In-Place Mise hors service, consultez [La mise hors service des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
>
> - [La conservation des litiges](create-a-litigation-hold.md) reste prise en charge comme méthode alternative pour conserver le contenu dans une boîte aux lettres et le rendre inactif après la suppression d’un compte d’utilisateur. Toutefois, en tant que technologie plus ancienne, nous vous recommandons d’utiliser la rétention Microsoft 365 à la place.

Une fois inactif, le contenu de la boîte aux lettres, y compris le [dossier Éléments récupérables](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) , est conservé jusqu’à ce que la conservation qui a été placée sur la boîte aux lettres avant d’être rendue inactive ne s’applique plus.  

Si la conservation applicable n’est pas basée sur le temps, telle qu’une conservation associée à une stratégie ou une étiquette de rétention Microsoft 365 indéfinie, un cas eDiscovery ou une ```LitigationHoldDuration``` conservation du litige (sans configuration), le contenu de la boîte aux lettres est conservé indéfiniment jusqu’à ce que la conservation soit supprimée.  

Toutefois, si la conservation est limitée dans le temps, le contenu de la boîte aux lettres est conservé jusqu’à l’expiration de la durée de conservation. À ce stade, tous les éléments du dossier Éléments récupérables sont définitivement supprimés (purgés) de la boîte aux lettres inactive.

> [!NOTE]
> Pour les boîtes aux lettres inactives, nous vous recommandons d’utiliser un paramètre de conservation et de suppression pour votre stratégie ou étiquettes de rétention Microsoft 365.  Si vous choisissez un paramètre conserver uniquement, le dossier Éléments récupérables est vidé à la fin de la durée de conservation, mais tous les autres éléments non supprimés restent indéfiniment dans la boîte aux lettres inactive.

À mesure que les réglementations et les stratégies évoluent, il peut arriver que vous deviez modifier la durée de la conservation affectée à la boîte aux lettres inactive.  Les étapes suivantes décrivent comment procéder.

## <a name="connect-to-powershell"></a>Se connecter à PowerShell

Comme nous l’avons mentionné précédemment, de nombreux types de conservations différents peuvent déclencher la création d’une boîte aux lettres inactive.  Pour cette raison, pour modifier la durée de conservation appliquée à la boîte aux lettres inactive, vous devez d’abord identifier le type de conservation qui l’affecte.  Pour ce faire, vous devez utiliser Exchange Online PowerShell pour identifier les types de conservations et, si la boîte aux lettres inactive est affectée par des stratégies ou des étiquettes de rétention Microsoft 365, vous devez également utiliser Security & Compliance PowerShell pour identifier les stratégies spécifiques.

- Pour vous connecter à Exchange Online PowerShell ou Security & Compliance PowerShell, consultez l’une des rubriques suivantes :

  - [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Se connecter à la sécurité et conformité PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>Étape 1 : Identifier les blocages sur une boîte aux lettres inactive

Étant donné que différents types de conservations ou une ou plusieurs stratégies de rétention Microsoft 365 peuvent être placés sur une boîte aux lettres inactive, la première étape consiste à identifier les conservations sur une boîte aux lettres inactive.
  
Exécutez la commande suivante dans Exchange Online PowerShell pour afficher les informations de conservation d’une boîte aux lettres inactive spécifique dans votre organisation.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Si vous devez identifier le type de conservation pour plusieurs boîtes aux lettres inactives et que votre organisation en a un grand nombre, il peut devenir impossible de les afficher à l’aide de PowerShell. Dans ce cas, vous pouvez exporter toutes les informations applicables vers un fichier CSV à l’aide de la commande suivante et en modifiant les ```Path``` informations nécessaires pour votre environnement :

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Pour les besoins de cet exemple, l’exemple suivant montre les résultats de six boîtes aux lettres inactives avec différents types de conservation possibles.

> [!NOTE]
> Plusieurs conservations, y compris plusieurs types de conservations, peuvent s’appliquer à une seule boîte aux lettres inactive.
  
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

Le tableau suivant identifie les six types de conservation différents qui ont été utilisés pour rendre chaque boîte aux lettres inactive dans l’exemple ci-dessus.
  
|**Boîte aux lettres inactive**|**Type de conservation**|**Comment identifier la conservation dans la boîte aux lettres inactive**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Conservation pour litige  <br/> | La  `LitigationHoldEnabled`  propriété est définie sur  `True` indiquant que la boîte aux lettres est en attente de litige. <br/><br/> En outre, la `LitigationHoldDuration` valeur est définie pour `365.00:00:00` indiquer que les éléments de boîte aux lettres ne seront plus soumis à une suspension de litige 365 jours après leur date de création (envoyée/reçue).  <br/><br/> Indique `LitigationHoldDate` la date à laquelle LitigationHold a été activé et `LitigationHoldOwner` identifie la personne à l’origine de la suspension du litige. <br/> |
|Carol Olson  <br/> |Stratégie de rétention Microsoft 365 à partir de la portail de conformité Microsoft Purview appliquée à des boîtes aux lettres spécifiques  <br/> |La  `InPlaceHolds`  propriété contient le GUID de la stratégie de rétention Microsoft 365 appliquée à la boîte aux lettres inactive. Vous pouvez indiquer qu’il s’agit d’une stratégie de rétention qui s’applique à des boîtes aux lettres spécifiques, car le GUID commence par le `mbx` préfixe et se termine par un `:2` ou `:3`. <br/><br/> Pour plus d’informations, consultez [Présentation du format de la valeur InPlaceHolds pour les stratégies de rétention](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | L’étiquette de rétention Microsoft 365 avec une action de conservation ou de conservation et de suppression est appliquée à au moins un élément de la boîte aux lettres  <br/> |La `ComplianceTagHoldApplied` propriété indique qu’un `True` élément a été étiqueté avec une étiquette de conservation, de conservation et de suppression.  <br/><br/> En outre, la `InPlaceHolds` propriété contient le GUID de la stratégie d’étiquette de rétention Microsoft 365 appliquée à la boîte aux lettres inactive.  <br/><br/> Pour plus d’informations, consultez [Identifier les boîtes aux lettres en attente, car une étiquette de rétention a été appliquée à un dossier ou à un élément](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Stratégie de rétention Microsoft 365 à l’échelle de l’organisation à partir du portail de conformité Microsoft Purview <br/> |La  `InPlaceHolds`  propriété est vide, `LitigationHoldEnabled` est `False` et `ComplianceTagHoldApplied` est `False`. Cela indique qu’une ou plusieurs stratégies de rétention Microsoft 365 (Exchange) entières appliquées à l’organisation dont hérite la boîte aux lettres inactive. <br/><br/> Pour plus d’informations, consultez [Comment vérifier qu’une stratégie de rétention à l’échelle de l’organisation est appliquée à une boîte aux lettres](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |Conservation de la casse eDiscovery dans le portail de conformité Microsoft Purview  <br/> |La  `InPlaceHolds`  propriété contient le GUID de la conservation de la casse eDiscovery qui est placée sur la boîte aux lettres inactive. Vous pouvez déterminer qu'il s'agit d'une mise en conservation de cas eDiscovery, car le GUID commence par le préfixe  `UniH`.  <br/><br/> Pour plus d’informations, consultez les [conservations eDiscovery](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |Conservation inaltérable  <br/> |La  `InPlaceHolds`  propriété contient le GUID du In-Place Hold placé sur la boîte aux lettres inactive. Vous pouvez indiquer qu’il s’agit d’une In-Place en attente, car le GUID ne commence pas par un préfixe.  <br/><br/> **REMARQUE** : À compter du 1er octobre 2020, la durée de conservation des conservations sur place ne peut plus être modifiée. Vous ne pouvez supprimer qu’une In-Place Conservation, ce qui entraîne la suppression de la boîte aux lettres inactive. <br/><br/> Pour plus d’informations, consultez [Retrait des outils eDiscovery hérités](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>Étape 2 : Modifier la durée de la conservation pour une boîte aux lettres inactive

Après avoir identifié le type de conservation placé sur la boîte aux lettres inactive (et s'il y a plusieurs conservations), l'étape suivante consiste à modifier la durée de la conservation.  Le processus varie en fonction du type de conservation appliqué.

- [Modifier la durée d’une stratégie de rétention Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Modifier la durée d’une étiquette de rétention Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-label)

- [Modifier la durée d’une conservation eDiscovery](#change-the-duration-for-an-ediscovery-hold)

- [Modifier la durée d’une conservation pour litige](#change-the-duration-for-a-litigation-hold)

- [Modifier la durée d’une conservation In-Place](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Modifier la durée d’une stratégie de rétention Microsoft 365

Pour modifier la durée de conservation d’une stratégie de rétention Microsoft 365, vous devez d’abord identifier la stratégie affectant la boîte aux lettres inactive en exécutant `Get-RetentionCompliancePolicy` le GUID associé à partir de la `InPlaceHolds` propriété sur la boîte aux lettres dans Security & Compliance PowerShell.

Veillez à supprimer le préfixe et le suffixe du GUID lors de l’exécution de cette commande.  Par exemple, à l’aide des exemples d’informations ci-dessus, vous prendriez la `InPlaceHolds` valeur de `mbxcdbbb86ce60342489bff371876e7f224:3` supprimer `mbx` puis `:3` de générer un GUID de stratégie de `cdbbb86ce60342489bff371876e7f224`.  Dans cet exemple, vous souhaitez exécuter :

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

Une fois que vous connaissez le nom de la stratégie, vous pouvez simplement modifier la stratégie de rétention dans le portail de conformité Microsoft Purview.  N’oubliez pas que les stratégies de rétention sont généralement appliquées à plusieurs emplacements. Par conséquent, la modification de la stratégie affecte tous les emplacements appliqués , à la fois inactifs et actifs, qui peuvent également inclure des emplacements autres qu’Exchange.  Pour plus d’informations, consultez [Créer et configurer des stratégies de rétention](create-retention-policies.md).  

> [!IMPORTANT]
> Les stratégies de [rétention avec verrouillage de conservation](retention-preservation-lock.md) activé peuvent avoir la période de rétention prolongée, mais pas diminuée ou supprimée.

Si l’intention est de modifier la période de rétention uniquement pour les boîtes aux lettres inactives, ou uniquement les boîtes aux lettres inactives spécifiques, vous pouvez envisager de déployer [des étendues de stratégie adaptative](retention.md#adaptive-or-static-policy-scopes-for-retention), qui peuvent être utilisées pour cibler individuellement des boîtes aux lettres spécifiques - ou des types de boîtes aux lettres, telles que des boîtes aux lettres inactives - à l’aide d’attributs et de propriétés Azure AD et Exchange.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Modifier la durée d’une étiquette de rétention Microsoft 365

Comme pour les stratégies de rétention, lors de la modification de la durée de conservation d’une étiquette de rétention Microsoft 365, vous devez d’abord identifier la stratégie qui publie l’étiquette affectant le contenu dans la boîte aux lettres inactive en exécutant `Get-RetentionCompliancePolicy` le GUID associé à partir de la `InPlaceHolds` propriété sur la boîte aux lettres dans Security & Compliance PowerShell.

Veillez à supprimer le préfixe et le suffixe du GUID lors de l’exécution de cette commande.  Par exemple, à l’aide des exemples d’informations ci-dessus, vous prendriez la `InPlaceHolds` valeur de `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` supprimer `mbx` puis `:1` de générer un GUID de stratégie de `6fe063689d404a5bb9940eed0f0bf5d2`.  Dans cet exemple, vous souhaitez exécuter :

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

Une fois que vous avez identifié la stratégie, vous saurez quelles étiquettes ont été publiées et leurs paramètres.  Étant donné que les étiquettes s’appliquent à des éléments individuels, en fonction du nombre d’étiquettes publiées avec la stratégie et de leurs paramètres, il se peut que vous ne puissiez pas identifier directement l’étiquette qui affecte le contenu.  

Une méthode que vous pouvez utiliser pour identifier le contenu auquel chaque étiquette s’applique consiste à utiliser [la recherche de contenu](content-search.md).  Par exemple, à l’aide des exemples d’informations ci-dessus, supposons que la stratégie publie plusieurs étiquettes, dont l’une est nommée « HR-Content ».  Avec [les autorisations appropriées](microsoft-365-compliance-center-permissions.md), une recherche de contenu peut être exécutée avec la [commande PowerShell New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch), en spécifiant l’adresse SMTP principale de la boîte aux lettres inactive, préconfigrée avec un point (`.`) et le paramètre permettant d’ignorer la `-AllowNotFoundExchangeLocationsEnabled $true` validation :

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Une fois la recherche créée, vous démarrez la recherche à l’aide de la commande suivante :

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

À l’aide de cette méthode, vous pouvez ensuite identifier les étiquettes de la stratégie d’étiquette identifiée qui s’appliquent au contenu de la boîte aux lettres inactive afin de pouvoir modifier leurs périodes de rétention. N’oubliez pas que les étiquettes de rétention sont généralement appliquées à plusieurs emplacements. Par conséquent, la modification d’une étiquette affecte tous les emplacements appliqués et le contenu étiqueté, qui peut également inclure des emplacements et du contenu autres qu’Exchange. Pour plus d’informations, consultez [Publier les étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md).

> [!NOTE]
> Tous les types d’étiquettes de rétention ne peuvent pas être modifiés.  Pour certaines étiquettes, vous pouvez uniquement augmenter le temps de rétention, et pour d’autres, vous ne pouvez pas du tout modifier la période de rétention.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>Modifier la durée d’une conservation eDiscovery

Les conservations associées aux cas eDiscovery sont des conservations indéfinies, ce qui signifie qu’aucune durée de conservation ne peut être modifiée. Les éléments sont conservés indéfiniment ou jusqu’à ce que la [conservation soit supprimée](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) ou que la casse soit fermée.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Modifier la durée pour une conservation pour litige

Vous devez utiliser Exchange Online PowerShell pour modifier la durée de conservation d’une conservation pour litige placée sur une boîte aux lettres inactive. Vous ne pouvez pas utiliser le CAE. Exécutez la commande suivante pour modifier la durée de la conservation. Dans cet exemple, la durée de conservation est remplacée par une durée illimitée :
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Les éléments de la boîte aux lettres inactive sont alors conservés indéfiniment ou jusqu'à ce que la conservation soit supprimée ou que la durée de la conservation soit remplacée par une autre valeur.
  
> [!TIP]
> La meilleure façon d'identifier une boîte aux lettres inactive est d'utiliser sa valeur **Distinguished Name** ou **Exchange GUID**. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres.

### <a name="change-the-duration-for-an-in-place-hold"></a>Modifier la durée pour une conservation inaltérable

In-Place les conservations ont été mises hors service et ne peuvent plus être modifiées. Si une boîte aux lettres inactive a une In-Place la conservation est appliquée, vous ne pouvez pas modifier la durée de conservation. Vous pouvez uniquement supprimer la In-Place Hold, ce qui entraîne la suppression de la boîte aux lettres inactive. Pour plus d’informations, consultez [Supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Plus d’informations

- **Comment la durée de la conservation est-elle calculée pour un élément dans une boîte aux lettres inactive ?** La durée est calculée à partir de la date de réception ou de création d’origine d’un élément de boîte aux lettres.
    
- **Que se passe-t-il lorsque la durée de la conservation arrive à expiration ?** Lorsque la durée de la conservation arrive à expiration pour un élément de boîte aux lettres dans le dossier Éléments récupérables, l'élément est supprimé définitivement (purgé) de la boîte aux lettres inactive. S’il n’existe aucune durée spécifiée pour la conservation placée sur la boîte aux lettres inactive, les éléments du dossier Éléments récupérables ne sont jamais purgés (sauf si la durée de conservation de la boîte aux lettres inactive est modifiée). 
    
- **Une stratégie MrM Exchange est-elle toujours traitée sur les boîtes aux lettres inactives ?**  Si une stratégie de rétention MRM a été appliquée à une boîte aux lettres avant qu’elle ne soit inactive, toutes les stratégies de suppression (balises de rétention MRM configurées avec une action **Supprimer** ) continueront d’être traitées sur la boîte aux lettres inactive. Cela signifie que les éléments marqués avec une stratégie de suppression MRM seront déplacés vers le dossier Éléments récupérables à l’expiration de la période de rétention. Ces éléments sont supprimés définitivement de la boîte aux lettres inactive à l'expiration de la durée de la conservation. Si aucune durée de conservation n'est spécifiée pour la boîte aux lettres inactive, les éléments du dossier Éléments récupérables seront conservés indéfiniment.

    À l’inverse, toutes les stratégies d’archivage (balises de rétention MRM configurées avec une action **MoveToArchive** ) incluses dans la stratégie de rétention MRM affectée à une boîte aux lettres inactive sont ignorées. Cela signifie que les éléments dans une boîte aux lettres inactive qui sont marqués avec une stratégie d'archivage restent dans la boîte aux lettres principale à l'expiration de la période de rétention. Ils ne sont pas déplacés vers la boîte aux lettres d'archivage ni vers le dossier Éléments récupérables dans la boîte aux lettres d'archivage. Ils seront conservés indéfiniment.
    > [!NOTE]
    > L’application d’une stratégie de rétention Exchange (fonctionnalité gestion des enregistrements de messagerie ou MRM dans Exchange Online) ne crée pas de boîte aux lettres inactive lorsque le compte d’utilisateur est supprimé.

- **Comme pour les boîtes aux lettres normales, l’Assistant Dossier géré (MFA) traite également les boîtes aux lettres inactives.** Dans Exchange Online, l’authentification multifacteur traite les boîtes aux lettres environ une fois tous les sept jours. Après avoir modifié la durée de la conservation pour une boîte aux lettres inactive, vous pouvez utiliser la cmdlet **Start-ManagedFolderAssistant** pour démarrer immédiatement le traitement de la nouvelle durée de la conservation pour la boîte aux lettres inactive. Exécutez la commande suivante. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Si un grand nombre `InPlaceHolds` d’entre eux sont placés sur une boîte aux lettres inactive, tous les GUID de conservation ne s’affichent pas.** Vous pouvez exécuter la commande suivante pour afficher les GUID de tous les `InPlaceHolds` éléments placés sur une boîte aux lettres inactive.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
