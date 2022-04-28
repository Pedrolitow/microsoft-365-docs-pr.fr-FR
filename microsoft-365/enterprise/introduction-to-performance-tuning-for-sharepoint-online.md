---
title: Introduction à l’optimisation des performances pour SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: Cet article explique quels aspects spécifiques vous devez prendre en compte lors de la conception de pages pour de meilleures performances dans SharePoint Online.
ms.openlocfilehash: b31696766d3201b6677bf0c63108fad72c3ed49d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100740"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introduction à l’optimisation des performances pour SharePoint Online

Cet article explique quels aspects spécifiques vous devez prendre en compte lors de la conception de pages pour de meilleures performances dans SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Métriques SharePoint Online

Les métriques générales suivantes pour SharePoint Online fournissent des données réelles sur les performances :
  
- Vitesse de chargement des pages
    
- Nombre d’allers-retours requis par page
    
- Problèmes liés au service
    
- Autres éléments qui provoquent une dégradation des performances
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusions tirées en raison des données

Les données nous indiquent :
  
- La plupart des pages fonctionnent bien sur SharePoint Online.
    
- Les pages non personnalisées se chargent rapidement.
    
- OneDrive Entreprise, les sites d’équipe et les pages système, tels que _layouts, etc., sont tous rapides à charger.
    
- Les 1 % les plus lents de SharePoint pages en ligne prennent plus de 5 000 millisecondes à charger.
    
Un test d’évaluation simple que vous pouvez utiliser consiste à mesurer les performances en comparant l’heure de chargement de votre propre portail à l’heure de chargement de la page d’accueil OneDrive Entreprise, car elle utilise peu de fonctionnalités personnalisées. Il s’agit souvent de la première étape que le support technique vous demande d’effectuer lors de la résolution des problèmes de performances réseau.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Utiliser un compte d’utilisateur standard lors de la vérification des performances

Un administrateur de collection de sites, un propriétaire de site, un éditeur ou un contributeur appartiennent à d’autres groupes de sécurité, disposent d’autorisations supplémentaires et ont donc des éléments supplémentaires qui SharePoint chargent sur une page.
  
Cela s’applique à SharePoint localement et SharePoint Online, mais dans un scénario local, les différences ne seront pas aussi faciles à remarquer que dans SharePoint Online.
  
Pour évaluer correctement les performances d’une page pour les utilisateurs, vous devez utiliser un compte d’utilisateur standard pour éviter de charger les contrôles de création et le trafic supplémentaire lié aux groupes de sécurité.
  
## <a name="connection-categories-for-performance-tuning"></a>Catégories de connexion pour le réglage des performances

Vous pouvez classer les connexions entre le serveur et l’utilisateur en trois composants principaux. Tenez compte de ces éléments lors de la conception de pages SharePoint Online pour obtenir des informations sur les temps de chargement.
  
- **Serveur** Serveurs hébergés par Microsoft dans les centres de données.
    
- **Réseau** Le réseau Microsoft, Internet et votre réseau local entre le centre de données et vos utilisateurs.
    
- **Navigateur** Emplacement de chargement de la page.
    
Au sein de ces trois connexions, il existe généralement cinq raisons qui provoquent 95 % des pages lentes. Chacune de ces raisons est abordée dans cet article :
  
- Problèmes de navigation
    
- Cumul de contenu
    
- Fichiers volumineux
    
- De nombreuses demandes adressées au serveur
    
- Traitement des composants WebPart
    
### <a name="server-connection"></a>Connexion au serveur

La plupart des problèmes qui affectent les performances avec SharePoint localement s’appliquent également à SharePoint Online.
  
Comme vous pouvez vous y attendre, vous disposez d’un contrôle beaucoup plus grand sur la façon dont les serveurs fonctionnent avec les SharePoint locaux. Avec SharePoint Les choses en ligne sont un peu différentes. Plus vous effectuez de travail sur un serveur, plus il faut de temps pour afficher une page. Avec SharePoint, les principaux coupables à cet égard sont les pages complexes avec plusieurs composants WebPart.
  
serveur SharePoint local
  
![Capture d’écran du serveur local.](../media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Capture d’écran du serveur en ligne.](../media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Avec SharePoint Online, certaines demandes de page peuvent en fait finir par appeler plusieurs serveurs. Vous pouvez vous retrouver avec une matrice de demandes entre les serveurs pour une requête individuelle. Ces interactions sont coûteuses du point de vue du chargement de page et ralentiront les choses.
  
Voici quelques exemples de ces interactions de serveur à serveur :
  
- Web vers les serveurs SQL
    
- Web vers les serveurs d’applications
    
L’autre chose qui peut ralentir les interactions du serveur est les absences dans le cache. Contrairement aux SharePoint locaux, il y a peu de chances que vous atteigniez le même serveur pour une page que vous avez visitée précédemment ; cela rend la mise en cache d’objets obsolète.
  
### <a name="network-connection"></a>Connexion réseau 

Avec des SharePoint locaux qui n’utilisent pas de wan, vous pouvez utiliser une connexion à haut débit entre le centre de données et les utilisateurs finaux. En règle générale, les choses sont faciles à gérer du point de vue du réseau.
  
Avec SharePoint Online, il y a quelques facteurs supplémentaires à prendre en compte, par exemple :
  
- Le réseau Microsoft
    
- The Internet
    
- Le fournisseur de services Internet
    
Quelle que soit la version de SharePoint (et le réseau) que vous utilisez, les éléments qui entraînent généralement l’occupation du réseau sont les suivants :
  
- Charge utile volumineuse
    
- De nombreux fichiers
    
- Grande distance physique par rapport au serveur
    
Microsoft CDN (réseau de distribution de contenu) est une fonctionnalité que vous pouvez utiliser dans SharePoint Online. Une CDN est essentiellement une collection distribuée de serveurs déployés sur plusieurs centres de données. Avec un CDN, le contenu des pages peut être hébergé sur un serveur proche du client, même si le client est loin du serveur SharePoint d’origine. Microsoft l’utilisera davantage à l’avenir pour stocker des instances locales de pages qui ne peuvent pas être personnalisées, par exemple la page d’accueil de l’administrateur SharePoint Online. Pour plus d’informations sur les CDN, consultez [Réseaux de distribution de contenu](content-delivery-networks.md).
  
La vitesse de connexion de votre fournisseur de services Internet est quelque chose que vous devez connaître, mais qui peut ne pas être en mesure de faire grand-chose. Un outil de test de vitesse simple vous indiquera la vitesse de connexion.
  
### <a name="browser-connection"></a>Connexion au navigateur

Il existe quelques facteurs à prendre en compte avec les navigateurs web du point de vue des performances.
  
La visite de pages complexes affecte les performances. La plupart des navigateurs n’ont qu’un petit cache (environ 90 Mo), tandis que la page web moyenne est généralement d’environ 1,6 Mo. Cela ne prend pas longtemps pour s’habituer.
  
La bande passante peut également être un problème. Par exemple, si un utilisateur regarde des vidéos dans une autre session, cela affecte les performances de votre page SharePoint. Bien que vous ne puissiez pas empêcher les utilisateurs de diffuser du contenu multimédia en continu, vous pouvez contrôler le chargement d’une page pour les utilisateurs.
  
Consultez les articles suivants pour connaître les différentes techniques de personnalisation de page SharePoint Online et d’autres meilleures pratiques pour vous aider à obtenir des performances optimales.
  
- [Options de navigation pour SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Utiliser l’outil Diagnostics de page pour SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optimisation des images pour SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Différer le chargement des images et des éléments JavaScript dans SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minimisation et regroupement dans SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Utilisation du réseau de distribution de contenu Office 365 avec SharePoint Online](use-microsoft-365-cdn-with-spo.md)
    
- [Utilisation du composant WebPart Recherche de contenu au lieu du composant WebPart Requête de contenu pour améliorer les performances dans SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planification de la capacité et test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnostic des problèmes de performances avec SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Utilisation du cache d’objets avec SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Procédure : éviter les limitations ou les blocages dans SharePoint Online](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online)
