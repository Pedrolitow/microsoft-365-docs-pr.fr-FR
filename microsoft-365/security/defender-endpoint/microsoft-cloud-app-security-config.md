---
title: Configurer l’intégration de Microsoft Defender for Cloud Apps
ms.reviewer: ''
description: Découvrez comment activer les paramètres pour activer l’intégration Microsoft Defender pour point de terminaison à Microsoft Defender for Cloud Apps.
keywords: cloud, application, sécurité, paramètres, intégration, découverte, rapport
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 5eab2e32e777c214ff2d56372badf5acafac033c
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232977"
---
# <a name="configure-microsoft-defender-for-cloud-apps-in-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender for Cloud Apps dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Pour tirer parti de Microsoft Defender pour point de terminaison signaux de découverte d’applications cloud, activez l’intégration Microsoft Defender for Cloud Apps.

> [!NOTE]
> Cette fonctionnalité sera disponible avec une licence E5 pour [les Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10 et Windows 11.

> [!TIP]
> Consultez [Microsoft Defender pour point de terminaison intégration avec Microsoft Defender for Cloud Apps](/cloud-app-security/mde-integration) pour une intégration détaillée de Microsoft Defender pour point de terminaison avec Microsoft Defender for Cloud Apps.

## <a name="enable-microsoft-defender-for-cloud-apps-in-microsoft-defender-for-endpoint"></a>Activer Microsoft Defender for Cloud Apps dans Microsoft Defender pour point de terminaison

1. Dans le volet de navigation, sélectionnez **Préférences pour configurer** \> **les fonctionnalités avancées**.
2. Sélectionnez **Microsoft Defender for Cloud Apps** et activez le bouton **bascule.**
3. Cliquez sur **Enregistrer les préférences**.

Une fois activé, Microsoft Defender pour point de terminaison commence immédiatement à transférer les signaux de découverte à Defender pour Cloud Apps.

## <a name="view-the-data-collected"></a>Afficher les données collectées

Pour afficher et accéder aux données Microsoft Defender pour point de terminaison dans Microsoft Cloud Apps Security, consultez [Examiner les appareils dans Defender pour Cloud Apps](/cloud-app-security/mde-integration#investigate-devices-in-cloud-app-security).

Pour plus d’informations sur la découverte du cloud, consultez [Utilisation des applications découvertes](/cloud-app-security/discovered-apps).

Si vous souhaitez essayer Microsoft Defender for Cloud Apps, consultez [Microsoft Defender for Cloud Apps Version d’évaluation](https://signup.microsoft.com/Signup?OfferId=757c4c34-d589-46e4-9579-120bba5c92ed&ali=1).

## <a name="related-topic"></a>Rubrique connexe

- [intégration Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-integration.md)
