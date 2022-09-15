---
title: 'Mise en réseau (vers le cloud) : point de vue d’un architecte'
description: Découvrez comment optimiser votre réseau pour la connectivité cloud en évitant les pièges les plus courants.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-identity-device-management
- M365-security-compliance
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: b9e6069165d39e5e27d47c69e1cfba08b1a94f4c
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730372"
---
# <a name="networking-up-to-the-cloudone-architects-viewpoint"></a>Mise en réseau (vers le cloud) : point de vue d’un architecte

Dans cet article, [Ed Fisher](https://www.linkedin.com/in/edfisher/), Architecte sécurité & conformité chez Microsoft, explique comment optimiser votre réseau pour la connectivité cloud en évitant les pièges les plus courants.

## <a name="about-the-author"></a>À propos de l’auteur

![Photo d’Ed Fisher.](../media/solutions-architecture-center/ed-fisher-networking.jpg)

Je suis actuellement un spécialiste technique principal de notre équipe de vente au détail et de biens de consommation, en me concentrant sur la sécurité & conformité. J’ai travaillé avec des clients qui ont déménagé à Office 365 au cours des dix dernières années. J’ai travaillé avec des petits magasins avec une poignée d’emplacements pour les agences gouvernementales et les entreprises avec des millions d’utilisateurs répartis dans le monde entier, et beaucoup d’autres clients entre, avec la majorité ayant des dizaines de milliers d’utilisateurs, plusieurs emplacements dans différentes parties du monde, la nécessité d’un plus haut degré de sécurité, et une multitude d’exigences de conformité. J’ai aidé des centaines d’entreprises et des millions d’utilisateurs à migrer vers le cloud en toute sécurité.

Avec un arrière-plan au cours des 25 dernières années qui inclut la sécurité, l’infrastructure et l’ingénierie réseau, et ayant déplacé deux de mes anciens employeurs à Office 365 avant de rejoindre Microsoft, j’ai été de votre côté de la table beaucoup de fois, et ne me souviens de ce que c’est comme. Bien qu’il n’y ait jamais deux clients identiques, la plupart ont des besoins similaires, et lorsque vous consommez un service standardisé tel qu’une plateforme SaaS ou PaaS, les meilleures approches ont tendance à être les mêmes.

## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Ce n’est pas le réseau , c’est la façon dont vous l’utilisez (mal) !

Peu importe le nombre de fois où cela se produit, il ne manque jamais de m’étonner de la façon dont les équipes de sécurité *créatives* et de mise en réseau essaient d’obtenir avec la façon dont ils pensent qu’ils doivent se connecter aux services cloud Microsoft. Il existe toujours une stratégie de sécurité, une norme de conformité ou une meilleure façon d’utiliser, sans être disposés à engager une conversation sur ce qu’ils essaient d’accomplir ou *sur la façon dont* il existe de meilleures méthodes, plus faciles, plus rentables et plus performantes.

Quand ce genre de chose est remonté à moi, je suis généralement prêt à relever le défi et de les guider à travers le hows et les pourquoi et les amener à l’endroit où ils ont besoin d’être. Mais si je suis totalement franc, je dois partager que parfois, je veux juste les laisser faire ce qu’ils feront, et revenir pour dire que je vous l’ai dit quand ils ont finalement concédé que cela ne fonctionne pas. Je veux peut-être faire ça parfois, mais je *ne le fais pas*. Ce que je fais est d’essayer d’expliquer tout ce que je vais inclure dans ce post. Quel que soit votre rôle, si votre organisation souhaite utiliser les services cloud Microsoft, il y a probablement une certaine sagesse dans ce qui suit qui peut vous aider.

## <a name="guiding-principles"></a>Principes directeurs

Commençons par des règles de base sur ce que nous faisons ici. Nous discutons de la façon de se connecter en toute sécurité aux services cloud pour garantir la complexité minimale et les performances maximales, tout en maintenant une sécurité réelle. Rien de ce qui suit n’est contraire à tout cela, même si vous, ou votre client, ne pourrez pas utiliser votre serveur proxy favori pour tout.

- **Juste parce que vous pouvez, ne signifie pas que vous devriez**: Ou pour paraphraser le Dr. Ian Malcolm du film De Parc de Jurassique « ... Ouais, oui, mais votre équipe de sécurité était si préoccupée par le fait qu’elle pouvait ou non qu’elle ne s’arrêtait pas pour penser si c’était le cas.
- **La sécurité ne signifie pas la complexité** : vous n’êtes pas plus sécurisé simplement parce que vous dépensez plus d’argent, que vous parcourez plus d’appareils ou que vous cliquez sur d’autres boutons.
- **Office 365 est accessible via Internet** : Mais ce n’est pas la même chose que Office 365 est Internet. Il s’agit d’un service SaaS géré par Microsoft et administré par vous. Contrairement aux sites web que vous visitez sur Internet, vous avez effectivement l’accès à lire derrière le rideau, et peut appliquer les contrôles dont vous avez besoin pour répondre à vos stratégies et vos normes de conformité, aussi longtemps que vous comprenez que, bien que vous pouvez atteindre vos objectifs, vous pouvez simplement avoir à les faire d’une manière différente.
- Les points d’étranglement **sont mauvais, les pannes localisées sont bonnes** : tout le monde veut toujours remettre en état tout son trafic Internet pour tous ses utilisateurs vers un point central, généralement pour qu’ils puissent la surveiller et appliquer la stratégie, mais souvent parce que c’est soit moins cher que de provisionner l’accès à Internet dans tous leurs emplacements, ou c’est juste comment ils le font. Mais ces points d’étranglement sont exactement cela... points où le trafic s’étrangle. Il n’y a rien de mal à empêcher vos utilisateurs de naviguer vers Instagram ou de diffuser en continu des vidéos de chat, mais ne traitez pas le trafic de votre application métier critique de la même façon.
- **Si DNS n’est pas heureux, rien n’est heureux** : le réseau le mieux conçu peut être bousculé par un DNS médiocre, que ce soit en récursifant les demandes adressées aux serveurs d’autres régions du monde ou en utilisant les serveurs DNS de votre fournisseur de services Internet ou d’autres serveurs DNS publics qui mettent en cache les informations de résolution DNS.
- **Ce n’est pas parce que c’est comme ça que vous** l’avez fait maintenant : la technologie change constamment et Office 365 ne fait pas exception. L’application de mesures de sécurité qui ont été développées et déployées pour des services locaux ou pour contrôler le web surf ne va pas fournir le même niveau d’assurance de sécurité et peut avoir un impact négatif significatif sur les performances.
- **Office 365 a été conçu pour être accessible via Internet**: C’est tout en un mot. Peu importe ce que vous voulez faire entre vos utilisateurs et votre périmètre, le trafic passe toujours par Internet une fois qu’il quitte votre réseau et avant qu’il arrive sur le nôtre. Même si vous utilisez Azure ExpressRoute pour acheminer un trafic sensible à la latence de votre réseau directement vers le nôtre, la connectivité Internet est absolument nécessaire. Acceptez-le. Ne vous en faites pas trop.

## <a name="where-bad-choices-are-often-made"></a>Où les mauvais choix sont souvent faits

Alors qu’il ya beaucoup d’endroits où les mauvaises décisions sont prises au nom de la sécurité, ce sont ceux que je rencontre le plus souvent avec les clients. De nombreuses conversations avec les clients impliquent toutes ces conversations à la fois.

### <a name="insufficient-resources-at-the-edge"></a>Ressources insuffisantes à la périphérie

Très peu de clients déploient des environnements greenfield, et ils ont des années d’expérience avec le fonctionnement de leurs utilisateurs et ce que leur sortie Internet est comme. Que les clients disposent de serveurs proxy ou autorisent l’accès direct et simplement le trafic sortant NAT, ils le font depuis des années et ne se demandent pas à quel point ils vont commencer à pomper à travers leur périmètre lorsqu’ils déplacent traditionnellement des applications internes vers le cloud.

La bande passante est toujours un problème, mais les appareils NAT peuvent ne pas avoir suffisamment de puissance pour gérer la charge accrue et peuvent commencer à fermer prématurément les connexions pour libérer des ressources. La plupart des logiciels clients qui se connectent à Office 365 s’attend à des connexions persistantes et un utilisateur qui utilise entièrement Office 365 peut avoir 32 connexions simultanées ou plus. Si l’appareil NAT les supprime prématurément, ces applications risquent de ne plus répondre lorsqu’elles essaient d’utiliser les connexions qui n’y sont plus. Quand ils abandonnent et essaient d’établir de nouvelles connexions, ils mettent encore plus de charge sur votre équipement réseau.

### <a name="localized-breakout"></a>Cassure localisée

Tout le reste de cette liste se résume à une chose : la sortie de votre réseau et le nôtre le plus rapidement possible. Le fait de rebasculer le trafic de vos utilisateurs vers un point de sortie central, en particulier lorsque ce point de sortie se trouve dans une autre région que celle où se trouvent vos utilisateurs, introduit une latence inutile et affecte à la fois l’expérience client et les vitesses de téléchargement. Microsoft dispose de points de présence dans le monde entier avec des serveurs frontaux pour tous nos services et le peering établi avec pratiquement tous les principaux isp. Par conséquent, le routage du trafic de vos utilisateurs *localement* garantit qu’il arrive rapidement dans notre réseau avec une latence minimale.

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>Le trafic de résolution DNS doit suivre le chemin de sortie Internet

Bien sûr, pour qu’un client trouve un point de terminaison, il doit utiliser DNS. Les serveurs DNS de Microsoft évaluent la source des demandes DNS pour s’assurer que nous renvoyons la réponse qui est, en termes Internet, la plus proche de la source de la requête. Assurez-vous que votre DNS est configuré afin que les demandes de résolution de noms s’exécutent sur le même chemin que le trafic de vos utilisateurs, de peur que vous leur donniez une sortie locale, mais vers un point de terminaison dans une autre région. Cela signifie que vous laissez les serveurs DNS locaux « aller à la racine » plutôt que de les transférer vers des serveurs DNS dans des centres de données distants. Et faites attention aux services DNS publics et privés, qui peuvent mettre en cache les résultats d’une partie du monde et les servir aux demandes d’autres parties du monde.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Pour le proxy ou non pour le proxy, c’est la question

L’une des premières choses à prendre en compte est de savoir s’il faut proxyer les connexions des utilisateurs à Office 365. Celui-là est facile; ne pas proxy. Office 365 est accessible via Internet, mais ce n’est pas L’Internet. Il s’agit d’une extension de vos principaux services et doit être traitée comme telle. Tout ce que vous pouvez souhaiter qu’un proxy fasse, tel que DLP, anti-programme malveillant ou inspection de contenu, est déjà disponible dans le service et peut être utilisé à grande échelle et sans avoir à déchiffrer les connexions chiffrées par TLS. Mais si vous voulez vraiment proxy du trafic que vous ne pouvez pas autrement contrôler, faites attention à nos conseils et [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) les catégories de trafic à [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md). Nous avons trois catégories de trafic pour Office 365. Optimiser et autoriser doit vraiment aller directement et contourner votre proxy. La valeur par défaut peut être transmise. Les détails sont dans ces documents... les lire.

La plupart des clients qui insiste sur l’utilisation d’un proxy, quand ils regardent réellement ce qu’ils font, viennent à se rendre compte que lorsque le client effectue une requête HTTP CONNECT au proxy, le proxy est maintenant juste un routeur supplémentaire coûteux. Les protocoles utilisés tels que MAPI et RTC ne sont même pas des protocoles que les proxys web comprennent, de sorte que même avec le craquage TLS, vous n’obtenez pas vraiment de sécurité supplémentaire. Vous obtenez une latence supplémentaire. Pour [https://aka.ms/pnc](../enterprise/microsoft-365-network-connectivity-principles.md) plus d’informations, notamment les catégories Optimiser, Autoriser et Par défaut pour le trafic Microsoft 365.

Enfin, tenez compte de l’impact global sur le proxy et de sa réponse correspondante pour gérer cet impact. À mesure que de plus en plus de connexions sont établies via le proxy, cela peut réduire le facteur d’échelle TCP afin qu’il n’ait pas à mettre en mémoire tampon autant de trafic. J’ai vu des clients où leurs proxys étaient tellement surchargés qu’ils utilisaient un facteur d’échelle de 0. Étant donné que Scale Factor est une valeur exponentielle et que nous aimons utiliser 8, chaque réduction de la valeur du facteur d’échelle est un impact négatif énorme sur le débit.

L’inspection TLS signifie SÉCURITÉ ! Mais pas vraiment ! De nombreux clients disposant de proxys souhaitent les utiliser pour inspecter tout le trafic, ce qui signifie que TLS « arrête et inspecte ». Lorsque vous effectuez cette opération pour un site web accessible via HTTPS (nonobstant les problèmes de confidentialité), votre proxy peut avoir à le faire pour 10 ou même 20 flux simultanés pendant quelques centaines de millisecondes. S’il y a un téléchargement important ou peut-être une vidéo impliquée, une ou plusieurs de ces connexions peuvent durer beaucoup plus longtemps, mais dans l’ensemble, la plupart de ces connexions établissent, transfèrent et se ferment très rapidement. L’arrêt et l’inspection signifient que le proxy doit doubler le travail. Pour chaque connexion du client au proxy, le proxy doit également établir une connexion distincte au point de terminaison. Ainsi, 1 devient 2, 2 devient 4, 32 devient 64 ... voir où je vais? Vous avez probablement dimensionné votre solution proxy très bien pour le web surf classique, mais quand vous essayez de faire la même chose pour les connexions clientes à Office 365, le nombre de connexions simultanées à long terme peut être des ordres de grandeur supérieurs à ce que vous avez dimensionné pour.

### <a name="streaming-isnt-important-except-that-it-is"></a>Le streaming n’est pas important, sauf qu’il *est*

Les seuls services dans Office 365 qui utilisent UDP sont Skype (bientôt mis hors service) et Microsoft Teams. Teams utilise UDP pour la diffusion en continu du trafic, y compris le partage audio, vidéo et de présentation. Le trafic de diffusion en continu est en direct, par exemple lorsque vous organisez une réunion en ligne avec la voix, la vidéo, et présentez des présentations ou effectuez des démonstrations. Ceux-ci utilisent UDP, car si les paquets sont supprimés ou arrivent dans l’ordre, il est quasiment imperceptible par l’utilisateur et le flux peut simplement continuer.

Lorsque vous n’autorisez pas le trafic UDP sortant des clients vers le service, ils peuvent revenir à l’utilisation de TCP. Toutefois, si un paquet TCP est supprimé, *tout s’arrête* jusqu’à ce que le délai de retransmission (RTO) expire et que le paquet manquant puisse être retransmis. Si un paquet arrive dans l’ordre, tout s’arrête jusqu’à ce que les autres paquets arrivent et puissent être réassemblés dans l’ordre. Les deux entraînent des problèmes perceptibles dans l’audio (rappelez-vous Max Headroom?) et vidéo (avez-vous cliqué sur quelque chose... oh, il est là) et conduire à des performances médiocres et une mauvaise expérience utilisateur. Et rappelez-vous ce que j’ai mis au-dessus de proxys? Lorsque vous forcez un client Teams à utiliser un proxy, vous le forcez à utiliser TCP. Vous êtes donc à l’origine de deux impacts négatifs sur les performances.

### <a name="split-tunneling-may-seem-scary"></a>Le tunneling fractionné peut sembler effrayant

Mais ce n’est pas le cas. Toutes les connexions à Office 365 sont sur TLS. Nous offrons TLS 1.2 depuis un certain temps maintenant et nous désactivons bientôt les versions antérieures, car les clients hérités les utilisent toujours et cela représente un risque.

Le fait de forcer une connexion TLS, ou 32 d’entre elles, à passer par un VPN avant d’accéder au service n’ajoute pas de sécurité. Il ajoute une latence et réduit le débit global. Dans certaines solutions VPN, il force même UDP à tunneliser via TCP, ce qui aura à nouveau un impact très négatif sur le trafic de streaming. Et, sauf si vous effectuez l’inspection TLS, il n’y a aucun avantage, tous les inconvénients. Un thème très courant parmi les clients, maintenant que la plupart de leur personnel est distant, est qu’ils constatent des impacts significatifs sur la bande passante et les performances en faisant en sorte que tous leurs utilisateurs se connectent à l’aide d’un VPN, au lieu de configurer le tunneling fractionné pour l’accès à [la catégorie Optimiser Office 365 points de terminaison](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

Il s’agit d’une solution simple pour effectuer le tunneling fractionné et c’est une solution que vous devez faire. Pour plus d’informations, veillez à consulter [Optimiser la connectivité Office 365 pour les utilisateurs distants à l’aide du tunneling fractionné VPN](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="the-sins-of-the-past"></a>Les péchés du passé

Souvent, la raison pour laquelle les mauvais choix sont faits provient d’une combinaison de (1) ne sachant pas comment le service fonctionne, (2) essayant d’adhérer aux stratégies d’entreprise qui ont été écrites avant d’adopter le cloud, et (3) les équipes de sécurité qui peuvent ne pas être facilement convaincus qu’il existe plusieurs façons d’atteindre leurs objectifs. J’espère que ce qui précède, et les liens ci-dessous, vous aideront avec le premier. Le parrainage de la direction peut être nécessaire pour passer la seconde. L’adressage des objectifs des stratégies de sécurité, plutôt que de leurs méthodes, permet d’atteindre le troisième objectif. De l’accès conditionnel à la modération du contenu, de la protection des données à la protection des informations, de la validation des points de terminaison aux menaces zero-day : tout objectif final qu’une stratégie de sécurité raisonnable peut avoir peut être atteint avec ce qui est disponible dans Office 365 et sans aucune dépendance vis-à-vis de l’équipement réseau local, des tunnels VPN forcés et des interruptions et inspections TLS.

Dans d’autres cas, le matériel qui a été dimensionné et acheté avant que l’organisation ne commence à passer au cloud ne peut tout simplement pas être mis à l’échelle pour gérer les nouveaux modèles et charges de trafic. Si vous devez vraiment acheminer tout le trafic via un point de sortie unique et/ou le proxy, préparez-vous à mettre à niveau l’équipement réseau et la bande passante en conséquence. Surveillez attentivement l’utilisation des deux, car l’expérience ne diminuera pas lentement à mesure que davantage d’utilisateurs sont intégrés. Tout ira bien jusqu’à ce que le point de basculement soit atteint, alors tout le monde souffre.

## <a name="exceptions-to-the-rules"></a>Exceptions aux règles

Si votre organisation requiert [des restrictions de locataire](/azure/active-directory/manage-apps/tenant-restrictions), vous devez utiliser un proxy avec arrêt TLS et inspecter pour forcer un certain trafic via le proxy, mais vous n’avez pas à forcer tout le trafic via celui-ci.  Il ne s’agit pas d’une proposition tout ou rien, alors faites attention à ce qui doit être modifié par le proxy.

Si vous souhaitez autoriser le tunneling fractionné mais également utiliser un proxy pour le trafic web général, assurez-vous que votre fichier PAC définit ce qui doit être direct, ainsi que la façon dont vous définissez le trafic intéressant pour ce qui passe par le tunnel VPN. Nous proposons des exemples de fichiers PAC qui [https://aka.ms/ipaddrs](../enterprise/urls-and-ip-address-ranges.md) faciliteront la gestion.

## <a name="conclusion"></a>Conclusion

Des dizaines de milliers d’organisations, dont presque toutes les fortunes 500, utilisent Office 365 tous les jours pour leurs fonctions stratégiques. Ils le font en toute sécurité, et ils le font sur Internet.

Quels que soient les objectifs de sécurité que vous avez en jeu, il existe des moyens de les atteindre qui ne nécessitent pas de connexions VPN, de serveurs proxy, d’interruption et d’inspection TLS, ou de sortie Internet centralisée pour que le trafic de vos utilisateurs hors de votre réseau et vers le nôtre aussi rapidement que vous le pouvez, ce qui offre les meilleures performances, que votre réseau soit le siège social de l’entreprise,  bureau à distance ou cet utilisateur travaillant à la maison. Nos conseils sont basés sur la façon dont les services Office 365 sont créés et pour garantir une expérience utilisateur sécurisée et performante.

## <a name="further-reading"></a>Lire plus en détail

[Principes de connectivité réseau Office 365](../enterprise/microsoft-365-network-connectivity-principles.md)

[URL et plages d’adresses IP Office 365](../enterprise/urls-and-ip-address-ranges.md)

[Gestion des points de terminaison Office 365](../enterprise/managing-office-365-endpoints.md)

[Service web URL et adresses IP Office 365](../enterprise/microsoft-365-ip-web-service.md)

[Évaluation de la connectivité réseau Office 365](../enterprise/assessing-network-connectivity.md)

[Paramétrage des performances et du réseau Office 365](../enterprise/network-planning-and-performance.md)

[Évaluation de la connectivité réseau Office 365](../enterprise/assessing-network-connectivity.md)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](../enterprise/performance-tuning-using-baselines-and-history.md)

[Plan de résolution des problèmes de performances pour Office 365](../enterprise/performance-troubleshooting-plan.md)

[Réseaux de distribution de contenu](../enterprise/content-delivery-networks.md)

[Test de connectivité Microsoft 365](https://connectivity.office.com/)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Office 365 connectivité pour les utilisateurs distants à l’aide du tunneling fractionné VPN](../enterprise/microsoft-365-vpn-split-tunnel.md)
