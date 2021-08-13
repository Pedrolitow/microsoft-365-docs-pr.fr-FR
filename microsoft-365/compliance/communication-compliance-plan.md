---
title: Planifier la conformité des communications
description: Découvrez la planification de l’utilisation de la conformité des communications dans votre organisation.
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
ms.openlocfilehash: 95712ea75b498c159d3a1d982f417a03d1d978a9d8529294522f25eb80cc6a65
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53802549"
---
# <a name="plan-for-communication-compliance"></a>Planifier la conformité des communications

Avant de commencer à mettre en place la conformité des [communications](communication-compliance.md) dans votre organisation, il existe d’importantes activités de planification et des considérations qui doivent être examinées par vos équipes de gestion des technologies de l’information et de la conformité. Une compréhension approfondie et la planification du déploiement dans les domaines suivants vous aideront à vous assurer que votre implémentation et l’utilisation des fonctionnalités de conformité des communications se déroulent sans problème et sont conformes aux meilleures pratiques pour la solution.

## <a name="work-with-stakeholders-in-your-organization"></a>Travailler avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées de votre organisation à collaborer pour prendre des mesures sur les alertes de conformité des communications. Certaines parties prenantes recommandées à envisager, y compris dans la planification initiale et le flux de travail de conformité des [communications](communication-compliance.md#workflow) de bout en bout, sont les personnes des zones suivantes de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planifier le flux de travail d’examen et de correction

Sélectionnez des parties prenantes dédiées pour surveiller et examiner les alertes et les cas à une cadence régulière dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de bien comprendre comment vous allez affecter des utilisateurs et des parties prenantes à différents groupes de rôles de conformité des communications au sein de votre organisation.

Selon la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à un ou plusieurs groupes de rôles pour les administrateurs, les réviseurs et les enquêteurs. Vous avez la possibilité d’affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les utilisateurs de conformité des communications au groupe de rôles Conformité des communications. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Planifiez le choix entre ces options de groupe de rôles lors de la configuration de la conformité des communications :

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de se lancer rapidement dans la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis séparez les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupe de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées des messages (et non le contenu du message), passer à des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas Advanced eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

## <a name="plan-for-policies"></a>Planifier les stratégies

La création de stratégies de conformité des communications est rapide et facile avec les [modèles prédéfinie](communication-compliance-feature-reference.md#policy-templates) pour le langage choquant, les informations sensibles et la conformité réglementaire. Les stratégies de conformité des communications personnalisées permettent de détecter et d’enquêter les problèmes spécifiques à votre organisation et aux exigences.

Lorsque vous planifiez des stratégies de conformité des communications, prenez en compte les points suivants :

- Envisagez d’ajouter tous les utilisateurs de votre organisation dans le cadre de vos stratégies de conformité des communications. L’identification d’utilisateurs spécifiques comme étant dans l’étendue des stratégies individuelles est utile dans certains cas, mais la plupart des organisations doivent inclure tous les utilisateurs dans les stratégies de conformité des communications optimisées pour la détection du harcèlement ou de la discrimination.
- Pour simplifier votre configuration, envisagez de créer des groupes pour les personnes qui ont besoin de révision de leurs communications. Si vous utilisez des groupes ; vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé.
- Configurez le pourcentage de communications à examiner à 100 % pour vous assurer que les stratégies capturent tous les problèmes problématiques dans les communications de votre organisation.
- Vous pouvez analyser les communications provenant de [sources](communication-compliance-feature-reference.md#supported-communication-types) tierces pour les données importées dans les boîtes aux lettres de Microsoft 365 organisation. Pour inclure la révision des communications dans ces plateformes, vous devez configurer un connecteur vers ces services avant que les messages qui rencontrent des conditions de stratégie soient surveillés par la stratégie de communication.
- Les stratégies peuvent prendre en charge les langues de surveillance autres que l’anglais dans les stratégies de conformité des communications personnalisées. Créez [un dictionnaire de](communication-compliance-feature-reference.md#custom-keyword-dictionaries) mots clés personnalisé de mots choquants dans le langage de votre choix ou créez votre propre modèle d’apprentissage automatique à l’aide de classifieurs entraidables dans Microsoft 365. [](classifier-get-started-with.md)
- Toutes les organisations ont des normes de communication et des besoins en matière de stratégie différents. Surveillez les mots clés spécifiques à l’aide des conditions de stratégie de conformité des [communications](communication-compliance-feature-reference.md#conditional-settings) ou surveillez les types spécifiques d’informations avec des types d’informations [sensibles personnalisés.](create-a-custom-sensitive-information-type.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité des communications pour votre organisation Microsoft 365, voir Configurer la conformité des communications pour [Microsoft 365](communication-compliance-configure.md) ou consultez l’étude de cas pour [Contoso](communication-compliance-case-study.md) et la façon dont il a configuré rapidement une stratégie de conformité des communications pour surveiller les langages choquants dans les communications Microsoft Teams, Exchange Online et Yammer.
