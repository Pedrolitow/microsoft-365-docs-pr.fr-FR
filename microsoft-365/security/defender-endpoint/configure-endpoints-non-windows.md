---
title: Intégrer des appareils non Windows au service Microsoft Defender for Endpoint
description: Configurez les appareils non Windows afin qu’ils peuvent envoyer des données de capteur au service Microsoft Defender for Endpoint.
keywords: intégrer des appareils non Windows, macos, linux, gestion des appareils, configurer Microsoft Defender pour les appareils Endpoint
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
ms.openlocfilehash: 777f5f63c4739f277ec24f826bc8a61a226fb65f
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339669"
---
# <a name="onboard-non-windows-devices"></a>Intégrer des appareils non Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-nonwindows-abovefoldlink) 

Defender pour le point de terminaison offre une expérience d’opérations de sécurité centralisée pour les Windows et les plateformes non Windows réseau. Vous pourrez voir les alertes de différents systèmes d’exploitation pris en charge dans Microsoft 365 Defender et mieux protéger le réseau de votre organisation. 

Vous devez connaître les versions exactes de Linux et macOS compatibles avec Defender for Endpoint pour que l’intégration fonctionne. Pour plus d'informations, voir :
- [Microsoft Defender pour point de terminaison sur la demande système Linux](microsoft-defender-endpoint-linux.md#system-requirements)  
- [Microsoft Defender pour point de terminaison sur macOS system requirements](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Intégration d’appareils non Windows intégrés
Pour intégrer des appareils non Windows, vous devez suivre les étapes suivantes :
1. Sélectionnez votre méthode d’intégration préférée :

   - Pour les appareils macOS, vous pouvez choisir d’intégrer via Microsoft Defender pour Endpoint ou via une solution tierce. Pour plus d’informations, [voir Microsoft Defender pour Endpoint sur Mac.](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac)

   - Pour les autres appareils non Windows choisissez Intégrer des appareils non Windows par le biais **d’une intégration tierce.**   
    1. Dans le volet de navigation, sélectionnez **Partenaires d’interopérabilité.**  >   Assurez-vous que la solution tierce est répertoriée.
    2. Dans **l’onglet Applications** partenaires, sélectionnez le partenaire qui prend en charge vos appareils Windows non connectés.
    3. Sélectionnez **Ouvrir la page du partenaire** pour ouvrir la page du partenaire. Suivez les instructions fournies sur la page.
    4. Après avoir créé un compte ou vous être abonné à la solution partenaire, vous devez passer à une étape où un administrateur global client de votre organisation est invité à accepter une demande d’autorisation de l’application partenaire. Lisez attentivement la demande d’autorisation pour vous assurer qu’elle est alignée sur le service dont vous avez besoin. 

        
2. Exécutez un test de détection en suivant les instructions de la solution tierce.

## <a name="offboard-non-windows-devices"></a>Appareils non-Windows par carte

1. Suivez la documentation du tiers pour déconnecter la solution tierce de Microsoft Defender for Endpoint.

2. Supprimez les autorisations pour la solution tierce dans votre client Azure AD.
   1. Connectez-vous au [Portail Azure](https://portal.azure.com).
   2. Sélectionnez **Azure Active Directory > Enterprise applications.**
   3. Sélectionnez l’application que vous souhaitez horsboard.
   4. Sélectionnez **le bouton** Supprimer.


## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Serveurs intégrés](configure-server-endpoints.md)
- [Configurer les paramètres de proxy et de connectivité Internet](configure-proxy-internet.md)
- [Résolution des problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
