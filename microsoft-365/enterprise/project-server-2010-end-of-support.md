---
title: Project Feuille de route de fin de la prise en charge de Server 2010
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
description: Le support prend fin Project Server 2010 se termine le 13 avril 2021. Utilisez cet article comme guide pour mettre à niveau vers Project Online ou une version plus récente de Project Server local.
ms.openlocfilehash: 0ca37d00ee670a8a3f7c83d75864b5af19587951
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53229754"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge de Project Server 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Project Server 2010 prendra fin le **13 avril 2021.** Cette date a été prolongée à partir de la date de fin de prise en charge précédente du 13 octobre 2020. Si vous utilisez actuellement Project Server 2010, notez que ces produits associés ont les dates de fin de support suivantes :

|Produit |Date de fin du support|
|---|---|
|Project 2010 Standard|13 octobre 2020|
|Project 2010 Professional|13 octobre 2020|

Pour plus d’informations sur la fin de la prise en charge, voir [Upgrade from Office 2010 servers and client products](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

Presque tous les produits Microsoft ont un cycle de vie de support, au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Une fois Project Server 2010 a atteint sa fin de prise en charge le 13 avril 2021, Microsoft ne fournira plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes détectés et qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.

- Correctifs de sécurité pour les vulnérabilités découvertes et qui peuvent rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Project Server 2010 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées précédemment, nous vous recommandons vivement de migrer de Project Server 2010 dès que possible.

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vos options de migration sont les :

- Migrer vers Project Online

- Migrer vers une version plus récente sur site de Project Server (de préférence Project Server 2019)

Voici les deux chemins que vous pouvez prendre pour éviter la fin de la prise en charge de Project Server 2010.

![Project Chemins de mise à niveau de Server 2010](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Pourquoi préférer migrer vers Project Server 2019 ?|Pourquoi préfère-t-il migrer vers Project Online ?|
|---|---|
|Les règles d’entreprise m’empêchent d’exploiter mon entreprise dans le cloud.  <br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.|J’ai des utilisateurs mobiles ou distants.<br/><br/>  Les coûts de migration des serveurs locaux sont un problème important (matériel, logiciel, temps et effort à implémenter, etc.). <br/><br/>  Après la migration, les coûts liés à la maintenance de mon environnement sont un problème (par exemple, les mises à jour automatiques, le temps de fonctionnement garanti, et ainsi de suite).|

> [!NOTE]
> Pour plus d’informations sur vos options de migration, voir Ressources pour vous aider à mettre à niveau Office serveurs et [clients 2010.](upgrade-from-office-2010-servers-and-products.md) Notez que Project Server ne prend pas en charge la configuration hybride, car Project Server et Project Online ne peuvent pas partager la même pool de ressources.

### <a name="what-are-my-options-for-project-client"></a>Quelles sont mes options pour Project client ?

Si vous utilisez Project Professionnel 2010 ou Project Standard 2010, vous avez les options ci-après :

- Passer à une version plus récente de Project Professionnel ou Project Standard
- Passer à une solution en ligne, telle que Project Online ou Project pour le web

#### <a name="move-to-a-newer-version-of-project-client"></a>Passer à une version plus récente du client Project client

Si vous migrez depuis Project Standard 2010, vous pouvez passer à une version plus récente de Project Standard (Project Standard 2016 ou Project Standard 2019). Nous vous recommandons de passer à la dernière version pour tirer parti des dernières fonctionnalités. La migration vers une version moins récente (Project Standard 2016) signifie également que vous devrez migrer à nouveau plus tôt.

De même, si vous migrez à partir de Project Professionnel 2010, vous pouvez passer à une version plus récente (Project Professionnel 2019 ou Project Professionnel 2016). Là encore, déplacez-vous vers la version la plus récente si possible. Si vous utilisez Project Professionnel pour vous connecter à Project Server, veillez à migrer vers une version de Project Professionnel qui se connecte à la version de Project Server que vous utilisez.

Project Professionnel 2010 peuvent également migrer vers le client de bureau Project Online, qui est une version basée sur un abonnement de Project Professionnel 2019. Il est inclus dans les abonnements Project (plan 3) et Project (plan 5) abonnements.

#### <a name="move-to-an-online-solution"></a>Passer à une solution en ligne

Vous pouvez également migrer de Project Professionnel 2010 ou Project Standard 2010 vers une solution Project en ligne basée sur un abonnement. Les Project (plan 3) plan 5 incluent Project Online et la dernière offre cloud, Project [pour le web.](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1) Les deux offrent de nouvelles fonctionnalités et avantages qui peuvent être explorés.

Pour plus d’informations sur les fonctionnalités et les licences, [voir Microsoft Project description du service.](/office365/servicedescriptions/project-online-service-description/project-online-service-description)

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Considérations importantes pour la migration depuis Project Server 2010

Prenons les considérations suivantes lorsque vous prévoyez de migrer Project Server 2010 :

- **Obtenir de l’aide d’un** fournisseur de solutions Microsoft : une mise à niveau à partir Project Server 2010 peut être un défi. Cela nécessite beaucoup de préparation et de planification. Cela peut être particulièrement difficile si vous n’étiez pas la personne qui a initialement Project Server 2010. Les fournisseurs de solutions Microsoft sont disponibles pour vous aider, que vous prévoyiez de migrer vers Project Server 2019 ou vers Project Online. Recherchez un fournisseur de solutions dans le [Centre de fournisseurs de solutions Microsoft.](https://go.microsoft.com/fwlink/p/?linkid=841249)

- **Planifiez** vos personnalisations : les personnalisations dans votre environnement Project Server 2010 peuvent ne pas fonctionner lorsque vous migrez vers Project Server 2019 ou Project Online. Il existe des différences significatives entre Project’architecture de serveur entre les versions. En outre, les systèmes d’exploitation, les serveurs de base de données et les navigateurs web requis qui fonctionnent avec les versions diffèrent. Planifiez la façon de tester ou de reconstruire vos personnalisations dans le nouvel environnement. Profitez de cette opportunité pour déterminer si des personnalisations spécifiques sont toujours nécessaires. Pour plus d'informations, voir [Create a plan for current customizations during upgrade to SharePoint 2013](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Temps et patience** : la planification, l’exécution et les tests de mise à niveau prennent beaucoup de temps et d’efforts, en particulier pour une mise à niveau vers Project Server 2019. Si vous migrez de Project Server 2010 vers Project Server 2019, vous devez d’abord migrer vers Project Server 2013, vérifier vos données, puis migrer vers Project Server 2016, puis vers Project Server 2019. Vous souhaitez peut-être consulter un fournisseur de solutions Microsoft pour obtenir une période et un coût estimé pour l’aider.

## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2010 vers Project Online, vous pouvez suivre les étapes suivantes pour migrer manuellement les données de votre plan de projet :

1. Enregistrez vos plans de projet Project Server 2010 au format .mpp.

2. En utilisant Project Professionnel 2016, Project Professionnel 2019 ou le client de bureau Project Online, ouvrez chaque fichier .mpp, puis enregistrez-le et publiez-le sur Project Online.

Vous pouvez créer manuellement votre configuration de PWA dans Project Online (par exemple, recréer les champs personnalisés ou les calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également vous aider dans ce processus.

Ressources clés :

|Resource|Description|
|---|---|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Comment configurer et utiliser les Project Online|
|[Description du service Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informations sur les différents plans Project Online disponibles|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version plus récente sur site de Project Server

Nous pensons vivement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migrer vers Project Online. Toutefois, nous comprenons également que certaines organisations doivent conserver les données de projet localement. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2010 vers Project Server 2013, Project Server 2016 ou Project Server 2019.

Si vous ne pouvez pas migrer vers Project Online, nous vous recommandons de migrer vers Project Server 2019. Project Server 2019 inclut la plupart des fonctionnalités clés des versions précédentes de Project Server. Et elle correspond le mieux à l’expérience disponible avec Project Online, bien que certaines fonctionnalités soient disponibles uniquement dans Project Online.

Une fois que vous avez terminé chaque migration, assurez-vous que vos données ont été correctement migrées.

> [!NOTE]
> Si vous êtes limité à une solution sur site et envisagez de migrer uniquement vers Project Server 2013, sachez que cette version ne dispose que de quelques années de support. Date de fin du support pour Project Server 2013 avec Service Pack 2 13 octobre 2023. Pour plus d’informations sur les dates de fin de support, voir [Politique de cycle de vie des produits Microsoft.](/lifecycle/)

### <a name="how-do-i-migrate-to-project-server-2019"></a>Comment migrer vers Project Server 2019 ?

Les différences architecturales entre Project Server 2010 et Project Server 2019 empêchent un chemin de migration direct. Vous devrez donc migrer vos données Project Server 2010 vers chaque version successive de Project Server jusqu’à ce que vous Project Server 2019. Étapes de mise à niveau Project Server 2010 vers Project Server 2019 :

1. Migrez vers Project Server 2013.

2. Migrez de Project Serve 2013 vers Project Server 2016.

3. Migrez de Project Server 2016 vers Project Server 2019.

Une fois que vous avez terminé chaque migration, assurez-vous que vos données ont été correctement migrées.

### <a name="step-1-migrate-to-project-server-2013"></a>Étape 1 : Migrer vers Project Server 2013

Pour obtenir des informations complètes sur la mise à niveau de Project Server 2010 vers Project Server 2013, voir [Upgrade to Project Server 2013](/project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/upgrade-to-project-server-2016)

  Obtenez une vue d’ensemble de la mise à niveau de Project Server 2010 vers Project Server 2013.
- [Planifier la mise à niveau vers Project Server 2013](/project/plan-for-upgrade-to-project-server-2016)

  Examiner les considérations relatives à la planification lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la exigences système.

- [Les nouveautés de la mise à Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) couvrent les modifications importantes apportées à cette version, notamment :

  - Il n’existe aucune mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est le seul moyen pris en charge de mettre à niveau Project Server 2010 vers Project Server 2013.

  - Le processus de mise à niveau convertira non seulement vos données Project Server 2010 au format Project Server 2013, mais consolidera également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.

  - Les SharePoint Server 2013 et Project Server 2013 sont passées à l’authentification basée sur les revendications par rapport à la version précédente. Si vous utilisez l’authentification classique, vous devez tenir compte de cela lors de la mise à niveau. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)

- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Microsoft Project Diagramme du processus de mise à niveau du serveur](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [La grande consolidation de bases de données, Project migration de Server 2010 vers 2013 en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>Étape 2 : Migrer vers Project Server 2016

Après avoir migré vers Project Server 2013 et vérifié que vos données ont bien été migrées, l’étape suivante consiste à migrer vers Project Server 2016.

Pour plus d’informations, [voir Mise à niveau vers Project Server 2016](/Project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d'ensemble du processus de mise à niveau vers Project Server 2016](/Project/overview-of-the-project-server-2016-upgrade-process)

  Comprendre ce que vous devez faire pour mettre à niveau Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  Examiner les considérations de planification à prendre en compte lors de la mise à niveau de Project Server 2013 vers Project Server 2016.

[Ce que vous devez savoir sur](/project/plan-for-upgrade-to-project-server-2016#thingknow) Project Server 2016 mise à niveau couvre les modifications importantes pour la mise à niveau vers cette version, notamment :

- Lorsque vous créez votre environnement Project Server 2016, notez que les fichiers Project Server 2016 d’installation sont inclus dans SharePoint Server 2016. Pour plus d’informations, voir [Déployer Project Server 2016](/project/deploy-project-server-2016).

- Les plans de ressources sont supprimés dans Project Server 2016. Vos plans de Project Server 2013 seront migrés vers les engagements de ressources Project Server 2016 et Project Online. Voir [Vue d’ensemble : engagements de](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) ressources pour plus d’informations.

### <a name="step-3-migrate-to-project-server-2019"></a>Étape 3 : Migrer vers Project Server 2019

Après avoir migré vers Project Server 2016 et vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vos données vers Project Server 2019.

Pour savoir ce que vous devez faire pour mettre à niveau Project Server 2016 vers Project Server 2019, voir Mise à niveau vers [Project Server 2019.](/Project/upgrade-to-project-server-2016)

Ressources clés :

- [Vue d’ensemble du Project de mise à niveau vers Server 2019](/project/overview-of-the-project-server-2019-upgrade-process)

  Obtenez une bonne compréhension de ce que vous devez faire pour mettre à niveau Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2019](/project/plan-for-upgrade-to-project-server-2019)

  Examiner les considérations de planification pour la mise à niveau de Project Server 2016 vers Project Server 2019.

- [Ce que vous devez savoir sur la mise Project Server 2019](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>Découvrez les modifications importantes pour la mise à niveau vers cette version, notamment :

  - Le processus de mise à niveau migre vos données de votre base de données Project Server 2016 vers la base de données SharePoint Server 2019 de contenu.  Project Server 2019 ne créera plus sa propre base de données Project server dans la batterie SharePoint Server.

  - Après la mise à niveau, sachez que plusieurs modifications ont été apportées Project Web App.  Pour plus [d’informations, voir Nouveautés de Project Server 2019.](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges)

**Autres ressources**:

- [Project Online descriptions de service](/office365/servicedescriptions/project-online-service-description/project-online-service-description): consultez les fonctionnalités de gestion de portefeuille incluses Project Server 2016 et Project Online Premium.

- [Microsoft Office Project de migration Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client Office 2010 et les serveurs et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![End of support for Office 2010 clients and servers and Windows 7 poster](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins que vous pouvez prendre pour éviter la fin de la prise en charge des produits client et serveur Office 2010 et de Windows 7, avec les chemins d’accès préférés et la prise en charge des options dans Microsoft 365 Entreprise mis en évidence.

Vous pouvez également [télécharger cette](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="related-topics"></a>Voir aussi

[Mise à jour à jour de SharePoint 2010](upgrade-from-sharepoint-2010.md)

[Mettre à niveau des serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md)
