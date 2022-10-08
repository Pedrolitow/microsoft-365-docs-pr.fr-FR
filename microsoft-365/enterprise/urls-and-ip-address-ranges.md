---
title: URL et plages d’adresses IP Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/29/2022
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: b52c3a4e197fa69e8db85e6ea1a542dd754b16f1
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68191832"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>URL et plages d’adresses IP Office 365

Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
*Office 365 dans le monde entier (+Cloud de la communauté du secteur public)*\|[Office 365 géré par 21 vianet](urls-and-ip-address-ranges-21vianet.md)\|[Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) \|

|Remarques|Télécharger|Utilisation|
|---|---|---|
|**Dernière mise à jour :** 29/09/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).|**Utilisation :** nos [fichiers PAC](managing-office-365-endpoints.md#pacfiles) proxy|
|

Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated as needed at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This cadence allows for customers who don't yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you're using a script or a network device to access this data, you should go to the [Web service](microsoft-365-ip-web-service.md) directly.

Les données de point de terminaison ci-dessous répertorient les conditions requises pour la connectivité de l’ordinateur d’un utilisateur à Office 365. Pour plus d’informations sur les adresses IP utilisées pour les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides, voir [Points de terminaison supplémentaires](additional-office365-ip-addresses-and-urls.md) pour plus d’informations.

Les points de terminaison sont regroupés en quatre zones de service représentant les trois charges de travail principales et un ensemble de ressources communes. Les groupes peuvent être utilisés pour associer des flux de trafic à une application particulière, mais étant donné que les fonctionnalités consomment souvent des points de terminaison sur plusieurs charges de travail, ces groupes peuvent être utilisés pour limiter l’accès.

Les colonnes de données affichées sont :

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as **Optimize**, **Allow**, or **Default**. This column also lists which endpoint sets are required to have network connectivity. For endpoint sets that aren't required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you're excluding an entire service area, the endpoint sets listed as required don't require connectivity.

   Vous pouvez en savoir plus sur ces catégories et des conseils pour leur gestion dans [les nouvelles catégories de points de terminaison Office 365](microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories).

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set.

   Certains itinéraires peuvent être publiés dans plusieurs communautés BGP, ce qui permet aux points de terminaison d’une plage d’adresses IP donnée de traverser le circuit ER, mais ne sont toujours pas pris en charge. Dans tous les cas, la valeur de la colonne ER d’un jeu de points de terminaison donné doit être respectée. Pour plus d’informations sur les communautés BGP, consultez [Utilisation de communautés BGP dans les scénarios ExpressRoute pour Office 365](bgp-communities-in-expressroute.md#key-planning-considerations-to-using-bgp-communities).

- **Addresses**: Lists the FQDNs or wildcard domain names and IP address ranges for the endpoint set. Note that an IP address range is in CIDR format and may include many individual IP addresses in the specified network.

- **Ports**: Lists the TCP or UDP ports that are combined with listed IP addresses to form the network endpoint. You may notice some duplication in IP address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](../includes/office-365-worldwide-endpoints.md)]

> [!NOTE]
> Pour des recommandations sur les adresses IP et les URL de Yammer, voir [L'utilisation d'adresses IP codées en dur pour Yammer n'est pas recommandée](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592)sur le blog Yammer.

## <a name="related-topics"></a>Rubriques connexes

[Points de terminaison supplémentaires non inclus dans le service web pour URL et adresses IP Office 365](additional-office365-ip-addresses-and-urls.md)

[Gestion des points de terminaison Office 365](managing-office-365-endpoints.md)

[Terminaux généraux Microsoft Stream ](/stream/network-overview#general-microsoft-stream-endpoints)
  
[Surveiller la connectivité Microsoft 365](./monitor-connectivity.md)

[L'AC racine et l'AC intermédiaire se regroupent sur le système d'application tiers](../compliance/encryption-office-365-certificate-chains.md)
  
[Connectivité des clients](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Réseaux de distribution de contenu](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - Cloud du gouvernement américain](https://www.microsoft.com/download/details.aspx?id=57063)

[Les gammes d'IP et les étiquettes de service de Microsoft Azure - China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Espace d’adresse IP public de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)

[Nom du service et protocole de transport Registre des numéros de port](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)
