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
ms.openlocfilehash: d64edc9d80722080db18c45127bfc82110d1ea9e
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48131536"
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

Sélectionnez les parties prenantes dédiées pour surveiller et passer en revue les alertes et les incidents à intervalles réguliers dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de comprendre comment vous affecterez les utilisateurs et les parties prenantes à différents groupes de rôles de conformité de communication au sein de votre organisation.

En fonction de la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez attribuer des utilisateurs à un ou plusieurs groupes de rôles pour les administrateurs, les relecteurs et les investigateurs. Vous avez la possibilité d’affecter des utilisateurs à des groupes de rôles spécifiques afin de gérer différents ensembles de fonctionnalités de conformité des communications. Ou vous pouvez décider d’affecter tous les utilisateurs de conformité de communication au groupe de rôles de conformité de communication. Utilisez un seul groupe de rôles ou plusieurs groupes pour mieux répondre aux exigences de gestion de la conformité.

Prévoyez de choisir parmi ces options de groupe de rôles lors de la configuration de la conformité des communications :

|**Rôle**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité de la communication** | Utilisez ce groupe de rôles pour gérer la conformité des communications de votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, investigateurs et visionneuses désignés, vous pouvez configurer des autorisations de conformité de la communication dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration est la méthode la plus simple pour démarrer rapidement la conformité de la communication et convient aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité de communication** | Utilisez ce groupe de rôles pour configurer initialement la conformité de la communication et par la suite pour séparer les administrateurs de conformité des communications en un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des affectations de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies pour lesquelles ils sont affectés en tant que relecteurs, afficher les métadonnées de message (et non le contenu des messages), faire remonter aux relecteurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Investigation de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’investigations de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des relecteurs supplémentaires, passer à un cas avancé eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité de la communication** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui géreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de la conformité de la communication et peuvent afficher tous les rapports de conformité des communications. |

## <a name="plan-for-policies"></a>Planifier les stratégies

La création de stratégies de conformité des communications est rapide et facile grâce aux [modèles prédéfinis](communication-compliance-feature-reference.md#policy-templates) pour le langage offensant, les informations sensibles et la conformité réglementaire. Les stratégies de conformité de communication personnalisées permettent de détecter et d’identifier les problèmes spécifiques à votre organisation et à vos besoins.

Lors de la planification des stratégies de conformité des communications, prenez en compte les éléments suivants :

- Envisagez d’ajouter tous les utilisateurs de votre organisation comme dans le cadre de vos stratégies de conformité de communication. L’identification des utilisateurs spécifiques en tant que tels dans le cadre des stratégies individuelles est utile dans certains cas, mais la plupart des organisations doivent inclure tous les utilisateurs dans les stratégies de conformité des communications optimisées pour la détection de harcèlement ou de discrimination.
- Pour simplifier votre configuration, pensez à créer des groupes pour les personnes qui ont besoin de leurs communications. Si vous utilisez des groupes ; vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé.
- Configurez le pourcentage de communications à réviser à 100% pour vous assurer que les stratégies interceptent tous les problèmes de communication pour votre organisation.
- Vous pouvez analyser les communications provenant de [sources tierces](communication-compliance-feature-reference.md#supported-communication-types) pour les données importées dans des boîtes aux lettres de votre organisation Microsoft 365. Pour inclure la révision des communications dans ces plateformes, vous devez configurer un connecteur pour ces services avant que les messages de stratégie de réunion soient surveillés par la stratégie de communication.
- Les stratégies peuvent prendre en charge des langues d’analyse autres que l’anglais dans les stratégies de conformité de communication personnalisées. Créez un [dictionnaire de mots clés personnalisés](communication-compliance-feature-reference.md#custom-keyword-dictionaries) de mots injurieux dans la langue de votre choix ou créez votre propre modèle de formation d’ordinateur à l’aide de [classifieurs](classifier-get-started-with.md) pilotables dans Microsoft 365.
- Toutes les organisations ont des normes de communication et des exigences de stratégie différentes. Surveiller des mots clés spécifiques en utilisant des [conditions de stratégie](communication-compliance-feature-reference.md#conditional-settings) de conformité de communication ou surveiller des types d’informations spécifiques avec des types d' [informations sensibles personnalisés](create-a-custom-sensitive-information-type.md).

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité de la communication pour votre organisation Microsoft 365, consultez la rubrique [configure communication Compliance for Microsoft 365](communication-compliance-configure.md) ou consultez l' [étude de cas pour Contoso](communication-compliance-case-study.md) , ainsi que la manière dont ils ont configuré rapidement une stratégie de conformité des communications pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer.
