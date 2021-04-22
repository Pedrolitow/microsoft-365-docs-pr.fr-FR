---
title: Accéder aux API Microsoft Defender pour point de terminaison.
ms.reviewer: ''
description: Découvrez comment vous pouvez utiliser les API pour automatiser les flux de travail et innover en fonction des fonctionnalités de Microsoft Defender for Endpoint
keywords: api, api, Microsoft Defender pour point de terminaison, api d'ouverture, api Microsoft Defender pour le point de terminaison, api publique, api prise en charge, alertes, appareil, utilisateur, domaine, ip, fichier, recherche avancée, requête
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
ms.openlocfilehash: 87dce8ff4fde505eb8d4e458c8d9fb56556f4d78
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935104"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Accéder aux API Microsoft Defender pour point de terminaison. 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


**S’applique à :** 
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 



Defender pour le point de terminaison expose la plupart de ses données et actions par le biais d'un ensemble d'API par programme. Ces API vous permettront d'automatiser les flux de travail et d'innover en fonction des fonctionnalités de Defender for Endpoint. L'accès à l'API nécessite une authentification OAuth2.0. Pour plus d'informations, voir flux de code [d'autorisation OAuth 2.0.](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)

Regardez cette vidéo pour obtenir une vue d'ensemble rapide des API de Defender for Endpoint. 
>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M]

En règle générale, vous devez suivre les étapes suivantes pour utiliser les API :
- Créer une application AAD
- Obtenir un jeton d'accès à l'aide de cette application
- Utiliser le jeton pour accéder à l'API Defender for Endpoint


Vous pouvez accéder à l'API Defender for Endpoint avec le contexte **de l'application** ou **le contexte utilisateur.**

- **Contexte de l'application : (recommandé)** <br>
    Utilisé par les applications qui s'exécutent sans utilisateur inscrit. par exemple, les applications qui s'exécutent en tant que daemons ou services d'arrière-plan.

    Étapes à suivre pour accéder à l'API Defender for Endpoint avec le contexte de l'application :

  1. Créez une application web AAD.
  2. Attribuez l'autorisation souhaitée à l'application, par exemple, « Lire les alertes » et « Isoler les ordinateurs ». 
  3. Créez une clé pour cette application.
  4. Obtenir un jeton à l'aide de l'application avec sa clé.
  5. Utiliser le jeton pour accéder à l'API Microsoft Defender for Endpoint

     Pour plus d'informations, voir [Obtenir l'accès avec le contexte de l'application.](exposed-apis-create-app-webapp.md)


- **Contexte utilisateur :** <br>
    Permet d'effectuer des actions dans l'API pour le compte d'un utilisateur.

    Étapes à suivre pour accéder à l'API Defender pour Endpoint avec le contexte de l'application :

  1. Créez une application native AAD.
  2. Attribuez l'autorisation souhaitée à l'application, par exemple « Lire les alertes » et « Isoler les ordinateurs » etc. 
  3. Obtenir un jeton à l'aide de l'application avec les informations d'identification de l'utilisateur.
  4. Utiliser le jeton pour accéder à l'API Microsoft Defender for Endpoint

     Pour plus d'informations, voir [Obtenir l'accès avec le contexte utilisateur.](exposed-apis-create-app-nativeapp.md)


## <a name="related-topics"></a>Voir aussi
- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder à Microsoft Defender pour le point de terminaison avec le contexte de l'application](exposed-apis-create-app-webapp.md)
- [Accéder à Microsoft Defender pour le point de terminaison avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md)
