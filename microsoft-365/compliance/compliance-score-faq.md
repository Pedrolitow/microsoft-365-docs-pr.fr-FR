---
title: Forum aux questions sur le score de conformité Microsoft (aperçu)
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
description: Trouvez des réponses aux questions fréquemment posées sur le score de conformité Microsoft, ce qui permet aux organisations de simplifier et d’automatiser les évaluations des risques.
ms.openlocfilehash: 6ba71620d689e6d028b61ff24f7c837337ef60c6
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45016199"
---
# <a name="compliance-score-preview-frequently-asked-questions"></a>Score de conformité (aperçu) Forum aux questions

## <a name="what-is-compliance-score"></a>Qu’est-ce que le score de conformité ?

Microsoft Compliance score est une fonctionnalité d’aperçu dans le [Centre de conformité microsoft 365](microsoft-365-compliance-center.md) qui vous aide à comprendre la position de la conformité de votre organisation. Il calcule un score basé sur les risques mesurant votre progression dans la réalisation d’actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires. Le score de conformité fournit un mappage de contrôle intégré qui permet de connecter des contrôles courants parmi les réglementations et normes clés. Ce mappage vous permet d’effectuer une action pour répondre à plusieurs besoins en même temps, ce qui vous permet de mettre à l’ampleur votre programme de conformité.

## <a name="whats-new-in-the-preview-version-of-compliance-score"></a>Quelles sont les nouveautés de la version d’évaluation du score de conformité ?

Consultez les [notes de publication du score de conformité](compliance-score-release-notes.md) pour en savoir plus sur les mises à jour des fonctionnalités et les problèmes connus.

## <a name="how-do-i-access-compliance-score"></a>Comment accéder au score de conformité ?

Accédez au [Centre de conformité microsoft 365](https://compliance.microsoft.com/) et **Connectez-vous** à l’aide d’un rôle d’administrateur général Microsoft 365 global, d’administrateur de conformité ou d’administration des données de conformité. Sélectionnez **score de conformité** dans le volet de navigation de gauche. Vous devez ensuite voir votre [tableau de bord de score de conformité avec votre score](compliance-score-setup.md#understand-the-compliance-score-dashboard). Si vous ne disposez pas de l’accès au rôle approprié, l’administrateur général de votre organisation peut vous accorder une autorisation.

## <a name="what-roles-or-permissions-are-needed-to-use-compliance-score"></a>Quels sont les rôles ou autorisations nécessaires pour utiliser le score de conformité ?

Le score de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Les actions que vous pouvez effectuer dépendent du type de rôle qui vous a été attribué. L’administrateur général Microsoft 365 de votre organisation est la personne qui peut effectuer les fonctions de configuration et administrer les rôles dans le score de conformité. Au minimum, les utilisateurs ont besoin du rôle de **lecteur global Azure ad** pour lire les données dans le score de conformité. Pour plus d’informations sur les autorisations, les rôles et les procédures de configuration, consultez [la rubrique Compliance score Setup](compliance-score-setup.md).

## <a name="what-is-the-difference-between-compliance-score-and-compliance-manager"></a>Quelle est la différence entre le score de conformité et le gestionnaire de conformité ?

Le score de conformité et le gestionnaire de conformité partagent le même serveur principal. Tout ce que vous faites dans un outil doit apparaître dans l’autre outil. Ils se trouvent à deux endroits différents : le score de conformité se trouve dans le centre de conformité Microsoft 365 et le gestionnaire de conformité se trouve dans le portail d’approbation de service Microsoft. Considérez le score de conformité comme une version simplifiée du gestionnaire de conformité, qui vous fournit une vue plus complète de la position actuelle de la conformité de votre organisation et des étapes que vous pouvez suivre pour l’améliorer.

Bien que vous puissiez effectuer de nombreuses actions directement dans le score de conformité, certaines fonctionnalités se trouvent dans le gestionnaire de conformité lors de la préversion publique. En savoir plus sur la [relation entre le score de conformité et le gestionnaire de conformité](compliance-score.md#relationship-to-compliance-manager).

Accéder au [Gestionnaire de conformité dans le portail d’approbation de service Microsoft](https://servicetrust.microsoft.com/ComplianceManager/V3). Veillez à **Sélectionner gestionnaire de conformité** dans le menu déroulant de la barre de navigation supérieure, qui possède les fonctionnalités les plus récentes, et *non pas le gestionnaire de conformité (classique)*, qui contient les fonctionnalités de la version préliminaire.

## <a name="should-i-use-compliance-score-or-compliance-manager"></a>Dois-je utiliser le score de conformité ou le gestionnaire de conformité ?

Le score de conformité est utile pour tous les membres de votre organisation qui jouent un rôle en conformité. Avec le score de conformité, vous n’avez pas besoin de vous familiariser avec les réglementations et les normes pour améliorer la protection des données de votre organisation. Le score de conformité est la position de départ optimale pour tous les utilisateurs. À partir de là, vous pouvez voir votre score de conformité, connaître les actions recommandées qui peuvent vous aider à réduire les risques, et à gérer vos évaluations.

Pour le moment, le gestionnaire de conformité est l’endroit où vous pouvez créer des modèles personnalisés pour générer des évaluations. En savoir plus sur [les actions prises en charge uniquement par le gestionnaire de conformité lors de la](compliance-score-release-notes.md#compliance-score-relationship-to-compliance-manager) préversion publique.

## <a name="if-i-have-a-high-score-does-it-mean-im-fully-compliant"></a>Si j’ai un score élevé, cela signifie-t-il que je suis entièrement conforme ?

Non. Votre score de conformité mesure votre progression dans l’exécution des actions recommandées qui permettent de réduire les risques liés à la protection des données et aux normes réglementaires. Il n’exprime pas une mesure absolue de la conformité de l’organisation avec une norme ou réglementation particulière. Le score de conformité ne doit pas être interprété comme une garantie de quelque façon que ce soit.

## <a name="what-regulations-and-standards-does-compliance-score-monitor"></a>Quels sont les règlements et normes dont le score de conformité est contrôlé ?

Le score de conformité vous donne un score initial basé sur la base de données de protection des données Microsoft 365, qui est un ensemble de contrôles qui inclut des normes et des réglementations industrielles communes. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et technologie Cybersecurity Framework) et ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Program) et RGPD (règlement général sur la protection des données de l’Union européenne).

Les organisations peuvent créer et ajouter des évaluations personnalisées qui sont plus pertinentes pour leur organisation. Utilisez l’un des [modèles](compliance-score-templates.md)de score de conformité prêts à l’emploi, personnalisez un modèle Microsoft avec vos propres contrôles et actions, ou créez votre propre modèle. Lisez les détails sur l' [utilisation des évaluations et des modèles](compliance-score-assessments.md).

## <a name="how-does-compliance-score-continuously-assess-my-environment"></a>Comment le score de conformité évalue-t-il en permanence mon environnement ?

Le score de conformité analyse automatiquement votre environnement et utilise le score de sécurité pour détecter les paramètres système. En savoir plus sur l' [évaluation continue](compliance-score-methodology.md#how-compliance-score-continuously-assesses-controls).

## <a name="what-is-the-difference-between-compliance-score-and-secure-score"></a>Quelle est la différence entre le score de conformité et le score de sécurité ?

Le score de conformité offre une vue étendue de la position de la protection et de la conformité des données de votre organisation. Le score de conformité fournit également des outils de flux de travail intégrés ; elle permet aux organisations d’affecter des tâches à des utilisateurs, de suivre l’implémentation des contrôles et l’état des tests, et de télécharger des preuves et de créer des rapports d’audit.

Microsoft Secure score est un outil d’analyse de la sécurité qui vous aide à comprendre la position de votre sécurité. [En savoir plus sur le score de sécurité et son fonctionnement](../security/mtp/microsoft-secure-score-new.md).

## <a name="which-cloud-services-are-covered-by-compliance-score"></a>Quels sont les services Cloud couverts par le score de conformité ?

Le score de conformité fournit actuellement des évaluations pour Office 365 et Intune. La couverture étendue est attendue dans les versions ultérieures et sera indiquée dans les [notes de publication du score de conformité](compliance-score-release-notes.md).

## <a name="can-i-use-compliance-score-for-non-microsoft-products"></a>Puis-je utiliser le score de conformité pour les produits non-Microsoft ?

Bien que le score de conformité offre une surveillance continue et des actions recommandées uniquement pour les services Cloud de Microsoft, vous pouvez ajouter des évaluations personnalisées dans le gestionnaire de conformité pour vos services tiers locaux. De cette manière, vous pouvez utiliser le score de conformité de Microsoft comme outil de gestion de la conformité SaaS pour vous aider à gérer tous les contrôles de vos biens numériques.

Vous pouvez utiliser l’un des [modèles](compliance-score-templates.md) prêts à utiliser pour créer des évaluations pour des normes particulières ou [créer votre propre modèle](working-with-compliance-manager.md#create-a-template), que vous devrez faire dans le gestionnaire de conformité.

## <a name="how-do-i-delete-a-template-or-assessment-i-no-longer-need"></a>Comment supprimer un modèle ou une évaluation dont je n’ai plus besoin ?

Pour supprimer une évaluation, ouvrez l’évaluation que vous souhaitez supprimer et sélectionnez **Supprimer l’évaluation**. Notez que la suppression d’une évaluation est définitive. Afficher des détails supplémentaires sur [la suppression des évaluations](compliance-score-assessments.md#delete-an-assessment). La suppression d’une évaluation ne supprime pas son modèle. Les modèles ne peuvent pas être supprimés, mais ils peuvent être masqués. Passez en revue [les instructions de masquage des modèles](working-with-compliance-manager.md#hide-a-template-or-an-assessment).

## <a name="what-test-procedures-does-microsoft-follow-for-controls"></a>Quelles sont les procédures de test suivies par Microsoft pour les contrôles ?

Microsoft participe à des audits annuels pour les contrôles. Vous pouvez consulter les rapports d’audit de nos auditeurs, qui peuvent être téléchargés à partir du [portail d’approbation de services Microsoft](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuideV3).

## <a name="why-are-some-controls-tested-annually-and-others-tested-every-three-years"></a>Pourquoi certains contrôles ont-ils été testés annuellement, et d’autres ont-ils été testés tous les trois ans ?

L’évaluation FedRAMP est un exemple de ce que cela peut être le cas. Elle est effectuée chaque année et teste une section de contrôles parmi les principales familles de contrôle. FedRAMP classifie les contrôles comme **principaux** lorsqu’ils sont suffisamment importants pour nécessiter des tests annuels. Les contrôles désignés comme non essentiels sont testés tous les trois ans. Un sous-ensemble de contrôles qui couvrent toutes les principales familles de contrôles est testé annuellement. De cette manière, chaque audit annuel examine les scénarios dans le tableau pour s’assurer que la solution est robuste. Pour en savoir plus sur le [processus d’évaluation annuel de FedRAMP](https://www.fedramp.gov/annual-assessment-guidance/).
