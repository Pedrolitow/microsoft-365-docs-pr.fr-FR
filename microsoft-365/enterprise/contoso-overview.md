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

Contoso Corporation est une entreprise multinationale avec son siège social à Paris. La société est une organisation de fabrication, de ventes et de support technique avec plus de 100 000 produits.

## <a name="contoso-around-the-world"></a>Contoso dans le monde

La figure 1 présente le siège social dans la région de Paris, le Hub régional et les bureaux satellites sur plusieurs continents.

![Bureaux de Contoso dans le monde entier](../media/contoso-overview/contoso-overview-fig1.png)

**Figure 1 : bureaux de Contoso dans le monde entier**
 
Contoso dispose de trois niveaux de bureaux :

- Headquarters

  Le siège social de contoso est un campus d’entreprise sur les hampes de Paris avec des dizaines de bâtiments pour les installations d’administration, d’ingénierie et de fabrication. Tous les centres de recherche contoso et sa présence sur Internet sont hébergés dans le siège de Paris.

  Le siège social compte 25 000 collaborateurs.

- Centres régionaux

  Les bureaux de Hub servent une région spécifique du monde à des ventes et des équipes de support technique de 60%. Chaque concentrateur régional est connecté au siège de Paris via une liaison WAN à bande passante élevée.

  Les hubs régionaux ont une moyenne de 2 000 travailleurs.

- Succursales

  Les bureaux satellites contiennent des équipes de support et de vente de 80%. Elles fournissent une présence sur site pour les clients Contoso dans les principales villes ou sous-régions. Chaque bureau satellite est connecté à un concentrateur régional via une liaison WAN à bande passante élevée.

  Les bureaux satellites ont une moyenne de 250 travailleurs.

Environ 25% de la main-d’œuvre contoso est mobile uniquement. Les hubs régionaux et les bureaux satellites ont un pourcentage supérieur de ces travailleurs. Fournir une meilleure prise en charge pour les travailleurs mobiles uniquement est un objectif professionnel important pour contoso.

## <a name="design-considerations-for-microsoft-365-for-enterprise"></a>Considérations relatives à la conception de Microsoft 365 pour les entreprises

Les architectes informatiques de contoso ont identifié les facteurs de conditions de conception suivants pour le déploiement de Microsoft 365 pour les entreprises :

- Plusieurs implantations géographiques avec des réglementations et des exigences de conformité locales
- Un centre de contenu intranet central dans le siège social et les serveurs d’applications régionales qui hébergent des applications métiers internes
- Une infrastructure existante du Microsoft Endpoint Configuration Manager
- Un mélange d’appareils informatiques clients qui exécutent Windows, Mac et Linux
- Un mélange d’appareils mobiles personnels et entreprise, notamment smartphones et tablettes iOS (iPhone et iPad) et Android
- Nombreux collaborateurs en télétravail et mobiles
- Nombreux partenaires commerciaux
- Un grand nombre de clients et d’autres informations personnelles confidentielles à gérer et à sécuriser
- Une grande quantité de propriété intellectuelle de qualité sous forme de directives de conception pour les produits et de secrets commerciaux fabrication

## <a name="next-step"></a>Étape suivante

Découvrez l' [infrastructure informatique locale de](contoso-infra-needs.md) Contoso Corporation et la façon dont les besoins de l’entreprise sont abordés avec Microsoft 365 pour les entreprises.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
