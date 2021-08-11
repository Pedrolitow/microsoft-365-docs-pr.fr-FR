---
title: Feuille de route de mise en réseau pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 08/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Feuille de route pour l’implémentation de la mise en réseau Microsoft 365.
ms.openlocfilehash: 7c8c67305ef67e9e7a20b2d341f339b8bdbab4090426861e37b5b5277bb249e7
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53800980"
---
# <a name="networking-roadmap-for-microsoft-365"></a>Feuille de route de mise en réseau pour Microsoft 365

Microsoft 365 pour entreprise inclut des services cloud de collaboration et de productivité, Microsoft Intune et de nombreux services d’identité et de sécurité de Microsoft Azure. Tous ces services cloud s’appuient sur la sécurité, les performances et la fiabilité des connexions à partir d’appareils clients via Internet ou des circuits dédiés. Pour héberger ces services et les rendre accessibles aux clients dans le monde entier, Microsoft a conçu une infrastructure réseau qui met en évidence les performances et l’intégration. 

Une partie essentielle de votre intégration Microsoft 365 consiste à vous assurer que vos connexions réseau et Internet sont définies pour un accès optimisé. La configuration de votre réseau local pour accéder à un cloud SaaS (Software-as-a-Service) distribué globalement est différente d’un réseau traditionnel optimisé pour le trafic vers des centres de données locaux et une connexion Internet centrale. 

Utilisez ces articles pour comprendre les différences clés et modifier vos équipements de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances de la part de vos utilisateurs locaux.

## <a name="plan"></a>Planification

Dans la phase de planification de votre implémentation réseau :

- [Comprendre le fonctionnement de la mise en réseau Microsoft 365](microsoft-365-networking-overview.md)
- [Évaluer votre connectivité réseau actuelle](assessing-network-connectivity.md)
- [Déterminer si ExpressRoute est le bon pour votre organisation](network-planning-with-expressroute.md)
- [Planifier vos périphériques réseau](plan-for-network-devices.md)
- [Configurer votre réseau pour la migration](network-and-migration-planning.md)

## <a name="deploy"></a>Déployer

Dans la phase de déploiement de votre implémentation réseau :

- [Vérifier que votre réseau d’entreprise est optimisé pour la connectivité Microsoft 365](set-up-network-for-microsoft-365.md)
- [Ajouter les domaines DNS pour votre organisation](../admin/setup/add-domain.md)
- [Optimiser votre connectivité aux points de terminaison Microsoft 365](microsoft-365-ip-web-service.md)
- [Optimiser la connectivité pour les travailleurs à distance](microsoft-365-vpn-split-tunnel.md)
- Si nécessaire, [configurez ExpressRoute](azure-expressroute.md)

## <a name="manage"></a>Gestion

Dans la phase de gestion de votre implémentation réseau :

- [Assurez-vous que vos appareils réseau utilisent les derniers points de terminaison Office 365](microsoft-365-endpoints.md)
- [Surveiller et régler les performances de votre réseau](network-planning-and-performance.md)
- [Surveiller vos connexions ExpressRoute](managing-expressroute-for-connectivity.md)

## <a name="network-equipment-vendors"></a>Fournisseurs d’équipement réseau

Si vous êtes un fournisseur d’équipement réseau, rejoignez le programme partenaire réseau [Microsoft 365.](microsoft-365-networking-partner-program.md) Inscrivez-vous au programme pour créer des principes de connectivité réseau Microsoft 365 dans vos produits et solutions. 

## <a name="how-contoso-did-networking-for-microsoft-365"></a>Comment Contoso a fait la mise en réseau pour Microsoft 365

Découvrez comment Contoso Corporation, une entreprise multinationale fictive mais représentative, [a optimisé ses appareils réseau et ses connexions Internet](contoso-networking.md) pour les services cloud Microsoft 365.

![Société Contoso](../media/contoso-overview/contoso-icon.png)

## <a name="next-step"></a>Étape suivante

Démarrez la planification de votre réseau avec la vue d’ensemble de la connectivité réseau [Microsoft 365.](microsoft-365-networking-overview.md)