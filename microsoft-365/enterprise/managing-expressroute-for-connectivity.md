---
title: Gestion d’ExpressRoute pour la connectivité d’Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: Découvrez comment gérer ExpressRoute pour Office 365, y compris les zones communes à configurer, telles que le filtrage des préfixes, la sécurité et la conformité.
ms.openlocfilehash: e8de0763df7d592bc41802b1ead48df06891e6dc
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50916667"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Gestion d’ExpressRoute pour la connectivité d’Office 365

ExpressRoute pour Office 365 offre un autre chemin de routage pour atteindre de nombreux services Office 365 sans avoir besoin de tout le trafic pour la sortie vers Internet. Bien que la connexion Internet à Office 365 soit toujours nécessaire, les itinéraires spécifiques publiés par Microsoft via BGP vers votre réseau préfèrent le circuit ExpressRoute direct, sauf s’il existe d’autres configurations dans votre réseau. Les trois domaines courants que vous souhaitez peut-être configurer pour gérer ce routage incluent le filtrage des préfixes, la sécurité et la conformité.
  
> [!NOTE]
> Microsoft a modifié la révision du domaine de routage de l’homologue Microsoft pour Azure ExpressRoute. À compter du 31 juillet 2017, tous les clients Azure ExpressRoute peuvent activer l’homologue Microsoft directement à partir de la console d’administration Azure ou via PowerShell. Après l’activation de l’homologue Microsoft, tout client peut créer des filtres d’itinéraire pour recevoir des annonces d’itinéraire BGP pour les applications Dynamics 365 Customer Engagement (anciennement CRM Online). Les clients qui ont besoin d’Azure ExpressRoute pour Office 365 doivent obtenir l’avis de Microsoft pour pouvoir créer des filtres d’itinéraire pour Office 365. Contactez votre équipe de compte Microsoft pour savoir comment demander un avis sur l’activation d’Office 365 ExpressRoute. Les abonnements non autorisés qui tentent de créer des filtres d’itinéraire pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrage des préfixes

Microsoft recommande aux clients d’accepter tous les itinéraires BGP publiés par Microsoft. Les itinéraires fournis font l’objet d’un processus rigoureux de révision et de validation, supprimant ainsi les avantages d’un examen approfondi. ExpressRoute offre en natif les contrôles recommandés tels que la propriété, l’intégrité et l’échelle du préfixe IP, sans filtrage des itinéraires entrants côté client.
  
Si vous avez besoin d’une validation supplémentaire de la propriété de l’itinéraire entre l’homologue public ExpressRoute, vous pouvez vérifier les itinéraires publiés par rapport à la liste de tous les préfixes IP IPv4 et IPv6 qui représentent les [plages d’adresses IP publiques](https://www.microsoft.com/download/details.aspx?id=53602)de Microsoft. Ces plages couvrent l’espace d’adressace Microsoft complet et changent rarement, fournissant un ensemble fiable de plages à filtrer, ce qui fournit également une protection supplémentaire aux clients qui sont préoccupés par la fuite d’itinéraires non-Microsoft dans leur environnement. En cas de modification, elle sera réalisée le 1er du mois et le numéro de version de la section **Détails** de la page change chaque fois que le fichier est mis à jour.
  
Il existe plusieurs raisons d’éviter l’utilisation des URL et des [plages d’adresses IP Office 365](./urls-and-ip-address-ranges.md) pour générer des listes de filtres de préfixes. Y compris les suivants :
  
- Les préfixes IP Office 365 subissent régulièrement de nombreuses modifications.

- Les URL et plages d’adresses IP Office 365 sont conçues pour gérer les listes d’adresses pare-feu et l’infrastructure proxy, et non le routage.

- Les URL et plages d’adresses IP Office 365 ne couvrent pas les autres services Microsoft qui peuvent être dans l’étendue de vos connexions ExpressRoute.

|**Option**|**Complexité**|**Contrôle des changements**|
|:-----|:-----|:-----|
|Accepter tous les itinéraires Microsoft  <br/> |**Faible :** Le client s’appuie sur les contrôles Microsoft pour s’assurer que tous les itinéraires sont correctement propriétaire.  <br/> |Aucun  <br/> |
|Filtrer les supernets de Microsoft  <br/> |**Moyen :** Le client implémente des listes récapitulées de filtres de préfixes pour autoriser uniquement les itinéraires dont Microsoft est propriétaire.  <br/> |Les clients doivent s’assurer que les mises à jour peu fréquentes sont reflétées dans les filtres d’itinéraire.  <br/> |
|Filtrer les plages d’adresses IP Office 365  <br/> [!CAUTION] Not-Recommended |**Élevé :** Le client filtre les itinéraires en fonction des préfixes IP Office 365 définis.  <br/> |Les clients doivent implémenter un processus de gestion des changements robuste pour les mises à jour mensuelles.  <br/> [!CAUTION] Cette solution nécessite des modifications importantes en cours. Les modifications non implémentées dans le temps entraîneront probablement une panne du service.   |

La connexion à Office 365 à l’aide d’Azure ExpressRoute est basée sur les annonces BGP de sous-réseaux IP spécifiques qui représentent les réseaux où les points de terminaison Office 365 sont déployés. En raison de la nature globale d’Office 365 et du nombre de services qui le sont, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. Si vous êtes préoccupé par le nombre de préfixes publiés dans votre environnement, la fonctionnalité de communauté [BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) vous permet de filtrer les publicités sur un ensemble spécifique de services Office 365. Cette fonctionnalité est désormais en prévisualisation.
  
Quelle que soit la façon dont vous gérez les publicités d’itinéraire BGP provenant de Microsoft, vous n’êtes pas exposé aux services Office 365 par rapport à la connexion à Office 365 via un circuit Internet uniquement. Microsoft conserve les mêmes niveaux de sécurité, de conformité et de performances, quel que soit le type de circuit utilisé par un client pour se connecter à Office 365.
  
### <a name="security"></a>Sécurité

Microsoft vous recommande de maintenir vos propres contrôles de périmètre de sécurité et réseau pour les connexions vers et depuis l’homologue public ExpressRoute et Microsoft, qui inclut les connexions vers et depuis les services Office 365. Des contrôles de sécurité doivent être en place pour les demandes réseau qui sont sortantes de votre réseau vers le réseau de Microsoft, ainsi que pour les demandes entrantes entre le réseau de Microsoft et votre réseau.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Trafic sortant entre le client et Microsoft
  
Lorsque les ordinateurs se connectent à Office 365, ils se connectent au même ensemble de points de terminaison, que la connexion soit réalisée via internet ou un circuit ExpressRoute. Quel que soit le circuit utilisé, Microsoft recommande de traiter les services Office 365 comme étant plus fiables que les destinations Internet génériques. Vos contrôles de sécurité sortants doivent se concentrer sur les ports et protocoles pour réduire l’exposition et réduire la maintenance en cours. Les informations de port requises sont disponibles dans l’article de référence sur les points de terminaison [Office 365.](./urls-and-ip-address-ranges.md)
  
Pour les contrôles ajoutés, vous pouvez utiliser le filtrage de niveau FQDN au sein de votre infrastructure proxy pour restreindre ou inspecter une partie ou l’ensemble des demandes réseau destinées à Internet ou Office 365. La gestion de la liste des FQDN à mesure que les fonctionnalités sont publiées et que les offres Office 365 évoluent nécessite une gestion des modifications plus robuste et le suivi des modifications apportées aux points de terminaison [Office 365 publiés.](./urls-and-ip-address-ranges.md)
  
> [!CAUTION]
> Microsoft vous recommande de ne pas vous fier uniquement aux préfixes IP pour gérer la sécurité sortante vers Office 365.

|**Option**|**Complexité**|**Contrôle des changements**|
|:-----|:-----|:-----|
|Aucune restriction  <br/> |**Faible :** Le client autorise l’accès sortant illimité à Microsoft.  <br/> |Aucun  <br/> |
|Restrictions de port  <br/> |**Faible :** Le client limite l’accès sortant à Microsoft par les ports attendus.  <br/> |Rare.  <br/> |
|Restrictions de FQDN  <br/> |**Élevé :** Le client limite l’accès sortant à Office 365 en fonction des FQDN publiés.  <br/> |Modifications mensuelles.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Trafic entrant entre Microsoft et le client
  
Il existe plusieurs scénarios facultatifs qui obligent Microsoft à établir des connexions à votre réseau.
  
- ADFS lors de la validation du mot de passe pour la signature.

- [Exchange Server déploiements hybrides.](/exchange/exchange-hybrid)

- Courrier provenant d’un client Exchange Online vers un hôte local.

- SharePoint Online Mail send from SharePoint Online to an on-premises host.

- [Recherche hybride fédérée SharePoint.](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online)

- [SharePoint hybride BCS](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype Entreprise hybride et/ou](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) [fédération Skype Entreprise](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype Entreprise Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft recommande d’accepter ces connexions sur votre circuit Internet au lieu de votre circuit ExpressRoute pour réduire la complexité. Si vos besoins en matière de conformité ou de performances imposent que ces connexions entrantes doivent être acceptées sur un circuit ExpressRoute, l’utilisation d’un pare-feu ou d’un proxy inverse pour l’étendue des connexions acceptées est recommandée. Vous pouvez utiliser les points [de terminaison Office 365](./urls-and-ip-address-ranges.md) pour déterminer les bons FQDN et préfixes IP.
  
### <a name="compliance"></a>Conformité

Nous ne nous appuyons pas sur le chemin de routage que vous utilisez pour l’un de nos contrôles de conformité. Que vous vous connectiez aux services Office 365 via un circuit ExpressRoute ou Internet, nos contrôles de conformité ne changeront pas. Vous devez passer en revue les différents niveaux de certification de conformité et de sécurité pour Office 365 afin de déterminer le meilleur choix pour répondre aux besoins de votre organisation.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Rubriques connexes

[Réseaux de distribution de contenu](content-delivery-networks.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)