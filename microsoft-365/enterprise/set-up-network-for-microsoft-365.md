---
title: Configurer votre réseau pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Trouvez des liens vers des articles avec des informations pour vous aider à configurer votre réseau pour Microsoft 365, notamment une vue d’ensemble de la connectivité réseau et la liste des points de terminaison.
ms.openlocfilehash: 0608fed03721a12d89fdac7d9bdd1574e34471b0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213228"
---
# <a name="set-up-your-network-for-microsoft-365"></a>Configurer votre réseau pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Une partie importante de votre intégration Microsoft 365 consiste à vous assurer que vos connexions réseau et Internet sont définies pour un accès optimisé. La configuration de votre réseau local pour accéder à un cloud SaaS (Software-as-a-Service) distribué globalement est différente d’un réseau traditionnel optimisé pour le trafic vers des centres de données locaux et une connexion Internet centrale. 

Utilisez ces articles pour comprendre les différences clés et modifier vos équipements de périmètre, ordinateurs clients et réseau local pour obtenir les meilleures performances de la part de vos utilisateurs locaux.

## <a name="how-microsoft-365-networking-works"></a>Fonctionnement Microsoft 365 réseau

Consultez les articles suivants pour obtenir une vue d’ensemble de la connectivité Microsoft 365 :

- [Vue d’ensemble de la connectivité réseau Microsoft 365](microsoft-365-networking-overview.md)
- [Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)
- [Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

Pour obtenir des conseils sur l’amélioration des performances, voir Planification réseau et optimisation des [performances pour Microsoft 365](network-planning-and-performance.md).

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a>Prise en charge Microsoft 365 réseau en tant que fournisseur d’équipement réseau

Si vous êtes un fournisseur d’équipement réseau, rejoignez le[programme de partenariat mise en réseau d’Office 365](microsoft-365-networking-partner-program.md). Inscrivez-vous au programme pour développer les principes de connectivité réseau Office 365 dans vos produits et solutions. 

## <a name="office-365-endpoints"></a>Points de terminaison Office 365

Les points de terminaison sont l’ensemble des adresses IP de destination, noms de domaine DNS et URL pour le trafic sur Internet Office 365. 

Pour optimiser les performances aux services Office 365 basés sur le cloud, certains points de terminaison nécessitent une gestion spéciale par les autres navigateurs client et les appareils dans votre réseau de périmètre. Ces appareils incluent pare-feux, SSL Break and Inspect et des appareils d’inspection des paquets, et systèmes de protection contre la perte de données.

Voir [Gestion des points de terminaison d’Office 365 ](managing-office-365-endpoints.md) pour plus d’informations.

Il existe actuellement cinq différents clouds Office 365. Ce tableau vous permet d’accéder à la liste des points de terminaison pour chacun d’eux.

| Points de terminaison | Description |
|:-------|:-----|
| [Points de terminaison internationaux](urls-and-ip-address-ranges.md) | Les points de terminaison pour les abonnements Office 365 dans le monde, dont le États-Unis Government Community Cloud (GCC). |
| [Points de terminaison DoD du gouvernement américain](microsoft-365-u-s-government-dod-endpoints.md) | Les points de terminaison pour les abonnements aux États-Unis Department of Defense (DoD). |
| [Points de terminaison GCC High du gouvernement américain](microsoft-365-u-s-government-gcc-high-endpoints.md) | Les points de terminaison pour les abonnements aux États-Unis pour le secteur public Communauté Cloud élevé (GCC élevé). |
| [Office 365 géré par les points de terminaison 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Les points de terminaison pour Office 365 géré par 21Vianet, qui est conçu pour répondre aux besoins d’Office 365 en Chine. |
| [Points de terminaison Office 365 Germany](microsoft-365-germany-endpoints.md) | Les points de terminaison pour un cloud en Europe distinct, pour les clients plus régulés en Allemagne, Union européenne (UE) et l’Association européenne de libre-échange (AELE). |
|||

Pour automatiser l’obtention de la dernière liste des points de terminaison pour votre cloud Office 365, voir [Service web d’URL et d’adresses IP Office 365](microsoft-365-ip-web-service.md).

Pour plus de points de terminaison, voir les articles suivants :

- [Autres points de terminaison supplémentaires non inclus dans les services web](additional-office365-ip-addresses-and-urls.md)
- [Requêtes réseau dans Office 2016 pour Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a>Rubriques supplémentaires pour la mise Microsoft 365 réseau

Consultez ces articles pour des rubriques spécialisées sur Microsoft 365 réseau :

- [Réseaux de distribution de contenu](content-delivery-networks.md)
- [Prise en charge du protocole IPv6 dans les services Office 365](ipv6-support.md)
- [Prise en charge de la traduction d’adresses réseau (NAT) avec Office 365](nat-support-with-microsoft-365.md)

## <a name="expressroute-for-microsoft-365"></a>ExpressRoute pour Microsoft 365

Consultez les articles suivants pour plus d’informations sur l’utilisation d’ExpressRoute pour le trafic Office 365 :

- [Azure ExpressRoute pour Office 365](azure-expressroute.md)
- [Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
- [Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
- [Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
