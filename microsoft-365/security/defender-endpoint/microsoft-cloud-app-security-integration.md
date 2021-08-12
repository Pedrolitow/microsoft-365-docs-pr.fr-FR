---
title: Vue d’ensemble de l’intégration de Microsoft Cloud App Security
ms.reviewer: ''
description: Microsoft Defender pour le point de terminaison s’intègre à Sécurité des applications cloud en 100 % des activités de mise en réseau des applications cloud.
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
ms.openlocfilehash: 2e55070cfc8f5ee138f93ca7ae254655fabcdc9867ba3fd2056f9bbc35f3d099
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53800071"
---
# <a name="microsoft-cloud-app-security-in-defender-for-endpoint-overview"></a>Microsoft Cloud App Security vue d’ensemble de Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Cloud App Security (Sécurité des applications cloud) est une solution complète qui offre une visibilité sur les services et applications cloud en vous permettant de contrôler et de limiter l’accès aux applications cloud, tout en appliquant des exigences de conformité sur les données stockées dans le cloud. Pour plus d’informations, [voir Sécurité des applications cloud](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> Cette fonctionnalité est disponible avec [](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) une licence E5 Enterprise Mobility + Security sur les appareils exécutant Windows 10 version 1809 ou ultérieure.

## <a name="microsoft-defender-for-endpoint-and-cloud-app-security-integration"></a>Microsoft Defender pour l’intégration des points de terminaison et Sécurité des applications cloud’équipe

Sécurité des applications cloud découverte s’appuie sur les journaux de trafic cloud qui lui sont transmis à partir du pare-feu d’entreprise et des serveurs proxy. Microsoft Defender pour le point de terminaison s’intègre à Sécurité des applications cloud en collectant et en apportant toutes les activités de mise en réseau des applications cloud, offrant ainsi une visibilité accrue de l’utilisation des applications cloud. La fonctionnalité d’analyse est intégrée à l’appareil, fournissant une couverture complète de l’activité réseau.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

L’intégration apporte les améliorations majeures suivantes à la découverte Sécurité des applications cloud existante :

- Disponible partout : étant donné que l’activité réseau est collectée directement à partir du point de terminaison, elle est disponible partout où l’appareil se trouve, sur ou en dehors du réseau d’entreprise, car il ne dépend plus du trafic acheminé via le pare-feu d’entreprise ou les serveurs proxy.

- Ne fonctionne pas, aucune configuration n’est requise : le transport des journaux de trafic cloud vers Sécurité des applications cloud nécessite une configuration de pare-feu et de serveur proxy. Avec l’intégration de Defender for Endpoint Sécurité des applications cloud, aucune configuration n’est requise. Il vous suffit de l’Centre de sécurité Microsoft Defender paramètres et vous êtes en bonne santé.\

- Contexte de périphérique : les journaux de trafic cloud n’ont pas de contexte de périphérique. L’activité réseau de Defender for Endpoint est signalée avec le contexte de périphérique (quel appareil a accédé à l’application cloud), afin que vous compreniez exactement où (appareil) l’activité réseau a eu lieu, en plus de la personne (utilisateur) qui l’a effectuée.

Pour plus d’informations sur la découverte dans le cloud, voir [Working with discovered apps](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’intégration de Microsoft Cloud App Security.](microsoft-cloud-app-security-config.md)
