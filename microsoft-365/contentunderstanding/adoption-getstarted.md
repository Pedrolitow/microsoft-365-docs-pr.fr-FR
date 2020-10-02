---
title: 'Microsoft SharePoint Syntex adoption : prise en main'
description: Découvrez comment utiliser et implémenter SharePoint Syntex dans votre organisation pour vous aider à résoudre les problèmes de votre entreprise.
ms.author: samanro
author: samanro
manager: pamgreen
ms.date: 7/20/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.custom: Adopt
search.appverid: ''
localization_priority: Normal
ms.openlocfilehash: f6bb4f5e09adcb1be6323a5d3d182cc3d1bc6017
ms.sourcegitcommit: 3f8e573244bc082518125e339a385c41ef6ee800
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "48337228"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Microsoft SharePoint Syntex adoption : prise en main

Les services de contenu intelligents disponibles dans SharePoint Syntex se composent de trois parties :

- **Présentation du contenu :** créer des modèles ai sans code pour classer et extraire des informations du contenu pour appliquer automatiquement des métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur le [mémorandum d’accord](document-understanding-overview.md)sur le contenu.
- **Traitement de contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et rationalisez les processus orientés contenu à l’aide de Power Automated. En savoir plus sur le [traitement du contenu](form-processing-overview.md).
- **Conformité du contenu :** Contrôlez et gérez le contenu pour améliorer la sécurité et la gouvernance grâce à l’intégration à la protection des informations Microsoft.

Avec de nouveaux services et fonctionnalités AI, vous pouvez créer des applications de présentation et de classification de contenu directement dans le flux de gestion de contenu à l’aide de SharePoint Syntex :

|Entrée manuelle| Traitement des formulaires | Présentation des documents |
|:-------|:--------|:--------|
| Saisie de données et main-d’œuvre intensive sur tout le contenu | Traiter le contenu numérique : photos, analyses, reçus, cartes de visite, vidéos avec OCR & texte |  Capturer les types de contenu et les métadonnées des contrats, curriculum vitae et autres documents structurés |
| Interactives   | Prédéfini, automatisé   | Personnalisé, assisté   | Personnalisé, conforme |
| Personnes qui effectuent le travail | Enseigné par vos experts techniques (PME). Capturez les types de contenu et les métadonnées des contrats, curriculum vitae et autres documents non structurés. | Les PME sont moins impliquées. à partir de bons de commande, d’applications, d’autres documents structurés et semi-structurés |

Le tableau suivant explique ce que vous obtenez lorsque vous utilisez SharePoint Syntex :

| Traitement des formulaires | Présentation des documents |
|:-------|:-------|
| Disponible pour l’APAC, l’Australie, le Canada, l’UE, JP, Amérique latine, UK, US | Disponible dans toutes les régions |
| Utilise les crédits du générateur AI-1M crédits = 2000 pages ; La consommation est d’environ 2000 factures = 2 unités. La gestion de l’énergie automatique est requise : Si vous avez besoin de plus d’informations, vous pouvez l’ajouter. crédits 1 m alloués pour 300 licences et licences achetées. Vous pouvez également acheter des crédits séparément. | Les modèles fonctionnent sur tous les alphabets latins. En plus de l’anglais : allemand, suédois, français, espagnol, italien et portugais. |
| Mise en service par rapport à l’environnement de service de données commun par défaut| Ne dispose pas de restrictions de capacité. |

Il existe deux manières différentes de comprendre votre contenu. Le type de modèle que vous utilisez est basé sur le format de fichier et le cas d’utilisation :

| Traitement des formulaires | Présentation des documents |
|:-------|:-------|
| Créé à partir de la bibliothèque de documents | Créé dans le centre de contenu, partie de SharePoint Syntex |
| Modèle créé dans le générateur AI | Modèle créé dans l’interface native |
| Utilisé pour les formats de fichier semi-structurés | Utilisé pour les formats de fichiers non structurés |
| Classifieur définissable | Classificateur de formation avec extracteurs facultatifs |
| Limité à une seule bibliothèque | Peut être appliqué à plusieurs bibliothèques |
| Formation sur PDF, JPG, format PNG, total de 50 Mo/500 pp | Formation sur des fichiers PDF, Office ou de messagerie 5-10, y compris des exemples négatifs |

SharePoint Syntex s’intègre aux fonctionnalités de conformité de Microsoft 365 telles que :

- Étiquettes de rétention qui définissent la stratégie des enregistrements en fonction de l’âge des documents ou des événements externes.
- Les étiquettes de confidentialité qui définissent les stratégies de DLP, de chiffrement, de partage et d’accès conditionnel.

Les utilisateurs peuvent appliquer des étiquettes ou les appliquer automatiquement par les modèles Syntex AI de SharePoint. Les plans de fichiers et d’analyse fournissent une gestion évolutive des stratégies et de l’utilisation des étiquettes.

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilotes à optimiser

Pour vous préparer à l’utilisation de SharePoint Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels elle sera utile. Les raisons qui permettent de déterminer le modèle qui sera nécessaire et de structurer votre organisation en fonction de l’emplacement auquel le modèle sera appliqué. Voici quelques scénarios dans lesquels la compréhension des documents peut aider votre organisation :

- Traitement de contenu : traiter les contrats, les instructions de travail et d’autres documents de type formulaire. L’incorporation des formulaires, formez le modèle pour comprendre et mapper les champs, puis exécutez vos formulaires via pour collecter automatiquement les données. Pour plus d’informations, voir [Form Processing Overview](form-processing-overview.md).
- Analyse des factures : extrayez les détails pertinents de vos factures et assurez-vous qu’ils respectent la stratégie ou sont traités de manière appropriée.

Pensez aux différentes façons dont SharePoint Syntex peut aider votre organisation :

- Automatiser les processus d’entreprise
- Améliorer la précision de la recherche
- Gérer les risques de conformité

### <a name="form-processing-scenario-example"></a>Exemple de scénario de traitement de formulaire

Par exemple, vous pouvez configurer un processus à l’aide de SharePoint Syntex et Power automatez les fonctionnalités pour suivre et surveiller les factures.

1. Configurez une bibliothèque pour stocker les documents de facturation.
1. Former le modèle pour reconnaître les champs dans les documents.
1. Extrayez les champs dont vous souhaitez effectuer le suivi dans une liste.
1. Configurez un flux pour vous informer des événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - Une facture a dépassé sa date d’échéance.
    - Une facture a un montant supérieur à votre montant d’approbation automatique.

![Suivre et surveiller les factures avec SharePoint Syntex et Power Automated](../media/content-understanding/process-invoices-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de les effectuer manuellement.
- Réduisez les erreurs potentielles et assurez une meilleure conformité à l’aide de flux de travail pour agir sur les factures et vous avertir de tout problème.

### <a name="document-understanding-scenario-example"></a>Exemple de scénario de document

En guise d’autre exemple, vous pouvez configurer un processus pour identifier les contrats de votre entreprise avec d’autres sociétés ou personnes. Vous pouvez configurer un modèle pour extraire des informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et l’ajouter à la bibliothèque sous la forme de champs que vous pouvez rapidement afficher. Vous pouvez également appliquer une étiquette de rétention à la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une période de temps spécifique pour respecter les réglementations de votre entreprise.

1. Commencez par le centre de contenu et créez un nouveau modèle de présentation de document pour les contrats.
1. Téléchargez des exemples de documents pour obtenir des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et examiner les résultats.
1. Former l’extracteur pour identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis tester l’extracteur.
1. Une fois le modèle terminé, appliquez le modèle à une bibliothèque où vous pouvez télécharger des contrats.
1. Appliquer une étiquette de rétention au champ date, afin que les contrats soient conservés dans la bibliothèque pendant la durée nécessaire à votre organisation pour les contrats.

![Suivre et surveiller les contrats avec des étiquettes de rétention et de Syntex SharePoint](../media/content-understanding/process-contracts-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de les effectuer manuellement.
- Garantir une meilleure conformité à l’aide des étiquettes de rétention pour garantir que les contrats sont conservés de manière appropriée.

### <a name="tips-for-identifying-scenarios"></a>Conseils pour l’identification des scénarios

Lors de la réflexion sur les scénarios d’entreprise à prendre en compte, posez-vous les questions suivantes :

- Est-ce qu’il résout un problème réel ?
- Seront-elles largement utilisées ou ont un impact important ?
- Est-il possible de l’obtenir ?
- Pouvez-vous mesurer la réussite ?

Hiérarchisez les scénarios en fonction de l’impact et de la facilité d’implémentation. Faites en sorte que votre zone de focalisation initiale soit plus rapide et plus facile à mettre en œuvre. Dépriorité des scénarios d’impact inférieur qui sont difficiles à mettre en œuvre.

## <a name="identify-roles--responsibilities"></a>Identifier les rôles & responsabilités

Déterminer les personnes de votre organisation qui créeront et géreront les modèles ? Les rôles suivants peuvent être impliqués :

| SharePoint/Knowledge admin | Administrateur Power Platform | Gestionnaire de connaissances | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| Rôle AAD| Ajouter un rôle | Rôle AAD | Champions  |
| Configurer le traitement de formulaires | Configurer un environnement de service de données commun pour le traitement des formulaires | Collecter des cas d’utilisation | Collecter des cas d’utilisation professionnelle |
| Gérer les centres de contenu et les autorisations| Acheter et attribuer des crédits AIB | Établir les meilleures pratiques et analyser le modèle d’analyse | Créer et appliquer des modèles |

Gestionnaire de connaissances, propriétaire du processus métier et propriétaire du modèle de contenu créez des modèles d’exemple et des adoptions de champion dans l’organisation.
Autres personnes impliquées : administrateur de conformité, gestionnaires de taxonomie.

Où vont-ils créer et appliquer les modèles ? Existe-t-il des processus ou des référentiels qui pourraient être améliorés ?

- Traitement des formulaires : Déterminez les sites qui recevront une action de traitement de formulaire.
- Présentation des documents : vous pouvez créer plusieurs centres de contenu pour différents secteurs d’activité.

## <a name="strategic-positioning"></a>Positionnement stratégique

Collaborez avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation de SharePoint Syntex. Recherchez et fournissez les ressources suivantes pour vous aider dans ce positionnement :

- Résultats de l’entreprise :
  - Résultats fiscaux potentiels
  - Résultats de la réactivité potentielle
  - Modèle de résultat commercial
- Achat/alignement des sponsors/cadres
  - Jeux de cas commerciaux
  - Modèles financiers
  - Préparation de l’entreprise-culture

## <a name="identify-stakeholders"></a>Identifier les parties prenantes

Identifier les parties prenantes de votre projet.

|Role |Responsibilities |Département |
|:-------|:-------|:--------|
| Commanditaire (s) exécutif (s)   | Communication de la vision et des valeurs de haut niveau à la société   |  Leadership exécutif   |
| Responsable (s) de projet | Superviser l’exécution complète du processus de lancement et de déploiement | Gestion de projets |
| Administrateurs de connaissances| Créer et gérer les centres de contenu | Service informatique ou autre|
| Gestionnaires de contenu et propriétaires de modèles| Collecter des cas d’utilisation et créer et appliquer des modèles | Tout service|
| Champions  | Aider à la gestion et à la gestion des objections | Tout service (personnel) |
| Administrateur des clients | Configurer les paramètres au niveau du client | Service informatique|
| Administrateur Power Platform| Configurer un environnement Common Data Services | Service informatique|

> [!Note]
> Bien que nous vous recommandons de disposer de chacun de ces rôles dans tout votre déploiement, vous pouvez constater que vous n’en avez pas besoin tous pour commencer à utiliser votre solution identifiée.

## <a name="readiness-checklist"></a>Liste de vérification de préparation

Pour vous préparer à l’implémentation de SharePoint Syntex, vous devez :

![Préparation pour la compréhension du contenu](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planifier l’état final
    - Les modèles de présentation des documents sont les moyens, pas la fin.
    - Planifiez l’exploit de la valeur des métadonnées extraites avec les éléments suivants :
      - Recherche
      - Filtrage et affichage de la mise en forme
      - Conformité
      - Automation
2. Identifier
    - Comprendre l’architecture d’informations et la fonctionnalité de gestion de contenu existantes.
    - Tout type de contenu existant est-il adapté aux modèles ?
    - Quels sont les processus existants qui seraient améliorés par les métadonnées ?
3. Conception
    - Concevoir votre approche de l’architecture des informations, des métadonnées gérées et des types de contenu
    - Concevez le processus de définition, de création et de gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifier les titulaires de participants, confirmer les scénarios et développer le plan de projet.
1. Configurez les paramètres et appliquez des licences.
1. Commencer la sensibilisation et la formation – recruter des champions.
1. Déployer en plusieurs étapes.  
1. Recueillez des commentaires et itérez.
1. À mesure que l’utilisation augmente, planifiez les crédits du générateur AI si nécessaire.
