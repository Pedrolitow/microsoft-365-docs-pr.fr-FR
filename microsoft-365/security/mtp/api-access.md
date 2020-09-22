---
title: Accéder aux API de protection contre les menaces Microsoft
description: Découvrez comment accéder aux API de protection contre les menaces Microsoft
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
ms.openlocfilehash: bccf36f46121caceeb6dc6d97c126f48149d9426
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48197880"
---
# <a name="access-the-microsoft-threat-protection-apis"></a>Accéder aux API de protection contre les menaces Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

>[!IMPORTANT] 
>Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.


 La protection contre les menaces Microsoft expose une grande partie de ses données et actions via un ensemble d’API de programmation. Ces API vous permettront d’automatiser les flux de travail et d’innover en fonction des fonctionnalités de protection contre les menaces Microsoft. L’accès à l’API nécessite l’authentification OAuth 2.0. Pour plus d’informations, reportez-vous au [flux de code d’autorisation OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).


En règle générale, vous devez effectuer les étapes suivantes pour utiliser les API :
- Créer une application AAD
- Obtenir un jeton d’accès à l’aide de cette application
- Utiliser le jeton pour accéder à l’API de protection contre les menaces Microsoft


Vous pouvez accéder à l’API de protection contre les menaces Microsoft avec le contexte de l' **application** ou le **contexte utilisateur**.

- **Contexte de l’application : (recommandé)** <br>
    Utilisé par les applications qui s’exécutent sans qu’aucun utilisateur ne soit connecté. par exemple, les applications qui s’exécutent en tant que services ou démons d’arrière-plan.

    Étapes à suivre pour accéder à l’API Microsoft Threat Protection avec le contexte de l’application :

  1. Créer une application Web AAD.
  2. Attribuez l’autorisation souhaitée à l’exemple applicationFor, **incident. Read. All**, **AdvancedHunting. Read. All**. 
  3. Créez une clé pour cette application.
  4. Obtenir un jeton à l’aide de l’application avec sa clé.
  5. Utiliser le jeton pour accéder à l’API de protection contre les menaces Microsoft

     Pour plus d’informations, consultez la rubrique [Get Access with application Context](api-create-app-web.md).


- **Contexte utilisateur :** <br>
    Permet d’effectuer des actions dans l’API pour le compte d’un utilisateur.

    Étapes à suivre pour accéder à l’API Microsoft Threat Protection avec le contexte de l’application :
  1. Créer une application native AAD.
  2. Attribuez l’autorisation souhaitée à l’application. Par exemple, **incident. Read**, **AdvancedHunting. Read**.
  3. Obtenir un jeton à l’aide de l’application avec des informations d’identification utilisateur.
  4. Utiliser le jeton pour accéder à l’API de protection contre les menaces Microsoft

     Pour plus d’informations, consultez la rubrique [Get Access with User Context](api-create-app-user-context.md).


## <a name="related-topics"></a>Voir aussi
- [API de protection contre les menaces Microsoft](api-supported.md)
- [Accéder à la protection contre les menaces Microsoft avec le contexte d’application](api-create-app-web.md)
- [Accéder à la protection contre les menaces Microsoft avec le contexte utilisateur](api-create-app-user-context.md)
