---
title: Scénarios et cas d’usage pour Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: laurieellis
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
description: Trouvez des scénarios sur l’utilisation des SharePoint Syntex dans votre organisation.
ms.openlocfilehash: 619acd5d71bc6f3ab1aa99d3b7fd068faa51d696
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59175756"
---
# <a name="scenarios-and-use-cases-for-microsoft-sharepoint-syntex"></a>Scénarios et cas d’usage pour Microsoft SharePoint Syntex

Utilisez les exemples de scénarios suivants pour vous faire des idées sur la façon dont vous pouvez SharePoint Syntex dans votre organisation.

- [Scénario : suivre les données des factures avec le traitement du formulaire](adoption-scenarios.md#scenario-track-data-from-invoices-with-form-processing)
- [Scénario : suivre les informations des contrats avec la compréhension des documents](adoption-scenarios.md#scenario-track-information-from-contracts-with-document-understanding)
- [Scénario : éviter les risques avec la gestion des enregistrements, la gouvernance des documents et les processus de conformité basés sur SharePoint Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex)
- [Scénario : capturer des informations à partir de documents précédemment inaccessibles](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Scénario : améliorer le traitement des données pour fournir des informations et des analyses](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Scénario : automatiser le traitement des commandes](adoption-scenarios.md#scenario-automate-order-processing)
- [Scénario : simplifier le processus de renouvellement du visa](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-data-from-invoices-with-form-processing"></a>Scénario : suivre les données des factures avec le traitement du formulaire

Par exemple, vous pouvez configurer un processus à l’aide SharePoint Syntex et Power Automate pour suivre et surveiller les factures.

1. Configurer une bibliothèque pour stocker les documents de facture.
1. Formez le modèle pour reconnaître les champs dans les documents.
1. Extrayez les champs que vous souhaitez suivre dans une liste.
1. Configurer un flux pour vous notifier d’événements spécifiques, tels que :
    - Une nouvelle facture est ajoutée.
    - La date d’échéance d’une facture est passée.
    - Une facture est pour un montant supérieur à votre montant d’approbation automatique.

![Suivez et surveillez les factures avec SharePoint Syntex et Power Automate.](../media/content-understanding/process-invoices-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des factures au lieu de les faire manuellement.
- Réduisez les erreurs potentielles et assurez-vous d’une meilleure conformité à l’aide de flux de travail pour vérifier les factures et vous informer des problèmes éventuels.

## <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Scénario : suivre les informations des contrats avec la compréhension des documents

Par exemple, vous pouvez configurer un processus pour identifier les contrats que votre entreprise a avec d’autres sociétés ou individus. Configurer un modèle pour extraire des informations clés de ces contrats, telles que le nom du client, les frais, les dates ou d’autres informations importantes, et ajouter les informations à la bibliothèque en tant que champs que vous pouvez rapidement afficher. Appliquez une étiquette de rétention à la bibliothèque de documents pour vous assurer que les contrats ne peuvent pas être supprimés avant une durée spécifique afin de respecter les réglementations de votre entreprise.

1. Commencez au centre de contenu et créez un modèle de compréhension des documents pour les contrats.
1. Télécharger exemples de documents pour des exemples positifs et négatifs, puis exécutez la formation pour identifier les documents de contrat et passer en revue les résultats.
1. Formez l’extracteur pour identifier les champs dans les contrats, tels que le nom du client, les frais et la date, puis testez l’extracteur.
1. Une fois le modèle terminé, appliquez-le à une bibliothèque dans laquelle vous pouvez télécharger des contrats.
1. Appliquez une étiquette de rétention au champ date, afin que les contrats soient conservés dans la bibliothèque pendant la durée requise.

![Suivre et surveiller les contrats avec les étiquettes SharePoint Syntex rétention.](../media/content-understanding/process-contracts-flow.png)

Lorsque vous automatisez ce scénario, vous pouvez :

- Gagnez du temps et de l’argent en extrayant automatiquement les données des contrats au lieu de les faire manuellement.
- Assurez-vous d’une meilleure conformité en utilisant des étiquettes de rétention pour vous assurer que les contrats sont conservés de manière appropriée.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex"></a>Scénario : éviter les risques avec la gestion des enregistrements, la gouvernance des documents et les processus de conformité basés sur SharePoint Syntex

La réduction des risques est un objectif commun pour la plupart des entreprises. Vous devrez peut-être :

- Un meilleur moyen de fournir/appliquer la gouvernance des informations au sein de votre client.
- Pour améliorer le système de classification des documents, des e-mails et d’autres formes de communication considérées comme des « enregistrements » pour les projets.
- Pour auditer les reçus, les contrats, etc., afin de garantir la conformité avec les stratégies de l’entreprise.
- Pour vous assurer que les projets ont toute la documentation requise pour la conformité.

Configurer certains processus de conformité avec les SharePoint Syntex pour capturer et classer, auditer et indicateurr correctement les documents et formulaires qui ont besoin d’une meilleure gouvernance. Vous pouvez vous appuyer sur SharePoint Syntex pour classer automatiquement le contenu au lieu de compter sur les utilisateurs finaux pour baliser manuellement, ou sur l’équipe de conformité pour appliquer manuellement les règles de gouvernance et l’archivage. Vous pouvez également activer une expérience de recherche simplifiée, gérer les volumes de données, appliquer des stratégies de gestion et de rétention des enregistrements, garantir la conformité, ainsi que les pratiques d’archivage et de purge des meilleures pratiques.

Lorsque vous automatisez ce scénario, vous pouvez être sûr que :

- La conformité est maintenue et les risques sont réduits.
- La taxonomie et la gestion des enregistrements sont appliquées de façon cohérente et précise.
- Les volumes de contenu sont contrôlés.
- Les employés peuvent facilement découvrir les bonnes informations dans le bon contexte.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scénario : capturer des informations à partir de documents précédemment inaccessibles

La plupart des organisations ont de grands référentiels de documents juridiques, de stratégies, de contrats, de documents RH et de directives de gouvernance. Exploitation de ces magasins de données pour extraire des informations précieuses telles que : projets, secteurs, thèmes, personnes, zones géographiques, etc.

Par exemple, un directeur RH doit accéder rapidement à tous les documents RH, y compris les CV, les stratégies RH et d’autres formulaires. Ils souhaitent également identifier rapidement les informations nécessaires à partir des CV et d’autres documents liés aux ressources humaines sans passer manuellement au travers des documents. Ils recherchent une solution qui leur permet de trouver rapidement les informations dont ils ont besoin sans avoir à examiner manuellement des milliers de CV, de stratégies RH et d’autres documents qui peuvent être répartis sur plusieurs sites.

Lorsque vous automatisez ce scénario, vous pouvez :

- Déverrouillez les connaissances du contenu numérique.
- Classifier les stratégies RH, cv, documents commerciaux, plans techniques, plans de compte et extraire des informations.
- Recherchez rapidement les informations ou le document que vous recherchez.
- Obtenez un accès instantané aux dernières informations.
- Réduisez les temps de recherche.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Scénario : améliorer le traitement des données pour fournir des informations et des analyses

Par exemple, une société de petite entreprise peut utiliser SharePoint Syntex pour extraire des informations à partir de documents FDA afin de répondre aux questions de leurs responsables. Le fait d’avoir les réponses plus facilement accessibles peut réduire le temps nécessaire pour produire ces réponses et augmenter la disponibilité des données afin de générer des réponses plus précises aux questions de direction.

Par exemple, un responsable de projet doit fournir rapidement des réponses aux questions relatives aux produits de mon équipe de direction. Ils doivent trouver des informations et des mesures relatives aux requêtes dans un tableau de bord consolidé. Ils recherchent une solution qui extrait les informations dont ils ont besoin à partir d’étiquettes de produits, de publications de produits et d’autres documents, et génère un rapport consolidé qu’ils peuvent utiliser lorsqu’ils font des rapports à leur équipe de direction.

Lorsque vous automatisez ce scénario, vous pouvez :

- Réduisez le temps de produire des réponses.
- Augmenter la disponibilité des données.
- Fournir des réponses plus précises.

## <a name="scenario-automate-order-processing"></a>Scénario : automatiser le traitement des commandes

Avec SharePoint Syntex, vous pouvez réduire le temps de traitement manuel des commandes client. Par exemple, vous pouvez charger des commandes de télécopie, de courrier électronique ou de papier dans SharePoint à l’aide du traitement ocr, puis extraire les métadonnées de ces commandes afin de pouvoir les traiter à l’aide de processus automatisés.

Par exemple, un responsable de la chaîne d’approvisionnement souhaite réduire les erreurs provoquées par l’entrée manuelle des données. Ils souhaitent éviter la révision manuelle et l’entrée de données des commandes client entrantes (papier, télécopie ou courrier électronique) afin de réduire les erreurs entrantes dans leurs systèmes d’entreprise. Ils souhaitent une solution qui applique des techniques d’IA et d’apprentissage automatique pour valider les informations de commande entrantes, extraire les données de base et les pousser automatiquement dans leur système ERP, pour l’traitement des commandes et le rapprochement.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- La précision de la commande et de l’expédition augmente.
- Les frais ou les pénalités associés aux erreurs de commande ou d’expédition sont réduits.
- Les retards de facturation ou de paiement diminuent.
- Les coûts de personnel sont réduits.

## <a name="scenario-simplify-visa-renewal-process"></a>Scénario : simplifier le processus de renouvellement du visa

SharePoint Syntex pouvez vous aider à automatiser les rappels et les renouvellements pour les informations clés du contrat. Par exemple, un directeur RH doit s’assurer que les visas des employés sont à jour et/ou renouvelés à temps. Ils souhaitent offrir aux utilisateurs un processus simple et intuitif pour la mise à jour de leur visa. Ils ont besoin d’une solution qui extrait les dates de renouvellement des contrats et envoie automatiquement des rappels aux employés lorsque leurs dates de renouvellement approchent.

Lorsque vous automatisez ce scénario, vous pouvez vous assurer que :

- Les niveaux de non-conformité sont réduits.
- Le nombre de rappels manuels est réduit.
- Le nombre d’amendes pour non-conformité est réduit.

## <a name="see-also"></a>Voir aussi

[Adoption SharePoint Syntex Microsoft : commencer](adoption-getstarted.md)