---
title: Configurer La fonction OnDemand en tant que source de contenu pour Apprentissage Microsoft Viva
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 10/07/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer La base de connaissances OnDemand en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ROBOTS: NOINDEX
ms.openlocfilehash: 6cc77ec25f7297fa2492b5a22d70e60350b8eccc
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586124"
---
# <a name="configure-cornerstone-ondemand-as-a-content-source-for-microsoft-viva-learning"></a>Configurer La fonction OnDemand en tant que source de contenu pour Apprentissage Microsoft Viva

>[!NOTE]
>Cette fonctionnalité n’est pas prise en charge en prévisualisation.

Cet article vous montre comment configurer La base de connaissances OnDemand en tant que source de contenu d’apprentissage tierce dans Learning. Tout d’abord, vous devez activer Learning et obtenir vos détails à partir de votre portail de base. Ensuite, vous devez terminer la configuration dans votre Centre d'administration Microsoft 365.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu OnDemand et tous les services associés sont soumis aux conditions de confidentialité et de service de Ce dernier.

## <a name="configure-in-your-cornerstone-portal"></a>Configurer dans votre portail de base

1. Connectez-vous à votre portail de base en tant qu’administrateur.
2. Choisissez **Edge**.
3. Go to **Marketplace** and search for Market.
4. Sélectionnez la vignette Learning’Err.
5. Choisissez **installer**.
6. Cochez la case pour confirmer que vous acceptez les conditions générales et choisissez **Installer.**
7. Sélectionnez **Configurer maintenant.**
8. Copiez l’ID client, la secret, le nom du portail et l’URL de base. Ensuite, revenir en arrière et rechercher l’un des deux.
9. Faites glisser le curseur pour activer l’intégration Learning’équipe.

## <a name="configure-in-microsoft-365-admin-center"></a>Configurer dans Centre d'administration Microsoft 365

1. Connectez-vous à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).
2. Accédez **à Paramètres,** puis **aux paramètres org.** Sélectionnez Contrôle Learning, puis activez l’élément OnDemand dans le panneau.
3. Remplissez les détails de configuration que vous avez récupérés à partir de votre portail de base.

    >[!NOTE]
    >Le nom d’affichage est le nom du carrousel sous lequel le contenu d’apprentissage De la structure fondamentale apparaîtra pour votre organisation dans Learning. Si vous n’entrez pas de nom, celui-ci affiche le nom par défaut « C’est-à-dire OnDemand ».

4. Sélectionnez **Enregistrer** pour activer le contenu De la première ligne de la Learning. L’affichage du contenu dans l’application Learning prend jusqu’à 24 heures.

## <a name="data-residency"></a>Résidence de données

Les métadonnées du client sont stockées de manière centralisée dans nos magasins de données et non dans des magasins de données spécifiques à la région.

## <a name="roles-and-permissions"></a>Rôles et autorisations

Actuellement, tous les utilisateurs au sein d’une organisation peuvent découvrir tous les cours spécifiques au client, mais ils pourront uniquement utiliser les cours qu’ils ont accès. La découverte de contenu spécifique à l’utilisateur basée sur les rôles et les autorisations est prévue pour les prochaines sorties.
