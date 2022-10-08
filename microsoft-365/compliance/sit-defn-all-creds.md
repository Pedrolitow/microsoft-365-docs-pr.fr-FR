---
title: Définition de toutes les entités d’informations d’identification
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Toutes les définitions d’entité de type d’informations sensibles d’informations d’identification.
ms.openlocfilehash: e1ee31762e8ef8df6857600b8b609a19cd56c7e2
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68506799"
---
# <a name="all-credential-sensitive-information-types"></a>Tous les types d’informations sensibles aux informations d’identification

Toutes les informations d’identification sont un type d’informations sensibles d’entité groupée (SIT). Il détecte les informations d’identification de tous les services et environnements pris en charge, notamment Amazon, Azure, GitHub, Google, Microsoft General, Slack et bien plus encore.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Divers

## <a name="pattern"></a>Modèle

Divers

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="description"></a>Description

Le SIT Toutes les informations d’identification est un SIT groupé qui recherche des types d’informations d’identification individuels. Cela inclut les valeurs évaluées par somme de contrôle et les combinaisons de mots clés/modèles. Toutes les analyses d’entité d’informations d’identification pour l’une des sommes de contrôle et/ou modèles de type informations d’identification sous-jacentes sont détectées dans un document.

## <a name="contains"></a>Contains

Cette entité groupée SIT contient les SIT individuels suivants :

- [Clé d’accès secret client Amazon S3](sit-defn-amazon-s3-client-secret-access-key.md)
- [Clé d’ordinateur ASP.NET](sit-defn-asp-net-machine-key.md) 
- [Jeton d’accès client Azure AD](sit-defn-azure-ad-client-access-token.md) 
- [Clé secrète client Azure AD](sit-defn-azure-ad-client-secret.md) 
- [Informations d’identification de l’utilisateur Azure AD](sit-defn-azure-ad-user-credentials.md)
- [mot de passe de déploiement Azure App Service](sit-defn-azure-app-service-deployment-password.md)
- [Clé d’accès partagée du service Azure Batch](sit-defn-azure-batch-shared-access-key.md) 
- [Clé secrète Azure Bot Framework](sit-defn-azure-bot-framework-secret-key.md) 
- [Secret d’application Azure Bot Service](sit-defn-azure-bot-service-app-secret.md) 
- [clé API Recherche cognitive Azure](sit-defn-azure-cognitive-search-api-key.md) 
- [Clé Azure Cognitive Service](sit-defn-azure-cognitive-service-key.md) 
- [clé d’accès Azure Container Registry](sit-defn-azure-container-registry-access-key.md) 
- [Clé d’accès au compte Azure COSMOS DB](sit-defn-azure-cosmos-db-account-access-key.md)
- [Jeton d’accès personnel Azure Databricks](sit-defn-azure-databricks-personal-access-token.md)
- [Secret d’application Azure DevOps](sit-defn-azure-devops-app-secret.md) 
- [Jeton d’accès personnel Azure DevOps](sit-defn-azure-devops-personal-access-token.md) 
- [Clé d’accès Azure EventGrid](sit-defn-azure-eventgrid-access-key.md) 
- [Maître de fonction Azure / clé API](sit-defn-azure-function-master-api-key.md) 
- [Clé d’accès partagé Azure IoT](sit-defn-azure-iot-shared-access-key.md)
- [Signature d’accès partagé Azure Logic App](sit-defn-azure-logic-app-shared-access-signature.md)
- [Clé API du service web Azure Machine Learning](sit-defn-azure-machine-learning-web-service-api-key.md) 
- [clé d’abonnement Azure Maps](sit-defn-azure-maps-subscription-key.md) 
- [Mot de passe de chaîne de connexion du cache Redis Azure](sit-defn-azure-redis-cache-connection-string-password.md)
- [signature d’accès partagé Azure Service Bus](sit-defn-azure-service-bus-shared-access-signature.md) 
- [Clé d’accès partagé Azure / jeton webhook](sit-defn-azure-shared-access-key-web-hook-token.md)
- [Clé d’accès Azure SignalR](sit-defn-azure-signalr-access-key.md) 
- [chaîne de connexion Azure SQL](sit-defn-azure-sql-connection-string.md)
- [Clé d’accès au compte de stockage Azure](sit-defn-azure-storage-account-access-key.md)
- [Signature d’accès partagé du compte de stockage Azure](sit-defn-azure-storage-account-shared-access-signature.md) 
- [Signature d’accès partagé du compte de stockage Azure pour les ressources à haut risque](sit-defn-azure-storage-account-shared-access-signature-high-risk-resources.md) 
- [Certificat de gestion des abonnements Azure](sit-defn-azure-subscription-management-certificate.md) 
- [Clé secrète client/API](sit-defn-client-secret-api-key.md)
- [Mot de passe général](sit-defn-general-password.md) 
- [Clé symétrique générale](sit-defn-general-symmetric-key.md)
- [Jeton d’accès personnel GitHub](sit-defn-github-personal-access-token.md)
- [Clé API Google](sit-defn-google-api-key.md) 
- [En-tête d’autorisation HTTP](sit-defn-http-authorization-header.md)
- [Clé microsoft Bing Cartes](sit-defn-google-api-key.md)
- [Jeton d’accès Slack](sit-defn-slack-access-token.md) 
- [Informations d’identification de connexion utilisateur](sit-defn-user-login-credentials.md)
- [Clé privée de certificat X.509](sit-defn-x-509-certificate-private-key.md)

## <a name="supported-languages"></a>Langues prises en charge

- Français
- Bulgare
- Chinois
- Croate
- Tchèque
- Danois
- Estonien
- Finnois
- Français
- Allemand
- Hongrois
- Islandais
- Irlandais
- Italien
- Japonais
- Letton
- Lituanien
- Maltais
- Néerlandais
- Norvégien
- Polonais
- Portugais
- Roumain
- Slovaque
- Slovène
- Espagnol
- Suédois
- Turc