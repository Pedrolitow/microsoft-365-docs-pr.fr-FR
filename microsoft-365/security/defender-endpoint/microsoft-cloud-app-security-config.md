---
title: Configurer l’intégration de Microsoft Cloud App Security.
ms.reviewer: ''
description: Découvrez comment activer les paramètres pour activer l’intégration de Microsoft Defender for Endpoint avec Microsoft Cloud App Security.
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
ms.openlocfilehash: 4f7aca5cb532510d55042c70d04d65f2aa08baa3
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52844753"
---
# <a name="configure-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>Configurer les Microsoft Cloud App Security dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)


Pour tirer parti des signaux de découverte d’application cloud Microsoft Defender for Endpoint, Microsoft Cloud App Security intégration.

>[!NOTE]
>Cette fonctionnalité sera disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10, version 1709 (os Build 16299.1085 avec [KB4493441](https://support.microsoft.com/help/4493441)), Windows 10, version 1803 (os build 17134.704 avec [KB4493464](https://support.microsoft.com/help/4493464)), Windows 10, version 1809 (os build 17763.379 avec [KB4489899)](https://support.microsoft.com/help/4489899)ou versions Windows 10 ultérieures.

> Consultez [l’intégration de Microsoft Defender for Endpoint Microsoft Cloud App Security](/cloud-app-security/mde-integration) pour une intégration détaillée de Microsoft Defender for Endpoint avec Microsoft Cloud App Security. 

## <a name="enable-microsoft-cloud-app-security-in-microsoft-defender-for-endpoint"></a>Activer Microsoft Cloud App Security dans Microsoft Defender pour le point de terminaison

1. Dans le volet de navigation, sélectionnez **Préférences configurer les**  >  **fonctionnalités avancées.**
2. Sélectionnez **Microsoft Cloud App Security** et basculez le bouton bascule sur **Sur**.
3. Cliquez **sur Enregistrer les préférences.**

Une fois activé, Microsoft Defender pour le point de terminaison démarre immédiatement le transmission des signaux de découverte Sécurité des applications cloud.

## <a name="view-the-data-collected"></a>Afficher les données collectées

Pour afficher et accéder aux données de point de terminaison Microsoft Defender dans Microsoft Cloud Apps Security, voir Examiner les appareils [dans Sécurité des applications cloud](/cloud-app-security/mde-integration#investigate-devices-in-cloud-app-security).


Pour plus d’informations sur la découverte dans le cloud, voir [Working with discovered apps](/cloud-app-security/discovered-apps).

Si vous souhaitez essayer d’Microsoft Cloud App Security, voir [Microsoft Cloud App Security Trial](https://signup.microsoft.com/Signup?OfferId=757c4c34-d589-46e4-9579-120bba5c92ed&ali=1).

## <a name="related-topic"></a>Rubrique connexe
- [Microsoft Cloud App Security’intégration](microsoft-cloud-app-security-integration.md)
