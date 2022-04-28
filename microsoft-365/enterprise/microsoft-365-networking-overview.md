---
title: Vue d’ensemble de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 08/27/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Explique pourquoi l’optimisation du réseau est importante pour les services SaaS, l’objectif de Microsoft 365 la mise en réseau et la façon dont SaaS nécessite une mise en réseau différente des autres charges de travail.
ms.openlocfilehash: 64af558653ff57e91068d2e028235b73c165376b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096763"
---
# <a name="microsoft-365-network-connectivity-overview"></a>vue d’ensemble de la connectivité réseau Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est un cloud SaaS distribué qui fournit des scénarios de productivité et de collaboration par le biais d’un ensemble diversifié de micro-services et d’applications. Les composants clients de Microsoft 365 tels que Outlook, Word et PowerPoint s’exécutent sur les ordinateurs utilisateur et se connectent à d’autres composants de Microsoft 365 qui s’exécutent dans les centres de données Microsoft. Le facteur le plus important qui détermine la qualité de l’expérience de l’utilisateur final Microsoft 365 est la fiabilité du réseau et la faible latence entre les clients Microsoft 365 et les portes d’entrée du service Microsoft 365.

Dans cet article, vous allez découvrir les objectifs de la mise en réseau Microsoft 365 et pourquoi Microsoft 365 réseau nécessite une approche différente de l’optimisation du trafic Internet générique.

## <a name="microsoft-365-networking-goals"></a>objectifs de mise en réseau Microsoft 365

L’objectif ultime de Microsoft 365 mise en réseau est d’optimiser l’expérience de l’utilisateur final en activant l’accès le moins restrictif entre les clients et les points de terminaison Microsoft 365 les plus proches. La qualité de l’expérience utilisateur final est directement liée aux performances et à la réactivité de l’application que l’utilisateur utilise. Par exemple, Microsoft Teams s’appuie sur une faible latence afin que les appels téléphoniques des utilisateurs, les conférences et les collaborations sur écran partagé soient sans problème, et Outlook s’appuie sur une connectivité réseau excellente pour les fonctionnalités de recherche instantanée qui appliquent l’indexation côté serveur et les fonctionnalités d’IA.

L’objectif principal de la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (RTT) des machines clientes au Réseau mondial Microsoft, le réseau principal du réseau public de Microsoft qui interconnecte tous les centres de données de Microsoft avec des points d’entrée d’application cloud à faible latence et à haute disponibilité répartis dans le monde entier. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

L’optimisation des performances réseau Microsoft 365 n’a pas besoin d’être compliquée. Vous pouvez obtenir les meilleures performances possibles en suivant quelques principes clés :

- Identifier Microsoft 365 trafic réseau
- Autoriser la sortie de branche locale du trafic réseau Microsoft 365 vers Internet à partir de chaque emplacement où les utilisateurs se connectent à Microsoft 365
- Autoriser Microsoft 365 trafic à contourner les proxys et les appareils d’inspection des paquets

Pour plus d’informations sur Microsoft 365 principes de connectivité réseau, consultez [Microsoft 365 Principes de connectivité réseau](microsoft-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Architectures réseau traditionnelles et SaaS

Les principes d’architecture réseau traditionnels pour les charges de travail client/serveur sont conçus en partant du principe que le trafic entre les clients et les points de terminaison ne s’étend pas en dehors du périmètre du réseau d’entreprise. En outre, dans de nombreux réseaux d’entreprise, toutes les connexions Internet sortantes parcourent le réseau d’entreprise et sortent d’un emplacement central.

Dans les architectures réseau traditionnelles, une latence plus élevée pour le trafic Internet générique est un compromis nécessaire pour maintenir la sécurité du périmètre réseau, et l’optimisation des performances pour le trafic Internet implique généralement la mise à niveau ou la mise à l’échelle de l’équipement aux points de sortie réseau. Toutefois, cette approche ne répond pas aux exigences en matière de performances réseau optimales des services SaaS tels que Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identification du trafic réseau Microsoft 365

Nous simplifions l’identification Microsoft 365 trafic réseau et simplifions la gestion de l’identification réseau.

- Nouvelles catégories de points de terminaison réseau pour différencier le trafic réseau hautement critique du trafic réseau qui n’est pas affecté par les latences Internet. Il n’existe qu’une poignée d’URL et de prise en charge des adresses IP dans la catégorie « Optimiser » la plus critique.
- Services web pour l’utilisation des scripts ou la configuration directe des appareils et la gestion des modifications de Microsoft 365 l’identification du réseau. Les modifications sont disponibles à partir du service web, au format RSS ou sur l’e-mail à l’aide d’un modèle Microsoft Flow.
- [Office 365 programme de partenaires réseau](./microsoft-365-networking-partner-program.md) avec des partenaires Microsoft qui fournissent des appareils ou des services qui suivent Microsoft 365 principes de connectivité réseau et disposent d’une configuration simple.

## <a name="securing-microsoft-365-connections"></a>Sécurisation des connexions Microsoft 365

L’objectif de la sécurité réseau traditionnelle est de renforcer le périmètre du réseau de l’entreprise contre les intrusions et les logiciels malveillants. La plupart des réseaux d’entreprise appliquent la sécurité réseau pour le trafic Internet à l’aide de technologies telles que les serveurs proxy, les pare-feu, l’arrêt et l’inspection SSL, l’inspection approfondie des paquets et les systèmes de protection contre la perte de données. Ces technologies fournissent une atténuation importante des risques pour les demandes Internet génériques, mais peuvent réduire considérablement les performances, l’évolutivité et la qualité de l’expérience de l’utilisateur final lorsqu’elles sont appliquées aux points de terminaison Microsoft 365.

Microsoft 365 permet de répondre aux besoins de votre organisation en matière de sécurité du contenu et de conformité de l’utilisation des données avec les fonctionnalités de sécurité et de gouvernance intégrées conçues spécifiquement pour Microsoft 365 fonctionnalités et charges de travail. Pour plus d’informations sur la sécurité et la conformité Microsoft 365, consultez la [feuille de route de sécurité Office 365](/office365/securitycompliance/security-roadmap). Pour plus d’informations sur les recommandations de Microsoft et la position de support sur les solutions réseau avancées qui effectuent un traitement de niveau avancé sur le trafic Microsoft 365, consultez [Utilisation d’appareils réseau tiers ou de solutions sur Office 365 trafic](https://support.microsoft.com/help/2690045).

## <a name="why-is-microsoft-365-networking-different"></a>Pourquoi Microsoft 365 mise en réseau est-elle différente ?

Microsoft 365 est conçu pour des performances optimales à l’aide de la sécurité des points de terminaison et des connexions réseau chiffrées, ce qui réduit la nécessité d’appliquer la sécurité de périmètre. Microsoft 365 centres de données sont situés dans le monde entier et le service est conçu pour utiliser différentes méthodes pour connecter les clients aux meilleurs points de terminaison de service disponibles. Étant donné que les données utilisateur et le traitement sont distribués entre de nombreux centres de données Microsoft, il n’existe aucun point de terminaison réseau unique auquel les machines clientes peuvent se connecter. En fait, les données et les services de votre locataire Microsoft 365 sont optimisés dynamiquement par microsoft Global Network pour s’adapter aux emplacements géographiques à partir desquels ils sont accessibles par les utilisateurs finaux.

Certains problèmes de performances courants sont créés lorsque Microsoft 365 trafic est soumis à l’inspection des paquets et à la sortie centralisée :

- Une latence élevée peut entraîner des performances médiocres des flux vidéo et audio, et une réponse lente de la récupération des données, des recherches, de la collaboration en temps réel, des informations de disponibilité du calendrier, du contenu dans le produit et d’autres services
- La sortie des connexions à partir d’un emplacement central met en échec les fonctionnalités de routage dynamique du Microsoft 365 réseau global, ce qui ajoute une latence et une durée d’aller-retour
- Le déchiffrement du trafic réseau sécurisé par SSL Microsoft 365 et son nouveau chiffrement peuvent entraîner des erreurs de protocole et des risques de sécurité

Le raccourcissement du chemin d’accès réseau à Microsoft 365 points d’entrée en autorisant le trafic client à se rapprocher le plus possible de son emplacement géographique peut améliorer les performances de connectivité et l’expérience de l’utilisateur final dans Microsoft 365. Il peut également aider à réduire l’impact des modifications futures de l’architecture réseau sur les performances et la fiabilité Microsoft 365. Le modèle de connectivité optimal consiste à toujours fournir une sortie réseau à l’emplacement de l’utilisateur, qu’il s’agisse du réseau d’entreprise ou d’emplacements distants tels que la maison, les hôtels, les cafés et les aéroports. Le trafic Internet générique et le trafic réseau d’entreprise basé sur wan seraient routées séparément et n’utiliseraient pas le modèle de sortie directe locale. Ce modèle local de sortie directe est représenté dans le diagramme ci-dessous.

![Architecture du réseau de sortie local.](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

L’architecture de sortie locale présente les avantages suivants pour le trafic de réseau Microsoft 365 par rapport au modèle traditionnel :
  
- Fournit des performances Microsoft 365 optimales en optimisant la longueur de l’itinéraire. Les connexions des utilisateurs finaux sont routées dynamiquement vers le point d’entrée Microsoft 365 le plus proche par l’infrastructure _Distributed Service Front Door_ de Microsoft Global Network, et le trafic est ensuite routé en interne vers les points de terminaison de données et de service via la fibre haute disponibilité à latence très faible de Microsoft.
- Réduit la charge sur l’infrastructure réseau d’entreprise en autorisant la sortie locale pour le trafic Microsoft 365, en contournant les proxys et les appareils d’inspection du trafic.
- Sécurise les connexions aux deux extrémités en appliquant des fonctionnalités de sécurité de point de terminaison client et cloud, évitant ainsi l’application de technologies de sécurité réseau redondantes.

> [!NOTE]
> L’infrastructure _Distributed Service Front Door_ est la périphérie réseau hautement disponible et évolutive de Microsoft Global Network avec des emplacements distribués géographiquement. Il met fin aux connexions des utilisateurs finaux et les achemine efficacement au sein du réseau global Microsoft. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Pour plus d’informations sur la compréhension et l’application Microsoft 365 principes de connectivité réseau, consultez [Microsoft 365 Principes de connectivité réseau](microsoft-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Conclusion

L’optimisation Microsoft 365 performances du réseau revient à éliminer les obstacles inutiles. En traitant Microsoft 365 connexions comme du trafic approuvé, vous pouvez empêcher l’introduction de la latence par l’inspection des paquets et la concurrence pour la bande passante proxy. L’autorisation de connexions locales entre les machines clientes et les points de terminaison Office 365 permet de router dynamiquement le trafic via microsoft Global Network.

## <a name="related-topics"></a>Rubriques connexes

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[URL et plages d’adresses IP Office 365](urls-and-ip-address-ranges.md)

[Service web URL et adresses IP Office 365](microsoft-365-ip-web-service.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Planification réseau et optimisation des performances pour Microsoft 365](network-planning-and-performance.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)

[Réseaux de distribution de contenu](content-delivery-networks.md)

[Test de connectivité Microsoft 365](https://aka.ms/netonboard)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
