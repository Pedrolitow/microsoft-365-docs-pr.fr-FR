---
title: Routage avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Dans cet article, découvrez les exigences de routage, les circuits et les domaines de routage Azure ExpressRoute à utiliser avec Office 365.
ms.openlocfilehash: d157515f60a68a46b033571a0fd39e6a5711b884
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58575827"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routage avec ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour comprendre correctement le trafic de routage vers Office 365 à l’aide d’Azure ExpressRoute, vous devez bien comprendre les principales exigences de [routage ExpressRoute,](/azure/expressroute/expressroute-routing) ainsi que les [circuits ExpressRoute](/azure/expressroute/expressroute-circuit-peerings)et les domaines de routage. Ces éléments d’aide sont les principes de base de l’utilisation d’ExpressRoute sur Office 365 clients s’appuieront sur ces éléments.
  
Voici quelques-uns des éléments clés que vous devrez comprendre dans les articles ci-dessus :
  
- Les circuits ExpressRoute ne sont pas mappés à une infrastructure physique spécifique, mais sont une connexion logique réalisée à un emplacement d’homologue unique par Microsoft et un fournisseur d’homologues en votre nom.

- Il existe un mappage 1:1 entre un circuit ExpressRoute et une clé client.

- Chaque circuit peut prendre en charge deux relations d’homologue indépendantes (l’homologue privé Azure et l’homologue Microsoft) ; Office 365 nécessite l’homologue Microsoft.

- Chaque circuit dispose d’une bande passante fixe partagée entre toutes les relations d’homologue.

- Les adresses IPv4 publiques et les numéros AS publics qui seront utilisés pour le circuit ExpressRoute doivent être validés en tant que propriétés de votre choix ou attribués exclusivement par le propriétaire de la plage d’adresses.

- Les circuits ExpressRoute virtuels sont redondants globalement et suivent les pratiques de routage BGP standard. C’est pourquoi nous recommandons deux circuits physiques par sortie vers votre fournisseur dans une configuration active/active.

Consultez la [page FAQ pour](/azure/expressroute/expressroute-faqs) plus d’informations sur les services pris en charge, les coûts et les détails de configuration. Pour plus d’informations sur la liste des fournisseurs de connectivité offrant une prise en charge de l’homologue Microsoft, voir l’article sur les emplacements [ExpressRoute.](/azure/expressroute/expressroute-locations) Nous avons également enregistré une série de formation [Azure ExpressRoute](https://channel9.msdn.com/series/aer) pour Office 365 en 10 partie sur Channel 9 pour expliquer plus en profondeur les concepts.
  
## <a name="ensuring-route-symmetry"></a>Garantir la symétrie de l’itinéraire

Les Office 365 serveurs frontux sont accessibles à la fois sur Internet et ExpressRoute. Ces serveurs préfèrent revenir en local sur les circuits ExpressRoute lorsque les deux sont disponibles. Pour cette raison, il existe un risque d’asymétrie d’itinéraire si le trafic provenant de votre réseau préfère router sur vos circuits Internet. Les itinéraires asymétriques sont un problème, car les appareils qui effectuent une inspection avec état des paquets peuvent bloquer le trafic de retour qui suit un chemin différent de celui des paquets sortants suivis.
  
Que vous initiez une connexion à Office 365 via Internet ou ExpressRoute, la source doit être une adresse routable publiquement. Avec de nombreux clients pairant directement avec Microsoft, il n’est pas possible d’avoir des adresses privées où la duplication est possible entre les clients.
  
Voici des scénarios dans lequel les communications entre Office 365 votre réseau local seront initiées. Pour simplifier la conception de votre réseau, nous vous recommandons de les router via le chemin Internet.
  
- Services SMTP tels que le courrier provenant d’un client Exchange Online vers un hôte local ou SharePoint Online Mail envoyé depuis SharePoint Online vers un hôte local. Le protocole SMTP est utilisé plus largement au sein du réseau de Microsoft que les préfixes d’itinéraire partagés sur les circuits ExpressRoute et la publicité sur les serveurs SMTP locaux sur ExpressRoute provoquera des défaillances avec ces autres services.

- ADFS lors de la validation du mot de passe pour la signature.

- [Exchange Server déploiements hybrides.](/exchange/exchange-hybrid)

- [SharePoint recherche hybride fédérée.](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online)

- [SharePoint hybride BCS](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype Entreprise hybride](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) et/ou [la fédération Skype Entreprise hybride.](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)

- [Skype Entreprise Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Pour que Microsoft soit de nouveau acheminé vers votre réseau pour ces flux de trafic bi-directionnel, les itinéraires BGP vers vos appareils locaux doivent être partagés avec Microsoft. Lorsque vous annoncez des préfixes d’itinéraire à Microsoft sur ExpressRoute, vous devez suivre les meilleures pratiques ci-après :

1) N’annoncez pas le même préfixe d’itinéraire d’adresse IP publique sur Internet public et sur ExpressRoute. Il est recommandé que les annonces de préfixe d’itinéraire IP BGP à Microsoft sur ExpressRoute soient d’une plage qui n’est pas publiée sur Internet du tout. Si cela n’est pas possible en raison de l’espace d’adressage IP disponible, il est essentiel de vous assurer que vous annoncez une plage plus spécifique sur ExpressRoute que les circuits Internet.

2) Utilisez des pools IP NAT distincts par circuit ExpressRoute et séparez-les de vos circuits Internet.

3) N’ignorez pas que tout itinéraire publié à Microsoft attirera le trafic réseau provenant de n’importe quel serveur du réseau de Microsoft, pas seulement ceux pour lesquels les itinéraires sont publiés sur votre réseau sur ExpressRoute. Annoncez uniquement des itinéraires vers des serveurs où les scénarios de routage sont définis et bien compris par votre équipe. Annoncer des préfixes d’itinéraire d’adresses IP distincts à chacun des circuits ExpressRoute de votre réseau.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Choix des applications et des fonctionnalités acheminées sur ExpressRoute

Lorsque vous configurez une relation d’homologue à l’aide du domaine de routage d’homologue Microsoft et que vous êtes approuvé pour l’accès approprié, vous pouvez voir tous les services PaaS et SaaS disponibles sur ExpressRoute. Les Office 365 conçus pour ExpressRoute peuvent être gérés avec des [communautés BGP](./bgp-communities-in-expressroute.md) ou des filtres [d’itinéraire.](/azure/expressroute/how-to-routefilter-portal)
  
Chacune des fonctionnalités Office 365 disponibles à l’aide de l’homologue Microsoft est répertoriée dans [l’article Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) points de terminaison par type d’application et FQDN. La raison d’utiliser le FQDN dans les tableaux est de permettre aux clients de gérer le trafic à l’aide de fichiers PAC ou d’autres configurations proxy. Consultez notre guide de gestion des points de terminaison [Office 365](./managing-office-365-endpoints.md) par exemple des fichiers PAC.
  
Dans certains cas, nous avons utilisé un domaine générique dans lequel un ou plusieurs sous-noms de domaine (FQDN) sont publiés différemment du domaine générique de niveau supérieur. Cela se produit généralement lorsque le caractère générique représente une longue liste de serveurs publiés sur ExpressRoute et Internet, alors qu’un petit sous-ensemble de destinations est uniquement publié sur Internet, ou inversement. Reportez-vous aux tableaux ci-dessous pour comprendre les différences.
  
Ce tableau affiche les FQDN génériques publiés sur Internet et Azure ExpressRoute, ainsi que les sous-FQDN publiés uniquement sur Internet.

|**Domaine générique publié sur les circuits ExpressRoute et Internet**|**Sous-FQDN publié sur les circuits Internet uniquement**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

En règle générale, les fichiers PAC sont destinés à envoyer des demandes réseau aux points de terminaison publiés ExpressRoute directement au circuit et à toutes les autres demandes réseau à votre proxy. Si vous configurez un fichier PAC comme celui-ci, composez votre fichier PAC dans l’ordre suivant :
  
1. Incluez les sous-FQDN de la colonne 2 dans le tableau ci-dessus en haut de votre fichier PAC, en envoyant le trafic vers votre proxy. Nous avons créé un exemple de fichier PAC que vous pouvez utiliser dans notre article sur la gestion Office 365 [de terminaison.](./managing-office-365-endpoints.md)

2. Incluez tous les FQDN marqués comme publiés sur ExpressRoute dans cet [article](./urls-and-ip-address-ranges.md) sous la première section, en envoyant le trafic directement vers votre circuit ExpressRoute.

3. Incluez d’autres points de terminaison ou règles réseau sous ces deux entrées, en envoyant le trafic vers votre proxy.

Ce tableau affiche les domaines génériques publiés sur les circuits Internet uniquement avec les sous-noms de domaine (FQDN) publiés sur Azure ExpressRoute et les circuits Internet. Pour votre fichier PAC ci-dessus, les FQDN de la colonne 2 du tableau ci-dessous sont répertoriés comme étant publiés sur ExpressRoute dans le lien référencé, ce qui signifie qu’ils sont inclus dans le deuxième groupe d’entrées dans le fichier.

|**Domaine générique publié sur des circuits Internet uniquement**|**Sous-FQDN publié sur les circuits ExpressRoute et Internet**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> <div style="display: inline">www.office.com</div>  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover- \<tenant\> .outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routage Office 365 trafic sur Internet et ExpressRoute

Pour router vers l Office 365 application de votre choix, vous devez déterminer un certain nombre de facteurs clés.
  
1. Quantité de bande passante nécessaire à l’application. L’échantillonnage de l’utilisation existante est la seule méthode fiable pour déterminer cela dans votre organisation.

2. Emplacement(s) de sortie dont vous souhaitez que le trafic réseau quitte votre réseau. Vous devez planifier de réduire la latence du réseau pour la connectivité à Office 365 car cela aura un impact sur les performances. Étant donné Skype Entreprise utilise la voix et la vidéo en temps réel, elle est particulièrement susceptible de subir une latence réseau médiocre.

3. Si vous souhaitez que l’ensemble ou un sous-ensemble de vos emplacements réseau utilise ExpressRoute.

4. Emplacements à partir des quel emplacements votre fournisseur réseau choisi propose ExpressRoute.

Une fois que vous avez répondu à ces questions, vous pouvez mettre en service un circuit ExpressRoute qui répond aux besoins de bande passante et d’emplacement. Pour plus d’aide sur la planification du réseau, reportez-vous [au guide Office 365](./network-planning-and-performance.md) optimisation du réseau et à l’étude de cas sur la façon dont Microsoft gère la planification des performances [réseau.](https://aka.ms/tunemsit)
  
### <a name="example-1-single-geographic-location"></a>Exemple 1 : emplacement géographique unique
  
Cet exemple est un scénario pour une société fictive appelée Trey Research qui a un emplacement géographique unique.
  
Les employés de Trey Research sont uniquement autorisés à se connecter aux services et aux sites web sur Internet que le service de sécurité autorise explicitement sur la paire de proxies sortants qui se trouve entre le réseau d’entreprise et son fournisseur de services Internet.
  
Trey Research prévoit d’utiliser Azure ExpressRoute pour Office 365 et reconnaît que certains trafics tels que le trafic destiné aux réseaux de distribution de contenu ne pourront pas être acheminés sur ExpressRoute pour Office 365 connexion. Étant donné que tout le trafic a déjà été route vers les périphériques proxy par défaut, ces demandes continueront de fonctionner comme auparavant. Une fois que Trey Research a établi qu’il peut répondre aux exigences de routage Azure ExpressRoute, il crée un circuit, configure le routage et relie le nouveau circuit ExpressRoute à un réseau virtuel. Une fois que la configuration fondamentale d’Azure ExpressRoute est en place, Trey Research utilise le fichier [PAC #2](./managing-office-365-endpoints.md) que nous publions pour router le trafic avec des données spécifiques au client sur l’ExpressRoute direct pour Office 365 connexions.
  
Comme le montre le diagramme suivant, Trey Research peut satisfaire à l’exigence d’acheminement du trafic Office 365 sur Internet et d’un sous-ensemble de trafic sur ExpressRoute à l’aide d’une combinaison de modifications de configuration du routage et du proxy sortant.
  
1. En utilisant [le #2 PAC que](./managing-office-365-endpoints.md) nous publions pour router le trafic via un point de sortie Internet distinct pour Azure ExpressRoute pour Office 365.

2. Les clients sont configurés avec un itinéraire par défaut vers les proxies de Trey Research.

Dans cet exemple de scénario, Trey Research utilise un périphérique proxy sortant. De même, les clients qui n’utilisent pas Azure ExpressRoute pour Office 365 peuvent utiliser cette technique pour router le trafic en fonction du coût d’inspection du trafic destiné aux points de terminaison à volume élevé connus.
  
Les FQDN de volume les plus élevés pour Exchange Online, SharePoint Online et Skype Entreprise Online sont les suivants :
  
![Réseau Edge client ExpressRoute.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\> -my.sharepoint.com, \<tenant-name\> - \<app\> .sharepoint.com

- \*. Lync.com avec les plages IP pour le trafic non-TCP

- \*broadcast.officeapps.live.com, \* excel.officeapps.live.com, \* onenote.officeapps.live.com, \* powerpoint.officeapps.live.com, \* view.officeapps.live.com, \* visio.officeapps.live.com, \* word-edit.officeapps.live.com, \* word-view.officeapps.live.com, office.live.com

En savoir plus sur le déploiement et la gestion des [paramètres de proxy](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) dans Windows 8 et [s’assurer Office 365 n’est](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)pas limitée par votre proxy .
  
Avec un seul circuit ExpressRoute, il n’existe pas de haute disponibilité pour Trey Research. En cas d’échec de la paire redondante des périphériques Edge de Trey qui dessert la connectivité ExpressRoute, il n’y a pas de circuit ExpressRoute supplémentaire vers qui faire l’objet d’un perf. Cela laisse Trey Research dans une situation préalable, car le fait de faire un pas vers Internet nécessitera une reconfiguration manuelle et, dans certains cas, de nouvelles adresses IP. Si Trey souhaite ajouter une haute disponibilité, la solution la plus simple consiste à ajouter des circuits ExpressRoute supplémentaires pour chaque emplacement et à configurer les circuits de manière active/active.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routage d’ExpressRoute Office 365 avec plusieurs emplacements

Le dernier scénario, le routage Office 365 trafic sur ExpressRoute est la base d’une architecture de routage encore plus complexe. Quel que soit le nombre d’emplacements, le nombre de continents où ces emplacements existent, le nombre de circuits ExpressRoute, etc., la possibilité d’router du trafic vers Internet et du trafic sur ExpressRoute sera nécessaire.
  
Les autres questions auxquelles vous devez répondre pour les clients ayant plusieurs emplacements géographiques sont les suivantes :
  
1. Avez-vous besoin d’un circuit ExpressRoute à chaque emplacement ? Si vous utilisez Skype Entreprise Online ou si vous êtes préoccupé par la sensibilité à la latence pour SharePoint Online ou Exchange Online, une paire redondante de circuits ExpressRoute actifs/actifs est recommandée à chaque emplacement. Pour plus d Skype Entreprise, voir le guide sur la qualité des médias et la connectivité réseau.

2. Si un circuit ExpressRoute n’est pas disponible dans une région particulière, comment Office 365 trafic destiné doit-il être acheminé ?

3. Quelle est la méthode préférée pour consolider le trafic dans le cas de réseaux avec de nombreux petits emplacements ?

Chacun de ces éléments présente un défi unique qui vous oblige à évaluer votre propre réseau et les options disponibles auprès de Microsoft.

|**Considération**|**Composants réseau à évaluer**|
|:-----|:-----|
|Circuits à plusieurs emplacements  <br/> |Nous vous recommandons d’au moins deux circuits configurés de manière active/active.  <br/> Les coûts, la latence et les besoins en bande passante doivent être comparés.  <br/> Utilisez le coût d’itinéraire BGP, les fichiers PAC et nat pour gérer le routage avec plusieurs circuits.  <br/> |
|Routage à partir d’emplacements sans circuit ExpressRoute  <br/> |Nous recommandons la sortie et la résolution DNS aussi proches que la personne à l’origine de la demande de Office 365.  <br/> Le forwarding DNS peut être utilisé pour permettre aux bureaux distants de découvrir le point de terminaison approprié.  <br/> Les clients du bureau distant doivent avoir un itinéraire disponible qui permet d’accéder au circuit ExpressRoute.  <br/> |
|Consolidation de petits bureaux  <br/> |La bande passante disponible et l’utilisation des données doivent être comparées avec soin.  <br/> |

> [!NOTE]
> Microsoft préfère ExpressRoute sur Internet si l’itinéraire est disponible quel que soit l’emplacement physique.
  
Chacune de ces considérations doit être prise en compte pour chaque réseau unique. Voici un exemple.
  
### <a name="example-2-multi-geographic-locations"></a>Exemple 2 : emplacements multi-géographiques
  
Cet exemple est un scénario pour une société fictive appelée Humongous Insurance qui possède plusieurs emplacements géographiques.
  
Humongous Insurance est géographiquement dispersé avec des bureaux dans le monde entier. Ils souhaitent implémenter Azure ExpressRoute Office 365 pour conserver la plupart de leurs Office 365 sur les connexions réseau directes. Humongous Insurance possède également des bureaux sur deux continents supplémentaires. Les employés dans le bureau distant où ExpressRoute n’est pas réalisable devront retourner à l’une des installations principales ou aux deux pour utiliser une connexion ExpressRoute.
  
Le principe directeur consiste à obtenir le trafic Office 365 vers un centre de données Microsoft aussi rapidement que possible. Dans cet exemple, Humongous Insurance doit décider si ses bureaux distants doivent être acheminés via Internet pour se rendre à un centre de données Microsoft via n’importe quelle connexion le plus rapidement possible ou si leurs bureaux distants doivent être acheminés via un réseau interne pour se rendre à un centre de données Microsoft via une connexion ExpressRoute aussi rapidement que possible.
  
Les centres de données, les réseaux et l’architecture d’applications de Microsoft sont conçus pour prendre des communications globalement disparates et les mettre en service de la manière la plus efficace possible. Il s’agit de l’un des plus grands réseaux au monde. Les demandes destinées aux Office 365 qui restent sur les réseaux des clients plus longtemps que nécessaire ne pourront pas tirer parti de cette architecture.
  
Dans la situation de Humongous Insurance, ils doivent continuer en fonction des applications qu’ils ont l’intention d’utiliser sur ExpressRoute. Par exemple, s’il s’agit d’un client Skype Entreprise Online ou s’il envisage d’utiliser la connectivité ExpressRoute lors de la connexion à des réunions Skype Entreprise Online externes, la conception recommandée dans le guide de connectivité réseau et qualité des médias Skype Entreprise Online consiste à mettre en service un circuit ExpressRoute supplémentaire pour le troisième emplacement. Cela peut être plus coûteux du point de vue de la mise en réseau . toutefois, le routage des demandes d’un continent vers un autre avant la livraison à un centre de données Microsoft peut entraîner une expérience médiocre ou inutilisable pendant les réunions et les communications Skype Entreprise Online.
  
Si Humongous Insurance n’utilise pas ou ne prévoit aucunement d’utiliser Skype Entreprise Online, le routage du Office 365 trafic réseau destiné à un continent avec une connexion ExpressRoute peut être réalisable, mais peut entraîner une latence inutile ou une congestion TCP. Dans les deux cas, il est recommandé de router le trafic Internet destiné à Internet sur le site local pour tirer parti des réseaux de distribution de contenu sur Office 365 réseaux.
  
![Zone multigé géographique ExpressRoute.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Lorsque Humongous Insurance planifie sa stratégie multigé géographique, il existe un certain nombre d’éléments à prendre en compte en matière de taille du circuit, de nombre de circuits, deover, etc.
  
Avec ExpressRoute dans un emplacement unique avec plusieurs régions qui tentent d’utiliser le circuit, Humongous Insurance souhaite s’assurer que les connexions à Office 365 à partir du bureau distant sont envoyées au centre de données Office 365 le plus proche du siège social et reçues par l’emplacement du siège social. Pour ce faire, Humongous Insurance implémente le forwarding DNS pour réduire le nombre d’allers-retours et de recherche DNS nécessaires pour établir la connexion appropriée avec l’environnement Office 365 le plus proche du point de sortie Internet du siège social. Cela empêche le client de résoudre un serveur frontal local et garantit que le serveur Front-End que la personne se connecte se trouve près du siège social où Humongous Insurance est homologue avec Microsoft. Vous pouvez également apprendre à [affecter un transfert conditionnel pour un nom de domaine.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10))
  
Dans ce scénario, le trafic provenant du bureau à distance résout l’infrastructure frontale Office 365 en Amérique du Nord et utilise Office 365 pour se connecter aux serveurs frontaux en fonction de l’architecture de l’application Office 365. Par exemple, Exchange Online la connexion en Amérique du Nord et ces serveurs frontux se connectent au serveur de boîtes aux lettres principal où le client réside. Tous les services ont un service de porte frontal largement distribué composé de destinations unicast et anycast.
  
Si Humongous possède des bureaux importants dans plusieurs continents, un minimum de deux circuits actifs/actifs par région est recommandé afin de réduire la latence pour les applications sensibles telles que Skype Entreprise Online. Si tous les bureaux sont situés sur un seul continent ou n’utilisent pas la collaboration en temps réel, le fait de disposer d’un point de sortie consolidé ou distribué est une décision propre au client. Lorsque plusieurs circuits sont disponibles, le routage BGP garantit le failover en cas d’indisponibilité d’un seul circuit.
  
En savoir plus sur les [exemples de configurations de routage](/azure/expressroute/expressroute-config-samples-routing) et [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat) .
  
## <a name="selective-routing-with-expressroute"></a>Routage sélectif avec ExpressRoute

Le routage sélectif avec ExpressRoute peut être nécessaire pour diverses raisons, telles que le test, le déploiement d’ExpressRoute sur un sous-ensemble d’utilisateurs. Les clients peuvent utiliser différents outils pour router de manière sélective Office 365 réseau sur ExpressRoute :
  
1. **Filtrage/séparation** des itinéraires : permet aux itinéraires BGP d’Office 365 sur ExpressRoute vers un sous-ensemble de vos sous-réseaux ou routeurs. Cela est trié selon le segment réseau du client ou l’emplacement physique du bureau. Ceci est courant pour le déploiement échelonné d’ExpressRoute pour Office 365 et est configuré sur vos appareils BGP.

2. **Fichiers PAC/URL** : diriger Office 365 trafic réseau destiné à des FQDN spécifiques à router sur un chemin d’accès spécifique. Cela est trié de manière sélective par ordinateur client identifié par le [déploiement de fichiers PAC.](./managing-office-365-endpoints.md)

3. **Filtrage des itinéraires**  -  [Les filtres d’itinéraire](/azure/expressroute/how-to-routefilter-portal) permettent de consommer un sous-ensemble de services pris en charge par le biais de l’homologue Microsoft.

4. **Communautés BGP** : le filtrage basé sur des balises de communauté [BGP](./bgp-communities-in-expressroute.md) permet à un client de déterminer quelles applications Office 365 traversent ExpressRoute et qui traverseront Internet.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Voir aussi

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Utilisation de communautés BGP dans ExpressRoute pour Office 365 scénarios](bgp-communities-in-expressroute.md)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages dʼadresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
