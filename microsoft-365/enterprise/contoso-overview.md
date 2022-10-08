---
title: Vue d’ensemble de Contoso Corporation
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre le fonctionnement de la société Contoso Corporation et la hiérarchie de ses bureaux internationaux.
ms.openlocfilehash: dbaac2a60e47843d74ec13effe95a87049b8c9ea
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68178886"
---
# <a name="overview-of-contoso-corporation"></a>Vue d’ensemble de Contoso Corporation

Contoso Corporation est une multinationale dont le siège social est à Paris. L’entreprise est une organisation de fabrication, de vente et de support avec plus de 100 000 produits.

## <a name="contoso-around-the-world"></a>Contoso dans le monde

La figure 1 montre le siège social à Paris et les bureaux régionaux et satellites sur différents continents.

![Bureaux de Contoso dans le monde entier.](../media/contoso-overview/contoso-overview-fig1.png)

**Figure 1 : Bureaux de Contoso dans le monde entier**
 
Contoso a trois niveaux de bureaux :

- Headquarters

  Le siège social de Contoso est un campus d’entreprise à la périphérie de Paris, avec des dizaines de bâtiments pour des installations administratives, d’ingénierie et de fabrication. Tous les centres de données Contoso et sa présence sur Internet sont hébergés au siège de Paris.

  Le siège social compte 25 000 collaborateurs.

- Centres régionaux

  Les bureaux hubs desservent une région spécifique du monde avec un personnel de vente et de support de 60 %. Chaque hub régional est connecté au siège de Paris via une liaison WAN à bande passante élevée.

  Les hubs régionaux ont en moyenne 2 000 travailleurs.

- Succursales

  Les bureaux satellites contiennent 80 % du personnel de vente et de support technique. Ils fournissent une présence sur site pour les clients Contoso dans des villes clés ou des sous-régions. Chaque bureau satellite est connecté à un hub régional via une liaison WAN à bande passante élevée.

  Les bureaux satellites ont en moyenne 250 travailleurs.

Environ 25 % de la main-d’œuvre de Contoso est mobile uniquement. Les centres régionaux et les bureaux satellites ont un pourcentage plus élevé de ces travailleurs. Fournir un meilleur soutien aux travailleurs mobiles est un objectif commercial important pour Contoso.

## <a name="design-considerations-for-microsoft-365-for-enterprise"></a>Considérations relatives à la conception pour Microsoft 365 pour les entreprises

Les architectes informatiques de Contoso ont identifié les facteurs de conception requis suivants pour le déploiement de Microsoft 365 pour les entreprises :

- Plusieurs implantations géographiques avec des réglementations et des exigences de conformité locales
- Un centre de données intranet central dans le bureau du siège social et des serveurs d’applications régionaux qui hébergent des applications métier internes
- Une infrastructure existante du Microsoft Endpoint Configuration Manager
- Combinaison d’appareils informatiques clients qui exécutent Windows, Mac et Linux
- Un mélange d’appareils mobiles personnels et entreprise, notamment smartphones et tablettes iOS (iPhone et iPad) et Android
- Nombreux collaborateurs en télétravail et mobiles
- Nombreux partenaires commerciaux
- Une grande quantité d’informations personnelles confidentielles et clientes à gérer et à sécuriser
- Une grande quantité de propriété intellectuelle de qualité sous forme de directives de conception pour les produits et de secrets commerciaux fabrication

## <a name="next-step"></a>Étape suivante

Découvrez [l’infrastructure informatique locale](contoso-infra-needs.md) de Contoso Corporation et comment les besoins de l’entreprise sont satisfaits avec Microsoft 365 pour les entreprises.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
