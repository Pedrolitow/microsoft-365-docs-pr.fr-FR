---
title: Ajouter d’autres fournisseurs de contenu pour Apprentissage Microsoft Viva
ms.author: chucked
author: chuckedmonson
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
description: Découvrez comment configurer d’autres fournisseurs de contenu en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ms.openlocfilehash: 4f1a8810f6b8615baa7e8b3fcd8d945ca08cf1d5
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60668263"
---
# <a name="add-other-content-providers-for-microsoft-viva-learning"></a>Ajouter d’autres fournisseurs de contenu pour Apprentissage Microsoft Viva

Un nombre croissant de fournisseurs de contenu d’apprentissage sont disponibles par le biais de Learning. Cet ensemble peut changer à tout moment à mesure que de plus en plus de fournisseurs rejoignent ou modifient leur statut avec le programme.

Certaines sources d’apprentissage seront activées par défaut et seront disponibles sans licence Premium Learning licence. Ces sources d’apprentissage sont les suivantes :

- LinkedIn Learning sélectionner 125 cours
- Microsoft Learn
- Microsoft 365 Formation

Les sources de contenu tierces ne sont pas activées par défaut. Pour activer ces sources, vous devez les ajouter dans le [Centre d'administration Microsoft 365](content-sources-365-admin-center.md#configure-settings-for-the-learning-content-sources) et suivre les instructions spécifiques indiquées dans le tableau suivant.

>[!NOTE]
>Vous aurez besoin d’une licence Premium pour connecter des sources de contenu externes, à l’exception de la sélection de LinkedIn Learning cours gratuits. [En savoir plus sur la gestion des licences.](https://www.microsoft.com/microsoft-viva/learning)

>[!NOTE]
>Il faut entre 24 et 48 heures pour que les utilisateurs de Learning voient le contenu des sources que vous avez activées dans le portail d’administration. Il faut également 24 à 48 heures pour masquer le contenu des formations LinkedIn Learning, Microsoft Learn et Microsoft 365 à Partir de Contrôles Learning une fois que vous les avez désactivés dans le portail d’administration.

|Fournisseur de contenu  |Instructions de configuration  |
|---------|---------|
|Go1     |[Configurer Go1 en tant que source de contenu](configure-go1-content-source.md)         |
|Skillsoft     |[Configurer Skillsoft en tant que source de contenu](configure-skillsoft-content-source.md)         |
|Udemy   |[Configurer Udemy en tant que source de contenu](configure-udemy-content-source.md)         |
|edX    |Suivez les étapes ci-dessous pour ajouter edX à votre Centre d'administration Microsoft 365.    |
|Coursera    |Suivez les étapes ci-dessous pour ajouter Coursera à votre Centre d'administration Microsoft 365.    |
|Pluralsight    |Suivez les étapes ci-dessous pour ajouter Pluralsight dans votre Centre d'administration Microsoft 365.    |
|Infosec    |Suivez les étapes ci-dessous pour ajouter Infosec à votre Centre d'administration Microsoft 365.    |
|În Bersin Academy    |Suivez les étapes ci-dessous pour ajouter La academy Dersin à votre Centre d'administration Microsoft 365.    |

1. Connectez-vous à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).
2. Accédez **à Paramètres,** puis **aux paramètres org.** Sélectionnez Contrôle Learning et activez le fournisseur de contenu ou le système de gestion de l’apprentissage que vous avez choisi dans le panneau.
3. Remplissez vos détails.
4. Sélectionnez **Enregistrer**.

>[!NOTE]
>Les fournisseurs de contenu disponibles peuvent faire l’objet de changements. Selon votre organisation, vous pouvez avoir accès à plus de fournisseurs de contenu que ceux répertoriés ici.

## <a name="content-ingestion-errors"></a>Erreurs d’ingestion de contenu

Si vous avez des erreurs dans votre Centre d'administration Microsoft 365 lors de l’ingestion de contenu, reportez-vous au tableau ci-dessous pour connaître les étapes suivantes. Notez qu’il s’agit d’une liste exhaustive qui peut contenir d’autres codes d’erreur à l’avenir.

|Fournisseur de contenu |Code d’erreur |Description du code d’erreur |
|:----------------|:----------|:----------------------|
|Tous les fournisseurs |USR_ERROR_INVALID_RESOURCE_CREDENTIALS |Les informations d’identification d’authentification que vous avez fournies ne sont pas valides. Veillez à entrer les informations d’identification correctes. Pour plus d’informations, contactez le support technique Microsoft. |
|Tous les fournisseurs |USR_ERROR_ACCESS_DENIED |Accès refusé par le partenaire. Confirmez que les informations d’identification que vous avez entrées sont correctes ou contactez l’équipe de support du fournisseur de contenu. |

## <a name="content-consumption-for-end-users"></a>Consommation de contenu pour les utilisateurs finaux

Une fois que vous avez ajouté un fournisseur de contenu en tant que source de contenu à partir du Centre d'administration Microsoft 365, le contenu du fournisseur est disponible vers l’application Learning Et est visible pour les utilisateurs finaux.

Une fois qu’un utilisateur choisit de jouer à un cours dans Learning, il est dirigé vers la page web du fournisseur de contenu et doit entrer les informations d’identification sur la page de connexion du fournisseur. [En savoir plus sur la consommation de contenu avec Learning](https://support.microsoft.com/office/01bfed12-c327-41e0-a68f-7fa527dcc98a).
