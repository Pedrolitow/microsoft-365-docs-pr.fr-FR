---
title: Configurer les limites de conformité pour les enquêtes eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
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
ms.openlocfilehash: 8b19347ad8e1c87d5b66cb49ed2af152b4765c37
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311915"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>Configurer les limites de conformité pour les enquêtes eDiscovery

Les instructions de cet article peuvent être appliquées lors de l’utilisation de core eDiscovery ou de Advanced eDiscovery pour gérer les enquêtes.

Les limites de conformité créent des limites logiques au sein d’une organisation qui contrôlent les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les comptes OneDrive et les sites SharePoint) que les gestionnaires eDiscovery peuvent rechercher. En outre, les limites de conformité contrôlent les personnes qui peuvent accéder aux cas eDiscovery utilisés pour gérer les enquêtes juridiques, des ressources humaines ou d’autres enquêtes au sein de votre organisation. La nécessité de frontières de conformité est souvent nécessaire pour les entreprises multinationales qui doivent respecter les réglementations et les réglementations géographiques et pour les gouvernements, qui sont souvent divisés en différentes agences. Dans Microsoft 365, les limites de conformité vous aident à répondre à ces exigences lors de recherches de contenu et de gestion d’enquêtes avec des cas eDiscovery.
  
Nous utilisons l’exemple de l’illustration suivante pour expliquer le fonctionnement des limites de conformité.
  
![Les limites de conformité sont constituées de filtres d’autorisations de recherche qui contrôlent l’accès aux agences et aux groupes de rôles d’administrateur qui contrôlent l’accès aux cas eDiscovery](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
Dans cet exemple, Contoso LTD est une organisation constituée de deux filiales, Fourth Coffee et Coho Winery. L’entreprise exige que les gestionnaires et enquêteurs eDiscovery ne peuvent rechercher que les boîtes aux lettres Exchange, les comptes OneDrive et les sites SharePoint dans leur agence. En outre, les gestionnaires et enquêteurs eDiscovery peuvent uniquement voir les cas eDiscovery dans leur agence, et ils peuvent uniquement accéder aux cas dont ils sont membres. En outre, dans ce scénario, les enquêteurs ne peuvent pas placer des emplacements de contenu en attente ou exporter du contenu à partir d’un cas. Voici comment les limites de conformité répondent à ces exigences.
  
- La fonctionnalité de filtrage des autorisations de recherche dans la recherche de contenu contrôle les emplacements de contenu que les gestionnaires et enquêteurs eDiscovery peuvent rechercher. Cela signifie que les gestionnaires et enquêteurs eDiscovery de l’Agence Fourth Coffee peuvent uniquement rechercher des emplacements de contenu dans la filiale Fourth Coffee. La même restriction s’applique à la filiale de Coho Winery.

- Les groupes de rôles fournissent les fonctions suivantes pour les limites de conformité :

  - Contrôler les personnes qui peuvent voir les cas eDiscovery dans le Centre de sécurité & conformité. Cela signifie que les gestionnaires et enquêteurs eDiscovery peuvent uniquement consulter les dossiers eDiscovery de leur agence.

  - Contrôler qui peut affecter des membres à un cas eDiscovery. Cela signifie que les gestionnaires et enquêteurs eDiscovery peuvent uniquement affecter des membres à des cas dont ils sont eux-mêmes membres.

  - Contrôler les tâches liées à eDiscovery que les membres peuvent effectuer en ajoutant ou en supprimant des rôles qui attribuent des autorisations spécifiques.

Voici le processus de configuration des limites de conformité :
  
[Étape 1 : Identifier un attribut utilisateur pour définir vos agences](#step-1-identify-a-user-attribute-to-define-your-agencies)

[Étape 2 : Déposez une demande au support Microsoft pour synchroniser l’attribut utilisateur avec OneDrive comptes](#step-2-file-a-request-with-microsoft-support-to-synchronize-the-user-attribute-to-onedrive-accounts)

[Étape 3 : Créer un groupe de rôles pour chaque agence](#step-3-create-a-role-group-for-each-agency)

[Étape 4 : Créer un filtre d’autorisations de recherche pour appliquer la limite de conformité](#step-4-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[Étape 5 : Créer un cas eDiscovery pour les enquêtes intra-agence](#step-5-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Avant de configurer les limites de conformité

Vous devez respecter les conditions préalables suivantes pour que l’attribut Azure Active Directory (Azure AD) que vous identité (à l’étape 1) puisse être synchronisé avec succès sur le compte OneDrive d’un utilisateur (à l’étape 2) :

- Une licence d’Exchange Online et une licence SharePoint Online doivent être attribuées aux utilisateurs.

- La taille des boîtes aux lettres utilisateur doit être d’au moins 10 Mo. Si la boîte aux lettres d’un utilisateur est inférieure à 10 Mo, l’attribut utilisé pour définir vos agences ne sera pas synchronisé sur le compte OneDrive utilisateur.

- Les limites de conformité et les attributs utilisés pour créer des filtres d’autorisations de recherche nécessitent que les attributs Azure Active Directory (Azure AD) soient synchronisés avec les boîtes aux lettres des utilisateurs. Pour vérifier que les attributs que vous souhaitez utiliser ont été synchronisés, exécutez l’cmdlet [Get-User](/powershell/module/exchange/get-user) dans Exchange Online PowerShell. La sortie de cette cmdlet affiche les attributs Azure AD synchronisés avec Exchange Online.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>Étape 1 : Identifier un attribut utilisateur pour définir vos agences

La première étape consiste à choisir un attribut Azure AD à utiliser pour définir vos agences. Cet attribut est utilisé pour créer le filtre d’autorisations de recherche qui limite un gestionnaire eDiscovery à rechercher uniquement les emplacements de contenu des utilisateurs affectés à une valeur spécifique pour cet attribut. Par exemple, supposons que Contoso décide d’utiliser l’attribut **Department.** La valeur de cet attribut pour les utilisateurs de la filiale Fourth Coffee serait et celle des utilisateurs de la filiale Coho Winery serait  `FourthCoffee` `CohoWinery` . À l’étape 4, vous utilisez cette  `attribute:value`  paire (par exemple, *Department:FourthCoffee)* pour limiter les emplacements de contenu utilisateur que les gestionnaires eDiscovery peuvent rechercher. 
  
Voici une liste des attributs utilisateur Azure AD que vous pouvez utiliser pour les limites de conformité :
  
- Société

- CustomAttribute1 - CustomAttribute15

- Service

- Bureau

- C (code pays à deux lettres) <sup>*</sup>

  > [!NOTE]
  > <sup>*</sup>Cet attribut est mapué à la propriété CountryOrRegion renvoyée en exécutant l’cmdlet **Get-User** dans Exchange Online PowerShell. La cmdlet renvoie le nom du pays traduit à partir du code de pays à deux lettres. Pour plus d’informations, voir la description du paramètre CountryOrRegion dans l’article de référence de la cmdlet [Set-User.](/powershell/module/exchange/set-user)

Bien que d’autres attributs utilisateur soient disponibles, en particulier pour Exchange boîtes aux lettres, les attributs répertoriés ci-dessus sont les seuls actuellement pris en charge par OneDrive.
  
## <a name="step-2-file-a-request-with-microsoft-support-to-synchronize-the-user-attribute-to-onedrive-accounts"></a>Étape 2 : Déposez une demande au support Microsoft pour synchroniser l’attribut utilisateur avec OneDrive comptes

L’étape suivante consiste à déposer une demande au support Microsoft pour synchroniser l’attribut Azure AD que vous avez choisi à l’étape 1 sur tous les comptes OneDrive de votre organisation. Une fois cette synchronisation entreprise, l’attribut (et sa valeur) que vous avez choisi à l’étape 1 sera mappé à une propriété gérée masquée nommée `ComplianceAttribute` . Vous utilisez cet attribut pour créer le filtre d’autorisations de recherche OneDrive à l’étape 4.
  
Incluez les informations suivantes lorsque vous envoyez la demande au support Microsoft :
  
- Nom de domaine par défaut de votre organisation

- Nom de l’attribut Azure AD (à partir de l’étape 1)

- Titre ou description suivant de l’objectif de la demande de support : « Activer la synchronisation OneDrive Entreprise avec Azure AD pour les filtres de sécurité de conformité ». Cela permet d’router la demande vers l’équipe d’ingénierie eDiscovery qui implémente la demande.

Une fois la modification d’ingénierie réalisée et l’attribut synchronisé avec OneDrive, le Support Microsoft vous envoie le numéro de build dans laquelle la modification a été réalisée et une date de déploiement estimée. Le processus de déploiement prend généralement de 4 à 6 semaines après l’envoi de la demande de support.
  
> [!IMPORTANT]
> Vous pouvez effectuer les étapes 3 à 5 avant de déployer cette modification d’attribut. Toutefois, l’exécution de recherches de contenu ne retournera pas de documents à partir de comptes OneDrive spécifiés dans un filtre d’autorisations de recherche tant que la synchronisation d’attributs n’a pas été déployée.
  
## <a name="step-3-create-a-role-group-for-each-agency"></a>Étape 3 : Créer un groupe de rôles pour chaque agence

L’étape suivante consiste à créer les groupes de rôles dans le Centre de sécurité & conformité qui s’alignera sur vos agences. Nous vous recommandons de créer un groupe de rôles en copiant le groupe des gestionnaires eDiscovery intégrés, en ajoutant les membres appropriés et en supprimant des rôles qui peuvent ne pas être applicables à vos besoins. Pour plus d’informations sur les rôles liés à eDiscovery, voir [Attribuer des autorisations eDiscovery.](assign-ediscovery-permissions.md)
  
Pour créer les groupes de rôles, accédez à la page **Autorisations** dans le Centre de sécurité et conformité et créez un groupe de rôles pour chaque équipe de chaque agence qui utilisera des limites de conformité et des cas eDiscovery pour gérer les enquêtes.
  
À l’aide du scénario de limites de conformité Contoso, quatre groupes de rôles doivent être créés et les membres appropriés ajoutés à chacun d’eux.
  
- Gestionnaires eDiscovery de Fourth Coffee

- Enquêteurs Fourth Coffee

- Gestionnaires eDiscovery de Coho Winery

- Enquêteurs Coho Winery
  
Pour répondre aux exigences du scénario de limites de  conformité  de Contoso, vous devez également supprimer les rôles de mise en attente et d’exportation des groupes de rôles d’enquêteurs pour empêcher les enquêteurs de placer des emplacements de contenu en attente et d’exporter du contenu à partir d’un cas.

## <a name="step-4-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>Étape 4 : Créer un filtre d’autorisations de recherche pour appliquer la limite de conformité

Une fois que vous avez créé des groupes de rôles pour chaque agence, l’étape suivante consiste à créer les filtres d’autorisations de recherche qui associent chaque groupe de rôles à son agence spécifique et définit la limite de conformité elle-même. Vous devez créer un filtre d’autorisations de recherche pour chaque agence. Pour plus d’informations sur la création de filtres d’autorisations de sécurité, voir Configurer le filtrage des [autorisations pour la recherche de contenu.](permissions-filtering-for-content-search.md)
  
Voici la syntaxe utilisée pour créer un filtre d’autorisations de recherche utilisé pour les limites de conformité.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<ComplianceAttribute>  -eq '<AttributeVale> '", "Site_<ComplianceAttribute>  -eq '<AttributeValue>' -or Site_Path -like '<SharePointURL>*'" -Action <Action >
```

Voici une description de chaque paramètre de la commande :
  
- `FilterName`: spécifie le nom du filtre. Utilisez un nom qui décrit ou identifie l’agence dans qui le filtre est utilisé.

- `Users`: spécifie les utilisateurs ou les groupes qui obtiennent ce filtre appliqué aux actions de recherche qu’ils effectuent. Pour les limites de conformité, ce paramètre spécifie les groupes de rôles (que vous avez créés à l’étape 3) dans l’agence pour qui vous créez le filtre. Notez qu’il s’agit d’un paramètre à valeurs multiples qui vous permet d’inclure un ou plusieurs groupes de rôles, séparés par des virgules.

- `Filters`: spécifie les critères de recherche pour le filtre. Pour les limites de conformité, vous définissez les filtres suivants. Chacun d’eux s’applique à un emplacement de contenu. 

    - `Mailbox`: spécifie les boîtes aux lettres que les groupes de rôles définis dans le  `Users` paramètre peuvent rechercher. Pour les limites de conformité,  *ComplianceAttribute*  est le même attribut que celui que vous avez identifié à l’étape 1 et  *AttributeValue*  spécifie l’agence. Ce filtre permet aux membres du groupe de rôles de rechercher uniquement les boîtes aux lettres d’une agence spécifique . par exemple, `"Mailbox_Department -eq 'FourthCoffee'"` . 

    - `Site`: spécifie les comptes OneDrive que les groupes de rôles définis dans le `Users` paramètre peuvent rechercher. Pour le OneDrive, utilisez la chaîne `ComplianceAttribute` réelle. Cette opération est m moire sur le même attribut que celui que vous avez identifié à l’étape 1 et qui est synchronisé avec les comptes OneDrive suite à la demande de support que vous avez soumise à l’étape 2 ; *AttributeValue* spécifie l’agence. Ce filtre permet aux membres du groupe de rôles de rechercher uniquement les comptes OneDrive dans une agence spécifique . par exemple, `"Site_ComplianceAttribute -eq 'FourthCoffee'"` .

    - `Site_Path`: spécifie les sites SharePoint que les groupes de rôles définis dans le `Users` paramètre peuvent rechercher. *SharePointURL* spécifie les sites de l’agence que les membres du groupe de rôles peuvent rechercher. Par exemple : `"Site_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee*'"`. Notez que `Site` les `Site_Path` filtres et les filtres sont connectés par **un opérateur -or.**

     > [!NOTE]
     > La syntaxe du paramètre `Filters` inclut une *liste de filtres.* Une liste de filtres est un filtre qui inclut un filtre de boîte aux lettres et un filtre de site séparés par une virgule. Dans l’exemple précédent, notez qu’une virgule sépare **Mailbox_ComplianceAttribute** et **Site_ComplianceAttribute**: `-Filters "Mailbox_<ComplianceAttribute>  -eq '<AttributeVale> '", "Site_ComplianceAttribute  -eq '<AttributeValue>' -or Site_Path -like '<SharePointURL>*'"` . Lorsque ce filtre est traitée pendant l’exécution d’une recherche de contenu, deux filtres d’autorisations de recherche sont créés à partir de la liste des filtres : un filtre de boîte aux lettres et un filtre de site. Une alternative à l’utilisation d’une liste de filtres serait de créer deux filtres d’autorisations de recherche distincts pour chaque agence : un filtre d’autorisations de recherche pour l’attribut de boîte aux lettres et un filtre pour les attributs de site. Dans les deux cas, les résultats seront identiques. L’utilisation d’une liste de filtres ou la création de filtres d’autorisations de recherche distincts est une question de préférence.

- `Action`: spécifie le type d’action de recherche à l’application du filtre. Par exemple, appliquerait le filtre uniquement lorsque les membres du groupe de rôles défini dans le paramètre  `-Action Search` `Users` exécutent une recherche. Dans ce cas, le filtre ne serait pas appliqué lors de l’exportation des résultats de recherche. Pour les limites de conformité, utilisez  `-Action All` le filtre pour qu’il s’applique à toutes les actions de recherche. 

    Pour obtenir la liste des actions de recherche, consultez la section « New-ComplianceSecurityFilter » dans Configurer le filtrage des [autorisations pour la](permissions-filtering-for-content-search.md#new-compliancesecurityfilter)recherche de contenu.

Voici quelques exemples de deux filtres d’autorisations de recherche qui seraient créés pour prendre en charge le scénario de limites de conformité Contoso. Ces deux exemples incluent une liste de filtres séparés par des virgules, dans laquelle les filtres de boîte aux lettres et de site sont inclus dans le même filtre des autorisations de recherche et sont séparés par une virgule.
  
### <a name="fourth-coffee"></a>Fourth Coffee

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "Site_ComplianceAttribute -eq 'FourthCoffee' -or Site_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee*'" -Action ALL
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "Site_ComplianceAttribute -eq 'CohoWinery' -or Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'" -Action ALL
```

## <a name="step-5-create-an-ediscovery-case-for-intra-agency-investigations"></a>Étape 5 : Créer un cas eDiscovery pour les enquêtes intra-agence

L’étape finale consiste à créer un cas eDiscovery principal ou un cas Advanced eDiscovery dans le centre de conformité Microsoft 365, puis à ajouter le groupe de rôles que vous avez créé à l’étape 3 en tant que membre du cas. Cela se traduit par deux caractéristiques importantes de l’utilisation des limites de conformité :
  
- Seuls les membres du groupe de rôles ajouté au cas pourront voir et accéder au cas dans le Centre de sécurité & conformité. Par exemple, si le groupe de rôles Enquêteurs fourth coffee est le seul membre d’un cas, les membres du groupe de rôles Fourth Coffee eDiscovery Managers (ou les membres d’un autre groupe de rôles) ne pourront pas voir ou accéder au cas.

- Lorsqu’un membre du groupe de rôles affecté à un cas exécute une recherche associée au cas, il peut uniquement rechercher les emplacements de contenu au sein de son agence (qui est défini par le filtre d’autorisations de recherche que vous avez créé à l’étape 4.)

Pour créer un cas et affecter des membres :

1. Go to the **Core eDiscovery** or **Advanced eDiscovery** page in the Microsoft 365 compliance center and create a case.

2. Dans la liste des cas, cliquez sur le nom du cas que vous avez créé.

3. Ajoutez des groupes de rôles en tant que membres au cas. Pour obtenir des instructions, consultez l’un des articles suivants :

   - [Ajouter des membres à un cas core eDiscovery](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

   - [Ajouter des membres à un cas d Advanced eDiscovery un dossier](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Lorsque vous ajoutez un groupe de rôles à un cas, vous ne pouvez ajouter que les groupes de rôles dont vous êtes membre.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Recherche et exportation de contenu dans des environnements multigé géographiques

Les filtres d’autorisations de recherche vous permettent également de contrôler l’emplacement où le contenu est acheminé pour l’exportation et le centre de données qui peut être recherché lors de la recherche d’emplacements de contenu [dans un environnement SharePoint Multi-Géo.](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)
  
- **Exporter les résultats de recherche :** Vous pouvez exporter les résultats de la recherche à partir Exchange boîtes aux lettres, SharePoint sites et OneDrive comptes à partir d’un centre de données spécifique. Cela signifie que vous pouvez spécifier l’emplacement du centre de données à partir de quel emplacement les résultats de la recherche seront exportés.

    Utilisez le **paramètre Region** pour les cmdlets **New-ComplianceSecurityFilter** ou **Set-ComplianceSecurityFilter** pour créer ou modifier le centre de données par lequel l’exportation sera acheminée.
  
    |**Valeur du paramètre**|**Emplacement du centre de données**|
    |:-----|:-----|
    |NAM  <br/> |Amérique du Nord (les centres de données sont aux États-Unis)  <br/> |
    |EUR  <br/> |Europe  <br/> |
    |APC  <br/> |Asie-Pacifique  <br/> |
    |CAN <br/> |Canada|
    |||

- **Router les recherches de contenu :** Vous pouvez router les recherches de contenu SharePoint sites et OneDrive comptes vers un centre de données satellite. Cela signifie que vous pouvez spécifier l’emplacement du centre de données où les recherches seront exécutés.

    Utilisez l’une des valeurs suivantes pour le paramètre **Region** pour contrôler l’emplacement du centre de données où les recherches s’exécuteront lors de la recherche SharePoint sites et OneDrive comptes. 
  
    |**Valeur du paramètre**|**Emplacements de routage du centre de données pour SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |États-Unis  <br/> |
    |EUR  <br/> |Europe  <br/> |
    |APC  <br/> |Asie-Pacifique  <br/> |
    |CAN  <br/> |États-Unis  <br/> |
    |AUS  <br/> |Asie-Pacifique  <br/> |
    |KOR  <br/> |Centre de données par défaut de l’organisation  <br/> |
    |GBR  <br/> |Europe  <br/> |
    |JPN  <br/> |Asie-Pacifique  <br/> |
    |IND  <br/> |Asie-Pacifique  <br/> |
    |LAM  <br/> |États-Unis  <br/> |
    |NOR  <br/> |Europe |
    |ER  <br/> |Centres de données d’Amérique du Nord |
    |||

   Si vous ne spécifiez pas le paramètre **Region** pour un filtre d’autorisations de recherche, le principal SharePoint de l’organisation sera recherché. Les résultats de la recherche sont exportés vers le centre de données le plus proche.

   Pour simplifier le concept, le paramètre **Region** contrôle le centre de données utilisé pour rechercher du contenu dans SharePoint et OneDrive. Cela ne s’applique pas à la recherche de contenu dans Exchange, car Exchange recherche de contenu ne sont pas liées par l’emplacement géographique des centres de données. En outre, la même **valeur de** paramètre Region peut également dicter le centre de données par le biais de qui les exportations sont acheminées. Cela est souvent nécessaire pour contrôler le déplacement des données entre les boarders géographiques.

> [!NOTE]
> Si vous utilisez Advanced eDiscovery, le paramètre **Region** ne contrôle pas la région à partir de celle à partir de qui les données sont exportées. Les données sont exportées à partir du centre de données principal de l’organisation. En outre, la recherche de contenu dans SharePoint et OneDrive n’est pas liée par l’emplacement géographique des centres de données. Tous les centres de données sont recherchés. Pour plus d’informations Advanced eDiscovery, voir Vue d’ensemble de la [solution Advanced eDiscovery dans Microsoft 365](overview-ediscovery-20.md).

Voici des exemples d’utilisation du **paramètre Region** lors de la création de filtres d’autorisation de recherche pour les limites de conformité. Cela suppose que la filiale Fourth Coffee est située en Amérique du Nord et que Coho Winery se trouve en Europe. 
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "Site_Department -eq 'FourthCoffee' -or Site_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee*'" -Action ALL -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "Site_Department -eq 'CohoWinery' -or Site_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'" -Action ALL -Region EUR
```

Gardez les points suivants à l’esprit lors de la recherche et de l’exportation de contenu dans des environnements multigé géographiques.
  
- Le paramètre **Région** ne contrôle pas les recherches dans les boîtes aux lettres Exchange. Tous les centres de données sont recherchés lorsque vous recherchez des boîtes aux lettres. Pour limiter l’étendue de Exchange boîtes aux lettres de recherche, utilisez le paramètre **Filters** lors de la création ou de la modification d’un filtre d’autorisations de recherche. 

- S’il est nécessaire qu’un gestionnaire eDiscovery recherche dans plusieurs régions SharePoint, vous devez créer un compte d’utilisateur différent pour ce gestionnaire eDiscovery à utiliser dans le filtre d’autorisations de recherche pour spécifier la région où se trouvent les sites SharePoint ou les comptes OneDrive. Pour plus d’informations sur cette configuration, voir la section « Recherche de contenu dans un environnement SharePoint Multi-Géo de contenu » dans la recherche [de contenu.](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment)

- Lors de la recherche de contenu dans SharePoint et OneDrive, le paramètre **Region** dirige les recherches vers l’emplacement principal ou satellite où le gestionnaire eDiscovery effectuera des enquêtes eDiscovery. Si un gestionnaire eDiscovery recherche des sites SharePoint et OneDrive en dehors de la région spécifiée dans le filtre des autorisations de recherche, aucun résultat de recherche n’est renvoyé.

- Lors de l’exportation des résultats de recherche, le contenu de tous les emplacements de contenu (y compris les Exchange, Skype Entreprise, SharePoint, OneDrive et autres services que vous pouvez rechercher à l’aide de l’outil de recherche de contenu) est téléchargé vers l’emplacement stockage Azure dans le centre de données spécifié par le paramètre **Region.** Cela permet aux organisations de rester conformes en ne permettant pas l’exportation de contenu à travers des bordures contrôlées. Si aucune région n’est spécifiée dans le filtre des autorisations de recherche, le contenu est téléchargé vers le centre de données principal de l’organisation.

- Vous pouvez modifier un filtre d’autorisations de recherche existant pour ajouter ou modifier la région en exécutant la commande suivante :

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Utilisation des limites de conformité pour SharePoint sites hub

[SharePoint sites hub](/sharepoint/dev/features/hub-site/hub-site-overview) s’alignent souvent sur les mêmes limites géographiques ou d’agence que les limites de conformité eDiscovery. Cela signifie que vous pouvez utiliser la propriété ID de site du site hub pour créer une limite de conformité. Pour ce faire, utilisez la cmdlet [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) dans SharePoint Online PowerShell pour obtenir le SiteId du site hub, puis utilisez cette valeur pour la propriété ID de service pour créer un filtre d’autorisations de recherche.

Utilisez la syntaxe suivante pour créer un filtre d’autorisations de recherche pour SharePoint site hub :

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'" -Action ALL
```

Voici un exemple de création d’un filtre d’autorisations de recherche pour un site hub pour l’agence Coho Winery :

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'" -Action ALL
```

## <a name="compliance-boundary-limitations"></a>Limites de conformité

Gardez les limitations suivantes à l’esprit lors de la gestion des cas eDiscovery et des enquêtes qui utilisent des limites de conformité.
  
- Lors de la création et de l’exécution d’une recherche, vous pouvez sélectionner des emplacements de contenu extérieurs à votre organisation. Toutefois, en raison du filtre d’autorisation de recherche, le contenu de ces emplacements n’est pas inclus dans les résultats de recherche.

- Les limites de conformité ne s’appliquent pas aux cas de découverte électronique. Cela signifie qu’un gestionnaire eDiscovery dans une agence peut placer un utilisateur dans une autre agence en attente. Toutefois, la limite de conformité est appliquée si le gestionnaire eDiscovery recherche les emplacements du contenu de l'utilisateur mis en attente. Cela signifie que le gestionnaire eDiscovery ne pourra pas effectuer de recherche dans les emplacements de contenu des utilisateurs, même s’il a pu mettre l’utilisateur en attente.

    De plus, les statistiques de conservation s’appliquent uniquement aux emplacements de contenu au sein de l’agence.

- Les filtres d’autorisation de recherche ne sont pas appliqués aux dossiers publics Exchange.

## <a name="more-information"></a>Plus d’informations

- Si une boîte aux lettres est supprimée de licence ou supprimée (logiciel), les attributs Azure AD ne sont plus synchronisés avec la boîte aux lettres. Si une conservation a été placée sur la boîte aux lettres lors de sa suppression, le contenu conservé dans la boîte aux lettres est toujours soumis à une limite de conformité ou à un filtre d’autorisations de recherche en fonction de la dernière synchronisation des attributs Azure AD avant la suppression de la boîte aux lettres. 

    En outre, la synchronisation entre la boîte aux lettres de l’utilisateur et le compte OneDrive cessera si la boîte aux lettres est supprimée (sans licence) ou supprimée (logiciel). La dernière valeur estampillée de l’attribut de conformité du compte OneDrive reste en vigueur.

- L’attribut de conformité est synchronisé à partir de la boîte aux lettres Exchange’un utilisateur vers son compte OneDrive tous les sept jours. Comme indiqué précédemment, cette synchronisation se produit uniquement lorsque l’utilisateur est affecté à la fois à une licence Exchange Online et SharePoint Online et que la boîte aux lettres de l’utilisateur est d’au moins 10 Mo.

- Si des limites de conformité et des filtres d’autorisations de recherche sont implémentés pour la boîte aux lettres et le compte OneDrive d’un utilisateur, nous vous recommandons de ne pas supprimer la boîte aux lettres d’un utilisateur et non son compte OneDrive. En d’autres termes, si vous supprimez la boîte aux lettres d’un utilisateur, vous devez également supprimer le compte OneDrive utilisateur.

- Il existe des situations (par exemple, un employé de retour) dans lesquelles un utilisateur peut avoir au moins deux OneDrive comptes. Dans ce cas, seul le compte OneDrive associé à l’utilisateur dans Azure AD sera synchronisé.

- Les limites de conformité et les filtres d’autorisations de recherche dépendent des attributs marqués sur le contenu dans Exchange, OneDrive et SharePoint et de l’indexation suivante de ce contenu marqué. 

- Nous vous déconseillons d’utiliser des filtres d’exclusion (par exemple, dans un filtre d’autorisations de recherche) pour une limite de conformité `-not()` basée sur le contenu. L’utilisation d’un filtre d’exclusion peut avoir des résultats inattendus si le contenu avec des attributs récemment mis à jour n’a pas été indexé. 

## <a name="frequently-asked-questions"></a>Foire aux questions

**Qui pouvez créer et gérer des filtres d’autorisations de recherche (à l’aide New-ComplianceSecurityFilter et Set-ComplianceSecurityFilter cmdlets) ?**
  
Pour créer, afficher et modifier des filtres d’autorisations de recherche, vous devez être membre du groupe de rôles Gestion de l’organisation dans le Centre de sécurité & conformité.
  
**Si un gestionnaire eDiscovery est affecté à plusieurs groupes de rôles qui s’étendent sur plusieurs agences, comment recherchent-ils du contenu dans une agence ou l’autre ?**
  
Le gestionnaire eDiscovery peut ajouter des paramètres à sa requête de recherche qui limitent la recherche à une agence spécifique. Par exemple, si une organisation a spécifié la propriété **CustomAttribute10** pour différencier les agences, elle peut l’appendre à sa requête de recherche pour rechercher des boîtes aux lettres et des comptes OneDrive dans une agence spécifique : `CustomAttribute10:<value> AND Site_ComplianceAttribute:<value>`
  
**Que se passe-t-il si la valeur de l’attribut utilisé comme attribut de conformité dans un filtre d’autorisations de recherche est modifiée ?**
  
Un filtre d’autorisations de recherche met jusqu’à trois jours pour appliquer la limite de conformité si la valeur de l’attribut utilisé dans le filtre est modifiée. Par exemple, dans le scénario Contoso, supposons qu’un utilisateur de l’agence Fourth Coffee est transféré vers l’agence Coho Winery. Par conséquent, la valeur de l’attribut **Department** sur l’objet utilisateur est modifiée de *FourthCoffee* à *CohoWinery*. Dans ce cas, fourth coffee eDiscovery et les investisseurs obtiennent les résultats de recherche pour cet utilisateur pendant trois jours après la changement de l’attribut. De même, il faut jusqu’à trois jours pour que les gestionnaires et enquêteurs eDiscovery de Coho Winery obtiennent les résultats de recherche de l’utilisateur.
  
**Un gestionnaire eDiscovery peut-il voir le contenu à partir de deux limites de conformité distinctes ?**
  
Oui, cette opération peut être effectuée lors de la recherche Exchange boîtes aux lettres en ajoutant le gestionnaire eDiscovery à des groupes de rôles qui ont une visibilité pour les deux agences. Toutefois, lorsque vous recherchez des sites SharePoint et des comptes OneDrive, un gestionnaire eDiscovery peut rechercher du contenu dans différentes limites de conformité uniquement si les agences se trouve dans le même emplacement géographique ou régional. **Remarque :** Cette limitation pour les sites ne s’applique pas dans Advanced eDiscovery car la recherche de contenu dans SharePoint et OneDrive n’est pas liée par un emplacement géographique.
  
**Les filtres d’autorisations de recherche fonctionnent-ils pour les conservations de cas eDiscovery, Microsoft 365 stratégies de rétention ou DLP ?**
  
Non, pas pour le moment.
  
**Si je spécifie une région pour contrôler l’endroit où le contenu est exporté, mais que je n’ai pas d’organisation SharePoint dans cette région, puis-je toujours effectuer des recherches SharePoint ?**
  
Si la région spécifiée dans le filtre des autorisations de recherche n’existe pas dans votre organisation, la région par défaut est recherché.
  
**Quel est le nombre maximal de filtres d’autorisations de recherche qui peuvent être créés dans une organisation ?**
  
Il n’existe aucune limite au nombre de filtres d’autorisations de recherche qui peuvent être créés dans une organisation. Toutefois, les performances de recherche seront impactées lorsqu’il existe plus de 100 filtres d’autorisations de recherche. Pour que le nombre de filtres d’autorisations de recherche dans votre organisation reste le plus petit possible, créez des filtres qui combinent des règles pour Exchange, SharePoint et OneDrive dans un seul filtre d’autorisations de recherche dans la mesure du possible.