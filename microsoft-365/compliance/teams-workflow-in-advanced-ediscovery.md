---
title: Flux de travail Teams dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Découvrez comment conserver, collecter, examiner et exporter du contenu à partir de Microsoft Teams dans eDiscovery (Premium).
ms.openlocfilehash: 46fe8491533f6d2fa6954eab76758213eaa7d30d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65414863"
---
# <a name="ediscovery-premium-workflow-for-content-in-microsoft-teams"></a>Flux de travail eDiscovery (Premium) pour le contenu dans Microsoft Teams

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article fournit un ensemble complet de procédures, de recommandations et de meilleures pratiques pour l’utilisation de Microsoft Purview eDiscovery (Premium) pour conserver, collecter, examiner et exporter du contenu à partir de Microsoft Teams. L’objectif de cet article est de vous aider à optimiser votre flux de travail eDiscovery pour Teams contenu.

Il existe cinq catégories de contenu Teams que vous pouvez collecter et traiter à l’aide d’eDiscovery (Premium) :

- **Teams conversations 1:1**. Messages de conversation, publications et pièces jointes partagés dans une conversation Teams entre deux personnes.  Teams conversations 1:1 sont également appelées *conversations*.

- **Teams conversations de groupe**. Messages de conversation, publications et pièces jointes partagés dans une conversation Teams entre trois personnes ou plus. Également appelé *conversations 1:N* ou *conversations de groupe*.

- **Teams canaux**. Messages de conversation, publications, réponses et pièces jointes partagés dans un canal Teams standard.

- **Canaux privés**. Messages, réponses et pièces jointes partagés dans un canal Teams privé.

- **Canaux partagés**. Messages, réponses et pièces jointes partagés dans un canal Teams partagé.

## <a name="where-teams-content-is-stored"></a>Où Teams contenu est stocké

Un prérequis pour gérer Teams contenu dans eDiscovery (Premium) consiste à comprendre le type de contenu Teams que vous pouvez collecter, traiter et examiner dans eDiscovery (Premium) et où ce contenu est stocké dans Microsoft 365. Le tableau suivant répertorie Teams type de contenu et où chacun est stocké.

|&nbsp;|Emplacement des messages et des billets de conversation|Emplacement des fichiers et pièces jointes|
|---|---|---|
|Teams conversations 1:1|Les messages dans les conversations 1:1 sont stockés dans la boîte aux lettres Exchange Online de tous les participants à la conversation.|Les fichiers partagés dans une conversation 1:1 sont stockés dans le compte OneDrive Entreprise de la personne qui a partagé le fichier.|
|Teams conversations de groupe|Les messages des conversations de groupe sont stockés dans la boîte aux lettres Exchange Online de tous les participants à la conversation.|Les fichiers partagés dans les conversations de groupe sont stockés dans le compte OneDrive Entreprise de la personne qui a partagé le fichier.|
|Équipes et canaux|Tous les messages et publications de canal sont stockés dans la boîte aux lettres Exchange Online associée à l’équipe.|Les fichiers partagés dans un canal sont stockés dans le site SharePoint Online associé à l’équipe.|
|Canaux privés|Les messages envoyés dans un canal privé sont stockés dans les boîtes aux lettres Exchange Online de tous les membres du canal privé.|Les fichiers partagés dans un canal privé sont stockés dans un site dédié SharePoint Online associé au canal privé.|
|Canaux partagés|Les messages envoyés dans un canal partagé sont stockés dans une boîte aux lettres système associée au canal partagé. <sup>1</sup>|Les fichiers partagés dans un canal partagé sont stockés dans un site dédié SharePoint Online associé au canal partagé.|

> [!NOTE]
> <sup>1</sup> Pour rechercher (et conserver) les messages envoyés dans un canal partagé, vous devez rechercher ou spécifier la boîte aux lettres Exchange Online pour l’équipe parente.

## <a name="create-a-case-for-teams-content"></a>Créer un cas pour Teams contenu

La première étape de la gestion du contenu Teams dans eDiscovery (Premium) consiste à créer un cas à l’aide du nouveau format de cas optimisé pour gérer Teams contenu. Voici les avantages de l’utilisation du nouveau format de cas pour Teams contenu :

- Prise en charge du thread de conversation, dans laquelle les messages supplémentaires de la même conversation qui incluent des éléments réactifs sont automatiquement collectés et ajoutés aux ensembles de révision.

- Teams conversations de conversation sont automatiquement ajoutées aux jeux de révision sous forme de fichier de transcription HTML. Les pièces jointes cloud partagées dans les conversations sont également ajoutées à l’ensemble de révisions. Cela permet de fournir un contexte aux conversations avec des éléments réactifs et de réduire le nombre total d’éléments produits par le contenu basé sur la conversation.

- Les collections pouvant atteindre 1 To peuvent être ajoutées à des jeux de révision, ce qui vous permet de collecter et de grandes quantités de contenu Teams dans un cas.

Pour plus d’informations sur l’augmentation des limites de cas, consultez [Utiliser le nouveau format de cas dans eDiscovery (Premium)](advanced-ediscovery-new-case-format.md).

Pour créer un cas :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche de l’portail de conformité Microsoft Purview, cliquez sur **eDiscovery > Avancé**.

3. Dans la page **eDiscovery (Premium),** cliquez sur l’onglet **Cas**, puis sur **Créer un cas**.

   La page de menu volant **Nouveau cas eDiscovery** s’affiche. La section **Format** de cas fournit la possibilité de créer un cas à l’aide du nouveau format de cas.

   ![Option Grand cas dans la page Nouveau cas eDiscovery.](..\media\AeDNewCaseFormat1.png)

4. Après avoir nommé le cas, sélectionnez l’option **Nouvelle** , puis cliquez sur **Enregistrer** pour créer le cas.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Ajouter Teams sources de données de garde et conserver Teams contenu  

L’étape suivante consiste à identifier les utilisateurs qui sont les gardiens de données dans votre enquête et à les ajouter, ainsi que leurs emplacements de contenu, en tant que consignatateurs au cas que vous avez créé dans la section précédente. Lorsque vous ajoutez des consignatateurs, vous pouvez spécifier leur boîte aux lettres et OneDrive compte en tant que sources de données de garde. Vous pouvez également spécifier Teams emplacements de contenu en tant que sources de données de consignataires pour mettre rapidement ces emplacements en attente légale afin de conserver le contenu pendant votre enquête. Il facilite également la collecte de contenu et son ajout à un ensemble de révisions.

Pour ajouter des consignataires à un cas et conserver les sources de données de garde :

1. Accédez au cas eDiscovery (Premium) que vous avez créé dans la section précédente, puis cliquez sur **Sources de données**.

2. Dans la page **Sources** de données, cliquez sur Ajouter **de nouveaux consignatateurs sourceAdd** de **données** > .

3. Dans l’Assistant **Nouveau consignateur** , ajoutez un ou plusieurs utilisateurs en tant que consignateurs au cas en tapant la première partie du nom ou de l’alias de l’utilisateur. Une fois que vous avez trouvé la personne appropriée, sélectionnez son nom pour l’ajouter à la liste.  

4. Développez chaque dépositaire pour afficher les sources de données primaires qui ont été automatiquement associées au consignat, et pour sélectionner d’autres emplacements à associer au consignateur.

   ![Sources de données consignatières.](..\media\TeamsCustodialDataLocations1.png)

5. Suivez ces instructions pour ajouter des sources de données de garde pour Teams contenu. Cliquez sur **Modifier** pour ajouter un emplacement de données.

   - **Boîtes aux lettres**. La boîte aux lettres du consignateur est sélectionnée par défaut. Conservez cette option sélectionnée pour ajouter (et conserver) des conversations 1:1, des conversations de groupe et des conversations de canal privé en tant que données de garde.

   - **OneDrives**. Le compte OneDrive du consignateur est sélectionné par défaut. Conservez cette option sélectionnée pour ajouter (et conserver) des fichiers partagés dans des conversations 1:1 et des conversations de groupe en tant que données de garde.

   - **SharePoint**. Ajoutez le site SharePoint associé à n’importe quel canal privé ou partagé dont le dépositaire est membre pour ajouter (et conserver) en tant que données de garde les fichiers partagés dans un canal. Cliquez sur **Modifier**, puis ajoutez l’URL du site SharePoint associé à un canal privé ou partagé. Pour savoir comment localiser les canaux privés et partagés dont un utilisateur est membre, consultez [eDiscovery des canaux privés et partagés](/microsoftteams/ediscovery-investigation#ediscovery-of-private-and-shared-channels).

   - **Teams**. Ajoutez les équipes dont le dépositaire est membre pour ajouter (et conserver) en tant que données de garde tous les messages de canal et tous les fichiers partagés dans un canal Teams. Cela inclut l’ajout de la boîte aux lettres pour l’équipe parente d’un canal partagé dont le consignateur est membre. Lorsque vous cliquez sur **Modifier**, la boîte aux lettres et le site associés à chaque équipe dont le gardien est membre sont affichés dans une liste. Sélectionnez les équipes que vous souhaitez associer au consignateur. Vous devez sélectionner la boîte aux lettres et le site correspondants pour chaque équipe.

   > [!NOTE]
   > Vous pouvez également ajouter la boîte aux lettres et le site de Teams dont les consignatateurs ne sont pas membres en tant qu’emplacement de données de consignat. Pour ce faire, cliquez sur **Modifier** en regard de **Exchange** et **SharePoint**, puis ajoutez la boîte aux lettres et le site associés à l’équipe.

6. Après avoir ajouté des consignats et configuré les sources de données de garde, cliquez sur **Suivant** pour afficher la page **Paramètres** de conservation.

   Une liste des consignats s’affiche et la case à cocher dans la colonne **Hold** est sélectionnée par défaut. Cela indique qu’une conservation sera placée sur les sources de données que vous avez associées à chaque consignateur. Laissez ces cases à cocher sélectionnées pour conserver ces données.

7. Dans la page **Paramètres de** conservation, cliquez sur **Suivant** pour passer en revue les paramètres des consignatateurs. Cliquez sur **Envoyer** pour ajouter les consignatateurs au cas.

Pour plus d’informations sur l’ajout et la conservation de sources de données dans un cas eDiscovery (Premium), consultez :

- [Ajouter des consignatateurs à un cas eDiscovery (Premium)](add-custodians-to-case.md)

- [Ajouter des sources de données non liées à la garde à un cas eDiscovery (Premium)](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Collecter Teams contenu et ajouter à l’ensemble de révisions

Après avoir ajouté des consignats au cas et conservé le contenu dans les sources de données de consignation, l’étape suivante du flux de travail consiste à rechercher Teams contenu pertinent pour votre investigation et à l’ajouter à un ensemble de révisions pour une révision et une analyse plus approfondies. Bien qu’il soit courant de collecter Teams contenu avec le contenu d’autres services Microsoft 365 tels que la messagerie électronique dans Exchange et les documents dans SharePoint, cette section se concentre spécifiquement sur la collecte Teams contenu dans une collection. Vous pouvez créer des collections supplémentaires qui collectent du contenu non Teams à ajouter à un ensemble de révisions.

Lorsque vous collectez Teams contenu pour un cas, le flux de travail comporte deux étapes :

1. **Créez un brouillon de collection**.  La première étape consiste à créer un *brouillon de collection*, qui est une estimation des éléments qui correspondent à vos critères de recherche. Vous pouvez afficher des informations sur les résultats correspondant à la requête de recherche, telles que le nombre total et la taille des éléments trouvés, les différentes sources de données où ils ont été trouvés et des statistiques sur la requête de recherche. Vous pouvez également afficher un aperçu d’un exemple d’éléments renvoyés par la collection. À l’aide de ces statistiques, vous pouvez modifier la requête de recherche et réexécuter le brouillon de la collection autant de fois que nécessaire pour limiter les résultats jusqu’à ce que vous soyez satisfait de la collecte du contenu pertinent pour votre cas.

2. **Validez un brouillon de collection dans un jeu de révision**. Une fois que vous êtes satisfait des résultats d’un brouillon de collection, vous pouvez valider la collection dans un ensemble de révisions. Lorsque vous validez un brouillon de collection, les éléments retournés par la collection sont ajoutés à un ensemble de révisions à des fins de révision, d’analyse et d’exportation.

Vous avez également la possibilité de ne pas exécuter un brouillon de collection et d’ajouter directement les résultats de la collection à un ensemble de révisions lorsque vous créez et exécutez la collection.

Pour créer une collection de contenu Teams :

1. Accédez au cas eDiscovery (Premium) auquel vous avez ajouté les consignatateurs dans la section précédente, puis cliquez sur **Collections**.

2. Dans la page **Collections**, sélectionnez **Nouvelle** **collectionStandard** > .

3. Tapez un nom (obligatoire) et une description (facultatif) pour la collection.

4. Dans la page **Sources de données custodiales** , cliquez sur **Sélectionner les consignatateurs** pour sélectionner les consignats que vous avez ajoutés au cas.

   La liste des consignats de cas s’affiche dans la page de menu volant **Sélectionner les consignatateurs** .

5. Sélectionnez un ou plusieurs consignatateurs, puis cliquez sur **Ajouter**.

   Une fois que vous avez ajouté des consignatateurs spécifiques à la collection, une liste de sources de données spécifiques pour chaque consignateur s’affiche. Il s’agit des sources de données que vous avez configurées lorsque vous avez ajouté le consignateur au cas. Toutes les sources de données des consignats sont sélectionnées par défaut. Cela inclut les Teams ou les canaux que vous avez associés à un consignateur.

   Nous vous recommandons d’effectuer les opérations suivantes lors de la collecte Teams contenu :

   - Supprimez les comptes OneDrive des consignatateurs de l’étendue de la collection (en désélectionnant la case à cocher dans la colonne **OneDrive du consignateur** pour chaque consignateur). Cela empêche la collecte des fichiers en double qui ont été attachés à des conversations 1:1 et des conversations de groupe. Les pièces jointes cloud sont collectées automatiquement à partir de chaque conversation trouvée dans la collection lorsque vous validez le projet de collection dans le jeu de révisions. En utilisant cette méthode (au lieu de rechercher OneDrive comptes dans le cadre de la collection), les fichiers joints à 1:1 et les conversations de groupe sont regroupés dans la conversation dans laquelle ils ont été partagés.

   - Désélectionnez la case dans la colonne **De site supplémentaire** pour supprimer les sites SharePoint contenant des fichiers partagés dans des canaux privés ou partagés. Cela élimine la collecte des fichiers en double qui ont été attachés à des conversations de canal privé ou partagé, car ces pièces jointes cloud sont automatiquement ajoutées au jeu de révision lorsque vous validez le projet de collection et regroupés dans les conversations dans lesquelles ils ont été partagés.

6. Si vous avez suivi les étapes précédentes pour ajouter Teams contenu en tant que sources de données de conservation, vous pouvez ignorer cette étape et sélectionner **Suivant**. Sinon, dans la page de l’Assistant **Sources de données non liées** à la garde, vous pouvez choisir des sources de données non liées à la garde qui contiennent Teams contenu que vous avez peut-être ajouté au cas pour effectuer une recherche dans la collection.

7. Si vous avez suivi les étapes précédentes pour ajouter Teams contenu en tant que sources de données de conservation, vous pouvez ignorer cette étape et sélectionner **Suivant**. Sinon, dans la page De l’Assistant **Emplacements supplémentaires** , vous pouvez ajouter d’autres sources de données à rechercher dans la collection. Par exemple, vous pouvez ajouter la boîte aux lettres et le site pour une équipe qui n’a pas été ajoutée en tant que source de données custodiale ou non custodiale. Sinon, sélectionnez **Suivant** et ignorez cette étape.

8. Dans la page De l’Assistant **Conditions**, configurez la requête de recherche pour collecter Teams contenu à partir des sources de données que vous avez spécifiées dans les pages précédentes de l’Assistant. Vous pouvez utiliser différents mots clés et conditions de recherche pour affiner l’étendue de la collection. Pour plus d’informations, consultez [Les requêtes de recherche de build pour les regroupements](building-search-queries.md).

   Pour vous assurer que la collection la plus complète de conversations Teams (y compris les conversations 1:1, les conversations de groupe et de canal) utilisent la condition **Type** et sélectionnez l’option **Messages instantanés**. Nous vous recommandons également d’inclure une plage de dates ou plusieurs mots clés pour limiter l’étendue de la collection aux éléments pertinents pour votre investigation. Voici une capture d’écran d’un exemple de requête utilisant les options **Type** et **Date** :

   ![Requête pour collecter Teams contenu.](..\media\TeamsConditionsQueryType.png)

9. Dans la page de l’Assistant **Enregistrer le brouillon ou collecter** , effectuez l’une des opérations suivantes, selon que vous souhaitez créer un brouillon ou valider la collection dans un ensemble de révisions.

   ![Enregistrez la collection brouillon ou la collection de validation.](..\media\TeamsDraftCommitCollection.png)

   1. **Enregistrez la collection en tant que brouillon**. Choisissez cette option pour créer un brouillon de collection. Comme expliqué précédemment, un brouillon de collection n’ajoute pas les résultats de la collection à un ensemble de révisions. Elle retourne une estimation des résultats de recherche qui correspondent à la requête de recherche pour les sources de données dans l’étendue de la collection. Cela vous donne la possibilité d’afficher [les statistiques et les rapports de collection[(collection-statistics-reports.md)] et de modifier et réexécuter le brouillon de la collection. Lorsque vous êtes satisfait du résultat d’un brouillon de collection, vous pouvez le valider dans un ensemble de révisions. Pour plus d’informations, consultez [Créer un projet de collection](create-draft-collection.md).

   2. **Collectez les éléments et ajoutez-les à un jeu de révision**. Choisissez cette option pour exécuter la collection, puis ajoutez les résultats à un ensemble de révisions. Vous pouvez ajouter la collection à un ensemble de révisions nouveau ou existant. Les options permettant de collecter des messages contextuels Teams conversation (également appelés *threads de conversation*) et de collecter des pièces jointes cloud sont sélectionnées par défaut et ne peuvent pas être désélectionnées. Ces options sont appliquées automatiquement en raison du nouveau format de cas que vous avez utilisé lors de la création initiale du cas pour Teams contenu. Pour plus d’informations sur la validation de regroupements dans un ensemble de révisions, consultez [Valider un brouillon de collection dans un ensemble de révisions](commit-draft-collection.md).

10. Une fois la configuration de la collection terminée, soumettez-la pour créer un brouillon ou collecter des éléments et les ajouter à un ensemble de révisions.

   Lorsque le processus d’ajout de la collection au jeu de révision est terminé, la valeur d’état de la collection sous l’onglet **Collections** est définie sur **Validé**.

## <a name="review-teams-content-in-a-review-set"></a>Examiner Teams contenu dans un ensemble de révisions

Une fois que vous avez ajouté des collections de Teams contenu à un ensemble de révisions, l’étape suivante consiste à examiner le contenu pour déterminer sa pertinence pour votre enquête et à l’éliminer si nécessaire. Un prérequis important pour passer en revue Teams contenu consiste à comprendre comment eDiscovery (Premium) traite Teams conversations et pièces jointes lors de leur ajout à un ensemble de révisions. Ce traitement de Teams contenu se traduit par les trois éléments suivants :

- **[Regroupement](#grouping)**. La façon dont les messages, les publications et les réponses Teams les conversations sont regroupés et présentés dans l’ensemble de révisions. Cela inclut également les pièces jointes dans les conversations de conversation sont extraites et regroupées dans la conversation.

- **[Thread de conversation de transcription](#transcript-conversation-threading)**. Comment eDiscovery (Premium) détermine le contenu supplémentaire d’une conversation à collecter pour fournir un contexte autour des éléments correspondant aux critères de collection.

- **[Déduplication](#deduplication-of-teams-content)**. Comment eDiscovery (Premium) gère le contenu Teams dupliqué.

- **[Métadonnées](#metadata-for-teams-content)**. Propriétés de métadonnées ajoutées par eDiscovery (Premium) à Teams contenu une fois qu’il a été collecté et ajouté à un ensemble de révisions.

Comprendre le regroupement, le thread de conversation, la déduplication et les métadonnées Teams vous aideront à optimiser la révision et l’analyse de Teams contenu. Cette section contient également [des conseils pour afficher Teams contenu dans un ensemble de révisions](#tips-for-viewing-teams-content-in-a-review-set).

### <a name="grouping"></a>Regroupement

Lorsque le contenu de Teams conversations de conversation est ajouté à un ensemble de révisions, les messages, les publications et les réponses des conversations sont agrégés dans des fichiers de transcription HTML. Une conversation de conversation unique peut avoir plusieurs fichiers de transcription. Une fonction importante de ces fichiers de transcription est de présenter Teams contenu en tant que conversations continues et non en tant que messages individuels (ou distincts). Cela permet de fournir un contexte pour les éléments correspondant aux critères de recherche de vos collections à l’étape précédente et de réduire le nombre d’éléments collectés dans le jeu de révision. Les transcriptions et les éléments associés peuvent être regroupés par *famille* ou *conversation*. Les éléments de la même famille ont la même valeur pour la propriété **de métadonnées FamilyId** . Les éléments de la même conversation ont la même valeur pour la propriété de métadonnées **ConversationId** .

Le tableau suivant décrit comment les différents types de contenu de conversation Teams sont regroupés par famille et conversation.

|type de contenu Teams|Regrouper par famille|Regrouper par conversation|
|---|---|---|
|Teams 1:1 et des conversations de groupe|Une transcription et toutes ses pièces jointes et éléments extraits partagent le même **FamilyId**. Chaque transcription a un **FamilyId** unique.|Tous les fichiers de transcription et leurs éléments de famille dans la même conversation partagent le même **ConversationId**. Cela inclut les éléments suivants : <ul><li>Tous les éléments et pièces jointes extraits de toutes les transcriptions qui partagent le même **ConversationId**.</li><li>Toutes les transcriptions pour la même conversation de conversation</li><li>Toutes les copies des consignats de chaque transcription</li><li>Transcriptions des collections suivantes de la même conversation de conversation</li></ul> <br/> Pour Teams 1:1 et les conversations de conversation de groupe, vous pouvez avoir plusieurs fichiers de transcription, chacun correspondant à un intervalle de temps différent dans la conversation. Étant donné que ces fichiers de transcription proviennent de la même conversation avec les mêmes participants, ils partagent le même **ConversationId**.|
|Conversations de canal standard, privées et partagées|Chaque billet et toutes les réponses et pièces jointes sont enregistrés dans sa propre transcription. Cette transcription et toutes ses pièces jointes et éléments extraits partagent le même **FamilyId**.|Chaque billet et ses pièces jointes et éléments extraits ont un **ConversationId** unique. S’il existe des collections ultérieures ou de nouvelles réponses du même billet, les transcriptions delta résultant de ces collections auront également le même **ConversationId**.|

Utilisez le contrôle **Groupe** dans la barre de commandes d’un jeu de révision pour afficher Teams contenu regroupé par famille ou conversation.

![Contrôle de groupe dans la barre de commandes.](..\media\TeamsGroupControl.png)

- Sélectionnez **Grouper les pièces jointes de la famille** pour afficher Teams contenu regroupé par famille. Chaque fichier de transcription s’affiche sur une ligne dans la liste des éléments de l’ensemble de révisions. Les pièces jointes sont imbriqués sous l’élément.

- Sélectionnez **Group Teams ou Yammer conversations** pour afficher Teams contenu regroupé par conversation. Chaque conversation s’affiche sur une ligne dans la liste des éléments de l’ensemble de révisions. Les fichiers de transcription et les pièces jointes sont imbriqués sous la conversation de niveau supérieur.

> [!NOTE]
> Les pièces jointes cloud sont regroupées avec les conversations dans lesquels elles apparaissent. Ce regroupement est effectué en affectant le même **FamilyId** que le fichier de transcription du message auquel le fichier a été attaché et le même **ConversationId** que la conversation dans laquelle le message est apparu. Cela signifie que plusieurs copies de pièces jointes cloud peuvent être ajoutées à l’ensemble de révisions si elles ont été jointes à différentes conversations.

#### <a name="viewing-transcript-files-for-conversations"></a>Affichage des fichiers de transcription pour les conversations

Lors de l’affichage des fichiers de transcription dans un jeu de révision, certains messages sont mis en surbrillance en violet. Les messages mis en surbrillance dépendent de la copie de la transcription que vous affichez. Par exemple, dans une conversation 1:1 entre User4 et User2, les messages publiés par User4 sont mis en surbrillance en violet lorsque vous affichez la transcription collectée à partir de la boîte aux lettres d’User4. Lorsque vous affichez la transcription de la même conversation par User2, les messages publiés par User2 sont mis en surbrillance en violet. Ce comportement de mise en surbrillance est basé sur la même expérience client Teams, où les publications d’un utilisateur sont mises en surbrillance en violet dans le client Teams.

Les captures d’écran suivantes montrent un exemple de conversation dans le client Teams et le fichier de transcription de la même conversation dans le jeu de révision. La mise en surbrillance violette dans le fichier de transcription indique que la transcription a été collectée à partir de la boîte aux lettres d’User2.

##### <a name="conversation-in-teams-client"></a>Conversation dans Teams client

![Conversation affichée dans le fichier de transcription du jeu de révision.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Conversation dans le fichier de transcription

![Même conversation affichée dans Teams client.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Thread de conversation de transcription

La fonctionnalité de thread de conversation dans le nouveau format de cas dans eDiscovery (Premium) vous permet d’identifier le contenu contextuel lié aux éléments susceptibles d’être pertinents pour votre investigation. Cette fonctionnalité produit des vues de conversation distinctes qui incluent des messages de conversation qui précèdent et suivent les éléments correspondant à la requête de recherche pendant la collecte. Cette fonctionnalité vous permet d’examiner efficacement et rapidement les conversations de conversation complètes (appelées *conversations thématiques*) dans Microsoft Teams. Comme expliqué précédemment, les conversations de conversation sont reconstruites dans des fichiers de transcription HTML quand eDiscovery (Premium) ajoute Teams contenu à un jeu de révision.

Voici la logique utilisée par eDiscovery (Premium) pour inclure des messages supplémentaires et des fichiers de transcription de réponses qui fournissent le contexte autour des éléments correspondent à la requête de collection (appelée *éléments réactifs*) que vous avez utilisée lors de la collecte Teams contenu. Les différents comportements de thread sont basés sur les types de conversations et la requête de recherche utilisée pour collecter les éléments réactifs. Il existe deux scénarios de collecte courants :

- Requêtes qui utilisent des paramètres de recherche, tels que des mots clés et des paires property:value

- Requêtes qui utilisent uniquement des plages de dates

|type de contenu Teams|Requêtes avec paramètres de recherche|Requêtes avec plages de dates|
|---|---|---|
|Teams 1:1 et des conversations de groupe|Les messages qui ont été publiés 12 heures avant et 12 heures après les éléments réactifs sont regroupés avec l’élément réactif dans un seul fichier de transcription.|Les messages d’une fenêtre de 24 heures sont regroupés dans un seul fichier de transcription.|
|Conversations de canal Teams standard, privées et partagées|Chaque billet qui contient des éléments réactifs et toutes les réponses correspondantes sont regroupés dans un seul fichier de transcription.|Chaque billet qui contient des éléments réactifs et toutes les réponses correspondantes sont regroupés dans un seul fichier de transcription.|

### <a name="deduplication-of-teams-content"></a>Déduplication du contenu Teams

La liste suivante décrit le comportement de déduplication (et de duplication) lors de la collecte de Teams contenu dans un jeu de révision.

- Chaque fichier de transcription ajouté à un jeu de révision doit être un mappage un-à-un au contenu stocké dans des emplacements de données. Cela signifie qu’eDiscovery (Premium) ne collecte pas de contenu Teams qui a déjà été ajouté au jeu de révision. Si un message de conversation est déjà collecté dans un jeu de révision, eDiscovery (Premium) n’ajoute pas le même message du même emplacement de données au jeu de révision dans les collections suivantes.

- Pour les conversations de groupe et 1:1, les copies des messages sont stockées dans la boîte aux lettres de chaque participant à la conversation. Les copies de la même conversation qui existent dans les boîtes aux lettres des différents participants sont collectées avec des métadonnées différentes. Par conséquent, chaque instance de la conversation est traitée comme unique et introduite dans le jeu de révision dans des fichiers de transcription distincts. Par conséquent, si tous les participants d’une conversation de groupe ou 1:1 sont ajoutés en tant que consignats dans un cas et inclus dans l’étendue d’une collection, des copies de chaque transcription (pour la même conservation) sont ajoutées au jeu de révision et seront regroupées avec le même **ConversationId**. Chacune de ces copies est associée à un consigna ateur correspondant. **Conseil** : la colonne **Custodian** dans la liste d’ensembles de révision identifie le consignateur pour le fichier de transcription correspondant.

- Dans les collections suivantes d’éléments de la même conversation, seul le contenu delta qui n’a pas été précédemment collecté est ajouté au jeu de révision et regroupé (en partageant le même **ConversationId**) avec les transcriptions précédemment collectées de la même conversation. Voici un exemple de ce comportement :

   1. La collection A collecte les messages d’une conversation entre User1 et User2 et ajoute à l’ensemble de révisions.

   2. La collection B collecte les messages de la même conversation, mais il existe de nouveaux messages entre User1 et User2 depuis l’exécution de la collection A.

   3. Seuls les nouveaux messages de la collection B sont ajoutés au jeu de révision. Ces messages sont ajoutés à un fichier de transcription distinct, mais la nouvelle transcription est regroupée avec les transcriptions de la collection A par le même **ConversationId**.

   Ce comportement s’applique à tous les types de conversations Teams.

### <a name="metadata-for-teams-content"></a>Métadonnées pour Teams contenu

Dans les ensembles de révision volumineux avec des milliers ou des millions d’éléments, il peut être difficile de limiter l’étendue de votre révision à Teams contenu. Pour vous aider à concentrer votre révision sur Teams contenu, il existe des propriétés de métadonnées spécifiques à Teams contenu. Vous pouvez utiliser ces propriétés pour organiser les colonnes de la liste de révision et [configurer des filtres et des requêtes](review-set-search.md) pour optimiser la révision de Teams contenu. Ces propriétés de métadonnées sont également incluses lorsque vous exportez du contenu Teams à partir d’eDiscovery (Premium), pour vous aider à organiser et afficher du contenu après l’exportation ou dans des outils eDiscovery tiers.

Le tableau suivant décrit les propriétés de métadonnées pour Teams contenu.

|Propriété de métadonnées|Description|
|---|---|
|ContainsEditedMessage|Indique si un fichier de transcription contient un message modifié. Les messages modifiés sont identifiés lors de l’affichage du fichier de transcription.|
|ConversationId|GUID qui identifie la conversation à laquelle l’élément est associé. Les fichiers de transcription et pièces jointes de la même conversation ont la même valeur pour cette propriété.|
|Nom de la conversation|Nom de la conversation à qui le fichier de transcription ou la pièce jointe est associé. Pour Teams 1:1 et les conversations de groupe, la valeur de cette propriété est l’UPN de tous les participants à la conversation sont concaténés. Par exemple, `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams conversation de canal (standard, privé et partagé) utilise le format suivant pour le nom de la conversation : `<Team name>,<Channel name>`. Par exemple, `eDiscovery vNext, General`.|
|ConversationType|Indique le type de conversation d’équipe. Pour Teams 1:1 et les conversations de groupe, la valeur de cette propriété est `Group`. Pour les conversations de canal standard, privées et partagées, la valeur est `Channel`.|
|Date|Horodatage du premier message dans le fichier de transcription.|
|FamilyId|GUID qui identifie le fichier de transcription pour une conversation de conversation. Les pièces jointes ont la même valeur pour cette propriété que le fichier de transcription qui contient le message auquel le fichier a été attaché.|
|FileClass|Indique ce type de contenu. Les éléments de Teams conversations ont la valeur `Conversation`. En revanche, Exchange messages électroniques ont la valeur `Email`.|
|MessageKind|Propriété de type message. Teams contenu a la valeur `microsoftteams , im`.|
|Destinataires|Liste de tous les utilisateurs qui ont reçu un message dans la conversation de transcription.|
|TeamsChannelName|Nom de canal Teams de la transcription.|

Pour obtenir des descriptions d’autres propriétés de métadonnées eDiscovery (Premium[), consultez Les champs de métadonnées de document dans eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="export-teams-content"></a>Exporter du contenu Teams

Une fois que vous avez examiné et éliminé Teams contenu dans un jeu de révision, vous pouvez exporter les fichiers de transcription qui contiennent du contenu qui répond à votre enquête. Il n’existe aucun paramètre d’exportation spécifique pour Teams contenu. Chaque fichier de transcription est exporté sous forme de fichier de message HTML. Ce fichier contient également des balises CDATA masquées avec toutes les métadonnées pour les messages de conversation individuels. Les propriétés de métadonnées décrites dans la section précédente sont incluses lorsque Teams contenu est exporté.  

Chaque fichier de transcription est référencé dans le fichier de chargement et peut être localisé à l’aide du chemin d’accès relatif dans le champ Export_native_path du fichier de chargement. Les fichiers de transcription se trouvent dans le dossier Conversations dans le dossier d’exportation racine.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Astuces pour afficher Teams contenu dans un ensemble de révisions

Voici quelques conseils et bonnes pratiques pour afficher Teams contenu dans un ensemble de révisions.

- Utilisez le contrôle **Personnaliser les colonnes** dans la barre de commandes pour ajouter et organiser des colonnes afin d’optimiser la révision de Teams contenu.

  ![Utilisez la page de menu volant Modifier la colonne pour ajouter, supprimer et organiser des colonnes.](..\media\EditReviewSetColumns.png)

   Vous pouvez ajouter et supprimer des colonnes utiles pour Teams contenu. Vous pouvez également séquencer l’ordre des colonnes en les faisant glisser et les déposer dans la page de menu volant **Modifier la colonne** . Vous pouvez également trier sur des colonnes pour regrouper Teams contenu avec des valeurs similaires pour la colonne sur laquelle vous effectuez le tri.

- Les colonnes utiles pour vous aider à passer en revue Teams contenu incluent **le consignataire**, **les destinataires** et le **type de fichier** ou **le type de message**.

- Utilisez [des filtres pour les propriétés](review-set-search.md) liées à Teams pour afficher rapidement Teams contenu. Il existe des filtres pour la plupart des propriétés de métadonnées décrites dans la section précédente.

## <a name="deleting-teams-chat-messages"></a>Suppression de messages de conversation Teams

Vous pouvez utiliser eDiscovery (Premium) et Microsoft Graph Explorer pour répondre aux incidents de débordement de données, lorsque du contenu contenant des informations confidentielles ou malveillantes est publié par le biais de messages de conversation Teams. Les administrateurs de votre organisation peuvent rechercher et supprimer des messages de conversation dans Microsoft Teams. Cela peut vous aider à supprimer des informations sensibles ou du contenu inapproprié dans Teams messages de conversation. Pour plus d’informations, consultez [Rechercher et vider les messages de conversation dans Teams](search-and-delete-Teams-chat-messages.md).

## <a name="reference-guide"></a>Guide de référence

Voici un guide de référence rapide pour l’utilisation d’eDiscovery (Premium) pour Microsoft Teams. Ce guide récapitule les points clés permettant d’utiliser eDiscovery (Premium) pour conserver, collecter, examiner et exporter du contenu à partir de Microsoft Teams.

![Miniature du guide de référence pour l’utilisation d’eDiscovery (Premium) pour Microsoft Teams.](../media/AeDTeamsReferenceGuide-thumbnail.png)

[Télécharger en tant que fichier PDF](https://download.microsoft.com/download/9/e/4/9e4eec6f-c476-452f-b414-4bd4b5c39dca/AeDTeamsReferenceGuide.pdf)
