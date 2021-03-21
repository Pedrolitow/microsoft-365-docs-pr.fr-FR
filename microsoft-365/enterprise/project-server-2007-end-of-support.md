---
title: Feuille de route pour la fin de l’assistance pour Project Server 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: Le 10 octobre 2017, le support a pris fin pour Project Server 2007, Project Portfolio Server et Project 2007. Utilisez cet article pour planifier votre mise à niveau maintenant.
ms.openlocfilehash: 12447eb2a021b3f92e3557b2c3ea87e859841346
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50927347"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Project Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

La prise en charge des serveurs et applications Office 2007 a pris fin en 2017 et vous devez prendre en compte les plans de migration. Si vous utilisez actuellement Project Server 2007 et les produits associés, notez les dates de fin de support suivantes :
  
|**Produit**|**Date de fin du support**|
|:-----|:-----|
|Project Server 2007  <br/> |10 octobre 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 octobre 2017  <br/> |
|Project 2007 Standard  <br/> |10 octobre 2017  <br/> |
|Project 2007 Professionnel  <br/> |10 octobre 2017  <br/> |
   
Pour plus d’informations sur les serveurs Office 2007 qui ont atteint la mise à niveau, voir Mise à niveau à partir des serveurs et produits [clients Office 2007.](upgrade-from-office-2007-servers-and-products.md)
  
## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

La plupart des produits Microsoft ont un cycle de vie de support au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Étant donné que Project Server 2007 a atteint sa fin de prise en charge le 10 octobre 2017, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.
    
- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Project Server 2007 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées précédemment, nous vous recommandons vivement de migrer à partir de Project Server 2007 dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Si vous utilisez Project Server 2007, vous devez explorer vos options de migration, à savoir :
  
- Migrer vers Project Online
    
- Migrer vers une version plus récente sur site de Project Server (de préférence Project Server 2016)
    
|**Pourquoi préfère-t-il migrer vers Project Online ?**|**Pourquoi préférer migrer vers Project Server 2016 ?**|
|:-----|:-----|
| J’ai des utilisateurs mobiles.  <br/> <br/>Les coûts de migration sont un problème important (matériel, logiciel, heures et efforts à implémenter). <br/><br/>  Après la migration, les coûts liés à la maintenance de mon environnement sont un problème majeur (par exemple, les mises à jour automatiques, le temps de fonctionnement garanti, et ainsi de suite).  <br/> | Les règles d’entreprise m’empêchent d’exploiter mon entreprise dans le cloud.<br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.  |
   
> [!NOTE]
> Pour plus d’informations sur les options de déplacement à partir de vos serveurs Office 2007, voir Ressources pour vous aider à mettre à niveau les serveurs et [clients Office 2007.](upgrade-from-office-2007-servers-and-products.md) Notez que Project Server ne prend pas en charge une configuration hybride, car Project Server et Project Online ne peuvent pas partager la même pool de ressources. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Considérations importantes lors de la migration à partir de Project Server 2007

Prenons les considérations suivantes lorsque vous prévoyez de migrer à partir de Project Server 2007 :
  
- **Obtenir de l’aide d’un** partenaire Microsoft : la mise à niveau à partir de Project Server 2007 peut être difficile et nécessite une préparation et une planification très complexes. Cela peut être particulièrement difficile si vous n’étiez pas la personne qui a installé Project Server 2007 à l’origine. Heureusement, certains partenaires Microsoft peuvent vous aider, que vous envisagez de migrer vers Project Server 2016 ou Project Online. Recherchez un partenaire Microsoft pour vous aider lors de votre migration sur [l’Microsoft Partner Center.](https://go.microsoft.com/fwlink/p/?linkid=841249) Recherchez le terme  *Gestion de projets et* de portefeuilles Or pour afficher la liste de tous les partenaires Microsoft qui ont une expertise dans Project. 
    
- **Planifier vos personnalisations** : la plupart des personnalisations que vous avez réalisées dans votre environnement Project Server 2007 peuvent ne pas fonctionner lorsque vous migrez vers Project Server 2016 ou Project Online. Il existe des différences significatives dans l’architecture Project Server entre les versions. Les systèmes d’exploitation, les serveurs de base de données et les navigateurs web clients requis qui sont pris en charge diffèrent également. Planifiez comment tester ou reconstruire vos personnalisations pour le nouvel environnement. La planification offre également une bonne opportunité de déterminer si chaque personnalisation est toujours nécessaire. Pour plus d'informations, voir [Create a plan for current customizations during upgrade to SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **Temps et patience** : la planification, l’exécution et les tests de mise à niveau prennent du temps et des efforts, en particulier si vous faites une mise à niveau vers Project Server 2016. Par exemple, si vous migrez de Project Server 2007 vers Project Server 2016, vous devez d’abord migrer vers Project Server 2010, vérifier vos données, puis faire la même chose lorsque vous migrez vers chaque version successive. Vous pouvez consulter un partenaire Microsoft pour obtenir des estimations de la durée et du coût.
    
## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2007 vers Project Online, vous pouvez faire les choses suivantes pour migrer manuellement vos données de plan de projet :
  
1. Enregistrez vos plans de projet de Project Server 2003 au format .mpp.
    
2. Dans Project Professionnel 2013, Project Professionnel 2016 ou le client de bureau Project Online, ouvrez chaque fichier .mpp, puis enregistrez-le et publiez-le dans Project Online.
    
Vous pouvez créer manuellement votre configuration Microsoft Project Web App (PWA) dans Project Online. Par exemple, recréez les champs personnalisés ou les calendriers d’entreprise nécessaires. Les partenaires Microsoft peuvent également vous aider dans ce processus.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Comment configurer et utiliser Project Online <br/> |
|[Project Online Service Descriptions](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |Informations sur les différents plans Project Online disponibles <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version plus récente sur site de Project Server

Nous pensons vivement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migreant vers Project Online. Toutefois, nous comprenons également que certaines organisations doivent conserver les données de projet dans un environnement local. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2007 vers Project Server 2010, Project Server 2013 ou Project Server 2016.
  
Si vous ne pouvez pas migrer vers Project Online, nous vous recommandons de migrer vers Project Server 2016. Project Server 2016 inclut toutes les fonctionnalités des versions précédentes de Project Server. Il correspond le mieux à l’expérience disponible avec Project Online, bien que certaines fonctionnalités soient disponibles uniquement dans Project Online.
  
Après chaque migration, vous devez vérifier que vos données ont été correctement migrées.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Comment migrer vers Project Server 2016 ?

Les différences architecturales entre Project Server 2007 et Project Server 2016 empêchent un chemin de migration direct. Vous devez donc migrer vos données Project Server 2007 vers chaque version successive de Project Server jusqu’à atteindre Project Server 2016.
  
Suivez ces étapes pour Project Server 2016 :
  
1. Migrez de Project Server 2007 vers Project Server 2010.
    
2. Migrez de Project Serve 2010 vers Project Server 2013.
    
3. Migrez de Project Server 2013 vers Project Server 2016.
    
Après chaque migration, assurez-vous que vos données ont été correctement migrées.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Étape 1 : Migrer de Project Server 2007 vers Project Server 2010

Pour obtenir une description complète de ce que vous devez faire pour mettre à niveau project server 2007 vers Project Server 2010, voir Mise à niveau vers [Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble de la mise à niveau de Project Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |Une vue d’affichage de haut niveau de ce que vous devez faire pour mettre à niveau de Project Server 2007 vers Project Server 2010 <br/> |
|[Planifier la mise à niveau vers Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |Considérations relatives à la planification lors de la mise à niveau de Project Server 2007 vers Project Server 2010, y compris la version système requise  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Comment mettre à niveau ?

Pour plus d’informations, [voir Mise à niveau vers Project Server 2010.](/previous-versions/office/project-server-2010/gg502590(v=office.14)) Mais il est important de comprendre qu’il existe deux méthodes distinctes que vous pouvez utiliser pour la mise à niveau :
  
- **Mise à niveau avec attachement de base de données :** Cette méthode ne permet de mettre à niveau que le contenu de votre environnement, et non les paramètres de configuration. Elle est requise si vous faites une mise à niveau à partir d’Office Project Server 2007 déployé sur du matériel qui prend uniquement en charge un système d’exploitation serveur 32 bits. Il existe deux types de méthodes de mise à niveau avec attachement de base de données :
    
  - **** Mise à niveau complète avec attachement de base de données : migre les données de projet stockées dans les bases de données Office Project Server 2007, ainsi que les données du site Microsoft Project Web App stockées dans une base de données de contenu SharePoint.
    
  - **Mise à niveau principale *avec attachement de base*** de données : migre uniquement les données de projet stockées dans les bases de données Project Server.
    
- **Mise à niveau sur place**: les données de configuration de la batterie de serveurs et tout le contenu de la batterie de serveurs sont mises à niveau sur le matériel existant dans un ordre fixe. Lorsque vous démarrez le processus de mise à niveau, le programme d’installation met l’ensemble de la batterie de serveurs hors connexion. Les sites web et les sites Microsoft Project Web App ne sont pas disponibles tant que la mise à niveau n’est pas terminée, puis le programme d’installation redémarre le serveur. Après avoir commencé une mise à niveau sur place, vous ne pouvez pas suspendre la mise à niveau ou revenir à la version précédente. Il est préférable de mettre en miroir votre environnement de production et d’effectuer la mise à niveau sur place vers cet environnement, et non dans votre environnement de production. 
    
Ressources supplémentaires :
  
- [SuperFlow pour la mise à niveau de Microsoft Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Migration de Project Server 2007 vers Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Considérations sur la mise à niveau pour project web app WebParts](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Kit de développement logiciel (SDK) Project](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>Étape 2 : Migrer vers Project Server 2013

Après avoir vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vers Project Server 2013.
  
Pour obtenir une description complète de ce que vous devez faire pour mettre à niveau project server 2010 vers Project Server 2013, voir Mise à niveau vers [Project Server 2013](/project/upgrade-to-project-server-2016). 
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/upgrade-to-project-server-2016) <br/> |Vue d’ensemble de la mise à niveau de Project Server 2010 vers Project Server 2013  <br/> |
|[Planifier la mise à niveau vers Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |Considérations relatives à la planification lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la version système requise <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à savoir sur la mise à niveau vers cette version

[Les nouveautés de la mise à niveau de Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) décrivent les modifications importantes apportées à la mise à niveau pour cette version. Les plus notables sont : 
  
- Il n’existe aucune mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour la mise à niveau de Project Server 2010 vers Project Server 2013.
    
- Le processus de mise à niveau convertira non seulement vos données Project Server 2010 au format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.
    
- Dans les versions 2013, SharePoint Server et Project Server ont été changés en authentification basée sur les revendications. Si vous utilisez l’authentification classique, vous devez prendre en compte ce facteur pour votre mise à niveau. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
Ressources supplémentaires :
  
- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La grande consolidation de bases de données, migration de Project Server 2010 vers 2013 en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Étape 3 : Migrer vers Project Server 2016

Après avoir vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vers Project Server 2016.
  
Pour obtenir une description complète de ce que vous devez faire pour la mise à niveau de Project Server 2013 vers Project Server 2016, voir Mise à niveau vers [Project Server 2016.](//project/upgrading-to-project-server-2016)
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d'ensemble du processus de mise à niveau vers Project Server 2016](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |Vue d’ensemble de la mise à niveau de Project Server 2013 vers Project Server 2016 <br/> |
|[Planifier la mise à niveau vers Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |Considérations sur la planification de la mise à niveau de Project Server 2013 vers Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à savoir sur la mise à niveau vers cette version

Ce que vous devez savoir sur la mise à [niveau de Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) vous indique certaines modifications importantes pour la mise à niveau pour cette version, notamment :
  
- Lorsque vous créez votre environnement Project Server 2016 vers lequel vous allez migrer vos données Project Server 2013, les fichiers d’installation Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, [voir Déployer Project Server 2016.](/project/deploy-project-server-2016)
    
- Les plans de ressources sont supprimés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers engagements de ressources dans Project Server 2016 et dans Project Online. Voir [Vue d’ensemble : engagements de](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) ressources pour plus d’informations. 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrer à partir de Portfolio Server 2007

Project Portfolio Server 2007 a été utilisé avec Project Server 2007 pour la stratégie de portefeuille, la hiérérisation et l’optimisation. Aucune version supplémentaire de Project Portfolio Server n’a été créée après cette version. Toutefois, les fonctionnalités de gestion de portefeuille sont disponibles dans Project Server 2016 et la version Premium de Project Online. Toutefois, les données de Project Portfolio Server 2007 ne peuvent pas être migrées vers l’une ou l’autre. Les données telles que les pilotes d’entreprise devront être recréés.
  
Autres ressources :
  
- [Descriptions du service Project Online :](/office365/servicedescriptions/project-online-service-description/project-online-service-description) Consultez les fonctionnalités de gestion de portefeuille incluses dans Project Server 2016 et Project Online Premium.
    
- [Microsoft Office guide de migration Project Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Rubriques connexes

[Feuille de route de fin de l’assistance pour SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[Ressources pour vous aider à mettre à niveau des serveurs et des clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
