---
title: Options de migration SharePoint 2007 à prendre en compte
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
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
description: Cet article contient des informations destinées aux utilisateurs qui utilisent SharePoint Server 2007 pour les aider à planifier leur mise à niveau.
ms.openlocfilehash: 99ac785f85892ad4cd6a9ac65a9fe822b109d743
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187776"
---
# <a name="sharepoint-2007-migration-options-to-consider"></a>Options de migration SharePoint 2007 à prendre en compte

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft SharePoint 2007 et SharePoint Server 2007 ont atteint la fin du support. Il est temps de mettre à niveau ! Cet article fournit des informations sur vos options de migration.
  
## <a name="common-upgrade-strategies-for-sharepoint"></a>Stratégies de mise à niveau courantes pour SharePoint

Il existe plusieurs méthodes pour mettre à niveau un environnement SharePoint Server. Si vous disposez d’une batterie de serveurs Microsoft Office SharePoint Server 2007, voici quelques exemples de méthodes de mise à niveau :
  
- liaison des bases de données.
    
- Mise à niveau côte à côte
    
- Mise à niveau sur place
    
- Mise à niveau hybride (sur place avec bases de données détachées/ attachement de base de données distinct)
    
- Hybrides SharePoint (se connecter en ligne à SharePoint local)
    
- Déplacer manuellement des données entre des collections de sites ou des bibliothèques
    
- Mise à niveau de l’Assistant FastTrack vers Microsoft 365 ([Conseiller de déploiement SharePoint Online](https://aka.ms/spoguidance))
    
- API de migration vers SharePoint Online (SPO) dans Microsoft 365
    
Qu’est-ce qui vous convient le mieux ?
  
Votre connaissance de ce que votre ferme fait et est utilisée pour est une force tactique quand il s’agit de mettre à niveau. La façon dont les utilisateurs utilisent la batterie de serveurs SharePoint vous aidera à choisir parmi vos options.
  
> [!TIP]
> Microsoft Office SharePoint Server 2007 dispose également d’une mise à niveau progressive qui n’est pas abordée ici. Pour afficher la liste des articles de mise à niveau spécifiques aux étapes, consultez la [feuille de route de fin de support sharePoint Server 2007](sharepoint-2007-end-of-support.md). 
  
N’oubliez pas de vérifier le [cycle de vie du produit](https://support.microsoft.com/lifecycle/search) et la configuration système requise pour n’importe quelle version de SharePoint vers laquelle vous effectuez la mise à niveau. C’est pourquoi vous savez quand la prochaine mise à niveau sera nécessaire (par exemple, si vous vous arrêtez à un produit hérité comme SharePoint Server 2010 pour planifier d’autres mises à niveau, être sûr de connaître sa date de fin de support) et être certain que vous disposez d’un matériel qui prend en charge votre plan. 
  
Si vous envisagez de migrer une partie ou la totalité de vos sites SharePoint vers Microsoft 365 dans le cloud, c’est le moment de marquer un signet d’un lien vers les [descriptions de service Microsoft 365 et Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Vous aurez besoin des descriptions de service pour en savoir plus sur les fonctionnalités de SharePoint Online et sur la façon dont elles peuvent différer de SharePoint Server local. Mettez à niveau les batteries de serveurs Microsoft Office SharePoint Server 2007 fonctionnelles. Si votre installation comporte des sites défectueux, corrigez-les avant la mise à niveau.
  
## <a name="a-note-about-managing-risk"></a>Remarque sur la gestion des risques

Les méthodes telles que « côte à côte » sont importantes dans le schéma de logique de mise à niveau. Lorsque vous effectuez une mise à niveau côte à côte, vous gérez votre batterie de serveurs Microsoft Office SharePoint Server 2007, mais vous créez une batterie de serveurs à partir de celle-ci (SharePoint Server 2010) sur un nouveau matériel. Cela permet de trois façons :
  
1. Vous pouvez effectuer des sauvegardes de vos bases de données Microsoft Office SharePoint Server 2007 pour les mettre à niveau séparément, à l’aide de l’attachement de base de données.
    
2. Si vous constatez que seules quelques bibliothèques de documents critiques et d’autres informations sont utilisées sur votre batterie de serveurs Microsoft Office SharePoint Server 2007, vous pouvez choisir de déplacer manuellement des données de Microsoft Office SharePoint Server 2007 vers SharePoint Server 2010, ou de ne déplacer que des sites et sites web spécifiques vers la version suivante (ce qui peut faciliter votre travail).
    
3. Moins vous en faites pour la batterie de serveurs Microsoft Office SharePoint Server 2007, directement, plus les données que la batterie de serveurs contient sont sécurisées au fur et à mesure de la mise à niveau.
    
Des méthodes telles que In-Place mise à niveau agissent directement sur votre batterie de serveurs Microsoft Office SharePoint Server 2007, ce qui vous offre moins d’options faciles pour abandonner un chemin d’accès et recommencer avec votre environnement vierge. Autant que possible, créez des mesures de sécurité (comme la prise et le test des sauvegardes de l’environnement d’origine). Par exemple, si votre batterie de serveurs Microsoft Office SharePoint Server 2007 est virtuelle et est dupliquée à des fins de sauvegarde et de restauration, sauvegardez et restaurez les bases de données les plus actuelles avant votre fenêtre de service pour la mise à niveau. Le fait de savoir que vous avez la possibilité de restaurer des sauvegardes de base de données vous donnera non seulement une sécurité en cas de défaillance, mais peut vous donner la tranquillité d’esprit.
  
> [!TIP]
> Des documents sur les meilleures pratiques pour la mise à niveau existent pour [Microsoft Office SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc261992(v=office.12)), [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc261992(v=office.14)), [SharePoint Server 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013) et [SharePoint Server 2016](/SharePoint/upgrade-and-update/best-practices-for-upgrade). Vous pouvez également rechercher des [partenaires Microsoft](https://partnercenter.microsoft.com/pcv/search) qui ont de l’expérience avec les mises à niveau ou les migrations Microsoft 365. 
  
## <a name="make-your-plan"></a>Créer votre plan

Si vous devez effectuer une mise à niveau, vous avez besoin d’un plan et une taille unique ne convient pas à tous ces cas. Votre plan peut être aussi simple que « Créer un abonnement Microsoft 365 avec SharePoint Online, inscrire un domaine et rediriger des personnes pour y enregistrer leurs fichiers ». Et ce n’est peut-être pas le cas. Cette décision vous appartient, et elle dépend de ce dont vous et vos utilisateurs avez vraiment besoin.
  
> [!NOTE]
> Il est risqué de s’exécuter sur des logiciels dont le cycle de vie est terminé. Les produits qui ne sont plus pris en charge ne sont plus corrigés lorsque des problèmes sont détectés. Cela signifie également que si de nouvelles menaces de sécurité surviennent, il n’y aura aucun correctif ou correctif de sécurité, car les produits de fin de cycle de vie ne sont plus pris en charge. S’il vous plaît éviter cette situation! 
  
### <a name="first-know-your-farm"></a>Tout d’abord, connaissez votre ferme

Lors de la mise à niveau, votre prise de décision doit être basée sur ce que votre batterie de serveurs fait pour votre organisation. Qu’est-ce qu’il répond ? Quel est son rôle ? Chaque batterie de serveurs de votre entreprise peut avoir un rôle différent. Certaines de vos batteries de serveurs SharePoint peuvent être  *critiques*, d’autres peuvent être des archives de fichiers, là pour assurer la sécurité. Ou, si votre batterie de serveurs remplit de nombreux rôles à la fois, vous devrez peut-être connaître les collections de sites, les sites web ou même les bibliothèques de documents, les personnalisations et leur importance. L’analyse de vos données à ce niveau peut sembler beaucoup de travail, mais cela permet de gagner du temps et des efforts pour maîtriser votre domaine avant de le mettre à niveau ou de le migrer. Une fois que vous connaissez toutes les pièces mobiles et les bits les plus importants, vous saurez également ce que vous avez dépassé et pouvez laisser derrière vous. Ces connaissances ne vous profiteront qu’à l’avenir. 
  
Par conséquent, que disent les utilisateurs est-il le plus important au sujet de votre batterie de serveurs SharePoint Server ?
  
- Fonctionnalités SharePoint intégrées
    
- Corpus de données volumineux (tel qu’une archive de fichiers)
    
- Disponibilité
    
- Applications critiques, composants WebPart ou documents dans la batterie de serveurs (batterie de serveurs critique)
    
- Les normes de conformité sont respectées
    
- Personnalisations
    
Si vous exécutez quelque chose d’essentiel pour votre entreprise à partir de votre batterie de serveurs SharePoint, dis-le agit comme un grand catalogue de données critiques sur les exigences du service client, vous pouvez placer une coche à côté de « Applications critiques », mais aussi « Disponibilité », c’est-à-dire que votre entreprise serait affectée si vous ne pouviez pas utiliser SharePoint pendant un certain temps. De même, vous pouvez vérifier « Personnalisations », car les services critiques offerts par votre batterie de serveurs sont basés sur du code personnalisé, des définitions de site ou de nombreuses personnalisations qui fonctionnent ensemble.
  
Si SharePoint répondait à ces besoins sans votre participation en dehors de l’utilisation de ce qui est intégré au logiciel, et que vous le mettez généralement à jour et effectuez une administration et une maintenance normales, vous avez peut-être choisi « SharePoint intégré » : cela peut également être votre raison de vous être assis sur une version antérieure de SharePoint. En d’autres termes, il fait déjà ce dont vous avez besoin et vous n’avez pas besoin de mettre à niveau jusqu’à présent, à la fin du support microsoft Office SharePoint Server 2007.
  
Lorsque vous répertoriez ces éléments, vous créez des critères pour votre mise à niveau. En d’autres termes, toute mise à niveau doit respecter cette barre pour être prise en compte. Cela vous permet d’exclure les méthodes qui ne répondent pas actuellement à vos besoins.
  
### <a name="a-simple-sample-plan"></a>Un exemple de plan simple

Il peut être nécessaire d’avoir un consensus plus large avec le leadership et d’autres administrateurs sur le chemin que votre mise à niveau SharePoint empruntera. Les administrateurs SharePoint Server collaborent souvent avec les administrateurs Microsoft SQL Server, collaborent avec des équipes de mise en réseau et de sécurité, etc. S’il existe de nombreuses parties prenantes, vous devrez peut-être créer un accord pour ou ajuster votre plan de mise à niveau et de migration. Par exemple, si vous migrez des données afin qu’une partie de votre entreprise utilise SharePoint Online dans Microsoft 365, il faudra probablement paramétrer ou tester les performances à l’intérieur de votre réseau. Les équipes concernées doivent être informées à l’avance.
  
Dans mon exemple simple, j’affiche la proposition d’un administrateur SharePoint, puis je répertorie le plan sur lequel toutes les parties prenantes se sont mises d’accord. Pour plus de clarté, documentez vos accords et décisions.
  
Le plan commence après une analyse approfondie d’une batterie de serveurs et tente d’identifier le rôle de la batterie de serveurs, les points de douleur et d’autres informations importantes qui permettront d’affiner certaines options de mise à niveau. Par la suite, une proposition de mise à niveau est faite par l’administrateur SharePoint et les parties prenantes s’accordent sur un plan d’action.
  
Ma liste de puces « la plus importante » :
  
- Disponibilité, fonctionnalités intégrées à SharePoint et normes de conformité.
    
- La plupart des données se trouve sur trois collections de sites, avec un espace de travail de réunion utilisé par une équipe de développement important et très utilisé dans plusieurs fuseaux horaires dans le monde entier.
    
- Il existe 17 autres sites largement utilisés.
    
- Deux bibliothèques de documents (Espace de travail de réunion et Documents sur la collection de sites racine) sont les plus volumineuses (plus de 8 000 documents chacun). Nous avons un grand nombre de documents archivés et de listes avec des pièces jointes de feuille de calcul.
    
- Il existe 14 listes de bibliothèques qui ont des données sensibles qui DOIVENT rester conformes.
    
- Nous DEVONS avoir la possibilité d’effectuer des conservations et des découvertes électroniques partout où nous allons.
    
- Certaines de ces données DOIVENT rester locales en raison des règles InfoSec.
    
 **Mes choix de mise à niveau et de migration :**
  
| Oui | Non |
|:-----|:-----|
|Mettre à niveau des bases de données avec l’attachement de base de données  <br/> |Mise à niveau sur place  <br/> |
|Mettre à niveau avec des batteries de serveurs côte à côte  <br/> |Mise à niveau hybride  <br/> |
|API de migration vers SPO dans Microsoft 365 (pour les données de site personnelles)  <br/> |SharePoint Hybride (pas encore nécessaire)  <br/> |
|Migrations manuelles de données vers SharePoint Online pour les données critiques  <br/> |Mise à niveau de l’Assistant FastTrack vers Microsoft 365  <br/> |
   
 **Mon plan proposé :**
  
Mettez à niveau localement, avec des versions de SharePoint côte à côte, certaines virtualisées, afin que nous puissions d’abord mettre à niveau les bases de données. Passez de SharePoint 2007 à SharePoint 2010. Les administrateurs et les développeurs testent la batterie de serveurs qui en résulte. Les utilisateurs testent la batterie de serveurs résultante. Corrigez les problèmes d’arrêt d’affichage pendant ce temps. Là encore, mettez à niveau côte à côte les bases de données SharePoint 2010 vers SharePoint 2013. Tester. Test utilisateur/pilote. Corrigez les problèmes d’arrêt d’affichage pendant ce temps.
  
- Déterminez si un objet hybride fédéré de recherche avec SPO répond à vos besoins.
    
- Envisagez [une assistance FastTrack](https://fasttrack.microsoft.com) si vous souhaitez effectuer une mise à niveau vers SharePoint Online à partir d’ici. 
    
- Déterminez si des collections de sites peuvent être déchargées vers un abonnement Microsoft 365. (Microsoft 365 répond à de [nombreuses normes de conformité](/compliance/regulatory/offering-home). Microsoft 365 dispose [d’eDiscovery](https://support.office.com/article/edea80d6-20a7-40fb-b8c4-5e8c8395f6da) et peut effectuer des [conservations](https://support.office.com/article/A18F8975-AA7F-43B4-A7D6-001D14744D8E) par le biais du Centre de conformité.) 
    
Sinon, continuez avec une mise à niveau côte à côte vers SharePoint Server 2016.
  
> [!NOTE]
> Entre les recommandations faites par les administrateurs qui planifient la mise à niveau et le processus réel se trouvent les conversations qui se produisent avec d’autres parties prenantes sur lesquelles repose la mise à niveau. Par exemple, l’économie force parfois les administrateurs à modifier leurs plans. Quelle que soit la décision finale, vous devez documenter le plan convenu, à l’avenir. Il peut ressembler à ceci : 
  
 **Mon plan d’action :**
  
En local, nous utilisons un environnement virtuel pour générer sharePoint Server 2010 et 2013 par défaut. SharePoint Server 2016 sera basé sur un nouveau matériel qui répond aux exigences système pour 2016. Nous allons effectuer des attachements de base de données pour mettre à niveau des bases de données à partir de SharePoint 2007 via toutes les versions entre celle-ci et SharePoint Server 2016. Les personnalisations de base sont recréées et testées dans l’environnement SharePoint Server 2016 pour l’instant, si les fonctionnalités natives ne répondent pas déjà à nos besoins. Si nous réussissons, nous aurons une batterie de serveurs locale sur un nouveau matériel avec des bases de données mises à niveau, et moins de personnalisations. Nous allons attacher les bases de données de contenu mises à niveau aux nouvelles collections de sites dans SharePoint Server 2013, tester, tester/piloter l’utilisateur, puis effectuer un basculement DNS vers le nouvel environnement SharePoint Server 2016 pour une utilisation en direct.
  
- Nous ne considérerons pas l’hybride fédéré entre SharePoint Server 2016 et SharePoint Online pour le moment.
    
- Environ 35 % de nos sites peuvent être transformés en nouveaux sites SPO avec des domaines de vanité, ou, en fin de compte, devenir OneDrive Entreprise stockage. Vous recherchez d’autres opportunités pour convertir des sites ou router de nouveaux sites en SPO.
    
- Une partie de cette partie de la migration sera manuelle, par glisser-déplacer vers OneDrive Entreprise sites personnels, et d’autres par l’API de migration.
    
Des étapes plus détaillées ou un certain nombre de liens vers des instructions de mise à niveau spécifiques doivent suivre un plan. L’ordinateur MOSS 2007 ne doit pas être mis hors service et les environnements virtuels doivent être maintenus pour des raisons de comparaison; toutefois, la mise à niveau sera terminée lorsque les utilisateurs seront redirigés vers SharePoint Server 2016.
  
Souvent, les principaux facteurs dans le choix d’une méthode sont le coût total de la mise à niveau et le coût dans le temps (vous en verrez plus à ce sujet dans l’article feuille de route de migration SharePoint). Toutefois, la planification à l’avance vous profitera grandement dans la définition des attentes, le choix sage, et le cadre à quoi ressemblera le succès.
  
## <a name="related-links"></a>Liens associés

[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
[Stratégie de cycle de vie Microsoft et recherche de cycle de vie](https://support.microsoft.com/lifecycle)
  
[Rechercher des partenaires Microsoft qui peuvent vous aider dans la mise à niveau ou la migration](https://partnercenter.microsoft.com/pcv/search)
