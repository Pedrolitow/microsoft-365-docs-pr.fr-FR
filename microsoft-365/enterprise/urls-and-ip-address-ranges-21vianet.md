---
title: URLs et plages d’adresses IP pour Office 365 géré par 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/28/2022
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- GMA150
- GPA150
- GEA150
ms.assetid: 5c47c07d-f9b6-4b78-a329-bfdc1b6da7a0
ms.custom: seo-marvel-apr2020
f1.keywords:
- NOCSH
description: Cet article répertorie les URL et les plages d’adresses IP pour Office 365 lorsqu’elles sont exploitées par 21Vianet en Chine.
hideEdit: true
ms.openlocfilehash: 477b3918f7a4d86628efd1a23a45c97e80e10e74
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68199040"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>URLs et plages d’adresses IP pour Office 365 géré par 21Vianet

 *S’applique à : Office 365 géré par 21Vianet- Administrateur Petite Entreprise, Office 365 géré par 21Vianet-Administrateur*

**Résumé**: les points de terminaison suivants (FQDNs, ports, URL, IPv4 et IPv6 préfixes) s’appliquent à Office 365 géré par 21 Vianet et sont prévus pour fournir des services de productivité aux organisations qui n’utilisent que ces offres.
  
 **points de terminaison Office 365 :** [Dans le monde entier (y compris gcc)](urls-and-ip-address-ranges.md)  | *Office 365 exploités par 21 Vianet* |  [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Dernière mise à jour :** 28/07/2022 : ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated as needed at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](microsoft-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Les colonnes de données affichées sont :

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]