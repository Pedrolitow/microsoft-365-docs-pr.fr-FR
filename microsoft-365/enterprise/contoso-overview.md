---
title: Présentation de la société Contoso Corporation
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre le fonctionnement de la société Contoso Corporation et la hiérarchie de ses bureaux internationaux.
ms.openlocfilehash: 206017744a004ba4e51b6e0d157b172cbe145c66
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686451"
---
# <a name="overview-of-the-contoso-corporation"></a>Présentation de la société Contoso Corporation

![Société Contoso](../media/contoso-overview/contoso-icon.png)

La société Contoso est une entreprise internationale dont le siège est à Paris. Il s’agit d’un conglomérat de production, de ventes et de service après-vente comptant plus de 100 000 produits.

## <a name="contoso-around-the-world"></a>Contoso dans le monde

Dans la Figure 1, le siège social de l’entreprise se situe à Paris, tandis que ses centres régionaux et ses succursales sont répartis sur plusieurs continents.

![Bureaux internationaux de Contoso](../media/contoso-overview/contoso-overview-fig1.png)

**Figure 1 : bureaux internationaux de Contoso**
 
Les bureaux internationaux de Contoso sont organisés en trois niveaux.

- Siège social

  Le siège social de Contoso Corporation s’intègre à une vaste zone d’activité, dans la banlieue parisienne, comportant des dizaines de bâtiments pour l’administration, l’ingénierie et la fabrication. Tous les centres de données de Contoso et la présence Internet résident dans le siège social.

  Le siège social compte 25 000 collaborateurs.

- Centres régionaux

  Les centres régionaux sont implantés dans différentes régions du monde et possèdent 60 % des équipes des ventes et du support technique. Chaque centre régional est relié au siège social grâce à une connexion WAN haut débit. 

  Chaque centre régional compte en moyenne 2 000 collaborateurs.

- Succursales

  Les succursales représentent 80 % des ventes et du personnel d’assistance et offrent une présence physique et sur site aux clients de Contoso dans les villes importantes ou des régions plus petites. Chaque succursale est connectée à un centre régional par le biais d’un lien WAN haut débit.

  Chaque succursale compte en moyenne 250 collaborateurs.

25 % des collaborateurs de Contoso travaillent en permanence sur le terrain. Ce pourcentage est supérieur dans les centres régionaux et les succursales.
Pour Contoso, il est essentiel de fournir un meilleur support technique aux collaborateurs qui passent tout leur temps sur le terrain.

## <a name="design-considerations-for-microsoft-365-for-enterprise"></a>Considérations relatives à la conception de Microsoft 365 pour les entreprises

Les architectes informatiques de contoso ont identifié les conditions requises et les considérations suivantes lors du déploiement de Microsoft 365 pour Enterprise : 

- Plusieurs implantations géographiques avec des réglementations et des exigences de conformité locales
- Un centre de données intranet central dans les locaux du siège social et des serveurs d’application régionaux qui hébergent en interne la gamme d’applications professionnelles
- Une infrastructure existante du Microsoft Endpoint Configuration Manager
- Un mélange d’appareils informatiques clients, comprenant Windows, Mac et Linux
- Un mélange d’appareils mobiles personnels et entreprise, notamment smartphones et tablettes iOS (iPhone et iPad) et Android
- Nombreux collaborateurs en télétravail et mobiles
- Nombreux partenaires commerciaux
- Une grande quantité de d’informations client et informations d’identification personnelle
- Une grande quantité de propriété intellectuelle de qualité sous forme de directives de conception pour les produits et de secrets commerciaux fabrication

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-infra-needs.md) l’infrastructure informatique locale de Contoso Corporation et les besoins de son entreprise avec Microsoft 365 pour les entreprises.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)



