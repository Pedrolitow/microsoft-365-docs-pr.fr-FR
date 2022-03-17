---
title: Comprendre l’ordre des stratégies dans Microsoft Defender pour les entreprises
description: En savoir plus sur l’ordre de priorité avec les stratégies dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 373f3eb821e00f903837f98896ed5dab0588e946
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63524906"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Comprendre l’ordre des stratégies dans Microsoft Defender pour les entreprises

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement [Microsoft 365 Business Premium clients,](../../business-premium/index.md) à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>Ordre des stratégies dans Microsoft Defender pour les entreprises

Microsoft Defender pour les entreprises inclut des stratégies prédéfines pour garantir la protection des appareils utilisés par vos employés. Votre équipe de sécurité peut également ajouter de nouvelles stratégies. Par exemple, supposons que vous souhaitez appliquer certains paramètres à certains appareils et différents paramètres à d’autres appareils. Pour ce faire, vous pouvez ajouter des stratégies, telles que des stratégies de protection nouvelle génération ou des stratégies de pare-feu.

À mesure que des stratégies sont ajoutées, vous remarquerez qu’un ordre de priorité est affecté. Vous pouvez modifier l’ordre de priorité des stratégies que vous définissez, mais vous ne pouvez pas modifier l’ordre de priorité des stratégies par défaut. Par exemple, supposons que pour vos Windows clients, vous avez trois stratégies de protection nouvelle génération. Dans ce cas, votre stratégie par défaut est numéro 3 en priorité. Vous pouvez modifier l’ordre de vos stratégies numéroées 1 et 2, mais la stratégie par défaut reste le numéro 3 dans votre liste. 

**Il est important de se souvenir de plusieurs stratégies que les appareils recevront uniquement la première stratégie appliquée.** En faisant référence à notre exemple précédent de trois stratégies de nouvelle génération, supposons que vous avez des appareils ciblés par les trois stratégies. Dans ce cas, ces appareils reçoivent le numéro de stratégie 1, mais ne reçoivent pas les stratégies numéro 2 et 3. 

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="key-points-to-remember-about-policy-order"></a>Points clés à retenir sur l’ordre de stratégie

- Un ordre de priorité est affecté aux stratégies.

- Les appareils reçoivent uniquement la première stratégie appliquée.

- Vous pouvez modifier l’ordre de priorité des stratégies.

- L’ordre de priorité le plus faible est attribué aux stratégies par défaut.

## <a name="next-steps"></a>Prochaines étapes

- [Commencer à utiliser Defender pour les entreprises](mdb-get-started.md)

- [Gérer les appareils](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)