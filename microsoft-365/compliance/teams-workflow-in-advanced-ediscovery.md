---
title: Flux de travail Teams dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: jefwan
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection: M365-security-compliance
description: Découvrez comment conserver, collecter, réviser et exporter du contenu à partir de Microsoft Teams dans Advanced eDiscovery.
ms.openlocfilehash: 462442d2319c2c199d39795b77b67c6dcefdb758
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573234"
---
# <a name="advanced-ediscovery-workflow-for-content-in-microsoft-teams-using-large-cases-preview"></a>Advanced eDiscovery flux de travail pour le contenu Microsoft Teams à l’aide de grands cas (aperçu)

Cet article fournit un ensemble complet de procédures, de directives et de meilleures pratiques pour l’utilisation de Advanced eDiscovery pour conserver, collecter, examiner et exporter du contenu à partir de Microsoft Teams. L’objectif de cet article est de vous aider à optimiser votre flux de travail eDiscovery pour Teams contenu.

Il existe quatre catégories de contenu Teams que vous pouvez collecter et traiter à l’aide de Advanced eDiscovery :

- **Teams conversations en 1:1.** Messages de conversation, publications et pièces jointes partagés dans une conversation Teams conversation entre deux personnes.  Teams conversations 1:1 sont également appelées *conversations.*

- **Teams conversations de groupe.** Messages de conversation, publications et pièces jointes partagés dans Teams conversation entre trois personnes ou plus. Également *appelées conversations 1:N* ou *conversations de groupe.*

- **Teams canaux.** Messages de conversation, publications, réponses et pièces jointes partagés dans un canal Teams de conversation.

- **Canaux Teams privés.** Messages, réponses et pièces jointes partagés dans un canal Teams privé.

## <a name="where-teams-content-is-stored"></a>Où Teams contenu est stocké

Une condition préalable à la gestion du contenu Teams dans Advanced eDiscovery consiste à comprendre le type de contenu Teams que vous pouvez collecter, traiter et examiner dans Advanced eDiscovery et où ce contenu est stocké dans Microsoft 365. Le tableau suivant répertorie Teams type de contenu et l’endroit où chacun d’eux est stocké.

||Emplacement des messages de conversation et des publications  |Emplacement des fichiers et des pièces jointes |
|:---------|:---------|:---------|
|Teams conversations 1:1     |Les messages des conversations 1:1 sont stockés dans la boîte aux lettres Exchange Online tous les participants de la conversation. |Les fichiers partagés dans une conversation 1:1 sont stockés dans le compte OneDrive Entreprise de la personne qui a partagé le fichier. |
|Teams de groupe     |Les messages des conversations de groupe sont stockés dans la boîte Exchange Online de tous les participants à la conversation. |Les fichiers partagés dans les conversations de groupe sont stockés dans le OneDrive Entreprise de la personne qui a partagé le fichier. |
|Équipes et canaux     |Tous les messages et publications de canal sont stockés dans la boîte Exchange Online boîte aux lettres associée à l’équipe.|Les fichiers partagés dans un canal sont stockés dans le site SharePoint Online associé à l’équipe.           |
|Canaux Teams privés     |Les messages envoyés dans un canal privé sont stockés dans Exchange Online boîtes aux lettres de tous les membres du canal privé.|Les fichiers partagés dans un canal privé sont stockés dans un site SharePoint Online dédié associé au canal privé.|
||||

## <a name="create-a-case-for-teams-content"></a>Créer un cas pour le contenu Teams contenu

La première étape de la gestion Teams contenu Advanced eDiscovery consiste à créer un cas à l’aide du format de cas de grande taille optimisé pour la gestion Teams contenu. Voici les avantages de l’utilisation du format de cas de grande taille pour Teams contenu :

- Prise en charge du thread de conversation, dans lequel les messages supplémentaires dans la même conversation qui incluent des éléments réactifs sont automatiquement collectés et ajoutés aux ensembles de révision.

- Teams conversations sont automatiquement ajoutées aux ensembles de révision en tant que fichier de transcription HTML. Les pièces jointes cloud partagées dans les conversations sont également ajoutées au jeu à réviser. Cela permet de fournir un contexte aux conversations avec des éléments réactifs et de réduire le nombre total d’éléments produits par le contenu basé sur la conversation.

- Des collections d’une taille de 1 To peuvent être ajoutées aux ensembles de révision, ce qui vous permet de collecter et d’obtenir de grandes quantités de Teams contenu dans un cas.

Pour plus d’informations sur l’augmentation des limites de cas pour les cas de grande [taille,](advanced-ediscovery-large-cases.md)voir Utiliser les cas importants Advanced eDiscovery .

Pour créer un cas important :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur **eDiscovery > Advanced**.

3. Dans la page **Advanced eDiscovery,** cliquez sur l’onglet **Cas,** puis cliquez **sur Créer un cas.**

   La page de présentation du nouveau cas **eDiscovery** s’affiche. La section **Format de** cas offre la possibilité de créer un cas important.

   ![Option de cas de grande taille dans la page Nouveau cas eDiscovery.](..\media\AeDLargeCases1.png)

4. Après avoir nommé le  cas, sélectionnez l’option Grand cas, puis cliquez sur **Enregistrer** pour créer le cas important.

## <a name="add-teams-custodial-data-sources-and-preserve-teams-content"></a>Ajouter Teams sources de données de conservation et conserver Teams contenu  

L’étape suivante consiste à identifier les utilisateurs qui sont les dépositaires de données dans votre enquête et à les ajouter, ainsi que leurs emplacements de contenu, en tant que dépositaires au cas que vous avez créé dans la section précédente. Lorsque vous ajoutez des dépositaires, vous pouvez spécifier leur boîte aux lettres OneDrive compte en tant que sources de données de conservation. Vous pouvez également spécifier Teams de contenu en tant que sources de données de dépositaire pour placer rapidement ces emplacements en conservation légale afin de conserver le contenu pendant votre enquête. Il facilite également la collecte de contenu et son ajout à un jeu à réviser.

Pour ajouter des dépositaires à un cas et conserver les sources de données conservées :

1. Go to the Advanced eDiscovery case that you created in the previous section, and then click **Data sources**.

2. Dans la page **Sources de données,** cliquez **sur Ajouter une source de données** Ajouter de nouveaux  >  **dépositaires.**

3. Dans **l’Assistant** Nouveau dépositaire, ajoutez un ou plusieurs utilisateurs en tant que dépositaires au cas en tapant la première partie du nom ou de l’alias de l’utilisateur. Une fois que vous avez trouvé la personne correcte, sélectionnez son nom pour l’ajouter à la liste.  

4. Développez chaque dépositaire pour afficher les sources de données principales qui ont été automatiquement associées au dépositaire et pour sélectionner d’autres emplacements à associer au dépositaire.

   ![Sources de données du dépositaire.](..\media\TeamsCustodialDataLocations1.png)

5. Suivez ces instructions pour ajouter des sources de données de garde Teams contenu. Cliquez **sur Modifier** pour ajouter un emplacement de données.

   - **Boîtes aux lettres**. La boîte aux lettres du dépositaire est sélectionnée par défaut. Conservez cette sélection pour ajouter (et conserver) des conversations 1:1, des conversations de groupe et des conversations de canal privé en tant que données de conservation.

   - **OneDrives**. Le compte de OneDrive du dépositaire est sélectionné par défaut. Conservez cette valeur sélectionnée pour ajouter (et conserver) des fichiers partagés dans des conversations 1:1 et des conversations de groupe en tant que données de garde.

   - **SharePoint**. Ajoutez le site SharePoint associé à n’importe quel canal privé dont le dépositaire est membre pour ajouter (et conserver) en tant que données de conservation les fichiers partagés dans le canal privé. Cliquez **sur** Modifier, puis ajoutez l’URL SharePoint site associé à un canal privé. Pour découvrir comment localiser les canaux privés dont un utilisateur est membre, voir [eDiscovery des canaux privés.](/microsoftteams/ediscovery-investigation#ediscovery-of-private-channels)

   - **Teams**. Ajoutez les équipes dont le dépositaire est membre pour ajouter (et conserver) en tant que données de conservation tous les messages de canal et tous les fichiers partagés à un canal Teams données. Lorsque vous cliquez **sur Modifier,** la boîte aux lettres et le site associés à chaque équipe dont le dépositaire est membre sont affichés dans une liste. Sélectionnez les équipes que vous souhaitez associer au dépositaire. Vous devez sélectionner la boîte aux lettres et le site correspondants pour chaque équipe.

   > [!NOTE]
   > Vous pouvez également ajouter la boîte aux lettres et le site d’Teams dont les dépositaires ne sont pas membres en tant qu’emplacement de données de dépositaire. Pour ce faire, cliquez sur **Modifier** en Exchange **et** **SharePoint** puis ajoutez la boîte aux lettres et le site associés à l’équipe.

6. Après avoir ajouté des dépositaires et configuré les sources de données de conservation, cliquez sur **Suivant** pour afficher la page **paramètres de conservation.**

   Une liste des dépositaires s’affiche et  la case à cocher dans la colonne Conservation est sélectionnée par défaut. Cela indique qu’une conservation sera placée sur les sources de données que vous avez associées à chaque dépositaire. Laissez ces case à cocher sélectionnées pour conserver ces données.

7. Dans la page **Paramètres de conservation,** cliquez sur **Suivant** pour passer en revue les paramètres des dépositaires. Cliquez **sur Envoyer** pour ajouter les dépositaires au cas.

Pour plus d’informations sur l’ajout et la conservation de sources de données dans Advanced eDiscovery cas, voir :

- [Ajouter des dépositaires à un Advanced eDiscovery de données](add-custodians-to-case.md)

- [Ajouter des sources de données non privatives à un Advanced eDiscovery de données](non-custodial-data-sources.md)

## <a name="collect-teams-content-and-add-to-review-set"></a>Collecter Teams contenu et ajouter au jeu à réviser

Après l’ajout de dépositaires au cas et la conservation du contenu dans les sources de données des dépositaires, l’étape suivante du flux de travail consiste à rechercher du contenu Teams pertinent pour votre examen et à l’ajouter à un groupe de révision pour une analyse et une analyse plus approfondies. Bien qu’il soit courant de collecter du contenu Teams avec du contenu provenant d’autres services Microsoft 365 tels que le courrier électronique dans des Exchange et des documents en SharePoint, cette section se concentre spécifiquement sur la collecte de contenu Teams dans une collection. Vous pouvez créer des collections supplémentaires qui collectent du contenu non Teams à ajouter à un jeu à réviser.

Lorsque vous collectez Teams contenu pour un cas, le flux de travail se présente en deux étapes :

1. **Créez un brouillon de collection.**  La première étape consiste à créer une *collection* provisoire, qui est une estimation des éléments qui correspondent à vos critères de recherche. Vous pouvez afficher des informations sur les résultats qui correspondent à la requête de recherche, telles que le nombre total et la taille des éléments trouvés, les différentes sources de données où ils ont été trouvés et les statistiques sur la requête de recherche. Vous pouvez également afficher un aperçu d’un exemple d’éléments qui ont été renvoyés par la collection. À l’aide de ces statistiques, vous pouvez modifier la requête de recherche et réexécuter le brouillon de la collection autant de fois que nécessaire pour affiner les résultats jusqu’à ce que vous êtes satisfait de collecter le contenu pertinent pour votre cas.

2. **Valider un brouillon de collection dans un jeu à réviser**. Une fois que vous êtes satisfait des résultats d’un brouillon de collection, vous pouvez valider la collection dans un jeu à réviser. Lorsque vous valider un brouillon de collection, les éléments renvoyés par la collection sont ajoutés à un jeu à réviser pour révision, analyse et exportation.

Vous avez également la possibilité de ne pas exécuter un brouillon de collection et d’ajouter les résultats de la collection directement à un jeu à réviser lorsque vous créez et exécutez la collection.

Pour créer une collection de Teams contenu :

1. Go to the Advanced eDiscovery case that you added the custodians to in the previous section, and then click **Collections**.

2. Dans la page **Collections,** **sélectionnez Nouvelle collection**  >  **Standard.**

3. Tapez un nom (obligatoire) et une description (facultatif) pour la collection.

4. Dans la page **Des sources de données** de conservation, cliquez sur Sélectionner les **dépositaires** pour sélectionner les dépositaires que vous avez ajoutés au cas.

   La liste des dépositaires de cas s’affiche dans la page de présentation Sélectionner des **dépositaires.**

5. Sélectionnez un ou plusieurs dépositaires, puis cliquez sur **Ajouter.**

   Une fois que vous avez ajouté des dépositaires spécifiques à la collection, une liste de sources de données spécifiques pour chaque dépositaire s’affiche. Voici les sources de données que vous avez configurées lorsque vous avez ajouté le dépositaire au cas. Toutes les sources de données des dépositaires sont sélectionnées par défaut. Cela inclut les Teams et les canaux privés que vous avez associés à un dépositaire.

   Nous vous recommandons de faire les choses suivantes lors de la collecte Teams contenu :

   - Supprimez les comptes OneDrive des dépositaires de **l’étendue** collection (en désélectionne la case à cocher dans la colonne OneDrive du dépositaire pour chaque dépositaire). Cela empêche la collection de fichiers en double qui ont été joints à des conversations 1:1 et à des conversations de groupe. Les pièces jointes cloud sont automatiquement collectées à partir de chaque conversation trouvée dans la collection lorsque vous validerez le brouillon de la collection dans le jeu à réviser. À l’aide de cette méthode (au lieu de rechercher des comptes OneDrive dans le cadre de la collection), les fichiers joints à 1:1 et aux conversations de groupe sont regroupés dans la conversation dans qui ils ont été partagés.

   - Désélectionne la case  à cocher dans la colonne Site supplémentaire pour supprimer les sites SharePoint contenant des fichiers partagés dans des canaux privés. Cela permet d’éliminer la collecte des fichiers en double joints aux conversations de canal privé, car les pièces jointes au cloud jointes aux conversations de canal privé sont automatiquement ajoutées à l’ensemble de révision lorsque vous validerez la collection de brouillons et regroupées dans les conversations qui ont été partagées.

6. Si vous avez précédemment suivi les étapes d’ajout Teams contenu en tant que sources de données de dépositaire, vous pouvez ignorer cette étape et sélectionner **Suivant**. Dans le cas contraire, dans la page De l’Assistant Sources de données non privatives, vous pouvez choisir des sources de données qui ne contiennent pas de Teams contenu que vous avez **peut-être** ajouté au cas pour effectuer une recherche dans la collection.

7. Si vous avez précédemment suivi les étapes d’ajout Teams contenu en tant que sources de données de dépositaire, vous pouvez ignorer cette étape et sélectionner **Suivant**. Dans le cas contraire, dans la page **De l’Assistant** Emplacements supplémentaires, vous pouvez ajouter d’autres sources de données pour effectuer des recherches dans la collection. Par exemple, vous pouvez ajouter la boîte aux lettres et le site d’une équipe qui n’a pas été ajouté en tant que source de données de garde ou non. Dans le cas contraire, **sélectionnez Suivant** et ignorez cette étape.

8. Dans la page **De l’Assistant** Conditions, configurez la requête de recherche pour collecter Teams contenu des sources de données que vous avez spécifiées dans les pages précédentes de l’Assistant. Vous pouvez utiliser différents mots clés et conditions de recherche pour affiner l’étendue de la collection. Pour plus d’informations, [voir Créer des requêtes de recherche pour les collections.](building-search-queries.md)

   Pour vous assurer que la collection la plus complète de conversations Teams (y compris 1:1, groupe, canal et conversations privées) utilisez la condition **Type** et sélectionnez l’option **Messages** instantanés. Nous vous recommandons également d’inclure une plage de dates ou plusieurs mots clés pour restreindre l’étendue de la collection aux éléments pertinents pour votre enquête. Voici une capture d’écran d’un exemple de requête à l’aide des options **Type** et **Date** :

   ![Requête pour collecter Teams contenu.](..\media\TeamsConditionsQueryType.png)

9. Dans la page **Enregistrer** le brouillon ou Collecter l’Assistant, faites l’une des choses suivantes selon que vous souhaitez créer un brouillon de collection ou valider la collection dans un jeu à réviser.

   ![Enregistrez la collection brouillon ou la collection de validation.](..\media\TeamsDraftCommitCollection.png)

   1. **Enregistrer la collection en tant que brouillon**. Choisissez cette option pour créer un brouillon de collection. Comme indiqué précédemment, un brouillon de collection n’ajoute pas les résultats de la collection à un jeu à réviser. Elle renvoie une estimation des résultats de recherche qui correspondent à la requête de recherche pour les sources de données dans l’étendue de la collection. Cela vous permet d’afficher [statistiques et rapports de collection[(collection-statistics-reports.md)] et de modifier et réexécuter la collection provisoire. Lorsque vous êtes satisfait du résultat d’un brouillon de collection, vous pouvez le valider dans un jeu à réviser. Pour plus d’informations, [voir Créer un brouillon de collection.](create-draft-collection.md)

   2. **Collectez des éléments et ajoutez-les à un jeu à réviser.** Choisissez cette option pour exécuter la collection, puis ajoutez les résultats à un jeu à réviser. Vous pouvez ajouter la collection à un jeu à réviser nouveau ou existant. Les options de collecte de messages Teams conversation contextuels (également appelées threads de *conversation)* et de collecte des pièces jointes cloud sont sélectionnées par défaut et ne peuvent pas être désélectionnés. Ces options sont appliquées automatiquement en raison du format de cas important que vous avez utilisé lors de la création initiale du nouveau cas pour Teams contenu. Pour plus d’informations sur la validation de collections dans un jeu à réviser, voir Valider un brouillon [de collection dans un jeu à réviser.](commit-draft-collection.md)

10. Une fois la configuration de la collection terminée, soumettez-la pour créer un brouillon de collection ou collectez des éléments et ajoutez-les à un jeu à réviser.

   Lorsque le processus d’ajout de la collection au jeu à réviser est terminé, la valeur d’état de la collection sous l’onglet **Collections** est définie sur **Committed**.

## <a name="review-teams-content-in-a-review-set"></a>Examiner le Teams contenu d’un jeu à réviser

Une fois que vous avez ajouté des collections de contenu Teams à un groupe de révision, l’étape suivante consiste à examiner le contenu pour en déterminer la pertinence par rapport à votre enquête et à l’annuler si nécessaire. Une condition préalable importante à la révision du contenu Teams consiste à comprendre comment Advanced eDiscovery traite Teams conversations et pièces jointes lors de leur ajout à un jeu à réviser. Ce traitement de Teams contenu se traduit par les trois éléments suivants :

- **[Regroupement.](#grouping)** Comment les messages, les publications et les réponses Teams conversations sont regroupés et présentés dans le jeu à réviser. Cela inclut également les pièces jointes dans les conversations de conversation sont extraites et regroupées dans la conversation.

- **[Threads de conversation de transcription.](#transcript-conversation-threading)** Comment Advanced eDiscovery le contenu supplémentaire d’une conversation à collecter pour fournir un contexte autour des éléments qui correspondent aux critères de la collection.

- **[Déduplication](#deduplication-of-teams-content)**. La façon Advanced eDiscovery gérer les doublons Teams contenu.

- **[Métadonnées](#metadata-for-teams-content)**. Propriétés de métadonnées Advanced eDiscovery ajoutées Teams contenu une fois qu’il est collecté et ajouté à un jeu à réviser.

Comprendre les métadonnées de regroupement, de thread de conversation, de déduplication et de Teams vous permet d’optimiser la révision et l’analyse Teams contenu. Cette section contient également des [conseils pour afficher Teams contenu dans un jeu à réviser.](#tips-for-viewing-teams-content-in-a-review-set)

### <a name="grouping"></a>Regroupement

Lorsque le contenu de Teams conversations est ajouté à un groupe de révision, les messages, les publications et les réponses des conversations sont regroupés dans des fichiers de transcription HTML. Une conversation unique peut avoir plusieurs fichiers de transcription. Une fonction importante de ces fichiers de transcription consiste à présenter Teams contenu sous forme de conversations continues et non en tant que messages individuels (ou distincts). Cela permet de fournir du contexte pour les éléments qui correspondent aux critères de recherche de vos collections à l’étape précédente et de réduire le nombre d’éléments collectés dans le jeu à réviser. Les transcriptions et les éléments associés peuvent être regroupés par *famille ou* *conversation.* Les éléments de la même famille auront la même valeur pour la **propriété de métadonnées FamilyId.** Les éléments de la même conversation auront la même valeur pour la propriété de métadonnées **ConversationId.**

Le tableau suivant décrit comment les différents types de Teams de conversation sont regroupés par famille et conversation.

| Teams type de contenu|Grouper par famille  |Grouper par conversation  |
|:---------|:---------|:---------|
|Teams 1:1 et conversations de groupe   | Une transcription et toutes ses pièces jointes et éléments extraits partagent le **même FamilyId**. Chaque transcription possède un **FamilyId** unique. |Tous les fichiers de transcription et leurs éléments de famille dans la même conversation partagent le même **ConversationId**. Cela inclut les éléments suivants :<br/><br/>  - Tous les éléments et pièces jointes extraits de toutes les transcriptions qui partagent le même **ConversationId**. <br/> - Toutes les transcriptions d’une même conversation<br/> - Toutes les copies de dépositaire de chaque transcription<br/> - Transcriptions des collections suivantes de la même conversation de conversation <br/><br/>  Pour Teams 1:1 et les conversations de groupe, vous pouvez avoir plusieurs fichiers de transcription, chacun correspondant à une période différente dans la conversation. Étant donné que ces fichiers de transcription sont issus de la même conversation avec les mêmes participants, ils partagent le même **ConversationId**.|
|Teams canal privé et les conversations de canal privé    | Chaque billet et toutes les réponses et pièces jointes sont enregistrés dans sa propre transcription. Cette transcription et toutes ses pièces jointes et éléments extraits partagent le **même FamilyId**.         |Chaque billet et ses pièces jointes et éléments extraits ont un **ConversationId** unique. S’il existe des collections ultérieures ou de nouvelles réponses à partir du même billet, les transcriptions delta résultant de ces collections auront également le même **ConversationId**.|
||||

Utilisez le **contrôle Groupe** dans la barre de commandes d’un jeu à réviser pour afficher Teams contenu groupé par famille ou conversation.

![Contrôle de groupe dans la barre de commandes.](..\media\TeamsGroupControl.png)

- Sélectionnez **les pièces jointes de la** famille de groupes pour Teams contenu groupé par famille. Chaque fichier de transcription s’affiche sur une ligne de la liste des éléments de révision. Les pièces jointes sont imbrmbrées sous l’élément.

- Sélectionnez **groupe Teams ou Yammer conversations** pour afficher Teams contenu regroupé par conversation. Chaque conversation s’affiche sur une ligne de la liste des éléments de révision. Les fichiers et pièces jointes de transcription sont imbrmbrés dans la conversation de niveau supérieur.

> [!NOTE]
> Les pièces jointes dans le cloud sont regroupées avec les conversations dans qui elles apparaissent. Ce regroupement s’accomplit en attribuant le **même ID** de famille que le fichier de transcription du message à qui le fichier a été joint et le même **ConversationId** que la conversation dans la conversation dans qui le message est apparu. Cela signifie que plusieurs copies de pièces jointes cloud peuvent être ajoutées au jeu à réviser si elles ont été jointes à différentes conversations.

#### <a name="viewing-transcript-files-for-conversations"></a>Affichage des fichiers de transcription pour les conversations

Lorsque vous affichez des fichiers de transcription dans un jeu à réviser, certains messages sont mis en surbrillant en violet. Les messages mis en surbrillez dépendent de la copie du dépositaire de la transcription que vous affichez. Par exemple, dans une conversation 1:1 entre User4 et User2, les messages publiés par User4 sont mis en surbrillant en violet lorsque vous affichez la transcription collectée à partir de la boîte aux lettres de User4. Lorsque vous affichez la transcription de la même conversation dans User2, les messages publiés par User2 sont mis en surbrillant en violet. Ce comportement de mise en surbrillance est basé sur la même expérience Teams client, où les publications d’un utilisateur sont mises en surbrillance en violet dans le client Teams client.

Les captures d’écran suivantes montrent un exemple de conversation dans le client Teams et le fichier de transcription de la même conversation dans le jeu à réviser. La mise en surbrillance violet dans le fichier de transcription indique que la transcription a été collectée à partir de la boîte aux lettres de l’utilisateur 2.

##### <a name="conversation-in-teams-client"></a>Conversation dans Teams client

![Conversation affichée dans le fichier de transcription du jeu à réviser.](..\media\TeamsClient1.png)

##### <a name="conversation-in-transcript-file"></a>Conversation dans le fichier de transcription

![Même conversation affichée dans Teams client.](..\media\TeamsTranscript1.png)

### <a name="transcript-conversation-threading"></a>Threads de conversation transcription

La fonctionnalité de thread de conversation dans le format grand cas dans Advanced eDiscovery vous permet d’identifier le contenu contextuel lié aux éléments qui peuvent être pertinents pour votre examen. Cette fonctionnalité produit des affichages de conversation distincts qui incluent des messages de conversation qui précèdent et suivent les éléments qui correspondent à la requête de recherche pendant la collecte. Cette fonctionnalité vous permet de passer en revue efficacement et rapidement les conversations de conversation complètes (appelées *conversations* threadées) dans Microsoft Teams. Comme expliqué précédemment, les conversations de conversation sont reconstruites dans des fichiers de transcription HTML lorsque Advanced eDiscovery ajoute Teams contenu à un jeu à réviser.

Voici la logique utilisée par Advanced eDiscovery pour inclure des fichiers de transcription de messages et de réponses supplémentaires qui fournissent un contexte autour des éléments qui correspondent à la requête de collection (appelée éléments réactifs) que vous avez utilisée lors de la collecte de Teams contenu. Différents comportements de thread sont basés sur les types de conversations et la requête de recherche utilisée pour collecter les éléments réactifs. Il existe deux scénarios de collection courants :

- Requêtes qui utilisent des paramètres de recherche, tels que les mots clés et les paires property:value

- Requêtes qui utilisent uniquement des plages de dates

| Teams type de contenu|Requêtes avec paramètres de recherche  |Requêtes avec plages de dates  |
|:---------|:---------|:---------|
|Teams 1:1 et conversations de groupe   |Les messages publiés 12 heures avant et 12 heures après les éléments réactifs sont regroupés avec l’élément réactif dans un fichier de transcription unique.   |Les messages d’une fenêtre de 24 heures sont regroupés dans un seul fichier de transcription.|
|Teams canal privé et les conversations de canal privé    |Chaque billet contenant des éléments réactifs et toutes les réponses correspondantes sont regroupés dans un fichier de transcription unique. |Chaque billet contenant des éléments réactifs et toutes les réponses correspondantes sont regroupés dans un fichier de transcription unique.|
||||

### <a name="deduplication-of-teams-content"></a>Déduplication du contenu Teams contenu

La liste suivante décrit le comportement de déduplication (et de duplication) lors de la collecte de Teams contenu dans un jeu à réviser.

- Chaque fichier de transcription ajouté à un jeu à réviser doit être un mappage un-à-un au contenu stocké dans des emplacements de données. Cela signifie Advanced eDiscovery ne collecte aucun contenu Teams qui a déjà été ajouté au jeu à réviser. Si un message de conversation est déjà collecté dans un jeu à réviser, Advanced eDiscovery n’ajoute pas le même message à partir du même emplacement de données au jeu à réviser dans les collections suivantes.

- Pour les conversations de groupe et 1:1, les copies des messages sont stockées dans la boîte aux lettres de chaque participant à la conversation. Les copies de la même conversation qui existent dans les boîtes aux lettres des différents participants sont collectées avec des métadonnées différentes. Par conséquent, chaque instance de la conversation est traitée comme unique et est mise dans le jeu à réviser dans des fichiers de transcription distincts. Ainsi, si tous les participants d’une conversation 1:1 ou de groupe sont ajoutés en tant que dépositaires dans un cas et inclus dans l’étendue d’une collection, les copies de chaque transcription (pour la même conservation) sont ajoutées au jeu à réviser et sont regroupées avec le même **ConversationId**. Chacune de ces copies est associée à un dépositaire correspondant. **Conseil**: la colonne **Custodian** dans la liste des ensembles de révision identifie le dépositaire pour le fichier de transcription correspondant.

- Dans les collections suivantes d’éléments de la même conversation, seul le contenu delta qui n’a pas été précédemment collecté est ajouté au jeu à réviser et regroupé (en partageant le même **ConversationId**) avec les transcriptions précédemment collectées à partir de la même conversation. Voici un exemple de ce comportement :

   1. La collection A collecte les messages d’une conversation entre User1 et User2 et les ajoute au jeu à réviser.

   2. La collection B collecte les messages de la même conversation, mais il existe de nouveaux messages entre User1 et User2 depuis l’utilisation de la collection A.

   3. Seuls les nouveaux messages de la collection B sont ajoutés au jeu à réviser. Ces messages sont ajoutés à un fichier de transcription distinct, mais la nouvelle transcription est groupée avec les transcriptions de la collection A par le même **ConversationId**.

   Ce comportement s’applique à tous les types de conversations Teams conversation.

### <a name="metadata-for-teams-content"></a>Métadonnées pour Teams contenu

Dans les grands ensembles de révision avec des milliers ou des millions d’éléments, il peut être difficile de restreindre l’étendue de votre révision Teams contenu. Pour vous aider à vous concentrer sur Teams contenu, il existe des propriétés de métadonnées spécifiques à Teams contenu. Vous pouvez utiliser ces propriétés pour organiser [](review-set-search.md) les colonnes dans la liste de révision et configurer des filtres et des requêtes afin d’optimiser la révision Teams contenu. Ces propriétés de métadonnées sont également incluses lorsque vous exportez du contenu Teams à partir de Advanced eDiscovery, pour vous aider à organiser et à afficher le contenu après l’exportation ou dans des outils eDiscovery tiers.

Le tableau suivant décrit les propriétés de métadonnées pour Teams contenu.

|Propriété de métadonnées  |Description  |
|:---------|:---------|
|ContainsEditedMessage      | Indique si un fichier de transcription contient un message modifié. Les messages modifiés sont identifiés lors de l’affichage du fichier de transcription.|
|ConversationId|GUID qui identifie la conversation à qui l’élément est associé. Les fichiers et pièces jointes de transcription de la même conversation ont la même valeur pour cette propriété.|
|Nom de la conversation     | Nom de la conversation à qui le fichier de transcription ou la pièce jointe est associé. Pour Teams 1:1 et les conversations de groupe, la valeur de cette propriété est l’UPN de tous les participants de la conversation sont concatenés. Par exemple : `User3 <User3@contoso.onmicrosoft.com>,User4 <User4@contoso.onmicrosoft.com>,User2 <User2@contoso.onmicrosoft.com>`. Teams canal privé et les conversations de canal privé utilisent le format suivant pour le nom de la conversation : `<Team name>,<Channel name>` .Par exemple : `eDiscovery vNext, General`.          |
|ConversationType     | Indique le type de conversation d’équipe. Pour Teams 1:1 et les conversations de groupe, la valeur de cette propriété est `Group` . Pour Teams de canal privé et privé, la valeur est `Channel` .|
|Date | Horodaté du premier message dans le fichier de transcription.|
|FamilyId|GUID qui identifie le fichier de transcription d’une conversation. Les pièces jointes auront la même valeur pour cette propriété que le fichier de transcription qui contient le message à qui le fichier a été joint.|
|FileClass     |Indique ce type de contenu. Les éléments de Teams conversations ont la valeur `Conversation` . En revanche, Exchange messages électroniques ont la valeur `Email` .|          |
|MessageKind     | Propriété du type de message. Teams contenu a la valeur `microsoftteams , im` . |
|Destinataires     | Liste de tous les utilisateurs qui ont reçu un message dans la conversation de transcription.|
|TeamsChannelName     | Nom Teams canal privé ou de la transcription.|
|||

Pour obtenir des descriptions des autres propriétés Advanced eDiscovery métadonnées, voir les champs de [métadonnées de](document-metadata-fields-in-Advanced-eDiscovery.md)document Advanced eDiscovery .

## <a name="export-teams-content"></a>Exporter Teams contenu

Une fois que vous avez examiné et Teams contenu dans un jeu à réviser, vous pouvez exporter les fichiers de transcription qui contiennent du contenu qui répond à votre enquête. Il n’existe aucun paramètre d’exportation spécifique pour Teams contenu. Chaque fichier de transcription est exporté en tant que fichier de message HTML. Ce fichier contient également des balises CDATA masquées avec toutes les métadonnées des messages de conversation individuels. Les propriétés de métadonnées abordées dans la section précédente sont incluses lorsque Teams contenu est exporté.  

Chaque fichier de transcription est référencé dans le fichier de chargement et peut se trouver à l’aide du chemin d’accès relatif dans le Export_native_path dans le fichier de chargement. Les fichiers de transcription se trouvent dans le dossier Conversations du dossier d’exportation racine.

## <a name="tips-for-viewing-teams-content-in-a-review-set"></a>Astuces pour l’affichage Teams contenu dans un jeu à réviser

Voici quelques conseils et meilleures pratiques pour afficher Teams contenu dans un jeu à réviser.

- Utilisez le **contrôle Personnaliser les colonnes** dans la barre de commandes pour ajouter et organiser des colonnes afin d’optimiser la révision Teams contenu.

  ![Utilisez la page de modification du flyout de colonne pour ajouter, supprimer et organiser des colonnes.](..\media\EditReviewSetColumns.png)

   Vous pouvez ajouter et supprimer des colonnes utiles pour Teams contenu. Vous pouvez également séquencer l’ordre des colonnes en les faisant glisser et en les faisant glisser dans la page volante Modifier **la** colonne. Vous pouvez également trier les colonnes pour Teams contenu avec des valeurs similaires pour la colonne sur qui vous tiez.

- Colonnes utiles pour vous aider à passer en revue Teams contenu inclut **le** dépositaire, les **destinataires** et le **type** de fichier ou **le type de message**.

- Utilisez [des filtres](review-set-search.md) pour Teams propriétés liées à l’affichage rapide Teams contenu. Il existe des filtres pour la plupart des propriétés de métadonnées décrites dans la section précédente.
