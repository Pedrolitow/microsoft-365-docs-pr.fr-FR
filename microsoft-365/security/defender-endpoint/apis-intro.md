---
title: Accéder aux API Microsoft Defender pour point de terminaison.
ms.reviewer: ''
description: Découvrez comment utiliser les API pour automatiser les workflows et innover en fonction des fonctionnalités Microsoft Defender for Endpoint
keywords: apis, api, wdatp, open api, microsoft defender pour endpoint api, microsoft defender atp, public api, apis pris en charge, alertes, appareil, utilisateur, domaine, ip, fichier, chasse avancée, requête
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: a91a401d5d57c7757bc043178c95dc42e7733b41
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52571828"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Accéder aux API Microsoft Defender pour point de terminaison. 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


**S’applique à :** 
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous voulez faire l’expérience de Microsoft Defender pour Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 



Defender for Endpoint expose une grande partie de ses données et actions à travers un ensemble d’API programmatiques. Ces API vous permettront d’automatiser les workflows et d’innover en fonction des fonctionnalités Defender for Endpoint. L’accès api nécessite une authentification OAuth2.0. Pour plus d’informations, [voir OAuth 2.0 Authorization Code Flow](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Regardez cette vidéo pour un aperçu rapide des API defender for Endpoint. 
>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M]

En général, vous devrez prendre les mesures suivantes pour utiliser les API :
- Créer une [application AAD](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Obtenez un jeton d’accès à l’aide de cette application
- Utilisez le jeton pour accéder à Defender pour l’API Endpoint


Vous pouvez accéder à Defender for Endpoint API avec le contexte **d’application ou** le **contexte utilisateur**.

- **Contexte d’application : (Recommandé)** <br>
    Utilisé par les applications qui s’exécutent sans un utilisateur connecté présent. par exemple, les applications qui s’exécutent sous forme de services d’arrière-plan ou de démons.

    Mesures à prendre pour accéder à Defender for Endpoint API avec le contexte de l’application :

  1. Créez une application Web AAD.
  2. Attribuez l’autorisation souhaitée à l’application, par exemple « Lire les alertes », « Isoler les machines ». 
  3. Créez une clé pour cette application.
  4. Obtenez un jeton en utilisant l’application avec sa clé.
  5. Utilisez le jeton pour accéder à l’API Microsoft Defender for Endpoint

     Pour plus d’informations, voir [Obtenez l’accès avec le contexte de l’application](exposed-apis-create-app-webapp.md).


- **Contexte de l’utilisateur :** <br>
    Utilisé pour effectuer des actions dans l’API pour le compte d’un utilisateur.

    Mesures à prendre pour accéder à Defender for Endpoint API avec le contexte de l’application :

  1. Créez l’application native AAD.
  2. Attribuez l’autorisation souhaitée à l’application, par exemple « Lire les alertes », « Isoler les machines », etc. 
  3. Obtenez un jeton à l’aide de l’application avec les informations d’identification de l’utilisateur.
  4. Utilisez le jeton pour accéder à l’API Microsoft Defender for Endpoint

     Pour plus d’informations, voir [Obtenez l’accès avec le contexte de l’utilisateur](exposed-apis-create-app-nativeapp.md).


## <a name="related-topics"></a>Voir aussi
- [Microsoft Defender pour les API endpoint](exposed-apis-list.md)
- [Accédez à Microsoft Defender pour Endpoint avec le contexte de l’application](exposed-apis-create-app-webapp.md)
- [Accédez à Microsoft Defender pour Endpoint avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md)
