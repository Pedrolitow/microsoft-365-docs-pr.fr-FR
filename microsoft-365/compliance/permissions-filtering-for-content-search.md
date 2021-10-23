---
title: Configurer le filtrage des autorisations pour eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: Utilisez le filtrage des autorisations de recherche pour autoriser les gestionnaires eDiscovery à rechercher uniquement un sous-ensemble de boîtes aux lettres et de sites dans votre organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 190ed836c30dbb08015c662f948d6b3dc9310c94
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60553375"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>Configurer le filtrage des autorisations pour eDiscovery

Vous pouvez utiliser le filtrage des autorisations de recherche pour laisser un gestionnaire eDiscovery rechercher uniquement un sous-ensemble de boîtes aux lettres et de sites dans votre organisation. Vous pouvez également utiliser le filtrage des autorisations pour permettre à ce gestionnaire de rechercher uniquement le contenu de boîte aux lettres ou de site qui répond à des critères de recherche spécifiques. Par exemple, vous voudrez peut-être permettre à un gestionnaire de découverte électronique de rechercher uniquement les boîtes aux lettres des utilisateurs dans un lieu ou un service spécifique. Pour ce faire, vous créez un filtre qui utilise un filtre de destinataires pris en charge pour limiter les boîtes aux lettres qu’un utilisateur ou un groupe d’utilisateurs spécifique peut rechercher. Vous pouvez également créer un filtre qui spécifie le contenu de boîte aux lettres qu’un utilisateur peut rechercher. Pour cela, vous devez créer un filtre qui utilise une propriété de message pouvant faire l’objet d’une recherche. De même, vous pouvez laisser un gestionnaire eDiscovery rechercher uniquement des sites SharePoint de votre organisation. Pour ce faire, vous devez créer un filtre limitant les sites pouvant faire l’objet d’une recherche. Vous pouvez aussi créer un filtre qui spécifie le contenu de site pouvant être recherché. Pour ce faire, vous devez créer un filtre qui utilise une propriété de site pouvant faire l’objet d’une recherche.

Les filtres d’autorisations de recherche sont appliqués lorsque vous recherchez du contenu à l’aide de la recherche de contenu, de core eDiscovery et de Advanced eDiscovery dans le Centre de conformité Microsoft 365. Lorsqu’un filtre d’autorisations de recherche est appliqué à un utilisateur spécifique, cet utilisateur peut effectuer les actions liées à la recherche suivantes :

- Recherche de contenu

- Aperçu des résultats de la recherche

- Exporter les résultats de la recherche

- Purger les éléments renvoyés par une recherche

Vous pouvez également utiliser le filtrage des autorisations de recherche pour créer des limites logiques (appelées limites de *conformité)* au sein d’une organisation qui contrôle les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les sites SharePoint et les comptes OneDrive) que des gestionnaires eDiscovery spécifiques peuvent rechercher. Pour plus d’informations, voir Configurer les limites de conformité pour les [enquêtes eDiscovery.](set-up-compliance-boundaries.md)
  
Les quatre cmdlets suivantes dans Security & Compliance PowerShell vous permettent de configurer et de gérer les filtres d’autorisations de recherche :
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Configuration requise pour configurer le filtrage des autorisations

- Pour exécuter les cmdlets de filtre de sécurité de conformité, vous devez être membre du groupe de rôles Gestion de l’organisation dans le Centre de conformité Microsoft 365. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Vous devez vous connecter à la fois Exchange Online et au Centre de sécurité & conformité PowerShell pour utiliser les cmdlets de filtre de sécurité de conformité. Cela est nécessaire, car ces cmdlets nécessitent l’accès aux propriétés de boîte aux lettres, c’est pourquoi vous devez vous connecter à Exchange Online PowerShell. Consultez les étapes décrites dans la section suivante.

- Consultez la section [More information](#more-information) pour plus d’informations sur les filtres d’autorisations de recherche.

- Le filtrage des autorisations de recherche s’applique aux boîtes aux lettres inactives, ce qui signifie que vous pouvez utiliser le filtrage de contenu de boîte aux lettres et de boîtes aux lettres pour limiter les recherches dans une boîte aux lettres inactive. Pour plus [d’informations](#more-information) sur le filtrage des autorisations et les boîtes aux lettres inactives, consultez la section Plus d’informations.

- Le filtrage des autorisations de recherche ne peut pas être utilisé pour limiter les personnes autorisées à rechercher des dossiers publics dans Exchange.

- Il n’existe aucune limite au nombre de filtres d’autorisations de recherche qui peuvent être créés dans une organisation. Toutefois, une requête de recherche peut avoir un maximum de 100 conditions. Dans ce cas, une condition est définie comme étant connectée à la requête par un opérateur booléen (par exemple, **AND**, **OR** et **NEAR**). La limite du nombre de conditions inclut la requête de recherche elle-même, ainsi que tous les filtres d’autorisations de recherche qui sont appliqués à l’utilisateur qui exécute la recherche. Par conséquent, plus vous avez de filtres d’autorisations de recherche (en particulier si ces filtres sont appliqués au même utilisateur ou groupe d’utilisateurs), plus il y a de chances de dépasser le nombre maximal de conditions pour une recherche. Pour empêcher votre organisation d’atteindre la limite de conditions, limitez le nombre de filtres d’autorisations de recherche dans votre organisation au plus petit nombre possible pour répondre aux besoins de votre entreprise. Pour plus d’informations, voir Configurer les limites de conformité pour les [enquêtes eDiscovery.](set-up-compliance-boundaries.md#frequently-asked-questions)

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Connecter pour Exchange Online et le Centre de sécurité & conformité PowerShell en une seule session

Avant de pouvoir exécuter correctement le script dans cette section, vous devez télécharger et installer Exchange Online module PowerShell V2. Pour plus d’informations, [voir à propos Exchange Online module PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Enregistrez le texte suivant dans un fichier Windows PowerShell script à l’aide d’un suffixe de nom **de fichier.ps1**. Par exemple, vous pouvez l’enregistrer dans un fichier nommé **ConnectEXO-SCC.ps1**.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. Sur votre ordinateur local, ouvrez Windows PowerShell, allez dans le dossier où se trouve le script que vous avez créé à l’étape précédente, puis exécutez le script . par exemple :

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Comment savoir si cela a fonctionné ? Après avoir exécuté le script, les cmdlets de Exchange Online et security & Compliance PowerShell sont importées dans votre session Windows PowerShell locale. Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter les cmdlets powerShell du centre Exchange Online sécurité et sécurité & conformité. Par exemple, vous pouvez exécuter **et Get-Mailbox** et **Get-ComplianceSearch**.

Pour résoudre les erreurs de connexion PowerShell, voir :

- [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

Le **filtre New-ComplianceSecurityFilter est** utilisé pour créer un filtre d’autorisations de recherche. Voici la syntaxe de base pour cette cmdlet :

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

Les sections suivantes décrivent les paramètres de cette cmdlet. Tous les paramètres sont requis pour créer un filtre d’autorisations de recherche.

### <a name="filtername"></a>*FilterName*

Le  _paramètre FilterName_ spécifie le nom du filtre d’autorisations. Ce nom est utilisé pour identifier un filtre lors de l’utilisation des cmdlets **Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** et **Remove-ComplianceSecurityFilter**.

### <a name="filters"></a>*Filters*

Le  _paramètre Filters_ spécifie les critères de recherche pour le filtre de sécurité de conformité. Vous pouvez créer trois types de filtres :  

- **Filtrage de boîtes aux lettres OneDrive de boîtes aux lettres :** Ce type de filtre spécifie les boîtes aux lettres et OneDrive comptes que les utilisateurs affectés (spécifiés par le paramètre _Users)_ peuvent rechercher. Ce type de filtre est appelé *filtre* d’emplacement de contenu, car il définit les emplacements de contenu qu’un utilisateur peut rechercher. La syntaxe de ce type de filtre est **Mailbox_** _MailboxPropertyName_, où _MailboxPropertyName_ spécifie une propriété de boîte aux lettres utilisée pour l’étendue des boîtes aux lettres et des comptes OneDrive qui peuvent être recherchés. Par exemple, le filtre de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les boîtes aux lettres et les comptes OneDrive dont la valeur est « OttawaUsers » dans la propriété `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` CustomAttribute10.

  Toute propriété de destinataire filtrable prise en charge peut être utilisée pour la propriété _MailboxPropertyName_ dans une boîte aux lettres ou un OneDrive filtre. Le tableau suivant liste quatre propriétés de destinataire couramment utilisées pour créer une boîte aux lettres ou un OneDrive filtre. Le tableau inclut également un exemple d’utilisation de la propriété dans un filtre.

  |Nom de la propriété  |Exemple  |
  |---------|---------|
  |Alias    |`"Mailbox_Alias -like 'v-'"`         |
  |Company  |`"Mailbox_Company -eq 'Contoso'"`        |
  |CountryOrRegion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Service |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Filtrage de contenu de boîte aux lettres :** Ce type de filtre est appliqué au contenu qui peut être recherché. Ce type de filtre est appelé *filtre* de contenu car il spécifie le contenu de boîte aux lettres que les utilisateurs affectés peuvent rechercher. La syntaxe de ce type de filtre est **MailboxContent_** _SearchablePropertyName: value_, où  _SearchablePropertyName_ spécifie une propriété KQL (Keyword Query Language) qui peut être spécifiée dans une recherche. Par exemple, le filtre de contenu de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les messages envoyés aux  `MailboxContent_recipients:contoso.com` destinataires dans contoso.com domaine. Pour obtenir la liste des propriétés de message utilisables dans une recherche, voir Requêtes par mot clé et conditions de recherche [pour eDiscovery.](keyword-queries-and-search-conditions.md#searchable-email-properties)

  > [!IMPORTANT]
  > Un seul filtre de recherche ne peut pas contenir de filtre de boîte aux lettres et de contenu de boîte aux lettres. Pour les combiner dans un seul filtre, vous devez utiliser une liste [de filtres.](#using-a-filters-list-to-combine-filter-types)  Toutefois, un filtre peut contenir une requête plus complexe du même type. Par exemple, `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Filtrage de contenu de site et de site :** Il existe deux filtres SharePoint et OneDrive que vous pouvez utiliser pour spécifier le site ou le contenu de site que les utilisateurs affectés peuvent rechercher.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Ces deux filtres sont interchangeables. Par exemple, `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` et  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` renvoyer les mêmes résultats. Pour obtenir la liste des propriétés de site utilisables dans une recherche, voir Requêtes par mot clé et conditions de recherche pour [eDiscovery](keyword-queries-and-search-conditions.md#searchable-site-properties) Pour obtenir une liste plus complète, voir Vue d’ensemble des propriétés gérées et d’analyse dans [SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Les propriétés marquées avec le signe **Oui** dans la colonne **Queryable** peuvent être utilisées pour créer un filtre de contenu de site ou de site.  

  > [!IMPORTANT]
  > La configuration d’un filtre de site avec l’une des propriétés prise en charge ne signifie pas que la propriété de site dans le filtre sera propagée à tous les documents sur ce site. Cela signifie que l’utilisateur est toujours responsable du remplit les champs de propriété spécifiques associés aux documents sur ce site afin que le filtre de site fonctionne et capture le contenu qui lui est associé. Par exemple, si l’utilisateur dispose d’un filtre de sécurité « Site_RefineableString00 -eq 'abc » appliqué et que l’utilisateur exécute une recherche à l’aide de la requête de mot clé « xyz ». Le filtre de sécurité est ajoute à la requête et la requête en cours d’exécution réelle serait « xyz **AND RefineableString0:'abc'**». L’utilisateur doit s’assurer que les documents sur le site ont bien des valeurs dans le champ RefineableString00 en tant que « abc ». Si ce n’est pas le cas, la requête de recherche ne retourne aucun résultat.

Gardez les considérations suivantes à l’esprit lors de la configuration du paramètre *Filters* pour les filtres d’autorisations de recherche :

- Contrairement aux boîtes aux lettres, il n’existe pas de filtre d’emplacement de contenu pour les sites, même si le filtre *Site* ressemble à un filtre d’emplacement. Tous les filtres pour SharePoint et OneDrive sont des filtres de contenu (c’est également la raison pour laquelle les filtres *Site_* et *SiteContent_* sont interchangeables), car les propriétés liées au site telles que *Path* sont estampillées directement sur les documents. Pourquoi ? C’est le résultat de la façon dont SharePoint est conçu. Dans SharePoint, il n’existe pas d'« objet de site » avec des propriétés, comme c’est le cas avec Exchange boîtes aux lettres. Par conséquent, la *propriété Path* est estampillée sur le document et contient l’URL du site où se trouve le document. C’est pourquoi un filtre *de site* est considéré comme un filtre de contenu et non comme un filtre d’emplacement de contenu.

- Vous devez créer un filtre d’autorisations de recherche pour empêcher explicitement les utilisateurs de rechercher des emplacements de contenu dans un service spécifique (par exemple, empêcher un utilisateur de rechercher une boîte aux lettres Exchange ou un site SharePoint). En d’autres termes, la création d’un filtre d’autorisations de recherche qui permet à un utilisateur de rechercher tous les sites SharePoint de l’organisation n’empêche pas cet utilisateur de rechercher des boîtes aux lettres. Par exemple, pour permettre aux administrateurs SharePoint de rechercher uniquement des sites SharePoint, vous devez créer un filtre qui les empêche de rechercher des boîtes aux lettres. De même, pour autoriser Exchange administrateurs à rechercher uniquement des boîtes aux lettres, vous devez créer un filtre qui les empêche de rechercher des sites.

### <a name="users"></a>*Utilisateurs*

Le  _paramètre Users_ spécifie les utilisateurs qui obtiennent ce filtre appliqué à leurs recherches. Identifiez les utilisateurs par leur alias ou leur adresse SMTP principale. Vous pouvez indiquer plusieurs valeurs séparées par des virgules ou attribuer le filtre à tous les utilisateurs à l’aide de la valeur **Tout**.

Vous pouvez également utiliser le paramètre _Users_ pour spécifier un groupe Centre de conformité Microsoft 365 rôle principal. Cela vous permet de créer un groupe de rôles personnalisé, puis d’attribuer à ce groupe de rôles un filtre d’autorisations de recherche. Par exemple, supposons que vous disposez d’un groupe de rôles personnalisé pour les gestionnaires de découverte électronique de la filiale américaine d’une multinationale. Vous pouvez utiliser le paramètre  _Users_ pour spécifier ce groupe de rôles (à l’aide de la propriété Name du groupe de rôles), puis utiliser le paramètre  _Filter_ pour autoriser uniquement la recherche de boîtes aux lettres aux États-Unis. Vous ne pouvez pas spécifier de groupes de distribution avec ce paramètre.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Utilisation d’une liste de filtres pour combiner des types de filtres

Une *liste de filtres* est un filtre qui inclut un filtre de boîte aux lettres et un filtre de site séparés par une virgule. Cette virgule fonctionne également en tant **qu’opérateur OR.** L’utilisation d’une liste de filtres est la seule méthode prise en charge pour combiner différents types de filtres. Dans l’exemple suivant, notez qu’une virgule sépare les filtres **de** boîte aux lettres **et de site** :

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Lorsqu’un filtre qui contient une liste de filtres est traitement pendant l’exécution d’une recherche, deux filtres d’autorisations de recherche sont créés à partir de la liste des filtres : un pour chaque filtre séparé par une virgule. Ainsi, dans l’exemple précédent, un filtre d’autorisations de recherche de boîte aux lettres et un filtre d’autorisations de recherche de site sont créés. Ces filtres sont connectés par **l’opérateur OR.**

Une alternative à l’utilisation d’une liste de filtres serait de créer deux filtres d’autorisations de recherche distincts. Ainsi, dans l’exemple précédent, vous créez un filtre pour l’attribut de boîte aux lettres et un filtre pour l’attribut de site. Dans les deux cas, les résultats sont identiques. L’utilisation d’une liste de filtres ou la création de filtres d’autorisations de recherche distincts est une question de préférence.

Gardez les éléments suivants à l’esprit concernant l’utilisation d’une liste de filtres :

- Vous devez utiliser une liste de filtres pour créer un filtre qui inclut un filtre **de** boîte aux lettres et un filtre **MailboxContent.**

- Chaque composant d’une liste de filtres peut contenir une syntaxe de filtre complexe. Par exemple, la boîte aux lettres et les filtres de site peuvent contenir plusieurs filtres séparés par **un opérateur :**

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Exemples de création de filtres d’autorisations de recherche

Voici quelques exemples d’utilisation de la cmdlet **New-ComplianceSecurityFilter** pour créer un filtre d’autorisations de recherche.

Cet exemple permet aux membres du groupe de rôles « US Discovery Managers » de rechercher uniquement les boîtes aux lettres et les OneDrive aux États-Unis.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
Cet exemple permet à l’utilisateur annb@contoso.com effectuer des actions de recherche uniquement pour les boîtes aux lettres et OneDrive comptes au Canada. Ce filtre contient le code pays numérique à trois chiffres pour le Canada selon la norme ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

Cet exemple permet aux utilisateurs donh et supf de rechercher uniquement les boîtes aux lettres et les comptes OneDrive qui ont la valeur « Marketing » pour la propriété de boîte aux lettres CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

Cet exemple permet aux membres du groupe de rôles « Fourth Coffee eDiscovery Managers » de rechercher uniquement les boîtes aux lettres et les comptes OneDrive qui ont la valeur « FourthCoffee » pour la propriété de boîte aux lettres Department. Le filtre permet également aux membres du groupe de rôles de rechercher des documents dans le site fourth coffee SharePoint.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Dans l’exemple précédent, un filtre de contenu de site supplémentaire ( ) doit être inclus afin que les membres du groupe de rôles peuvent rechercher des documents dans `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'` OneDrive comptes. Si ce filtre n’est pas inclus, le filtre autorise uniquement les membres du groupe de rôles à rechercher des documents situés dans `https://contoso.sharepoint.com/sites/FourthCoffee` .

Cet exemple permet aux membres du groupe de rôles Gestionnaire eDiscovery de rechercher uniquement les boîtes aux lettres et les comptes OneDrive des membres du groupe de distribution Utilisateurs Ottawa. LGet-DistributionGroup cmdlet dans Exchange Online PowerShell permet de rechercher les membres du groupe Utilisateurs Ottawa.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

Cet exemple empêche tout utilisateur d’effectuer des actions de recherche sur les boîtes aux lettres et OneDrive comptes de membres du groupe de distribution Executive Team. Cela signifie que les utilisateurs peuvent supprimer du contenu de ces boîtes aux lettres. LGet-DistributionGroup cmdlet dans Exchange Online PowerShell est utilisée pour rechercher les membres du groupe Équipe de direction.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

Cet exemple permet aux membres du groupe de rôles OneDrive eDiscovery Managers personnalisé de rechercher uniquement du contenu dans OneDrive comptes de l’organisation.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
Cet exemple limite l’utilisateur à effectuer des actions de recherche uniquement sur les messages électroniques envoyés au cours de l’année 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Comme dans l’exemple précédent, cet exemple limite l’utilisateur à effectuer des actions de recherche uniquement sur les documents qui ont été modifiés pour la dernière fois au cours de l’année civile 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

Cet exemple empêche les membres du groupe de rôles « gestionnaires de découverte OneDrive » d’effectuer des actions de recherche sur n’importe quelle boîte aux lettres de l’organisation.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

Cet exemple empêche toute personne de l’organisation d’effectuer des actions de recherche sur les messages électroniques qui ont été envoyés ou reçus par des feds ou sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

Cet exemple utilise une liste de filtres pour combiner des filtres de boîte aux lettres et de site. Dans cet exemple, le filtre de boîte aux lettres est un filtre d’emplacement de contenu et le filtre de site est un filtre de contenu.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter est** utilisé pour renvoyer une liste de filtres d’autorisations de recherche. Utilisez le  _paramètre FilterName_ pour renvoyer des informations pour un filtre de recherche spécifique.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter est** utilisé pour modifier un filtre d’autorisations de recherche existant. Les sections suivantes décrivent les paramètres de cette cmdlet. Le seul paramètre obligatoire est  _FilterName_.
  
### <a name="filtername"></a>*FilterName*

Le  _paramètre FilterName_ spécifie le nom du filtre d’autorisations.

### <a name="users"></a>*Utilisateurs*

Le  _paramètre Users_ spécifie les utilisateurs qui obtiennent ce filtre appliqué à leurs recherches. Étant donné qu’il s’agit d’une propriété à valeurs multiples, la spécification d’un utilisateur ou d’un groupe d’utilisateurs avec ce paramètre a pour effet de réécrire la liste d’utilisateurs existante. Consultez les exemples suivants pour obtenir la syntaxe qui permet d’ajouter et de supprimer des utilisateurs sélectionnés.

Vous pouvez également utiliser le paramètre _Users_ pour spécifier un groupe Centre de conformité Microsoft 365 rôle principal. Cela vous permet de créer un groupe de rôles personnalisé, puis d’attribuer à ce groupe de rôles un filtre d’autorisations de recherche. Par exemple, supposons que vous disposez d’un groupe de rôles personnalisé pour les gestionnaires de découverte électronique de la filiale américaine d’une multinationale. Vous pouvez utiliser le paramètre  _Users_ pour spécifier ce groupe de rôles (à l’aide de la propriété Name du groupe de rôles), puis utiliser le paramètre  _Filter_ pour autoriser uniquement la recherche de boîtes aux lettres aux États-Unis. Vous ne pouvez pas spécifier de groupes de distribution avec ce paramètre.

### <a name="filters"></a>*Filters*

Le  _paramètre Filters_ spécifie les critères de recherche pour le filtre de sécurité de conformité. Vous pouvez créer trois types de filtres :

- **Filtrage des boîtes aux OneDrive et des boîtes aux lettres :** Ce type de filtre spécifie les boîtes aux lettres et OneDrive comptes que les utilisateurs affectés (spécifiés par le paramètre _Users)_ peuvent rechercher. La syntaxe de ce type de filtre est **Mailbox_** _MailboxPropertyName_,  _où MailboxPropertyName_ spécifie une propriété de boîte aux lettres utilisée pour l’étendue des boîtes aux lettres qui peuvent être recherchés. Par exemple, le filtre de boîte aux lettres autoriserait l’utilisateur affecté à ce filtre à rechercher uniquement les boîtes aux lettres dont la valeur est « OttawaUsers » dans la  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` propriété CustomAttribute10.  Toute propriété de destinataire filtrable prise en charge peut être utilisée pour la _propriété MailboxPropertyName._ Pour obtenir la liste des propriétés pris en charge, voir [Propriétés filtrables pour le paramètre -RecipientFilter](/powershell/exchange/recipientfilter-properties).

- **Filtrage de contenu de boîte aux lettres :** Ce type de filtre est appliqué au contenu qui peut être recherché. Il spécifie le contenu de boîte aux lettres que les utilisateurs affectés peuvent rechercher. La syntaxe de ce type de filtre est **MailboxContent_** _SearchablePropertyName:value_,  _où SearchablePropertyName_ spécifie une propriété KQL (Keyword Query Language) qui peut être spécifiée dans une recherche. Par exemple, le filtre de contenu de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les messages envoyés aux  `MailboxContent_recipients:contoso.com` destinataires dans contoso.com domaine.  Pour obtenir la liste des propriétés de message utilisables dans une recherche, voir Requêtes par mot clé et conditions de recherche [pour eDiscovery.](keyword-queries-and-search-conditions.md) 

- **Filtrage de contenu de site et de site :** Il existe deux filtres SharePoint et OneDrive Entreprise de site que vous pouvez utiliser pour spécifier le site ou le contenu de site que les utilisateurs affectés peuvent rechercher :

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Ces deux filtres sont interchangeables. Par exemple,  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` et  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` renvoyer les mêmes résultats. Pour obtenir la liste des propriétés de site utilisables dans une recherche, voir [Vue](/SharePoint/technical-reference/crawled-and-managed-properties-overview)d’ensemble des propriétés gérées et SharePoint . Les propriétés marquées avec le signe **Oui** dans la colonne **Queryable** peuvent être utilisées pour créer un filtre de contenu de site ou de site.

### <a name="examples-of-changing-search-permissions-filters"></a>Exemples de modification des filtres d’autorisations de recherche

Ces exemples montrent comment utiliser les cmdlets **Get-ComplianceSecurityFilter** et **Set-ComplianceSecurityFilter** pour ajouter ou supprimer un utilisateur à la liste existante d’utilisateurs à qui le filtre est affecté. Lorsque vous ajoutez ou supprimez des utilisateurs pour un filtre, spécifiez l’utilisateur à l’aide de son adresse SMTP.
  
Cet exemple ajoute un utilisateur au filtre.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

Cet exemple supprime un utilisateur du filtre.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>Remove-ComplianceSecurityFilter

**Remove-ComplianceSecurityFilter est** utilisé pour supprimer un filtre de recherche. Utilisez le  _paramètre FilterName_ pour spécifier le filtre à supprimer.
  
## <a name="more-information"></a>Plus d’informations

- **Comment fonctionne le filtrage des autorisations de recherche ?** Le filtre d’autorisations est intégré à la requête de recherche lors de l’application d’une recherche. Le filtre d’autorisations est joint à la requête de recherche par **l’opérateur booléen AND.** La logique de requête pour la requête de recherche et le filtre d’autorisations seraient comme ceci :

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Par exemple, vous avez un filtre d’autorisations qui permet à Bob d’effectuer toutes les actions de recherche sur les boîtes aux lettres des membres du groupe de distribution Workers. Ensuite, Bob exécute une recherche sur toutes les boîtes aux lettres de l’organisation avec la requête de  `sender:jerry@adatum.com` recherche. Étant donné que le filtre d’autorisations et la requête de recherche sont combinés logiquement par un opérateur **AND,** la recherche renvoie tout message envoyé par jerry@adatum.com à tout membre du groupe de distribution Workers. 

- **Que se passe-t-il si vous disposez de plusieurs filtres d’autorisations de recherche ?** Dans une requête de recherche, plusieurs filtres d’autorisations sont combinés par **des opérateurs booléens OR.** Par conséquent, des résultats sont renvoyés si l’un des filtres détecte une condition recherchée. Dans une recherche, tous les filtres (combinés par des opérateurs **OR)** sont ensuite combinés à la requête de recherche par **l’opérateur AND.**

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Prenons l’exemple précédent, où un filtre de recherche permet à Bob de rechercher uniquement les boîtes aux lettres des membres du groupe de distribution Workers. Nous créons un autre filtre qui empêche Pierre de rechercher la boîte aux lettres de Paul (« Mailbox_Alias -ne ’Paul’ »). Supposons également que Paul est membre du groupe Employés. Lorsque Bob exécute une recherche (à partir de l’exemple précédent) sur toutes les boîtes aux lettres de l’organisation, les résultats de la recherche sont renvoyés pour la boîte aux lettres de Bob, même si vous avez appliqué un filtre pour empêcher Bob de rechercher la boîte aux lettres de Bob. En effet, le critère du premier filtre, qui autorise Pierre à effectuer des recherches dans le groupe Employés, est vérifié. Ainsi, Paul étant membre du groupe Employés, Pierre peut effectuer des recherches dans sa boîte aux lettres.

- **Le filtrage des autorisations de recherche fonctionne-t-il pour les boîtes aux lettres inactives ?** Oui, vous pouvez utiliser des filtres de contenu de boîte aux lettres et de boîtes aux lettres pour limiter les recherches dans les boîtes aux lettres inactives de votre organisation. Comme pour une boîte aux lettres normale, une boîte aux lettres inactive doit être configurée avec la propriété de destinataire utilisée pour créer un filtre d’autorisations. Si nécessaire, vous pouvez utiliser la commande **Get-Mailbox -InactiveMailboxOnly** pour afficher les propriétés des boîtes aux lettres inactives. Pour plus d’informations, voir [Créer et gérer des boîtes aux lettres inactives.](create-and-manage-inactive-mailboxes.md)
  
- **Le filtrage des autorisations de recherche fonctionne-t-il pour les dossiers publics ?** Non. Comme indiqué précédemment, le filtrage des autorisations de recherche ne peut pas être utilisé pour limiter les personnes autorisées à rechercher des dossiers publics dans Exchange. Par exemple, les éléments des emplacements de dossiers publics ne peuvent pas être exclus des résultats de la recherche par un filtre d’autorisations.

- **Autoriser un utilisateur à rechercher tous les emplacements de contenu dans un service spécifique l’empêche-t-il également de rechercher des emplacements de contenu dans un autre service ?** Non. Comme indiqué précédemment, vous devez créer un filtre d’autorisations de recherche pour empêcher explicitement les utilisateurs de rechercher des emplacements de contenu dans un service spécifique (par exemple, empêcher un utilisateur de rechercher une boîte aux lettres Exchange ou un site SharePoint). En d’autres termes, la création d’un filtre d’autorisations de recherche qui permet à un utilisateur de rechercher tous les sites SharePoint de l’organisation n’empêche pas cet utilisateur de rechercher des boîtes aux lettres. Par exemple, pour permettre aux administrateurs SharePoint de rechercher uniquement des sites SharePoint, vous devez créer un filtre qui les empêche de rechercher des boîtes aux lettres. De même, pour autoriser Exchange administrateurs à rechercher uniquement des boîtes aux lettres, vous devez créer un filtre qui les empêche de rechercher des sites.

- **Les filtres d’autorisations de recherche sont-ils comptabilisés dans les limites des caractères de requête de recherche ?** Oui. Les filtres d’autorisations de recherche comptent par rapport à la limite de caractères pour les requêtes de recherche. Pour plus d’informations, [voir Limites dans Advanced eDiscovery](limits-ediscovery20.md).

**Quel est le nombre maximal de filtres d’autorisations de recherche qui peuvent être créés dans une organisation ?**
  
Il n’existe aucune limite au nombre de filtres d’autorisations de recherche qui peuvent être créés dans une organisation. Toutefois, une requête de recherche peut avoir un maximum de 100 conditions. Dans ce cas, une condition est définie comme étant connectée à la requête par un opérateur booléen (par exemple, **AND**, **OR** et **NEAR**). La limite du nombre de conditions inclut la requête de recherche elle-même, ainsi que tous les filtres d’autorisations de recherche qui sont appliqués à l’utilisateur qui exécute la recherche. Par conséquent, plus vous avez de filtres d’autorisations de recherche (en particulier si ces filtres sont appliqués au même utilisateur ou groupe d’utilisateurs), plus il y a de chances de dépasser le nombre maximal de conditions pour une recherche.

Pour comprendre le fonctionnement de cette limite, vous devez comprendre qu’un filtre d’autorisations de recherche est intégré à la requête de recherche lors de l’application d’une recherche. Un filtre d’autorisations de recherche est joint à la requête de recherche par **l’opérateur booléen AND.** La logique de requête pour la requête de recherche et un seul filtre d’autorisations de recherche seraient comme ceci :

```text
<SearchQuery> AND <PermissionsFilter>
```

Plusieurs filtres d’autorisations de recherche sont combinés par l’opérateur **booléen OR,** puis ces conditions sont connectées à la requête de recherche par l’opérateur **AND.**

La logique de requête pour la requête de recherche et les filtres d’autorisations de recherche multiples seraient comme ceci :

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Il est possible que la requête de recherche elle-même se compose de plusieurs conditions connectées par des opérateurs booléens. Chaque condition dans la requête de recherche est également comptabilisée dans la limite de 100 conditions.

En outre, le nombre de filtres d’autorisations de recherche qui sont appendés à une requête dépend de l’utilisateur qui exécute la recherche. Lorsqu’un utilisateur spécifique exécute une recherche, les filtres d’autorisations de recherche qui sont appliqués à l’utilisateur (qui est défini par le paramètre *Users* dans le filtre) sont intégrés à la requête. Votre organisation peut avoir des centaines de filtres d’autorisations de recherche, mais si plus de 100 filtres sont appliqués aux mêmes utilisateurs, il est probable que la limite de 100 conditions sera dépassée lorsque ces utilisateurs exécuteront des recherches.

Il y a une chose à garder à l’esprit sur la limite de condition. Le nombre de sites SharePoint qui sont inclus dans les filtres d’autorisations de recherche ou de requête de recherche compte également dans cette limite. 

Pour empêcher votre organisation d’atteindre la limite de conditions, limitez le nombre de filtres d’autorisations de recherche dans votre organisation au plus petit nombre possible pour répondre aux besoins de votre entreprise.