---
title: Vue d’ensemble de la connectivité réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- NOCSH
description: Explique pourquoi l’optimisation du réseau est importante pour les services SaaS, l’objectif de Microsoft 365 réseau et comment SaaS nécessite une mise en réseau différente des autres charges de travail.
ms.openlocfilehash: ce9b7f7f8011e0d0b12d9b0524cf540948f7aab8
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58533158"
---
# <a name="microsoft-365-network-connectivity-overview"></a>Microsoft 365 vue d’ensemble de la connectivité réseau

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Microsoft 365 est un cloud SaaS (Software-as-a-Service) distribué qui fournit des scénarios de productivité et de collaboration par le biais d’un ensemble variés de micro-services et d’applications. Les composants clients de Microsoft 365 tels que Outlook, Word et PowerPoint s’exécutent sur les ordinateurs des utilisateurs et se connectent à d’autres composants de Microsoft 365 qui s’exécutent dans les centres de données Microsoft. Le facteur le plus significatif qui détermine la qualité de l’expérience de l’utilisateur final Microsoft 365 est la fiabilité du réseau et une faible latence entre les clients Microsoft 365 et les Microsoft 365 frontaux du service.

Dans cet article, vous allez découvrir les objectifs de la mise en réseau Microsoft 365 et pourquoi la mise en réseau Microsoft 365 nécessite une approche d’optimisation différente de celle du trafic Internet générique.

## <a name="microsoft-365-networking-goals"></a>Microsoft 365 réseau

L’objectif ultime de Microsoft 365 réseau est d’optimiser l’expérience de l’utilisateur final en activant l’accès le moins restrictif entre les clients et les points de terminaison Microsoft 365 les plus proches. La qualité de l’expérience de l’utilisateur final est directement liée aux performances et à la réactivité de l’application que l’utilisateur utilise. Par exemple, Microsoft Teams s’appuie sur une faible latence pour que les appels téléphoniques, les conférences et les collaborations à l’écran partagé soient sans problème, et Outlook repose sur une excellente connectivité réseau pour les fonctionnalités de recherche instantanée qui tirent parti de l’indexation côté serveur et des fonctionnalités d’IA.

L’objectif principal dans la conception du réseau doit être de réduire la latence en réduisant le temps d’aller-retour (RTT) entre les ordinateurs clients et le réseau mondial microsoft, la dorsale principale du réseau public de Microsoft qui interconnecte tous les centres de données Microsoft avec une faible latence et des points d’entrée d’application cloud haute disponibilité répartis dans le monde entier. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

L’optimisation Microsoft 365 performances réseau n’a pas besoin d’être compliquée. Vous pouvez obtenir les meilleures performances possibles en suivant quelques principes clés :

- Identifier le Microsoft 365 réseau
- Autoriser la sortie de la succursale locale Microsoft 365 trafic réseau vers Internet à partir de chaque emplacement où les utilisateurs se connectent Microsoft 365
- Autoriser Microsoft 365 trafic à contourner les proxies et les périphériques d’inspection des paquets

Pour plus d’informations Microsoft 365 principes de connectivité réseau, voir Microsoft 365 principes de [connectivité réseau.](microsoft-365-network-connectivity-principles.md)

## <a name="traditional-network-architectures-and-saas"></a>Architectures réseau traditionnelles et SaaS

Les principes d’architecture réseau traditionnels pour les charges de travail client/serveur sont conçus autour de l’hypothèse que le trafic entre les clients et les points de terminaison ne s’étend pas en dehors du périmètre du réseau d’entreprise. En outre, dans de nombreux réseaux d’entreprise, toutes les connexions Internet sortantes traversent le réseau d’entreprise et sortent d’un emplacement central.

Dans les architectures réseau traditionnelles, une latence plus élevée pour le trafic Internet générique est un compromis nécessaire pour maintenir la sécurité du périmètre du réseau, et l’optimisation des performances pour le trafic Internet implique généralement la mise à niveau ou la montée en main de l’équipement aux points de sortie du réseau. Toutefois, cette approche ne permet pas de répondre aux exigences de performances réseau optimales des services SaaS tels que Microsoft 365.

## <a name="identifying-microsoft-365-network-traffic"></a>Identification du Microsoft 365 réseau

Nous facilitez l’identification Microsoft 365 le trafic réseau et la gestion de l’identification réseau.

- Nouvelles catégories de points de terminaison réseau pour différencier le trafic réseau hautement critique du trafic réseau qui n’est pas impacté par les latentes Internet. Il n’existe qu’une poignée d’URL et d’adresses IP de prise en charge dans la catégorie « Optimiser » la plus critique.
- Services Web pour l’utilisation des scripts ou la configuration directe de l’appareil et la gestion des Microsoft 365'identification réseau. Les modifications sont disponibles à partir du service web, au format RSS ou sur le courrier électronique à l’aide Power Automate modèle.
- [Office 365 programme partenaire](./microsoft-365-networking-partner-program.md) réseau avec des partenaires Microsoft qui fournissent des appareils ou des services qui suivent Microsoft 365 principes de connectivité réseau et ont une configuration simple.

## <a name="securing-microsoft-365-connections"></a>Sécurisation Microsoft 365 connexions

L’objectif de la sécurité réseau traditionnelle est de renforcer le périmètre du réseau de l’entreprise contre les intrusions et les logiciels malveillants. La plupart des réseaux d’entreprise appliquent la sécurité réseau pour le trafic Internet à l’aide de technologies telles que les serveurs proxy, les pare-feu, les coupures et inspections SSL, l’inspection approfondie des paquets et les systèmes de protection contre la perte de données. Ces technologies fournissent une atténuation importante des risques pour les demandes Internet génériques, mais peuvent réduire considérablement les performances, l’évolutivité et la qualité de l’expérience de l’utilisateur final lorsqu’elles sont appliquées aux points de terminaison Microsoft 365.

Microsoft 365 aide à répondre aux besoins de votre organisation en matière de sécurité du contenu et de conformité de l’utilisation des données avec les fonctionnalités de sécurité et de gouvernance intégrées conçues spécifiquement pour les fonctionnalités Microsoft 365 et les charges de travail. Pour plus d’informations sur Microsoft 365 sécurité et conformité, voir la [feuille de route Office 365 sécurité.](/office365/securitycompliance/security-roadmap) Pour plus d’informations sur les recommandations de Microsoft et la position de prise en charge sur les solutions réseau avancées qui effectuent un traitement de niveau avancé sur le trafic Microsoft 365, voir Utilisation de périphériques réseau tiers ou de solutions sur le trafic [Office 365.](https://support.microsoft.com/help/2690045)

## <a name="why-is-microsoft-365-networking-different"></a>Pourquoi la mise Microsoft 365 réseau est-elle différente ?

Microsoft 365 est conçu pour optimiser les performances à l’aide de la sécurité des points de terminaison et des connexions réseau chiffrées, ce qui réduit le besoin d’application de la sécurité de périmètre. Microsoft 365 centres de données sont situés dans le monde entier et le service est conçu pour utiliser différentes méthodes pour connecter les clients aux points de terminaison de service les plus disponibles. Étant donné que les données utilisateur et le traitement sont distribués entre de nombreux centres de données Microsoft, il n’existe pas de point de terminaison réseau unique auquel les ordinateurs clients peuvent se connecter. En fait, les données et les services de votre client Microsoft 365 sont optimisés dynamiquement par le réseau global Microsoft pour s’adapter aux emplacements géographiques à partir des lesquels ils sont accessibles par les utilisateurs finaux.

Certains problèmes de performances courants sont créés lorsque Microsoft 365 trafic est soumis à l’inspection des paquets et à la sortie centralisée :

- Une latence élevée peut entraîner des performances extrêmement médiocres des flux vidéo et audio, et une réponse lente à la récupération des données, aux recherches, à la collaboration en temps réel, aux informations de libre/occupé du calendrier, au contenu du produit et à d’autres services
- La sortie de connexions à partir d’un emplacement central va à l’inverse des capacités de routage dynamique du réseau global Microsoft 365, ce qui ajoute une latence et une durée d’aller-retour
- Le déchiffrement du protocole SSL Microsoft 365 le trafic réseau et le re-chiffrement peut entraîner des erreurs de protocole et présente un risque de sécurité

Le raccourcissement du chemin d’accès réseau vers les points d’entrée Microsoft 365 en permettant au trafic client de s’egresser aussi près que possible de son emplacement géographique peut améliorer les performances de connectivité et l’expérience de l’utilisateur final dans Microsoft 365. Elle peut également aider à réduire l’impact des modifications futures apportées à l’architecture réseau sur Microsoft 365 performances et la fiabilité. Le modèle de connectivité optimal consiste à toujours fournir une sortie réseau à l’emplacement de l’utilisateur, que ce soit sur le réseau de l’entreprise ou sur des emplacements distants tels que la maison, les restaurants, les café et les aéroports. Le trafic Internet générique et le trafic réseau d’entreprise wan sont acheminés séparément et n’utilisent pas le modèle de sortie directe locale. Ce modèle local de sortie directe est représenté dans le diagramme ci-dessous.

![Architecture du réseau de sortie local](../media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

L’architecture de sortie locale présente les avantages suivants pour le trafic de réseau Microsoft 365 par rapport au modèle traditionnel :
  
- Fournit des performances Microsoft 365 optimales en optimisant la longueur de l’itinéraire. Les connexions des utilisateurs finaux sont acheminées dynamiquement vers le point  d’entrée Microsoft 365 le plus proche par l’infrastructure de service frontal distribué du réseau mondial Microsoft, puis le trafic est acheminé en interne vers les points de terminaison de données et de service sur la fibre de haute disponibilité à latence très faible de Microsoft.
- Réduit la charge sur l’infrastructure réseau d’entreprise en permettant la sortie locale du trafic Microsoft 365, en contournant les proxies et les périphériques d’inspection du trafic.
- Sécurisation des connexions aux deux extrémités en tirant parti des fonctionnalités de sécurité de point de terminaison client et de sécurité cloud, en évitant l’application de technologies de sécurité réseau redondantes.

> [!NOTE]
> _L’infrastructure de porte_ principale du service distribué est la périphérie réseau hautement disponible et évolutive du réseau mondial Microsoft avec des emplacements géographiquement distribués. Il met fin aux connexions des utilisateurs finaux et les approvisionnement efficacement au sein du réseau global Microsoft. Si vous souhaitez en savoir plus sur le réseau mondial de Microsoft, consultez l’article [Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Pour plus d’informations sur la compréhension et l’application Microsoft 365 la connectivité réseau, voir Microsoft 365 principes de [connectivité réseau.](microsoft-365-network-connectivity-principles.md)

## <a name="conclusion"></a>Conclusion

L’optimisation Microsoft 365 performances réseau revient vraiment à supprimer les obstacles inutiles. En traitant les connexions Microsoft 365 comme du trafic approuvé, vous pouvez empêcher l’introduction de la latence par l’inspection des paquets et la concurrence pour la bande passante proxy. Autoriser les connexions locales entre les ordinateurs clients et Office 365 points de terminaison permet d’router dynamiquement le trafic via le réseau global Microsoft.

## <a name="related-topics"></a>Voir aussi

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