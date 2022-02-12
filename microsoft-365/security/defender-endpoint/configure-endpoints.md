---
title: Outils et méthodes d’intégration pour Windows appareils
description: Intégrer Windows appareils afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
keywords: Intégrer Windows, stratégie de groupe, gestionnaire de configuration de point de terminaison, gestion des appareils mobiles, script local, gp, sccm, mdm, intune
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
ms.openlocfilehash: c4b70bfa9875d1e8c09d21e9435d8b4200555b5c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62765599"
---
# <a name="onboarding-tools-and-methods-for-windows-devices-in-defender-for-endpoint"></a>Outils et méthodes d’intégration pour les Windows dans Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Protection contre la perte de données de point de terminaison (DLP) pour Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 risques internes](/microsoft-365/compliance/insider-risk-management)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les appareils de votre organisation doivent être configurés pour que le service Defender for Endpoint puisse obtenir des données de capteur de leur part. Il existe différentes méthodes et outils de déploiement que vous pouvez utiliser pour configurer les appareils de votre organisation.

En règle générale, vous identifiez l’appareil Windows que vous intégrerez, puis suivez l’outil correspondant approprié à l’appareil ou à votre environnement.

![Image des outils et méthodes d’intégration](images/onboarding-config-tools.png)

## <a name="endpoint-onboarding-tools"></a>Outils d’intégration de point de terminaison

Selon le point Windows que vous souhaitez intégrer, utilisez l’outil ou la méthode correspondant décrit dans le tableau suivant.

Windows appareil | Outil ou méthode d’intégration
:---|:---
|<ul><li> Windows 10</li> <li>Windows Server 1803 et 2019 et 2022</li> <li>Windows Server 2012 R2 et 2016<sup>[[1](#fn1)]<sup></li></ul>  |   [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md)<br>   [Stratégie de groupe](configure-endpoints-gp.md)<br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Microsoft Endpoint Manager/ Gestion des périphériques mobiles (Intune)](configure-endpoints-mdm.md)<br>    [Scripts VDI](configure-endpoints-vdi.md) <br><br> **REMARQUE** : un script local convient pour une preuve de concept, mais ne doit pas être utilisé pour le déploiement de production. Pour un déploiement de production, nous vous recommandons d’utiliser la stratégie de groupe, Microsoft Endpoint Configuration Manager ou Intune.
|<ul><li> Windows Server 2008 R2 SP1 </li></ul>| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br>[Intégrer les versions précédentes de Windows](onboard-downlevel.md) [ou Microsoft Defender pour le cloud](/azure/security-center/security-center-wdatp) <br><br> **REMARQUE** : Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
|<ul><li> Windows 7 SP1 </li> <li>  Windows 7 SP1 Pro </li> <li>  Windows 8.1 Professionnel </li> <li> Windows 8,1 Entreprise</li></ul>  | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **REMARQUE** : Microsoft Monitoring Agent est désormais l’agent Azure Log Analytics. Pour en savoir plus, consultez la vue [d’ensemble de l’agent Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).

(<a id="fn1">1</a>) les Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions des serveurs Windows [intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

>[!IMPORTANT]
>Pour pouvoir acheter Microsoft Defender pour Endpoint Server SKU, vous devez avoir déjà acheté un minimum combiné des licences d’abonnement suivantes, Windows E5/A5, Microsoft 365 E5/A5 ou Microsoft 365 E5 Sécurité.  Pour plus d’informations sur les licences, consultez les conditions [d’utilisation du produit](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).  

Rubrique|Description
:---|:---
[Intégrer des appareils à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)|Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Vous pouvez utiliser la version Microsoft Endpoint Manager (branche actuelle) 1606 ou la version 1602 de Microsoft Endpoint Manager (branche actuelle) ou une version antérieure pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide des outils de Gestion des appareils mobiles](configure-endpoints-mdm.md)|Utilisez les outils de Gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Intégrer des appareils en utilisant un script local](configure-endpoints-script.md)|Découvrez comment utiliser le script local pour déployer le package de configuration sur des points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)|Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)

Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).
