---
title: Score de conformité Microsoft (aperçu)
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
description: Microsoft Compliance score (Preview) aide les organisations à simplifier et à automatiser les évaluations des risques et suggère des actions recommandées pour résoudre les risques.
ms.openlocfilehash: 0cb8bd0b5aa39be2a9a6e706afa21bb7dc53eadb
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016137"
---
# <a name="microsoft-compliance-score-preview"></a>Score de conformité Microsoft (aperçu)

**Dans cet article :** Découvrez le score de conformité, comment il simplifie la gestion de la conformité et comment le configurer pour votre organisation.

Nouveautés **:** La version de juin 2020 inclut de nouvelles fonctionnalités permettant de créer et de gérer des évaluations, ainsi que d’afficher les contrôles dans le score de conformité. Consultez les [notes de publication du score de conformité](compliance-score-release-notes.md) pour découvrir les nouveautés de la préversion publique du score de conformité.

## <a name="what-is-compliance-score"></a>Qu’est-ce que le score de conformité

[Microsoft Compliance score](https://compliance.microsoft.com/compliancescore) est une fonctionnalité d’aperçu dans le [Centre de conformité Microsoft 365](microsoft-365-compliance-center.md) pour vous aider à comprendre la position de la conformité de votre organisation. Il calcule un score basé sur les risques mesurant votre progression dans la réalisation d’actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires.

Vous pouvez utiliser le score de conformité comme un outil permettant de suivre toutes vos évaluations de risques. Il fournit des fonctionnalités de flux de travail pour vous aider à effectuer efficacement les évaluations des risques par le biais d’un outil courant.

Les utilisateurs du [Gestionnaire de conformité](compliance-manager-overview.md) remarqueront que le score de conformité est désormais une fonctionnalité autonome avec un design plus simple et plus convivial pour aider les organisations à gérer plus facilement la conformité.

La page principale du score de conformité est votre tableau de bord personnalisé. Il indique votre score actuel, vous aide à voir ce qui vous convient et vous guide sur les actions à effectuer pour améliorer votre score. Votre tableau de bord de score de conformité doit ressembler à ceci :

![Score de conformité-tableau de bord](../media/compliance-score-dashboard.png "Tableau de bord de score de conformité")

### <a name="simplified-compliance-management"></a>Gestion simplifiée de la conformité

Le score de conformité simplifie la gestion de la conformité en fournissant les éléments suivants :

- **Évaluations continues**: analyse automatiquement les environnements Microsoft 365 afin de détecter et de surveiller l’efficacité des contrôles de protection des données dans votre système.
- **Actions recommandées**: fournit des recommandations et des instructions pas à pas pour la mise en œuvre de contrôles afin d’optimiser votre score
-  **Mappage de contrôle intégré**: vous permet de rester au fait des dernières évolutions du paysage de conformité grâce à une infrastructure de contrôle commune intégrée

> [!IMPORTANT]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme une garantie de conformité. Il vous revient d’évaluer et de valider l’efficacité des contrôles client selon votre environnement réglementaire. Ces services sont actuellement en version préliminaire et soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également [les conseils Microsoft 365 sur les licences pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="relationship-to-compliance-manager"></a>Relation avec le gestionnaire de conformité

Considérez le score de conformité comme une expérience simplifiée du gestionnaire de conformité. Bien que les deux outils existants soient distincts mais encore intégrés, le score de conformité permet de surveiller plus facilement la position globale de votre conformité et de prendre des mesures pour l’améliorer.

Le score de conformité partage le même serveur principal avec le gestionnaire de conformité. Tout ce que vous faites dans un outil doit apparaître dans l’autre outil.

Certaines fonctionnalités d’évaluation et de gestion des modèles restent dans le gestionnaire de conformité lors de la préversion publique. Nous vous recommandons de commencer toutes les activités de gestion de la conformité dans le score de conformité. Lorsque vous accédez à des fonctions gérées par le gestionnaire de conformité, nous vous guiderons.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Comprendre la relation entre le score de conformité et le gestionnaire de conformité](compliance-score-release-notes.md#compliance-score-relationship-to-compliance-manager).

## <a name="understanding-your-score"></a>Présentation de votre score

Récompenses du score de conformité vous permet d’effectuer les actions prises pour se conformer à une réglementation, à une norme ou à une stratégie. Chaque action a un impact différent sur votre score en fonction des risques potentiels impliqués. Votre score peut vous aider à déterminer l’action à mettre en évidence afin d’améliorer votre position de conformité globale.

Le score de conformité vous donne un score initial basé sur la base de données de protection des données Microsoft 365.  Cette configuration de référence est un ensemble de contrôles qui inclut des normes et des réglementations clés pour la protection des données et la gouvernance générale des données. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

L’évaluation de la base de données de protection des données est utilisée pour calculer votre score initial avant de configurer d’autres évaluations. Lors de votre première visite, le score de conformité collecte déjà des signaux à partir de vos solutions Microsoft 365. Vous verrez en un clin d’œil comment votre organisation est en fonction des normes et des réglementations clés en matière de protection des données, et découvrez les actions d’amélioration suggérées à entreprendre.

Étant donné que chaque organisation a des besoins spécifiques, le score de conformité repose sur la configuration et la gestion de vos propres évaluations afin de mieux atténuer les risques. Par exemple, si votre organisation appartient au secteur financier, vous souhaiterez peut-être ajouter l’évaluation FFIEC. Si votre organisation appartient au secteur de la santé, vous pouvez ajouter l’évaluation HIPAA/Hi-Tech.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Comprendre comment le score de conformité est calculé et surveillé en continu](compliance-score-methodology.md).

[Créez et gérez les évaluations dans le score de conformité](compliance-score-assessments.md).

## <a name="key-components-controls-assessments-templates-improvement-actions"></a>Composants clés : contrôles, évaluations, modèles, actions d’amélioration

Le score de conformité utilise plusieurs composants pour vous aider à gérer vos activités de conformité. Lorsque vous utilisez le score de conformité pour affecter, tester et surveiller les activités de conformité, il est utile de comprendre les principaux composants : contrôles, évaluations, modèles et actions d’amélioration.

### <a name="controls"></a>Contrôles

Un contrôle est une exigence d’un règlement, d’une norme ou d’une stratégie. Il définit le mode d’évaluation et de gestion de la configuration du système, du processus organisationnel et des personnes chargées de satisfaire une exigence spécifique d’un règlement, d’une norme ou d’une stratégie.

Le score de conformité effectue le suivi de deux types de contrôles :

1. **Contrôles gérés par Microsoft**: contrôles pour les services Cloud Microsoft, que Microsoft est responsable de l’implémentation
2. **Vos contrôles**: parfois appelés contrôles client, il s’agit de contrôles implémentés et gérés par votre organisation.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Surveillez la progression de vos contrôles](compliance-score-assessments.md#monitor-assessment-progress-and-controls).

### <a name="assessments"></a>Évaluations

Une évaluation est un regroupement de contrôles à partir d’un règlement, d’une norme ou d’une stratégie spécifique. La réalisation des actions d’une évaluation vous permet de répondre aux exigences d’une norme, d’une réglementation ou d’une loi. Par exemple, vous pouvez avoir une évaluation qui, lorsque vous terminez toutes les actions qu’elle contient, présente vos paramètres Microsoft 365 en fonction des exigences de la norme ISO 27001.

Les évaluations comportent plusieurs composants :

- **Services dans l’étendue**: l’ensemble spécifique des services Microsoft applicables à l’évaluation
- **Contrôles gérés par Microsoft**: contrôles que Microsoft implémente et teste
- **Vos contrôles**: contrôles que vous gérez
- **Score d’évaluation**: pourcentage de points obtenus en effectuant des actions d’amélioration au sein de cette évaluation

Lors de la création d’évaluations, vous les affectez à un **groupe**. Vous pouvez configurer des groupes de la manière la plus logique pour votre organisation. Par exemple, vous pouvez regrouper les évaluations par année, standard de conformité, service, teams au sein de votre organisation ou une autre méthode. Une fois que vous avez créé des groupes, vous pouvez [filtrer votre tableau de bord de score de conformité](compliance-score-setup.md#filtering-your-dashboard-view) pour afficher votre score par un ou plusieurs groupes.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Créez et gérez les évaluations dans le score de conformité](compliance-score-assessments.md).

### <a name="templates"></a>Modèles

Le score de conformité fournit des modèles prêts à vous permettre de créer rapidement des évaluations. Vous pouvez modifier ces modèles pour créer une évaluation optimisée pour vos besoins. Vous pouvez également créer une évaluation personnalisée en développant votre propre modèle avec vos propres contrôles et actions. Par exemple, vous souhaiterez peut-être utiliser un modèle pour couvrir un contrôle de processus d’entreprise interne ou une norme de protection des données régionale qui n’est pas couverte par l’un de nos modèles.

La création de vos propres modèles vous permet de suivre non seulement les évaluations de Microsoft Cloud, mais également d’autres évaluations des risques dans l’étendue de votre organisation.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Affichez les modèles disponibles dans score de conformité pour la création d’évaluations](compliance-score-templates.md).

[Obtenir des instructions détaillées sur la création et la modification du gestionnaire de conformité des modèles](working-with-compliance-manager.md#templates).

### <a name="improvement-actions"></a>Actions d’amélioration

Les actions d’amélioration centralisent vos activités de conformité. Chaque action d’amélioration fournit des conseils détaillés sur la mise en œuvre pour vous aider à vous aligner sur les normes et réglementations sur la protection des données. Des actions peuvent être attribuées à des utilisateurs de votre organisation pour effectuer le travail d’implémentation et de test. Vous pouvez également stocker la documentation, les notes et les mises à jour de l’état des enregistrements au cours de l’action d’amélioration.

#### <a name="learn-more"></a>Si vous souhaitez en savoir plus

[Utilisez les actions d’amélioration pour gérer votre flux de travail de conformité](compliance-score-improvement-actions.md).

## <a name="next-steps-set-up-and-customize"></a>Étapes suivantes : configurer et personnaliser

Découvrez comment vous connecter, définir des autorisations et des rôles, configurer des mises à jour de score sécurisé et personnaliser votre vue de tableau de bord au niveau de [la configuration du score de conformité](compliance-score-setup.md).

Ensuite, commencez à personnaliser le score de conformité pour votre organisation en [configurant des évaluations](compliance-score-assessments.md).