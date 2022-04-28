---
title: Routage avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.openlocfilehash: c63e3ae14c9b369265622f17c2e542818620aa3e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092908"
---
# <a name="routing-with-expressroute-for-office-365"></a>Routage avec ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour bien comprendre le trafic de routage vers Office 365 à l’aide d’Azure ExpressRoute, vous devez avoir une bonne compréhension des [principales exigences de routage ExpressRoute](/azure/expressroute/expressroute-routing), ainsi que des [circuits ExpressRoute et des domaines de routage](/azure/expressroute/expressroute-circuit-peerings). Ceux-ci présentent les principes fondamentaux de l’utilisation d’ExpressRoute sur lequel Office 365 clients s’appuieront.
  
Voici quelques-uns des éléments clés des articles ci-dessus que vous devez comprendre :
  
- Les circuits ExpressRoute ne sont pas mappés à une infrastructure physique spécifique, mais sont une connexion logique établie à un emplacement de peering unique par Microsoft et un fournisseur de peering en votre nom.

- Il existe un mappage 1:1 entre un circuit ExpressRoute et une clé du client.

- Chaque circuit peut gérer deux relations de peering indépendantes (peering privé Azure et peering Microsoft) ; Office 365 nécessite le peering Microsoft.

- Chaque circuit a une bande passante fixe qui est partagée entre toutes les relations de peering.

- Toutes les adresses IPv4 publiques et les numéros AS publics qui seront utilisés pour le circuit ExpressRoute doivent être validés comme appartenant à vous, ou attribués exclusivement à vous par le propriétaire de la plage d’adresses.

- Les circuits ExpressRoute virtuels sont redondants globalement et suivent les pratiques de routage BGP standard. C’est pourquoi nous vous recommandons deux circuits physiques par sortie vers votre fournisseur dans une configuration active/active.

Consultez la [page FAQ](/azure/expressroute/expressroute-faqs) pour plus d’informations sur les services pris en charge, les coûts et les détails de configuration. Pour plus d’informations sur la liste des fournisseurs de connectivité offrant la prise en charge du peering Microsoft, consultez [l’article sur les emplacements ExpressRoute](/azure/expressroute/expressroute-locations) . Nous avons également enregistré une série de 10 parties [d’Azure ExpressRoute pour Office 365 Training](https://channel9.msdn.com/series/aer) sur Channel 9 afin d’expliquer plus en détail les concepts.
  
## <a name="ensuring-route-symmetry"></a>Garantir la symétrie des itinéraires

Les serveurs frontaux Office 365 sont accessibles sur Internet et ExpressRoute. Ces serveurs préfèrent revenir en local via des circuits ExpressRoute lorsque les deux sont disponibles. Pour cette raison, il existe une possibilité d’asymétrie de routage si le trafic de votre réseau préfère le routage via vos circuits Internet. Les itinéraires asymétriques sont un problème, car les appareils qui effectuent une inspection avec état des paquets peuvent bloquer le trafic de retour qui suit un chemin différent de celui des paquets sortants suivis.
  
Que vous initiez ou non une connexion à Office 365 via Internet ou ExpressRoute, la source doit être une adresse routable publiquement. Avec de nombreux clients qui peering directement avec Microsoft, avoir des adresses privées où la duplication est possible entre les clients n’est pas possible.
  
Voici les scénarios dans lesquels les communications entre Office 365 et votre réseau local sont lancées. Pour simplifier la conception de votre réseau, nous vous recommandons d’effectuer le routage suivant sur le chemin d’accès Internet.
  
- Services SMTP tels que le courrier d’un locataire Exchange Online vers un hôte local ou SharePoint Courrier en ligne envoyé de SharePoint Online à un hôte local. Le protocole SMTP est utilisé plus largement dans le réseau de Microsoft que les préfixes de route partagés sur les circuits ExpressRoute et la publicité de serveurs SMTP locaux sur ExpressRoute entraîne des échecs avec ces autres services.

- ADFS lors de la validation du mot de passe pour la connexion.

- [Exchange Server déploiements hybrides](/exchange/exchange-hybrid).

- [SharePoint recherche hybride fédérée](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS hybride](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype Entreprise fédération hybride](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) et/ou [Skype Entreprise](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype Entreprise Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Pour que Microsoft puisse revenir à votre réseau pour ces flux de trafic bidirectionnel, les itinéraires BGP vers vos appareils locaux doivent être partagés avec Microsoft. Lorsque vous publiez des préfixes de routage vers Microsoft via ExpressRoute, vous devez suivre les bonnes pratiques suivantes :

1) Ne publiez pas le même préfixe de route d’adresse IP publique sur l’Internet public et via ExpressRoute. Il est recommandé que les annonces de préfixe de route BGP IP à Microsoft sur ExpressRoute proviennent d’une plage qui n’est pas du tout publiée sur Internet. Si cela n’est pas possible en raison de l’espace d’adressage IP disponible, il est essentiel de s’assurer que vous publiez une plage plus spécifique sur ExpressRoute que tous les circuits Internet.

2) Utilisez des pools d’adresses IP NAT distincts par circuit ExpressRoute et distincts de vos circuits Internet.

3) Tout itinéraire publié pour Microsoft attirera le trafic réseau de n’importe quel serveur du réseau de Microsoft, et pas seulement ceux pour lesquels les itinéraires sont publiés sur votre réseau via ExpressRoute. Publiez uniquement des itinéraires vers des serveurs où les scénarios de routage sont définis et bien compris par votre équipe. Publiez des préfixes de routage d’adresse IP distincts sur chacun de plusieurs circuits ExpressRoute à partir de votre réseau.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Choix des applications et fonctionnalités acheminées via ExpressRoute

Lorsque vous configurez une relation de peering à l’aide du domaine de routage de peering Microsoft et que vous êtes approuvé pour l’accès approprié, vous pouvez voir tous les services PaaS et SaaS disponibles sur ExpressRoute. Les services Office 365 conçus pour ExpressRoute peuvent être gérés avec des [communautés BGP](./bgp-communities-in-expressroute.md) ou [des filtres de routage](/azure/expressroute/how-to-routefilter-portal).
  
Chacune des fonctionnalités Office 365 disponibles à l’aide du peering Microsoft est répertoriée dans [l’article Office 365 points de terminaison](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) par type d’application et nom de domaine complet. La raison de l’utilisation du nom de domaine complet dans les tables est de permettre aux clients de gérer le trafic à l’aide de fichiers PAC ou d’autres configurations de proxy. Consultez notre guide de [gestion des points](./managing-office-365-endpoints.md) de terminaison Office 365, par exemple des fichiers PAC.
  
Dans certains cas, nous avons utilisé un domaine générique où un ou plusieurs sous-noms de domaine complets sont publiés différemment du domaine générique de niveau supérieur. Cela se produit généralement lorsque le caractère générique représente une longue liste de serveurs qui sont tous publiés sur ExpressRoute et Internet, tandis qu’un petit sous-ensemble de destinations est uniquement publié sur Internet, ou inversement. Reportez-vous aux tableaux ci-dessous pour comprendre où se trouvent les différences.
  
Ce tableau affiche les noms de domaine complets génériques publiés sur Internet et Azure ExpressRoute, ainsi que les sous-noms de domaine complets publiés uniquement sur Internet.

|**Domaine générique publié sur les circuits ExpressRoute et Internet**|**Sous-nom de domaine complet publié sur les circuits Internet uniquement**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

En règle générale, les fichiers PAC sont destinés à envoyer des demandes réseau aux points de terminaison publiés par ExpressRoute directement au circuit et toutes les autres demandes réseau à votre proxy. Si vous configurez un fichier PAC comme celui-ci, composez votre fichier PAC dans l’ordre suivant :
  
1. Incluez les sous-noms de domaine complets de la colonne 2 dans le tableau ci-dessus en haut de votre fichier PAC, en envoyant le trafic vers votre proxy. Nous avons créé un exemple de fichier PAC à utiliser dans notre article sur la [gestion des points de terminaison Office 365](./managing-office-365-endpoints.md).

2. Incluez tous les noms de domaine complets marqués comme publiés dans ExpressRoute dans [cet article](./urls-and-ip-address-ranges.md) sous la première section, en envoyant le trafic directement à votre circuit ExpressRoute.

3. Incluez tous les autres points de terminaison ou règles réseau sous ces deux entrées, en envoyant le trafic vers votre proxy.

Ce tableau affiche les domaines génériques publiés sur les circuits Internet uniquement avec les sous-noms de domaine complets publiés sur Azure ExpressRoute et les circuits Internet. Pour votre fichier PAC ci-dessus, les noms de domaine complets de la colonne 2 du tableau ci-dessous sont répertoriés comme étant publiés sur ExpressRoute dans le lien référencé, ce qui signifie qu’ils seraient inclus dans le deuxième groupe d’entrées du fichier.

|**Domaine générique publié sur les circuits Internet uniquement**|**Sous-nom de domaine complet publié sur ExpressRoute et les circuits Internet**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Routage Office 365 le trafic via Internet et ExpressRoute

Pour accéder à l’application Office 365 de votre choix, vous devez déterminer un certain nombre de facteurs clés.
  
1. Quantité de bande passante nécessaire à l’application. L’échantillonnage de l’utilisation existante est la seule méthode fiable pour déterminer cela dans votre organisation.

2. Emplacement(s) de sortie duquel vous souhaitez que le trafic réseau quitte votre réseau. Vous devez prévoir de réduire la latence réseau pour la connectivité à Office 365, car cela aura un impact sur les performances. Étant donné que Skype Entreprise utilise la voix et la vidéo en temps réel, elle est vulnérable à une faible latence réseau.

3. Si vous souhaitez que tout ou partie de vos emplacements réseau utilisent ExpressRoute.

4. À partir de quels emplacements votre fournisseur de réseau choisi offre ExpressRoute.

Une fois que vous avez déterminé les réponses à ces questions, vous pouvez approvisionner un circuit ExpressRoute qui répond aux besoins de bande passante et d’emplacement. Pour plus d’aide à la planification réseau, reportez-vous au [Office 365 guide de réglage du réseau](./network-planning-and-performance.md) et à l’étude de [cas sur la façon dont Microsoft gère la planification des performances réseau](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Exemple 1 : Emplacement géographique unique
  
Cet exemple est un scénario pour une société fictive appelée Trey Research qui a un emplacement géographique unique.
  
Les employés de Trey Research sont uniquement autorisés à se connecter aux services et sites web sur Internet que le service de sécurité autorise explicitement sur la paire de proxys sortants qui se trouvent entre le réseau d’entreprise et leur fournisseur de services Internet.
  
Trey Research prévoit d’utiliser Azure ExpressRoute pour Office 365 et reconnaît que certains trafics tels que le trafic destiné aux réseaux de distribution de contenu ne pourront pas être acheminés via ExpressRoute pour Office 365 connexion. Étant donné que tout le trafic est déjà acheminé vers les périphériques proxy par défaut, ces demandes continueront de fonctionner comme avant. Une fois trey Research déterminé qu’ils peuvent répondre aux exigences de routage Azure ExpressRoute, ils procèdent à la création d’un circuit, à la configuration du routage et à la liaison du nouveau circuit ExpressRoute à un réseau virtuel. Une fois la configuration Azure ExpressRoute fondamentale en place, Trey Research utilise le [fichier PAC #2 que nous publions](./managing-office-365-endpoints.md) pour router le trafic avec des données spécifiques au client via ExpressRoute direct pour les connexions Office 365.
  
Comme illustré dans le diagramme suivant, Trey Research est en mesure de satisfaire à l’exigence de router le trafic Office 365 sur Internet et un sous-ensemble de trafic via ExpressRoute à l’aide d’une combinaison de changements de configuration de routage et de proxy sortant.
  
1. À l’aide du [fichier PAC #2 que nous publions](./managing-office-365-endpoints.md) pour acheminer le trafic via un point de sortie Internet distinct pour Azure ExpressRoute pour Office 365.

2. Les clients sont configurés avec un itinéraire par défaut vers les proxys de Trey Research.

Dans cet exemple de scénario, Trey Research utilise un périphérique proxy sortant. De même, les clients qui n’utilisent pas Azure ExpressRoute pour Office 365 peuvent utiliser cette technique pour acheminer le trafic en fonction du coût d’inspection du trafic destiné aux points de terminaison à volume élevé connus.
  
Les noms de domaine complets en volume les plus élevés pour Exchange Online, SharePoint Online et Skype Entreprise Online sont les suivants :
  
![Réseau de périphérie client ExpressRoute.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>.sharepoint.com, \<tenant-name\>-my.sharepoint.com, \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com ainsi que les plages d’adresses IP pour le trafic non TCP

- \*broadcast.officeapps.live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \*word-edit.officeapps.live.com, \*word-view.officeapps.live.com, office.live.com

Apprenez-en davantage sur [le déploiement et la gestion des paramètres de proxy dans Windows 8](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) et [assurez-vous que Office 365 n’est pas limité par votre proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Avec un seul circuit ExpressRoute, il n’y a pas de haute disponibilité pour Trey Research. En cas d’échec de la paire redondante d’appareils de périphérie trey qui assurent la connectivité ExpressRoute, il n’y a pas de circuit ExpressRoute supplémentaire vers lequel basculer. Cela laisse Trey Research dans une situation difficile, car le basculement vers Internet nécessitera une reconfiguration manuelle et, dans certains cas, de nouvelles adresses IP. Si Trey souhaite ajouter une haute disponibilité, la solution la plus simple consiste à ajouter des circuits ExpressRoute supplémentaires pour chaque emplacement et à configurer les circuits de manière active/active.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Routage ExpressRoute pour Office 365 avec plusieurs emplacements

Le dernier scénario, le routage Office 365 le trafic via ExpressRoute, constitue la base d’une architecture de routage encore plus complexe. Quel que soit le nombre d’emplacements, le nombre de continents où ces emplacements existent, le nombre de circuits ExpressRoute, et ainsi de suite, la possibilité d’acheminer du trafic vers Internet et un certain trafic via ExpressRoute sera nécessaire.
  
Les questions supplémentaires qui doivent être traitées pour les clients disposant de plusieurs emplacements dans plusieurs zones géographiques sont les suivantes :
  
1. Avez-vous besoin d’un circuit ExpressRoute à chaque emplacement ? Si vous utilisez Skype Entreprise Online ou si vous vous préoccupez de la sensibilité à la latence pour SharePoint Online ou Exchange Online, une paire redondante de circuits ExpressRoute actifs/actifs est recommandée à chaque emplacement. Pour plus d’informations, consultez le guide de connectivité réseau et de qualité des médias Skype Entreprise.

2. Si un circuit ExpressRoute n’est pas disponible dans une région particulière, comment Office 365 trafic destiné doit-il être routé ?

3. Quelle est la méthode recommandée pour consolider le trafic dans le cas de réseaux avec de nombreux petits emplacements ?

Chacun d’eux présente un défi unique qui vous oblige à évaluer votre propre réseau et les options disponibles auprès de Microsoft.

|**Considération**|**Composants réseau à évaluer**|
|:-----|:-----|
|Circuits dans plusieurs emplacements  <br/> |Nous vous recommandons d’avoir au moins deux circuits configurés de manière active/active.  <br/> Les besoins en coûts, en latence et en bande passante doivent être comparés.  <br/> Utilisez le coût de routage BGP, les fichiers PAC et NAT pour gérer le routage avec plusieurs circuits.  <br/> |
|Routage à partir d’emplacements sans circuit ExpressRoute  <br/> |Nous recommandons la sortie et la résolution DNS à proximité de la personne qui lance la demande de Office 365.  <br/> Le transfert DNS peut être utilisé pour permettre aux bureaux distants de découvrir le point de terminaison approprié.  <br/> Les clients du bureau distant doivent disposer d’un itinéraire qui fournit l’accès au circuit ExpressRoute.  <br/> |
|Consolidation des petits bureaux  <br/> |La bande passante disponible et l’utilisation des données doivent être soigneusement comparées.  <br/> |

> [!NOTE]
> Microsoft préférera ExpressRoute sur Internet si l’itinéraire est disponible quel que soit l’emplacement physique.
  
Chacune de ces considérations doit être prise en compte pour chaque réseau unique. Voici un exemple.
  
### <a name="example-2-multi-geographic-locations"></a>Exemple 2 : emplacements multi-géographiques
  
Cet exemple est un scénario pour une société fictive appelée « Humongous Insurance » qui a plusieurs emplacements géographiques.
  
Humongous Insurance est géographiquement dispersée avec des bureaux partout dans le monde. Ils souhaitent implémenter Azure ExpressRoute pour Office 365 afin de conserver la plupart de leur trafic Office 365 sur les connexions réseau directes. Humongous Insurance a également des bureaux sur deux continents supplémentaires. Les employés du bureau à distance où ExpressRoute n’est pas possible devront revenir à l’une des installations principales ou les deux pour utiliser une connexion ExpressRoute.
  
Le principe directeur est d’obtenir Office 365 trafic destiné à un centre de données Microsoft le plus rapidement possible. Dans cet exemple, Humongous Insurance doit décider si ses bureaux distants doivent router via Internet pour accéder à un centre de données Microsoft le plus rapidement possible via n’importe quelle connexion ou si leurs bureaux distants doivent être acheminés sur un réseau interne pour se rendre à un centre de données Microsoft via une connexion ExpressRoute le plus rapidement possible.
  
Les centres de données, les réseaux et l’architecture d’application de Microsoft sont conçus pour prendre des communications disparates et les traiter de la manière la plus efficace possible. Il s’agit de l’un des plus grands réseaux au monde. Les demandes destinées aux Office 365 qui restent sur les réseaux clients plus longtemps que nécessaire ne pourront pas tirer parti de cette architecture.
  
Dans le cas de Humongous Insurance, ils devraient continuer selon les applications qu’ils envisagent d’utiliser via ExpressRoute. Par exemple, s’il s’agit d’un client Skype Entreprise Online ou si vous envisagez d’utiliser la connectivité ExpressRoute lors de la connexion à des réunions externes Skype Entreprise Online, la conception recommandée dans le guide de connectivité réseau et de qualité des médias Skype Entreprise Online consiste à approvisionner un circuit ExpressRoute supplémentaire pour le troisième emplacement. Cela peut être plus coûteux du point de vue de la mise en réseau; Toutefois, le routage des demandes d’un continent vers un autre avant de les remettre à un centre de données Microsoft peut entraîner une expérience médiocre ou inutilisable pendant Skype Entreprise réunions et communications en ligne.
  
Si Humongous Insurance n’utilise pas ou n’envisage pas d’utiliser Skype Entreprise Online de quelque manière que ce soit, le routage Office 365 trafic réseau destiné à un continent avec une connexion ExpressRoute peut être réalisable, mais peut entraîner une latence inutile ou une congestion TCP. Dans les deux cas, il est recommandé de router le trafic internet vers Internet sur le site local pour tirer parti des réseaux de distribution de contenu sur lesquels Office 365 s’appuie.
  
![Multi-géographie ExpressRoute.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Quand Humongous Insurance planifie sa stratégie multi-géographique, il y a beaucoup de choses à prendre en compte autour de la taille du circuit, du nombre de circuits, du basculement, etc.
  
Avec ExpressRoute dans un emplacement unique où plusieurs régions tentent d’utiliser le circuit, Humongous Insurance souhaite s’assurer que les connexions à Office 365 à partir du bureau distant sont envoyées au centre de données Office 365 plus proche du siège social et reçues par l’emplacement du siège social. Pour ce faire, Humongous Insurance implémente le transfert DNS afin de réduire le nombre d’allers-retours et de recherches DNS nécessaires pour établir la connexion appropriée avec l’environnement Office 365 le plus proche du point de sortie Internet du siège social. Cela empêche le client de résoudre un serveur frontal local et garantit que le serveur Front-End que la personne se connecte se trouve à proximité du siège social où Humongous Insurance effectue un peering avec Microsoft. Vous pouvez également apprendre à [attribuer un redirecteur conditionnel pour un nom de domaine](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
Dans ce scénario, le trafic provenant du bureau distant résoudrait l’infrastructure frontale Office 365 dans Amérique du Nord et utiliserait Office 365 pour se connecter aux serveurs principaux en fonction de l’architecture de l’application Office 365. Par exemple, Exchange Online met fin à la connexion dans Amérique du Nord et ces serveurs frontaux se connectent au serveur de boîtes aux lettres back-end où se trouve le locataire. Tous les services ont un service de porte d’entrée largement distribué composé de destinations monodiffusion et anycast.
  
Si Humongous a des bureaux majeurs sur plusieurs continents, un minimum de deux circuits actifs/actifs par région est recommandé afin de réduire la latence pour les applications sensibles telles que Skype Entreprise Online. Si tous les bureaux se trouvent sur un seul continent ou n’utilisent pas de collaboration en temps réel, le fait d’avoir un point de sortie consolidé ou distribué est une décision propre au client. Lorsque plusieurs circuits sont disponibles, le routage BGP garantit le basculement en cas d’indisponibilité d’un circuit unique.
  
En savoir plus sur les [exemples de configurations de routage](/azure/expressroute/expressroute-config-samples-routing) et [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>Routage sélectif avec ExpressRoute

Un routage sélectif avec ExpressRoute peut être nécessaire pour différentes raisons, telles que le test, le déploiement d’ExpressRoute sur un sous-ensemble d’utilisateurs. Il existe différents outils que les clients peuvent utiliser pour acheminer de manière sélective Office 365 trafic réseau via ExpressRoute :
  
1. **Filtrage/séparation** des itinéraires : permettre aux itinéraires BGP de Office 365 sur ExpressRoute vers un sous-ensemble de vos sous-réseaux ou routeurs. Cette opération est acheminée de manière sélective par segment de réseau client ou par emplacement de bureau physique. Cela est courant pour le déploiement échelonné d’ExpressRoute pour Office 365 et est configuré sur vos appareils BGP.

2. **Fichiers/URL PAC** : diriger Office 365 trafic réseau destiné à des noms de domaine complets spécifiques à router sur un chemin spécifique. Cette opération achemine de manière sélective par ordinateur client, comme identifié par [le déploiement de fichiers PAC](./managing-office-365-endpoints.md).

3. **Filtrage des itinéraires** -  [Les filtres de routage](/azure/expressroute/how-to-routefilter-portal) permettent de consommer un sous-ensemble de services pris en charge par le biais du peering Microsoft.

4. **Communautés BGP** : le filtrage basé sur [des balises de communauté BGP](./bgp-communities-in-expressroute.md) permet à un client de déterminer quelles applications Office 365 traverseront ExpressRoute et qui traverseront Internet.

Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>Rubriques connexes

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
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
