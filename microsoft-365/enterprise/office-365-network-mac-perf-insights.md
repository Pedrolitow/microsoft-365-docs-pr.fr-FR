---
title: Microsoft 365 Network Insights (prévisualisation)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 Network Insights (prévisualisation)
ms.openlocfilehash: d6786ce6cd58ce6f350804fbbacd272b8c077dc0
ms.sourcegitcommit: 1ac884d8470b2f2a58b6f79e324fd91e4d11dceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "50055472"
---
# <a name="microsoft-365-network-insights-preview"></a>Microsoft 365 Network Insights (prévisualisation)

**Les informations réseau sont** des mesures de performances collectées à partir de votre client Microsoft 365 et disponibles uniquement pour les utilisateurs administratifs de votre client. Les informations sont affichées dans le Centre d’administration Microsoft 365 à l’adresse <https://portal.microsoft.com/adminportal/home#/networkperformance> .

Les informations sont conçues pour vous aider à concevoir des périmètres réseau pour vos bureaux. Chaque insight fournit des détails en direct sur les caractéristiques de performances d’un problème commun spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre client.

Il existe six informations réseau spécifiques qui peuvent être affichées pour chaque emplacement de bureau :

- [Sortie du réseau backhauled](#backhauled-network-egress)
- [Périphérique intermédiaire réseau](#network-intermediary-device)
- [Meilleures performances détectées pour les clients proches de chez vous](#better-performance-detected-for-customers-near-you)
- [Utilisation d’une porte d’entrée de service Exchange Online non optimale](#use-of-a-non-optimal-exchange-online-service-front-door)
- [Utilisation d’une porte d’entrée de service SharePoint Online non optimale](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint](#low-download-speed-from-sharepoint-front-door)
- [Sortie réseau optimale de l’utilisateur chinois](#china-user-optimal-network-egress)

Il existe deux informations réseau au niveau du client qui peuvent être affichées pour le client. Ceux-ci apparaissent également dans les pages de score de producvitivy :

- [Exemples de connexions Exchange touchés par des problèmes de connectivité](#exchange-sampled-connections-impacted-by-connectivity-issues)
- [Exemples de connexions SharePoint touchés par des problèmes de connectivité](#sharepoint-sampled-connections-impacted-by-connectivity-issues)

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le Centre d’administration Microsoft 365 sont actuellement en état de prévisualisation et sont disponibles uniquement pour les clients Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

## <a name="backhauled-network-egress"></a>Sortie du réseau backhauled

Cette information s’affiche si le service d’informations réseau détecte que la distance entre un emplacement utilisateur donné et la sortie réseau est supérieure à 500 miles (800 kilomètres), ce qui indique que le trafic Microsoft 365 est rétrogradé vers un périphérique edge Internet ou un proxy commun.

Cette information est abrégée en « Sortie » dans certains affichages récapitulatifs.

![Sortie du réseau backhauled](../media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>Scénario

Cela indique que la distance entre l’emplacement du bureau et la sortie réseau est de plus de 500 km (800 kilomètres). L’emplacement du bureau est identifié par un emplacement d’ordinateur client obscurci et l’emplacement de sortie réseau est identifié à l’aide de l’adresse IP inversée pour les bases de données d’emplacement. L’emplacement du bureau peut être incorrect si les services de localisation Windows sont désactivés sur les ordinateurs. L’emplacement de sortie réseau peut être incorrect si les informations de la base de données d’adresses IP inverses sont inexactes.

Ces informations incluent l’emplacement du bureau, le pourcentage estimé du nombre total d’utilisateurs locataires sur l’emplacement, l’emplacement de sortie du réseau actuel, la pertinence de l’emplacement de sortie, la distance entre l’emplacement et le point de sortie actuel, la date à laquelle la condition a été détectée pour la première fois et la date à laquelle la condition a été résolue.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour ce faire, nous vous recommandons d’utiliser une sortie réseau plus proche de l’emplacement du bureau afin que la connectivité puisse être acheminée de manière optimale vers le réseau global de Microsoft et vers la porte d’entrée du service Microsoft 365 la plus proche. Une sortie étroite du réseau vers les emplacements de bureau des utilisateurs permet également d’améliorer les performances à l’avenir, car Microsoft étend à la fois les points de présence réseau et les portes avant du service Microsoft 365 à l’avenir.

Pour plus d’informations sur la résolution de ce problème, voir la sortie des [connexions](microsoft-365-network-connectivity-principles.md#egress-network-connections-locally) réseau localement dans les principes de connectivité réseau [d’Office 365.](microsoft-365-network-connectivity-principles.md)

## <a name="network-intermediary-device"></a>Périphérique intermédiaire réseau

Cette information s’affiche si nous avons détecté des appareils entre vos utilisateurs et le réseau de Microsoft qui peuvent avoir un impact sur l’expérience utilisateur d’Office 365. Il est recommandé de les contourner pour le trafic réseau Microsoft 365 spécifique destiné aux centres de données Microsoft. Cette recommandation est également décrite dans les principes de connectivité réseau [de Microsoft 365](microsoft-365-network-connectivity-principles.md)

### <a name="what-does-this-mean"></a>Scénario

Les périphériques intermédiaires réseau tels que les serveurs proxy, les VPN et les périphériques de protection contre la perte de données peuvent affecter les performances et la stabilité des clients Microsoft 365 où le trafic est intermédiaire.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Configurez le périphérique intermédiaire réseau détecté pour contourner le traitement du trafic réseau Microsoft 365.

## <a name="better-performance-detected-for-customers-near-you"></a>Meilleures performances détectées pour les clients proches de chez vous

Cette information s’affiche si le service d’informations réseau détecte qu’un nombre significatif de clients dans votre zone d’information offrent de meilleures performances que les utilisateurs de votre organisation à cet emplacement de bureau.

Cette information est abrégée en « Homologues » dans certains affichages récapitulatifs.

![Performances relatives du réseau](../media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>Scénario

Cette vue d’ensemble examine les performances agrégées des clients Microsoft 365 dans la même ville que cet emplacement de bureau. Cette information s’affiche si la latence moyenne de vos utilisateurs est supérieure de 10 % à la latence moyenne des locataires voisins.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Il peut y avoir de nombreuses raisons à cette condition, notamment la latence dans votre réseau d’entreprise ou votre isp isp, les goulots d’étranglement ou les problèmes de conception de l’architecture. Examinez la latence entre chaque saut de l’itinéraire entre votre réseau de bureau et la porte d’entrée Microsoft 365 actuelle. Pour plus d’informations, voir Principes de connectivité réseau [Microsoft 365.](microsoft-365-network-connectivity-principles.md)

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Utilisation d’une porte d’entrée de service Exchange Online non optimale

Cette information s’affiche si le service d’informations réseau détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas à une porte d’entrée de service Exchange Online optimale.

Cette information est abrégée en « Routage » dans certains affichages récapitulatifs.

![Porte d’entrée EXO non optimale](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>Scénario

Nous listons les portes d’entrée du service Exchange Online qui conviennent à une utilisation à partir de la ville de l’emplacement du bureau avec de bonnes performances. Si le test actuel indique l’utilisation d’une porte d’entrée du service Exchange Online qui ne figure pas dans cette liste, nous appelons cette recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une porte d’entrée du service Exchange Online non optimale peut être causée par une rétrograder réseau avant la sortie du réseau d’entreprise, auquel cas nous recommandons une sortie de réseau local et directe. Cela peut également être dû à l’utilisation d’un serveur de résolution récursive DNS distant, auquel cas nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>Utilisation d’une porte d’entrée de service SharePoint Online non optimale

Cette information s’affiche si le service d’informations réseau détecte que les utilisateurs d’un emplacement spécifique ne se connectent pas à la porte d’entrée du service SharePoint Online la plus proche.

Cette information est abrégée en « Afd » dans certains affichages récapitulatifs.

![Porte d’entrée SPO non optimale](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>Scénario

Nous identifions la porte d’entrée du service SharePoint Online à qui le client de test se connecte. Ensuite, pour la ville de l’emplacement du bureau, nous comparons cela à la porte d’entrée du service SharePoint Online attendue pour cette ville. Si ce n’est pas le cas, nous vous en faire la recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une porte frontale de service SharePoint Online non optimale peut être causée par une rétrograder du réseau avant la sortie du réseau d’entreprise, auquel cas nous recommandons la sortie du réseau local et direct. Cela peut également être dû à l’utilisation d’un serveur de résolution récursive DNS distant, auquel cas nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint

Cette information s’affiche si le service d’informations réseau détecte que la bande passante entre l’emplacement du bureau spécifique et SharePoint Online est inférieure à 1 Mbits/s.

Cette information est abrégée « Débit » dans certains affichages récapitulatifs.

### <a name="what-does-this-mean"></a>Scénario

La vitesse de téléchargement qu’un utilisateur peut obtenir à partir des portes frontales du service SharePoint Online et OneDrive Entreprise est mesurée en mégaoctets par seconde (MBits/s). Si cette valeur est inférieure à 1 Mbits/s, nous fournissons cette information.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour améliorer les vitesses de téléchargement, vous devrez peut-être augmenter la bande passante. Sinon, il peut y avoir une congestion du réseau entre les ordinateurs des utilisateurs au niveau de l’emplacement du bureau et du service SharePoint Online. Cette perte est parfois appelée perte congestive et limite la vitesse de téléchargement disponible pour les utilisateurs, même si une bande passante suffisante est disponible.

## <a name="china-user-optimal-network-egress"></a>Sortie réseau optimale de l’utilisateur chinois

Cette information s’affiche si des utilisateurs de votre organisation en Chine se connectent à votre client Microsoft 365 dans d’autres emplacements géographiques. 

### <a name="what-does-this-mean"></a>Scénario

Si votre organisation dispose d’une connectivité WAN privée, nous vous recommandons de configurer un circuit réseau WAN à partir de vos bureaux en Chine qui dispose d’une sortie réseau vers Internet à l’un des emplacements suivants :

- Hong Kong
- Japon
- Taïwan
- Corée du Sud
- Singapour
- Malaisie

Une sortie d’Internet plus éloignée des utilisateurs que ces emplacements réduit les performances, et la sortie en Chine peut entraîner des problèmes de latence et de connectivité élevés en raison d’une congestion croisée.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour plus d’informations sur la façon d’atténuer les problèmes de performances liés à cette information, consultez l’optimisation des performances globales du client [Microsoft 365](microsoft-365-networking-china.md)pour les utilisateurs chinois.

## <a name="exchange-sampled-connections-impacted-by-connectivity-issues"></a>Exemples de connexions Exchange touchés par des problèmes de connectivité

Cette information indique quand 50 % ou plus des connexions échantillonées sont impactées. L’impact est défini par l’évaluation Exchange inférieure à 60 % pour chaque échantillon.

### <a name="what-does-this-mean"></a>Scénario

Il s’agit d’une indication que la majorité de vos utilisateurs rencontreront probablement des problèmes d’expérience utilisateur avec Outlook qui se connecte à Exchange Online. Le pourcentage d’échantillons représente probablement le pourcentage d’utilisateurs qui indiquent moins de 60 points.  

### <a name="what-should-i-do"></a>Que dois-je faire ?

Activez la visibilité de la connectivité réseau de l’emplacement du bureau si vous ne l’avez pas déjà fait. Vous souhaitez identifier les bureaux qui sont touchés par une connectivité réseau médiocre qui a un impact sur Exchange et trouver des moyens d’améliorer le périmètre réseau à chaque bureau qui connecte les utilisateurs au réseau de Microsoft.

## <a name="sharepoint-sampled-connections-impacted-by-connectivity-issues"></a>Exemples de connexions SharePoint touchés par des problèmes de connectivité

Cette information indique quand 50 % ou plus des connexions échantillonées sont impactées. L’impact est défini par l’évaluation SharePoint inférieure à 40 % pour chaque échantillon.

### <a name="what-does-this-mean"></a>Scénario

Il s’agit d’une indication que la majorité de vos utilisateurs rencontreront probablement des problèmes d’expérience utilisateur avec SharePoint et OneDrive. Le pourcentage d’échantillons représente probablement le pourcentage d’utilisateurs qui indiquent moins de 40 points.  

### <a name="what-should-i-do"></a>Que dois-je faire ?

Activez la visibilité de la connectivité réseau de l’emplacement du bureau si vous ne l’avez pas déjà fait. Vous souhaitez identifier les bureaux qui sont touchés par une connectivité réseau médiocre qui a un impact sur SharePoint et trouver des moyens d’améliorer le périmètre réseau à chaque bureau qui connecte les utilisateurs au réseau de Microsoft.

## <a name="related-topics"></a>Rubriques connexes

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Évaluation du réseau Microsoft 365 (prévisualisation)](office-365-network-mac-perf-score.md)

[Outil de test de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)](office-365-network-mac-location-services.md)
