---
title: Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Compliance Manager aide les organisations à simplifier et à automatiser les évaluations des risques, et suggère des actions recommandées pour aider à résoudre les risques.
ms.openlocfilehash: 1d5f036b8bc97da431ed6e41017d59e01db749a4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997095"
---
# <a name="microsoft-purview-compliance-manager"></a>Gestionnaire de conformité Microsoft Purview

> [!TIP]
> *Saviez-vous que vous pouvez essayer les versions Premium des neuf solutions Microsoft Purview gratuitement ?* Utilisez la version d’évaluation des solutions Purview de 90 jours pour découvrir comment des fonctionnalités Purview robustes peuvent aider votre organisation à répondre à ses besoins de conformité. Microsoft 365 E3 et Office 365 E3 clients peuvent commencer maintenant sur le [hub d’essais du portail de conformité Microsoft Purview](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Découvrez plus d’informations sur [les personnes qui peuvent s’inscrire et les conditions d’évaluation](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**Dans cet article :** Découvrez ce qu’est le Gestionnaire de conformité, comment il permet de simplifier la conformité et de réduire les risques, ainsi que ses composants clés.

## <a name="what-is-compliance-manager"></a>Qu’est-ce que le Gestionnaire de conformité ?

Le [Gestionnaire de conformité Microsoft Purview](https://compliance.microsoft.com/compliancemanager) est une fonctionnalité du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> qui vous permet de gérer les exigences de conformité de votre organisation avec plus de facilité et de commodité. Le Gestionnaire de conformité peut vous aider tout au long de votre parcours de conformité, de l’inventaire des risques de protection de vos données à la gestion des complexités de l’implémentation de contrôles, la mise à jour des réglementations et des certifications et la création de rapports aux auditeurs.

Regardez la vidéo ci-dessous pour découvrir comment le Gestionnaire de conformité peut simplifier la façon dont votre organisation gère la conformité :
<br>
<br>
>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4FGYZ]

Le Gestionnaire de conformité permet de simplifier la conformité et de réduire les risques en fournissant :

- Des évaluations prédéfinifiées pour les normes et réglementations courantes de l’industrie et régionales, ou des évaluations personnalisées pour répondre à vos besoins de conformité uniques (les évaluations disponibles dépendent de votre contrat de licence; [en savoir plus](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)).

- Fonctionnalités de flux de travail pour vous aider à évaluer efficacement vos risques à l’aide d’un seul outil.

- Conseils détaillés pas à pas sur les suggestions d’actions d’amélioration pour vous aider à vous conformer aux normes et réglementations les plus pertinentes pour votre organisation. Pour les actions gérées par Microsoft, vous verrez les détails de l’implémentation et les résultats de l’audit.

- Un score de conformité basé sur les risques pour vous aider à comprendre votre posture de conformité en mesurant votre progression dans l’exécution des actions d’amélioration.

Votre tableau de bord gestionnaire de conformité affiche votre score de conformité actuel, vous aide à voir ce qui nécessite une attention particulière et vous guide vers les principales actions d’amélioration. Voici un exemple de ce à quoi ressemblera votre tableau de bord gestionnaire de conformité :

![Gestionnaire de conformité – tableau de bord.](../media/compliance-manager-dashboard.png "Tableau de bord du Gestionnaire de conformité")

## <a name="understanding-your-compliance-score"></a>Comprendre votre score de conformité

Le Gestionnaire de conformité vous attribue des points pour avoir terminé les actions d’amélioration prises pour se conformer à une réglementation, une norme ou une stratégie, et combine ces points dans un score de conformité global. Chaque action a un impact différent sur votre score en fonction des risques potentiels impliqués. Votre score de conformité peut vous aider à hiérarchiser l’action sur laquelle vous devez vous concentrer pour améliorer votre posture de conformité globale.

Le Gestionnaire de conformité vous donne un score initial basé sur la base de référence de protection des données Microsoft 365. Cette base de référence est un ensemble de contrôles qui inclut des réglementations et des normes clés pour la protection des données et la gouvernance générale des données.

##### <a name="learn-more"></a>En savoir plus

[Comprendre comment votre score de conformité est calculé](compliance-score-calculation.md).

[Découvrez comment utiliser des actions d’amélioration](compliance-manager-improvement-actions.md).

## <a name="key-elements-controls-assessments-templates-improvement-actions"></a>Éléments clés : contrôles, évaluations, modèles, actions d’amélioration

Le Gestionnaire de conformité utilise plusieurs éléments de données pour vous aider à gérer vos activités de conformité. À mesure que vous utilisez le Gestionnaire de conformité pour affecter, tester et surveiller les activités de conformité, il est utile d’avoir une compréhension de base des éléments clés : contrôles, évaluations, modèles et actions d’amélioration.

### <a name="controls"></a>Contrôles

Un contrôle est une exigence pour une règlementation, une norme ou une stratégie. Il détermine le mode d’évaluation et de gestion de la configuration du système, des processus organisationnels et des personnes responsables de la conformité à une exigence spécifique d’une réglementation, d’une norme ou d’une stratégie.

Le Gestionnaire de conformité effectue le suivi des types de contrôles suivants :

1. **Contrôles managés Microsoft** : contrôles pour les services cloud Microsoft, que Microsoft est responsable de l’implémentation
2. **Vos contrôles** : parfois appelés contrôles gérés par le client, il s’agit de contrôles implémentés et gérés par votre organisation
3. **Contrôles partagés** : il s’agit de contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation

##### <a name="learn-more"></a>En savoir plus

[Surveillez la progression de vos contrôles](compliance-manager-assessments.md#monitor-assessment-progress-and-controls).

[Découvrez comment le Gestionnaire de conformité évalue en permanence les contrôles](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

### <a name="assessments"></a>Évaluations

Une évaluation consiste à regrouper des contrôles à partir d’une réglementation, d’une norme ou d’une stratégie spécifique. Effectuer les actions d’une évaluation vous permet de répondre aux exigences d’une norme, d’un règlement ou d’une loi. Par exemple, vous pouvez avoir une évaluation qui, lorsque vous effectuez toutes les actions qu’elle contient, vous aide à mettre vos paramètres Microsoft 365 en conformité avec les exigences ISO 27001.

Les évaluations ont plusieurs composants :

- **Services concernés** : ensemble spécifique de services Microsoft applicable à l’évaluation
- **Contrôles managés Microsoft** : contrôles pour les services cloud Microsoft, que Microsoft implémente en votre nom
- **Vos contrôles** : parfois appelés contrôles gérés par le client, il s’agit de contrôles implémentés et gérés par votre organisation
- **Contrôles partagés** : il s’agit de contrôles que votre organisation et Microsoft partagent la responsabilité de l’implémentation
- **Score d’évaluation** : indique vos progrès dans la réalisation du total des points possibles à partir des actions au sein de l’évaluation qui sont gérées par votre organisation et par Microsoft

Lorsque vous créez des évaluations, vous les affectez à un groupe. Vous pouvez configurer des groupes de la manière la plus logique pour votre organisation. Par exemple, vous pouvez regrouper des évaluations par année d’audit, région, solution, équipes au sein de votre organisation ou d’une autre façon. Une fois que vous avez créé des groupes, vous pouvez [filtrer votre tableau de bord gestionnaire de conformité](compliance-manager-setup.md#filtering-your-dashboard-view) pour afficher votre score par un ou plusieurs groupes.

##### <a name="learn-more"></a>En savoir plus

[Générez et gérez des évaluations dans le Gestionnaire de conformité](compliance-manager-assessments.md).

### <a name="templates"></a>Modèles

Le Gestionnaire de conformité fournit des modèles pour vous aider à créer rapidement des évaluations. Vous pouvez modifier ces modèles pour créer une évaluation optimisée pour vos besoins. Vous pouvez également créer une évaluation personnalisée en créant un modèle avec vos propres contrôles et actions. Par exemple, vous souhaiterez peut-être qu’un modèle couvre un contrôle de processus métier interne, ou une norme régionale de protection des données qui n’est pas couverte par l’un de nos modèles d’évaluation prédéfinissants de plus de 325.

##### <a name="learn-more"></a>En savoir plus

[Affichez la liste des modèles d’évaluation fournis par le Gestionnaire de conformité](compliance-manager-templates-list.md).

[Obtenez des instructions détaillées sur la création et la modification de modèles pour les évaluations](compliance-manager-templates.md).

### <a name="improvement-actions"></a>Actions d’amélioration

Les actions d’amélioration permettent de centraliser vos activités de conformité. Chaque action d’amélioration fournit des conseils recommandés destinés à vous aider à vous aligner sur les réglementations et normes de protection des données. Des actions d’amélioration peuvent être affectées aux utilisateurs de votre organisation pour effectuer des travaux d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements dans l’action d’amélioration.

##### <a name="learn-more"></a>En savoir plus

[Utilisez des actions d’amélioration pour gérer votre flux de travail de conformité](compliance-manager-improvement-actions.md).

[Découvrez l’impact des actions sur votre score de conformité](compliance-score-calculation.md#action-types-and-points).

## <a name="supported-languages"></a>Langues prises en charge

Le Gestionnaire de conformité est disponible dans les langues suivantes :

- Anglais
- Bahasa Indonésien
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

Découvrez comment vous connecter, attribuer des autorisations et des rôles, configurer des paramètres et personnaliser l’affichage de votre tableau de bord à [Démarrage avec le Gestionnaire de conformité](compliance-manager-setup.md).

Ensuite, commencez à personnaliser le Gestionnaire de conformité pour vous aider à vous conformer aux normes du secteur qui sont les plus importantes pour votre organisation [en configurant des évaluations](compliance-manager-assessments.md).

Pour vous aider à vous conformer aux réglementations en matière de confidentialité des données, nous avons conçu un flux de travail qui vous guide tout au long d’un processus de bout en bout pour planifier et implémenter des fonctionnalités dans Microsoft 365, notamment à l’aide du Gestionnaire de conformité. Pour plus d’informations, consultez [Déployer la protection des informations pour la confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy). 
