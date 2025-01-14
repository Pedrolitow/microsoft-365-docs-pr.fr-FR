---
title: Client Windows d’intégration de Defender pour point de terminaison
description: Intégrer le client Windows.
keywords: intégration, Microsoft Defender pour point de terminaison intégration, sccm, stratégie de groupe, mdm, script local, test de détection
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 4cce49d70b9700b34a676ec2c08feea64d518aa0
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68224005"
---
# <a name="defender-for-endpoint-onboarding-windows-client"></a>Client Windows d’intégration de Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Protection contre la perte de données (DLP) de point de terminaison](/microsoft-365/compliance/endpoint-dlp-learn-about)
- [Gestion des risques internes](/microsoft-365/compliance/insider-risk-management)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https:%2F%2Faka.ms%2FMDEp2OpenTrial)

Vous devez parcourir la section d’intégration du portail Defender pour point de terminaison pour intégrer l’un des appareils pris en charge. Selon l’appareil, vous serez guidé avec les étapes appropriées et les options d’outils de gestion et de déploiement fournies pour l’appareil.

Les appareils de votre organisation doivent être configurés pour que le service Defender pour point de terminaison puisse obtenir des données de capteur à partir de ces appareils. Vous pouvez utiliser différentes méthodes et outils de déploiement pour configurer les appareils de votre organisation.

En général, vous allez identifier le client que vous insérez, puis suivre l’outil correspondant approprié à l’appareil ou à votre environnement.

:::image type="content" source="images/onboarddevices.png" alt-text="Intégrer des appareils" lightbox="images/onboarddevices.png":::

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows à l’aide de Microsoft Intune](configure-endpoints-mdm.md)
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer les appareils Windows utilisant un script local](configure-endpoints-script.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)