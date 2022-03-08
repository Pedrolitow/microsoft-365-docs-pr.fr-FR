---
title: Implémentation de la tunneling fractionnement VPN pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
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
ms.openlocfilehash: ee8c0929682370d581c9d1b5c738d682d3f91a01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320436"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>Implémentation de la tunneling fractionnement VPN pour Microsoft 365

>[!NOTE]
>Cet article fait partie d’un ensemble d’articles qui traitent Microsoft 365'optimisation des utilisateurs distants.

>- Pour une vue d’ensemble de l’utilisation de la tunneling fractionnement VPN pour optimiser la connectivité Microsoft 365 pour les utilisateurs distants, voir Vue d’ensemble : [tunneling fractionnel VPN pour Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Pour obtenir la liste détaillée des scénarios de tunneling fractionnement VPN, voir [Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Pour obtenir des instructions sur la sécurisation Teams trafic multimédia dans les environnements de tunnel partagé VPN, voir Sécurisation du trafic Teams multimédia [pour la tunnelisation fractionnée VPN](microsoft-365-vpn-securing-teams.md).
>- Pour plus d’informations sur la configuration de Stream et d’événements en direct dans les environnements VPN, voir Considérations spéciales pour Stream et les [événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md).
>- Pour plus d’informations sur l’optimisation Microsoft 365 performances des clients internationaux pour les utilisateurs en Chine, voir Microsoft 365 [optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md).

La stratégie recommandée par Microsoft pour optimiser la connectivité des travailleurs à distance est axée sur la réduction rapide des problèmes et la fourniture de performances élevées en quelques étapes simples. Ces étapes ajustent l’approche VPN héritée pour quelques points de terminaison définis qui contournent les serveurs VPN en goulot d’étranglement. Un modèle de sécurité équivalent, voire supérieur, peut être appliqué dans différentes couches pour supprimer la nécessité de sécuriser tout le trafic à la sortie du réseau d’entreprise. Dans la plupart des cas, cela peut être réalisé efficacement en quelques heures et est ensuite évolutif à d’autres charges de travail, selon la demande et le temps requis.

## <a name="implement-vpn-split-tunneling"></a>Implémenter un tunnel partagé VPN

Dans cet article, vous trouverez les étapes simples nécessaires pour migrer votre architecture de client VPN d’un _tunnel imposé VPN_ vers un tunnel imposé VPN à quelques _exceptions_ près, le modèle de [tunnel partagé VPN n°2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) dans les [scénarios de tunnel partagé VPN courants pour Microsoft 365](microsoft-365-vpn-common-scenarios.md).

Le diagramme ci-dessous montre comment fonctionne la solution tunnel partagé VPN recommandée :

![Détails de la solution VPN de tunnel partagé.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. Identifier les points de terminaison à optimiser

Dans [l’article Microsoft 365 url et plages d’adresses IP](urls-and-ip-address-ranges.md), Microsoft identifie clairement les points de terminaison clés dont vous avez besoin pour optimiser et les catégorise en tant **qu’Optimiser**. Il n’existe actuellement que quatre URL et 20 sous-réseaux IP qui doivent être optimisés. Ce petit groupe de points de terminaison représente environ 70 % à 80 % du volume du trafic vers le service Microsoft 365, y compris les points de terminaison sensibles à la latence, tels que ceux pour Teams multimédia. Il s’agit essentiellement du trafic que nous devons prendre en charge de manière particulière et c’est également le trafic qui placera une pression incroyable sur les chemins d’accès réseau traditionnels et l’infrastructure VPN.

Les URL dans cette catégorie présentent les caractéristiques suivantes :

- Les points de terminaison détenus et gérés par Microsoft sont-ils hébergés sur une infrastructure Microsoft
- Ont-ils des adresses IP fournies
- Faible taux de modifications et qui devraient rester de taille réduite (actuellement 20 sous-réseaux IP)
- Sont-ils sensibles au bande passante et/ou à la latence
- Sont-ils en mesure d'avoir les éléments de sécurité requis fournis dans le service plutôt qu'en ligne sur le réseau
- Représente environ 70 à 80 % du volume du trafic vers Microsoft 365 service

Pour plus d’informations Microsoft 365 les points de terminaison et la façon dont ils sont classés et [gérés, voir Managing Microsoft 365 endpoints](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>Optimiser les URL

Les URL optimisées actuelles sont accessibles dans le tableau ci-dessous. Dans la plupart des cas, vous devez uniquement utiliser les points de terminaison d’URL dans un [fichier PAC de navigateur](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) où les points de terminaison sont configurés pour être envoyés directement, plutôt que vers le proxy.

| Optimiser les URL | Port/Protocol | Objectif |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | Il s’agit de l’une des principales URL qu’Outlook utilise pour se connecter à son serveur Exchange Online et qui présente un volume élevé d’utilisation de la bande passante et de nombre de connexions. Une latence de réseau faible est requise pour les fonctionnalités en ligne telles que la recherche instantanée, les autres calendriers de boîte aux lettres, la recherche de disponibilités, la gestion des règles et alertes, l’archivage Exchange Online, les courriers électroniques faisant partie de la boîte d’envoi. |
| <https://outlook.office.com> | TCP 443 | Cette URL est utilisée par Outlook Online Web Access pour se connecter au serveur Exchange Online, et est sensible à la latence du réseau. La connectivité est particulièrement nécessaire pour le chargement et le téléchargement de fichiers volumineux avec SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | Il s’agit de l’URL principale de SharePoint Online avec une utilisation à bande passante élevée. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | Il s’agit de l’URL principale de OneDrive Entreprise et de l’utilisation de la bande passante élevée et éventuellement d’un nombre élevé de connexions à partir de l’outil de synchronisation OneDrive Entreprise. |
| Adresses IP des médias Teams (aucune URL) | UDP 3478, 3479, 3480, et 3481 | Allocation de découverte de relais et trafic en temps réel. Voici les points de terminaison utilisés pour Skype Entreprise et Microsoft Teams trafic multimédia (appels, réunions, etc.). La plupart des points de terminaison sont fournis lorsque le client Microsoft Teams établit un appel (et est inclus dans les adresses IP requises répertoriées pour le service). L’utilisation du protocole UDP est nécessaire pour optimiser la qualité des médias.   |

Dans les exemples ci-dessus, **le** client doit être remplacé par votre Microsoft 365 client. Par exemple, **contoso.onmicrosoft.com** _utiliserait_ contoso.sharepoint.com et _contoso-my.sharepoint.com_.

#### <a name="optimize-ip-address-ranges"></a>Optimiser les plages d’adresses IP

Au moment d’écrire les plages d’adresses IP correspondant à ces points de terminaison sont les suivantes. Il est vivement recommandé d’utiliser un [script](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) tel que cet exemple, le [service web IP et URL Microsoft 365](microsoft-365-ip-web-service.md) ou la [page URL/IP](urls-and-ip-address-ranges.md) pour vérifier les mises à jour lors de l’application de la configuration et mettre en place une stratégie pour le faire régulièrement.

```markdown
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

Le client VPN doit être configuré de sorte que le trafic vers le **Optimiser** IPs soient acheminés de cette façon. Cela permet au trafic d’utiliser les ressources Microsoft locales telles que les portails frontaux du service Microsoft 365, telles que la porte frontale [Azure](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/), qui fournit des services Microsoft 365 et des points de terminaison de connectivité aussi proches que possible de vos utilisateurs. Cela nous permet de fournir des niveaux de performances élevés aux utilisateurs où [qu’ils](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) soient dans le monde et de tirer pleinement parti du réseau mondial de Microsoft, qui se trouve probablement à quelques millisecondes de la sortie directe de vos utilisateurs.

## <a name="howto-guides-for-common-vpn-platforms"></a>Guides d’utilisation pour les plateformes VPN courantes

Cette section fournit des liens vers des guides détaillés pour implémenter la tunneling fractionnée pour Microsoft 365 trafic provenant des partenaires les plus courants dans cet espace. Nous ajouterons des guides à mesure qu’ils seront disponibles.

- **Windows 10 vpn :** optimisation du trafic Microsoft 365 pour les travailleurs à distance avec le [client VPN Windows 10 natif](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco AnyConnect**: [Optimiser le tunnel mixte AnyConnect pour Office 365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect :** [optimisation du trafic Microsoft 365 via vpn split Tunnel exclure l’itinéraire d’accès](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **Big-IP APM** des réseaux F5 : optimisation du trafic Microsoft 365 sur l’accès à distance via des VPN lors de l’utilisation de [BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Passerelle Citrix** : [optimisation du tunnel fractionné VPN de la passerelle Citrix pour Office 365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN Tunneling: How to configure split tunneling to exclude Microsoft 365 applications](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **VPN de point** de [contrôle : comment configurer split Tunnel pour Microsoft 365 et d’autres applications SaaS](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>Articles connexes

[Vue d’ensemble : tunnel vpn partagé pour Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Scénarios courants de tunneling fractionnement VPN pour Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sécurisation Teams trafic multimédia pour la tunnelisation fractionnée VPN](microsoft-365-vpn-securing-teams.md)

[Considérations spéciales pour les flux et les événements en direct dans les environnements VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimisation des performances pour les utilisateurs chinois](microsoft-365-networking-china.md)

[Principes de connectivité réseau Microsoft 365](microsoft-365-network-connectivity-principles.md)

[Évaluation de la connectivité réseau Microsoft 365](assessing-network-connectivity.md)

[Microsoft 365 réseau et l’optimisation des performances](network-planning-and-performance.md)

[D'autres méthodes pour les professionnels de la sécurité et de l’informatique pour optimiser les contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui (blog de l'équipe de sécurité Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Améliorer les performances de VPN chez Microsoft : utiliser les profils VPN Windows 10 pour autoriser les connexions automatiques](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Fonctionnement sur VPN : comment Microsoft maintient les employés travaillant à distance connectés](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Réseau mondial Microsoft](/azure/networking/microsoft-global-network)
