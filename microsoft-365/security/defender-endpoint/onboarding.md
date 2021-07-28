---
title: Intégrer au service Microsoft Defender pour point de terminaison
description: Découvrez comment intégrer des points de terminaison au service Microsoft Defender for Endpoint
keywords: microsoft defender pour le point de terminaison, intégrer, déployer
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
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 262b297976f0bc8155630e98406688fce050b8e2
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53623167"
---
# <a name="onboard-to-the-microsoft-defender-for-endpoint-service"></a>Intégrer au service Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Découvrez les différentes phases du déploiement de Microsoft Defender pour Endpoint et comment configurer les fonctionnalités au sein de la solution.

Le déploiement de Defender pour endpoint est un processus en trois phases :

|[![phase de déploiement : préparer](images/phase-diagrams/prepare.png)](prepare-deployment.md) <br> [Phase 1 : préparation](prepare-deployment.md)|[![phase de déploiement : configuration](images/phase-diagrams/setup.png)](production-deployment.md) <br> [Phase 2 : configuration](production-deployment.md)|![phase de déploiement : intégration](images/phase-diagrams/onboard.png) <br> Phase 3 : intégration|
|---|---|---|
|||*Vous êtes là !*|

Vous êtes actuellement en phase d’intégration.

Voici les étapes à suivre pour déployer Defender pour Endpoint :

- Étape 1 : Intégrer des points de terminaison au service
- Étape 2 : Configurer les fonctionnalités

## <a name="step-1-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 1 : Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge

La [rubrique Planifier le](deployment-strategy.md) déploiement décrit les étapes générales à suivre pour déployer Defender pour Endpoint.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du processus d’intégration et en savoir plus sur les outils et méthodes disponibles.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Après avoir identifié votre architecture, vous devez choisir la méthode de déploiement à utiliser. L’outil de déploiement que vous choisissez influence la façon dont vous intégrerez les points de terminaison au service.

### <a name="onboarding-tool-options"></a>Options de l’outil d’intégration

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison que vous devez intégrer.

|Point de terminaison|Options de l’outil|
|---|---|
|**Windows**|[Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration à Azure Defender](configure-server-endpoints.md#integration-with-azure-defender)|
|**MacOS**|[Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JamF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md)|
|**Serveur Linux**|[Script local](linux-install-manually.md) <br> [Sondent](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Basée sur l’application](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-2-configure-capabilities"></a>Étape 2 : Configurer les fonctionnalités

Après avoir intégré les points de terminaison, vous allez configurer les différentes fonctionnalités telles que protection évolutive des points de terminaison, la protection nouvelle génération et la réduction de la surface d’attaque.

## <a name="example-deployments"></a>Exemples de déploiements

Dans ce guide de déploiement, nous allons vous guider tout au long de l’utilisation de deux outils de déploiement pour intégrer des points de terminaison et configurer des fonctionnalités.

Les outils de l’exemple de déploiement sont les :

- [Intégration à l'aide de Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Intégration à l'aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

À l’aide des outils de déploiement mentionnés ci-dessus, vous serez guidé dans la configuration des fonctionnalités defender pour point de terminaison suivantes :

- Détection de point de terminaison et configuration de la réponse
- Configuration de la protection nouvelle génération
- Configuration de la réduction de la surface d’attaque

## <a name="related-topics"></a>Voir aussi

- [Intégration à l'aide de Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Intégration à l'aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
- [Documents sécurisés dans Microsoft 365 E5](../office-365-security/safe-docs.md)
