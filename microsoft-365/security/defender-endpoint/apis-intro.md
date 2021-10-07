---
title: Accéder aux API Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez comment vous pouvez utiliser les API pour automatiser les flux de travail et innover en fonction des fonctionnalités de Microsoft Defender for Endpoint
keywords: api, api, wdatp, api d’ouverture, microsoft defender pour l’api de point de terminaison, microsoft defender atp, api publique, api pris en charge, alertes, appareil, utilisateur, domaine, ip, fichier, recherche avancée, requête
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1ccd9982f387fb5af984bf2b381053d786cc5615
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60191994"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Accéder aux API Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender pour le point de terminaison expose la plupart de ses données et actions par le biais d’un ensemble d’API par programme. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de Defender for Endpoint. L’accès à l’API nécessite une authentification OAuth2.0. Pour plus d’informations, [voir code d’autorisation OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Regardez cette vidéo pour obtenir une vue d’ensemble rapide des API de Defender for Endpoint.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :

- Créer une [application AAD](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Defender for Endpoint

Vous pouvez accéder à l’API Defender for Endpoint avec le contexte **de l’application** ou **le contexte utilisateur.**

- **Contexte de l’application : (recommandé)**

  Utilisé par les applications qui s’exécutent sans utilisateur inscrit. par exemple, les applications qui s’exécutent en tant que daemons ou services d’arrière-plan.

  Étapes à suivre pour accéder à l’API Defender for Endpoint avec le contexte de l’application :

  1. Créez une application web AAD.
  2. Attribuez l’autorisation souhaitée à l’application, par exemple, « Lire les alertes » et « Isoler les ordinateurs ».
  3. Créez une clé pour cette application.
  4. Obtenir un jeton à l’aide de l’application avec sa clé.
  5. Utiliser le jeton pour accéder à l’API Microsoft Defender for Endpoint

     Pour plus d’informations, voir [Obtenir l’accès avec le contexte de l’application.](exposed-apis-create-app-webapp.md)

- **Contexte utilisateur :**

  Permet d’effectuer des actions dans l’API pour le compte d’un utilisateur.

  Étapes à suivre pour accéder à l’API Defender pour Endpoint avec le contexte de l’application :

  1. Créez une application native AAD.
  2. Attribuez l’autorisation souhaitée à l’application, par exemple « Lire les alertes » et « Isoler les ordinateurs » etc.
  3. Obtenir un jeton à l’aide de l’application avec les informations d’identification de l’utilisateur.
  4. Utiliser le jeton pour accéder à l’API Microsoft Defender for Endpoint

     Pour plus d’informations, voir [Obtenir l’accès avec le contexte utilisateur.](exposed-apis-create-app-nativeapp.md)

## <a name="related-topics"></a>Rubriques connexes

- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder à Microsoft Defender pour le point de terminaison avec le contexte de l’application](exposed-apis-create-app-webapp.md)
- [Accéder à Microsoft Defender pour le point de terminaison avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md)
