---
title: Utiliser le gestionnaire de conformité pour gérer les actions d’amélioration
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Découvrez comment utiliser le score de conformité et le gestionnaire de conformité pour améliorer votre niveau de protection des données personnelles.
ms.openlocfilehash: 5b41fa9fc52253d415a22aaa3422a87c4f1bda7c
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48377098"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Utiliser le gestionnaire de conformité pour gérer les actions d’amélioration

Le gestionnaire de conformité Microsoft peut vous aider à gérer les améliorations apportées aux réglementations de confidentialité des données, telles que le règlement général sur la protection des [données (RGPD)](../compliance/gdpr.md), la Loi sur la [protection des consommateurs California CCPA)](../compliance/ccpa-faq.md), le HIPAA-Hi (USA Health Care Privacy Act) et le Brésil (Data Protection Act).

Cet article fournit des instructions sur l’utilisation de cet outil à des fins de confidentialité des données.

>[!Note]
>Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité. Il vous revient d’évaluer et de valider l’efficacité des contrôles client selon votre environnement réglementaire. Ces services sont soumis aux conditions des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Consultez également [les conseils Microsoft 365 sur les licences pour la sécurité et la conformité](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)
>

## <a name="getting-started-with-compliance-manager"></a>Mise en route avec le gestionnaire de conformité

#### <a name="what-is-compliance-manager"></a>Qu’est-ce que le gestionnaire de conformité

Le [Gestionnaire de conformité](../compliance/compliance-manager.md) est un outil d’évaluation de risque basé sur un flux de travail dans le centre de conformité Microsoft 365 pour la gestion des activités de conformité réglementaire liées aux services Cloud de Microsoft. Dans le cadre de votre abonnement Microsoft 365 ou Azure Active Directory (Azure AD), le gestionnaire de conformité vous aide à gérer la conformité réglementaire dans le cadre du modèle de responsabilité partagé pour les services Cloud de Microsoft.

**Prêt à utiliser les évaluations**

Le gestionnaire de conformité fournit des modèles prédéfinis pour la [création d’évaluations](../compliance/compliance-manager-assessments.md) alignées sur les réglementations liées à la confidentialité des données, telles que RGPD et HIPAA/Hi. Les modèles disposent d’un mappage de contrôle intégré pour vous aider à prendre des mesures d’amélioration pour répondre aux exigences de la réglementation. Chaque évaluation fournit des informations sur les contrôles que chaque réglementation appelle pour le service cible, ainsi que les contrôles gérés et les contrôles gérés par Microsoft. 

L’utilisation d’un modèle prédéfini vous permet de commencer rapidement à utiliser les évaluations des risques. À mesure que vous vous familiarisez avec le gestionnaire de conformité, vous pouvez personnaliser un modèle prédéfini en ajoutant vos propres contrôles et actions d’amélioration, ou vous pouvez créer vos propres évaluations personnalisées pour répondre aux besoins de votre organisation.

Affichez la [liste complète des modèles d’évaluation](../compliance/compliance-manager-templates-list.md) fournis par le gestionnaire de conformité.

**Score de conformité en temps réel**

Le gestionnaire de conformité fournit également un score de conformité qui mesure votre progression dans l’exécution des actions d’amélioration recommandées dans les contrôles. Vous pouvez utiliser ce score pour surveiller votre progression et hiérarchiser les actions en fonction de leur potentiel pour réduire les risques.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Utiliser le Guide de démarrage rapide du gestionnaire de conformité

Le Guide de [démarrage rapide du gestionnaire de conformité](../compliance/compliance-manager-quickstart.md) fournit des étapes et des liens vers des ressources clés pour vous aider à utiliser le gestionnaire de conformité :

- [Première visite : familiarisation avec le gestionnaire de conformité](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Utilisation de votre tableau de bord du gestionnaire de conformité
    - Comprendre votre score de conformité
    - En savoir plus sur les actions d’amélioration
    - Présentation des évaluations et des modèles
- [Rampe : configurer le gestionnaire de conformité pour gérer vos activités de conformité](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Création et gestion de votre première évaluation
    - Exécution des tests d’implémentation et de test sur les actions d’amélioration pour terminer les contrôles dans vos évaluations
    - Comprendre l’impact de différentes actions sur votre score de conformité
- [Montée en puissance parallèle : utiliser les fonctionnalités avancées pour répondre à vos besoins personnalisés](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Création d’évaluations personnalisées pour suivre les produits non-Microsoft 365
    - Modification des modèles existants pour ajouter ou supprimer des contrôles
    - Configuration du test automatisé des actions d’amélioration

## <a name="how-your-compliance-score-is-calculated"></a>Comment votre score de conformité est calculé

Votre score de conformité est calculé en fonction d’une combinaison de Microsoft et des implémentations gérées par le client. Voir le [calcul du score de conformité](../compliance/compliance-score-calculation.md) pour une explication détaillée.

Les contrôles se voient attribuer une valeur de score selon qu’ils sont obligatoires ou discrétionnaires, et s’ils sont préventifs, détectives ou correcteurs. Ces éléments représentent le risque de ne pas les implémenter par rapport à d’autres contrôles.

Comme indiqué dans l’article de calcul du score de conformité, les contrôles de prévention obtiennent un meilleur score que le détective et les correcteurs, et les contrôles obligatoires obtiennent un meilleur score que les contrôles discrétionnaires.

L’interface utilisateur de l’administrateur de score de conformité ne répertorie pas ces paramètres, et ne permet pas de les filtrer. Toutefois, si vous téléchargez le modèle associé à partir du gestionnaire de conformité, le jeu de données résultant répertorie ces paramètres pour la plupart des réglementations.

Pour les contrôles techniques, le gestionnaire de conformité met automatiquement à jour le score de l’action d’amélioration une fois que l’action a été correctement implémentée et testée. D’autres actions non techniques, &mdash; telles que celles qui sont opérationnelles ou liées à la documentation, &mdash; doivent être enregistrées manuellement, telles que mises en œuvre avant que les points soient pris en compte dans votre score.

Vous pouvez également mettre en œuvre certaines actions d’amélioration à d’autres fins &mdash; , par exemple, à l’aide d’étiquettes de rétention pour des raisons autres que le respect du règlement sur la confidentialité des données &mdash; , afin que vous soyez crédité pour l’utilisation d’une telle fonctionnalité même si elle est utilisée à d’autres fins, et qu’elle ne fait pas partie d’une action de conformité intentionnelle.

Votre score de conformité doit être considéré comme une mesure relative permettant de suivre l’amélioration à grande échelle. Vous ne devez pas suivre un score parfait.

## <a name="additional-guidance"></a>Conseils supplémentaires

Voici quelques conseils importants pour utiliser le gestionnaire de conformité afin de vous aider à respecter la réglementation relative à la confidentialité des données :

- Chaque règlement sur la confidentialité des données comporte une combinaison de contrôles techniques, de spécifications de documentation et d’exigences opérationnelles, de processus et de création de rapports. Tous ces éléments s’affichent dans les actions d’amélioration.

- Pour attirer l’attention sur l’affichage des actions d’amélioration dans votre domaine, vous pouvez filtrer par type d’action dans l’onglet **solutions** de l’administrateur du gestionnaire de conformité. En savoir plus sur [le filtrage du tableau de bord gestionnaire de conformité](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- L’importance relative et la priorité des actions d’amélioration identifiées dans le gestionnaire de conformité doivent être considérées comme faisant partie d’une analyse des risques plus large, ainsi que le risque de confidentialité des données que vous avez déterminé que votre organisation a besoin de gérer.

- Même avec une agrégation des actions d’amélioration pour plusieurs exigences réglementaires, si les modèles d’évaluation de la réglementation pour RGPD, LGPD, CCPA et HIPAA-Hi sont sélectionnés, par exemple, presque 400 les actions d’amélioration seront répertoriées dans le gestionnaire de conformité. Pour mieux aborder cette longue liste, utilisez le filtre d’action d’amélioration pour réduire le jeu de résultats à une liste plus facile à gérer.

- Le filtre categories permet de filtrer les actions d’amélioration par le biais du regroupement logique, que les articles Track, pretent, Protect, retain et investigation de cette solution globale s’alignent sur.

- Certains des contrôles répertoriés dans les actions d’amélioration peuvent être considérés plus directement liés à un article réglementaire spécifique, tandis que d’autres contrôles peuvent être plus indirectement associés à l’esprit d’une réglementation et de nombreuses activités ou méthodes recommandées.