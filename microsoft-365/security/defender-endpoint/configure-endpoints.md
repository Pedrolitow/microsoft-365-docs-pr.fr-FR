---
title: Outils et méthodes d’intégration pour les appareils Windows
description: Intégrer des appareils Windows afin qu’ils puissent envoyer des données de capteur au capteur Microsoft Defender pour point de terminaison
keywords: Intégrer des appareils Windows, stratégie de groupe, gestionnaire de configuration de point de terminaison, gestion des appareils mobiles, script local, gp, sccm, mdm, intune
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: fbc5a0981a6318d767252e968e45874d889aee85
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949098"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Outils et méthodes d’intégration pour les appareils Windows dans Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Protection contre la perte de données (DLP) de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Gestion des risques internes](/microsoft-365/compliance/insider-risk-management)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les appareils de votre organisation doivent être configurés pour que le service Defender pour point de terminaison puisse obtenir des données de capteur à partir de ces appareils. Vous pouvez utiliser différentes méthodes et outils de déploiement pour configurer les appareils de votre organisation.

En général, vous allez identifier l’appareil Windows que vous intègrez, puis suivre l’outil correspondant approprié à l’appareil ou à votre environnement.

:::image type="content" source="images/onboarding-config-tools.png" alt-text="Outils et méthodes d’intégration" lightbox="images/onboarding-config-tools.png":::

## <a name="endpoint-onboarding-tools"></a>Outils d’intégration de point de terminaison

Selon le point de terminaison Windows que vous souhaitez intégrer, utilisez l’outil ou la méthode correspondant décrit dans le tableau suivant.

appareil Windows | Outil ou méthode d’intégration
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 et 2019 et 2022</li> <li>Windows Server 2012 R2 et 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md)<br>   [Stratégie de groupe](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/Mobile Gestion des appareils (Intune)](configure-endpoints-mdm.md)<br>    [Scripts VDI](configure-endpoints-vdi.md) <br><br> **REMARQUE** : Un script local convient à une preuve de concept, mais ne doit pas être utilisé pour le déploiement en production. Pour un déploiement de production, nous vous recommandons d’utiliser stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Intégrer des versions antérieures de Windows](onboard-downlevel.md) ou [Microsoft Defender pour le cloud](/azure/security-center/security-center-wdatp) <br><br> **REMARQUE** : Microsoft Monitoring Agent est maintenant l’agent Azure Log Analytics. Pour en savoir plus, consultez [la vue d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 Pro SP1 </li> <li>  Windows 8.1 Professionnel </li> <li> Windows 8,1 Entreprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **REMARQUE** : Microsoft Monitoring Agent est maintenant l’agent Azure Log Analytics. Pour en savoir plus, consultez [la vue d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [Les serveurs de Windows d’intégration](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>Pour pouvoir acheter Microsoft Defender pour point de terminaison référence (SKU) Server, vous devez avoir déjà acheté un minimum combiné des éléments suivants, Windows E5/A5, Microsoft 365 E5/A5 ou Microsoft 365 E5 Sécurité licences d’abonnement.  Pour plus d’informations sur les licences, consultez les [termes du produit](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Rubrique|Description
:---|:---
[Intégrer des appareils à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)|Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Vous pouvez utiliser Microsoft Endpoint Manager (current branch) version 1606 ou Microsoft Endpoint Manager (current branch) version 1602 ou antérieure pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide des outils de Gestion des appareils mobiles](configure-endpoints-mdm.md)|Utilisez les outils de Gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Intégrer des appareils en utilisant un script local](configure-endpoints-script.md)|Découvrez comment utiliser le script local pour déployer le package de configuration sur des points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)|Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).
