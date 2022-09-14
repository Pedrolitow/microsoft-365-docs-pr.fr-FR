---
title: Utilisation du composant WebPart Recherche de contenu au lieu du composant WebPart Requête de contenu pour améliorer les performances dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
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
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: Découvrez comment améliorer les performances en remplaçant le composant WebPart Requête de contenu par le composant WebPart Recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
ms.openlocfilehash: b286688e3a3ed958eec5c31e3e106f79ecfa7b3c
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67671784"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Utilisation du composant WebPart Recherche de contenu au lieu du composant WebPart Requête de contenu pour améliorer les performances dans SharePoint Online

Cet article explique comment améliorer les performances en remplaçant le composant WebPart Requête de contenu par le composant WebPart Recherche de contenu dans SharePoint Server 2013 et SharePoint Online.
  
L’une des nouvelles fonctionnalités les plus puissantes de SharePoint Server 2013 et SharePoint Online est le composant WebPart Recherche de contenu (CSWP). Ce composant WebPart utilise l’index de recherche pour récupérer rapidement les résultats, qui sont présentés à l’utilisateur. Utilisez le composant WebPart Recherche de contenu au lieu du composant WebPart Requête de contenu (CQWP) dans vos pages pour améliorer les performances de vos utilisateurs.
  
L’utilisation d’un composant WebPart Recherche de contenu sur un composant WebPart Requête de contenu entraîne presque toujours de meilleures performances de chargement de page sur SharePoint Online. Il existe une configuration supplémentaire pour obtenir la requête appropriée, mais les récompenses sont des performances améliorées et des utilisateurs plus heureux.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparaison du gain de performances obtenu à l’aide du composant WebPart Recherche de contenu au lieu du composant WebPart Requête de contenu

Les exemples suivants montrent les gains de performances relatifs que vous pouvez recevoir lorsque vous utilisez un composant WebPart Recherche de contenu au lieu d’un composant WebPart Requête de contenu. Les effets sont plus évidents avec une structure de site complexe et des requêtes de contenu étendues.
  
Cet exemple de site présente les caractéristiques suivantes :
  
- 8 niveaux de sous-sites.
    
- Listes utilisant un type de contenu « fruit » personnalisé.
    
- Dans le composant WebPart, la requête de contenu est large, renvoyant tous les éléments avec le type de contenu « fruit ».
    
- L’exemple utilise uniquement 50 éléments sur les 8 sites. Les effets seront encore plus prononcés pour les sites avec plus de contenu.
    
Voici une capture d’écran des résultats du composant WebPart Requête de contenu.
  
![Graphique montrant la requête de contenu pour le composant WebPart.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
Dans Internet Explorer, utilisez l’onglet **Réseau** des outils de développement F12 pour examiner les détails de l’en-tête de réponse. Dans la capture d’écran suivante, la valeur de **SPRequestDuration** pour ce chargement de page est de 924 millisecondes. 
  
![Capture d’écran montrant la durée de la demande de 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indique la quantité de travail effectuée sur le serveur pour préparer la page. Le basculement de contenu par requête de composants WebPart avec contenu par composants WebPart de recherche réduit considérablement le temps nécessaire au rendu de la page. En revanche, une page avec un composant WebPart Recherche de contenu équivalent, qui retourne le même nombre de résultats, a une valeur **SPRequestDuration** de 106 millisecondes, comme illustré dans cette capture d’écran : 
  
![Capture d’écran montrant la durée de la demande de 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Ajout d’un composant WebPart Recherche de contenu dans SharePoint Online

L’ajout d’un composant WebPart Recherche de contenu est similaire à un composant WebPart Requête de contenu standard. Consultez la section  *« Ajouter un composant WebPart Recherche de contenu »*  dans [Configurer un composant WebPart Recherche de contenu dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Création de la requête de recherche appropriée pour votre composant WebPart Recherche de contenu

Une fois que vous avez ajouté un composant WebPart Recherche de contenu, vous pouvez affiner la recherche et retourner les éléments souhaités. Pour obtenir des instructions détaillées sur la procédure à suivre, consultez la section  *« Afficher le contenu en configurant une requête avancée dans un composant WebPart Recherche*  de contenu » dans [Configurer un composant WebPart Recherche de contenu dans SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Outil de création et de test de requêtes

Pour obtenir un outil permettant de générer et de tester des requêtes complexes, consultez [l’outil De requête de recherche](https://github.com/pnp/PnP-Tools/tree/master/Solutions/SharePoint.Search.QueryTool#download-the-tool).
  

