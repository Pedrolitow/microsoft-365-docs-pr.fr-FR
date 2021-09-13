---
title: Utiliser Office 365 réseau de distribution de contenu (CDN) avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Découvrez comment utiliser le Office 365 réseau de distribution de contenu (CDN) pour accélérer la livraison de vos ressources SharePoint Online.
ms.openlocfilehash: 494f0574707693f7d36fa2e1c61ee942e4c088a6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202085"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online

Vous pouvez utiliser le réseau de distribution de contenu Office 365 intégré pour héberger des ressources statiques afin d’améliorer les performances de vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. En outre, le Office 365 CDN utilise le [protocole HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) pour améliorer la compression et le pipelining HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

> [!NOTE]
> Le Office 365 CDN est uniquement disponible pour les clients dans le cloud **de production** (dans le monde). Les locataires du gouvernement des États-Unis, de la Chine et de l’Allemagne ne sont actuellement pas en charge Office 365 CDN.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger sur le réseau de distribution de contenu Office 365, vous pouvez ajouter des origines **publiques**, **privées** ou les deux. Pour [plus d’informations](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) sur la différence entre les origines publique et privée, voir Choisir si chaque origine doit être publique ou privée.

![Office 365 CDN diagramme conceptuel.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 CDN diagramme conceptuel")

Si vous connaissez déjà le mode de travail des CDN, vous ne devez effectuer que quelques étapes pour activer le Office 365 CDN pour votre client. Cette rubrique décrit comment. Lisez la suite pour savoir comment commencer à héberger vos ressources statiques.

> [!TIP]
> Il existe d’autres CDN hébergés par Microsoft qui peuvent être utilisés avec Office 365 pour des scénarios d’utilisation spécialisés, mais qui ne sont pas abordés dans cette rubrique, car ils n’entrent pas dans le cadre du Office 365 CDN. Pour plus d’informations, [voir autres CDN Microsoft.](content-delivery-networks.md#other-microsoft-cdns)

 **Revenir à [la planification réseau et au réglage](./network-planning-and-performance.md)des performances pour Office 365 .**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Vue d’ensemble de l’utilisation Office 365 CDN dans SharePoint Online

Pour configurer les Office 365 CDN pour votre organisation, suivez les étapes de base suivantes :

+ [Planifier le déploiement du Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Déterminez les ressources statiques que vous souhaitez héberger sur le CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Déterminez l’endroit où vous souhaitez stocker vos biens.](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets) Cet emplacement peut être un site SharePoint, une bibliothèque ou un dossier et est appelé une _origine_.
  + [Choisissez si chaque origine doit être publique ou privée.](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) Vous pouvez ajouter plusieurs origines de types public et privé.

+ Installer et configurer le CDN, à l’aide de PowerShell ou de l’SharePoint Online CLI

  + [Configurer l’CDN à l’aide de SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Installer et configurer le CDN à l’aide de PowerShell PnP](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Configurer et configurer le CDN à l’aide de l’Office 365 CLI](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Lorsque vous aurez terminé cette étape, vous aurez :

  + Activé le CDN pour votre organisation.
  + Ajout de vos origines, en identifiant chaque origine comme étant publique ou privée.

Une fois l’installation terminée, vous pouvez gérer les Office 365 CDN [au](use-microsoft-365-cdn-with-spo.md#CDNManage) fil du temps en :

+ Ajout, mise à jour et suppression d’éléments
+ Ajout et suppression d’origines
+ Configuration des stratégies CDN de sécurité
+ Si nécessaire, désactivez le CDN

Enfin, voir [Utiliser vos ressources CDN pour](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) en savoir plus sur l’accès à vos ressources CDN à partir d’origines publiques et privées.

Voir [Résolution des problèmes Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) pour obtenir des conseils sur la résolution des problèmes courants.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planifier le déploiement du Office 365 CDN

Avant de déployer le Office 365 CDN pour votre client Office 365, vous devez prendre en compte les facteurs suivants dans le cadre de votre processus de planification.

  + [Déterminez les ressources statiques que vous souhaitez héberger sur le CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Déterminer l’endroit où vous souhaitez stocker vos biens](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Choisir si chaque origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Déterminez les ressources statiques que vous souhaitez héberger sur le CDN

En règle générale, les CDN sont plus efficaces pour héberger des ressources _statiques_ ou des ressources qui ne changent pas très souvent. Une bonne règle de base consiste à identifier les fichiers qui répondent à une partie ou à l’ensemble de ces conditions :

+ Fichiers statiques incorporés dans une page (tels que des scripts et des images) qui peuvent avoir un impact incrémentielle significatif sur les temps de chargement des pages
+ Fichiers de grande taille tels que les fichiers exécutables et d’installation
+ Bibliothèques de ressources qui la prise en charge du code côté client

Par exemple, les petits fichiers qui sont demandés à plusieurs reprises comme des images de site et des scripts peuvent améliorer considérablement les performances de rendu du site et réduire de manière incrémentielle la charge sur vos sites SharePoint Online lorsque vous les ajoutez à une origine CDN. Les fichiers plus volumineux tels que les fichiers exécutables d’installation peuvent être téléchargés à partir du CDN, ce qui a un impact positif sur les performances et réduit la charge sur votre site SharePoint Online, même s’ils ne sont pas accessibles aussi souvent.

L’amélioration des performances par fichier dépend de nombreux facteurs, notamment la proximité du client avec le point de terminaison CDN le plus proche, les conditions temporaires sur le réseau local, etc. De nombreux fichiers statiques sont relativement petits et peuvent être téléchargés à partir Office 365 en moins d’une seconde. Toutefois, une page web peut contenir de nombreux fichiers incorporés avec un temps de téléchargement cumulé de plusieurs secondes. Le fait de servir ces fichiers à partir CDN réduire considérablement le temps de chargement global de la page. Voir [quels gains de performances un CDN fournir ?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) pour obtenir un exemple.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Déterminer l’endroit où vous souhaitez stocker vos biens

Le CDN récupère vos biens à partir d’un emplacement appelé _origine._ Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL. Vous avez une grande flexibilité lorsque vous spécifiez des origines pour votre organisation. Par exemple, vous pouvez spécifier plusieurs origines ou une origine unique où vous souhaitez placer toutes vos ressources CDN ressources. Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux.

Vous pouvez créer un conteneur pour vos origines, telles que des dossiers ou des bibliothèques de documents, et ajouter des fichiers que vous souhaitez rendre disponibles à partir du CDN. Il s’agit d’une bonne approche si vous avez un ensemble spécifique de ressources que vous souhaitez être disponible à partir du CDN et que vous souhaitez limiter l’ensemble de ressources CDN uniquement à ces fichiers dans le conteneur.

Vous pouvez également configurer une collection de sites, un site, une bibliothèque ou un dossier existant en tant qu’origine, ce qui rend tous les biens éligibles dans le conteneur disponibles à partir du CDN. Avant d’ajouter un conteneur existant en tant qu’origine, il est important de vous assurer de connaître son contenu et ses autorisations afin de ne pas exposer par inadvertance des biens à un accès anonyme ou à des utilisateurs non autorisés.

Vous pouvez définir des _stratégies CDN pour_ exclure le contenu de vos origines du CDN. CDN excluent les biens des origines publiques ou privées par des attributs tels que le _type_ de fichier et la classification de _site_ et sont appliquées à toutes les origines du CdnType (privé ou public) que vous spécifiez dans la stratégie. Par exemple, si vous ajoutez une origine privée constituée d’un site qui contient plusieurs  sous-sites, vous pouvez définir une stratégie pour exclure les sites marqués comme confidentiels afin que le contenu des sites avec cette classification appliquée ne soit pas servi à partir du CDN. La stratégie s’applique au contenu de _toutes les_ origines privées que vous avez ajoutées au CDN.

N’oubliez pas que plus le nombre d’origines est élevé, plus l’impact sur le temps qu’il faut au service CDN pour traiter les demandes est important. Nous vous recommandons de limiter autant que possible le nombre d’origines.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Choisir si chaque origine doit être publique ou privée

Lorsque vous identifiez une origine, vous spécifiez si elle doit être _rendue publique_ ou _privée._ L’accès CDN ressources d’origines publiques est anonyme et CDN contenu des origines privées est sécurisé par des jetons générés dynamiquement pour une sécurité accrue. Quelle que soit l’option que vous choisissez, Microsoft s’charge de toutes les opérations importantes pour vous en ce qui concerne l’administration du CDN lui-même. En outre, vous pouvez changer d’avis ultérieurement, après avoir CDN et identifié vos origines.

Les options publiques et privées offrent des gains de performances similaires, mais chacune possède des attributs et des avantages uniques.

**Les** origines publiques au sein Office 365 CDN sont accessibles de manière anonyme et les ressources hébergées sont accessibles par toute personne ayant l’URL de la bien. Comme l’accès au contenu des origines publiques est anonyme, vous ne devez l’utiliser que pour mettre en cache du contenu générique non sensible, comme des scripts, des icônes, des images et des fichiers JavaScript.

**Les** origines privées au sein Office 365 CDN fournissent un accès privé au contenu utilisateur, tel que SharePoint bibliothèques de documents, sites et images propriétaires en ligne. L’accès au contenu dans les origines privées est sécurisé par des jetons générés dynamiquement afin que seuls les utilisateurs ayant des autorisations d’accès à la bibliothèque de documents ou à l’emplacement de stockage d’origine y accèdent. Les origines privées dans le Office 365 CDN ne peuvent être utilisées que pour le contenu SharePoint Online, et vous pouvez uniquement accéder aux ressources des origines privées via la redirection à partir de votre client SharePoint Online.

Vous pouvez en savoir plus sur CDN’accès aux biens d’une origine privée fonctionne dans Utilisation de [biens dans les origines privées.](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attributs et avantages de l’hébergement de biens dans les origines publiques

+ Les ressources exposées dans une origine publique sont accessibles par tout le monde de manière anonyme.
    > [!IMPORTANT]
    > Vous ne devez jamais placer dans une origine publique des ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation.

+ Si vous supprimez une ressource d’une origine publique, celle-ci reste disponible pendant un maximum de 30 jours à partir du cache. Cependant, nous rendons les liens vers la ressource dans le CDN non valides dans les 15 minutes.

+ Lorsque vous hébergez des feuilles de style (fichiers CSS) depuis une origine publique, vous pouvez utiliser les URI et les chemins d’accès relatifs dans le code. Cela signifie que vous pouvez faire référence à l’emplacement d’images d’arrière-plan et d’autres objets de manière relative, par rapport à l’emplacement de la ressource qui les appelle.

+ Bien que vous pouvez construire l’URL d’une origine publique, vous devez continuer avec précaution et vous assurer d’utiliser la propriété de contexte de page et de suivre les instructions pour ce faire. En effet, si l’accès au CDN devient indisponible, l’URL ne renverra pas automatiquement à votre organisation dans SharePoint Online, ce qui pourrait générer des liens défectueux et d’autres erreurs. L’URL est également sujette à modification, c’est pourquoi elle ne doit pas simplement être codée en dur à sa valeur actuelle.

+ Les types de fichiers par défaut inclus pour les origines publiques sont .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff et .woff2. Vous pouvez spécifier des types de fichiers supplémentaires.

+ Vous pouvez configurer une stratégie pour exclure les biens qui ont été identifiés par les classifications de site que vous spécifiez. Par exemple, vous pouvez choisir d’exclure toutes les ressources marquées comme « confidentiel » ou « accès réservé », même s’il s’agit d’un type de fichier autorisé et qu’elles ont une origine publique.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attributs et avantages de l’hébergement de biens dans des origines privées

+ Les origines privées ne peuvent être utilisées que pour SharePoint en ligne.

+ Les utilisateurs ne peuvent accéder aux biens qu’à partir d’une origine privée s’ils sont autorisés à accéder au conteneur. Vous êtes protégé contre l’accès anonyme à ces ressources.

+ Les biens d’origine privée doivent être référents à partir du client SharePoint Online. L’accès direct aux ressources CDN privées ne fonctionne pas.

+ Si vous supprimez un bien de l’origine privée, il se peut qu’il reste disponible jusqu’à une heure à partir du cache . toutefois, nous invalidons les liens vers la CDN dans les 15 minutes suivant sa suppression.

+ Les types de fichier par défaut inclus pour les origines privées sont les suivants : .gif, .ico, .jpeg, .jpg, .js et .png. Vous pouvez spécifier des types de fichiers supplémentaires.

+ Comme pour les origines publiques, vous pouvez configurer une stratégie pour exclure les biens qui ont été identifiés par des classifications de site que vous spécifiez, même si vous utilisez des caractères génériques pour inclure tous les biens dans un dossier ou une bibliothèque de documents.

Pour plus d’informations sur l’utilisation des concepts de Office 365 CDN, de CDN général et d’autres CDN Microsoft que vous pouvez utiliser avec votre client Office 365, voir Réseaux de distribution de [contenu.](content-delivery-networks.md)

### <a name="default-cdn-origins"></a>Origines CDN par défaut

Sauf indication contraire, Office 365 définit des origines par défaut lorsque vous activez l’Office 365 CDN. Si vous décidez initialement de ne pas les configurer, vous pouvez ajouter ces origines une fois l’installation terminée. Sauf si vous comprenez les conséquences de l’ignorer de la configuration des origines par défaut et que vous en avez une raison spécifique, vous devez autoriser leur création lorsque vous activez l’CDN.

Origines des CDN privées par défaut :

+ \*/userphoto.aspx
+ \*/siteassets

Origines des CDN public par défaut :

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets est_ une origine publique par défaut qui a été ajoutée au service Office 365 CDN en décembre 2017. Cette origine doit être présente pour que les solutions SharePoint Framework dans le CDN fonctionnent. Si vous avez activé le Office 365 CDN avant décembre 2017, ou si vous avez ignoré la configuration des origines par défaut lorsque vous avez activé le CDN, vous pouvez ajouter manuellement cette origine. Pour plus d’informations, voir Mon part Web Part côté client ou SharePoint Framework solution ne [fonctionne pas.](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working)

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Configurer l’Office 365 CDN à l’aide de SharePoint Online Management Shell

Les procédures de cette section nécessitent l’utilisation de SharePoint Online Management Shell pour vous connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Pour configurer et configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de SharePoint Online Management Shell, effectuer ces étapes.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Permettre à votre organisation d’utiliser le Office 365 CDN

Avant d’apporter des modifications aux paramètres de CDN client, vous devez récupérer l’état actuel de la configuration CDN privée dans votre client Office 365 client. Connecter à votre client à l’aide de SharePoint Online Management Shell :

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

À présent, utilisez la cmdlet **Get-SPOTenantCdnEnabled** pour récupérer les paramètres CDN’état du client :

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

L’état du CDN pour le CdnType spécifié est produit à l’écran.

Utilisez la cmdlet **Set-SPOTenantCdnEnabled** pour permettre à votre organisation d’utiliser le Office 365 CDN. Vous pouvez permettre à votre organisation d’utiliser des origines publiques, des origines privées ou les deux à la fois. Vous pouvez également configurer le CDN pour ignorer la configuration des origines par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées, mais ignorer la configuration des origines par défaut, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Voir [Default CDN origins](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.

Pour permettre à votre organisation d’utiliser des origines publiques, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privées, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette cmdlet, voir [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Modifier la liste des types de fichiers à inclure dans le Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de la **cmdlet Set-SPOTenantCdnPolicy,** vous devez supprimer la liste actuellement définie. Si vous souhaitez ajouter des types de fichiers supplémentaires à la liste, utilisez d’abord la cmdlet pour connaître les types de fichiers qui sont déjà autorisés et les inclure dans la liste avec vos nouveaux.

La cmdlet **Set-SPOTenantCdnPolicy** permet de définir des types de fichiers statiques qui peuvent être hébergés par des origines publiques et privées dans le CDN. Par défaut, les types de ressources courants sont autorisés, par exemple .css, .gif, .jpg et .js.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Par exemple, pour activer la CDN héberger les fichiers .css et .png, entrez la commande :

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Pour voir les types de fichiers actuellement autorisés par le CDN, utilisez la cmdlet **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces cmdlets, voir [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) et [Get-SPOTenantCdnPolicies.](/powershell/module/sharepoint-online/)

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Modifier la liste des classifications de site que vous souhaitez exclure du Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous excluez les classifications de site à l’aide de la **cmdlet Set-SPOTenantCdnPolicy,** vous devez supprimer la liste actuellement définie. Si vous souhaitez exclure des classifications de site supplémentaires, utilisez d’abord l’cmdlet pour connaître les classifications qui sont déjà exclues, puis ajoutez-les avec vos nouvelles classifications.

Utilisez la cmdlet **Set-SPOTenantCdnPolicy** pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Pour voir quelles classifications de site sont actuellement restreintes, utilisez la cmdlet **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Les propriétés qui seront renvoyées sont _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ et _ExcludeIfNoScriptDisabled_.

La _propriété IncludeFileExtensions_ contient la liste des extensions de fichier qui seront servies à partir du CDN.

> [!NOTE]
> Les extensions de fichier par défaut sont différentes entre public et privé.

La _propriété ExcludeRestrictedSiteClassifications_ contient les classifications de site que vous souhaitez exclure du CDN. Par exemple, vous pouvez  exclure les sites marqués comme confidentiels afin que le contenu des sites avec cette classification ne soit pas servi à partir du CDN.

La _propriété ExcludeIfNoScriptDisabled_ exclut le contenu du CDN en fonction des paramètres d’attribut _NoScript_ au niveau du site. Par défaut, _l’attribut NoScript_ est activé pour les _sites_ modernes et **désactivé pour** les sites _classiques._  Cela dépend des paramètres de votre client.

Pour plus d’informations sur ces cmdlets, voir [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) et [Get-SPOTenantCdnPolicies.](/powershell/module/sharepoint-online/)

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Ajouter une origine pour vos ressources

Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

> [!IMPORTANT]
> Vous ne devez jamais placer dans une origine publique des ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

La valeur du _chemin d’accès_ est le chemin d’accès relatif à la bibliothèque ou au dossier qui contient les biens. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Les origines peuvent prendre en charge les caractères génériques qui sont précédés de l’URL. Cela vous permet de créer des origines qui s’étendent sur plusieurs sites. Par exemple, pour inclure toutes les ressources dans le dossier masterpages de tous vos sites en tant qu’origine publique dans le CDN, tapez la commande suivante :

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Le modificateur générique * ne peut être utilisé qu’au début du chemin d’accès et correspond à tous les segments d’URL sous **/** l’URL spécifiée.
+ Le chemin d’accès peut pointer vers une bibliothèque de documents, un dossier ou un site. Par exemple, le chemin _d’accès */site1_ correspond à toutes les bibliothèques de documents sous le site.

Vous pouvez ajouter une origine avec un chemin d’accès relatif spécifique. Vous ne pouvez pas ajouter une origine à l’aide du chemin d’accès complet.

Cet exemple ajoute une origine privée de la bibliothèque siteassets sur un site spécifique :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Cet exemple ajoute une origine privée du dossier _folder1_ dans la bibliothèque de biens de site de la collection de sites :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

S’il y a un espace dans le chemin d’accès, vous pouvez soit entourer le chemin d’accès entre guillemets doubles, soit remplacer l’espace par l’URL encodant %20. Les exemples suivants ajoutent une origine privée du dossier _1_ dans la bibliothèque de biens de site de la collection de sites :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> Dans les origines privées, les biens partagés à partir d’une origine doivent avoir une version majeure publiée avant d’être accessibles à partir du CDN.

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple : Configurer une origine publique pour vos pages maîtres et pour votre bibliothèque de styles pour SharePoint Online

Normalement, ces origines sont définies pour vous par défaut lorsque vous activez la Office 365 CDN. Toutefois, si vous souhaitez les activer manuellement, suivez ces étapes.

+ Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’origine publique.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir les pages maîtres en tant qu’origine publique.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple : configurer une origine privée pour les ressources de votre site, les pages de site et les images de publication pour SharePoint Online

+ Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir le dossier des ressources du site en tant qu’origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir le dossier des pages de site en tant qu’origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir le dossier d’images de publication en tant qu’origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour une collection de sites pour SharePoint Online

Utilisez la cmdlet **Add-SPOTenantCdnOrigin** pour définir une collection de sites en tant qu’origine privée. Par exemple :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Vous pouvez voir un message _de configuration en_ attente qui est attendu lorsque le client SharePoint Online se connecte au service CDN client. Cela peut prendre jusqu’à 15 minutes.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Gérer les Office 365 CDN

Une fois que vous avez CDN, vous pouvez apporter des modifications à votre configuration lorsque vous mettez à jour le contenu ou que vos besoins changent, comme décrit dans cette section.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Ajouter, mettre à jour ou supprimer des ressources du Office 365 CDN

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des biens existants à tout moment. Il vous suffit d’apporter vos modifications aux ressources du dossier ou de la bibliothèque SharePoint que vous avez identifiée comme origine. Si vous ajoutez une nouvelle valeur, elle est disponible via le CDN immédiatement. Toutefois, si vous mettez à jour le bien, la propagation de la nouvelle copie et sa mise à disposition dans le CDN prennent jusqu’à 15 minutes.

Si vous devez récupérer l’emplacement de l’origine, vous pouvez utiliser la cmdlet **Get-SPOTenantCdnOrigins.** Pour plus d’informations sur l’utilisation de cette cmdlet, voir [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Supprimer une origine du Office 365 CDN

Vous pouvez supprimer l’accès à un dossier ou une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez la cmdlet **Remove-SPOTenantCdnOrigin.**

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Pour plus d’informations sur l’utilisation de cette cmdlet, voir [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modifier une origine dans le Office 365 CDN

Vous ne pouvez pas modifier une origine que vous avez créée. Supprimez plutôt l’origine, puis ajoutez-en une nouvelle. Pour plus d’informations, [voir Pour supprimer](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) une origine du Office 365 CDN et pour ajouter une origine pour vos [ressources.](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh)

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Désactiver le Office 365 CDN

Utilisez la cmdlet **Set-SPOTenantCdnEnabled** pour désactiver l’CDN pour votre organisation. Si les origines publique et privée sont activées pour le CDN, vous devez exécuter l’cmdlet deux fois comme indiqué dans les exemples suivants.

Pour désactiver l’utilisation des origines publiques dans le CDN, entrez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans le CDN, entrez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette cmdlet, voir [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Installer et configurer le Office 365 CDN à l’aide de PowerShell PnP

Les procédures de cette section exigent que vous utilisez PnP PowerShell pour vous connecter à SharePoint Online. Pour obtenir des instructions, voir [La mise en place de PowerShell PnP.](https://github.com/SharePoint/PnP-PowerShell#getting-started)

Effectuer ces étapes pour configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de PowerShell PnP.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Permettre à votre organisation d’utiliser le Office 365 CDN

Avant d’apporter des modifications aux paramètres de CDN client, vous devez récupérer l’état actuel de la configuration CDN privée dans votre client Office 365 client. Connecter votre client à l’aide de PowerShell PnP :

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

À présent, utilisez la cmdlet **Get-PnPTenantCdnEnabled** pour récupérer les paramètres d’CDN du client :

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

L’état du CDN pour le CdnType spécifié est produit à l’écran.

La cmdlet **Set-PnPTenantCdnEnabled** permet à votre organisation d’utiliser les Office 365 CDN. Vous pouvez permettre à votre organisation d’utiliser des origines publiques, des origines privées ou les deux en même temps. Vous pouvez également configurer le CDN pour ignorer la configuration des origines par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique.

Dans PowerShell PnP :

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées, mais ignorer la configuration des origines par défaut, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Voir [Default CDN origins](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.

Pour permettre à votre organisation d’utiliser des origines publiques, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privées, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette cmdlet, voir [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Modifier la liste des types de fichiers à inclure dans le Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de la **cmdlet Set-PnPTenantCdnPolicy,** vous devez supprimer la liste actuellement définie. Si vous souhaitez ajouter des types de fichiers supplémentaires à la liste, utilisez d’abord la cmdlet pour connaître les types de fichiers qui sont déjà autorisés et les inclure dans la liste avec vos nouveaux.

La cmdlet **Set-PnPTenantCdnPolicy** permet de définir des types de fichiers statiques qui peuvent être hébergés par des origines publiques et privées dans le CDN. Par défaut, les types de ressources courants sont autorisés, par exemple .css, .gif, .jpg et .js.

Dans PowerShell PnP :

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Par exemple, pour activer la CDN héberger les fichiers .css et .png, entrez la commande :

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Pour voir les types de fichiers actuellement autorisés par le CDN, utilisez l’cmdlet **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces cmdlets, voir [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) et [Get-PnPTenantCdnPolicies.](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Modifier la liste des classifications de site que vous souhaitez exclure du Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous excluez les classifications de site à l’aide de **l’cmdlet Set-PnPTenantCdnPolicy,** vous devez supprimer la liste actuellement définie. Si vous souhaitez exclure des classifications de site supplémentaires, utilisez d’abord l’cmdlet pour connaître les classifications qui sont déjà exclues, puis ajoutez-les avec vos nouvelles classifications.

La cmdlet **Set-PnPTenantCdnPolicy** permet d’exclure les classifications de site que vous ne souhaitez pas rendre disponibles sur le CDN. Par défaut, aucune classification de site n’est exclue.

Dans PowerShell PnP :

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Pour voir quelles classifications de site sont actuellement restreintes, utilisez l’cmdlet **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Les propriétés qui seront renvoyées sont _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ et _ExcludeIfNoScriptDisabled_.

La _propriété IncludeFileExtensions_ contient la liste des extensions de fichier qui seront servies à partir du CDN.

> [!NOTE]
> Les extensions de fichier par défaut sont différentes entre public et privé.

La _propriété ExcludeRestrictedSiteClassifications_ contient les classifications de site que vous souhaitez exclure du CDN. Par exemple, vous pouvez  exclure les sites marqués comme confidentiels afin que le contenu des sites avec cette classification ne soit pas servi à partir du CDN.

La _propriété ExcludeIfNoScriptDisabled_ exclut le contenu du CDN en fonction des paramètres d’attribut _NoScript_ au niveau du site. Par défaut, _l’attribut NoScript_ est activé pour les _sites_ modernes et **désactivé pour** les sites _classiques._  Cela dépend des paramètres de votre client.

Pour plus d’informations sur ces cmdlets, voir [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) et [Get-PnPTenantCdnPolicies.](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies)

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Ajouter une origine pour vos ressources

Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

> [!IMPORTANT]
> Vous ne devez jamais placer dans une origine publique des ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

La valeur du _chemin d’accès_ est le chemin d’accès relatif à la bibliothèque ou au dossier qui contient les biens. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Les origines peuvent prendre en charge les caractères génériques qui sont précédés de l’URL. Cela vous permet de créer des origines qui s’étendent sur plusieurs sites. Par exemple, pour inclure toutes les ressources dans le dossier masterpages de tous vos sites en tant qu’origine publique dans le CDN, tapez la commande suivante :

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Le modificateur générique * ne peut être utilisé qu’au début du chemin d’accès et correspond à tous les segments d’URL sous **/** l’URL spécifiée.
+ Le chemin d’accès peut pointer vers une bibliothèque de documents, un dossier ou un site. Par exemple, le chemin _d’accès */site1_ correspond à toutes les bibliothèques de documents sous le site.

Vous pouvez ajouter une origine avec un chemin d’accès relatif spécifique. Vous ne pouvez pas ajouter une origine à l’aide du chemin d’accès complet.

Cet exemple ajoute une origine privée de la bibliothèque de biens de site sur un site spécifique :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Cet exemple ajoute une origine privée du dossier _folder1_ dans la bibliothèque de biens de site de la collection de sites :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

S’il y a un espace dans le chemin d’accès, vous pouvez soit entourer le chemin d’accès entre guillemets doubles, soit remplacer l’espace par l’URL encodant %20. Les exemples suivants ajoutent une origine privée du dossier _1_ dans la bibliothèque de biens de site de la collection de sites :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> Dans les origines privées, les biens partagés à partir d’une origine doivent avoir une version majeure publiée avant d’être accessibles à partir du CDN.

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple : Configurer une origine publique pour vos pages maîtres et pour votre bibliothèque de styles pour SharePoint Online

Normalement, ces origines sont définies pour vous par défaut lorsque vous activez la Office 365 CDN. Toutefois, si vous souhaitez les activer manuellement, suivez ces étapes.

+ Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’origine publique.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir les pages maîtres en tant qu’origine publique.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple : configurer une origine privée pour les ressources de votre site, les pages de site et les images de publication pour SharePoint Online

+ La cmdlet **Add-PnPTenantCdnOrigin** permet de définir le dossier des ressources du site comme une origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir le dossier des pages de site comme une origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir le dossier d’images de publication en tant qu’origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour une collection de sites pour SharePoint Online

Utilisez la cmdlet **Add-PnPTenantCdnOrigin** pour définir une collection de sites en tant qu’origine privée. Par exemple :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, voir [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Vous pouvez voir un message _de configuration en_ attente qui est attendu lorsque le client SharePoint Online se connecte au service CDN client. Cela peut prendre jusqu’à 15 minutes.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Gérer les Office 365 CDN

Une fois que vous avez CDN, vous pouvez apporter des modifications à votre configuration lorsque vous mettez à jour le contenu ou que vos besoins changent, comme décrit dans cette section.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Ajouter, mettre à jour ou supprimer des ressources du Office 365 CDN

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des biens existants à tout moment. Il vous suffit d’apporter vos modifications aux ressources du dossier ou de la bibliothèque SharePoint que vous avez identifiée comme origine. Si vous ajoutez une nouvelle valeur, elle est disponible via le CDN immédiatement. Toutefois, si vous mettez à jour le bien, la propagation de la nouvelle copie et sa mise à disposition dans le CDN prennent jusqu’à 15 minutes.

Si vous avez besoin de récupérer l’emplacement de l’origine, vous pouvez utiliser l’cmdlet **Get-PnPTenantCdnOrigin.** Pour plus d’informations sur l’utilisation de cette cmdlet, voir [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Supprimer une origine du Office 365 CDN

Vous pouvez supprimer l’accès à un dossier ou une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez **l’cmdlet Remove-PnPTenantCdnOrigin.**

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Pour plus d’informations sur l’utilisation de cette cmdlet, voir [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modifier une origine dans le Office 365 CDN

Vous ne pouvez pas modifier une origine que vous avez créée. Supprimez plutôt l’origine, puis ajoutez-en une nouvelle. Pour plus d’informations, [voir Pour supprimer](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) une origine du Office 365 CDN et pour ajouter une origine pour vos [ressources.](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh)

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Désactiver le Office 365 CDN

Utilisez la cmdlet **Set-PnPTenantCdnEnabled** pour désactiver le CDN pour votre organisation. Si les origines publique et privée sont activées pour le CDN, vous devez exécuter l’cmdlet deux fois comme indiqué dans les exemples suivants.

Pour désactiver l’utilisation des origines publiques dans le CDN, entrez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans le CDN, entrez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette cmdlet, voir [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a>Installation et configuration du CDN Office 365 à l’aide de la CLI Office 365

Les procédures de cette section nécessitent que vous avez installé [l’Office 365 CLI](https://aka.ms/o365cli). Ensuite, connectez-vous à Office 365 client à l’aide de la [commande de](https://pnp.github.io/office365-cli/cmd/login/) connexion.

Pour configurer et configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de l’Office 365 CLI, complétez ces étapes.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-the-office-365-cdn"></a>Activer le Office 365 CDN

Vous pouvez gérer l’état du CDN Office 365 dans votre client à l’aide de la commande [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).

Pour activer le CDN public Office 365 dans votre client exécutez la commande suivante :

```cli
spo cdn set --type Public --enabled true
```

Pour activer le Office 365 SharePoint CDN, exécutez :

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Affichage de l’état actuel du CDN Office 365

Pour vérifier si le type particulier de Office 365 CDN est activé ou désactivé, utilisez la commande [get spo cdn.](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/)

Pour vérifier si le CDN public Office 365 est activé, exécutez la commande suivante :

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Afficher les origines Office 365 CDN de l’affichage

Pour afficher les origines actuellement configurées du CDN public Office 365, exécutez la commande suivante :

```cli
spo cdn origin list --type Public
```

Voir [Default CDN’origines pour](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) plus d’informations sur les origines qui sont provisionn es par défaut lorsque vous activez le Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>Ajouter une origine Office 365 CDN’origine

> [!IMPORTANT]
> Vous ne devez jamais placer les ressources qui sont considérées comme sensibles à votre organisation dans une bibliothèque de documents SharePoint configurée en tant qu’origine publique.

Utilisez la commande [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) pour définir une origine de CDN. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Où `path` se trouve le chemin d’accès relatif au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs.

Pour inclure toutes les ressources dans la galerie de **pages** maîtres de tous les sites en tant qu’origine publique, exécutez :

```cli
spo cdn origin add --type Public --origin */masterpage
```

Pour configurer une origine privée pour une collection de sites spécifique, exécutez la commande suivante :

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Après l’ajout d’une origine de CDN, un délai de 15 minutes maximum peut être nécessaire avant que vous ne puissiez récupérer des fichiers par le biais du service de CDN. Vous pouvez vérifier si l’origine spécifique a déjà été activée à l’aide la commande [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).

### <a name="remove-an-office-365-cdn-origin"></a>Supprimer une origine Office 365 CDN’origine

Utilisez la commande [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) pour supprimer une origine de CDN pour le type de CDN spécifié.

Pour supprimer une origine publique de la configuration CDN, exécutez :

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> La suppression d CDN d’une bibliothèque de documents n’affecte pas les fichiers stockés dans une bibliothèque de documents correspondant à cette origine. Si ces ressources ont été référencés à l’aide de leur URL SharePoint, SharePoint revenir automatiquement à l’URL d’origine pointant vers la bibliothèque de documents. Toutefois, si des ressources ont été référencés à l’aide d’une URL CDN publique, la suppression de l’origine va rompre le lien et vous devrez les modifier manuellement.

### <a name="modify-an-office-365-cdn-origin"></a>Modifier une origine Office 365 CDN de données

Il n’est pas possible de modifier une origine de CDN existante. Vous devez plutôt supprimer l’origine de CDN définie précédemment à l’aide de la commande `spo cdn origin remove` et en ajouter une nouvelle à l’aide de la commande `spo cdn origin add`.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Modifier les types de fichiers à inclure dans le Office 365 CDN

Par défaut, les types de fichiers suivants sont inclus dans le CDN : _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff et .woff2_. Si vous devez inclure des types de fichier supplémentaires dans le CDN, vous pouvez modifier la configuration du CDN à l’aide de la commande [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Lorsque vous modifiez la liste des types de fichier, vous remplacez la liste actuellement définie. Pour inclure des types de fichier supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) afin de vérifier les types de fichier qui sont actuellement configurés.

Pour ajouter le type _de fichier JSON_ à la liste par défaut des types de fichiers inclus dans le CDN public, exécutez :

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Modification de la liste des classifications de site que vous souhaitez exclure du CDN Office 365

Utilisez la commande [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

> [!NOTE]
> Lorsque vous modifiez la liste des classifications de site exclues, vous remplacez la liste actuellement définie. Pour exclure des classifications supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) afin de vérifier les classifications qui sont actuellement configurées.

Pour exclure des sites classés _comme HBI_ de l’CDN public, exécutez

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Désactiver le Office 365 CDN

Pour désactiver le CDN Office 365, utilisez la commande `spo cdn set`, par exemple :

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Utilisation de vos ressources CDN de gestion

Maintenant que vous avez activé la CDN et configuré les origines et les stratégies, vous pouvez commencer à utiliser CDN ressources.

Cette section vous aidera à comprendre comment utiliser les URL de CDN dans vos pages et votre contenu SharePoint afin que SharePoint redirige les demandes de ressources des origines publiques et privées vers le CDN.

+ [Mise à jour des liens vers CDN ressources](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Utilisation de biens dans les origines publiques](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Utilisation de biens dans des origines privées](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Pour plus d’informations sur l’utilisation du CDN pour l’hébergement de composants Web Part côté client, voir la rubrique Host [your client-side web part from Office 365 CDN (Hello World Part 4)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

> [!NOTE]
> Si vous ajoutez le dossier _ClientSideAssets_ à la liste CDN origines, les composants Web CDN hébergés par le client ne seront pas restituer.  Les fichiers utilisés par les composants Web Parts SPFX peuvent uniquement utiliser le CDN public et le dossier ClientSideAssets est une origine par défaut pour les CDN.

### <a name="updating-links-to-cdn-assets"></a>Mise à jour des liens vers CDN ressources

Pour utiliser les ressources que vous avez ajoutées à une origine, il vous suffit de mettre à jour les liens vers le fichier d’origine avec le chemin d’accès au fichier dans l’origine.

+ Modifiez la page ou le contenu qui contient des liens vers des ressources que vous avez ajoutées à une origine. Vous pouvez également utiliser l’une des différentes méthodes pour rechercher et remplacer globalement les liens entre un site ou une collection de sites d’entrée si vous souhaitez mettre à jour le lien vers un bien donné partout où il apparaît.
+ Pour chaque lien vers une valeur d’origine, remplacez le chemin d’accès par le chemin d’accès au fichier dans l CDN d’origine. Vous pouvez utiliser des chemins d’accès relatifs.
+ Enregistrez la page ou le contenu.

Par exemple, considérez l’image _/site/SiteAssets/images/image.png_, que vous avez copiée dans le dossier de bibliothèque de documents _/site/CDN_origins/public/_. Pour utiliser la CDN, remplacez le chemin d’accès d’origine à l’emplacement du fichier image par le chemin d’accès à l’origine pour rendre la nouvelle URL _/site/CDN_origins/public/image.png_.

Si vous souhaitez utiliser l’URL complète de la bien au lieu d’un chemin d’accès relatif, construisez le lien de la sorte :

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> En règle générale, vous ne devez pas coder en dur les URL directement dans les ressources de la CDN. Toutefois, vous pouvez créer manuellement des URL pour les ressources dans les origines publiques si nécessaire. Pour plus d’informations, [voir Codage CDN URL pour les biens publics.](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets)

Pour savoir comment vérifier que les biens sont servis à partir du CDN, voir Comment puis-je confirmer que les biens sont [servis](use-microsoft-365-cdn-with-spo.md#CDNConfirm) par le CDN ? dans La résolution des problèmes de Office 365 CDN [.](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting)

### <a name="using-assets-in-public-origins"></a>Utilisation de biens dans les origines publiques

La  fonctionnalité publication dans SharePoint Online réécrit automatiquement les URL des biens stockés dans des origines publiques en leurs équivalents CDN afin que les biens soient servis à partir du service CDN au lieu de SharePoint.

Si votre origine se trouve dans un site où la fonctionnalité publication est activée et que les ressources que vous souhaitez décharger vers le CDN sont dans l’une des catégories suivantes, SharePoint réécrit automatiquement les URL des biens de l’origine, à condition que le bien n’ait pas été exclu par une stratégie CDN.

Voici un aperçu des liens qui sont réécrits automatiquement par la fonctionnalité de publication SharePoint :

+ URL IMG/LINK/CSS dans les réponses HTML de pages de publications classiques
  + Cela comprend les images ajoutées par des auteurs dans le contenu HTML d’une page.
+ URL d’images de composants WebPart de diaporamas de bibliothèque d’images
+ Champs d’image dans les résultats d’API REST SPList (RenderListDataAsStream)
  + Utilisez la nouvelle _propriété ImageFieldsToTryRewriteToCdnUrls_ pour fournir une liste de champs séparés par des virgules
  + Prend en charge les champs lien hypertexte et PublishingImage
+ SharePoint rendus d’image

Le diagramme suivant illustre le flux de travail lorsque SharePoint reçoit une demande de page contenant des biens d’une origine publique.

![Diagramme de flux de travail : récupération Office 365 CDN ressources à partir d’une origine publique.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Flux de travail : récupération de ressources Office 365 CDN d’une origine publique")

> [!TIP]
> Si vous souhaitez désactiver la réécriture automatique pour des URL spécifiques sur une page, vous pouvez consulter la page et ajouter le paramètre de chaîne de requête **? NoAutoReWrites=true** à la fin de chaque lien à désactiver.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Construction d CDN URL pour les biens publics

Si  la fonctionnalité publication n’est pas activée pour une origine publique ou si la bien n’est pas l’un des types de liens pris en charge par la fonctionnalité de réécriture automatique du service CDN, vous pouvez créer manuellement des URL à l’emplacement CDN des ressources et utiliser ces URL dans votre contenu.

> [!NOTE]
> Vous ne pouvez pas coder en dur ou construire des URL CDN sur des ressources d’origine privée, car le jeton d’accès requis qui constitue la dernière section de l’URL est généré au moment où la ressource est demandée. Vous pouvez construire l’URL pour les CDN public et l’URL ne doit pas être codée en dur, car elle est sujette à modification.

Pour les ressources CDN publiques, le format d’URL ressemblera à ce qui suit :

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Remplacez **TenantHostName par** le nom de votre client. Exemple :

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> La propriété de contexte de page doit être utilisée pour construire le préfixe au lieu de coder en dur « https://publiccdn.sharepointonline.com ». L’URL est sujette à modification et ne doit pas être codée en dur. Si vous utilisez des modèles d’affichage avec Classic SharePoint Online, vous pouvez utiliser la propriété « window._spPageContextInfo.publicCdnBaseUrl » dans votre modèle d’affichage pour le préfixe de l’URL. Si vous utilisez des composants Web SPFx pour des SharePoint vous pouvez utiliser la propriété « this.context.pageContext.legacyPageContext.publicCdnBaseUrl ». Cela fournit le préfixe de sorte que s’il est modifié, votre implémentation sera mise à jour avec lui. Par exemple, pour SPFx, l’URL peut être construite à l’aide de la propriété " this.context.pageContext.legacyPageContext.publicCdnBaseUrl » + « / » + « host » + « / » + « relativeURL for the item ». Consultez [l’utilisation CDN code côté client](https://youtu.be/IH1RbQlbhIA) qui fait partie de la série de performances de la campagne [1](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Utilisation de biens dans des origines privées

Aucune configuration supplémentaire n’est requise pour utiliser des biens dans des origines privées. SharePoint Online réécrit automatiquement les URL des biens dans des origines privées afin que les demandes de ces biens soient toujours reçues à partir du CDN. Vous ne pouvez pas créer manuellement des URL pour CDN ressources dans des origines privées, car ces URL contiennent des jetons qui doivent être générés automatiquement par SharePoint Online au moment où le bien est demandé.

L’accès aux biens dans les origines privées est protégé par des jetons générés dynamiquement en fonction des autorisations utilisateur sur l’origine, avec les avertissements décrits dans les sections suivantes. Les utilisateurs doivent au moins **avoir un accès** en lecture aux origines pour CDN pour restituer le contenu.

Le diagramme suivant illustre le flux de travail lorsque SharePoint reçoit une demande pour une page contenant des biens d’une origine privée.

![Diagramme de flux de travail : récupération Office 365 CDN ressources à partir d’une origine privée.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Flux de travail : récupération de ressources Office 365 CDN d’une origine privée")

#### <a name="token-based-authorization-in-private-origins"></a>Autorisation basée sur un jeton dans les origines privées

L’accès aux biens dans les origines privées du Office 365 CDN est accordé par les jetons générés par SharePoint Online. Les utilisateurs qui ont déjà l’autorisation d’accéder au dossier ou à la bibliothèque désigné par l’origine se sont automatiquement vus accorder des jetons qui permettent à l’utilisateur d’accéder au fichier en fonction de son niveau d’autorisation. Ces jetons d’accès sont valides pendant 30 à 90 minutes après qu’ils ont été générés pour empêcher les attaques de relecture de jeton.

Une fois le jeton d’accès généré, SharePoint Online renvoie un URI personnalisé au client contenant deux _paramètres_ d’autorisation (jeton d’autorisation Edge) et un secret _(jeton_ d’autorisation d’origine). La structure de chaque _jeton est<'expiration au format d’heure Époque >__<'>_. Par exemple :

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Toute personne en possession du jeton peut accéder à la ressource dans le CDN. Toutefois, les URL contenant ces jetons d’accès sont partagées uniquement sur HTTPS. Par conséquent, à moins que l’URL ne soit explicitement partagée par un utilisateur final avant l’expiration du jeton, le bien ne sera pas accessible aux utilisateurs non autorisés.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Les autorisations au niveau de l’élément ne sont pas pris en charge pour les biens dans les origines privées

Il est important de noter que SharePoint Online ne prend pas en charge les autorisations au niveau de l’élément pour les biens dans les origines privées. Par exemple, pour un fichier situé à l’emplacement , les utilisateurs ont un accès effectif au fichier `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg` dans les conditions suivantes :

|Utilisateur  |Autorisations  |Accès efficace  |
|---------|---------|---------|
|Utilisateur 1     |A accès à folder1         |Peut accéder image1.jpg à partir du CDN         |
|Utilisateur 2     |N’a pas accès à folder1         |Impossible d'image1.jpg à partir du CDN         |
|Utilisateur 3     |N’a pas accès au dossier 1, mais est autorisé explicitement à accéder image1.jpg dans SharePoint Online         |Peut accéder à l'image1.jpg directement à partir de SharePoint Online, mais pas à partir du CDN         |
|Utilisateur 4     |A accès au dossier 1, mais a été explicitement refusé l’accès image1.jpg dans SharePoint Online         |Impossible d’accéder au bien à partir de SharePoint Online, mais peut y accéder à partir du CDN même si l’accès au fichier n’est pas autorisé dans SharePoint Online         |

<a name="CDNTroubleshooting"> </a>
## <a name="troubleshooting-the-office-365-cdn"></a>Résolution des problèmes de la Office 365 CDN

<a name="CDNConfirm"> </a>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Comment puis-je confirmer que les ressources sont servies par le CDN ?

Une fois que vous avez ajouté des liens vers des ressources CDN à une page, vous pouvez confirmer que le bien est servi à partir du CDN en naviguant jusqu’à la page, en cliquant avec le bouton droit sur l’image une fois qu’elle est restituer et en passant en revue l’URL de l’image.

Vous pouvez également utiliser les outils de développement de votre navigateur pour afficher l’URL de chaque bien sur une page, ou utiliser un outil de suivi réseau tiers.

> [!NOTE]
> Si vous utilisez un outil réseau tel que Fiddler pour tester vos ressources en dehors du rendu de la bien à partir d’une page SharePoint, vous devez ajouter manuellement l’en-tête de référence « Referer: » à la requête GET où l’URL est l’URL racine de votre client `https://yourdomain.sharepoint.com` SharePoint Online.

Vous ne pouvez pas tester CDN URL directement dans un navigateur web, car vous devez avoir un référent provenant de SharePoint Online. Toutefois, si vous ajoutez l’URL de la CDN à une page SharePoint, puis que vous ouvrez la page dans un navigateur, le bien CDN s’affichera sur la page.

Pour plus d’informations sur l’utilisation des outils de développement dans Microsoft Edge navigateur, voir [Microsoft Edge Outils de développement.](/microsoft-edge/devtools-guide)

Pour regarder une courte vidéo hébergée sur la chaîne [YouTube Modèles](https://aka.ms/sppnp-videos) et pratiques du développeur SharePoint montrant comment vérifier que votre CDN fonctionne, voir Vérifier l’utilisation de votre [CDN](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5)et garantir une connectivité réseau optimale.

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Pourquoi les ressources d’une nouvelle origine ne sont-elles pas disponibles ?
Les ressources des nouvelles origines ne seront pas immédiatement disponibles pour une utilisation, car il faut du temps pour que l’inscription se propage dans le CDN et que les ressources soient téléchargées de l’origine vers le stockage CDN. Le temps nécessaire à la mise à disposition des ressources dans le CDN dépend du nombre de ressources et de la taille des fichiers.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Ma solution de serveur Web SharePoint Framework côté client ne fonctionne pas

Lorsque vous activez la Office 365 CDN pour les origines publiques, le service CDN crée automatiquement ces origines par défaut :

+ */MASTERPAGE
+ */BIBLIOTHÈQUE DE STYLES
+ */CLIENTSIDEASSETS

Si l’origine */clientsideassets est manquante, SharePoint Framework solutions de recherche échouent et aucun message d’avertissement ou d’erreur n’est généré. Cette origine peut être manquante soit parce que la CDN a été activée avec le paramètre _-NoDefaultOrigins_ définie sur **$true,** soit parce que l’origine a été supprimée manuellement.

Vous pouvez vérifier les origines présentes avec la commande PowerShell suivante :

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Vous pouvez également vérifier avec l’Office 365 CLI :

```cli
spo cdn origin list
```

Pour ajouter l’origine dans PowerShell :

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Pour ajouter l’origine dans l’Office 365 CLI :

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Quels sont les modules PowerShell et les shells CLI dont je ai besoin pour travailler avec les Office 365 CDN ?

Vous pouvez choisir d’utiliser le Office 365 CDN à l’aide du module **PowerShell SharePoint Online Management Shell** ou de l’Office 365 **CLI**.

+ [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Installation d’Office 365 CLI](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a>Voir aussi

[Réseaux de distribution de contenu](./content-delivery-networks.md)

[Planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md)

[SharePoint Série de performances - série Office 365 CDN vidéo](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
