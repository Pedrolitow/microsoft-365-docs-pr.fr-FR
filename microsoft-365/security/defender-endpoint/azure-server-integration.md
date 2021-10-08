---
title: Intégration à Azure Defender
description: En savoir plus sur l’intégration de Microsoft Defender pour Endpoint à Azure Defender
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
ms.openlocfilehash: a702585a558cf6754cbd2eaf23d5061879120ac8
ms.sourcegitcommit: be095345257225394674698beb3feeb0696ec86d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2021
ms.locfileid: "60240612"
---
# <a name="integration-with-azure-defender"></a>Intégration à Azure Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft Defender pour point de terminaison
- Azure Defender

Microsoft Defender pour point de terminaison peut s’intégrer à Azure Defender pour fournir une solution de protection Windows serveur complète. Avec cette intégration, Azure Defender peut utiliser la puissance de Defender for Endpoint pour fournir une détection améliorée des menaces pour Windows serveurs.

Les fonctionnalités suivantes sont incluses dans cette intégration :

- Intégration automatisée : le capteur Defender for Endpoint est automatiquement activé sur les serveurs Windows intégrés à Azure Defender. Pour plus d’informations sur l’intégration d’Azure Defender, voir Utiliser la [licence Microsoft Defender for Endpoint intégrée.](/azure/security-center/security-center-wdatp)

    > [!NOTE]
    > L’intégration entre Azure Defender pour serveurs et Microsoft Defender pour point de terminaison a été étendue pour prendre en charge [Windows Server 2019 et Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)

- Windows serveurs surveillés par Azure Defender seront également disponibles dans Defender pour le point de terminaison : Azure Defender se connecte en toute transparence au client Defender for Endpoint, fournissant une vue unique sur les clients et les serveurs.  En outre, les alertes Defender pour le point de terminaison seront disponibles dans la console Azure Defender.
- Enquête sur le serveur : les clients Azure Defender peuvent accéder Centre de sécurité Microsoft Defender pour effectuer une enquête détaillée afin de découvrir l’étendue d’une violation potentielle.

> [!IMPORTANT]
> - Lorsque vous utilisez Azure Defender pour surveiller les serveurs, un client Defender pour point de terminaison est automatiquement créé (aux États-Unis pour les utilisateurs américains, dans l’UE pour les utilisateurs européens et anglais).<br>
Les données collectées par Defender pour le point de terminaison sont stockées dans l’emplacement géographique du client, comme identifié lors de l’approvisionnement.
> - Si vous utilisez Defender pour endpoint avant d’utiliser Azure Defender, vos données seront stockées à l’emplacement spécifié lors de la création de votre client, même si vous intégrez Azure Defender ultérieurement.
> - Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Si vous devez déplacer vos données vers un autre emplacement, vous devez contacter le Support Microsoft pour réinitialiser le client. <br>
La surveillance des points de terminaison de serveur utilisant cette intégration a été désactivée pour Office 365 Cloud de la communauté du secteur public clients.



## <a name="related-topics"></a>Rubriques connexes
- [Intégrer des versions antérieures de Windows](onboard-downlevel.md)
- [Intégration Windows Server 2012 R2, 2016, SAC version 1803 et 2019](configure-server-endpoints.md)