---
title: Passer en revue les conversations dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez la fonctionnalité de reconstruction de conversation dans Advanced eDiscovery (thread de conversation) pour reconstruire, examiner et exporter des conversations dans des groupes Microsoft Teams et Yammer conversation.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: b726c09e1e88fb86db7d2fcf5994d6643d6922838388335ef7fd60ad31d10493
ms.sourcegitcommit: 4f074a8598a430344a2361728a64b8b8c0e1d215
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2021
ms.locfileid: "54523608"
---
# <a name="conversation-threading-in-advanced-ediscovery"></a>Threads de conversation dans Advanced eDiscovery

La messagerie instantanée est un moyen pratique de poser des questions, de partager des idées ou de communiquer rapidement entre de larges publics. Comme les plateformes de messagerie instantanée, telles que les groupes Microsoft Teams et Yammer, deviennent essentielles à la collaboration d’entreprise, les organisations doivent évaluer la façon dont leur flux de travail eDiscovery traite ces nouvelles formes de communication et de collaboration.

La fonctionnalité de reconstruction de conversation Advanced eDiscovery est conçue pour vous aider à identifier le contenu contextuel et à produire des vues de conversation distinctes. Cette fonctionnalité vous permet de passer en revue efficacement et rapidement les conversations de messagerie instantanée complètes (également appelées *conversations* threadées) générées sur des plateformes telles que Microsoft Teams.

Avec la reconstruction de conversation, vous pouvez utiliser les fonctionnalités intégrées pour reconstruire, examiner et exporter des conversations threadées. Utilisez la reconstruction Advanced eDiscovery conversation pour :

- Conserver des métadonnées de niveau message uniques dans tous les messages d’une conversation.

- Collectez des messages contextuels autour de vos résultats de recherche.

- Passer en revue, annoter et redessier des conversations threadées.

- Exporter des messages individuels ou des conversations threadées

## <a name="terminology"></a>Terminologie

Voici quelques définitions pour vous aider à commencer à utiliser la reconstruction de conversation.

- **Messages :** Représente la plus petite unité d’une conversation. La taille, la structure et les métadonnées des messages peuvent varier.

- **Conversation :** Représente un regroupement d’un ou plusieurs messages. Dans différentes applications, les conversations peuvent être représentées de différentes manières. Dans certaines applications, il existe une action explicite qui résulte de la réponse à un message existant. Les conversations sont formées explicitement à la suite de cette action de l’utilisateur. Par exemple, voici une capture d’écran d’une conversation de canal dans Microsoft Teams.

   ![Microsoft Teams Conversation de canal](../media/threadedchat.png)

   Dans d’autres applications (telles que les messages de conversation de groupe dans Teams), il n’existe pas de chaîne de réponse formelle et les messages apparaissent plutôt comme une « série plate de messages » au sein d’un thread unique. Dans ces types d’applications, les conversations sont déduites d’un groupe de messages qui se produisent dans un certain temps. Ce « groupement souple » de messages (par opposition à une chaîne de réponse) représente la conversation « va-et-vient » sur un sujet spécifique.

## <a name="step-1-create-a-draft-collection"></a>Étape 1 : Créer un brouillon de collection

Une fois que vous avez identifié les dépositaires et les emplacements de contenu pertinents, vous pouvez créer une recherche pour rechercher du contenu potentiellement pertinent. Sous **l’onglet Collections** du Advanced eDiscovery, vous pouvez créer une collection en cliquant sur **Nouvelle collection** et en suivant l’Assistant. Pour plus d’informations sur la création d’une collection, la création d’une requête de recherche et l’aperçu des résultats de la recherche, voir [Créer un brouillon de collection.](create-draft-collection.md)

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Étape 2 : Valider un brouillon de collection dans un jeu à réviser

Après avoir examiné et finalisé la requête de recherche dans une collection, vous pouvez ajouter les résultats de la recherche à un jeu à réviser. Lorsque vous ajoutez vos résultats de recherche dans un jeu à réviser, les données d’origine sont copiées dans une zone stockage Azure pour faciliter le processus de révision et d’analyse. Pour plus d’informations sur l’ajout de résultats de recherche à un jeu à réviser, voir Valider un [brouillon de collection dans un jeu à réviser.](commit-draft-collection.md)

Lorsque vous ajoutez des éléments de conversations à un jeu à réviser, vous pouvez utiliser l’option de conversations threadées pour collecter des messages contextuels à partir de conversations qui contiennent des éléments qui correspondent aux critères de recherche de la collection. Une fois que vous avez sélectionné l’option conversations de thread, les choses suivantes peuvent se produire :

  ![Récupération de conversation](../media/messagesandconversations.png)

1. À l’aide d’une requête de mot clé et de plage de dates, la recherche a renvoyé un succès sur *le message 3*. Ce message faisait partie d’une conversation plus importante, illustrée par *CRC1*.

2. Lorsque vous ajoutez les données dans un jeu à réviser et activez les options de récupération de conversation, Advanced eDiscovery revenir en arrière et collecter d’autres éléments dans *CRC1*.

3. Une fois que les éléments ont été ajoutés au jeu à réviser, vous pouvez passer en revue tous les messages individuels à partir *de CRC1*.

Pour activer l’option de conversations threadées, voir [Valider un brouillon de collection dans un jeu à réviser.](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set)

## <a name="step-3-review-and-export-threaded-conversations"></a>Étape 3 : Examiner et exporter des conversations threadées

Une fois que le contenu a été traitée et ajoutée au jeu à réviser, vous pouvez commencer à examiner les données du jeu à réviser. Les messages individuels sont threadés ensemble et présentés en tant que conversations. Cela vous permet de passer en revue et d’exporter des conversations contextuelles.

  ![Ensemble de révision de conversation](../media/ConversationRSOptions.PNG)

Les sections suivantes décrivent l’examen et l’exportation des conversations.

### <a name="reviewing-conversations"></a>Examen des conversations

Dans un jeu à réviser, vous pouvez utiliser les options suivantes pour faciliter le processus de révision.

- **Grouper par conversation :** Groupe les messages au sein d’une même conversation pour aider les utilisateurs à simplifier et accélérer leur processus de révision.

- **Vue récapitulatif :** Affiche la conversation threadée. Dans cette vue, vous pouvez voir la conversation entière et accéder aux métadonnées de chaque message individuel.

   - Afficher les métadonnées des messages individuels

   - Télécharger des messages individuels

- **Affichage texte :** Fournit le texte extrait pour l’intégralité de la conversation.

- **Affichage annoter :** Vous permet de marquer un affichage thread de la conversation. Tous les messages de la conversation partagent le même document annoté.

- **Marquage :** Lorsque vous visualisez des conversations dans un jeu  à réviser, vous pouvez afficher et appliquer des balises en cliquant sur le panneau marquage dans le panneau de codage.

- **Réexécutez la conversion de conversation :** Lorsque des messages sont ajoutés à un groupe de révision de conversation, un travail de conversion est automatiquement exécuté pour créer le résumé de thread et annoter des affichages. Si le travail de reconstruction de conversation échoue, vous pouvez réexécuter ce travail en cliquant sur Action > créer des **PDF** de conversation dans le jeu à réviser.

### <a name="exporting-conversations"></a>Exportation de conversations

Pour les options que vous pouvez sélectionner lors de l’exportation de conversations à partir d’un jeu à réviser, voir [Exporter des documents à partir d’un jeu à réviser.](export-documents-from-review-set.md#export-options)

Plus précisément, vous pouvez exporter des conversations de conversation entières dans un fichier PDF unique ou vous pouvez exporter chaque message de conversation d’une conversation en tant que fichier individuel.

## <a name="more-information"></a>Informations supplémentaires

Pour en savoir plus sur l’examen des données de cas dans Advanced eDiscovery, consultez les articles suivants :

- [Interroger et filtrer du contenu dans un jeu à réviser](review-set-search.md)
- [Étiqueter les documents d’un jeu à réviser](tagging-documents.md)
- [Afficher les données de cas](view-documents-in-review-set.md)
- [Analyser les données de cas](analyzing-data-in-review-set.md)
- [Exporter les données de cas](exporting-data-ediscover20.md)
