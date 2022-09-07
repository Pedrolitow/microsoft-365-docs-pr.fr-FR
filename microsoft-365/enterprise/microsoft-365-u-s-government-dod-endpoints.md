---
title: Office 365 points de terminaison DOD du gouvernement des États-Unis
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 08/29/2022
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
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
description: Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent Office 365 plans DoD du gouvernement des États-Unis uniquement.
hideEdit: true
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 7328fce563dccae912125696c60aba0247718910
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67611867"
---
# <a name="office-365-us-government-dod-endpoints"></a>Office 365 points de terminaison DoD du gouvernement des États-Unis

*S’applique à : Office 365 Admin*

Office 365 nécessite une connexion à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent Office 365 plans DoD du gouvernement des États-Unis uniquement.
  
**points de terminaison Office 365 :** [dans le monde entier (y compris le GCC)](urls-and-ip-address-ranges.md) \| [Office 365 exploités par 21 vianet](urls-and-ip-address-ranges-21vianet.md) \| *Office 365 U.S. Government DoD* \| [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md)

<br>
****

|Remarques|Télécharger|
|---|---|
|**Dernière mise à jour :** 29/08/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|**Télécharger :** la liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)|
|

Commencez par [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données du point de terminaison sont mis à jour sont mises à jour au besoin au début de chaque mois avec de nouvelles adresses IP et URL publiés 30 jours avant d’être activé(e). Cela permet aux clients qui n’ont pas encore de mises à jour automatisées de terminer leurs processus avant que la nouvelle connectivité ne soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour les demandes des remontés de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services web REST. Si vous utilisez un script ou un appareil réseau pour accéder à ces données, vous devez accéder directement au [service Web](microsoft-365-ip-web-service.md) .

Les données de point de terminaison ci-dessous répertorient les conditions requises pour la connectivité de l’ordinateur d’un utilisateur à Office 365. Il n’inclut pas les connexions réseau de Microsoft à un réseau client, parfois appelé connexions réseau hybrides ou entrantes. Pour plus d’informations, consultez [Points de terminaison supplémentaires non inclus dans le service web](additional-office365-ip-addresses-and-urls.md).

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est classé comme « Optimiser », « Autoriser » ou « Par défaut ». Vous pouvez en savoir plus sur ces catégories et des conseils pour leur gestion à l’adresse [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Cette colonne répertorie également les ensembles de points de terminaison requis pour avoir une connectivité réseau. Pour les ensembles de points de terminaison qui n’ont pas besoin d’une connectivité réseau, nous fournissons des notes dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez une zone de service entière, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER** : **Oui si** l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec Office 365 préfixes d’itinéraire. La communauté BGP qui inclut les préfixes d’itinéraire affichés s’aligne sur la zone de service répertoriée. Quand ER est **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne faut pas supposer qu’aucun itinéraire n’est publié pour un ensemble de points de terminaison où ER est **Non**. Si vous envisagez d’utiliser Azure AD Connect, lisez la [section des considérations spéciales](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) pour vous assurer que vous disposez de la configuration Azure AD Connect appropriée.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.

- **Ports** : répertorie les ports TCP ou UDP associés aux adresses pour former le point de terminaison réseau. Vous remarquerez peut-être certains doublons dans les plages d’adresses IP lorsque plusieurs ports sont répertoriés.

[!INCLUDE [Office 365 U.S. Government DoD endpoints](../includes/office-365-u.s.-government-dod-endpoints.md)]
  
Remarques à propos de ce tableau :

- Le Centre de sécurité et de conformité (SCC) prend en charge Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités exposées via la SCC, telles que la création de rapports, l’audit, la découverte électronique (Premium), la protection contre la perte de données unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, PST Import et eDiscovery Export, ne prennent actuellement pas en charge Azure ExpressRoute avec seulement Office 365 filtres de routage en raison de leur dépendance à Stockage Blob Azure. Pour utiliser ces fonctionnalités, vous devez disposer d’une connectivité distincte pour Stockage Blob Azure à l’aide de toutes les options de connectivité Azure prises en charge, notamment la connectivité Internet ou Azure ExpressRoute avec des filtres de routage public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour ces deux fonctionnalités. L’équipe Office 365 Information Protection est consciente de cette limitation et travaille activement à la prise en charge d’Azure ExpressRoute pour Office 365 comme limité à Office 365 filtres de routage pour ces deux fonctionnalités.

- D’autres points de terminaison facultatifs pour les Applications Microsoft 365 pour les grandes entreprises ne sont pas répertoriés et ne sont pas nécessaires pour que les utilisateurs lancent Applications Microsoft 365 pour les grandes entreprises applications et modifient des documents. Les points de terminaison facultatifs sont hébergés dans des centres de données Microsoft et ne traitent pas, ne transmettent ni ne stockent les données client. Nous recommandons que les connexions utilisateur à ces points de terminaison soient dirigées vers le périmètre de sortie Internet par défaut.
