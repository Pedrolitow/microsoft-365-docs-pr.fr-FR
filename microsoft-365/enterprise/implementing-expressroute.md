---
title: Implémentation d’ExpressRoute pour Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: Découvrez comment implémenter ExpressRoute pour Office 365, qui fournit un autre chemin de routage à de nombreux services Office 365 accessibles sur Internet.
ms.openlocfilehash: d577a30d97630b32fa080c9d17620b429562c5df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090360"
---
# <a name="implementing-expressroute-for-office-365"></a>Implémentation d’ExpressRoute pour Office 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

ExpressRoute pour Office 365 fournit un autre chemin d’accès de routage à de nombreux services Office 365 accessibles sur Internet. L’architecture d’ExpressRoute pour Office 365 est basée sur la publicité des préfixes d’adresses IP publiques de Office 365 services qui sont déjà accessibles via Internet dans vos circuits ExpressRoute approvisionnés pour une redistribution ultérieure de ces préfixes IP dans votre réseau. Avec ExpressRoute, vous activez efficacement plusieurs chemins de routage différents, via Internet et ExpressRoute, pour de nombreux services Office 365. Cet état de routage sur votre réseau peut représenter une modification significative de la façon dont votre topologie de réseau interne est conçue.
  
 **Statut:** Guide complet v2
  
Vous devez planifier soigneusement votre ExpressRoute pour Office 365 implémentation afin de prendre en compte les complexités réseau liées à la disponibilité du routage via un circuit dédié avec des itinéraires injectés dans votre réseau principal et Sur Internet. Si vous et votre équipe n’effectuez pas la planification et les tests détaillés dans ce guide, il existe un risque élevé de perte intermittente ou totale de connectivité aux services Office 365 lorsque le circuit ExpressRoute est activé.
  
Pour réussir l’implémentation, vous devez analyser les exigences de votre infrastructure, passer par une évaluation et une conception détaillées du réseau, planifier soigneusement le déploiement de manière intermédiaire et contrôlée, et créer un plan de validation et de test détaillé. Pour un environnement distribué volumineux, il n’est pas rare de voir les implémentations s’étendre sur plusieurs mois. Ce guide est conçu pour vous aider à planifier à l’avance.
  
La planification des déploiements à grande échelle peut prendre six mois et inclure souvent des membres de l’équipe de nombreux domaines de l’organisation, notamment les administrateurs de réseau, de pare-feu et de serveur proxy, les administrateurs Office 365, la sécurité, le support des utilisateurs finaux, la gestion de projet et le parrainage exécutif. Votre investissement dans le processus de planification réduit la probabilité que vous rencontrez des échecs de déploiement entraînant un temps d’arrêt ou un dépannage complexe et coûteux.
  
Nous nous attendons à ce que les prérequis suivants soient remplis avant le démarrage de ce guide d’implémentation.
  
1. Vous avez effectué une évaluation réseau pour déterminer si ExpressRoute est recommandé et approuvé.

2. Vous avez sélectionné un fournisseur de services réseau ExpressRoute. Recherchez des détails sur les [partenaires ExpressRoute et les emplacements de peering](/azure/expressroute/expressroute-locations).

3. Vous avez déjà lu et compris la [documentation ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) et votre réseau interne est en mesure de répondre aux prérequis d’ExpressRoute de bout en bout.

4. Votre équipe a lu tous les conseils publics et la documentation sur [https://aka.ms/expressrouteoffice365](./azure-expressroute.md)[https://aka.ms/ert](https://aka.ms/ert), et a regardé la série [Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer) sur Channel 9 afin d’acquérir une compréhension des détails techniques critiques, notamment :

      - Dépendances Internet des services SaaS.

      - Comment éviter les itinéraires asymétriques et gérer un routage complexe.

      - Comment incorporer des contrôles de sécurité, de disponibilité et de niveau application de périmètre.

## <a name="begin-by-gathering-requirements"></a>Commencez par collecter les exigences
<a name="requirements"> </a>

Commencez par déterminer les fonctionnalités et services que vous envisagez d’adopter au sein de votre organisation. Vous devez déterminer les fonctionnalités des différents services Office 365 seront utilisées et les emplacements sur votre réseau qui hébergeront des personnes utilisant ces fonctionnalités. Avec le catalogue de scénarios, vous devez ajouter les attributs réseau dont chacun de ces scénarios a besoin ; tels que les flux de trafic réseau entrant et sortant et si les points de terminaison Office 365 sont disponibles sur ExpressRoute ou non.
  
Pour rassembler les exigences de votre organisation :
  
- Cataloguez le trafic réseau entrant et sortant pour les services Office 365 que votre organisation utilise. Consultez Office 365 page URL et plages d’adresses IP pour obtenir la description des flux requis par différents scénarios Office 365.

- Collectez la documentation de la topologie de réseau existante montrant les détails de votre réseau principal et de votre topologie réseau internes, la connectivité des sites satellites, la connectivité utilisateur du dernier mille, le routage vers les points de sortie de périmètre réseau et les services proxy.

  - Identifiez les points de terminaison de service entrants sur les diagrammes réseau auxquels Office 365 et d’autres services Microsoft se connecteront, montrant à la fois les chemins de connexion Internet et ExpressRoute proposés.

  - Identifiez tous les emplacements d’utilisateur géographique et la connectivité WAN entre les emplacements, ainsi que les emplacements qui ont actuellement une sortie vers Internet et les emplacements proposés pour avoir une sortie vers un emplacement de peering ExpressRoute.

  - Identifiez tous les appareils périphériques, tels que les proxys, les pare-feu, etc., et cataloguez leur relation avec les flux qui transitent par Internet et ExpressRoute.

  - Indiquez si les utilisateurs finaux accèderont à Office 365 services via le routage direct ou le proxy d’application indirect pour les flux Internet et ExpressRoute.

- Ajoutez l’emplacement de votre locataire et des emplacements de réunion à votre diagramme de réseau.

- Estimer les caractéristiques de performance et de latence réseau attendues et observées des principaux emplacements utilisateur à Office 365. N’oubliez pas que Office 365 est un ensemble global et distribué de services et que les utilisateurs se connectent à des emplacements qui peuvent être différents de l’emplacement de leur locataire. Pour cette raison, il est recommandé de mesurer et d’optimiser la latence entre l’utilisateur et le bord le plus proche du réseau mondial Microsoft via ExpressRoute et les connexions Internet. Vous pouvez utiliser vos résultats de l’évaluation réseau pour faciliter cette tâche.

- Répertorie les exigences de sécurité réseau et de haute disponibilité de l’entreprise qui doivent être satisfaites avec la nouvelle connexion ExpressRoute. Par exemple, comment les utilisateurs continuent-ils à accéder à Office 365 en cas de sortie Internet ou d’échec du circuit ExpressRoute?

- Indiquez quels flux réseau entrants et sortants Office 365 utiliseront le chemin d’accès Internet et qui utiliseront ExpressRoute. Les spécificités des emplacements géographiques de vos utilisateurs et les détails de votre topologie de réseau local peuvent nécessiter que le plan soit différent d’un emplacement utilisateur à un autre.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Cataloguer votre trafic réseau sortant et entrant
<a name="trafficCatalog"> </a>

Pour réduire le routage et d’autres complexités réseau, nous vous recommandons d’utiliser ExpressRoute uniquement pour Office 365 pour les flux de trafic réseau qui sont nécessaires pour passer par une connexion dédiée en raison des exigences réglementaires ou à la suite de l’évaluation du réseau. En outre, nous vous recommandons d’organiser l’étendue du routage ExpressRoute et d’aborder les flux de trafic réseau sortants et entrants en tant qu’étapes différentes et distinctes du projet d’implémentation. Déployer ExpressRoute pour Office 365 uniquement pour les flux de trafic réseau sortant initiés par l’utilisateur et laisser les flux de trafic réseau entrants sur Internet peut aider à contrôler l’augmentation de la complexité topologique et les risques liés à l’introduction de possibilités de routage asymétrique supplémentaires.
  
Votre catalogue de trafic réseau doit contenir des listes de toutes les connexions réseau entrantes et sortantes que vous aurez entre votre réseau local et Microsoft.
  
- Les flux de trafic réseau sortant sont tous les scénarios dans lesquels une connexion est initiée à partir de votre environnement local, par exemple à partir de clients ou serveurs internes, avec une destination du services Microsoft. Ces connexions peuvent être directes à Office 365 ou indirectes, par exemple lorsque la connexion passe par des serveurs proxy, des pare-feu ou d’autres périphériques réseau sur le chemin d’accès à Office 365.

- Les flux de trafic réseau entrant sont tous les scénarios où une connexion est initiée à partir du cloud Microsoft vers un hôte local. Ces connexions doivent généralement passer par le pare-feu et d’autres infrastructures de sécurité requises par la stratégie de sécurité du client pour les flux provenant de l’extérieur.

Lisez la section **Assurer la symétrie des itinéraires** de l’article [Routage avec ExpressRoute pour Office 365 afin](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) de déterminer les services qui envoient le trafic entrant et recherchez la colonne marquée **ExpressRoute pour Office 365** dans l’article de référence [des points](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) de terminaison Office 365 pour déterminer le reste des informations de connectivité.
  
Pour chaque service qui nécessite une connexion sortante, vous devez décrire la connectivité planifiée pour le service, notamment le routage réseau, la configuration du proxy, l’inspection des paquets et les besoins en bande passante.
  
Pour chaque service qui nécessite une connexion entrante, vous aurez besoin d’informations supplémentaires. Les serveurs dans le cloud Microsoft établissent des connexions à votre réseau local. Pour vous assurer que les connexions sont établies correctement, vous devez décrire tous les aspects de cette connectivité, y compris ; les entrées DNS publiques pour les services qui acceptent ces connexions entrantes, les adresses IP IPv4 au format CIDR, l’équipement ISP impliqué et la façon dont nat entrant ou NAT source est géré pour ces connexions.
  
Les connexions entrantes doivent être examinées, qu’elles se connectent via Internet ou ExpressRoute pour garantir que le routage asymétrique n’a pas été introduit. Dans certains cas, les points de terminaison locaux auxquels Office 365 services lancent des connexions entrantes peuvent également être accessibles par d’autres microsoft et non services Microsoft. Il est primordial que l’activation du routage ExpressRoute vers ces services à des fins Office 365 ne brise pas d’autres scénarios. Dans de nombreux cas, les clients peuvent avoir besoin d’implémenter des modifications spécifiques à leur réseau interne, telles que la NAT basée sur la source, pour s’assurer que les flux entrants de Microsoft restent symétriques une fois ExpressRoute activé.
  
Voici un exemple du niveau de détail requis. Dans ce cas, Exchange hybride routerait vers le système local via ExpressRoute. 

|Connection, propriété   |Valeur  |
|----------|-----------|
|**Direction du trafic réseau** <br/> |Entrant  <br/> |
|**Service** <br/> |Environnement Exchange hybride  <br/> |
|**Point de terminaison Office 365 public (source)** <br/> |Exchange Online (adresses IP)  <br/> |
|**Point de terminaison local public (destination)** <br/> |5.5.5.5  <br/> |
|**Entrée DNS publique (Internet)** <br/> |Autodiscover.contoso.com  <br/> |
|**Ce point de terminaison local sera-t-il utilisé par d’autres services Microsoft (non Office 365) ?** <br/> |Non  <br/> |
|**Ce point de terminaison local sera-t-il utilisé par les utilisateurs/systèmes sur Internet ?** <br/> |Oui  <br/> |
|**Systèmes internes publiés via des points de terminaison publics** <br/> |Exchange Server rôle d’accès client (local) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Publication IP du point de terminaison public** <br/> |**Vers Internet** : 5.5.0.0/16 **Vers ExpressRoute** : 5.5.5.0/24  <br/> |
|**Contrôles de sécurité/périmètre** <br/> |**Chemin d’accès Internet** : DeviceID_002  **chemin ExpressRoute** : DeviceID_003  <br/> |
|**Haute disponibilité** <br/> |Actif/actif sur 2 circuits géoredondants /ExpressRoute - Chicago et Dallas  <br/> |
|**Contrôle de symétrie du chemin d’accès** <br/> |**Méthode** : **chemin Internet** NAT source : connexions entrantes NAT sources à 192.168.5.5 **Chemin ExpressRoute** : connexions NAT sources à 192.168.1.0 (Chicago) et 192.168.2.0 (Dallas)  <br/> |

Voici un exemple de service sortant uniquement :

|**Connection, propriété**|**Valeur**|
|----------|-----------|
|**Direction du trafic réseau** <br/> |Sortant  <br/> |
|**Service** <br/> |SharePoint Online  <br/> |
|**Point de terminaison local (source)** <br/> |Station de travail utilisateur  <br/> |
|**Point de terminaison Office 365 public (destination)** <br/> |SharePoint Online (adresses IP)  <br/> |
|**Entrée DNS publique (Internet)** <br/> |\*.sharepoint.com (et plus de noms de domaine complets)  <br/> |
|**références CDN** <br/> |cdn.sharepointonline.com (et plus de noms de domaine complets) : adresses IP gérées par CDN fournisseurs)  <br/> |
|**Publication IP et NAT en usage** <br/> |**Chemin Internet/NAT source** : 1.1.1.0/24  <br/> **Chemin ExpressRoute/NAT source** : 1.1.2.0/24 (Chicago) et 1.1.3.0/24 (Dallas)  <br/> |
|**Méthode de connectivité** <br/> |**Internet** : via le proxy de couche 7 (fichier .pac)  <br/> **ExpressRoute** : routage direct (aucun proxy)  <br/> |
|**Contrôles de sécurité/périmètre** <br/> |**Chemin Internet** : DeviceID_002  <br/> **Chemin ExpressRoute** : DeviceID_003  <br/> |
|**Haute disponibilité** <br/> |**Chemin Internet** : sortie Internet redondante  <br/> **Chemin ExpressRoute** : Routage actif/actif sur 2 circuits ExpressRoute géoredondants - Chicago et Dallas  <br/> |
|**Contrôle de symétrie du chemin d’accès** <br/> |**Méthode** : NAT source pour toutes les connexions  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Conception de votre topologie de réseau avec connectivité régionale
<a name="topology"> </a>

Une fois que vous avez compris les services et leurs flux de trafic réseau associés, vous pouvez créer un diagramme réseau qui intègre ces nouvelles exigences de connectivité et illustre les modifications que vous allez apporter pour utiliser ExpressRoute pour Office 365. Votre diagramme doit inclure :
  
1. Tous les emplacements utilisateur à partir desquels Office 365 et d’autres services sont accessibles.

2. Tous les points de sortie Internet et ExpressRoute.

3. Tous les appareils sortants et entrants qui gèrent la connectivité à l’entrée et à l’extérieur du réseau, y compris les routeurs, les pare-feu, les serveurs proxy d’application et la détection/prévention des intrusions.

4. Destinations internes pour tout le trafic entrant, telles que les serveurs ADFS internes qui acceptent les connexions à partir des serveurs proxy d’application web ADFS.

5. Catalogue de tous les sous-réseaux IP qui seront publiés

6. Identifiez chaque emplacement à partir duquel les personnes accèderont à Office 365 et répertoriez les emplacements de rencontre qui seront utilisés pour ExpressRoute.

7. Emplacements et parties de votre topologie de réseau interne, où les préfixes IP Microsoft appris à partir d’ExpressRoute seront acceptés, filtrés et propagés.

8. La topologie de réseau doit illustrer l’emplacement géographique de chaque segment de réseau et la façon dont il se connecte au réseau Microsoft via ExpressRoute et/ou Internet.

Le diagramme ci-dessous montre chaque emplacement où les utilisateurs utiliseront Office 365, ainsi que les annonces de routage entrant et sortant vers Office 365.
  
![Rencontre géographique régionale ExpressRoute.](../media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Pour le trafic sortant, les personnes accèdent Office 365 de l’une des trois manières suivantes :
  
1. Grâce à un lieu de rencontre à Amérique du Nord pour les habitants de Californie.

2. Grâce à un lieu de rencontre à Hong Kong pour les gens de Hong Kong.

3. Par le biais d’Internet au Bangladesh où il y a moins de personnes et aucun circuit ExpressRoute approvisionné.

![Connexions sortantes pour le diagramme régional.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
De même, le trafic réseau entrant provenant de Office 365 retourne de l’une des trois manières suivantes :
  
1. Grâce à un lieu de rencontre à Amérique du Nord pour les habitants de Californie.

2. Grâce à un lieu de rencontre à Hong Kong pour les gens de Hong Kong.

3. Par le biais d’Internet au Bangladesh où il y a moins de personnes et aucun circuit ExpressRoute approvisionné.

![Connexions entrantes pour le diagramme régional.](../media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Déterminer l’emplacement de rencontre approprié

La sélection des emplacements de rencontre, qui sont l’emplacement physique où votre circuit ExpressRoute connecte votre réseau au réseau Microsoft, est influencée par les emplacements à partir desquels les utilisateurs accèderont à Office 365. En tant qu’offre SaaS, Office 365 ne fonctionne pas sous le modèle régional IaaS ou PaaS de la même façon qu’Azure. Au lieu de cela, Office 365 est un ensemble distribué de services de collaboration, où les utilisateurs peuvent avoir besoin de se connecter à des points de terminaison dans plusieurs centres de données et régions, qui peuvent ne pas nécessairement se trouver dans le même emplacement ou la même région où le locataire de l’utilisateur est hébergé.
  
Cela signifie que la considération la plus importante que vous devez prendre en compte lors de la sélection d’emplacements de réunion pour ExpressRoute pour Office 365 est l’endroit où les membres de votre organisation se connectent. La recommandation générale pour une connectivité optimale Office 365 est d’implémenter le routage, afin que les demandes des utilisateurs à Office 365 services soient transmises au réseau Microsoft via le chemin d’accès réseau le plus court, ce qui est également souvent appelé routage « hot potato ». Par exemple, si la plupart des utilisateurs Office 365 se trouvent dans un ou deux emplacements, la sélection d’emplacements de réunion situés à proximité de l’emplacement de ces utilisateurs crée la conception optimale. Si votre entreprise a de grandes populations d’utilisateurs dans de nombreuses régions différentes, vous pouvez envisager d’avoir plusieurs circuits ExpressRoute et des emplacements de rencontre. Pour certains de vos emplacements utilisateur, le chemin d’accès le plus court/le plus optimal au réseau Microsoft et Office 365, peut ne pas être via vos points de rencontre réseau internes et ExpressRoute, mais via Internet.
  
Il existe souvent plusieurs emplacements de réunion qui peuvent être sélectionnés dans une région avec une proximité relative avec vos utilisateurs. Renseignez le tableau suivant pour guider vos décisions.

**Lieux de rencontre ExpressRoute planifiés en Californie et à New York**

|Emplacement  <br/> |Nombre de personnes  <br/> |Latence attendue pour le réseau Microsoft via la sortie Internet  <br/> |Latence attendue pour le réseau Microsoft via ExpressRoute  <br/> |
|----------|-----------|----------|-----------|
|Los Angeles  <br/> |10 000  <br/> |~15 ms  <br/> |~10ms (via silicon valley)  <br/> |
|Washington DC  <br/> |15 000  <br/> |~20 ms  <br/> |~10ms (via New York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~15 ms  <br/> |~40ms (via New York)  <br/> |

Une fois que l’architecture réseau globale montrant la région Office 365, les emplacements de réunion du fournisseur de services réseau ExpressRoute et la quantité de personnes par emplacement ont été développées, il peut être utilisé pour identifier si des optimisations peuvent être effectuées. Il peut également afficher les connexions réseau d’épingle à cheveux globales où le trafic achemine vers un emplacement distant afin d’obtenir l’emplacement de rencontre-moi. Si une épingle à cheveux sur le réseau mondial est découverte, elle doit être corrigée avant de continuer. Trouvez un autre emplacement de rencontre ou utilisez des points de sortie de sortie Internet sélectifs pour éviter l’épingle à cheveux.
  
Le premier diagramme montre un exemple de client avec deux emplacements physiques dans Amérique du Nord. Vous pouvez voir les informations sur les emplacements des bureaux, les Office 365 les emplacements des locataires et plusieurs choix pour les emplacements de réunion ExpressRoute. Dans cet exemple, le client a sélectionné l’emplacement de la réunion en fonction de deux principes, dans l’ordre :
  
1. Proximité la plus proche des personnes de leur organisation.

2. Le plus proche à proximité d’un centre de données Microsoft où Office 365 est hébergé.

![ExpressRoute US geographic meet-me.](../media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
En développant ce concept un peu plus loin, le deuxième diagramme montre un exemple de client multi-national confronté à des informations et à des prises de décision similaires. Ce client a un petit bureau au Bangladesh avec seulement une petite équipe de dix personnes qui se sont concentrées sur l’augmentation de leur empreinte dans la région. Il y a un point de rencontre à Chennai et un centre de données Microsoft avec Office 365 hébergé à Chennai, donc un emplacement de rencontre serait logique ; toutefois, pour dix personnes, la dépense du circuit supplémentaire est lourde. Lorsque vous examinez votre réseau, vous devez déterminer si la latence impliquée dans l’envoi de votre trafic réseau sur votre réseau est plus efficace que de dépenser le capital pour acquérir un autre circuit ExpressRoute.
  
Les dix personnes au Bangladesh peuvent également bénéficier de meilleures performances avec leur trafic réseau envoyé via Internet vers le réseau Microsoft qu’elles ne le feraient sur leur réseau interne, comme nous l’avons montré dans les diagrammes d’introduction et reproduits ci-dessous.
  
![Connexions sortantes pour le diagramme régional.](../media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Créer votre plan d’implémentation ExpressRoute pour Office 365
<a name="implementation"> </a>

Votre plan d’implémentation doit inclure à la fois les détails techniques de la configuration d’ExpressRoute et les détails de la configuration de toute l’autre infrastructure sur votre réseau, tels que les éléments suivants.
  
- Planifiez les services répartis entre ExpressRoute et Internet.

- Planifiez la bande passante, la sécurité, la haute disponibilité et le basculement.

- Concevoir le routage entrant et sortant, y compris les optimisations de chemin d’accès de routage appropriées pour différents emplacements

- Déterminez la distance à laquelle les itinéraires ExpressRoute seront publiés dans votre réseau et quel est le mécanisme permettant aux clients de sélectionner le chemin d’accès Internet ou ExpressRoute ; par exemple, le routage direct ou le proxy d’application.

- Planifiez les modifications d’enregistrement DNS, y compris les entrées [de l’infrastructure de stratégie de l’expéditeur](../security/office-365-security/set-up-spf-in-office-365-to-help-prevent-spoofing.md) .

- Planifier la stratégie NAT, y compris nat source sortante et entrante.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planifier votre routage avec des chemins d’accès réseau Internet et ExpressRoute
<a name="paths"> </a>

- Pour votre déploiement initial, tous les services entrants, tels que la messagerie entrante ou la connectivité hybride, sont recommandés pour utiliser Internet.

- Planifiez le routage LAN client de l’utilisateur final, tel que [la configuration d’un fichier PAC/WPAD, un](./managing-office-365-endpoints.md) itinéraire par défaut, des serveurs proxy et des annonces de routage BGP.

- Planifiez le routage de périmètre, notamment les serveurs proxy, les pare-feu et les proxys cloud.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planifier la bande passante, la sécurité, la haute disponibilité et le basculement
<a name="availability"> </a>

Créez un plan pour la bande passante requise pour chaque charge de travail Office 365 majeure. Estimer séparément les besoins en bande passante Exchange Online, SharePoint Online et Skype Entreprise Online. Vous pouvez utiliser les calculatrices d’estimation que nous avons fournies pour Exchange Online et Skype Entreprise comme point de départ. Toutefois, un test pilote avec un échantillon représentatif des profils utilisateur et des emplacements est nécessaire pour bien comprendre les besoins en bande passante de votre organisation.
  
Ajoutez la façon dont la sécurité est gérée à chaque emplacement de sortie Internet et ExpressRoute à votre plan. N’oubliez pas toutes les connexions ExpressRoute pour Office 365 utiliser le peering public et devez toujours être sécurisée conformément aux stratégies de sécurité de votre entreprise de connexion à des réseaux externes.
  
Ajoutez des détails à votre plan sur les personnes qui seront affectées par le type de panne et la façon dont ces personnes seront en mesure d’effectuer leur travail à pleine capacité de la manière la plus simple.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planifier les exigences de bande passante, notamment les exigences de Skype Entreprise sur jitter, latence, congestion et headroom
  
Skype Entreprise Online a également des exigences réseau supplémentaires spécifiques, qui sont détaillées dans l’article [Media Quality and Network Connectivity Performance in Skype Entreprise Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Lisez la section Planification de la **bande passante pour Azure ExpressRoute** dans [la planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Lorsque vous effectuez une évaluation de la bande passante avec vos utilisateurs pilotes, vous pouvez utiliser notre guide ; [Office 365 réglage des performances à l’aide de lignes de base et de l’historique des performances](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planifier les exigences de haute disponibilité
  
Créez un plan de haute disponibilité pour répondre à vos besoins et incorporez-le dans votre diagramme de topologie réseau mis à jour. Lisez la section **Haute disponibilité et basculement avec Azure ExpressRoute** dans [la planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planifier les exigences de sécurité réseau
  
Créez un plan pour répondre à vos exigences de sécurité réseau et incorporez-le dans votre diagramme de topologie réseau mis à jour. Lisez la section **Application de contrôles de sécurité à Azure ExpressRoute pour Office 365 scénarios** de [planification réseau avec ExpressRoute pour Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Concevoir une connectivité de service sortant
<a name="outbound"> </a>

ExpressRoute pour Office 365 a des exigences réseau *sortantes* qui peuvent ne pas être familières. Plus précisément, les adresses IP qui représentent vos utilisateurs et réseaux pour Office 365 et agir comme points de terminaison sources pour les connexions réseau sortantes à Microsoft doivent respecter des exigences spécifiques décrites ci-dessous.
  
1. Les points de terminaison doivent être des adresses IP publiques, inscrites auprès de votre entreprise ou auprès d’un opérateur qui vous fournit une connectivité ExpressRoute.

2. Les points de terminaison doivent être publiés sur Microsoft et validés/acceptés par ExpressRoute.

3. Les points de terminaison ne doivent pas être publiés sur Internet avec la même métrique de routage préférée ou plus.

4. Les points de terminaison ne doivent pas être utilisés pour la connectivité aux services Microsoft qui ne sont pas configurés sur ExpressRoute.

Si votre conception réseau ne répond pas à ces exigences, il existe un risque élevé que vos utilisateurs rencontrent des échecs de connectivité à Office 365 et à d’autres services Microsoft en raison d’un holage noir de route ou d’un routage asymétrique. Cela se produit lorsque les demandes d’services Microsoft sont routées via ExpressRoute, mais que les réponses sont routées sur Internet, ou inversement, et que les réponses sont supprimées par des périphériques réseau avec état tels que des pare-feu.
  
La méthode la plus courante que vous pouvez utiliser pour répondre aux exigences ci-dessus consiste à utiliser la nat source, implémentée dans le cadre de votre réseau ou fournie par votre opérateur ExpressRoute. La nat source vous permet d’extraire les détails et l’adressage IP privé de votre réseau Internet à partir d’ExpressRoute et ; associés à des annonces de routage IP appropriées, fournissent un mécanisme simple pour garantir la symétrie du chemin d’accès. Si vous utilisez des appareils réseau avec état spécifiques aux emplacements de peering ExpressRoute, vous devez implémenter des pools NAT distincts pour chaque peering ExpressRoute pour garantir la symétrie du chemin d’accès.
  
En savoir plus sur les [exigences NAT d’ExpressRoute](/azure/expressroute/expressroute-nat).
  
Ajoutez les modifications de la connectivité sortante au diagramme de topologie réseau.
  
### <a name="design-inbound-service-connectivity"></a>Concevoir une connectivité de service entrant
<a name="inbound"> </a>

La plupart des déploiements de Office 365 d’entreprise supposent une certaine forme de connectivité entrante entre les Office 365 et les services locaux, par exemple pour les Exchange, les SharePoint et Skype Entreprise scénarios hybrides, les migrations de boîtes aux lettres et l’authentification à l’aide de l’infrastructure ADFS. Quand ExpressRoute vous activez un chemin de routage supplémentaire entre votre réseau local et Microsoft pour la connectivité sortante, ces connexions entrantes peuvent être affectées par inadvertance par le routage asymétrique, même si vous envisagez de faire en sorte que ces flux continuent à utiliser Internet. Quelques précautions décrites ci-dessous sont recommandées pour s’assurer qu’il n’y a aucun impact sur les flux entrants basés sur Internet de Office 365 vers des systèmes locaux.
  
Pour réduire les risques de routage asymétrique pour les flux de trafic réseau entrant, toutes les connexions entrantes doivent utiliser la nat source avant d’être routées vers des segments de votre réseau, qui ont une visibilité du routage dans ExpressRoute. Si les connexions entrantes sont autorisées sur un segment réseau avec une visibilité du routage dans ExpressRoute sans nat source, les demandes provenant de Office 365 entrent à partir d’Internet, mais la réponse revient à Office 365 préférera le chemin réseau ExpressRoute vers le réseau Microsoft, ce qui entraîne un routage asymétrique.
  
Vous pouvez envisager l’un des modèles d’implémentation suivants pour répondre à cette exigence :
  
1. Effectuez une nat source avant que les demandes ne soient acheminées vers votre réseau interne à l’aide d’équipements réseau tels que des pare-feu ou des équilibreurs de charge sur le chemin d’accès d’Internet à vos systèmes locaux.

2. Assurez-vous que les itinéraires ExpressRoute ne sont pas propagés aux segments réseau où résident les services entrants, tels que les serveurs frontaux ou les systèmes proxy inverses, la gestion des connexions Internet.

La prise en compte explicite de ces scénarios dans votre réseau et la conservation de tous les flux de trafic réseau entrants sur Internet permettent de réduire le déploiement et le risque opérationnel de routage asymétrique.
  
Dans certains cas, vous pouvez choisir de diriger certains flux entrants sur des connexions ExpressRoute. Pour ces scénarios, prenez en compte les considérations supplémentaires suivantes.
  
1. Office 365 ne pouvez cibler que les points de terminaison locaux qui utilisent des adresses IP publiques. Cela signifie que même si le point de terminaison entrant local n’est exposé qu’à Office 365 sur ExpressRoute, il doit toujours avoir une adresse IP publique associée.

2. Toutes les résolutions de noms DNS effectuées par Office 365 services pour résoudre les points de terminaison locaux se produisent à l’aide du DNS public. Cela signifie que vous devez inscrire le nom de domaine complet des points de terminaison de service entrants aux mappages IP sur Internet.

3. Pour recevoir des connexions réseau entrantes via ExpressRoute, les sous-réseaux IP publics de ces points de terminaison doivent être publiés sur Microsoft via ExpressRoute.

4. Évaluez soigneusement ces flux de trafic réseau entrant pour vous assurer que la sécurité et les contrôles réseau appropriés sont appliqués conformément aux stratégies de sécurité et de réseau de votre entreprise.

5. Une fois vos points de terminaison entrants locaux publiés sur Microsoft via ExpressRoute, ExpressRoute devient le chemin d’accès de routage par défaut vers ces points de terminaison pour tous les services Microsoft, y compris les Office 365. Cela signifie que ces sous-réseaux de point de terminaison doivent être utilisés uniquement pour les communications avec Office 365 services et aucun autre service sur le réseau Microsoft. Sinon, votre conception entraîne un routage asymétrique où les connexions entrantes d’autres services Microsoft préfèrent acheminer le trafic entrant via ExpressRoute, tandis que le chemin d’accès de retour utilisera Internet.

6. Si un circuit ExpressRoute ou un emplacement de réunion est arrêté, vous devez vous assurer que les points de terminaison entrants locaux sont toujours disponibles pour accepter les demandes sur un chemin d’accès réseau distinct. Cela peut signifier la publicité de sous-réseaux pour ces points de terminaison via plusieurs circuits ExpressRoute.

7. Nous vous recommandons d’appliquer la nat source pour tous les flux de trafic réseau entrant entrants entrants entrants dans votre réseau via ExpressRoute, en particulier lorsque ces flux traversent des périphériques réseau avec état tels que des pare-feu.

8. Certains services locaux, tels que le proxy ADFS ou la découverte automatique Exchange, peuvent recevoir des demandes entrantes provenant des services Office 365 et des utilisateurs à partir d’Internet. Pour ces demandes Office 365 cible le même nom de domaine complet que les demandes des utilisateurs sur Internet. Autoriser les connexions utilisateur entrantes à partir d’Internet vers ces points de terminaison locaux, tout en forçant Office 365 connexions à utiliser ExpressRoute, représente une complexité de routage importante. Pour la grande majorité des clients implémentant des scénarios aussi complexes sur ExpressRoute n’est pas recommandé en raison de considérations opérationnelles. Cette surcharge supplémentaire inclut la gestion des risques liés au routage asymétrique et vous obligera à gérer soigneusement les publicités et les stratégies de routage sur plusieurs dimensions.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Mettez à jour votre plan de topologie réseau pour montrer comment éviter les itinéraires asymétriques
<a name="asymmetric"> </a>

Vous souhaitez éviter le routage asymétrique pour vous assurer que les membres de votre organisation peuvent utiliser en toute transparence Office 365 ainsi que d’autres services importants sur Internet. Il existe deux configurations courantes que les clients ont qui provoquent un routage asymétrique. Le moment est venu de passer en revue la configuration réseau que vous envisagez d’utiliser et de vérifier si l’un de ces scénarios de routage asymétrique pourrait exister.
  
Pour commencer, nous allons examiner quelques situations différentes associées au diagramme de réseau suivant. Dans ce diagramme, tous les serveurs qui reçoivent des demandes entrantes, tels qu’ADFS ou des serveurs hybrides locaux, se trouvent dans le centre de données du New Jersey et sont publiés sur Internet.
  
1. Bien que le réseau de périmètre soit sécurisé, aucun NAT source n’est disponible pour les demandes entrantes.

2. Les serveurs du centre de données du New Jersey peuvent voir les itinéraires Internet et ExpressRoute.

![Vue d’ensemble de la connectivité ExpressRoute.](../media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
Nous avons également des suggestions sur la façon de les corriger.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problème 1 : Connexion cloud-locale via Internet
  
Le diagramme suivant illustre le chemin d’accès réseau asymétrique pris lorsque votre configuration réseau ne fournit pas nat pour les requêtes entrantes provenant du cloud Microsoft sur Internet.
  
1. La requête entrante de Office 365 récupère l’adresse IP du point de terminaison local à partir du DNS public et envoie la demande à votre réseau de périmètre.

2. Dans cette configuration défectueuse, aucune nat source n’est configurée ou disponible sur le réseau de périmètre où le trafic est envoyé, ce qui entraîne l’utilisation de l’adresse IP source réelle comme destination de retour.

  - Le serveur sur votre réseau achemine le trafic de retour vers Office 365 via n’importe quelle connexion réseau ExpressRoute disponible.

  - Le résultat est un chemin asymétrique pour ce flux vers Office 365, ce qui entraîne une rupture de la connexion.

![Problème de routage asymétrique ExpressRoute 1.](../media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Solution 1a : NAT source
  
L’ajout d’une nat source à la demande entrante résout ce réseau mal configuré. Dans ce schéma :
  
1. La demande entrante continue d’entrer via le réseau de périmètre du centre de données du New Jersey. Cette fois, source NAT est disponible.

2. La réponse du serveur revient vers l’adresse IP associée à la NAT source au lieu de l’adresse IP d’origine, ce qui entraîne le retour de la réponse le long du même chemin d’accès réseau.

![Solution de routage asymétrique ExpressRoute 1.](../media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Solution 1b : Étendue des itinéraires
  
Vous pouvez également choisir de ne pas autoriser la publication des préfixes BGP ExpressRoute, en supprimant le chemin d’accès réseau secondaire de ces ordinateurs. Dans ce schéma :
  
1. La demande entrante continue d’entrer via le réseau de périmètre du centre de données du New Jersey. Cette fois, les préfixes publiés par Microsoft sur le circuit ExpressRoute ne sont pas disponibles pour le centre de données du New Jersey.

2. La réponse du serveur revient vers l’adresse IP associée à l’adresse IP d’origine sur la seule route disponible, ce qui entraîne le retour de la réponse le long du même chemin d’accès réseau.

![Solution de routage asymétrique ExpressRoute 2.](../media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problème 2 : Connexion cloud à locale via ExpressRoute
  
Le diagramme suivant illustre le chemin d’accès réseau asymétrique pris lorsque votre configuration réseau ne fournit pas nat pour les requêtes entrantes provenant du cloud Microsoft via ExpressRoute.
  
1. La requête entrante de Office 365 récupère l’adresse IP à partir de DNS et envoie la requête à votre réseau de périmètre.

2. Dans cette configuration défectueuse, aucune nat source n’est configurée ou disponible sur le réseau de périmètre où le trafic est envoyé, ce qui entraîne l’utilisation de l’adresse IP source réelle comme destination de retour.

  - L’ordinateur sur votre réseau achemine le trafic de retour vers Office 365 via n’importe quelle connexion réseau ExpressRoute disponible.

  - Le résultat est une connexion asymétrique à Office 365.

![Problème de routage asymétrique ExpressRoute 2.](../media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Solution 2 : NAT source
  
L’ajout d’une nat source à la demande entrante résout ce réseau mal configuré. Dans ce schéma :
  
1. La demande entrante continue d’entrer via le réseau de périmètre du centre de données de New York. Cette fois, source NAT est disponible.

2. La réponse du serveur revient vers l’adresse IP associée à la NAT source au lieu de l’adresse IP d’origine, ce qui entraîne le retour de la réponse le long du même chemin d’accès réseau.

![Solution de routage asymétrique ExpressRoute 3.](../media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Vérifier que la conception réseau a une symétrie de chemin d’accès

À ce stade, vous devez vérifier sur papier que votre plan d’implémentation offre une symétrie de routage pour les différents scénarios dans lesquels vous allez utiliser Office 365. Vous allez identifier l’itinéraire réseau spécifique qui doit être effectué lorsqu’une personne utilise différentes fonctionnalités du service. À partir du réseau local et du routage WAN, jusqu’aux périphériques de périmètre, au chemin de connectivité ; ExpressRoute ou Internet, et sur la connexion au point de terminaison en ligne.
  
Vous devez le faire pour tous les services réseau Office 365 qui ont été précédemment identifiés comme des services que votre organisation adoptera.
  
Il est utile de faire ce document pas à pas des itinéraires avec une deuxième personne. Expliquez-leur d’où chaque tronçon réseau est censé obtenir son prochain itinéraire et assurez-vous que vous êtes familiarisé avec les chemins d’accès de routage. N’oubliez pas qu’ExpressRoute fournit toujours un itinéraire plus étendu vers les adresses IP de serveur Microsoft, ce qui lui permet de réduire le coût d’itinéraire par rapport à un itinéraire Internet par défaut.
  
### <a name="design-client-connectivity-configuration"></a>Concevoir la configuration de la connectivité du client
<a name="asymmetric"> </a>

![Utilisation de fichiers PAC avec ExpressRoute.](../media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Si vous utilisez un serveur proxy pour le trafic lié à Internet, vous devez ajuster les fichiers de configuration PAC ou client pour vous assurer que les ordinateurs clients de votre réseau sont correctement configurés pour envoyer le trafic ExpressRoute que vous souhaitez Office 365 sans transiter votre serveur proxy, et que le trafic restant, y compris un trafic Office 365, est envoyé au proxy approprié. Lisez notre guide sur la [gestion des points](./managing-office-365-endpoints.md) de terminaison Office 365, par exemple, les fichiers PAC.
  
> [!NOTE]
> Les points de terminaison changent fréquemment, aussi souvent qu’une fois par semaine. Vous devez uniquement apporter des modifications en fonction des services et fonctionnalités que votre organisation a adoptés pour réduire le nombre de modifications que vous devez apporter pour rester à jour. Portez une attention particulière à la **date d’effet** dans le flux RSS où les modifications sont annoncées et un enregistrement est conservé de toutes les modifications passées, les adresses IP qui sont annoncées peuvent ne pas être publiées ou supprimées de la publicité, jusqu’à ce que la date effective soit atteinte.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Créer vos procédures de déploiement et de test
<a name="testing"> </a>

Votre plan d’implémentation doit inclure à la fois la planification des tests et la restauration. Si votre implémentation ne fonctionne pas comme prévu, le plan doit être conçu pour affecter le moins de personnes avant la découverte des problèmes. Voici quelques principes généraux que votre plan doit prendre en compte.
  
1. Organisez l’intégration du segment réseau et du service utilisateur pour réduire les interruptions.

2. Planifiez le test des itinéraires avec traceroute et connexion TCP à partir d’un hôte connecté à Internet distinct.

3. De préférence, les tests des services entrants et sortants doivent être effectués sur un réseau de test isolé avec un client de test Office 365.

      - Vous pouvez également effectuer des tests sur un réseau de production si le client n’utilise pas encore Office 365 ou est en phase pilote.

      - Vous pouvez également effectuer des tests lors d’une panne de production réservée aux tests et à la surveillance uniquement.

      - Vous pouvez également effectuer des tests en vérifiant les itinéraires de chaque service sur chaque nœud de routeur de couche 3. Ce recul ne doit être utilisé que si aucun autre test n’est possible, car l’absence de tests physiques présente un risque.

### <a name="build-your-deployment-procedures"></a>Créer vos procédures de déploiement

Vos procédures de déploiement doivent être déployées par étapes sur de petits groupes de personnes afin de permettre le test avant le déploiement sur de plus grands groupes de personnes. Voici plusieurs façons d’organiser le déploiement d’ExpressRoute.
  
1. Configurez ExpressRoute avec le peering Microsoft et faites transférer les annonces de routage à un seul hôte à des fins de test intermédiaire.

2. Publiez des itinéraires vers le réseau ExpressRoute vers un segment de réseau unique au début et développez les annonces de routage par segment de réseau ou région.

3. Si vous déployez Office 365 pour la première fois, utilisez le déploiement réseau ExpressRoute comme pilote pour quelques personnes.

4. Si vous utilisez des serveurs proxy, vous pouvez également configurer un fichier PAC de test pour diriger quelques personnes vers ExpressRoute avec des tests et des commentaires avant d’en ajouter d’autres.

Votre plan d’implémentation doit répertorier chacune des procédures de déploiement qui doivent être effectuées ou les commandes qui doivent être utilisées pour déployer la configuration réseau. Lorsque le temps de panne réseau arrive, toutes les modifications apportées doivent être du plan de déploiement écrit qui a été écrit à l’avance et examiné par les pairs. Consultez nos conseils sur la configuration technique d’ExpressRoute.
  
- Mise à jour de vos enregistrements TXT SPF si vous avez modifié les adresses IP des serveurs locaux qui continueront à envoyer des e-mails.

- Mise à jour des entrées DNS pour les serveurs locaux si vous avez modifié des adresses IP pour prendre en charge une nouvelle configuration NAT.

- Assurez-vous que vous êtes abonné au flux RSS pour Office 365 notifications de point de terminaison afin de conserver les configurations de routage ou de proxy.

Une fois votre déploiement ExpressRoute terminé, les procédures du plan de test doivent être exécutées. Les résultats de chaque procédure doivent être enregistrés. Vous devez inclure des procédures de retour à l’environnement de production d’origine si les résultats du plan de test indiquent que l’implémentation n’a pas réussi.
  
### <a name="build-your-test-procedures"></a>Créer vos procédures de test

Vos procédures de test doivent inclure des tests pour chaque service réseau sortant et entrant pour Office 365 à la fois qui utilisera ExpressRoute et ceux qui ne le feront pas. Les procédures doivent inclure des tests à partir de chaque emplacement réseau unique, y compris les utilisateurs qui ne sont pas locaux dans le réseau local de l’entreprise.
  
Voici quelques exemples d’activités de test.
  
1. Effectuez un test ping à partir de votre routeur local vers votre routeur d’opérateur réseau.

2. Vérifiez que les annonces d’adresses IP 500+ Office 365 et CRM Online sont reçues par votre routeur local.

3. Vérifiez que votre nat entrant et sortant fonctionne entre ExpressRoute et le réseau interne.

4. Vérifiez que les itinéraires vers votre NAT sont publiés à partir de votre routeur.

5. Vérifiez qu’ExpressRoute a accepté vos préfixes publiés.

      - Utilisez l’applet de commande suivante pour vérifier les publicités de peering :

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Vérifiez que votre plage d’adresses IP NAT publique n’est pas publiée pour Microsoft par le biais d’un autre circuit ExpressRoute ou réseau Internet public, sauf s’il s’agit d’un sous-ensemble spécifique d’une plage plus grande, comme dans l’exemple précédent.

7. Les circuits ExpressRoute sont appairés, vérifiez que les deux sessions BGP sont en cours d’exécution.

8. Configurez un hôte unique à l’intérieur de votre NAT et utilisez ping, tracert et tcpping pour tester la connectivité entre le nouveau circuit et l’hôte outlook.office365.com. Vous pouvez également utiliser un outil tel que Wireshark ou Microsoft Network Monitor 3.4 sur un port mis en miroir vers le MSEE pour vérifier que vous êtes en mesure de vous connecter à l’adresse IP associée à outlook.office365.com.

9. Tester les fonctionnalités au niveau de l’application pour Exchange Online.

  - Testez Outlook est en mesure de se connecter à Exchange Online et d’envoyer/recevoir des e-mails.

  - Test Outlook est en mesure d’utiliser le mode en ligne.

  - Testez la connectivité des smartphones et la fonctionnalité d’envoi/réception.

10. Tester les fonctionnalités au niveau de l’application pour SharePoint Online

  - Testez OneDrive Entreprise client de synchronisation.

  - Testez SharePoint l’accès web en ligne.

11. Testez les fonctionnalités au niveau de l’application pour Skype Entreprise scénarios d’appel :

  - Participez à une téléconférence en tant qu’utilisateur authentifié [invitation lancée par l’utilisateur final].

  - Inviter un utilisateur à une téléconférence [invitation envoyée à partir de MCU].

  - Participez à la conférence en tant qu’utilisateur anonyme à l’aide de l’application web Skype Entreprise.

  - Rejoignez l’appel à partir de votre connexion PC câblée, de votre téléphone IP et de votre appareil mobile.

  - Appel à l’utilisateur fédéré o Appel à la validation RTC : l’appel est terminé, la qualité de l’appel est acceptable, le temps de connexion est acceptable.

  - Vérifiez que l’état de présence des contacts est mis à jour pour les membres du locataire et les utilisateurs fédérés.

### <a name="common-problems"></a>Problèmes courants

Le routage asymétrique est le problème d’implémentation le plus courant. Voici quelques sources courantes à rechercher :
  
- Utilisation d’une topologie de routage réseau ouverte ou plate sans nat source en place.

- N’utilisez pas SNAT pour router vers les services entrants via les connexions Internet et ExpressRoute.

- Ne testez pas les services entrants sur ExpressRoute sur un réseau de test avant le déploiement à grande échelle.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Déploiement de la connectivité ExpressRoute via votre réseau
<a name="testing"> </a>

Organisez votre déploiement sur un segment du réseau à la fois, en déployant progressivement la connectivité à différentes parties du réseau avec un plan de restauration pour chaque nouveau segment de réseau. Si votre déploiement est aligné sur un déploiement Office 365, déployez d’abord sur vos utilisateurs pilotes Office 365 et étendez-le à partir de là.
  
Tout d’abord pour votre test, puis pour la production :
  
- Exécutez les étapes de déploiement pour activer ExpressRoute.

- Testez que les itinéraires réseau sont comme prévu.

- Effectuez des tests sur chaque service entrant et sortant.

- Restauration si vous découvrez des problèmes.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurer une connexion de test à ExpressRoute avec un segment de réseau de test

Maintenant que vous avez le plan terminé sur papier, il est temps de tester à petite échelle. Dans ce test, vous allez établir une connexion ExpressRoute unique avec le peering Microsoft à un sous-réseau de test sur votre réseau local. Vous pouvez configurer un [client d’essai Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) avec une connectivité vers et depuis le sous-réseau de test et inclure tous les services sortants et entrants que vous utiliserez en production dans le sous-réseau de test. Configurez DNS pour le segment de réseau de test et établissez tous les services entrants et sortants. Exécutez votre plan de test et assurez-vous que vous êtes familiarisé avec le routage pour chaque service et la propagation de l’itinéraire.
  
### <a name="execute-the-deployment-and-test-plans"></a>Exécuter les plans de déploiement et de test

Lorsque vous effectuez les éléments décrits ci-dessus, vérifiez les zones que vous avez terminées et assurez-vous que vous et votre équipe les avez examinés avant d’exécuter vos plans de déploiement et de test.
  
- Liste des services sortants et entrants impliqués dans la modification du réseau.

- Diagramme d’architecture réseau globale montrant à la fois la sortie d’Internet et les emplacements de rencontre ExpressRoute.

- Diagramme de routage réseau illustrant les différents chemins d’accès réseau utilisés pour chaque service déployé.

- Un plan de déploiement avec des étapes pour implémenter les modifications et la restauration si nécessaire.

- Un plan de test pour tester chaque Office 365 et service réseau.

- Validation papier terminée des itinéraires de production pour les services entrants et sortants.

- Test terminé sur un segment de réseau de test, y compris les tests de disponibilité.

Choisissez une fenêtre de panne suffisamment longue pour s’exécuter dans l’ensemble du plan de déploiement et du plan de test, dispose d’un certain temps pour la résolution des problèmes et du temps de restauration si nécessaire.
  
> [!CAUTION]
> En raison de la nature complexe du routage sur Internet et ExpressRoute, il est recommandé d’ajouter du temps de mémoire tampon supplémentaire à cette fenêtre pour gérer la résolution des problèmes de routage complexe.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configurer QoS pour Skype Entreprise Online

QoS est nécessaire pour obtenir des avantages de voix et de réunion pour Skype Entreprise Online. Vous pouvez configurer QoS après avoir vérifié que la connexion réseau ExpressRoute ne bloque aucun de vos autres accès au service Office 365. La configuration de QoS est décrite dans l’article [ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d).
  
## <a name="troubleshooting-your-implementation"></a>Résolution des problèmes d’implémentation
<a name="troubleshooting"> </a>

La première chose à examiner est les étapes de ce guide d’implémentation, avez-vous manqué dans votre plan d’implémentation ? Retour et exécutez d’autres tests réseau de petite taille si possible pour répliquer l’erreur et la déboguer.
  
Identifiez les services entrants ou sortants qui ont échoué pendant le test. Obtenez spécifiquement les adresses IP et les sous-réseaux pour chacun des services qui ont échoué. Allez-y et parcourez le diagramme de topologie réseau sur papier et validez le routage. Validez spécifiquement l’endroit où le routage ExpressRoute est publié, testez ce routage pendant la panne si possible avec des traces.
  
Exécutez PSPing avec une trace réseau vers chaque point de terminaison client et évaluez les adresses IP source et de destination pour vérifier qu’elles sont conformes aux attentes. Exécutez telnet sur n’importe quel hôte de messagerie que vous exposez sur le port 25 et vérifiez que SNAT masque l’adresse IP source d’origine si cela est attendu.
  
Gardez à l’esprit que lors du déploiement de Office 365 avec une connexion ExpressRoute, vous devez vous assurer que la configuration réseau pour ExpressRoute est optimale et que vous avez également optimisé les autres composants de votre réseau, tels que les ordinateurs clients. En plus d’utiliser ce guide de planification pour résoudre les étapes que vous avez peut-être manquées, nous avons également écrit un [plan de résolution des problèmes de performances pour Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c).
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/implementexpressroute365]()
  
## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Utilisation de communautés BGP dans ExpressRoute pour Office 365 scénarios](bgp-communities-in-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimisation de votre réseau pour Skype Entreprise Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Paramétrage des performances et du réseau Office 365](network-planning-and-performance.md)
