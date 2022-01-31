---
title: Implémentation de la tunneling fractionnement VPN pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/28/2022
audience: Admin
ms.article: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Comment implémenter la tunneling fractionnement VPN pour Microsoft 365
ms.openlocfilehash: 59414e32f187dc4e8354dc0c20228a4222fa2754
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2022
ms.locfileid: "62281181"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implémentation de la tunneling fractionnement VPN pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour une vue d’ensemble de l’utilisation de la tunneling fractionnement VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, voir Vue d’ensemble : [tunneling fractionnel VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour plus d’informations sur l Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

Depuis de nombreuses années, les entreprises utilisent des VPN pour prendre en charge les expériences à distance pour leurs utilisateurs. Bien que les charges de travail principales restent en local, un VPN du client distant acheminé via un centre de données sur le réseau d’entreprise était la méthode principale pour les utilisateurs distants pour accéder aux ressources d’entreprise. Pour protéger ces connexions, les entreprises construisent des couches de solutions de sécurité réseau sur les chemins VPN. Cette sécurité a été conçue pour protéger l’infrastructure interne et pour protéger la navigation mobile des sites web externes en réroutant le trafic vers le VPN, puis via le périmètre Internet local. Les VPN, les périmètres réseau et l’infrastructure de sécurité associée ont souvent été conçus et mis à l’échelle pour un volume défini de trafic, généralement avec la plupart de la connectivité initiée à partir du réseau d’entreprise et la plupart d’entre elles restant dans les limites du réseau interne.

Pendant un certain temps, les modèles VPN où toutes les connexions à partir de l’appareil utilisateur distant sont routés vers le réseau local (appelées _tunnel imposé_) étaient très durables tant que l’échelle simultanée des utilisateurs distants était modeste et que les volumes de trafic qui traversent le réseau privé (VPN) étaient faibles.  Certains clients ont continué à utiliser le tunneling de force VPN comme état de quo même après que leurs applications ont été déplacées de l’intérieur du périmètre d’entreprise vers les clouds SaaS publics.

L’utilisation de VPN tunnelés forcés pour la connexion à des applications cloud distribuées et sensibles aux performances est sous-optimale, mais les effets négatifs ont été acceptés par certaines entreprises afin de maintenir le quo de sécurité. Un exemple de diagramme de ce scénario est illustré ci-dessous :

![Fractionner Tunnel la configuration VPN.](../media/vpn-split-tunneling/enterprise-network-traditional.png)

This problem has been growing for many years, with many customers reporting a significant shift of network traffic patterns. Le trafic qui était utilisé pour rester sur site se connecte désormais aux points de terminaison cloud externes. De nombreux clients Microsoft signalent qu’auparavant, environ 80 % du trafic réseau était vers une source interne (représentée par la ligne pointillée dans le diagramme ci-dessus). En 2020, ce nombre est désormais d’environ 20 % ou moins car ils ont déplacé des charges de travail majeures vers le cloud, ces tendances ne sont pas rares avec d’autres entreprises. Au fil du temps, au fur et à mesure de l’évolution du cloud, le modèle ci-dessus devient de plus en plus fastidieux et fastidieux, empêchant ainsi une organisation d’être agile au fur et à mesure qu’elle passe à un monde avant tout cloud.

La crise mondiale de grippe COVID-19 a aggravé ce problème et exige des mesures correctives immédiates. La nécessité d'assurer la sécurité des employés a généré des demandes sans précédent en matière de technologies de l'information pour prendre en charge la productivité du travail à domicile à une échelle massive. Microsoft 365 est bien placé pour aider les clients à répondre à cette demande, mais la forte concurrence des utilisateurs travaillant à domicile génère un volume élevé de trafic Microsoft 365 qui, s’il est acheminé via un tunnel forcé VPN et des périmètres réseau locaux, entraîne une saturation rapide et exécute l’infrastructure VPN hors capacité. Dans cette nouvelle réalité, l’utilisation du VPN pour accéder à Microsoft 365 n’est plus seulement un obstacle aux performances, mais un mur dur qui non seulement a un impact sur les Microsoft 365 mais également sur les opérations d’entreprise critiques qui doivent encore s’appuyer sur le VPN pour fonctionner.

Microsoft travaille en étroite collaboration avec des clients et une grande industrie depuis de nombreuses années afin d’offrir des solutions efficaces et modernes à ces problèmes à partir de nos propres services et de s’adapter aux meilleures pratiques industrielles. Les principes de connectivité du service Microsoft 365 ont été conçus pour fonctionner efficacement pour les [utilisateurs distants](./microsoft-365-network-connectivity-principles.md) tout en permettant à une organisation de maintenir la sécurité et de contrôler sa connectivité. Ces solutions peuvent également être implémentées rapidement avec un travail limité tout en ayant un impact positif significatif sur les problèmes décrits ci-dessus.

La stratégie recommandée par Microsoft pour optimiser la connectivité des travailleurs à distance est axée sur la réduction rapide des problèmes et la fourniture de performances élevées en quelques étapes simples. Ces étapes ajustent l’approche VPN héritée pour quelques points de terminaison définis qui contournent les serveurs VPN en goulot d’étranglement. Un modèle de sécurité équivalent, voire supérieur, peut être appliqué dans différentes couches pour supprimer la nécessité de sécuriser tout le trafic à la sortie du réseau d’entreprise. Dans la plupart des cas, cela peut être réalisé efficacement en quelques heures et est ensuite évolutif à d’autres charges de travail, selon la demande et le temps requis.

## <a name="common-vpn-scenarios"></a>Scénarios VPN courants

Dans la liste ci-dessous, vous verrez les scénarios VPN les plus courants dans les environnements d’entreprise. La plupart des clients utilisent généralement le modèle 1 (tunnel imposé VPN). Cette section vous aidera à passer rapidement et en toute sécurité au modèle **2**, ce qui est réalisable avec un effort relativement faible et qui présente des avantages considérables pour les performances du réseau et l’expérience utilisateur.

| Modèle | Description |
| --- | --- |
| [1. Tunnel imposé VPN](#1-vpn-forced-tunnel) | 100 % du trafic passe dans le tunnel VPN, y compris sur site, Internet et tout O365/M365 |
| [2. Tunnel imposé VPN avec quelques exceptions](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) | Le tunnel VPN est utilisé par défaut (point d’itinéraire par défaut vers VPN), avec peu de scénarios d’exemption les plus importants autorisés à passer directement |
| [3. Tunnel imposé VPN avec de larges exceptions](#3-vpn-forced-tunnel-with-broad-exceptions) | Le tunnel VPN est utilisé par défaut (points d’itinéraire par défaut vers VPN), avec de grandes exceptions qui sont autorisées à passer directement (par exemple, tous les Microsoft 365, Tous les salesforce, Tous les zooms) |
| [4. Tunnel sélectif VPN](#4-vpn-selective-tunnel) | Le tunnel VPN est utilisé uniquement pour les services basés sur un réseau d’entreprise. L’itinéraire par défaut (Internet et tous les services Internet) est directement acheminé. |
| [5. Pas de VPN](#5-no-vpn) | Variante de #2. Au lieu du VPN hérité, tous les services de réseau d’entreprise sont publiés par le biais d’approches de sécurité modernes (comme Zscaler ZPA, Azure Active Directory (Azure AD) Proxy/MCAS, etc.) |

### <a name="1-vpn-forced-tunnel"></a>1. Tunnel imposé VPN

Scénario de départ le plus courant pour la plupart des clients d’entreprise. Un VPN forcé est utilisé, ce qui signifie que 100 % du trafic est dirigé vers le réseau d’entreprise, que le point de terminaison réside dans le réseau d’entreprise ou non. Tout trafic externe (Internet) tel que Microsoft 365 ou la navigation Internet est ensuite épinglé à l’extérieur de l’équipement de sécurité local, tel que les proxies. Dans le monde actuel où près de 100 % des utilisateurs travaillent à distance, ce modèle met donc une charge élevée sur l’infrastructure VPN et est susceptible d’entraver considérablement les performances de l’ensemble du trafic d’entreprise et donc de l’entreprise pour fonctionner efficacement en temps de crise.

![Vpn forced Tunnel model 1.](../media/vpn-split-tunneling/vpn-model-1.png)

### <a name="2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions"></a>2. Tunnel imposé VPN avec un petit nombre d’exceptions approuvées

Considérablement plus efficace pour qu’une entreprise fonctionne. Ce modèle permet à quelques points de terminaison contrôlés et définis qui sont sensibles à la charge élevée et à la latence de contourner le tunnel VPN et d’être directement Microsoft 365 service. Cela améliore considérablement les performances des services déchargés et réduit également la charge sur l’infrastructure VPN, ce qui permet aux éléments qui en ont encore besoin de fonctionner avec une contention moindre des ressources. C’est sur ce modèle que cet article se concentre sur l’assistance à la transition, car il permet d’agir rapidement sur des actions simples et définies avec de nombreux résultats positifs.

![Fractionner Tunnel vpn modèle 2.](../media/vpn-split-tunneling/vpn-model-2.png)

### <a name="3-vpn-forced-tunnel-with-broad-exceptions"></a>3. Tunnel imposé VPN avec de larges exceptions

Élargit l’étendue du modèle 2. Au lieu d’envoyer directement un petit groupe de points de terminaison définis, il envoie tout le trafic directement aux services de confiance tels que Microsoft 365 et SalesForce. Cela permet de réduire davantage la charge sur l’infrastructure VPN d’entreprise et d’améliorer les performances des services définis. Comme ce modèle est susceptible de prendre plus de temps pour évaluer la faisabilité et l’implémenter, il s’agit probablement d’une étape qui peut être prise de manière itérative à une date ultérieure une fois que le modèle 2 est correctement mis en place.

![Fractionner Tunnel VPN modèle 3.](../media/vpn-split-tunneling/vpn-model-3.png)

### <a name="4-vpn-selective-tunnel"></a>4. Tunnel sélectif VPN

Inverse le troisième modèle dans la mesure où seul le trafic identifié comme ayant une adresse IP d’entreprise est envoyé vers le bas du tunnel VPN et par conséquent, le chemin d’accès Internet est l’itinéraire par défaut pour tout le reste. Ce modèle nécessite qu’une organisation se trouve bien sur le chemin d’accès [Approbation zéro](https://www.microsoft.com/security/zero-trust?rtc=1) pour pouvoir implémenter ce modèle en toute sécurité. Il convient de noter que ce modèle ou une variante de celui-ci deviendra probablement la valeur par défaut nécessaire au fil du temps, car de plus en plus de services s’éloignent du réseau d’entreprise et se déplacent vers le cloud.

Microsoft utilise ce modèle en interne. Vous trouverez plus d’informations sur l’implémentation par Microsoft de la tunneling fractionnement VPN lors de l’exécution sur VPN : comment Microsoft maintient ses employés à [distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv).

![Modèle VPN Tunnel partagé 4.](../media/vpn-split-tunneling/vpn-model-4.png)

### <a name="5-no-vpn"></a>5. Pas de VPN

Une version plus avancée du modèle numéro 2, dans laquelle tous les services internes sont publiés par le biais d’une approche de sécurité moderne ou d’une solution SDWAN telle que Azure AD Proxy, Defender pour les applications cloud, Zscaler ZPA, etc.

![Partage Tunnel vpn 5.](../media/vpn-split-tunneling/vpn-model-5.png)

## <a name="implement-vpn-split-tunneling"></a>Implémenter un tunnel partagé VPN

Dans cette section, vous trouverez les étapes simples nécessaires pour migrer votre architecture cliente VPN d’un _tunnel imposé VPN_ vers un _tunnel imposé VPN à quelques exceptions_ près, le modèle de [tunnel partagé VPN n°2](#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) dans les [scénarios VPN courants](#common-vpn-scenarios).

Le diagramme ci-dessous montre comment fonctionne la solution tunnel partagé VPN recommandée :

![Détails de la solution VPN de tunnel partagé.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identifier les points de terminaison à optimiser

Dans [l’article Microsoft 365 url et plages d’adresses IP](urls-and-ip-address-ranges.md), Microsoft identifie clairement les points de terminaison clés dont vous avez besoin pour optimiser et les classe en tant qu’Optimiser. Il n’existe actuellement que quatre URL et 20 sous-réseaux IP qui doivent être optimisés. Ce petit groupe de points de terminaison représente environ 70 % à 80 % du volume du trafic vers le service Microsoft 365, y compris les points de terminaison sensibles à la latence tels que ceux pour Teams multimédia. Il s’agit essentiellement du trafic que nous devons prendre en charge de manière particulière et c’est également le trafic qui placera une pression incroyable sur les chemins d’accès réseau traditionnels et l’infrastructure VPN.

Les URL dans cette catégorie présentent les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Sont-ils sensibles au bande passante et/ou à la latence
- Sont-ils en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représente environ 70 à 80 % du volume du trafic vers Microsoft 365 service

Pour plus d’informations sur Microsoft 365 de terminaison et sur leur classement et leur gestion, voir [Managing Microsoft 365 endpoints](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optimiser les URL

Les URL optimisées actuelles sont accessibles dans le tableau ci-dessous. Dans la plupart des cas, vous devez uniquement utiliser les points de terminaison d’URL dans un [fichier PAC de navigateur](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) où les points de terminaison sont configurés pour être envoyés directement, plutôt que vers le proxy.

| Optimiser les URL | Port/Protocol | Objectif |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Il s’agit de l’une des principales URL qu’Outlook utilise pour se connecter à son serveur Exchange Online et qui présente un volume élevé d’utilisation de la bande passante et de nombre de connexions. Une latence de réseau faible est requise pour les fonctionnalités en ligne telles que la recherche instantanée, les autres calendriers de boîte aux lettres, la recherche de disponibilités, la gestion des règles et alertes, l’archivage Exchange Online, les courriers électroniques faisant partie de la boîte d’envoi. |
| <https://outlook.office.com> | TCP 443 | Cette URL est utilisée par Outlook Online Web Access pour se connecter au serveur Exchange Online, et est sensible à la latence du réseau. La connectivité est particulièrement nécessaire pour le chargement et le téléchargement de fichiers volumineux avec SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Il s’agit de l’URL principale de SharePoint Online avec une utilisation à bande passante élevée. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Il s’agit de l’URL principale de OneDrive Entreprise et de l’utilisation de la bande passante élevée et éventuellement d’un nombre élevé de connexions à partir de l’outil de synchronisation OneDrive Entreprise. |
| Adresses IP des médias Teams (aucune URL) | UDP 3478, 3479, 3480, et 3481 | Allocation de découverte de relais et trafic en temps réel (3478), audio (3479), vidéo (3480) et partage d’écran vidéo (3481). Voici les points de terminaison utilisés pour Skype Entreprise et Microsoft Teams trafic multimédia (appels, réunions, etc.). La plupart des points de terminaison sont fournis lorsque le client Microsoft Teams établit un appel (et est inclus dans les adresses IP requises répertoriées pour le service). L’utilisation du protocole UDP est nécessaire pour optimiser la qualité des médias.   |

Dans les exemples ci-dessus, **le** client doit être remplacé par votre Microsoft 365 client. Par exemple, **contoso.onmicrosoft.com** _utiliserait_ contoso.sharepoint.com et _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optimiser les plages d’adresses IP

Au moment d’écrire les plages d’adresses IP correspondant à ces points de terminaison sont les suivantes. Il est vivement recommandé d’utiliser un [script](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) tel que cet exemple, le [service web MICROSOFT 365 IP et URL](microsoft-365-ip-web-service.md) ou la [page URL/IP](urls-and-ip-address-ranges.md) pour vérifier les mises à jour lors de l’application de la configuration et mettre en place une stratégie pour le faire régulièrement.

```
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. Optimiser l’accès à ces points de terminaison via le VPN

Maintenant que nous avons identifié ces points de terminaison critiques, nous devons les détourner du tunnel VPN et leur permettre d’utiliser la connexion Internet locale de l’utilisateur pour se connecter directement au service. La façon dont cette opération peut être effectuée varie en fonction du produit VPN et de la plateforme de l’ordinateur utilisés, mais la plupart des solutions VPN autorisent une configuration simple de la stratégie pour appliquer cette logique. Pour plus d’informations sur les recommandations de tunnels partagés spécifiques à la plateforme VPN, consultez [Comment utiliser les guides d’utilisation pour les plateformes VPN courantes](#howto-guides-for-common-vpn-platforms).

Si vous souhaitez tester la solution manuellement, vous pouvez exécuter l’exemple PowerShell suivant pour émuler la solution au niveau de la table d’itinéraires. Cet exemple ajoute un itinéraire pour chacun des sous-réseaux IP de média Teams dans la table des itinéraires. Vous pouvez tester les performances des médias Teams avant et après, et observer la différence dans les itinéraires pour les points de terminaison spécifiés.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>Exemple : ajouter des sous-réseaux IP de média Teams dans la table des itinéraires

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Dans le script ci-dessus, _$intIndex_ est l’index de l’interface connectée à Internet (trouver en exécutant **get-netadapter** dans PowerShell ; recherchez la valeur de _ifIndex_) et _$gateway_ est la passerelle par défaut de cette interface (trouver en exécutant **ipconfig** dans une invite de commandes ou **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop** dans PowerShell).

Une fois que vous avez ajouté les itinéraires, vous pouvez vérifier que la table d’itinéraires est correcte en exécutant **impression d'itinéraire** dans une invite de commandes ou dans PowerShell. La sortie doit contenir les itinéraires que vous avez ajoutés, affichant l’index d’interface (_22_ dans cet exemple) et la passerelle pour cette interface (_192.168.1.1_ dans cet exemple) :

![Router la sortie d’impression.](../media/vpn-split-tunneling/vpn-route-print.png)

Pour ajouter des itinéraires pour toutes les plages d’adresses IP actuelles dans la catégorie Optimiser, vous pouvez utiliser la variante de script suivante pour interroger le [service web d’URL et d’ADRESSE IP Microsoft 365](microsoft-365-ip-web-service.md) pour l’ensemble actuel de sous-réseaux IP Optimiser et les ajouter à la table d’itinéraires.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>Exemple : ajouter des sous-réseaux Optimiser dans la table des itinéraires

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

Si vous avez ajouté par inadvertance des itinéraires avec des paramètres incorrects ou si vous souhaitez simplement annuler vos modifications, vous pouvez supprimer les itinéraires que vous venez d'ajouter avec la commande suivante :

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

Le client VPN doit être configuré de sorte que le trafic vers le **Optimiser** IPs soient acheminés de cette façon. Cela permet au trafic d’utiliser les ressources Microsoft locales telles que les portails frontaux du service Microsoft 365, telles que [azure front door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/), qui offrent des services Microsoft 365 et des points de terminaison de connectivité aussi proches que possible de vos utilisateurs. Cela nous permet de fournir des niveaux de performances élevés aux utilisateurs où [qu’ils](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) soient dans le monde et de tirer pleinement parti du réseau mondial de Microsoft, qui se trouve probablement à quelques millisecondes de la sortie directe de vos utilisateurs.

## <a name="configuring-and-securing-teams-media-traffic"></a>Configuration et sécurisation du trafic multimédia Teams

Certains administrateurs peuvent avoir besoin d'informations plus détaillées sur le fonctionnement des flux d'appels dans Teams à l'aide d'un modèle de tunnel partagé et sur la manière dont les connexions sont sécurisées.

### <a name="configuration"></a>Configuration

Pour les appels et les réunions, tant que les sous-réseaux IP Optimiser pour les médias Teams sont correctement en place dans la table d’itinéraires, lorsque Teams appelle la fonction [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) pour déterminer l’interface locale qui correspond à l’itinéraire qu’il doit utiliser pour une destination particulière, l’interface locale est renvoyée pour les destinations Microsoft dans les blocs IP Microsoft répertoriés ci-dessus.

Certains logiciels clients VPN autorisent la manipulation des itinéraires sur la base de l’URL. Cependant, le trafic médiatique de Teams n'est pas associé à une URL, le contrôle du routage de ce trafic doit donc être effectué à l'aide de sous-réseaux IP.

Dans certains scénarios, souvent non liés à la configuration du client Teams, le trafic multimédia traverse également le tunnel VPN, même lorsque les itinéraires corrects sont en place. Si vous rencontrez ce scénario, l’utilisation d’une règle de pare-feu pour empêcher les sous-réseaux IP Teams ou les ports d’utiliser le VPN devrait suffire.

>[!IMPORTANT]
>Pour vous assurer que Teams trafic multimédia est acheminé via la méthode souhaitée dans tous les scénarios VPN, assurez-vous que les utilisateurs exécutent Microsoft Teams client version **1.3.00.13565** ou supérieure. Cette version inclut des améliorations dans la façon dont le client détecte les chemins d’accès réseau disponibles.

Le trafic de signalisation est effectué sur HTTPS et n’est pas aussi sensible à la latence que le trafic multimédia et  est marqué comme Autoriser dans les données URL/IP et peut donc être acheminé en toute sécurité via le client VPN si vous le souhaitez.

>[!NOTE]
>Microsoft Edge **96 et** supérieures prend également en charge la tunneling fractionnée VPN pour le trafic pair à pair. Cela signifie que les clients peuvent tirer parti de la tunneling fractionnement VPN pour Teams clients web sur Edge, par exemple. Les clients qui souhaitent la configurer pour les sites web qui s’exécutent sur Edge peuvent y parvenir en prenant l’étape supplémentaire d’activation de la stratégie [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Sécurité

L’un des arguments courants pour éviter les tunnelages fractionnements est le fait qu’il est moins sécurisé de le faire, c’est-à-dire Tout trafic qui ne passe pas par le tunnel VPN ne bénéficiera d’aucun schéma de chiffrement appliqué au tunnel VPN et sera donc moins sécurisé.

L’argument de compteur principal permet de faire en sorte que le trafic multimédia soit déjà chiffré via _SRTP (Protocole de transport sécurisé en temps réel)_, un profil de protocole RTP (Protocole de transport en temps réel) qui assure la confidentialité, l’authentification et la protection contre les attaques contre le trafic RTP. SRTP lui-même utilise une clé de session générée de façon aléatoire, qui est échangée via le canal de signalement sécurisé TLS. Celui-ci sont décrites en détail dans [Ce guide de sécurité](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), mais la section principale est consacrée au chiffrement de médias.

Le trafic multimédia est chiffré à l’aide de SRTP, qui utilise une clé de session générée par un générateur de nombres aléatoires sécurisés et échangées à l’aide du canal TLS de signalisation. De plus, le flux de contenu entrant dans les deux directions entre le serveur de médiation et son saut interne suivant est également chiffré à l’aide de SRTP.

Skype Entreprise Online génère les noms d’utilisateur et les mots de passe pour sécuriser l’accès aux relais de contenu par le biais de _Traverser à l’aide de relais autour de NAT (TURN)_. Les relais de média échangent le nom d’utilisateur/mot de passe sur un canal SIP sécurisé par TLS. Il est important de noter que même si un tunnel VPN peut être utilisé pour connecter le client au réseau d’entreprise, le trafic doit toujours circuler sous sa forme SRTP lorsqu’il quitte le réseau d’entreprise pour atteindre le service.

Des informations sur la façon dont Teams atténue les problèmes de sécurité courants tels que les utilitaires de voix ou de traversée de session pour les attaques d’amplification _NAT (STUN)_ sont disponibles dans [5.1 Security Considerations for Implementers](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Vous pouvez également consulter des informations sur les contrôles de sécurité modernes dans les scénarios de travail à distance sur [Autres méthodes pour les professionnels de la sécurité et l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui (blog de l’équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Tests

Une fois la stratégie en place, vous devez vérifier qu’elle fonctionne comme prévu. Plusieurs méthodes s’offrent à vous pour tester que le chemin d’accès est correctement configuré pour utiliser la connexion Internet locale :

- Exécutez le [test Microsoft 365 de](https://aka.ms/netonboard) connectivité qui exécutera pour vous des tests de connectivité, y compris des itinéraires de suivi comme ci-dessus. Nous ajoutons également dans cet outil des tests VPN qui doivent également fournir des informations supplémentaires.

- Un simple **tracert vers un** point de terminaison dans l’étendue du tunnel partagé doit afficher le chemin d’accès pris, par exemple :

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Vous devriez ensuite voir un chemin d’accès via le isp local à ce point de terminaison qui doit résoudre une adresse IP dans les plages de Teams que nous avons configurées pour la tunnellation fractionner.

- Prenez une capture réseau à l’aide d’un outil tel que Wireshark. Filtrez sur le protocole UDP pendant un appel et le trafic s'acheminera vers une adresse IP dans la plage **Optimiser** Teams. Si le tunnel VPN est utilisé pour ce trafic, le trafic multimédia n’est pas visible dans le suivi.

### <a name="additional-support-logs"></a>Journaux de support supplémentaires

Si vous avez besoin de données supplémentaires pour résoudre les problèmes, ou si vous demandez l’aide du support technique Microsoft, vous pouvez obtenir les informations suivantes afin de vous permettre d’accélérer la recherche d’une solution. Le jeu d’outils **TSS Windows script** de dépannage universel basé sur CMD du support Microsoft peut vous aider à collecter les journaux pertinents de manière simple. L’outil et les instructions d’utilisation sont à l’aide <https://aka.ms/TssTools>de .

## <a name="how-to-optimize-stream--live-events"></a>Comment optimiser les événements en & stream

le trafic des événements en direct Microsoft 365 (cela inclut les participants aux événements en direct produits par Teams et ceux produits avec un encodeur externe via Teams, Stream ou Yammer) et le trafic de flux à la demande est actuellement classé comme trafic par défaut ou Optimiser dans la  liste [URL/IP du service](urls-and-ip-address-ranges.md). Ces points de terminaison sont classés  par défaut, car ils sont hébergés sur des CDN qui peuvent également être utilisés par d’autres services. Les clients préfèrent généralement proxyer ce type de trafic et appliquer tous les éléments de sécurité normalement effectués sur des points de terminaison tels que ceux-ci.

De nombreux clients ont demandé des données URL/IP nécessaires pour connecter leurs utilisateurs aux événements Stream/Live directement à partir de leur connexion Internet locale, plutôt que d’router le trafic à volume élevé et sensible à la latence via l’infrastructure VPN. En règle générale, cela n’est pas possible sans des espaces de noms dédiés et des informations IP précises pour les points de terminaison, qui ne sont pas fournis pour les points de terminaison Microsoft 365 classés par **défaut.**

Utilisez les étapes suivantes pour activer la connectivité directe pour le service Stream/Live Events à partir des clients à l’aide d’un VPN de tunnel forcé. Cette solution est destinée à offrir aux clients une option pour éviter le routage du trafic d’événements en direct sur VPN alors qu’il y a un trafic réseau élevé en raison de scénarios de travail à domicile. Si possible, il est conseillé d’accéder au service via un proxy d’inspection.

>[!NOTE]
>À l’aide de cette solution, il peut y avoir des éléments de service qui ne sont pas résolus en adresses IP fournies et par conséquent traversent le VPN, mais l’essentiel du trafic à volume élevé comme les données de diffusion en continu doit le faire. Il peut y avoir d’autres éléments en dehors de l’étendue des événements en direct/flux qui sont capturés par ce déchargement, mais ceux-ci doivent  être limités car ils doivent répondre à la fois au nom de domaine complet et à la correspondance IP avant de passer directement.

>[!IMPORTANT]
>Les clients sont invités à évaluer le risque d’envoyer davantage de trafic qui contourne le VPN par rapport au gain de performances pour les événements en direct.

Pour implémenter l’exception de tunnel forcé Teams live events et Stream, les étapes suivantes doivent être appliquées :

### <a name="1-configure-external-dns-resolution"></a>1. Configurer la résolution DNS externe

Les clients ont besoin d’une résolution DNS externe récursive pour être disponibles afin que les noms d’hôte suivants soient résolus en adresses IP.

- \*.azureedge.net
- \*.media.azure.net
- \*.bmc.cdn.office.net

**\*.azureedge.net** est utilisé pour les événements Stream (Configurer des encodeurs pour la diffusion en continu en direct dans [Microsoft Stream - Microsoft Stream | Microsoft Docs](/stream/live-encoder-setup)).

**\*.media.azure.net** **\*et .bmc.cdn.office.net** sont utilisés pour les événements en direct produits par Teams (événements de démarrage rapide, événements pris en charge par RTMP-In [ID de feuille de route 84960]) programmés à partir du client Teams.

 Certains de ces points de terminaison sont partagés avec d’autres éléments en dehors des événements Stream/Live, il n’est pas conseillé d’utiliser simplement ces FQDN pour configurer le déchargement VPN, même si techniquement possible dans votre solution VPN (par exemple, si elle fonctionne sur le nom deqdn plutôt que sur IP).

Les FQDN ne sont pas requis dans la configuration VPN, ils sont purement à utiliser dans les fichiers PAC en combinaison avec les adresses IP pour envoyer le trafic direct approprié.

### <a name="2-implement-pac-file-changes-where-required"></a>2. Implémenter les modifications de fichier PAC (le cas échéant)

Pour les organisations qui utilisent un fichier PAC pour router le trafic via un proxy sur VPN, cette action est normalement obtenue à l’aide de FQDN. Toutefois, avec les événements Stream/Live, les noms d’hôte fournis contiennent des caractères génériques **\*tels que .azureedge.net**, qui englobent également d’autres éléments pour lesquels il n’est pas possible de fournir des listes IP complètes. Par conséquent, si la demande est envoyée directement en fonction de la correspondance de caractère générique DNS seule, le trafic vers ces points de terminaison sera bloqué car il n’existe aucun itinéraire via le chemin d’accès direct pour celui-ci à l’étape [3](#3-configure-routing-on-the-vpn-to-enable-direct-egress).

Pour résoudre ce problème, nous pouvons fournir les IP suivantes et les utiliser en combinaison avec les noms d’hôtes de l’étape [1](#1-configure-external-dns-resolution) dans un exemple de fichier PAC. Le fichier PAC vérifie si l’URL correspond à celles utilisées pour les événements Stream/Live, puis, si c’est le cas, il vérifie également si l’ADRESSE IP renvoyée par une recherche DNS correspond à celles fournies pour le service. Si _les deux_ correspondent, le trafic est acheminé directement. Si l’un des deux éléments (FQDN/IP) ne correspond pas, le trafic est envoyé au proxy. Par conséquent, la configuration garantit que tout ce qui est résolu en adresse IP en dehors de l’étendue des espaces de noms IP et définis traverse normalement le proxy via le VPN.

#### <a name="gathering-the-current-lists-of-cdn-endpoints"></a>Collecte des listes actuelles de points CDN de terminaison

Les événements en direct utilisent plusieurs CDN pour diffuser des données aux clients, afin de fournir la meilleure couverture, la meilleure qualité et la meilleure résilience. Actuellement, les Azure CDN microsoft et Verizon sont utilisés. Au fil du temps, cela peut être modifié en raison de situations telles que la disponibilité régionale. Cet article est une source qui vous permet de rester à jour sur les plages IP.

Pour Azure CDN à partir de Microsoft, vous pouvez télécharger la liste à partir de Télécharger les [plages IP azure et les balises de service – Cloud public](https://www.microsoft.com/download/details.aspx?id=56519) à partir du Centre de téléchargement Microsoft officiel - vous devez rechercher spécifiquement la balise de service *AzureFrontdoor.Frontend* dans le JSON ; *addressPrefixes* affiche les sous-réseaux IPv4/IPv6. Au fil du temps, les IP peuvent changer, mais la liste des balises de service est toujours mise à jour avant leur utilisation.

For Azure CDN from Verizon (Edgecast) you can find an exhaustive list using [https://docs.microsoft.com/rest/api/cdn/edge-nodes/list](/rest/api/cdn/edge-nodes/list) (click **Try It** ) - you will need to look specifically for the **Premium\_ Verizon** section. Notez que cette API affiche toutes les IP edgecast (origine et anycast). Il n’existe actuellement aucun mécanisme permettant à l’API de faire la distinction entre l’origine et Anycast.

Pour l’implémenter dans un fichier PAC, vous pouvez utiliser l’exemple suivant qui envoie le trafic Microsoft 365 Optimiser le trafic direct (ce qui est recommandé) via le FQDN et le trafic stream/live events direct critique via une combinaison du FQDN et de l’adresse IP renvoyée. Le nom de l’espace réservé _Contoso_ doit être modifié pour le nom de votre client spécifique où _contoso_ est issu contoso.onmicrosoft.com

##### <a name="example-pac-file"></a>Exemple de fichier PAC

Voici un exemple de la façon de générer les fichiers PAC :

1. Enregistrez le script ci-dessous sur votre disque dur local _sousGet-TLEPacFile.ps1_.
1. Go to the [Verizon URL](/rest/api/cdn/edge-nodes/list#code-try-0) and download the resulting JSON (copy paste it into a file like cdnedgenodes.json)
1. Placez le fichier dans le même dossier que le script.
1. Dans une fenêtre PowerShell, exécutez la commande suivante. Modifiez le nom du client pour autre chose si vous souhaitez les URL SPO. Il s’agit du type 2, donc **Optimiser** et **autoriser** (le type 1 est Optimiser uniquement).

   ```powershell
   .\Get-TLEPacFile.ps1 -Instance Worldwide -Type 2 -TenantName <contoso> -CdnEdgeNodesFilePath .\cdnedgenodes.json -FilePath TLE.pac
   ```

5. Le fichier TLE.pac contient tous les espaces de noms et les IPS (IPv4/IPv6).

###### <a name="get-tlepacfileps1"></a>Get-TLEPacFile.ps1

```powershell
# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

<#PSScriptInfo

.VERSION 1.0.4

.AUTHOR Microsoft Corporation

.GUID 7f692977-e76c-4582-97d5-9989850a2529

.COMPANYNAME Microsoft

.COPYRIGHT
Copyright (c) Microsoft Corporation. All rights reserved.
Licensed under the MIT License.

.TAGS PAC Microsoft Microsoft365 365

.LICENSEURI

.PROJECTURI http://aka.ms/ipurlws

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

#>

<#

.SYNOPSIS

Create a PAC file for Microsoft 365 prioritized connectivity

.DESCRIPTION

This script will access updated information to create a PAC file to prioritize Microsoft 365 Urls for
better access to the service. This script will allow you to create different types of files depending
on how traffic needs to be prioritized.

.PARAMETER Instance

The service instance inside Microsoft 365.

.PARAMETER ClientRequestId

The client request id to connect to the web service to query up to date Urls.

.PARAMETER DirectProxySettings

The direct proxy settings for priority traffic.

.PARAMETER DefaultProxySettings

The default proxy settings for non priority traffic.

.PARAMETER Type

The type of prioritization to give. Valid values are 1 and 2, which are 2 different modes of operation.
Type 1 will send Optimize traffic to the direct route. Type 2 will send Optimize and Allow traffic to
the direct route.

.PARAMETER Lowercase

Flag this to include lowercase transformation into the PAC file for the host name matching.

.PARAMETER TenantName

The tenant name to replace wildcard Urls in the webservice.

.PARAMETER ServiceAreas

The service areas to filter endpoints by in the webservice.

.PARAMETER FilePath

The file to print the content to.

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type1.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance China -Type 2 -DefaultProxySettings "PROXY 4.4.4.4:70" -FilePath type2.pac

.EXAMPLE

Get-TLEPacFile.ps1 -ClientRequestId b10c5ed1-bad1-445f-b386-b919946339a7 -Instance WorldWide -Lowercase -TenantName tenantName -ServiceAreas Sharepoint

#>

#Requires -Version 2

[CmdletBinding(SupportsShouldProcess=$True)]
Param (
    [Parameter(Mandatory = $false)]
    [ValidateSet('Worldwide', 'Germany', 'China', 'USGovDoD', 'USGovGCCHigh')]
    [String] $Instance = "Worldwide",

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [guid] $ClientRequestId = [Guid]::NewGuid().Guid,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DirectProxySettings = 'DIRECT',

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [String] $DefaultProxySettings = 'PROXY 10.10.10.10:8080',

    [Parameter(Mandatory = $false)]
    [ValidateRange(1, 2)]
    [int] $Type = 1,

    [Parameter(Mandatory = $false)]
    [switch] $Lowercase = $false,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $TenantName,

    [Parameter(Mandatory = $false)]
    [ValidateSet('Exchange', 'SharePoint', 'Common', 'Skype')]
    [string[]] $ServiceAreas,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $FilePath,

    [Parameter(Mandatory = $false)]
    [ValidateNotNullOrEmpty()]
    [string] $CdnEdgeNodesFilePath
)

##################################################################################################################
### Global constants
##################################################################################################################

$baseServiceUrl = "https://endpoints.office.com/endpoints/$Instance/?ClientRequestId={$ClientRequestId}"
$directProxyVarName = "direct"
$defaultProxyVarName = "proxyServer"
$bl = "`r`n"

##################################################################################################################
### Functions to create PAC files
##################################################################################################################

function Get-PacClauses
{
    param(
        [Parameter(Mandatory = $false)]
        [string[]] $Urls,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $ReturnVarName
    )

    if (!$Urls)
    {
        return ""
    }

    $clauses =  (($Urls | ForEach-Object { "shExpMatch(host, `"$_`")" }) -Join "$bl        || ")

@"
    if($clauses)
    {
        return $ReturnVarName;
    }
"@
}

function Get-PacString
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [array[]] $MapVarUrls
    )

@"
// This PAC file will provide proxy config to Microsoft 365 services
//  using data from the public web service for all endpoints
function FindProxyForURL(url, host)
{
    var $directProxyVarName = "$DirectProxySettings";
    var $defaultProxyVarName = "$DefaultProxySettings";

$( if ($Lowercase) { "    host = host.toLowerCase();" })

$( ($MapVarUrls | ForEach-Object { Get-PACClauses -ReturnVarName $_.Item1 -Urls $_.Item2 }) -Join "$bl$bl" )

$( if (!$ServiceAreas -or $ServiceAreas.Contains('Skype')) { Get-TLEPacConfiguration })

    return $defaultProxyVarName;
}
"@ -replace "($bl){3,}","$bl$bl" # Collapse more than one blank line in the PAC file so it looks better.
}

##################################################################################################################
### Functions to get and filter endpoints
##################################################################################################################

function Get-TLEPacConfiguration {
    param ()
    $PreBlock = @"
    // Don't Proxy Teams Live Events traffic

    if(shExpMatch(host, "*.azureedge.net")
    || shExpMatch(host, "*.bmc.cdn.office.net")
    || shExpMatch(host, "*.media.azure.net"))
    {
        var resolved_ip = dnsResolveEx(host);

"@
    $TLESb = New-Object 'System.Text.StringBuilder'
    $TLESb.Append($PreBlock) | Out-Null

    if (![string]::IsNullOrEmpty($CdnEdgeNodesFilePath) -and (Test-Path -Path $CdnEdgeNodesFilePath)) {
        $CdnData = Get-Content -Path $CdnEdgeNodesFilePath -Raw -ErrorAction SilentlyContinue | ConvertFrom-Json | Select-Object -ExpandProperty value | 
            Where-Object { $_.name -eq 'Premium_Verizon'} | Select-Object -First 1 -ExpandProperty properties | 
            Select-Object -ExpandProperty ipAddressGroups
        $CdnData | Select-Object -ExpandProperty ipv4Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
        $CdnData | Select-Object -ExpandProperty ipv6Addresses | ForEach-Object {
            if ($TLESb.Length -eq $PreBlock.Length) {
                $TLESb.Append("        if(") | Out-Null
            }
            else {
                $TLESb.AppendLine() | Out-Null
                $TLESb.Append("        || ") | Out-Null
            }
            $TLESb.Append("isInNetEx(resolved_ip, `"$($_.BaseIpAddress)/$($_.prefixLength)`")") | Out-Null
        }
    }
    $AzureIPsUrl = Invoke-WebRequest -Uri "https://www.microsoft.com/en-us/download/confirmation.aspx?id=56519" -UseBasicParsing -ErrorAction SilentlyContinue  | 
            Select-Object -ExpandProperty Links | Select-Object -ExpandProperty href | 
            Where-Object { $_.EndsWith('.json') -and $_ -match 'ServiceTags' } | Select-Object -First 1
    if ($AzureIPsUrl) {
        Invoke-RestMethod -Uri $AzureIPsUrl -ErrorAction SilentlyContinue | Select-Object -ExpandProperty values | 
            Where-Object { $_.name -eq 'AzureFrontDoor.Frontend' } | Select-Object -First 1 -ExpandProperty properties |
            Select-Object -ExpandProperty addressPrefixes | ForEach-Object {
                if ($TLESb.Length -eq $PreBlock.Length) {
                    $TLESb.Append("        if(") | Out-Null
                }
                else {
                    $TLESb.AppendLine() | Out-Null
                    $TLESb.Append("        || ") | Out-Null
                }
                $TLESb.Append("isInNetEx(resolved_ip, `"$_`")") | Out-Null
            }
    }
    if ($TLESb.Length -gt $PreBlock.Length) {
        $TLESb.AppendLine(")") | Out-Null
        $TLESb.AppendLine("        {") | Out-Null
        $TLESb.AppendLine("            return $directProxyVarName;") | Out-Null
        $TLESb.AppendLine("        }") | Out-Null
    }
    else {
        $TLESb.AppendLine("        // no addresses found for service via script") | Out-Null
    }
    $TLESb.AppendLine("    }") | Out-Null
    return $TLESb.ToString()
}

function Get-Regex
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $Fqdn
    )

    return "^" + $Fqdn.Replace(".", "\.").Replace("*", ".*").Replace("?", ".?") + "$"
}

function Match-RegexList
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $ToMatch,

        [Parameter(Mandatory = $false)]
        [string[]] $MatchList
    )

    if (!$MatchList)
    {
        return $false
    }
    foreach ($regex in $MatchList)
    {
        if ($regex -ne $ToMatch -and $ToMatch -match (Get-Regex $regex))
        {
            return $true
        }
    }
    return $false
}

function Get-Endpoints
{
    $url = $baseServiceUrl
    if ($TenantName)
    {
        $url += "&TenantName=$TenantName"
    }
    if ($ServiceAreas)
    {
        $url += "&ServiceAreas=" + ($ServiceAreas -Join ",")
    }
    return Invoke-RestMethod -Uri $url
}

function Get-Urls
{
    param(
        [Parameter(Mandatory = $false)]
        [psobject[]] $Endpoints
    )

    if ($Endpoints)
    {
        return $Endpoints | Where-Object { $_.urls } | ForEach-Object { $_.urls } | Sort-Object -Unique
    }
    return @()
}

function Get-UrlVarTuple
{
    param(
        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [string] $VarName,

        [Parameter(Mandatory = $false)]
        [string[]] $Urls
    )
    return New-Object 'Tuple[string,string[]]'($VarName, $Urls)
}

function Get-MapVarUrls
{
    Write-Verbose "Retrieving all endpoints for instance $Instance from web service."
    $Endpoints = Get-Endpoints

    if ($Type -eq 1)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -eq "Optimize" })
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -ne "Optimize" }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
    elseif ($Type -eq 2)
    {
        $directUrls = Get-Urls ($Endpoints | Where-Object { $_.category -in @("Optimize", "Allow")})
        $nonDirectPriorityUrls = Get-Urls ($Endpoints | Where-Object { $_.category -notin @("Optimize", "Allow") }) | Where-Object { Match-RegexList $_ $directUrls }
        return @(
            Get-UrlVarTuple -VarName $defaultProxyVarName -Urls $nonDirectPriorityUrls
            Get-UrlVarTuple -VarName $directProxyVarName -Urls $directUrls
        )
    }
}

##################################################################################################################
### Main script
##################################################################################################################

$content = Get-PacString (Get-MapVarUrls)

if ($FilePath)
{
    $content | Out-File -FilePath $FilePath -Encoding ascii
}
else
{
    $content
}
```

Le script va automatiquement passer la liste Azure en fonction de [l’URL](https://www.microsoft.com/download/details.aspx?id=56519) de téléchargement et des clés **d’AzureFrontDoor.Frontend**, il n’est donc pas nécessaire de l’obtenir manuellement.

Là encore, il n’est pas conseillé d’effectuer un déchargement VPN à l’aide uniquement des FQDN . l’utilisation des noms de domaine complets et des adresses IP dans la fonction permet d’limiter l’utilisation de ce déchargement à un ensemble limité de points de terminaison, y compris les événements en direct/flux. La façon dont la fonction est structurée entraîne la recherche DNS pour le nom de domaine complet qui correspond directement à ceux répertoriés par le client, c’est-à-dire que la résolution DNS des espaces de noms restants reste inchangée.

Si vous souhaitez limiter le risque de déchargement des points de terminaison non liés aux événements en direct et au flux, **\*** vous pouvez supprimer le domaine .azureedge.net de la configuration, qui est l’endroit où réside la plupart de ce risque, car il s’agit d’un domaine partagé utilisé pour tous les clients Azure CDN. L’inconvénient est que tout événement utilisant un encodeur externe n’est pas optimisé, mais que les événements produits/organisés au sein Teams seront.

### <a name="3-configure-routing-on-the-vpn-to-enable-direct-egress"></a>3. Configurer le routage sur le VPN pour activer la sortie directe

La dernière étape consiste à ajouter un itinéraire direct pour les IP d’événements en direct décrits dans la collecte des **listes** actuelles de points de terminaison CDN dans la configuration VPN pour vous assurer que le trafic n’est pas envoyé via le tunnel forcé dans le VPN. Des informations détaillées sur la façon de le faire pour Microsoft 365 Optimiser les points de terminaison se trouvent dans la section Implémenter la [tunnellisation](#implement-vpn-split-tunneling) fractionner VPN et le processus est exactement le même pour les IP stream/événements en direct répertoriés dans ce document.

Notez que [seules](#gathering-the-current-lists-of-cdn-endpoints) les IP (et non les FQDN) de collecte des listes actuelles de points de terminaison CDN doivent être utilisées pour la configuration VPN.

### <a name="stream--live-events-optimization-faq"></a>FAQ sur l& évérisation des événements en direct stream

#### <a name="will-this-send-all-my-traffic-to-the-service-direct"></a>Cela enverra-t-il tout mon trafic au service direct ?

Non, cela envoie directement le trafic de diffusion en continu sensible à la latence pour un événement en direct ou une vidéo de flux, tout autre trafic continuera à utiliser le tunnel VPN s’il n’est pas résolu en adresses IP publiées.

#### <a name="do-i-need-to-use-the-ipv6-addresses"></a>Dois-je utiliser les adresses IPv6 ?

Non, la connectivité ne peut être IPv4 que si nécessaire.

#### <a name="why-are-these-ips-not-published-in-the-microsoft-365-urlip-service"></a>Pourquoi ces adresses IP ne sont-elles pas publiées dans le service MICROSOFT 365 URL/IP ?

Microsoft dispose de contrôles stricts sur le format et le type d’informations qui se trouve dans le service pour s’assurer que les clients peuvent utiliser de manière fiable les informations pour implémenter un routage sécurisé et optimal en fonction de la catégorie de point de terminaison.

La  catégorie de point de terminaison par défaut ne dispose d’aucune information IP fournie pour de nombreuses raisons (les points de terminaison par défaut peuvent être en dehors du contrôle de Microsoft, peuvent changer trop fréquemment ou se retrouver dans des blocs partagés avec d’autres éléments). Pour cette raison, les points de terminaison par défaut sont conçus pour être envoyés via le FQDN à un proxy d’inspection, comme le trafic web normal.

Dans ce cas, les points de terminaison ci-dessus sont des CDN qui peuvent être utilisés par des éléments non Contrôlés par Microsoft autres que Des événements en direct ou Stream. Ainsi, l’envoi du trafic direct signifie également toute autre chose qui résout ces IP sera également envoyée directement à partir du client. En raison de la nature unique de la crise globale actuelle et pour répondre aux besoins à court terme de nos clients, Microsoft a fourni les informations ci-dessus que les clients peuvent utiliser comme bon leur semble.

Microsoft travaille à reconfigurer les points de terminaison Des événements en direct pour leur permettre d’être inclus dans les catégories de points de terminaison Autoriser/Optimiser à l’avenir.

#### <a name="do-i-only-need-to-allow-access-to-these-ips"></a>Dois-je uniquement autoriser l’accès à ces IP ?

Non, l’accès à tous  les points de terminaison marqués obligatoires dans le [service URL/IP](urls-and-ip-address-ranges.md) est essentiel au fonctionnement du service. En outre, tout point de terminaison facultatif marqué pour Stream (ID 41-45) est requis.

#### <a name="what-scenarios-will-this-advice-cover"></a>Quels scénarios seront couverts par ce conseil ?

1. Événements en direct produits dans l’application Teams
2. Affichage du contenu hébergé par Stream
3. Événements produits par l’appareil externe (encodeur)

#### <a name="does-this-advice-cover-presenter-traffic"></a>Ce conseil couvre-t-il le trafic du présentateur ?

Ce n’est pas le cas, les conseils ci-dessus sont purement pour les personnes qui consomment le service. Lors d’une présentation à partir d’Teams le trafic du présentateur s’affichera vers les points de terminaison UDP marqués Optimiser répertoriés à la ligne 11 de l’URL/service IP avec des conseils détaillés de déchargement VPN décrits dans la section Implémenter le [tunneling](#implement-vpn-split-tunneling) fractionné VPN.

#### <a name="does-this-configuration-risk-traffic-other-than-live-events-amp-stream-being-sent-direct"></a>Cette configuration risque-t-elle que le trafic autre que le flux d’événements &amp; en direct soit envoyé directement ?

Oui, en raison des FQDN partagés utilisés pour certains éléments du service, cela est inévitable. Ce trafic est normalement envoyé via un proxy d’entreprise qui peut appliquer l’inspection. Dans un scénario de tunnel partagé VPN, l’utilisation de FQDN et d’IPs limite ce risque au minimum, mais il existera toujours. Les clients peuvent supprimer le domaine .azureedge.net de la configuration de déchargement et réduire ce risque à un minimum, mais cela supprime le déchargement des événements en direct pris en charge par Stream (événements d’encodeur externes Teams programmés, événements Yammer produits dans Teams, événements d’encodeur externes Yammer programmés et événements stream programmés ou affichage à la demande à partir de Stream).**\*** Les événements programmés et produits dans Teams ne sont pas affectés.

## <a name="howto-guides-for-common-vpn-platforms"></a>Guides d’utilisation pour les plateformes VPN courantes

Cette section fournit des liens vers des guides détaillés pour implémenter la tunneling fractionnée pour Microsoft 365 trafic provenant des partenaires les plus courants dans cet espace. Nous ajouterons des guides à mesure qu’ils seront disponibles.

- **Windows 10 VPN :** optimisation du trafic Microsoft 365 pour les travailleurs à distance avec le [client VPN Windows 10 natif](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco AnyConnect**: [Optimiser le tunnel mixte AnyConnect pour Office 365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect :** [optimisation du trafic Microsoft 365 via vpn split Tunnel exclure l’itinéraire d’accès](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **Big-IP APM** des réseaux F5 : optimisation du trafic Microsoft 365 sur l’accès à distance via des VPN lors de l’utilisation de [BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Passerelle Citrix** : [optimisation du tunnel fractionné VPN de la passerelle Citrix pour Office 365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN Tunneling: How to configure split tunneling to exclude Microsoft 365 applications](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **VPN de point** de contrôle [: comment configurer split Tunnel pour Microsoft 365 applications SaaS et d’autres applications SaaS](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="vpn-split-tunneling-faq"></a>FAQ sur la tunnellation fractionnement VPN

L’équipe de sécurité Microsoft a publié d’autres méthodes pour les professionnels de la sécurité et les services [informatiques afin d’obtenir des contrôles](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/) de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui, un billet de blog qui décrit les principales façons pour les professionnels de la sécurité et les services informatiques d’obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui. De plus, vous trouverez ci-dessous quelques-unes des questions et réponses les plus fréquemment posées à ce sujet.

### <a name="how-do-i-stop-users-accessing-other-tenants-i-do-not-trust-where-they-could-exfiltrate-data"></a>Comment empêcher les utilisateurs d'accéder à d'autres locataires en qui je n'ai pas confiance et où ils pourraient exfiltrer des données ?

La réponse est une [fonctionnalité de appelée restrictions de locataire](/azure/active-directory/manage-apps/tenant-restrictions). Le trafic d’authentification n’est pas un volume élevé, ni particulièrement sensible à la latence. Par ailleurs, il peut être envoyé via la solution VPN au proxy local où la fonctionnalité est appliquée. Une liste d’autorisation des clients de confiance est conservée ici et si le client tente d’obtenir un jeton à un client qui n’est pas approuvé, le proxy refuse simplement la demande. Si le locataire est digne de confiance, un jeton est accessible si l'utilisateur a les informations d'identification et les droits appropriés.

Ainsi, même si un utilisateur peut établir une connexion TCP/UDP aux points de terminaison marqués Optimiser ci-dessus, sans jeton valide pour accéder au client en question, il ne peut simplement pas se connecter et accéder/déplacer des données.

### <a name="does-this-model-allow-access-to-consumer-services-such-as-personal-onedrive-accounts"></a>Ce modèle autorise-t-il l’accès aux services grand public tels que les comptes OneDrive personnels ?

Non, ce n’est pas le cas, les points de terminaison Microsoft 365 ne sont pas les mêmes que les services grand public (Onedrive.live.com par exemple), de sorte que le tunnel fractioné ne permet pas à un utilisateur d’accéder directement aux services grand public. Le trafic vers les points de terminaison consommateurs continuera à utiliser le tunnel VPN et les stratégies existantes continueront à s’appliquer.

### <a name="how-do-i-apply-dlp-and-protect-my-sensitive-data-when-the-traffic-no-longer-flows-through-my-on-premises-solution"></a>Comment appliquer le DLP et protéger mes données sensibles lorsque le trafic ne passe plus par ma solution locale ?

Pour éviter la divulgation accidentelle d’informations sensibles, Microsoft 365 dispose d’un ensemble riche [d’outils intégrés](../compliance/information-protection.md). Vous pouvez utiliser les [fonctionnalités DLP](../compliance/dlp-learn-about-dlp.md) intégrées de Teams et de SharePoint pour détecter des informations sensibles stockées ou partagées de manière inappropriée. Si une partie de votre stratégie de travail à distance implique une stratégie BYOD (Bring-your-own-device), vous pouvez utiliser [](/azure/active-directory/conditional-access/app-based-conditional-access) l’accès conditionnel basé sur l’application pour empêcher le téléchargement de données sensibles sur les appareils personnels des utilisateurs

### <a name="how-do-i-evaluate-and-maintain-control-of-the-users-authentication-when-they-are-connecting-directly"></a>Comment évaluer et maintenir le contrôle de l’authentification de l’utilisateur lorsqu’il se connecte directement ?

En plus de la fonctionnalité restrictions de locataire signalée au T1, les [stratégies d’accès conditionnel](/azure/active-directory/conditional-access/overview) peuvent être appliquées pour évaluer de façon dynamique le risque d’une demande d’authentification et réagir de façon appropriée. Microsoft recommande que le [](https://www.microsoft.com/security/zero-trust?rtc=1) modèle confiance zéro soit implémenté au fil du temps et nous pouvons utiliser des stratégies d’accès conditionnel Azure AD pour maintenir le contrôle dans un monde mobile et cloud. Les stratégies d'accès conditionnel peuvent être utilisées pour décider en temps réel si une demande d'authentification est acceptée ou non, en fonction de nombreux facteurs tels que :

- Appareil, l’appareil est-il connu/approuvé/lié au domaine ?
- IP : la demande d’authentification provient-elle d’une adresse IP d’entreprise connue ? Ou d’un pays dans lequel nous ne sommes pas dignes de confiance ?
- Application : l’utilisateur est-il autorisé à utiliser cette application ?

Nous pouvons ensuite déclencher une stratégie telle que approuver, déclencher l’authentification multifacteur ou bloquer l’authentification en fonction de ces stratégies.

### <a name="how-do-i-protect-against-viruses-and-malware"></a>Comment puis-je me protéger contre les virus et les programmes malveillants ?

Là encore, Microsoft 365 protection des points de terminaison marqués Optimiser dans différentes couches du service lui-même, [décrites dans ce document](/office365/Enterprise/office-365-malware-and-ransomware-protection). Comme indiqué, il est beaucoup plus efficace de fournir ces éléments de sécurité dans le service lui-même plutôt que d’essayer de le faire en ligne avec des appareils qui ne comprennent peut-être pas complètement les protocoles/trafic. Par défaut, SharePoint Online analyse automatiquement les [téléchargements](../security/office-365-security/virus-detection-in-spo.md) de fichiers pour les programmes malveillants connus

Pour les Exchange de terminaison répertoriés ci-dessus, [Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) et [Microsoft Defender pour Microsoft 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) assurent une excellente sécurité du trafic vers le service.

### <a name="can-i-send-more-than-just-the-optimize-traffic-direct"></a>Puis-je envoyer plus que le message direct Optimiser le trafic ?

Une priorité doit être accordée au points de terminaison marqués **Optimiser**, car ceux-ci vous permettront de bénéficier d’un niveau de travail optimal. Toutefois, si vous le souhaitez, les points de terminaison autoriser marqués sont requis pour que le service fonctionne et que des adresses IP soient fournies pour les points de terminaison qui peuvent être utilisés si nécessaire.

Plusieurs fournisseurs proposent également des solutions de proxy/sécurité basées sur le cloud, _appelées passerelles web sécurisées_ , qui fournissent une application centrale de sécurité, de contrôle et de stratégie d’entreprise pour la navigation web générale. Ces solutions peuvent fonctionner bien dans un monde cloud, si hautement disponible, performant et mis en service à proximité de vos utilisateurs en permettant à un accès Internet sécurisé d’être remis à partir d’un emplacement basé sur le cloud à proximité de l’utilisateur. Cela supprime la nécessité d’une épingle via le réseau VPN/d’entreprise pour le trafic de navigation général, tout en permettant le contrôle central de sécurité.

Même avec ces solutions en place toutefois, Microsoft recommande toujours vivement d’optimiser les Microsoft 365 trafic est envoyé directement au service.

Pour obtenir des instructions sur l’accès direct à un réseau virtuel Azure, voir Travail à distance à l’aide de la passerelle [VPN Azure point à site](/azure/vpn-gateway/work-remotely-support).

### <a name="why-is-port-80-required-is-traffic-sent-in-the-clear"></a>Pourquoi le port 80 est-il obligatoire ? Le trafic est-il envoyé en clair ?

Le port 80 est uniquement utilisé pour les opérations telles que la redirection vers une session de port 443, les données client ne sont pas envoyées ou sont accessibles via le port 80. [Le](../compliance/encryption.md) chiffrement décrit le chiffrement pour les données en transit et au repos pour Microsoft 365, et [Les types](/microsoftteams/microsoft-teams-online-call-flows#types-of-traffic) de trafic indiquent comment nous utilisons SRTP pour protéger Teams trafic multimédia.

### <a name="does-this-advice-apply-to-users-in-china-using-a-worldwide-instance-of-microsoft-365"></a>Ce conseil s’applique-t-il aux utilisateurs en Chine à l’aide d’une instance Microsoft 365 ?

**Pas de**, ce n’est pas le cas. La seule mise en garde aux conseils ci-dessus est que les utilisateurs de la RPC se connectent à une instance mondiale de Microsoft 365. En raison de l'encombrement fréquent des réseaux transfrontaliers dans la région, les performances de la sortie directe d'Internet peuvent être variables. La plupart des clients dans la région utilisent un réseau privé virtuel (VPN) pour transférer le trafic vers le réseau d’entreprise et utiliser leur circuit MPLS autorisé ou similaires à des sortir du pays via un chemin optimisé. Cela est décrit plus en détail dans l’article [Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

### <a name="does-split-tunnel-configuration-work-for-teams-running-in-a-browser"></a>La configuration en tunnel partagé fonctionne-t-elle pour Teams’exécution dans un navigateur ?

Oui, avec des avertissements. La Teams est prise en charge dans les navigateurs répertoriés dans [Obtenir des clients pour Microsoft Teams](/microsoftteams/get-clients#web-client).

En outre, Microsoft Edge **96** et supérieures prend en charge la tunneling fractionné VPN pour le trafic pair à pair en activant la stratégie [Edge WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled). Pour l’instant, d’autres navigateurs peuvent ne pas prendre en charge la tunneling fractionnée VPN pour le trafic pair à pair.

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunneling partagé VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)
