---
title: Outil de test de la connectivité du réseau Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Outil de test de la connectivité du réseau Microsoft 365
ms.openlocfilehash: e4045a8fde1d33bdc0072fbce9368d0ef8774ae7
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670562"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Outil de test de la connectivité du réseau Microsoft 365

L’outil de test de connectivité réseau Microsoft 365 se trouve à l’adresse <https://connectivity.office.com>. Il s’agit d’un outil complémentaire pour l’évaluation du réseau et les insights réseau disponibles dans le Centre d'administration Microsoft 365 sous la **| Menu connectivité**.

> [!IMPORTANT]
> Il est important de se connecter à votre locataire Microsoft 365, car tous les rapports de test sont partagés avec votre administrateur et chargés sur le locataire lorsque vous êtes connecté.

> [!div class="mx-imgBorder"]
> ![Outil de test de connectivité.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>L’outil de test de connectivité réseau prend en charge les locataires dans WW Commercial, mais pas GCC Moderate, GCC High, DoD ou Chine.

Les insights réseau dans le centre Administration Microsoft 365 sont basés sur des mesures régulières dans le produit pour votre locataire Microsoft 365, agrégées chaque jour. En comparaison, les insights réseau du test de connectivité réseau Microsoft 365 sont exécutés localement dans l’outil.

Les tests dans le produit sont limités et l’exécution de tests locaux pour l’utilisateur collecte davantage de données, ce qui permet d’obtenir des insights plus approfondis. Les insights réseau dans le centre de Administration Microsoft 365 indiquent qu’il existe un problème de mise en réseau à un emplacement de bureau spécifique. Le test de connectivité Microsoft 365 peut aider à identifier la cause racine de ce problème et à fournir une action ciblée d’amélioration des performances.

Nous vous recommandons d’utiliser ces insights ensemble, où l’état de la qualité de la mise en réseau peut être évalué pour chaque emplacement de bureau dans le centre Administration Microsoft 365 et où des informations plus spécifiques sont disponibles après le déploiement de tests basés sur le test de connectivité Microsoft 365.

## <a name="what-happens-at-each-test-step"></a>Que se passe-t-il à chaque étape de test ?

### <a name="office-location-identification"></a>Identification de l’emplacement d’Office

Lorsque vous cliquez sur le bouton *Exécuter le test* , nous affichons la page de test en cours d’exécution et identifions l’emplacement du bureau. Vous pouvez taper votre emplacement par ville, état et pays ou choisir de le faire détecter pour vous. Si vous détectez l’emplacement du bureau, l’outil demande la latitude et la longitude du navigateur web et limite la précision à 300 mètres par 300 mètres avant l’utilisation. Il n’est pas nécessaire d’identifier l’emplacement plus précisément que le bâtiment pour mesurer les performances du réseau.

### <a name="javascript-tests"></a>Tests JavaScript

Après l’identification de l’emplacement du bureau, nous exécutons un test de latence TCP en JavaScript et nous demandons au service des données sur les serveurs de porte d’entrée de service Microsoft 365 en cours d’utilisation et recommandés. Une fois ces tests terminés, nous les affichons sur la carte et dans l’onglet Détails où ils peuvent être affichés avant l’étape suivante.

### <a name="download-the-advanced-tests-client-application"></a>Télécharger l’application cliente tests avancés

Ensuite, nous commençons le téléchargement de l’application cliente tests avancés. Nous nous fions à l’utilisateur pour lancer l’application cliente et le runtime .NET 6.0 doit également être installé.

Le test de connectivité réseau Microsoft 365 comprend deux parties : le site <https://connectivity.office.com> web et une application cliente Windows téléchargeable qui exécute des tests de connectivité réseau avancés. La plupart des tests nécessitent l’exécution de l’application. Il remplira les résultats dans la page web au fur et à mesure qu’il s’exécutera.

Vous serez invité à télécharger l’application de test client avancée à partir du site web une fois les tests du navigateur web terminés. Ouvrez et exécutez le fichier à l’invite.

> [!div class="mx-imgBorder"]
> ![Application cliente de tests avancés.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Démarrer l’application cliente tests avancés

Une fois l'application client démarrée, la page Web sera mise à jour pour afficher ce résultat. Les données de test commencent à être reçues sur la page web. La page est mise à jour chaque fois que de nouvelles données sont reçues et vous pouvez passer en revue les données à mesure qu’elles arrivent.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Tests avancés terminés et chargement du rapport de test

Une fois les tests terminés, la page web et le client de tests avancés le montrent tous les deux. Si l’utilisateur est connecté, le rapport de test est chargé sur le locataire du client.

## <a name="sharing-your-test-report"></a>Partage de votre rapport de test

Le rapport de test nécessite une authentification au nom de votre compte Microsoft 365. Votre administrateur sélectionne la façon dont vous pouvez partager votre rapport de test. Les paramètres par défaut permettent le partage de vos rapports avec d’autres utilisateurs de votre organisation et le lien ReportID n’est pas disponible. Les rapports expirent par défaut après 90 jours.

### <a name="sharing-your-report-with-your-administrator"></a>Partage de votre rapport avec votre administrateur

Si vous êtes connecté lorsqu’un rapport de test se produit, le rapport est partagé avec votre administrateur.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Partage avec votre équipe de compte Microsoft, le support technique ou d’autres membres du personnel

Les rapports de test (à l’exclusion de toute identification personnelle) sont partagés avec les employés de Microsoft. Ce partage est activé par défaut et peut être désactivé par votre administrateur dans le **| Page Connectivité réseau** dans le centre de Administration Microsoft 365.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Partage avec d’autres utilisateurs qui se connectent au même locataire Microsoft 365

Vous pouvez choisir des utilisateurs avec lesquels partager votre rapport. Le choix est activé par défaut, mais il peut être désactivé par votre administrateur.

> [!div class="mx-imgBorder"]
> ![Partage d’un lien vers vos résultats de test avec un utilisateur.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Partage avec toute personne utilisant un lien ReportID

Vous pouvez partager votre rapport de test avec n’importe qui en fournissant l’accès à un lien ReportID. Ce lien génère une URL que vous pouvez envoyer à une personne afin qu’elle puisse afficher le rapport de test sans se connecter. Ce partage est désactivé par défaut et doit être activé par votre administrateur.

> [!div class="mx-imgBorder"]
> ![Partage d’un lien vers vos résultats de test.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Résultats du test de connectivité réseau

Les résultats sont affichés dans les onglets **Résumé** et **Détails**. L’onglet Résumé affiche une carte du périmètre réseau détecté et une comparaison de l’évaluation réseau avec d’autres clients Microsoft 365 à proximité. Il permet également le partage du rapport de test. Voici à quoi ressemble l’affichage des résultats récapitulatifs :

> [!div class="mx-imgBorder"]
> ![Résultats récapitulatifs de l’outil de test de connectivité réseau.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Voici un exemple de sortie de l’onglet Détails. Sous l’onglet Détails, nous affichons une coche de cercle vert si le résultat a été comparé favorablement. Nous affichons un point d’exclamation de triangle rouge si le résultat a dépassé un seuil indiquant un insight réseau. Les sections suivantes décrivent chacune des lignes de résultats de l’onglet Détails et expliquent les seuils utilisés pour les insights réseau.

> [!div class="mx-imgBorder"]
> ![Exemples de résultats de test de l’outil de connectivité réseau.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Vos informations d’emplacement

Cette section affiche les résultats des tests liés à votre emplacement.

#### <a name="your-location"></a>Votre emplacement

L’emplacement de l’utilisateur est détecté à partir du navigateur web des utilisateurs. Il peut également être tapé au choix de l’utilisateur. Il est utilisé pour identifier les distances réseau vers des parties spécifiques du périmètre réseau d’entreprise. Seule la ville de cette détection d’emplacement et la distance vers d’autres points réseau sont enregistrées dans le rapport.

L’emplacement du bureau de l’utilisateur s’affiche dans la vue cartographique.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Emplacement de sortie réseau (emplacement où votre réseau se connecte à votre fournisseur de services Internet)

Nous identifions l’adresse IP de sortie réseau côté serveur. Les bases de données d’emplacement sont utilisées pour rechercher l’emplacement approximatif de la sortie réseau. Ces bases de données ont généralement une précision d’environ 90 % des adresses IP. Si l’emplacement recherché à partir de l’adresse IP de sortie réseau n’est pas exact, cela entraînerait un résultat faux. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser des sites web d’emplacement d’adresse IP réseau accessibles publiquement pour comparer votre emplacement réel.

#### <a name="your-distance-from-the-network-egress-location"></a>Votre distance par rapport à l'emplacement de la sortie du réseau

Nous déterminons la distance entre cet emplacement et l’emplacement du bureau. Cela s’affiche sous forme d’insight réseau si la distance est supérieure à **800 kilomètres (500 kilomètres** ), car cela est susceptible d’augmenter la latence TCP de plus de 25 ms et peut affecter l’expérience utilisateur.

La carte montre l’emplacement de sortie du réseau par rapport à l’emplacement du bureau de l’utilisateur indiquant le backhaul réseau à l’intérieur du WAN d’entreprise.

Implémentez la sortie réseau locale et directe des emplacements des bureaux des utilisateurs vers Internet pour une connectivité réseau Microsoft 365 optimale. Les améliorations apportées à la sortie locale et directe constituent la meilleure façon d’aborder cette insight réseau.

#### <a name="proxy-server-information"></a>Informations sur le serveur proxy

Nous identifions si les serveurs proxy sont configurés sur l’ordinateur local pour passer le trafic réseau Microsoft 365 dans la catégorie **Optimiser** . Nous identifions la distance entre l’emplacement du bureau de l’utilisateur et les serveurs proxy.

La distance est d’abord testée par le test ping ICMP. Si cela échoue, nous testons avec TCP ping et enfin, nous cherchons l’adresse IP du serveur proxy dans une base de données d’emplacement d’adresse IP. Nous affichons un insight réseau si le serveur proxy se trouve à plus de **800 kilomètres** de l’emplacement du bureau de l’utilisateur.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Réseau privé virtuel (VPN) que vous utilisez pour vous connecter à votre organisation

Ce test détecte si vous utilisez un VPN pour vous connecter à Microsoft 365. Un résultat de passage indique si vous n’avez pas de VPN ou si vous disposez d’un VPN avec la configuration de tunnel fractionné recommandée pour Microsoft 365.

#### <a name="vpn-split-tunnel"></a>Tunnel fractionné VPN

Chaque itinéraire de catégorie **Optimiser** pour Exchange Online, SharePoint Online et Microsoft Teams est testé pour voir s’il est tunnelné sur le VPN. Une charge de travail fractionnée évite entièrement le VPN. Une charge de travail tunnel est envoyée via le VPN. Une charge de travail tunnel sélective a des itinéraires envoyés sur le VPN et d’autres fractionnés. Un résultat de passage indique si toutes les charges de travail sont fractionnées ou tunnelées sélectivement.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Clients de votre région métropolitaine avec de meilleures performances

La latence réseau entre l’emplacement du bureau de l’utilisateur et le service Exchange Online est comparée aux autres clients Microsoft 365 dans la même zone de métro. Un insight réseau s’affiche si 10 % ou plus des clients de la même région métropolitaine ont de meilleures performances. Cela signifie que leurs utilisateurs auront de meilleures performances dans l’interface utilisateur de Microsoft 365.

Cet insight réseau est généré sur la base du fait que tous les utilisateurs d’une ville ont accès à la même infrastructure de télécommunications et à la même proximité des circuits Internet et du réseau de Microsoft.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Délai d’exécution d’une requête DNS sur votre réseau

Cela montre le serveur DNS configuré sur l’ordinateur client qui a exécuté les tests. Il peut s’agir d’un serveur récursif DNS, mais cela est rare. Il est plus probable qu’il s’agit d’un serveur de redirecteur DNS, qui met en cache les résultats DNS et transfère toutes les demandes DNS non mises en cache à un autre serveur DNS.

Elle est fournie uniquement pour des informations et ne contribue à aucun insight réseau.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Distance et/ou heure de connexion à un programme de résolution récursif DNS

Le programme de résolution récursif DNS en usage est identifié en effectuant une requête DNS spécifique, puis en demandant au serveur de noms DNS l’adresse IP à partir de laquelle il a reçu la même requête. Cette adresse IP est le résolveur récursif DNS et elle sera recherchée dans les bases de données d’emplacement d’adresse IP pour trouver l’emplacement. La distance entre l’emplacement du bureau de l’utilisateur et l’emplacement du serveur récursif DNS est ensuite calculée. Cela s’affiche sous forme d’insight réseau si la distance est supérieure à **500 milles** (800 kilomètres).

L’emplacement recherché à partir de l’adresse IP de sortie du réseau peut ne pas être précis, ce qui entraînerait un résultat faux de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser des sites web d’emplacement d’adresse IP réseau accessibles publiquement.

Cet insight réseau aura un impact spécifique sur la sélection de la porte d’entrée du service Exchange Online. Pour résoudre ce problème, la sortie du réseau local et direct doit être un prérequis, puis le résolveur récursif DNS doit se trouver à proximité de cette sortie réseau.

### <a name="exchange-online"></a>Exchange Online

Cette section affiche les résultats des tests liés à Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Emplacement de la porte d’entrée du service Exchange

La porte d’entrée du service Exchange en cours d’utilisation est identifiée de la même façon qu’Outlook le fait et nous mesurons la latence TCP réseau à partir de l’emplacement utilisateur vers celui-ci. La latence TCP est affichée et la porte d’entrée du service Exchange en cours d’utilisation est comparée à la liste des meilleures portes d’entrée de service pour l’emplacement actuel. Il s’agit d’un insight réseau si l’une des meilleures portes d’entrée du service Exchange n’est pas utilisée.

Le fait de ne pas utiliser l’une des meilleures portes d’entrée du service Exchange peut être dû à un problème de retour réseau avant la sortie du réseau d’entreprise, auquel cas nous recommandons une sortie réseau locale et directe. Cela peut également être dû à l’utilisation d’un serveur de résolution récursif DNS distant, auquel cas nous vous recommandons d’aligner le serveur récursif DNS avec la sortie réseau.

Nous calculons une amélioration potentielle de la latence TCP (ms) à la porte d’entrée du service Exchange. Pour ce faire, examinez la latence réseau de l’emplacement du bureau utilisateur testé et soustrait la latence réseau de l’emplacement actuel à la porte d’entrée du service Exchange des placards. La différence représente l’opportunité potentielle d’amélioration.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Meilleures portes d’entrée du service Exchange pour votre emplacement

Cela répertorie les meilleurs emplacements de porte d’entrée du service Exchange par ville pour votre emplacement.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Porte d’entrée du service enregistrée dans le DNS client

Cela montre le nom DNS et l’adresse IP du serveur de porte d’entrée du service Exchange vers lequel vous avez été dirigé. Il est fourni uniquement pour des informations et il n’existe aucun insight réseau associé.

### <a name="sharepoint-online"></a>SharePoint Online

Cette section affiche les résultats des tests liés à SharePoint Online et OneDrive.

#### <a name="the-service-front-door-location"></a>Emplacement de la porte d’entrée du service

La porte d’entrée du service SharePoint en cours d’utilisation est identifiée de la même façon que le client OneDrive et nous mesurons la latence TCP réseau à partir de l’emplacement du bureau de l’utilisateur vers celui-ci.

#### <a name="download-speed"></a>Vitesse de téléchargement

Nous mesurons la vitesse de téléchargement d’un fichier de 15 Mo à partir de la porte d’entrée du service SharePoint. Le résultat s’affiche en mégaoctets par seconde pour indiquer le fichier de taille en mégaoctets qui peut être téléchargé à partir de SharePoint ou OneDrive en **une seconde**. Le nombre doit être similaire à un dixième de la bande passante minimale du circuit en mégabits par seconde. Par exemple, si vous disposez d’une connexion Internet de 100 Mbits/s, vous pouvez vous attendre à 10 mégaoctets par seconde (10 Mbits/s).

#### <a name="buffer-bloat"></a>Objet bloat de mémoire tampon

Pendant le téléchargement de 15 Mo, nous mesurons la latence TCP sur la porte d’entrée du service SharePoint. Il s’agit de la latence sous charge et elle est comparée à la latence lorsqu’elle n’est pas sous charge. L’augmentation de la latence en cas de charge est souvent attribuable au chargement (ou à l’ballonnement) des mémoires tampons d’appareil réseau consommateur. Un insight réseau s’affiche pour tout objet bloat de 100 ms ou plus.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Porte d’entrée du service enregistrée dans le DNS client

Cela montre le nom DNS et l’adresse IP du serveur de porte d’entrée du service SharePoint vers lequel vous avez été dirigé. Il est fourni uniquement pour des informations et il n’existe aucun insight réseau associé.

### <a name="microsoft-teams"></a>Microsoft Teams

Cette section affiche les résultats des tests liés à Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Connectivité multimédia (partage audio, vidéo et application)

Cette opération teste la connectivité UDP à la porte d’entrée du service Microsoft Teams. Si ce blocage est bloqué, Microsoft Teams peut toujours fonctionner à l’aide de TCP, mais l’audio et la vidéo seront altérés. En savoir plus sur ces mesures réseau UDP, qui s’appliquent également à Microsoft Teams dans [Media Quality and Network Connectivity Performance dans Skype Entreprise Online](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

#### <a name="packet-loss"></a>Perte de paquets

Affiche la perte de paquets UDP mesurée dans un appel audio de test de 10 secondes du client à la porte d’entrée du service Microsoft Teams. Cette valeur doit être inférieure à **1,00 %** pour une passe.

#### <a name="latency"></a>Latence

Affiche la latence UDP mesurée, qui doit être inférieure à **100 ms**.

#### <a name="jitter"></a>Gigue

Affiche la gigue UDP mesurée, qui doit être inférieure à **30 ms**.

#### <a name="connectivity"></a>Connectivité

Nous testons la connectivité HTTP de l’emplacement du bureau de l’utilisateur à tous les points de terminaison réseau Microsoft 365 requis. Ceux-ci sont publiés à l’adresse [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Un insight réseau s’affiche pour tous les points de terminaison réseau requis, auxquels il n’est pas possible de se connecter.

La connectivité peut être bloquée par un serveur proxy, un pare-feu ou un autre appareil de sécurité réseau sur le périmètre du réseau d’entreprise. La connectivité au port TCP 80 est testée avec une requête HTTP et la connectivité au port TCP 443 est testée avec une requête HTTPS. En l’absence de réponse, le nom de domaine complet est marqué comme un échec. S’il existe un code de réponse HTTP 407, le nom de domaine complet est marqué comme un échec. S’il existe un code de réponse HTTP 403, nous vérifions l’attribut Serveur de la réponse et, s’il semble être un serveur proxy, nous le marquerons comme un échec. Vous pouvez simuler les tests que nous effectuons avec l’outil en ligne de commande Windows curl.exe.

Nous testons le certificat SSL à chaque point de terminaison réseau Microsoft 365 requis qui se trouve dans la catégorie Optimiser ou autoriser, comme défini à l’adresse [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Si des tests ne trouvent pas de certificat Microsoft SSL, le réseau chiffré connecté doit avoir été intercepté par un appareil réseau intermédiaire. Un insight réseau s’affiche sur tous les points de terminaison réseau chiffrés interceptés.

Lorsqu’un certificat SSL n’est pas fourni par Microsoft est trouvé, nous affichons le nom de domaine complet pour le test et le propriétaire du certificat SSL en service. Ce propriétaire de certificat SSL peut être un fournisseur de serveur proxy ou un certificat auto-signé d’entreprise.

#### <a name="network-path"></a>Chemin d’accès réseau

Cette section présente les résultats d’un itinéraire de trace ICMP vers la porte d’entrée du service Exchange Online, la porte d’entrée du service SharePoint Online et la porte d’entrée du service Microsoft Teams. Il est fourni uniquement pour des informations et il n’existe aucun insight réseau associé. Trois itinéraires de trace sont fournis. Un itinéraire de trace vers _outlook.office365.com_, un itinéraire de trace vers le serveur frontal SharePoint des clients ou vers _microsoft.sharepoint.com_ si aucun itinéraire n’a été fourni, et un itinéraire de trace vers _world.tr.teams.microsoft.com_.

## <a name="connectivity-reports"></a>Rapports de connectivité

Lorsque vous êtes connecté, vous pouvez consulter les rapports précédents que vous avez exécutés. Vous pouvez également les partager ou les supprimer de la liste.

> [!div class="mx-imgBorder"]
> ![Rapports.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>État d’intégrité du réseau

Cela indique tout problème d’intégrité important avec le réseau mondial de Microsoft, qui peut avoir un impact sur les clients Microsoft 365.

> [!div class="mx-imgBorder"]
> ![État d’intégrité du réseau.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Test à partir de la ligne de commande

Nous fournissons un exécutable de ligne de commande qui peut être utilisé par vos outils de déploiement et d’exécution distants et exécutez les mêmes tests que ceux disponibles dans le site web de l’outil de test de connectivité réseau Microsoft 365.

L’outil de test en ligne de commande peut être téléchargé ici : [Outil de ligne de commande](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Vous pouvez l’exécuter en double-cliquant sur l’exécutable dans Windows Explorateur de fichiers, ou vous pouvez le démarrer à partir d’une invite de commandes, ou vous pouvez le planifier avec le planificateur de tâches.

La première fois que vous lancez l’exécutable, vous êtes invité à accepter le contrat de licence utilisateur final (CLUF) avant d’effectuer le test. Si vous avez déjà lu et accepté le CLUF, vous pouvez créer un fichier vide appelé Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt dans le répertoire de travail actuel pour le processus exécutable lors de son lancement. Pour accepter le CLUF, vous pouvez taper « y » et appuyer sur Entrée dans la fenêtre de ligne de commande lorsque vous y êtes invité.

L’exécutable accepte les paramètres de ligne de commande suivants :
- -h pour afficher un lien vers cette documentation d’aide
- -testlist &lt;spécifie&gt; les tests à exécuter. Par défaut, seuls les tests de base sont exécutés. Les noms de test valides sont les suivants : all, dnsConnectivityPerf, dnsResolverIdentification, bufferBloat, traceroute, proxy, vpn, skype, connectivity, networkInterface
- -filepath &lt;filedir&gt; Directory path of test result files. La valeur autorisée est le chemin absolu ou relatif d’un répertoire accessible
- -city &lt;city&gt; Pour les champs ville, état et pays, la valeur spécifiée sera utilisée si elle est fournie. S’il n’est pas fourni, les services d’emplacement Windows (WLS) sont interrogés. Si WLS échoue, l’emplacement est détecté à partir de la sortie réseau des machines 
- -state state &lt;state&gt;
- -country &lt;country&gt; 
- -proxy &lt;account&gt; &lt;password&gt; proxy account name and password can be provided if you require a proxy to access the Internet

### <a name="results"></a>Résultats
La sortie des résultats est écrite dans un fichier JSON dans un dossier appelé TestResults qui est créé dans le répertoire de travail actuel du processus, sauf s’il existe déjà. Le format de nom de fichier pour la sortie est connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json. Les résultats se trouvent dans les nœuds JSON qui correspondent à la sortie affichée sur la page web du site web de l’outil de test de connectivité réseau Microsoft 365. Un nouveau fichier de résultats est créé chaque fois que vous l’exécutez et l’exécutable autonome ne charge pas les résultats sur votre locataire Microsoft pour l’afficher dans les pages de connectivité réseau Administration Center. Les codes de porte d’entrée, les longitudes et les latitudes ne sont pas inclus dans le fichier de résultats.

### <a name="launching-from-windows-file-explorer"></a>Lancement à partir de Windows Explorateur de fichiers
Vous pouvez simplement double-cliquer sur l’exécutable pour démarrer le test et une fenêtre d’invite de commandes s’affiche.

### <a name="launching-from-the-command-prompt"></a>Lancement à partir de l’invite de commandes
Dans une fenêtre d’invite de commandes CMD.EXE, vous pouvez taper le chemin d’accès et le nom de l’exécutable pour l’exécuter. Le nom de fichier est Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Lancement à partir du planificateur de tâches Windows
Dans Le planificateur de tâches Windows, vous pouvez ajouter une tâche pour lancer l’exécutable de test autonome. Vous devez spécifier le répertoire de travail actuel de la tâche où vous avez créé le fichier accepté par le CLUF, car l’exécutable se bloquera jusqu’à ce que le CLUF soit accepté. Vous ne pouvez pas accepter le CLUF de manière interactive si le processus est démarré en arrière-plan sans console.

### <a name="more-details-on-the-standalone-executable"></a>Plus d’informations sur l’exécutable autonome
L’outil de ligne de commande utilise les services d’emplacement Windows pour rechercher les informations de pays d’état de la ville des utilisateurs pour déterminer certaines distances. Si les services d’emplacement Windows sont désactivés dans le panneau de configuration, les évaluations basées sur l’emplacement utilisateur sont vides. Dans les paramètres Windows, « Services d’emplacement » doit être activé et « Autoriser les applications de bureau à accéder à votre emplacement » doit également être activé.

L’outil de ligne de commande tente d’installer le .NET Framework s’il n’est pas déjà installé. Il télécharge également l’exécutable de test principal à partir de l’outil de test de connectivité réseau Microsoft 365 et le lance.

## <a name="faq"></a>FAQ

Voici les réponses à certaines de nos questions fréquemment posées.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Qu’est-ce qui est nécessaire pour exécuter le client de test avancé ?

Le client de test avancé nécessite le runtime .NET 6.0. Si vous exécutez le client de test avancé sans celui installé, vous êtes dirigé vers [la page du programme d’installation de .NET 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore). Veillez à installer à partir de la colonne Exécuter les applications de bureau pour Windows. Les autorisations d’administrateur sur l’ordinateur sont nécessaires pour installer le runtime .NET 6.0.

Le client de test avancé utilise SignalR pour communiquer avec la page web. Pour cela, vous devez vous assurer que la connectivité du port TCP 443 à **connectivity.service.signalr.net** est ouverte. Cette URL n’est pas publiée dans la <https://aka.ms/o365ip> mesure où cette connectivité n’est pas requise pour un utilisateur d’application cliente Microsoft 365.

### <a name="what-is-microsoft-365-service-front-door"></a>Qu’est-ce que la porte d’entrée du service Microsoft 365 ?

La porte d’entrée du service Microsoft 365 est un point d’entrée sur le réseau mondial de Microsoft où les clients et services Office mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé que votre connexion réseau soit arrêtée dans la porte d’entrée Microsoft 365 la plus proche de votre ville ou de votre métro.

> [!NOTE]
> La porte d’entrée du service Microsoft 365 n’a pas de relation directe avec le produit **Azure Front Door Service** disponible sur la Place de marché Azure.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Quelle est la meilleure porte d’entrée du service Microsoft 365 ?

Une meilleure porte d’entrée du service Microsoft 365 (anciennement appelée porte d’entrée de service optimale) est celle qui est la plus proche de votre sortie réseau, généralement dans votre ville ou région métropolitaine. Utilisez l’outil de performances réseau Microsoft 365 pour déterminer l’emplacement de votre porte d’entrée de service Microsoft 365 en service et la meilleure porte d’entrée de service. Si l’outil détermine que votre porte d’entrée en service est l’une des meilleures, vous devez vous attendre à une connectivité optimale au réseau mondial de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Il s’agit également de l’emplacement où vous disposez d’un appareil NAT (Network Address Translation) et généralement où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement de sortie Internet, cela peut identifier une forme de backhaul WAN significative.

## <a name="related-topics"></a>Voir aussi

[Connectivité réseau dans le centre de Administration Microsoft 365](office-365-network-mac-perf-overview.md)

[Insights sur les performances réseau de Microsoft 365](office-365-network-mac-perf-insights.md)

[Évaluation du réseau Microsoft 365](office-365-network-mac-perf-score.md)

[Services d’emplacement de connectivité réseau Microsoft 365](office-365-network-mac-location-services.md)
