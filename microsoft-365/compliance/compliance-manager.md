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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Le gestionnaire de conformité Microsoft aide les organisations à simplifier et à automatiser les évaluations des risques et suggère des actions recommandées pour résoudre les risques.
ms.openlocfilehash: b6ffd0156b295f03049d68ba99ad30c0ab8ae43b
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48204336"
---
# <a name="microsoft-compliance-manager"></a>Gestionnaire de conformité Microsoft

**Dans cet article :** Découvrez ce que le gestionnaire de conformité est, comment il simplifie la conformité et réduit les risques, et ses composants clés.

## <a name="whats-new-the-ga-release-of-compliance-manager"></a>Nouveautés : la version GA du gestionnaire de conformité

Le gestionnaire de conformité est désormais généralement disponible (GA) en tant que solution de gestion de la conformité de bout en bout dans le [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md). Avec cette version, le gestionnaire de conformité termine la transition à partir de son emplacement précédent dans le portail d’approbation de service Microsoft.

Le début de la préversion publique du score de conformité est devenu un outil centralisé doté de fonctionnalités de gestion de la conformité améliorées et d’une plus grande facilité d’utilisation.  La version GA offre une plus grande collection d’évaluations prédéfinies pour vous aider à mettre à l’échelle vos activités de conformité.

**En savoir plus sur la version GA :**
- Nos [questions fréquemment posées](compliance-manager-faq.md) vous guident plus en détail sur l’évolution.
- Découvrez les améliorations apportées aux fonctionnalités GA dans ce billet de [blog](https://aka.ms/compliancemanager/GAblog).

Regardez la vidéo ci-dessous pour savoir comment le gestionnaire de conformité peut vous aider à simplifier la gestion de la conformité de votre organisation :
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4FGYZ]

## <a name="what-is-compliance-manager"></a>Qu’est-ce que le gestionnaire de conformité

Le [Gestionnaire de conformité Microsoft](https://compliance.microsoft.com/compliancemanager) est une fonctionnalité du [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md) qui vous permet de gérer les besoins de conformité de votre organisation avec plus de commodité et de commodité. Le gestionnaire de conformité peut vous aider tout au long du processus de conformité, de la prise en compte de vos risques de protection des données à la gestion des complexités de l’implémentation des contrôles, au respect des réglementations et des certifications, ainsi qu’à la création de rapports auprès des auditeurs.

Le gestionnaire de conformité simplifie la conformité et réduit les risques en fournissant :

- Des évaluations prédéfinies pour les normes et réglementations régionales courantes, ou des évaluations personnalisées pour répondre à vos besoins uniques en matière de conformité (les évaluations disponibles dépendent de votre contrat de licence ; [en savoir plus](https://go.microsoft.com/fwlink/?linkid=2132371)).

- Fonctionnalités de flux de travail pour vous aider à effectuer efficacement les évaluations des risques via un seul outil.

- Des conseils détaillés sur les actions d’amélioration suggérées pour vous aider à respecter les normes et réglementations les plus pertinentes pour votre organisation. Pour les actions gérées par Microsoft, vous verrez les détails de l’implémentation et les résultats de l’audit.

- Un score de conformité basé sur les risques pour vous aider à comprendre la position de votre conformité en mesurant votre progression dans la réalisation des actions d’amélioration.

Votre tableau de bord du gestionnaire de conformité indique votre score de conformité actuel, vous aide à voir ce qui vous convient et vous guide sur les actions d’amélioration clés. Voici un exemple de tableau de bord du gestionnaire de conformité :

![Gestionnaire de conformité-tableau de bord](../media/compliance-manager-dashboard.png "Tableau de bord du gestionnaire de conformité")

## <a name="understanding-your-compliance-score"></a>Comprendre votre score de conformité

Prix du gestionnaire de conformité vous permet d’effectuer des actions d’amélioration prises afin de se conformer à une réglementation, une norme ou une stratégie, et combine ces points dans un score de conformité global. Chaque action a un impact différent sur votre score en fonction des risques potentiels impliqués. Votre score de conformité peut vous aider à hiérarchiser l’action à mettre en évidence pour améliorer votre position de conformité globale.

Le gestionnaire de conformité fournit un score initial basé sur la base de données de protection des données Microsoft 365. Cette configuration de référence est un ensemble de contrôles qui inclut des normes et des réglementations clés pour la protection des données et la gouvernance générale des données.

##### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Comprendre comment le score de conformité est calculé](compliance-score-calculation.md).

[Découvrez comment utiliser les actions d’amélioration](compliance-manager-improvement-actions.md).

## <a name="key-elements-controls-assessments-templates-improvement-actions"></a>Éléments clés : contrôles, évaluations, modèles, actions d’amélioration

Le gestionnaire de conformité utilise plusieurs éléments de données pour vous aider à gérer vos activités de conformité. Lorsque vous utilisez le gestionnaire de conformité pour affecter, tester et surveiller les activités de conformité, il est utile de posséder une compréhension de base des éléments clés : contrôles, évaluations, modèles et actions d’amélioration.

### <a name="controls"></a>Contrôles

Un contrôle est une exigence d’un règlement, d’une norme ou d’une stratégie. Il définit le mode d’évaluation et de gestion de la configuration du système, du processus organisationnel et des personnes chargées de satisfaire une exigence spécifique d’un règlement, d’une norme ou d’une stratégie.

Le gestionnaire de conformité suit les types de contrôles suivants :

1. **Contrôles gérés par Microsoft**: contrôles pour les services Cloud Microsoft, que Microsoft est responsable de l’implémentation
2. **Vos contrôles**: parfois appelés contrôles gérés par le client, il s’agit de contrôles implémentés et gérés par votre organisation.
3. **Contrôles partagés**: les contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation

##### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Surveillez la progression de vos contrôles](compliance-manager-assessments.md#monitor-assessment-progress-and-controls).

[Découvrez comment le gestionnaire de conformité évalue en permanence les contrôles](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

### <a name="assessments"></a>Évaluations

Une évaluation est un regroupement de contrôles à partir d’un règlement, d’une norme ou d’une stratégie spécifique. La réalisation des actions d’une évaluation vous permet de répondre aux exigences d’une norme, d’une réglementation ou d’une loi. Par exemple, vous pouvez avoir une évaluation qui, lorsque vous terminez toutes les actions qu’elle contient, permet de mettre vos paramètres Microsoft 365 en ligne avec la configuration ISO 27001 requise.

Les évaluations comportent plusieurs composants :

- **Services dans l’étendue**: l’ensemble spécifique des services Microsoft applicables à l’évaluation
- **Contrôles gérés par Microsoft**: contrôles pour les services de Cloud Computing Microsoft, que Microsoft met en œuvre en votre nom
- **Vos contrôles**: parfois appelés contrôles gérés par le client, il s’agit de contrôles implémentés et gérés par votre organisation.
- **Contrôles partagés**: les contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation
- **Score d’évaluation**: indique votre progression dans la réalisation de tous les points possibles à partir d’actions au sein de l’évaluation gérée par votre organisation et par Microsoft

Lors de la création d’évaluations, vous les affectez à un groupe. Vous pouvez configurer des groupes de la manière la plus logique pour votre organisation. Par exemple, vous pouvez regrouper les évaluations en fonction de l’année, de la région, de la solution, des équipes au sein de votre organisation ou d’une autre façon. Une fois que vous avez créé des groupes, vous pouvez [filtrer votre tableau de bord du gestionnaire de conformité](compliance-manager-setup.md#filtering-your-dashboard-view) pour afficher votre score par un ou plusieurs groupes.

##### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Créer et gérer des évaluations dans le gestionnaire de conformité](compliance-manager-assessments.md).

### <a name="templates"></a>Modèles

Le gestionnaire de conformité fournit des modèles pour vous aider à créer rapidement des évaluations. Vous pouvez modifier ces modèles pour créer une évaluation optimisée pour vos besoins. Vous pouvez également créer une évaluation personnalisée en créant un modèle avec vos propres contrôles et actions. Par exemple, vous souhaiterez peut-être utiliser un modèle pour couvrir un contrôle de processus d’entreprise interne ou une norme régionale de protection des données qui n’est pas couverte par l’un de nos plus de 150 modèles d’évaluation prédéfinis.

##### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Affichez la liste des modèles d’évaluation fournis par le gestionnaire de conformité](compliance-manager-templates-list.md).

[Obtenir des instructions détaillées sur la création et la modification de modèles pour les évaluations](compliance-manager-templates.md).

### <a name="improvement-actions"></a>Actions d’amélioration

Les actions d’amélioration permettent de centraliser vos activités de conformité. Chaque action d’amélioration fournit des conseils recommandés pour vous aider à vous aligner sur les normes et réglementations en matière de protection des données. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au cours de l’action d’amélioration.

##### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Utilisez les actions d’amélioration pour gérer votre flux de travail de conformité](compliance-manager-improvement-actions.md).

[Découvrez comment les actions ont un impact sur votre score de conformité](compliance-score-calculation.md#action-types-and-points).

## <a name="supported-languages"></a>Langues prises en charge

Le gestionnaire de conformité est disponible dans les langues suivantes :

- Anglais
- Bahasa indonésien
- Bahasa malais
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

## <a name="next-steps-set-up-and-customize"></a>Étapes suivantes : configurer et personnaliser

Découvrez comment vous connecter, attribuer des autorisations et des rôles, configurer des paramètres et personnaliser l’affichage de votre tableau de bord dans la rubrique [prise en main du gestionnaire de conformité](compliance-manager-setup.md).

Ensuite, commencez à personnaliser le gestionnaire de conformité afin de vous conformer aux normes industrielles les plus importantes pour votre organisation en [configurant des évaluations](compliance-manager-assessments.md).