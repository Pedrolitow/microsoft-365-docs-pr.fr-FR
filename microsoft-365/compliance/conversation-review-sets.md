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
description: Découvrez comment utiliser la fonctionnalité reconstruction de conversation dans Advanced eDiscovery pour reconstruire, réviser et exporter des conversations threadées.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: bf5c39f567240b58546dbeb353e3e461e9b69e48
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358342"
---
# <a name="review-conversations-in-advanced-ediscovery"></a>Passer en revue les conversations dans Advanced eDiscovery 

La messagerie instantanée est un moyen pratique de poser des questions, de partager des idées ou de communiquer rapidement entre de larges publics. Comme les plateformes de messagerie instantanée, telles que Microsoft Teams, sont essentielles à la collaboration d’entreprise, les organisations doivent évaluer la façon dont leur flux de travail eDiscovery traite ces nouvelles formes de communication et de collaboration. 

La fonctionnalité reconstruction de conversation dans Advanced eDiscovery est conçue pour vous aider à identifier le contenu contextuel et à produire des vues de conversation distinctes. Cette fonctionnalité vous permet de passer en revue efficacement et rapidement les conversations par message instantané (également appelées *conversations* threadées) générées sur des plateformes telles que Microsoft Teams.

Avec la reconstruction de conversation, vous pouvez utiliser les fonctionnalités intégrées pour reconstruire, réviser et exporter des conversations threadées. Utilisez la reconstruction de conversation Advanced eDiscovery pour :

- Conserver des métadonnées de niveau message uniques dans tous les messages d’une conversation.

- Collectez des messages contextuels autour de vos résultats de recherche.

- Passer en revue, annoter et redessier des conversations threadées.

- Exporter des messages individuels ou des conversations threadées

## <a name="terminology"></a>Terminologie

Voici quelques définitions pour vous aider à commencer à utiliser la reconstruction de conversation.

- **Messages :** Représente la plus petite unité d’une conversation. La taille, la structure et les métadonnées des messages peuvent varier. 

- **Conversation :** Représente un regroupement d’un ou plusieurs messages. Dans différentes applications, les conversations peuvent être représentées de différentes manières. Dans certaines applications, il existe une action explicite qui résulte de la réponse à un message existant. Les conversations sont formées explicitement à la suite de cette action de l’utilisateur. Par exemple, voici une capture d’écran d’une conversation de canal dans Microsoft Teams.

   ![Conversation du canal Microsoft Teams](../media/threadedchat.png)

   Dans d’autres applications (telles que les messages de conversation 1xN dans Teams), il n’existe pas de chaîne de réponse formelle et les messages apparaissent plutôt comme une « série plate de messages » au sein d’un thread unique. Dans ces types d’applications, les conversations sont déduites d’un groupe de messages qui se produisent dans un certain temps. Ce « groupement souple » de messages (par opposition à une chaîne de réponse) représente la conversation « va-et-vient » sur un sujet spécifique. 

## <a name="step-1-run-a-search"></a>Étape 1 : Exécuter une recherche

Une fois que vous avez identifié les dépositaires et les emplacements de contenu pertinents, vous pouvez créer une recherche pour rechercher du contenu potentiellement pertinent. Sous **l’onglet Recherches** dans le cas Advanced eDiscovery,  vous pouvez créer une recherche en cliquant sur Nouvelle recherche et en suivant l’Assistant. Pour plus d’informations sur la création d’une recherche, la création d’une requête de recherche et l’affichage des résultats de la recherche, voir Collecter des données [pour un cas.](create-search-to-collect-data.md)

## <a name="step-2-create-a-conversation-review-set"></a>Étape 2 : Créer un groupe de révision de conversation

Dans un jeu à réviser, vous pouvez rechercher, baliser, annoter et écrire des documents, des messages électroniques et des conversations. Dans Advanced eDiscovery, vous pouvez personnaliser votre révision des conversations, en fonction de messages individuels ou de conversations threadées. Cela est déterminé par le type de jeu à réviser à partir de quel type vous ajoutez les résultats de la recherche créée à l’étape 1. Il existe deux types différents d’ensembles de révision : 
  
  - **Ensembles de révision standard :** Les messages des conversations sont traitées et affichées en tant qu’éléments individuels. 
  
  -  **Ensembles de révision de conversation :** Les messages dans les conversations sont traitées individuellement mais affichées dans un affichage conversation. Dans un groupe de révision de conversation, vous pouvez annoter, baliser et redacter des messages dans un affichage de conversation thread. 

Pour plus d’informations sur la façon de réviser et de gérer le contenu d’un jeu à réviser, voir [Gérer les ensembles de révision.](managing-review-sets.md) 

## <a name="step-3-enable-conversation-retrieval-options"></a>Étape 3 : Activer les options de récupération des conversations

Après avoir examiné et finalisé votre requête de recherche, vous pouvez ajouter les résultats de la recherche à un jeu à réviser. Lorsque vous ajoutez vos résultats de recherche dans un jeu à réviser, les données d’origine sont copiées dans une zone de stockage Azure pour faciliter le processus de révision et d’analyse. Pour plus d’informations sur l’ajout de résultats de recherche à un jeu à réviser, voir Ajouter des résultats de [recherche à un jeu à réviser.](add-data-to-review-set.md) 

Lorsque vous ajoutez des données de conversations à un jeu à réviser, vous pouvez utiliser les options de récupération de conversation pour développer votre recherche et inclure des messages contextuels. Une fois que vous avez définie les options de récupération de conversation, les choses suivantes peuvent se produire :

  ![Récupération de conversation](../media/messagesandconversations.png)
  
1. À l’aide d’une requête de mot clé et de plage de dates, la recherche a renvoyé un succès sur *le message 3*. Ce message faisait partie d’une conversation plus importante, illustrée par *CRC1*. 
  
2. Lorsque vous ajoutez les données dans un jeu à réviser et activez les options de récupération de conversation, Advanced eDiscovery retourne et collecte d’autres éléments dans *CRC1*. 
  
3. Une fois que les éléments ont été ajoutés au jeu à réviser, vous pouvez passer en revue tous les messages individuels à partir *de CRC1*. 

Pour activer la récupération de conversation :
  
1. Sous **l’onglet Recherches** dans le cas Advanced eDiscovery,  sélectionnez une recherche, puis cliquez sur Ajouter à la révision définie sur la page volante.
  
2. Sélectionnez un jeu à réviser existant ou créez-en un. Vous pouvez configurer les options de récupération lors de l’ajout de résultats de recherche à un jeu à réviser standard ou conversation.
  
3. Sous **Options de collecte,** configurez les options de récupération de conversation pour les sources  de contenu que vous souhaitez développer dans votre recherche, puis cliquez sur Ajouter pour démarrer le processus.  
  
4. Une fois **que le travail Ajouter à l’ensemble de** révision sous l’onglet **Travaux** est terminé, vous pouvez commencer à examiner les conversations.

## <a name="step-4-review-and-export-conversations-in-a-review-set"></a>Étape 4 : Examiner et exporter des conversations dans un jeu à réviser

Une fois que le contenu a été traitée et ajoutée au jeu à réviser, vous pouvez commencer à examiner les données du jeu à réviser. Les fonctionnalités de révision sont différentes selon que le contenu a été ajouté à un jeu à réviser standard ou à un groupe de révision de conversation. 

### <a name="reviewing-conversations-in-a-standard-review-set"></a>Examen des conversations dans un jeu à réviser standard

Dans un jeu à réviser standard, les messages sont traitées et affichées en tant qu’éléments individuels, comme ils sont stockés dans un dossier de boîte aux lettres. Dans ce flux de travail, chaque message est traitée en tant qu’élément distinct. Par conséquent, les options de synthèse de thread et d’exportation ne sont pas disponibles dans un jeu à réviser standard. 

  ![Jeu à réviser standard](../media/standardrs.PNG)

### <a name="reviewing-conversations-in-a-conversation-review-set"></a>Examen des conversations dans un groupe de révision de conversation

Dans un groupe de révision de conversation, les messages individuels sont threadés ensemble et présentés en tant que conversations. Cela vous permet de passer en revue et d’exporter des conversations contextuelles. 

  ![Ensemble de révision de conversation](../media/ConversationRSOptions.PNG)

Les sections suivantes décrivent l’examen et l’exportation de conversations dans un groupe de révision de conversation.

#### <a name="reviewing-conversations"></a>Examen des conversations

Dans un groupe de révision de conversation, vous pouvez utiliser les options suivantes pour faciliter le processus de révision.

- **Grouper par conversation :** Groupe les messages au sein d’une même conversation pour aider les utilisateurs à simplifier et accélérer leur processus de révision. 

- **Vue récapitulatif :** Affiche la conversation threadée. Dans cette vue, vous pouvez voir la conversation entière et accéder aux métadonnées de chaque message individuel.  
  
   - Afficher les métadonnées des messages individuels
   
   - Télécharger des messages individuels

- **Affichage texte :** Fournit le texte extrait pour l’intégralité de la conversation. 

- **Affichage annoter :** Vous permet de marquer un affichage thread de la conversation. Tous les messages de la conversation partagent le même document annoté.

- **Marquage :** Lorsque vous visualisez des conversations dans un jeu  à réviser, vous pouvez afficher et appliquer des balises en cliquant sur le panneau marquage dans le panneau de codage.

- **Réexécutez la conversion de conversation :** Lorsque des messages sont ajoutés à un groupe de révision de conversation, un travail de conversion est automatiquement exécuté pour créer le résumé de thread et annoter des affichages. Si le travail de reconstruction de conversation échoue, vous pouvez réexécuter ce travail en cliquant sur Action > Créer des **PDF** de conversation dans le jeu à réviser.

#### <a name="exporting-conversations"></a>Exportation de conversations

Dans un groupe de révision de conversation, vous pouvez définir les options suivantes pour exporter des conversations :

![Exporter les options pour les conversations](../media/export.png)

a. Options de métadonnées

   - **Charger le fichier :** Les métadonnées sont incluses pour chaque message, message électronique et document. Il existe une ligne pour chaque message d’une conversation. 

   - **Balises :** Les balises de votre processus de révision sont incluses dans le fichier de métadonnées. Les messages d’une conversation partagent les mêmes balises. 

b. Options de conversation
  
   - **Fichiers de conversation :** Lorsque vous exportez des fichiers de conversation, l’affichage annoté est converti en fichier PDF et téléchargé dans le dossier d’exportation. Les messages d’un fichier de conversation pointent vers la version PDF du même fichier de conversation.  
  
   - **Messages de conversation individuels :** Lorsque vous exportez des messages individuels, chaque message unique de la conversation est exporté en tant qu’élément autonome. Le fichier est exporté au même format que dans la boîte aux lettres. Pour une conversation spécifique, vous recevez plusieurs fichiers .msg. 

     >[!NOTE]
     > Si vous avez appliqué des annotations au fichier de conversation, ces annotations ne seront pas transférées vers les messages individuels. 

c. Autres options

   - **Générer des fichiers texte pour tout le contenu exporté :** Génère un fichier texte pour chaque conversation exportée à partir du jeu à réviser. 

   - **Remplacez le contenu exporté par des PDF rédigés :** Si des fichiers de conversation rédigés sont générés pendant le processus de révision, ces fichiers sont disponibles pendant l’exportation. Vous pouvez décider d’exporter uniquement les fichiers natifs (en ne sélectionnant pas cette option) ou de remplacer les fichiers natifs par les versions expurgées des fichiers natifs (en sélectionnant cette option), qui sont exportés en tant que fichiers PDF.

## <a name="more-information"></a>Plus d’informations

Pour en savoir plus sur l’examen des données de cas dans Advanced eDiscovery, consultez les articles suivants :

- [Afficher les données de cas](view-documents-in-review-set.md)

- [Analyser les données de cas](analyzing-data-in-review-set.md)

- [Exporter les données de cas](exporting-data-ediscover20.md)
