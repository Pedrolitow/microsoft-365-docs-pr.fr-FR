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
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Découvrez comment utiliser le Score de conformité et le Gestionnaire de conformité pour améliorer votre niveau de protection des données personnelles.
ms.openlocfilehash: 87131ea65661e8285fd7c3b36a87c79b618348d7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918569"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>Utiliser le Gestionnaire de conformité pour gérer les actions d’amélioration

Le Gestionnaire de conformité Microsoft peut vous aider à gérer les améliorations liées aux réglementations en matière de confidentialité des données, telles que le Règlement général sur la protection des données [(RGPD)](/compliance/regulatory/gdpr)de l’Union européenne, le [CCPA (California Consumer Protection Act),](/compliance/regulatory/ccpa-faq)hipAA-HITECH (loi américaine sur la confidentialité des soins de santé) et le LGPD (Brazil Data Protection Act).

Cet article fournit des conseils sur l’utilisation de cet outil à des fins de confidentialité des données.

>[!Note]
>Les recommandations du Gestionnaire de conformité ne doivent pas être interprétées comme des garanties de conformité. C’est à vous d’évaluer et de valider l’efficacité des contrôles client par rapport à votre environnement réglementaire. Ces services sont soumis aux conditions générales des [conditions générales des services en ligne.](https://go.microsoft.com/fwlink/?linkid=2108910) Voir aussi les [conseils Microsoft 365 licences pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)
>

## <a name="getting-started-with-compliance-manager"></a>Mise en place avec le Gestionnaire de conformité

#### <a name="what-is-compliance-manager"></a>Qu’est-ce que le Gestionnaire de conformité ?

[Le Gestionnaire de](../compliance/compliance-manager.md) conformité est un outil d’évaluation des risques basé sur un flux de travail dans le centre Microsoft 365 conformité pour la gestion des activités de conformité réglementaire liées aux services cloud de Microsoft. Dans le cadre de votre abonnement Microsoft 365 ou Azure Active Directory (Azure AD), le Gestionnaire de conformité vous aide à gérer la conformité réglementaire dans le modèle de responsabilité partagée pour les services cloud de Microsoft.

**Prêt à utiliser les évaluations**

Le Gestionnaire de conformité fournit [](../compliance/compliance-manager-assessments.md) des modèles pré-créés pour la création d’évaluations qui sont alignées sur les réglementations liées à la confidentialité des données, telles que le R GDPR et HIPAA/HITECH. Les modèles ont un mappage de contrôle intégré pour vous aider à prendre des mesures d’amélioration pour répondre aux exigences du règlement. Chaque évaluation fournit des informations sur les contrôles que chaque réglementation appelle pour un service cible spécifique, décomposé par les contrôles que vous gérez et contrôle que Microsoft gère. 

L’utilisation d’un modèle pré-créé vous permet de commencer rapidement à évaluer les risques. À mesure que vous maîtrisez l’utilisation du Gestionnaire de conformité, vous pouvez personnaliser un modèle prédépendant en ajoutant vos propres contrôles et actions d’amélioration, ou vous pouvez créer vos propres évaluations personnalisées en fonction des besoins de votre organisation.

Affichez [la liste complète des modèles d’évaluation](../compliance/compliance-manager-templates-list.md) fournis par le Gestionnaire de conformité.

**Score de conformité en temps réel**

Le Gestionnaire de conformité vous fournit également un score de conformité qui mesure votre progression dans l’exécution des actions d’amélioration recommandées au sein des contrôles. Vous pouvez utiliser ce score pour surveiller votre progression et hiérarchiser les actions en fonction de leur capacité à réduire les risques.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>Utiliser le guide de démarrage rapide du Gestionnaire de conformité

Le guide [de démarrage rapide du Gestionnaire de conformité](../compliance/compliance-manager-quickstart.md) fournit des étapes et des liens vers des ressources clés pour vous aider à travailler avec le Gestionnaire de conformité :

- [Première visite : familiarisez-vous avec le Gestionnaire de conformité](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - Travailler avec votre tableau de bord du Gestionnaire de conformité
    - Comprendre votre score de conformité
    - En savoir plus sur les actions d’amélioration
    - Présentation des évaluations et des modèles
- [Montée en puissance : configurer le Gestionnaire de conformité pour gérer vos activités de conformité](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - Création et gestion de votre première évaluation
    - Exécution d’un travail d’implémentation et de test sur des actions d’amélioration pour effectuer des contrôles dans vos évaluations
    - Comprendre l’impact des différentes actions sur votre score de conformité
- [Montée en niveau : utiliser des fonctionnalités avancées pour répondre à vos besoins personnalisés](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - Création de vos évaluations personnalisées pour suivre les produits Microsoft 365 non personnalisés
    - Modification de modèles existants pour ajouter ou supprimer des contrôles
    - Configuration du test automatisé des actions d’amélioration

## <a name="how-your-compliance-score-is-calculated"></a>Comment votre score de conformité est calculé

Votre score de conformité est calculé en fonction d’une combinaison d’implémentations de contrôle géré par le client et Microsoft. Voir [le calcul du score de conformité](../compliance/compliance-score-calculation.md) pour obtenir une explication détaillée.

Une valeur de score est attribuée aux contrôles selon qu’ils sont obligatoires ou discrétionnaires, et qu’ils soient préventives, marqueurs ou correctifs. Ceux-ci représentent collectivement le risque de ne pas l’implémenter par rapport à d’autres contrôles.

Comme le décrit l’article de calcul du score de conformité, les contrôles préventives obtiennent un score plus élevé que les contrôles de observation et de correction, et les contrôles obligatoires obtiennent un score plus élevé que les contrôles discrétionnaires.

L’interface utilisateur d’administration du Score de conformité ne liste pas ces paramètres et ne permet pas non plus de filtrer par eux. Toutefois, si vous téléchargez le modèle associé à partir du Gestionnaire de conformité, le jeu de données résultant indique ces paramètres pour la plupart des réglementations.

Pour les contrôles techniques, le Gestionnaire de conformité met automatiquement à jour le score d’action d’amélioration une fois que l’action a été correctement implémentée et testée. D’autres actions de contrôle non techniques, telles que celles qui sont opérationnelles ou liées à la documentation, doivent être enregistrées manuellement comme implémentées avant que les points comptent pour &mdash; &mdash; votre score.

Vous êtes nombreux à implémenter certaines actions d’amélioration à d’autres fins, par exemple en utilisant des étiquettes de rétention pour des raisons autres que la conformité à la réglementation sur la confidentialité des données, afin d’obtenir des crédits pour l’utilisation d’une telle fonctionnalité même si elle est utilisée à d’autres fins, et non dans le cadre d’une action délibérée de &mdash; &mdash; conformité.

Votre score de conformité doit être considéré comme une mesure relative pour suivre l’amélioration à grande échelle. Vous ne devez pas poursuivre un score parfait.

## <a name="additional-guidance"></a>Conseils supplémentaires

Voici quelques conseils importants concernant l’utilisation du Gestionnaire de conformité pour vous aider à respecter la réglementation en matière de confidentialité des données :

- Chaque règlement sur la confidentialité des données combine des contrôles techniques, des spécifications de documentation et des exigences opérationnelles, de processus et de création de rapports. Tous ces éléments s’affiche dans les actions d’amélioration.

- Pour concentrer l’affichage des actions d’amélioration sur votre domaine d’intérêt, vous pouvez filtrer par type d’action dans l’onglet **Solutions** de l’administrateur du Gestionnaire de conformité. En savoir plus sur [le filtrage de votre affichage du tableau de bord du Gestionnaire de conformité.](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view)

- L’importance relative et la priorité des actions d’amélioration identifiées dans le Gestionnaire de conformité doivent être prises en compte dans le cadre d’un examen plus large des risques, ainsi que du risque de confidentialité des données que vous avez déterminé que votre organisation doit gérer.

- Même avec l’agrégation d’actions d’amélioration parmi plusieurs exigences réglementaires, si les modèles d’évaluation de la réglementation pour le RGPD, le LGPD, le CCPA et HIPAA-HITECH sont sélectionnés, par exemple, près de 400 actions d’amélioration seront répertoriées dans le Gestionnaire de conformité. Pour mieux aborder cette longue liste, utilisez le filtre d’action d’amélioration pour réduire le jeu de résultats à une liste plus facile à gérer.

- Le filtre Catégories permet de filtrer les actions d’amélioration par regroupement logique, auquel s’alignent les articles Suivi, Prévention, Protection, Conserver et Examiner de cette solution globale.

- Certains des contrôles répertoriés dans les actions d’amélioration peuvent être considérés plus directement liés à un article réglementaire spécifique, tandis que d’autres contrôles peuvent être associés plus indirectement à l’étude d’une réglementation et de nombreuses fois sont simplement des activités recommandées ou des meilleures pratiques.