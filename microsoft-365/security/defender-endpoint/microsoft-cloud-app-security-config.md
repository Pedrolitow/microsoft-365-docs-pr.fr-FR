---
title: Configurer l’intégration de Microsoft Cloud App Security
ms.reviewer: ''
description: Découvrez comment activer les paramètres pour activer l’intégration de Microsoft Defender for Endpoint à Microsoft Cloud App Security.
keywords: cloud, application, sécurité, paramètres, intégration, découverte, rapport
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
ms.openlocfilehash: f5e2919ae3fcbbb443f6d160c68633ee3427ae5a
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51187528"
---
# <a name="configure-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>Configurer Microsoft Cloud App Security dans Microsoft Defender pour endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Pour tirer parti des signaux de découverte d’application cloud Microsoft Defender for Endpoint, activer l’intégration de Microsoft Cloud App Security.

>[!NOTE]
>Cette fonctionnalité sera disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10, version 1709 (os Build 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (os build 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809 (os build 17763.379 avec [KB4489899)](https://support.microsoft.com/help/4489899)ou versions ultérieures de Windows 10.

> Consultez [l’intégration de Microsoft Defender for Endpoint avec Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/mde-integration) pour une intégration détaillée de Microsoft Defender for Endpoint avec Microsoft Cloud App Security. 

## <a name="enable-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>Activer Microsoft Cloud App Security dans Microsoft Defender pour le point de terminaison

1. Dans le volet de navigation, sélectionnez **Préférences configurer les**  >  **fonctionnalités avancées.**
2. Sélectionnez **Microsoft Cloud App Security et** basculez sur **Le.**
3. Cliquez **sur Enregistrer les préférences.**

Une fois activé, Microsoft Defender pour le point de terminaison démarre immédiatement le transmission des signaux de découverte vers Cloud App Security.

## <a name="view-the-data-collected"></a>Afficher les données collectées

Pour afficher et accéder aux données du point de terminaison Microsoft Defender dans Microsoft Cloud Apps Security, voir Examiner les appareils [dans Cloud App Security.](https://docs.microsoft.com/cloud-app-security/mde-integration#investigate-devices-in-cloud-app-security)


Pour plus d’informations sur la découverte dans le cloud, voir [Working with discovered apps](https://docs.microsoft.com/cloud-app-security/discovered-apps).

Si vous souhaitez essayer Microsoft Cloud App Security, consultez La version d’essai [de Microsoft Cloud App Security.](https://signup.microsoft.com/Signup?OfferId=757c4c34-d589-46e4-9579-120bba5c92ed&ali=1)

## <a name="related-topic"></a>Rubrique connexe
- [Intégration de Microsoft Cloud App Security](microsoft-cloud-app-security-integration.md)
