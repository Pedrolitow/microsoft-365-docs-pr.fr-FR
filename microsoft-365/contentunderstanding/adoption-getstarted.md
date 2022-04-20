---
title: Démarrage l’adoption de Microsoft SharePoint Syntex
description: Découvrez comment utiliser et implémenter des SharePoint Syntex dans votre organisation pour vous aider à rationaliser vos processus métier.
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 9b11c5077551aad666d565b0f3c077b3e43dc78e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937826"
---
# <a name="get-started-driving-adoption-of-microsoft-sharepoint-syntex"></a>Démarrage l’adoption de Microsoft SharePoint Syntex

Considérez les services de contenu intelligents disponibles dans SharePoint Syntex comme ayant trois parties :

- **Compréhension du contenu :** Créez des modèles iA sans code pour classifier et extraire des informations à partir du contenu afin d’appliquer automatiquement des métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur la [compréhension du contenu](document-understanding-overview.md).
- **Traitement du contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et rationalisez les processus centrés sur le contenu à l’aide de Power Automate. En savoir plus sur le [traitement du contenu](form-processing-overview.md).
- **Conformité du contenu :** Contrôlez et gérez le contenu pour améliorer la sécurité et la gouvernance avec l’intégration à Microsoft Purview Information Protection.

Avec les nouveaux services et fonctionnalités d’IA, vous pouvez créer des applications de compréhension et de classification de contenu directement dans le flux de gestion de contenu à l’aide de SharePoint Syntex. Il existe deux façons différentes de comprendre votre contenu. Le type de modèle que vous utilisez est basé sur le format de fichier et le cas d’utilisation.

| Traitement des formulaires | Compréhension de document |
|:-------|:-------|
| Créé à partir de la bibliothèque de documents. | Créé dans le centre de contenu, faisant partie de SharePoint Syntex. |
| Modèle créé dans le générateur d’IA. | Modèle créé dans l’interface native. |
| Utilisé pour les formats de fichiers semi-structurés. | Utilisé pour les formats de fichiers non structurés. |
| Classifieur settable. | Classifieur pouvant être entraîné avec des extracteurs facultatifs. |
| Limité à une bibliothèque unique. | Peut être appliqué à plusieurs bibliothèques. |
| Entraîner au format PDF, JPG, PNG, total 50 Mo/500 pp. | Entraînez-vous sur 5 à 10 fichiers PDF, Office ou courrier électronique, avec des exemples négatifs. |

Pour une comparaison plus complète des fonctionnalités, consultez [La différence entre la compréhension des documents et les modèles de traitement des formulaires](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilotes à optimiser

Pour préparer l’utilisation de SharePoint Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels il sera utile. Le « pourquoi » permet de déterminer le modèle qui sera nécessaire et comment structurer votre organisation en fonction de l’endroit où le modèle sera appliqué. Voici quelques scénarios dans lesquels la compréhension des documents peut aider votre organisation :

- **Traitement du contenu :** Traitez les contrats, les instructions de travail et d’autres documents de type formulaire. Prenez les formulaires, formez le modèle pour comprendre et mapper les champs, puis exécutez vos formulaires pour collecter automatiquement les données. Pour plus d’informations, consultez [la vue d’ensemble du traitement des formulaires](form-processing-overview.md).
- **Analyse des factures :** Extrayez les détails pertinents de vos factures et assurez-vous qu’elles sont conformes à la stratégie ou traitées correctement.

Réfléchissez aux façons dont SharePoint Syntex peut aider votre organisation :

- Automatiser les processus métier
- Améliorer la précision de la recherche
- Gérer les risques de conformité

Lorsque vous envisagez les scénarios métier à prendre en compte, posez-vous les questions suivantes :

- Est-ce qu’il résout un problème réel?
- Sera-t-il largement utilisé ou aura-t-il un large impact ?
- Est-il obtenu ?
- Pouvez-vous mesurer la réussite ?

Hiérarchiser les scénarios en fonction de l’impact et de la facilité d’implémentation. Augmentez les scénarios d’impact de votre zone de focus initiale qui peuvent également être implémentés facilement. Supprimez la hiérarchisation des scénarios à impact inférieur difficiles à implémenter.

Utilisez les [exemples de scénarios et les cas d’utilisation](adoption-scenarios.md) pour demander des idées sur la façon dont vous pouvez utiliser SharePoint Syntex dans votre organisation.

## <a name="identify-roles--responsibilities"></a>Identifier les rôles & responsabilités

Déterminez qui dans votre organisation créera et gérera les modèles. Les rôles suivants peuvent être impliqués.

| Administrateur/SharePoint d’informations | Administrateur Power Platform | Responsables d’informations | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| rôle AAD| rôle AAD | rôle AAD | Champions |
| Configurer le traitement des formulaires | Configurer l’environnement Dataverse pour le traitement des formulaires | Collecter les cas d’usage | Collecter les cas d’usage métier |
| Gérer les centres de contenu et les autorisations| Acheter et allouer des crédits AIB | Établir les meilleures pratiques et passer en revue l’analytique des modèles | Créer et appliquer des modèles |

Le gestionnaire de connaissances, le propriétaire du processus d’entreprise et le propriétaire du modèle de contenu créent des exemples de modèles et défendent l’adoption dans l’organisation.
Autres personnes susceptibles d’être impliquées : administrateur de conformité, gestionnaires de taxonomie.

Où vont-ils générer et appliquer les modèles ? Existe-t-il des processus ou des référentiels existants qui pourraient être améliorés ?

- Traitement des formulaires : déterminez les sites qui recevront l’action de traitement de formulaire.
- Compréhension des documents : vous pouvez créer plusieurs centres de contenu pour différents domaines d’activité.

## <a name="strategic-positioning"></a>Positionnement stratégique

Collaborez avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation de SharePoint Syntex. Recherchez et fournissez les ressources suivantes pour faciliter ce positionnement :

- Résultats métier :
  - Résultats budgétaires potentiels
  - Résultats potentiels en matière d’agilité
  - Modèle de résultat métier
- Parties prenantes/Sponsor Exec buy-in/alignment
  - Présentations de cas d’affaires
  - Modèles financiers
  - Préparation de l’entreprise - culture

## <a name="identify-stakeholders"></a>Identifier les parties prenantes

Identifiez les parties prenantes de votre projet.

|Role |Responsibilities |Service |
|:-------|:-------|:--------|
| Sponsor(s) exécutif(s)   | Communiquer la vision et les valeurs de haut niveau de l'entreprise.   |  Direction exécutive   |
| Project prospects | Superviser l'ensemble de l'exécution du lancement et du processus de déploiement. | Gestion de projet |
| Administrateurs des connaissances| Créer et gérer les centres de contenu | Informatique ou autre service|
| Gestionnaires de contenu et propriétaires de modèles| Collecter les cas d’usage et créer et appliquer des modèles | Tout département|
| Champions | Contribuer à l'évangélisation et à la gestion des objections | Tout département (personnel) |
| Administrateur de locataires | Configurer les paramètres au niveau du locataire | Département informatique|
| Administrateur de Power Platform| Configurer l’environnement Dataverse | Département informatique|

> [!NOTE]
> Bien que nous vous recommandons d’effectuer chacun de ces rôles tout au long de votre déploiement, vous constaterez peut-être que vous n’avez pas tous besoin de ces rôles pour commencer à utiliser votre solution identifiée.

## <a name="readiness-checklist"></a>Liste de vérification de la préparation

Pour vous préparer à l’implémentation de SharePoint Syntex, vous devez :

![Préparation à la compréhension du contenu.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planifier l’état final
    - Les modèles de compréhension des documents sont les moyens, et non la fin.
    - Planifiez l’exploitation de la valeur des métadonnées extraites avec :
      - Rechercher
      - Filtrage et affichage de la mise en forme
      - Conformité
      - Automation
2. Identifier
    - Comprendre l’architecture des informations et l’utilisation des fonctionnalités de gestion de contenu existantes.
    - Les types de contenu existants sont-ils de bons candidats pour les modèles ?
    - Quels processus existants seraient améliorés par les métadonnées ?
3. Conception
    - Concevez votre approche de l’architecture des informations, des métadonnées managées et des types de contenu.
    - Concevez le processus de définition, de création et de gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifiez les détenteurs d’enjeux, confirmez les scénarios et développez un plan de projet.
1. Configurez les paramètres et appliquez des licences.
1. Commencer la sensibilisation et la formation – Recruter des champions.
1. Déployer par étapes.  
1. Recueillir des commentaires et itérer.
1. À mesure que l’utilisation augmente, planifiez les crédits AI Builder en fonction des besoins.

## <a name="see-also"></a>Voir aussi

[Scénarios et cas d’usage pour SharePoint Syntex](adoption-scenarios.md)

[Gérer des contrats en utilisant la solution Microsoft 365](solution-manage-contracts-in-microsoft-365.md)
