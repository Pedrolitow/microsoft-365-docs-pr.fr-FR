---
title: Prise en main de l’adoption de Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.date: ''
audience: admin
ms.topic: article
ms.service: microsoft-syntex
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
description: Découvrez comment utiliser et implémenter Microsoft Syntex dans votre organisation pour simplifier vos processus métier.
ms.openlocfilehash: e824356fb5c729a6a508abebecffd4b6ea0c6e45
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660574"
---
# <a name="get-started-driving-adoption-of-microsoft-syntex"></a>Prise en main de l’adoption de Microsoft Syntex

Considérez les services de contenu intelligents disponibles dans Microsoft Syntex comme étant en trois parties :

- **Compréhension du contenu :** Créez des modèles IA sans code pour classifier et extraire des informations du contenu afin d’appliquer automatiquement des métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur [la compréhension du contenu](document-understanding-overview.md).
- **Traitement du contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et rationalisez les processus centrés sur le contenu à l’aide de Power Automate. En savoir plus sur le [traitement du contenu](form-processing-overview.md).
- **Conformité du contenu :** Contrôlez et gérez le contenu pour améliorer la sécurité et la gouvernance avec l’intégration à Protection des données Microsoft Purview.

Avec les nouveaux services et fonctionnalités d’IA, vous pouvez créer des applications de compréhension et de classification du contenu directement dans le flux de gestion de contenu à l’aide de Syntex. Pour les types de modèles personnalisés, il existe trois façons différentes de comprendre votre contenu. Le type de modèle personnalisé que vous utilisez est basé sur le format de fichier et le cas d’usage.

| Traitement de documents non structurés | Traitement de document structuré | Traitement de documents en forme libre |
| ------- | ------- | ------- |
| Créé dans le centre de contenu, qui fait partie de Syntex. | Créé à partir de la bibliothèque de documents. | Créé à partir de la bibliothèque de documents. |
| Modèle créé dans l’interface native. | Modèle créé dans AI Builder. | Modèle créé dans AI Builder. |
| Utilisé pour les formats de fichiers semi-structurés ou non structurés. | Utilisé pour les formats de fichiers structurés ou semi-structurés. | Utilisé pour les formats de fichier non structurés ou de forme libre. |
| Classifieur pouvant être formé avec des extracteurs facultatifs. | Classifieur paramétrable. | Classifieur paramétrable. |
| Peut être appliqué à plusieurs bibliothèques. | Limité à une seule bibliothèque. | Limité à une seule bibliothèque. |
| Entraînez-vous sur 5 à 10 fichiers PDF, Office ou courrier électronique, avec des exemples négatifs. | Entraîner au format PDF, JPG, PNG, au total 50 Mo/500 pp. | Entraîner au format PDF, JPG, PNG, au total 50 Mo/500 pp. |

Pour une comparaison plus complète des fonctionnalités personnalisées, consultez [Comparer des modèles personnalisés dans Syntex](difference-between-document-understanding-and-form-processing-model.md).

Si vous n’avez pas besoin de créer un modèle personnalisé, vous pouvez utiliser un [modèle prédéfini](prebuilt-overview.md) qui a déjà été formé pour des documents structurés spécifiques.

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilotes à optimiser

Pour préparer l’utilisation de Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels il sera utile. Le « pourquoi » permet de déterminer le modèle qui sera nécessaire et comment structurer votre organisation en fonction de l’endroit où le modèle sera appliqué. Voici quelques scénarios dans lesquels les modèles personnalisés peuvent aider votre organisation :

- **Traitement du contenu** : traitez les contrats, les énoncés de travail et d’autres documents de type formulaire. Réception des formulaires, entraînez le modèle pour comprendre et mapper les champs, puis exécutez vos formulaires pour collecter automatiquement les données.

- **Analyse des factures** : extrayez les détails pertinents de vos factures et assurez-vous qu’elles sont conformes à la stratégie ou traitées de manière appropriée.

Réfléchissez aux façons dont Syntex peut aider votre organisation :

- Automatiser les processus métier
- Améliorer la précision de la recherche
- Gérer les risques de conformité

Lorsque vous réfléchissez aux scénarios métier à prendre en compte, posez-vous les questions suivantes :

- Est-ce que cela résout un problème réel?
- Sera-t-il largement utilisé ou aura-t-il un large impact?
- Est-il accessible ?
- Pouvez-vous mesurer le succès ?

Hiérarchiser les scénarios en fonction de l’impact et de la facilité d’implémentation. Faites de votre domaine d’intérêt initial des scénarios d’impact plus élevés qui peuvent également être facilement implémentés. Dé-hiérarchiser les scénarios à impact inférieur qui sont difficiles à implémenter.

Utilisez les [exemples de scénarios et de cas d’usage](adoption-scenarios.md) pour obtenir des idées sur la façon dont vous pouvez utiliser Syntex dans votre organisation.

## <a name="identify-roles-and-responsibilities"></a>Découvrir les rôles et les responsabilités

Déterminez qui, dans votre organisation, créera et gérera les modèles. Les rôles suivants peuvent être impliqués.

| Administrateur/SharePoint d’informations | Administrateur Power Platform | Responsables d’informations | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| Rôle AAD| Rôle AAD | Rôle AAD | Champions  |
| Configurer le traitement de documents structurés et les modèles de traitement de documents en forme libre | Configurer l’environnement Dataverse | Collecter des cas d’usage | Collecter des cas d’usage métier |
| Gérer les centres de contenu et les autorisations| Acheter et allouer des crédits AIB | Établir les meilleures pratiques et passer en revue l’analyse des modèles | Créer et appliquer des modèles |

Le responsable des connaissances, le propriétaire des processus métier et le propriétaire du modèle de contenu créent des exemples de modèles et défendent l’adoption au sein de l’organisation. D’autres personnes susceptibles d’être impliquées par l’administrateur de conformité et les gestionnaires de taxonomie.

Où vont-ils créer et appliquer les modèles ? Existe-t-il des processus ou des dépôts existants qui pourraient être améliorés ?

- Traitement de documents non structurés : vous pouvez créer plusieurs centres de contenu pour différents domaines d’activité.
- Traitement de document structuré ou traitement de document de forme libre : déterminez les sites qui obtiendront cette action.

## <a name="strategic-positioning"></a>Positionnement stratégique

Collaborez avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation de Syntex. Recherchez et fournissez les ressources suivantes pour faciliter ce positionnement :

- Résultats métier :
  - Résultats financiers potentiels
  - Résultats potentiels de l’agilité
  - Modèle de résultat métier
- Parties prenantes/Exec sponsor buy-in/alignment
  - Présentations d’analyse de rentabilité
  - Modèles financiers
  - Préparation de l’entreprise - culture

## <a name="identify-stakeholders"></a>Identifier les parties prenantes

Identifiez les parties prenantes de votre projet.

|Role |Responsibilities |Service |
|:-------|:-------|:--------|
| Sponsor exécutif   | Communiquer la vision et les valeurs de haut niveau de l'entreprise.   |  Direction exécutive   |
| Chef de projet | Superviser l'ensemble de l'exécution du lancement et du processus de déploiement. | Gestion de projet |
| Administrateurs des connaissances| Créer et gérer les centres de contenu | Service informatique ou autre service|
| Gestionnaires de contenu et propriétaires de modèles| Collecter des cas d’usage et créer et appliquer des modèles | Tout département|
| Champions | Contribuer à l'évangélisation et à la gestion des objections | Tout département (personnel) |
| Administrateur de locataires | Configurer les paramètres au niveau du locataire | Département informatique|
| Administrateur de Power Platform| Configurer l’environnement Dataverse | Département informatique|

> [!NOTE]
> Bien que nous vous recommandons de remplir chacun de ces rôles tout au long de votre déploiement, vous pouvez constater que vous n’en avez pas tous besoin pour commencer à utiliser votre solution identifiée.

## <a name="readiness-checklist"></a>Liste de contrôle de préparation

Pour vous préparer à implémenter Syntex, vous devez :

![Préparation à la compréhension du contenu.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planifier l’état final
    - Les modèles sont les moyens, pas la fin.
    - Planifiez l’exploitation de la valeur des métadonnées extraites avec :
      - Rechercher
      - Filtrage et mise en forme de l’affichage
      - Conformité
      - Automation
2. Identifier
    - Comprendre l’architecture des informations existante et l’utilisation des fonctionnalités de gestion de contenu.
    - Les types de contenu existants sont-ils de bons candidats pour les modèles ?
    - Quels processus existants seraient améliorés par les métadonnées ?
3. Conception
    - Concevez votre approche de l’architecture des informations, des métadonnées managées et des types de contenu.
    - Concevez le processus pour la définition, la création et la gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifiez les parties prenantes, confirmez les scénarios et développez un plan de projet.
2. Configurez les paramètres et appliquez des licences.
3. Commencez la sensibilisation et la formation : recruter des champions.
4. Déploiement par étapes.  
5. Recueillir des commentaires et itérer.
6. À mesure que l’utilisation augmente, planifiez les crédits AI Builder en fonction des besoins.

## <a name="see-also"></a>Voir aussi

[Centre d’adoption Microsoft Syntex](https://adoption.microsoft.com/sharepoint-syntex/adoption/)

[Scénarios et cas d’usage pour Microsoft Syntex](adoption-scenarios.md)

[Vue d’ensemble des types de modèles dans Microsoft Syntex](syntex-overview.md)
