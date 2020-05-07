---
title: Planifier la conformité des communications
description: Découvrez comment planifier l’utilisation de la conformité de la communication dans votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 214c5376d4c074525253707e181eee69cefff85e
ms.sourcegitcommit: eb3c7f473e8fe62624f52c9bb38dcd6a96fa58a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44045849"
---
# <a name="plan-for-communication-compliance"></a>Planifier la conformité des communications

Avant de commencer à respecter les [règles de communication](communication-compliance.md) au sein de votre organisation, il existe des activités de planification et des considérations importantes qui doivent être examinées par vos équipes de gestion de la conformité et de la technologie de l’information. La compréhension et la planification rigoureuses du déploiement dans les domaines suivants permettent de s’assurer que l’implémentation et l’utilisation des fonctionnalités de conformité de la communication se déroulent en douceur et qu’elles sont alignées sur les meilleures pratiques de la solution.

## <a name="work-with-stakeholders-in-your-organization"></a>Utilisation des parties prenantes au sein de votre organisation

Identifiez les parties prenantes appropriées dans votre organisation afin de collaborer afin de prendre des mesures sur les alertes de conformité de communication. Certaines parties prenantes recommandées pour l’inclusion dans la planification initiale et le [flux de travail de conformité](communication-compliance.md#workflow) de la communication de bout en bout sont des personnes des zones suivantes de votre organisation :

- Technologies de l’information
- Conformité
- Confidentialité
- Sécurité
- ressources humaines ;
- Informations juridiques

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planifier le flux de travail d’enquête et de correction

Sélectionnez relecteurs dédiés pour surveiller et vérifier les alertes régulièrement dans le centre de [conformité Microsoft 365](https://compliance.microsoft.com/). N’oubliez pas que vous devez [créer un nouveau groupe de rôles](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance) pour activer les autorisations des relecteurs auprès de l' **administrateur de révision de surveillance**, de la gestion des **cas**, de l' **administrateur de conformité**et des rôles de **révision** pour examiner et corriger les messages avec des correspondances de stratégie.

## <a name="plan-for-policies"></a>Planifier les stratégies

La création de stratégies de conformité des communications est rapide et facile grâce aux [modèles prédéfinis](communication-compliance-feature-reference.md#policy-templates) pour le langage offensant, les informations sensibles et la conformité réglementaire. Les stratégies de conformité de communication personnalisées permettent de détecter et d’identifier les problèmes spécifiques à votre organisation et à vos besoins.

Lors de la planification des stratégies de conformité des communications, prenez en compte les éléments suivants :

- Envisagez d’ajouter tous les utilisateurs de votre organisation comme dans le cadre de vos stratégies de conformité de communication. L’identification des utilisateurs spécifiques en tant que tels dans le cadre des stratégies individuelles est utile dans certains cas, mais la plupart des organisations doivent inclure tous les utilisateurs dans les stratégies de conformité des communications optimisées pour la détection de harcèlement ou de discrimination.
- Pour simplifier votre configuration, pensez à créer des groupes pour les personnes qui ont besoin de leurs communications. Si vous utilisez des groupes ; vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez analyser les communications entre deux groupes distincts de personnes, ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.
- Configurez le pourcentage de communications à réviser à 100% pour vous assurer que les stratégies interceptent tous les problèmes de communication pour votre organisation.
- Vous pouvez analyser les communications provenant de [sources tierces](communication-compliance-feature-reference.md#supported-communication-types) pour les données importées dans des boîtes aux lettres de votre organisation Microsoft 365. Pour inclure la révision des communications dans ces plateformes, vous devez configurer un connecteur pour ces services avant que les messages de stratégie de réunion soient surveillés par la stratégie de communication.
- Les stratégies peuvent prendre en charge des langues d’analyse autres que l’anglais dans les stratégies de conformité de communication personnalisées. Créez un [dictionnaire de mots clés personnalisés](communication-compliance-feature-reference.md#custom-keyword-dictionaries) de mots injurieux dans la langue de votre choix ou créez votre propre modèle de formation d’ordinateur à l’aide de [classifieurs](classifier-getting-started-with.md) pilotables dans Microsoft 365.
- Toutes les organisations ont des normes de communication et des exigences de stratégie différentes. Surveiller des mots clés spécifiques en utilisant des [conditions de stratégie](communication-compliance-feature-reference.md#conditional-settings) de conformité de communication ou surveiller des types d’informations spécifiques avec des types d' [informations sensibles personnalisés](create-a-custom-sensitive-information-type.md).

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité de la communication pour votre organisation Microsoft 365, consultez la rubrique [configure communication Compliance for Microsoft 365](communication-compliance-configure.md) ou consultez l' [étude de cas pour Contoso](communication-compliance-case-study.md) , ainsi que la manière dont ils ont configuré rapidement une stratégie de conformité des communications pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer.
