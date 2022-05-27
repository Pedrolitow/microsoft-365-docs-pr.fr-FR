---
title: Gestion d’ExpressRoute pour la connectivité d’Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 7/13/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Découvrez comment gérer ExpressRoute pour Office 365, y compris les zones courantes à configurer comme le filtrage de préfixe, la sécurité et la conformité.
ms.openlocfilehash: 493a7c0ca14d05a2b84763b9e9485f828574a930
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753867"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Gestion d’ExpressRoute pour la connectivité d’Office 365

ExpressRoute pour Office 365 offre un autre chemin de routage pour atteindre de nombreux services Office 365 sans avoir besoin de tout le trafic vers la sortie vers Internet. Bien que la connexion Internet à Office 365 soit toujours nécessaire, les itinéraires spécifiques que Microsoft publie via BGP vers votre réseau rendent le circuit ExpressRoute direct préféré, sauf s’il existe d’autres configurations dans votre réseau. Les trois domaines courants que vous pouvez configurer pour gérer ce routage incluent le filtrage de préfixe, la sécurité et la conformité.
  
> [!NOTE]
> Microsoft a modifié la façon dont le domaine de routage du peering Microsoft est examiné pour Azure ExpressRoute. À compter du 31 juillet 2017, tous les clients Azure ExpressRoute peuvent activer le peering Microsoft directement à partir de la console d’administration Azure ou via PowerShell. Après avoir activé le peering Microsoft, n’importe quel client peut créer des filtres de routage pour recevoir des annonces de routage BGP pour les applications Dynamics 365 Customer Engagement (anciennement CRM Online). Les clients qui ont besoin d’Azure ExpressRoute pour Office 365 doivent obtenir une révision de Microsoft avant de pouvoir créer des filtres de routage pour Office 365. Contactez votre équipe de compte Microsoft pour savoir comment demander une révision pour l’activation de Office 365 ExpressRoute. Les abonnements non autorisés qui tentent de créer des filtres de routage pour Office 365 recevront un [message d’erreur](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrage de préfixe

Microsoft recommande aux clients d’accepter tous les itinéraires BGP tels qu’ils sont publiés à partir de Microsoft. Les itinéraires fournis font l’objet d’un processus rigoureux de révision et de validation, supprimant tous les avantages à un examen plus approfondi. ExpressRoute offre en mode natif les contrôles recommandés, tels que la propriété du préfixe IP, l’intégrité et la mise à l’échelle, sans filtrage des itinéraires entrants côté client.
  
Si vous avez besoin d’une validation supplémentaire de la propriété des itinéraires dans le peering public ExpressRoute, vous pouvez vérifier les itinéraires publiés par rapport à la liste de tous les préfixes IP IPv4 et IPv6 qui représentent [les plages d’adresses IP publiques de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Ces plages couvrent l’espace d’adressage Microsoft complet et changent rarement, fournissant un ensemble fiable de plages à filtrer par rapport à qui fournit également une protection supplémentaire aux clients qui sont préoccupés par les itinéraires non appartenant à Microsoft qui fuitent dans leur environnement. En cas de modification, elle est effectuée le 1er du mois et le numéro de version dans la section **détails** de la page change chaque fois que le fichier est mis à jour.
  
Il existe de nombreuses raisons d’éviter l’utilisation des [URL Office 365 et des plages d’adresses IP pour générer des listes de filtres](./urls-and-ip-address-ranges.md) de préfixe. Y compris les éléments suivants :
  
- Les préfixes IP Office 365 subissent fréquemment de nombreuses modifications.

- Les url Office 365 et les plages d’adresses IP sont conçues pour gérer les listes d’autorisation de pare-feu et l’infrastructure proxy, et non le routage.

- Les URL Office 365 et les plages d’adresses IP ne couvrent pas les autres services Microsoft qui peuvent être dans l’étendue de vos connexions ExpressRoute.

|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Accepter tous les itinéraires Microsoft  <br/> |**Faible:** Le client s’appuie sur les contrôles Microsoft pour s’assurer que tous les itinéraires sont correctement détenus.  <br/> |Aucun  <br/> |
|Filtrer les supernets appartenant à Microsoft  <br/> |**Moyen:** Le client implémente des listes de filtres de préfixe résumées pour autoriser uniquement les itinéraires appartenant à Microsoft.  <br/> |Les clients doivent s’assurer que les mises à jour peu fréquentes sont reflétées dans les filtres de routage.  <br/> |
|Filtrer Office 365 plages d’adresses IP  <br/> [!CAUTION] Not-Recommended |**Haute:** Le client filtre les itinéraires en fonction des préfixes OFFICE 365 IP définis.  <br/> |Les clients doivent implémenter un processus de gestion des modifications robuste pour les mises à jour mensuelles.  <br/> [!CAUTION] Cette solution nécessite des modifications importantes en cours. Les modifications non implémentées dans le temps entraîneront probablement une interruption de service.   |

La connexion à Office 365 à l’aide d’Azure ExpressRoute est basée sur des publicités BGP de sous-réseaux IP spécifiques qui représentent des réseaux où Office 365 points de terminaison sont déployés. En raison de la nature globale de Office 365 et du nombre de services qui composent Office 365, les clients ont souvent besoin de gérer les publicités qu’ils acceptent sur leur réseau. Si vous êtes concerné par le nombre de préfixes publiés dans votre environnement, la fonctionnalité [de communauté BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) vous permet de filtrer les publicités sur un ensemble spécifique de services Office 365. Cette fonctionnalité est maintenant en préversion.
  
Quelle que soit la façon dont vous gérez les annonces de routage BGP en provenance de Microsoft, vous ne bénéficiez pas d’une exposition spéciale aux services Office 365 par rapport à la connexion à Office 365 sur un seul circuit Internet. Microsoft maintient les mêmes niveaux de sécurité, de conformité et de performances, quel que soit le type de circuit utilisé par un client pour se connecter à Office 365.
  
### <a name="security"></a>Sécurité

Microsoft vous recommande de gérer vos propres contrôles de périmètre de réseau et de sécurité pour les connexions allant et depuis le peering Public ExpressRoute et Microsoft, qui incluent les connexions vers et depuis Office 365 services. Des contrôles de sécurité doivent être en place pour les demandes réseau sortantes de votre réseau vers le réseau de Microsoft et entrantes depuis le réseau de Microsoft vers votre réseau.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Sortant du client vers Microsoft
  
Lorsque les ordinateurs se connectent à Office 365, ils se connectent au même ensemble de points de terminaison, que la connexion soit établie via un circuit Internet ou ExpressRoute. Quel que soit le circuit utilisé, Microsoft vous recommande de traiter Office 365 services comme plus fiables que les destinations Internet génériques. Vos contrôles de sécurité sortants doivent se concentrer sur les ports et les protocoles pour réduire l’exposition et réduire la maintenance continue. Les informations de port requises sont disponibles dans l’article de référence [sur les points de terminaison Office 365](./urls-and-ip-address-ranges.md).
  
Pour les contrôles ajoutés, vous pouvez utiliser le filtrage au niveau du nom de domaine complet au sein de votre infrastructure proxy pour restreindre ou inspecter une partie ou l’ensemble des demandes réseau destinées à Internet ou Office 365. La gestion de la liste des noms de domaine complets à mesure que les fonctionnalités sont publiées et que les offres de Office 365 évoluent nécessitent une gestion des modifications plus robuste et un suivi des modifications [apportées aux points](./urls-and-ip-address-ranges.md) de terminaison Office 365 publiés.
  
> [!CAUTION]
> Microsoft vous recommande de ne pas vous fier uniquement aux préfixes IP pour gérer la sécurité sortante pour Office 365.

|**Option**|**Complexité**|**Modifier le contrôle**|
|:-----|:-----|:-----|
|Aucune restriction  <br/> |**Faible:** Le client autorise un accès sortant illimité à Microsoft.  <br/> |Aucun  <br/> |
|Restrictions de port  <br/> |**Faible:** Le client restreint l’accès sortant à Microsoft par les ports attendus.  <br/> |Rares.  <br/> |
|Restrictions relatives au nom de domaine complet  <br/> |**Haute:** Le client restreint l’accès sortant aux Office 365 en fonction des noms de domaine complets publiés.  <br/> |Modifications mensuelles.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Entrant de Microsoft vers le client
  
Il existe plusieurs scénarios facultatifs qui nécessitent que Microsoft établisse des connexions à votre réseau.
  
- ADFS lors de la validation du mot de passe pour la connexion.

- [Exchange Server déploiements hybrides](/exchange/exchange-hybrid).

- Courrier d’un locataire Exchange Online vers un hôte local.

- SharePoint courrier en ligne envoyé de SharePoint Online à un hôte local.

- [SharePoint recherche hybride fédérée](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS hybride](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype Entreprise fédération hybride](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) et/ou [Skype Entreprise](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype Entreprise Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

Microsoft vous recommande d’accepter ces connexions sur votre circuit Internet au lieu de votre circuit ExpressRoute pour réduire la complexité. Si vos besoins en matière de conformité ou de performances déterminent que ces connexions entrantes doivent être acceptées sur un circuit ExpressRoute, il est recommandé d’utiliser un pare-feu ou un proxy inverse pour étendre les connexions acceptées. Vous pouvez utiliser les [points de terminaison Office 365](./urls-and-ip-address-ranges.md) pour déterminer les noms de domaine complets et les préfixes IP appropriés.
  
### <a name="compliance"></a>Conformité

Nous ne nous appuyons pas sur le chemin de routage que vous utilisez pour l’un de nos contrôles de conformité. Que vous vous connectiez à Office 365 services via un circuit ExpressRoute ou Internet, nos contrôles de conformité ne changeront pas. Vous devez passer en revue les différents niveaux de conformité et de certification de sécurité pour Office 365 afin de déterminer le meilleur choix pour répondre aux besoins de votre organisation.
  
Voici un lien que vous pouvez utiliser pour revenir : [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>Voir aussi

[Réseaux de distribution de contenu](content-delivery-networks.md)
  
[URL et plages d’adresses IP Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute for Office 365 Training](https://channel9.msdn.com/series/aer)