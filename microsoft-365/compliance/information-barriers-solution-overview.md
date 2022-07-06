---
title: Obstacles aux informations
description: Découvrez comment configurer des barrières à l’information dans Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, conformité, obstacles à l’information
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-scenario
ms.openlocfilehash: 21ad4f0cc6614bed3c579a8025d83200446fec18
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627236"
---
# <a name="information-barriers"></a>Obstacles aux informations

Microsoft 365 permet la communication et la collaboration entre les groupes et les organisations et prend en charge les moyens de restreindre la communication et la collaboration entre des groupes d’utilisateurs spécifiques si nécessaire. Cela peut inclure des situations ou des scénarios dans lesquels vous souhaitez restreindre la communication et la collaboration entre deux groupes afin d’éviter un conflit d’intérêts au sein de votre organisation. Cela peut également inclure des situations où vous devez restreindre la communication et la collaboration entre certaines personnes au sein de votre organisation pour protéger les informations internes.

Microsoft Purview Information Barriers (IB) est pris en charge dans Microsoft Teams, SharePoint Online et OneDrive Entreprise. Un administrateur de conformité ou un administrateur ib peut définir des stratégies pour autoriser ou empêcher les communications entre des groupes d’utilisateurs dans Microsoft Teams. Les stratégies IB peuvent être utilisées pour des situations comme celles-ci :

- L’utilisateur du groupe de commerçants de jour ne doit pas communiquer ni partager de fichiers avec l’équipe marketing
- Le personnel financier travaillant sur des informations confidentielles de l’entreprise ne doit pas communiquer ou partager des fichiers avec certains groupes au sein de son organisation
- Une équipe interne avec du matériel de secret commercial ne doit pas appeler ou discuter en ligne avec des personnes de certains groupes au sein de leur organisation
- Une équipe de recherche doit uniquement appeler ou discuter en ligne avec une équipe de développement de produits

## <a name="configure-information-barriers"></a>Configurer les obstacles à l’information

Utilisez les étapes suivantes pour configurer IB pour votre organisation :

![Étapes d’obstacles à l’information sur les solutions à risque interne.](../media/ir-solution-ib-steps.png)

1. En savoir plus sur [les obstacles à l’information](information-barriers.md)
2. Configurer [les prérequis et les autorisations](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)
3. Segmenter [les utilisateurs de votre organisation](information-barriers-policies.md#step-2-segment-users-in-your-organization)
4. Créer et configurer des [stratégies IB](information-barriers-policies.md#step-3-create-ib-policies)
5. Appliquer des [stratégies IB](information-barriers-policies.md#step-4-apply-ib-policies)

## <a name="more-information-about-information-barriers"></a>Plus d’informations sur les obstacles à l’information

- [Attributs pour les stratégies IB](information-barriers-attributes.md)
- [Modifier ou supprimer des stratégies IB](information-barriers-edit-segments-policies.md)
