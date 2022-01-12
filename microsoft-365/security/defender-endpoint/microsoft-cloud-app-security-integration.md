---
title: Vue d’ensemble de l’intégration de Microsoft Defender for Cloud Apps
ms.reviewer: ''
description: Microsoft Defender pour le point de terminaison s’intègre à Defender pour les applications cloud en axant toutes les activités de mise en réseau des applications cloud.
keywords: cloud, application, réseau, visibilité, utilisation
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
ms.topic: conceptual
ms.date: 10/18/2018
ms.technology: mde
ms.openlocfilehash: d3cf5259aeb070175d5d2a4a95154974c6cd4d56
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61867821"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>Vue d’ensemble de Microsoft Defender for Cloud Apps in Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender pour les applications cloud est une solution complète qui offre une visibilité sur les applications et services cloud en vous permettant de contrôler et de limiter l’accès aux applications cloud, tout en appliquant des exigences de conformité sur les données stockées dans le cloud. Pour plus d’informations, [voir Defender pour les applications cloud.](/cloud-app-security/what-is-cloud-app-security)

> [!NOTE]
> Cette fonctionnalité est disponible avec [](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) une licence E5 pour les Enterprise Mobility + Security sur les appareils exécutant Windows 10 version 1809 ou ultérieure, ou Windows 11.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>Intégration de Microsoft Defender pour Endpoint et Defender pour les applications cloud

Defender for Cloud Apps discovery s’appuie sur les journaux de trafic cloud qui lui sont transmis à partir du pare-feu d’entreprise et des serveurs proxy. Microsoft Defender pour le point de terminaison s’intègre à Defender pour les applications cloud en collectant et en apportant toutes les activités de mise en réseau des applications cloud, offrant ainsi une visibilité accrue de l’utilisation des applications cloud. La fonctionnalité d’analyse est intégrée à l’appareil, fournissant une couverture complète de l’activité réseau.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

L’intégration apporte les améliorations majeures suivantes à la découverte de Defender for Cloud Apps existante :

- Disponible partout : étant donné que l’activité réseau est collectée directement à partir du point de terminaison, elle est disponible partout où l’appareil se trouve, sur ou en dehors du réseau d’entreprise, car il ne dépend plus du trafic acheminé via le pare-feu d’entreprise ou les serveurs proxy.

- Ne fonctionne pas, aucune configuration n’est requise : le transport des journaux de trafic cloud vers Defender pour les applications cloud nécessite une configuration de pare-feu et de serveur proxy. Avec l’intégration de Defender for Endpoint et Defender for Cloud Apps, aucune configuration n’est requise. Il vous suffit de l’Microsoft 365 Defender paramètres et vous êtes bon à aller.

- Contexte de périphérique : les journaux de trafic cloud n’ont pas de contexte de périphérique. L’activité réseau de Defender for Endpoint est signalée avec le contexte de périphérique (quel appareil a accédé à l’application cloud), afin que vous compreniez exactement où (appareil) l’activité réseau a eu lieu, en plus de qui (utilisateur) l’a effectuée.

Pour plus d’informations sur la découverte cloud, voir [Working with discovered apps](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’intégration de Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-config.md)
