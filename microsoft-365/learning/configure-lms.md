---
title: Ajouter des systèmes de gestion de l’apprentissage Apprentissage Microsoft Viva
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 11/01/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer des systèmes de gestion de l’apprentissage en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ms.openlocfilehash: 84f2e0d50b36f7fe54d82db9fb5564dcbbcbe9fa
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60677147"
---
# <a name="add-learning-management-systems-for-microsoft-viva-learning"></a>Ajouter des systèmes de gestion de l’apprentissage Apprentissage Microsoft Viva

Un nombre croissant de systèmes de gestion de l’apprentissage sont disponibles par le biais de Learning. Cet ensemble peut changer à tout moment à mesure que de plus en plus de fournisseurs rejoignent ou modifient leur statut avec le programme.

Learning de gestion ne sont pas activés par défaut. Pour activer ces sources, vous devez les ajouter dans le [Centre d'administration Microsoft 365](content-sources-365-admin-center.md#configure-settings-for-the-learning-content-sources) et suivre les instructions spécifiques indiquées dans le tableau suivant.

>[!NOTE]
>Vous aurez besoin d’une licence Premium pour connecter des systèmes de gestion de l’apprentissage. [En savoir plus sur la gestion des licences.](https://www.microsoft.com/microsoft-viva/learning)

>[!NOTE]
>Il faut entre 24 et 48 heures pour que les utilisateurs de Learning voient le contenu des sources que vous avez activées dans le portail d’administration.

## <a name="learning-management-systems"></a>Learning de gestion des systèmes

|Learning gestion des données  |Instructions de configuration  |
|---------|---------|
|Cornerstone OnDemand |[Configurer La fonction OnDemand en tant que source de contenu](configure-cornerstone-content-source.md)         |
|Saba    |[Configurer Le nom de la source de contenu](configure-saba-content-source.md)         |
|SAP SuccessFactors   |[Configurer SAP SuccessFactors en tant que source de contenu](configure-successfactors-content-source.md)         |

>[!NOTE]
>Les systèmes de gestion de l’apprentissage disponibles peuvent faire l’objet de changements. Selon votre organisation, vous avez peut-être accès à différents systèmes de gestion de l’apprentissage que ceux répertoriés ici.

## <a name="content-ingestion-errors"></a>Erreurs d’ingestion de contenu

Si vous avez des erreurs dans votre Centre d'administration Microsoft 365 lors de l’ingestion de contenu, reportez-vous au tableau ci-dessous pour connaître les étapes suivantes. Notez qu’il s’agit d’une liste exhaustive qui peut contenir d’autres codes d’erreur à l’avenir.

|Learning gestion des données |Code d’erreur |Description du code d’erreur |
|:----------------|:----------|:----------------------|
|Tous les LMS |USR_ERROR_INVALID_RESOURCE_CREDENTIALS |Les informations d’identification d’authentification que vous avez fournies ne sont pas valides. Veillez à entrer les informations d’identification correctes. Pour plus d’informations, contactez le support technique Microsoft. |
|Tous les LMS |USR_ERROR_ACCESS_DENIED |Accès refusé par le partenaire. Confirmez que les informations d’identification que vous avez entrées sont correctes ou contactez l’équipe de support du fournisseur de contenu. |
|SuccessFactors |USR_ERROR_SFTP_NO_FILES_FOUND |Aucun nouveau contenu n’a été ingéré car aucun fichier n’était présent sur le serveur SFTP SuccessFactors. |
|SuccessFactors |USR_ERROR_SF_PACKAGE_NOT_FOUND |Aucun nouveau contenu ingéré comme package requis n’a été trouvé sur le serveur SFTP SuccessFactors. |
|Cornerstone OnDemand |USR_ERROR_INVALID_RESOURCE_CREDENTIALS |Les informations d’identification d’authentification que vous avez fournies ne sont pas valides. Assurez-vous que les informations d’identification sont copiées à partir Apprentissage Microsoft Viva portail OnDemand de la base de données. |

## <a name="content-consumption-for-end-users"></a>Consommation de contenu pour les utilisateurs finaux

Une fois que vous avez ajouté un système de gestion de l’apprentissage en tant que source de contenu à partir du Centre d'administration Microsoft 365, le contenu du LMS est dirigé vers l’application Contrôle Learning et est visible pour les utilisateurs finaux.

Une fois qu’un utilisateur choisit de lire un cours dans Le Learning, il est dirigé vers la page web LMS et doit entrer les informations d’identification de connexion sur la page de connexion LMS. [En savoir plus sur la consommation de contenu avec Learning](https://support.microsoft.com/office/01bfed12-c327-41e0-a68f-7fa527dcc98a).
