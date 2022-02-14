---
title: Planification du réseau avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: Dans cet article, vous allez découvrir Azure ExpressRoute pour Office 365 et comment l’utiliser pour la planification réseau.
ms.openlocfilehash: d411d44ffe08da684b3cbca9a9449c4d04126a39
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62806587"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planification du réseau avec ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

ExpressRoute pour Office 365 la connectivité de couche 3 entre votre réseau et les centres de données de Microsoft. Les circuits utilisent le protocole BGP (Border Gateway Protocol) pour router les annonces Office 365 serveurs frontaux. Du point de vue de vos appareils locaux, lorsqu’ils doivent sélectionner le chemin d’accès TCP/IP correct vers Office 365, Azure ExpressRoute est considéré comme une alternative à Internet.
  
Azure ExpressRoute ajoute un chemin d’accès direct à un ensemble spécifique de fonctionnalités et de services pris en charge proposés Office 365 serveurs au sein des centres de données microsoft. Azure ExpressRoute ne remplace pas la connectivité Internet aux centres de données Microsoft ou les services Internet de base tels que la résolution des noms de domaine. Azure ExpressRoute et vos circuits Internet doivent être sécurisés et redondants.
  
Le tableau suivant met en évidence quelques différences entre les connexions Internet et Azure ExpressRoute dans le contexte de Office 365.

|**Différences dans la planification du réseau**|**Connexion réseau Internet**|**Connexion réseau ExpressRoute**|
|:-----|:-----|:-----|
| Accès aux services Internet requis, y compris ;  <br/>  Résolution de noms DNS  <br/>  Vérification de la révocation de certificats  <br/>  Réseaux de distribution de contenu (CDN)  <br/> |Oui  <br/> |Les demandes à l’infrastructure DNS et/CDN microsoft peuvent utiliser le réseau ExpressRoute.  <br/> |
| Accès aux services Office 365, y compris ;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Entreprise Online  <br/>  Office dans un navigateur  <br/>  Office 365'authentification et le portail d’authentification  <br/> |Oui, toutes les applications et fonctionnalités  <br/> |Oui, applications [et fonctionnalités spécifiques](./urls-and-ip-address-ranges.md) <br/> |
|Sécurité sur site au niveau du périmètre.  <br/> |Oui  <br/> |Oui  <br/> |
|Planification de la haute disponibilité.  <br/> |Faire un point d’accès à une autre connexion réseau Internet  <br/> |Faire un pas vers une autre connexion ExpressRoute  <br/> |
|Connexion directe avec un profil réseau prévisible.  <br/> |Non  <br/> |Oui  <br/> |
|Connectivité IPv6.  <br/> |Oui  <br/> |Oui  <br/> |

Développez les titres ci-dessous pour obtenir des conseils sur la planification réseau. Nous avons également enregistré une série de formations [Azure ExpressRoute](https://channel9.msdn.com/series/aer) en 10 Office 365 plus approfondie.

## <a name="existing-azure-expressroute-customers"></a>Clients Azure ExpressRoute existants

Si vous utilisez un circuit Azure ExpressRoute existant et souhaitez ajouter une connectivité Office 365 sur ce circuit, vous devez examiner le nombre de circuits, les emplacements de sortie et la taille des circuits pour vous assurer qu’ils répondent aux besoins de votre utilisation de Office 365. La plupart des clients ont besoin d’une bande passante supplémentaire et de nombreux circuits supplémentaires.
  
Pour permettre l’accès Office 365 sur vos circuits Azure ExpressRoute existants, configurez les filtres [d’itinéraire](/azure/expressroute/how-to-routefilter-portal) pour vous assurer que les services Office 365 sont accessibles.
  
L’abonnement Azure ExpressRoute est centrée sur les clients, ce qui signifie que les abonnements sont liés aux clients. En tant que client, vous pouvez avoir plusieurs circuits Azure ExpressRoute et accéder à de nombreuses ressources cloud Microsoft sur ces circuits. Par exemple, vous pouvez choisir d’accéder à une machine virtuelle hébergée par Azure, un client de test Office 365 et un client de production Office 365 sur une paire de circuits Azure ExpressRoute redondants.
  
Ce tableau décrit les deux types de relations d’homologue que vous pouvez choisir d’implémenter sur vos circuits.

|**Relation d’homologue**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Services** <br/> |IaaS : machines virtuelles Azure  <br/> |PaaS : services publics Azure  <br/> SaaS : Office 365  <br/> SaaS : Dynamics 365  <br/> |
|Initiation de la connexion**** <br/> |Client à Microsoft  <br/> Microsoft pour le client  <br/> |Client à Microsoft  <br/> Microsoft pour le client  <br/> |
|**Prise en charge de QoS** <br/> |Aucune QoS  <br/> |<sup>QoS1</sup> <br/> |

<sup>1 </sup> QoS prend en charge Skype Entreprise uniquement pour le moment.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planification de la bande passante pour Azure ExpressRoute

Chaque client Office 365 a des besoins de bande passante uniques en fonction du nombre de personnes à chaque emplacement, de leur niveau d’activité avec chaque application Office 365 et d’autres facteurs tels que l’utilisation de l’équipement local ou hybride et des configurations de sécurité réseau.
  
Une bande passante trop faible entraîne une congestion, des retransmissions de données et des retards imprévisibles. Le fait d’avoir trop de bande passante entraîne un coût inutile. Sur un réseau existant, la bande passante est souvent appelée en pourcentage la quantité d’espace disponible sur le circuit. Une espace d’en-tête de 10 % entraîne probablement une congestion et une espace d’en-tête de 80 % signifie généralement un coût inutile. Les allocations de cibles d’en-tête classiques sont de 20 % à 50 %.
  
Pour trouver le niveau de bande passante approprié, le meilleur mécanisme consiste à tester votre consommation réseau existante. C’est la seule façon d’obtenir une véritable mesure de l’utilisation et des besoins, car chaque configuration réseau et chaque application sont d’une certaine manière uniques. Lors de la mesure, vous devez prêter une attention particulière à la consommation totale de bande passante, à la latence et à la congestion TCP pour comprendre les besoins de votre réseau.
  
Une fois que vous avez une base de référence estimée qui inclut toutes les applications réseau, pilotez des Office 365 avec un petit groupe qui comprend les différents profils des personnes de votre organisation pour déterminer l’utilisation réelle et utilisez les deux mesures pour estimer la quantité de bande passante dont vous aurez besoin pour chaque emplacement de bureau. S’il existe des problèmes de latence ou de congestion TCP dans vos tests, vous devrez peut-être déplacer la sortie plus près des personnes à l’aide de Office 365 ou supprimer l’analyse réseau intensive telle que le déchiffrement/inspection SSL.
  
Toutes nos recommandations sur le type de traitement réseau recommandé s’appliquent aux circuits ExpressRoute et Internet. Il en va de même pour le reste des instructions sur notre [site d’optimisation des performances](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Application de contrôles de sécurité à Azure ExpressRoute pour Office 365 scénarios

La sécurisation de la connectivité Azure ExpressRoute commence par les mêmes principes que la sécurisation de la connectivité Internet. De nombreux clients choisissent de déployer des contrôles de réseau et de périmètre le long du chemin ExpressRoute connectant leur réseau local à Office 365 et autres clouds Microsoft. Ces contrôles peuvent inclure des pare-feu, des proxies d’application, la prévention des fuites de données, la détection des intrusions, des systèmes de prévention des intrusions, etc. Dans de nombreux cas, les clients appliquent différents niveaux de contrôles au trafic initié depuis l’local vers Microsoft, par rapport au trafic initié par Microsoft vers le réseau local du client, ou au trafic initié depuis l’local vers une destination Internet générale.
  
Voici quelques exemples d’intégration de la sécurité au modèle de connectivité [ExpressRoute](/azure/expressroute/expressroute-connectivity-models) que vous choisissez de déployer.

|**Option d’intégration ExpressRoute**|**Modèle de périmètre de sécurité réseau**|
|:-----|:-----|
|Colocation au niveau d’un échange cloud  <br/> |Installez une nouvelle infrastructure de sécurité/périmètre ou utilisez-la dans la fonctionnalité de colocation où la connexion ExpressRoute est établie.  <br/> Utilisez la fonction de colocation uniquement à des fins de routage/interconnectage et de retour des connexions de la colocation vers l’infrastructure de sécurité/périmètre locale.  <br/> |
|Ethernet de point à point  <br/> |Mettre fin à la connexion ExpressRoute de point à point dans l’emplacement d’infrastructure de sécurité/périmètre local existant.  <br/> Installez une nouvelle infrastructure de sécurité/périmètre spécifique au chemin ExpressRoute et terminez la connexion point à point à cet endroit.  <br/> |
|Tout-à-tout IPVPN  <br/> |Utilisez une infrastructure de sécurité/périmètre locale existante à tous les emplacements qui sortent du réseau IPVPN utilisé pour ExpressRoute pour la Office 365 réseau.  <br/> Épinglez l’adresse IPVPN utilisée pour ExpressRoute pour Office 365 à des emplacements locaux spécifiques désignés pour servir de sécurité/périmètre.  <br/> |

Certains fournisseurs de services offrent également des fonctionnalités de sécurité/périmètre gérées dans le cadre de leurs solutions d’intégration avec Azure ExpressRoute.
  
Lorsque vous envisagez de placer la topologie des options de périmètre de réseau/sécurité utilisées pour ExpressRoute pour Office 365 connexions, voici quelques considérations supplémentaires.
  
- Les contrôles de profondeur et de type réseau/sécurité peuvent avoir un impact sur les performances et l’évolutivité de l Office 365 utilisateur.

- Les flux sortants (locaux-Microsoft\>) et entrants (Microsoft\> local) [s’ils sont activés] peuvent avoir des exigences différentes. Ceux-ci sont probablement différents des destinations Internet générales sortantes.

- Office 365 requises pour les ports/protocoles et les sous-réseaux IP nécessaires sont les mêmes, que le trafic soit acheminé via ExpressRoute pour Office 365 ou via Internet.

- L’emplacement de premier plan des contrôles de sécurité/réseau du client détermine le réseau de bout en bout final entre l’utilisateur et le service Office 365 et peut avoir un impact significatif sur la latence et la congestion du réseau.

- Les clients sont encouragés à concevoir leur topologie de sécurité/périmètre à utiliser avec ExpressRoute pour Office 365 conformément aux meilleures pratiques en matière de redondance, de haute disponibilité et de récupération d’urgence.

Voici un exemple de Woodgrove Bank qui compare les différentes options de connectivité Azure ExpressRoute aux modèles de sécurité de périmètre mentionnés ci-dessus.
  
### <a name="example-1-securing-azure-expressroute"></a>Exemple 1 : sécurisation d’Azure ExpressRoute
  
Woodgrove Bank envisage d’implémenter Azure ExpressRoute et après avoir planifié l’architecture optimale pour le [routage avec ExpressRoute pour Office 365](routing-with-expressroute.md) et après avoir utilisé les instructions ci-dessus pour comprendre les besoins en bande passante, elle détermine la meilleure méthode pour sécuriser son périmètre.
  
Pour Woodgrove, une organisation internationale ayant des emplacements sur plusieurs continents, la sécurité doit englober tous les périmètres. L’option de connectivité optimale pour Woodgrove est une connexion à plusieurs points avec plusieurs emplacements d’pairage dans le monde entier pour répondre aux besoins de leurs employés sur chaque continent. Chaque continent inclut des circuits Azure ExpressRoute redondants sur le continent et la sécurité doit englober tous ces circuits.
  
L’infrastructure existante de Woodgrove est fiable et peut gérer le travail supplémentaire. Par conséquent, Woodgrove Bank est en mesure d’utiliser l’infrastructure pour sa sécurité Azure ExpressRoute et son périmètre Internet. Si ce n’était pas le cas, Woodgrove pourrait choisir d’acheter davantage d’équipements pour compléter son équipement existant ou pour gérer un autre type de connexion.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Haute disponibilité et failover avec Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Nous vous recommandons de mettre en service au moins deux circuits actifs de chaque sortie avec ExpressRoute vers votre fournisseur ExpressRoute. Il s’agit de l’endroit le plus courant où nous voyons des échecs pour les clients et vous pouvez facilement l’éviter en approvisionnement d’une paire de circuits ExpressRoute actifs/actifs. Nous vous recommandons également d’utiliser au moins deux circuits Internet actifs/actifs, car de nombreux services Office 365 sont disponibles uniquement sur Internet.
  
À l’intérieur du point de sortie de votre réseau se trouve de nombreux autres périphériques et circuits qui jouent un rôle essentiel dans la façon dont les personnes percevoir la disponibilité. Ces parties de vos scénarios de connectivité ne sont pas couvertes par les SSL ExpressRoute ou Office 365, mais elles jouent un rôle essentiel dans la disponibilité du service de bout en bout, telle qu’elle est perçue par les membres de votre organisation.
  
Concentrez-vous sur les personnes qui utilisent et utilisent les Office 365, si un échec d’un composant affecte l’expérience des utilisateurs utilisant le service, recherchez des moyens de limiter le pourcentage total de personnes affectées. Si un mode de failover est complexe sur le plan opérationnel, prenons en compte l’expérience des personnes qui ont longtemps été en récupération et recherchez des modes de récupération automatisés et simples d’un point de vue opérationnel.
  
En dehors de votre réseau, Office 365, ExpressRoute et votre fournisseur ExpressRoute ont tous différents niveaux de disponibilité.
  
### <a name="service-availability"></a>Disponibilité du service
  
- Office 365 services sont [couverts](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) par des contrats de niveau de service bien définis, qui incluent des mesures de disponibilité et de disponibilité pour des services individuels. Une des raisons Office 365 maintenir des niveaux de disponibilité de service aussi élevés est la possibilité pour des composants individuels de faire un pas en toute transparence entre les nombreux centres de données Microsoft, à l’aide du réseau Microsoft global. Ce failover s’étend du centre de données et du réseau aux points de sortie Internet multiples et permet le failover en toute transparence du point de vue des personnes qui utilisent le service.

- ExpressRoute [fournit un SLA de disponibilité de 99,9 %](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) sur des circuits dédiés individuels entre Microsoft Network Edge et le fournisseur ExpressRoute ou l’infrastructure partenaire. Ces niveaux de service sont appliqués au niveau du circuit ExpressRoute, qui se compose de deux [interconnexions indépendantes](/azure/expressroute/expressroute-introduction) entre l’équipement Microsoft redondant et l’équipement du fournisseur de réseau dans chaque emplacement d’homologue.

### <a name="provider-availability"></a>Disponibilité du fournisseur
  
- Les dispositions de niveau de service de Microsoft s’arrêtent chez votre fournisseur ou partenaire ExpressRoute. C’est également le premier endroit où vous pouvez faire des choix qui influenceront votre niveau de disponibilité. Vous devez évaluer attentivement les caractéristiques d’architecture, de disponibilité et de résilience que votre fournisseur ExpressRoute offre entre votre périmètre réseau et la connexion de vos fournisseurs à chaque emplacement d’homologue Microsoft. Portez une attention particulière aux aspects logiques et physiques de la redondance, de l’équipement d’homologue, des circuits wan fournis par l’opérateur et de toute valeur supplémentaire qui ajoute des services tels que des services NAT ou des pare-feu gérés.

### <a name="designing-your-availability-plan"></a>Conception de votre plan de disponibilité
  
Nous vous recommandons vivement de planifier et de concevoir une haute disponibilité et une résilience dans vos scénarios de connectivité de bout en bout pour Office 365. Une conception doit inclure ;
  
- Aucun point de défaillance unique, y compris les circuits Internet et ExpressRoute.

- Réduction du nombre de personnes affectées et de la durée de cet impact pour la plupart des modes d’échec anticipés.

- Optimisation pour un processus de récupération simple, répétable et automatique à partir des modes d’échec les plus attendus.

- Prise en charge des demandes complètes de votre trafic réseau et de vos fonctionnalités par le biais de chemins redondants, sans dégradation substantielle.

Vos scénarios de connectivité doivent inclure une topologie réseau optimisée pour plusieurs chemins d’accès réseau indépendants et actifs Office 365. Cela permet une meilleure disponibilité de bout en bout qu’une topologie optimisée uniquement pour la redondance au niveau de l’appareil ou de l’équipement.
  
> [!TIP]
> Si vos utilisateurs sont répartis sur plusieurs continents ou régions géographiques et que chacun de ces emplacements se connecte sur des circuits WAN redondants à un emplacement local unique où se trouve un seul circuit ExpressRoute, vos utilisateurs auront moins de disponibilité de service de bout en bout qu’une conception de topologie réseau qui inclut des circuits ExpressRoute indépendants qui connectent les différentes régions à l’emplacement d’homologue le plus proche.
  
Nous vous recommandons de mettre en service au moins deux circuits ExpressRoute avec chaque circuit qui se connecte avec un emplacement d’homologue géographique différent. Vous devez fournir cette paire active-active de circuits pour chaque région où les utilisateurs utiliseront la connectivité ExpressRoute pour Office 365 services. Cela permet à chaque région de rester connectée en cas d’urgence qui affecte un emplacement principal tel qu’un centre de données ou un emplacement d’homologue. Leur configuration en tant qu’actif/actif permet à l’utilisateur final de distribuer le trafic sur plusieurs chemins d’accès réseau. Cela réduit l’étendue des personnes affectées lors de pannes d’équipements réseau ou d’appareils.
  
Nous vous déconseillons d’utiliser un seul circuit ExpressRoute avec Internet comme sauvegarde.
  
### <a name="example-2-failover-and-high-availability"></a>Exemple 2 : failover et haute disponibilité
  
La conception multi-géographique de Woodgrove Bank a fait l’objet d’un examen du routage, de la bande passante, de la sécurité et doit maintenant faire l’objet d’un examen de haute disponibilité. Woodgrove pense que la haute disponibilité couvre trois catégories . résilience, fiabilité et redondance ;
  
La résilience permet à Woodgrove de récupérer rapidement après des défaillances. La fiabilité permet à Woodgrove d’offrir un résultat cohérent au sein du système. La redondance permet à Woodgrove de se déplacer entre une ou plusieurs instances d’infrastructure en miroir.
  
Dans chaque configuration edge, Woodgrove possède des pare-feux redondants, des proxies et des IDS. Pour l’Amérique du Nord, Woodgrove dispose d’une configuration edge dans son centre de données Dallas et d’une autre configuration edge dans son centre de données de Dallas. L’équipement redondant à chaque emplacement offre une résilience à cet emplacement.
  
La configuration réseau de Woodgrove Bank repose sur quelques principes clés :
  
- Dans chaque région géographique, il existe plusieurs circuits Azure ExpressRoute.

- Chaque circuit d’une région peut prendre en charge l’ensemble du trafic réseau au sein de cette région.

- Le routage préférera clairement l’un ou l’autre chemin d’accès en fonction de la disponibilité, de l’emplacement, etc.

- Le failover entre les circuits Azure ExpressRoute se produit automatiquement sans configuration ou action supplémentaire requise par Woodgrove.

- Le failover entre les circuits Internet se produit automatiquement sans configuration ou action supplémentaire requise par Woodgrove.

Dans cette configuration, avec une redondance au niveau physique et virtuel, Woodgrove Bank est en mesure d’offrir une résilience locale, une résilience régionale et une résilience globale de manière fiable. Woodgrove a choisi cette configuration après avoir évalué un seul circuit Azure ExpressRoute par région, ainsi que la possibilité de faire un pas vers Internet.
  
Si Woodgrove ne parvient pas à avoir plusieurs circuits Azure ExpressRoute par région, le routage du trafic provenant d’Amérique du Nord vers le circuit Azure ExpressRoute en Asie-Pacifique ajouterait un niveau inacceptable de latence et la configuration requise du forwardeur DNS ajouterait de la complexité.
  
L’utilisation d’Internet comme configuration de sauvegarde n’est pas recommandée. Cela rompt le principe de fiabilité de Woodgrove, ce qui entraîne une expérience incohérente d’utilisation de la connexion. En outre, la configuration manuelle serait nécessaire pour faire échouer l’étude des annonces BGP qui ont été configurées, de la configuration NAT, de la configuration DNS et de la configuration du proxy. Cette complexité ajoutée augmente le temps de récupération et réduit leur capacité à diagnostiquer et dépanner les étapes impliquées.
  
Vous avez toujours des questions sur la façon de planifier et d’implémenter la gestion du trafic ou Azure ExpressRoute ? Lisez le reste de notre [réseau et conseils sur les performances](./network-planning-and-performance.md) ou le [FAQ Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Travailler avec des fournisseurs Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Choisissez les emplacements de vos circuits en fonction de votre planification de la bande passante, de la latence, de la sécurité et de la haute disponibilité. Une fois que vous connaissez les emplacements optimaux, vous souhaitez placer des circuits pour examiner la [liste actuelle des fournisseurs par région](/azure/expressroute/expressroute-locations).
  
Travaillez avec votre fournisseur ou fournisseur pour sélectionner les meilleures options de connectivité, point à point, multi-point ou hébergé. N’oubliez pas que vous pouvez combiner et faire correspondre les options de connectivité tant que la bande passante et d’autres composants redondants peuvent prendre en charge votre conception de routage et de haute disponibilité.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Voir aussi
<a name="BKMK_high-availability"> </a>

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Utilisation de communautés BGP dans ExpressRoute pour Office 365 scénarios](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
  
[Points de terminaison Office 365 - FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)