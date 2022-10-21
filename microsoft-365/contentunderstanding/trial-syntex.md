---
title: Exécuter une version d’évaluation de Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.service: microsoft-syntex
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- Adopt
- admindeeplinkMAC
search.appverid: ''
ms.localizationpriority: medium
description: Découvrez comment planifier, inscrire et exécuter un programme pilote d’essai pour Microsoft Syntex dans votre organisation.
ms.openlocfilehash: 028c91912d04f99c030d9de887c0c344961add3d
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662684"
---
# <a name="run-a-trial-of-microsoft-syntex"></a>Exécuter une version d’évaluation de Microsoft Syntex

Cet article explique comment configurer et exécuter un programme pilote d’évaluation pour déployer Microsoft Syntex dans votre organisation. Il recommande également les meilleures pratiques pour la version d’évaluation.

## <a name="sign-up-for-a-trial"></a>S’inscrire à une version d’évaluation

La version d’évaluation de Syntex donne accès à 300 utilisateurs pendant 30 jours.

> [!NOTE]
> Jusqu’à 300 utilisateurs sont inclus dans la version d’évaluation pour garantir l’ajout automatique de 1 million de crédits AI Builder. Vous n’avez pas besoin d’inclure 300 utilisateurs pour qu’une version d’évaluation réussisse.

Vous pouvez obtenir la version d’évaluation à partir de l’une des sources suivantes :

- Page du [produit Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- Le [Centre d'administration Microsoft 365](https://admin.microsoft.com)
    1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com).
    2. Accédez à **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**Acheter des services**</a>.
    3. Faites défiler la page vers le bas jusqu’à la section **Modules complémentaires**.
    4. Dans la vignette Syntex, sélectionnez **Détails**.
    5. Sélectionnez **Démarrer l’essai gratuit**.
    6. Pour confirmer la version d’évaluation, suivez les étapes restantes de l’Assistant.

Vous devez être administrateur général ou administrateur de facturation Microsoft 365 pour activer une version d’évaluation.

### <a name="who-should-be-involved-in-a-trial"></a>Qui devrait être impliqué dans un procès

|Rôle|Activité|
|---|---|
|Administrateur général ou administrateur de facturation Microsoft 365|Activer la version d’évaluation et attribuer des licences|
|Microsoft 365 administrateur global ouadministrateur SharePoint administrateur|Configurer Syntex et créer des centres de contenu|
|Utilisateurs professionnels|Génération et test de modèles|

### <a name="before-you-activate-a-trial"></a>Avant d’activer une version d’évaluation

Pour planifier correctement un essai Syntex, tenez compte des facteurs suivants :

- Le test le plus significatif est effectué sur des scénarios et des données « réels ».
- Vous ne pouvez activer un essai Syntex qu’une seule fois par locataire.

Un locataire de test ou de démonstration peut être utilisé comme un « dry run » pour parcourir les étapes d’activation et les contrôles d’administration. Mais il est probablement préférable d’évaluer la création de modèle sur un locataire de production.

Pour optimiser la valeur d’un essai sur un locataire de production, la planification et l’engagement commercial sont essentiels. Vous devez faire appel à un ou plusieurs secteurs d’activité pour identifier trois à six cas d’usage susceptibles d’être traités par Syntex. Ces cas d’usage doivent :

- Incluez des scénarios qui peuvent être résolus à l’aide d’un modèle personnalisé ou d’un modèle prédéfini.

- Avoir une compréhension claire de l’objectif de toutes les métadonnées extraites; par exemple, afficher la mise en forme ou l’automatisation à l’aide de Power Automate. Alors que Syntex se concentre sur la classification des documents et l’extraction des métadonnées, la valeur à quantifier est ce que ces métadonnées permettent.

- Être basé sur un jeu de données défini ; par exemple, des sites ou des bibliothèques SharePoint spécifiques. Une idée fausse courante de Syntex est que les modèles à usage général peuvent être appliqués à l’ensemble du contenu de l’organisation. Une vue plus précise est que les modèles sont conçus pour aider à résoudre des problèmes métier spécifiques dans des emplacements ciblés.

Tous ces cas d’usage peuvent ne pas convenir à Syntex. L’objectif d’un essai de qualité n’est pas de prouver que Syntex sera adapté à tous les scénarios. Au lieu de cela, la version d’évaluation doit vous aider à mieux comprendre la valeur du produit.

Pour chacun des cas d’usage planifiés, identifiez les utilisateurs qui sont des experts en la matière dans le contenu ou le processus connexe. La création de modèles Syntex est axée sur des experts du domaine dans le contenu, plutôt que sur des professionnels de l’informatique ou des ressources de développement.

## <a name="activate-a-trial"></a>Activer une version d’évaluation

Lorsque vous lancez une version d’évaluation, vous devez :

- Attribuez des licences aux utilisateurs concernés.
- Effectuez [une configuration supplémentaire de Syntex](set-up-content-understanding.md).
  - Vous souhaiterez peut-être [créer d’autres centres de contenu](create-a-content-center.md).

Une fois la version d’évaluation activée, vous pouvez créer des modèles et traiter des fichiers. Consultez [les conseils pour la création de modèle](create-a-content-center.md).

## <a name="during-a-trial"></a>Pendant une version d’évaluation

Les périodes d’essai étant limitées, il est préférable de se concentrer initialement sur la possibilité pour les modèles Syntex de classifier les documents et d’extraire des métadonnées pour les cas d’usage définis. Une fois la période d’essai terminée, vous pouvez évaluer la façon dont les métadonnées peuvent être utilisées.

## <a name="after-a-trial"></a>Après un essai

En fonction du résultat de l’essai, vous pouvez décider s’il faut passer à la production de Syntex.

### <a name="proceed-to-production-use"></a>Passer à l’utilisation en production

Pour garantir la continuité du service, vous devez acheter le nombre requis de [licences](syntex-licensing.md) et attribuer ces licences aux utilisateurs. Les utilisateurs d’essai qui ne disposent pas d’une licence complète à la fin de la période d’évaluation ne pourront pas utiliser entièrement Syntex.

Vous devrez peut-être estimer l’utilisation prévue des modèles de traitement de documents structurés ou de forme libre, et planifier le nombre attendu de crédits AI Builder. Pour obtenir [de l’aide, consultez Estimer la capacité AI Builder qui vous convient](https://powerapps.microsoft.com/ai-builder-calculator/).

### <a name="dont-proceed-to-production-use"></a>Ne pas passer à l’utilisation en production

Si vous n’achetez pas de licences après la version d’évaluation :

- Vous ne pourrez pas créer de modèles.

- Les bibliothèques qui exécutaient des modèles ne classifient plus automatiquement les fichiers ou n’extraient plus les modèles.

- Les fichiers précédemment classifiés ou les métadonnées extraites ne seront pas affectés.

- Les centres de contenu et les modèles qu’ils contiennent ne seront pas automatiquement supprimés. Ceux-ci restent disponibles si vous décidez d’acheter des licences à l’avenir.

- Les modèles de traitement de documents structurés ou de forme libre seront stockés dans l’instance Dataverse (anciennement appelée Common Data Service (CDS)) de l’environnement Power Platform par défaut. Ceux-ci peuvent être utilisés avec les futures licences pour Syntex ou avec les fonctionnalités d’AI Builder dans Power Platform.

## <a name="see-also"></a>Voir aussi

[Prise en main de l’adoption de Microsoft Syntex](adoption-getstarted.md)

[Scénarios et cas d’usage pour Microsoft Syntex](adoption-scenarios.md)