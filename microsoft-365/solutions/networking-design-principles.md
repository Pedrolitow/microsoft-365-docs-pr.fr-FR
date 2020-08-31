---
title: Mise en réseau (vers le Cloud) — point de vue d’un architecte
description: Description.
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
ms.openlocfilehash: a005d56dcca08c05eb433ef75ca3870785b39f19
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47308128"
---
# <a name="networking-up-to-the-cloud--one-architects-viewpoint"></a>Mise en réseau (vers le Cloud) — point de vue d’un architecte

Dans cet article, [Ed Fisher](https://www.linkedin.com/in/edfisher/), Security & architecte de conformité chez Microsoft, explique comment optimiser votre réseau pour la connectivité au Cloud en évitant les pièges les plus courants. 

## <a name="about-the-author"></a>À propos de l’auteur

![Photo de la Ed Fisher](../media/solutions-architecture-center/ed-fisher-networking.jpg) 

Je suis actuellement spécialiste technique de la région sud-est qui se concentre sur la sécurité & la conformité. J’ai travaillé avec des clients qui se déplacent vers Office 365 au cours des dix dernières années. J’ai travaillé avec des magasins de petite taille avec quelques emplacements aux agences gouvernementales et aux entreprises comptant des millions d’utilisateurs répartis dans le monde entier, et de nombreux autres clients entre, avec une majorité de dizaines de milliers d’utilisateurs, plusieurs emplacements dans différentes régions du monde, la nécessité d’un niveau de sécurité plus élevé et une multitude d’exigences en matière de conformité. J’ai aidé des centaines d’entreprises et des millions d’utilisateurs se déplacent vers le Cloud en toute sécurité et en toute sécurité.

Avec un arrière-plan sur les 25 dernières années incluant la sécurité, l’infrastructure et l’ingénierie réseau, et après avoir déplacé deux de mes employeurs précédents vers Office 365 avant de rejoindre Microsoft, je suis de votre côté du tableau beaucoup de fois et vous avez oublié ce qui vous plaît. Bien que deux clients ne soient jamais les mêmes, la plupart ont des besoins similaires, et lorsque vous utilisez un service standardisé tel qu’une plateforme SaaS ou PaaS, les meilleures approches tendent à être les mêmes.



## <a name="its-not-the-network--its-how-youre-misusing-it"></a>Il ne s’agit pas du réseau, mais de la manière dont vous êtes (mis) en service.

Quel que soit le nombre de fois qu’il se produit, il ne parvient jamais à me amazer comment les équipes de sécurité *créatives* et les équipes de mise en réseau essaient de se connecter aux services Cloud de Microsoft. Il y a toujours une stratégie de sécurité, une norme de conformité ou une meilleure façon d’insister sur l’utilisation de, sans être disposé à participer à une conversation sur ce qu’elle tente d’accomplir, ou à mieux comprendre *Comment* elles sont plus efficaces, plus faciles, plus économiques et plus performantes. 

Lorsque ce type de contenu est remonté, je suis généralement prêt à suivre le défi et à les guider dans le Hows et le Whys, puis à l’endroit où ils doivent se trouver. Mais si je suis entièrement Frank, je dois partager cela, je dois parfois les autoriser à faire ce qu’ils feront, et revenons à dire que je vous ai dit, quand ils concéderont finalement qu’ils ne fonctionnent pas. J’aurais pu le faire, mais ce n’est *pas*le cas. Je tente d’expliquer tous les éléments que je vais inclure dans ce billet. Quel que soit votre rôle, si votre organisation souhaite utiliser les services de Cloud Computing Microsoft, il y a probablement des informations utiles pour ce qui peut vous aider.


## <a name="guiding-principles"></a>Principes de guidage
Nous allons commencer par certaines règles de ce que nous faisons ici. Nous abordons comment se connecter en toute sécurité aux services Cloud pour garantir la complexité minimale et les performances maximales, tout en maintenant une véritable sécurité. Aucune des opérations suivantes n’est à prendre en considération, même si vous, ou votre client, n’utiliserez pas votre serveur proxy favori pour tout.

- **Tout comme vous pouvez le faire, cela ne signifie pas,** ou de paraphraser le Dr. Ian Malcolm du Jurassic Park Movie. . . Oui, mais votre équipe de sécurité a été tellement préoccupée par le fait qu’ils ne pouvaient pas se faire croire, le cas échéant. "    
- **La sécurité ne signifie pas de complexité** , vous n’êtes pas plus sûr, car vous consacrez plus d’argent, acheminez des périphériques ou cliquez sur plus de boutons.
- **Office 365 est accessible via Internet** , mais ce n’est pas la même chose qu’Office 365 est Internet. Il s’agit d’un service SaaS géré par Microsoft et géré par vous-même. Contrairement aux sites Web que vous visitez sur Internet, vous pouvez en fait lire le Rideau et appliquer les contrôles dont vous avez besoin pour répondre à vos stratégies et à vos normes de conformité, tant que vous comprenez que bien que vous puissiez atteindre vos objectifs, vous devrez peut-être les effectuer de différentes manières.
- Les **Chokepointss sont mauvaises, les modifications localisées sont bonnes** , tout le monde veut toujours rediriger tout le trafic Internet de tous leurs utilisateurs vers un point central, généralement afin qu’ils puissent surveiller et appliquer la stratégie, mais souvent parce qu’il est moins onéreux que le provisionnement de l’accès Internet dans tous leurs emplacements, ou il s’agit de la façon dont ils le font. Mais ces chokepoints sont exactement les mêmes que... points d’étranglement du trafic. Il n’y a aucun problème à empêcher vos utilisateurs de naviguer vers Instagram ou des vidéos de diffusion en continu, mais ne traitez pas le trafic de votre application métier stratégique de la même façon.
- **Si ain’t satisfait, ain’t rien,** le réseau de meilleure conception peut être Hamstrung par un DNS médiocre, qu’il s’agisse de requêtes récurrentes vers des serveurs d’autres régions du monde ou à l’aide des serveurs DNS de votre fournisseur de services Internet ou d’autres serveurs publics DNS qui cachent les informations de résolution DNS. 
- **En d’autres termes, vous** n’êtes pas tenu de le faire maintenant : les changements technologiques en permanence et Office 365 ne constituent pas une exception. L’application de mesures de sécurité qui ont été développées et déployées pour les services locaux ou pour contrôler la navigation Web n’offre pas le même niveau de sécurité et peut avoir un impact négatif significatif sur les performances.
- **Office 365 a été conçu pour être accessible sur Internet** , c’est en bref. Quelle que soit la marche à suivre entre vos utilisateurs et votre serveur Edge, le trafic se déplace toujours sur Internet une fois qu’il quitte votre réseau et avant que celui-ci ne se connecte à la nôtre. Même si vous utilisez Azure ExpressRoute pour acheminer le trafic sensible à la latence de votre réseau directement vers le nôtre, la connectivité Internet est absolument requise. Acceptez-la. Ne vous repensez pas.

## <a name="where-bad-choices-are-often-made"></a>Où les choix incorrects sont souvent faits

S’il existe de nombreux endroits où des décisions incorrectes sont prises dans le nom de la sécurité, il s’agit des éléments que je rencontre le plus souvent avec les clients. De nombreuses conversations des clients impliquent tous ces éléments en même temps.

### <a name="insufficient-resources-at-the-edge"></a>Ressources insuffisantes sur le serveur Edge
Très peu de clients déploient des environnements déploiements, et ils disposent d’années d’expérience quant à la façon dont leurs utilisateurs travaillent et à quoi leur sortie Internet est similaire. Que les clients disposent de serveurs proxy ou autorisent l’accès direct et simplement le trafic sortant NAT, ils le font pendant des années et ne considèrent pas seulement le nombre de fois qu’ils vont commencer à pomper leurs applications internes dans le Cloud.

La bande passante est toujours un problème, mais les périphériques NAT ne disposent pas d’une puissance suffisante pour gérer l’augmentation de la charge et peuvent démarrer prématurément la fermeture des connexions pour libérer des ressources. La plupart du logiciel client qui se connecte à Office 365 attend des connexions permanentes et un utilisateur d’Office 365 peut avoir au moins 32 connexions simultanées. Si le périphérique NAT les supprime prématurément, ces applications peuvent cesser de répondre lorsqu’ils essaient d’utiliser les connexions qui ne sont plus là. Lorsqu’ils renonceront à établir de nouvelles connexions, ils mettent davantage de charges sur votre équipement réseau.

### <a name="localized-breakout"></a>Répartition localisée
Tous les autres éléments de cette liste sont inactifs : la mise en route de votre réseau et le nôtre aussi rapidement que possible. Le fait de rediriger le trafic de vos utilisateurs vers un point de sortie central, en particulier lorsque ce point se trouve dans une autre région que celle de vos utilisateurs, présente une latence inutile et influe sur l’expérience client et les vitesses de téléchargement. Microsoft a des points de présence dans le monde entier avec des points de terminaison pour tous nos services et homologations établis avec pratiquement tous les principaux fournisseurs de services Internet, ce *qui permet de* Router rapidement le trafic de vos utilisateurs vers le réseau avec une latence minimale. 

### <a name="dns-resolution-traffic-should-follow-the-internet-egress-path"></a>Le trafic de résolution DNS doit suivre le chemin de sortie Internet.
Bien entendu, pour qu’un client trouve un point de terminaison, il doit utiliser le système DNS. Les serveurs DNS de Microsoft évaluent la source des demandes DNS afin de s’assurer que nous renvoyons la réponse qui est, dans les conditions Internet, la plus proche de la source de la demande. Assurez-vous que votre DNS est configuré de sorte que les demandes de résolution de noms redirigent le même chemin que le trafic de vos utilisateurs, tandis que vous les leur donnez une sortie locale mais un point de terminaison dans une autre région. Cela signifie qu’il faut laisser les serveurs DNS locaux « aller à la racine » au lieu de transférer vers les serveurs DNS dans les centres de données à distance. Et méfiez-vous des services DNS publics et privés, qui peuvent mettre en cache les résultats d’une partie du monde et les traiter aux demandes d’autres parties du monde.

### <a name="to-proxy-or-not-to-proxy-that-is-the-question"></a>Pour effectuer un proxy ou un proxy, il s’agit de la question
L’une des premières considérations à prendre en considération est de s’indiquer si les connexions des utilisateurs doivent être proxy vers Office 365. Il s’agit d’un jeu d’enfant ; ne pas effectuer de proxy. Office 365 est accessible via Internet, mais il ne s’agit pas d’Internet. Il s’agit d’une extension de vos services principaux et doit être traitée comme telle. Tout ce que vous pouvez souhaiter faire d’un proxy, comme DLP ou anti-programme malveillant ou l’inspection de contenu, est déjà disponible dans le service, et peut être utilisé à l’étendue et ne doit pas déchiffrer les connexions TLS chiffrées. Toutefois, si vous voulez vraiment transmettre par proxy le trafic que vous ne pouvez pas contrôler, faites attention à nos conseils sur [https://aka.ms/pnc](https://aka.ms/pnc) et les catégories de trafic à l’adresse [https://aka.ms/ipaddrs](https://aka.ms/ipaddrs) . Il existe trois catégories de trafic pour Office 365. Optimize et allow doivent absolument être acheminés et contourner votre proxy. La valeur par défaut peut être proxy. Les détails sont dans ces documents. . . les lire.

La plupart des clients qui insistent sur l’utilisation d’un proxy, lorsqu’ils examinent réellement ce qu’ils font, sont conscients que lorsque le client effectue une demande de connexion HTTP au proxy, le proxy est maintenant un routeur supplémentaire onéreux. Les protocoles utilisés, comme MAPI et RTC, ne sont même pas des protocoles compris par les proxys Web, de sorte que même avec le craquage TLS, vous n’obtenez pas de sécurité supplémentaire. Vous *obtenez une* latence supplémentaire. Pour plus d’informations, reportez-vous à la rubrique relative aux [https://aka.ms/pnc](https://aka.ms/pnc) catégories Optimize, Allow et Default pour le trafic Microsoft 365.

Enfin, tenez compte de l’impact global sur le proxy et sur sa réponse correspondante pour répondre à cet impact. À mesure que de plus en plus de connexions sont établies via le proxy, il peut diminuer le facteur d’échelle TCP afin qu’il n’ait pas besoin de mettre en mémoire tampon autant de trafic. J’ai vu des clients où leurs proxys étaient tellement surchargés qu’ils utilisaient un facteur d’échelle de 0. Étant donné que le facteur d’échelle est une valeur exponentielle et que nous souhaitons utiliser 8, chaque réduction de la valeur de facteur d’échelle est un impact négatif important sur le débit.

L’inspection TLS signifie sécurité ! Mais pas vraiment ! De nombreux clients avec des proxys veulent les utiliser pour inspecter tout le trafic, et cela signifie que TLS « arrête et inspecte ». Lorsque vous effectuez cette opération pour un site Web accessible via HTTPs (Nonobstant les préoccupations de confidentialité), votre proxy peut avoir à le faire pour dix ou même vingt flux simultanés pendant quelques centaines de millisecondes. S’il existe un grand téléchargement ou une vidéo impliquée, une ou plusieurs de ces connexions peuvent durer plus longtemps, mais en général, la plupart de ces connexions établissent, transfèrent et se ferment très rapidement. Si vous effectuez une interruption et une inspection, le proxy doit doubler le travail. Pour chaque connexion entre le client et le proxy, le proxy doit également établir une connexion distincte vers le point de terminaison. Par conséquent, un devient deux, deux devient 4, 32 devient 64. . . que dois-je faire ? Vous avez probablement dimensionné votre solution de proxy pour une navigation Web classique, mais lorsque vous essayez d’effectuer la même chose pour les connexions client vers Office 365, le nombre de connexions simultanées à long terme peut être supérieur à celui de la taille des données.

### <a name="streaming-isnt-important-except-that-it-is"></a>La diffusion en continu n’est pas importante, sauf qu’elle *est*
Les seuls services dans Office 365 qui utilisent le protocole UDP sont Skype (prochainement déclassé) et Microsoft Teams. Teams utilise UDP pour le trafic de diffusion en continu, y compris l’audio, la vidéo et le partage de présentations. Le trafic de diffusion en continu est actif, par exemple lorsque vous avez une réunion en ligne avec des voix, des vidéos et des platines de présentation ou en effectuant des démonstrations. Ces éléments utilisent le protocole UDP, car si les paquets sont supprimés ou arrivent dans un ordre insuffisant, il n’est pratiquement pas perceptible par l’utilisateur et le flux peut simplement continuer. 

Lorsque vous n’autorisez pas le trafic UDP sortant des clients vers le service, ils peuvent revenir à l’utilisation de TCP. Toutefois, si un paquet TCP est abandonné, *tout s’arrête* jusqu’à ce que le délai d’expiration de retransmission (RTO) expire et que le paquet manquant puisse être retransmis. Si un paquet arrive dans le désordre, tout s’arrête jusqu’à ce que les autres paquets arrivent et puissent être réassemblés dans l’ordre. Les deux conduisent à des problèmes perceptibles dans l’audio (mémoriser la hauteur maximale ?) et à la vidéo (vous avez cliqué sur Someth. . . Oh, c’est le cas) et entraînent des performances médiocres et une expérience utilisateur incorrecte. Et rappelez-vous ce que j’ai présenté au-dessus des proxys ? Lorsque vous forcez un client teams à utiliser un proxy, vous le forcez à utiliser le protocole TCP. À présent, vous provoquez un impact négatif sur les performances à deux reprises.

### <a name="split-tunneling-may-seem-scary"></a>Le tunneling fractionné peut sembler effrayant
Mais ce n’est pas le cas. Toutes les connexions à Office 365 sont sur TLS. Nous proposons une offre TLS 1,2 pour un certain temps maintenant et nous désactiverons les versions plus anciennes bientôt, car les clients hérités continueront à les utiliser et cela est un risque.

En forçant une connexion TLS, ou 32, de le faire passer sur un réseau privé virtuel (VPN) avant de passer au service n’ajoute pas de sécurité. Elle ajoute la latence et réduit le débit global. Dans certaines solutions VPN, il force même le tunnel UDP vers le trafic TCP, ce qui aura un impact très négatif sur le trafic de diffusion en continu. À moins que vous n’effectuiez une inspection TLS, il n’y a aucun inconvénient. Un thème très commun parmi les clients actuellement, maintenant que la plupart de leurs employés sont à distance, il s’agit d’un impact significatif sur la bande passante et les performances de la connexion de tous leurs utilisateurs à l’aide d’un VPN, au lieu de configurer le tunneling fractionné pour l’accès à [optimiser les points de terminaison Office 365](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-network-connectivity-principles#new-office-365-endpoint-categories)de la catégorie.

Il est facile de procéder à un tunneling fractionné et c’est une solution à effectuer. Pour plus d’informations, vérifiez que vous avez examiné [optimiser la connectivité Office 365 pour les utilisateurs distants à l’aide du tunneling VPN Split](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel).


## <a name="the-sins-of-the-past"></a>Le péchés du passé
De nombreuses fois, les choix incorrects proviennent d’une combinaison de (1) qui ne connaît pas le fonctionnement du service, (2) qui tentent d’adhérer aux stratégies de l’entreprise écrites avant l’adoption du Cloud, et (3) les équipes de sécurité qui peuvent ne pas être facilement convaincues qu’il existe plusieurs façons d’atteindre leurs objectifs. J’espère que les liens ci-dessus, ainsi que les liens ci-dessous, vous aideront à utiliser le premier. Le soutien de la direction peut être requis pour franchir le second. L’adressage des objectifs des stratégies de sécurité, plutôt que leurs méthodes, contribue à la troisième. De l’accès conditionnel à la modération du contenu, DLP à la protection des informations, validation des points de terminaison sur les menaces « Zero-Day », tout objectif final une stratégie de sécurité raisonnable peut être réalisée avec ce qui est disponible dans Office 365 et sans aucune dépendance vis-à-vis des équipements réseau sur site, des tunnels VPN forcés et l’interruption et l’inspection TLS 

Autres fois, le matériel qui a été dimensionné et acheté avant le début de la migration vers le Cloud ne peut plus être mis à l’échelle pour gérer les nouveaux modèles et charges de trafic. Si vous devez véritablement acheminer tout le trafic via un seul point de sortie, et/ou proxy, soyez prêt à mettre à niveau le matériel réseau et la bande passante en conséquence. Surveiller soigneusement l’utilisation des deux, car l’expérience ne diminue pas lentement en fonction du nombre d’utilisateurs intégrés. Tout sera fin jusqu’à ce que le point de basculement soit atteint, tout le monde en souffre. 

## <a name="exceptions-to-the-rules"></a>Exceptions aux règles

Si votre organisation requiert des [restrictions client](https://docs.microsoft.com/azure/active-directory/manage-apps/tenant-restrictions), vous devez utiliser un proxy avec la panne TLS et inspecter pour forcer le trafic via le proxy, mais vous n’avez pas besoin d’imposer tout le trafic via ce dernier.  Il ne s’agit pas d’une proposition tout ou rien, donc faites attention à ce qui doit être modifié par le proxy. 

Si vous souhaitez autoriser le tunneling fractionné mais utiliser également un proxy pour le trafic Web général, assurez-vous que votre fichier PAC définit ce qui doit être direct, ainsi que la façon dont vous définissez un trafic intéressant pour ce qui passe par le tunnel VPN. Nous offrons des exemples de fichiers PAC qui faciliteront [https://aka.ms/ipaddrs](https://aka.ms/ipaddrs) leur gestion.

## <a name="conclusion"></a>Conclusion

Des dizaines de milliers d’organisations, dont la plupart des 500 fortune, utilisent Office 365 tous les jours pour leurs fonctions critiques. Ils le font de manière sécurisée, et ils le font sur Internet.

 Quels que soient les objectifs de sécurité que vous avez joués, il existe des moyens de les accomplir qui ne nécessitent pas de connexions VPN, de serveurs proxy, de panne et d’analyse TLS, ou de sortie Internet centralisée pour faire passer le trafic de vos utilisateurs à votre réseau et au nôtre aussi rapidement que possible, ce qui fournit les meilleures performances, que votre réseau soit le siège social ou cet utilisateur travaille à domicile. Nos conseils s’appuient sur la façon dont les services Office 365 sont créés et garantissent une expérience utilisateur sécurisée et performante.

## <a name="further-reading"></a>Autres lectures

[Principes de connectivité réseau Office 365](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-network-connectivity-principles)

[URL et plages d’adresses IP Office 365](https://docs.microsoft.com/microsoft-365/enterprise/urls-and-ip-address-ranges)

[Gestion des points de terminaison Office 365](https://docs.microsoft.com/microsoft-365/enterprise/managing-office-365-endpoints)

[Service web URL et adresses IP Office 365](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-ip-web-service)

[Évaluation de la connectivité réseau Office 365](https://docs.microsoft.com/microsoft-365/enterprise/assessing-network-connectivity)

[Paramétrage des performances et du réseau Office 365](https://docs.microsoft.com/microsoft-365/enterprise/network-planning-and-performance)

[Évaluation de la connectivité réseau Office 365](https://docs.microsoft.com/microsoft-365/enterprise/assessing-network-connectivity)

[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](https://docs.microsoft.com/microsoft-365/enterprise/performance-tuning-using-baselines-and-history)

[Plan de résolution des problèmes de performances pour Office 365](https://docs.microsoft.com/microsoft-365/enterprise/performance-troubleshooting-plan)

[Réseaux de distribution de contenu](https://docs.microsoft.com/microsoft-365/enterprise/content-delivery-networks)

[Test de connectivité Microsoft 365](https://connectivity.office.com/)

[Comment Microsoft construit son réseau mondial rapide et fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog sur la mise en réseau Office 365](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking)

[Connectivité Office 365 pour les utilisateurs distants utilisant le tunneling VPN Split Tunneling](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-vpn-split-tunnel)


