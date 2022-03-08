---
title: Scénarios courants de tunneling fractionnement VPN pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Scénarios courants de tunneling fractionnement VPN pour Microsoft 365
ms.openlocfilehash: 26f4cf10de3282c5257592a26ea61d073a0d3cd4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331144"
---
# <a name="common-vpn-split-tunneling-scenarios-for-microsoft-365"></a>Scénarios courants de tunneling fractionnement VPN pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour une vue d’ensemble de l’utilisation de la tunneling fractionnement VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, voir Vue d’ensemble : [tunneling fractionnel VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des instructions détaillées sur l’implémentation de la tunneling fractionnement VPN, voir [Implementing VPN split tunneling for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir des instructions sur la sécurisation Teams trafic multimédia dans les environnements de tunnel partagé VPN, voir Sécurisation du trafic Teams multimédia [pour la tunnelisation fractionnée VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration de Stream et d’événements en direct dans les environnements VPN, voir Considérations spéciales pour Stream et les [événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

Dans la liste ci-dessous, vous verrez les scénarios VPN les plus courants dans les environnements d’entreprise. La plupart des clients utilisent généralement le modèle 1 (tunnel imposé VPN). Cette section vous aidera à passer rapidement et en toute sécurité au modèle **2**, ce qui est réalisable avec un effort relativement faible et qui présente des avantages considérables pour les performances du réseau et l’expérience utilisateur.

| Modèle | Description |
| --- | --- |
| [1. Tunnel imposé VPN](#1-vpn-forced-tunnel) | 100 % du trafic passe dans le tunnel VPN, y compris sur site, Internet et tout O365/M365 |
| [2. Tunnel imposé VPN avec quelques exceptions](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | Le tunnel VPN est utilisé par défaut (point d’itinéraire par défaut vers VPN), avec peu de scénarios d’exemption les plus importants autorisés à passer directement |
| [3. Tunnel imposé VPN avec de larges exceptions](#3-vpn-forced-tunnel-with-broad-exceptions) | Le tunnel VPN est utilisé par défaut (points d’itinéraire par défaut vers VPN), avec de grandes exceptions qui sont autorisées à passer directement (par exemple, tous les Microsoft 365, Tous les salesforce, Tous les zooms) |
| [4. Tunnel sélectif VPN](#4-vpn-selective-tunnel) | Le tunnel VPN est utilisé uniquement pour les services basés sur un réseau d’entreprise. L’itinéraire par défaut (Internet et tous les services Internet) est directement acheminé. |
| [5. Pas de VPN](#5-no-vpn) | Variante de #2. Au lieu du VPN hérité, tous les services de réseau d’entreprise sont publiés par le biais d’approches de sécurité modernes (comme Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS, etc.) |

## <a name="1-vpn-forced-tunnel"></a>1. Tunnel imposé VPN

Scénario de départ le plus courant pour la plupart des clients d’entreprise. Un VPN forcé est utilisé, ce qui signifie que 100 % du trafic est dirigé vers le réseau d’entreprise, que le point de terminaison réside dans le réseau d’entreprise ou non. Tout trafic externe (Internet) tel que Microsoft 365 ou la navigation Internet est ensuite épinglé à l’extérieur de l’équipement de sécurité local, tel que les proxies. Dans le monde actuel où près de 100 % des utilisateurs travaillent à distance, ce modèle met donc une charge élevée sur l’infrastructure VPN et est susceptible d’entraver considérablement les performances de l’ensemble du trafic d’entreprise et donc de l’entreprise pour fonctionner efficacement en temps de crise.

![Vpn forced Tunnel model 1.](../media/vpn-split-tunneling/vpn-model-1.png)

## <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. Tunnel imposé VPN avec un petit nombre d’exceptions approuvées

Considérablement plus efficace pour qu’une entreprise fonctionne. Ce modèle permet à quelques points de terminaison contrôlés et définis qui sont sensibles à la charge élevée et à la latence de contourner le tunnel VPN et d’être directement Microsoft 365 service. Cela améliore considérablement les performances des services déchargés et réduit également la charge sur l’infrastructure VPN, ce qui permet aux éléments qui en ont encore besoin de fonctionner avec une contention moindre des ressources. C’est sur ce modèle que cet article se concentre sur l’assistance à la transition, car il permet d’agir rapidement sur des actions simples et définies avec de nombreux résultats positifs.

![Fractionnement Tunnel VPN modèle 2.](../media/vpn-split-tunneling/vpn-model-2.png)

## <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. Tunnel imposé VPN avec de larges exceptions

Élargit l’étendue du modèle 2. Au lieu d’envoyer directement un petit groupe de points de terminaison définis, il envoie tout le trafic directement aux services de confiance tels que Microsoft 365 et SalesForce. Cela permet de réduire davantage la charge sur l’infrastructure VPN d’entreprise et d’améliorer les performances des services définis. Comme ce modèle est susceptible de prendre plus de temps pour évaluer la faisabilité et l’implémenter, il s’agit probablement d’une étape qui peut être prise de manière itérative à une date ultérieure une fois que le modèle 2 est correctement mis en place.

![Fractionner Tunnel VPN modèle 3.](../media/vpn-split-tunneling/vpn-model-3.png)

## <a name="4-vpn-selective-tunnel"></a>4. Tunnel sélectif VPN

Inverse le troisième modèle dans la mesure où seul le trafic identifié comme ayant une adresse IP d’entreprise est envoyé vers le bas du tunnel VPN et par conséquent, le chemin d’accès Internet est l’itinéraire par défaut pour tout le reste. Ce modèle nécessite qu’une organisation se trouve bien sur le chemin d’accès [Approbation zéro](https://www.microsoft.com/security/zero-trust?rtc=1) pour pouvoir implémenter ce modèle en toute sécurité. Il convient de noter que ce modèle ou une variante de celui-ci deviendra probablement la valeur par défaut nécessaire au fil du temps, car de plus en plus de services s’éloignent du réseau d’entreprise et se déplacent vers le cloud.

Microsoft utilise ce modèle en interne. Vous trouverez plus d’informations sur l’implémentation par Microsoft de la tunneling fractionnement VPN lors de l’exécution sur VPN : comment Microsoft maintient ses employés à [distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Fractionner Tunnel vpn modèle 4.](../media/vpn-split-tunneling/vpn-model-4.png)

## <a name="5-no-vpn"></a>5. Pas de VPN

Une version plus avancée du modèle numéro 2, dans laquelle tous les services internes sont publiés par le biais d’une approche de sécurité moderne ou d’une solution SDWAN telle que Azure AD Proxy, Defender pour les applications cloud, Zscaler ZPA, etc.

![Modèle VPN Tunnel partagé 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunnel vpn partagé pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation de la tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales pour les flux et les événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
