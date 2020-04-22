---
title: Configurer des utilisateurs et des cas dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 60ffd80b-4376-419d-b6e4-a72029b9907c
description: 'Découvrez comment configurer des rôles d’utilisateur, créer des cas et affecter des utilisateurs à des cas dans Advanced eDiscovery.  '
ms.openlocfilehash: 5c82ad8b630974d3afeb1928f8dd229ffb0dc36a
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636068"
---
# <a name="set-up-users-and-cases-in-advanced-ediscovery-classic"></a>Configurer des utilisateurs et des cas dans Advanced eDiscovery (classique)

Cette rubrique décrit comment configurer des utilisateurs et des cas pour Advanced eDiscovery (classique).
  
> [!IMPORTANT]
> À mesure que nous continuons à investir dans les versions plus récentes de Advanced eDiscovery, nous annonçaons le retrait de la fonctionnalité eDiscovery avancée, également appelée *Advanced eDiscovery (Classic)* ou *Advanced eDiscovery v 1.0*. Si vous utilisez Advanced eDiscovery v 1.0, veuillez faire la transition vers [Advanced eDiscovery v2.0](overview-ediscovery-20.md) (également connu sous le nom de *solution eDiscovery avancée dans Microsoft 365*) dès que possible. Advanced eDiscovery 2.0 contient des fonctionnalités similaires à celles de Advanced eDiscovery v1.0, et elle offre également de nombreuses fonctions inédites telles que la gestion des consignataires, la gestion des communications et les jeux à réviser. Pour en savoir plus sur le retrait d’Advanced eDiscovery v1.0, voir la [Suppression des outils hérités eDiscovery](legacy-ediscovery-retirement.md#advanced-ediscovery-v10). 
  
## <a name="prerequisites"></a>Conditions préalables

Avant de configurer des cas et des utilisateurs dans Advanced eDiscovery, les éléments suivants sont requis :
  
- Pour analyser les données d’un utilisateur à l’aide de Advanced eDiscovery, l’utilisateur (le dépositaire des données) doit disposer d’une licence Office 365 E5. Par ailleurs, les utilisateurs disposant d’une licence Office 365 E1 ou E3 peuvent se voir attribuer une licence avancée eDiscovery autonome. Les administrateurs et les responsables de la mise en conformité qui sont affectés à des cas et utilisent Advanced eDiscovery pour analyser les données n’ont pas besoin d’une licence E5. 
    
- Vous devez être membre du groupe de rôles gestionnaire eDiscovery dans le centre de sécurité &amp; conformité pour créer un cas eDiscovery et y ajouter des membres. Pour vous ajouter au groupe de rôles gestionnaire de découverte électronique &amp; dans le centre de sécurité conformité, vous devez être un administrateur général de votre organisation. Si vous n’êtes pas un administrateur général, vous devrez demander à un administrateur général de vous ajouter au groupe de rôles gestionnaire de découverte électronique. Si vous souhaitez en savoir plus, consultez les articles : 
    
  - [Autorisations dans le centre de sécurité &amp; conformité Microsoft 365](~/security/office-365-security/protect-against-threats.md)
    
  - [Attribuer des autorisations eDiscovery dans le centre de &amp; sécurité conformité Microsoft 365](assign-ediscovery-permissions.md)
    
## <a name="step-1-assign-users-ediscovery-permissions"></a>Étape 1 : attribuer des autorisations eDiscovery aux utilisateurs

La première étape consiste à attribuer aux utilisateurs les autorisations requises dans le &amp; Centre de sécurité conformité afin qu’ils puissent m’ajouter en tant que membre d’un cas eDiscovery. Une fois qu’un utilisateur est ajouté en tant que membre d’un cas &amp; dans le centre de sécurité conformité, il pourra accéder à l’incident dans Advanced eDiscovery.
  
Pour attribuer aux utilisateurs les autorisations nécessaires afin qu’ils puissent être ajoutés en tant que membre d’un cas de découverte électronique, voir l’étape 1 dans [les cas &amp; eDiscovery dans le centre de sécurité conformité de Microsoft 365](ediscovery-cases.md#step-1-assign-ediscovery-permissions-to-potential-case-members).
  
## <a name="step-2-create-an-ediscovery-case-and-add-members"></a>Étape 2 : créer un cas eDiscovery et ajouter des membres

L’étape suivante consiste à créer un nouveau cas eDiscovery dans le centre &amp; de sécurité et à ajouter des membres. Les membres de ce cas seront alors en mesure d’accéder au cas dans Advanced eDiscovery.
  
1. Pour créer un cas de découverte électronique, voir l’étape 2 dans [cas de découverte électronique dans &amp; le centre de sécurité conformité Microsoft 365](ediscovery-cases.md#step-2-create-a-new-case).
    
2. Pour ajouter des membres à un cas eDiscovery, reportez-vous à l’étape 3 dans [cas de découverte électronique dans le centre de sécurité &amp; conformité Microsoft 365](ediscovery-cases.md#step-3-add-members-to-a-case)
    
## <a name="step-3-go-a-case-in-advanced-ediscovery"></a>Étape 3 : passer un cas dans Advanced eDiscovery

Une fois que vous avez créé un cas eDiscovery et ajouté des membres, vous (ou tout membre du cas) pouvez accéder à la casse correspondante dans Advanced eDiscovery. Pour accéder à un cas dans Advanced eDiscovery, reportez-vous à l’étape 8 dans [les cas de découverte électronique dans le centre de sécurité &amp; conformité Microsoft 365](ediscovery-cases.md#step-8-go-to-the-case-in-advanced-ediscovery).
  
## <a name="see-also"></a>Voir aussi

[Advanced eDiscovery (classique)](office-365-advanced-ediscovery.md)
  
[Préparation des données](prepare-data-for-advanced-ediscovery.md)
 
