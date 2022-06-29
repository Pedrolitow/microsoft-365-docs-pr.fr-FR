---
title: URLs et plages d’adresses IP pour Office 365 géré par 21Vianet
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/01/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
ms.openlocfilehash: e99a89e511faef069f0856e046ea1898e896b3c1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489900"
---
# <a name="urls-and-ip-address-ranges-for-office-365-operated-by-21vianet"></a>URLs et plages d’adresses IP pour Office 365 géré par 21Vianet

 *S’applique à : Office 365 géré par 21Vianet- Administrateur Petite Entreprise, Office 365 géré par 21Vianet-Administrateur*

**Résumé**: les points de terminaison suivants (FQDNs, ports, URL, IPv4 et IPv6 préfixes) s’appliquent à Office 365 géré par 21 Vianet et sont prévus pour fournir des services de productivité aux organisations qui n’utilisent que ces offres.
  
 **points de terminaison Office 365 :** [Dans le monde entier (y compris gcc)](urls-and-ip-address-ranges.md)  | *Office 365 exploités par 21 Vianet* |  [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) |  [Office 365 U.S. Government GCC High](microsoft-365-u-s-government-gcc-high-endpoints.md) |
  
**Dernière mise à jour :** 01/06/2022 - ![RSS.](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Abonnement au journal des modifications](https://endpoints.office.com/version/China?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)

**Téléchargement :** toutes les destinations obligatoires et facultatives dans une liste [au format JSON](https://endpoints.office.com/endpoints/China?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Commencez avec la [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) afin de comprendre nos recommandations pour gérer la connectivité réseau à l’aide de ces données. Les données de points de terminaison sont mises à jour au début de chaque mois avec de nouvelles adresses IP et URL publiées 30 jours avant d’être activées. Cela permet aux clients qui n’ont pas encore de mises à jour automatisées de terminer leurs processus avant qu’une nouvelle connectivité soit requise. Les points de terminaison peuvent également être mis à jour au cours du mois si besoin pour traiter les demandes de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données contenues sur la page ci-dessous sont générées à partir des services web REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devriez aller directement au [service web](microsoft-365-ip-web-service.md).

Les données de point de terminaison ci-dessous répertorient les exigences de connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Elles n’incluent pas les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides.

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER** : cette option est définie sur **Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La Communauté BGP qui inclut les préfixes d’itinéraire indiqués s’aligne avec la zone de service répertoriée. Quand ER est défini sur **Non**, cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, le fait qu’ER soit défini sur **Non** ne signifie pas pour autant qu’aucun itinéraire n’est proposé pour un ensemble de points de terminaison.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports**: Répertorie les ports TCP ou UDP qui sont combinées avec les adresses pour former le point de terminaison réseau. Vous remarquerez peut-être que certains duplication dans les plages d’adresses IP lorsqu’il y a des ports différents répertoriés.

[!INCLUDE [Office 365 operated by 21Vianet endpoints](../includes/office-365-operated-by-21vianet-endpoints.md)]