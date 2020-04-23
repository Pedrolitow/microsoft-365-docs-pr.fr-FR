---
title: 'Étape 5 : Optimiser les performances du service Microsoft 365 et du client'
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/23/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Configurez les paramètres TCP et les services Microsoft 365 pour de meilleures performances.
ms.openlocfilehash: 2db35f67ff19998b8a70742ec8fa24cb8d517c5d
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43631464"
---
# <a name="step-5-optimize-client-and-microsoft-365-service-performance"></a>Étape 5 : Optimiser les performances du service Microsoft 365 et du client

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![Phase 1 : Réseau](../media/deploy-foundation-infrastructure/networking_icon-small.png)

Vous pouvez accroître les performances en ajustant la façon dont le protocole TCP fonctionne entre les appareils clients et les services Microsoft 365.

Pour les appareils clients, vous pouvez modifier les paramètres TCP suivants sur des appareils clients afin d’optimiser les performances TCP :

- [Mise à l’échelle des fenêtres TCP](https://blogs.technet.microsoft.com/onthewire/2014/03/28/ensuring-your-office-365-network-connection-isnt-throttled-by-your-proxy/), pour que votre appareil client puisse envoyer plus de données avant d’exiger un accusé de réception
- [Durée d’inactivité TCP](https://blogs.technet.microsoft.com/onthewire/2014/03/04/network-perimeters-tcp-idle-session-settings-for-outlook-on-office-365/), pour que votre appareil client puisse gérer les connexions ouvertes plus efficacement
- [Taille maximale de segment TCP](https://blogs.technet.microsoft.com/onthewire/2014/06/27/checking-your-tcp-packets-are-pulling-their-weight-tcp-max-segment-size-or-mss/), pour que votre appareil client puisse envoyer les blocs de données les plus volumineux dans un paquet
- [Accusés de réception sélectifs TCP](https://blogs.technet.microsoft.com/onthewire/2014/06/27/ensuring-your-tcp-stack-isnt-throwing-data-away/), pour que votre appareil client puisse accuser reçu des données plus efficacement

Pour les services Microsoft 365, consultez ces ressources supplémentaires pour optimiser les performances :

- [Exchange Online](https://docs.microsoft.com/office365/enterprise/tune-exchange-online-performance)
- [Skype Entreprise Online](https://docs.microsoft.com/office365/enterprise/tune-skype-for-business-online-performance)
- [SharePoint Online](https://docs.microsoft.com/office365/enterprise/tune-sharepoint-online-performance)
- [Project Web App dans Project Online](https://docs.microsoft.com/ProjectOnline/tune-project-online-performance)

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](networking-exit-criteria.md#crit-networking-step5) pour cette étape.

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure réseau](networking-exit-criteria.md)
