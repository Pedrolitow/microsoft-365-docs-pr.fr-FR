---
title: 'Mise en réseau (vers le cloud) : l’œuvre d’un architecte'
description: Découvrez comment optimiser votre réseau pour la connectivité cloud en évitant les pièges les plus courants.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 7de9aec29b0a57e85e3539fc2e99384de545c52a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50904635"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Mise en réseau (vers le cloud) : l’œuvre d’un architecte

Dans cet article, [Ed Fisher,](https://www.linkedin.com/in/edfisher/)architecte de sécurité & conformité chez Microsoft, explique comment optimiser votre réseau pour la connectivité cloud en évitant les pièges les plus courants. 

## <a name="about-the-author"></a>À propos de l’auteur

![Photo Ed Fisher](../media/solutions-architecture-center/ed-fisher-networking.jpg) 

Je suis actuellement spécialiste technique principal dans la région Sud-Est et je me concentre sur la sécurité & conformité. J’ai travaillé avec des clients qui sont passés à Office 365 au cours des 10 dernières années. J’ai travaillé avec des boutiques de petite taille avec quelques emplacements pour les agences gouvernementales et les entreprises avec des millions d’utilisateurs répartis dans le monde entier, et de nombreux autres clients entre eux, la majorité ayant des dizaines de milliers d’utilisateurs, plusieurs emplacements dans différentes régions du monde, le besoin d’un niveau de sécurité plus élevé et une multitude d’exigences de conformité. J’ai aidé des centaines d’entreprises et des millions d’utilisateurs à se déplacer vers le cloud en toute sécurité.

Avec une expérience au cours des 25 dernières années qui inclut la sécurité, l’infrastructure et l’ingénierie réseau, et ayant déplacé deux de mes précédents employeurs vers Office 365 avant de rejoindre Microsoft, j’ai été de votre côté du tableau à de nombreuses reprises et ne vous souvenez pas de ce que c’est. Même si deux clients ne sont jamais identiques, la plupart ont des besoins similaires et lorsque vous consommez un service standardisé tel que n’importe quelle plateforme SaaS ou PaaS, les meilleures approches ont tendance à être les mêmes.

## <a name="its-not-the-networkits-how-youre-misusing-it"></a>Il ne s’agit pas du réseau, mais de la façon dont vous l’utilisez (mal) !

Quel que soit le nombre de fois que  cela se produit, il ne m’est jamais difficile de savoir comment les équipes de sécurité créatives et les équipes réseau essaient de se connecter aux services cloud de Microsoft. Il existe toujours une stratégie de sécurité, une norme de conformité ou une meilleure façon pour eux de s’engager sur l’utilisation, sans être disposés à s’engager dans une conversation sur ce qu’ils essaient d’accomplir, ou sur la façon dont ils sont meilleurs, plus faciles, plus rentables et plus performants. 

Lorsque ce genre de chose est resserrée pour moi, j’accepte généralement de relever le défi et de les aider à savoir comment et pourquoi et les obtenir à l’endroit où ils doivent se trouver. Mais si je suis totalement désolé, je dois partager ce que je souhaite parfois leur laisser faire, et revenir pour dire que je vous l’ai dit lorsqu’ils ont finalement concédé qu’il ne fonctionne pas. Je souhaite peut-être le faire parfois, mais ce *n’est pas le cas.* Ce que je fais, c’est essayer d’expliquer tout ce que je vais inclure dans ce billet. Quel que soit votre rôle, si votre organisation souhaite utiliser les services cloud de Microsoft, ce qui suit peut vous aider.

## <a name="guiding-principles"></a>Principes directeurs

Commençons par quelques règles de base relatives à ce que nous faisons ici. Nous abordons la façon de se connecter en toute sécurité aux services cloud pour garantir la complexité minimale et les performances maximales, tout en conservant une sécurité réelle. Rien de ce qui suit n’est contredessant tout cela, même si vous ou votre client, n’êtes pas en mesure d’utiliser votre serveur proxy favori pour tout.

- **Ce n’est pas** parce que vous le pouvez que vous devez : Ou pour parrasser Dr. Dr. Films à partir du film Parcage De Park « ... Oui, oui, mais votre équipe de sécurité était si préoccupé par le fait qu’elle pouvait ou non ne pas s’arrêter de penser s’il le devrait. »
- **La sécurité ne signifie pas de** la complexité : vous n’êtes pas plus sécurisé simplement parce que vous dépensez plus d’argent, que vous passez par plusieurs appareils ou que vous cliquez sur d’autres boutons.
- **Office 365 est accessible sur Internet**: mais ce n’est pas la même chose qu’Office 365'internet. Il s’agit d’un service SaaS géré par Microsoft et géré par vous. Contrairement aux sites web que vous visitez sur Internet, vous êtes en réalité en train de jeter un œil à la réalité et vous pouvez appliquer les contrôles dont vous avez besoin pour respecter vos stratégies et vos normes de conformité, tant que vous comprenez que même si vous pouvez atteindre vos objectifs, vous devrez peut-être simplement les faire d’une autre manière.
- Les points de terminaison sont mauvais, les **coupures localisées** sont bonnes : tout le monde veut toujours retourner tout son trafic Internet pour tous ses utilisateurs vers un point central, généralement pour pouvoir la surveiller et appliquer la stratégie, mais souvent parce qu’il est moins coûteux que de mettre en service l’accès à Internet à tous ses emplacements, ou c’est simplement la façon dont ils le font. Mais ces points de terminaison sont exactement comme cela... points où le trafic se pointe. Il n’y a rien de mal à empêcher vos utilisateurs de naviguer vers Streaming ou de diffuser en continu des vidéos cat, mais ne traitez pas votre trafic d’application métier critique de la même manière.
- Si **DNS n’est pas satisfait, il n’est** pas satisfait : le réseau le mieux conçu peut être mis en cache par un DNS médiocre, que ce soit en récursant des demandes à des serveurs dans d’autres régions du monde ou en utilisant les serveurs DNS de votre isp ou d’autres serveurs DNS publics qui cachent les informations de résolution DNS.
- Le simple fait que vous utilisiez cette technique ne signifie pas que vous devez le faire maintenant : la technologie change constamment et Office 365 **n’est** pas une exception. L’application de mesures de sécurité développées et déployées pour des services locaux ou pour contrôler la sécurité web ne fournira pas le même niveau d’assurance de sécurité et peut avoir un impact négatif significatif sur les performances.
- **Office 365 a été conçu pour être accessible sur Internet**: il s’agit d’un résumé. Quelle que soit la relation entre vos utilisateurs et votre périphérie, le trafic passe toujours par Internet une fois qu’il quitte votre réseau et avant d’être sur le notre. Même si vous utilisez Azure ExpressRoute pour router du trafic sensible de latence de votre réseau directement vers le notre, la connectivité Internet est absolument nécessaire. Acceptez-le. Ne le suressoyez pas.

## <a name="where-bad-choices-are-often-made"></a>L’endroit où les choix sont souvent effectués

Bien qu’il existe de nombreux endroits où de mauvaises décisions sont prises au nom de la sécurité, ce sont celles que je rencontre le plus souvent avec les clients. De nombreuses conversations client impliquent toutes ces questions en même temps.

### <a name="insufficient-resources-at-the-edge"></a>Ressources insuffisantes au niveau du bord

Très peu de clients déploient des environnements verts et ils ont des années d’expérience dans le fonctionnement de leurs utilisateurs et leur sortie Internet. Que les clients utilisent des serveurs proxy ou autorisent l’accès direct et simplement le trafic sortant NAT, ils le font depuis des années et ne réfléchissent pas à la quantité d’informations qu’ils vont utiliser pour commencer à se déplacer sur leur serveur edge à mesure qu’ils déplacent des applications internes vers le cloud.

La bande passante est toujours un problème, mais les périphériques NAT peuvent ne pas être suffisamment puissants pour gérer la charge accrue et commencer à fermer prématurément les connexions pour libérer des ressources. La plupart des logiciels clients qui se connectent à Office 365 s’attendent à des connexions persistantes et un utilisateur utilisant pleinement Office 365 peut avoir 32 connexions simultanées ou plus. Si l’appareil NAT les dépose prématurément, ces applications risquent de ne plus être résponsives lorsqu’elles tentent d’utiliser les connexions qui n’y sont plus. Lorsqu’ils abandonnent et tentent d’établir de nouvelles connexions, ils donnent encore plus de charge à votre engrenage réseau.

### <a name="localized-breakout"></a>Breakout localisée

Tout le reste de cette liste revient à une chose : sortir de votre réseau et sur le notre aussi rapidement que possible. La rétrogradation du trafic de vos utilisateurs vers un point de sortie central, en particulier lorsque ce point de sortie se trouve dans une autre région que celle de vos utilisateurs, introduit une latence inutile et a un impact à la fois sur l’expérience client et les vitesses de téléchargement. Microsoft dispose de points de présence dans le monde entier avec des serveurs frontaux pour tous nos services  et l’peering établi avec pratiquement tous les principaux isP, de sorte que le routage du trafic de vos utilisateurs localement garantit qu’il arrive rapidement sur notre réseau avec une latence minimale.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>Le trafic de résolution DNS doit suivre le chemin de sortie Internet

Bien entendu, pour qu’un client trouve un point de terminaison, il doit utiliser DNS. Les serveurs DNS de Microsoft évaluent la source des demandes DNS pour s’assurer que nous renvoyons la réponse qui est, en termes Internet, la plus proche de la source de la demande. Assurez-vous que votre DNS est configuré pour que les demandes de résolution de noms sortent du même chemin que le trafic de vos utilisateurs, de sorte que vous leur donnez une sortie locale, mais vers un point de terminaison dans une autre région. Cela signifie que vous laissez les serveurs DNS locaux « aller à la racine » plutôt que de les faire passer vers des serveurs DNS situés dans des centres de données distants. Et surveillez les services DNS publics et privés, qui peuvent mettre en cache les résultats d’une partie du monde et les servir aux demandes provenant d’autres régions du monde.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Pour proxyer ou non proxy, c’est la question

L’une des premières choses à prendre en compte est de savoir s’il faut proxyer les connexions des utilisateurs Office 365. Celui-ci est facile ; ne pas proxy. Office 365 est accessible via Internet, mais il ne s’agit pas d’Internet. Il s’agit d’une extension de vos services principaux et doit être traitée comme telle. Tout ce que vous souhaitez peut-être qu’un proxy, comme la DLP, le logiciel anti-programme malveillant ou l’inspection du contenu, soit déjà disponible dans le service, soit utilisé à grande échelle et sans avoir à déchiffrer les connexions chiffrées par TLS. Mais si vous souhaitez vraiment proxy trafic que vous ne pouvez pas autrement contrôler, faites attention à nos conseils et les [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) catégories de trafic à [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) . Nous avons trois catégories de trafic pour Office 365. Optimiser et autoriser doit vraiment aller directement et contourner votre proxy. La valeur par défaut peut être resserée par proxi. Les détails sont dans ces documents... lisez-les.

La plupart des clients qui demandent l’utilisation d’un proxy, lorsqu’ils voient réellement ce qu’ils font, se rendent compte que lorsque le client effectue une demande HTTP CONNECT au proxy, le proxy n’est plus qu’un routeur supplémentaire coûteux. Les protocoles utilisés tels que MAPI et RTC ne sont même pas des protocoles que les proxies web comprennent. Ainsi, même avec la fissuration TLS, vous n’êtes pas vraiment en mesure d’obtenir une sécurité supplémentaire. Vous *avez une* latence supplémentaire. Pour [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) plus d’informations, notamment sur les catégories Optimiser, Autoriser et Par défaut, Microsoft 365 trafic.

Enfin, prenons en compte l’impact global sur le proxy et sa réponse correspondante pour gérer cet impact. À mesure que de plus en plus de connexions sont réalisées via le proxy, cela peut réduire le facteur d’échelle TCP afin de ne pas avoir à mettre en mémoire tampon autant de trafic. J’ai vu des clients où leurs proxies étaient si surchargés qu’ils utilisaient un facteur d’échelle de 0. Étant donné que le facteur d’échelle est une valeur exponentielle et que nous aimez utiliser 8, chaque réduction de la valeur Scale Factor a un impact négatif considérable sur le débit.

Inspection TLS signifie SÉCURITÉ ! Mais pas vraiment ! De nombreux clients ayant des proxies souhaitent les utiliser pour inspecter tout le trafic, ce qui signifie que TLS « casse et inspecte ». Lorsque vous le faites pour un site web accédé sur HTTPS (problèmes de confidentialité nonobstant), votre proxy peut avoir à le faire pour 10, voire 20 flux simultanés pendant quelques centaines de millisecondes. S’il existe un téléchargement important ou peut-être une vidéo impliquée, une ou plusieurs de ces connexions peuvent durer beaucoup plus longtemps, mais dans l’ensemble, la plupart de ces connexions établissent, transfèrent et se ferment très rapidement. En cas de coupure et d’inspection, le proxy doit doubler le travail. Pour chaque connexion entre le client et le proxy, le proxy doit également effectuer une connexion distincte au point de terminaison. Ainsi, 1 devient 2, 2 devient 4, 32 devient 64... voir où je vais ? Vous avez probablement dimensionisé votre solution proxy pour une solution web classique, mais lorsque vous essayez de faire la même chose pour les connexions client à Office 365, le nombre de connexions simultanées à durée de vie longue peut être un ordre de magnitude supérieur à ce que vous avez dimensioné.

### <a name="streaming-isnt-important-except-that-it-is"></a>La diffusion en continu n’est pas importante, sauf que *c’est le cas*

Les seuls services dans Office 365 qui utilisent UDP sont Skype (bientôt retiré) et Microsoft Teams. Teams utilise UDP pour le trafic de diffusion en continu, y compris l’audio, la vidéo et le partage de présentation. Le trafic de diffusion en continu est en direct, par exemple lorsque vous avez une réunion en ligne avec des présentations vocales, vidéo et des présentations ou des démonstrations. Ceux-ci utilisent UDP car si des paquets sont supprimés ou arrivent dans l’ordre, il est pratiquement insérezable par l’utilisateur et le flux peut simplement continuer.

Lorsque vous n’autorisez pas le trafic UDP sortant des clients vers le service, ils peuvent revenir au protocole TCP. Toutefois, si un paquet TCP est *supprimé,* tout s’arrête jusqu’à ce que le délai d’expiration de la retransmission expire et que le paquet manquant puisse être retransmis. Si un paquet arrive dans l’ordre, tout s’arrête jusqu’à ce que les autres paquets arrivent et peuvent être réassemblés dans l’ordre. Les deux entraînent des problèmes perceptibles dans l’audio (vous vous souvenez de Max Headroom ?) et de la vidéo (avez-vous cliqué sur quelque chose... Il en est ainsi) et entraîne des performances médiocres et une mauvaise expérience utilisateur. Et vous souvenez-vous de ce que j’ai placé ci-dessus sur les proxies ? Lorsque vous forcez un client Teams à utiliser un proxy, vous le forcez à utiliser le protocole TCP. Vous êtes donc deux fois à l’origine d’un impact négatif sur les performances.

### <a name="split-tunneling-may-seem-scary"></a>La tunnellation fractionner peut sembler sombre

Mais ce n’est pas le cas. Toutes les connexions à Office 365 sont sur TLS. Nous proposons TLS 1.2 depuis un certain temps et nous allons bientôt désactiver les versions antérieures, car les clients hérités les utilisent toujours et c’est un risque.

Le fait de forcer une connexion TLS, ou 32 d’entre elles, à passer par un VPN avant de passer au service n’ajoute pas de sécurité. Elle ajoute de la latence et réduit le débit global. Dans certaines solutions VPN, cela force même UDP à tunneler via TCP, ce qui aura à nouveau un impact très négatif sur le trafic de diffusion en continu. Et, sauf si vous faites une inspection TLS, il n’y a aucun inconvénient, c’est tout l’inconvénient. L’un des thèmes les plus courants chez les clients, maintenant que la plupart de leurs employés sont distants, est qu’ils voient un impact significatif sur la bande passante et les performances en faisant en sorte que tous leurs utilisateurs se connectent à l’aide d’un VPN, au lieu de configurer le tunneling fractionnel pour l’accès aux points de terminaison de catégorie [optimiser Office 365.](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories)

Il s’agit d’un correctif simple pour la tunnellation fractionner et c’est l’une des choses que vous devez faire. Pour plus d’informations, veillez à consulter Optimiser la Office 365 pour les utilisateurs distants à l’aide de [la tunneling fractionnement VPN.](../enterprise/microsoft-365-vpn-split-tunnel.md)

## <a name="the-sins-of-the-past"></a>L’expérience du passé

Bien souvent, les mauvaises décisions proviennent d’une combinaison (1) de non-connaissance du fonctionnement du service, (2) d’une tentative d’adhésion aux stratégies d’entreprise écrites avant l’adoption du cloud et (3) d’équipes de sécurité qui ne sont peut-être pas faciles à comprendre qu’il existe plusieurs façons d’atteindre leurs objectifs. Nous espérons que les liens ci-dessus vous aideront pour la première. Le soutien exécutif peut être requis pour passer au-delà de la seconde. La protection des objectifs des stratégies de sécurité, plutôt que leurs méthodes, est utile avec le troisième. De l’accès conditionnel à la modération de contenu, de la protection contre la protection des informations, de la validation des points de terminaison aux menaces zero-day, tout objectif final qu’une stratégie de sécurité raisonnable peut avoir peut être atteint avec ce qui est disponible dans Office 365 et sans dépendance vis-à-vis de l’engrenage réseau local, des tunnel VPN forcés et des coupures et inspections TLS.

D’autres fois, le matériel qui a été dimensionnée et achetée avant que l’organisation ne commence à passer au cloud ne peut simplement pas être mis à l’échelle pour gérer les nouveaux modèles et charges de trafic. Si vous devez véritablement router tout le trafic via un point de sortie unique et/ou le proxy, soyez prêt à mettre à niveau l’équipement réseau et la bande passante en conséquence. Surveillez attentivement l’utilisation sur les deux, car l’expérience ne diminue pas lentement à mesure que de plus en plus d’utilisateurs sont intégrés. Tout se passera bien jusqu’à ce que le point de conseil soit atteint, tout le monde en sera atteint.

## <a name="exceptions-to-the-rules"></a>Exceptions aux règles

Si votre organisation nécessite des [restrictions](/azure/active-directory/manage-apps/tenant-restrictions)de client, vous devez utiliser un proxy avec une coupure TLS et une inspection pour forcer un certain trafic via le proxy, mais vous n’avez pas à forcer tout le trafic à le traverser.  Il ne s’agit pas d’une proposition tout ou rien. Soyez donc attentif aux modifications que doit modifier le proxy.

Si vous comptez autoriser la tunnelisation fractionnée, mais également utiliser un proxy pour le trafic web général, assurez-vous que votre fichier PAC définit ce qui doit être directement défini, ainsi que la façon dont vous définissez le trafic intéressant pour ce qui passe par le tunnel VPN. Nous proposons des exemples de fichiers PAC [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) qui facilitent cette gestion.

## <a name="conclusion"></a>Conclusion

Des dizaines de milliers d’organisations, y compris la quasi-totalité des Classements 500, utilisent Office 365 tous les jours pour leurs fonctions critiques de mission. Ils le font en toute sécurité, et sur Internet.

Quels que soient les objectifs de sécurité que vous avez en jeu, il existe des moyens d’y parvenir qui ne nécessitent pas de connexions VPN, de serveurs proxy, d’analyse et d’inspection TLS ou de sortie Internet centralisée pour récupérer le trafic de vos utilisateurs hors de votre réseau et sur le notre aussi rapidement que possible, ce qui offre les meilleures performances, que votre réseau soit le siège social de l’entreprise ou non. , un bureau à distance ou cet utilisateur travaillant à la maison. Nos instructions sont basées sur la façon dont les services Office 365 sont créés et pour garantir une expérience utilisateur sécurisée et performante.

## <a name="further-reading"></a>Lecture supplémentaire

[Principes Office 365 la connectivité réseau](../enterprise/microsoft-365-network-connectivity-principles.md)

[URL et plages d’adresses IP Office 365](../enterprise/urls-and-ip-address-ranges.md)

[Gestion des points de terminaison Office 365](../enterprise/managing-office-365-endpoints.md)

[Service web URL et adresses IP Office 365](../enterprise/microsoft-365-ip-web-service.md)

[Évaluation de la connectivité réseau Office 365](../enterprise/assessing-network-connectivity.md)

[Paramétrage des performances et du réseau Office 365](../enterprise/network-planning-and-performance.md)

[Évaluation de la connectivité réseau Office 365](../enterprise/assessing-network-connectivity.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](../enterprise/performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](../enterprise/performance-troubleshooting-plan.md)

[Réseaux de distribution de contenu](../enterprise/content-delivery-networks.md)

[Test de connectivité Microsoft 365](https://connectivity.office.com/)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 pour les utilisateurs distants à l’aide de la tunneling fractionnement VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)