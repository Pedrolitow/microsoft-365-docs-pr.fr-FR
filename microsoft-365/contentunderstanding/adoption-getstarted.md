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
ms.openlocfilehash: e88a7de1c81995b878dbf8a9308fbc774583289e
ms.sourcegitcommit: 8950d3cb0f3087be7105e370ed02c7a575d00ec2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2021
ms.locfileid: "50597057"
---
# <a name="microsoft-sharepoint-syntex-adoption-get-started"></a>Adoption de Microsoft SharePoint Syntex : commencer

Pensez aux services de contenu intelligent disponibles dans SharePoint Syntex comme ayant trois parties :

- **Compréhension du contenu : créez** des modèles d’IA sans code pour classifier et extraire des informations du contenu afin d’appliquer automatiquement les métadonnées pour la découverte et la réutilisation des connaissances. En savoir plus sur [la compréhension du contenu.](document-understanding-overview.md)
- **Traitement de contenu :** Automatisez la capture, l’ingestion et la catégorisation du contenu et rationalisez les processus centrées sur le contenu à l’aide de Power Automate. En savoir plus sur [le traitement du contenu.](form-processing-overview.md)
- **Conformité du contenu :** Contrôler et gérer le contenu pour améliorer la sécurité et la gouvernance avec l’intégration à Microsoft Information Protection.

Grâce aux nouvelles fonctionnalités et services d’IA, vous pouvez créer des applications de compréhension et de classification de contenu directement dans le flux de gestion de contenu à l’aide de SharePoint Syntex. Il existe deux façons de comprendre votre contenu. Le type de modèle que vous utilisez est basé sur le format de fichier et le cas d’utilisation :

| Traitement des formulaires | Compréhension du document |
|:-------|:-------|
| Créé à partir d’une bibliothèque de documents. | Créé dans le centre de contenu, qui fait partie de SharePoint Syntex. |
| Modèle créé dans le Générateur d’IA. | Modèle créé dans l’interface native. |
| Utilisé pour les formats de fichiers semi-structurés. | Utilisé pour les formats de fichiers non structurés. |
| Classifieur settable. | Classifieur entraisable avec des extracteurs facultatifs. |
| Limité à une seule bibliothèque. | Peut être appliqué à plusieurs bibliothèques. |
| Formation au format PDF, JPG, PNG, total 50 Mo/500 pp. | Formez-vous sur les fichiers PDF, Office ou e-mail 5-10, y compris des exemples négatifs. |

Pour une comparaison plus complète des fonctionnalités, voir Différence entre la compréhension des documents et [les modèles de traitement des formulaires.](difference-between-document-understanding-and-form-processing-model.md)

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identifier les scénarios d’entreprise pilote pour optimiser

Pour vous préparer à l’utilisation de SharePoint Syntex dans votre organisation, vous devez d’abord comprendre les scénarios dans lesquels il sera utile. Le « pourquoi » permet de déterminer le modèle qui sera nécessaire et comment structurer votre organisation en fonction de l’endroit où le modèle sera appliqué. Voici quelques scénarios dans lequel la compréhension des documents peut aider votre organisation :

- **Traitement de contenu :** Traiter des contrats, des instructions de travail et d’autres documents de type formulaire. Admission des formulaires, formation du modèle à comprendre et maque les champs, puis exécutez vos formulaires pour collecter automatiquement les données. Pour plus d’informations, voir [Vue d’ensemble du traitement des formulaires.](form-processing-overview.md)
- **Analyse des factures :** Retirez les détails pertinents de vos factures et assurez-vous qu’elles sont conformes à la stratégie ou qu’elles sont traitées correctement.

Réfléchissez aux façons dont SharePoint Syntex peut aider votre organisation :

- Automatiser les processus d’entreprise
- Améliorer la précision de la recherche
- Gérer les risques de conformité

Lorsque vous réfléchissez aux scénarios d’entreprise à prendre en compte, posez-vous les questions suivantes :

- Permet-elle de résoudre un problème réel ?
- Sera-t-elle largement utilisée ou aura-t-elle un large impact ?
- Est-il possible de l’obtenir ?
- Pouvez-vous mesurer la réussite ?

Hiérarchiser les scénarios en fonction de l’impact et de la facilité d’implémentation. Faites en sorte que vos scénarios d’impact initial sur le domaine de travail soient plus faciles à implémenter. Ne pas hiérarchiser les scénarios à faible impact qui sont difficiles à implémenter.

Utilisez les exemples de scénarios suivants pour vous faire part de vos idées sur l’utilisation de SharePoint Syntex dans votre organisation.

### <a name="scenario-track-data-from-invoices-with-form-processing"></a>Scénario : suivre les données des factures avec le traitement du formulaire

Par exemple, vous pouvez configurer un processus à l’aide des fonctionnalités SharePoint Syntex et Power Automate pour suivre et surveiller les factures.

1. Configurer une bibliothèque pour stocker les documents de facture.
1. Formez le modèle pour reconnaître les champs dans les documents.
1. Extrayez les champs que vous souhaitez suivre dans une liste.
1. Configurer un flux pour vous notifier d’événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - La date d’échéance d’une facture est passée.
    - Une facture est pour un montant supérieur à votre montant d’approbation automatique.

![Suivre et surveiller les factures avec SharePoint Syntex et Power Automate](../media/content-understanding/process-invoices-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de les faire manuellement.
- Réduisez les erreurs potentielles et assurez-vous d’une meilleure conformité à l’aide de flux de travail pour vérifier les factures et vous informer de tout problème.

### <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Scénario : suivre les informations des contrats avec la compréhension des documents

Par exemple, vous pouvez configurer un processus pour identifier les contrats que votre entreprise a avec d’autres sociétés ou individus. Configurer un modèle pour extraire des informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et ajouter les informations à la bibliothèque en tant que champs que vous pouvez rapidement afficher. Appliquez une étiquette de rétention à la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une durée spécifique afin de respecter les réglementations de votre entreprise.

1. Commencez au centre de contenu et créez un modèle de compréhension des documents pour les contrats.
1. Téléchargez des exemples de documents pour obtenir des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et passer en revue les résultats.
1. Formez l’extracteur pour identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis testez l’extracteur.
1. Une fois le modèle terminé, appliquez-le à une bibliothèque dans laquelle vous pouvez télécharger des contrats.
1. Appliquez une étiquette de rétention au champ date, afin que les contrats soient conservés dans la bibliothèque pendant la durée requise.

![Suivre et surveiller les contrats avec SharePoint Syntex et les étiquettes de rétention](../media/content-understanding/process-contracts-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de les faire manuellement.
- Assurez-vous d’une meilleure conformité en utilisant des étiquettes de rétention pour vous assurer que les contrats sont conservés de manière appropriée.

### <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex"></a>Scénario : éviter les risques avec la gestion des enregistrements, la gouvernance des documents et les processus de conformité basés sur SharePoint Syntex

La réduction des risques est un objectif commun pour la plupart des entreprises. Vous devrez peut-être :

- Un meilleur moyen de fournir/appliquer la gouvernance des informations au sein de votre client.
- Pour améliorer le système de classification des documents, des e-mails et d’autres formes de communication considérées comme des « enregistrements » pour les projets.
- Pour auditer les reçus, les contrats, etc., afin de garantir la conformité avec les stratégies de l’entreprise.
- Pour vous assurer que les projets ont toute la documentation requise pour la conformité.

Configurer certains processus de conformité avec SharePoint Syntex pour capturer et classer, auditer et indicateurr correctement les documents et formulaires qui ont besoin d’une meilleure gouvernance. Vous pouvez vous appuyer sur SharePoint Syntex pour classer automatiquement le contenu au lieu de compter sur les utilisateurs finaux pour baliser manuellement, ou l’équipe de conformité pour appliquer manuellement les règles de gouvernance et l’archivage. Vous pouvez également activer une expérience de recherche simplifiée, gérer les volumes de données, appliquer des stratégies de gestion et de rétention des enregistrements, garantir la conformité, ainsi que les pratiques d’archivage et de purge des meilleures pratiques.

Lorsque vous automatisez ce scénario, vous pouvez être sûr que :

- La conformité est maintenue et les risques sont réduits.
- La taxonomie et la gestion des enregistrements sont appliquées de façon cohérente et précise.
- Les volumes de contenu sont contrôlés.
- Les employés peuvent facilement découvrir les bonnes informations dans le bon contexte.

### <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scénario : capturer des informations à partir de documents précédemment inaccessibles

La plupart des organisations ont de grands référentiels de documents juridiques, de stratégies, de contrats, de documents RH et de directives de gouvernance. Exploitation de ces magasins de données pour extraire des informations précieuses telles que : projets, secteurs, thèmes, personnes, zones géographiques, etc.

Par exemple, un directeur RH doit accéder rapidement à tous les documents RH, y compris les CV, les stratégies RH et d’autres formulaires. Ils souhaitent également identifier rapidement les informations nécessaires à partir des CV et d’autres documents liés aux ressources humaines sans passer manuellement au travers des documents. Ils recherchent une solution qui leur permet de trouver rapidement les informations dont ils ont besoin sans avoir à examiner manuellement des milliers de CV, de stratégies RH et d’autres documents qui peuvent être répartis sur plusieurs sites.

Lorsque vous automatisez ce scénario, vous pouvez :

- Déverrouillez les connaissances du contenu numérique.
- Classifier les stratégies RH, cv, documents commerciaux, plans techniques, plans de compte et extraire des informations.
- Recherchez rapidement les informations ou le document que vous recherchez.
- Accédez instantanément aux dernières informations.
- Réduisez les temps de recherche.

### <a name="scenario-improve-data-processing-to-provide-insights--analytics"></a>Scénario : améliorer le traitement des données pour fournir des informations & analytique

Par exemple, une société de petite entreprise peut utiliser SharePoint Syntex pour extraire des informations à partir de documents FDA afin de répondre aux questions de leurs responsables. Le fait d’avoir les réponses plus facilement accessibles peut réduire le temps nécessaire pour produire ces réponses et augmenter la disponibilité des données afin de générer des réponses plus précises aux questions de direction.

Par exemple, un responsable de projet doit fournir rapidement des réponses aux questions relatives aux produits de mon équipe de direction. Ils doivent trouver des informations et des mesures relatives aux requêtes dans un tableau de bord consolidé. Ils recherchent une solution qui extrait les informations dont ils ont besoin à partir d’étiquettes de produits, de publications de produits et d’autres documents, et génère un rapport consolidé qu’ils peuvent utiliser lorsqu’ils font des rapports à leur équipe de direction.

Lorsque vous automatisez ce scénario, vous pouvez :

- Réduisez le temps de produire des réponses.
- Augmenter la disponibilité des données.
- Fournir des réponses plus précises.

### <a name="scenario-automate-order-processing"></a>Scénario : automatiser le traitement des commandes

Avec SharePoint Syntex, vous pouvez réduire le temps de traitement manuel des commandes client. Par exemple, vous pouvez charger des commandes de télécopie, de courrier électronique ou de papier dans SharePoint à l’aide du traitement OCR, puis extraire les métadonnées de ces commandes afin de pouvoir les traiter à l’aide de processus automatisés.

Par exemple, un responsable de la chaîne d’approvisionnement souhaite réduire les erreurs provoquées par l’entrée manuelle des données. Ils souhaitent éviter la révision manuelle et l’entrée de données des commandes client entrantes (papier, télécopie ou courrier électronique) afin de réduire les erreurs entrantes dans leurs systèmes d’entreprise. Ils souhaitent une solution qui applique des techniques d’IA et d’apprentissage automatique pour valider les informations de commande entrantes, extraire les données de base et les pousser automatiquement dans leur système ERP, pour l’traitement des commandes et le rapprochement.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- La précision de la commande et de l’expédition augmente.
- Les frais ou les pénalités associés aux erreurs de commande ou d’expédition sont réduits.
- Les retards de facturation ou de paiement diminuent.
- Les coûts de personnel sont réduits.

### <a name="scenario-simplify-visa-renewal-process"></a>Scénario : simplifier le processus de renouvellement du visa

SharePoint Syntex peut vous aider à automatiser les rappels et les renouvellements pour les informations clés du contrat. Par exemple, un directeur RH doit s’assurer que les visas des employés sont à jour et/ou renouvelés à temps. Ils souhaitent offrir aux utilisateurs un processus simple et intuitif pour la mise à jour de leur visa. Ils ont besoin d’une solution qui extrait les dates de renouvellement des contrats et envoie automatiquement des rappels aux employés lorsque leurs dates de renouvellement approchent.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- Les niveaux de non-conformité sont réduits.
- Le nombre de rappels manuels est réduit.
- Le nombre d’amendes pour non-conformité est réduit.

## <a name="identify-roles--responsibilities"></a>Identifier les rôles & responsabilités

Déterminer qui dans votre organisation créera et gérera les modèles ? Les rôles suivants peuvent être impliqués :

| SharePoint/Administrateur de connaissances | Administrateur de plateforme Power Platform | Gestionnaire de connaissances | Propriétaire du modèle |
|:-------|:-------|:-------|:-------|
| Rôle AAD| Rôle AAD | Rôle AAD | Champions  |
| Configurer le traitement des formulaires | Configurer l’environnement de service de données courant pour le traitement des formulaires | Recueillir des cas d’utilisation | Recueillir des cas d’utilisation professionnelle |
| Gérer les centres de contenu et les autorisations| Acheter et allouer des crédits AIB | Établir les meilleures pratiques et examiner l’analyse du modèle | Créer et appliquer des modèles |

Le gestionnaire de connaissances, le propriétaire des processus d’entreprise et le propriétaire du modèle de contenu créent des exemples de modèles et l’adoption de champion dans l’organisation.
Autres personnes impliquées : administrateur de conformité, responsables de taxonomie.

Où créeront-ils et appliqueront-ils les modèles ? Existe-t-il des processus ou des référentiels existants qui pourraient être améliorés ?

- Traitement de formulaire : déterminez les sites qui obtiennent l’action de traitement du formulaire.
- Compréhension des documents : vous pouvez créer plusieurs centres de contenu pour différents domaines d’activité.

## <a name="strategic-positioning"></a>Positionnement stratégique

Travaillez en équipe avec les parties prenantes pour vous assurer qu’elles sont alignées sur la stratégie d’utilisation de SharePoint Syntex. Recherchez et fournissez les ressources suivantes pour vous aider à ce positionnement :

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
3. Création
    - Concevoir votre approche de l’architecture des informations, des métadonnées gérées et des types de contenu
    - Concevez le processus de définition, de création, de gestion.

## <a name="engage-your-organization"></a>Impliquer votre organisation

1. Identifiez les titulaires de la mise en jeu, confirmez les scénarios et développez un plan de projet.
1. Configurez les paramètres et appliquez des licences.
1. Commencer la sensibilisation et la formation : recrutementz des champions.
1. Déployer par étapes.  
1. Recueillir des commentaires et itérer.
1. À mesure que l’utilisation augmente, planifiez les crédits du Générateur d’IA selon vos besoins.
