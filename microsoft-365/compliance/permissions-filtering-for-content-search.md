---
title: Configuration du filtrage des autorisations pour la recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: Utilisez le filtrage des autorisations de recherche de contenu pour laisser un gestionnaire eDiscovery rechercher uniquement un sous-ensemble de boîtes aux lettres et de sites dans votre organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 74555f605f29ff0fa979dd939d192bf2ef643b96
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58253892"
---
# <a name="configure-permissions-filtering-for-content-search"></a>Configuration du filtrage des autorisations pour la recherche de contenu

Vous pouvez utiliser le filtrage des autorisations de recherche pour laisser un gestionnaire eDiscovery rechercher uniquement un sous-ensemble de boîtes aux lettres et de sites dans votre organisation. Vous pouvez également utiliser le filtrage des autorisations pour permettre à ce gestionnaire de rechercher uniquement le contenu de boîte aux lettres ou de site qui répond à des critères de recherche spécifiques. Par exemple, vous voudrez peut-être permettre à un gestionnaire de découverte électronique de rechercher uniquement les boîtes aux lettres des utilisateurs dans un lieu ou un service spécifique. Pour ce faire, vous créez un filtre qui utilise un filtre de destinataires pris en charge pour limiter les boîtes aux lettres qu’un utilisateur ou un groupe d’utilisateurs spécifique peut rechercher. Vous pouvez également créer un filtre qui spécifie le contenu de boîte aux lettres qu’un utilisateur peut rechercher. Pour cela, vous devez créer un filtre qui utilise une propriété de message pouvant faire l’objet d’une recherche. De même, vous pouvez laisser un gestionnaire eDiscovery rechercher uniquement des SharePoint sites spécifiques dans votre organisation. Pour ce faire, vous devez créer un filtre limitant les sites pouvant faire l’objet d’une recherche. Vous pouvez aussi créer un filtre qui spécifie le contenu de site pouvant être recherché. Pour ce faire, vous devez créer un filtre qui utilise une propriété de site pouvant faire l’objet d’une recherche.

Vous pouvez également utiliser le filtrage des autorisations de recherche pour créer des limites logiques (appelées limites de *conformité)* au sein d’une organisation qui contrôle les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les sites SharePoint et les comptes OneDrive) que des gestionnaires eDiscovery spécifiques peuvent rechercher. Pour plus d’informations, voir Configurer les limites de conformité pour les [enquêtes eDiscovery dans Office 365](tagging-and-assessment-in-advanced-ediscovery.md).
  
Le filtrage des autorisations de recherche est pris en charge par la fonctionnalité de recherche de contenu dans le Centre de sécurité & conformité. Ces quatre cmdlets vous permettent de configurer et de gérer les filtres d’autorisations de recherche :
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>Configuration requise pour configurer le filtrage des autorisations

- Pour exécuter les cmdlets de filtre de sécurité de conformité, vous devez être membre du groupe de rôles Gestion de l’organisation dans le Centre de sécurité & conformité. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Vous devez vous connecter à la fois Exchange Online et au Centre de sécurité & conformité PowerShell pour utiliser les cmdlets de filtre de sécurité de conformité. Cela est nécessaire, car ces cmdlets nécessitent l’accès aux propriétés de boîte aux lettres, c’est pourquoi vous devez vous connecter à Exchange Online PowerShell. Consultez les étapes décrites dans la section suivante.

- Consultez la section [More information](#more-information) pour plus d’informations sur les filtres d’autorisations de recherche.

- Le filtrage des autorisations de recherche s’applique aux boîtes aux lettres inactives, ce qui signifie que vous pouvez utiliser le filtrage de contenu de boîte aux lettres et de boîtes aux lettres pour limiter les recherches dans une boîte aux lettres inactive. Pour plus [d’informations sur](#more-information) le filtrage des autorisations et les boîtes aux lettres inactives, consultez la section Plus d’informations.

- Le filtrage des autorisations de recherche ne peut pas être utilisé pour limiter les personnes autorisées à rechercher des dossiers publics dans Exchange.

- Il n’existe aucune limite au nombre de filtres d’autorisations de recherche qui peuvent être créés dans une organisation. Toutefois, les performances de recherche seront impactées lorsqu’il existe plus de 100 filtres d’autorisations de recherche. Pour que le nombre de filtres d’autorisations de recherche dans votre organisation reste le plus petit possible, créez des filtres qui combinent des règles pour Exchange, SharePoint et OneDrive dans un seul filtre chaque fois que possible.

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

Comment savoir si cela a fonctionné ? Après avoir exécuté le script, les cmdlets de Exchange Online et security & Compliance PowerShell sont importées dans votre session Windows PowerShell locale. Si vous ne recevez aucune erreur, la connexion est établie. Un test rapide consiste à exécuter une cmdlet Exchange Online et de sécurité & conformité. Par exemple, vous pouvez exécuter **et Get-Mailbox** et **Get-ComplianceSearch**.

Pour résoudre les erreurs de connexion PowerShell, voir :

- [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

Le **filtre New-ComplianceSecurityFilter est** utilisé pour créer un filtre d’autorisations de recherche. Le tableau suivant décrit les paramètres de cette cmdlet. Tous les paramètres sont obligatoires pour créer un filtre de sécurité de conformité.
  
| Paramètre | Description |
|:-----|:-----|
| _Action_ <br/> | Le  _paramètre Action_ spécifie le type d’action de recherche à appliquer au filtre. Les actions de recherche de contenu possibles sont les suivantes :  <br/><br/> **Exporter :** Le filtre est appliqué lors de l’exportation des résultats de recherche.  <br/> **Aperçu :** Le filtre est appliqué lors de l’aperçu des résultats de recherche.  <br/> **Purge :** Le filtre est appliqué lors de la purge des résultats de recherche.  <br/> **Recherche :** Le filtre est appliqué lors de l’exécution d’une recherche.  <br/> **Tous :** Le filtre est appliqué à toutes les actions de recherche.  <br/> |
| _FilterName_ <br/> |Le  _paramètre FilterName_ spécifie le nom du filtre d’autorisations. Ce nom est utilisé pour identifier un filtre lors de l’utilisation des cmdlets **Get-ComplianceSecurityFilter**, **Set-ComplianceSecurityFilter** et **Remove-ComplianceSecurityFilter**.  <br/> |
| _Filters_ <br/> | Le  _paramètre Filters_ spécifie les critères de recherche pour le filtre de sécurité de conformité. Vous pouvez créer trois types de filtres :  <br/><br/> **Filtrage de boîtes aux lettres OneDrive de boîtes aux lettres :** Ce type de filtre spécifie les boîtes aux lettres et OneDrive comptes que les utilisateurs affectés (spécifiés par le paramètre _Users)_ peuvent rechercher. La syntaxe de ce type de filtre est **Mailbox_** _MailboxPropertyName_, où _MailboxPropertyName_ spécifie une propriété de boîte aux lettres utilisée pour l’étendue des boîtes aux lettres et des comptes OneDrive qui peuvent être recherchés. Par exemple, le filtre de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les boîtes aux lettres et les comptes OneDrive dont la valeur est « OttawaUsers » dans la propriété `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` CustomAttribute10.  <br/>  Toute propriété de destinataire filtrable prise en charge peut être utilisée pour la _propriété MailboxPropertyName._ Pour obtenir la liste des propriétés pris en charge, voir [Propriétés filtrables pour le paramètre -RecipientFilter](/powershell/exchange/recipientfilter-properties).  <br/><br/> **Filtrage de contenu de boîte aux lettres :** Ce type de filtre est appliqué au contenu qui peut être recherché. Il spécifie le contenu de boîte aux lettres que les utilisateurs affectés peuvent rechercher. La syntaxe de ce type de filtre est **MailboxContent_** _SearchablePropertyName: value_, où  _SearchablePropertyName_ spécifie une propriété KQL (Keyword Query Language) qui peut être spécifiée dans une recherche de contenu. Par exemple, le filtre de contenu de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les messages envoyés aux  `MailboxContent_recipients:contoso.com` destinataires dans contoso.com domaine.  <br/>  Pour obtenir la liste des propriétés de message utilisables dans une recherche, voir Requêtes par mot clé et conditions de recherche [pour la recherche de contenu.](keyword-queries-and-search-conditions.md) <br/> <br/> **Important :**  Un seul filtre de recherche ne peut pas contenir de filtre de boîte aux lettres et de contenu de boîte aux lettres. Pour les combiner dans un seul filtre, vous devez utiliser une liste [de filtres.](#using-a-filters-list-to-combine-filter-types)  Toutefois, un filtre peut contenir une requête plus complexe du même type. Par exemple,  `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`.  <br/><br/> **Filtrage de contenu de site et de site :** Il existe deux filtres SharePoint et OneDrive Entreprise de site que vous pouvez utiliser pour spécifier le site ou le contenu de site que les utilisateurs affectés peuvent rechercher :  <br/><br/> - **Site_** _SearchableSiteProperty_ <br/> - **SiteContent_** _SearchableSiteProperty_ <br/><br/>  Ces deux filtres sont interchangeables. Par exemple,  `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` et  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` renvoyer les mêmes résultats. Toutefois, pour vous aider à identifier ce qu’un filtre fait, vous pouvez utiliser pour spécifier des propriétés liées au site (telles qu’une URL de site) et pour spécifier des propriétés liées au contenu (telles que les types de  `Site_`  `SiteContent_` documents). Par exemple, le filtre permet à l’utilisateur affecté à ce filtre de rechercher uniquement du  `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"` contenu dans la collection de https://contoso.sharepoint.com/sites/doctors sites. Le filtre permet à l’utilisateur affecté à ce filtre de rechercher uniquement des  `"SiteContent_FileExtension -eq 'docx'"` documents Word (Word 2007 et ultérieur).  <br/><br/>  Pour obtenir la liste des propriétés de site utilisables dans une recherche, voir [Vue](/SharePoint/technical-reference/crawled-and-managed-properties-overview)d’ensemble des propriétés gérées et SharePoint . Les propriétés marquées avec le signe **Oui** dans la colonne **Queryable** peuvent être utilisées pour créer un filtre de contenu de site ou de site.  <br/><br/> **Important :** <br/><br/> - La configuration d’un filtre de site avec l’une des propriétés prise en charge ne signifie pas que la propriété de site dans le filtre sera propagée à tous les fichiers sur ce site. Cela signifie que l’utilisateur est toujours responsable du remplit les champs de propriété spécifiques associés aux fichiers sur ce site afin que le filtre de site fonctionne et capture le contenu qui lui est propre. Par exemple, si l’utilisateur dispose d’un filtre de sécurité « Site_RefineableString00 -eq 'abc » appliqué et que l’utilisateur exécute une recherche de conformité à l’aide de la requête de mot clé « xyz ». Le filtre de sécurité est ajoute à la requête et la requête en cours d’exécution réelle serait « xyz **AND RefineableString0:'abc'**». L’utilisateur doit s’assurer que les fichiers du site ont bien des valeurs dans le champ RefineableString00 comme abc. Si ce n’est pas le cas, cette requête de recherche ne retourne aucun résultat. <br/><br/>- Vous devez créer un filtre d’autorisations de recherche pour empêcher explicitement les utilisateurs de rechercher des emplacements de contenu dans un service spécifique (par exemple, empêcher un utilisateur de rechercher une boîte aux lettres Exchange ou un site SharePoint). En d’autres termes, la création d’un filtre d’autorisations de recherche qui permet à un utilisateur de rechercher tous les sites SharePoint de l’organisation n’empêche pas cet utilisateur de rechercher des boîtes aux lettres. Par exemple, pour autoriser SharePoint administrateurs à rechercher uniquement SharePoint sites, vous devez créer un filtre qui les empêche de rechercher des boîtes aux lettres. De même, pour autoriser Exchange administrateurs à rechercher uniquement des boîtes aux lettres, vous devez créer un filtre qui les empêche de rechercher des sites.           |
| _Utilisateurs_ <br/> |Le  _paramètre Users_ spécifie les utilisateurs qui obtiennent ce filtre appliqué à leurs recherches de contenu. Identifiez les utilisateurs par leur alias ou leur adresse SMTP principale. Vous pouvez indiquer plusieurs valeurs séparées par des virgules ou attribuer le filtre à tous les utilisateurs à l’aide de la valeur **Tout**.  <br/> Vous pouvez également utiliser le paramètre  _Users_ pour spécifier un groupe de rôles du Centre de sécurité & conformité. Cela vous permet de créer un groupe de rôles personnalisé, puis d’attribuer à ce groupe de rôles un filtre d’autorisations de recherche. Par exemple, supposons que vous disposez d’un groupe de rôles personnalisé pour les gestionnaires de découverte électronique de la filiale américaine d’une multinationale. Vous pouvez utiliser le paramètre  _Users_ pour spécifier ce groupe de rôles (à l’aide de la propriété Name du groupe de rôles), puis utiliser le paramètre  _Filter_ pour autoriser uniquement la recherche de boîtes aux lettres aux États-Unis.  <br/> Vous ne pouvez pas spécifier de groupes de distribution avec ce paramètre.  <br/> |
   
### <a name="using-a-filters-list-to-combine-filter-types"></a>Utilisation d’une liste de filtres pour combiner des types de filtres

Une *liste de filtres* est un filtre qui inclut un filtre de boîte aux lettres et un filtre de site séparés par une virgule. L’utilisation d’une liste de filtres est la seule méthode prise en charge pour combiner différents types de filtres. Dans l’exemple suivant, notez qu’une virgule sépare les filtres **de** boîte aux lettres **et de site** :

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "Site_Path -like 'https://contoso.sharepoint.com/sites/doctors*'"
```

Lorsqu’un filtre qui contient une liste de filtres est traitement pendant l’exécution d’une recherche de contenu, deux filtres d’autorisations de recherche sont créés à partir de la liste des filtres : un pour chaque filtre séparé par une virgule. Ainsi, dans l’exemple précédent, un filtre d’autorisations de recherche de boîte aux lettres et un filtre d’autorisations de recherche de site sont créés. 

Une alternative à l’utilisation d’une liste de filtres serait de créer deux filtres d’autorisations de recherche distincts. Ainsi, dans l’exemple précédent, vous créez un filtre pour l’attribut de boîte aux lettres et un filtre pour l’attribut de site. Dans les deux cas, les résultats sont identiques. L’utilisation d’une liste de filtres ou la création de filtres d’autorisations de recherche distincts est une question de préférence.

Gardez les points suivants à l’esprit concernant l’utilisation d’une liste de filtres :

- Vous devez utiliser une liste de filtres pour créer un filtre qui inclut un filtre **de** boîte aux lettres et un filtre **MailboxContent.**

- Chaque composant d’une liste de filtres peut contenir une syntaxe de filtre complexe. Par exemple, les filtres de boîte aux lettres et de site peuvent contenir plusieurs filtres séparés par **un opérateur :**

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Exemples de création de filtres d’autorisations de recherche

Voici quelques exemples d’utilisation de la cmdlet **New-ComplianceSecurityFilter** pour créer un filtre d’autorisations de recherche. 
  
Cet exemple permet à l’utilisateur annb@contoso.com effectuer toutes les actions de recherche de contenu uniquement pour les boîtes aux lettres au Canada. Ce filtre contient le code pays numérique à trois chiffres pour le Canada selon la norme ISO 3166-1.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'" -Action All
```

Cet exemple permet aux utilisateurs donh et suzanf de rechercher uniquement les boîtes aux lettres possédant la valeur « Marketing » pour la propriété de boîte aux lettres CustomAttribute1.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'" -Action Search
```

Cet exemple permet aux membres du groupe de rôles « US Discovery Managers » d’effectuer toutes les actions de recherche de contenu uniquement sur les boîtes aux lettres aux États-Unis. Ce filtre contient le code pays numérique à trois chiffres pour les États-Unis selon la norme ISO 3166-1.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryCode  -eq '840'" -Action All
```

Cet exemple permet aux membres du groupe de rôles Gestionnaire eDiscovery de rechercher uniquement les boîtes aux lettres des membres du groupe de distribution Utilisateurs Ottawa. LGet-DistributionGroup cmdlet dans Exchange Online PowerShell permet de rechercher les membres du groupe Utilisateurs Ottawa.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'" -Action Search
```

Cet exemple empêche tout utilisateur de supprimer le contenu de boîtes aux lettres de membres du groupe de distribution Executive Team. LGet-DistributionGroup cmdlet dans Exchange Online PowerShell est utilisée pour rechercher les membres du groupe Équipe de direction.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" -Action Purge
```

Cet exemple permet aux membres du groupe de rôles OneDrive eDiscovery Managers personnalisé de rechercher uniquement du contenu dans OneDrive Entreprise emplacements de l’organisation.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "Site_Path -like 'https://contoso-my.sharepoint.com/personal*'" -Action Search
```

> [!NOTE]
> Pour restreindre les utilisateurs à la recherche de sites spécifiques, utilisez le  `Site_Path` filtre, comme illustré dans l’exemple précédent. `Site_Site`L’utilisation ne fonctionne pas. 
  
Cet exemple limite l’utilisateur à l’exécution de toutes les actions de recherche de contenu uniquement sur les messages électroniques envoyés au cours de l’année 2015.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'" -Action All
```

Comme l’exemple précédent, cet exemple limite l’utilisateur à l’exécution de toutes les actions de recherche de contenu sur les documents modifiés au cours de l’année 2015.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" -Action All
```

Cet exemple empêche les membres du groupe de rôles « gestionnaires de découverte OneDrive » d’effectuer des actions de recherche de contenu sur n’importe quelle boîte aux lettres de l’organisation. 

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"  -Action All
```

Cet exemple empêche toute personne de l’organisation de rechercher des messages électroniques qui ont été envoyés ou reçus par des feds ou sarad.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'" -Action Search
```

Cet exemple utilise une liste de filtres pour combiner des filtres de boîte aux lettres et de site.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'" -Action ALL
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter est** utilisé pour renvoyer une liste de filtres d’autorisations de recherche. Utilisez le  _paramètre FilterName_ pour renvoyer des informations pour un filtre de recherche spécifique. 
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter est** utilisé pour modifier un filtre d’autorisations de recherche existant. Le seul paramètre obligatoire est  _FilterName_. 
  
| Paramètre | Description |
|:-----|:-----|
| _Action_| Le  _paramètre Action_ spécifie le type d’action de recherche à appliquer au filtre. Les actions de recherche de contenu possibles sont les suivantes : <br/><br/> **Exporter :** Le filtre est appliqué lors de l’exportation des résultats de recherche.  <br/> **Aperçu :** Le filtre est appliqué lors de l’aperçu des résultats de recherche.  <br/> **Purge :** Le filtre est appliqué lors de la purge des résultats de recherche.  <br/> **Recherche :** Le filtre est appliqué lors de l’exécution d’une recherche.  <br/> **Tous :** Le filtre est appliqué à toutes les actions de recherche.  <br/> |
| _FilterName_|Le  _paramètre FilterName_ spécifie le nom du filtre d’autorisations. |
| _Filters_| Le  _paramètre Filters_ spécifie les critères de recherche pour le filtre de sécurité de conformité. Vous pouvez créer deux types de filtres différents : <br/><br/>**Filtrage des boîtes aux OneDrive et des boîtes aux lettres :** Ce type de filtre spécifie les boîtes aux lettres et OneDrive comptes que les utilisateurs affectés (spécifiés par le paramètre _Users)_ peuvent rechercher. La syntaxe de ce type de filtre est **Mailbox_** _MailboxPropertyName_,  _où MailboxPropertyName_ spécifie une propriété de boîte aux lettres utilisée pour l’étendue des boîtes aux lettres qui peuvent être recherchés. Par exemple, le filtre de boîte aux lettres autoriserait l’utilisateur affecté à ce filtre à rechercher uniquement les boîtes aux lettres dont la valeur est « OttawaUsers » dans la  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` propriété CustomAttribute10.  Toute propriété de destinataire filtrable prise en charge peut être utilisée pour la _propriété MailboxPropertyName._ Pour obtenir la liste des propriétés pris en charge, voir [Propriétés filtrables pour le paramètre -RecipientFilter](/powershell/exchange/recipientfilter-properties). <br/><br/>**Filtrage de contenu de boîte aux lettres :** Ce type de filtre est appliqué au contenu qui peut être recherché. Il spécifie le contenu de boîte aux lettres que les utilisateurs affectés peuvent rechercher. La syntaxe de ce type de filtre est **MailboxContent_** _SearchablePropertyName:value_,  _où SearchablePropertyName_ spécifie une propriété KQL (Keyword Query Language) qui peut être spécifiée dans une recherche de contenu. Par exemple, le filtre de contenu de boîte aux lettres permet à l’utilisateur affecté à ce filtre de rechercher uniquement les messages envoyés aux  `MailboxContent_recipients:contoso.com` destinataires dans contoso.com domaine.  Pour obtenir la liste des propriétés de message utilisables dans une recherche, voir [Requêtes par mot clé pour la recherche de contenu.](keyword-queries-and-search-conditions.md) <br/><br/>**Filtrage de contenu de site et de site :** Il existe deux filtres SharePoint et OneDrive Entreprise de site que vous pouvez utiliser pour spécifier le site ou le contenu de site que les utilisateurs affectés peuvent rechercher : <br/><br/>- **Site_** *SearchableSiteProperty* <br/>- **SiteContent** _ *SearchableSiteProperty*<br/><br/>Ces deux filtres sont interchangeables. Par exemple,  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` et renvoie les mêmes  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` résultats. Toutefois, pour vous aider à identifier ce qu’un filtre fait, vous pouvez utiliser pour spécifier des propriétés liées au site (telles qu’une URL de site) et pour spécifier des propriétés liées au contenu (telles que les types de  `Site_`  `SiteContent_` documents). Par exemple, le filtre permet à l’utilisateur affecté à ce filtre de rechercher uniquement du  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` contenu dans la collection de https://contoso.spoppe.com/sites/doctors sites. Le filtre permet à l’utilisateur affecté à ce filtre de rechercher uniquement des  `"SiteContent_FileExtension -eq 'docx'"` documents Word (Word 2007 et ultérieur).  <br/><br/>Pour obtenir la liste des propriétés de site utilisables dans une recherche, voir [Vue](/SharePoint/technical-reference/crawled-and-managed-properties-overview)d’ensemble des propriétés gérées et SharePoint . Les propriétés marquées avec le signe **Oui** dans la colonne **Queryable** peuvent être utilisées pour créer un filtre de contenu de site ou de site. <br/><br/>          |
| _Utilisateurs_|Le  _paramètre Users_ spécifie les utilisateurs qui obtiennent ce filtre appliqué à leurs recherches de contenu. Étant donné qu’il s’agit d’une propriété à valeurs multiples, la spécification d’un utilisateur ou d’un groupe d’utilisateurs avec ce paramètre a pour effet de réécrire la liste d’utilisateurs existante. Consultez les exemples suivants pour obtenir la syntaxe qui permet d’ajouter et de supprimer des utilisateurs sélectionnés. <br/><br/>Vous pouvez également utiliser le paramètre  _Users_ pour spécifier un groupe de rôles du Centre de sécurité & conformité. Cela vous permet de créer un groupe de rôles personnalisé, puis d’attribuer à ce groupe de rôles un filtre d’autorisations de recherche. Par exemple, supposons que vous disposez d’un groupe de rôles personnalisé pour les gestionnaires de découverte électronique de la filiale américaine d’une multinationale. Vous pouvez utiliser le paramètre  _Users_ pour spécifier ce groupe de rôles (à l’aide de la propriété Name du groupe de rôles), puis utiliser le paramètre  _Filter_ pour autoriser uniquement la recherche de boîtes aux lettres aux États-Unis. <br/><br/>Vous ne pouvez pas spécifier de groupes de distribution avec ce paramètre. |

## <a name="examples-of-changing-search-permissions-filters"></a>Exemples de modification des filtres d’autorisations de recherche

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

- **Comment fonctionne le filtrage des autorisations de recherche ?** Le filtre d’autorisations est ajouté à la requête de recherche lors de l’exécution d’une recherche de contenu. Le filtre d’autorisations est joint à la requête de recherche par **l’opérateur booléen AND.** Par exemple, vous avez un filtre d’autorisations qui permet à Bob d’effectuer toutes les actions de recherche sur les boîtes aux lettres des membres du groupe de distribution Workers. Ensuite, Bob exécute une recherche de contenu sur toutes les boîtes aux lettres de l’organisation avec la requête de  `sender:jerry@adatum.com` recherche. Étant donné que le filtre d’autorisations et la requête de recherche sont combinés logiquement par un opérateur **AND,** la recherche renvoie tous les messages envoyés par jerry@adatum.com à tout membre du groupe de distribution Workers. 
    
- **Que se passe-t-il si vous disposez de plusieurs filtres d’autorisations de recherche ?** Dans une requête de recherche de contenu, plusieurs filtres d’autorisations sont combinés par des opérateurs booléens **OR**. Par conséquent, des résultats sont renvoyés si l’un des filtres détecte une condition recherchée. Dans une recherche de contenu, tous les filtres (combinés par des opérateurs **OR**) sont ensuite combinés avec la requête de recherche par l’opérateur **AND**. Prenons l’exemple précédent, où un filtre de recherche permet à Bob de rechercher uniquement les boîtes aux lettres des membres du groupe de distribution Workers. Nous créons un autre filtre qui empêche Pierre de rechercher la boîte aux lettres de Paul (« Mailbox_Alias -ne ’Paul’ »). Supposons également que Paul est membre du groupe Employés. Lorsque Bob exécute une recherche de contenu (à partir de l’exemple précédent) sur toutes les boîtes aux lettres de l’organisation, les résultats de la recherche sont renvoyés pour la boîte aux lettres de Bob, même si vous avez appliqué un filtre pour empêcher Bob de rechercher la boîte aux lettres de Bob. En effet, le critère du premier filtre, qui autorise Pierre à effectuer des recherches dans le groupe Employés, est vérifié. Ainsi, Paul étant membre du groupe Employés, Pierre peut effectuer des recherches dans sa boîte aux lettres. 
    
- **Le filtrage des autorisations de recherche fonctionne-t-il pour les boîtes aux lettres inactives ?** Oui, vous pouvez utiliser des filtres de contenu de boîte aux lettres et de boîtes aux lettres pour limiter les recherches dans les boîtes aux lettres inactives de votre organisation. Comme pour une boîte aux lettres normale, une boîte aux lettres inactive doit être configurée avec la propriété de destinataire utilisée pour créer un filtre d’autorisations. Si nécessaire, vous pouvez utiliser la commande **Get-Mailbox -InactiveMailboxOnly** pour afficher les propriétés des boîtes aux lettres inactives. Pour plus d’informations, voir [Créer et gérer des boîtes aux lettres inactives dans Office 365](create-and-manage-inactive-mailboxes.md).
    
- **Le filtrage des autorisations de recherche fonctionne-t-il pour les dossiers publics ?** Non. Comme indiqué précédemment, le filtrage des autorisations de recherche ne peut pas être utilisé pour limiter les personnes autorisées à rechercher des dossiers publics dans Exchange. Par exemple, les éléments des emplacements de dossiers publics ne peuvent pas être exclus des résultats de la recherche par un filtre d’autorisations. 

- **Autoriser un utilisateur à rechercher tous les emplacements de contenu dans un service spécifique l’empêche-t-il également de rechercher des emplacements de contenu dans un autre service ?** Non. Comme expliqué précédemment, vous devez créer un filtre d’autorisations de recherche pour empêcher explicitement les utilisateurs de rechercher des emplacements de contenu dans un service spécifique (par exemple, empêcher un utilisateur de rechercher une boîte aux lettres Exchange ou un site SharePoint). En d’autres termes, la création d’un filtre d’autorisations de recherche qui permet à un utilisateur de rechercher tous les sites SharePoint de l’organisation n’empêche pas cet utilisateur de rechercher des boîtes aux lettres. Par exemple, pour autoriser SharePoint administrateurs à rechercher uniquement SharePoint sites, vous devez créer un filtre qui les empêche de rechercher des boîtes aux lettres. De même, pour autoriser Exchange administrateurs à rechercher uniquement des boîtes aux lettres, vous devez créer un filtre qui les empêche de rechercher des sites.

- **Les filtres d’autorisations de recherche sont-ils comptabilisés dans les limites des caractères de requête de recherche ?** Oui. Les filtres d’autorisations de recherche comptent par rapport à la limite de caractères pour les requêtes de recherche. Pour plus d’informations, [voir Limites dans Advanced eDiscovery](limits-ediscovery20.md).

