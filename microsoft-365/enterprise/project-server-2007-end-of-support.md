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
description: Le 10 octobre 2017, la prise en charge s’est terminée pour Project Server 2007, Project Portfolio Server et Project 2007. Utilisez cet article pour planifier votre mise à niveau maintenant.
ms.openlocfilehash: f59b319ec39c6b2d1df0876c916332491f1bb0f6
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519798"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Project Server 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Prise en charge terminée pour les serveurs et applications Office 2007 dans 2017, et vous devez prendre en compte les plans de migration. Si vous utilisez actuellement Project Server 2007 et les produits associés, notez les dates de fin de prise en charge suivantes :
  
|**Produit**|**Fin de la date de prise en charge**|
|:-----|:-----|
|Project Server 2007  <br/> |10 octobre 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 octobre 2017  <br/> |
|Project 2007 standard  <br/> |10 octobre 2017  <br/> |
|Project 2007 professionnel  <br/> |10 octobre 2017  <br/> |
   
Pour plus d’informations sur les serveurs Office 2007 qui arrivent à la retraite, voir [Upgrade from Office 2007 Servers and client Products](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la *fin de la prise en charge* ?

La plupart des produits Microsoft ont un cycle de vie de la prise en charge au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la publication initiale du produit. La fin de ce cycle de vie est appelée fin de la prise en charge du produit. Étant donné que Project Server 2007 a atteint sa fin de prise en charge le 10 octobre 2017, Microsoft ne fournit plus :
  
- Support technique pour les problèmes susceptibles de se produire.
    
- Correctifs de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.
    
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Project Server 2007 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées précédemment, nous vous recommandons vivement de procéder à une migration à partir de Project Server 2007 dès que possible.
  
## <a name="what-are-my-options"></a>Quelles sont les options ?

Si vous utilisez Project Server 2007, vous devez explorer vos options de migration, qui sont les suivantes :
  
- Migrer vers Project Online
    
- Migrer vers une version plus récente de Project Server (de préférence Project Server 2016)
    
|**Pourquoi migrer vers Project Online ?**|**Pourquoi migrer vers Project Server 2016**|
|:-----|:-----|
| J’ai des utilisateurs mobiles.  <br/> <br/>Les coûts de migration sont une préoccupation importante (matériel, logiciel, heures et effort à mettre en œuvre). <br/><br/>  Après la migration, les coûts de maintenance de mon environnement représentent une préoccupation majeure (par exemple, mises à jour automatiques, temps de fonctionnement garanti, etc.).  <br/> | Les règles d’entreprise m’empêchent de faire fonctionner mon entreprise dans le Cloud.<br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.  |
   
> [!NOTE]
> Pour plus d’informations sur les options de navigation à partir de vos serveurs Office 2007, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients office 2007](upgrade-from-office-2007-servers-and-products.md). Notez que Project Server ne prend pas en charge une configuration hybride, car Project Server et Project Online ne peuvent pas partager la même liste de ressources. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>Considérations importantes lors de la migration à partir de Project Server 2007

Tenez compte des éléments suivants lorsque vous envisagez de migrer à partir de Project Server 2007 :
  
- **Obtenir de l’aide auprès d’un partenaire Microsoft : la** mise à niveau à partir de Project Server 2007 peut être complexe et nécessite une préparation et une planification très nombreuses. Cela peut s’avérer particulièrement complexe si vous n’étiez pas la personne qui a configuré initialement Project Server 2007. Heureusement, il existe des partenaires Microsoft qui peuvent vous aider, que vous souhaitiez migrer vers Project Server 2016 ou Project online. Recherchez un partenaire Microsoft pour vous aider dans votre migration sur le [Centre de partenaires Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). Recherchez la liste de tous les partenaires Microsoft qui disposent d’une expertise dans Project en fonction de la  *gestion des projets et des portefeuilles Gold* . 
    
- **Planifier vos personnalisations** : bon nombre des personnalisations effectuées dans votre environnement Project Server 2007 risquent de ne pas fonctionner lors de la migration vers project Server 2016 ou Project online. Il existe des différences notables dans l’architecture de Project Server entre les versions. Les systèmes d’exploitation, les serveurs de bases de données et les navigateurs Web clients requis et pris en charge diffèrent également. Planifiez la procédure de test ou de reconstruction de vos personnalisations pour le nouvel environnement. La planification permet également de déterminer si chaque personnalisation est toujours nécessaire. Pour plus d'informations, voir [Create a plan for current customizations during upgrade to SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=842061). 
    
- **Temps et patience** : la planification, l’exécution et le test de la mise à niveau prennent du temps et des efforts, notamment si vous effectuez une mise à niveau vers Project Server 2016. Par exemple, si vous effectuez une migration de Project Server 2007 vers Project Server 2016, vous devez d’abord migrer vers Project Server 2010, vérifier vos données, puis effectuer la même opération lors de la migration vers chaque version successive. Vous voudrez peut-être vérifier auprès d’un partenaire Microsoft que vous estimez le temps qu’il va prendre et ce qu’il va coûter.
    
## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2007 vers Project Online, vous pouvez effectuer les opérations suivantes pour migrer manuellement vos données de plan de projet :
  
1. Enregistrez vos plans de projet à partir de Project Server 2003 au format. mpp.
    
2. Dans Project Professionnel 2013, Project Professional 2016 ou le client de bureau Project Online, ouvrez chaque fichier. mpp, puis enregistrez-le et publiez-le dans Project online.
    
Vous pouvez créer manuellement votre configuration de Microsoft Project Web App (PWA) dans Project online. Par exemple, recréez les champs personnalisés ou les calendriers d’entreprise nécessaires. Les partenaires de Microsoft peuvent également vous aider dans ce processus.
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |Procédure de configuration et d’utilisation de Project Online <br/> |
|[Descriptions de service Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088) <br/> |Informations sur les différents plans Project Online à votre disposition <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en migrant vers Project online. Mais nous comprenons également que certaines organisations doivent conserver les données de projet dans un environnement local. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2007 vers Project Server 2010, Project Server 2013 ou Project Server 2016.
  
Si vous ne pouvez pas effectuer une migration vers Project Online, nous vous recommandons de migrer vers Project Server 2016. Project Server 2016 inclut toutes les fonctionnalités des versions précédentes de Project Server. Il correspond le mieux à l’expérience disponible avec Project Online, bien que certaines fonctionnalités ne soient disponibles que dans Project online.
  
Après chaque migration, vous devez vérifier que vos données ont été correctement migrées.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>Comment migrer vers Project Server 2016 ?

Les différences d’architecture entre Project Server 2007 et Project Server 2016 empêchent un chemin de migration direct. Par conséquent, vous devez migrer vos données Project Server 2007 vers chaque version successive de Project Server jusqu’à ce que vous accédiez à Project Server 2016.
  
Suivez les étapes ci-dessous pour Project Server 2016 :
  
1. Migrer de Project Server 2007 vers Project Server 2010.
    
2. Migrer de Project serve 2010 vers Project Server 2013.
    
3. Migrer de Project Server 2013 vers Project Server 2016.
    
Après chaque migration, assurez-vous que vos données ont été correctement migrées.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>Étape 1 : migrer de Project Server 2007 vers Project Server 2010

Pour obtenir une description complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2007 vers Project Server 2010, consultez la rubrique [Upgrade to Project server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812).
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble de la mise à niveau vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841813) <br/> |Vue de haut niveau de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2007 vers Project Server 2010 <br/> |
|[Planifier une mise à niveau vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841815) <br/> |Considérations relatives à la planification lors de la mise à niveau de Project Server 2007 vers Project Server 2010, y compris la configuration système requise  <br/> |
   
#### <a name="how-do-i-upgrade"></a>Comment effectuer une mise à niveau ?

Pour plus d’informations, consultez la rubrique [Upgrade to Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841812). Toutefois, il est important de comprendre qu’il existe deux méthodes distinctes que vous pouvez utiliser pour effectuer la mise à niveau :
  
- **Mise à niveau avec attachement de base de données :** Cette méthode met uniquement à niveau le contenu de votre environnement, pas les paramètres de configuration. Elle est requise si vous effectuez une mise à niveau à partir d’Office Project Server 2007 déployé sur du matériel qui prend uniquement en charge un système d’exploitation de serveur 32 bits. Il existe deux types de méthodes de mise à niveau par attachement de base de données :
    
  - ***Mise à niveau complète* avec liaison de base de données** : migre les données de projet stockées dans les bases de données Office Project Server 2007, ainsi que les données de site Microsoft Project Web App stockées dans une base de données de contenu SharePoint.
    
  - ***Mise à niveau principale* avec liaison de base de données** : migre uniquement les données de projet stockées dans les bases de données Project Server.
    
- **Mise à niveau sur place**: les données de configuration de la batterie de serveurs et tout le contenu de la batterie de serveurs sont mis à niveau sur le matériel existant dans un ordre fixe. Lorsque vous démarrez le processus de mise à niveau, le programme d’installation met l’ensemble de la batterie hors connexion. Les sites Web et les sites Microsoft Project Web App sont indisponibles jusqu’à ce que la mise à niveau soit terminée, puis que le programme d’installation redémarre le serveur. Après avoir commencé une mise à niveau sur place, vous ne pouvez pas suspendre la mise à niveau ou revenir à la version précédente. Il est préférable de créer une image en miroir de votre environnement de production et de procéder à la mise à niveau sur place vers cet environnement, et non dans votre environnement de production. 
    
Ressources supplémentaires :
  
- [SuperFlow pour la mise à niveau de Microsoft Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841277)
    
- [Migration de Project Server 2007 vers Project Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841278)
    
- [Considérations relatives à la mise à niveau des composants WebPart Project Web App](https://go.microsoft.com/fwlink/p/?linkid=841276)
    
- [Kit de développement logiciel (SDK) Project](https://go.microsoft.com/fwlink/p/?linkid=841275)
    
### <a name="step-2-migrate-to-project-server-2013"></a>Étape 2 : migrer vers Project Server 2013

Une fois que vous avez vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vers Project Server 2013.
  
Pour obtenir une description complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013, consultez la rubrique [Upgrade to Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822). 
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822) <br/> |Vue d’ensemble de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013  <br/> |
|[Planifier une mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823) <br/> |Considérations relatives à la planification lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la configuration système requise <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à connaître sur la mise à niveau vers cette version

[Nouveautés de la mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) décrit les modifications importantes apportées à la mise à niveau pour cette version. Les plus notables sont les suivants : 
  
- Il n’existe pas de mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour la mise à niveau de Project Server 2010 vers Project Server 2013.
    
- Le processus de mise à niveau ne convertit pas uniquement vos données Project Server 2010 au format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.
    
- Dans les versions 2013, SharePoint Server et Project Server sont modifiés pour l’authentification basée sur les revendications. Si vous utilisez l’authentification classique, vous devez tenir compte de ce facteur pour votre mise à niveau. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=841825).
    
Ressources supplémentaires :
  
- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)
    
- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)
    
- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [La consolidation de base de données, Project Server 2010 vers 2013 migration en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>Étape 3 : migrer vers Project Server 2016

Une fois que vous avez vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vers Project Server 2016.
  
Pour obtenir une description complète de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016, consultez la rubrique [Upgrade to Project server 2016](https://docs.microsoft.com//project/upgrading-to-project-server-2016).
  
Ressources clés :
  
|**Ressource**|**Description**|
|:-----|:-----|
|[Vue d'ensemble du processus de mise à niveau vers Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841260) <br/> |Vue d’ensemble de ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016 <br/> |
|[Planifier la mise à niveau vers Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841826) <br/> |Considérations relatives à la planification de la mise à niveau de Project Server 2013 vers Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>Éléments à connaître sur la mise à niveau vers cette version

Les [éléments que vous devez connaître à propos de la mise à niveau de Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841827) vous indiquent des modifications importantes pour la mise à niveau de cette version, notamment :
  
- Lorsque vous créez votre environnement Project Server 2016 vers lequel migrer vos données Project Server 2013, les fichiers d’installation de Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, consultez la rubrique [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).
    
- Les plans de ressources sont déconseillés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers les engagements de ressources dans Project Server 2016 et dans Project online. Pour plus d’informations, voir [vue d’ensemble : engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) . 
    
## <a name="migrate-from-portfolio-server-2007"></a>Migrer à partir du serveur de portefeuille 2007

Project Portfolio Server 2007 a été utilisé avec Project Server 2007 pour la stratégie de portefeuille, la définition des priorités et l’optimisation. Aucune version supplémentaire de Project Portfolio Server n’a été créée après cette version. Toutefois, les fonctionnalités de gestion de portefeuilles sont disponibles dans Project Server 2016 et la version Premium de Project online. Toutefois, les données de Project Portfolio Server 2007 ne peuvent pas être migrées vers. Les données telles que les axes stratégiques doivent être recréées.
  
Autres ressources :
  
- [Description du service Project Online :](https://go.microsoft.com/fwlink/p/?linkid=841280) Voir les fonctionnalités de gestion de portefeuille comprises dans Project Server 2016 et Project Online Premium.
    
- [Guide de migration de Microsoft Office Project Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>Voir aussi

[Feuille de route de prise en charge de SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
  
