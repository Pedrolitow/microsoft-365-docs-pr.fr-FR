---
title: Gérer Microsoft Defender pour Endpoint Plan 1
description: Gérer et mettre à jour Defender pour Endpoint Plan 1. Gérer les paramètres, obtenir des mises à jour et corriger les faux positifs/négatifs.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 5217cf3f8b61c4e5bc24dfc205fb78c5bde5a3b5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466628"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1"></a>Gérer Microsoft Defender pour Endpoint Plan 1

**S’applique à**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Lorsque vous utilisez Defender pour endpoint Plan 1 dans votre organisation, votre équipe de sécurité peut prendre certaines mesures pour maintenir votre solution de sécurité. Lorsque votre équipe de sécurité réunit votre plan de maintenance et d’exploitation, veillez à inclure au moins les activités suivantes :

- [Gérer les informations de sécurité et les mises à jour des produits](#manage-security-intelligence-and-product-updates)
- [Ajuster et ajuster Defender pour le point de terminaison](#fine-tune-and-adjust-defender-for-endpoint)
- [Corriger les faux positifs/négatifs](#address-false-positivesnegatives)

## <a name="manage-security-intelligence-and-product-updates"></a>Gérer les informations de sécurité et les mises à jour des produits

Le Antivirus Microsoft Defender à jour est essentiel pour la protection contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque. Microsoft publie des mises à jour régulières pour l’intelligence de la sécurité, les antivirus et la protection contre les programmes malveillants. Les mises à jour sont organisées en deux catégories : 

- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit 

Pour gérer votre veille sur la sécurité et les mises à jour de produit, voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Ajuster et ajuster Defender pour le point de terminaison

Defender pour le point de terminaison vous offre beaucoup de flexibilité et d’options de configuration. Vous pouvez ajuster et ajuster vos paramètres en fonction des besoins de votre organisation. Par exemple, vous pouvez utiliser Microsoft Endpoint Manager, une stratégie de groupe et d’autres méthodes pour gérer vos paramètres de sécurité de point de terminaison. 

Pour plus d’informations, [voir Gérer Defender pour endpoint](manage-mde-post-migration.md).

## <a name="address-false-positivesnegatives"></a>Corriger les faux positifs/négatifs

Un faux positif est un artefact, tel qu’un fichier ou un processus, qui a été détecté comme malveillant, même s’il ne s’agit pas réellement d’une menace. Un faux négatif est une entité qui n’a pas été détectée comme une menace, même si elle l’est réellement. Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection de point de terminaison, y compris Defender pour le point de terminaison. Toutefois, vous pouvez prendre des mesures pour résoudre ces types de problèmes et affiner votre solution, comme le montre l’image suivante :

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Vue d’ensemble du processus faux positifs et négatifs" lightbox="../../media/defender-endpoint/false-positives-overview.png":::

Si vous voyez des faux positifs/négatifs dans Defender pour le point de terminaison, consultez Adresse [des faux positifs/négatifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md).

## <a name="next-steps"></a>Étapes suivantes

- [Découvrez les nouveautés de Microsoft Defender pour le point de terminaison](whats-new-in-microsoft-defender-endpoint.md)