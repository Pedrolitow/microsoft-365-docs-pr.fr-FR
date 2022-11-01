---
title: Rechercher et supprimer des messages de conversation dans Teams
description: Utilisez eDiscovery (Premium) et l’Explorateur Microsoft Graph pour rechercher et vider les messages de conversation dans Microsoft Teams, et répondre aux incidents de déversement de données dans Teams.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: f559e1303e27c55adecf4e3dee80fc3d39c0eb73
ms.sourcegitcommit: b439d097e55bba35d9328447d993bbcac7a178a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68802619"
---
# <a name="search-and-purge-chat-messages-in-teams-preview"></a>Rechercher et vider les messages de conversation dans Teams (préversion)

Vous pouvez utiliser eDiscovery (Premium) et l’Explorateur Microsoft Graph pour rechercher et supprimer des messages de conversation dans Microsoft Teams. Cela peut vous aider à trouver et à supprimer des informations sensibles ou du contenu inapproprié. Ce flux de travail de recherche et de vidage vous aidera également à répondre à un incident de déversement de données, lorsque du contenu contenant des informations confidentielles ou malveillantes est publié via des messages de conversation Teams.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-search-and-purge-chat-messages"></a>Avant de rechercher et de vider les messages de conversation

- Pour créer un cas eDiscovery (Premium) et utiliser des regroupements pour rechercher des messages de conversation, vous devez être membre du groupe de rôles **Gestionnaire eDiscovery** dans le portail de conformité Microsoft Purview. Pour supprimer les messages de conversation, vous devez disposer du rôle **Rechercher et vider** . Ce rôle est attribué aux groupes de rôles Enquêteur de données et Gestion de l’organisation par défaut. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).
- La recherche et le vidage sont pris en charge pour les conversations au sein de votre locataire. La prise en charge des conversations Teams Connect Chat (accès externe ou fédération) est activée dans l’interface dans certains cas, mais ne fonctionne pas comme prévu.
- Un maximum de 10 éléments par boîte aux lettres peuvent être supprimés à la fois. Étant donné que la possibilité de rechercher et de supprimer des messages de conversation est destinée à être un outil de réponse aux incidents, cette limite permet de garantir que les messages de conversation sont rapidement supprimés.

## <a name="search-and-purge-workflow"></a>Rechercher et vider le flux de travail

Voici le processus de recherche et de vidage des messages de conversation Teams :

![Flux de travail pour rechercher et vider les messages de conversation Teams.](../media/TeamsSearchAndPurgeWorkflow.png)

## <a name="step-1-create-a-case-in-ediscovery-premium"></a>Étape 1 : Créer un cas dans eDiscovery (Premium)

La première étape consiste à créer un cas dans eDiscovery (Premium) pour gérer le processus de recherche et de vidage. Pour plus d’informations sur la création d’un cas, consultez [Utiliser le nouveau format de cas](advanced-ediscovery-new-case-format.md).

## <a name="step-2-create-a-draft-collection"></a>Étape 2 : Créer un brouillon de collection

Après avoir créé un cas, l’étape suivante consiste à créer un brouillon de collection pour rechercher les messages de conversation Teams que vous souhaitez vider. Le processus de vidage que vous effectuez à l’étape 5 vide tous les éléments qui se trouvent dans la collection de brouillons.

Dans eDiscovery (Premium), une *collection* est une recherche eDiscovery des emplacements de contenu Teams qui contiennent les messages de conversation que vous souhaitez vider. Créez la collection brouillon dans le cas où vous avez créé à l’étape précédente. Pour plus d’informations, consultez [Créer un brouillon de collection](create-draft-collection.md).

### <a name="data-sources-for-chat-messages"></a>Sources de données pour les messages de conversation

Utilisez le tableau suivant pour déterminer les sources de données à rechercher en fonction du type de message de conversation que vous devez vider.

| Pour ce type de conversation...|Rechercher dans cette source de données...|
|:---------|:---------|
|Conversations Teams 1:1     |Boîte aux lettres des participants à la conversation.|
|Conversations de groupe Teams     |Boîtes aux lettres des participants à la conversation.|
|Canaux Teams (standard et partagés) |Boîte aux lettres associée à l’équipe parente.|
|Canaux privés Teams |Boîte aux lettres des membres du canal privé.|

> [!NOTE]
> À l’étape 4, vous devez également identifier et supprimer toutes les stratégies de conservation et de rétention affectées à la boîte aux lettres qui contient le type de messages de conversation que vous souhaitez supprimer.

### <a name="tips-for-searching-for-chat-messages"></a>Conseils pour la recherche de messages de conversation

Pour vous assurer que la collection la plus complète de conversations de conversation Teams (y compris les conversations 1:1 et de groupe, et les conversations à partir de conversations standard, partagées et privées), utilisez la condition **Type** et sélectionnez l’option **Messages instantanés** lorsque vous générez la requête de recherche pour le brouillon de collection. Nous vous recommandons également d’inclure une plage de dates ou plusieurs mots clés pour limiter l’étendue de la collection aux éléments pertinents pour votre recherche d’une enquête de vidage.

Voici une capture d’écran d’un exemple de requête utilisant les options **Type** et **Date** :

   ![Requête pour collecter du contenu Teams.](..\media\TeamsConditionsQueryType.png)

Pour plus d’informations, consultez [Générer des requêtes de recherche pour les collections](building-search-queries.md).

## <a name="step-3-review-and-verify-chat-messages-to-purge"></a>Étape 3 : Examiner et vérifier les messages de conversation à vider

Comme mentionné précédemment, le processus de vidage à l’étape 5 supprime les éléments retournés par la collection. Il est donc important de passer en revue les résultats brouillons de la collection pour vous assurer que la collection retourne uniquement les éléments que vous souhaitez vider. Pour passer en revue un exemple d’éléments d’une collection de brouillons, consultez la section « Étapes suivantes après la fin d’un brouillon de collection » dans [Créer un brouillon de collection](create-draft-collection.md#next-steps-after-a-draft-collection-is-complete).

En outre, vous pouvez utiliser les statistiques de collection (en particulier les statistiques top locations) pour générer une liste des sources de données qui contiennent des éléments retournés par la collection. Utilisez cette liste à l’étape suivante pour supprimer les stratégies de conservation et de rétention des sources de données qui contiennent les résultats de la recherche. Pour plus d’informations, consultez [Statistiques et rapports de collecte](collection-statistics-reports.md).

## <a name="step-4-remove-holds-and-retention-policies-from-data-sources"></a>Étape 4 : Supprimer les stratégies de conservation et de rétention des sources de données

Avant de pouvoir vider les messages de conversation d’une boîte aux lettres, vous devez supprimer toute stratégie de conservation ou de rétention affectée à une boîte aux lettres cible. Si ce n’est pas le cas, la conversation que vous essayez de supprimer sera conservée.

Utilisez la liste des boîtes aux lettres qui contiennent les messages de conversation que vous souhaitez supprimer et déterminez si une stratégie de conservation ou de rétention est affectée à ces boîtes aux lettres, puis supprimez la mise en attente ou la stratégie de rétention. Veillez à identifier la stratégie de conservation ou de rétention que vous supprimez afin de pouvoir réaffecter aux boîtes aux lettres à l’étape 7.

Pour obtenir des instructions sur l’identification et la suppression des stratégies de conservation et de rétention, consultez « Étape 3 : Supprimer toutes les conservations de la boîte aux lettres » dans [Supprimer les éléments du dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox).

## <a name="step-5-purge-chat-messages-from-teams"></a>Étape 5 : Vider les messages de conversation de Teams

Vous êtes maintenant prêt à vider les messages de conversation de Teams. Vous allez utiliser l’Explorateur Microsoft Graph pour effectuer les trois tâches suivantes :

1. Obtenez l’ID du cas eDiscovery (Premium) que vous avez créé à l’étape 1. C’est le cas qui contient la collection créée à l’étape 2.

2. Obtenez l’ID de la collection que vous avez créée à l’étape 2 et vérifié les résultats de la recherche à l’étape 3. La requête de recherche de cette collection retourne les messages de conversation qui seront vidés.

3. Videz les messages de conversation retournés par la collection.

Pour plus d’informations sur l’utilisation de l’Explorateur Graph, consultez [Utiliser l’Explorateur Graph pour essayer les API Microsoft Graph](/graph/graph-explorer/graph-explorer-overview).

> [!IMPORTANT]
> Les API sous la version /beta dans Microsoft Graph sont susceptibles de changer. L’utilisation de ces API dans des applications de production n’est pas prise en charge. Pour déterminer si une API est disponible dans la version 1.0, utilisez le sélecteur de version.

> [!IMPORTANT]
> Pour effectuer ces trois tâches dans l’Explorateur Graph, vous devrez peut-être donner votre consentement aux autorisations eDiscovery.Read.All et eDiscovery.ReadWrite.All. Pour plus d’informations, consultez la section « Consentement aux autorisations » dans [Utilisation de l’Explorateur Graph](/graph/graph-explorer/graph-explorer-features#consent-to-permissions).

### <a name="get-the-case-id"></a>Obtenir l’ID de cas

1. Accédez à l’Explorateur <https://developer.microsoft.com/graph/graph-explorer> Graph et connectez-vous à l’aide d’un compte auquel le rôle **Rechercher et vider** est attribué dans le portail de conformité Microsoft Purview.

2. Exécutez la requête GET suivante pour récupérer l’ID du cas eDiscovery (Premium). Utilisez la valeur `https://graph.microsoft.com/beta/security/ediscovery/cases` dans la barre d’adresse de la requête de requête. Veillez à sélectionner **v1.0** dans la liste déroulante version de l’API.

   ![DEMANDE GET pour l’ID de cas.](..\media\ediscovery-GraphGetRequestForCaseId.png)

   Cette demande retourne des informations sur tous les cas dans votre organisation sous l’onglet **Aperçu de la réponse** .

3. Faites défiler la réponse pour localiser le cas eDiscovery (Premium). Utilisez la propriété **displayName** pour identifier le cas.

   ![Réponse avec l’ID de cas.](..\media\GraphResponseForCaseId.png)

4. Copiez l’ID correspondant (ou copiez-le et collez-le dans un fichier texte). Vous utiliserez cet ID dans la tâche suivante pour obtenir l’ID de collection.

> [!TIP]
> Au lieu d’utiliser la procédure précédente pour obtenir l’ID de cas, vous pouvez ouvrir le cas dans le portail de conformité Microsoft Purview et copier l’ID de cas à partir de l’URL.

### <a name="get-the-collection-id"></a>Obtenir l’ID de collection

1. Dans l’Explorateur Graph, exécutez la requête GET suivante pour récupérer l’ID de la collection que vous avez créée à l’étape 2 et contient les éléments que vous souhaitez vider. Utilisez la valeur `https://graph.microsoft.com/beta/security/ediscovery/cases('caseId')/sourceCollections` dans la barre d’adresse de la requête de requête, où CaseId est l’ID que vous avez obtenu dans la procédure précédente. Veillez à entourer l’ID de casse avec des parenthèses et des guillemets simples.

   ![REQUÊTE GET pour l’ID de collection.](..\media\ediscovery-GraphGetRequestForCollectionId.png)

   Cette requête retourne des informations sur toutes les collections dans le cas sous l’onglet **Aperçu de la réponse** .

2. Faites défiler la réponse pour localiser la collection qui contient les éléments que vous souhaitez vider. Utilisez la propriété **displayName** pour identifier la collection que vous avez créée à l’étape 3.

   ![Réponse avec l’ID de collection.](..\media\GraphResponseForCollectionId.png)

   Dans la réponse, la requête de recherche de la collection s’affiche dans la propriété **contentQuery** . Les éléments retournés par cette requête seront vidés dans la tâche suivante.

3. Copiez l’ID correspondant (ou copiez-le et collez-le dans un fichier texte). Vous utiliserez cet ID dans la tâche suivante pour vider les messages de conversation.

> [!TIP]
> Au lieu d’utiliser la procédure précédente pour obtenir l’ID de collection, vous pouvez ouvrir le cas dans le portail de conformité Microsoft Purview. Ouvrez le cas et accédez à l’onglet Travaux. Sélectionnez la collection appropriée et, sous Informations de support, recherchez l’ID du travail (l’ID de travail affiché ici est identique à l’ID de collection).

### <a name="purge-the-chat-messages"></a>Vider les messages de conversation

1. Dans l’Explorateur Graph, exécutez la requête POST suivante pour vider les éléments retournés par la collection que vous avez créée à l’étape 2. Utilisez la valeur `https://graph.microsoft.com/beta/security/ediscovery/cases('caseId')/sourceCollections('collectionId')/purgeData` dans la barre d’adresse de la requête de requête, où caseId et collectionId sont les ID que vous avez obtenus dans les procédures précédentes. Veillez à entourer les valeurs d’ID de parenthèses et de guillemets simples.

      ![Demande POST pour supprimer les éléments retournés par la collection.](..\media\ediscovery-GraphPOSTRequestToPurgeItems.png)

   Si la requête POST réussit, un code de réponse HTTP s’affiche dans une bannière verte indiquant que la demande a été acceptée.

   ![Réponse à la demande de vidage.](..\media\ediscovery-GraphResponseForPurge.png)

  Pour plus d’informations sur purgeData, consultez [sourceCollection : purgeData](/graph/api/ediscovery-sourcecollection-purgedata).

> [!NOTE]
> Étant donné que l’Explorateur Microsoft Graph n’est pas disponible dans le cloud du gouvernement des États-Unis (GCC, GCC High et DOD), vous devez utiliser PowerShell pour effectuer ces tâches.

Vous pouvez également vider les messages de conversation à l’aide de PowerShell. Par exemple, pour vider les messages dans le cloud du gouvernement des États-Unis, vous pouvez utiliser une commande similaire à :

``
Connect-MgGraph -Scopes "ediscovery.ReadWrite.All" -Environment USGov
``

``Invoke-MgGraphRequest  -Method POST -Uri '/beta/security/cases/ediscoveryCases/<case ID>/searches/<collection ID>/purgeData'
``

Pour plus d’informations sur l’utilisation de PowerShell pour vider les messages de conversation, consultez [ediscoverySearch : purgeData](/graph/api/security-ediscoverysearch-purgedata).

## <a name="step-6-verify-chat-messages-are-purged"></a>Étape 6 : Vérifier que les messages de conversation sont vidés

Après avoir exécuté la requête POST pour vider les messages de conversation, ces messages sont supprimés du client Teams et remplacés par un généré automatiquement indiquant qu’un administrateur a supprimé le message. Pour obtenir un exemple de ce message, consultez la section [Expérience utilisateur](#end-user-experience) final de cet article.

Les messages de conversation vidés sont déplacés vers le dossier SubstrateHolds, qui est un dossier de boîte aux lettres masqué. Les messages de conversation vidés y sont stockés pendant au moins 1 jour, puis supprimés définitivement la prochaine fois que le travail du minuteur s’exécute (généralement entre 1 et 7 jours). Pour plus d’informations, consultez [En savoir plus sur la rétention pour Microsoft Teams](retention-policies-teams.md).

> [!NOTE]
> Étant donné que l’Explorateur Microsoft Graph n’est pas disponible dans le cloud du gouvernement des États-Unis (GCC, GCC High et DOD), vous devez utiliser PowerShell pour effectuer ces tâches.

## <a name="step-7-reapply-holds-and-retention-policies-to-data-sources"></a>Étape 7 : Réappliquer les stratégies de conservation et de rétention aux sources de données

Après avoir vérifié que les messages de conversation sont vidés et supprimés du client Teams, vous pouvez réappliquer les stratégies de conservation et de rétention que vous avez supprimées à l’étape 4.

<!--
## Deleting chat messages in federated environments

Admins can use the procedures in this article to search and delete Teams chat messages in federated environments. However, you must adhere to the following guidelines. These guidelines are based on the organizational ownership of the conversation thread that contains the messages you want to delete. An organization is the owner of a conversation thread that is started by a user in that organization. In other words, when a user starts a chat, the user's organization becomes the owner of the conversation thread.

- Admins can delete the compliance copy in conversation threads owned by their organization. That means compliance copies are purged when the admin who purges the chat messages in Step 5 is in the same organization as the user who initiated the conversation thread that contains the purged messages. If a conversation thread has users in two organizations, compliance copies for the other organization will be retained.

- If a conversation thread has users in two organizations, purged chat messages are removed from the Teams client in both organizations.

- The only way to purge chat messages from user mailboxes in your organization for chat messages in conversation threads owned by another organization is to use retention policies for Teams. For more information, see [Learn about retention for Microsoft Teams](retention-policies-teams.md).
-->

## <a name="end-user-experience"></a>Expérience de l’utilisateur final

Pour les messages de conversation supprimés, les utilisateurs verront un message généré automatiquement indiquant « Ce message a été supprimé par un administrateur ».

![Affichage du message de conversation vidé dans le client Teams.](..\media\TeamsPurgeTombstone.png)

Le message de la capture d’écran précédente remplace le message de conversation qui a été supprimé.

> [!NOTE]
> Si vous êtes un utilisateur final et qu’un message de conversation a été supprimé, contactez votre administrateur pour plus d’informations.
