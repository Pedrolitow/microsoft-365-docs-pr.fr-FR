---
title: Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Le Gestionnaire de conformité Microsoft permet aux organisations de simplifier et d’automatiser les évaluations des risques, et suggère des actions recommandées pour résoudre les risques.
ms.openlocfilehash: 7eb8e0fdea26ca24453ca7071ab1282c686d5848
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244394"
---
# <a name="microsoft-compliance-manager"></a>Gestionnaire de conformité Microsoft

**Dans cet article :** Découvrez ce qu’est le Gestionnaire de conformité, comment il contribue à simplifier la conformité et à réduire les risques, ainsi que ses composants clés.

## <a name="whats-new-the-ga-release-of-compliance-manager"></a>Nouveautés : la version GA du Gestionnaire de conformité

Le Gestionnaire de conformité est désormais généralement disponible (GA) en tant que solution de gestion de la conformité de bout en bout dans le centre [Microsoft 365 conformité.](microsoft-365-compliance-center.md) Avec cette version, le Gestionnaire de conformité termine la transition à partir de son emplacement précédent dans le portail d’confiance des services Microsoft. Le Gestionnaire de conformité est également disponible pour les clients modérés, Cloud de la communauté du secteur public et du département de la Défense (DoD) du gouvernement américain Community (Cloud de la communauté du secteur public).

Ce qui a commencé par la prévisualisation publique du Score de conformité est devenu un outil centralisé avec des fonctionnalités de gestion de la conformité améliorées et une plus grande facilité d’utilisation.  La version GA apporte une collection plus importante d’évaluations pré-conçues pour vous aider à mettre à l’échelle vos activités de conformité.

**En savoir plus sur la version GA :**
- Nos [questions fréquemment posées](compliance-manager-faq.md) vous viennent en détail sur l’évolution.
- Découvrez les améliorations apportées aux fonctionnalités ga dans [ce billet de blog.](https://aka.ms/compliancemanager/GAblog)

Regardez la vidéo ci-dessous pour découvrir comment le Gestionnaire de conformité peut simplifier la gestion de la conformité par votre organisation :
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4FGYZ]

## <a name="what-is-compliance-manager"></a>Qu’est-ce que le Gestionnaire de conformité ?

[Le Gestionnaire de conformité Microsoft](https://compliance.microsoft.com/compliancemanager) est une fonctionnalité du Centre [de](microsoft-365-compliance-center.md) conformité Microsoft 365 qui vous permet de gérer les exigences de conformité de votre organisation avec plus de simplicité et de commodité. Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire de vos risques de protection des données à la gestion des complexités de l’implémentation des contrôles, à la mise à jour des réglementations et des certifications et à la gestion des rapports aux auditeurs.

Le Gestionnaire de conformité simplifie la conformité et réduit les risques en fournissant :

- Évaluations pré-conçues pour les normes et réglementations régionales et industrielles courantes, ou évaluations personnalisées pour répondre à vos besoins de conformité uniques (les évaluations disponibles dépendent de votre contrat de licence ; [en savoir plus](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)).

- Fonctionnalités de flux de travail pour vous aider à effectuer efficacement vos évaluations des risques à l’aide d’un seul outil.

- Recommandations détaillées détaillées sur les suggestions d’actions d’amélioration pour vous aider à vous conformer aux normes et réglementations les plus pertinentes pour votre organisation. Pour les actions gérées par Microsoft, vous verrez les détails de l’implémentation et les résultats de l’audit.

- Un score de conformité basé sur les risques pour vous aider à comprendre votre posture de conformité en mesurant votre progression dans l’exécution des actions d’amélioration.

Votre tableau de bord du Gestionnaire de conformité affiche votre score de conformité actuel, vous aide à voir ce qui nécessite une attention particulière et vous guide vers les actions d’amélioration clés. Voici un exemple de ce à quoi ressemblera votre tableau de bord du Gestionnaire de conformité :

![Gestionnaire de conformité - Tableau de bord](../media/compliance-manager-dashboard.png "Tableau de bord du Gestionnaire de conformité")

## <a name="understanding-your-compliance-score"></a>Comprendre votre score de conformité

Le Gestionnaire de conformité vous indique que vous avez terminé les actions d’amélioration prises pour se conformer à une réglementation, une norme ou une stratégie, et combine ces points dans un score de conformité global. Chaque action a un impact différent sur votre score en fonction des risques potentiels impliqués. Votre score de conformité peut vous aider à hiérarchiser l’action sur laquelle vous concentrer pour améliorer votre posture de conformité globale.

Le Gestionnaire de conformité vous donne un score initial basé sur la ligne de base Microsoft 365 protection des données. Cette ligne de base est un ensemble de contrôles qui inclut des réglementations et des normes clés en matière de protection des données et de gouvernance générale des données.

##### <a name="learn-more"></a>En savoir plus

[Comprendre comment votre score de conformité est calculé.](compliance-score-calculation.md)

[Découvrez comment travailler avec des actions d’amélioration.](compliance-manager-improvement-actions.md)

## <a name="key-elements-controls-assessments-templates-improvement-actions"></a>Éléments clés : contrôles, évaluations, modèles, actions d’amélioration

Le Gestionnaire de conformité utilise plusieurs éléments de données pour vous aider à gérer vos activités de conformité. Lorsque vous utilisez le Gestionnaire de conformité pour affecter, tester et surveiller les activités de conformité, il est utile de bien comprendre les éléments clés : contrôles, évaluations, modèles et actions d’amélioration.

### <a name="controls"></a>Contrôles

Un contrôle est une exigence d’une réglementation, d’une norme ou d’une stratégie. Il définit la façon dont vous évaluez et gérez la configuration du système, le processus organisationnel et les personnes responsables de répondre à une exigence spécifique d’une réglementation, d’une norme ou d’une stratégie.

Le Gestionnaire de conformité suit les types de contrôles suivants :

1. **Contrôles gérés par Microsoft**: contrôles pour les services cloud de Microsoft, dont Microsoft est responsable de l’implémentation
2. **Vos contrôles**: parfois appelés contrôles gérés par le client, ces contrôles sont implémentés et gérés par votre organisation
3. **Contrôles partagés**: il s’existe des contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation

##### <a name="learn-more"></a>En savoir plus

[Surveillez la progression de vos contrôles.](compliance-manager-assessments.md#monitor-assessment-progress-and-controls)

[Découvrez comment le Gestionnaire de conformité évalue en permanence les contrôles.](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls)

### <a name="assessments"></a>Évaluations

Une évaluation consiste à grouper des contrôles à partir d’une réglementation, d’une norme ou d’une stratégie spécifique. L’exécution des actions d’une évaluation vous aide à répondre aux exigences d’une norme, d’une réglementation ou d’une loi. Par exemple, vous pouvez avoir une évaluation qui, lorsque vous y avez terminé toutes les actions, vous aide à aligner vos paramètres Microsoft 365 avec les exigences ISO 27001.

Les évaluations ont plusieurs composants :

- **Services concernés** : ensemble spécifique de services Microsoft applicable à l’évaluation
- **Contrôles gérés par Microsoft**: contrôles pour les services cloud de Microsoft, que Microsoft implémente en votre nom
- **Vos contrôles**: parfois appelés contrôles gérés par le client, ces contrôles sont implémentés et gérés par votre organisation
- **Contrôles partagés**: il s’existe des contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation
- **Score d’évaluation**: indique votre progression dans l’obtention du nombre total de points possibles à partir d’actions au sein de l’évaluation gérées par votre organisation et par Microsoft

Lorsque vous créez des évaluations, vous les affectez à un groupe. Vous pouvez configurer les groupes de la manière la plus logique pour votre organisation. Par exemple, vous pouvez grouper les évaluations par année d’audit, région, solution, équipes au sein de votre organisation ou d’une autre façon. Une fois que vous avez créé des groupes, vous pouvez filtrer votre tableau de bord du [Gestionnaire](compliance-manager-setup.md#filtering-your-dashboard-view) de conformité pour afficher votre score d’un ou plusieurs groupes.

##### <a name="learn-more"></a>En savoir plus

[Créer et gérer des évaluations dans le Gestionnaire de conformité.](compliance-manager-assessments.md)

### <a name="templates"></a>Modèles

Le Gestionnaire de conformité fournit des modèles pour vous aider à créer rapidement des évaluations. Vous pouvez modifier ces modèles pour créer une évaluation optimisée pour vos besoins. Vous pouvez également créer une évaluation personnalisée en créant un modèle avec vos propres contrôles et actions. Par exemple, vous souhaitez peut-être qu’un modèle couvre un contrôle de processus d’entreprise interne ou une norme de protection des données régionale qui n’est pas couverte par l’un de nos modèles d’évaluation pré-créés 325+.

##### <a name="learn-more"></a>En savoir plus

[Affichez la liste des modèles d’évaluation fournis par le Gestionnaire de conformité.](compliance-manager-templates-list.md)

[Obtenez des instructions détaillées sur la création et la modification de modèles d’évaluations.](compliance-manager-templates.md)

### <a name="improvement-actions"></a>Actions d’amélioration

Les actions d’amélioration permettent de centraliser vos activités de conformité. Chaque action d’amélioration fournit des recommandations destinées à vous aider à vous aligner sur les réglementations et normes en matière de protection des données. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer des tâches d’implémentation et de test. Vous pouvez également stocker de la documentation, des notes et enregistrer des mises à jour d’état dans l’action d’amélioration.

##### <a name="learn-more"></a>En savoir plus

[Utilisez les actions d’amélioration pour gérer votre flux de travail de conformité.](compliance-manager-improvement-actions.md)

[Découvrez comment les actions ont un impact sur votre score de conformité.](compliance-score-calculation.md#action-types-and-points)

## <a name="supported-languages"></a>Langues prises en charge

Le Gestionnaire de conformité est disponible dans les langues suivantes :

- Français
- Bahasa indonésien
- Bahasa Malais
- Chinois (simplifié)
- Chinois (traditionnel)
- Tchèque
- Danois
- Néerlandais
- Finnois
- Français
- Allemand
- Hébreu
- Hongrois
- Italien
- Japonais
- Coréen
- Norvégien
- Polonais
- Portugais (Brésil)
- Russe
- Espagnol
- Suédois
- Thaï
- Turc

## <a name="next-steps-set-up-and-customize"></a>Étapes suivantes : configurer et personnaliser

Découvrez comment vous inscrire, attribuer des autorisations et des rôles, configurer des paramètres et personnaliser l’affichage de votre tableau de bord lors de la mise en place du [Gestionnaire de conformité.](compliance-manager-setup.md)

Commencez ensuite à personnaliser le Gestionnaire de conformité pour vous aider à vous conformer aux normes industrielles les plus importantes pour votre organisation en [mettant en place des évaluations.](compliance-manager-assessments.md)

Pour vous aider à vous conformer aux réglementations en matière de confidentialité des données, nous avons conçu un flux de travail qui vous guide tout au long d’un processus de bout en bout pour planifier et implémenter des fonctionnalités au sein de Microsoft 365, notamment à l’aide du Gestionnaire de conformité. Pour plus d’informations, consultez [Déployer la protection des informations pour la confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy). 