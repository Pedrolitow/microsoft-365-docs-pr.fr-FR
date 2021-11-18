---
title: Analyser les données d’un jeu à réviser dans Advanced eDiscovery
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
description: Découvrez les outils disponibles pour organiser les ensembles de documents lors de l’analyse Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: dc1bd7b8a717d5f53514209fe50499844644f27b
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2021
ms.locfileid: "61064462"
---
# <a name="analyze-data-in-a-review-set-in-advanced-ediscovery"></a>Analyser les données d’un jeu à réviser dans Advanced eDiscovery

Lorsque le nombre de documents collectés est élevé, il peut être difficile de les examiner tous. Advanced eDiscovery fournit un certain nombre d’outils pour analyser les documents afin de réduire le volume de documents à examiner sans perte d’informations et pour vous aider à organiser les documents de manière cohérente. Pour en savoir plus sur ces fonctionnalités, voir :

- [Détecter des quasi-duplicatas](near-duplicate-detection-in-advanced-ediscovery.md)

- [Threading de messagerie](email-threading-in-advanced-ediscovery.md)

- [Thèmes](themes-in-advanced-ediscovery.md)

## <a name="run-analytics-for-a-review-set"></a>Exécuter l’analyse pour un jeu à réviser

Pour analyser les données d’un jeu à réviser :

1. Configurez les paramètres d’analyse pour votre cas. Pour plus d’informations, voir Configurer les paramètres de recherche [et d’analyse.](configure-search-and-analytics-settings-in-advanced-ediscovery.md)

2. Ouvrez le jeu à réviser que vous souhaitez analyser.

3. Cliquez **sur Exécuter** le document  >  **d’analyse &'analyse de courrier électronique.**

   ![Select Run document & email analytics from the Analytics dropdown list](..\media\RunAnalytics1.png)

Vous pouvez vérifier la progression de l’analyse sous **l’onglet Travaux** du cas.

 Une fois l’analyse terminée, vous pouvez afficher le rapport d’analyse, exécuter des requêtes dans votre jeu à réviser sur les sorties de l’analyse (voir Requête dans votre jeu à [réviser)](review-set-search.md)et voir les documents associés d’un document donné (voir Données de révision dans le jeu à [réviser).](reviewing-data-in-review-set.md)

## <a name="using-the-for-review-filter-query"></a>Utilisation de la requête filtre Pour révision

Après avoir lancé l’analyse pour le jeu à réviser, vous pouvez utiliser une requête de filtre générée automatiquement (appelée Pour *révision)* qui filtre votre avis afin d’exclure les éléments immatéraux, en double ou non inclus. Vous n’avez ainsi que les éléments représentatifs, uniques et inclus dans l’ensemble de révision.

Pour appliquer la **requête** filtre Pour révision à  un jeu à réviser, sélectionnez la liste de listes de listes des requêtes de filtre enregistrées, puis sélectionnez **\[ AutoGen] Pour révision.**

![Select For Review from the Saved filter queries dropdown list](..\media\ForReviewFilterQuery1.png)

Voici la syntaxe de la requête **de** filtre Pour révision :

`(((FileClass="Email") AND (InclusiveType="InclusiveMinus" OR InclusiveType="Inclusive")) OR ((FileClass="Attachment") AND (UniqueInEmailSet="true")) OR ((FileClass="Document") AND (MarkAsRepresentative="Unique")) OR (FileClass="Conversations"))`

La liste suivante décrit le résultat de la requête de filtre en termes de contenu affiché une fois que vous l’avez appliqué au jeu à réviser.

- **E-mail**. Affiche les éléments marqués comme **inclusive** ou **InclusiveMinus**. Un élément inclus est le message final dans un thread de messagerie. Il contient tout le contenu précédent dans le thread de messagerie. Inclus moins il contient une ou plusieurs pièces jointes associées au message spécifique dans le thread de messagerie. Un réviseur peut utiliser la valeur moins inclusive pour déterminer quels messages spécifiques du thread de messagerie ont des pièces jointes associées.

- **Pièces jointes**. Filtre les pièces jointes en double dans le même ensemble de messages électroniques. Seules les pièces jointes qui sont uniques dans un thread de messagerie électronique sont affichées.

- **Documents et autres**. Filtre les documents en double. Seuls les documents qui sont uniques dans le jeu à réviser sont affichés.

- **Teams conversations.** Toutes les Teams (et les Yammer) du jeu à réviser sont affichées.

Pour plus d’informations sur les types d’inclusion et l’unicité des documents, voir [Threads](email-threading-in-advanced-ediscovery.md)de messagerie dans Advanced eDiscovery .

> [!NOTE]
> Lors de la prévisualisation publique du format  grand cas en [Advanced eDiscovery,](advanced-ediscovery-large-cases.md)la requête de filtre Pour révision n’a pas renvoyé de conversations Teams ou Yammer pour les ensembles de révision (dans les cas qui utilisent le format grand cas) créés avant le 4 novembre 2021. Ce problème a été résolu. Cela signifie que si  vous réappliquez la requête Pour révision à un groupe de révision dans un cas qui utilise le format grand cas, davantage d’éléments qui correspondent à la requête de filtre peuvent être affichés, car toutes les conversations Teams ou Yammer sont incluses.

## <a name="analytics-report"></a>Rapport d’analyse

Pour afficher le rapport d’analyse d’un jeu à réviser :

1. Ouvrez le jeu à réviser.

2. Cliquez **sur Afficher** les rapports  >  **d’analyse.**

Le **rapport d’analyse** possède sept composants issus de l’analyse :

- **Population cible :** Nombre de messages électroniques, pièces jointes et documents libres trouvés dans le jeu à réviser.

- **Documents (à l’exclusion des pièces jointes) :** Nombre de documents libres qui sont des tableaux croisés dynamiques, des doublons proches uniques d’un tableau croisé dynamique ou un doublon exact d’un autre document.

- **E-mails :** Nombre de messages électroniques marqués comme étant inclus, inclus, moins ou aucun des messages ci-dessus.

- **Pièces jointes :** Nombre de pièces jointes qui sont uniques ou dupliquées d’une autre pièce jointe dans le jeu à réviser.

- **Nombre de documents par type de fichier :** Nombre de fichiers, identifié par l’extension de fichier.

- **Documents par source :** Résumé du contenu par sa source de données d’origine.

- **Documents agrégés par processus :** Résumé du contenu par processus d’ensemble de révision. 
