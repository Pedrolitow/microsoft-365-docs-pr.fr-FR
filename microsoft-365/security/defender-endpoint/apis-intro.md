---
title: Accéder aux API Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez comment utiliser les API pour automatiser les flux de travail et innover en fonction des fonctionnalités Microsoft Defender pour point de terminaison
keywords: api, api, wdatp, api ouverte, api microsoft defender pour point de terminaison, microsoft defender atp, api publique, api prises en charge, alertes, appareil, utilisateur, domaine, ip, fichier, repérage avancé, requête
ms.mktglfcycl: deploy
ms.sitesec: library
ms.service: microsoft-365-security
ms.subservice: mde
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.custom: api
search.appverid: met150
ms.openlocfilehash: bd2bc8dad27774609000e6c28921c8cfbc63e816
ms.sourcegitcommit: b9282493c371d59c2e583b9803825096499b5e2c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68151846"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>Accéder aux API Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison plans 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Defender pour point de terminaison expose une grande partie de ses données et actions par le biais d’un ensemble d’API programmatiques. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de Defender pour point de terminaison. L’accès à l’API nécessite l’authentification OAuth2.0. Pour plus d’informations, consultez [le flux de code d’autorisation OAuth 2.0](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Regardez cette vidéo pour obtenir une vue d’ensemble rapide des API de Defender pour point de terminaison.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

En général, vous devez effectuer les étapes suivantes pour utiliser les API :

- Créer une [application AAD](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API Defender pour point de terminaison

Vous pouvez accéder à l’API Defender pour point de terminaison avec **le contexte d’application** ou le **contexte utilisateur**.

- **Contexte d’application : (recommandé)**

  Utilisé par les applications qui s’exécutent sans qu’un utilisateur connecté soit présent. par exemple, les applications qui s’exécutent en tant que services ou démons en arrière-plan.

  Étapes à suivre pour accéder à l’API Defender pour point de terminaison avec le contexte de l’application :

  1. Créez une application web AAD.
  2. Affectez l’autorisation souhaitée à l’application, par exemple, « Lire les alertes », « Isoler les machines ».
  3. Créez une clé pour cette application.
  4. Obtenez un jeton à l’aide de l’application avec sa clé.
  5. Utiliser le jeton pour accéder à l’API Microsoft Defender pour point de terminaison

     Pour plus d’informations, consultez [Obtenir un accès avec le contexte d’application](exposed-apis-create-app-webapp.md).

- **Contexte utilisateur :**

  Utilisé pour effectuer des actions dans l’API pour le compte d’un utilisateur.

  Étapes à suivre pour accéder à l’API Defender pour point de terminaison avec le contexte utilisateur :

  1. Créez une application native AAD.
  2. Affectez l’autorisation souhaitée à l’application, par exemple « Lire les alertes », « Isoler les machines », etc.
  3. Obtenez un jeton à l’aide de l’application avec les informations d’identification de l’utilisateur.
  4. Utiliser le jeton pour accéder à l’API Microsoft Defender pour point de terminaison

     Pour plus d’informations, consultez [Obtenir un accès avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>Voir aussi

- [API Microsoft Defender pour point de terminaison](exposed-apis-list.md)
- [Accéder Microsoft Defender pour point de terminaison avec le contexte d’application](exposed-apis-create-app-webapp.md)
- [Accéder Microsoft Defender pour point de terminaison avec le contexte utilisateur](exposed-apis-create-app-nativeapp.md)
