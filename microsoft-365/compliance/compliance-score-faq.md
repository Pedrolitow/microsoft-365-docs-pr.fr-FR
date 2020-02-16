---
title: FAQ sur le score de conformité Microsoft
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
ms.openlocfilehash: 9a71abba7b38bcf1e39073133f82abaedfc0d270
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42078641"
---
# <a name="microsoft-compliance-score-preview-frequently-asked-questions"></a>Score de conformité Microsoft (aperçu) Forum aux questions

## <a name="what-is-compliance-score"></a>Qu’est-ce que le score de conformité ?

Microsoft Compliance score est une fonctionnalité d’aperçu dans le [Centre de conformité microsoft 365](microsoft-365-compliance-center.md) qui vous aide à comprendre la position de la conformité de votre organisation. Il calcule un score basé sur les risques mesurant votre progression dans la réalisation d’actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires. Il fournit également un mappage de contrôle intégré qui permet de connecter des contrôles courants entre les réglementations et normes clés, de sorte que vous pouvez prendre une mesure pour répondre à plusieurs exigences en même temps et améliorer l’envergure de votre programme de conformité.

## <a name="how-do-i-access-compliance-score"></a>Comment accéder au score de conformité ?

Accédez au [Centre de conformité microsoft 365](https://compliance.microsoft.com/) et **Connectez-vous** à l’aide d’un rôle d’administrateur général Microsoft 365 global, d’administrateur de conformité ou d’administration des données de conformité. Sélectionnez **score de conformité** dans le volet de navigation de gauche. Vous devez ensuite voir votre [tableau de bord de score de conformité avec votre score](compliance-score-setup.md#understand-the-compliance-score-dashboard). Si vous ne disposez pas de l’accès au rôle approprié, l’administrateur général de votre organisation peut vous accorder une autorisation.

## <a name="what-roles-or-permissions-are-needed-to-use-compliance-score"></a>Quels sont les rôles ou autorisations nécessaires pour utiliser le score de conformité ?

Le score de conformité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC), et les actions que vous pouvez effectuer dépendent du type de rôle qui vous a été attribué. L’administrateur général Microsoft 365 de votre organisation est la personne qui peut effectuer les fonctions de configuration et administrer les rôles dans le score de conformité. Au minimum, les utilisateurs ont besoin du rôle de **lecteur global Azure ad** pour lire les données dans le score de conformité. Pour plus d’informations sur les autorisations, les rôles et les procédures de configuration, consultez [la rubrique Compliance score Setup](compliance-score-setup.md).

## <a name="what-is-the-difference-between-compliance-score-and-compliance-manager"></a>Quelle est la différence entre le score de conformité et le gestionnaire de conformité ?

Le score de conformité et le gestionnaire de conformité partagent le même serveur principal, mais ils se trouvent dans deux emplacements différents (le score de conformité se trouve dans le centre de conformité Microsoft 365 et le gestionnaire de conformité se trouve dans le portail d’approbation de service Microsoft). Considérez le score de conformité comme une version simplifiée du gestionnaire de conformité, qui vous fournit une vue plus complète de la position actuelle de la conformité de votre organisation et des étapes que vous pouvez suivre pour l’améliorer. Bien que vous puissiez effectuer de nombreuses actions directement dans le score de conformité, certaines fonctionnalités résident dans le gestionnaire de conformité pour l’instant. En savoir plus sur la [relation entre le score de conformité et le gestionnaire de conformité](compliance-score.md#relationship-to-compliance-manager).

## <a name="who-should-use-compliance-score-and-who-should-use-compliance-manager"></a>Qui doit utiliser le score de conformité et qui doit utiliser le gestionnaire de conformité ?

Le score de conformité est utile pour tous les membres de votre organisation qui jouent un rôle dans la surveillance de la conformité et l’exécution des activités afin de se conformer aux normes réglementaires. Avec le score de conformité, vous n’avez pas besoin de vous familiariser avec les réglementations et les normes pour améliorer la protection des données de votre organisation. Le score de conformité est la position de départ optimale pour tous les utilisateurs. À partir de là, vous pouvez voir votre score de conformité, connaître les actions recommandées qui peuvent vous aider à réduire les risques et, dans de nombreux cas, lancer directement dans les solutions pour effectuer ces actions.

Pour le moment, le gestionnaire de conformité est l’endroit où les utilisateurs peuvent gérer les évaluations et créer des modèles personnalisés pour créer des évaluations. En savoir plus sur [les actions prises en charge uniquement par le gestionnaire de conformité lors de la](compliance-score-release-notes.md#compliance-score-relationship-to-compliance-manager) préversion publique.

## <a name="if-i-have-a-high-score-does-it-mean-im-fully-compliant"></a>Si j’ai un score élevé, cela signifie-t-il que je suis entièrement conforme ?

Non. Votre score de conformité mesure votre progression dans l’exécution des actions recommandées qui permettent de réduire les risques liés à la protection des données et aux normes réglementaires. Il n’exprime pas une mesure absolue de la conformité de l’organisation avec une norme ou réglementation particulière. Le score de conformité ne doit pas être interprété comme une garantie de quelque façon que ce soit.

## <a name="what-regulations-and-standards-does-compliance-score-monitor"></a>Quels sont les règlements et normes dont le score de conformité est contrôlé ?

Le score de conformité vous donne un score initial basé sur la base de données de protection des données Microsoft 365, qui est un ensemble de contrôles qui inclut des normes et des réglementations industrielles communes. Cette ligne de base présente principalement des éléments d’Institut CSF (Institut national de normes et de technologie Cybersecurity Framework) et de l’ISO (Organisation internationale de normalisation), ainsi que de FedRAMP (Federal Risk and Authorization Management Programme) et RGPD (règlement général sur la protection des données de l’Union européenne).

Les organisations peuvent créer et ajouter des évaluations personnalisées qui sont plus pertinentes pour leur organisation. Vous pouvez utiliser l’un des [modèles prédéfinis](compliance-score.md#templates) de score de conformité pour créer des évaluations pour des normes particulières ou [créer votre propre modèle](working-with-compliance-manager.md#create-a-template-1).

Pour en savoir plus sur [la façon dont le score de conformité calcule votre score](compliance-score-methodology.md).

## <a name="what-is-the-difference-between-compliance-score-and-secure-score"></a>Quelle est la différence entre le score de conformité et le score de sécurité ?

Le score de conformité offre une vue étendue de la position de la protection et de la conformité des données de votre organisation. Le score de conformité fournit également des outils de flux de travail intégrés ; elle permet aux organisations d’affecter des tâches à des utilisateurs, de suivre l’implémentation des contrôles et l’état des tests, et de télécharger des preuves et de créer des rapports d’audit.

Microsoft Secure score est un outil d’analyse de la sécurité pour vous aider à comprendre votre position de sécurité. [En savoir plus sur le score de sécurité et son fonctionnement](../security/mtp/microsoft-secure-score.md).

## <a name="which-cloud-services-are-covered-by-compliance-score"></a>Quels sont les services Cloud couverts par le score de conformité ?

Le score de conformité fournit actuellement des évaluations pour Office 365 et Intune. La couverture étendue est attendue dans les versions ultérieures et sera indiquée dans les [notes de publication du score de conformité](compliance-score-release-notes.md).

## <a name="can-i-use-compliance-score-for-non-microsoft-products"></a>Puis-je utiliser le score de conformité pour les produits non-Microsoft ?

Bien que le score de conformité offre une surveillance continue et des actions recommandées uniquement pour les services Cloud de Microsoft, vous pouvez ajouter des évaluations personnalisées dans le gestionnaire de conformité pour vos services tiers locaux. De cette manière, vous pouvez utiliser le score de conformité de Microsoft comme outil de gestion de la conformité SaaS pour vous aider à gérer tous les contrôles de vos biens numériques.

Vous pouvez utiliser l’un des [modèles prédéfinis](compliance-score.md#templates) de score de conformité pour créer des évaluations pour des normes particulières ou [créer votre propre modèle](working-with-compliance-manager.md#create-a-template-1).

## <a name="how-do-i-delete-a-template-or-assessment-i-no-longer-need"></a>Comment supprimer un modèle ou une évaluation dont je n’ai plus besoin ?

Vous ne pouvez pas supprimer une évaluation ou un modèle, mais vous pouvez les masquer dans votre vue. Passez en revue [les instructions pour masquer les évaluations](working-with-compliance-manager.md#hide-a-template-or-an-assessment).
