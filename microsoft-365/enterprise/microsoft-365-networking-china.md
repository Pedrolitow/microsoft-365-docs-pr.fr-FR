---
title: Microsoft 365 optimisation globale des performances des locataires pour les utilisateurs chinois
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Cet article fournit des conseils pour optimiser les performances réseau pour les utilisateurs chinois de locataires Microsoft 365 globaux.
ms.openlocfilehash: f7e4e69277a252fd1af52559d3bc4360fd3cfd51
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637866"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 optimisation globale des performances des locataires pour les utilisateurs chinois

> [!IMPORTANT]
> Ces conseils sont spécifiques aux scénarios d’utilisation dans lesquels les **utilisateurs Microsoft 365 d’entreprise situés en Chine** se connectent à un **locataire Microsoft 365 mondial**. Ces instructions ne s’appliquent **pas** aux locataires dans Office 365 exploités par 21Vianet.

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent de l’optimisation Microsoft 365 pour les utilisateurs distants.

>- Pour obtenir une vue d’ensemble de l’utilisation du tunneling fractionné VPN pour optimiser Microsoft 365 connectivité pour les utilisateurs distants, consultez [Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des instructions détaillées sur l’implémentation du tunneling fractionné VPN, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionné [VPN, consultez les scénarios de tunneling fractionné VPN courants pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des conseils sur la sécurisation Teams trafic multimédia dans les environnements de tunneling fractionné VPN, consultez [Sécurisation Teams trafic multimédia pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration des événements stream et en direct dans les environnements VPN, consultez [considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).

Pour les entreprises disposant de locataires Microsoft 365 mondiaux et d’une présence d’entreprise en Chine, Microsoft 365 performances client pour les utilisateurs basés en Chine peut être compliquée par des facteurs propres à l’architecture Internet de China Telco.

Les FAI chinois ont réglementé les connexions offshore à l’Internet public mondial qui passent par des dispositifs périphériques sujets à des niveaux élevés de congestion du réseau transfrontalier. Cette congestion crée une perte de paquets et une latence pour tout le trafic Internet entrant et sortant de Chine.

![Microsoft 365 trafic non optimal.](../media/O365-networking/China-O365-unoptimized.png)

La perte et la latence des paquets sont préjudiciables aux performances des services réseau, en particulier les services qui nécessitent des échanges de données volumineux (tels que les transferts de fichiers volumineux) ou qui nécessitent des performances quasiment en temps réel (applications audio et vidéo).

L’objectif de cette rubrique est de fournir des meilleures pratiques pour atténuer l’impact de la congestion du réseau transfrontalier en Chine sur les services Microsoft 365. Cette rubrique ne traite pas d’autres problèmes courants de performances du dernier kilomètre, tels que les problèmes de latence élevée des paquets en raison d’un routage complexe au sein des transporteurs chinois.

## <a name="corporate-network-best-practices"></a>Meilleures pratiques en matière de réseau d’entreprise

De nombreuses entreprises ayant des locataires et des utilisateurs Microsoft 365 mondiaux en Chine ont implémenté des réseaux privés qui transportent le trafic réseau d’entreprise entre des bureaux en Chine et des emplacements offshore dans le monde entier. Ces entreprises peuvent tirer parti de cette infrastructure réseau pour éviter la congestion du réseau transfrontalier et optimiser leurs performances de service Microsoft 365 en Chine.

> [!IMPORTANT]
> Comme pour toutes les implémentations de wan privé, vous devez toujours consulter les exigences réglementaires de votre pays et/ou région pour vous assurer que votre configuration réseau est conforme.

Dans un premier temps, il est essentiel de suivre nos conseils de référence en matière de [planification réseau et d’optimisation des performances pour Microsoft 365](./network-planning-and-performance.md). L’objectif principal devrait être d’éviter d’accéder aux services Microsoft 365 mondiaux à partir d’Internet en Chine si possible.

- Tirez parti de votre réseau privé existant pour acheminer le trafic réseau Microsoft 365 entre les réseaux des bureaux en Chine et les sites offshore qui sortent sur l’Internet public en dehors de la Chine. Presque n’importe quel endroit en dehors de la Chine offrira un avantage évident. Les administrateurs réseau peuvent optimiser davantage en sortant dans des zones avec une faible latence d’interconnexion avec le [réseau mondial Microsoft](/azure/networking/microsoft-global-network). Hong Kong, Singapour, le Japon et la Corée du Sud en sont des exemples.
- Configurez les appareils utilisateur pour accéder au réseau d’entreprise via une connexion VPN afin de permettre au trafic Microsoft 365 de transiter par la liaison offshore privée du réseau d’entreprise. Assurez-vous que les clients VPN ne sont pas configurés pour utiliser le tunneling fractionné ou que les machines utilisateur sont configurées pour ignorer le tunneling fractionné pour le trafic Microsoft 365. Pour plus d’informations sur l’optimisation de la connectivité VPN pour Teams et le trafic multimédia en temps réel, consultez [cette section](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Configurez votre réseau pour acheminer tout le trafic Microsoft 365 via votre lien offshore privé. Si vous devez réduire le volume de trafic sur votre liaison privée, vous pouvez choisir de router uniquement les points de terminaison dans la catégorie **Optimiser** et d’autoriser les demandes **d’autorisation** et de points de terminaison **par défaut** pour transiter par Internet. Cela améliore les performances et réduit la consommation de bande passante en limitant le trafic optimisé vers les services critiques qui sont les plus sensibles à la latence élevée et à la perte de paquets.
- Si possible, utilisez UDP au lieu de TCP pour le trafic de diffusion multimédia en direct, comme pour Teams. UDP offre de meilleures performances de streaming multimédia en direct que TCP.

Pour plus d’informations sur la façon de router de manière sélective Microsoft 365 trafic, consultez [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md). Pour obtenir la liste de toutes les URL et adresses IP Office 365 dans le monde entier, consultez [Office 365 URL et plages d’adresses IP](urls-and-ip-address-ranges.md).

![Microsoft 365 le trafic - optimisé.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Meilleures pratiques de l’utilisateur

Les utilisateurs en Chine qui se connectent à des locataires Microsoft 365 mondiaux à partir d’emplacements distants tels que des maisons, des cafés, des hôtels et des succursales sans connexion aux réseaux d’entreprise peuvent rencontrer des performances réseau médiocres, car le trafic entre leurs appareils et les Microsoft 365 doivent transiter par les circuits réseau transfrontaliers ingérés de la Chine.

Si les réseaux privés transfrontaliers et/ou l’accès VPN au réseau d’entreprise ne sont pas une option, les problèmes de performances par utilisateur peuvent toujours être atténués en formant vos utilisateurs basés en Chine à suivre ces bonnes pratiques.

- Utilisez des clients Office riches qui prennent en charge la mise en cache (par exemple, Outlook, Teams, OneDrive, etc.) et évitez les clients web. Office fonctionnalités de mise en cache des clients et d’accès hors connexion peuvent réduire considérablement l’impact de la congestion et de la latence du réseau.
- Si votre locataire Microsoft 365 a été configuré avec la fonctionnalité _de Audioconférence_, Teams utilisateurs peuvent participer à des réunions via le réseau téléphonique commuté (RTC). Pour plus d’informations, consultez [Audioconférence dans Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Si les utilisateurs rencontrent des problèmes de performances réseau, ils doivent signaler les problèmes à leur service informatique et les signaler au support Microsoft si des problèmes liés à Microsoft 365 services sont suspectés. Tous les problèmes ne sont pas dus aux performances du réseau transfrontalier.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optimisation des performances réseau des réunions Microsoft Teams pour les utilisateurs en Chine

Pour les organisations disposant de locataires Microsoft 365 mondiaux et d’une présence en Chine, Microsoft 365 performances client pour les utilisateurs basés en Chine peut être compliquée par des facteurs propres à l’architecture Internet en Chine. De nombreuses entreprises et établissements scolaires ont fait état de bons résultats en suivant ces conseils. Toutefois, l’étendue est limitée aux emplacements réseau des utilisateurs qui sont sous le contrôle de la configuration de la mise en réseau informatique, par exemple, les emplacements de bureau ou les points de terminaison d’accueil/mobiles avec connectivité VPN. Microsoft Teams appels et réunions sont souvent utilisés à partir d’emplacements externes, tels que des bureaux à domicile, des lieux mobiles, sur la route et des cafés. Étant donné que les appels et les réunions reposent sur le trafic multimédia en temps réel, ces Teams expériences sont particulièrement sensibles à la congestion du réseau.

Par conséquent, Microsoft s’est associé à des fournisseurs de télécommunications pour transporter Teams et Skype Entreprise trafic multimédia en temps réel en ligne à l’aide d’un chemin de réseau préférentiel de meilleure qualité entre les connexions Internet nationales et publiques en Chine et les services Teams et Skype dans le cloud Microsoft 365 mondial. Cette fonctionnalité a entraîné une amélioration plus de dix fois plus importante de la perte de paquets et d’autres métriques clés qui ont un impact sur l’expérience de votre utilisateur.

>[!IMPORTANT]
>Actuellement, ces améliorations ne concernent pas la participation à des réunions d’événements en direct Microsoft, telles que les grandes réunions de type diffusion ou « town hall » à l’aide de Teams ou de Microsoft Stream. Les améliorations du réseau bénéficieront aux utilisateurs qui présentent ou produisent une réunion Événements en direct, car cette expérience fait office de réunion Teams régulière pour le producteur ou le présentateur.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Meilleures pratiques relatives au réseau de l’organisation pour les réunions Teams

Vous devez réfléchir à la façon de tirer parti de ces améliorations du réseau, étant donné que les conseils précédents pour envisager une extension de réseau privé afin d’éviter la congestion du réseau transfrontalier. Il existe deux options générales pour les réseaux de bureaux de l’organisation :

1. Ne rien faire de nouveau. Continuez à suivre les instructions antérieures concernant la déviation du réseau privé pour éviter la congestion transfrontalière. Teams trafic multimédia en temps réel tirera parti de cette configuration, comme auparavant.
2. Implémentez un modèle de fractionnement/hybride.
   - Utilisez les instructions précédentes pour tout le trafic signalé pour l’optimisation, à l’exception des réunions Teams et de l’appel du trafic multimédia en temps réel.
   - Routez Teams réunion et appelez le trafic multimédia en temps réel sur l’Internet public. Pour plus d’informations sur l’identification du trafic réseau multimédia en temps réel, consultez les informations suivantes.

L’envoi Teams trafic audio et vidéo multimédia en temps réel sur l’Internet public, qui utilise une connectivité de qualité supérieure, peut entraîner des économies considérables, car il est gratuit ou payant d’envoyer ce trafic sur un réseau privé. Il peut y avoir des avantages supplémentaires similaires si les utilisateurs utilisent également des clients SDWAN ou VPN. Certaines organisations peuvent également préférer que davantage de leurs données transitent par des connexions Internet publiques en général.

Les mêmes options peuvent s’appliquer aux configurations SDWAN ou VPN. Par exemple, un utilisateur utilise un SDWAN ou un VPN pour acheminer Microsoft 365 trafic vers le réseau d’entreprise, puis en tirant parti de l’extension privée de ce réseau pour éviter la congestion transfrontalière. Le SDWAN ou le VPN de l’utilisateur peut maintenant être configuré pour exclure Teams réunion et appeler le trafic en temps réel du routage VPN. Cette configuration VPN est appelée tunneling fractionné. Pour plus d’informations, consultez [le tunneling fractionné VPN pour Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel).

Vous pouvez également continuer à utiliser votre SDWAN ou VPN pour tout le trafic Microsoft 365, y compris pour Microsoft Teams trafic en temps réel. Microsoft n’a aucune recommandation sur l’utilisation de solutions SDWAN ou VPN.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Meilleures pratiques relatives aux réseaux domestiques, mobiles et utilisateur pour les réunions Teams

Les utilisateurs en Chine peuvent tirer parti de ces améliorations simplement en se connectant au service Internet public en Chine avec une connexion fixe ou mobile. Teams trafic audio et vidéo multimédia en temps réel sur l’Internet public bénéficie directement d’une connectivité et d’une qualité améliorées.

Toutefois, les données d’autres services Microsoft 365 et d’autres trafics dans Teams, tels que les conversations ou les fichiers, ne bénéficieront pas directement de ces améliorations. Les utilisateurs en dehors du réseau de l’organisation peuvent toujours rencontrer des performances réseau médiocres pour ce trafic. Comme indiqué dans cet article, vous pouvez atténuer ces effets à l’aide d’un VPN ou d’un SDWAN. Vous pouvez également faire en sorte que vos utilisateurs utilisent des clients de bureau enrichis sur des clients web, qui prennent en charge la mise en cache dans l’application pour atténuer les problèmes réseau.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identification Teams trafic réseau multimédia en temps réel

Pour configurer un appareil réseau ou une configuration VPN/SDWAN, vous devez exclure uniquement le Teams trafic audio et vidéo multimédia en temps réel. Les détails du trafic sont disponibles pour l’ID 11 dans la liste officielle des [URL Office 365 et des plages d’adresses IP](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Toutes les autres configurations réseau doivent rester telles quelle.

Microsoft travaille en permanence à améliorer l’expérience utilisateur Microsoft 365 et les performances des clients par rapport à la plus large gamme possible d’architectures et de caractéristiques réseau. Visitez le [Community de Office 365 tech réseau](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) pour démarrer ou participer à une conversation, rechercher des ressources et envoyer des demandes de fonctionnalités et des suggestions

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Scénarios courants de tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 l’optimisation du réseau et des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
