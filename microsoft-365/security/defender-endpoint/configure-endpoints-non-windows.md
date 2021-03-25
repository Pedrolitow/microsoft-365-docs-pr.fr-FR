---
title: Intégrer des appareils autres que Windows au service Microsoft Defender for Endpoint
description: Configurez les appareils autres que Windows afin qu’ils peuvent envoyer des données de capteur au service Microsoft Defender ATP.
keywords: intégrer des appareils non Windows, macos, linux, gestion des appareils, configurer des appareils Windows ATP, configurer Microsoft Defender pour les appareils Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c292c57c179a832728b03a7fc94fb7085d3ea0ec
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51166076"
---
# <a name="onboard-non-windows-devices"></a>Intégrer des appareils autres que Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-nonwindows-abovefoldlink) 

Defender pour le point de terminaison offre une expérience d’opérations de sécurité centralisée pour Windows, ainsi que pour les plateformes autres que Windows. Vous pourrez voir les alertes de différents systèmes d’exploitation pris en charge dans le Centre de sécurité Microsoft Defender et mieux protéger le réseau de votre organisation. 

Vous devez connaître les versions exactes de Linux et macOS compatibles avec Defender for Endpoint pour que l’intégration fonctionne. Pour plus d’informations, reportez-vous aux rubriques suivantes :
- [Microsoft Defender for Endpoint for Linux system requirements](microsoft-defender-endpoint-linux.md#system-requirements)  
- [Microsoft Defender pour endpoint pour Mac : système requis.](microsoft-defender-endpoint-mac.md#system-requirements)

## <a name="onboarding-non-windows-devices"></a>Intégration d’appareils autres que Windows
Pour intégrer des appareils autres que Windows, vous devez suivre les étapes suivantes :
1. Sélectionnez votre méthode d’intégration préférée :

   - Pour les appareils macOS, vous pouvez choisir d’intégrer via Microsoft Defender ATP ou via une solution tierce. Pour plus d’informations, [voir Microsoft Defender pour Endpoint pour Mac.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/microsoft-defender-atp-mac)
   - Pour les autres appareils non-Windows, choisissez Intégrer des appareils **non-Windows via une intégration tierce.**   
       
     1. Dans le volet de navigation, sélectionnez **Partenaires d’interopérabilité.**  >   Assurez-vous que la solution tierce est répertoriée.

        2. Dans **l’onglet Applications** partenaires, sélectionnez le partenaire qui prend en charge vos appareils autres que Windows.

        3. Sélectionnez **Ouvrir la page du partenaire** pour ouvrir la page du partenaire. Suivez les instructions fournies sur la page.

        4. Après avoir créé un compte ou vous être abonné à la solution partenaire, vous devez passer à une étape où un administrateur global client de votre organisation est invité à accepter une demande d’autorisation de l’application partenaire. Lisez attentivement la demande d’autorisation pour vous assurer qu’elle est alignée sur le service dont vous avez besoin. 

        
2. Exécutez un test de détection en suivant les instructions de la solution tierce.

## <a name="offboard-non-windows-devices"></a>Appareils non-Windows hors windows

1. Suivez la documentation du tiers pour déconnecter la solution tierce de Microsoft Defender for Endpoint.

2. Supprimez les autorisations pour la solution tierce dans votre client Azure AD.
   1. Connectez-vous au [portail Azure](https://portal.azure.com).
   2. Sélectionnez **Azure Active Directory > applications d’entreprise.**
   3. Sélectionnez l’application que vous souhaitez hors-carte.
   4. Sélectionnez **le bouton** Supprimer.


## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Serveurs intégrés](configure-server-endpoints.md)
- [Configurer les paramètres de proxy et de connectivité Internet](configure-proxy-internet.md)
- [Résolution des problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
