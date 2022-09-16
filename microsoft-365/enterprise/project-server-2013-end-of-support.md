---
title: Feuille de route de fin de support de Project Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: Le support prend fin pour Project Server 2013 le 11 avril 2023. Utilisez cet article comme guide pour effectuer une mise à niveau vers Project Online ou une version plus récente de Project Server localement.
ms.openlocfilehash: 5d7a31ebcb43cb157383ab0faf5ecfe5dd7c5940
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736363"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Feuille de route de fin du support pour Project Server 2013

Project Server 2013 prendra fin le **11 avril 2023**. Si vous utilisez actuellement Project Server 2013, notez que l’application de bureau Project 2013 a également les mêmes dates de fin de support.

## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

Presque tous les produits Microsoft ont un cycle de vie de support, au cours duquel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues et mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Une fois Que Project Server 2013 a atteint sa fin de support le 11 avril 2023, Microsoft ne fournira plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes détectés et susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités découvertes et susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Project Server 2013 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées précédemment, nous vous recommandons vivement de migrer à partir de Project Server 2013 dès que possible.

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vos options de migration sont les suivantes :

- Migrer vers Project Online

- Migrer vers une version locale plus récente de Project Server (de préférence Project Server Édition d'abonnement)

|Pourquoi préférerais-je migrer vers Project Server 2019 ?|Pourquoi préférerais-je migrer vers Project Online ?|
|---|---|
|Les règles d’entreprise me empêchent d’exploiter mon activité dans le cloud.  <br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.|J’ai des utilisateurs mobiles ou distants.<br/><br/>  Les coûts liés à la migration de serveurs locaux constituent un problème important (matériel, logiciel, temps et effort d’implémentation, etc.). <br/><br/>  Après la migration, les coûts de maintenance de mon environnement sont un problème (par exemple, les mises à jour automatiques, la durée de fonctionnement garantie, etc.).|

> [!NOTE]
> Project Server ne prend pas en charge la configuration hybride, car Project Server et Project Online ne peuvent pas partager le même pool de ressources.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>Considérations importantes pour la migration à partir de Project Server 2013

Tenez compte des éléments suivants lorsque vous envisagez de migrer à partir de Project Server 2013 :

- **Obtenir de l’aide auprès d’un fournisseur de solutions Microsoft** : une mise à niveau de Project Server 2013 peut être un défi. Il nécessite beaucoup de préparation et de planification. Cela peut être particulièrement difficile si vous n’êtes pas la personne qui a configuré Project Server 2013 à l’origine. Les fournisseurs de solutions Microsoft sont disponibles pour vous aider, que vous envisagez de migrer vers Project Server Édition d'abonnement ou vers Project Online. Recherchez un fournisseur de solutions dans le [centre de fournisseurs de solutions Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **Temps et patience** : la planification, l’exécution et les tests de mise à niveau prendront beaucoup de temps et d’efforts, en particulier pour une mise à niveau vers Project Server Édition d'abonnement. Si vous migrez de Project Server 2013 vers Project Server Édition d'abonnement, vous devez d’abord migrer vers Project Server 2016, vérifier vos données, puis Project Server Édition d'abonnement. Vous souhaiterez peut-être vérifier auprès d’un fournisseur de solutions Microsoft pour une période de temps et le coût estimé pour qu’il les aide.

## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2013 vers Project Online, vous pouvez suivre ces étapes pour migrer manuellement les données de votre plan de projet :

1. Enregistrez vos plans de projet de Project Server 2013 au format .mpp.

2. À l’aide de Project Professionnel 2016, Project Professionnel 2019 ou du client de bureau Project Online, ouvrez chaque fichier .mpp, puis enregistrez-le et publiez-le dans Project Online.

Vous pouvez créer manuellement votre configuration PWA dans Project Online (par exemple, recréer les champs personnalisés ou les calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également vous aider dans ce processus.

Ressources clés :

|Ressource|Description|
|---|---|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Comment configurer et utiliser Project Online|
|[Description du service Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informations sur les différents plans Project Online disponibles|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version locale plus récente de Project Server

Nous croyons fermement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migrant vers Project Online. Mais nous comprenons également que certaines organisations doivent conserver les données de projet localement. Si vous choisissez de conserver vos données de projet localement, vous pouvez migrer votre environnement Project Server 2013 vers Project Server 2016, Project Server 2019 ou Project Server Édition d'abonnement.

Si vous ne pouvez pas migrer vers Project Online, nous vous recommandons de migrer vers Project Server Édition d'abonnement qui inclut la plupart des fonctionnalités clés dans les versions précédentes de Project Server. Et il correspond le plus à l’expérience disponible avec Project Online, bien que certaines fonctionnalités soient disponibles uniquement dans Project Online. Les facteurs supplémentaires à prendre en compte sont les suivants :

- Project Server Édition d'abonnement introduit un modèle de mise à jour continue qui élimine la nécessité de publier de nouvelles versions majeures de Project Server à l’avenir.
- Les Project Server 2016 et 2019 prendront fin le 14 juillet 2026. Si vous effectuez une migration vers l’une ou l’autre version, vous devez planifier une autre mise à niveau dans les trois ans. Pour plus d’informations, consultez les pages de cycle de vie du support pour [2016](/lifecycle/products/project-server-2016) et [2019](/lifecycle/products/project-server-2019).

Une fois chaque migration terminée, assurez-vous que vos données ont bien migré.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>如何实现 migrer vers Project Server Édition d'abonnement ?

Les différences architecturales entre Project Server 2013 et Project Server Édition d'abonnement empêchent un chemin de migration direct. Vous devez donc migrer vos données Project Server 2013 d’abord vers Project Server 2016, puis vers Project Server Édition d'abonnement. 

1. Migrer vers Project Server 2016.

2. Migrer de Project Server 2016 vers Project Server Édition d'abonnement.

Une fois chaque migration terminée, assurez-vous que vos données ont bien migré.

### <a name="step-1-migrate-to-project-server-2016"></a>Étape 1 : Migrer vers Project Server 2016

Pour obtenir des informations complètes sur la mise à niveau de Project Server 2013 vers Project Server 2016, consultez [Mettre à niveau vers Project Server 2016](/project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau Project Server 2016](/project/upgrade-to-project-server-2016) : obtenez une vue d’ensemble générale de la mise à niveau de Project Server 2013 vers Project Server 2016.
- [Plan to upgrade to Project Server 2016](/project/plan-for-upgrade-to-project-server-2016): Look at planning considerations when upgrade from Project Server 2013 to Project Server 2016, including system requirements.
- [Mise à niveau vers Project Server 2016](/project/upgrading-to-project-server-2016) : consultez les instructions détaillées sur le processus de mise à niveau.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>Étape 2 : Migrer vers Project Server Édition d'abonnement

Une fois que vous êtes passé à Project Server 2016 et que vous avez vérifié que vos données ont bien migré, l’étape suivante consiste à migrer vers Project Server Édition d'abonnement.

Pour plus d’informations, consultez [Mettre à niveau vers Project Server Édition d'abonnement](/project/upgrade-project-server-subscription-edition).

Ressources clés :

- [Vue d’ensemble du processus de mise à niveau Project Server Édition d'abonnement](/project/overview-project-server-subscription-edition-upgrade-process) : découvrez ce que vous devez faire pour effectuer une mise à niveau de Project Server 2013 vers Project Server 2016.
- [Planifier la mise à niveau vers Project Server Édition d'abonnement](/Project/plan-upgrade-project-server-subscription-edition) : examinez les considérations de planification à prendre lors de la mise à niveau de Project Server 2013 vers Project Server 2016.
- [Mise à niveau vers Project Server Édition d'abonnement](/project/how-to-upgrade-project-server-subscription-edition) : consultez les instructions détaillées sur le processus de mise à niveau.


