---
title: Planifier le déploiement de Microsoft Defender pour point de terminaison
description: Sélectionnez la meilleure stratégie de déploiement de Microsoft Defender pour les points de terminaison pour votre environnement
keywords: déployer, planifier, stratégie de déploiement, cloud natif, gestion, sur site, évaluation, intégration, local, stratégie de groupe, gp, gestionnaire de point de terminaison, mem
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
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cfdbb84cfcc2cda08572709adb3b13db83e319fa
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62766463"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planifier le déploiement de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Planifiez votre déploiement de Microsoft Defender for Endpoint afin d’optimiser les fonctionnalités de sécurité de la suite et de mieux protéger votre entreprise contre les cybermenaces.

Cette solution fournit des conseils sur l’identification de l’architecture de votre environnement, la sélection du type d’outil de déploiement qui répond le mieux à vos besoins et des instructions sur la configuration des fonctionnalités.

![Image du flux de déploiement.](images/deployment-guide-plan.png)

## <a name="step-1-identify-architecture"></a>Étape 1 : identifier l’architecture

Comme nous savons que chaque environnement d’entreprise est unique, nous avons fourni plusieurs options pour vous offrir la flexibilité nécessaire pour choisir le déploiement du service.

Selon votre environnement, certains outils conviennent mieux à certaines architectures.

Utilisez les documents suivants pour sélectionner l’architecture defender pour point de terminaison appropriée qui convient le mieux à votre organisation.

| Item | Description |
|:-----|:-----|
|[![Image miniature de la stratégie de déploiement de Defender for Endpoint.](images/mde-deployment-strategy.png)](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)  \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) | Le matériel architectural vous aide à planifier votre déploiement pour les architectures suivantes : <ul><li> Cloud-natif </li><li> Cogestion </li><li> Sur site</li><li>Évaluation et intégration locale</li>

## <a name="step-2-select-deployment-method"></a>Étape 2 : sélectionner la méthode de déploiement

| Point de terminaison     | Outil de déploiement                       |
|--------------|------------------------------------------|
| **Fenêtres**  |  [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-azure-defender)  |
| **MacOS**    | [Script local](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](linux-install-manually.md) <br> [Sondent](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 

Le tableau suivant répertorie les points de terminaison pris en charge et l’outil de déploiement correspondant que vous pouvez utiliser pour planifier le déploiement de manière appropriée.

|Point de terminaison|Outil de déploiement|
|---|---|
|**Fenêtres**|[Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-azure-defender)|
|**MacOS**|[Script local](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md)|
|**Serveur Linux**|[Script local](linux-install-manually.md) <br> [Sondent](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Basée sur l’application](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Étape 3 : Configurer les fonctionnalités

Après l’intégration des points de terminaison, configurez les fonctionnalités de sécurité dans Defender pour le point de terminaison afin que vous pouvez optimiser la protection de sécurité robuste disponible dans la suite. Les fonctionnalités incluent :

- Détection et réponse du point de terminaison
- Protection de nouvelle génération
- Réduction de la surface d'attaque

## <a name="related-topics"></a>Voir aussi

- [Phases de déploiement](deployment-phases.md)
