---
title: Project Feuille de route de fin de la prise en charge de Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: Le support prend fin Project Server 2013 le 11 avril 2023. Utilisez cet article comme guide pour mettre à niveau vers Project Online ou une version plus récente de Project Server local.
ms.openlocfilehash: 5a9ae38e819dfdb8f9cc2ca3719dccea2d33fa3e
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60889856"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Project Feuille de route de fin de l’assistance pour Server 2013

Project Server 2013 prendra fin le **11 avril 2023.** Si vous utilisez actuellement Project Server 2013, notez que Project application de bureau 2013 a également les mêmes dates de fin de prise en charge.

## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

Presque tous les produits Microsoft ont un cycle de vie de support, au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues et des mises à jour de sécurité. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Une fois Project Server 2013 a atteint sa fin de prise en charge le 11 avril 2023, Microsoft ne fournira plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes détectés et qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.

- Correctifs de sécurité pour les vulnérabilités découvertes et qui peuvent rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Project Server 2013 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées précédemment, nous vous recommandons vivement de migrer de Project Server 2013 dès que possible.

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vos options de migration sont les :

- Migrer vers Project Online

- Migrer vers une version plus récente sur site de Project Server (de préférence Project Server Subscription Edition)

|Pourquoi préférer migrer vers Project Server 2019 ?|Pourquoi préfère-t-il migrer vers Project Online ?|
|---|---|
|Les règles d’entreprise m’empêchent d’exploiter mon entreprise dans le cloud.  <br/><br/>  J’ai besoin de contrôler les mises à jour de mon environnement.|J’ai des utilisateurs mobiles ou distants.<br/><br/>  Les coûts de migration des serveurs locaux sont un problème important (matériel, logiciel, temps et effort à implémenter, etc.). <br/><br/>  Après la migration, les coûts liés à la maintenance de mon environnement sont un problème (par exemple, les mises à jour automatiques, le temps de fonctionnement garanti, et ainsi de suite).|

> [!NOTE]
> Project Le serveur ne prend pas en charge la configuration hybride, Project Server et Project Online ne peuvent pas partager la même pool de ressources.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>Considérations importantes pour la migration depuis Project Server 2013

Prenons les considérations suivantes lorsque vous prévoyez de migrer Project Server 2013 :

- **Obtenir de l’aide d’un** fournisseur de solutions Microsoft : une mise à niveau à partir Project Server 2013 peut être un défi. Cela nécessite beaucoup de préparation et de planification. Cela peut être particulièrement difficile si vous n’étiez pas la personne qui a initialement Project Server 2013. Les fournisseurs de solutions Microsoft sont disponibles pour vous aider, que vous prévoyiez de migrer vers Project Server Subscription Edition ou vers Project Online. Recherchez un fournisseur de solutions dans le [Centre de fournisseurs de solutions Microsoft.](https://go.microsoft.com/fwlink/p/?linkid=841249)

- **Temps et patience** : la planification, l’exécution et les tests de mise à niveau prennent beaucoup de temps et d’efforts, en particulier pour une mise à niveau vers Project Server Subscription Edition. Si vous migrez de Project Server 2013 vers Project Server Subscription Edition, vous devez d’abord migrer vers Project Server 2016, vérifier vos données, puis Project Server Subscription Edition. Vous souhaitez peut-être consulter un fournisseur de solutions Microsoft pour obtenir une période et un coût estimé pour l’aider.

## <a name="migrate-to-project-online"></a>Migrer vers Project Online

Si vous choisissez de migrer de Project Server 2013 vers Project Online, vous pouvez suivre ces étapes pour migrer manuellement les données de votre plan de projet :

1. Enregistrez vos plans de Project Server 2013 au format .mpp.

2. En utilisant Project Professionnel 2016, Project Professionnel 2019 ou le client de bureau Project Online, ouvrez chaque fichier .mpp, puis enregistrez-le et publiez-le sur Project Online.

Vous pouvez créer manuellement votre configuration de PWA dans Project Online (par exemple, recréer les champs personnalisés ou les calendriers d’entreprise nécessaires). Les fournisseurs de solutions Microsoft peuvent également vous aider dans ce processus.

Ressources clés :

|Resource|Description|
|---|---|
|[Prenez en main Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|Comment configurer et utiliser les Project Online|
|[Description du service Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|Informations sur les différents plans Project Online disponibles|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>Migrer vers une version plus récente sur site de Project Server

Nous pensons vivement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migrer vers Project Online. Toutefois, nous comprenons également que certaines organisations doivent conserver les données de projet localement. Si vous choisissez de conserver vos données de projet en local, vous pouvez migrer votre environnement Project Server 2013 vers Project Server 2016, Project Server 2019 ou Project Server Subscription Edition.

Si vous ne pouvez pas migrer vers Project Online, nous vous recommandons de migrer vers Project Server Subscription Edition qui inclut la plupart des fonctionnalités clés des versions précédentes de Project Server. Et elle correspond le mieux à l’expérience disponible avec Project Online, bien que certaines fonctionnalités soient disponibles uniquement dans Project Online. Les facteurs supplémentaires à prendre en compte sont les suivants :

- Project Server Subscription Edition introduit un modèle de mise à jour continue qui élimine la nécessité de publier de nouvelles versions principales de Project Server à l’avenir.
- Les Project Server 2016 et 2019 arriveront à la fin du support le 14 juillet 2026. Si vous migrez vers l’une ou l’autre version, vous devrez planifier une autre mise à niveau dans un délai de trois ans. Pour plus d’informations, consultez les pages de cycle de vie du support [pour 2016](/lifecycle/products/project-server-2016) et [2019.](/lifecycle/products/project-server-2019)

Une fois que vous avez terminé chaque migration, assurez-vous que vos données ont été correctement migrées.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>Comment migrer vers Project Server Subscription Edition ?

Les différences architecturales entre Project Server 2013 et Project Server Subscription Edition empêchent un chemin de migration direct. Vous devez donc d’abord migrer vos données Project Server 2013 vers Project Server 2016, puis vers Project Server Subscription Edition. 

1. Migrez vers Project Server 2016.

2. Migrez de Project Server 2016 vers Project Server Subscription Edition.

Une fois que vous avez terminé chaque migration, assurez-vous que vos données ont été correctement migrées.

### <a name="step-1-migrate-to-project-server-2016"></a>Étape 1 : Migrer vers Project Server 2016

Pour obtenir des informations complètes sur la mise à niveau de Project Server 2013 vers Project Server 2016, voir [Upgrade to Project Server 2016](/project/upgrade-to-project-server-2016).

Ressources clés :

- [Vue d’ensemble Project Server 2016](/project/upgrade-to-project-server-2016)processus de mise à niveau : obtenez une vue d’ensemble de la mise à niveau de Project Server 2013 vers Project Server 2016.
- [Planifier la mise à](/project/plan-for-upgrade-to-project-server-2016)niveau vers Project Server 2016 : examiner les considérations relatives à la planification lors de la mise à niveau de Project Server 2013 vers Project Server 2016, y compris la Project Server 2016 système requise.
- [Mise à niveau vers Project Server 2016](/project/upgrading-to-project-server-2016): consultez les instructions détaillées sur le processus de mise à niveau.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>Étape 2 : Migrer vers Project Server Subscription Edition

Après avoir migré vers Project Server 2016 et vérifié que vos données ont bien été migrées, l’étape suivante consiste à migrer vers Project Server Subscription Edition.

Pour plus d’informations, [voir Upgrade to Project Server Subscription Edition](/project/upgrade-project-server-subscription-edition).

Ressources clés :

- [Vue d’ensemble du processus de mise](/project/overview-project-server-subscription-edition-upgrade-process)à niveau Project Server Subscription Edition : comprendre ce que vous devez faire pour passer de Project Server 2013 à Project Server 2016.
- [Planifier la](/Project/plan-upgrade-project-server-subscription-edition)mise à niveau vers Project Server Subscription Edition : examiner les considérations de planification à prendre en compte lors de la mise à niveau de Project Server 2013 vers Project Server 2016.
- [Mise à niveau vers Project Server Subscription Edition](/project/how-to-upgrade-project-server-subscription-edition): consultez les instructions détaillées sur le processus de mise à niveau.


