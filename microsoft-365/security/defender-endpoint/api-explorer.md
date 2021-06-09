---
title: Explorateur d’API dans Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Utiliser l’Explorateur d’API pour créer et faire des requêtes API, tester et envoyer des demandes pour n’importe quelle API disponible
keywords: api, explorer, envoyer, demander, obtenir, publier,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6a5684d71d34b3efdfe915ae674b4fcb90342154
ms.sourcegitcommit: 5d8de3e9ee5f52a3eb4206f690365bb108a3247b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "52769796"
---
# <a name="api-explorer"></a>Explorateur d’API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)


L’Explorateur d’API Microsoft Defender pour point de terminaison est un outil qui vous permet d’explorer différentes API Defender pour endpoint de manière interactive. 

L’Explorateur d’API facilite la construction et l’envoi de requêtes API, de test et d’envoi de requêtes pour n’importe quel point de terminaison de l’API Defender for Endpoint disponible. Utilisez l’Explorateur d’API pour prendre des mesures ou rechercher des données qui ne sont peut-être pas encore disponibles via l’interface utilisateur.

L’outil est utile lors du développement d’applications. Il vous permet d’effectuer des requêtes API qui respectent vos paramètres d’accès utilisateur, ce qui réduit la nécessité de générer des jetons d’accès.

Vous pouvez également utiliser l’outil pour explorer la galerie d’exemples de requêtes, copier des exemples de code de résultat et générer des informations de débogage.

Avec l’Explorateur d’API, vous pouvez :

- Exécuter des demandes pour n’importe quelle méthode et voir les réponses en temps réel
- Parcourez rapidement les exemples d’API et découvrez les paramètres qu’ils supportent
- Effectuer facilement des appels d’API ; pas besoin de s’authentifier au-delà de la signature du portail de gestion

## <a name="access-api-explorer"></a>Explorateur d’API Access

Dans le menu de navigation de gauche, sélectionnez **Partenaires & API**  >  **Explorer.**

## <a name="supported-apis"></a>API prise en charge

L’Explorateur d’API prend en charge toutes les API proposées par Defender for Endpoint.
  
La liste des API prise en charge est disponible dans la [documentation des API.](apis-intro.md) 

## <a name="get-started-with-the-api-explorer"></a>Mise en place de l’Explorateur d’API

1. Dans le volet gauche se trouve une liste d’exemples de demandes que vous pouvez utiliser. 
2. Suivez les liens et cliquez sur **Exécuter la requête.** 

Certains exemples peuvent nécessiter la spécification d’un paramètre dans l’URL, par exemple, {machine- ID}.

## <a name="faq"></a>FAQ

**Ai-je besoin d’un jeton d’API pour utiliser l’Explorateur d’API ?** <br>
Les informations d’identification pour accéder à une API ne sont pas nécessaires. L’Explorateur d’API utilise le jeton du portail de gestion Defender for Endpoint chaque fois qu’il effectue une demande.

Les informations d’authentification de l’utilisateur connecté sont utilisées pour vérifier que l’Explorateur d’API est autorisé à accéder aux données en votre nom.

Les demandes d’API spécifiques sont limitées en fonction de vos privilèges RBAC. Par exemple, une demande d'« indicateur d’soumission » est limitée au rôle d’administrateur de sécurité. 
