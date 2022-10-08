---
title: Scénarios courants de tunneling fractionné VPN pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Scénarios courants de tunneling fractionné VPN pour Microsoft 365
ms.openlocfilehash: 7da7679a92c87a90a174ce05bd7e5db5458507af
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68195762"
---
# <a name="common-vpn-split-tunneling-scenarios-for-microsoft-365"></a>Scénarios courants de tunneling fractionné VPN pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent de l’optimisation de Microsoft 365 pour les utilisateurs distants.

>- Pour obtenir une vue d’ensemble de l’utilisation du tunneling fractionné VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, consultez [Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir des conseils détaillés sur l’implémentation du tunneling fractionné VPN, consultez [Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Pour obtenir des conseils sur la sécurisation du trafic multimédia Teams dans les environnements de tunneling fractionné VPN, consultez [Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration des événements stream et en direct dans les environnements VPN, consultez [considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation des performances des locataires Microsoft 365 dans le monde entier pour les utilisateurs en Chine, consultez [l’optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

Dans la liste ci-dessous, vous verrez les scénarios VPN les plus courants dans les environnements d’entreprise. La plupart des clients utilisent généralement le modèle 1 (tunnel imposé VPN). Cette section vous aidera à passer rapidement et en toute sécurité au **modèle 2**, ce qui est réalisable avec relativement peu d’efforts et présente d’énormes avantages pour les performances réseau et l’expérience utilisateur.

| Modèle | Description |
| --- | --- |
| [1. Tunnel imposé VPN](#1-vpn-forced-tunnel) | 100 % du trafic passe dans le tunnel VPN, y compris en local, Internet et tout O365/M365 |
| [2. Tunnel imposé VPN avec quelques exceptions](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | Le tunnel VPN est utilisé par défaut (point d’itinéraire par défaut vers VPN), avec peu de scénarios d’exemption les plus importants autorisés à passer directement |
| [3. Tunnel imposé VPN avec de larges exceptions](#3-vpn-forced-tunnel-with-broad-exceptions) | Le tunnel VPN est utilisé par défaut (points d’itinéraire par défaut vers VPN), à de grandes exceptions près qui sont autorisées à passer directement (par exemple, tous les microsoft 365, Tous Salesforce, Tous les zooms) |
| [4. Tunnel sélectif VPN](#4-vpn-selective-tunnel) | Le tunnel VPN est utilisé uniquement pour les services basés sur un réseau d’entreprise. L’itinéraire par défaut (Internet et tous les services Internet) est direct. |
| [5. Pas de VPN](#5-no-vpn) | Variante de #2. Au lieu d’un VPN hérité, tous les services de réseau d’entreprise sont publiés par le biais d’approches de sécurité modernes (comme Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS, etc.) |

## <a name="1-vpn-forced-tunnel"></a>1. Tunnel imposé VPN

Scénario de démarrage le plus courant pour la plupart des clients d’entreprise. Un VPN forcé est utilisé, ce qui signifie que 100 % du trafic est dirigé vers le réseau d’entreprise, que le point de terminaison réside dans le réseau d’entreprise ou non. Tout trafic externe (Internet) lié, tel que Microsoft 365 ou la navigation Internet, est ensuite épinglé à l’extérieur de l’équipement de sécurité local, tel que les proxys. Dans le climat actuel où près de 100 % des utilisateurs travaillent à distance, ce modèle place donc une charge élevée sur l’infrastructure VPN et est susceptible d’entraver considérablement les performances de tout le trafic d’entreprise et, par conséquent, l’entreprise à fonctionner efficacement en période de crise.

![Modèle de tunnel forcé VPN 1.](../media/vpn-split-tunneling/vpn-model-1.png)

## <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. Tunnel imposé VPN avec un petit nombre d’exceptions approuvées

Considérablement plus efficace pour qu’une entreprise fonctionne sous. Ce modèle permet à quelques points de terminaison contrôlés et définis qui sont sensibles à une charge et une latence élevées de contourner le tunnel VPN et d’accéder directement au service Microsoft 365. Cela améliore considérablement les performances des services déchargés et réduit également la charge sur l’infrastructure VPN, ce qui permet aux éléments qui l’exigent toujours de fonctionner avec une contention plus faible pour les ressources. C’est ce modèle que cet article se concentre sur l’aide à la transition, car il permet d’effectuer rapidement des actions simples et définies avec de nombreux résultats positifs.

![Modèle VPN de tunnel fractionné 2.](../media/vpn-split-tunneling/vpn-model-2.png)

## <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. Tunnel imposé VPN avec de larges exceptions

Élargit l’étendue du modèle 2. Au lieu d’envoyer directement un petit groupe de points de terminaison définis, il envoie tout le trafic directement aux services approuvés tels que Microsoft 365 et SalesForce. Cela permet de réduire davantage la charge sur l’infrastructure VPN d’entreprise et d’améliorer les performances des services définis. Étant donné que ce modèle est susceptible de prendre plus de temps pour évaluer la faisabilité et la mise en œuvre, il s’agit probablement d’une étape qui peut être effectuée de manière itérative à une date ultérieure une fois le modèle 2 correctement mis en place.

![Modèle VPN de tunnel fractionné 3.](../media/vpn-split-tunneling/vpn-model-3.png)

## <a name="4-vpn-selective-tunnel"></a>4. Tunnel sélectif VPN

Inverse le troisième modèle dans la mesure où seul le trafic identifié comme ayant une adresse IP d’entreprise est envoyé dans le tunnel VPN et, par conséquent, le chemin d’accès Internet est l’itinéraire par défaut pour tout le reste. Ce modèle nécessite qu’une organisation se trouve bien sur le chemin d’accès [Approbation zéro](https://www.microsoft.com/security/zero-trust?rtc=1) pour pouvoir implémenter ce modèle en toute sécurité. Il convient de noter que ce modèle ou une variante de celui-ci deviendra probablement la valeur par défaut nécessaire au fil du temps, car davantage de services s’éloignent du réseau d’entreprise et vers le cloud.

Microsoft utilise ce modèle en interne. Vous trouverez plus d’informations sur l’implémentation par Microsoft du tunneling fractionné VPN sur [Running on VPN : Comment Microsoft maintient la connexion de sa main-d’œuvre distante](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Modèle VPN de tunnel fractionné 4.](../media/vpn-split-tunneling/vpn-model-4.png)

## <a name="5-no-vpn"></a>5. Pas de VPN

Version plus avancée du modèle numéro 2, dans laquelle tous les services internes sont publiés via une approche de sécurité moderne ou une solution SDWAN telle que le proxy Azure AD, Defender pour Cloud Apps, Zscaler ZPA, etc.

![Modèle VPN de tunnel fractionné 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implémentation du tunneling fractionné VPN pour Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Sécurisation du trafic multimédia Teams pour le tunneling fractionné VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales sur les événements stream et en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Optimisation des performances de Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Optimisation des performances et du réseau Microsoft 365](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
