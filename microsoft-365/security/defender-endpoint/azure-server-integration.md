---
title: Intégration de à Microsoft Defender pour le cloud
description: En savoir plus sur l’intégration de Microsoft Defender pour point de terminaison à Microsoft Defender pour cloud
keywords: intégration, serveur, azure, 2012r2, 2016, 2019, intégration de serveur, gestion des appareils, configurer des serveurs Microsoft Defender pour point de terminaison, intégrer des serveurs Microsoft Defender pour point de terminaison, intégrer serveurs Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.service: microsoft-365-security
ms.subservice: mde
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: e0e01cbb2d565f6daab6570b723e491b1fc1e179
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67811744"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>Intégration de à Microsoft Defender pour le cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender pour le cloud

Microsoft Defender pour point de terminaison pouvez intégrer Microsoft Defender pour cloud pour fournir une solution complète de protection de serveur Windows. Avec cette intégration, Microsoft Defender pour cloud peut utiliser la puissance de Defender pour point de terminaison pour améliorer la détection des menaces pour les serveurs Windows.

Les fonctionnalités suivantes sont incluses dans cette intégration :

- Intégration automatisée : le capteur Defender pour point de terminaison est automatiquement activé sur les serveurs Windows intégrés à Microsoft Defender pour cloud. Pour plus d’informations sur l’intégration de Microsoft Defender pour le cloud, consultez [Utiliser la licence Microsoft Defender pour point de terminaison intégrée](/azure/security-center/security-center-wdatp).

    > [!NOTE]
    > L’intégration entre Microsoft Defender pour serveurs et Microsoft Defender pour point de terminaison a été développée pour prendre en charge [Windows Server 2019 et Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)

- Les serveurs Windows surveillés par Microsoft Defender pour cloud seront également disponibles dans Defender pour point de terminaison : Microsoft Defender pour Cloud se connecte en toute transparence au locataire Defender pour point de terminaison, en fournissant une vue unique entre les clients et les serveurs.  En outre, les alertes Defender pour point de terminaison seront disponibles dans la console Microsoft Defender pour le cloud.
- Investigation sur le serveur : les clients Microsoft Defender pour cloud peuvent accéder au portail Microsoft 365 Defender pour effectuer une investigation détaillée afin de découvrir l’étendue d’une violation potentielle.

> [!IMPORTANT]
> - Lorsque vous utilisez Microsoft Defender pour cloud pour surveiller les serveurs, un locataire Defender pour point de terminaison est automatiquement créé (aux États-Unis pour les utilisateurs américains, dans l’UE pour les utilisateurs européens et britanniques).<br>
Les données collectées par Defender pour point de terminaison sont stockées dans l’emplacement géographique du locataire, comme identifié lors de l’approvisionnement.
> - Si vous utilisez Defender pour point de terminaison avant d’utiliser Microsoft Defender pour cloud, vos données sont stockées à l’emplacement que vous avez spécifié lors de la création de votre locataire, même si vous intégrez Microsoft Defender pour Cloud ultérieurement.
> - Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Si vous devez déplacer vos données vers un autre emplacement, vous devez contacter Support Microsoft pour réinitialiser le locataire. <br>
La surveillance des points de terminaison de serveur utilisant cette intégration a été désactivée pour Office 365 clients GCC.



## <a name="related-topics"></a>Voir aussi
- [Intégrer des versions antérieures de Windows](onboard-downlevel.md)
- [Intégrer Windows Server 2012 R2, 2016, SAC version 1803 et 2019](configure-server-endpoints.md)
