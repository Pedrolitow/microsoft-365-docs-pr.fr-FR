---
title: Configurer Microsoft Defender pour l’intégration des applications cloud
ms.reviewer: ''
description: Découvrez comment activer les paramètres pour activer l’intégration de Microsoft Defender for Endpoint avec Microsoft Defender pour les applications cloud.
keywords: cloud, application, sécurité, paramètres, intégration, découverte, rapport
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 88952a3f2c8173b20b8ee81322a0312144197ad5
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111602"
---
# <a name="configure-microsoft-defender-for-cloud-apps-in-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour les applications cloud dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pour tirer parti des signaux de découverte d’applications cloud Microsoft Defender pour endpoint, activer l’intégration de Microsoft Defender pour les applications cloud.

> [!NOTE]
> Cette fonctionnalité sera disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10, version 1709 (os build 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (os build 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809  (Os Build 17763.379 avec [KB4489899](https://support.microsoft.com/help/4489899)) ou version Windows 10 versions ultérieures.

> Consultez [Microsoft Defender pour l’intégration de point](/cloud-app-security/mde-integration) de terminaison avec Microsoft Defender pour les applications cloud pour une intégration détaillée de Microsoft Defender for Endpoint avec Microsoft Defender pour les applications cloud.

## <a name="enable-microsoft-defender-for-cloud-apps-in-microsoft-defender-for-endpoint"></a>Activer Microsoft Defender pour les applications cloud dans Microsoft Defender pour le point de terminaison

1. Dans le volet de navigation, sélectionnez **Préférences configurer les** \> **fonctionnalités avancées.**
2. Sélectionnez **Microsoft Defender pour les applications cloud** et basculez sur **Le.**
3. Cliquez **sur Enregistrer les préférences.**

Une fois activé, Microsoft Defender pour le point de terminaison commence immédiatement à forwardr les signaux de découverte vers Defender pour les applications cloud.

## <a name="view-the-data-collected"></a>Afficher les données collectées

Pour afficher et accéder aux données du point de terminaison Microsoft Defender dans Microsoft Cloud Apps Security, voir Examiner les appareils [dans Defender pour les applications cloud.](/cloud-app-security/mde-integration#investigate-devices-in-cloud-app-security)

Pour plus d’informations sur la découverte cloud, voir [Working with discovered apps](/cloud-app-security/discovered-apps).

Si vous souhaitez essayer Microsoft Defender pour les applications cloud, consultez La version d’essai [de Microsoft Defender pour les applications cloud.](https://signup.microsoft.com/Signup?OfferId=757c4c34-d589-46e4-9579-120bba5c92ed&ali=1)

## <a name="related-topic"></a>Rubrique connexe

- [Intégration de Microsoft Defender pour les applications cloud](microsoft-cloud-app-security-integration.md)
