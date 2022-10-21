---
title: Scénarios et cas d’usage pour Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
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
description: Recherchez des scénarios métier sur l’utilisation de Microsoft Syntex dans votre organisation.
ms.openlocfilehash: a43231e268e69a74cdc0bbc35df2cdd24d9e0d37
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660904"
---
# <a name="scenarios-and-use-cases-for-microsoft-syntex"></a>Scénarios et cas d’usage pour Microsoft Syntex

Utilisez les exemples de scénarios suivants pour vous demander des idées sur la façon dont vous pouvez utiliser Microsoft Syntex dans votre organisation.

- [Scénario : Suivre les informations des factures à l’aide du modèle de traitement de document structuré](adoption-scenarios.md#scenario-track-information-from-invoices-by-using-the-structured-document-processing-model)
- [Scénario : Suivre les informations des contrats à l’aide du modèle de traitement de document non structuré](adoption-scenarios.md#scenario-track-information-from-contracts-by-using-the-unstructured-document-processing-model)
- [Scénario : Évitez les risques avec la gestion des enregistrements, la gouvernance des documents et les processus de conformité basés sur Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-syntex)
- [Scénario : Capturer des informations à partir de documents précédemment inaccessibles](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Scénario : Améliorer le traitement des données pour fournir des insights et des analyses](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Scénario : Automatiser le traitement des commandes](adoption-scenarios.md#scenario-automate-order-processing)
- [Scénario : Simplifier le processus de renouvellement des visas](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-information-from-invoices-by-using-the-structured-document-processing-model"></a>Scénario : Suivre les informations des factures à l’aide du modèle de traitement de document structuré

Par exemple, vous pouvez configurer un processus à l’aide des fonctionnalités Syntex et Power Automate pour suivre et surveiller les factures.

1. Configurez une bibliothèque pour stocker les documents de facture.
2. Entraînez le modèle à reconnaître les champs dans les documents.
3. Extrayez les champs que vous souhaitez suivre dans une liste.
4. Configurez un flux pour vous avertir d’événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - Une facture dépasse sa date d’échéance.
    - Une facture correspond à un montant supérieur à votre montant d’approbation automatique.

![Suivez et surveillez les factures avec Syntex et Power Automate.](../media/content-understanding/process-invoices-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de le faire manuellement.
- Réduisez les erreurs potentielles et garantissez une meilleure conformité en utilisant des flux de travail pour vérifier les factures et vous informer des éventuels problèmes.

## <a name="scenario-track-information-from-contracts-by-using-the-unstructured-document-processing-model"></a>Scénario : Suivre les informations des contrats à l’aide du modèle de traitement de document non structuré

Autre exemple, vous pouvez configurer un processus pour identifier les contrats que votre entreprise a avec d’autres entreprises ou individus. Configurez un modèle pour extraire des informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et ajoutez les informations à la bibliothèque sous forme de champs que vous pouvez afficher rapidement. Appliquez une étiquette de rétention sur la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une durée spécifique pour se conformer aux réglementations de votre entreprise.

1. Commencez par le centre de contenu et créez un modèle de traitement de document non structuré pour les contrats.
2. Chargez des exemples de documents pour obtenir des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et passer en revue les résultats.
3. Entraînez l’extracteur à identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis testez l’extracteur.
4. Une fois le modèle terminé, appliquez le modèle à une bibliothèque dans laquelle vous pouvez charger des contrats.
5. Appliquez une étiquette de rétention au champ de date afin que les contrats soient conservés dans la bibliothèque pendant la durée requise.

![Suivez et surveillez les contrats avec Syntex et les étiquettes de rétention.](../media/content-understanding/process-contracts-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de le faire manuellement.
- Assurez-vous d’une meilleure conformité en utilisant des étiquettes de rétention pour vous assurer que les contrats sont conservés de manière appropriée.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-syntex"></a>Scénario : Évitez les risques avec la gestion des enregistrements, la gouvernance des documents et les processus de conformité basés sur Syntex

La réduction des risques est un objectif commun pour la plupart des entreprises. Vous aurez peut-être besoin des éléments suivants :

- Un meilleur moyen de fournir/appliquer la gouvernance des informations au sein de votre locataire.
- Améliorer le système de classification des documents, des e-mails et d’autres formes de communication considérés comme des « enregistrements » pour les projets.
- Pour auditer les reçus, les contrats, etc., afin de garantir la conformité aux stratégies de l’entreprise.
- Pour vous assurer que les projets disposent de toute la documentation requise pour la conformité.

Configurez certains processus de conformité avec Syntex pour capturer et classer de manière appropriée, auditer et marquer les documents et formulaires qui nécessitent une meilleure gouvernance. Vous pouvez vous appuyer sur Syntex pour classifier automatiquement le contenu plutôt que sur les utilisateurs finaux à étiqueter manuellement, ou sur l’équipe de conformité pour appliquer manuellement les règles de gouvernance et l’archivage. Vous pouvez également activer une expérience de recherche simplifiée, gérer les volumes de données, appliquer des stratégies de gestion des enregistrements et de rétention, garantir la conformité et les meilleures pratiques d’archivage et de purge.

Lorsque vous automatisez ce scénario, vous pouvez vous sentir en sécurité :

- La conformité est maintenue et les risques sont réduits.
- La gestion de la taxonomie et des enregistrements est appliquée de manière cohérente et précise.
- Les volumes de contenu sont contrôlés.
- Les employés peuvent facilement découvrir les informations appropriées dans le contexte approprié.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scénario : Capturer des informations à partir de documents précédemment inaccessibles

La plupart des organisations disposent de grands référentiels de documents juridiques, de stratégies, de contrats, de documents RH et de directives de gouvernance. Utilisez ces magasins de données pour extraire des informations précieuses telles que : projets, secteurs, thèmes, personnes, zones géographiques, etc.

Par exemple, un directeur rh doit accéder rapidement à tous les documents RH, y compris les CV, les stratégies RH et d’autres formulaires. Et ils souhaitent rapidement identifier les informations nécessaires à partir de CV et d’autres documents liés aux RH sans passer au crible manuellement les documents. Ils recherchent une solution qui leur permet de trouver rapidement les informations dont ils ont besoin sans avoir à consulter manuellement des milliers de CV, de stratégies RH et d’autres documents qui peuvent être répartis sur plusieurs sites.

Lorsque vous automatisez ce scénario, vous pouvez :

- Déverrouillez les connaissances du contenu numérique.
- Classifiez les stratégies RH, les CV, les documents commerciaux, les blueprints techniques et les plans de compte, et extrayez des informations.
- Trouvez rapidement les informations ou le document que vous recherchez.
- Obtenez un accès instantané aux informations les plus récentes.
- Réduisez les temps de recherche.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Scénario : Améliorer le traitement des données pour fournir des insights et des analyses

Par exemple, une société pharmaceutique pourrait utiliser Syntex pour extraire des informations des documents de la FDA afin de répondre aux questions de leurs dirigeants. Le fait d’avoir les réponses plus facilement accessibles peut réduire le temps nécessaire pour produire ces réponses et augmenter la disponibilité des données pour générer des réponses plus précises aux questions des dirigeants.

Par exemple, un responsable de projet doit fournir rapidement des réponses aux questions relatives aux produits de mon équipe de direction. Ils doivent trouver des informations et des métriques relatives aux requêtes dans un tableau de bord consolidé. Ils recherchent une solution qui extrait les informations dont ils ont besoin à partir des étiquettes de produits, des brochures sur les produits et d’autres documents, et qui génère un rapport consolidé qu’ils peuvent utiliser pour faire rapport à leur équipe de direction.

Lorsque vous automatisez ce scénario, vous pouvez :

- Réduisez le temps nécessaire pour produire des réponses.
- Augmenter la disponibilité des données.
- Fournissez des réponses plus précises.

## <a name="scenario-automate-order-processing"></a>Scénario : Automatiser le traitement des commandes

Avec Syntex, vous pouvez réduire le temps de traitement manuel des commandes des clients. Par exemple, vous pouvez charger des commandes à partir d’une télécopie, d’un e-mail ou d’un papier dans SharePoint à l’aide du traitement OCR, puis extraire les métadonnées de ces commandes afin de pouvoir les traiter à l’aide de processus automatisés.

Par exemple, un gestionnaire de chaîne d’approvisionnement souhaite réduire les erreurs provoquées par l’entrée manuelle de données. Ils souhaitent éviter la révision manuelle et la saisie de données des commandes client entrantes (papier, télécopie ou e-mail) afin de réduire les erreurs dans leurs systèmes d’entreprise. Ils veulent une solution qui applique des techniques d’IA et de Machine Learning pour valider les informations de commande entrantes, extraire les données de base et les pousser automatiquement dans leur système ERP, pour le traitement et le rapprochement des commandes.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- La précision des commandes et de l’expédition augmente.
- Les frais ou pénalités associés aux erreurs de commande ou d’expédition sont réduits.
- Les retards de facturation ou de paiement diminuent.
- Les coûts de personnel sont réduits.

## <a name="scenario-simplify-visa-renewal-process"></a>Scénario : Simplifier le processus de renouvellement des visas

Syntex peut vous aider à automatiser les rappels et les renouvellements pour les informations de contrat clés. Par exemple, un directeur des ressources humaines doit s’assurer que les visas des employés sont à jour ou renouvelés à temps. Ils veulent donner aux gens un processus simple et intuitif pour mettre à jour leurs visas. Ils ont besoin d’une solution qui extrait les dates de renouvellement des contrats et envoie automatiquement des rappels aux employés lorsque leurs dates de renouvellement approchent.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- Les niveaux de non-conformité sont réduits.
- Le nombre de rappels manuels est réduit.
- Le nombre d’amendes en cas de non-conformité est réduit.

## <a name="see-also"></a>Voir aussi

[Prise en main de l’adoption de Microsoft Syntex](adoption-getstarted.md)

[Gérer des contrats en utilisant la solution Microsoft 365](solution-manage-contracts-in-microsoft-365.md)
