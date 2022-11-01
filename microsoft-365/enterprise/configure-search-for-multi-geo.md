---
title: Configurer la recherche pour Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: tlarsen
author: tklarsen
manager: arnek
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.custom: seo-marvel-mar2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Découvrez comment configurer la recherche dans un environnement multigéographique. Seuls certains clients, tels que OneDrive, peuvent retourner des résultats dans un environnement multigéographique.
ms.openlocfilehash: 2cd31d6b5b5b4f6b957741b8b9209c7693ca169f
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804639"
---
# <a name="configure-search-for-microsoft-365-multi-geo"></a>Configurer la recherche pour Microsoft 365 Multi-Geo

## <a name="configure-multi-geo-search"></a>Configurer la recherche multigéographique

Votre _locataire_ multigéographique disposera de fonctionnalités de recherche agrégée permettant à une requête de recherche de retourner des résultats à partir de n’importe où dans le _locataire_.

Par défaut, les recherches effectuées à partir de ces points d’entrée retournent des résultats agrégés, même si chaque index de recherche se trouve dans son emplacement _Geography_ approprié :

- OneDrive Entreprise
- Delve
- Page d’accueil SharePoint
- Centre de recherche

En outre, les fonctionnalités de recherche multigéographique peuvent être configurées pour vos applications de recherche personnalisées qui utilisent l’API de recherche SharePoint.

Consultez [Configurer la recherche pour OneDrive Entreprise Multi-Géo](configure-search-for-multi-geo.md) pour obtenir des instructions, y compris des informations sur les limitations et les différences.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validation de la configuration de Microsoft 365 Multi-Geo

Voici certains cas d’utilisation de base que vous pourriez vouloir inclure dans votre plan de validation avant de déployer à grande échelle Microsoft 365 Multi-Geo dans votre entreprise. Une fois que vous avez terminé ces tests et les cas d’utilisation supplémentaires éventuels et pertinents pour votre entreprise, vous pouvez choisir de commencer à ajouter des utilisateurs à votre groupe pilote initial.

OneDrive Entreprise :

Sélectionnez OneDrive dans le lanceur d’applications Microsoft 365 et vérifiez que vous êtes automatiquement dirigé vers l’emplacement _Géographique_ approprié pour l’utilisateur, en fonction du PDL de l’utilisateur. OneDrive Entreprise doit maintenant commencer à être approvisionné à cet emplacement. Après l’approvisionnement, essayez de charger et de télécharger quelques documents.

Application mobile OneDrive :

Connectez-vous à votre application mobile OneDrive avec vos informations d’identification de compte de test. Confirmez que vous pouvez voir vos fichiers OneDrive Entreprise et que vous pouvez interagir avec eux à partir de votre appareil mobile.

Synchronisation OneDrive client :

Vérifiez que le client Synchronisation OneDrive détecte automatiquement votre emplacement _OneDrive Entreprise Geography_ lors de la connexion. Si vous devez télécharger le client de synchronisation, vous pouvez cliquer sur **Synchroniser** dans la bibliothèque OneDrive.

Applications Office :

Vérifiez que vous pouvez accéder à OneDrive Entreprise en vous connectant à partir d’une application Office, telle que Word. Ouvrez l’application Office et sélectionnez **OneDrive – \<TenantName\>**. Office détecte votre emplacement OneDrive et affiche les fichiers que vous pouvez ouvrir.

Partage:

Essayez de partager des fichiers OneDrive. Vérifiez que le sélecteur de personnes affiche tous vos utilisateurs SharePoint Online, quel que soit leur emplacement _géographique_ .

Dans un environnement multigéographique, chaque emplacement _Geography_ a son propre index de recherche et son propre centre de recherche. Lorsqu’un utilisateur effectue une recherche, la requête est distribuée à tous les index et les résultats renvoyés sont fusionnés.

Par exemple, un utilisateur dans un emplacement _Geography_ peut rechercher du contenu stocké dans un autre emplacement _Geography_ , ou du contenu sur un site SharePoint limité à un autre emplacement Geography. Si l’utilisateur a accès à ce contenu, la recherche affiche le résultat.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>Quels clients de recherche fonctionnent dans un environnement multigéographique ?

Ces clients peuvent retourner les résultats de tous les emplacements Geography :

- OneDrive
- Delve
- Page d’accueil SharePoint
- Centre de recherche
- Applications de recherche personnalisée qui utilisent l’API de recherche SharePoint

### <a name="onedrive"></a>OneDrive

Dès que l’environnement multigéographique a été configuré, les utilisateurs qui effectuent une recherche dans OneDrive obtiennent les résultats de tous les emplacements _Geography_ .

### <a name="delve"></a>Delve

Dès que l’environnement multigéographique a été configuré, les utilisateurs qui effectuent une recherche dans Delve obtiennent les résultats de tous les emplacements _Geography_ .

Le flux Delve et la fiche de profil n’affichent que les aperçus de fichiers stockés dans l’emplacement central. Pour les fichiers stockés dans des emplacements _géographiques satellites_ , l’icône du type de fichier s’affiche à la place.

### <a name="the-sharepoint-home-page"></a>Page d’accueil SharePoint

Dès que l’environnement multigéographique a été configuré, les utilisateurs verront les actualités, les sites récents et suivis de plusieurs emplacements _Geography_ sur leur page d’accueil SharePoint. S’ils utilisent la zone de recherche de la page d’accueil SharePoint, ils obtiendront des résultats fusionnés à partir de plusieurs emplacements _Geography_ .

### <a name="the-search-center"></a>Centre de recherche

Une fois l’environnement multigéographique configuré, chaque centre de recherche continue d’afficher uniquement les résultats de son propre emplacement _géographique_ . Les administrateurs doivent [modifier les paramètres de chaque centre de recherche](#_Set_up_a_1) pour obtenir les résultats de tous les emplacements _Geography_ . Ensuite, les utilisateurs qui effectuent une recherche dans le Centre de recherche obtiennent les résultats de tous les emplacements _Geography_ .

### <a name="custom-search-applications"></a>Applications de recherche personnalisée

Comme d’habitude, les applications de recherche personnalisées interagissent avec les index de recherche à l’aide des API REST recherche SharePoint existantes. Pour obtenir des résultats à partir de tous ou de certains emplacements _Geography_ , l’application doit [appeler l’API et inclure les nouveaux paramètres de requête multigéographique](#_Get_custom_search) dans la requête. Cela déclenche un ventilateur hors de la requête vers tous les emplacements _Geography_ .

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>Qu’est-ce qui diffère de la recherche dans un environnement multigéographique ?

Certaines fonctionnalités de recherche auxquelles vous êtes habitué fonctionnent différemment dans un environnement multigéographique.

<table>
<thead>
<tr class="header">
<th align="left">Fonctionnalité</th>
<th align="left">Mode de fonctionnement</th>
<th align="left">Solution de contournement</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Résultats promus</td>
<td align="left">Vous pouvez créer des règles de requête avec des résultats promus à différents niveaux : pour l’ensemble du _locataire_, pour une collection de sites ou pour un site. Dans un environnement multigéographique, définissez les résultats promus au niveau _du locataire_ pour promouvoir les résultats dans les centres de recherche dans tous les emplacements _Geography_ . Si vous souhaitez uniquement promouvoir les résultats dans le Centre de recherche situé à l’emplacement _Geography_ de la collection de sites ou du site, définissez les résultats promus au niveau de la collection de sites ou du site. Ces résultats ne sont pas promus dans d’autres emplacements _Geography_ .</td>
<td align="left">Si vous n’avez pas besoin de résultats promus différents par emplacement _Geography_ , par exemple des règles différentes pour les déplacements, nous vous recommandons de définir des résultats promus au niveau _du locataire_ .</td>
</tr>
<tr class="even">
<td align="left">Affinements de la recherche</td>
<td align="left">La recherche retourne des affinements à partir de tous les emplacements _Geography_ d’un _locataire_ , puis les agrège. L’agrégation est un effort optimal, ce qui signifie que le nombre d’affinements peut ne pas être précis à 100 %. Pour la plupart des scénarios pilotés par la recherche, cette précision est suffisante.
</td>
<td align="left">Pour les applications pilotées par la recherche qui dépendent de l’exhaustivité de l’affinement, interrogez chaque emplacement _Geography_ indépendamment.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">La recherche multigéographique ne prend pas en charge le compartimentage dynamique pour les affinements numériques.</td>
<td align="left">Utilisez le <a href="/sharepoint/dev/general-development/query-refinement-in-sharepoint">paramètre « Discretize »</a> pour les affinements numériques.</td>
</tr>
<tr class="even">
<td align="left">ID de document</td>
<td align="left">Si vous développez une application pilotée par la recherche qui dépend des ID de document, notez que les ID de document dans un environnement multigéographique ne sont pas uniques entre les emplacements _Géographiques_ , mais sont uniques par emplacement _Geography_ .</td>
<td align="left">Nous avons ajouté une colonne qui identifie l’emplacement _Geography_ . Utilisez cette colonne pour atteindre l’unicité. Cette colonne est nommée « GeoLocationSource ».</td>
</tr>
<tr class="odd">
<td align="left">Nombre de résultats</td>
<td align="left">La page des résultats de la recherche affiche les résultats combinés des emplacements _Geography_ , mais il n’est pas possible de mettre en page au-delà de 500 résultats.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Recherche hybride</td>
<td align="left">Dans un environnement SharePoint hybride avec <a href="/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">recherche hybride dans le cloud</a>, le contenu local est ajouté à l’index Microsoft 365 de l’emplacement central.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>Quels sont les éléments qui ne sont pas pris en charge par la recherche dans un environnement multigéographique ?

Certaines fonctionnalités de recherche auxquelles vous êtes habitué ne sont pas prises en charge dans un environnement multigéographique.

<table>
<thead>
<tr class="header">
<th align="left">Fonctionnalité de recherche</th>
<th align="left">Remarque</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Authentification d’application uniquement</td>
<td align="left">L’authentification d’application uniquement (accès privilégié depuis les services) n’est pas prise en charge dans la recherche multigéographique.</td>
</tr>
<tr class="even">
<td align="left">Invités</td>
<td align="left">Les invités obtiennent uniquement les résultats de l’emplacement _Geography_ à partir duquel ils effectuent des recherches.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>Comment fonctionne la recherche dans un environnement Multi-Géo ?

Tous les clients de recherche utilisent les API REST de recherche SharePoint existantes pour interagir avec les index de recherche.

![Diagramme montrant comment les API REST Recherche SharePoint interagissent avec les index de recherche.](../media/configure-search-for-multi-geo-image1-1.png)

1. Un client de recherche appelle le point de terminaison REST de recherche avec la propriété de requête EnableMultiGeoSearch= true.
2. La requête est envoyée à tous les emplacements _Geography_ dans le _locataire_.
3. Les résultats de la recherche de chaque emplacement _Geography_ sont fusionnés et classés.
4. Le client obtient des résultats de recherche unifiés.

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notez que nous ne fusionnons pas les résultats de recherche avant d’avoir reçu les résultats de tous les emplacements géographiques. Cela signifie que les recherches géographiques multiples souffrent d’une latence supplémentaire par rapport aux recherches dans un environnement ne comportant qu’un seul emplacement géographique.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Obtenir un centre de recherche pour afficher les résultats de tous les emplacements géographiques

Chaque centre de recherche possède plusieurs secteurs verticaux et vous devez configurer chaque secteur vertical individuellement.

1. Vérifiez que vous effectuez ces étapes avec un compte doté d’autorisations pour modifier la page des résultats de la recherche et le composant WebPart Search Result.

2. Accédez à la page des résultats de la recherche (reportez-vous à la [liste](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) des pages des résultats de la recherche)

3. Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.

   ![Modifier la sélection de page dans Paramètres.](../media/configure-search-for-multi-geo-image2.png)

4. Dans le composant WebPart de résultats de recherche, déplacez le pointeur vers le coin supérieur droit et cliquez sur la flèche, puis sur **Modifier le composant WebPart** dans le menu. Le volet des outils du composant WebPart des résultats de recherche s’ouvre sous le ruban en haut à droite de la page.

   ![Modifier la sélection du composant WebPart.](../media/configure-search-for-multi-geo-image3.png)

5. Dans le volet des outils du composant WebPart, dans la section **Paramètres**, sous **Paramètres de contrôle des résultats**, sélectionnez **Afficher les résultats multigéographiques** pour que le composant WebPart Résultats de la recherche affiche les résultats de tous les emplacements géographiques.

6. Cliquez sur **OK** pour enregistrer vos changements et fermer le volet des outils du composant WebPart.

7. Vérifiez les changements que vous avez apportés au composant WebPart Résultats de la recherche en cliquant sur **Archiver** sur l’onglet Page du menu principal.

8. Publiez les changements en utilisant le lien fourni dans la note en haut de la page.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Configurer des applications de recherche personnalisée pour qu’elles affichent les résultats de l’ensemble ou d’une partie des emplacements géographiques

Les applications de recherche personnalisée obtiennent les résultats de tout ou partie des emplacements _Geography_ en spécifiant des paramètres de requête avec la requête adressée à l’API REST Recherche SharePoint. Selon les paramètres de requête, la requête est étendue à tous les emplacements _Geography_ ou à certains emplacements géographiques. Par exemple, si vous avez uniquement besoin d’interroger un sous-ensemble d’emplacements _Geography_ pour trouver des informations pertinentes, vous pouvez contrôler le ventilateur uniquement sur ceux-ci. Si la demande réussit, l’API REST Recherche SharePoint retourne les données de réponse.

### <a name="requirement"></a>Conditions requises

Pour chaque emplacement géographique, vous devez vous assurer que tous les utilisateurs de l’organisation ont reçu l’autorisation de **lecture** du site web racine (par exemple contoso **APAC**.sharepoint.com/ et contoso **EU**.sharepoint.com/). [En savoir plus sur les autorisations](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Paramètres de requête

EnableMultiGeoSearch : il s’agit d’une valeur booléenne qui spécifie si la requête doit être transférée aux index d’autres emplacements géographiques du _locataire multigéographique_. Définissez-la sur **true** pour étendre la requête et sur **false** pour ne pas l’étendre. Si vous n’incluez pas ce paramètre, la valeur par défaut est **false**, sauf lorsque vous effectuez un appel de l’API REST contre un site qui utilise le modèle Centre de recherche d’entreprise, dans ce cas, la valeur par défaut est **true**. Si vous utilisez ce paramètre dans un environnement qui n’est pas multigéographique, le paramètre est ignoré.

TypeClient : il s’agit d’une chaîne. Entrez un nom de client unique pour chaque application de recherche. Si vous n’incluez pas ce paramètre, la requête n’est pas étendue à d’autres emplacements géographiques.

MultiGeoSearchConfiguration : il s’agit d’une liste facultative des emplacements géographiques dans le _locataire_ multigéographique vers lequel la requête doit être exécutée lorsque **EnableMultiGeoSearch a la** **valeur true**. Si vous n’incluez pas ce paramètre ou que vous le laissez vide, la requête est étendue à d’autres emplacements géographiques. Pour chaque emplacement géographique, entrez les éléments suivants au format JSON :

<table>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Emplacement _Geography_ , par exemple NAM.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">Le point de terminaison auquel se connecter, par exemple https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">GUID de l’origine des résultats, par exemple B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Données de réponse

MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:

<table>
<thead>
<tr class="header">
<th align="left">Valeur</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Complet</td>
<td align="left">Résultats complets de <strong>tous les</strong> emplacements _Geography_ .</td>
</tr>
<tr class="even">
<td align="left">Partiel</td>
<td align="left">Résultats partiels d’un ou de plusieurs emplacements _Geography_ . Les résultats sont incomplets en raison d’une erreur temporaire.</td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Requête à l’aide du service REST

With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.

#### <a name="request-headers"></a>En-têtes de demande

<table>
<thead>
<tr class="header">
<th align="left">Nom</th>
<th align="left">Valeur</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Exemple de demande GET étendue à **tous** les emplacements géographiques

```http
https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'
```

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Exemple de demande GET à distribuer à **certains** emplacements géographiques

```http
https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

> [!NOTE]
> Les symboles virgule et deux-points de la liste des emplacements géographiques pour la propriété MultiGeoSearchConfiguration sont précédés par le caractère **barre oblique inverse**, car les demandes GET utilisent des syboles deux-points pour séparer les propriétés, et des virgules pour séparer les arguments des propriétés. Sans barre oblique inverse comme caractère d’échappement, la propriété MultiGeoSearchConfiguration est interprétée de façon erronée.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Exemple de demande POST étendue à **tous** les emplacements géographiques

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Exemple de demande POST étendue à **certains** emplacements géographiques

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### <a name="query-using-csom"></a>Requête utilisant CSOM

Voici un exemple de requête CSOM qui est étendue à **tous les** emplacements _Geography_ :

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
