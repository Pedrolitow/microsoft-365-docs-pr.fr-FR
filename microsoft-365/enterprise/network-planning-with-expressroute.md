---
title: Planification du réseau avec ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/14/2018
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
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
description: Dans cet article, vous allez découvrir Azure ExpressRoute pour Office 365 et comment l’utiliser pour la planification du réseau.
ms.openlocfilehash: 9ec6626bb84645557373fbf15c183fac708e8237
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68189778"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planification du réseau avec ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

ExpressRoute pour Office 365 fournit une connectivité de couche 3 entre votre réseau et les centres de données de Microsoft. Les circuits utilisent les annonces de routage BGP (Border Gateway Protocol) des serveurs frontaux de Office 365. Du point de vue de vos appareils locaux, lorsqu’ils doivent sélectionner le chemin TCP/IP approprié pour Office 365, Azure ExpressRoute est considéré comme une alternative à Internet.
  
Azure ExpressRoute ajoute un chemin d’accès direct à un ensemble spécifique de fonctionnalités et de services pris en charge qui sont proposés par Office 365 serveurs dans les centres de données de Microsoft. Azure ExpressRoute ne remplace pas la connectivité Internet aux centres de données Microsoft ou aux services Internet de base tels que la résolution de noms de domaine. Azure ExpressRoute et vos circuits Internet doivent être sécurisés et redondants.
  
Le tableau suivant met en évidence quelques différences entre les connexions Internet et Azure ExpressRoute dans le contexte de Office 365.

|**Différences dans la planification réseau**|**Connexion réseau Internet**|**Connexion réseau ExpressRoute**|
|:-----|:-----|:-----|
| Accès aux services Internet requis, y compris ;  <br/>  Résolution de noms DNS  <br/>  Vérification de la révocation de certificat  <br/>  Réseaux de distribution de contenu (CDN)  <br/> |Oui  <br/> |Les demandes adressées à l’infrastructure DNS et/ou CDN appartenant à Microsoft peuvent utiliser le réseau ExpressRoute.  <br/> |
| Accès aux services Office 365, y compris ;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Entreprise Online  <br/>  Office dans un navigateur  <br/>  portail Office 365 et authentification  <br/> |Oui, toutes les applications et fonctionnalités  <br/> |Oui, [applications et fonctionnalités spécifiques](./urls-and-ip-address-ranges.md) <br/> |
|Sécurité locale au périmètre.  <br/> |Oui  <br/> |Oui  <br/> |
|Planification de la haute disponibilité.  <br/> |Basculer vers une autre connexion réseau Internet  <br/> |Basculer vers une autre connexion ExpressRoute  <br/> |
|Connexion directe avec un profil réseau prévisible.  <br/> |Non  <br/> |Oui  <br/> |
|Connectivité IPv6.  <br/> |Oui  <br/> |Oui  <br/> |

Développez les titres ci-dessous pour obtenir des conseils de planification réseau supplémentaires.

## <a name="existing-azure-expressroute-customers"></a>Clients Azure ExpressRoute existants

Si vous utilisez un circuit Azure ExpressRoute existant et souhaitez ajouter Office 365 connectivité sur ce circuit, vous devez examiner le nombre de circuits, les emplacements de sortie et la taille des circuits pour vous assurer qu’ils répondent aux besoins de votre utilisation Office 365. La plupart des clients ont besoin d’une bande passante supplémentaire et beaucoup nécessitent plus de circuits.
  
Pour activer l’accès à Office 365 sur vos circuits Azure ExpressRoute [existants, configurez les filtres de routage](/azure/expressroute/how-to-routefilter-portal) pour vous assurer que les services Office 365 sont accessibles.
  
L’abonnement Azure ExpressRoute est centré sur le client, ce qui signifie que les abonnements sont liés aux clients. En tant que client, vous pouvez avoir plusieurs circuits Azure ExpressRoute et accéder à de nombreuses ressources cloud Microsoft sur ces circuits. Par exemple, vous pouvez choisir d’accéder à une machine virtuelle hébergée par Azure, à un locataire de test Office 365 et à un locataire de production Office 365 sur une paire de circuits Azure ExpressRoute redondants.
  
Ce tableau décrit les deux types de relations de peering que vous pouvez choisir d’implémenter sur vos circuits.

|**Relation de peering**|**Azure Private**|**Microsoft**|
|:-----|:-----|:-----|
|**Services** <br/> |IaaS : Azure Machines Virtuelles  <br/> |PaaS : services publics Azure  <br/> SaaS : Office 365  <br/> SaaS : Dynamics 365  <br/> |
|Initiation de connexion**** <br/> |Client à Microsoft  <br/> Microsoft à client  <br/> |Client à Microsoft  <br/> Microsoft à client  <br/> |
|**Prise en charge de QoS** <br/> |Aucun QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1 </sup> QoS prend en charge Skype Entreprise uniquement pour le moment.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planification de la bande passante pour Azure ExpressRoute

Chaque Office 365 client a des besoins de bande passante uniques en fonction du nombre de personnes à chaque emplacement, de leur activité avec chaque application Office 365 et d’autres facteurs tels que l’utilisation d’équipements locaux ou hybrides et de configurations de sécurité réseau.
  
Une bande passante trop faible entraîne une congestion, des retransmissions de données et des retards imprévisibles. Une bande passante trop importante entraîne des coûts inutiles. Sur un réseau existant, la bande passante est souvent appelée en pourcentage de la quantité d’espace disponible sur le circuit. Le fait d’avoir 10 % d’espace d’en-tête entraîne probablement une congestion et une marge de 80 % signifie généralement des coûts inutiles. Les allocations cibles de salle d’en-tête classiques sont comprises entre 20 % et 50 %.
  
Pour trouver le niveau de bande passante approprié, le meilleur mécanisme consiste à tester votre consommation réseau existante. Il s’agit de la seule façon d’obtenir une véritable mesure de l’utilisation et des besoins, car chaque configuration réseau et applications sont d’une certaine manière uniques. Lors de la mesure, vous devez prêter une attention particulière à la consommation totale de bande passante, à la latence et à la congestion TCP pour comprendre les besoins de votre réseau.
  
Une fois que vous avez une base de référence estimée qui inclut toutes les applications réseau, pilotez Office 365 avec un petit groupe qui comprend les différents profils des personnes de votre organisation pour déterminer l’utilisation réelle, et utilisez les deux mesures pour estimer la quantité de bande passante dont vous aurez besoin pour chaque emplacement de bureau. En cas de problèmes de latence ou de congestion TCP détectés dans vos tests, vous devrez peut-être rapprocher la sortie des personnes qui utilisent Office 365 ou supprimer l’analyse réseau intensive telle que le déchiffrement/inspection SSL.
  
Toutes nos recommandations sur le type de traitement réseau recommandé s’appliquent à la fois aux circuits ExpressRoute et Internet. Il en va de même pour le reste des conseils sur notre [site d’optimisation des performances](./network-planning-and-performance.md).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Application de contrôles de sécurité à Azure ExpressRoute pour Office 365 scénarios

La sécurisation de la connectivité Azure ExpressRoute commence par les mêmes principes que la sécurisation de la connectivité Internet. De nombreux clients choisissent de déployer des contrôles réseau et de périmètre le long du chemin ExpressRoute connectant leur réseau local à Office 365 et à d’autres clouds Microsoft. Ces contrôles peuvent inclure des pare-feu, des proxys d’application, la prévention des fuites de données, la détection des intrusions, les systèmes de prévention des intrusions, etc. Dans de nombreux cas, les clients appliquent différents niveaux de contrôles au trafic initié à partir d’un site local vers Microsoft, par rapport au trafic initié par Microsoft vers le réseau local du client, et au trafic initié à partir d’un site local vers une destination Internet générale.
  
Voici quelques exemples d’intégration de la sécurité au [modèle de connectivité ExpressRoute](/azure/expressroute/expressroute-connectivity-models) que vous choisissez de déployer.

|**Option d’intégration ExpressRoute**|**Modèle de périmètre de sécurité réseau**|
|:-----|:-----|
|Colocalisé lors d’un échange cloud  <br/> |Installez une nouvelle infrastructure de sécurité/périmètre existante ou utilisez-la dans l’installation de colocation où la connexion ExpressRoute est établie.  <br/> Utilisez l’installation de colocation uniquement à des fins de routage/interconnexion et de connexions de retour de l’installation de colocation vers l’infrastructure de sécurité/périmètre locale.  <br/> |
|Ethernet point à point  <br/> |Arrêtez la connexion ExpressRoute point à point dans l’emplacement de sécurité/d’infrastructure de périmètre local existant.  <br/> Installez une nouvelle infrastructure de sécurité/périmètre spécifique au chemin ExpressRoute et arrêtez la connexion point à point.  <br/> |
|IPVPN tout-à-n’importe quel  <br/> |Utilisez une infrastructure de sécurité/périmètre locale existante à tous les emplacements qui passent dans le IPVPN utilisé pour ExpressRoute pour Office 365 connectivité.  <br/> Épingler l’ADRESSE IPVPN utilisée pour ExpressRoute pour Office 365 à des emplacements locaux spécifiques désignés pour servir de sécurité/périmètre.  <br/> |

Certains fournisseurs de services offrent également des fonctionnalités de sécurité/périmètre gérées dans le cadre de leurs solutions d’intégration à Azure ExpressRoute.
  
Lorsque vous envisagez de placer la topologie des options de périmètre réseau/de sécurité utilisées pour ExpressRoute pour les connexions Office 365, voici quelques considérations supplémentaires
  
- La profondeur et le type des contrôles réseau/sécurité peuvent avoir un impact sur les performances et l’extensibilité de l’expérience utilisateur Office 365.

- Les flux sortants (locaux-Microsoft\>) et entrants (Microsoft locaux\>) [s’ils sont activés] peuvent avoir des exigences différentes. Celles-ci sont probablement différentes des destinations Internet générales.

- Office 365 exigences pour les ports/protocoles et les sous-réseaux IP nécessaires sont les mêmes, que le trafic soit routé via ExpressRoute pour Office 365 ou via Internet.

- Le positionnement topologique des contrôles de sécurité/réseau du client détermine le réseau final de bout en bout entre l’utilisateur et le service Office 365 et peut avoir un impact considérable sur la latence et la congestion du réseau.

- Les clients sont encouragés à concevoir leur topologie de sécurité/périmètre à utiliser avec ExpressRoute pour Office 365 conformément aux meilleures pratiques en matière de redondance, de haute disponibilité et de récupération d’urgence.

Voici un exemple de Contoso qui compare les différentes options de connectivité Azure ExpressRoute avec les modèles de sécurité de périmètre décrits ci-dessus.
  
### <a name="example-1-securing-azure-expressroute"></a>Exemple 1 : Sécurisation d’Azure ExpressRoute
  
Contoso envisage d’implémenter Azure ExpressRoute et après avoir planifié l’architecture optimale pour le [routage avec ExpressRoute pour Office 365](routing-with-expressroute.md) et après avoir utilisé les conseils ci-dessus pour comprendre les besoins en bande passante, ils déterminent la meilleure méthode pour sécuriser leur périmètre.
  
Pour Contoso, une organisation multinationale avec des emplacements sur plusieurs continents, la sécurité doit couvrir tous les périmètres. L’option de connectivité optimale pour Contoso est une connexion à plusieurs points avec plusieurs emplacements de peering dans le monde entier pour répondre aux besoins de leurs employés sur chaque continent. Chaque continent inclut des circuits Azure ExpressRoute redondants au sein du continent et la sécurité doit couvrir tous ces circuits.
  
L’infrastructure existante de Contoso est fiable et peut gérer le travail supplémentaire. Par conséquent, Contoso est en mesure d’utiliser l’infrastructure pour sa sécurité Azure ExpressRoute et le périmètre Internet. Si ce n’était pas le cas, Contoso pourrait choisir d’acheter plus d’équipement pour compléter son équipement existant ou pour gérer un autre type de connexion.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Haute disponibilité et basculement avec Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Nous vous recommandons d’approvisionner au moins deux circuits actifs à partir de chaque sortie avec ExpressRoute vers votre fournisseur ExpressRoute. Il s’agit de l’endroit le plus courant où nous voyons des défaillances pour les clients et vous pouvez facilement l’éviter en approvisionnant une paire de circuits ExpressRoute actifs/actifs. Nous vous recommandons également d’utiliser au moins deux circuits Internet actifs/actifs, car de nombreux services Office 365 sont disponibles uniquement sur Internet.
  
À l’intérieur du point de sortie de votre réseau se trouvent de nombreux autres appareils et circuits qui jouent un rôle essentiel dans la façon dont les gens perçoivent la disponibilité. Ces parties de vos scénarios de connectivité ne sont pas couvertes par ExpressRoute ni par les contrats SLA Office 365, mais elles jouent un rôle essentiel dans la disponibilité du service de bout en bout, comme le perçoivent les membres de votre organisation.
  
Concentrez-vous sur les personnes qui utilisent et fonctionnent Office 365, si une défaillance d’un composant affecte l’expérience des utilisateurs à l’aide du service, recherchez des moyens de limiter le pourcentage total de personnes affectées. Si un mode de basculement est complexe d’un point de vue opérationnel, tenez compte de l’expérience des utilisateurs pendant une longue période de récupération et recherchez des modes de basculement opérationnels simples et automatisés.
  
En dehors de votre réseau, Office 365, ExpressRoute et votre fournisseur ExpressRoute ont tous des niveaux de disponibilité différents.
  
### <a name="service-availability"></a>Disponibilité du service
  
- Office 365 services sont couverts par [des contrats de niveau de service](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) bien définis, qui incluent des métriques de temps d’activité et de disponibilité pour des services individuels. Une des raisons pour lesquelles Office 365 pouvez maintenir ces niveaux de haute disponibilité de service est la possibilité pour les composants individuels de basculer en toute transparence entre les nombreux centres de données Microsoft, à l’aide du réseau Microsoft global. Ce basculement s’étend du centre de données et du réseau aux points de sortie Internet multiples et permet le basculement en toute transparence du point de vue des utilisateurs du service.

- ExpressRoute [fournit un contrat SLA de disponibilité de 99,9 %](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) sur des circuits dédiés individuels entre Microsoft Network Edge et le fournisseur ExpressRoute ou l’infrastructure partenaire. Ces niveaux de service sont appliqués au niveau du circuit ExpressRoute, qui se compose de [deux interconnexions indépendantes](/azure/expressroute/expressroute-introduction) entre l’équipement Microsoft redondant et l’équipement du fournisseur de réseau dans chaque emplacement de peering.

### <a name="provider-availability"></a>Disponibilité du fournisseur
  
- Les arrangements de niveau de service de Microsoft s’arrêtent à votre fournisseur ou partenaire ExpressRoute. Il s’agit également du premier endroit où vous pouvez faire des choix qui influenceront votre niveau de disponibilité. Vous devez évaluer étroitement les caractéristiques d’architecture, de disponibilité et de résilience que votre fournisseur ExpressRoute offre entre votre périmètre réseau et la connexion de vos fournisseurs à chaque emplacement de peering Microsoft. Accordez une attention particulière aux aspects logiques et physiques de la redondance, de l’équipement de peering, des circuits WAN fournis par le transporteur et de toute valeur ajoutée supplémentaire, comme les services NAT ou les pare-feu managés.

### <a name="designing-your-availability-plan"></a>Conception de votre plan de disponibilité
  
Nous vous recommandons vivement de planifier et de concevoir la haute disponibilité et la résilience dans vos scénarios de connectivité de bout en bout pour Office 365. Une conception doit inclure ;
  
- Aucun point de défaillance unique, y compris les circuits Internet et ExpressRoute.

- Réduction du nombre de personnes affectées et de la durée de cet impact pour la plupart des modes d’échec prévus.

- Optimisation du processus de récupération simple, reproductible et automatique à partir des modes d’échec les plus attendus.

- Prise en charge des demandes complètes de votre trafic réseau et de vos fonctionnalités par le biais de chemins redondants, sans dégradation substantielle.

Vos scénarios de connectivité doivent inclure une topologie réseau optimisée pour plusieurs chemins d’accès réseau indépendants et actifs à Office 365. Cela donnera une meilleure disponibilité de bout en bout qu’une topologie optimisée uniquement pour la redondance au niveau de l’appareil ou de l’équipement individuel.
  
> [!TIP]
> Si vos utilisateurs sont répartis sur plusieurs continents ou régions géographiques et que chacun de ces emplacements se connecte via des circuits WAN redondants à un seul emplacement local où se trouve un circuit ExpressRoute unique, vos utilisateurs bénéficieront d’une disponibilité de service de bout en bout inférieure à une conception de topologie de réseau qui inclut des circuits ExpressRoute indépendants qui connectent les différentes régions à l’emplacement de peering le plus proche.
  
Nous vous recommandons d’approvisionner au moins deux circuits ExpressRoute avec chaque circuit connecté à un emplacement de peering géographique différent. Vous devez configurer cette paire active-active de circuits pour chaque région où les utilisateurs utiliseront la connectivité ExpressRoute pour Office 365 services. Cela permet à chaque région de rester connectée lors d’une catastrophe qui affecte un emplacement majeur tel qu’un centre de données ou un emplacement de peering. Leur configuration en tant qu’actif/actif permet de répartir le trafic des utilisateurs finaux entre plusieurs chemins d’accès réseau. Cela réduit l’étendue des personnes affectées en cas de pannes d’appareils ou d’équipements réseau.
  
Nous vous déconseillons d’utiliser un seul circuit ExpressRoute avec Internet comme sauvegarde.
  
### <a name="example-2-failover-and-high-availability"></a>Exemple 2 : basculement et haute disponibilité
  
La conception multi-géographique de Contoso a fait l’objet d’un examen du routage, de la bande passante, de la sécurité et doit maintenant faire l’objet d’une révision de haute disponibilité. Contoso considère la haute disponibilité comme couvrant trois catégories ; la résilience, la fiabilité et la redondance.
  
La résilience permet à Contoso de récupérer rapidement des défaillances. La fiabilité permet à Contoso d’offrir un résultat cohérent au sein du système. La redondance permet à Contoso de se déplacer entre une ou plusieurs instances d’infrastructure en miroir.
  
Dans chaque configuration de périphérie, Contoso dispose de pare-feu, proxys et IDS redondants. Pour Amérique du Nord, Contoso dispose d’une configuration de périphérie dans son centre de données Dallas et d’une autre configuration de périphérie dans son centre de données Virginia. L’équipement redondant à chaque emplacement offre une résilience à cet emplacement.
  
La configuration réseau de Contoso repose sur quelques principes clés :
  
- Dans chaque région géographique, il existe plusieurs circuits Azure ExpressRoute.

- Chaque circuit d’une région peut gérer tout le trafic réseau au sein de cette région.

- Le routage préférera clairement l’un ou l’autre chemin d’accès en fonction de la disponibilité, de l’emplacement, et ainsi de suite.

- Le basculement entre les circuits Azure ExpressRoute se produit automatiquement sans configuration ou action supplémentaire requise par Contoso.

- Le basculement entre les circuits Internet se produit automatiquement sans configuration ou action supplémentaire requise par Contoso.

Dans cette configuration, avec la redondance au niveau physique et virtuel, Contoso est en mesure d’offrir une résilience locale, une résilience régionale et une résilience globale de manière fiable. Contoso a choisi cette configuration après avoir évalué un seul circuit Azure ExpressRoute par région, ainsi que la possibilité de basculer vers Internet.
  
Si Contoso ne pouvait pas avoir plusieurs circuits Azure ExpressRoute par région, le routage du trafic provenant de Amérique du Nord vers le circuit Azure ExpressRoute en Asie-Pacifique ajouterait un niveau inacceptable de latence et la configuration du redirecteur DNS requise ajoute de la complexité.
  
L’utilisation d’Internet comme configuration de sauvegarde n’est pas recommandée. Cela rompt le principe de fiabilité de Contoso, ce qui entraîne une expérience incohérente à l’aide de la connexion. En outre, une configuration manuelle serait nécessaire pour basculer en tenant compte des publicités BGP qui ont été configurées, de la configuration NAT, de la configuration DNS et de la configuration du proxy. Cette complexité de basculement supplémentaire augmente le temps de récupération et réduit leur capacité à diagnostiquer et à dépanner les étapes impliquées.
  
Vous avez encore des questions sur la façon de planifier et d’implémenter la gestion du trafic ou Azure ExpressRoute ? Lisez le reste de nos [conseils sur le réseau et les performances](./network-planning-and-performance.md) ou le [FAQ Azure ExpressRoute](/azure/expressroute/expressroute-faqs).
  
## <a name="working-with-azure-expressroute-providers"></a>Utilisation des fournisseurs Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Choisissez les emplacements de vos circuits en fonction de la bande passante, de la latence, de la sécurité et de la planification de la haute disponibilité. Une fois que vous connaissez les emplacements optimaux, vous souhaitez placer les circuits [passer en revue la liste actuelle des fournisseurs par région](/azure/expressroute/expressroute-locations).
  
Collaborez avec votre fournisseur ou fournisseur pour sélectionner les meilleures options de connectivité, point à point, multipoint ou hébergée. N’oubliez pas que vous pouvez combiner et faire correspondre les options de connectivité tant que la bande passante et d’autres composants redondants prennent en charge votre conception de routage et de haute disponibilité.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/planningexpressroute365]()
  
## <a name="related-topics"></a>Rubriques connexes
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