---
title: Accéder aux API Microsoft 365 Defender
description: Découvrez comment accéder aux API Microsoft 365 Defender
keywords: accès, API, contexte d’application, contexte utilisateur, application AAD, jeton d’accès
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 5e01aaf2ee9255fd909b26278346fd4ccf54729a
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719237"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Accéder aux API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft 365 Defender expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous aident à automatiser les flux de travail et à utiliser pleinement les fonctionnalités de Microsoft 365 Defender.

En règle générale, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créer une application Azure Active Directory
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

> [!NOTE]
> L’accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Une fois que vous avez effectué ces étapes, vous êtes prêt à accéder à l’API Microsoft 365 Defender à l’aide d’un contexte particulier.

## <a name="application-context-recommended"></a>Contexte d’application (recommandé)

Utilisez ce contexte pour les applications qui s’exécutent sans qu’un utilisateur connecté soit présent, tel que des services d’arrière-plan ou des démons.

1. Créez une application Web Azure Active Directory.
2. Attribuez les autorisations souhaitées à l’application.
3. Créez une clé pour l’application.
4. Obtenir un jeton de sécurité à l’aide de l’application et de sa clé.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez **[la rubrique créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)**.

## <a name="user-context"></a>Contexte utilisateur

Utilisez ce contexte pour effectuer des actions au nom d’un utilisateur unique.

1. Créez une application native Azure Active Directory.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenir un jeton de sécurité à l’aide des informations d’identification de l’utilisateur pour l’application.
4. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez **[la rubrique créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur](api-create-app-user-context.md)**.

## <a name="partner-context"></a>Contexte partenaire

Utilisez ce contexte lorsque vous devez fournir une application à de nombreux utilisateurs sur [plusieurs clients](https://docs.microsoft.com/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Créez une application mutualisée mutualisée d’Azure Active Directory.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenir le consentement de l' [administrateur](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) pour l’application de chaque client.
4. Obtenir un jeton de sécurité à l’aide des informations d’identification de l’utilisateur en fonction de l’ID de client d’un client.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez la rubrique **[créer une application avec un accès partenaire aux API Microsoft 365 Defender](api-partner-access.md)**.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Autorisation 2,0 OAuth pour l’authentification de l’utilisateur et l’accès à l’API](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Gérer les secrets dans vos applications serveur avec le coffre de clés Azure](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/)
- [Créer une application « Hello World » qui accède aux API Microsoft 365](api-hello-world.md)
