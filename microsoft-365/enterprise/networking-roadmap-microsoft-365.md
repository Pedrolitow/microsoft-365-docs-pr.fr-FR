---
title: Feuille de route de mise en réseau pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/03/2022
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Feuille de route pour la planification, l’implémentation et la gestion de la mise en réseau Microsoft 365.
ms.openlocfilehash: f9c88e2f6e9181b39cfb35508b07e6b57da43b9d
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67695841"
---
# <a name="networking-roadmap-for-microsoft-365"></a>Feuille de route de mise en réseau pour Microsoft 365

Microsoft 365 entreprise inclut des services cloud de collaboration et de productivité, des Microsoft Intune et de nombreux services d’identité et de sécurité de Microsoft Azure. Tous ces services cloud s’appuient sur la sécurité, les performances et la fiabilité des connexions à partir d’appareils clients via Internet ou des circuits dédiés. Pour héberger ces services et les rendre accessibles aux clients dans le monde entier, Microsoft a conçu une infrastructure réseau qui met en évidence les performances et l’intégration.

Une partie essentielle de votre intégration à Microsoft 365 consiste à vous assurer que votre réseau et vos connexions Internet sont configurés pour un accès optimisé. La configuration de votre réseau local pour accéder à un cloud SaaS (Software as a Service) distribué à l’échelle mondiale est différente d’un réseau traditionnel optimisé pour le trafic vers des centres de données locaux et une connexion Internet centrale.

Utilisez ces articles pour comprendre les différences clés et modifier vos équipements de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances de la part de vos utilisateurs locaux.

## <a name="plan"></a>Planification

Dans la phase de planification de votre implémentation réseau :

- [Comprendre le fonctionnement de la mise en réseau Microsoft 365](microsoft-365-networking-overview.md)
- [En savoir plus sur les principes de connectivité réseau](microsoft-365-network-connectivity-principles.md)
- [Évaluer votre connectivité réseau actuelle](assessing-network-connectivity.md)
- [Déterminer si ExpressRoute convient à votre organisation](network-planning-with-expressroute.md)
- [Planifier vos appareils réseau](plan-for-network-devices.md)
- [Configurer votre réseau pour la migration](network-and-migration-planning.md)

## <a name="deploy"></a>Déployer

Dans la phase de déploiement de votre implémentation réseau :

- [Vérifier que votre réseau d’entreprise est optimisé pour la connectivité Microsoft 365](set-up-network-for-microsoft-365.md)
- [Ajouter les domaines DNS pour votre organisation](../admin/setup/add-domain.md)
- [Optimiser la connectivité pour les travailleurs distants à l’aide du tunneling fractionné VPN](microsoft-365-vpn-split-tunnel.md)
- [Configurer cdN pour améliorer les performances réseau](office-365-cdn-quickstart.md)
- [Optimiser votre connectivité aux points de terminaison Microsoft 365](microsoft-365-ip-web-service.md)
- Si nécessaire, [configurez ExpressRoute](azure-expressroute.md)

## <a name="manage"></a>Gestion

Dans la phase de gestion de votre implémentation réseau :

- [Tester et optimiser à l’aide de l’outil de test de connectivité réseau Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)
- [Vérifiez que vos appareils réseau utilisent les derniers points de terminaison Office 365](microsoft-365-endpoints.md)
- [Surveiller et optimiser les performances de votre réseau](network-planning-and-performance.md)
- [Surveiller votre connectivité Microsoft 365](monitor-connectivity.md)

## <a name="network-equipment-vendors"></a>Fournisseurs d’équipement réseau

Si vous êtes fournisseur d’équipement réseau, rejoignez le [Programme de partenariat réseau Microsoft 365](microsoft-365-networking-partner-program.md). Inscrivez-vous au programme pour créer des principes de connectivité réseau Microsoft 365 dans vos produits et solutions.

## <a name="how-contoso-did-networking-for-microsoft-365"></a>Comment Contoso a effectué la mise en réseau pour Microsoft 365

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a optimisé ses appareils réseau et ses connexions Internet](contoso-networking.md) pour les services cloud Microsoft 365.

![The Contoso Corporation.](../media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

Démarrez votre planification réseau avec la [vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md).
