---
title: Intégrer des appareils au service Microsoft Defender ATP
description: Intégrer des appareils Windows 10, des serveurs, des appareils autres que Windows et apprendre à exécuter un test de détection.
keywords: intégration, microsoft defender pour l’intégration de point de terminaison, intégration windows atp, sccm, stratégie de groupe, mdm, script local, test de détection
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1deb8a0e00785705937d4cf6de71a030d3d9c971
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061144"
---
# <a name="onboard-devices-to-the-microsoft-defender-for-endpoint-service"></a>Intégrer des appareils au service Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

Vous devez passer à la section d’intégration du portail Defender for Endpoint pour intégrer l’un des appareils pris en charge. En fonction de l’appareil, vous serez guidé avec les étapes appropriées et des options d’outils de gestion et de déploiement adaptées à l’appareil. 

En règle générale, pour intégrer des appareils au service :

- Vérifier que l’appareil remplit les [conditions minimales requises](minimum-requirements.md)
- En fonction de l’appareil, suivez les étapes de configuration fournies dans la section d’intégration du portail Defender for Endpoint
- Utiliser l’outil de gestion et la méthode de déploiement appropriés pour vos appareils
- Exécuter un test de détection pour vérifier que les appareils sont correctement intégrés et signaler au service

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4bGqr]

## <a name="onboarding-tool-options"></a>Options de l’outil d’intégration
Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison que vous devez intégrer.

| Point de terminaison     | Options de l’outil                       |
|--------------|------------------------------------------|
| **Windows**  |  [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Gestionnaire de point de terminaison Microsoft/ Gestionnaire d’appareils mobiles](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md)   |
| **MacOS**    | [Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](linux-install-manually.md) <br> [Sondent](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Basée sur l’application](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 




## <a name="in-this-section"></a>Dans cette section
Rubrique | Description
:---|:---
[Intégrer les versions précédentes de Windows](onboard-downlevel.md)| Intégrer des appareils Windows 7 et Windows 8.1 à Defender for Endpoint. 
[Intégrer des appareils Windows 10](configure-endpoints.md) | Vous devez intégrer des appareils pour qu’il signale au service Defender for Endpoint. Découvrez les outils et méthodes que vous pouvez utiliser pour configurer des appareils dans votre entreprise.
[Serveurs intégrés](configure-server-endpoints.md) |  Intégrer Windows Server 2008 R2 SP1, Windows Server 2012 R2, Windows Server 2016, Windows Server (SAC) version 1803 et ultérieure, Windows Server 2019 et versions ultérieures, et Windows Server 2019 core edition à Defender pour Endpoint.
[Intégrer des appareils autres que Windows](configure-endpoints-non-windows.md) | Defender pour le point de terminaison offre une expérience d’opérations de sécurité centralisée pour Windows, ainsi que pour les plateformes autres que Windows. Vous pourrez voir les alertes de différents systèmes d’exploitation pris en charge dans le Centre de sécurité Microsoft Defender et mieux protéger le réseau de votre organisation. Cette expérience tire parti des données de capteur d’un produit de sécurité tiers. 
[Exécuter un test de détection sur un appareil nouvellement intégré](run-detection-test.md) | Exécutez un script sur un appareil nouvellement intégré pour vérifier qu’il est correctement signalé au service Defender for Endpoint.
[Configurer les paramètres proxy et Internet](configure-proxy-internet.md)| Activez la communication avec le service cloud Defender for Endpoint en configurant les paramètres de proxy et de connectivité Internet.
[Résoudre les problèmes d’intégration](troubleshoot-onboarding.md) | Découvrez comment résoudre les problèmes qui peuvent survenir lors de l’intégration.

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
