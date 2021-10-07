---
title: Gérer Microsoft Defender pour Endpoint Plan 1 (prévisualisation)
description: Gérer et mettre à jour Defender pour Endpoint Plan 1. Gérer les paramètres, obtenir des mises à jour et corriger les faux positifs/négatifs.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 09/13/2021
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 298f63a0df664cada6cf6d2a67a06770b66ea6ea
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60194116"
---
# <a name="manage-microsoft-defender-for-endpoint-plan-1-preview"></a>Gérer Microsoft Defender pour Endpoint Plan 1 (prévisualisation)

> [!TIP]
> Si vous avez Microsoft 365 E3 ou A3, mais pas Microsoft 365 E5 ou A5, visitez le site pour vous inscrire [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial) au programme d’aperçu !

Lorsque vous utilisez Defender pour Endpoint Plan 1 (prévisualisation) dans votre organisation, votre équipe de sécurité peut prendre certaines mesures pour maintenir votre solution de sécurité. Lorsque votre équipe de sécurité réunit votre plan de maintenance et d’exploitation, veillez à inclure au moins les activités suivantes :

- [Gérer les informations de sécurité et les mises à jour des produits](#manage-security-intelligence-and-product-updates)
- [Ajuster et ajuster Defender pour le point de terminaison](#fine-tune-and-adjust-defender-for-endpoint)
- [Corriger les faux positifs/négatifs](#address-false-positivesnegatives)

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article contient des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Defender for Endpoint Plan 1 (prévisualisation).

## <a name="manage-security-intelligence-and-product-updates"></a>Gérer les informations de sécurité et les mises à jour des produits

Le Antivirus Microsoft Defender à jour est essentiel pour la protection contre les nouveaux programmes malveillants et les nouvelles techniques d’attaque. Microsoft publie des mises à jour régulières pour l’intelligence de la sécurité, les antivirus et la protection contre les programmes malveillants. Les mises à jour sont organisées en deux catégories : 

- Mises à jour de l’intelligence de la sécurité
- Mises à jour de produit 

Pour gérer votre veille sur la sécurité et les mises à jour de produit, voir Gérer Antivirus Microsoft Defender mises à jour [et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md)

## <a name="fine-tune-and-adjust-defender-for-endpoint"></a>Ajuster et ajuster Defender pour le point de terminaison

Defender pour le point de terminaison vous offre beaucoup de flexibilité et d’options de configuration. Vous pouvez ajuster et ajuster vos paramètres en fonction des besoins de votre organisation. Par exemple, vous pouvez utiliser Microsoft Endpoint Manager, une stratégie de groupe et d’autres méthodes pour gérer vos paramètres de sécurité de point de terminaison. 

Pour plus d’informations, [voir Gérer Defender pour endpoint.](manage-atp-post-migration.md)

## <a name="address-false-positivesnegatives"></a>Corriger les faux positifs/négatifs

Un faux positif est un artefact, tel qu’un fichier ou un processus, qui a été détecté comme malveillant, même s’il ne s’agit pas réellement d’une menace. Un faux négatif est une entité qui n’a pas été détectée comme une menace, même si elle l’est réellement. Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection de point de terminaison, y compris Defender pour le point de terminaison. Toutefois, vous pouvez prendre des mesures pour résoudre ces types de problèmes et affiner votre solution, comme le montre l’image suivante :

:::image type="content" source="../../media/defender-endpoint/false-positives-overview.png" alt-text="Vue d’ensemble du processus faux positifs et négatifs":::

Si vous voyez des faux positifs/négatifs dans Defender pour le point de terminaison, consultez Adresse [faux positifs/négatifs dans Microsoft Defender pour point de terminaison.](defender-endpoint-false-positives-negatives.md)

## <a name="next-steps"></a>Étapes suivantes

- [Découvrez les nouveautés de Microsoft Defender pour le point de terminaison](whats-new-in-microsoft-defender-atp.md)