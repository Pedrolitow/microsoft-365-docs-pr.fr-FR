---
title: Options de migration SharePoint 2007 à prendre en compte
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- SPS150
- OSU140
- SPO160
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: 66325a43-5816-4f8e-81ba-c11b71345b7c
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Cet article contient des informations pour les utilisateurs qui utilisent SharePoint Server 2007 pour les aider à planifier leur mise à niveau.
ms.openlocfilehash: 3e37a01f1a2d387cda6723a8df1f73734fa3ba9d
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46694953"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Options de migration SharePoint 2007 à prendre en compte

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft SharePoint 2007 et SharePoint Server 2007 ont atteint la fin de la prise en charge. Il est temps de mettre à niveau ! Cet article fournit des informations sur vos options de migration.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Stratégies de mise à niveau courantes pour SharePoint

Il existe plusieurs méthodes pour mettre à niveau un environnement SharePoint Server. Si vous avez une batterie Microsoft Office SharePoint Server 2007, voici quelques exemples de méthodes de mise à niveau :
  
- liaison des bases de données.
    
- Mise à niveau côte à côte
    
- Mise à niveau sur place
    
- Mise à niveau hybride (sur place avec bases de données détachées/attachement de base de données distinct)
    
- SharePoint hybrides (connexion en ligne à SharePoint local)
    
- Déplacer manuellement des données entre des collections de sites ou des bibliothèques
    
- Mise à niveau de l’Assistant FastTrack vers Microsoft 365 ([Conseiller de déploiement SharePoint Online](https://aka.ms/spoguidance))
    
- API de migration vers SharePoint Online (SPO) dans Microsoft 365
    
Qu’est-ce qui fonctionne le mieux pour vous ?
  
Votre connaissance des opérations de votre batterie de serveurs et de son utilisation constitue une force tactique lorsqu’il s’agit de mettre à niveau. La façon dont les personnes utilisent la batterie de serveurs SharePoint vous aidera à choisir parmi vos options.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 présente également une mise à niveau progressive qui n’est pas couverte ici. Pour consulter la liste des articles de mise à niveau spécifiques aux étapes, consultez la feuille de route de fin de la prise en charge de [SharePoint Server 2007.](sharepoint-2007-end-of-support.md) 
  
N’oubliez pas de vérifier le cycle [de vie du](https://support.microsoft.com/lifecycle/search) produit et la system requirements pour n’importe quelle version de SharePoint vers qui vous êtes en train de mettre à niveau. C’est pour cette raison que vous savez quand la prochaine mise à niveau sera nécessaire (par exemple, si vous mettez en pause un produit hérité tel que SharePoint Server 2010 pour planifier d’autres mises à niveau, assurez-vous de connaître sa date de fin de prise en charge) et assurez-vous que vous avez du matériel qui prend en charge votre plan. 
  
Si vous envisagez de passer d’une partie ou de l’ensemble de vos sites SharePoint à Microsoft 365 dans le cloud, il s’agit d’un moment pour mettre en signet un lien vers les descriptions des [services Microsoft 365 et Office 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-service-descriptions-technet-library) Vous aurez besoin des descriptions de service pour en savoir plus sur les fonctionnalités SharePoint Online et sur la façon dont elles peuvent différer de SharePoint Server sur site. Mettre à niveau Microsoft Office batteries de serveurs SharePoint Server 2007. Si votre installation a des sites qui sont rompus, corrigez-les avant la mise à niveau.
  
## <a name="a-note-about-managing-risk"></a>Remarque sur la gestion des risques

Les méthodes telles que « côte à côte » sont importantes dans le schéma de logique de mise à niveau. Lorsque vous faites une mise à niveau côte à côte, vous maintenez votre batterie de serveurs Microsoft Office SharePoint Server 2007, mais créez une batterie de serveurs à partir de la version suivante (SharePoint Server 2010) sur un nouveau matériel. Cela vous aide de trois manières :
  
1. Vous pouvez sauvegarder vos bases de données SharePoint Server 2007 Microsoft Office pour les mettre à niveau séparément, à l’aide de l’attachement de base de données.
    
2. Si vous vous rendez compte qu’un petit nombre de bibliothèques de documents critiques et d’autres informations sont en cours d’utilisation sur votre batterie de serveurs SharePoint Server 2007 Microsoft Office, vous pouvez choisir de déplacer manuellement des données de Microsoft Office SharePoint Server 2007 vers SharePoint Server 2010, ou de n’utiliser que des sites et des sites web spécifiques vers la version suivante (ce qui peut faciliter votre travail).
    
3. Moins vous faites d’Microsoft Office batterie de serveurs SharePoint Server 2007 directement, plus les données que contient la batterie de serveurs sont sûres lors de la mise à niveau.
    
Les méthodes telles que la mise à niveau In-Place agissent directement sur votre batterie de serveurs SharePoint Server 2007 Microsoft Office, ce qui vous offre moins d’options faciles pour abandonner un chemin d’accès et recommencer avec votre environnement. Dans la mesure du possible, créez certaines mesures de sécurité (par exemple, prendre et tester des sauvegardes de l’environnement d’origine). Par exemple, si votre batterie de serveurs SharePoint Server 2007 Microsoft Office est virtuelle et qu’elle est dupliquée à des fins de sauvegarde et de restauration, sauvegardez et restituer les bases de données les plus à jour avant votre fenêtre de service pour la mise à niveau. Le fait de savoir que vous avez la possibilité de restaurer des sauvegardes de base de données ne vous donnera pas seulement une sécurité d’échec, mais peut vous donner l’esprit.
  
> [!TIP]
> Les documents de meilleures pratiques pour la mise à [niveau existent pour Microsoft Office SharePoint Server 2007](https://technet.microsoft.com/library/cc261992%28v=office.12%29.aspx), [SharePoint Server 2010](https://technet.microsoft.com/library/cc261992%28v=office.14%29.aspx), [SharePoint Server 2013](https://technet.microsoft.com/library/cc261992%28v=office.15%29.aspx)et [SharePoint Server 2016](https://technet.microsoft.com/library/cc261992%28v=office.16%29.aspx). Vous pouvez également rechercher des [partenaires Microsoft qui](https://partnercenter.microsoft.com/pcv/search) ont de l’expérience avec les mises à niveau ou les migrations Microsoft 365. 
  
## <a name="make-your-plan"></a>Planifier votre plan

Si vous avez besoin d’une mise à niveau, vous avez besoin d’un plan et une seule taille ne correspond pas à toutes les situations. Votre plan peut être aussi simple que « Créer un abonnement Microsoft 365 avec SharePoint Online, inscrire un domaine et rediriger les utilisateurs pour y enregistrer leurs fichiers ». Et ce n’est peut-être pas le cas. Cette décision vous est propre et vous et vos utilisateurs en avez réellement besoin.
  
> [!NOTE]
> Il est risqué de s’exécuter sur un logiciel dont le cycle de vie est terminé. Les produits qui ne sont plus supportés ne sont plus corrigés lorsque des problèmes sont trouvés. Cela signifie également que si de nouvelles menaces de sécurité surviennent, il n’y aura aucun correctif de sécurité, car les produits de fin de cycle de vie ne sont plus pris en charge. Évitez cette situation . 
  
### <a name="first-know-your-farm"></a>Tout d’abord, connaissez votre batterie de serveurs

Lors de la mise à niveau, votre prise de décision doit être basée sur ce que fait votre batterie de serveurs pour votre organisation. Quels sont les besoins qu’il répond ? Quel est son rôle ? Chaque batterie de serveurs de votre entreprise peut avoir un rôle différent. Certaines de vos batteries  de serveurs SharePoint peuvent être critiques, d’autres peuvent être des archives de fichiers, pour assurer la sécurité. Ou, si votre batterie de serveurs remplit plusieurs rôles en même temps, vous devrez peut-être connaître les collections de sites, les sites web ou même les bibliothèques de documents, toutes les personnalisations et leur importance. L’analyse de vos données à ce niveau peut sembler beaucoup de travail, mais cela permet de maîtriser votre domaine avant de le mettre à niveau ou de le migrer. Une fois que vous connaissez tous les composants mobiles et les bits les plus importants, vous savez également ce que vous avez dépassé et que vous pouvez laisser derrière vous. Cette connaissance ne vous sera bénéfique qu’à l’avenir. 
  
Qu’est-ce que les utilisateurs pensent comme le plus important de votre batterie de serveurs SharePoint Server ?
  
- Fonctionnalités SharePoint intégrées
    
- Le corpus de données de grande taille (par exemple, une archive de fichiers)
    
- Disponibilité
    
- Applications critiques, composants Web Parts ou documents dans la batterie de serveurs (batterie de serveurs critique)
    
- Normes de conformité respectées
    
- Personnalisations
    
Si vous exécutez quelque chose d’essentiel pour votre entreprise à partir de votre batterie de serveurs SharePoint, dites qu’elle agit comme un grand catalogue de données critiques sur les besoins du service client, vous pouvez placer une coche à côté des « applications critiques » mais aussi de la « disponibilité » : autrement dit, votre entreprise serait impactée si vous ne pouviez pas utiliser SharePoint pendant un certain temps. De même, vous pouvez vérifier « Personnalisations » car les services critiques offerts par votre batterie de serveurs sont basés sur du code personnalisé, des définitions de site ou un certain nombre de personnalisations qui fonctionnent ensemble.
  
Si SharePoint satisfait à ces besoins sans avoir à faire quoi que ce soit en dehors de l’utilisation des logiciels intégrés, et que vous le mettez généralement à jour et effectuez une administration et une maintenance normales, vous avez peut-être choisi « SharePoint intégré » ; c’est peut-être également la raison pour laquelle vous vous reposez sur une version antérieure de SharePoint. En d’autres termes, il fait déjà ce dont vous avez besoin et vous n’avez pas eu besoin de mettre à niveau jusqu’à Microsoft Office la fin de la prise en charge de SharePoint Server 2007.
  
Lorsque vous listez ces éléments à puces, vous créez des critères pour votre mise à niveau. En d’autres termes, toute mise à niveau doit respecter cette barre pour être envisagée. Cela vous permet d’exclure les méthodes qui ne correspondent actuellement pas à vos besoins.
  
### <a name="a-simple-sample-plan"></a>Un exemple de plan simple

Vous devrez peut-être faire davantage de consensus avec la direction et d’autres administrateurs sur le chemin d’accès que prendra votre mise à niveau SharePoint. Les administrateurs SharePoint Server collaborent souvent avec Microsoft SQL Server administrateurs, collaborent avec les équipes de mise en réseau et de sécurité, et bien plus encore. Lorsque de nombreuses parties prenantes sont concernées, vous devrez peut-être établir un accord pour votre plan de mise à niveau et de migration ou l’ajuster. Par exemple, si vous migrez des données de sorte qu’une partie de votre entreprise utilise SharePoint Online dans Microsoft 365, vous devrez probablement ajuster les performances ou tester votre réseau. Les équipes concernées doivent être informées à l’avance.
  
Dans mon exemple simple, j’affiche la proposition d’un administrateur SharePoint, puis je présente le plan que toutes les parties prenantes ont accepté. Pour plus de clarté, documentez vos accords et décisions.
  
Le plan démarre après une analyse approfondie d’une batterie de serveurs et tente d’identifier le rôle de la batterie de serveurs, les problèmes et d’autres informations importantes qui vont aboutir à une définition plus précise de certaines options de mise à niveau. Par la suite, une proposition de mise à niveau est faite par l’administrateur SharePoint et les parties prenantes s’accordent sur un plan d’action.
  
Ma liste à puces « la plus importante » :
  
- Disponibilité, fonctionnalités intégrées à SharePoint et normes de conformité.
    
- La plupart des données sont sur trois collections de sites, avec un espace de travail de réunion utilisé par une équipe de dév. particulièrement important et très utilisé dans plusieurs fuseaux horaires dans le monde entier.
    
- Il existe d’autres sites très utilisés.
    
- Deux bibliothèques de documents (Espace de travail de réunion et Documents sur la collection de sites racine) sont plus grandes (plus de 8 000 documents chacune). Nous avons un grand nombre de documents archivés et de listes avec des pièces jointes de feuilles de calcul.
    
- Il existe 14 listes de bibliothèques qui ont des données sensibles qui doivent rester conformes.
    
- Nous DEVONS avoir la possibilité de mettre en place des holds et de la découverte électronique partout où nous allons.
    
- Certaines de ces données DOIVENT rester en local, en raison des règles InfoSec.
    
 **Mes choix de mise à niveau et de migration :**
  
| Oui | Non |
|:-----|:-----|
|Mettre à niveau les bases de données avec attachement de base de données  <br/> |Mise à niveau sur place  <br/> |
|Mise à niveau avec des batteries de serveurs côte à côte  <br/> |Mise à niveau hybride  <br/> |
|API de migration vers SPO dans Microsoft 365 (pour les données de site personnel)  <br/> |SharePoint hybride (pas encore nécessaire)  <br/> |
|Certaines migrations de données manuelles vers SharePoint Online pour les données critiques  <br/> |Mise à niveau de l’Assistant FastTrack vers Microsoft 365  <br/> |
   
 **Mon plan proposé :**
  
Mettre à niveau sur site, avec des versions de SharePoint côte à côte, certaines virtualisées, afin que nous pouvons d’abord mettre à niveau les bases de données. Passer de SharePoint 2007 à SharePoint 2010. Les administrateurs et les devs testent la batterie de serveurs résultante. Les utilisateurs testent la batterie de serveurs résultante. Résoudre les problèmes d’arrêt de l’émission pendant cette période. Là encore, côte à côte, mettre à niveau les bases de données SharePoint 2010 vers SharePoint 2013. Tester. Test/pilote de l’utilisateur. Résoudre les problèmes d’arrêt de l’émission pendant cette période.
  
- Envisagez si une recherche hybride fédérée avec SPO répond à vos besoins.
    
- Prenons [l’aide](https://fasttrack.microsoft.com) de FastTrack si vous souhaitez mettre à niveau vers SharePoint Online à partir d’ici. 
    
- Déterminez si des collections de sites peuvent être déchargées vers un abonnement Microsoft 365. (Microsoft 365 répond à de nombreuses normes [de conformité.](https://technet.microsoft.com/library/office-365-compliance.aspx) Microsoft 365 dispose [d’eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) et peut faire des [holds](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) via le Centre de conformité.) 
    
Sinon, continuez avec une mise à niveau côte à côte vers SharePoint Server 2016.
  
> [!NOTE]
> Entre les recommandations faites par les administrateurs qui planifient la mise à niveau et le processus réel se trouve les conversations qui se produisent avec d’autres parties prenantes sur lesquelles repose la mise à niveau. Par exemple, l’économie oblige parfois les administrateurs à modifier leurs plans. Quelle que soit la décision finale, vous devez documenter ce qu’est le plan convenu à l’avenir. Il peut ressembler à ceci : 
  
 **Mon plan d’action :**
  
En local, nous utilisons un environnement virtuel pour créer sharePoint Server 2010 et 2013 par défaut. SharePoint Server 2016 repose sur un nouveau matériel qui répond à la configuration système requise pour 2016. Nous allons mettre à niveau les bases de données à partir de SharePoint 2007 vers toutes les versions entre elles et SharePoint Server 2016. Les personnalisations de base sont actuellement recréées et testées dans l’environnement SharePoint Server 2016, si les fonctionnalités natives ne répondent pas déjà à nos besoins. Si nous réussissons, nous allons avoir une batterie de serveurs locale sur un nouveau matériel avec des bases de données mises à niveau et moins de personnalisations. Nous allons attacher les bases de données de contenu mises à niveau aux nouvelles collections de sites dans SharePoint Server 2013, tester, tester/piloter, puis faire un cut-over DNS vers le nouvel environnement SharePoint Server 2016 pour une utilisation dynamique.
  
- Nous n’envisagerons pas l’hybridation fédérée entre SharePoint Server 2016 et SharePoint Online pour le moment.
    
- On estime que 35 % de nos sites peuvent être transformés en nouveaux sites SPO avec des domaines de vanity, ou, en fin de compte, devenir un espace de stockage OneDrive Entreprise. Recherchez d’autres opportunités pour convertir des sites ou router de nouveaux sites vers SPO.
    
- Une partie de cette partie de la migration sera manuelle, par glisser-déposer vers les sites personnels OneDrive Entreprise, et d’autres par API de migration.
    
Des étapes plus détaillées ou un certain nombre de liens vers des itinéraires de mise à niveau spécifiques doivent suivre un plan. L’ordinateur MOSS 2007 ne doit pas être désaffecté et les environnements virtuels doivent être conservés à des fins de comparaison . Toutefois, la mise à niveau est terminée lorsque les utilisateurs sont redirigés vers SharePoint Server 2016.
  
Souvent, les principaux facteurs dans le choix d’une méthode sont le coût total de la mise à niveau et le coût dans le temps (vous trouverez plus d’informations à ce sujet dans l’article feuille de route de migration SharePoint). Toutefois, la planification à l’avance vous permettra de définir les attentes, de choisir judicieusement et de définir à quoi ressemblera la réussite.
  
## <a name="related-links"></a>Liens associés

[Ressources pour vous aider à mettre à niveau des serveurs et des clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Recherche de politique de cycle de vie et de cycle de vie Microsoft](https://support.microsoft.com/lifecycle)
  
[Rechercher des partenaires Microsoft qui peuvent vous aider avec la mise à niveau ou la migration](https://partnercenter.microsoft.com/pcv/search)
  

