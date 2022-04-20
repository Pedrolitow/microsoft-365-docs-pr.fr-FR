---
title: Analyser les données d’un ensemble de révisions dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez les outils disponibles pour organiser les ensembles de documents lors de l’analyse d’un cas de découverte électronique (Premium) Microsoft Purview.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c12b71d4bc2ddbf39df4e9414689cafeb4f4f785
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935695"
---
# <a name="analyze-data-in-a-review-set-in-ediscovery-premium"></a>Analyser les données d’un ensemble de révisions dans eDiscovery (Premium)

Lorsque le nombre de documents collectés est important, il peut être difficile de les examiner tous. Microsoft Purview eDiscovery (Premium) fournit un certain nombre d’outils pour analyser les documents afin de réduire le volume de documents à examiner sans perte d’informations et pour vous aider à organiser les documents de manière cohérente. Pour en savoir plus sur ces fonctionnalités, consultez :

- [Détecter des quasi-duplicatas](near-duplicate-detection-in-advanced-ediscovery.md)

- [Threading de messagerie](email-threading-in-advanced-ediscovery.md)

- [Thèmes](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Exécuter l’analytique pour un ensemble de révisions

Pour analyser les données d’un jeu de révision :

1. Configurez les paramètres d’analytique pour votre cas. Pour plus d’informations, consultez [Configurer les paramètres de recherche et d’analytique](configure-search-and-analytics-settings-in-advanced-ediscovery.md).

2. Ouvrez l’ensemble de révisions à analyser.

3. Cliquez sur Le document **AnalyticsRun** >  **& l’analyse des e-mails**.

   ![Sélectionnez Exécuter le document & l’analyse des e-mails dans la liste déroulante Analytics](..\media\RunAnalytics1.png)

Vous pouvez vérifier la progression de l’analyse sous l’onglet **Travaux** du cas.

 Une fois l’analyse terminée, vous pouvez afficher le rapport d’analyse, exécuter des requêtes dans votre ensemble de révisions sur les sorties de l’analyse (voir [Requête dans votre jeu de révisions](review-set-search.md) et voir les documents connexes d’un document donné (voir [Passer en revue les données dans l’ensemble de révisions](reviewing-data-in-review-set.md)).

## <a name="using-the-for-review-filter-query"></a>Utilisation de la requête de filtre De révision

Après avoir exécuté l’analytique pour le jeu de révisions, vous pouvez utiliser une requête de filtre générée automatiquement (appelée *Révision*) qui filtre votre révision pour exclure les éléments immatériaux, dupliqués ou non inclusifs. Vous disposez ainsi uniquement des éléments représentatifs, uniques et inclusifs dans l’ensemble de révisions.

Pour appliquer la requête de filtre **De révision** à un ensemble de révisions, sélectionnez la liste **déroulante des requêtes de filtre enregistrées** , puis sélectionnez **\[AutoGen] Pour révision**.

![Sélectionner pour révision dans la liste déroulante Requêtes de filtre enregistrées](..\media\ForReviewFilterQuery1.png)

Voici la syntaxe de la requête de filtre **For Review** :

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

La liste suivante décrit le résultat de la requête de filtre en termes de contenu affiché après l’avoir appliqué au jeu de révision.

- **E-mail**. Affiche les éléments marqués comme **Inclusive** ou **InclusiveMinus**. Un élément inclusif est le dernier message d’un thread de messagerie. Il contient tout le contenu précédent dans le thread d’e-mail. Inclus moins qu’il contient une ou plusieurs pièces jointes associées au message spécifique dans le thread d’e-mail. Un réviseur peut utiliser la valeur inclusive moins pour déterminer quels messages spécifiques du thread de messagerie ont des pièces jointes associées.

- **Pièces jointes**. Filtre les pièces jointes en double dans le même jeu de courriers électroniques. Seules les pièces jointes uniques dans un thread de messagerie sont affichées.

- **Documents et autres**. Filtre les documents en double. Seuls les documents qui sont uniques dans l’ensemble de révisions sont affichés.

- **Teams conversations**. Toutes les conversations Teams (et Yammer) dans le jeu de révision sont affichées.

Pour plus d’informations sur les types inclusifs et l’unicité des documents, consultez [threading e-mail dans eDiscovery (Premium)](email-threading-in-advanced-ediscovery.md).

> [!NOTE]
> Pendant la préversion publique [du nouveau format de cas](advanced-ediscovery-new-case-format.md) dans eDiscovery (Premium), la requête de filtre **For Review** n’a pas retourné Teams ou Yammer conversations pour les jeux de révision (dans les cas qui utilisent le format de cas volumineux) créées avant le 4 novembre 2021. Ce problème a été résolu. Cela signifie que si vous réappliquez la requête **For Review** à un ensemble de révisions dans un cas qui utilise le format de cas volumineux, d’autres éléments correspondant à la requête de filtre peuvent être affichés, car toutes les conversations Teams ou Yammer sont incluses.

## <a name="analytics-report"></a>Rapport d’analyse

Pour afficher le rapport d’analyse d’un ensemble de révisions :

1. Ouvrez le jeu de révisions.

2. Cliquez sur **Rapports AnalyticsShow** > .

Le rapport **Analytics** comporte sept composants de l’analyse :

- **Population cible :** Nombre d’e-mails, de pièces jointes et de documents non disponibles trouvés dans l’ensemble de révisions.

- **Documents (à l’exception des pièces jointes) :** Nombre de documents libres qui sont des tableaux croisés dynamiques, des doublons uniques proches d’un tableau croisé dynamique ou un doublon exact d’un autre document.

- **E-mails:** Nombre de messages électroniques marqués comme une copie inclusive, inclusive, inclusive moins, ou aucun des messages ci-dessus.

- **Pièces jointes:** Nombre de pièces jointes qui sont uniques ou dupliquées d’une autre pièce jointe dans l’ensemble de révision.

- **Nombre de documents par type de fichier :** Nombre de fichiers identifiés par extension de fichier.

- **Documents par source :** Récapitulatif du contenu par sa source de données d’origine.

- **Documents agrégés par processus :** Récapitulatif du contenu par processus d’ensemble de révision. 
