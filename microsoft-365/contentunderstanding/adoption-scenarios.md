---
title: Scénarios et cas d’usage pour Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
ms.date: ''
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
description: Recherchez des scénarios métier sur l’utilisation de Microsoft Syntex dans votre organisation.
ms.openlocfilehash: 66cb9eeb572be506b246275a6e609d395c70a48e
ms.sourcegitcommit: ca082da1c51a3f643f152492579eef5679d52bd0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68547837"
---
# <a name="scenarios-and-use-cases-for-microsoft-syntex"></a>Scénarios et cas d’usage pour Microsoft Syntex

Utilisez les exemples de scénarios suivants pour vous demander comment utiliser Microsoft Syntex dans votre organisation.

- [Scénario : Suivre les données des factures avec le traitement des formulaires](adoption-scenarios.md#scenario-track-data-from-invoices-with-form-processing)
- [Scénario : Suivre les informations des contrats avec compréhension de document](adoption-scenarios.md#scenario-track-information-from-contracts-with-document-understanding)
- [Scénario : Éviter les risques liés aux processus de gestion des enregistrements, de gouvernance des documents et de conformité basés sur Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-syntex)
- [Scénario : Capturer des informations à partir de documents précédemment inaccessibles](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Scénario : Améliorer le traitement des données pour fournir des insights et des analyses](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Scénario : Automatiser le traitement des commandes](adoption-scenarios.md#scenario-automate-order-processing)
- [Scénario : Simplifier le processus de renouvellement des visas](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-data-from-invoices-with-form-processing"></a>Scénario : Suivre les données des factures avec le traitement des formulaires

Par exemple, vous pouvez configurer un processus à l’aide des fonctionnalités Syntex et Power Automate pour suivre et surveiller les factures.

1. Configurez une bibliothèque pour stocker les documents de facture.
1. Entraîner le modèle pour reconnaître les champs dans les documents.
1. Extrayez les champs à suivre dans une liste.
1. Configurez un flux pour vous avertir pour des événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - Une facture a dépassé sa date d’échéance.
    - Une facture correspond à un montant supérieur à votre montant d’approbation automatique.

![Suivez et surveillez les factures avec Syntex et Power Automate.](../media/content-understanding/process-invoices-flow.png)

Quand vous automatiserez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de les faire manuellement.
- Réduisez les erreurs potentielles et assurez une meilleure conformité en utilisant des flux de travail pour vérifier les factures et vous informer de tout problème.

## <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Scénario : Suivre les informations des contrats avec compréhension de document

Par ailleurs, vous pouvez configurer un processus pour identifier les contrats que votre entreprise a conclus avec d’autres sociétés ou particuliers. Configurez un modèle pour extraire les informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et ajoutez les informations à la bibliothèque en tant que champs que vous pouvez afficher rapidement. Appliquez une étiquette de rétention sur la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une durée spécifique pour une conformité appropriée aux réglementations de votre entreprise.

1. Commencez au centre de contenu et créez un nouveau modèle de compréhension de document pour les contrats.
1. Chargez des exemples de documents pour obtenir des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et passer en revue les résultats.
1. Entraînez l’extracteur pour identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis testez l’extracteur.
1. Une fois le modèle terminé, appliquez-le à une bibliothèque dans laquelle vous pouvez charger des contrats.
1. Appliquez une étiquette de rétention au champ de date afin que les contrats soient conservés dans la bibliothèque pendant la durée requise.

![Suivez et surveillez les contrats avec Syntex et les étiquettes de rétention.](../media/content-understanding/process-contracts-flow.png)

Quand vous automatiserez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de les faire manuellement.
- Assurez une meilleure conformité en utilisant des étiquettes de rétention pour garantir que les contrats sont conservés correctement.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-syntex"></a>Scénario : Éviter les risques liés aux processus de gestion des enregistrements, de gouvernance des documents et de conformité basés sur Syntex

La réduction des risques est un objectif commun pour la plupart des entreprises. Vous aurez peut-être besoin des éléments suivantes :

- Un meilleur moyen de fournir/d’appliquer la gouvernance des informations dans votre locataire.
- Améliorer le système de classification des documents, e-mails et autres formes de communication considérés comme des « enregistrements » pour les projets.
- Pour auditer les reçus, les contrats, et ainsi de suite, pour garantir la conformité avec les stratégies de l’entreprise.
- Pour s’assurer que les projets disposent de toute la documentation requise pour la conformité.

Configurez certains processus de conformité avec Syntex pour capturer et classifier, auditer et marquer de manière appropriée les documents et formulaires qui nécessitent une meilleure gouvernance. Vous pouvez vous appuyer sur Syntex pour classer automatiquement le contenu au lieu de compter sur les utilisateurs finaux pour baliser manuellement, ou sur l’équipe de conformité pour appliquer manuellement les règles de gouvernance et l’archivage. Vous pouvez également activer une expérience de recherche simplifiée, gérer les volumes de données, appliquer des stratégies de gestion et de rétention des enregistrements, garantir la conformité et les meilleures pratiques d’archivage et de purge.

Lorsque vous automatiserez ce scénario, vous pouvez vous sentir en sécurité :

- La conformité est confirmée et les risques sont réduits.
- La taxonomie et la gestion des enregistrements sont appliquées de manière cohérente et précise.
- Les volumes de contenu sont contrôlés.
- Les employés peuvent facilement découvrir les bonnes informations dans le contexte approprié.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scénario : Capturer des informations à partir de documents précédemment inaccessibles

La plupart des organisations disposent de grands référentiels de documents juridiques, de stratégies, de contrats, de documents RH et de directives de gouvernance. Extrayez ces magasins de données pour extraire des informations précieuses telles que : projets, secteurs, thèmes, personnes, zones géographiques, etc.

Par exemple, un directeur des ressources humaines doit accéder rapidement à tous les documents RH, y compris les cv, les stratégies RH et d’autres formulaires. Et ils souhaitent identifier rapidement les informations nécessaires à partir de CV et d’autres documents liés aux RH sans passer manuellement au crible les documents. Ils recherchent une solution qui leur permet de trouver rapidement les informations dont ils ont besoin sans avoir à examiner manuellement des milliers de CV, de stratégies rhéographiques et d’autres documents qui peuvent être répartis sur plusieurs sites.

Quand vous automatiserez ce scénario, vous pouvez :

- Déverrouillez les connaissances à partir du contenu numérique.
- Classifier les stratégies RH, les CV, les documents de vente, les blueprints techniques, les plans de compte et extraire des informations.
- Recherchez rapidement les informations ou le document appropriés que vous recherchez.
- Obtenez un accès instantané aux informations les plus récentes.
- Réduisez les temps de recherche.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Scénario : Améliorer le traitement des données pour fournir des insights et des analyses

Par exemple, une société pharmaceutique pourrait utiliser Syntex pour extraire des informations de documents de la FDA afin de répondre aux questions de ses dirigeants. Le fait d’avoir les réponses plus facilement accessibles peut réduire le temps nécessaire pour produire ces réponses et augmenter la disponibilité des données afin de générer des réponses plus précises aux questions de leadership.

Par exemple, un responsable de projet doit fournir rapidement des réponses aux questions relatives aux produits de mon équipe de direction. Ils doivent trouver des informations et des métriques relatives aux requêtes dans un tableau de bord consolidé. Ils recherchent une solution qui extrait les informations dont ils ont besoin à partir d’étiquettes de produits, de brochures sur les produits et d’autres documents, et génère un rapport consolidé qu’ils peuvent utiliser lorsqu’ils rendent compte à leur équipe de direction.

Quand vous automatiserez ce scénario, vous pouvez :

- Réduisez le temps nécessaire pour produire des réponses.
- Augmentez la disponibilité des données.
- Fournir des réponses plus précises.

## <a name="scenario-automate-order-processing"></a>Scénario : Automatiser le traitement des commandes

Avec Syntex, vous pouvez réduire le temps de traitement manuel des commandes client. Par exemple, vous pouvez charger des commandes à partir d’une télécopie, d’un e-mail ou d’un papier dans la bibliothèque de documents SharePoint à l’aide du traitement OCR, puis extraire les métadonnées de ces commandes afin de pouvoir les traiter à l’aide de processus automatisés.

Par exemple, un gestionnaire de chaîne d’approvisionnement souhaite réduire les erreurs provoquées par l’entrée manuelle de données. Ils souhaitent éviter la révision manuelle et l’entrée de données des commandes des clients entrants (papier, télécopie ou e-mail) afin de réduire les erreurs qui se sont produites dans leurs systèmes d’entreprise. Ils souhaitent une solution qui applique des techniques d’IA et de Machine Learning pour valider les informations de commande entrantes, extraire les données de base et les envoyer automatiquement dans leur système ERP, pour l’exécution et le rapprochement des commandes.

Quand vous automatiserez ce scénario, vous pouvez vous assurer que :

- La précision de la commande et de l’expédition augmente.
- Les frais ou pénalités associés aux erreurs de commande ou d’expédition sont réduits.
- Les retards de facturation ou de paiement diminuent.
- Les coûts de personnel sont réduits.

## <a name="scenario-simplify-visa-renewal-process"></a>Scénario : Simplifier le processus de renouvellement des visas

Syntex peut vous aider à automatiser les rappels et les renouvellements pour les informations de contrat clés. Par exemple, un directeur des ressources humaines doit s’assurer que les visas des employés sont à jour et/ou renouvelés à temps. Ils veulent donner aux gens un processus simple et intuitif pour mettre à jour leurs visas. Ils ont besoin d’une solution qui extrait les dates de renouvellement des contrats et envoie automatiquement des rappels aux employés lorsque leurs dates de renouvellement approchent.

Quand vous automatiserez ce scénario, vous pouvez vous assurer que :

- Les niveaux de non-conformité sont réduits.
- Le nombre de rappels manuels est réduit.
- Le nombre d’amendes pour non-conformité est réduit.

## <a name="see-also"></a>Voir aussi

[Prise en main de l’adoption de Syntex](adoption-getstarted.md)