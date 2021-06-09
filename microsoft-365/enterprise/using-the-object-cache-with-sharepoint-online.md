---
title: Utilisation du cache d’objets avec SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 local et SharePoint Online.
ms.openlocfilehash: 279d156a941aad6fbe7adbcf052c57f5b58c652f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46695873"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Utilisation du cache d’objets avec SharePoint Online

Cet article explique la différence entre l’utilisation du cache d’objets dans SharePoint Server 2013 local et SharePoint Online.
  
L’utilisation du cache d’objets dans le déploiement SharePoint Online a un impact négatif significatif. Toute dépendance au cache d’objets dans SharePoint Online réduit la fiabilité de votre page. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Fonctionnement SharePoint cache d’objets SharePoint Server 2013

Lorsque SharePoint Server 2013 est hébergé en local, le client dispose de serveurs web frontaux privés qui hébergent le cache d’objets. Cela signifie que le cache est dédié à un client et est limité uniquement par la quantité de mémoire disponible et allouée au cache d’objets. Étant donné qu’un seul client est servi dans le scénario local, les serveurs web frontaux ont généralement des utilisateurs qui font des demandes aux mêmes sites plusieurs fois. Cela signifie que le cache est rapidement plein et qu’il reste plein des résultats de requête de liste et des objets SharePoint que vos utilisateurs demandent régulièrement.
  
![Affiche le trafic et la charge vers les serveurs web frontaux locaux](../media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Par conséquent, la deuxième fois qu’un utilisateur visite une page, le temps de chargement de la page s’améliore. Après au moins quatre chargements de la même page, la page est mise en cache sur tous les serveurs web frontux.
  
En revanche, dans SharePoint Online, il y a beaucoup plus de serveurs, mais aussi beaucoup plus de sites. Chaque utilisateur peut se connecter à un autre serveur web frontal dont le cache n’est pas rempli. Ou peut-être le cache est-il rempli pour un serveur, mais l’utilisateur suivant de ce serveur web frontal demande une page à partir d’un autre site. Ou, même si l’utilisateur suivant demande la même page que lors de sa visite précédente, il est à charge équilibrée vers un autre serveur web frontal qui n’a pas cette page dans son cache. Dans ce dernier cas, la mise en cache n’aide pas du tout les utilisateurs.
  
Dans la figure suivante, chaque point représente une page qu’un utilisateur demande et où il est mis en cache. Différentes couleurs représentent différents clients qui utilisent l’infrastructure SaaS.
  
![Affiche les résultats de la mise en cache d’objets dans SharePoint Online](../media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Comme vous pouvez le voir sur le diagramme, les chances pour un utilisateur donné d’atteindre un serveur avec la version mise en cache de sa page sont faibles. En outre, en raison du débit élevé et du fait que les serveurs sont partagés entre de nombreux sites, le cache ne dure pas longtemps, car il n’y a que trop d’espace disponible pour la mise en cache.
  
Pour toutes ces raisons, le fait de compter sur les utilisateurs pour obtenir des objets mis en cache n’est pas un moyen efficace de garantir une expérience utilisateur de qualité et des temps de chargement de page dans SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Si nous ne pouvons pas compter sur le cache d’objets pour améliorer les performances dans SharePoint Online, qu’utilisons-nous à la place ?

Étant donné que vous ne devez pas vous fier à la mise en cache dans SharePoint Online, vous devez évaluer d’autres approches de conception pour SharePoint personnalisations qui utilisent le cache d’objets. Cela implique d’utiliser des approches pour les problèmes de performances qui ne reposent pas sur la mise en cache d’objets afin de produire de bons résultats pour les utilisateurs. Cela est décrit dans certains des autres articles de cette série et inclut :
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

