---
title: Feuille de route Project Server 2010 end-support
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
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
description: Les fins de prise en charge de Project Server 2010 se terminent le 13 avril 2021. Utilisez cet article pour effectuer une mise à niveau vers Project Online ou une version plus récente de Project Server en local.
ms.openlocfilehash: 239b3d93cfa6a1184ea21225fa97732712b8eb14
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519701"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge de Project Server 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Project Server 2010 atteindra la fin de la prise en charge le **13 avril 2021**. Cette date a été étendue à partir de la date de fin de prise en charge précédente du 13 octobre 2020. Si vous utilisez actuellement Project Server 2010, Notez que les produits associés ont les dates de fin de prise en charge suivantes :

|Produit |Fin de la date de prise en charge|
|---|---|
|Project 2010 standard|13 octobre 2020|
|Project 2010 professionnel|13 octobre 2020|

Pour plus d’informations sur la finalisation de l’assistance, consultez la rubrique [Upgrade from Office 2010 Servers and client Products](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la *fin de la prise en charge* ?

Presque tous les produits Microsoft ont un cycle de vie de la prise en charge, pendant lesquels ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans après la publication initiale du produit. La fin de ce cycle de vie est appelée fin de la prise en charge du produit. Une fois que Project Server 2010 a atteint sa fin d’assistance le 13 avril 2021, Microsoft ne fournira plus les éléments suivants :

- Support technique pour les problèmes susceptibles de se produire.

- Correctifs de bogues pour les problèmes découverts et susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Project Server 2010 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées précédemment, nous vous recommandons vivement de procéder à une migration à partir de Project Server 2010 dès que possible.

## <a name="what-are-my-options"></a>Quelles sont les options ?

Vos options de migration sont les suivantes :

- Migrer vers Project Online

- Migrer vers une version plus récente de Project Server (de préférence Project Server 2019)

Voici les deux chemins que vous pouvez suivre pour éviter la fin de la prise en charge de Project Server 2010.

![Chemins de mise à niveau vers Project Server 2010](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Pourquoi choisir de migrer vers Project Server 2019 ?|Pourquoi choisir de migrer vers Project Online ?|
|---|---|
|Les règles d’entreprise m’empêchent de faire fonctionner mon entreprise dans le Cloud.  <br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.|J’ai des utilisateurs mobiles ou distants.<br/><br/>  Les coûts de migration des serveurs locaux constituent une préoccupation importante (matériel, logiciel, temps et efforts à mettre en œuvre, etc.). <br/><br/>  Après la migration, les coûts de maintenance de mon environnement constituent une préoccupation (par exemple, mises à jour automatiques, temps de fonctionnement garanti, etc.).|

> [!NOTE]
> Pour plus d’informations sur vos options de migration, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md). Notez que Project Server ne prend pas en charge la configuration hybride, car Project Server et Project Online ne peuvent pas partager la même liste de ressources.

### <a name="what-are-my-options-for-project-client"></a>Quelles sont les options de mon client Project ?

Si vous utilisez Project Professionnel 2010 ou Project standard 2010, vos options sont les suivantes :

- Passer à une version plus récente de Project Professionnel ou Project standard
- Accéder à une solution en ligne, telle que Project Online ou Project pour le Web

#### <a name="move-to-a-newer-version-of-project-client"></a>Passer à une version plus récente du client Project

Si vous effectuez une migration à partir de Project standard 2010, vous pouvez passer à une version plus récente de Project standard (Project standard 2016 ou Project standard 2019). Nous vous recommandons de passer à la version la plus récente pour tirer parti des fonctionnalités les plus récentes. La migration vers une version moins récente (Project standard 2016) signifie également que vous devrez remigrer plus tôt.

De même, si vous effectuez une migration à partir de Project Professionnel 2010, vous pouvez passer à une version plus récente (Project Professionnel 2019 ou Project Professionnel 2016). De nouveau, accédez à la version la plus récente, si possible. Si vous utilisez Project professionnel pour vous connecter à Project Server, assurez-vous d’effectuer la migration vers une version de Project professionnel qui se connecte avec la version de Project Server que vous utilisez.

Project Professional 2010 les utilisateurs peuvent également migrer vers le client de bureau Project Online, qui est une version basée sur un abonnement de Project Professionnel 2019. Il est inclus dans les abonnements de plan de projet 3 et de plan de projet 5.

#### <a name="move-to-an-online-solution"></a>Déplacer vers une solution en ligne

Vous pouvez également effectuer une migration depuis Project Professionnel 2010 ou Project standard 2010 vers une solution en ligne basée sur l’abonnement à un projet. Project Plan 3 et plan 5 incluent Project Online et la dernière offre Cloud, [Project pour le Web](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Les deux offrent de nouvelles fonctionnalités et les avantages qui méritent d’être explorés.

Pour plus d’informations sur les fonctionnalités et les licences, voir [Description du service Microsoft Project](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description).

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Considérations importantes pour la migration à partir de Project Server 2010

Tenez compte des éléments suivants lorsque vous envisagez de migrer à partir de Project Server 2010 :

- **Obtenir de l’aide auprès d’un fournisseur de solutions Microsoft** -une mise à niveau à partir de Project Server 2010 peut s’avérer difficile. Elle nécessite une préparation et une planification très nombreuses. Cela peut s’avérer particulièrement complexe si vous n’étiez pas la personne qui a configuré initialement Project Server 2010. Les fournisseurs de solutions Microsoft sont disponibles pour vous aider, que vous envisagez de migrer vers Project Server 2019 ou Project online. Recherchez un fournisseur de solutions dans le [Centre de fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Plan for your customizations** : les personnalisations dans votre environnement project Server 2010 risquent de ne pas fonctionner lors de la migration vers project Server 2019 ou Project online. Il existe des différences notables dans l’architecture de Project Server entre les versions. En outre, les systèmes d’exploitation, les serveurs de bases de données et les navigateurs Web requis qui fonctionnent avec les versions diffèrent. Préparez-vous à tester ou à recréer vos personnalisations dans le nouvel environnement. Profitez de cette opportunité pour déterminer si des personnalisations spécifiques sont toujours nécessaires. Pour plus d'informations, voir [Create a plan for current customizations during upgrade to SharePoint 2013](https://docs.microsoft.com/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Temps et patience** : la planification de la mise à niveau, l’exécution et les tests prendront beaucoup de temps et de travail, en particulier pour une mise à niveau vers Project Server 2019. Si vous effectuez une migration de Project Server 2010 vers Project Server 2019, vous devez d’abord effectuer une migration vers Project Server 2013, vérifier vos données, puis migrer vers Project Server 2016, puis vers Project Server 2019. Vous voudrez peut-être vérifier auprès d’un fournisseur de solutions Microsoft une période et un coût estimé pour les aider.

## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2010 vers Project Online, vous pouvez effectuer les étapes suivantes pour migrer manuellement vos données de plan de projet :

1. Enregistrez vos plans de projet à partir de Project Server 2010 au format. mpp.

2. À l’aide de Project Professionnel 2016, Project Professional 2019 ou le client de bureau Project Online, ouvrez chaque fichier. mpp, puis enregistrez-le et publiez-le dans Project online.

Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréer des champs personnalisés ou des calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également aider à ce processus.

Ressources clés :

|Resource|Description|
|---|---|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Procédure de configuration et d’utilisation de Project Online|
|[Description du service Project Online](https://go.microsoft.com/fwlink/p/?linkid=829088)|Informations sur les différents plans Project Online disponibles|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Nous pensons fortement que vous pouvez obtenir la meilleure valeur et l’expérience utilisateur en migrant vers Project online. Toutefois, nous comprenons également que certaines organisations doivent conserver les données de projet en local. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2010 vers Project Server 2013, Project Server 2016 ou Project Server 2019.

Si vous ne pouvez pas effectuer une migration vers Project Online, nous vous recommandons de migrer vers Project Server 2019. Project Server 2019 inclut la plupart des fonctionnalités clés dans les versions précédentes de Project Server. Il correspond le mieux à l’expérience disponible avec Project Online, bien que certaines fonctionnalités ne soient disponibles que dans Project online.

Une fois toutes les migrations terminées, vérifiez que vos données ont été correctement migrées.

> [!NOTE]
> Si vous êtes limité à une solution locale et que vous envisagez de migrer uniquement vers Project Server 2013, sachez que cette version n’a que quelques années de prise en charge. Date de fin de prise en charge pour Project Server 2013 avec Service Pack 2 (13 octobre 2023). Pour plus d’informations sur les dates de fin de prise en charge, consultez la rubrique [stratégie de cycle de vie des produits Microsoft](https://go.microsoft.com/fwlink/p/?linkid=842066).

### <a name="how-do-i-migrate-to-project-server-2019"></a>Comment migrer vers Project Server 2019 ?

Les différences d’architecture entre Project Server 2010 et Project Server 2019 empêchent un chemin de migration direct. Par conséquent, vous devez migrer vos données Project Server 2010 vers chaque version successive de Project Server jusqu’à ce que vous accédiez à Project Server 2019. Étapes de mise à niveau de Project Server 2010 vers Project Server 2019 :

1. Migrer vers Project Server 2013.

2. Migrer de Project serve 2013 vers Project Server 2016.

3. Migrer de Project Server 2016 vers Project Server 2019.

Une fois toutes les migrations terminées, vérifiez que vos données ont été correctement migrées.

### <a name="step-1-migrate-to-project-server-2013"></a>Étape 1 : migrer vers Project Server 2013

Pour obtenir des informations détaillées sur la mise à niveau de Project Server 2010 vers Project Server 2013, consultez la rubrique [Upgrade to Project server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841822)

  Obtenez une vue d’ensemble de haut niveau sur la mise à niveau de Project Server 2010 vers Project Server 2013.
- [Planifier une mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841823)

  Examinez les considérations relatives à la planification lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la configuration système requise.

- [Nouveautés de la mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841824) couvre les modifications importantes de cette version, notamment les suivantes :

   - Il n’existe pas de mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013.

   - Le processus de mise à niveau ne convertit pas uniquement vos données Project Server 2010 au format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.

   - SharePoint Server 2013 et Project Server 2013 ont été remplacés par l’authentification basée sur les revendications à partir de la version précédente. Si vous utilisez l’authentification classique, vous devez tenir compte de ce qui suit lors de la mise à niveau. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013]( https://docs.microsoft.com/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](https://go.microsoft.com/fwlink/p/?linkid=841274)

- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](https://go.microsoft.com/fwlink/p/?linkid=841272)

- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [La consolidation de base de données, Project Server 2010 vers 2013 migration en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>Étape 2 : migrer vers Project Server 2016

Une fois que vous avez effectué le déplacement vers Project Server 2013 et vérifiez que vos données ont été correctement migrées, l’étape suivante consiste à migrer vers Project Server 2016.

Pour plus d’informations, consultez la rubrique [Upgrade to Project Server 2016](https://docs.microsoft.com/Project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d'ensemble du processus de mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/overview-of-the-project-server-2016-upgrade-process)

  Découvrez ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2016](https://docs.microsoft.com/Project/plan-for-upgrade-to-project-server-2016)

  Examinez les points à prendre en compte lors de la mise à niveau de Project Server 2013 vers Project Server 2016.

Les [éléments que vous devez connaître à propos de la mise à niveau vers Project Server 2016](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2016#thingknow) couvrent les modifications importantes pour la mise à niveau vers cette version, notamment :

- Lorsque vous créez votre environnement Project Server 2016, Notez que les fichiers d’installation de Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, consultez la rubrique [Deploy Project Server 2016](https://go.microsoft.com/fwlink/p/?linkid=841829).

- Les plans de ressources sont déconseillés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers les engagements de ressources dans Project Server 2016 et dans Project online. Pour plus d’informations, voir [vue d’ensemble : engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) .

### <a name="step-3-migrate-to-project-server-2019"></a>Étape 3 : migrer vers Project Server 2019

Après avoir effectué une migration vers Project Server 2016 et vérifié que vos données ont été correctement migrées, l’étape suivante consiste à migrer vos données vers Project Server 2019.

Pour savoir ce que vous devez faire pour effectuer une mise à niveau de Project Server 2016 vers Project Server 2019, consultez la rubrique [Upgrade to Project server 2019](https://docs.microsoft.com/Project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2019](https://docs.microsoft.com/project/overview-of-the-project-server-2019-upgrade-process)

  Découvrez de façon approfondie ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2019](https://docs.microsoft.com/project/plan-for-upgrade-to-project-server-2019)

  Examinez les considérations relatives à la planification de la mise à niveau de Project Server 2016 vers Project Server 2019.

- [Choses à savoir sur la mise à niveau de Project Server 2019](https://go.microsoft.com/fwlink/p/?linkid=841827)<br/><br/>Découvrez les modifications importantes pour la mise à niveau vers cette version, notamment :

   - Le processus de mise à niveau consiste à migrer vos données de votre base de données Project Server 2016 vers la base de données de contenu SharePoint Server 2019.  Project Server 2019 ne créera plus sa propre base de données Project Server dans la batterie de serveurs SharePoint Server.

   - Après la mise à niveau, vous devez tenir compte de plusieurs modifications apportées dans Project Web App.  Pour plus d’informations, consultez [la rubrique what’s New in Project Server 2019](https://docs.microsoft.com/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**Autres ressources**:

- [Description du service Project Online](https://go.microsoft.com/fwlink/p/?linkid=841280): voir les fonctionnalités de gestion de portefeuille incluses dans project Server 2016 et Project Online Premium.

- [Guide de migration de Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin de la prise en charge des clients et serveurs Office 2010 et de l’affiche Windows 7](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins que vous pouvez suivre pour éviter la fin de la prise en charge pour les produits client et serveur Office 2010 et Windows 7, avec les chemins d’accès et les options de prise en charge par défaut dans Microsoft 365 entreprise en surbrillance.

Vous pouvez également [Télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format Letter, Legal ou tabloïd (11 x 17).

## <a name="related-topics"></a>Voir aussi

[Mise à jour à jour de SharePoint 2010](upgrade-from-sharepoint-2010.md)

[Mettre à niveau des serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md)
