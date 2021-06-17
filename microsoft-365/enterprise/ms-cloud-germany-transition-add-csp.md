---
title: Informations supplémentaires pour les fournisseurs de solutions Cloud
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: 'Résumé : Informations supplémentaires pour les fournisseurs de solutions Cloud pertinents pour la migration à partir de Microsoft Cloud Deutschland.'
ms.openlocfilehash: 843552c55acba57c5c2da4a1a885d65cb4e59d84
ms.sourcegitcommit: 34c06715e036255faa75c66ebf95c12a85f8ef42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "52984915"
---
# <a name="additional-information-for-cloud-solution-providers"></a>Informations supplémentaires pour les fournisseurs de solutions Cloud

Les fournisseurs de solutions Cloud (CSP) qui prennent en charge les clients doivent prendre des mesures supplémentaires lors de la migration de Microsoft Cloud Deutschland vers la nouvelle région de centre de données allemande.

## <a name="partner-tenant-migration"></a>Migration des locataires partenaires

Les clients Microsoft Cloud Deutschland partenaires ne seront pas migrés. Au lieu de cela, un nouveau client Office 365 services sera créé pour chaque partenaire Microsoft dans la nouvelle région de centres de données allemande.

Les clients du programme CSP seront migrés vers la nouvelle région de centres de données allemande et liés au nouveau client de services Office 365 du même partenaire. Après la transition du client, le partenaire peut gérer le client à l’aide du nouveau client Office 365 services dans la région du centre de données allemand.

## <a name="missing-subscriptions-in-azure"></a>Abonnements manquants dans Azure

Une fois la transition des abonnements et des licences [terminée (phase 3),](ms-cloud-germany-transition-phases.md#phase-3-subscription-transfer) les fournisseurs de solutions Cloud n’auront plus accès à l’abonnement Azure.

Pour récupérer l’accès, suivez ces étapes pour élever [l’accès](/azure/role-based-access-control/elevate-access-global-admin)afin de gérer tous les abonnements Et groupes de gestion Azure.
