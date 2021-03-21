---
title: Points de terminaison Office 365 pour le gouvernement américain GCC High
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 01/28/2021
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid: MET150
ms.assetid: cbd2369c-fd96-464c-bf48-c99826b459ee
description: Dans cet article, vous trouverez des points de terminaison accessibles pour les clients qui utilisent les plans Office 365 pour le gouvernement américain GCC High.
hideEdit: true
ms.openlocfilehash: 4089be4e3e28493afc27972d77f30bca81364f37
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50923873"
---
# <a name="office-365-us-government-gcc-high-endpoints"></a>Points de terminaison Office 365 pour le gouvernement américain GCC High

 *S’applique à : Administrateur Office 365*

Office 365 nécessite une connectivité à Internet. Les points de terminaison ci-dessous doivent être accessibles aux clients qui utilisent office 365 pour le gouvernement américain GCC High uniquement.
  
 **Points de terminaison Office 365:**[Dans le monde ( GCC inclus)](urls-and-ip-address-ranges.md) | [Office 365 géré par 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](microsoft-365-germany-endpoints.md)  | [Office 365 U.S. Government DoD](microsoft-365-u-s-government-dod-endpoints.md) | *Office 365 U.S. Government GCC High* |
  
|||
|:-----|:-----|
|**Last updated:** 28/01/2021 - ![ RSS Change Log ](../media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [subscription](https://endpoints.office.com/version/USGOVGCCHigh?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |**Télécharger :** la liste complète au [format JSON](https://endpoints.office.com/endpoints/USGOVGCCHigh?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Commencez par [Gestion des points de terminaison Office 365](managing-office-365-endpoints.md) pour comprendre nos recommandations en matière de gestion de la connectivité réseau à l’aide de ces données. Les données du point de terminaison sont mis à jour sont mises à jour au besoin au début de chaque mois avec de nouvelles adresses IP et URL publiés 30 jours avant d’être activé(e). Cela permet aux clients qui n’ont pas encore de mises à jour automatisées d’effectuer leurs processus avant qu’une nouvelle connectivité soit nécessaire. Les points de terminaison peuvent également être mis à jour au cours du mois si nécessaire pour les demandes des remontés de support, les incidents de sécurité ou autres exigences opérationnelles immédiates. Les données affichées sur cette page ci-dessous sont toutes générées à partir des services web REST. Si vous utilisez un script ou un périphérique réseau pour accéder à ces données, vous devez accéder directement au [service web](microsoft-365-ip-web-service.md).

Les données de point de terminaison ci-dessous répertorient les exigences de connectivité à partir de l’ordinateur d’un utilisateur vers Office 365. Elles n’incluent pas les connexions réseau de Microsoft vers un réseau client, parfois appelées connexions réseau entrantes ou hybrides.

Les points de terminaison sont regroupés en quatre zones de service. Les trois premières zones de service peuvent être sélectionnées indépendamment pour la connectivité. La quatrième zone de service est une dépendance courante (appelée Microsoft 365 Common et Office) et doit toujours avoir une connectivité réseau.

Les colonnes de données affichées sont :

- **ID** : numéro d’identification de la ligne, également connu sous forme d’un ensemble de points de terminaison. Cet ID est le même que celui retourné par le service web pour l’ensemble de points de terminaison.

- **Catégorie** : indique si l’ensemble de points de terminaison est associé à la classe « Optimiser », « Autoriser » ou « Par défaut ». Des informations sur ces catégories et des instructions pour les gérer sont disponibles dans la rubrique [https://aka.ms/pnc](./microsoft-365-network-connectivity-principles.md). Cette colonne répertorie également les ensembles de points de terminaison nécessaires pour que la connectivité réseau fonctionne. Pour les ensembles de points de terminaison qui ne nécessitent pas de connectivité réseau, nous fournissons des remarques dans ce champ pour indiquer les fonctionnalités manquantes si l’ensemble de points de terminaison est bloqué. Si vous excluez l’ensemble d’une zone de service, les ensembles de points de terminaison répertoriés comme requis ne nécessitent pas de connectivité.

- **ER :** il s’agit **de Oui** si l’ensemble de points de terminaison est pris en charge sur Azure ExpressRoute avec des préfixes d’itinéraire Office 365. La communauté BGP qui inclut les préfixes d’itinéraire indiqués s’aligne sur la zone de service répertoriée. Lorsque ER est **Non,** cela signifie qu’ExpressRoute n’est pas pris en charge pour cet ensemble de points de terminaison. Toutefois, il ne doit pas être supposé qu’aucun itinéraire n’est publié pour un ensemble de points de terminaison où ER est **Non**. Si vous envisagez d’utiliser Azure AD Connect, lisez la section des [considérations](/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) spéciales pour vous assurer que vous avez la configuration Azure AD Connect appropriée.

- **Adresses** : répertorie les noms de domaine complets ou noms de domaines génériques et plages d’adresses IP pour l’ensemble de points de terminaison. Notez qu’une plage d’adresses IP est au format CIDR et peut inclure plusieurs adresses IP individuelles dans le réseau spécifié.
 
- **Ports** : répertorie les ports TCP ou UDP associés aux adresses pour former le point de terminaison réseau. Vous remarquerez peut-être certains doublons dans les plages d’adresses IP lorsque plusieurs ports sont répertoriés.
 
[!INCLUDE [Office 365 U.S. Government GCC High endpoints](../includes/office-365-u.s.-government-gcc-high-endpoints.md)]

Remarques à propos de ce tableau :

- Le Centre de sécurité et conformité (SCC) fournit la prise en charge d’Azure ExpressRoute pour Office 365. Il en va de même pour de nombreuses fonctionnalités exposées via le SCC, telles que la rapport, l’audit, advanced eDiscovery, la DLP unifiée et la gouvernance des données. Deux fonctionnalités spécifiques, importation PST et exportation eDiscovery, ne permettent actuellement pas de prendre en charge Azure ExpressRoute avec uniquement des filtres d’itinéraire Office 365 en raison de leur dépendance sur le stockage d’objets blob Azure. Pour utiliser ces fonctionnalités, vous avez besoin d’une connectivité distincte au stockage d’objets blob Azure à l’aide de toutes les options de connectivité Azure supportables, qui incluent la connectivité Internet ou Azure ExpressRoute avec des filtres d’itinéraire public Azure. Vous devez évaluer l’établissement d’une telle connectivité pour ces deux fonctionnalités. L’équipe De protection des informations Office 365 connaît cette limitation et travaille activement pour prendre en charge Azure ExpressRoute pour Office 365 comme limité aux filtres d’itinéraire Office 365 pour ces deux fonctionnalités.

- D’autres points de terminaison facultatifs pour Microsoft 365 Apps for enterprise ne sont pas répertoriés et ne sont pas requis pour que les utilisateurs lancent les applications Microsoft 365 Apps for enterprise et modifient des documents. Les points de terminaison facultatifs sont hébergés dans des centres de données Microsoft et ne traiter, ne transmettent pas ou ne stockent pas de données client. Nous recommandons que les connexions utilisateur à ces points de terminaison soient dirigées vers le périmètre de sortie Internet par défaut.