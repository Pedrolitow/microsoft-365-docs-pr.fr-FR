---
title: Passer en revue les conversations dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
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
description: Découvrez la fonctionnalité de reconstruction de conversation dans Microsoft Purview eDiscovery (Premium) (appelée thread de conversation) pour reconstruire, examiner et exporter des conversations de conversation dans des groupes Microsoft Teams et Yammer.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 5b5c56bd64041523b5fcbae8ddd741f99dac8e8a
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67821338"
---
# <a name="conversation-threading-in-ediscovery-premium"></a>Thread de conversation dans eDiscovery (Premium)

La messagerie instantanée est un moyen pratique de poser des questions, de partager des idées ou de communiquer rapidement au sein d’un large public. Comme les plateformes de messagerie instantanée, comme les groupes Microsoft Teams et Yammer, deviennent essentielles à la collaboration d’entreprise, les organisations doivent évaluer la façon dont leur flux de travail eDiscovery résout ces nouvelles formes de communication et de collaboration.

La fonctionnalité de reconstruction de conversation dans Microsoft Purview eDiscovery (Premium) est conçue pour vous aider à identifier le contenu contextuel et à produire des vues de conversation distinctes. Cette fonctionnalité vous permet d’examiner efficacement et rapidement les conversations de messages instantanés complètes (également appelées *conversations thread*) générées dans des plateformes telles que Microsoft Teams.

Avec la reconstruction de conversation, vous pouvez utiliser des fonctionnalités intégrées pour reconstruire, examiner et exporter des conversations thread. Utilisez la reconstruction de conversation eDiscovery (Premium) pour :

- Conservez les métadonnées uniques au niveau du message dans tous les messages d’une conversation.

- Collectez des messages contextuels autour de vos résultats de recherche.

- Passez en revue, annotez et répétez les conversations thread.

- Exporter des messages individuels ou des conversations thread

## <a name="terminology"></a>Terminologie

Voici quelques définitions pour vous aider à commencer à utiliser la reconstruction de conversation.

- **Messages:** Représente la plus petite unité d’une conversation. La taille, la structure et les métadonnées des messages peuvent varier.

- **Conversation:** Représente un regroupement d’un ou plusieurs messages. Dans différentes applications, les conversations peuvent être représentées de différentes manières. Dans certaines applications, il existe une action explicite qui résulte de la réponse à un message existant. Les conversations sont formées explicitement à la suite de cette action de l’utilisateur. Par exemple, voici une capture d’écran d’une conversation de canal dans Microsoft Teams.

   ![Conversation de canal Microsoft Teams.](../media/threadedchat.png)

   Dans d’autres applications (par exemple, les messages de conversation de groupe dans Teams), il n’existe pas de chaîne de réponse formelle et les messages apparaissent à la place comme un « fleuve plat de messages » au sein d’un thread unique. Dans ces applications de types, les conversations sont déduites d’un groupe de messages qui se produisent dans un certain temps. Ce « regroupement souple » de messages (par opposition à une chaîne de réponse) représente la conversation « aller et retour » sur un sujet spécifique qui l’intéresse.

## <a name="step-1-create-a-draft-collection"></a>Étape 1 : Créer un brouillon de collection

Une fois que vous avez identifié les consignats et les emplacements de contenu pertinents, vous pouvez créer une recherche pour rechercher du contenu potentiellement pertinent. Sous l’onglet **Collections** dans le cas eDiscovery (Premium), vous pouvez créer une collection en cliquant sur **Nouvelle collection** et en suivant l’Assistant. Pour plus d’informations sur la façon dont vous pouvez créer une collection, créer une requête de recherche et afficher un aperçu des résultats de la recherche, consultez [Créer un brouillon de collection](create-draft-collection.md).

## <a name="step-2-commit-a-draft-collection-to-a-review-set"></a>Étape 2 : Valider un brouillon de collection dans un ensemble de révisions

Une fois que vous avez examiné et finalisé la requête de recherche dans une collection, vous pouvez ajouter les résultats de la recherche à un ensemble de révisions. Lorsque vous ajoutez vos résultats de recherche dans un jeu de révision, les données d’origine sont copiées dans une zone de stockage Azure pour faciliter le processus de révision et d’analyse. Pour plus d’informations sur l’ajout de résultats de recherche à un ensemble de révisions, consultez [Commit a draft collection to a review set](commit-draft-collection.md).

Lorsque vous ajoutez des éléments de conversations à un ensemble de révisions, vous pouvez utiliser l’option conversations thread pour collecter des messages contextuels à partir de conversations qui contiennent des éléments qui correspondent aux critères de recherche de la collection. Une fois que vous avez sélectionné l’option de conversation de thread, les événements suivants peuvent se produire :

  ![Récupération de conversation.](../media/messagesandconversations.png)

1. À l’aide d’un mot clé et d’une requête de plage de dates, la recherche a retourné une correspondance sur *message 3*. Ce message faisait partie d’une conversation plus large, illustrée par *CRC1*.

2. Lorsque vous ajoutez les données dans un jeu de révision et activez les options de récupération de conversation, eDiscovery (Premium) revient en arrière et collecte d’autres éléments dans *CRC1*.

3. Une fois que les éléments ont été ajoutés au jeu de révision, vous pouvez passer en revue tous les messages individuels de *CRC1*.

Pour activer l’option conversations thread, consultez [Valider un brouillon de collection dans un ensemble de révisions](commit-draft-collection.md#commit-a-draft-collection-to-a-review-set).

## <a name="step-3-review-and-export-threaded-conversations"></a>Étape 3 : Examiner et exporter des conversations thread

Une fois que le contenu a été traité et ajouté au jeu de révision, vous pouvez commencer à examiner les données du jeu de révision. Les messages individuels sont threadés ensemble et présentés en tant que conversations. Cela vous permet d’examiner et d’exporter des conversations contextuelles.

  ![Ensemble de révisions de conversation.](../media/ConversationRSOptions.PNG)

Les sections suivantes décrivent l’examen et l’exportation des conversations.

### <a name="reviewing-conversations"></a>Examen des conversations

Dans un ensemble de révisions, vous pouvez utiliser les options suivantes pour faciliter le processus de révision.

- **Regrouper par conversation :** Regroupe les messages dans la même conversation pour aider les utilisateurs à simplifier et à accélérer leur processus de révision.

- **Vue récapitulative :** Affiche la conversation thread. Dans cette vue, vous pouvez voir l’intégralité de la conversation et accéder aux métadonnées pour chaque message individuel.

   - Afficher les métadonnées des messages individuels

   - Télécharger des messages individuels

- **Affichage texte :** Fournit le texte extrait pour l’ensemble de la conversation.

- **Annoter la vue :** Vous permet de marquer une vue thread de la conversation. Tous les messages de la conversation partagent le même document annoté.

- **Marquage:** Lorsque vous affichez des conversations dans un ensemble de révisions, vous pouvez afficher et appliquer des balises en cliquant sur **le panneau De balisage** dans le panneau de codage.

- **Réexécuter la conversion de conversation :** Lorsque des messages sont ajoutés à un jeu de révision de conversation, un travail de conversion est exécuté automatiquement pour créer le résumé thread et annoter les vues. Si le travail de reconstruction de conversation échoue, vous pouvez réexécuter ce travail en cliquant sur **Action > Créer des fichiers PDF de conversation** dans le jeu de révision.

### <a name="exporting-conversations"></a>Exportation de conversations

Pour connaître les options que vous pouvez sélectionner lors de l’exportation de conversations à partir d’un ensemble de révisions, consultez [Exporter des documents à partir d’un ensemble de révisions](export-documents-from-review-set.md#export-options).

Plus précisément, vous pouvez exporter des conversations de conversation entières dans un fichier PDF unique ou exporter chaque message de conversation dans une conversation en tant que fichier individuel.

## <a name="more-information"></a>Plus d’informations

Pour en savoir plus sur la façon de passer en revue les données de cas dans eDiscovery (Premium), consultez les articles suivants :

- [Interroger et filtrer du contenu dans un jeu à réviser](review-set-search.md)
- [Étiqueter les documents d’un jeu à réviser](tagging-documents.md)
- [Afficher les données de cas](view-documents-in-review-set.md)
- [Analyser les données de cas](analyzing-data-in-review-set.md)
- [Exporter les données de cas](exporting-data-ediscover20.md)
