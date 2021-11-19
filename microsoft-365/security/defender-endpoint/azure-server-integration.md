---
title: Intégration à Microsoft Defender pour le cloud
description: En savoir plus sur l’intégration de Microsoft Defender for Endpoint à Microsoft Defender pour cloud
keywords: intégration, serveur, azure, 2012r2, 2016, 2019, intégration de serveur, gestion des appareils, configuration de Microsoft Defender pour les serveurs endpoint, intégration de Microsoft Defender pour les serveurs Endpoint, intégration de Microsoft Defender pour les serveurs Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 248b9aaf8affb3fc575b6624bef8cce18f14358d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61109850"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>Intégration à Microsoft Defender pour le cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour le cloud

Microsoft Defender pour le point de terminaison peut s’intégrer à Microsoft Defender pour le Cloud pour fournir une solution de protection Windows serveur complète. Avec cette intégration, Microsoft Defender pour le Cloud peut utiliser la puissance de Defender for Endpoint pour fournir une détection améliorée des menaces pour Windows serveurs.

Les fonctionnalités suivantes sont incluses dans cette intégration :

- Intégration automatisée : le capteur Defender for Endpoint est automatiquement activé sur les serveurs Windows intégrés à Microsoft Defender pour le Cloud. Pour plus d’informations sur l’intégration de Microsoft Defender pour le cloud, voir Utiliser la [licence Microsoft Defender pour point de terminaison intégrée.](/azure/security-center/security-center-wdatp)

    > [!NOTE]
    > L’intégration entre Microsoft Defender pour les serveurs et Microsoft Defender pour point de terminaison a été étendue pour prendre en charge [Windows Server 2019 et Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)

- Windows serveurs surveillés par Microsoft Defender pour le cloud seront également disponibles dans Defender pour le point de terminaison : Microsoft Defender pour le Cloud se connecte en toute transparence au client Defender pour Endpoint, fournissant une vue unique sur les clients et les serveurs.  En outre, les alertes defender pour point de terminaison seront disponibles dans la console Microsoft Defender pour le cloud.
- Enquête sur le serveur : les clients Microsoft Defender pour le Cloud peuvent accéder à Centre de sécurité Microsoft Defender pour effectuer une enquête détaillée afin de découvrir l’étendue d’une violation potentielle.

> [!IMPORTANT]
> - Lorsque vous utilisez Microsoft Defender pour le Cloud pour surveiller les serveurs, un client Defender pour endpoint est automatiquement créé (aux États-Unis pour les utilisateurs américains, dans l’UE pour les utilisateurs européens et anglais).<br>
Les données collectées par Defender pour le point de terminaison sont stockées dans l’emplacement géographique du client, comme identifié lors de l’approvisionnement.
> - Si vous utilisez Defender pour endpoint avant d’utiliser Microsoft Defender pour le cloud, vos données seront stockées à l’emplacement que vous avez spécifié lors de la création de votre client, même si vous intégrez Microsoft Defender pour le Cloud ultérieurement.
> - Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Si vous devez déplacer vos données vers un autre emplacement, vous devez contacter le Support Microsoft pour réinitialiser le client. <br>
La surveillance des points de terminaison de serveur utilisant cette intégration a été désactivée pour Office 365 Cloud de la communauté du secteur public clients.



## <a name="related-topics"></a>Sujets connexes
- [Intégrer des versions antérieures de Windows](onboard-downlevel.md)
- [Intégration Windows Server 2012 R2, 2016, SAC version 1803 et 2019](configure-server-endpoints.md)
