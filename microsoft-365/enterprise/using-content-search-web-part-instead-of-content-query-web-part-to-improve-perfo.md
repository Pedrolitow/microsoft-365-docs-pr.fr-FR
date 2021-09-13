---
title: Utilisation du service Web De recherche de contenu au lieu du partie Web De requête de contenu pour améliorer les performances dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
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
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Découvrez comment améliorer les performances en remplaçant le partie Web De requête de contenu par le partie Web De recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
ms.openlocfilehash: 270019b59666c3f52d67648a88c453278149fccd
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202037"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Utilisation du service Web De recherche de contenu au lieu du partie Web De requête de contenu pour améliorer les performances dans SharePoint Online

Cet article explique comment améliorer les performances en remplaçant le volet Web De requête de contenu par le service Web De recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
  
L’une des nouvelles fonctionnalités les plus puissantes de SharePoint Server 2013 et SharePoint Online est le service Web De recherche de contenu (CSWP). Ce partie Web Part utilise l’index de recherche pour récupérer rapidement les résultats qui sont affichés à l’utilisateur. Utilisez le partie Web Part de recherche de contenu au lieu du partie Web De requête de contenu (CQWP) dans vos pages pour améliorer les performances pour vos utilisateurs.
  
L’utilisation d’un élément Web Part de recherche de contenu sur un partie Web De requête de contenu entraîne presque toujours de meilleures performances de chargement de page sur SharePoint Online. Il existe quelques configurations supplémentaires pour obtenir la requête la plus à même d’obtenir la requête, mais les avantages sont des performances améliorées et une plus grande efficacité des utilisateurs.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparaison des gains de performances que vous obtenez en utilisant le partie Web Part de recherche de contenu au lieu du partie Web Part de requête de contenu

Les exemples suivants montrent les gains de performances relatifs que vous pouvez obtenir lorsque vous utilisez un élément Web Part de recherche de contenu au lieu d’un élément Web Part requête de contenu. Les effets sont plus évidents avec une structure de site complexe et des requêtes de contenu très larges.
  
Cet exemple de site présente les caractéristiques suivantes :
  
- 8 niveaux de sous-sites.
    
- Listes utilisant un type de contenu « fruit » personnalisé.
    
- Dans le partie Web Part, la requête de contenu est large, renvoyant tous les éléments avec le type de contenu « fruit ».
    
- L’exemple utilise uniquement 50 éléments sur les 8 sites. Les effets seront encore plus marqués pour les sites avec plus de contenu.
    
Voici une capture d’écran des résultats du partie Web De requête de contenu.
  
![Graphique montrant la requête de contenu pour le partie Web.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Dans Internet Explorer,  utilisez l’onglet Réseau des outils de développement F12 pour examiner les détails de l’en-tête de réponse. Dans la capture d’écran suivante, la valeur de **SPRequestDuration** pour ce chargement de page est de 924 millisecondes. 
  
![Capture d’écran montrant la durée de la demande de 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration indique** la quantité de travail effectuée sur le serveur pour préparer la page. Le changement de contenu par requête composants WebPart contenu par recherche composants WebPart réduit considérablement le temps qu’il faut pour restituer la page. En revanche, une page avec un élément Web De recherche de contenu équivalent, renvoyant le même nombre de résultats a une valeur **SPRequestDuration** de 106 millisecondes comme illustré dans cette capture d’écran : 
  
![Capture d’écran montrant la durée de la demande 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Ajout d’un partie Web De recherche de contenu dans SharePoint Online

L’ajout d’un élément Web Part de recherche de contenu est très similaire à un élément Web Part requête de contenu normal. Consultez la section *« Ajouter un élément Web Part* de recherche de contenu » dans [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Création de la requête de recherche pour votre partie Web De recherche de contenu

Une fois que vous avez ajouté un élément Web Part de recherche de contenu, vous pouvez affiner la recherche et renvoyer les éléments que vous souhaitez. Pour obtenir des instructions détaillées sur la façon de le faire, voir la section « Afficher le contenu en configurant une requête avancée dans un élément *Web* Part de recherche de contenu » dans [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Outil de création et de test de requête

Pour obtenir un outil permettant de créer et de tester des requêtes complexes, voir l’outil de requête [de](https://sp2013searchtool.codeplex.com/) recherche sur Codeplex. 
  

