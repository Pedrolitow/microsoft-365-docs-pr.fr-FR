---
title: Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
description: Découvrez comment utiliser le score de conformité et le Gestionnaire de conformité pour améliorer votre niveau de protection des données personnelles.
ms.openlocfilehash: 469584abbf784fe6c556aab14a49a5ed44280a69
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947448"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration

Microsoft Purview Compliance Manager peut vous aider à gérer les améliorations liées aux réglementations sur la confidentialité des données telles que le [Règlement général sur la protection des données (RGPD)](/compliance/regulatory/gdpr) de l’Union européenne, le [CCPA (California Consumer Protection Act),](/compliance/regulatory/ccpa-faq) HIPAA-HITECH (Loi américaine sur la confidentialité des soins de santé) et la Loi brésilienne sur la protection des données (LGPD).

Cet article fournit des conseils sur l’utilisation de cet outil à des fins de confidentialité des données.

> [!NOTE]
> Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité. C’est à vous d’évaluer et de valider l’efficacité des contrôles clients en fonction de votre environnement réglementaire. Ces services sont soumis aux conditions générales des conditions générales des [services en ligne](https://go.microsoft.com/fwlink/?linkid=2108910). Voir aussi [Microsoft 365 conseils de gestion des licences pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>Prise en main du Gestionnaire de conformité

#### <a name="what-is-compliance-manager"></a>Qu’est-ce que le Gestionnaire de conformité ?

[Le Gestionnaire de conformité](../compliance/compliance-manager.md) est un outil d’évaluation des risques basé sur le flux de travail dans le portail de conformité Microsoft Purview pour la gestion des activités de conformité réglementaire liées aux services cloud Microsoft. Dans le cadre de votre abonnement Microsoft 365 ou Azure Active Directory (Azure AD), le Gestionnaire de conformité vous aide à gérer la conformité réglementaire dans le modèle de responsabilité partagée pour les services cloud Microsoft.

**Prêt à utiliser des évaluations**

Le Gestionnaire de conformité fournit des modèles prédéfinies pour [la génération d’évaluations](../compliance/compliance-manager-assessments.md) alignées sur les réglementations relatives à la confidentialité des données, telles que le RGPD et HIPAA/HITECH. Les modèles ont un mappage de contrôle intégré pour vous aider à prendre des mesures d’amélioration pour répondre aux exigences du règlement. Chaque évaluation fournit des informations sur les contrôles que chaque réglementation appelle spécifiques au service cible, divisés par les contrôles que vous gérez et les contrôles gérés par Microsoft.

L’utilisation d’un modèle prédéfagé vous permet de commencer rapidement à évaluer les risques. À mesure que vous maîtrisez mieux l’utilisation du Gestionnaire de conformité, vous pouvez personnaliser un modèle prédéfféri en ajoutant vos propres contrôles et actions d’amélioration, ou vous pouvez créer vos propres évaluations personnalisées en fonction des besoins de votre organisation.

Affichez la [liste complète des modèles d’évaluation](../compliance/compliance-manager-templates-list.md) fournis par le Gestionnaire de conformité.

**Score de conformité en temps réel**

Le Gestionnaire de conformité vous fournit également un score de conformité qui mesure votre progression dans l’exécution des actions d’amélioration recommandées dans les contrôles. Vous pouvez utiliser ce score pour surveiller votre progression et hiérarchiser les actions en fonction de leur potentiel de réduction des risques.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Utiliser le guide de démarrage rapide du Gestionnaire de conformité

Le guide de [démarrage rapide du Gestionnaire de conformité](../compliance/compliance-manager-quickstart.md) fournit des étapes graduées et des liens vers des ressources clés pour vous aider à travailler avec le Gestionnaire de conformité :

- [Première visite : familiarisez-vous avec le Gestionnaire de conformité](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Utilisation de votre tableau de bord gestionnaire de conformité
    - Comprendre votre score de conformité
    - Learning sur les actions d’amélioration
    - Présentation des évaluations et des modèles
- [Montée en puissance : configurer le Gestionnaire de conformité pour gérer vos activités de conformité](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Création et gestion de votre première évaluation
    - Exécution de travaux d’implémentation et de test sur des actions d’amélioration pour effectuer des contrôles dans vos évaluations
    - Comprendre l’impact des différentes actions sur votre score de conformité
- [Montée en puissance : utiliser des fonctionnalités avancées pour répondre à vos besoins personnalisés](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Création de vos évaluations personnalisées pour suivre les produits non Microsoft 365
    - Modification de modèles existants pour ajouter ou supprimer des contrôles
    - Configuration des tests automatisés des actions d’amélioration

## <a name="how-your-compliance-score-is-calculated"></a>Comment votre score de conformité est calculé

Votre score de conformité est calculé en fonction d’une combinaison d’implémentations de contrôle géré par Microsoft et par le client. Consultez [le calcul du score de conformité](../compliance/compliance-score-calculation.md) pour obtenir une explication détaillée.

Les contrôles se voient attribuer une valeur de score selon qu’ils sont obligatoires ou discrétionnaires, et s’ils sont préventifs, détectives ou correctifs. Ils représentent collectivement le risque de ne pas l’implémenter par rapport à d’autres contrôles.

Comme indiqué dans l’article de calcul du score de conformité, les contrôles préventifs obtiennent un score plus élevé que les contrôles de détection et de correction, et les contrôles obligatoires obtiennent un score plus élevé que les contrôles discrétionnaires.

L’interface utilisateur de l’administrateur du score de conformité ne répertorie pas ces paramètres et ne fournit pas la possibilité de les filtrer. Toutefois, si vous téléchargez le modèle associé à partir du Gestionnaire de conformité, le jeu de données résultant répertorie ces paramètres pour la plupart des réglementations.

Pour les contrôles techniques, le Gestionnaire de conformité met automatiquement à jour le score d’action d’amélioration une fois l’action correctement implémentée et testée. D’autres actions&mdash; de contrôle non techniques sont aussi nombreuses que celles qui sont opérationnelles ou liées à la documentation&mdash; à enregistrer manuellement comme implémentée avant que les points ne soient comptabilisés dans votre score.

Vous êtes nombreux également à implémenter certaines actions d’amélioration à d’autres fins&mdash;, par exemple en utilisant des étiquettes de rétention pour des raisons autres que la conformité&mdash; à la réglementation sur la confidentialité des données. Vous pourriez obtenir un crédit pour l’utilisation d’une telle fonctionnalité, même si elle est utilisée à d’autres fins, et non dans le cadre d’une action de conformité délibérée.

Votre score de conformité doit être considéré comme une mesure relative pour suivre l’amélioration à grande échelle. Vous ne devriez pas poursuivre un score parfait.

## <a name="additional-guidance"></a>Conseils supplémentaires

Voici quelques conseils importants pour utiliser le Gestionnaire de conformité pour vous aider à respecter la réglementation sur la confidentialité des données :

- Chaque réglementation sur la confidentialité des données comprend une combinaison de contrôles techniques, de spécifications de documentation et d’exigences opérationnelles, de processus et de création de rapports. Tous ces éléments apparaissent dans les actions d’amélioration.

- Pour concentrer l’affichage des actions d’amélioration sur votre domaine d’intérêt, vous pouvez filtrer par type d’action dans l’onglet **Solutions** de l’administrateur du Gestionnaire de conformité. En savoir plus sur [le filtrage de l’affichage du tableau de bord du Gestionnaire de conformité](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- L’importance relative et la priorité des actions d’amélioration identifiées dans le Gestionnaire de conformité doivent être prises en compte dans le cadre d’un examen plus large des risques, ainsi que du risque de confidentialité des données que vous avez déterminé que votre organisation doit gérer.

- Même avec l’agrégation des actions d’amélioration entre plusieurs exigences réglementaires, si les modèles d’évaluation de réglementation pour le RGPD, le CCPA et HIPAA-HITECH sont sélectionnés, par exemple, près de 400 actions d’amélioration seront répertoriées dans le Gestionnaire de conformité. Pour mieux aborder cette longue liste, utilisez le filtre d’action d’amélioration pour réduire le jeu de résultats à une liste plus gérable.

- Le filtre Catégories permet de filtrer les actions d’amélioration en regroupant logiquement les articles Track, Prevent, Protect, Retain et Investigate de cette solution globale.

- Certains des contrôles répertoriés dans les mesures d’amélioration peuvent être considérés comme plus directement liés à un article réglementaire spécifique, tandis que d’autres contrôles peuvent être plus indirectement associés à l’esprit d’une réglementation et, bien souvent, sont simplement des activités recommandées ou des meilleures pratiques.