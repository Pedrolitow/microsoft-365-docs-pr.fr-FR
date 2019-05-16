---
title: 'Étape 5 : Optimiser les performances du service Office 365 et du client'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/13/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Configurez les paramètres TCP et les services Office 365 pour de meilleures performances.
ms.openlocfilehash: 9e786b36d7a2afccc3b9112b815cd42a40317c15
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34073184"
---
# <a name="step-5-optimize-client-and-office-365-service-performance"></a>Étape 5 : Optimiser les performances du service Office 365 et du client

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

Vous pouvez accroître les performances en ajustant la façon dont le protocole TCP fonctionne entre les appareils clients et les services Office 365.

Pour les appareils clients, vous pouvez modifier les paramètres TCP suivants sur des appareils clients afin d’optimiser les performances TCP :

- [Mise à l’échelle des fenêtres TCP](https://blogs.technet.microsoft.com/onthewire/2014/03/28/ensuring-your-office-365-network-connection-isnt-throttled-by-your-proxy/), pour que votre appareil client puisse envoyer plus de données avant d’exiger un accusé de réception
- [Durée d’inactivité TCP](https://blogs.technet.microsoft.com/onthewire/2014/03/04/network-perimeters-tcp-idle-session-settings-for-outlook-on-office-365/), pour que votre appareil client puisse gérer les connexions ouvertes plus efficacement
- [Taille maximale de segment TCP](https://blogs.technet.microsoft.com/onthewire/2014/06/27/checking-your-tcp-packets-are-pulling-their-weight-tcp-max-segment-size-or-mss/), pour que votre appareil client puisse envoyer les blocs de données les plus volumineux dans un paquet
- [Accusés de réception sélectifs TCP](https://blogs.technet.microsoft.com/onthewire/2014/06/27/ensuring-your-tcp-stack-isnt-throwing-data-away/), pour que votre appareil client puisse accuser reçu des données plus efficacement

Pour les services Office 365, consultez ces ressources supplémentaires pour optimiser les performances :

- [Exchange Online](https://support.office.com/article/Tune-Exchange-Online-performance-026e83cb-a945-4543-97b0-a8af6e80ac61)
- [Skype Entreprise Online](https://support.office.com/article/Tune-Skype-for-Business-Online-performance-beec23c2-c5d6-4e84-a8af-e82aefca7802)
- [SharePoint Online](https://support.office.com/article/Tune-SharePoint-Online-performance-f0522d4a-fbf4-41f9-854e-c9b59555091d)
- [Project Online](https://support.office.com/article/Tune-Project-Online-performance-12ba0ebd-c616-42e5-b9b6-cad570e8409c)

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](networking-exit-criteria.md#crit-networking-step5) pour cette étape.

## <a name="next-step"></a>Étape suivante

[Critères de sortie de l’infrastructure réseau](networking-exit-criteria.md)
