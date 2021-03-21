---
title: Optimisation des performances globales du client Microsoft 365 pour les utilisateurs chinois
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Cet article fournit des conseils pour optimiser les performances réseau pour les utilisateurs chinois des clients Microsoft 365 globaux.
ms.openlocfilehash: 2ba0509425b60aec35d29b23b84e3b6346d2f5cb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50923193"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Optimisation des performances globales du client Microsoft 365 pour les utilisateurs chinois

>[!IMPORTANT]
>Ces conseils sont spécifiques aux scénarios d’utilisation dans lesquels les utilisateurs **d’entreprise Microsoft 365** situés en Chine se connectent à un client **Microsoft 365 global.** Ces instructions ne **s’appliquent** pas aux locataires d’Office 365 géré par 21Vianet.

Pour les entreprises ayant des clients Microsoft 365 globaux et une présence d’entreprise en Chine, les performances des clients Microsoft 365 pour les utilisateurs basés en Chine peuvent être compliquées par des facteurs propres à l’architecture Internet de China Telco.

Les fournisseurs de services Internet chinois ont des connexions réglementées à internet public mondial qui traversent des périphériques de périmètre qui sont sujets à des niveaux élevés de congestion du réseau 2- frontière. Cette congestion crée une perte de paquets et une latence pour tout le trafic Internet en entrée et en sortie de chine.

![Trafic Microsoft 365 - non optimale](../media/O365-networking/China-O365-unoptimized.png)

La perte de paquets et la latence sont néfastes pour les performances des services réseau, en particulier les services qui nécessitent des échanges de données importants (tels que des transferts de fichiers importants) ou nécessitant des performances quasiment en temps réel (applications audio et vidéo).

L’objectif de cette rubrique est de fournir les meilleures pratiques pour atténuer l’impact de la congestion du réseau frontière chinois sur les services Microsoft 365. Cette rubrique ne permet pas de résoudre d’autres problèmes courants de performances au dernier kilomètre, tels que les problèmes de latence élevée des paquets en raison d’un routage complexe au sein des opérateurs chinois.

## <a name="corporate-network-best-practices"></a>Meilleures pratiques en matière de réseau d’entreprise

De nombreuses entreprises ayant des clients et des utilisateurs Microsoft 365 globaux en Chine ont implémenté des réseaux privés qui transportent le trafic réseau d’entreprise entre des bureaux en Chine et des emplacements géographiques dans le monde entier. Ces entreprises peuvent tirer parti de cette infrastructure réseau pour éviter la congestion du réseau 2-ème et optimiser les performances de leurs services Microsoft 365 en Chine.

>[!IMPORTANT]
>Comme pour toutes les implémentations de réseau wan privé, vous devez toujours consulter les exigences réglementaires pour votre pays et/ou région afin de vous assurer que votre configuration réseau est conforme.

Dans un premier temps, il est essentiel de suivre nos recommandations réseau de référence sur la planification réseau et l’optimisation des performances [pour Microsoft 365.](./network-planning-and-performance.md) L’objectif principal doit être d’éviter d’accéder aux services Microsoft 365 globaux à partir d’Internet en Chine si possible.

- Tirez parti de votre réseau privé existant pour transporter le trafic réseau Microsoft 365 entre les réseaux de bureaux chinois et les emplacements géographiques qui sont en sortie sur Internet public en dehors de la Chine. Presque n’importe quel emplacement en dehors de la Chine sera clairement avantageux. Les administrateurs réseau peuvent optimiser davantage en dégressant dans les zones où la latence faible est interconnectée avec [le réseau global Microsoft.](/azure/networking/microsoft-global-network) Hong Kong, le Japon et la Corée du Sud sont des exemples.
- Configurez les appareils utilisateur pour accéder au réseau d’entreprise sur une connexion VPN pour permettre au trafic Microsoft 365 de transiter par le lien privé privé du réseau d’entreprise. Assurez-vous que les clients VPN ne sont pas configurés pour utiliser la tunnellation fractionnée ou que les appareils utilisateur sont configurés pour ignorer la tunnellation fractionnée pour le trafic Microsoft 365.
- Configurez votre réseau pour router tout le trafic Microsoft 365 sur votre lien privé privé. Si vous devez réduire le volume de trafic sur votre lien privé, vous pouvez choisir  de  router uniquement les points de terminaison dans la catégorie Optimiser et d’autoriser les demandes aux points de terminaison Autoriser et Par défaut transiter par Internet.  Cela permet d’améliorer les performances et de réduire la consommation de bande passante en limitant le trafic optimisé aux services critiques les plus sensibles à la latence élevée et à la perte de paquets.
- Si possible, utilisez UDP au lieu de TCP pour le trafic de diffusion multimédia en direct, par exemple pour Teams. UDP offre de meilleures performances de diffusion multimédia en direct que TCP.

Pour plus d’informations sur l’itinéraire sélectif du trafic Microsoft 365, voir Gestion des points de terminaison [Office 365.](managing-office-365-endpoints.md) Pour obtenir la liste de toutes les URL et adresses IP Office 365 dans le monde, voir URL et [plages d’adresses IP Office 365.](urls-and-ip-address-ranges.md)

![Trafic Microsoft 365 optimisé](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Meilleures pratiques de l’utilisateur

Les utilisateurs en Chine qui se connectent à des clients Microsoft 365 globaux à partir d’emplacements distants tels que des domiciles, des café, des magasins de succursales et des magasins de succursales sans connexion aux réseaux d’entreprise peuvent avoir des performances réseau médiocres, car le trafic entre leurs appareils et Microsoft 365 doit transiter par les circuits réseau nationaux saturés en Chine.

Si les réseaux privés nationaux et/ou l’accès VPN au réseau d’entreprise ne sont pas une option, les problèmes de performances par utilisateur peuvent toujours être atténués en formation de vos utilisateurs basés en Chine pour qu’ils suivent ces meilleures pratiques.

- Utilisez des clients Office enrichis qui assurent la prise en charge de la mise en cache (par exemple, Outlook, Teams, OneDrive, etc.) et évitez les clients web. Les fonctionnalités de mise en cache du client Office et d’accès hors connexion peuvent considérablement réduire l’impact de la congestion et de la latence du réseau.
- Si votre client Microsoft 365 a été configuré avec la fonctionnalité _d’audioconférence,_ les utilisateurs de Teams peuvent participer à des réunions via le réseau téléphonique commuté (PSTN). Pour plus d’informations, [voir Audioconférence dans Office 365.](/microsoftteams/audio-conferencing-in-office-365)
- Si les utilisateurs font face à des problèmes de performances réseau, ils doivent signaler à leur service informatique la résolution des problèmes et faire une escalade vers le support Microsoft si des problèmes avec les services Microsoft 365 sont suspectés. Tous les problèmes ne sont pas dus aux performances du réseau frontal.

Microsoft s’efforce continuellement d’améliorer l’expérience utilisateur de Microsoft 365 et les performances des clients sur le plus large éventail possible d’architectures et de caractéristiques réseau. Visitez la [communauté technique Office 365](https://techcommunity.microsoft.com/t5/office-365/bd-p/Office365General) pour démarrer ou rejoindre une conversation, rechercher des ressources et soumettre des suggestions et des demandes de fonctionnalités.

## <a name="related-topics"></a>Rubriques connexes

[Planification réseau et optimisation des performances pour Microsoft 365](./network-planning-and-performance.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)