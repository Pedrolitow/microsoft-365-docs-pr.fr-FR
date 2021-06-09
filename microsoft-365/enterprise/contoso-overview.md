---
title: Vue d’ensemble de Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre le fonctionnement de la société Contoso Corporation et la hiérarchie de ses bureaux internationaux.
ms.openlocfilehash: b0c00ed5657d914851f28278a2f4cf80660b53b0
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754267"
---
# <a name="overview-of-contoso-corporation"></a>Vue d’ensemble de Contoso Corporation

Contoso Corporation est une multinationale dont le siège social est à Paris. L’entreprise est une organisation de production, de vente et de support qui compte plus de 100 000 produits.

## <a name="contoso-around-the-world"></a>Contoso dans le monde

La figure 1 présente le siège social à Paris et les centres régionaux et les succursales sur différents continents.

![Bureaux Contoso dans le monde entier](../media/contoso-overview/contoso-overview-fig1.png)

**Figure 1 : Bureaux Contoso dans le monde entier**
 
Contoso possède trois niveaux de bureaux :

- Headquarters

  Le siège social de Contoso est un campus d’entreprise sur la périphérie de Paris avec des dizaines de bâtiments pour les installations administratives, d’ingénierie et de fabrication. Tous les centres de données Contoso et sa présence internet sont hébergés au siège social parisien.

  Le siège social compte 25 000 collaborateurs.

- Centres régionaux

  Les bureaux hub servent une région spécifique du monde avec 60 % de chiffre d’affaires et de personnel de support technique. Chaque hub régional est connecté au siège social parisien via une liaison WAN à bande passante élevée.

  Les centres régionaux ont en moyenne 2 000 travailleurs.

- Succursales

  Les succursales contiennent 80 % des ventes et du personnel de support technique. Ils fournissent une présence sur site pour les clients Contoso dans les villes clés ou sous-agrégations. Chaque bureau satellite est connecté à un hub régional via une liaison wan à bande passante élevée.

  Les succursales ont en moyenne 250 employés.

Environ 25 % des employés de Contoso sont mobiles uniquement. Les centres régionaux et les succursales ont un pourcentage plus élevé de ces employés. La fourniture d’une meilleure prise en charge des travailleurs mobiles uniquement est un objectif commercial important pour Contoso.

## <a name="design-considerations-for-microsoft-365-for-enterprise"></a>Considérations de conception pour Microsoft 365 entreprise

Les architectes informatiques de Contoso ont identifié les facteurs de conception requis suivants pour le déploiement Microsoft 365 entreprise :

- Plusieurs implantations géographiques avec des réglementations et des exigences de conformité locales
- Un centre de données intranet central dans les bureaux du siège social et les serveurs d’applications régionaux qui hébergent des applications métier internes
- Une infrastructure existante du Microsoft Endpoint Configuration Manager
- Combinaison d’appareils informatiques clients qui exécutent Windows, Mac et Linux
- Un mélange d’appareils mobiles personnels et entreprise, notamment smartphones et tablettes iOS (iPhone et iPad) et Android
- Nombreux collaborateurs en télétravail et mobiles
- Nombreux partenaires commerciaux
- Une grande quantité d’informations personnelles confidentielles et de clients à gérer et à sécuriser
- Une grande quantité de propriété intellectuelle de qualité sous forme de directives de conception pour les produits et de secrets commerciaux fabrication

## <a name="next-step"></a>Étape suivante

Découvrez [l’infrastructure](contoso-infra-needs.md) informatique locale de Contoso Corporation et la façon dont les besoins de l’entreprise sont traités avec Microsoft 365 entreprise.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
