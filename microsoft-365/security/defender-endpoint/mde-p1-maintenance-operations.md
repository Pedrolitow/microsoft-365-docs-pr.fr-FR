---
title: Gérer Microsoft Defender pour point de terminaison plan 1
description: Gérer et mettre à jour Defender pour point de terminaison Plan 1. Gérez les paramètres, obtenez des mises à jour et traitez les faux positifs/négatifs.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 41b76968dbaf868d200ab9841893300a36e80fc6
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67514254"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Gérer Microsoft Defender pour point de terminaison plan 1

**S’applique à**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Lorsque vous utilisez Defender pour point de terminaison Plan 1 dans votre organisation, votre équipe de sécurité peut prendre certaines mesures pour maintenir votre solution de sécurité. Lorsque votre équipe de sécurité met en place votre plan de maintenance et d’exploitation, veillez à inclure au moins les activités suivantes :

- [Gérer les mises à jour des informations de sécurité et des produits](#manage-security-intelligence-and-product-updates)
- [Ajuster et ajuster Defender pour point de terminaison](#fine-tune-and-adjust-defender-for-endpoint)
- [Résoudre les faux positifs/négatifs](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Gérer les mises à jour des informations de sécurité et des produits

La mise à jour de l’Antivirus Microsoft Defender est essentielle à la protection contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque. Microsoft publie des mises à jour régulières pour la protection contre les logiciels malveillants, antivirus et de sécurité. Mises à jour sont organisées en deux catégories : 

- Mises à jour de la veille de sécurité
- Mises à jour de produit 

Pour gérer vos mises à jour de sécurité et de produit, consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Ajuster et ajuster Defender pour point de terminaison

Defender pour point de terminaison vous offre beaucoup de flexibilité et d’options de configuration. Vous pouvez ajuster et ajuster vos paramètres en fonction des besoins de votre organisation. Par exemple, vous pouvez utiliser Microsoft Endpoint Manager, stratégie de groupe et d’autres méthodes pour gérer vos paramètres de sécurité de point de terminaison. 

Pour plus d’informations, consultez [Gérer Defender pour point de terminaison](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Résoudre les faux positifs/négatifs

Un faux positif est un artefact, tel qu’un fichier ou un processus, qui a été détecté comme malveillant, même s’il ne s’agit pas réellement d’une menace. Un faux négatif est une entité qui n’a pas été détectée comme une menace, même si elle l’est réellement. Des faux positifs/négatifs peuvent se produire avec n’importe quelle solution endpoint protection, y compris Defender pour point de terminaison. Toutefois, vous pouvez prendre des mesures pour résoudre ces types de problèmes et affiner votre solution, comme illustré dans l’image suivante :

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Vue d’ensemble du processus faux positifs et négatifs" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Si vous voyez des faux positifs/négatifs dans Defender pour point de terminaison, consultez [Adresse des faux positifs/négatifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Prochaines étapes

- [Découvrez les nouveautés de Microsoft Defender pour point de terminaison](whats-new-in-microsoft-defender-endpoint.md)