---
title: Ajouter d’autres fournisseurs de contenu pour Apprentissage Microsoft Viva
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 10/22/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer d’autres fournisseurs en tant que source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ROBOTS: NOINDEX
ms.openlocfilehash: 1a638131b9bf8cca41f7ee8575e472885929d3c8
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60588004"
---
# <a name="add-other-content-providers-for-microsoft-viva-learning"></a>Ajouter d’autres fournisseurs de contenu pour Apprentissage Microsoft Viva

>[!NOTE]
>Cette fonctionnalité n’est pas prise en charge en prévisualisation.

Un nombre croissant de fournisseurs de contenu d’apprentissage et de systèmes de gestion de l’apprentissage sont disponibles par le biais de Learning. Cet ensemble peut changer à tout moment à mesure que de plus en plus de fournisseurs rejoignent ou modifient leur statut avec le programme.

Les sources de contenu tierces ne sont pas activées par défaut. Pour activer ces sources, vous devez les ajouter dans le [Centre d'administration Microsoft 365](content-sources-365-admin-center.md#configure-settings-for-the-learning-content-sources) et suivre les instructions spécifiques indiquées dans le tableau suivant.

|Fournisseur de contenu  |Instructions de configuration  |
|---------|---------|
|Cornerstone OnDemand |[Configurer La fonction OnDemand en tant que source de contenu](configure-cornerstone-content-source.md)         |
|Go1     |[Configurer Go1 en tant que source de contenu](configure-go1-content-source.md)         |
|Saba    |[Configurer Le nom d’une source de contenu](configure-saba-content-source.md)         |
|Skillsoft     |[Configurer Skillsoft en tant que source de contenu](configure-skillsoft-content-source.md)         |
|SAP SuccessFactors   |[Configurer SAP SuccessFactors en tant que source de contenu](configure-successfactors-content-source.md)         |
|Udemy   |[Configurer Udemy en tant que source de contenu](configure-udemy-content-source.md)         |

## <a name="content-ingestion-errors"></a>Erreurs d’ingestion de contenu

Si vous avez des erreurs dans votre Centre d'administration Microsoft 365 lors de l’ingestion de contenu, reportez-vous au tableau ci-dessous pour connaître les étapes suivantes. Notez qu’il s’agit d’une liste exhaustive qui peut contenir d’autres codes d’erreur à l’avenir.

|Fournisseur de contenu |Code d’erreur |Description du code d’erreur |
|:----------------|:----------|:----------------------|
|Tous les fournisseurs |USR_ERROR_INVALID_RESOURCE_CREDENTIALS |Les informations d’identification d’authentification que vous avez fournies ne sont pas valides. Veillez à entrer les informations d’identification correctes. Pour plus d’informations, contactez le support technique Microsoft. |
|Tous les fournisseurs |USR_ERROR_ACCESS_DENIED |Accès refusé par le partenaire. Confirmez que les informations d’identification que vous avez entrées sont correctes ou contactez l’équipe de support du fournisseur de contenu. |
|SuccessFactors |USR_ERROR_SFTP_NO_FILES_FOUND |Aucun nouveau contenu n’a été ingéré car aucun fichier n’était présent sur le serveur SFTP SuccessFactors. |
|SuccessFactors |USR_ERROR_SF_PACKAGE_NOT_FOUND |Aucun nouveau contenu ingéré comme package requis n’a été trouvé sur le serveur SFTP SuccessFactors. |
|Cornerstone OnDemand |USR_ERROR_INVALID_RESOURCE_CREDENTIALS |Les informations d’identification d’authentification que vous avez fournies ne sont pas valides. Assurez-vous que les informations d’identification sont copiées à partir de l’application Learning dans le portail OnDemand. |

## <a name="third-party-content-consumption"></a>Consommation de contenu tierce

Une fois que vous avez ajouté un fournisseur de contenu tiers en tant que source de contenu à partir de la Centre d'administration Microsoft 365, le contenu du fournisseur est disponible vers l’application Learning De plus, il est visible pour les utilisateurs finaux.

Une fois qu’un utilisateur choisit de lire un cours dans Le Learning, il est dirigé vers la page web du fournisseur de contenu et doit entrer les informations d’identification sur la page de connexion du fournisseur. [En savoir plus sur la consommation de contenu avec Learning](https://support.microsoft.com/office/viva-learning-preview-01bfed12-c327-41e0-a68f-7fa527dcc98a).
