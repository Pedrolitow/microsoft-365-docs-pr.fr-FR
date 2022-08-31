---
title: Accéder aux API Microsoft 365 Defender
description: Découvrez comment accéder aux API Microsoft 365 Defender
keywords: access, apis, contexte d’application, contexte utilisateur, application aad, jeton d’accès
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.custom: api
ms.openlocfilehash: 0562ff901aa8021973fb1ed36e8caf464f22d672
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481567"
---
# <a name="access-the-microsoft-365-defender-apis"></a>Accéder aux API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft 365 Defender expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous aident à automatiser les flux de travail et à tirer pleinement profit des fonctionnalités de Microsoft 365 Defender.

En général, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créer une application Azure Active Directory
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Microsoft 365 Defender

> [!NOTE]
> L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Une fois ces étapes effectuées, vous êtes prêt à accéder à l’API Microsoft 365 Defender à l’aide d’un contexte particulier.

## <a name="application-context-recommended"></a>Contexte d’application (recommandé)

Utilisez ce contexte pour les applications qui s’exécutent sans qu’un utilisateur connecté soit présent, comme les services en arrière-plan ou les démons.

1. Créez une application web Azure Active Directory.
2. Affectez les autorisations souhaitées à l’application.
3. Créez une clé pour l’application.
4. Obtenez un jeton de sécurité à l’aide de l’application et de sa clé.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez **[Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md)**.

## <a name="user-context"></a>Contexte utilisateur

Utilisez ce contexte pour effectuer des actions pour le compte d’un seul utilisateur.

1. Créez une application native Azure Active Directory.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur pour l’application.
4. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez **[Créer une application pour accéder à Microsoft 365 Defender API pour le compte d’un utilisateur](api-create-app-user-context.md)**.

## <a name="partner-context"></a>Contexte du partenaire

Utilisez ce contexte lorsque vous devez fournir une application à de nombreux utilisateurs sur [plusieurs locataires](/azure/active-directory/develop/single-and-multi-tenant-apps).

1. Créez une application multilocataire Azure Active Directory.
2. Attribuez l’autorisation souhaitée à l’application.
3. Obtenez le [consentement de l’administrateur](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) pour l’application auprès de chaque locataire.
4. Obtenez un jeton de sécurité à l’aide des informations d’identification de l’utilisateur en fonction de l’ID de locataire d’un client.
5. Utilisez le jeton pour accéder à l’API Microsoft 365 Defender.

Pour plus d’informations, consultez **[Créer une application avec accès partenaire aux API Microsoft 365 Defender](api-partner-access.md)**.

## <a name="related-articles"></a>Articles connexes

- [Vue d’ensemble des API Microsoft 365 Defender](api-overview.md)
- [Autorisation OAuth 2.0 pour la connexion utilisateur et l’accès à l’API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [Gérer les secrets dans vos applications serveur avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [Créer une application « Hello World » qui accède aux API Microsoft 365](api-hello-world.md)
