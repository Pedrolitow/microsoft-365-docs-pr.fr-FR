---
title: Configurer La fonction OnDemand en tant que source de contenu pour Apprentissage Microsoft Viva
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 10/27/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer La base de connaissances OnDemand en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ms.openlocfilehash: 4a4b49b4dbe2dd0c946438f103ccb668c01645e5
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60950604"
---
# <a name="configure-cornerstone-ondemand-as-a-content-source-for-microsoft-viva-learning"></a>Configurer La fonction OnDemand en tant que source de contenu pour Apprentissage Microsoft Viva

Cet article vous montre comment configurer La base de connaissances OnDemand en tant que source de contenu d’apprentissage tierce dans Learning. Tout d’abord, vous devez activer Learning et obtenir vos détails à partir de votre portail de base. Ensuite, vous devez terminer la configuration dans votre Centre d'administration Microsoft 365.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu OnDemand et tous les services associés sont soumis aux conditions de confidentialité et de service de Ce dernier.

## <a name="configure-in-your-cornerstone-portal"></a>Configurer dans votre portail de base

1. Connectez-vous à votre portail de base en tant qu’administrateur.

    ![Image du portail de l’angle.](../media/learning/csod-1.png)

2. Choisissez **Edge**.

    ![Image du volet Edge.](../media/learning/csod-2.png)

3. Go to **Marketplace** and search for Market.

    ![Image de marketplace.](../media/learning/csod-3.png)

4. Sélectionnez la vignette Learning’Err.

    ![Image du curseur pointant sur la vignette Learning Sur Marketplace.](../media/learning/csod-4.png)

5. Choisissez **installer**.

    ![Image du curseur pointant sur le bouton Installer après la sélection de la vignette Learning.](../media/learning/csod-5.png)

6. Cochez la case pour confirmer que vous acceptez les conditions générales et choisissez **Installer.**

    ![Image de l’écran d’installation avec la case Conditions générales cochée.](../media/learning/csod-6.png)

7. Sélectionnez **Configurer maintenant.**

    ![Image de la fenêtre d’installation avec un bouton qui indique « Configurer maintenant » à droite et « Plus tard sur la gauche ».](../media/learning/csod-7.png)

8. Copiez l’ID client, la secret, le nom du portail et l’URL de base. Ensuite, revenir en arrière et rechercher l’un des deux.

    ![Image de l’écran de configuration où vous pouvez trouver votre ID client, votre secret client, votre nom de portail et votre URL de base.](../media/learning/csod-8.png)

9. Faites glisser le curseur pour activer l’intégration Learning’équipe.

    ![Image de l’Learning’intégration à la position de l’entreprise.](../media/learning/csod-10.png)

## <a name="configure-in-your-microsoft-365-admin-center"></a>Configurer dans votre Centre d'administration Microsoft 365

1. Connectez-vous à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).
2. Accédez **à Paramètres,** puis **aux paramètres org.** Sélectionnez Contrôle Learning, puis activez l’élément OnDemand dans le panneau.
3. Remplissez les détails de configuration que vous avez récupérés à partir de votre portail de base.

    >[!NOTE]
    >Le nom d’affichage est le nom du carrousel sous lequel le contenu d’apprentissage De la structure fondamentale apparaîtra pour votre organisation dans Learning. Si vous n’entrez pas de nom, celui-ci affiche le nom par défaut « C’est-à-dire OnDemand ».

4. Sélectionnez **Enregistrer** pour activer le contenu De la première ligne de la Learning. L’affichage du contenu dans l’application Learning prend jusqu’à 24 heures.

>[!NOTE]
>Actuellement, tous les utilisateurs au sein d’une organisation peuvent découvrir tous les cours spécifiques au client, mais ils pourront uniquement utiliser les cours qu’ils ont accès. La découverte de contenu spécifique à l’utilisateur basée sur les rôles et les autorisations est prévue pour les prochaines sorties.
