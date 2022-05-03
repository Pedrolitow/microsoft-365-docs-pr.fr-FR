---
title: Comprendre l’ordre des stratégies dans Microsoft Defender pour les PME
description: Découvrez l’ordre de priorité avec les stratégies de cybersécurité pour protéger vos appareils d’entreprise avec Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 4003585c82c835c21218fd1200b3468140c8370b
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174087"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>Comprendre l’ordre des stratégies dans Microsoft Defender pour les PME

## <a name="policy-order-in-microsoft-defender-for-business"></a>Ordre de stratégie dans Microsoft Defender pour les PME

Microsoft Defender pour les PME inclut des stratégies prédéfinies pour vous assurer que les appareils utilisés par vos employés sont protégés. Votre équipe de sécurité peut également ajouter de nouvelles stratégies. Par exemple, supposons que vous souhaitez appliquer certains paramètres à certains appareils et différents paramètres à d’autres appareils. Pour ce faire, ajoutez des stratégies, telles que des stratégies de protection de nouvelle génération ou des stratégies de pare-feu.

À mesure que des stratégies sont ajoutées, vous remarquerez qu’un ordre de priorité est attribué. Vous pouvez modifier l’ordre de priorité des stratégies que vous définissez, mais vous ne pouvez pas modifier l’ordre de priorité des stratégies par défaut. Par exemple, supposons que pour vos appareils clients Windows, vous disposez de trois stratégies de protection de nouvelle génération. Dans ce cas, votre stratégie par défaut est le numéro 3 en priorité. Vous pouvez modifier l’ordre de vos stratégies numérotées 1 et 2, mais la stratégie par défaut reste numéro 3 dans votre liste. 

**La chose importante à retenir sur plusieurs stratégies est que les appareils recevront la première stratégie appliquée uniquement.** Si vous faites référence à notre exemple précédent de trois stratégies de nouvelle génération, supposons que vous avez des appareils ciblés par les trois stratégies. Dans ce cas, ces appareils recevront le numéro de stratégie 1, mais ne recevront pas les stratégies numérotées 2 et 3. 

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="key-points-to-remember-about-policy-order"></a>Points clés à retenir sur l’ordre de stratégie

- Les stratégies se voient attribuer un ordre de priorité.
- Les appareils reçoivent uniquement la première stratégie appliquée.
- Vous pouvez modifier l’ordre de priorité des stratégies.
- Les stratégies par défaut reçoivent l’ordre de priorité le plus bas.

## <a name="next-steps"></a>Prochaines étapes

- [Démarrage à l’aide de Defender entreprise](mdb-get-started.md)
- [Gérer les appareils](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)