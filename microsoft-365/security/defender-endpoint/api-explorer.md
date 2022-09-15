---
title: Explorateur d’API dans Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Utiliser l’Explorateur d’API pour construire et effectuer des requêtes d’API, tester et envoyer des demandes pour n’importe quelle API disponible
keywords: api, explorateur, envoyer, demander, obtenir, publier,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 7e38ef8f7034ff86220fc9452c5d0ea94443783d
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67699387"
---
# <a name="api-explorer"></a>Explorateur d’API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

L’Explorateur d’API Microsoft Defender pour point de terminaison est un outil qui vous permet d’explorer différentes API Defender pour point de terminaison de manière interactive.

L’Explorateur d’API facilite la construction et l’exécution de requêtes d’API, de tests et d’envoi de demandes pour tout point de terminaison d’API Defender pour point de terminaison disponible. Utilisez l’Explorateur d’API pour effectuer des actions ou rechercher des données qui ne sont peut-être pas encore disponibles via l’interface utilisateur.

L’outil est utile pendant le développement d’applications. Il vous permet d’effectuer des requêtes d’API qui respectent vos paramètres d’accès utilisateur, ce qui réduit la nécessité de générer des jetons d’accès.

Vous pouvez également utiliser l’outil pour explorer la galerie d’exemples de requêtes, copier des exemples de code de résultat et générer des informations de débogage.

Avec l’Explorateur d’API, vous pouvez :

- Exécutez des demandes pour n’importe quelle méthode et consultez les réponses en temps réel.
- Parcourez rapidement les exemples d’API et découvrez les paramètres qu’ils prennent en charge.
- Passer facilement des appels d’API ; pas besoin de s’authentifier au-delà de la connexion au portail de gestion.

## <a name="access-api-explorer"></a>Explorateur d’API Access

Dans le menu de navigation de gauche, sélectionnez Partenaires & **[l’Explorateur](https://security.microsoft.com/interoperability/api-explorer)** **d’API API**\>.

## <a name="supported-apis"></a>API prises en charge

L’Explorateur d’API prend en charge toutes les API offertes par Defender pour point de terminaison.

La liste des API prises en charge est disponible dans la [documentation des API](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>Prise en main de l’Explorateur d’API

1. Dans le volet gauche, il existe une liste d’exemples de demandes que vous pouvez utiliser.
2. Suivez les liens et cliquez sur **Exécuter la requête**.

Certains exemples peuvent nécessiter la spécification d’un paramètre dans l’URL, par exemple, {machine- ID}.

## <a name="faq"></a>FAQ

**Dois-je disposer d’un jeton d’API pour utiliser l’Explorateur d’API ?** <br>
Les informations d’identification pour accéder à une API ne sont pas nécessaires. L’Explorateur d’API utilise le jeton du portail de gestion defender pour point de terminaison chaque fois qu’il effectue une requête.

Les informations d’identification d’authentification de l’utilisateur connecté sont utilisées pour vérifier que l’Explorateur d’API est autorisé à accéder aux données en votre nom.

Les demandes d’API spécifiques sont limitées en fonction de vos privilèges RBAC. Par exemple, une demande d'« indicateur d’envoi » est limitée au rôle d’administrateur de sécurité.
