---
title: Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: Découvrez comment utiliser les communautés BGP dans Azure ExpressRoute pour gérer le nombre de préfixes IP et la bande passante requise pour les scénarios Office 365.
ms.openlocfilehash: 3a1de8725ae967352723649e602d944ca6948310
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690065"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Utilisation des communautés BGP dans ExpressRoute pour les scénarios Office 365

La connexion à Office 365 à l’aide d’Azure ExpressRoute est basée sur les annonces BGP de sous-réseaux IP spécifiques qui représentent les réseaux où les points de terminaison Office 365 sont déployés. En raison de la nature globale d’Office 365 et du nombre de services qui constituent Office 365, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. réduction du nombre de sous-réseaux IP ; Appelés préfixes IP tout au long du reste de cet article, pour s’aligner sur la terminologie de gestion du réseau BGP, les objectifs finaux suivants sont atteints pour les clients :
  
- Gérer le nombre de **préfixes IP** publiés acceptés : les clients qui ont une infrastructure réseau interne ou un opérateur réseau qui ne prend en charge qu’un nombre limité de préfixes IP et les clients qui ont un opérateur réseau qui facture l’acceptation de préfixes supérieurs à un nombre limité souhaiteront évaluer le nombre total de préfixes déjà publiés sur leur réseau et sélectionner les applications Office 365 les mieux adaptées à ExpressRoute.

- **Gérez** la quantité de bande passante requise sur le circuit Azure ExpressRoute : les clients peuvent contrôler l’enveloppe de bande passante des services Office 365 via le chemin ExpressRoute et le chemin Internet. Cela permet aux clients de réserver la bande passante ExpressRoute pour des applications spécifiques telles que Skype Entreprise et de router les autres applications Office 365 via le chemin Internet.

Pour aider les clients à atteindre ces objectifs, les préfixes IP Office 365 publiés sur ExpressRoute sont marqués avec des valeurs de communauté BGP spécifiques au service, comme illustré dans l’exemple ci-dessous.
  
> [!NOTE]
> Vous devez vous attendre à ce qu’un certain trafic réseau associé à d’autres applications soit inclus dans la valeur de la communauté. This is expected behavior for a global Software as a Service offering with shared services and datacenters. Cela a été réduit dans la mesure du possible avec les deux objectifs ci-dessus, en gérant le nombre de préfixes et/ou la bande passante à l’esprit.

|**Service**|**Valeur de la communauté BGP**|**Notes**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |Inclut les services Exchange et EOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype Entreprise\*  <br/> |12076:5030  <br/> |Skype Entreprise Online & services Microsoft Teams  <br/> |
|Autres services Office 365\*  <br/> |12076:5100  <br/> |Inclut Azure Active Directory (scénarios d’authentification et de synchronisation d’annuaires) ainsi que les services du portail Office 365  <br/> |
|\*L’étendue des scénarios de service inclus dans ExpressRoute est expliquée dans l’article sur les points de terminaison [Office 365.](https://aka.ms/o365endpoints)  <br/> \*\*Des services supplémentaires et des valeurs de communauté BGP peuvent être ajoutés à l’avenir. [Consultez la liste actuelle des communautés BGP.](https://azure.microsoft.com/documentation/articles/expressroute-routing/)  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>Quels sont les scénarios les plus courants pour l’utilisation des communautés BGP ?

Les clients peuvent utiliser des communautés BGP pour contrôler les groupes de préfixes IP acceptés par leur réseau via Azure ExpressRoute, ce qui a une incidence sur le nombre total de préfixes IP et l’enveloppe de bande passante attendue de certains services Office 365. Il est important de comprendre que tout Office 365 nécessitera un trafic internet, quelle que soit l’utilisation d’Azure ExpressRoute ou des communautés BGP. Les trois scénarios suivants sont les utilisations les plus courantes de cette fonctionnalité.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Scénario 1 : réduction du nombre de préfixes IP Office 365

Contoso Corporation est une entreprise de 50 000 personnes qui utilise actuellement Office 365 pour Exchange Online et SharePoint Online. Lors de l’examen des exigences d’ExpressRoute, Contoso détermine que ses périphériques réseau dans de nombreux emplacements régionaux ne peuvent pas gérer des tailles de table de routage supérieures à 100 entrées d’itinéraire supplémentaires. Contoso a examiné le nombre total de préfixes IP qu’ExpressRoute publierait pour l’ensemble complet des services Office 365 et a conclu qu’il dépasse 100. Pour rester sous les 100 entrées d’itinéraire supplémentaires, Contoso limite l’utilisation d’ExpressRoute pour Office 365 à la valeur de la communauté BGP SharePoint Online, 12076:5020, reçue via l’homologue Microsoft ExpressRoute.

|**Balise de communauté BGP utilisée**|**Routable des fonctionnalités sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive Entreprise  <br/> | DNS, CRL, &amp; demandes CDN  <br/>  Tous les autres services Office 365 ne sont pas spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services cloud de Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/>  Exchange Online, Exchange Online Protection et Skype Entreprise Online  <br/> |

> [!NOTE]
> Pour obtenir des nombres de préfixes inférieurs pour chaque service, une quantité minimale de chevauchement entre les services est persistante. Ce comportement est normal.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Scénario 2 : portée de l’utilisation d’ExpressRoute et de la bande passante interne à certains services Office 365

Fabrikam Inc, une grande entreprise multinationale avec un réseau hétérogène distribué, est abonné à de nombreux services Office 365, notamment ; Exchange Online, SharePoint Online et Skype Entreprise Online. L’infrastructure de routage interne de Fabrikam peut gérer des milliers de préfixes IP dans ses tables de routage ; Toutefois, Fabrikam souhaite uniquement mettre en service ExpressRoute et la bande passante interne pour les applications Office 365 les plus sensibles aux performances du réseau et utiliser leur bande passante Internet existante pour toutes les autres applications Office 365.
  
Pour cette raison, Fabrikam étendue sa bande passante Azure ExpressRoute à uniquement la valeur de la communauté BGP Skype Entreprise Online, 12076:5030, reçue via l’homologue Microsoft ExpressRoute. Le reste du trafic réseau associé à Office 365 continue d’utiliser les points de sortie Internet.

|**Balise de communauté BGP utilisée**|**Routable des fonctionnalités sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|Skype Entreprise  <br/> (12076:5030)  <br/> |Signalisation SIP Skype, téléchargements, voix, vidéo et partage de bureau  <br/> | DNS, CRL, &amp; demandes CDN  <br/>  Tous les autres services Office 365 ne sont pas spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services cloud de Microsoft  <br/>  Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/>  Télémétrie Skype Entreprise, conseils rapides du client Skype, connectivité de messagerie instantanée publique  <br/>  Exchange Online, Exchange Online Protection et SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Scénario 3 : portée d’Azure ExpressRoute pour les services Office 365 uniquement

Woodgrove Bank est un client de plusieurs services cloud Microsoft, notamment Office 365. Après avoir évalué leur capacité et leur consommation réseau, Woodgrove Bank décide de déployer Azure ExpressRoute comme chemin d’accès préféré pour les services Office 365 pris en charge. Les tables de routage peuvent prendre en charge l’ensemble complet des préfixes IP Office 365 et les circuits Azure ExpressRoute qu’ils ont mis en service, prendre en charge tous les besoins de latence et de bande passante projetés.
  
Pour garantir le trafic réseau associé aux services cloud de Microsoft autres qu’Office 365, Woodgrove Bank limite l’utilisation d’ExpressRoute pour Office 365 à tous les préfixes IP marqués avec des valeurs communautaires BGP spécifiques d’Office 365, 12076:5010, 12076:5020, 12076:5100.

|**Balise de communauté BGP utilisée**|**Routable des fonctionnalités sur Azure ExpressRoute**|**Itinéraires Internet requis**|
|:-----|:-----|:-----|
|Exchange, Skype Entreprise & Microsoft Teams, SharePoint, &amp; autres services  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive Entreprise  <br/> Signalisation SIP Skype, téléchargements, voix, vidéo et partage de bureau  <br/> Portail Office 365, authentification Office 365, &amp; Office dans un navigateur  <br/> | DNS, CRL, &amp; demandes CDN  <br/>  Tous les autres services Office 365 ne sont pas spécifiquement pris en charge sur Azure ExpressRoute  <br/>  Tous les autres services cloud de Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Considérations clés sur la planification de l’utilisation des communautés BGP

Les clients qui choisissent de tirer parti des communautés BGP pour influencer la façon dont ExpressRoute est publié et propagé via le réseau client doivent prendre en compte les considérations suivantes :
  
- Lorsque vous utilisez des communautés BGP dans votre conception réseau, il est important de s’assurer que la symétrie de l’itinéraire est conservée. Dans certains cas, l’ajout ou la suppression de communautés BGP peut créer une situation dans laquelle le routage symétrique est rompu et votre configuration de routage doit être mise à jour pour rétablir le routage symétrique.

- La portée d’Azure ExpressRoute avec les valeurs de la communauté BGP est une action du client. Microsoft publiera tous les préfixes IP associés à la relation d’homologue, quelle que soit l’portée configurée par le client.

- Azure ExpressRoute ne prend en charge aucune action sur le réseau de Microsoft en fonction des communautés BGP attribuées par le client.

- Les préfixes IP utilisés par Office 365 sont uniquement marqués avec des valeurs de communauté BGP spécifiques au service. Les communautés BGP spécifiques aux emplacements ne sont pas pris en charge. Les services Office 365 sont de nature globale, le filtrage des préfixes en fonction de l’emplacement du client ou des données dans le cloud Office 365 n’est pas pris en charge. L’approche recommandée consiste à configurer votre réseau pour coordonner le chemin réseau le plus court ou le plus privilégié de l’emplacement réseau de l’utilisateur vers le réseau global Microsoft, quel que soit l’emplacement physique de l’adresse IP du service Office 365 qu’il demande.

- Les préfixes IP inclus dans chaque valeur de communauté BGP représentent un sous-réseau qui contient des adresses IP pour l’application Office 365 associée à la valeur. Dans certains cas, plusieurs applications Office 365 ont des adresses IP dans un sous-réseau, ce qui entraîne l’existence d’un préfixe IP dans plusieurs valeurs communautaires. Ce comportement est attendu, bien que rarement, en raison de la fragmentation de l’allocation et n’a pas d’impact sur le nombre de préfixes ou les objectifs de gestion de la bande passante. Les clients sont encouragés à utiliser l’approche « Autoriser ce qui est nécessaire » plutôt que de « refuser ce qui n’est pas nécessaire » lorsque vous tirez parti des communautés BGP pour Office 365 afin de minimiser l’effet.

- L’utilisation de communautés BGP ne modifie pas les exigences de connectivité réseau sous-jacentes ou la configuration requise pour utiliser Office 365. Les clients qui souhaitent accéder à Office 365 doivent toujours pouvoir accéder à Internet.

- La portée d’Azure ExpressRoute avec les communautés BGP affecte uniquement les itinéraires que votre réseau interne peut voir sur la relation d’homologue Microsoft. Vous devrez peut-être effectuer des configurations supplémentaires au niveau de l’application, telles que l’utilisation d’une configuration PAC ou WPAD conjointement avec le routage d’étendue.

- Outre l’utilisation des communautés BGP attribuées par Microsoft, les clients peuvent choisir d’affecter leurs propres communautés BGP aux préfixes IP Office 365 appris via Azure ExpressRoute pour influencer le routage interne. Un cas d’utilisation courant consiste à affecter une communauté BGP basée sur un emplacement à tous les itinéraires appris via chaque emplacement d’homologue ExpressRoute donné, puis à utiliser ces informations en aval dans le réseau du client pour coordonner le chemin réseau le plus court ou le plus privilégié dans le réseau de Microsoft. L’utilisation des communautés BGP attribuées par le client avec ExpressRoute pour les scénarios Office 365 n’est pas du tout dans le cadre du contrôle ou de la visibilité de Microsoft.

Voici un lien que vous pouvez utiliser pour revenir [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365) :
  
## <a name="related-topics"></a>Rubriques connexes

[Évaluation de la connectivité réseau Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute pour Office 365](azure-expressroute.md)
  
[Gestion d’ExpressRoute pour la connectivité d’Office 365](managing-expressroute-for-connectivity.md)
  
[Routage avec ExpressRoute pour Office 365](routing-with-expressroute.md)
  
[Planification de réseau avec ExpressRoute pour Office 365](network-planning-with-expressroute.md)
  
[Qualité des médias et performances de connectivité réseau dans Skype Entreprise Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute et QoS dans Skype Entreprise Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Appel du flux à l’aide d’ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implémentation d’ExpressRoute pour Office 365](implementing-expressroute.md)
  
[Prise en charge des communautés BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Réglage des performances Office 365 à l’aide du planning de référence et de l’historique des performances](performance-tuning-using-baselines-and-history.md)
  
[Plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)
