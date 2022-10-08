---
title: Points de terminaison Office 365 U.S. Government GCC High
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/29/2022
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Dans cet article, vous trouverez des points de terminaison accessibles aux clients qui utilisent Office 365 plans GCC High du gouvernement des États-Unis.
hideEdit: true
ms.openlocfilehash: cde1037c30788182fe1982390f7d0a76e0b9d77b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68165468"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Points de terminaison Office 365 U.S. Government GCC High

*S’applique à : Office 365 Admin*

Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent Office 365 plans GCC High du gouvernement des États-Unis uniquement.
  
 **points de terminaison Office 365 :** [dans le monde entier (y compris le GCC)](urls-and-ip-address-ranges.md) \| [Office 365 exploités par 21 vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) \| *Office 365 U.S. Government GCC High*

<br>

****

|Remarques|Télécharger|
|---|---|
|**Dernière mise à jour :** 29/06/2022 – ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Télécharger :** la liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

 Commencez par [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données du point de terminaison sont mis à jour sont mises à jour au besoin au début de chaque mois avec de nouvelles adresses IP et URL publiés 30 jours avant d’être activé(e). Cela permet aux clients qui n’ont pas encore de mises à jour automatisées de terminer leurs processus avant que la nouvelle connectivité ne soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour les demandes des remontés de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services web REST. Si vous utilisez un script ou un appareil réseau pour accéder à ces données, vous devez accéder directement au [service Web](microsoft-365-ip-web-service.md) .

Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Les colonnes de données affichées sont :

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Catégorie** : indique si l’ensemble de points de terminaison est classé comme « Optimiser », « Autoriser » ou « Par défaut ». Vous pouvez en savoir plus sur ces catégories et des conseils pour leur gestion à l’adresse [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Cette colonne répertorie également les ensembles de points de terminaison requis pour avoir une connectivité réseau. Pour les ensembles de points de terminaison qui ne sont pas requis pour avoir une connectivité réseau, nous fournissons des notes dans ce champ pour indiquer les fonctionnalités qui manquent si l’ensemble de points de terminaison est bloqué. Si vous excluez une zone de service entière, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER** : **Oui si** l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec Office 365 préfixes d’itinéraire. La communauté BGP qui inclut les préfixes d’itinéraire affichés s’aligne sur la zone de service répertoriée. Quand ER est **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne faut pas supposer qu’aucun itinéraire n’est publié pour un ensemble de points de terminaison où ER est **Non**. Si vous envisagez d’utiliser Azure AD Connect, lisez la [section des considérations spéciales](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) pour vous assurer que vous disposez de la configuration Azure AD Connect appropriée.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.

- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 U.S. Government GCC High endpoints](../includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Remarques à propos de ce tableau :

- Le Centre de sécurité et de conformité (SCC) prend en charge Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités exposées via la SCC, telles que la création de rapports, l’audit, la découverte électronique (Premium), la protection contre la perte de données unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, PST Import et eDiscovery Export, ne prennent actuellement pas en charge Azure ExpressRoute avec seulement Office 365 filtres de routage en raison de leur dépendance à Stockage Blob Azure. Pour utiliser ces fonctionnalités, vous devez disposer d’une connectivité distincte pour Stockage Blob Azure à l’aide de toutes les options de connectivité Azure prises en charge, notamment la connectivité Internet ou Azure ExpressRoute avec des filtres de routage public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour ces deux fonctionnalités. L’équipe Office 365 Information Protection est consciente de cette limitation et travaille activement à la prise en charge d’Azure ExpressRoute pour Office 365 comme limité à Office 365 filtres de routage pour ces deux fonctionnalités.

- D’autres points de terminaison facultatifs pour les Applications Microsoft 365 pour les grandes entreprises ne sont pas répertoriés et ne sont pas nécessaires pour que les utilisateurs lancent Applications Microsoft 365 pour les grandes entreprises applications et modifient des documents. Les points de terminaison facultatifs sont hébergés dans des centres de données Microsoft et ne traitent pas, ne transmettent ni ne stockent les données client. Nous recommandons que les connexions utilisateur à ces points de terminaison soient dirigées vers le périmètre de sortie Internet par défaut.
