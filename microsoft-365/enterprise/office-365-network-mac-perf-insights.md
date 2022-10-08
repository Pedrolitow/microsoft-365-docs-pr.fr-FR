---
title: Microsoft 365 Network Insights
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
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
description: Microsoft 365 Network Insights
ms.openlocfilehash: ce5200708ffd0ec3b9beb3de43b8a5f75fb734c1
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191956"
---
# <a name="microsoft-365-network-insights"></a>Microsoft 365 Network Insights

**Les insights réseau sont des** métriques de performances collectées à partir de votre locataire Microsoft 365 et disponibles pour être consultées uniquement par les utilisateurs administratifs de votre locataire. Les insights sont affichés dans le centre Administration Microsoft 365 à l’adresse <https://portal.microsoft.com/adminportal/home#/networkperformance>.

Les insights sont destinés à vous aider à concevoir des périmètres réseau pour vos emplacements de bureau. Chaque insight fournit des détails en direct sur les caractéristiques de performances d’un problème courant spécifique pour chaque emplacement géographique où les utilisateurs accèdent à votre locataire.

Six insights réseau spécifiques peuvent être affichés pour chaque emplacement de bureau :

- [Sortie réseau backhauled](#backhauled-network-egress)
- [Appareil intermédiaire réseau](#network-intermediary-device)
- [Meilleures performances détectées pour les clients proches de chez vous](#better-performance-detected-for-customers-near-you)
- [Utilisation d’une porte d’entrée de service Exchange Online non optimale](#use-of-a-non-optimal-exchange-online-service-front-door)
- [Utilisation d’une porte d’entrée de service SharePoint Online non optimale](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint](#low-download-speed-from-sharepoint-front-door)
- [Sortie réseau optimale de l’utilisateur chinois](#china-user-optimal-network-egress)

Il existe deux insights réseau au niveau du locataire qui peuvent être affichés pour le locataire :

- [Connexions exchange échantillonnées affectées par des problèmes de connectivité](#exchange-sampled-connections-affected-by-connectivity-issues)
- [Connexions échantillonnées SharePoint affectées par des problèmes de connectivité](#sharepoint-sampled-connections-affected-by-connectivity-issues)

Ces informations apparaissent également dans les pages de score de productivité.

>[!IMPORTANT]
>Les insights réseau, les recommandations en matière de performances et les évaluations dans le Centre Administration Microsoft 365 sont actuellement en préversion et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

## <a name="backhauled-network-egress"></a>Sortie réseau backhauled

Cet insight s’affiche si le service d’insights réseau détecte que la distance entre un emplacement utilisateur donné et la sortie réseau est supérieure à 500 milles (800 kilomètres). Cela peut indiquer que le trafic Microsoft 365 est renvoyé vers un périphérique Internet ou un proxy courant.

Cet aperçu est abrégé en « sortie » dans certaines vues récapitulatives.

> [!div class="mx-imgBorder"]
> ![Sortie réseau backhauled.](../media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Cela indique que la distance entre l’emplacement du bureau et la sortie du réseau est supérieure à 500 milles (800 kilomètres). L’emplacement du bureau est identifié par un emplacement d’ordinateur client masqué et l’emplacement de sortie réseau est identifié à l’aide de l’adresse IP inversée vers les bases de données d’emplacement. L’emplacement du bureau peut être incorrect si les services d’emplacement Windows sont désactivés sur les ordinateurs. L’emplacement de sortie réseau peut être inexact si les informations de la base de données d’adresses IP inversées sont inexactes.

Les détails de cet insight sont les suivants :

- Emplacement du bureau
- Pourcentage estimé du nombre total d’utilisateurs locataires à l’emplacement
- Emplacement de sortie réseau actuel
- Pertinence de l’emplacement de sortie
- Distance entre l’emplacement et le point de sortie actuel
- Date à laquelle la condition a été détectée pour la première fois
- Date à laquelle la condition a été résolue

### <a name="what-should-i-do"></a>Que dois-je faire ?

Nous vous recommandons de passer le plus près possible de l’emplacement du bureau.  Le trafic Microsoft 365 doit s’acheminer de manière optimale vers le réseau global de Microsoft et vers la porte d’entrée du service Microsoft 365 la plus proche. La fermeture de la sortie réseau aux emplacements de bureau des utilisateurs permet également d’améliorer les performances, car Microsoft étend à la fois les points de présence réseau et les portes d’entrée du service Microsoft 365 à l’avenir.

Pour plus d’informations sur la résolution de ce problème, consultez [les connexions réseau de sortie localement](microsoft-365-network-connectivity-principles.md#egress-network-connections-locally) dans les [principes de connectivité réseau de Microsoft 365](microsoft-365-network-connectivity-principles.md).

## <a name="network-intermediary-device"></a>Appareil intermédiaire réseau

Cet aperçu s’affiche si nous avons détecté des appareils entre vos utilisateurs et le réseau de Microsoft. Nous recommandons que le trafic réseau Microsoft 365 sensible à la latence contourne ces appareils. Cette recommandation est également décrite dans les [principes de connectivité réseau de Microsoft 365](microsoft-365-network-connectivity-principles.md).

L’un des insights intermédiaires réseau que nous montrons est l’interruption et l’inspection SSL lorsque les points de terminaison réseau Microsoft 365 critiques pour Exchange, SharePoint et Teams sont interceptés et déchiffrés par des appareils intermédiaires réseau.

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Les appareils intermédiaires réseau tels que les serveurs proxy, les VPN et les appareils de protection contre la perte de données peuvent affecter les performances et la stabilité des clients Microsoft 365 où le trafic est intermédiaire.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Configurez l’appareil intermédiaire réseau détecté pour contourner le traitement du trafic réseau Microsoft 365.

## <a name="better-performance-detected-for-customers-near-you"></a>Meilleures performances détectées pour les clients proches de chez vous

Cette information s’affiche si le service d’insights réseau détecte qu’un grand nombre de clients de votre région métropolitaine ont de meilleures performances que les utilisateurs de cet emplacement de bureau.

Cet aperçu est abrégé en « Pairs » dans certaines vues récapitulatives.

> [!div class="mx-imgBorder"]
> ![Performances réseau relatives.](../media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Cet aperçu examine les performances agrégées des clients Microsoft 365 dans la même ville que cet emplacement de bureau. Cet insight s’affiche si la latence moyenne de vos utilisateurs est supérieure de 10 % à la latence moyenne des locataires voisins.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Il peut y avoir de nombreuses raisons à cette condition, notamment la latence dans votre réseau d’entreprise ou votre fournisseur de services Internet, les goulots d’étranglement ou les problèmes de conception d’architecture. Examinez la latence entre chaque tronçon de l’itinéraire entre votre réseau de bureaux et la porte d’entrée Microsoft 365 actuelle. Pour plus d’informations, consultez les [principes de connectivité réseau de Microsoft 365](microsoft-365-network-connectivity-principles.md).

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Utilisation d’une porte d’entrée de service Exchange Online non optimale

Cet aperçu s’affiche si le service d’insights réseau détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas à une porte d’entrée de service Exchange Online optimale.

Cet aperçu est abrégé en « routage » dans certaines vues récapitulatives.

> [!div class="mx-imgBorder"]
> ![Porte d’entrée EXO non optimale.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Nous répertorions Exchange Online portes d’entrée de service qui conviennent pour une utilisation à partir de la ville de l’emplacement du bureau. Si le test actuel montre l’utilisation d’une porte d’entrée de service Exchange Online qui ne figure pas dans cette liste, nous appelons cette recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une porte d’entrée de service Exchange Online non optimale peut être causée par un retour en arrière du réseau, auquel cas nous recommandons une sortie réseau locale et directe. Si vous avez implémenté un serveur récursif DNS distant, nous vous recommandons d’aligner la configuration du serveur avec la sortie réseau.

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a>Utilisation d’une porte d’entrée de service SharePoint Online non optimale

Cet aperçu s’affiche si le service d’insights réseau détecte que les utilisateurs situés à un emplacement spécifique ne se connectent pas à la porte d’entrée du service SharePoint Online la plus proche.

Cet aperçu est abrégé en « Afd » dans certaines vues récapitulatives.

> [!div class="mx-imgBorder"]
> ![Porte d’entrée SPO non optimale.](../media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Nous identifions la porte d’entrée du service SharePoint Online à laquelle le client de test se connecte. Ensuite, pour la ville d’emplacement du bureau, nous comparons cela à la porte d’entrée du service SharePoint Online attendue pour cette ville. S’il ne correspond pas, nous faisons cette recommandation.

### <a name="what-should-i-do"></a>Que dois-je faire ?

L’utilisation d’une porte d’entrée de service SharePoint Online non optimale peut être due à une régression réseau avant la sortie du réseau d’entreprise, auquel cas nous recommandons une sortie de réseau local et direct. Cela peut également être dû à l’utilisation d’un serveur de résolveur récursif DNS distant, auquel cas nous vous recommandons d’aligner le serveur récursif DNS avec la sortie réseau.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Vitesse de téléchargement faible à partir de la porte d’entrée SharePoint

Cet insight s’affiche si le service d’insights réseau détecte que la bande passante entre l’emplacement du bureau spécifique et SharePoint Online est inférieure à 1 Mbit/s.

Cet aperçu est abrégé en « Débit » dans certaines vues récapitulatives.

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

La vitesse de téléchargement qu’un utilisateur peut obtenir à partir de SharePoint Online et OneDrive Entreprise portes d’entrée du service est mesurée en mégaoctets par seconde (Mbits/s). Si cette valeur est inférieure à 1 Mbit/s, nous fournissons cet insight.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour améliorer la vitesse de téléchargement, il peut être nécessaire d’augmenter la bande passante. Il peut également y avoir une congestion du réseau entre les ordinateurs situés à l’emplacement du bureau et la porte d’entrée du service SharePoint Online. Cette condition limite la vitesse de téléchargement disponible pour les utilisateurs, même si une bande passante suffisante est disponible.

## <a name="china-user-optimal-network-egress"></a>Sortie réseau optimale de l’utilisateur chinois

Cet aperçu s’affiche si les utilisateurs de votre organisation en Chine se connectent à votre locataire Microsoft 365 dans d’autres emplacements géographiques.

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Si votre organisation dispose d’une connectivité WAN privée, nous vous recommandons de configurer un circuit réseau WAN à partir de vos emplacements de bureau en Chine qui dispose d’une sortie réseau vers Internet à l’un des emplacements suivants :

- Hong Kong
- Japon
- Taïwan
- Corée du Sud
- Singapour
- Malaisie

La sortie d’Internet plus éloignée des utilisateurs que ces emplacements réduit les performances, et la sortie en Chine peut entraîner des problèmes de latence et de connectivité élevés en raison de la congestion transfrontalière.

### <a name="what-should-i-do"></a>Que dois-je faire ?

Pour plus d’informations sur la façon d’atténuer les problèmes de performances liés à cet insight, consultez [l’optimisation des performances globales des locataires Microsoft 365 pour les utilisateurs chinois](microsoft-365-networking-china.md).

## <a name="exchange-sampled-connections-affected-by-connectivity-issues"></a>Connexions exchange échantillonnées affectées par des problèmes de connectivité

Cet insight indique quand 50 % ou plus des connexions échantillonnées sont affectées. L’impact est défini par l’évaluation Exchange inférieure à 60 % pour chaque échantillon.

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Cela indique que la plupart de vos utilisateurs rencontrent probablement des problèmes avec Outlook se connectant à Exchange Online. Le pourcentage d’échantillons représente le pourcentage d’utilisateurs qui affichent moins de 60 points.  

### <a name="what-should-i-do"></a>Que dois-je faire ?

Activez la visibilité de la connectivité réseau de l’emplacement office si vous ne l’avez pas déjà fait. Identifiez les bureaux affectés par une connectivité réseau médiocre et trouvez des moyens d’améliorer le périmètre réseau à chacun d’eux qui connecte les utilisateurs au réseau de Microsoft.

## <a name="sharepoint-sampled-connections-affected-by-connectivity-issues"></a>Connexions échantillonnées SharePoint affectées par des problèmes de connectivité

Cet insight indique quand 50 % ou plus des connexions échantillonnées sont affectées. L’impact est défini par l’évaluation SharePoint inférieure à 40 % pour chaque échantillon.

### <a name="what-does-this-mean"></a>Qu’est-ce que cela signifie ?

Cela indique que la plupart de vos utilisateurs rencontrent probablement des problèmes avec SharePoint et OneDrive. Le pourcentage d’échantillons représente le pourcentage d’utilisateurs qui affichent moins de 40 points.  

### <a name="what-should-i-do"></a>Que dois-je faire ?

Activez la visibilité de la connectivité réseau de l’emplacement office si vous ne l’avez pas déjà fait. Identifiez les bureaux affectés par une connectivité réseau médiocre et trouvez des moyens d’améliorer le périmètre réseau à chacun d’eux qui connecte les utilisateurs au réseau de Microsoft.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre de Administration Microsoft 365](office-365-network-mac-perf-overview.md)

[Évaluation du réseau Microsoft 365](office-365-network-mac-perf-score.md)

[Outil de test de la connectivité du réseau Microsoft 365](office-365-network-mac-perf-onboarding-tool.md)

[Services d’emplacement de connectivité réseau Microsoft 365](office-365-network-mac-location-services.md)
