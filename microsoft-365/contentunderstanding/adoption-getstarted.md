---
title: 'Adoption SharePoint Syntex Microsoft : commencer'
description: Découvrez comment utiliser et implémenter des SharePoint Syntex votre organisation pour vous aider à résoudre vos problèmes d’entreprise.
ms.author: samanro
author: samanro
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
localization_priority: Normal
ms.openlocfilehash: 0390163d1128bcb83fad0ad91c94c1a02d738a4e
ms.sourcegitcommit: 8db88004f4c015138b20c55095ada2c0c79e5910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2021
ms.locfileid: "58928715"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Adoption SharePoint Syntex Microsoft : commencer

Pensez aux services de contenu intelligents disponibles dans SharePoint Syntex comme ayant trois parties :

- **Compréhension du contenu :** Créez des modèles d’IA sans code pour classifier et extraire des informations du contenu afin d’appliquer automatiquement les métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur [la compréhension du contenu.](document-understanding-overview.md)
- **Traitement de contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et simplifiez les processus centrées sur le contenu à l’aide Power Automate. En savoir plus sur [le traitement du contenu.](form-processing-overview.md)
- **Conformité du contenu :** Contrôler et gérer le contenu pour améliorer la sécurité et la gouvernance avec l’intégration Protection des données Microsoft.

Grâce aux nouvelles fonctionnalités et services d’IA, vous pouvez créer des applications de compréhension et de classification du contenu directement dans le flux de gestion de contenu à l’aide SharePoint Syntex. Il existe deux façons de comprendre votre contenu. Le type de modèle que vous utilisez est basé sur le format de fichier et le cas d’utilisation :

| Traitement des formulaires | Compréhension de document |
|:-------|:-------|
| Créé à partir d’une bibliothèque de documents. | Créé dans le centre de contenu, faisant partie SharePoint Syntex. |
| Modèle créé dans le Générateur d’IA. | Modèle créé dans l’interface native. |
| Utilisé pour les formats de fichiers semi-structurés. | Utilisé pour les formats de fichiers non structurés. |
| Classifieur settable. | Classifieur entraisable avec des extracteurs facultatifs. |
| Limité à une seule bibliothèque. | Peut être appliqué à plusieurs bibliothèques. |
| Formation au format PDF, JPG, PNG, total 50 Mo/500 pp. | Entraînez-vous sur 5 à 10 fichiers PDF, Office ou courrier électronique, avec des exemples négatifs. |

Pour une comparaison plus complète des fonctionnalités, voir Différence entre la compréhension des documents et [les modèles de traitement des formulaires.](difference-between-document-understanding-and-form-processing-model.md)

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilote pour optimiser

Pour vous préparer à l’utilisation SharePoint Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels il sera utile. Le « pourquoi » permet de déterminer le modèle qui sera nécessaire et comment structurer votre organisation en fonction de l’endroit où le modèle sera appliqué. Voici quelques scénarios dans lequel la compréhension des documents peut aider votre organisation :

- **Traitement de contenu :** Traiter des contrats, des instructions de travail et d’autres documents de type formulaire. Admission des formulaires, formation du modèle à comprendre et maque les champs, puis exécutez vos formulaires pour collecter automatiquement les données. Pour plus d’informations, voir [Vue d’ensemble du traitement des formulaires.](form-processing-overview.md)
- **Analyse des factures :** Retirez les détails pertinents de vos factures et assurez-vous qu’elles sont conformes à la stratégie ou qu’elles sont traitées correctement.

Réfléchissez aux façons dont SharePoint Syntex peut aider votre organisation :

- Automatiser les processus métier
- Améliorer la précision de la recherche
- Gérer les risques de conformité

Lorsque vous réfléchissez aux scénarios d’entreprise à prendre en compte, posez-vous les questions suivantes :

- Permet-elle de résoudre un problème réel ?
- Sera-t-elle largement utilisée ou aura-t-elle un large impact ?
- Est-il possible de l’obtenir ?
- Pouvez-vous mesurer la réussite ?

Hiérarchiser les scénarios en fonction de l’impact et de la facilité d’implémentation. Faites en sorte que vos scénarios d’impact initial sur le domaine de travail soient plus faciles à implémenter. Ne pas hiérarchiser les scénarios à faible impact qui sont difficiles à implémenter.

Utilisez les [exemples de scénarios](adoption-scenarios.md) et les cas d’utilisation pour vous faire des idées sur la façon dont vous pouvez SharePoint Syntex dans votre organisation.

## <a name="identify-roles--responsibilities"></a>Identifier les rôles & responsabilités

Déterminer qui dans votre organisation créera et gérera les modèles ? Les rôles suivants peuvent être impliqués :

| Administrateur/SharePoint d’informations | Administrateur Power Platform | Responsables d’informations | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| Rôle AAD| Rôle AAD | Rôle AAD | Champions  |
| Configurer le traitement des formulaires | Configurer l’environnement dataverse pour le traitement des formulaires | Recueillir des cas d’utilisation | Recueillir des cas d’utilisation professionnelle |
| Gérer les centres de contenu et les autorisations| Acheter et allouer des crédits AIB | Établir les meilleures pratiques et examiner l’analyse du modèle | Créer et appliquer des modèles |

Le gestionnaire de connaissances, le propriétaire des processus d’entreprise et le propriétaire du modèle de contenu créent des exemples de modèles et l’adoption de champion dans l’organisation.
Autres personnes impliquées : administrateur de conformité, responsables de taxonomie.

Où créeront-ils et appliqueront-ils les modèles ? Existe-t-il des processus ou des référentiels existants qui pourraient être améliorés ?

- Traitement de formulaire : déterminez les sites qui obtiennent l’action de traitement du formulaire.
- Compréhension des documents : vous pouvez créer plusieurs centres de contenu pour différents domaines d’activité.

## <a name="strategic-positioning"></a>Positionnement stratégique

Travaillez avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation des SharePoint Syntex. Recherchez et fournissez les ressources suivantes pour vous aider à ce positionnement :

- Résultats de l’entreprise :
  - Résultats fiscaux potentiels
  - Possibilités d’agilité
  - Modèle de résultat commercial
- Parties prenantes/Sponsor Exec : buy-in/alignment
  - Jeux de cas d’entreprise
  - Modèles financiers
  - Préparation de l’entreprise - culture

## <a name="identify-stakeholders"></a>Identifier les parties prenantes

Identifiez les parties prenantes de votre projet.

|Role |Responsibilities |Service |
|:-------|:-------|:--------|
| Sponsor(s) exécutif(s)   | Communiquer la vision et les valeurs de haut niveau de l'entreprise.   |  Direction exécutive   |
| Project(s) | Superviser l'ensemble de l'exécution du lancement et du processus de déploiement. | Gestion de projet |
| Administrateurs des connaissances| Créer et gérer les centres de contenu | Service informatique ou autre service|
| Gestionnaires de contenu et propriétaires de modèles| Collecter des cas d’utilisation, créer et appliquer des modèles | Tout département|
| Champions | Contribuer à l'évangélisation et à la gestion des objections | Tout département (personnel) |
| Administrateur de locataires | Configurer les paramètres au niveau du locataire | Département informatique|
| Administrateur de Power Platform| Configurer l’environnement dataverse | Département informatique|

> [!NOTE]
> Même si nous vous recommandons de remplir chacun de ces rôles tout au long de votre déploiement, il se peut que vous n’en exigeiez pas tous la mise en place de votre solution identifiée.

## <a name="readiness-checklist"></a>Liste de vérification de préparation

Pour vous préparer à l’SharePoint Syntex, vous devez :

![Préparation pour la compréhension du contenu.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planifier l’état final
    - Les modèles de compréhension de document sont les moyens, et non la fin.
    - Planifiez l’exploitation de la valeur des métadonnées extraites avec :
      - Rechercher
      - Filtrage et mise en forme de l’affichage
      - Conformité
      - Automation
2. Identifier
    - Comprendre l’utilisation existante de l’architecture des informations et de la fonctionnalité de gestion de contenu.
    - Les types de contenu existants sont-ils de bons candidats pour les modèles ?
    - Quels processus existants seraient améliorés par les métadonnées ?
3. Conception
    - Concevez votre approche de l’architecture des informations, des métadonnées gérées et des types de contenu.
    - Concevez le processus de définition, de création, de gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifiez les titulaires de la mise en jeu, confirmez les scénarios et développez un plan de projet.
1. Configurez les paramètres et appliquez des licences.
1. Commencer la sensibilisation et la formation : recrutementz des champions.
1. Déployer par étapes.  
1. Recueillir des commentaires et itérer.
1. À mesure que l’utilisation augmente, planifiez les crédits du Générateur d’IA selon vos besoins.

## <a name="see-also"></a>Voir aussi

[Scénarios et cas d’utilisation pour SharePoint Syntex](adoption-scenarios.md) 
 [Gérer les contrats à l’aide d’Microsoft 365 solution](solution-manage-contracts-in-microsoft-365.md)
