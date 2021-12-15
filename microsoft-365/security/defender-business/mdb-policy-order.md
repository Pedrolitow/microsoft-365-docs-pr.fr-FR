---
title: Comprendre l’ordre des stratégies dans Microsoft Defender pour les entreprises (prévisualisation)
description: En savoir plus sur l’ordre de priorité avec les stratégies dans Microsoft Defender entreprise (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/13/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: c2ccbb0ae11703b8da25569a34655cabee940c5b
ms.sourcegitcommit: 74f79aacb4ffcc6cb0e315239b1493324eabb449
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2021
ms.locfileid: "61507732"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business-preview"></a>Comprendre l’ordre des stratégies dans Microsoft Defender pour les entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Ordre des stratégies dans Microsoft Defender pour les entreprises

Microsoft Defender pour Entreprise (prévisualisation) inclut des stratégies prédéfines pour garantir la protection des appareils utilisés par vos employés. Votre équipe de sécurité peut également ajouter de nouvelles stratégies. Par exemple, supposons que vous souhaitez appliquer certains paramètres à certains appareils et différents paramètres à d’autres appareils. Pour ce faire, vous pouvez ajouter des stratégies, telles que des stratégies de protection nouvelle génération ou des stratégies de pare-feu.

À mesure que des stratégies sont ajoutées, vous remarquerez qu’un ordre de priorité est affecté. Vous pouvez modifier l’ordre de priorité des stratégies que vous définissez, mais vous ne pouvez pas modifier l’ordre de priorité des stratégies par défaut. Par exemple, supposons que pour vos Windows clients, vous avez trois stratégies de protection nouvelle génération. Dans ce cas, votre stratégie par défaut est numéro 3 en priorité. Vous pouvez modifier l’ordre de vos stratégies numéroées 1 et 2, mais la stratégie par défaut reste le numéro 3 dans votre liste. 

**Il est important de se souvenir de plusieurs stratégies que les appareils recevront uniquement la première stratégie appliquée.** En faisant référence à notre exemple précédent de trois stratégies de nouvelle génération, supposons que vous avez des appareils ciblés par les trois stratégies. Dans ce cas, ces appareils reçoivent le numéro de stratégie 1, mais ne reçoivent pas les stratégies numéro 2 et 3. 

## <a name="key-points-to-remember-about-policy-order"></a>Points clés à retenir sur l’ordre de stratégie

- Un ordre de priorité est affecté aux stratégies

- Les appareils reçoivent la première stratégie appliquée uniquement

- Vous pouvez modifier l’ordre de priorité des stratégies

- L’ordre de priorité le plus faible est attribué aux stratégies par défaut

## <a name="next-steps"></a>Étapes suivantes

- [Commencer à utiliser Defender pour les entreprises (prévisualisation)](mdb-get-started.md)

- [Gérer les appareils](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)