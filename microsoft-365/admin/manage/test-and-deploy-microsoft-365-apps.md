---
title: Tester et déployer Microsoft 365 Apps
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: ''
ms.custom: AdminSurgePortfolio
search.appverid: MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Recherchez, testez et déployez des applications partenaires Microsoft et Microsoft pour les utilisateurs et les groupes de votre organisation à partir du portail Applications intégrées dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: b0dc6277461ff03e8aae2e820543f8e5d9e2303c
ms.sourcegitcommit: 7d4aa58ae9fc893825b6e648fa3f072c3ac59628
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "49790189"
---
# <a name="test-and-deploy-microsoft-365-apps-in-the-microsoft-365-admin-center"></a>Tester et déployer Microsoft 365 Apps dans le Centre d’administration Microsoft 365

Le Centre d’administration Microsoft 365 vous offre la flexibilité nécessaire pour déployer des applications partenaires Microsoft et Microsoft à partir d’un emplacement unique. La possibilité de rechercher, de tester et de déployer entièrement des applications achetées et sous licence par Microsoft et les partenaires Microsoft à partir du portail des applications intégrées offre la commodité et les avantages dont votre organisation a besoin pour maintenir les services professionnels mis à jour régulièrement et s’exécutant efficacement.  

Pour plus d’informations sur l’achat et la gestion des licences d’applications Microsoft 365 pour votre organisation, consultez le billet de blog intitulé Gérer et déployer les applications Microsoft 365 à partir du Centre d’administration [Microsoft 365.](https://techcommunity.microsoft.com/t5/microsoft-365-blog/manage-and-deploy-microsoft-365-apps-from-the-microsoft-365/ba-p/1194324)
  
## <a name="manage-apps-in-the-integrated-apps-portal"></a>Gérer les applications dans le portail Applications intégrées

En choisissant Applications intégrées dans le Centre d’administration Microsoft 365, vous pouvez gérer les tests et le déploiement des applications partenaires Microsoft et Microsoft achetées et sous licence. 

1. Dans le centre d’administration, dans le navigation gauche, choisissez **Paramètres,** puis choisissez **Applications intégrées.** 

2. Choisissez une application avec **l’état** **d’autres applications disponibles.**

3. **Sélectionnez** Déployer en haut de la page en haut du message qui fait référence à l’attente de déploiement.

    Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner **Déployer.**

    a. Sélectionnez **Ajouter des utilisateurs,** **choisissez Déploiement complet,** puis choisissez Toute **l’organisation** ou **des utilisateurs/groupes spécifiques.**

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué.

    Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation.

    b. Sélectionnez **Mettre à** jour , **Terminé** et vous pouvez maintenant sélectionner **Déployer** sous l’onglet **Vue d’ensemble.**  

4. Examinez les informations de l’application, puis sélectionnez **Déployer.** 

5. Sélectionnez **Terminé** sur la page **Déploiement** terminé. 

    Examinez les détails du test ou du déploiement complet sous **l’onglet Vue d’ensemble.**

## <a name="find-published-apps-for-testing-and-full-deployment"></a>Rechercher des applications publiées pour le test et le déploiement complet 

Vous pouvez rechercher, tester et déployer entièrement des applications publiées qui n’apparaissent pas déjà dans la liste de la page Applications intégrées. En achetant et en accordant des licences aux applications à partir du Centre d’administration, vous pouvez ajouter des applications partenaires Microsoft et Microsoft à votre liste à partir d’un emplacement unique.

1. Dans le centre d’administration, dans le navigation gauche, choisissez **Paramètres,** puis choisissez **Applications intégrées.** 

2. Sélectionnez **Obtenir des applications au-dessus** de la liste des applications.

3. Dans la page **Applications microsoft 365** publiées, sélectionnez l’application que vous souhaitez déployer en choisissant **Obtenir maintenant.**

4. Acceptez les autorisations, puis sélectionnez **Continuer**.

5. **Sélectionnez** Déployer en haut de la page en haut du message qui fait référence à l’attente de déploiement.

    Certaines applications nécessitent que vous ajoutiez des utilisateurs avant de pouvoir sélectionner **Déployer.**

    a. Sélectionnez **Ajouter des utilisateurs,** **choisissez Déploiement complet,** puis choisissez Toute **l’organisation** ou **des utilisateurs/groupes spécifiques.**

    Des utilisateurs/groupes spécifiques peuvent être un groupe Microsoft 365, un groupe de sécurité ou un groupe distribué.

    Vous pouvez également choisir **de tester le déploiement** si vous préférez attendre le déploiement de l’application dans toute l’organisation.

    b. Sélectionnez **Mettre à** **jour,** Terminé et vous pouvez maintenant sélectionner **Déployer** sous l’onglet **Vue d’ensemble.**  

6. Examinez les informations de l’application, puis sélectionnez **Déployer.** 

7. Sélectionnez **Terminé** sur la page **Déploiement** terminé. 

    Examinez les détails du test ou du déploiement complet sous **l’onglet Vue d’ensemble.**

Dans le Centre d’administration Microsoft 365, l’état de chaque application déployée est **correct** avec un **type** de déploiement de déploiement de **test,** un déploiement complet ou **personnalisé,** et la date à laquelle vous avez déployé l’application. 

> [!NOTE]
> Si une application a été précédemment déployée à partir d’un autre portail que le portail Applications intégrées, le **type de** déploiement est **personnalisé.**

## <a name="unsupported-scenarios"></a>Scénarios non pris en place

Les scénarios suivants ne sont actuellement pas pris en charge pour le déploiement à partir du portail Applications intégrées :

- L’application ou le add-in est lié à plusieurs logiciels en tant qu’offre de service (SaaS).
- L’application SaaS est liée à des applications et des applications, mais elle n’a pas d’AADid associée.
- Deux applications SaaS partagent le même AADid et elles sont toutes deux liées à des applications ou des applications.
  