---
title: Microsoft 365 optimisation des performances globales des clients pour les utilisateurs chinois
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/17/2020
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
description: Cet article fournit des conseils pour optimiser les performances réseau pour les utilisateurs chinois Microsoft 365 clients.
ms.openlocfilehash: 36ae5bf08cfb529c7c6a23b5b3c1a8e17c73f412a0de196296b14226d5ec88a8
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53864321"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 optimisation des performances globales des clients pour les utilisateurs chinois

> [!IMPORTANT]
> Ces conseils sont spécifiques aux scénarios d’utilisation dans lesquels les utilisateurs **Microsoft 365** entreprise situés en Chine se connectent à un **client Microsoft 365 global.** Ces instructions ne **s’appliquent** pas aux locataires Office 365 gérés par 21Vianet.

Pour les entreprises avec des clients Microsoft 365 globaux et une présence d’entreprise en Chine, les performances du client Microsoft 365 pour les utilisateurs basés en Chine peuvent être compliquées par des facteurs propres à l’architecture Internet de China Telco.

Les fournisseurs de services Internet chinois ont des connexions réglementées à internet public mondial qui traversent des périphériques de périmètre qui sont sujets à des niveaux élevés de congestion du réseau erréglementé. Cette congestion crée une perte de paquets et une latence pour tout le trafic Internet en entrée et en sortie de chine.

![Microsoft 365 trafic non optimale](../media/O365-networking/China-O365-unoptimized.png)

La perte de paquets et la latence sont néfastes pour les performances des services réseau, en particulier les services qui nécessitent des échanges de données importants (tels que des transferts de fichiers importants) ou nécessitant des performances quasiment en temps réel (applications audio et vidéo).

L’objectif de cette rubrique est de fournir les meilleures pratiques pour atténuer l’impact de la congestion du réseau frontière chinois sur Microsoft 365 services. Cette rubrique ne permet pas de résoudre d’autres problèmes courants de performances au dernier kilomètre, tels que les problèmes de latence élevée des paquets en raison d’un routage complexe au sein des opérateurs chinois.

## <a name="corporate-network-best-practices"></a>Meilleures pratiques en matière de réseau d’entreprise

De nombreuses entreprises nationaux Microsoft 365 clients et utilisateurs en Chine ont implémenté des réseaux privés qui transportent le trafic réseau d’entreprise entre des bureaux en Chine et des emplacements géographiques dans le monde entier. Ces entreprises peuvent tirer parti de cette infrastructure réseau pour éviter la congestion du réseau err er et optimiser leurs performances Microsoft 365 service en Chine.

> [!IMPORTANT]
> Comme avec toutes les implémentations de réseau wan privé, vous devez toujours consulter les exigences réglementaires pour votre pays et/ou région afin de vous assurer que votre configuration réseau est conforme.

Dans un premier temps, il est essentiel de suivre nos recommandations réseau de référence sur la planification réseau et l’optimisation des performances [pour Microsoft 365](./network-planning-and-performance.md). L’objectif principal doit être d’éviter d’accéder aux services de Microsoft 365 globaux à partir d’Internet en Chine si possible.

- Tirez parti de votre réseau privé existant pour transporter Microsoft 365 trafic réseau entre les réseaux de bureaux chinois et les emplacements géographiques qui sont en sortie sur Internet public en dehors de la Chine. Presque n’importe quel emplacement en dehors de la Chine sera clairement avantageux. Les administrateurs réseau peuvent optimiser davantage en dégressant dans les zones où la latence faible est interconnectée avec [le réseau global Microsoft.](/azure/networking/microsoft-global-network) Hong Kong, le Japon et la Corée du Sud sont des exemples.
- Configurez les appareils utilisateur pour accéder au réseau d’entreprise sur une connexion VPN pour autoriser le trafic Microsoft 365 transiter par le lien privé privé du réseau d’entreprise. Assurez-vous que les clients VPN ne sont pas configurés pour utiliser la tunnellation fractionnée ou que les appareils utilisateur sont configurés pour ignorer la tunnellation fractionnée pour Microsoft 365 trafic. Pour plus d’informations sur l’optimisation de la connectivité VPN pour Teams trafic multimédia en temps réel et en temps réel, consultez [cette section.](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china)
- Configurez votre réseau pour router tout le trafic Microsoft 365 sur votre lien privé privé. Si vous devez réduire le volume de trafic sur votre lien privé, vous pouvez choisir  de  router uniquement les points de terminaison dans la catégorie Optimiser et d’autoriser les demandes de points de terminaison Autoriser et Par défaut à transiter sur Internet.  Cela permet d’améliorer les performances et de réduire la consommation de bande passante en limitant le trafic optimisé aux services critiques les plus sensibles à la latence élevée et à la perte de paquets.
- Si possible, utilisez UDP au lieu de TCP pour le trafic de diffusion multimédia en direct, par exemple pour Teams. UDP offre de meilleures performances de diffusion multimédia en direct que TCP.

Pour plus d’informations sur l’itinéraire Microsoft 365 de manière sélective, voir [Managing Office 365 endpoints](managing-office-365-endpoints.md). Pour obtenir la liste de toutes les URL Office 365 et adresses IP dans le monde entier, voir Office 365 [URL et plages d’adresses IP.](urls-and-ip-address-ranges.md)

![Microsoft 365 trafic : optimisé](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Meilleures pratiques de l’utilisateur

En Chine, les utilisateurs qui se connectent à des clients Microsoft 365 globaux à partir d’emplacements distants tels que des domiciles, des café, des magasins de magasins et des succursales sans connexion aux réseaux d’entreprise peuvent avoir des performances réseau médiocres, car le trafic entre leurs appareils et Microsoft 365 doit transiter par les circuits réseau nationaux saturés.

Si les réseaux privés nationaux et/ou l’accès VPN au réseau d’entreprise ne sont pas une option, les problèmes de performances par utilisateur peuvent toujours être atténués en formation de vos utilisateurs basés en Chine pour qu’ils suivent ces meilleures pratiques.

- Utilisez des clients Office riches qui assurent la prise en charge de la mise en cache (par exemple, Outlook, Teams, OneDrive, etc.) et évitez les clients web. Office la mise en cache du client et les fonctionnalités d’accès hors connexion peuvent considérablement réduire l’impact de la congestion et de la latence du réseau.
- Si votre client Microsoft 365 a été configuré avec la fonctionnalité _d’audioconférence,_ les utilisateurs Teams peuvent participer à des réunions via le réseau téléphonique commuté (PSTN). Pour plus d’informations, [voir l’audioconférence dans Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Si les utilisateurs font face à des problèmes de performances réseau, ils doivent signaler à leur service informatique la résolution des problèmes et faire une escalade vers le support Microsoft si des problèmes avec les services Microsoft 365 sont suspectés. Tous les problèmes ne sont pas dus aux performances du réseau frontal.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optimisation des performances Microsoft Teams réseau des réunions pour les utilisateurs en Chine

Pour les organisations avec des clients Microsoft 365 internationaux et une présence en Chine, les performances des clients Microsoft 365 pour les utilisateurs basés en Chine peuvent être compliquées par des facteurs propres à l’architecture Internet en Chine. De nombreuses entreprises et écoles ont signalé de bons résultats en suivant ces instructions. Toutefois, l’étendue est limitée aux emplacements réseau des utilisateurs qui sont sous le contrôle de la configuration de la mise en réseau informatique, par exemple, les emplacements de bureau ou les points de terminaison famille/mobile avec connectivité VPN. Microsoft Teams appels et réunions sont souvent utilisés à partir d’emplacements externes, tels que des bureaux à domicile, des emplacements mobiles, sur la route et des café. Étant donné que les appels et les réunions dépendent du trafic multimédia en temps réel, ces Teams expériences sont particulièrement sensibles à la congestion du réseau.

Par conséquent, Microsoft s’est associé à des fournisseurs de télécommunications pour transporter du trafic multimédia en temps réel Teams et Skype Entreprise Online à l’aide d’un chemin réseau de qualité supérieure et durable entre les connexions Internet publiques et nationales en Chine et les services Teams et Skype dans le cloud global Microsoft 365. Cette fonctionnalité a permis d’améliorer plus de dix fois la perte de paquets et d’autres mesures clés qui ont un impact sur l’expérience de votre utilisateur.

>[!IMPORTANT]
>Actuellement, ces améliorations ne s’adressent pas aux réunions Microsoft Live Events telles que les grandes réunions de type diffusion ou « salle de réunion » à l’aide de Teams ou Microsoft Stream. Pour afficher une réunion Live Events, les utilisateurs en Chine doivent utiliser un réseau privé ou une solution SDWAN/VPN. Toutefois, les améliorations apportées au réseau seront bénéfiques aux utilisateurs qui présentent ou produisent une réunion Live Events, car cette expérience fait office de réunion Teams régulière pour le producteur ou le présentateur.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Meilleures pratiques en matière de réseau d’organisation Teams réunions

Vous devez réfléchir à la façon de tirer parti de ces améliorations réseau, étant donné que les instructions précédentes pour envisager une extension de réseau privé afin d’éviter la congestion du réseau entre les frontières. Il existe deux options générales pour les réseaux Office de l’organisation :

1. Ne rien faire de nouveau. Continuez à suivre les instructions précédentes concernant la déviation du réseau privé afin d’éviter la congestion croisée. Teams trafic multimédia en temps réel tirera parti de cette configuration, comme auparavant.
2. Implémenter un modèle partagé/hybride.
   - Utilisez les instructions précédentes pour tout le trafic marqué pour l’optimisation, à l’exception Teams réunions et l’appel du trafic multimédia en temps réel.
   - Routez Teams réunion et appelez le trafic multimédia en temps réel sur Internet public. Consultez les informations suivantes pour plus d’informations sur l’identification du trafic réseau multimédia en temps réel.

L’envoi d’un trafic audio et vidéo multimédia en temps réel sur Internet public, qui utilise une connectivité de qualité supérieure, peut entraîner des économies considérable, car il est gratuit ou payant d’envoyer ce trafic sur un réseau privé. Teams Il peut y avoir des avantages supplémentaires similaires si les utilisateurs utilisent également des clients SDWAN ou VPN. En règle générale, certaines organisations préfèrent que davantage de données traversent des connexions Internet publiques.

Les mêmes options peuvent s’appliquer aux configurations SDWAN ou VPN. Par exemple, un utilisateur utilise un SDWAN ou un VPN pour router le trafic Microsoft 365 vers le réseau d’entreprise, puis tire parti de l’extension privée de ce réseau pour éviter une congestion croisée. Le réseau SDWAN ou VPN de l’utilisateur peut désormais être configuré pour exclure Teams réunion et appeler le trafic en temps réel du routage VPN. Cette configuration VPN est appelée tunneling fractionnel. Pour plus [d’informations, voir tunneling](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) vpn Office 365'informations.

Vous pouvez également continuer à utiliser votre SDWAN ou VPN pour tout le trafic Microsoft 365, y compris pour Microsoft Teams trafic en temps réel. Microsoft n’a aucune recommandation sur l’utilisation de solutions SDWAN ou VPN.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Meilleures pratiques en matière de réseau d’accueil, de mobilité et d’utilisateur pour Teams réunions

Les utilisateurs en Chine peuvent tirer parti de ces améliorations simplement en se connectant au service Internet public en Chine avec une connexion fixe ou mobile. Teams trafic audio et vidéo multimédia en temps réel sur Internet public bénéficie directement de l’amélioration de la connectivité et de la qualité.

Toutefois, les données provenant d’autres services Microsoft 365 et d’autres trafics dans Teams, tels que les conversation ou les fichiers, ne bénéficieront pas directement de ces améliorations. Les utilisateurs en dehors du réseau de l’organisation peuvent encore faire l’expérience de mauvaises performances réseau pour ce trafic. Comme indiqué dans cet article, vous pouvez atténuer ces effets à l’aide d’un VPN ou de SDWAN. Vos utilisateurs peuvent également utiliser des clients de bureau enrichis sur des clients web, qui la prise en charge de la mise en cache dans l’application pour atténuer les problèmes réseau.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identification du Teams réseau multimédia en temps réel

Pour configurer un périphérique réseau ou une configuration VPN/SDWAN, vous devez exclure uniquement le trafic audio et vidéo Teams multimédia en temps réel. Les détails du trafic se trouvent pour l’ID 11 dans la liste officielle des URL Office 365 et des [plages d’adresses IP.](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams) Toutes les autres configurations réseau doivent rester telles quel.

Microsoft s’efforce continuellement d’améliorer Microsoft 365 l’expérience utilisateur et les performances des clients sur le plus large éventail possible d’architectures et de caractéristiques réseau. Visitez la Office 365 de mise en [réseau](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) Community pour démarrer ou rejoindre une conversation, rechercher des ressources et soumettre des suggestions et des demandes de fonctionnalités

## <a name="related-topics"></a>Sujets connexes

[Planification réseau et optimisation des performances pour Microsoft 365](./network-planning-and-performance.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
