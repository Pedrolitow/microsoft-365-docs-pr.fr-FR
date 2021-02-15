---
title: 'Adoption de Microsoft SharePoint Syntex : commencer'
description: Découvrez comment utiliser et implémenter SharePoint Syntex dans votre organisation pour vous aider à résoudre vos problèmes d’entreprise.
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: 7/20/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
localization_priority: Normal
ms.openlocfilehash: 7a0bd04121d7400cced22e43a539bd21c45a7fc3
ms.sourcegitcommit: 162c01dfaa2fdb3225ce4c24964c1065ce22ed5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "49976570"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Adoption de Microsoft SharePoint Syntex : commencer

Pensez aux services de contenu intelligent disponibles dans SharePoint Syntex comme ayant trois parties :

- **Compréhension du contenu : créer** des modèles d’IA sans code pour classifier et extraire des informations du contenu afin d’appliquer automatiquement les métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur [la compréhension du contenu.](document-understanding-overview.md)
- **Traitement de contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et rationalisez les processus centrées sur le contenu à l’aide de Power Automate. En savoir plus sur [le traitement du contenu.](form-processing-overview.md)
- **Conformité du contenu :** Contrôler et gérer le contenu pour améliorer la sécurité et la gouvernance avec l’intégration à Microsoft Information Protection.

Grâce aux nouvelles fonctionnalités et services d’IA, vous pouvez créer des applications de compréhension et de classification de contenu directement dans le flux de gestion de contenu à l’aide de SharePoint Syntex. Il existe deux façons de comprendre votre contenu. Le type de modèle que vous utilisez est basé sur le format de fichier et le cas d’utilisation :

| Traitement des formulaires | Compréhension des documents |
|:-------|:-------|
| Créé à partir d’une bibliothèque de documents. | Créé dans le centre de contenu, qui fait partie de SharePoint Syntex. |
| Modèle créé dans le Générateur d’IA. | Modèle créé dans l’interface native. |
| Utilisé pour les formats de fichiers semi-structurés. | Utilisé pour les formats de fichiers non structurés. |
| Classifieur settable. | Classifieur entraisable avec des extracteurs facultatifs. |
| Limité à une seule bibliothèque. | Peut être appliqué à plusieurs bibliothèques. |
| Formation au format PDF, JPG, PNG, total 50 Mo/500 pp. | Formez-vous sur les fichiers PDF, Office ou e-mail 5-10, y compris des exemples négatifs. |

Le tableau suivant explique la disponibilité et la gestion des licences pour SharePoint Syntex :

| Traitement des formulaires | Compréhension des documents |
|:-------|:-------|
| Le traitement de formulaire s’appuie sur power platform. <br>Pour plus d’informations sur la disponibilité globale pour la plateforme Power Platform et le Générateur d’IA, voir [Disponibilité de la plateforme Power.](https://dynamics.microsoft.com/geographic-availability/) | Disponible dans toutes les régions. |
| Utilise les crédits générateur d’IA.<br>Les crédits peuvent être achetés par lots de 1 M.<br>1M de crédits sont inclus lorsque vous achetez plus de 300 licences SharePoint Syntex.<br>Les crédits 1M permettent le traitement de 2 000 pages de fichiers. | Les modèles fonctionnent sur toutes les langues de l’alphabet latin. En plus de l’anglais : allemand, suédois, français, espagnol, italien et portugais. |
| Mise en service dans l’environnement de service de données commun par défaut. | N’a pas de restrictions de capacité. |

Pour plus d’informations sur les crédits et les unités du Générateur d’IA, voir [Licences du Générateur d’IA.](https://docs.microsoft.com/ai-builder/administer-licensing)

SharePoint Syntex s’intègre aux fonctionnalités de conformité De Microsoft 365 telles que :

- Étiquettes de rétention qui définissent la stratégie d’enregistrements en fonction de l’âge du document ou des événements externes.
- Étiquettes de confidentialité qui définissent des stratégies d’accès conditionnel, de chiffrement, de partage et de DLP.

Les utilisateurs peuvent appliquer des étiquettes, ou elles peuvent être appliquées automatiquement par les modèles SharePoint Syntex AI. Les analyses et les plans de gestion de fichiers offrent une gestion à l’échelle de l’utilisation et des stratégies des étiquettes.

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilote pour optimiser

Pour vous préparer à l’utilisation de SharePoint Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels il sera utile. La raison pour laquelle vous déterminez le modèle qui sera nécessaire et comment structurer votre organisation en fonction de l’endroit où le modèle sera appliqué. Voici quelques scénarios dans lequel la compréhension des documents peut aider votre organisation :

- Traitement de contenu : traiter des contrats, des instructions de travail et d’autres documents de type formulaire. Admission des formulaires, formation du modèle à comprendre et maque les champs, puis exécutez vos formulaires pour collecter automatiquement les données. Pour plus d’informations, voir [Vue d’ensemble du traitement des formulaires.](form-processing-overview.md)
- Analyse des factures : retirez les détails pertinents de vos factures et assurez-vous qu’elles sont conformes à la stratégie ou qu’elles sont traitées correctement.

Réfléchissez aux façons dont SharePoint Syntex peut aider votre organisation :

- Automatiser les processus d’entreprise
- Améliorer la précision de la recherche
- Gérer les risques de conformité

### <a name="form-processing-scenario-example"></a>Exemple de scénario de traitement de formulaire

Par exemple, vous pouvez configurer un processus à l’aide des fonctionnalités SharePoint Syntex et Power Automate pour suivre et surveiller les factures.

1. Configurer une bibliothèque pour stocker les documents de facture.
1. Formez le modèle pour reconnaître les champs dans les documents.
1. Extrayez les champs que vous souhaitez suivre dans une liste.
1. Configurer un flux pour vous notifier d’événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - La date d’échéance d’une facture est passée.
    - Une facture représente un montant supérieur à votre montant d’approbation automatique.

![Suivre et surveiller les factures avec SharePoint Syntex et Power Automate](../media/content-understanding/process-invoices-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de les faire manuellement.
- Réduisez les erreurs potentielles et assurez-vous d’une meilleure conformité en utilisant des flux de travail pour agir sur les factures et vous informer de tout problème.

### <a name="document-understanding-scenario-example"></a>Exemple de scénario de compréhension de document

Par exemple, vous pouvez configurer un processus pour identifier les contrats que votre entreprise a avec d’autres sociétés ou individus. Vous pouvez configurer un modèle pour extraire des informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et l’ajouter à la bibliothèque en tant que champs que vous pouvez rapidement afficher. Vous pouvez également appliquer une étiquette de rétention à la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une durée spécifique afin de respecter les réglementations de votre entreprise.

1. Commencez au centre de contenu et créez un modèle de compréhension des documents pour les contrats.
1. Téléchargez des exemples de documents pour obtenir des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et passer en revue les résultats.
1. Formez l’extracteur pour identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis testez l’extracteur.
1. Une fois le modèle terminé, appliquez-le à une bibliothèque dans laquelle vous pouvez télécharger des contrats.
1. Appliquez une étiquette de rétention au champ date, afin que les contrats soient conservés dans la bibliothèque pendant la durée nécessaire à votre organisation pour les contrats.

![Suivre et surveiller les contrats avec SharePoint Syntex et les étiquettes de rétention](../media/content-understanding/process-contracts-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de les faire manuellement.
- Assurez-vous d’une meilleure conformité en utilisant des étiquettes de rétention pour vous assurer que les contrats sont conservés de manière appropriée.

### <a name="tips-for-identifying-scenarios"></a>Conseils pour identifier les scénarios

Lorsque vous réfléchissez aux scénarios d’entreprise à prendre en compte, posez-vous les questions suivantes :

- Permet-elle de résoudre un problème réel ?
- Sera-t-elle largement utilisée ou aura-t-elle un large impact ?
- Est-il possible de l’obtenir ?
- Pouvez-vous mesurer la réussite ?

Hiérarchiser les scénarios en fonction de l’impact et de la facilité d’implémentation. Faites en sorte que vos scénarios d’impact initial sur le domaine de travail soient plus faciles à implémenter. Ne pas hiérarchiser les scénarios à faible impact qui sont difficiles à implémenter.

## <a name="identify-roles--responsibilities"></a>Identifier les rôles & responsabilités

Déterminer qui dans votre organisation créera et gérera les modèles ? Les rôles suivants peuvent être impliqués :

| SharePoint/Administrateur de connaissances | Administrateur de plateforme Power Platform | Gestionnaire de connaissances | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| Rôle AAD| Rôle ADD | Rôle AAD | Champions  |
| Configurer le traitement des formulaires | Configurer l’environnement de service de données courant pour le traitement des formulaires | Recueillir des cas d’utilisation | Recueillir des cas d’utilisation professionnelle |
| Gérer les centres de contenu et les autorisations| Acheter et allouer des crédits AIB | Établir les meilleures pratiques et examiner l’analyse du modèle | Créer et appliquer des modèles |

Le gestionnaire de connaissances, le propriétaire des processus d’entreprise et le propriétaire du modèle de contenu créent des exemples de modèles et l’adoption de champion dans l’organisation.
Autres personnes impliquées : administrateur de conformité, responsables de taxonomie.

Où créeront-ils et appliqueront-ils les modèles ? Existe-t-il des processus ou des référentiels existants qui pourraient être améliorés ?

- Traitement de formulaire : déterminez les sites qui obtiennent l’action de traitement du formulaire.
- Compréhension des documents : vous pouvez créer plusieurs centres de contenu pour différents domaines d’activité.

## <a name="strategic-positioning"></a>Positionnement stratégique

Travaillez avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation de SharePoint Syntex. Recherchez et fournissez les ressources suivantes pour vous aider à ce positionnement :

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

|Role |Responsibilities |Département |
|:-------|:-------|:--------|
| Sponsor(s) exécutif(s)   | Communiquer une vision et des valeurs de haut niveau à l’entreprise   |  Direction   |
| Responsables de projet | Superviser l’ensemble du processus d’exécution et de déploiement du lancement | Gestion de projets |
| Administrateurs du savoir| Créer et gérer les centres de contenu | Service informatique ou autre service|
| Gestionnaires de contenu et propriétaires de modèles| Collecter des cas d’utilisation, créer et appliquer des modèles | N’importe quel service|
| Champions  | Contribuer à l’évodabilité et à la gestion de la gestion des oppositions | N’importe quel service (personnel) |
| Administrateur des clients | Configurer les paramètres au niveau du client | Service informatique|
| Administrateur de plateforme Power Platform| Configurer un environnement de services de données courant | Service informatique|

> [!Note]
> Même si nous vous recommandons de remplir chacun de ces rôles tout au long de votre déploiement, il se peut que vous n’en exigeiez pas tous la mise en place de votre solution identifiée.

## <a name="readiness-checklist"></a>Liste de vérification de préparation

Pour vous préparer à l’implémentation de SharePoint Syntex, vous devez :

![Préparation pour la compréhension du contenu](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planifier l’état final
    - Les modèles de compréhension de documents sont les moyens, et non la fin.
    - Planifiez l’exploitation de la valeur des métadonnées extraites avec :
      - Recherche
      - Filtrage et mise en forme de l’affichage
      - Conformité
      - Automation
2. Identifier
    - Comprendre l’utilisation existante de l’architecture des informations et de la fonctionnalité de gestion de contenu.
    - Les types de contenu existants sont-ils de bons candidats pour les modèles ?
    - Quels processus existants seraient améliorés par les métadonnées ?
3. Conception
    - Concevoir votre approche de l’architecture des informations, des métadonnées gérées et des types de contenu
    - Concevez le processus de définition, de création, de gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifiez les titulaires de la mise en jeu, confirmez les scénarios et développez un plan de projet.
1. Configurez les paramètres et appliquez des licences.
1. Commencer la sensibilisation et la formation : recrutementz des champions.
1. Déployer par étapes.  
1. Recueillir des commentaires et itérer.
1. À mesure que l’utilisation augmente, planifiez les crédits du Générateur d’IA selon vos besoins.
