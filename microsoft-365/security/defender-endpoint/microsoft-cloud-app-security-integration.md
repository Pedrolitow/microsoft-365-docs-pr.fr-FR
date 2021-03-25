---
title: Vue d’ensemble de l’intégration de Microsoft Cloud App Security
ms.reviewer: ''
description: Microsoft Defender pour le point de terminaison s’intègre à Cloud App Security en axant toutes les activités de mise en réseau des applications cloud.
keywords: cloud, application, réseau, visibilité, utilisation
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
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d756c738f9f61638a9e7424aa3fdf639f8f02f2a
ms.sourcegitcommit: 6f2288e0c863496dfd0ee38de754bd43096ab3e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51185598"
---
# <a name="microsoft-cloud-app-security-in-defender-for-endpoint-overview"></a>Vue d’ensemble de Microsoft Cloud App Security dans Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Cloud App Security (Cloud App Security) est une solution complète qui offre une visibilité sur les applications et services cloud en vous permettant de contrôler et de limiter l’accès aux applications cloud, tout en appliquant des exigences de conformité sur les données stockées dans le cloud. Pour plus d’informations, [voir Cloud App Security.](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)

>[!NOTE]
>Cette fonctionnalité est disponible avec une licence E5 pour [Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10 version 1809 ou ultérieure.

## <a name="microsoft-defender-for-endpoint-and-cloud-app-security-integration"></a>Intégration de Microsoft Defender pour Endpoint et Cloud App Security 

La découverte de Cloud App Security s’appuie sur les journaux de trafic cloud qui lui sont transmis à partir du pare-feu d’entreprise et des serveurs proxy. Microsoft Defender pour le point de terminaison s’intègre à Cloud App Security en collectant et en apportant toutes les activités de mise en réseau des applications cloud, offrant ainsi une visibilité renforcée de l’utilisation des applications cloud. La fonctionnalité d’analyse est intégrée à l’appareil, fournissant une couverture complète de l’activité réseau.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yQ]


L’intégration apporte les améliorations majeures suivantes à la découverte de Cloud App Security existante : 

- Disponible partout : étant donné que l’activité réseau est collectée directement à partir du point de terminaison, elle est disponible partout où l’appareil se trouve, sur ou en dehors du réseau d’entreprise, car il ne dépend plus du trafic acheminé via le pare-feu d’entreprise ou les serveurs proxy. 

- Ne fonctionne pas, aucune configuration n’est requise : le transport des journaux de trafic cloud vers Cloud App Security nécessite une configuration de pare-feu et de serveur proxy. Avec l’intégration de Defender for Endpoint et Cloud App Security, aucune configuration n’est requise. Il vous suffit de l’allumer dans les paramètres du Centre de sécurité Microsoft Defender et vous êtes en bonne santé. 

- Contexte de périphérique : les journaux de trafic cloud n’ont pas de contexte de périphérique. L’activité réseau de Defender for Endpoint est signalée avec le contexte de périphérique (quel appareil a accédé à l’application cloud), afin que vous compreniez exactement où (appareil) l’activité réseau a eu lieu, en plus de qui (utilisateur) l’a effectuée. 

Pour plus d’informations sur la découverte dans le cloud, voir [Working with discovered apps](https://docs.microsoft.com/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’intégration de Microsoft Cloud App Security](microsoft-cloud-app-security-config.md)
