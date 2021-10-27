---
title: Configurer Go1 en tant que source de contenu pour Apprentissage Microsoft Viva
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
description: Découvrez comment configurer Go1 en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ROBOTS: NOINDEX
ms.openlocfilehash: ade44c0cc7607ab1b7a247ee60bdd2ca3505e6e9
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60586160"
---
# <a name="configure-go1-as-a-content-source-for-microsoft-viva-learning"></a>Configurer Go1 en tant que source de contenu pour Apprentissage Microsoft Viva

>[!NOTE]
>Cette fonctionnalité n’est pas prise en charge en prévisualisation.

Cet article vous montre comment configurer Go1 en tant que source de contenu d’apprentissage tierce dans Learning.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu Go1 et les services associés sont soumis aux conditions de confidentialité et de service de Go1.

Go1 permet d’accéder à des milliers de cours à partir de principaux fournisseurs de contenu. [En savoir plus sur Go1](https://www.go1.com/go1-microsoft-viva). Suivez ces étapes pour ajouter Go1 en tant que source d’apprentissage dans Learning.

## <a name="create-a-developers-app-in-go1"></a>Créer une application de développeur dans Go1

Tout d’abord, vous devez suivre ces étapes pour créer une application dans votre portail Go1. Cette application génère vos clés d’API, que vous pouvez utiliser pour vous authentifier auprès de Go1 et effectuer des demandes à l’API.

1. Connectez-vous à votre portail Go1 en tant qu’administrateur.

2. Sélectionnez **Intégrations dans** les options de menu.

3. Sélectionnez **Développeurs.**

    <!--![Image of the Developers option in the Integrations menu.](../media/learning/go1-1.png)-->

4. Sélectionnez le **bouton Créer une** application.

    <!--![Image of the Create App button.](../media/learning/go1-2.png)-->

5. Entrez un nom pour l’application, par exemple« My-go1-titre-integration ».

6. Entrez une URL de retour d’appel, par exemple, « Mycompany.mygo1.com ».

    <!--![Image of the field where you enter the name and callback URL.](../media/learning/go1-3.png)-->

7. Enregistrez les informations que vous avez entrées.

8. Vos informations s’affichent avec le secret masqué. Sélectionnez les ellipses (**...**), puis **sélectionnez Afficher la secret** pour afficher la secret.

9. Copiez les valeurs suivantes :

    - **URL hôte du client :** Il s’agit de l’URL de votre portail Go1. Elle ressemblera à « https://mycompany.mygo1.com ».
    - **ID client :** Vous pouvez trouver votre ID dans votre portail Go1 sous les options du menu **Intégrations/Développeur.**
    - **Secret :** Vous pouvez trouver votre secret dans votre portail Go1 sous les options du menu **Intégrations/Développeur.**

## <a name="complete-configuration-in-the-microsoft-365-admin-center"></a>Configuration complète dans le Centre d'administration Microsoft 365

Copiez et collez les valeurs que vous avez récupérées à partir de votre portail Go1 dans l’écran d’installation de Go1 dans la Centre d'administration Microsoft 365.

En savoir plus [sur la création d’une application](https://help.go1.com/en/articles/4642648-integrate-with-the-go1-api)de développeur privé pour Go1.
