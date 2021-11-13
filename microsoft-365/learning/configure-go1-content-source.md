---
title: Configurer Go1 en tant que source de contenu pour Apprentissage Microsoft Viva
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
description: Découvrez comment configurer Go1 en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ms.openlocfilehash: 1adef6275be2a8656eaad9a7f47805d13299e3c7
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60950532"
---
# <a name="configure-go1-as-a-content-source-for-microsoft-viva-learning"></a>Configurer Go1 en tant que source de contenu pour Apprentissage Microsoft Viva

Cet article vous montre comment configurer Go1 en tant que source de contenu d’apprentissage tierce dans Learning.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu Go1 et les services associés sont soumis aux conditions de confidentialité et de service de Go1.

Go1 permet d’accéder à des milliers de cours à partir de principaux fournisseurs de contenu. [En savoir plus sur Go1](https://www.go1.com/go1-microsoft-viva). Suivez ces étapes pour ajouter Go1 en tant que source d’apprentissage dans Learning.

## <a name="configure-in-your-go1-portal"></a>Configurer dans votre portail Go1

>[!NOTE]
>Vous devez avoir des autorisations d’administrateur dans Go1 pour effectuer ces étapes.

Tout d’abord, vous devez suivre ces étapes pour créer une application dans votre portail Go1. Cette application génère vos clés d’API, que vous pouvez utiliser pour vous authentifier auprès de Go1 et effectuer des demandes à l’API.

1. Connectez-vous à votre portail Go1 en tant qu’administrateur.

2. Sélectionnez **Intégrations dans** les options de menu.

3. Sélectionnez **Développeurs.**
4. Sélectionnez le **bouton Créer une** application.
5. Entrez un nom pour l’application, par exemple« My-go1-titre-integration ».
6. Entrez une URL de retour d’appel, par exemple, « Mycompany.mygo1.com ».
7. Enregistrez les informations que vous avez entrées.
8. Vos informations s’affichent avec la secret masquée. Sélectionnez les ellipses (**...**), puis **sélectionnez Afficher la secret** pour afficher la secret.
9. Copiez les valeurs suivantes :

    - **URL hôte du client :** Il s’agit de l’URL de votre portail Go1. Elle ressemblera à « https://mycompany.mygo1.com ».
    - **ID client :** Vous pouvez trouver votre ID dans votre portail Go1 sous les options du menu **Intégrations/Développeur.**
    - **Secret :** Vous pouvez trouver votre secret dans votre portail Go1 sous les options du menu **Intégrations/Développeur.**

En savoir plus [sur la création d’une application](https://help.go1.com/en/articles/4642648-integrate-with-the-go1-api)de développeur privé pour Go1.

## <a name="configure-in-your-microsoft-365-admin-center"></a>Configurer dans votre Centre d'administration Microsoft 365

>[!NOTE]
>Vous devez avoir des autorisations d’administrateur Microsoft 365 pour effectuer ces étapes.

1. Connectez-vous à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).
2. Accédez **à Paramètres,** puis **aux paramètres org.** Sélectionnez Contrôle Learning, puis activez Go1 dans le panneau.
3. Remplissez les détails de configuration que vous avez récupérés à partir de votre portail Go1.
4. Sélectionnez **Enregistrer** pour activer le contenu Go1 dans Le Learning. L’affichage du contenu dans l’application Learning prend jusqu’à 24 heures.
