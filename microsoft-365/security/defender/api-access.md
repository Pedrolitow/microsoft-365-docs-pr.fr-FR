---
title: Accéder aux API Microsoft 365 Defender de données
description: Découvrez comment accéder aux API Microsoft 365 Defender de données
keywords: access, api, contexte d’application, contexte utilisateur, application aad, jeton d’accès
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a8406c0ec27c238615b25f60b988efbb50a8d7d7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62172234"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Accéder aux API Microsoft 365 Defender de données

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft 365 Defender expose la plupart de ses données et actions par le biais d’un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser Microsoft 365 Defender fonctionnalités de l’utilisateur.

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :

- Créer une application Azure Active Directory application
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Microsoft 365 Defender de connexion

> [!NOTE]
> L’accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, [voir code d’autorisation OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Une fois ces étapes accomplies, vous êtes prêt à accéder à l’API Microsoft 365 Defender à l’aide d’un contexte particulier.

## <a name="application-context-recommended"></a>Contexte de l’application (recommandé)

Utilisez ce contexte pour les applications qui s’exécutent sans utilisateur inscrit, tels que les services d’arrière-plan ou les daemons.

1. Créez une Azure Active Directory application web.
2. Attribuez les autorisations souhaitées à l’application.
3. Créez une clé pour l’application.
4. Obtenez un jeton de sécurité à l’aide de l’application et de sa clé.
5. Utilisez le jeton pour accéder à l Microsoft 365 Defender API.

Pour plus d’informations, voir **[Créer une application pour accéder Microsoft 365 Defender sans utilisateur.](api-create-app-web.md)**

## <a name="user-context"></a>Contexte utilisateur

Utilisez ce contexte pour effectuer des actions au nom d’un seul utilisateur.

1. Créez une Azure Active Directory application native.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur pour l’application.
4. Utilisez le jeton pour accéder à l Microsoft 365 Defender API.

Pour plus d’informations, voir **[Créer une application pour accéder Microsoft 365 Defender API au nom d’un utilisateur.](api-create-app-user-context.md)**

## <a name="partner-context"></a>Contexte du partenaire

Utilisez ce contexte lorsque vous devez fournir une application à de nombreux utilisateurs sur [plusieurs clients.](/azure/active-directory/develop/single-and-multi-tenant-apps)

1. Créez une Azure Active Directory application multi-client.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenir [le consentement de l’administrateur](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) pour l’application auprès de chaque client.
4. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur en fonction de l’ID de locataire d’un client.
5. Utilisez le jeton pour accéder à l Microsoft 365 Defender API.

Pour plus d’informations, voir Créer une application avec un accès partenaire **[à Microsoft 365 Defender API.](api-partner-access.md)**

## <a name="related-articles"></a>Articles connexes

- [présentation Microsoft 365 Defender API de Microsoft 365 Defender’api](api-overview.md)
- [Autorisation OAuth 2.0 pour la connexion de l’utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Créer une application « Hello World » qui accède aux API Microsoft 365'application](api-hello-world.md)
