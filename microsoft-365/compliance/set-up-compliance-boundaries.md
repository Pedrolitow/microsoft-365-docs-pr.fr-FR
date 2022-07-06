---
title: Configurer les limites de conformité pour les investigations eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1b45c82f-26c8-44fb-9f3b-b45436fe2271
description: Découvrez comment utiliser les limites de conformité pour créer des limites logiques qui contrôlent les emplacements de contenu utilisateur qu’un gestionnaire eDiscovery peut rechercher dans Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 903992df71b82a7dc1081bb286871e0b7af72d37
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625058"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Configurer les limites de conformité pour les investigations eDiscovery

Les instructions de cet article peuvent être appliquées lors de l’utilisation de Microsoft Purview eDiscovery (Standard) ou Microsoft Purview eDiscovery (Premium) pour gérer les enquêtes.

Les limites de conformité créent des limites logiques au sein d'une organisation qui contrôlent les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les comptes OneDrive et les sites Microsoft Office SharePoint Online) que les gestionnaires de découverte électronique peuvent rechercher. En outre, les limites de conformité contrôlent qui peut accéder aux cas eDiscovery utilisés pour gérer les ressources juridiques, humaines ou d’autres enquêtes au sein de votre organisation. Le besoin de limites de conformité est souvent nécessaire pour les sociétés multinationales qui doivent respecter les réglementations et les conseils d’administration géographiques et pour les gouvernements, qui sont souvent divisés en différents organismes. Dans Microsoft 365, les limites de conformité vous aident à répondre à ces exigences lors de l’exécution de recherches de contenu et de la gestion des investigations avec des cas eDiscovery.
  
Nous utilisons l’exemple de l’illustration suivante pour expliquer le fonctionnement des limites de conformité.
  
![Les limites de conformité consistent en des filtres d'autorisations de recherche qui contrôlent l'accès aux agences et aux groupes de rôles d'administrateur qui contrôlent l'accès aux cas de découverte électronique.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
Dans cet exemple, Contoso LTD est une organisation qui se compose de deux filiales, Fourth Coffee et Coho Winery. L’entreprise exige que les responsables et les enquêteurs eDiscovery puissent uniquement effectuer des recherches dans les boîtes aux lettres Exchange, les comptes OneDrive et les sites SharePoint dans leur agence. En outre, les responsables et les enquêteurs eDiscovery peuvent uniquement voir les cas eDiscovery dans leur agence, et ils ne peuvent accéder qu’aux cas dont ils sont membres. En outre, dans ce scénario, les enquêteurs ne peuvent pas placer les emplacements de contenu en attente ou exporter du contenu à partir d’un cas. Voici comment les limites de conformité répondent à ces exigences.
  
- La fonctionnalité de filtrage des autorisations de recherche pour eDiscovery contrôle les emplacements de contenu que les responsables et les enquêteurs eDiscovery peuvent rechercher. Cela signifie que les gestionnaires et enquêteurs eDiscovery de l’Agence Fourth Coffee peuvent uniquement rechercher des emplacements de contenu dans la filiale Fourth Coffee. La même restriction s’applique à la filiale de Coho Winery.

- [Les groupes de rôles](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) fournissent les fonctions suivantes pour les limites de conformité :

  - Contrôler qui peut voir les cas eDiscovery dans le portail de conformité Microsoft Purview. Cela signifie que les gestionnaires et enquêteurs eDiscovery peuvent uniquement consulter les dossiers eDiscovery de leur agence.

  - Contrôler qui peut affecter des membres à un cas eDiscovery. Cela signifie que les gestionnaires et enquêteurs eDiscovery peuvent uniquement affecter des membres à des cas dont ils sont eux-mêmes membres.

  - Contrôlez les tâches liées à eDiscovery que les membres peuvent effectuer en ajoutant ou en supprimant des rôles qui attribuent des autorisations spécifiques.

- Lorsqu’un filtre d’autorisations de recherche est appliqué à un groupe de rôles, les membres du groupe de rôles peuvent effectuer les actions liées à la recherche suivantes tant que les autorisations d’exécution d’une action sont attribuées au groupe de rôles :

  - Recherche de contenu

  - Aperçu des résultats de la recherche

  - Exporter les résultats de la recherche

  - Vider les éléments retournés par une recherche

Voici le processus de configuration des limites de conformité :
  
[Étape 1 : Identifier un attribut utilisateur pour définir vos agences](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Étape 2 : Créer un groupe de rôles pour chaque agence](#step-2-create-a-role-group-for-each-agency)

[Étape 3 : Créer un filtre d’autorisations de recherche pour appliquer la limite de conformité](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Étape 4 : Créer un cas eDiscovery pour une enquête intra-agence](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Avant de configurer les limites de conformité

- Une licence Exchange Online doit être attribuée aux utilisateurs. Pour vérifier cela, utilisez l’applet [de commande Get-User](/powershell/module/exchange/get-user) dans Exchange Online PowerShell.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Étape 1 : Identifier un attribut utilisateur pour définir vos agences

La première étape consiste à choisir un attribut à utiliser qui définira vos agences. Cet attribut est utilisé pour créer le filtre d’autorisations de recherche qui limite un gestionnaire eDiscovery à rechercher uniquement les emplacements de contenu des utilisateurs auxquels une valeur spécifique est attribuée pour cet attribut. Par exemple, supposons que Contoso décide d’utiliser l’attribut **Department** . La valeur de cet attribut pour les utilisateurs de la filiale Fourth Coffee serait  `FourthCoffee`  et la valeur pour les utilisateurs de la filiale Coho Winery serait `CohoWinery`. À l’étape 3, vous utilisez cette  `attribute:value`  paire (par exemple, *Department:FourthCoffee*) pour limiter les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher. 
  
Voici quelques exemples d’attributs utilisateur que vous pouvez utiliser pour les limites de conformité :
  
- Société

- CustomAttribute1 - CustomAttribute15

- Service

- Bureau

- CountryOrRegion (code de pays à deux lettres)

Pour obtenir la liste complète, consultez la liste complète des [filtres de boîte aux lettres pris en](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) charge.

## <a name="step-2-create-a-role-group-for-each-agency"></a>Étape 2 : Créer un groupe de rôles pour chaque agence

L’étape suivante consiste à créer les groupes de rôles dans le portail de conformité qui seront alignés sur vos agences. Nous vous recommandons de créer un groupe de rôles en copiant le groupe des gestionnaires eDiscovery intégrés, en ajoutant les membres appropriés et en supprimant des rôles qui peuvent ne pas être applicables à vos besoins. Pour plus d’informations sur les rôles liés à eDiscovery, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md).
  
Pour créer les groupes de rôles, accédez à la page Autorisations dans le portail de conformité et créez un groupe de rôles pour chaque équipe de chaque agence qui utilisera les **limites** de conformité et les cas eDiscovery pour gérer les enquêtes.
  
À l’aide du scénario de limites de conformité Contoso, quatre groupes de rôles doivent être créés et les membres appropriés doivent être ajoutés à chacun d’eux.
  
- Gestionnaires eDiscovery de Fourth Coffee

- Enquêteurs Fourth Coffee

- Gestionnaires eDiscovery de Coho Winery

- Enquêteurs Coho Winery
  
Pour répondre aux exigences du scénario de limites de conformité Contoso, vous devez également supprimer les rôles **De conservation** et **d’exportation** des groupes de rôles d’enquêteurs afin d’empêcher les enquêteurs de placer des conservations sur des emplacements de contenu et d’exporter du contenu à partir d’un cas.

> [!IMPORTANT]
> Si un rôle est ajouté ou supprimé d’un groupe de rôles que vous avez ajouté en tant que membre d’un cas, le groupe de rôles est automatiquement supprimé en tant que membre du cas (ou dans tous les cas dont le groupe de rôles est membre). La raison en est que votre organisation ne fournit pas par inadvertance des autorisations supplémentaires aux membres d’un cas. De même, si un groupe de rôles est supprimé, il sera supprimé de tous les cas dont il était membre.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Étape 3 : Créer un filtre d’autorisations de recherche pour appliquer la limite de conformité

Une fois que vous avez créé des groupes de rôles pour chaque agence, l’étape suivante consiste à créer les filtres d’autorisations de recherche qui associent chaque groupe de rôles à son agence spécifique et définissent la limite de conformité elle-même. Vous devez créer un filtre d’autorisations de recherche pour chaque agence. Pour plus d’informations sur la création de filtres d’autorisations de sécurité, consultez [Configurer le filtrage des autorisations pour la recherche de contenu](permissions-filtering-for-content-search.md).
  
Voici la syntaxe utilisée pour créer un filtre d’autorisations de recherche utilisé pour les limites de conformité pour le scénario de cet article.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Voici une description de chaque paramètre dans la commande :
  
- `FilterName`: spécifie le nom du filtre. Utilisez un nom qui décrit ou identifie l’agence dans laquelle le filtre est utilisé.

- `Users`: spécifie les utilisateurs ou groupes auxquels ce filtre est appliqué aux actions de recherche qu’ils effectuent. Pour les limites de conformité, ce paramètre spécifie les groupes de rôles (que vous avez créés à l’étape 3) dans l’agence pour laquelle vous créez le filtre. Notez qu’il s’agit d’un paramètre à valeurs multiples qui vous permet d’inclure un ou plusieurs groupes de rôles, séparés par des virgules.

- `Filters`: spécifie les critères de recherche pour le filtre. Pour les limites de conformité, vous définissez les filtres suivants. Chacun s’applique à différents emplacements de contenu.

  - `Mailbox`: spécifie les boîtes aux lettres ou les comptes OneDrive que les groupes de rôles définis dans le `Users` paramètre peuvent rechercher. Ce filtre permet aux membres du groupe de rôles de rechercher uniquement les boîtes aux lettres ou les comptes OneDrive dans une agence spécifique; par exemple, `"Mailbox_Department -eq 'FourthCoffee'"`.

  - `SiteContent`: ce filtre comprend deux filtres distincts. Le premier `SiteContent_Path` spécifie les sites SharePoint dans l’agence que les groupes de rôles définis dans le `Users` paramètre peuvent rechercher. Par exemple : `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. Le deuxième `SiteContent_Path` filtre (connecté au premier `SiteContent_Path` filtre par l’opérateur `or` ) spécifie le domaine OneDrive de l’agence (également appelé domaine *MySite* ). Par exemple : `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Vous pouvez également utiliser le filtre à la `Site_Path` place du `SiteContent` filtre. Les `Site` filtres et `SiteContent` les filtres sont interchangeables et n’affectent pas les filtres d’autorisations de recherche décrits dans cet article.

    > [!IMPORTANT]
    > Pourquoi le `SiteContent` filtre pour OneDrive est-il inclus dans le filtre d’autorisations de recherche précédent ? Bien que le `Mailbox` filtre s’applique *aux boîtes* aux lettres et aux comptes OneDrive, l’inclusion du filtre SharePoint exclut les comptes OneDrive si vous n’incluez pas également le filtre OneDrive `Site` . Si le filtre d’autorisations de recherche n’incluait pas de filtre SharePoint, vous n’auriez pas besoin d’inclure un filtre OneDrive distinct, car le filtre de boîte aux lettres inclurait des comptes OneDrive dans l’étendue de la limite de conformité. En d’autres termes, un filtre d’autorisations de recherche avec uniquement le `Mailbox` filtre inclut les boîtes aux lettres et les comptes OneDrive.

Voici quelques exemples de deux filtres d’autorisations de recherche qui seraient créés pour prendre en charge le scénario de limites de conformité Contoso. Ces deux exemples incluent une liste de filtres séparés par des virgules, dans laquelle les filtres de boîte aux lettres et de site sont inclus dans le même filtre des autorisations de recherche et sont séparés par une virgule.
  
### <a name="fourth-coffee"></a>Quatrième café

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> La syntaxe des `Filters` paramètres dans les exemples précédents inclut une *liste de filtres*. Une liste de filtres est un filtre qui inclut un filtre de boîte aux lettres et un filtre de chemin d’accès de site séparés par une virgule. Dans l’exemple précédent, notez qu’une virgule sépare `Mailbox` et `SiteContent` filtre : `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Lorsque ce filtre est traité pendant l’exécution d’une recherche eDiscovery, deux filtres d’autorisations de recherche sont créés à partir de la liste des filtres : un filtre de boîte aux lettres et un filtre SharePoint/OneDrive. Une alternative à l’utilisation d’une liste de filtres consiste à créer deux filtres d’autorisations de recherche distincts pour chaque agence : un filtre d’autorisations de recherche pour l’attribut de boîte aux lettres et un filtre pour les attributs de site SharePoint et OneDrive. Dans les deux cas, les résultats seront les mêmes. L’utilisation d’une liste de filtres ou la création de filtres d’autorisations de recherche distincts est une question de préférence.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Comment fonctionnent les filtres d’autorisations de recherche dans ce scénario ?

Voici comment les filtres d’autorisation de recherche sont appliqués pour chaque agence dans ce scénario.

1. Le `Mailbox` filtre est d’abord appliqué pour définir les emplacements de contenu que les gestionnaires eDiscovery peuvent rechercher. Dans ce cas, les responsables de Coho Winery eDiscovery peuvent uniquement rechercher dans les boîtes aux lettres et les comptes OneDrive des utilisateurs dont la propriété de boîte aux lettres *Department* a la valeur **FourthCoffee**; Les responsables de Coho Winery eDiscovery peuvent uniquement rechercher dans les boîtes aux lettres et les comptes OneDrive des utilisateurs dont la propriété de boîte aux lettres *Department* a la valeur **CohoWinery**. Le `Mailbox` filtre est un *filtre d’emplacement de contenu*, car il spécifie les emplacements de contenu que les gestionnaires eDiscovery peuvent rechercher. Dans les deux filtres, les gestionnaires eDiscovery peuvent uniquement rechercher des emplacements de contenu avec une valeur de propriété de boîte aux lettres spécifique.

2. Une fois que les emplacements de contenu pouvant être recherchés sont définis, la partie suivante du filtre définit le contenu que les gestionnaires eDiscovery peuvent rechercher. Le premier `SiteContent` filtre permet aux responsables fourth coffee eDiscovery de rechercher uniquement les documents qui ont une propriété de chemin d’accès de site qui contient (ou commence par) `https://contoso.sharepoint.com/sites/FourthCoffee`; Les responsables de Coho Winery eDiscovery peuvent uniquement rechercher des documents qui ont une propriété de chemin d’accès de site qui contient (ou commence par). `https://contoso.sharepoint.com/sites/CohoWinery` Par conséquent, les deux `SiteContent` filtres sont *des filtres de contenu* , car ils définissent le contenu qui peut être recherché. Dans les deux filtres, les gestionnaires eDiscovery peuvent uniquement rechercher des documents avec une valeur de propriété de document spécifique. Tous les filtres liés à SharePoint sont des filtres de contenu, car les propriétés de site pouvant faire l’objet d’une recherche sont estampillées sur tous les documents. Pour plus d’informations, consultez [Configurer le filtrage des autorisations pour eDiscovery](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Bien que le scénario de cet article ne les utilise pas, vous pouvez également utiliser des filtres de contenu de boîte aux lettres pour spécifier le contenu que les gestionnaires eDiscovery peuvent rechercher. La syntaxe des filtres de contenu de boîte aux lettres est `"MailboxContent_<property> -<comparison operator> '<value>'"`. Vous pouvez créer des filtres de contenu en fonction des plages de dates, des destinataires et des domaines, ou de toute propriété de courrier pouvant faire l’objet d’une recherche. Par exemple, ce filtre autorise les gestionnaires eDiscovery à rechercher uniquement les éléments de courrier envoyés ou reçus par les utilisateurs du domaine contoso.com : `"MailboxContent_Participants -like 'contoso.com'"`. Pour plus d’informations sur les filtres de contenu de boîte aux lettres, consultez [Configurer le filtrage des autorisations de recherche](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Le filtre d’autorisations de recherche est joint à la requête de recherche par l’opérateur **AND** Boolean. Cela signifie que lorsqu’un responsable eDiscovery dans l’une des agences exécute une recherche eDiscovery, les éléments retournés par la recherche doivent correspondre à la requête de recherche et aux conditions définies dans le filtre d’autorisations de recherche.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>Étape 4 : Créer un cas eDiscovery pour les enquêtes intra-agences

La dernière étape consiste à créer un cas eDiscovery (Standard) ou eDiscovery (Premium) dans le portail de conformité, puis à ajouter le groupe de rôles que vous avez créé à l’étape 2 en tant que membre du cas. Cela entraîne deux caractéristiques importantes de l’utilisation des limites de conformité :
  
- Seuls les membres du groupe de rôles ajoutés au cas pourront voir et accéder au cas dans le portail de conformité. Par exemple, si le groupe de rôles Fourth Coffee Investigators est le seul membre d’un cas, les membres du groupe de rôles Fourth Coffee eDiscovery Managers (ou membres d’un autre groupe de rôles) ne pourront pas voir ou accéder au cas.

- Lorsqu’un membre du groupe de rôles affecté à un cas exécute une recherche associée au cas, il peut uniquement rechercher les emplacements de contenu au sein de son agence (qui est défini par le filtre d’autorisations de recherche que vous avez créé à l’étape 3.)

Pour créer un cas et affecter des membres :

1. Accédez à la page **eDiscovery (Standard)** ou **eDiscovery (Premium)** dans le portail de conformité et créez un cas.

2. Dans la liste des cas, cliquez sur le nom du cas que vous avez créé.

3. Ajoutez des groupes de rôles en tant que membres au cas. Pour obtenir des instructions, consultez l’un des articles suivants :

   - [Ajouter des membres à un cas eDiscovery (Standard)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

   - [Ajouter des membres à un cas eDiscovery (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Lorsque vous ajoutez un groupe de rôles à un cas, vous pouvez uniquement ajouter les groupes de rôles dont vous êtes membre.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Recherche et exportation de contenu dans des environnements multigéographiques

Les filtres d’autorisations de recherche vous permettent également de contrôler où le contenu est routée pour l’exportation et quel centre de données peut être recherché lors de la recherche d’emplacements de contenu dans un [environnement SharePoint Multi-Géo](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).
  
- **Exporter les résultats de la recherche :** Vous pouvez exporter les résultats de la recherche à partir de boîtes aux lettres Exchange, de sites SharePoint et de comptes OneDrive à partir d’un centre de données spécifique. Cela signifie que vous pouvez spécifier l’emplacement du centre de données à partir de lequel les résultats de la recherche seront exportés.

    Utilisez le paramètre *Region* pour les applets de commande **New-ComplianceSecurityFilter** ou **Set-ComplianceSecurityFilter** pour créer ou modifier le centre de données vers lequel l’exportation sera acheminée.
  
    |**Valeur du paramètre**|**Emplacement du centre de données**|
    |:-----|:-----|
    |NAM  <br/> |Amérique du Nord (les centres de données se trouvent aux États-Unis)  <br/> |
    |EUR  <br/> |Europe  <br/> |
    |APC  <br/> |Asie-Pacifique  <br/> |
    |CAN <br/> |Canada|
    |||

- **Recherches de contenu de routage :** Vous pouvez acheminer les recherches de contenu des sites SharePoint et des comptes OneDrive vers un centre de données satellite. Cela signifie que vous pouvez spécifier l’emplacement du centre de données où les recherches seront exécutées.

    Utilisez l’une des valeurs suivantes pour le paramètre *Region* pour contrôler l’emplacement du centre de données dans lequel les recherches s’exécuteront lors de la recherche de sites SharePoint et de comptes OneDrive.
  
    |**Valeur du paramètre**|**Emplacements de routage du centre de données pour SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |US  <br/> |
    |EUR  <br/> |Europe  <br/> |
    |APC  <br/> |Asie-Pacifique  <br/> |
    |CAN  <br/> |US  <br/> |
    |AUS  <br/> |Asie-Pacifique  <br/> |
    |KOR  <br/> |Centre de données par défaut de l’organisation  <br/> |
    |GBR  <br/> |Europe  <br/> |
    |JPN  <br/> |Asie-Pacifique  <br/> |
    |IND  <br/> |Asie-Pacifique  <br/> |
    |LAM  <br/> |US  <br/> |
    |NOR  <br/> |Europe |
    |BRA  <br/> |Centres de données nord-américains |
    |||

   Si vous ne spécifiez pas le paramètre *Region* pour un filtre d’autorisations de recherche, la région SharePoint principale de l’organisation est recherchée. Les résultats de la recherche sont exportés vers le centre de données le plus proche.

   Pour simplifier le concept, le paramètre *Region* contrôle le centre de données utilisé pour rechercher du contenu dans SharePoint et OneDrive. Cela ne s’applique pas à la recherche de contenu dans Exchange, car les recherches de contenu Exchange ne sont pas liées par l’emplacement géographique des centres de données. En outre, la même valeur de paramètre *Region* peut également dicter le centre de données vers lequel les exportations sont acheminées. Cela est souvent nécessaire pour contrôler le déplacement des données entre les boarders géographiques.

> [!NOTE]
> Si vous utilisez eDiscovery (Premium), le paramètre *Region* ne contrôle pas la région à partir de laquelle les données sont exportées. Les données sont exportées à partir de l’emplacement central de l’organisation. En outre, la recherche de contenu dans SharePoint et OneDrive n’est pas liée par l’emplacement géographique des centres de données. Tous les centres de données sont recherchés. Pour plus d’informations sur eDiscovery (Premium), consultez [Vue d’ensemble de la solution eDiscovery (Premium) dans Microsoft 365](overview-ediscovery-20.md).

Voici des exemples d’utilisation du paramètre *Region* lors de la création de filtres d’autorisation de recherche pour les limites de conformité. Cela suppose que la filiale Fourth Coffee est située à Amérique du Nord et que Coho Winery est en Europe.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Gardez à l’esprit les éléments suivants lors de la recherche et de l’exportation de contenu dans des environnements multigéographiques.
  
- Le paramètre *Région* ne contrôle pas les recherches dans les boîtes aux lettres Exchange. Tous les centres de données sont recherchés lorsque vous recherchez des boîtes aux lettres. Pour limiter l’étendue de la recherche de boîtes aux lettres Exchange, utilisez le paramètre *Filtres* lors de la création ou de la modification d’un filtre d’autorisations de recherche.

- S’il est nécessaire qu’un gestionnaire eDiscovery effectue une recherche dans plusieurs régions SharePoint, vous devez créer un autre compte d’utilisateur pour ce gestionnaire eDiscovery à utiliser dans le filtre d’autorisations de recherche afin de spécifier la région où se trouvent les sites SharePoint ou les comptes OneDrive. Pour plus d’informations sur cette configuration, consultez la section « Recherche de contenu dans un environnement SharePoint Multi-Géo » dans [Recherche de contenu](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- Lors de la recherche de contenu dans SharePoint et OneDrive, le paramètre *Region* dirige les recherches vers l’emplacement principal ou satellite où le gestionnaire eDiscovery effectuera des investigations eDiscovery. Si un gestionnaire eDiscovery recherche des sites SharePoint et OneDrive en dehors de la région spécifiée dans le filtre d’autorisations de recherche, aucun résultat de recherche n’est retourné.

- Lors de l’exportation des résultats de recherche à partir d’eDiscovery (Standard), le contenu de tous les emplacements de contenu (y compris Exchange, Skype Entreprise, SharePoint, OneDrive et d’autres services que vous pouvez rechercher à l’aide de l’outil Recherche de contenu) est chargé vers l’emplacement stockage Azure dans le centre de données spécifié par le paramètre *Region*. Cela permet aux organisations de rester conformes en n’autorisant pas l’exportation de contenu au-delà des frontières contrôlées. Si aucune région n’est spécifiée dans le filtre d’autorisations de recherche, le contenu est chargé dans le centre de données principal de l’organisation.

  Lors de l’exportation de contenu à partir d’eDiscovery (Premium), vous ne pouvez pas contrôler où le contenu est chargé à l’aide du paramètre *Region* . Le contenu est chargé vers un emplacement stockage Azure dans un centre de données situé à l’emplacement central de votre organisation. Pour obtenir la liste des emplacements géographiques en fonction de votre emplacement central, consultez [la configuration de Microsoft 365 Multi-Geo eDiscovery](../enterprise/multi-geo-ediscovery-configuration.md).

- Vous pouvez modifier un filtre d’autorisations de recherche existant pour ajouter ou modifier la région en exécutant la commande suivante :

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Utilisation des limites de conformité pour les sites hub SharePoint

Les [sites hub SharePoint](/sharepoint/dev/features/hub-site/hub-site-overview) s’alignent souvent sur les mêmes limites géographiques ou d’agence que les limites de conformité eDiscovery. Cela signifie que vous pouvez utiliser la propriété iD de site du site hub pour créer une limite de conformité. Pour ce faire, utilisez l’applet de commande [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) dans SharePoint Online PowerShell pour obtenir l’ID de site pour le site hub, puis utilisez cette valeur pour la propriété ID de service afin de créer un filtre d’autorisations de recherche.

Utilisez la syntaxe suivante pour créer un filtre d’autorisations de recherche pour un site hub SharePoint :

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Voici un exemple de création d’un filtre d’autorisations de recherche pour un site hub pour l’agence Coho Winery :

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Limites de conformité

Gardez à l’esprit les limitations suivantes lors de la gestion des cas eDiscovery et des enquêtes qui utilisent des limites de conformité.
  
- Lors de la création et de l’exécution d’une recherche, vous pouvez sélectionner des emplacements de contenu extérieurs à votre organisation. Toutefois, en raison du filtre d’autorisation de recherche, le contenu de ces emplacements n’est pas inclus dans les résultats de recherche.

- Les limites de conformité ne s’appliquent pas aux conservations dans les cas eDiscovery. Cela signifie qu’un gestionnaire eDiscovery dans une agence peut placer un utilisateur dans une autre agence en attente. Toutefois, la limite de conformité est appliquée si le gestionnaire eDiscovery recherche les emplacements du contenu de l'utilisateur mis en attente. Cela signifie que le gestionnaire eDiscovery ne pourra pas effectuer de recherche dans les emplacements de contenu des utilisateurs, même s’il a pu mettre l’utilisateur en attente.

- Si un filtre d’autorisations de recherche (boîte aux lettres ou filtre de site) vous est attribué et que vous essayez d’exporter des éléments non indexés pour une recherche qui inclut tous les sites SharePoint de votre organisation, vous recevrez le message d’erreur suivant : `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Si un filtre d’autorisations de recherche vous est attribué et que vous souhaitez exporter des éléments non indexés à partir de SharePoint, vous devez réexécuter la recherche et inclure des sites SharePoint spécifiques à rechercher. Sinon, vous ne pourrez exporter des éléments indexés qu’à partir d’une recherche qui inclut tous les sites SharePoint. Pour plus d’informations sur les options lorsque vous exportez des résultats de recherche, consultez [Exporter les résultats de la recherche de contenu](export-search-results.md#step-1-prepare-search-results-for-export).

- Les filtres d’autorisation de recherche ne sont pas appliqués aux dossiers publics Exchange.

## <a name="more-information"></a>Plus d’informations

- Si une boîte aux lettres est supprimée de licence ou supprimée de manière réversible, l’utilisateur ne sera plus pris en compte dans la limite de conformité. Si une conservation a été placée sur la boîte aux lettres lors de sa suppression, le contenu conservé dans la boîte aux lettres est toujours soumis à une limite de conformité ou à un filtre d’autorisations de recherche.

- Si les limites de conformité et les filtres d’autorisations de recherche sont implémentés pour un utilisateur, nous vous recommandons de ne pas supprimer la boîte aux lettres d’un utilisateur et non son compte OneDrive. En d’autres termes, si vous supprimez la boîte aux lettres d’un utilisateur, vous devez également supprimer le compte OneDrive de l’utilisateur, car mailbox_RecipientFilter est utilisé pour appliquer le filtre d’autorisation de recherche pour OneDrive.

- Les limites de conformité et les filtres d’autorisations de recherche dépendent des attributs marqués sur le contenu dans Exchange, OneDrive et SharePoint, ainsi que de l’indexation ultérieure de ce contenu estampillé.

- Nous vous déconseillons d’utiliser des filtres d’exclusion (par `-not()` exemple, dans un filtre d’autorisations de recherche) pour une limite de conformité basée sur le contenu. L’utilisation d’un filtre d’exclusion peut avoir des résultats inattendus si le contenu avec des attributs récemment mis à jour n’a pas été indexé.

## <a name="frequently-asked-questions"></a>Foire aux questions

**Qui peut créer et gérer des filtres d’autorisations de recherche (à l’aide d'New-ComplianceSecurityFilter et d’applets de commande Set-ComplianceSecurityFilter) ?**
  
Pour créer, afficher et modifier des filtres d’autorisations de recherche, vous devez être membre du groupe de rôles Gestion de l’organisation dans le portail de conformité.
  
**Si un responsable eDiscovery est affecté à plusieurs groupes de rôles qui s’étendent sur plusieurs agences, comment recherchent-ils du contenu dans une agence ou l’autre ?**
  
Le gestionnaire eDiscovery peut ajouter des paramètres à sa requête de recherche qui limitent la recherche à une agence spécifique. Par exemple, si une organisation a spécifié la propriété **CustomAttribute10** pour différencier les agences, elle peut ajouter ce qui suit à sa requête de recherche pour rechercher des boîtes aux lettres et des comptes OneDrive dans une agence spécifique : `CustomAttribute10:<value>`
  
**Que se passe-t-il si la valeur de l’attribut utilisé comme attribut de conformité dans un filtre d’autorisations de recherche est modifiée ?**
  
Un filtre d’autorisations de recherche prend jusqu’à trois jours pour appliquer la limite de conformité si la valeur de l’attribut utilisé dans le filtre est modifiée. Par exemple, dans le scénario Contoso, supposons qu’un utilisateur de l’agence Fourth Coffee soit transféré à l’agence Coho Winery. Par conséquent, la valeur de l’attribut **Department** sur l’objet utilisateur passe de *FourthCoffee* à *CohoWinery*. Dans ce cas, Fourth Coffee eDiscovery et les investisseurs obtiennent des résultats de recherche pour cet utilisateur pendant trois jours après la modification de l’attribut. De même, il faut jusqu’à trois jours pour que les responsables et les enquêteurs de Coho Winery eDiscovery obtiennent les résultats de recherche de l’utilisateur.
  
**Un gestionnaire eDiscovery peut-il voir le contenu de deux limites de conformité distinctes ?**
  
Oui, cela peut être fait lors de la recherche de boîtes aux lettres Exchange en ajoutant le gestionnaire eDiscovery aux groupes de rôles qui ont une visibilité pour les deux agences. Toutefois, lors de la recherche de sites SharePoint et de comptes OneDrive, un gestionnaire eDiscovery peut rechercher du contenu dans des limites de conformité différentes uniquement si les agences se trouvent dans la même région ou emplacement géographique. **Note:** Cette limitation pour les sites ne s’applique pas à eDiscovery (Premium), car la recherche de contenu dans SharePoint et OneDrive n’est pas liée par emplacement géographique.
  
**Les filtres d’autorisations de recherche fonctionnent-ils pour les conservations de cas eDiscovery, les stratégies de rétention Microsoft 365 ou DLP ?**
  
Non, ce n’est actuellement pas possible.
  
**Si je spécifie une région pour contrôler l’emplacement d’exportation du contenu, mais que je n’ai pas d’organisation SharePoint dans cette région, puis-je toujours rechercher dans SharePoint ?**
  
Si la région spécifiée dans le filtre d’autorisations de recherche n’existe pas dans votre organisation, la région par défaut est recherchée.
  
**Quel est le nombre maximal de filtres d’autorisations de recherche qui peuvent être créés dans une organisation ?**
  
Il n’existe aucune limite au nombre de filtres d’autorisations de recherche qui peuvent être créés dans une organisation. Toutefois, une requête de recherche peut avoir un maximum de 100 conditions. Dans ce cas, une condition est définie comme un élément connecté à la requête par un opérateur booléen (par exemple **, AND**, **OR** et **NEAR**). La limite du nombre de conditions inclut la requête de recherche elle-même, ainsi que tous les filtres d’autorisations de recherche appliqués à l’utilisateur qui exécute la recherche. Par conséquent, plus vous disposez de filtres d’autorisations de recherche (en particulier si ces filtres sont appliqués au même utilisateur ou groupe d’utilisateurs), plus les chances de dépasser le nombre maximal de conditions pour une recherche sont meilleures.

Pour comprendre le fonctionnement de cette limite, vous devez comprendre qu’un filtre d’autorisations de recherche est ajouté à la requête de recherche lors de l’exécution d’une recherche. Un filtre d’autorisations de recherche est joint à la requête de recherche par l’opérateur **AND** Boolean. La logique de requête pour la requête de recherche et un filtre d’autorisations de recherche unique se présenteraient comme suit :

```text
<SearchQuery> AND <PermissionsFilter>
```

Plusieurs filtres d’autorisations de recherche sont combinés par l’opérateur **BOOLEAN OR** , puis ces conditions sont connectées à la requête de recherche par l’opérateur **AND** .

La logique de requête pour la requête de recherche et les filtres d’autorisations de recherche multiples ressemblent à ceci :

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Il est possible que la requête de recherche elle-même se compose de plusieurs conditions connectées par des opérateurs booléens. Chaque condition de la requête de recherche est également comptabilisée dans la limite de 100 conditions.

En outre, le nombre de filtres d’autorisations de recherche ajoutés à une requête dépend de l’utilisateur qui exécute la recherche. Lorsqu’un utilisateur spécifique exécute une recherche, les filtres d’autorisations de recherche qui sont appliqués à l’utilisateur (qui est défini par le paramètre *Utilisateurs* dans le filtre) sont ajoutés à la requête. Votre organisation peut avoir des centaines de filtres d’autorisations de recherche, mais si plus de 100 filtres sont appliqués aux mêmes utilisateurs, il est probable que la limite de 100 conditions soit dépassée lorsque ces utilisateurs exécutent des recherches.

Il y a encore une chose à garder à l’esprit au sujet de la limite de condition. Le nombre de sites SharePoint spécifiques inclus dans les filtres de requêtes de recherche ou d’autorisations de recherche est également comptabilisé dans cette limite. 

Pour empêcher votre organisation d’atteindre la limite des conditions, conservez le nombre de filtres d’autorisations de recherche dans votre organisation le moins possible pour répondre aux besoins de votre entreprise.
