---
title: Vue d’ensemble de l’intégration de Microsoft Defender for Cloud Apps
ms.reviewer: ''
description: Microsoft Defender pour point de terminaison s’intègre à Defender pour Cloud Apps en transférant toutes les activités de mise en réseau d’applications cloud.
keywords: cloud, application, mise en réseau, visibilité, utilisation
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.openlocfilehash: b07c3ec5749aa7e7c7f23415f1f50521b9b507b3
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521464"
---
# <a name="microsoft-defender-for-cloud-apps-in-defender-for-endpoint-overview"></a>vue d’ensemble de Microsoft Defender for Cloud Apps dans Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender for Cloud Apps est une solution complète qui offre une visibilité sur les applications et services cloud en vous permettant de contrôler et de limiter l’accès aux applications cloud, tout en appliquant les exigences de conformité sur les données stockées dans le cloud. Pour plus d’informations, consultez [Defender pour Cloud Apps](/cloud-app-security/what-is-cloud-app-security).

> [!NOTE]
> Cette fonctionnalité est disponible avec une licence E5 pour [les Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security) sur les appareils exécutant Windows 10 version 1809 ou ultérieure, ou Windows 11.

## <a name="microsoft-defender-for-endpoint-and-defender-for-cloud-apps-integration"></a>intégration de Microsoft Defender pour point de terminaison et Defender pour Cloud Apps

La découverte de Defender pour Cloud Apps s’appuie sur les journaux de trafic cloud qui lui sont transférés à partir du pare-feu d’entreprise et des serveurs proxy. Microsoft Defender pour point de terminaison s’intègre à Defender pour Cloud Apps en collectant et en transférant toutes les activités de mise en réseau d’applications cloud, offrant une visibilité inégalée de l’utilisation des applications cloud. La fonctionnalité de surveillance est intégrée à l’appareil, fournissant une couverture complète de l’activité réseau.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4yQ]

L’intégration fournit les améliorations majeures suivantes à la découverte existante de Defender pour Cloud Apps :

- Disponible partout : étant donné que l’activité réseau est collectée directement à partir du point de terminaison, elle est disponible partout où l’appareil se trouve, sur ou hors du réseau d’entreprise, car il n’est plus dépendant du trafic acheminé via le pare-feu d’entreprise ou les serveurs proxy.

- Fonctionne correctement, aucune configuration n’est requise . Le transfert des journaux de trafic cloud vers Defender pour Cloud Apps nécessite une configuration de pare-feu et de serveur proxy. Avec l’intégration de Defender pour point de terminaison et Defender pour Cloud Apps, aucune configuration n’est requise. Il suffit de l’activer dans Microsoft 365 Defender paramètres et vous êtes bon pour aller.

- Contexte de l’appareil : les journaux du trafic cloud ne disposent pas du contexte de l’appareil. L’activité réseau de Defender pour point de terminaison est signalée avec le contexte de l’appareil (auquel l’appareil a accédé à l’application cloud). Vous pouvez donc comprendre exactement où (appareil) l’activité réseau a eu lieu, en plus de l’utilisateur qui l’a effectuée.

Pour plus d’informations sur la découverte du cloud, consultez [Utilisation des applications découvertes](/cloud-app-security/discovered-apps).

## <a name="related-topic"></a>Rubrique connexe

- [Configurer l’intégration de Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-config.md)
