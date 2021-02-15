---
title: Outil de test de connectivité réseau Microsoft 365 (aperçu)
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
description: Outil de test de connectivité réseau Microsoft 365 (aperçu)
ms.openlocfilehash: b29eb29cd390c3febd0992e942cf8ab39f652fb2
ms.sourcegitcommit: 26c2f01d6f88f6c288b04f9f08062d68dd1e67e1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49569986"
---
# <a name="microsoft-365-network-connectivity-test-tool-preview"></a>Outil de test de connectivité réseau Microsoft 365 (aperçu)

L’outil de test de connectivité réseau Microsoft 365 se trouve à l’emplacement . <https://connectivity.office.com> Il s’agit d’un outil précieux pour l’évaluation du réseau et les informations d’informations réseau disponibles dans le Centre d’administration Microsoft 365 sous le **centre d'| Menu Connectivité.**

> [!IMPORTANT]
> Il est important de se connectez à votre client Microsoft 365, car tous les rapports de test sont partagés avec votre administrateur et chargés vers le client lorsque vous êtes en cours de signature.

![Outil de test de connectivité](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>L’outil de test de connectivité réseau prend en charge les clients de WW Commercial et d’Allemagne, mais pas GCC Moderate, GCC High, DoD ou China.

Les informations réseau dans le Centre d’administration Microsoft 365 sont basées sur des mesures régulières dans le produit pour votre client Microsoft 365 qui sont agrégées chaque jour. En comparaison, les informations réseau du test de connectivité réseau Microsoft 365 sont exécutés localement et une fois dans l’outil. Les tests qui peuvent être effectués dans le produit sont limités et en exécutant des tests locaux pour l’utilisateur, davantage de données peuvent être recueillies, ce qui permet d’obtenir des informations plus approfondies. Considérez ensuite que les informations réseau dans le Centre d’administration Microsoft 365 indiquent qu’il existe un problème de réseau pour l’utilisation de Microsoft 365 à un emplacement de bureau spécifique. Le test de connectivité Microsoft 365 peut aider à identifier la cause première de ce problème, ce qui entraîne une action recommandée d’amélioration des performances réseau.

Nous vous recommandons de les utiliser ensemble lorsque l’état de la qualité de la mise en réseau peut être évalué pour chaque emplacement de bureau dans le Centre d’administration Microsoft 365 et que des informations plus spécifiques soient trouvées après le déploiement des tests basés sur le test de connectivité Microsoft 365.

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le Centre d’administration Microsoft 365 sont actuellement en état de prévisualisation et sont uniquement disponibles pour les clients Microsoft 365 qui ont été inscrits au programme d’aperçu des fonctionnalités.

## <a name="what-happens-at-each-test-step"></a>Que se passe-t-il à chaque étape de test ?

### <a name="office-location-identification"></a>Identification de l’emplacement du bureau

Lorsque vous cliquez sur le bouton Exécuter le test, nous montrons la page de test en cours d’exécution et identifions l’emplacement du bureau. Vous pouvez taper votre emplacement par ville, état et pays, ou le détecter à partir du navigateur web. Si vous la détectez, nous demandons la latitude et la longitude au navigateur web et limitons la précision à 300 m par 300 m avant d’utiliser. Nous le faisons car il n’est pas nécessaire d’identifier l’emplacement plus précisément que le bâtiment pour les performances du réseau. 

### <a name="javascript-tests"></a>Tests JavaScript

Après l’identification de l’emplacement du bureau, nous exécuterons un test de latence TCP dans JavaScript et nous demandons des données au service sur les serveurs de porte du service Office 365 en cours d’utilisation et recommandés. Une fois ces étapes terminées, nous les montrons sur la carte et dans l’onglet Détails où elles peuvent être vues avant l’étape suivante.

### <a name="download-the-advanced-tests-client-application"></a>Télécharger l’application cliente de tests avancés

Ensuite, nous commençons le téléchargement de l’application cliente de tests avancés. Nous dépendons de l’utilisateur pour lancer l’application cliente et .NET Core doit également être installé.

Il existe deux parties au test de connectivité réseau Microsoft 365 ; le site web <https://connectivity.office.com> et une application cliente Windows téléchargeable qui exécute des tests de connectivité réseau avancés; La plupart des tests nécessitent l’application à exécuter. Il remplit de nouveau les résultats dans la page web au cours de son application.

Vous serez invité à télécharger l’application de test client avancée à partir du site web une fois les tests du navigateur web terminés. Ouvrez et exécutez le fichier à l’invite.

![Application cliente tests avancés](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Démarrer l’application cliente de tests avancés

Une fois que l’application cliente démarre, la page web se met à jour pour afficher ces données et les données de test commencent à être reçues sur la page web. Il est mis à jour chaque fois que de nouvelles données sont reçues et vous pouvez passer en revue les données à mesure qu’elles arrivent.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Tests avancés terminés et chargement de rapport de test

Une fois les tests terminés, la page web et le client de tests avancés l’indiquent tous les deux et si l’utilisateur est signé dans le rapport de test est téléchargé vers le client des clients.

## <a name="sharing-your-test-report"></a>Partage de votre rapport de test

Le rapport de test nécessite une se connectez à votre compte Office 365. Votre administrateur sélectionne la façon dont vous pouvez partager votre rapport de test.

### <a name="sharing-your-report-with-your-administrator"></a>Partage de votre rapport avec votre administrateur

Tous les rapports de test lorsque vous êtes inscrit sont partagés avec votre administrateur.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Partage avec votre équipe de compte Microsoft, le support ou d’autres membres du personnel

Les rapports de test qui excluent toute identification personnelle sont partagés avec les employés de Microsoft. Cette option est activée par défaut et peut être désactivée par votre administrateur dans le **| Page Connectivité réseau** dans le Centre d’administration Microsoft 365.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-office-365-tenant"></a>Partage avec d’autres utilisateurs qui se connectent au même client Office 365

Vous pouvez choisir des utilisateurs avec qui partager votre rapport, ce qui est activé par défaut. Il peut également être désactivé par votre administrateur.

![Partage d’un lien vers les résultats de vos tests avec un utilisateur](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Partage avec tout le monde à l’aide d’un lien ReportID

Vous pouvez partager votre rapport de test avec n’importe qui en donnant accès à un lien ReportID. Cela génère une URL que vous pouvez envoyer à quelqu’un afin qu’il puisse afficher le rapport de test sans se signer. Cette option est désactivée par défaut et doit être activée par votre administrateur.

![Partage d’un lien vers les résultats de vos tests](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Résultats des tests de connectivité réseau

Les résultats sont affichés dans les **onglets Résumé** **et** Détails. L’onglet résumé présente une carte du périmètre réseau détecté et une comparaison de l’évaluation du réseau avec d’autres clients Office 365 à proximité. Il permet également le partage du rapport de test. Voici à quoi ressemble l’affichage des résultats récapitulatifs.

![Résultats récapitulatifs de l’outil de test de connectivité réseau](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Voici un exemple de sortie de l’onglet Détails que l’outil affiche. Sous l’onglet Détails, une coche verte s’affiche si le résultat a été comparé de façon privilégiée à un seuil. Nous montrons un point d’exclamation de triangle rouge si le résultat a dépassé un seuil indiquant une information réseau. Les sections suivantes décrivent chacune des lignes de résultats de l’onglet Détails et expliquent les seuils utilisés pour les informations réseau.

![Exemple de résultats de test de l’outil de test de connectivité réseau](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Informations sur votre emplacement

Cette section affiche les résultats des tests liés à votre emplacement.

#### <a name="your-location"></a>Votre emplacement

L’emplacement de l’utilisateur est détecté à partir du navigateur web des utilisateurs ou il peut être tapé au choix des utilisateurs. Il permet d’identifier les distances réseau avec des parties spécifiques du périmètre du réseau d’entreprise. Seule la ville de cette détection d’emplacement et la distance avec les autres points réseau sont enregistrées dans le rapport.

L’emplacement du bureau de l’utilisateur est affiché sur l’affichage de carte.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Emplacement de sortie réseau (emplacement où votre réseau se connecte à votre isp)

Nous identifions l’adresse IP de sortie du réseau côté serveur. Les bases de données d’emplacements sont utilisées pour rechercher l’emplacement approximatif de la sortie réseau. Ces bases de données ont généralement une précision d’environ 90 % des adresses IP. Si l’emplacement examiné à partir de l’adresse IP de sortie du réseau n’est pas précis, cela entraînerait un faux résultat à partir de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser des sites web d’emplacement d’adresse IP réseau accessibles publiquement pour comparer votre emplacement réel.

#### <a name="your-distance-from-the-network-egress-location"></a>Votre distance par rapport à l’emplacement de sortie réseau

Nous déterminons la distance entre cet emplacement et l’emplacement du bureau. Cela s’affiche sous la mesure d’une information réseau si la distance est supérieure à **500 miles** (800 kilomètres), car cela est susceptible d’augmenter la latence TCP de plus de 25 ms et d’affecter l’expérience utilisateur.

L’emplacement de sortie réseau est affiché sur l’affichage de carte et connecté à l’emplacement du bureau de l’utilisateur indiquant le backhaul réseau à l’intérieur du réseau wan d’entreprise.

Il est recommandé d’implémenter la sortie réseau locale et directe des emplacements de bureau des utilisateurs vers Internet pour la connectivité réseau Microsoft 365. Les améliorations apportées à la sortie locale et directe sont le meilleur moyen de résoudre ce problème réseau.

#### <a name="proxy-server-information"></a>Informations sur le serveur proxy

Nous identifions les serveurs proxy configurés sur l’ordinateur local. Nous identifions si l’un de ces éléments est configuré dans le chemin d’accès réseau pour optimiser le trafic réseau Microsoft 365 de catégorie. Nous identifions la distance entre l’emplacement du bureau de l’utilisateur et les serveurs proxy. La distance est d’abord testée par le test PING ICMP et, si cela échoue, nous testons le ping TCP et, enfin, en cas d’échec, nous allons rechercher l’adresse IP du serveur proxy dans une base de données d’emplacements d’adresses IP. Nous montrons un aperçu du réseau si le serveur proxy se trouve à plus de **500 km** (800 kilomètres) de l’emplacement du bureau de l’utilisateur.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Réseau privé virtuel (VPN) que vous utilisez pour vous connecter à votre organisation

Cela permet de détecter si vous utilisez un VPN pour vous connecter à Office 365. Un résultat de passage indique si vous n’avez pas de VPN ou si vous avez un VPN avec une configuration de tunnel fractionnement recommandée pour Office 365.

#### <a name="vpn-split-tunnel"></a>Tunnel partagé VPN

Chaque itinéraire de catégorie d’optimisation pour Exchange Online, SharePoint Online et Microsoft Teams est testé pour voir s’il est tunnelé sur le VPN ou non. Une charge de travail fractionner évite entièrement le VPN. Une charge de travail tunnelée est envoyée sur le VPN. Une charge de travail tunnelée sélective dispose de certains itinéraires envoyés sur le VPN et d’autres fractionnés. Un résultat de passage indique si toutes les charges de travail sont fractionnés ou triés de façon sélective.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Clients de votre région métropolitain avec de meilleures performances

La latence TCP réseau de l’emplacement du bureau de l’utilisateur par rapport à la porte d’entrée du service Exchange Online est comparée aux autres clients Microsoft 365 dans la même zone. Un aperçu réseau s’affiche si 10 % ou plus des clients d’une même zone d’entreprise ont de meilleures performances. Cela signifie que leurs utilisateurs auront de meilleures performances dans l’interface utilisateur Microsoft 365.

Cette information réseau est générée sur la base du fait que tous les utilisateurs d’une ville ont accès à la même infrastructure de télécommunications et à la même proximité des circuits Internet et du réseau de Microsoft.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Temps d’effectuer une demande DNS sur votre réseau

Cela indique le serveur DNS configuré sur l’ordinateur client qui a effectué les tests. Il peut s’agit d’un serveur de résolution récursive DNS, mais cela est rare. Il est plus probable qu’il s’agit d’un serveur de forwardeur DNS qui met en cache les résultats DNS et les demandes DNS non mises en cache vers un autre serveur DNS.

Il est fourni uniquement pour les informations et ne contribue à aucune information réseau.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Votre distance et/ou votre temps de connexion à un résolveur récursif DNS

Le résolveur récursif DNS en cours d’utilisation est identifié en faisant une demande DNS spécifique, puis en demandant au serveur de noms DNS l’adresse IP à partir de qui il a reçu la même demande. Cette adresse IP est le résolveur récursif DNS et elle sera recherche dans les bases de données d’emplacements d’adresses IP pour trouver l’emplacement. La distance entre l’emplacement du bureau de l’utilisateur et l’emplacement du serveur de résolution récursive DNS est ensuite calculée. Il s’agit d’un aperçu réseau si la distance est supérieure à **500 miles** (800 kilomètres).

L’emplacement de sortie de l’adresse IP de sortie du réseau n’est peut-être pas précis et cela entraînerait un faux résultat à partir de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser des sites web d’emplacement d’adresse IP réseau accessibles publiquement.

Cette information réseau aura un impact spécifique sur la sélection de la porte d’entrée du service Exchange Online. Pour résoudre ce problème, la sortie de réseau local et directe doit être une condition préalable, puis le résolveur récursif DNS doit être situé à proximité de cette sortie réseau.

### <a name="exchange-online"></a>Exchange Online

Cette section présente les résultats des tests liés à Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Emplacement de la porte d’entrée du service Exchange

La porte d’entrée du service Exchange en cours d’utilisation est identifiée de la même manière qu’Outlook et nous mesureons la latence TCP du réseau à partir de l’emplacement de l’utilisateur. La latence TCP est affichée et la porte d’entrée du service Exchange en cours d’utilisation est comparée à la liste des meilleures portes d’entrée de service pour l’emplacement actuel. Il s’agit d’une information réseau si l’une des meilleures porte d’entrée du service Exchange n’est pas en cours d’utilisation.

L’utilisation de l’une des meilleures porte d’entrée du service Exchange peut être causée par une rétrograder du réseau avant la sortie du réseau d’entreprise, auquel cas nous recommandons la sortie du réseau local et direct. Cela peut également être dû à l’utilisation d’un serveur de résolution récursif DNS distant, auquel cas nous vous recommandons d’aligner le serveur de résolution récursif DNS avec la sortie réseau.

Nous calculons une amélioration potentielle de la latence TCP (ms) sur la porte d’entrée du service Exchange. Pour ce faire, il s’agit de la latence testée du réseau d’emplacements du bureau de l’utilisateur et de la soustraction de la latence du réseau de l’emplacement actuel vers la porte d’entrée du service Exchange. La différence représente l’opportunité potentielle d’amélioration.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Meilleures adresses de service Exchange pour votre emplacement

Cette liste répertorie les meilleurs emplacements de porte d’entrée du service Exchange par ville pour votre emplacement.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Porte frontale du service enregistrée dans le DNS client

Cela indique le nom DNS et l’adresse IP du serveur frontal du service Exchange vers qui vous avez été dirigé. Il est fourni pour des informations uniquement et il n’y a pas d’informations réseau associées.

### <a name="sharepoint-online"></a>SharePoint Online

Cette section présente les résultats des tests liés à SharePoint Online et OneDrive.

#### <a name="the-service-front-door-location"></a>Emplacement de la porte d’entrée du service

La porte d’entrée du service SharePoint en cours d’utilisation est identifiée de la même manière que le client OneDrive et nous mesurons la latence TCP du réseau à partir de l’emplacement du bureau de l’utilisateur.

#### <a name="download-speed"></a>Vitesse de téléchargement

Nous mesurons la vitesse de téléchargement d’un fichier de 15 Mo à partir de la porte d’entrée du service SharePoint. Le résultat est affiché en mégaoctets par seconde pour indiquer quel fichier de taille en mégaoctets peut être téléchargé à partir de SharePoint ou OneDrive en **une seconde.** Le nombre doit être similaire à un dixième de la bande passante du circuit minimum en mégabits par seconde. Par exemple, si vous avez une connexion Internet de 100 Mbits/s, vous pouvez vous attendre à 10 mégaoctets par seconde (10 Mbits/s).

#### <a name="buffer-bloat"></a>Tampons de tampon

Pendant le téléchargement de 15 Mo, nous mesurons la latence TCP sur la porte d’entrée du service SharePoint. Il s’agit de la latence sous charge et comparée à la latence lorsqu’elle n’est pas sous charge. L’augmentation de la latence en cas de charge est souvent due au chargement des mémoires tampons des périphériques réseau grand public (ou trop importantes). Une vue d’un réseau est affichée pour tout problème de 1 000 ou plus.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Porte frontale du service enregistrée dans le DNS client

Cela indique le nom DNS et l’adresse IP du serveur frontal du service SharePoint vers qui vous avez été dirigé. Il est fourni pour des informations uniquement et il n’y a pas d’informations réseau associées.

### <a name="microsoft-teams"></a>Microsoft Teams

Cette section présente les résultats des tests liés à Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Connectivité multimédia (audio, vidéo et partage d’application)

Cela teste la connectivité UDP au service Microsoft Teams frontal. Si ce blocage est bloqué, Microsoft Teams peut toujours fonctionner à l’aide de TCP, mais l’audio et la vidéo seront altérés. En savoir plus sur ces mesures de réseau UDP qui s’appliquent également à Microsoft Teams au niveau de la qualité des médias et des performances de connectivité [réseau dans Skype Entreprise Online](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)

#### <a name="packet-loss"></a>Perte de paquets

Indique la perte de paquets UDP mesurée dans un appel audio de test de 10 secondes entre le client et le service Microsoft Teams. Cette valeur doit être inférieure **à 1,00 %** pour une passe.

#### <a name="latency"></a>Latence

Indique la latence UDP mesurée, qui doit être inférieure à **100 ms.**

#### <a name="jitter"></a>Gigue

Indique la gigue UDP mesurée, qui doit être inférieure à **30 ms**.

#### <a name="connectivity"></a>Connectivité

Nous testons la connectivité HTTP à partir de l’emplacement du bureau de l’utilisateur vers tous les points de terminaison réseau Microsoft 365 requis. Ceux-ci sont publiés sur [https://aka.ms/o365ip](https://aka.ms/o365ip) . Un aperçu réseau est affiché pour tous les points de terminaison réseau requis qui ne peuvent pas être connectés.

La connectivité peut être bloquée par un serveur proxy, un pare-feu ou un autre périphérique de sécurité réseau sur le périmètre du réseau d’entreprise. La connectivité au port TCP 80 est testée avec une demande HTTP et la connectivité au port TCP 443 est testée avec une demande HTTPS. En l’absence de réponse, le nom de groupe est marqué comme un échec. S’il existe un code de réponse HTTP 407, le FQDN est marqué comme un échec. S’il existe un code de réponse HTTP 403, nous vérifions l’attribut serveur de la réponse et s’il s’agit d’un serveur proxy, nous le marquerons comme un échec. Vous pouvez simuler les tests effectués avec l’outil de ligne de commande Windows curl.exe.

Nous testons le certificat SSL à chaque point de terminaison réseau Microsoft 365 requis qui se trouve dans la catégorie Optimiser ou Autoriser comme défini à [https://aka.ms/o365ip](https://aka.ms/o365ip) . Si des tests ne trouvent pas de certificat Microsoft SSL, le réseau chiffré connecté doit avoir été intercepté par un périphérique réseau intermédiaire. Un aperçu réseau est affiché sur tous les points de terminaison réseau chiffrés interceptés.

Lorsqu’un certificat SSL n’est pas fourni par Microsoft, nous montrons le FQDN du test et le propriétaire du certificat SSL en cours d’utilisation. Ce propriétaire de certificat SSL peut être un fournisseur de serveur proxy ou un certificat auto-signé d’entreprise.

#### <a name="network-path"></a>Chemin d’accès réseau

Cette section présente les résultats d’un itinéraire de suivi ICMP vers la porte d’entrée du service Exchange Online, la porte d’entrée du service SharePoint Online et la porte d’entrée du service Microsoft Teams. Il est fourni pour des informations uniquement et il n’y a pas d’informations réseau associées. Trois traceroutes sont fournies. Traceroute vers _outlook.office365.com_, traceroute vers le client SharePoint frontal ou _vers microsoft.sharepoint.com_ si ce n’est pas le cas, et traceroute vers world.tr.teams.microsoft.com . 

## <a name="connectivity-reports"></a>Rapports de connectivité

Une fois que vous êtes signé, vous pouvez passer en revue les rapports précédents que vous avez exécutés. Vous pouvez également les partager ou les supprimer de la liste.

![Rapports](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>État d’état du réseau

Cela indique les problèmes d’état d’santé importants avec le réseau mondial de Microsoft qui peuvent avoir un impact sur les clients Microsoft 365.

![État d’état du réseau](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="faq"></a>FAQ

Voici des réponses à certaines de nos questions fréquemment posées.

### <a name="is-this-tool-released-and-supported-by-microsoft"></a>Cet outil est-il publié et pris en charge par Microsoft ?

Il s’agit actuellement d’une prévisualisation et nous prévoyons de fournir des mises à jour régulièrement jusqu’à ce que nous atteindions l’état de la version de disponibilité générale avec le support de Microsoft. Veuillez nous faire part de vos commentaires pour nous aider à améliorer. Nous prévoyons de publier un guide d’intégration réseau Office 365 plus détaillé dans le cadre de cet outil personnalisé pour l’organisation par ses résultats de test.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Qu’est-ce qui est requis pour exécuter le client de test avancé ?

Le client de test avancé requiert .NET Core 3.1 Desktop Runtime. Si vous exécutez le client de test avancé sans celui installé, vous serez dirigé vers la page du programme d’installation [.NET Core 3.1.](https://dotnet.microsoft.com/download/dotnet-core/3.1) N’oubliez pas d’installer Desktop Runtime et non le SDK, ou le ASP.NET Core Runtime qui sont plus haut sur la page. Les autorisations d’administrateur sur l’ordinateur sont requises pour installer .NET Core.

### <a name="what-is-microsoft-365-service-front-door"></a>Qu’est-ce que le service Microsoft 365 frontal ?

La porte d’entrée du service Microsoft 365 est un point d’entrée sur le réseau mondial de Microsoft où les clients et services Office terminent leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé d’interrompre votre connexion réseau sur la porte d’entrée Microsoft 365 la plus proche de votre ville ou de votre ville.

Remarque : la porte d’entrée du service Microsoft 365 n’a pas de relation directe avec le produit **azure front door service** disponible sur azure marketplace.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Quelle est la meilleure porte d’entrée du service Microsoft 365 ?

Une meilleure porte d’entrée du service Microsoft 365 (anciennement appelée porte d’entrée de service optimale) est celle qui est la plus proche de la sortie de votre réseau, généralement dans votre ville ou région. Utilisez l’outil de performances réseau Microsoft 365 pour déterminer l’emplacement de votre service Microsoft 365 en cours d’utilisation et la ou les meilleures porte d’entrée du service. Si l’outil détermine que votre porte frontale en cours d’utilisation est l’une des meilleures, vous devez vous attendre à une excellente connectivité au réseau mondial de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Il s’agit également de l’emplacement où vous avez un périphérique de traduction d’adresses réseau (NAT) et généralement où vous vous connectez à un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement de sortie Internet, cela peut identifier un backhaul wan significatif.

## <a name="related-topics"></a>Rubriques connexes

[Connectivité réseau dans le Centre d’administration Microsoft 365 (prévisualisation)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Microsoft 365 (prévisualisation)](office-365-network-mac-perf-score.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (prévisualisation)](office-365-network-mac-location-services.md)
