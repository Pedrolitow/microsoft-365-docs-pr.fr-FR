---
title: Rechercher et supprimer des messages de conversation dans Teams
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: Utilisez eDiscovery (Premium) et Microsoft Graph Explorer pour rechercher et vider les messages de conversation dans Microsoft Teams et répondre aux incidents de débordement de données dans Teams.
ms.openlocfilehash: a692af67b486b4bb353df8ce8be1653d17f26be8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998467"
---
# <a name="search-and-purge-chat-messages-in-teams"></a>Rechercher et vider les messages de conversation dans Teams

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Vous pouvez utiliser eDiscovery (Premium) et Microsoft Graph Explorer pour rechercher et supprimer des messages de conversation dans Microsoft Teams. Cela peut vous aider à rechercher et supprimer des informations sensibles ou du contenu inapproprié. Ce flux de travail de recherche et de vidage vous aidera également à répondre à un incident de débordement de données, lorsque du contenu contenant des informations confidentielles ou malveillantes est publié par le biais de messages de conversation Teams.

> [!NOTE]
> Cet article s’applique aux organisations Microsoft 365 Entreprise. La prise en charge du cloud us government (y compris Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD) sera bientôt disponible.

## <a name="before-you-search-and-purge-chat-messages"></a>Avant de rechercher et de vider les messages de conversation

- Pour créer un cas eDiscovery (Premium) et utiliser des collections pour rechercher des messages de conversation, vous devez être membre du groupe de rôles **eDiscovery Manager** dans le portail de conformité Microsoft Purview. Pour supprimer des messages de conversation, vous devez disposer du rôle **Rechercher et vider** . Ce rôle est attribué par défaut aux groupes de rôles De l’Enquêteur de données et Gestion de l’organisation. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).
- La recherche et le vidage sont pris en charge pour les conversations au sein de votre locataire. La prise en charge des conversations Teams Connecter conversation (accès externe ou fédération) est activée dans l’interface dans certains cas, mais ne fonctionne pas comme prévu.
- Un maximum de 10 éléments par boîte aux lettres peuvent être supprimés à la fois. Étant donné que la possibilité de rechercher et de supprimer des messages de conversation est destinée à être un outil de réponse aux incidents, cette limite permet de s’assurer que les messages de conversation sont rapidement supprimés.

## <a name="search-and-purge-workflow"></a>Flux de travail de recherche et de vidage

Voici le processus de recherche et de vidage Teams messages de conversation :

![Flux de travail pour rechercher et vider Teams messages de conversation.](../media/TeamsSearchAndPurgeWorkflow.png)

## <a name="step-1-create-a-case-in-ediscovery-premium"></a>Étape 1 : Créer un cas dans eDiscovery (Premium)

La première étape consiste à créer un cas dans eDiscovery (Premium) pour gérer le processus de recherche et de vidage. Pour plus d’informations sur la création d’un cas, consultez [Utiliser le nouveau format de cas](advanced-ediscovery-new-case-format.md). 

## <a name="step-2-create-a-draft-collection"></a>Étape 2 : Créer un brouillon de collection

Après avoir créé un cas, l’étape suivante consiste à créer un brouillon de collection pour rechercher les messages de conversation Teams que vous souhaitez vider. Le processus de vidage que vous effectuez est l’étape 5 pour vider tous les éléments qui se trouvent dans la collection brouillon.

Dans eDiscovery (Premium), une *collection* est une recherche eDiscovery des emplacements de contenu Teams qui contiennent les messages de conversation que vous souhaitez vider. Créez la collection brouillon dans le cas que vous avez créé à l’étape précédente. Pour plus d’informations, consultez [Créer un projet de collection](create-draft-collection.md).

### <a name="data-sources-for-chat-messages"></a>Sources de données pour les messages de conversation

Utilisez le tableau suivant pour déterminer les sources de données à rechercher en fonction du type de message de conversation que vous devez vider.

| Pour ce type de conversation...|Recherchez cette source de données...|
|:---------|:---------|
|Teams conversations 1:1     |Boîte aux lettres des participants à la conversation.|
|Teams conversations de groupe     |Boîtes aux lettres des participants à la conversation.|
|canaux Teams (standard et partagés) |Boîte aux lettres associée à l’équipe parente.|
|Teams canaux privés |Boîte aux lettres des membres du canal privé.|

> [!NOTE]
> À l’étape 4, vous devez également identifier et supprimer les conservations et stratégies de rétention affectées à la boîte aux lettres qui contient le type de messages de conversation que vous souhaitez supprimer.

### <a name="tips-for-searching-for-chat-messages"></a>Astuces pour rechercher des messages de conversation

Pour vous assurer que la collection la plus complète de conversations Teams (y compris les conversations de groupe et 1:1, et les conversations de conversations standard, partagées et privées) utilisent la condition **Type** et sélectionnez l’option **Messages instantanés** lorsque vous générez la requête de recherche pour le brouillon de la collection. Nous vous recommandons également d’inclure une plage de dates ou plusieurs mots clés pour limiter l’étendue de la collection aux éléments pertinents pour votre recherche dans le cadre d’une investigation de vidage.

Voici une capture d’écran d’un exemple de requête utilisant les options **Type** et **Date** :

   ![Requête pour collecter Teams contenu.](..\media\TeamsConditionsQueryType.png)

Pour plus d’informations, consultez [Les requêtes de recherche de build pour les regroupements](building-search-queries.md).

## <a name="step-3-review-and-verify-chat-messages-to-purge"></a>Étape 3 : Vérifier et vérifier les messages de conversation à vider

Comme mentionné précédemment, le processus de vidage à l’étape 5 supprime les éléments retournés par la collection. Il est donc important de passer en revue les résultats de la collection brouillon pour vous assurer que la collection ne renvoie que les éléments que vous souhaitez vider. Pour passer en revue un exemple d’éléments d’une collection brouillon, consultez la section « Étapes suivantes après la fin d’une collection brouillon » dans [Créer une collection brouillon](create-draft-collection.md#next-steps-after-a-draft-collection-is-complete).

En outre, vous pouvez utiliser les statistiques de collecte (en particulier les statistiques top locations) pour générer une liste des sources de données qui contiennent des éléments retournés par la collection. Utilisez cette liste à l’étape suivante pour supprimer les stratégies de conservation et de rétention des sources de données qui contiennent des résultats de recherche. Pour plus d’informations, consultez [les statistiques et les rapports](collection-statistics-reports.md) de collecte.

## <a name="step-4-remove-holds-and-retention-policies-from-data-sources"></a>Étape 4 : Supprimer les conservations et les stratégies de rétention des sources de données

Avant de pouvoir vider les messages de conversation d’une boîte aux lettres, vous devez supprimer toute stratégie de conservation ou de rétention affectée à une boîte aux lettres cible. Si ce n’est pas le cas, la conversation que vous essayez de supprimer est conservée.

Utilisez la liste des boîtes aux lettres contenant les messages de conversation que vous souhaitez supprimer et déterminez si une stratégie de conservation ou de rétention est affectée à ces boîtes aux lettres, puis supprimez la stratégie de conservation ou de rétention. Veillez à identifier la stratégie de conservation ou de rétention que vous supprimez afin de pouvoir réattribuer aux boîtes aux lettres à l’étape 7.

Pour obtenir des instructions sur l’identification et la suppression des conservations et des stratégies de rétention, consultez « Étape 3 : Supprimer toutes les conservations de la boîte aux lettres » dans [Supprimer les éléments dans le dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox). 

## <a name="step-5-purge-chat-messages-from-teams"></a>Étape 5 : Vider les messages de conversation de Teams

Vous êtes maintenant prêt à vider réellement les messages de conversation de Teams. Vous allez utiliser Microsoft Graph Explorer pour effectuer les trois tâches suivantes :

1. Obtenez l’ID du cas eDiscovery (Premium) que vous avez créé à l’étape 1. C’est le cas qui contient la collection créée à l’étape 2.

2. Obtenez l’ID de la collection que vous avez créée à l’étape 2 et vérifié les résultats de la recherche à l’étape 3. La requête de recherche de cette collection retourne les messages de conversation qui seront purgés.

3. Purgez les messages de conversation retournés par la collection.

Pour plus d’informations sur l’utilisation de Graph Explorer, consultez [Utiliser Graph Explorer pour essayer les API Microsoft Graph](/graph/graph-explorer/graph-explorer-overview).

> [!IMPORTANT]
> Pour effectuer ces trois tâches dans Graph Explorer, vous devrez peut-être accepter les autorisations eDiscovery.Read.All et eDiscovery.ReadWrite.All. Pour plus d’informations, consultez la section « Consentement aux autorisations » dans [Working with Graph Explorer](/graph/graph-explorer/graph-explorer-features#consent-to-permissions).

### <a name="get-the-case-id"></a>Obtenir l’ID de la casse

1. Accédez à <https://developer.microsoft.com/graph/graph-explorer> l’Explorateur Graph avec un compte auquel le rôle **Rechercher et vider** est attribué dans le portail de conformité Microsoft Purview.

2. Exécutez la requête GET suivante pour récupérer l’ID du cas eDiscovery (Premium). Utilisez la valeur `https://graph.microsoft.com/beta/compliance/ediscovery/cases` dans la barre d’adresses de la requête de requête. Veillez à sélectionner **v1.0** dans la liste déroulante des versions de l’API.

   ![Demande GET pour l’ID de cas.](..\media\GraphGetRequestForCaseId.png)

   Cette demande retourne des informations sur tous les cas de votre organisation sous l’onglet **Aperçu** de la réponse.

3. Faites défiler la réponse pour localiser le cas eDiscovery (Premium). Utilisez la propriété **displayName** pour identifier le cas.

   ![Réponse avec l’ID de cas.](..\media\GraphResponseForCaseId.png)

4. Copiez l’ID correspondant (ou copiez-le et collez-le dans un fichier texte). Vous utiliserez cet ID dans la tâche suivante pour obtenir l’ID de collection.

> [!TIP]
> Au lieu d’utiliser la procédure précédente pour obtenir l’ID de cas, vous pouvez ouvrir le cas dans le portail de conformité Microsoft Purview et copier l’ID de cas à partir de l’URL.

### <a name="get-the-collection-id"></a>Obtenir l’ID de collection

1. Dans Graph’Explorateur, exécutez la requête GET suivante pour récupérer l’ID de la collection que vous avez créée à l’étape 2 et contient les éléments que vous souhaitez vider. Utilisez la valeur `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections` dans la barre d’adresses de la requête de requête, où CaseId est l’ID que vous avez obtenu dans la procédure précédente. Veillez à entourer l’ID du boîtier de parenthèses et de guillemets simples.

   ![Demande GET pour l’ID de collection.](..\media\GraphGetRequestForCollectionId.png)

   Cette demande retourne des informations sur toutes les collections dans le cas sous l’onglet **Aperçu** de la réponse.

2. Faites défiler la réponse pour localiser la collection qui contient les éléments que vous souhaitez vider. Utilisez la propriété **displayName** pour identifier la collection que vous avez créée à l’étape 3.

   ![Réponse avec l’ID de collection.](..\media\GraphResponseForCollectionId.png)

   Dans la réponse, la requête de recherche de la collection s’affiche dans la propriété **contentQuery** . Les éléments retournés par cette requête seront purgés dans la tâche suivante.

3. Copiez l’ID correspondant (ou copiez-le et collez-le dans un fichier texte). Vous utiliserez cet ID dans la tâche suivante pour vider les messages de conversation.

### <a name="purge-the-chat-messages"></a>Vider les messages de conversation

1. Dans Graph Explorer, exécutez la requête POST suivante pour vider les éléments retournés par la collection que vous avez créée à l’étape 2. Utilisez la valeur `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections('collectionId')/purgeData` dans la barre d’adresses de la requête de requête, où caseId et collectionId sont les ID que vous avez obtenus dans les procédures précédentes. Veillez à entourer les valeurs d’ID de parenthèses et de guillemets simples.

      ![Demande POST pour supprimer les éléments retournés par la collection.](..\media\GraphPOSTRequestToPurgeItems.png)

   Si la requête POST réussit, un code de réponse HTTP s’affiche dans une bannière verte indiquant que la demande a été acceptée.

   ![Réponse pour la demande de vidage.](..\media\GraphResponseForPurge.png)

## <a name="step-6-verify-chat-messages-are-purged"></a>Étape 6 : Vérifier que les messages de conversation sont purgés

Après avoir exécuté la demande POST pour vider les messages de conversation, ces messages sont supprimés du client Teams et remplacés par un message généré automatiquement indiquant qu’un administrateur a supprimé le message. Pour obtenir un exemple de ce message, consultez la section [Expérience de l’utilisateur final](#end-user-experience) dans cet article.

Les messages de conversation vidés sont déplacés vers le dossier SubstrateHolds, qui est un dossier de boîte aux lettres masqué. Les messages de conversation vidés y sont stockés pendant au moins 1 jour, puis sont définitivement supprimés la prochaine fois que le travail du minuteur s’exécute (généralement entre 1 et 7 jours). Pour plus d’informations, consultez [En savoir plus sur la rétention des Microsoft Teams](retention-policies-teams.md).

## <a name="step-7-reapply-holds-and-retention-policies-to-data-sources"></a>Étape 7 : Réappliquer des stratégies de conservation et de rétention dans des sources de données

Après avoir vérifié que les messages de conversation sont purgés et supprimés du client Teams, vous pouvez réappliquer les stratégies de conservation et de rétention que vous avez supprimées à l’étape 4.

<!--
## Deleting chat messages in federated environments

Admins can use the procedures in this article to search and delete Teams chat messages in federated environments. However, you must adhere to the following guidelines. These guidelines are based on the organizational ownership of the conversation thread that contains the messages you want to delete. An organization is the owner of a conversation thread that is started by a user in that organization. In other words, when a user starts a chat, the user's organization becomes the owner of the conversation thread.

- Admins can delete the compliance copy in conversation threads owned by their organization. That means compliance copies are purged when the admin who purges the chat messages in Step 5 is in the same organization as the user who initiated the conversation thread that contains the purged messages. If a conversation thread has users in two organizations, compliance copies for the other organization will be retained.

- If a conversation thread has users in two organizations, purged chat messages are removed from the Teams client in both organizations.

- The only way to purge chat messages from user mailboxes in your organization for chat messages in conversation threads owned by another organization is to use retention policies for Teams. For more information, see [Learn about retention for Microsoft Teams](retention-policies-teams.md).
-->

## <a name="end-user-experience"></a>Expérience de l’utilisateur final

Pour les messages de conversation supprimés, les utilisateurs voient un message généré automatiquement indiquant « Ce message a été supprimé par un administrateur ».

![Affichage du message de conversation purgé dans Teams client.](..\media\TeamsPurgeTombstone.png)

Le message de la capture d’écran précédente remplace le message de conversation qui a été supprimé.

> [!NOTE]
> Si vous êtes un utilisateur final et qu’un message de conversation a été supprimé, contactez votre administrateur pour plus d’informations.
