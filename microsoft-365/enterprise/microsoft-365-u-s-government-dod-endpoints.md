---
title: Office 365 Points de terminaison DOD pour le gouvernement américain
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/28/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent Office 365 les plans DoD du gouvernement américain uniquement.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 32a760843453a4d243ee65802325852323402140
ms.sourcegitcommit: 4886457c0d4248407bddec56425dba50bb60d9c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2021
ms.locfileid: "53286428"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 Points de terminaison DoD pour le gouvernement américain

*S’applique à : Office 365 Admin*

Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent Office 365 les plans DoD du gouvernement américain uniquement.
  
**Office 365** points de terminaison : Office 365 internationaux (y compris [Cloud de la communauté du secteur public)](urls-and-ip-address-ranges.md) gérés par \| [21 Vianet](urls-and-ip-address-ranges-21vianet.md) \| [Office 365 Germany](microsoft-365-germany-endpoints.md) Office 365 \| *U.S. Government DoD* Office 365 \| [U.S. Government Cloud de la communauté du secteur public High](microsoft-365-u-s-government-gcc-high-endpoints.md)

<br>

****

|Notes|Télécharger|
|---|---|
|**Dernière mise à jour :** 28/05/2021 : ![RSS](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Modifier l'abonnement au journal](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Télécharger :** la liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

Commencez par [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données du point de terminaison sont mis à jour sont mises à jour au besoin au début de chaque mois avec de nouvelles adresses IP et URL publiés 30 jours avant d’être activé(e). Cela permet aux clients qui n’ont pas encore de mises à jour automatisées d’effectuer leurs processus avant qu’une nouvelle connectivité soit nécessaire. Les points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour les demandes des remontés de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services web REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au [service web](microsoft-365-ip-web-service.md).

Les données de point de terminaison ci-dessous répertorient les conditions requises pour la connectivité de l’ordinateur d’un utilisateur Office 365. Il n’inclut pas les connexions réseau de Microsoft à un réseau client, parfois appelées connexions réseau hybrides ou entrantes. Pour plus d’informations, voir [Points de terminaison supplémentaires non inclus dans le service web.](additional-office365-ip-addresses-and-urls.md)

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER :** il s’agit **de Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute Office 365 préfixes d’itinéraire. La communauté BGP qui inclut les préfixes d’itinéraire indiqués s’aligne sur la zone de service répertoriée. Lorsque ER est **Non,** cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne doit pas être supposé qu’aucun itinéraire n’est publié pour un ensemble de points de terminaison où ER est **Non**. Si vous envisagez d’utiliser Azure AD Connecter, lisez la section des [considérations](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) spéciales pour vous assurer que vous avez la configuration azure AD Connecter appropriée.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.

- **Ports** : répertorie les ports TCP ou UDP associés aux adresses pour former le point de terminaison réseau. Vous remarquerez peut-être certains doublons dans les plages d’adresses IP lorsque plusieurs ports sont répertoriés.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Remarques à propos de ce tableau :

- Le Centre de sécurité et conformité (SCC) fournit la prise en charge d’Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités exposées par le biais du SCC, telles que la gestion des rapports, l’audit, Advanced eDiscovery, la DLP unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, importation PST et exportation eDiscovery, ne permettent actuellement pas de prendre en charge Azure ExpressRoute avec uniquement des filtres d’itinéraire Office 365 en raison de leur dépendance à Azure Blob Stockage. Pour utiliser ces fonctionnalités, vous avez besoin d’une connectivité distincte à Azure Blob Stockage à l’aide de toutes les options de connectivité Azure supportables, qui incluent la connectivité Internet ou Azure ExpressRoute avec des filtres d’itinéraire public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour ces deux fonctionnalités. L’équipe Office 365 Information Protection est au courant de cette limitation et travaille activement pour prendre en charge Azure ExpressRoute pour Office 365 comme limité aux filtres d’itinéraire Office 365 pour ces deux fonctionnalités.

- Il existe d’autres points de terminaison facultatifs pour Applications Microsoft 365 pour les grandes entreprises qui ne sont pas répertoriés et qui ne sont pas requis pour que les utilisateurs lancent des applications Applications Microsoft 365 pour les grandes entreprises et modifient des documents. Les points de terminaison facultatifs sont hébergés dans les centres de données Microsoft et ne traiter, ne transmettent pas ou ne stockent pas de données client. Nous recommandons que les connexions utilisateur à ces points de terminaison soient dirigées vers le périmètre de sortie Internet par défaut.
