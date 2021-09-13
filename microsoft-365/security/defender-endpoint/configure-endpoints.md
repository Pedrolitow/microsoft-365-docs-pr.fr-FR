---
title: Outils et méthodes d’intégration pour les appareils Windows 10.
description: Intégrer Windows 10 appareils afin qu’ils peuvent envoyer des données de capteur au capteur Microsoft Defender for Endpoint
keywords: Intégrer Windows 10 appareils, stratégie de groupe, gestionnaire de configuration de point de terminaison, gestion des appareils mobiles, script local, gp, sccm, mdm, intune
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
ms.openlocfilehash: eb71cc8ee014c1e96f4e57fb58785e0c15b4602a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59222607"
---
# <a name="onboarding-tools-and-methods-for-windows-10-devices-in-defender-for-endpoint"></a>Outils et méthodes d’intégration pour Windows 10 dans Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Microsoft 365 Gestion des risques internes](/microsoft-365/compliance/insider-risk-management)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les appareils de votre organisation doivent être configurés pour que le service Defender for Endpoint puisse obtenir des données de capteur de leur part. Il existe différentes méthodes et outils de déploiement que vous pouvez utiliser pour configurer les appareils de votre organisation.

Les méthodes et outils de déploiement suivants sont pris en charge :


Rubrique|Description
:---|:---
[Intégrer des appareils à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)|Utilisez la stratégie de groupe pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)|Vous pouvez utiliser la version Microsoft Endpoint Manager (branche actuelle) 1606 ou la version 1602 de Microsoft Endpoint Manager (branche actuelle) ou une version antérieure pour déployer le package de configuration sur les appareils.
[Intégrer des appareils à l’aide des outils de Gestion des appareils mobiles](configure-endpoints-mdm.md)|Utilisez les outils de gestion des appareils mobiles ou Microsoft Intune pour déployer le package de configuration sur l’appareil.
[Intégrer des appareils en utilisant un script local](configure-endpoints-script.md)|Découvrez comment utiliser le script local pour déployer le package de configuration sur les points de terminaison.
[Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)|Découvrez comment utiliser le package de configuration pour configurer des appareils VDI.

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpoints-belowfoldlink)


Après avoir intégré l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, voir Exécuter un test de détection sur un appareil [Microsoft Defender pour point de terminaison nouvellement intégré.](run-detection-test.md)