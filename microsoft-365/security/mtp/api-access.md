---
title: Accéder aux API Microsoft 365 Defender
description: Découvrez comment accéder aux API Microsoft 365 Defender
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
ms.openlocfilehash: ea787adfba0afb425da5f6ea0f6609f96e06b378
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49932153"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Accéder aux API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations concernent des produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft 365 Defender expose la plupart de ses données et actions par le biais d’un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser pleinement les fonctionnalités de Microsoft 365 Defender.

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :

- Créer une application Azure Active Directory
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

> [!NOTE]
> L’accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, voir flux de code [d’autorisation OAuth 2.0.](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)

Une fois ces étapes accomplies, vous êtes prêt à accéder à l’API Microsoft 365 Defender à l’aide d’un contexte particulier.

## <a name="application-context-recommended"></a>Contexte de l’application (recommandé)

Utilisez ce contexte pour les applications qui s’exécutent sans utilisateur inscrit, tels que les services d’arrière-plan ou les daemons.

1. Créez une application web Azure Active Directory.
2. Attribuez les autorisations souhaitées à l’application.
3. Créez une clé pour l’application.
4. Obtenez un jeton de sécurité à l’aide de l’application et de sa clé.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, voir **[Créer une application pour accéder à Microsoft 365 Defender sans utilisateur.](api-create-app-web.md)**

## <a name="user-context"></a>Contexte utilisateur

Utilisez ce contexte pour effectuer des actions au nom d’un seul utilisateur.

1. Créez une application native Azure Active Directory.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur pour l’application.
4. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, voir Créer une application pour accéder aux **[API Microsoft 365 Defender au nom d’un utilisateur.](api-create-app-user-context.md)**

## <a name="partner-context"></a>Contexte du partenaire

Utilisez ce contexte lorsque vous devez fournir une application à de nombreux utilisateurs sur [plusieurs clients.](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps)

1. Créez une application azure Active Directory multi-client.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenir [le consentement de l’administrateur](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) pour l’application auprès de chaque client.
4. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur en fonction de l’ID de locataire d’un client.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, voir Créer une application avec un accès partenaire aux **[API Microsoft 365 Defender.](api-partner-access.md)**

## <a name="related-articles"></a>Articles connexes

- [Présentation des API Microsoft 365 Defender](api-overview.md)
- [Autorisation OAuth 2.0 pour la connexion de l’utilisateur et l’accès à l’API](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/)
- [Créer une application « Hello World » qui accède aux API Microsoft 365](api-hello-world.md)
