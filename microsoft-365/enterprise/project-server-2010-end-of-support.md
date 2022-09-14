---
title: Feuille de route de fin de support de Project Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: La prise en charge de Project Server 2010 se termine le 13 avril 2021. Utilisez cet article comme guide pour effectuer une mise à niveau vers Project Online ou une version plus récente de Project Server localement.
ms.openlocfilehash: ccf65987547304df5527cca862dbd0467d2f52a4
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670772"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge de Project Server 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Project Server 2010 prendra fin le **13 avril 2021**. Cette date a été prolongée par rapport à la date de fin de prise en charge précédente du 13 octobre 2020. Si vous utilisez actuellement Project Server 2010, notez que ces produits associés ont les dates de fin de support suivantes :

|Produit |Date de fin du support|
|---|---|
|Project 2010 Standard|13 octobre 2020|
|Project 2010 Professionnel|13 octobre 2020|

Pour plus d’informations sur la fin du support, consultez [Mise à niveau à partir des serveurs et produits clients Office 2010](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

Presque tous les produits Microsoft ont un cycle de vie de support, au cours duquel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues et mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Une fois Que Project Server 2010 a atteint sa fin de support le 13 avril 2021, Microsoft ne fournira plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes détectés et susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Project Server 2010 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées précédemment, nous vous recommandons vivement de migrer à partir de Project Server 2010 dès que possible.

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vos options de migration sont les suivantes :

- Migrer vers Project Online

- Migrer vers une version locale plus récente de Project Server (de préférence Project Server 2019)

Voici les deux chemins que vous pouvez suivre pour éviter la fin de la prise en charge de Project Server 2010.

![Chemins de mise à niveau de Project Server 2010.](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|Pourquoi préférerais-je migrer vers Project Server 2019 ?|Pourquoi préférerais-je migrer vers Project Online ?|
|---|---|
|Les règles d’entreprise me empêchent d’exploiter mon activité dans le cloud.  <br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.|J’ai des utilisateurs mobiles ou distants.<br/><br/>  Les coûts liés à la migration de serveurs locaux constituent un problème important (matériel, logiciel, temps et effort d’implémentation, etc.). <br/><br/>  Après la migration, les coûts de maintenance de mon environnement sont un problème (par exemple, les mises à jour automatiques, la durée de fonctionnement garantie, etc.).|

> [!NOTE]
> Pour plus d’informations sur vos options de migration, consultez [Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et de clients Office 2010](upgrade-from-office-2010-servers-and-products.md). Notez que Project Server ne prend pas en charge la configuration hybride, car Project Server et Project Online ne peuvent pas partager le même pool de ressources.

### <a name="what-are-my-options-for-project-client"></a>Quelles sont mes options pour le client Project ?

Si vous utilisez Project Professionnel 2010 ou Project Standard 2010, vos options sont les suivantes :

- Passer à une version plus récente de Project Professionnel ou Project Standard
- Passer à une solution en ligne, telle que Project Online ou Project pour le web

#### <a name="move-to-a-newer-version-of-project-client"></a>Passer à une version plus récente du client Project

Si vous effectuez une migration à partir de Project Standard 2010, vous pouvez passer à une version plus récente de Project Standard (Project Standard 2016 ou Project Standard 2019). Nous vous recommandons de passer à la version la plus récente pour tirer parti des dernières fonctionnalités. La migration vers une version moins récente (Project Standard 2016) signifie également que vous devrez effectuer une nouvelle migration plus tôt.

De même, si vous effectuez une migration à partir de Project Professionnel 2010, vous pouvez passer à une version plus récente (Project Professionnel 2019 ou Project Professionnel 2016). Là encore, passez à la version la plus récente si possible. Si vous utilisez Project Professionnel pour vous connecter à Project Server, veillez à migrer vers une version de Project Professionnel qui se connecte à la version de Project Server que vous utilisez.

Project Professionnel 2010, les utilisateurs peuvent également migrer vers le client bureau Project Online, qui est une version basée sur un abonnement de Project Professionnel 2019. Il est inclus dans les abonnements Project (plan 3) et Project (plan 5).

#### <a name="move-to-an-online-solution"></a>Passer à une solution en ligne

Vous pouvez également migrer de Project Professionnel 2010 ou Project Standard 2010 vers une solution en ligne basée sur un abonnement Project. Project (plan 3) et Plan 5 incluent Project Online et la dernière offre cloud, [Project pour le web](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). Les deux offrent de nouvelles fonctionnalités et des avantages qui méritent d’être explorés.

Pour plus d’informations sur les fonctionnalités et les licences, consultez [la description du service Microsoft Project](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>Considérations importantes pour la migration à partir de Project Server 2010

Tenez compte des éléments suivants lorsque vous envisagez de migrer à partir de Project Server 2010 :

- **Obtenir de l’aide auprès d’un fournisseur de solutions Microsoft** - Une mise à niveau de Project Server 2010 peut être un défi. Il nécessite beaucoup de préparation et de planification. Cela peut être particulièrement difficile si vous n’êtes pas la personne qui a configuré Project Server 2010 à l’origine. Les fournisseurs de solutions Microsoft sont disponibles pour vous aider, que vous envisagez de migrer vers Project Server 2019 ou vers Project Online. Recherchez un fournisseur de solutions dans le [centre de fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Planifier vos personnalisations** : les personnalisations dans votre environnement Project Server 2010 peuvent ne pas fonctionner lorsque vous migrez vers Project Server 2019 ou Project Online. Il existe des différences significatives dans l’architecture de Project Server entre les versions. En outre, les systèmes d’exploitation, serveurs de base de données et navigateurs web requis qui fonctionnent avec les versions diffèrent. Ayez un plan pour tester ou reconstruire vos personnalisations dans le nouvel environnement. Profitez de cette occasion pour déterminer si des personnalisations spécifiques sont toujours nécessaires. Pour plus d'informations, voir [Create a plan for current customizations during upgrade to SharePoint 2013](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **Temps et patience** : la planification, l’exécution et les tests de mise à niveau prendront beaucoup de temps et d’efforts, en particulier pour une mise à niveau vers Project Server 2019. Si vous effectuez une migration de Project Server 2010 vers Project Server 2019, vous devez d’abord migrer vers Project Server 2013, vérifier vos données, puis migrer vers Project Server 2016, puis vers Project Server 2019. Vous souhaiterez peut-être vérifier auprès d’un fournisseur de solutions Microsoft pour une période de temps et le coût estimé pour qu’il les aide.

## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2010 vers Project Online, vous pouvez suivre ces étapes pour migrer manuellement les données de votre plan de projet :

1. Enregistrez vos plans de projet de Project Server 2010 au format .mpp.

2. À l’aide de Project Professionnel 2016, Project Professionnel 2019 ou du client de bureau Project Online, ouvrez chaque fichier .mpp, puis enregistrez-le et publiez-le dans Project Online.

Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréer les champs personnalisés ou les calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également vous aider dans ce processus.

Ressources clés :

|Ressource|Description|
|---|---|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Comment configurer et utiliser Project Online|
|[Description du service Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informations sur les différents plans Project Online disponibles|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Nous croyons fermement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migrant vers Project Online. Mais nous comprenons également que certaines organisations doivent conserver les données de projet localement. Si vous choisissez de conserver vos données de projet localement, vous pouvez migrer votre environnement Project Server 2010 vers Project Server 2013, Project Server 2016 ou Project Server 2019.

Si vous ne pouvez pas migrer vers Project Online, nous vous recommandons de migrer vers Project Server 2019. Project Server 2019 inclut la plupart des fonctionnalités clés des versions précédentes de Project Server. Et il correspond le plus à l’expérience disponible avec Project Online, bien que certaines fonctionnalités soient disponibles uniquement dans Project Online.

Une fois chaque migration terminée, assurez-vous que vos données ont bien migré.

> [!NOTE]
> Si vous êtes limité à une solution locale et que vous envisagez de migrer uniquement vers Project Server 2013, gardez à l’esprit que cette version ne dispose que de quelques années de support supplémentaires. Date de fin du support pour Project Server 2013 avec Service Pack 2 13 octobre 2023. Pour plus d’informations sur les dates de fin de support, consultez la politique de [cycle de vie des produits Microsoft](/lifecycle/).

### <a name="how-do-i-migrate-to-project-server-2019"></a>Comment faire migrer vers Project Server 2019 ?

Les différences architecturales entre Project Server 2010 et Project Server 2019 empêchent un chemin de migration direct. Vous devez donc migrer vos données Project Server 2010 vers chaque version successive de Project Server jusqu’à ce que vous atteigniez Project Server 2019. Étapes de mise à niveau de Project Server 2010 vers Project Server 2019 :

1. Migrer vers Project Server 2013.

2. Migrer de Project Serve 2013 vers Project Server 2016.

3. Migrer de Project Server 2016 vers Project Server 2019.

Une fois chaque migration terminée, assurez-vous que vos données ont bien migré.

### <a name="step-1-migrate-to-project-server-2013"></a>Étape 1 : Migrer vers Project Server 2013

Pour obtenir des informations complètes sur la mise à niveau de Project Server 2010 vers Project Server 2013, consultez [Mise à niveau vers Project Server 2013](/project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/upgrade-to-project-server-2016)

  Obtenez une vue d’ensemble générale de la mise à niveau de Project Server 2010 vers Project Server 2013.
- [Planifier la mise à niveau vers Project Server 2013](/project/plan-for-upgrade-to-project-server-2016)

  Examinez les considérations relatives à la planification lors de la mise à niveau de Project Server 2010 vers Project Server 2013, y compris la configuration système requise.

- [Les nouveautés de la mise à niveau de Project Server 2013 couvrent](/project/what-s-new-in-project-server-2013-upgrade) les modifications importantes apportées à cette version, notamment :

  - Il n’existe aucune mise à niveau sur place vers Project Server 2013. La méthode d’attachement de base de données est la seule méthode prise en charge pour effectuer une mise à niveau de Project Server 2010 vers Project Server 2013.

  - Le processus de mise à niveau convertit non seulement vos données Project Server 2010 au format Project Server 2013, mais consolide également les quatre bases de données Project Server 2010 en une seule base de données Project Web App.

  - SharePoint Server 2013 et Project Server 2013 sont tous deux passés à l’authentification basée sur les revendications de la version précédente. Si vous utilisez l’authentification classique, vous devez prendre cela en compte lors de la mise à niveau. Pour plus d'informations, voir [Migrer de l'authentification en mode classique vers l'authentification basée sur les revendications dans SharePoint 2013](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau vers Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)

- [Mettre à niveau vos bases de données et collections de sites Project Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Diagramme du processus de mise à niveau de Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [La grande consolidation de base de données, Project Server 2010 à 2013 Migration en 8 étapes simples](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>Étape 2 : Migrer vers Project Server 2016

Après avoir migré vers Project Server 2013 et vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vers Project Server 2016.

Pour plus d’informations, consultez [Mettre à niveau vers Project Server 2016](/Project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d'ensemble du processus de mise à niveau vers Project Server 2016](/Project/overview-of-the-project-server-2016-upgrade-process)

  Découvrez ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  Examinez les considérations de planification à prendre en compte lors de la mise à niveau de Project Server 2013 vers Project Server 2016.

[Les informations que vous devez savoir sur Project Server 2016 mise à niveau](/project/plan-for-upgrade-to-project-server-2016#thingknow) couvrent les modifications importantes apportées à la mise à niveau vers cette version, notamment :

- Lorsque vous créez votre environnement Project Server 2016, notez que les fichiers d’installation Project Server 2016 sont inclus dans SharePoint Server 2016. Pour plus d’informations, consultez [Déployer Project Server 2016](/project/deploy-project-server-2016).

- Les plans de ressources sont dépréciés dans Project Server 2016. Vos plans de ressources Project Server 2013 seront migrés vers Resource Engagements dans Project Server 2016 et dans Project Online. Pour plus [d’informations, consultez Vue d’ensemble : Engagements de ressources](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) .

### <a name="step-3-migrate-to-project-server-2019"></a>Étape 3 : Migrer vers Project Server 2019

Après avoir migré vers Project Server 2016 et vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vos données vers Project Server 2019.

Pour savoir ce que vous devez faire pour effectuer une mise à niveau de Project Server 2016 vers Project Server 2019, consultez [Mise à niveau vers Project Server 2019](/Project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau de Project Server 2019](/project/overview-of-the-project-server-2019-upgrade-process)

  Découvrez ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.

- [Planifier la mise à niveau vers Project Server 2019](/project/plan-for-upgrade-to-project-server-2019)

  Examinez les considérations relatives à la planification de la mise à niveau de Project Server 2016 vers Project Server 2019.

- [Informations à savoir sur la mise à niveau de Project Server 2019](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>Découvrez les modifications importantes apportées à la mise à niveau vers cette version, notamment :

  - Le processus de mise à niveau migre vos données de votre base de données Project Server 2016 vers la base de données de contenu SharePoint Server 2019.  Project Server 2019 ne crée plus sa propre base de données Project Server dans la batterie de serveurs SharePoint Server.

  - Après la mise à niveau, tenez compte de plusieurs modifications apportées à Project Web App.  Pour plus [d’informations, consultez Les nouveautés de Project Server 2019](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**Autres ressources** :

- [Project Online Descriptions du service](/office365/servicedescriptions/project-online-service-description/project-online-service-description) : consultez les fonctionnalités de gestion de portefeuille incluses dans Project Server 2016 et Project Online Premium.

- [Guide de migration de Microsoft Office Project Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Récapitulatif des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin du support pour les clients et serveurs Office 2010 et l’affiche Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche illustre les différents chemins d’accès que vous pouvez suivre pour éviter la fin de la prise en charge des produits clients et serveurs Office 2010 et windows 7, avec les chemins d’accès et la prise en charge des options préférés dans Microsoft 365 Entreprise mis en évidence.

Vous pouvez également [télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="related-topics"></a>Voir aussi

[Mise à jour à jour de SharePoint 2010](upgrade-from-sharepoint-2010.md)

[Mettre à niveau des serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md)
