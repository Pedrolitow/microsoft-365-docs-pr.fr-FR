---
title: Microsoft 365 Isolation du client dans les Graph microsoft Delve
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Dans cet article, trouvez une explication du fonctionnement de l’isolation Microsoft 365 client dans les Office Graph et Delve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 966f02726a2cce18e30e4d5bc7ab0beb5db51a29
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53464090"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft 365 Isolation du client dans les Graph microsoft Delve

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Isolation du client dans microsoft Graph

Microsoft [Graph](https://developer.microsoft.com/graph) modèle l’activité dans les services Microsoft 365, notamment Exchange Online, SharePoint Online, Yammer, Skype Entreprise, Azure Active Directory et bien plus encore, et dans les services externes, tels que d’autres services services Microsoft ou tiers. Les composants Graph Microsoft sont utilisés dans Microsoft 365. L’Graph Microsoft représente une collection de contenu et d’activité, ainsi que les relations entre eux qui se produisent dans l’ensemble Office suite. Il utilise des techniques sophistiquées d’apprentissage automatique pour connecter les utilisateurs au contenu pertinent, aux conversations et aux personnes qui les entourent. Par exemple, l’index client dans SharePoint Online possède un index Microsoft Graph qui sert à traiter les requêtes Delve, le moteur de traitement de l’analyse dans SharePoint Online est utilisé pour stocker les signaux et calculer les informations, et Exchange Online calcule le cache de destinataires de chaque utilisateur en tant qu’entrée dans l’analyse des clients.

L’Graph Microsoft contient des informations sur les objets d’entreprise, tels que les personnes et les documents, ainsi que sur les relations et les interactions entre ces objets. Les relations et les interactions sont représentées par des *connexions*. L’Graph Microsoft est segmentée par client de telle manière que les bords ne peuvent exister qu’entre les différents *nods* dans la même location. Un *nœud* est une entité avec un URI (Uniform Resource Identifier), un type de  nœud, une liste de contrôle d’accès et un ensemble de facettes contenant des métadonnées et des bords. Chaque nœud possède des métadonnées et des bords associés, organisés en *facettes* comme dans le modèle de connaissances commun. *Les* métadonnées sont des propriétés nommées stockées sur un nœud qui peuvent être utilisées pour la recherche, le filtrage ou l’analyse au sein du Graph Microsoft. Une *facette est* une collection logique de métadonnées et de bords sur un nœud. Chaque facette décrit un aspect d’un nœud. 

L’Graph Microsoft n’importe pas toutes les données dans un référentiel unique ; Au lieu de cela, il stocke les métadonnées et les relations relatives aux données qui se trouve ailleurs. L’Graph Microsoft se compose de plusieurs magasins de données et composants de traitement :

- Le magasin Graph client fournit un stockage en bloc optimisé pour une analyse efficace.
- Le cache de contenu actif fournit un accès aléatoire rapide aux nœuds et aux bords actifs pour stimuler les expériences utilisateur.
- Le routeur d’entrée avertit les composants internes et externes des modifications apportées au graphique client.

Les analyses au sein de chaque charge de travail donnent des informations pertinentes pour les calculs à l’échelle du client et les poussent vers le graphique client. Les raisons de l’analyse du client sur toute l’activité dans une location pour produire des informations sur les modèles de comportement. Par exemple, Exchange Online le cache de destinataires pour chaque utilisateur avec des analyses qui raisonneraient efficacement sur la boîte aux lettres de chaque utilisateur. Ces analyses par utilisateur produisent un ensemble de *edges RecipientCache* sur chaque personne, qui sont à leur tour poussées vers le graphique client. Cela permet de maintenir la plus grande partie du traitement de l’analyse aussi proche que possible des données sources.

## <a name="tenant-isolation-in-delve"></a>Isolation du client dans Delve

Comme mentionné précédemment, l’Graph Microsoft fournit des expériences qui aident les utilisateurs à découvrir et à collaborer sur les activités actuelles de leur entreprise, et fournissent une plateforme centrée sur les entités pour l’analyse sur la raison du contenu et de l’activité sur les charges de travail et au-delà de Microsoft 365. Delve est la première expérience de ce type optimisée par microsoft Graph.
Delve est une expérience web Microsoft 365 qui propose du contenu de Microsoft 365 et Yammer Entreprise aux utilisateurs Microsoft 365 via microsoft Graph. L’expérience web affiche des données sous forme de tableaux différents, chacun avec une rubrique spécifique, telle que La tendance autour de moi *ou* Modifié *par moi.* Chaque tableau se compose de plusieurs cartes de document qui affichent un texte récapitulatif et une image du document. La carte permet aux utilisateurs d’ouvrir le document ou une page Yammer le document. Il existe une page pour chaque personne dans un client Microsoft 365 qui affiche les documents les plus pertinents pour cette personne, ainsi que des icônes qui peuvent appeler Exchange Online ou Skype Entreprise pour interagir avec cette personne. Étant donné Delve est basée sur l’API microsoft Graph, elle est liée par l’isolation basée sur le client de cette API.