---
title: Utiliser Office 365 réseau de distribution de contenu (CDN) avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.openlocfilehash: 42836fa8a43b7251be27cfd841b67d47e12b036e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092004"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online

Vous pouvez utiliser le réseau de distribution de contenu Office 365 intégré pour héberger des ressources statiques afin d’améliorer les performances de vos pages SharePoint Online. Le réseau de distribution de contenu Office 365 améliore les performances en procédant à la mise en cache des ressources statiques au plus près des navigateurs qui les demandent, ce qui permet d’accélérer les téléchargements et de réduire la latence. En outre, l’Office 365 CDN utilise le [protocole HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) pour améliorer la compression et le pipeline HTTP. Le réseau de distribution de contenu Office 365 est inclus dans votre abonnement SharePoint Online.

> [!NOTE]
> La Office 365 CDN est uniquement disponible pour les locataires dans le cloud **de production** (dans le monde entier). Les locataires du gouvernement des États-Unis, de la Chine et de l’Allemagne ne prennent actuellement pas en charge les Office 365 CDN.

Le réseau de distribution de contenu Office 365 est composé de plusieurs réseaux de distribution de contenu qui vous permettent d’héberger des ressources statiques à différents emplacements (ou _origines_) et de les servir à partir de réseaux à haut débit mondiaux. Selon le type de contenu que vous souhaitez héberger sur le réseau de distribution de contenu Office 365, vous pouvez ajouter des origines **publiques**, **privées** ou les deux. Pour plus d’informations sur la différence entre les [origines publiques et privées, voir choisir si chaque origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) .

![Office 365 CDN diagramme conceptuel.](../media/O365-CDN/o365-cdn-flow-transparent.png "diagramme conceptuel Office 365 CDN")

Si vous êtes déjà familiarisé avec le fonctionnement des CDN, vous n’avez qu’à effectuer quelques étapes pour activer le Office 365 CDN pour votre locataire. Cette rubrique décrit comment procéder. Lisez la suite pour plus d’informations sur la prise en main de l’hébergement de vos ressources statiques.

> [!TIP]
> D’autres CDN hébergés par Microsoft peuvent être utilisés avec des Office 365 pour des scénarios d’utilisation spécialisés, mais ne sont pas abordés dans cette rubrique, car ils ne sont pas inclus dans le Office 365 CDN. Pour plus d’informations, consultez [Autres CDN Microsoft](content-delivery-networks.md#other-microsoft-cdns).

 **Revenez à [la planification réseau et au réglage des performances pour Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>Vue d’ensemble de l’utilisation des Office 365 CDN dans SharePoint Online

Pour configurer le Office 365 CDN pour votre organisation, procédez comme suit :

+ [Planifier le déploiement du Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [Déterminez les ressources statiques que vous souhaitez héberger sur le CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [Déterminez où stocker vos ressources](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). Cet emplacement peut être un site, une bibliothèque ou un dossier SharePoint et est appelé une _origine_.
  + [Choisissez si chaque origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Vous pouvez ajouter plusieurs origines de types public et privé.

+ Configurez et configurez le CDN à l’aide de PowerShell ou de l’interface CLI pour Microsoft 365

  + [Configurer et configurer le CDN à l’aide de SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [Configurer et configurer le CDN à l’aide de PnP PowerShell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [Configurer et configurer le CDN à l’aide de l’interface CLI pour Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  Une fois cette étape terminée, vous disposerez des fonctionnalités suivantes :

  + Activation de la CDN pour votre organisation.
  + Ajout de vos origines, en identifiant chaque origine comme publique ou privée.

Une fois que vous avez terminé l’installation, vous pouvez [gérer les Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) au fil du temps en :

+ Ajout, mise à jour et suppression de ressources
+ Ajout et suppression d’origines
+ Configuration des stratégies CDN
+ Si nécessaire, désactivez le CDN

Enfin, consultez [Utilisation de vos ressources CDN](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) pour en savoir plus sur l’accès à vos ressources CDN à partir d’origines publiques et privées.

Consultez [résolution des problèmes liés à la Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) pour obtenir des conseils sur la résolution des problèmes courants.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>Planifier le déploiement du Office 365 CDN

Avant de déployer le Office 365 CDN pour votre locataire Office 365, vous devez prendre en compte les facteurs suivants dans le cadre de votre processus de planification.

  + [Déterminer les ressources statiques que vous souhaitez héberger sur le CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [Déterminer l’emplacement de stockage de vos ressources](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [Choisir si chaque origine doit être publique ou privée](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>Déterminer les ressources statiques que vous souhaitez héberger sur le CDN

En général, les CDN sont les plus efficaces pour héberger des _ressources statiques_ ou des ressources qui ne changent pas très souvent. Une bonne règle générale consiste à identifier les fichiers qui remplissent une partie ou l’ensemble de ces conditions :

+ Fichiers statiques incorporés dans une page (comme les scripts et les images) qui peuvent avoir un impact incrémentiel significatif sur les temps de chargement des pages
+ Fichiers volumineux tels que les fichiers exécutables et d’installation
+ Bibliothèques de ressources qui prennent en charge le code côté client

Par exemple, les petits fichiers demandés à plusieurs reprises, tels que les images de site et les scripts, peuvent améliorer considérablement les performances de rendu de site et réduire de manière incrémentielle la charge sur vos sites SharePoint Online lorsque vous les ajoutez à une origine CDN. Les fichiers plus volumineux tels que les exécutables d’installation peuvent être téléchargés à partir du CDN, ce qui a un impact positif sur les performances et réduit la charge sur votre site SharePoint Online, même s’ils ne sont pas accessibles aussi souvent.

L’amélioration des performances par fichier dépend de nombreux facteurs, notamment la proximité du client avec le point de terminaison CDN le plus proche, les conditions temporaires sur le réseau local, etc. De nombreux fichiers statiques sont assez petits et peuvent être téléchargés à partir de Office 365 en moins d’une seconde. Toutefois, une page web peut contenir de nombreux fichiers incorporés avec un temps de téléchargement cumulé de plusieurs secondes. Le service de ces fichiers à partir de la CDN peut réduire considérablement le temps de chargement global de la page. Pour obtenir un exemple, consultez [les gains de performances fournis par un CDN](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide).

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>Déterminer l’emplacement de stockage de vos ressources

Le CDN extrait vos ressources à partir d’un emplacement appelé _origine_. Une origine peut être un site SharePoint, une bibliothèque de documents ou un dossier accessible par une URL. Vous disposez d’une grande flexibilité lorsque vous spécifiez des origines pour votre organisation. Par exemple, vous pouvez spécifier plusieurs origines ou une seule origine où vous souhaitez placer toutes vos ressources CDN. Vous pouvez choisir d’avoir des origines publiques ou privées pour votre organisation. La plupart des organisations choisiront d’implémenter une combinaison des deux.

Vous pouvez créer un conteneur pour vos origines, comme des dossiers ou des bibliothèques de documents, et ajouter des fichiers que vous souhaitez rendre disponibles à partir du CDN. Il s’agit d’une bonne approche si vous avez un ensemble spécifique de ressources que vous souhaitez mettre à disposition à partir de la CDN et que vous souhaitez limiter l’ensemble de ressources CDN uniquement à ces fichiers dans le conteneur.

Vous pouvez également configurer une collection de sites, un site, une bibliothèque ou un dossier existant en tant qu’origine, ce qui rend toutes les ressources éligibles dans le conteneur disponibles à partir de la CDN. Avant d’ajouter un conteneur existant en tant qu’origine, il est important de vous assurer que vous connaissez son contenu et ses autorisations afin de ne pas exposer par inadvertance des ressources à des utilisateurs anonymes ou non autorisés.

Vous pouvez définir _CDN stratégies_ pour exclure du contenu de vos origines du CDN. CDN stratégies excluent les ressources d’origines publiques ou privées par des attributs tels que _le type de fichier_ et la _classification de site_, et sont appliquées à toutes les origines du CdnType (privé ou public) que vous spécifiez dans la stratégie. Par exemple, si vous ajoutez une origine privée composée d’un site qui contient plusieurs sous-sites, vous pouvez définir une stratégie pour exclure les sites marqués comme **confidentiels** afin que le contenu des sites avec cette classification appliquée ne soit pas servi à partir du CDN. La stratégie s’applique au contenu de _toutes les_ origines privées que vous avez ajoutées au CDN.

Gardez à l’esprit que plus le nombre d’origines est élevé, plus l’impact sur le temps nécessaire au service CDN pour traiter les demandes est important. Nous vous recommandons de limiter autant que possible le nombre d’origines.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>Choisir si chaque origine doit être publique ou privée

Lorsque vous identifiez une origine, vous spécifiez si elle doit être rendue _publique_ ou _privée_. L’accès aux ressources CDN dans les origines publiques est anonyme et CDN contenu dans les origines privées est sécurisé par des jetons générés dynamiquement pour une sécurité accrue. Quelle que soit l’option que vous choisissez, Microsoft fait tout le travail pour vous quand il s’agit de l’administration de la CDN elle-même. En outre, vous pouvez changer d’avis ultérieurement, après avoir configuré le CDN et identifié vos origines.

Les options publiques et privées offrent des gains de performances similaires, mais chacune possède des attributs et des avantages uniques.

**Les origines publiques** dans le Office 365 CDN sont accessibles anonymement et les ressources hébergées sont accessibles par toute personne disposant de l’URL de la ressource. Comme l’accès au contenu des origines publiques est anonyme, vous ne devez l’utiliser que pour mettre en cache du contenu générique non sensible, comme des scripts, des icônes, des images et des fichiers JavaScript.

**Les origines privées** dans le Office 365 CDN fournissent un accès privé au contenu utilisateur, tel que SharePoint bibliothèques de documents, sites et images propriétaires en ligne. L’accès au contenu dans les origines privées est sécurisé par des jetons générés dynamiquement afin qu’il soit accessible uniquement aux utilisateurs disposant d’autorisations sur la bibliothèque de documents ou l’emplacement de stockage d’origine. Les origines privées dans le Office 365 CDN ne peuvent être utilisées que pour SharePoint contenu en ligne, et vous pouvez uniquement accéder aux ressources d’origine privée via la redirection à partir de votre locataire SharePoint Online.

Vous pouvez en savoir plus sur le fonctionnement de CDN’accès aux ressources d’une origine privée dans [Using assets in private origins](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>Attributs et avantages de l’hébergement de ressources dans des origines publiques

+ Les ressources exposées dans une origine publique sont accessibles par tout le monde de manière anonyme.
    > [!IMPORTANT]
    > Vous ne devez jamais placer les ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation dans une origine publique.

+ Si vous supprimez une ressource d’une origine publique, celle-ci reste disponible pendant un maximum de 30 jours à partir du cache. Cependant, nous rendons les liens vers la ressource dans le CDN non valides dans les 15 minutes.

+ Lorsque vous hébergez des feuilles de style (fichiers CSS) depuis une origine publique, vous pouvez utiliser les URI et les chemins d’accès relatifs dans le code. Cela signifie que vous pouvez faire référence à l’emplacement d’images d’arrière-plan et d’autres objets de manière relative, par rapport à l’emplacement de la ressource qui les appelle.

+ Bien que vous puissiez construire l’URL d’une origine publique, vous devez faire preuve de prudence et vous assurer d’utiliser la propriété de contexte de page et de suivre les instructions pour ce faire. En effet, si l’accès au CDN devient indisponible, l’URL ne renverra pas automatiquement à votre organisation dans SharePoint Online, ce qui pourrait générer des liens défectueux et d’autres erreurs. L’URL est également susceptible d’être modifiée, ce qui explique pourquoi elle ne doit pas être codée en dur en fonction de sa valeur actuelle.

+ Les types de fichiers par défaut inclus pour les origines publiques sont .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff et .woff2. Vous pouvez spécifier des types de fichiers supplémentaires.

+ Vous pouvez configurer une stratégie pour exclure les ressources identifiées par les classifications de site que vous spécifiez. Par exemple, vous pouvez choisir d’exclure toutes les ressources marquées comme « confidentiel » ou « accès réservé », même s’il s’agit d’un type de fichier autorisé et qu’elles ont une origine publique.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>Attributs et avantages de l’hébergement de ressources dans des origines privées

+ Les origines privées ne peuvent être utilisées que pour les ressources SharePoint Online.

+ Les utilisateurs ne peuvent accéder aux ressources qu’à partir d’une origine privée s’ils ont les autorisations nécessaires pour accéder au conteneur. Vous êtes protégé contre l’accès anonyme à ces ressources.

+ Les ressources d’origine privée doivent être référencées à partir du locataire SharePoint Online. L’accès direct aux ressources CDN privées ne fonctionne pas.

+ Si vous supprimez une ressource de l’origine privée, celle-ci peut continuer à être disponible pendant une heure dans le cache; toutefois, nous invaliderons les liens vers la ressource dans le CDN dans les 15 minutes suivant la suppression de la ressource.

+ Les types de fichier par défaut inclus pour les origines privées sont les suivants : .gif, .ico, .jpeg, .jpg, .js et .png. Vous pouvez spécifier des types de fichiers supplémentaires.

+ Tout comme avec les origines publiques, vous pouvez configurer une stratégie pour exclure les ressources identifiées par les classifications de site que vous spécifiez, même si vous utilisez des caractères génériques pour inclure toutes les ressources dans un dossier ou une bibliothèque de documents.

Pour plus d’informations sur l’utilisation des Office 365 CDN, des concepts CDN généraux et d’autres CDN Microsoft que vous pouvez utiliser avec votre locataire Office 365, consultez [Réseaux de distribution de contenu](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>Origines CDN par défaut

Sauf indication contraire, Office 365 configure certaines origines par défaut lorsque vous activez le Office 365 CDN. Si vous choisissez initialement de ne pas les approvisionner, vous pouvez ajouter ces origines une fois l’installation terminée. Sauf si vous comprenez les conséquences de l’omission de la configuration des origines par défaut et que vous ayez une raison spécifique de le faire, vous devez les autoriser à être créés lorsque vous activez le CDN.

Origines de CDN privées par défaut :

+ \*/userphoto.aspx
+ \*/siteassets

Origines de CDN publiques par défaut :

+ \*/masterpage
+ \*Bibliothèque /style
+ \*/clientsideassets

> [!NOTE]
> _clientsideassets_ est une origine publique par défaut qui a été ajoutée au service Office 365 CDN en décembre 2017. Cette origine doit être présente pour que SharePoint Framework solutions du CDN fonctionnent. Si vous avez activé le Office 365 CDN avant décembre 2017 ou si vous avez ignoré la configuration des origines par défaut lorsque vous avez activé le CDN, vous pouvez ajouter manuellement cette origine. Pour plus [d’informations, consultez Mon composant WebPart côté client ou SharePoint Framework solution ne fonctionne pas](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>Configurer et configurer le Office 365 CDN à l’aide de SharePoint Online Management Shell

Les procédures décrites dans cette section vous obligent à utiliser le SharePoint Online Management Shell pour vous connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Effectuez ces étapes pour configurer et configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de SharePoint Online Management Shell.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Permettre à votre organisation d’utiliser le Office 365 CDN

Avant d’apporter des modifications au locataire CDN paramètres, vous devez récupérer l’état actuel de la configuration de CDN privée dans votre locataire Office 365. Connecter à votre locataire à l’aide de SharePoint Online Management Shell :

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

Utilisez maintenant l’applet de commande **Get-SPOTenantCdnEnabled** pour récupérer les paramètres d’état CDN du locataire :

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

L’état du CDN pour le CdnType spécifié est généré à l’écran.

Utilisez l’applet **de commande Set-SPOTenantCdnEnabled** pour permettre à votre organisation d’utiliser le Office 365 CDN. Vous pouvez autoriser votre organisation à utiliser des origines publiques, des origines privées ou les deux à la fois. Vous pouvez également configurer le CDN pour ignorer la configuration des origines par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées, mais sans configurer les origines par défaut, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Pour plus d’informations sur les origines approvisionnées par défaut lorsque vous activez le Office 365 CDN, et sur l’impact potentiel de l’omission de la configuration des origines par défaut, consultez les [origines CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) par défaut.

Pour permettre à votre organisation d’utiliser des origines publiques, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privées, tapez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette applet de commande, consultez [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Modifier la liste des types de fichiers à inclure dans le Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez ajouter des types de fichiers supplémentaires à la liste, utilisez d’abord l’applet de commande pour déterminer quels types de fichiers sont déjà autorisés et les inclure dans la liste avec vos nouveaux types.

Utilisez l’applet de commande **Set-SPOTenantCdnPolicy** pour définir des types de fichiers statiques qui peuvent être hébergés par des origines publiques et privées dans le CDN. Par défaut, les types de ressources courants sont autorisés, par exemple .css, .gif, .jpg et .js.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Par exemple, pour permettre au CDN d’héberger des fichiers .css et .png, entrez la commande :

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Pour voir quels types de fichiers sont actuellement autorisés par le CDN, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces applets de commande, consultez [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) et [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Modifier la liste des classifications de sites à exclure du Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous excluez des classifications de site à l’aide de l’applet de commande **Set-SPOTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez exclure des classifications de site supplémentaires, utilisez d’abord l’applet de commande pour déterminer quelles classifications sont déjà exclues, puis ajoutez-les avec vos nouvelles classifications.

Utilisez la cmdlet **Set-SPOTenantCdnPolicy** pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

Dans Windows PowerShell pour SharePoint Online :

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

Pour voir quelles classifications de site sont actuellement restreintes, utilisez l’applet de commande **Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

Les propriétés qui seront retournées sont _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ et _ExcludeIfNoScriptDisabled_.

La propriété _IncludeFileExtensions_ contient la liste des extensions de fichier qui seront traitées à partir du CDN.

> [!NOTE]
> Les extensions de fichier par défaut sont différentes entre public et privé.

La propriété _ExcludeRestrictedSiteClassifications_ contient les classifications de site que vous souhaitez exclure du CDN. Par exemple, vous pouvez exclure les sites marqués comme **confidentiels** afin que le contenu des sites avec cette classification appliquée ne soit pas servi à partir de la CDN.

La propriété _ExcludeIfNoScriptDisabled_ exclut le contenu du CDN en fonction des paramètres d’attribut _NoScript_ au niveau du site. Par défaut, l’attribut _NoScript_ est défini sur **Activé** pour les sites _modernes_ et **Désactivé** pour les sites _classiques_ . Cela dépend des paramètres de votre locataire.

Pour plus d’informations sur ces applets de commande, consultez [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) et [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Ajouter une origine pour vos ressources

Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

> [!IMPORTANT]
> Vous ne devez jamais placer les ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation dans une origine publique.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

La valeur du _chemin d’accès_ est le chemin d’accès relatif à la bibliothèque ou au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Origins prend en charge les caractères génériques ajoutés à l’URL. Cela vous permet de créer des origines qui s’étendent sur plusieurs sites. Par exemple, pour inclure toutes les ressources dans le dossier masterpages de tous vos sites en tant qu’origine publique dans le CDN, tapez la commande suivante :

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Le modificateur générique ***/** ne peut être utilisé qu’au début du chemin d’accès et correspond à tous les segments d’URL sous l’URL spécifiée.
+ Le chemin d’accès peut pointer vers une bibliothèque de documents, un dossier ou un site. Par exemple, le chemin _*/site1_ correspond à toutes les bibliothèques de documents sous le site.

Vous pouvez ajouter une origine avec un chemin relatif spécifique. Vous ne pouvez pas ajouter d’origine à l’aide du chemin d’accès complet.

Cet exemple montre comment ajouter une origine privée de la bibliothèque siteassets sur un site spécifique :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Cet exemple montre comment ajouter une origine privée du dossier _folder1_ dans la bibliothèque de ressources de site de la collection de sites :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

S’il y a un espace dans le chemin d’accès, vous pouvez soit entourer le chemin d’accès entre guillemets doubles, soit remplacer l’espace par l’encodage d’URL %20. Les exemples suivants ajoutent une origine privée du _dossier dossier 1_ dans la bibliothèque de ressources de site de la collection de sites :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> Dans les origines privées, les ressources partagées à partir d’une origine doivent avoir une version majeure publiée avant d’être accessibles à partir de la CDN.

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple : Configurer une origine publique pour vos pages maîtres et votre bibliothèque de styles pour SharePoint Online

Normalement, ces origines sont configurées pour vous par défaut lorsque vous activez le Office 365 CDN. Toutefois, si vous souhaitez les activer manuellement, procédez comme suit.

+ Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’origine publique.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir les pages maîtres comme une origine publique.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour vos ressources de site, pages de site et images de publication pour SharePoint Online

+ Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier des ressources du site en tant qu’origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier des pages de site comme une origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir le dossier d’images de publication en tant qu’origine privée.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour une collection de sites pour SharePoint Online

Utilisez l’applet de commande **Add-SPOTenantCdnOrigin** pour définir une collection de sites comme une origine privée. Par exemple :

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Vous pouvez voir un message _de configuration en attente_ qui est attendu lorsque le locataire SharePoint Online se connecte au service CDN. Cela peut prendre jusqu’à 15 minutes.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>Gérer les Office 365 CDN

Une fois que vous avez configuré le CDN, vous pouvez apporter des modifications à votre configuration à mesure que vous mettez à jour le contenu ou que vos besoins changent, comme décrit dans cette section.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Ajouter, mettre à jour ou supprimer des ressources du Office 365 CDN

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des ressources existantes quand vous le souhaitez. Il vous suffit d’apporter vos modifications aux ressources du dossier ou de la bibliothèque SharePoint que vous avez identifiée comme origine. Si vous ajoutez une nouvelle ressource, elle est immédiatement disponible via le CDN. Toutefois, si vous mettez à jour la ressource, il faudra jusqu’à 15 minutes pour que la nouvelle copie se propage et devienne disponible dans le CDN.

Si vous devez récupérer l’emplacement de l’origine, vous pouvez utiliser l’applet de commande **Get-SPOTenantCdnOrigins** . Pour plus d’informations sur l’utilisation de cette applet de commande, consultez [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Supprimer une origine du Office 365 CDN

Vous pouvez supprimer l’accès à un dossier ou à une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez l’applet **de commande Remove-SPOTenantCdnOrigin** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Pour plus d’informations sur l’utilisation de cette applet de commande, consultez [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modifier une origine dans le Office 365 CDN

Vous ne pouvez pas modifier une origine que vous avez créée. Au lieu de cela, supprimez l’origine, puis ajoutez-en une nouvelle. Pour plus d’informations, consultez [Pour supprimer une origine du Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) et [Pour ajouter une origine pour vos ressources](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Désactiver l’Office 365 CDN

Utilisez l’applet **de commande Set-SPOTenantCdnEnabled** pour désactiver le CDN pour votre organisation. Si les origines publiques et privées sont activées pour le CDN, vous devez exécuter l’applet de commande deux fois comme indiqué dans les exemples suivants.

Pour désactiver l’utilisation des origines publiques dans le CDN, entrez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans le CDN, entrez la commande suivante :

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette applet de commande, consultez [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>Configurer et configurer le Office 365 CDN à l’aide de PnP PowerShell

Les procédures décrites dans cette section vous obligent à utiliser PnP PowerShell pour vous connecter à SharePoint Online. Pour obtenir des instructions, consultez [Prise en main de PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).

Effectuez ces étapes pour configurer et configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de PnP PowerShell.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>Permettre à votre organisation d’utiliser le Office 365 CDN

Avant d’apporter des modifications au locataire CDN paramètres, vous devez récupérer l’état actuel de la configuration de CDN privée dans votre locataire Office 365. Connecter à votre locataire à l’aide de PnP PowerShell :

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

Utilisez maintenant l’applet de commande **Get-PnPTenantCdnEnabled** pour récupérer les paramètres d’état CDN du locataire :

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

L’état du CDN pour le CdnType spécifié est généré à l’écran.

Utilisez l’applet **de commande Set-PnPTenantCdnEnabled** pour permettre à votre organisation d’utiliser le Office 365 CDN. Vous pouvez autoriser votre organisation à utiliser des origines publiques, des origines privées ou les deux en même temps. Vous pouvez également configurer le CDN pour ignorer la configuration des origines par défaut lorsque vous l’activez. Vous pouvez toujours ajouter ces origines ultérieurement, comme décrit dans cette rubrique.

Dans PnP PowerShell :

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

Par exemple, pour permettre à votre organisation d’utiliser des origines publiques et privées, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines publiques et privées, mais sans configurer les origines par défaut, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

Pour plus d’informations sur les origines approvisionnées par défaut lorsque vous activez le Office 365 CDN, et sur l’impact potentiel de l’omission de la configuration des origines par défaut, consultez les [origines CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) par défaut.

Pour permettre à votre organisation d’utiliser des origines publiques, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

Pour permettre à votre organisation d’utiliser des origines privées, tapez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

Pour plus d’informations sur cette applet de commande, consultez [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>Modifier la liste des types de fichiers à inclure dans le Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous définissez des types de fichiers à l’aide de l’applet de commande **Set-PnPTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez ajouter des types de fichiers supplémentaires à la liste, utilisez d’abord l’applet de commande pour déterminer quels types de fichiers sont déjà autorisés et les inclure dans la liste avec vos nouveaux types.

Utilisez l’applet de commande **Set-PnPTenantCdnPolicy** pour définir des types de fichiers statiques qui peuvent être hébergés par des origines publiques et privées dans le CDN. Par défaut, les types de ressources courants sont autorisés, par exemple .css, .gif, .jpg et .js.

Dans PnP PowerShell :

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

Par exemple, pour permettre au CDN d’héberger des fichiers .css et .png, entrez la commande :

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

Pour voir quels types de fichiers sont actuellement autorisés par le CDN, utilisez l’applet de commande **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Pour plus d’informations sur ces applets de commande, consultez [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) et [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>Modifier la liste des classifications de sites à exclure du Office 365 CDN (facultatif)

> [!TIP]
> Lorsque vous excluez des classifications de site à l’aide de l’applet de commande **Set-PnPTenantCdnPolicy** , vous remplacez la liste actuellement définie. Si vous souhaitez exclure des classifications de site supplémentaires, utilisez d’abord l’applet de commande pour déterminer quelles classifications sont déjà exclues, puis ajoutez-les avec vos nouvelles classifications.

Utilisez l’applet de commande **Set-PnPTenantCdnPolicy** pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles sur le CDN. Par défaut, aucune classification de site n’est exclue.

Dans PnP PowerShell :

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

Pour voir quelles classifications de site sont actuellement restreintes, utilisez l’applet de commande **Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

Les propriétés qui seront retournées sont _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ et _ExcludeIfNoScriptDisabled_.

La propriété _IncludeFileExtensions_ contient la liste des extensions de fichier qui seront traitées à partir du CDN.

> [!NOTE]
> Les extensions de fichier par défaut sont différentes entre public et privé.

La propriété _ExcludeRestrictedSiteClassifications_ contient les classifications de site que vous souhaitez exclure du CDN. Par exemple, vous pouvez exclure les sites marqués comme **confidentiels** afin que le contenu des sites avec cette classification appliquée ne soit pas servi à partir de la CDN.

La propriété _ExcludeIfNoScriptDisabled_ exclut le contenu du CDN en fonction des paramètres d’attribut _NoScript_ au niveau du site. Par défaut, l’attribut _NoScript_ est défini sur **Activé** pour les sites _modernes_ et **Désactivé** pour les sites _classiques_ . Cela dépend des paramètres de votre locataire.

Pour plus d’informations sur ces applets de commande, consultez [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) et [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>Ajouter une origine pour vos ressources

Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir une origine. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

> [!IMPORTANT]
> Vous ne devez jamais placer les ressources qui contiennent des informations utilisateur ou qui sont considérées comme sensibles à votre organisation dans une origine publique.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

La valeur du _chemin d’accès_ est le chemin d’accès relatif à la bibliothèque ou au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs. Origins prend en charge les caractères génériques ajoutés à l’URL. Cela vous permet de créer des origines qui s’étendent sur plusieurs sites. Par exemple, pour inclure toutes les ressources dans le dossier masterpages de tous vos sites en tant qu’origine publique dans le CDN, tapez la commande suivante :

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ Le modificateur générique ***/** ne peut être utilisé qu’au début du chemin d’accès et correspond à tous les segments d’URL sous l’URL spécifiée.
+ Le chemin d’accès peut pointer vers une bibliothèque de documents, un dossier ou un site. Par exemple, le chemin _*/site1_ correspond à toutes les bibliothèques de documents sous le site.

Vous pouvez ajouter une origine avec un chemin relatif spécifique. Vous ne pouvez pas ajouter d’origine à l’aide du chemin d’accès complet.

Cet exemple montre comment ajouter une origine privée de la bibliothèque de ressources du site sur un site spécifique :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Cet exemple montre comment ajouter une origine privée du dossier _folder1_ dans la bibliothèque de ressources de site de la collection de sites :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

S’il y a un espace dans le chemin d’accès, vous pouvez soit entourer le chemin d’accès entre guillemets doubles, soit remplacer l’espace par l’encodage d’URL %20. Les exemples suivants ajoutent une origine privée du _dossier dossier 1_ dans la bibliothèque de ressources de site de la collection de sites :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> Dans les origines privées, les ressources partagées à partir d’une origine doivent avoir une version majeure publiée avant d’être accessibles à partir de la CDN.

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>Exemple : Configurer une origine publique pour vos pages maîtres et votre bibliothèque de styles pour SharePoint Online

Normalement, ces origines sont configurées pour vous par défaut lorsque vous activez le Office 365 CDN. Toutefois, si vous souhaitez les activer manuellement, procédez comme suit.

+ Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir la bibliothèque de styles en tant qu’origine publique.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir les pages maîtres comme une origine publique.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour vos ressources de site, pages de site et images de publication pour SharePoint Online

+ Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir le dossier des ressources du site comme une origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir le dossier des pages de site comme une origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir le dossier d’images de publication en tant qu’origine privée.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Cela peut prendre jusqu’à 15 minutes.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>Exemple : Configurer une origine privée pour une collection de sites pour SharePoint Online

Utilisez l’applet de commande **Add-PnPTenantCdnOrigin** pour définir une collection de sites comme une origine privée. Par exemple :

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

Pour plus d’informations sur cette commande et sa syntaxe, consultez [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

Une fois que vous avez exécuté la commande, le système synchronise la configuration dans le centre de données. Vous pouvez voir un message _de configuration en attente_ qui est attendu lorsque le locataire SharePoint Online se connecte au service CDN. Cela peut prendre jusqu’à 15 minutes.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>Gérer les Office 365 CDN

Une fois que vous avez configuré le CDN, vous pouvez apporter des modifications à votre configuration à mesure que vous mettez à jour le contenu ou que vos besoins changent, comme décrit dans cette section.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>Ajouter, mettre à jour ou supprimer des ressources du Office 365 CDN

Une fois que vous avez terminé les étapes de configuration, vous pouvez ajouter de nouvelles ressources et mettre à jour ou supprimer des ressources existantes quand vous le souhaitez. Il vous suffit d’apporter vos modifications aux ressources du dossier ou de la bibliothèque SharePoint que vous avez identifiée comme origine. Si vous ajoutez une nouvelle ressource, elle est immédiatement disponible via le CDN. Toutefois, si vous mettez à jour la ressource, il faudra jusqu’à 15 minutes pour que la nouvelle copie se propage et devienne disponible dans le CDN.

Si vous devez récupérer l’emplacement de l’origine, vous pouvez utiliser l’applet de commande **Get-PnPTenantCdnOrigin** . Pour plus d’informations sur l’utilisation de cette applet de commande, consultez [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>Supprimer une origine du Office 365 CDN

Vous pouvez supprimer l’accès à un dossier ou à une bibliothèque SharePoint que vous avez identifié comme origine. Pour ce faire, utilisez l’applet **de commande Remove-PnPTenantCdnOrigin** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

Pour plus d’informations sur l’utilisation de cette applet de commande, consultez [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>Modifier une origine dans le Office 365 CDN

Vous ne pouvez pas modifier une origine que vous avez créée. Au lieu de cela, supprimez l’origine, puis ajoutez-en une nouvelle. Pour plus d’informations, consultez [Pour supprimer une origine du Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) et [Pour ajouter une origine pour vos ressources](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>Désactiver l’Office 365 CDN

Utilisez l’applet **de commande Set-PnPTenantCdnEnabled** pour désactiver le CDN pour votre organisation. Si les origines publiques et privées sont activées pour le CDN, vous devez exécuter l’applet de commande deux fois comme indiqué dans les exemples suivants.

Pour désactiver l’utilisation des origines publiques dans le CDN, entrez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

Pour désactiver l’utilisation des origines privées dans le CDN, entrez la commande suivante :

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

Pour plus d’informations sur cette applet de commande, consultez [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>Configurer et configurer le Office 365 CDN à l’aide de l’interface CLI pour Microsoft 365

Les procédures décrites dans cette section exigent que vous ayez installé l’interface [CLI pour Microsoft 365](https://aka.ms/cli-m365). Ensuite, connectez-vous à votre locataire Office 365 à l’aide de la commande [de connexion](https://pnp.github.io/cli-microsoft365/cmd/login/).

Effectuez ces étapes pour configurer et configurer le CDN pour héberger vos ressources dans SharePoint Online à l’aide de l’interface CLI pour Microsoft 365.

<details>
  <summary>Cliquez pour développer</summary>

### <a name="enable-the-office-365-cdn"></a>Activer le Office 365 CDN

Vous pouvez gérer l’état du CDN Office 365 dans votre client à l’aide de la commande [spo cdn set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

Pour activer le CDN public Office 365 dans votre client exécutez la commande suivante :

```cli
spo cdn set --type Public --enabled true
```

Pour activer le Office 365 SharePoint CDN, exécutez :

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>Affichage de l’état actuel du CDN Office 365

Pour vérifier si le type particulier de Office 365 CDN est activé ou désactivé, utilisez la commande [get spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

Pour vérifier si le CDN public Office 365 est activé, exécutez la commande suivante :

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>Afficher les origines Office 365 CDN

Pour afficher les origines actuellement configurées du CDN public Office 365, exécutez la commande suivante :

```cli
spo cdn origin list --type Public
```

Pour plus d’informations sur les origines approvisionnées par défaut lorsque vous activez le Office 365 CDN, consultez les [origines](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) CDN par défaut.

### <a name="add-an-office-365-cdn-origin"></a>Ajouter une origine Office 365 CDN

> [!IMPORTANT]
> Vous ne devez jamais placer les ressources considérées comme sensibles à votre organisation dans une bibliothèque de documents SharePoint configurée comme une origine publique.

Utilisez la commande [spo cdn origin add](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) pour définir une origine de CDN. Vous pouvez définir plusieurs origines. L’origine est une URL pointant vers un dossier ou une bibliothèque SharePoint qui contient les ressources qui doivent être hébergées par le CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

Où `path` se trouve le chemin d’accès relatif au dossier qui contient les ressources. Vous pouvez utiliser des caractères génériques en plus des chemins d’accès relatifs.

Pour inclure toutes les ressources dans la **galerie de pages maîtres** de tous les sites en tant qu’origine publique, exécutez :

```cli
spo cdn origin add --type Public --origin */masterpage
```

Pour configurer une origine privée pour une collection de sites spécifique, exécutez la commande suivante :

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> Après l’ajout d’une origine de CDN, un délai de 15 minutes maximum peut être nécessaire avant que vous ne puissiez récupérer des fichiers par le biais du service de CDN. Vous pouvez vérifier si l’origine spécifique a déjà été activée à l’aide la commande [spo cdn origin list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/).

### <a name="remove-an-office-365-cdn-origin"></a>Supprimer une origine Office 365 CDN

Utilisez la commande [spo cdn origin remove](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) pour supprimer une origine de CDN pour le type de CDN spécifié.

Pour supprimer une origine publique de la configuration CDN, exécutez :

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> La suppression d’une origine CDN n’affecte pas les fichiers stockés dans une bibliothèque de documents correspondant à cette origine. Si ces ressources ont été référencées à l’aide de leur URL SharePoint, SharePoint revenez automatiquement à l’URL d’origine pointant vers la bibliothèque de documents. Toutefois, si des ressources ont été référencées à l’aide d’une URL de CDN publique, la suppression de l’origine interrompt le lien et vous devrez les modifier manuellement.

### <a name="modify-an-office-365-cdn-origin"></a>Modifier une origine Office 365 CDN

Il n’est pas possible de modifier une origine de CDN existante. Vous devez plutôt supprimer l’origine de CDN définie précédemment à l’aide de la commande `spo cdn origin remove` et en ajouter une nouvelle à l’aide de la commande `spo cdn origin add`.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>Modifier les types de fichiers à inclure dans le Office 365 CDN

Par défaut, les types de fichiers suivants sont inclus dans le CDN : _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, .woff et .woff2_. Si vous devez inclure des types de fichier supplémentaires dans le CDN, vous pouvez modifier la configuration du CDN à l’aide de la commande [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/).

> [!NOTE]
> Lorsque vous modifiez la liste des types de fichier, vous remplacez la liste actuellement définie. Pour inclure des types de fichier supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) afin de vérifier les types de fichier qui sont actuellement configurés.

Pour ajouter le type de fichier _JSON_ à la liste par défaut des types de fichiers inclus dans le CDN public, exécutez :

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>Modification de la liste des classifications de site que vous souhaitez exclure du CDN Office 365

Utilisez la commande [spo cdn policy set](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) pour exclure les classifications de site que vous ne souhaitez pas rendre disponibles via le CDN. Par défaut, aucune classification de site n’est exclue.

> [!NOTE]
> Lorsque vous modifiez la liste des classifications de site exclues, vous remplacez la liste actuellement définie. Pour exclure des classifications supplémentaires, utilisez d’abord la commande [spo cdn policy list](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) afin de vérifier les classifications qui sont actuellement configurées.

Pour exclure des sites classés _HBI_ du CDN public, exécutez

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>Désactiver l’Office 365 CDN

Pour désactiver le CDN Office 365, utilisez la commande `spo cdn set`, par exemple :

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>Utilisation de vos ressources CDN

Maintenant que vous avez activé la CDN et configuré les origines et les stratégies, vous pouvez commencer à utiliser vos ressources CDN.

Cette section vous aidera à comprendre comment utiliser CDN URL dans vos pages et contenus SharePoint afin que SharePoint redirige les demandes de ressources d’origine publique et privée vers le CDN.

+ [Mise à jour des liens vers CDN ressources](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [Utilisation de ressources dans des origines publiques](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [Utilisation de ressources dans des origines privées](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

Pour plus d’informations sur l’utilisation de la CDN pour l’hébergement de composants WebPart côté client, consultez la rubrique [Héberger votre composant WebPart côté client à partir de Office 365 CDN (Hello World partie 4).](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)

> [!NOTE]
> Si vous ajoutez le dossier _ClientSideAssets_ à la liste des origines CDN **privées**, les composants WebPart personnalisés hébergés par CDN ne s’affichent pas. Les fichiers utilisés par les composants WebPart SPFX peuvent uniquement utiliser la CDN publique et le dossier ClientSideAssets est une origine par défaut pour les CDN publiques.

### <a name="updating-links-to-cdn-assets"></a>Mise à jour des liens vers CDN ressources

Pour utiliser les ressources que vous avez ajoutées à une origine, il vous suffit de mettre à jour les liens vers le fichier d’origine avec le chemin d’accès au fichier dans l’origine.

+ Modifiez la page ou le contenu qui contient des liens vers les ressources que vous avez ajoutées à une origine. Vous pouvez également utiliser l’une des méthodes suivantes pour rechercher et remplacer globalement des liens entre un site d’entrée ou une collection de sites si vous souhaitez mettre à jour le lien vers un élément multimédia donné partout où il apparaît.
+ Pour chaque lien vers une ressource dans une origine, remplacez le chemin par le chemin d’accès au fichier dans l’origine CDN. Vous pouvez utiliser des chemins relatifs.
+ Enregistrez la page ou le contenu.

Par exemple, considérez l’image _/site/SiteAssets/images/image.png_, que vous avez copiée dans le dossier de bibliothèque de documents _/site/CDN_origins/public/_. Pour utiliser la ressource CDN, remplacez le chemin d’accès d’origine à l’emplacement du fichier image par le chemin d’accès à l’origine pour créer la nouvelle URL _/site/CDN_origins/public/image.png_.

Si vous souhaitez utiliser l’URL complète de la ressource au lieu d’un chemin relatif, construisez le lien comme suit :

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> En général, vous ne devez pas coder en dur les URL directement dans les ressources du CDN. Toutefois, vous pouvez construire manuellement des URL pour les ressources d’origine publique si nécessaire. Pour plus d’informations, consultez [Hardcoding CDN URL pour les ressources publiques](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

Pour en savoir plus sur la façon de vérifier que les ressources sont traitées à partir de l’CDN, consultez [Comment faire vérifier que les ressources sont traitées par le CDN ?](use-microsoft-365-cdn-with-spo.md#CDNConfirm) dans [la résolution des problèmes de l’Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

### <a name="using-assets-in-public-origins"></a>Utilisation de ressources dans des origines publiques

La **fonctionnalité Publication** dans SharePoint Online réécrit automatiquement les URL des ressources stockées dans des origines publiques vers leurs équivalents CDN afin que les ressources soient traitées à partir du service CDN au lieu de SharePoint.

Si votre origine se trouve dans un site avec la fonctionnalité Publication activée et que les ressources que vous souhaitez décharger vers le CDN se trouvent dans l’une des catégories suivantes, SharePoint réécrivez automatiquement les URL des ressources à l’origine, à condition que la ressource n’ait pas été exclue par une stratégie de CDN.

Voici un aperçu des liens qui sont réécrits automatiquement par la fonctionnalité de publication SharePoint :

+ URL IMG/LINK/CSS dans les réponses HTML de pages de publications classiques
  + Cela comprend les images ajoutées par des auteurs dans le contenu HTML d’une page.
+ URL d’images de composants WebPart de diaporamas de bibliothèque d’images
+ Champs d’image dans les résultats d’API REST SPList (RenderListDataAsStream)
  + Utilisez la nouvelle propriété _ImageFieldsToTryRewriteToCdnUrls_ pour fournir une liste de champs séparés par des virgules
  + Prend en charge les champs de lien hypertexte et les champs PublishingImage
+ rendus d’image SharePoint

Le diagramme suivant illustre le flux de travail lorsque SharePoint reçoit une demande pour une page contenant des ressources d’une origine publique.

![Diagramme de flux de travail : récupération de Office 365 CDN ressources à partir d’une origine publique.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "Flux de travail : récupération de ressources Office 365 CDN à partir d’une origine publique")

> [!TIP]
> Si vous souhaitez désactiver la réécriture automatique pour des URL spécifiques sur une page, vous pouvez consulter la page et ajouter le paramètre de chaîne de requête **? NoAutoReWrites=true** jusqu’à la fin de chaque lien que vous souhaitez désactiver.

#### <a name="constructing-cdn-urls-for-public-assets"></a>Construction d’URL CDN pour les ressources publiques

Si la fonctionnalité _publication_ n’est pas activée pour une origine publique ou si la ressource n’est pas l’un des types de liens pris en charge par la fonctionnalité de réécriture automatique du service CDN, vous pouvez construire manuellement des URL à l’emplacement CDN des ressources et utiliser ces URL dans votre contenu.

> [!NOTE]
> Vous ne pouvez pas encoder ou construire CDN URL sur des ressources d’une origine privée, car le jeton d’accès requis qui forme la dernière section de l’URL est généré au moment où la ressource est demandée. Vous pouvez construire l’URL de la CDN publique et l’URL ne doit pas être codée en dur, car elle est susceptible d’être modifiée.

Pour les ressources CDN publiques, le format d’URL se présente comme suit :

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

Remplacez **TenantHostName par** le nom de votre locataire. Exemple :

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> La propriété de contexte de page doit être utilisée pour construire le préfixe au lieu du codage en dur «https://publiccdn.sharepointonline.com ». L’URL est susceptible d’être modifiée et ne doit pas être codée en dur. Si vous utilisez des modèles d’affichage avec classic SharePoint Online, vous pouvez utiliser la propriété « window._spPageContextInfo.publicCdnBaseUrl » dans votre modèle d’affichage pour le préfixe de l’URL. Si vous êtes SPFx composants WebPart pour les SharePoint modernes et classiques, vous pouvez utiliser la propriété « this.context.pageContext.legacyPageContext.publicCdnBaseUrl ». Cela fournit le préfixe afin que, s’il est modifié, votre implémentation soit mise à jour avec elle. Par exemple, pour SPFx, l’URL peut être construite à l’aide de la propriété « this.context.pageContext.legacyPageContext.publicCdnBaseUrl » + « / » + « host » + « / » + « relativeURL pour l’élément ». Consultez [l’utilisation de CDN dans le code côté client](https://youtu.be/IH1RbQlbhIA) qui fait partie de la [série de performances de la saison 1](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>Utilisation de ressources dans des origines privées

Aucune configuration supplémentaire n’est requise pour utiliser des ressources dans des origines privées. SharePoint Online réécrit automatiquement les URL des ressources d’origine privée afin que les demandes de ces ressources soient toujours traitées à partir du CDN. Vous ne pouvez pas générer manuellement des URL pour CDN ressources dans des origines privées, car ces URL contiennent des jetons qui doivent être générés automatiquement par SharePoint Online au moment où la ressource est demandée.

L’accès aux ressources dans les origines privées est protégé par des jetons générés dynamiquement en fonction des autorisations utilisateur sur l’origine, avec les mises en garde décrites dans les sections suivantes. Les utilisateurs doivent avoir au moins un accès en **lecture** aux origines pour que le CDN affiche le contenu.

Le diagramme suivant illustre le flux de travail quand SharePoint reçoit une demande pour une page contenant des ressources d’une origine privée.

![Diagramme de flux de travail : récupération de Office 365 CDN ressources à partir d’une origine privée.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "Flux de travail : récupération de ressources Office 365 CDN à partir d’une origine privée")

#### <a name="token-based-authorization-in-private-origins"></a>Autorisation basée sur des jetons dans des origines privées

L’accès aux ressources d’origine privée dans le Office 365 CDN est accordé par les jetons générés par SharePoint Online. Les utilisateurs qui ont déjà l’autorisation d’accéder au dossier ou à la bibliothèque désigné par l’origine reçoivent automatiquement des jetons qui permettent à l’utilisateur d’accéder au fichier en fonction de son niveau d’autorisation. Ces jetons d’accès sont valides pendant 30 à 90 minutes après leur génération pour empêcher les attaques par relecture de jetons.

Une fois le jeton d’accès généré, SharePoint Online retourne un URI personnalisé au client contenant deux paramètres d’autorisation _eat_ (jeton d’autorisation edge) et _oat_ (jeton d’autorisation d’origine). La structure de chaque jeton est _<'heure d’expiration au format époque'>__<'>de signature sécurisée_. Par exemple :

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> Toute personne en possession du jeton peut accéder à la ressource dans le CDN. Toutefois, les URL contenant ces jetons d’accès sont partagées uniquement via HTTPS. Par conséquent, à moins que l’URL ne soit explicitement partagée par un utilisateur final avant l’expiration du jeton, la ressource ne sera pas accessible aux utilisateurs non autorisés.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>Les autorisations au niveau de l’élément ne sont pas prises en charge pour les ressources d’origine privée

Il est important de noter que SharePoint Online ne prend pas en charge les autorisations au niveau de l’élément pour les ressources d’origine privée. Par exemple, pour un fichier situé à `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`l’emplacement , les utilisateurs ont un accès effectif au fichier en fonction des conditions suivantes :

|Utilisateur  |Autorisations  |Accès effectif  |
|---------|---------|---------|
|Utilisateur 1     |A accès à dossier1         |Peut accéder à image1.jpg à partir du CDN         |
|Utilisateur 2     |N’a pas accès au dossier1         |Impossible d’accéder à image1.jpg à partir du CDN         |
|Utilisateur 3     |N’a pas accès à dossier1, mais est autorisé explicitement à accéder à image1.jpg dans SharePoint Online         |Peut accéder directement à la image1.jpg de ressources à partir de SharePoint Online, mais pas à partir de la CDN         |
|Utilisateur 4     |A accès à dossier1, mais s’est vu refuser explicitement l’accès à image1.jpg dans SharePoint Online         |Impossible d’accéder à l’élément multimédia à partir de SharePoint Online, mais peut y accéder à partir de la CDN en dépit du refus d’accès au fichier dans SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>Résolution des problèmes liés à la Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>Comment faire confirmer que les biens sont servis par le CDN ?

Une fois que vous avez ajouté des liens vers CDN ressources à une page, vous pouvez vérifier que la ressource est traitée à partir du CDN en accédant à la page, en cliquant avec le bouton droit sur l’image une fois qu’elle a été affichée et en examinant l’URL de l’image.

Vous pouvez également utiliser les outils de développement de votre navigateur pour afficher l’URL de chaque ressource sur une page, ou utiliser un outil de suivi réseau tiers.

> [!NOTE]
> Si vous utilisez un outil réseau tel que Fiddler pour tester vos ressources en dehors du rendu de la ressource à partir d’une page SharePoint, vous devez ajouter manuellement l’en-tête de référent « Referer : `https://yourdomain.sharepoint.com`» à la requête GET où l’URL est l’URL racine de votre locataire SharePoint Online.

Vous ne pouvez pas tester CDN URL directement dans un navigateur web, car vous devez disposer d’un référent provenant de SharePoint Online. Toutefois, si vous ajoutez l’URL de la ressource CDN à une page SharePoint, puis que vous ouvrez la page dans un navigateur, vous verrez la ressource CDN affichée sur la page.

Pour plus d’informations sur l’utilisation des outils de développement dans le navigateur Microsoft Edge, consultez [Microsoft Edge Outils de développement](/microsoft-edge/devtools-guide).

Pour visionner une courte vidéo hébergée dans la [chaîne YouTube SharePoint Developer Patterns and Practices](https://aka.ms/sppnp-videos) montrant comment vérifier que votre CDN fonctionne, consultez [Vérifier votre utilisation CDN et garantir une connectivité réseau optimale](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>Pourquoi les ressources d’une nouvelle origine ne sont-ils pas disponibles ?
Les ressources de nouvelles origines ne seront pas immédiatement disponibles pour être utilisées, car il faut du temps pour que l’inscription se propage via le CDN et que les ressources soient chargées de l’origine vers CDN stockage. Le temps nécessaire pour que les ressources soient disponibles dans le CDN dépend du nombre de ressources et de la taille des fichiers.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>Mon composant WebPart côté client ou ma solution SharePoint Framework ne fonctionne pas

Lorsque vous activez le Office 365 CDN pour les origines publiques, le service CDN crée automatiquement les origines par défaut suivantes :

+ */MASTERPAGE
+ */BIBLIOTHÈQUE DE STYLE
+ */CLIENTSIDEASSETS

Si l’origine */clientsideassets est manquante, SharePoint Framework solutions échouent et aucun message d’avertissement ou d’erreur n’est généré. Cette origine peut être manquante soit parce que le CDN a été activé avec le paramètre _-NoDefaultOrigins_ défini sur **$true**, soit parce que l’origine a été supprimée manuellement.

Vous pouvez vérifier quelles origines sont présentes avec la commande PowerShell suivante :

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

Vous pouvez également vérifier auprès de l’interface CLI Office 365 :

```cli
spo cdn origin list
```

Pour ajouter l’origine dans PowerShell :

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

Pour ajouter l’origine dans l’interface CLI Office 365 :

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>Quels modules PowerShell et interpréteurs de commandes CLI dois-je utiliser avec le Office 365 CDN ?

Vous pouvez choisir d’utiliser le Office 365 CDN à l’aide du module PowerShell **SharePoint Online Management Shell** ou de **l’interface CLI Office 365**.

+ [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [Installation d’Office 365 CLI](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>Voir aussi

[Réseaux de distribution de contenu](./content-delivery-networks.md)

[Planification réseau et optimisation des performances pour Office 365](./network-planning-and-performance.md)

[SharePoint Performance Series - série vidéo Office 365 CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
