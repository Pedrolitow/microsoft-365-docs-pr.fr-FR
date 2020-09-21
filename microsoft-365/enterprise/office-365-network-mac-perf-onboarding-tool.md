---
title: Test de connectivité réseau Microsoft 365 (aperçu)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/17/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Test de connectivité réseau Microsoft 365 (aperçu)
ms.openlocfilehash: 40a46ecb39366c64c99077e90bb35c5056f36b9d
ms.sourcegitcommit: cd11588b47904c7d2ae899a9f5280f93d3850171
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2020
ms.locfileid: "48171349"
---
# <a name="microsoft-365-network-connectivity-test-preview"></a>Test de connectivité réseau Microsoft 365 (aperçu)

L’outil de test de connectivité réseau Microsoft 365 se trouve à l’adresse <https://connectivity.office.com> . Il s’agit d’un outil complémentaire pour les informations sur l’évaluation du réseau et les informations sur le réseau disponibles dans le centre d’administration Microsoft 365 sous **Health | Menu connectivité** .

![Outil de test de connectivité](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>L’outil de test de connectivité réseau prend en charge les clients dans le commerce WW et l’Allemagne, mais pas dans les GCC modérés, GCC High, DoD ou Chine.

Le réseau Insights dans le centre d’administration 365 de Microsoft est basé sur des mesures de produit standard pour votre client Microsoft 365 qui sont agrégées chaque jour. En comparaison, les informations réseau du test de connectivité réseau Microsoft 365 sont exécutées localement et une fois dans l’outil. Les tests pouvant être effectués dans-le produit sont limités et l’exécution de tests locaux sur l’utilisateur permet de collecter davantage de données, ce qui donne lieu à des analyses plus approfondies. Envisagez ensuite que le réseau Insights dans le centre d’administration 365 de Microsoft indique qu’il existe un problème de réseau pour l’utilisation de Microsoft 365 à un emplacement de bureau spécifique. Le test de connectivité de Microsoft 365 peut vous aider à identifier la cause première de ce problème à l’aide d’une action d’amélioration des performances réseau recommandée.

Nous vous recommandons de les utiliser ensemble pour évaluer l’état de la qualité du réseau pour chaque emplacement de bureau dans le centre d’administration 365 de Microsoft et d’autres informations spécifiques après le déploiement des tests en fonction du test de connectivité de Microsoft 365.

>[!IMPORTANT]
>Les informations sur le réseau, les recommandations en matière de performances et les évaluations dans le centre d’administration 365 de Microsoft sont actuellement en état d’aperçu et sont uniquement disponibles pour les locataires Microsoft 365 qui ont été apportées dans le programme d’aperçu des fonctionnalités.

## <a name="what-happens-at-each-test-step"></a>Que se passe-t-il à chaque étape de test ?

### <a name="office-location-identification"></a>Identification de l’emplacement Office

Lorsque vous cliquez sur le bouton exécuter le test, vous affichez la page de test en cours d’exécution et identifiez l’emplacement du bureau. Vous pouvez taper votre emplacement par ville, État et pays ou vous pouvez le détecter à partir du navigateur Web. Si vous la détectez ensuite, nous recherchons la latitude et la longitude à partir du navigateur Web et limitons la précision à 300 m par 300M avant l’utilisation. Nous faisons cela car il n’est pas nécessaire d’identifier l’emplacement de manière plus précise que les performances du réseau. 

### <a name="javascript-tests"></a>Tests JavaScript

Après l’identification de l’emplacement Office, nous exécutons un test de latence TCP dans JavaScript et nous demandeons des données au service concernant les serveurs frontaux de service Office 365 en cours d’utilisation et recommandés. Une fois terminées, nous les affichons sur la carte et dans l’onglet Détails, où elles peuvent être affichées avant la prochaine étape.

### <a name="download-the-advanced-tests-client-application"></a>Télécharger l’application cliente de tests avancés

Nous allons ensuite démarrer le téléchargement de l’application cliente de tests avancés. Nous comptons sur l’utilisateur pour lancer l’application cliente et l’installation de .NET Core doit également être installée.

Il existe deux parties au test de connectivité réseau Microsoft 365 ; le site Web <https://connectivity.office.com> et une application cliente téléchargeable Windows qui exécute des tests de connectivité réseau avancés. La plupart des tests requièrent l’exécution de l’application. Il remplira de nouveau les résultats dans la page Web lors de son exécution.

Vous serez invité à télécharger l’application de test de client avancée à partir du site Web une fois les tests de navigateur Web terminés. Ouvrez et exécutez le fichier lorsque vous y êtes invité.

![Application cliente de tests avancés](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Démarrer l’application cliente de tests avancés

Une fois que l’application cliente démarre la page Web est mise à jour pour afficher et que les données de test commencent à être reçues sur la page Web. Elle est mise à jour chaque fois que de nouvelles données sont reçues et vous pouvez passer en revue les données à mesure qu’elles arrivent.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Tests avancés terminés et chargement des rapports de test

Une fois les tests terminés, la page Web et le client de tests avancés l’indiquent et, si l’utilisateur est signé, le rapport de test est téléchargé vers le client client.

## <a name="sharing-your-test-report"></a>Partage de votre rapport de test

Le rapport de test nécessite une connexion à votre compte Office 365. Votre administrateur sélectionne la manière dont vous pouvez partager votre rapport de test.

### <a name="sharing-your-report-with-your-administrator"></a>Partage de votre rapport avec votre administrateur

Tous les rapports de test pendant que vous êtes connecté sont partagés avec votre administrateur.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Partage avec votre équipe de compte Microsoft, support technique ou autres membres du personnel

Les rapports de test sans identification personnelle sont partagés avec les employés Microsoft. Cette option est activée par défaut et peut être désactivée par votre administrateur dans le paramètre **intégrité | Page connectivité réseau** dans le centre d’administration 365 de Microsoft.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-office-365-tenant"></a>Partage avec d’autres utilisateurs qui se connectent au même client Office 365

Vous pouvez choisir les utilisateurs pour lesquels vous souhaitez partager votre rapport, et cette option est activée par défaut. Elle peut également être désactivée par votre administrateur.

![Partage d’un lien vers vos résultats de test avec un utilisateur](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Partager avec quiconque en utilisant un lien ReportID

Vous pouvez partager votre rapport de test avec quiconque en fournissant un accès à un lien ReportID. Cette opération génère une URL que vous pouvez envoyer à quelqu’un afin qu’il puisse afficher le rapport de test sans se connecter. Cette option est désactivée par défaut et doit être activée par votre administrateur.

![Partage d’un lien vers vos résultats de test](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Résultats des tests de connectivité réseau

Les résultats sont affichés dans les onglets **Résumé** et **Détails** . L’onglet Résumé affiche une carte du périmètre réseau détecté et une comparaison entre l’évaluation du réseau et les autres clients Office 365 à proximité. Elle permet également de partager le rapport de test. Voici à quoi ressemble l’affichage des résultats de synthèse.

![Résultats de synthèse de l’outil de test connectivité réseau](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Voici un exemple de la sortie de l’onglet Détails que l’outil affiche. Dans l’onglet Détails, une coche de cercle vert s’affiche si le résultat a été comparé favorablement à un seuil. Nous affichons un point d’exclamation de triangle rouge si le résultat dépassait un seuil indiquant un aperçu réseau. Les sections suivantes décrivent chacune des lignes de résultats de l’onglet Détails et expliquent les seuils utilisés pour les informations sur le réseau.

![Exemple de résultats de test de connectivité réseau](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Informations de votre emplacement

Cette section affiche les résultats des tests liés à votre emplacement.

#### <a name="your-location"></a>Votre emplacement

L’emplacement de l’utilisateur est détecté à partir du navigateur Web des utilisateurs ou il peut être saisi au choix des utilisateurs. Il permet d’identifier les distances réseau par des parties spécifiques du périmètre réseau de l’entreprise. Seule la ville de cette détection d’emplacement et la distance aux autres points réseau sont enregistrées dans le rapport.

L’emplacement du Bureau de l’utilisateur est indiqué sur la carte.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Emplacement de sortie réseau (emplacement où votre réseau se connecte à votre fournisseur de services Internet)

Nous identifions l’adresse IP de sortie réseau côté serveur. Les bases de données d’emplacement sont utilisées pour Rechercher l’emplacement approximatif de la sortie réseau. Ces bases de données ont généralement une précision d’environ 90% des adresses IP. Si l’emplacement recherché à partir de l’adresse IP de sortie réseau n’est pas exact, cela entraînerait un résultat faux à partir de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser les sites Web d’emplacement d’adresses IP réseau accessibles au public pour comparer votre emplacement réel.

#### <a name="your-distance-from-the-network-egress-location"></a>Votre distance par rapport à l’emplacement de sortie réseau

Nous déterminons la distance à partir de cet emplacement vers l’emplacement du bureau. Il s’agit d’un aperçu réseau si la distance est supérieure à **500 milles** (800 kilomètres), car cela est susceptible d’augmenter la latence TCP de plus de 25ms et peut affecter l’expérience utilisateur.

L’emplacement de sortie du réseau est affiché sur la carte et connecté à l’emplacement du Bureau de l’utilisateur indiquant le trajet réseau à l’intérieur du réseau étendu de l’entreprise.

L’implémentation d’une sortie réseau locale et directe à partir d’emplacements de bureau d’utilisateurs vers Internet est recommandée pour la connectivité réseau Microsoft 365. Les améliorations apportées à la sortie locale et directe sont la meilleure façon de traiter cette analyse réseau.

#### <a name="proxy-server-information"></a>Informations sur le serveur proxy

Nous allons identifier les serveurs proxy configurés sur l’ordinateur local. Nous allons identifier si l’un de ces éléments est configuré dans le chemin d’accès réseau pour optimiser la catégorie trafic réseau Microsoft 365. Nous identifions la distance entre l’emplacement du Bureau de l’utilisateur et les serveurs proxy. La distance est testée en premier par la commande ping ICMP et, si cela échoue, que nous testons avec le ping TCP et finalement, si cette opération échoue, nous examinons l’adresse IP du serveur proxy dans une base de données d’emplacement d’adresse IP. Nous affichons un Network Insight si le serveur proxy est plus de **500 kilomètres** (800 kilomètres) de l’emplacement du Bureau de l’utilisateur.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Réseau privé virtuel (VPN) que vous utilisez pour vous connecter à votre organisation

Cela détecte si vous utilisez un VPN pour vous connecter à Office 365. Un résultat de transmission s’affiche si vous n’avez pas de réseau privé virtuel (VPN) ou si vous disposez d’un VPN avec la configuration de tunnel fractionné recommandée pour Office 365.

#### <a name="vpn-split-tunnel"></a>Tunnel VPN Split

Chaque itinéraire de catégorie Optimize for Exchange Online, SharePoint Online et Microsoft teams est testé pour vérifier s’il est en tunnel sur le réseau privé virtuel (VPN) ou non. Une charge de travail fractionnée évite totalement le VPN. Une charge de travail en tunnel est entièrement envoyée via le VPN. Une charge de travail sélective par tunnel comporte des itinéraires envoyés via le VPN et d’autres. Un résultat de transmission s’affiche si toutes les charges de travail sont divisées ou par tunneling sélective.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Les clients de votre région métropolitaine avec de meilleures performances

La latence TCP réseau de l’emplacement du Bureau de l’utilisateur vers le capot frontal du service Exchange Online est comparée à celle des autres clients Microsoft 365 dans la même région de métro. Un aperçu réseau s’affiche si 10% ou plus de clients dans la même zone de métro offrent de meilleures performances. Cela signifie que leurs utilisateurs bénéficieront de meilleures performances dans l’interface utilisateur de Microsoft 365.

Cette vue réseau est générée en fonction du fait que tous les utilisateurs d’une ville ont accès à la même infrastructure de télécommunications et à la même proximité des circuits Internet et du réseau de Microsoft.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Temps nécessaire pour effectuer une demande DNS sur votre réseau

Cela indique le serveur DNS configuré sur l’ordinateur client qui a exécuté les tests. Il peut s’agir d’un serveur de résolution récursive DNS, mais cela n’est pas courant. Il est plus probable qu’un serveur de redirection DNS met en cache les résultats DNS et transfère les demandes DNS non mises en cache vers un autre serveur DNS.

Il est fourni à des fins d’information uniquement et ne contribue pas à une analyse réseau.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Distance à partir de et/ou de l’heure de connexion à un solveur récursive DNS

Le programme de résolution de contenu DNS en cours d’utilisation est identifié en effectuant une demande DNS spécifique, puis en demandant au serveur de noms DNS l’adresse IP à partir de laquelle il a reçu la même demande. Cette adresse IP est le résolveur récursif DNS et il est recherché dans les bases de données d’emplacement des adresses IP pour trouver l’emplacement. La distance entre l’emplacement du Bureau de l’utilisateur et l’emplacement du serveur de résolution récursive DNS est ensuite calculée. Il s’agit d’un aperçu réseau si la distance est supérieure à **500 kilomètres** (800 kilomètres).

L’emplacement recherché à partir de l’adresse IP de sortie du réseau n’est peut-être pas exact, ce qui entraîne un résultat faux de ce test. Pour vérifier si cette erreur se produit pour une adresse IP spécifique, vous pouvez utiliser les sites Web d’emplacement d’adresses IP réseau accessibles au public.

Cette analyse réseau a un impact spécifique sur la sélection du capot frontal du service Exchange Online. Pour répondre à cette compréhension, la sortie locale et directe du réseau doit être un prérequis, puis le résolveur DNS récursif doit se trouver près de cette sortie réseau.

### <a name="exchange-online"></a>Exchange Online

Cette section présente les résultats des tests liés à Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Emplacement des portes frontales du service Exchange

La porte d’appel frontale du service Exchange en cours d’utilisation est identifiée de la même manière qu’Outlook le fait et nous Mesurez la latence du réseau TCP depuis l’emplacement de l’utilisateur vers celui-ci. La latence TCP est indiquée et la porte d’appel frontale du service Exchange est comparée à la liste des meilleures portes avant de service pour l’emplacement actuel. Il s’agit d’un aperçu réseau si l’une des meilleures portes avant du service Exchange n’est pas utilisée.

Le fait de ne pas utiliser l’une des meilleures portes avant du service Exchange peut être dû à la sortie du réseau d’entreprise avant la sortie du réseau d’entreprise, auquel cas nous vous recommandons de sortir du réseau local et direct. Il peut également être dû à l’utilisation d’un serveur de résolution récursive DNS à distance dans ce cas, nous vous recommandons d’aligner le serveur de résolution récursive DNS avec la sortie réseau.

Nous calculons une amélioration potentielle de la latence TCP (MS) vers le capot frontal du service Exchange. Cette opération est réalisée en examinant la latence du réseau des utilisateurs testés et en soustrayant la latence réseau de l’emplacement actuel vers le capot frontal du service Exchange armoires. La différence représente la possibilité d’amélioration potentielle.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Meilleure porte (s) de service Exchange pour votre emplacement

Cette liste répertorie les meilleurs emplacements de portes avant de service Exchange par ville pour votre emplacement.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Portes frontales de service enregistrées dans le DNS du client

Indique le nom DNS et l’adresse IP du serveur de portes frontales du service Exchange auquel vous étiez dirigé. Il est fourni à des fins d’information uniquement et aucune analyse réseau n’est associée.

### <a name="sharepoint-online"></a>SharePoint Online

Cette section présente les résultats des tests liés à SharePoint Online et OneDrive.

#### <a name="the-service-front-door-location"></a>Emplacement de la porte avant du service

La porte d’appel frontale SharePoint service est identifiée de la même manière que le client OneDrive, et la latence du réseau TCP est mesurée à partir de l’emplacement du Bureau de l’utilisateur.

#### <a name="download-speed"></a>Vitesse de téléchargement

Nous mesurons la vitesse de téléchargement d’un fichier de 15 Mo à partir du volet frontal du service SharePoint. Le résultat est indiqué en mégaoctets par seconde pour indiquer la taille du fichier en mégaoctets pouvant être téléchargé à partir de SharePoint ou de OneDrive en **une seconde**. Le nombre doit ressembler à un dixième de la bande passante minimale du circuit en mégabits par seconde. Par exemple, si vous disposez d’une connexion Internet à 100 Mbps, vous pouvez vous attendre à 10 mégaoctets par seconde (10 Mbits/s).

#### <a name="buffer-bloat"></a>Augmentation de la mémoire tampon

Pendant le téléchargement de 15 Mo, nous Mesurez la latence TCP sur la porte d’accès frontale du service SharePoint. Il s’agit de la latence sous charge et est comparée à la latence lorsque celle-ci n’est pas chargée. L’augmentation de la latence lors de la charge est souvent imputable aux mémoires tampon du périphérique du réseau grand public en cours de chargement (ou encombrées). Un aperçu réseau est affiché pour toute augmentation de 1 000 ou plus.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Portes frontales de service enregistrées dans le DNS du client

Indique le nom DNS et l’adresse IP du serveur de portes frontales du service SharePoint auquel vous étiez dirigé. Il est fourni à des fins d’information uniquement et aucune analyse réseau n’est associée.

### <a name="microsoft-teams"></a>Microsoft Teams

Cette section présente les résultats des tests liés à Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Connectivité multimédia (audio, vidéo et partage d’applications)

Cela permet de tester la connectivité UDP au porte-tout du service Microsoft Teams. Si elle est bloquée, il est possible que Microsoft teams fonctionne toujours en utilisant le protocole TCP, mais les fonctionnalités audio et vidéo seront altérées. En savoir plus sur ces mesures de réseau UDP, qui s’appliquent également à Microsoft teams en matière de [performances de la qualité des médias et de la connectivité réseau dans Skype entreprise Online](https://docs.microsoft.com/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance)

#### <a name="packet-loss"></a>Perte de paquets

Indique la perte de paquets UDP mesurée dans un appel audio de test de 10 secondes entre le client et le porte-tout du service Microsoft Teams. Cette limite doit être inférieure à **1,00%** pour un passe.

### <a name="latency"></a>Latence

Indique la latence UDP mesurée, qui doit être inférieure à **100 ms**.

#### <a name="jitter"></a>Scintill

Indique la gigue UDP mesurée, qui doit être inférieure à **30ms**.

#### <a name="connectivity"></a>Connectivité

Nous testons la connectivité HTTP à partir de l’emplacement du Bureau de l’utilisateur vers tous les points de terminaison réseau Microsoft 365 requis. Ces éléments sont publiés à l’adresse [https://aka.ms/o365ip](https://aka.ms/o365ip) . Network Insight est illustré pour les points de terminaison réseau requis qui ne peuvent pas être connectés à.

La connectivité ay est bloquée par un serveur proxy, un pare-feu ou un autre périphérique de sécurité réseau sur le périmètre du réseau d’entreprise ou en cours d’utilisation en tant que proxy Cloud.

Nous testons le certificat SSL à chaque point de terminaison réseau Microsoft 365 requis qui se trouve dans la catégorie Optimize ou Allow, comme défini sur [https://aka.ms/o365ip](https://aka.ms/o365ip) . Si un ou plusieurs tests ne trouvent pas de certificat SSL Microsoft, le réseau chiffré doit avoir été intercepté par un périphérique réseau intermédiaire. Un Network Insight est illustré sur tous les points de terminaison réseau chiffrés interceptés.

Lorsqu’un certificat SSL n’est pas fourni par Microsoft, nous affichons le nom de domaine complet (FQDN) pour le test et le propriétaire du certificat SSL en cours d’utilisation. Ce propriétaire de certificat SSL peut être un fournisseur de serveur proxy, ou il peut s’agir d’un certificat auto-signé de l’entreprise.

#### <a name="network-path"></a>Chemin d’accès réseau

Cette section présente les résultats d’un itinéraire ICMP vers le volet frontal du service Exchange Online, le volet frontal du service SharePoint Online et le porte de service frontal de Microsoft Teams. Il est fourni à des fins d’information uniquement et aucune analyse réseau n’est associée. Trois traceroutes sont fournies. Un traceroute vers _Outlook.office365.com_, un traceroute vers le serveur frontal SharePoint du client ou vers _Microsoft.SharePoint.com_ s’il n’en a pas été fourni, et un traceroute vers _World.TR.Teams.Microsoft.com_.

## <a name="connectivity-reports"></a>Rapports de connectivité

Lorsque vous êtes connecté, vous pouvez consulter les rapports précédents que vous avez exécutés. Vous pouvez également les partager ou les supprimer de la liste.

![Rapports](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>État de l’intégrité du réseau

Cela présente des problèmes d’intégrité significatifs avec le réseau mondial de Microsoft, qui peuvent avoir un impact sur les clients de Microsoft 365.

![État de l’intégrité du réseau](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="faq"></a>Forum Aux Questions

Voici des réponses à certaines de nos questions fréquemment posées.

### <a name="is-this-tool-released-and-supported-by-microsoft"></a>Cet outil est-il publié et pris en charge par Microsoft ?

Il s’agit actuellement d’un aperçu et nous prévoyons de fournir des mises à jour régulièrement jusqu’à ce que nous arrivions à l’état de publication de disponibilité générale avec prise en charge de Microsoft. Veuillez nous faire part de vos commentaires afin de nous aider à améliorer. Nous prévoyons de publier un guide d’intégration réseau Office 365 plus détaillé dans le cadre de cet outil, qui est personnalisé pour l’organisation par les résultats des tests.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Qu’est-ce qui est requis pour exécuter le client de test avancé ?

Le client de test avancé requiert .NET Core 3,1 Desktop Runtime. Si vous exécutez le client de test avancé sans l’installer, vous serez redirigé vers [la page .net Core 3,1 installer](https://dotnet.microsoft.com/download/dotnet-core/3.1). Veillez à installer le runtime de bureau et non le kit de développement logiciel, ou le runtime ASP.NET principal qui est plus haut sur la page. Les autorisations d’administrateur sur l’ordinateur sont requises pour installer .NET Core. 

### <a name="what-is-microsoft-365-service-front-door"></a>Qu’est-ce que le service frontal de Microsoft 365 ?

Le service frontal Microsoft 365 est un point d’entrée sur le réseau mondial de Microsoft où les clients et les services Office mettent fin à leur connexion réseau. Pour une connexion réseau optimale à Microsoft 365, il est recommandé que votre connexion réseau soit interrompue dans le volet frontal Microsoft 365 le plus proche de votre ville ou de votre métro.

Remarque : le service frontal de Microsoft 365 n’a pas de relation directe avec le produit du **service de capot frontal Azure** disponible sur Azure Marketplace.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Quelle est la meilleure porte d’avance sur le service Microsoft 365 ?

Une meilleure porte d’appel de service Microsoft 365 (anciennement connu sous le nom de porte d’accès frontale de service optimale) est la plus proche de la sortie de votre réseau, généralement dans votre ville ou votre zone de métro. Utilisez l’outil de performances réseau Microsoft 365 pour déterminer l’emplacement de votre porte d’appel de service Microsoft 365 et des portes avant du service. Si l’outil détermine que votre porte frontale en cours est l’une des meilleures, vous devez vous attendre à une connectivité efficace dans le réseau global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>Qu’est-ce qu’un emplacement de sortie Internet ?

L’emplacement de sortie Internet est l’emplacement où votre trafic réseau quitte votre réseau d’entreprise et se connecte à Internet. Elle est également identifiée comme l’emplacement où vous avez un périphérique de traduction d’adresses réseau (NAT) et généralement l’endroit où vous vous connectez avec un fournisseur de services Internet (ISP). Si vous voyez une longue distance entre votre emplacement et votre emplacement Internet sortant, cela peut indiquer une sorte de trajet WAN important.

## <a name="related-topics"></a>Voir aussi

[Recommandations relatives aux performances réseau dans le centre d’administration Microsoft 365 (version préliminaire)](office-365-network-mac-perf-overview.md)

[Informations sur les performances du réseau Microsoft 365 (aperçu)](office-365-network-mac-perf-insights.md)

[Microsoft 365 Network Assessment (aperçu)](office-365-network-mac-perf-score.md)

[Services d’emplacement de connectivité réseau Microsoft 365 (aperçu)](office-365-network-mac-location-services.md)
