---
title: Éléments partiellement indexés dans la recherche de contenu
description: Découvrez les éléments non indexés dans Exchange et SharePoint que vous pouvez inclure dans une recherche de contenu que vous exécutez dans le portail de conformité Microsoft Purview.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 05/13/2022
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnindexedItemsLearnMore
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- SPO160
- MOE150
- MET150
ms.openlocfilehash: b1f0af9bf7c69b87cfa867191a714f81702ab367
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688113"
---
# <a name="partially-indexed-items-in-content-search"></a>Éléments partiellement indexés dans la recherche de contenu

Une recherche de contenu que vous exécutez à partir du portail de conformité Microsoft Purview inclut automatiquement des éléments partiellement indexés dans les résultats estimés de la recherche lorsque vous exécutez une recherche. Les éléments partiellement indexés sont des éléments de boîte aux lettres Exchange et des documents sur SharePoint et OneDrive Entreprise sites qui, pour une raison quelconque, n’ont pas été complètement indexés pour la recherche. Dans Exchange, un élément partiellement indexé contient généralement un fichier (d’un type de fichier qui ne peut pas être indexé) qui est joint à un message électronique. Voici d’autres raisons pour lesquelles les éléments ne peuvent pas être indexés pour la recherche et sont retournés en tant qu’éléments partiellement indexés lorsque vous exécutez une recherche eDiscovery :
  
- Le type de fichier n’est paspris en charge ou est désactivé pour l’indexation.
- Les messages ont un fichier joint qui ne peut pas être ouvert ; il s’agit de la cause la plus courante d’éléments de courrier partiellement indexés.
- Le type de fichier est pris en charge pour l’indexation, mais une erreur d’indexation s’est produite pour un fichier spécifique.
- Le nombre de fichiers joints à un message électronique est trop important.
- Un fichier joint à un message électronique est trop volumineux.
- Un fichier est chiffré avec des technologies autres que Microsoft.
- Un fichier est protégé par mot de passe.

> [!NOTE]
> La plupart des organisations ont moins de 1 % du contenu par volume et moins de 12 % par taille partiellement indexée. La raison de la différence entre le volume et la taille est que les fichiers plus volumineux ont une probabilité plus élevée de contenir du contenu qui ne peut pas être complètement indexé.
  
Pour les enquêtes juridiques, votre organisation peut être tenue d’examiner les éléments partiellement indexés. Vous pouvez également spécifier s’il faut inclure des éléments partiellement indexés lorsque vous exportez des résultats de recherche vers un ordinateur local ou lorsque vous préparez les résultats pour analyse avec eDiscovery (Premium). Pour plus d’informations, consultez [Examen des éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md).
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="file-types-not-indexed-for-search"></a>Types de fichier non indexés pour la recherche

Certains types de fichiers, tels que les fichiers Bitmap (.bmp) ou MP3 (.mp3), ne contiennent pas de contenu pouvant être indexé. Par conséquent, les serveurs d’indexation de recherche dans Exchange et SharePoint n’effectuent pas d’indexation de texte intégral sur ces types de fichiers. Ces types de fichier sont considérés comme non pris en charge. Il existe également des types de fichier pour lesquels l’indexation de texte intégral a été désactivée, soit par défaut, soit par un administrateur. Les types de fichiers non pris en charge et désactivés sont étiquetés comme des éléments non indexés dans les recherches de contenu. Comme indiqué précédemment, les éléments partiellement indexés peuvent être inclus dans l’ensemble des résultats de recherche lorsque vous exécutez une recherche, exportez les résultats de la recherche vers un ordinateur local ou préparez les résultats de recherche pour eDiscovery (Premium).
  
Pour obtenir la liste des formats de fichiers pris en charge et désactivés, consultez les articles suivants :
  
- **Échange** -  [Formats de fichiers indexés par recherche Exchange](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)
- **Échange** -  [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)
- **Sharepoint** -  [Extensions de nom de fichier analysés par défaut et types de fichiers analysés dans SharePoint](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types)
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Les messages et documents avec des types de fichiers partiellement indexés peuvent être retournés dans les résultats de recherche

Tous les messages électroniques contenant une pièce jointe partiellement indexée ou tous les documents SharePoint partiellement indexés ne sont pas retournés automatiquement en tant qu’élément partiellement indexé. Cela est dû au fait que d’autres propriétés de message ou de document, telles que la propriété **Subject** dans les messages électroniques et les propriétés **Title** ou **Author** pour les documents, sont indexées et disponibles pour faire l’objet d’une recherche. Par exemple, une recherche par mot clé pour « financial » renvoie des éléments avec une pièce jointe de fichier partiellement indexée si ce mot clé apparaît dans l’objet d’un message électronique ou dans le nom de fichier ou le titre d’un document. Toutefois, si le mot clé apparaît uniquement dans le corps du fichier, le message ou le document est retourné en tant qu’élément partiellement indexé.
  
De même, les messages comportant des pièces jointes partiellement indexées et des documents d’un type de fichier partiellement indexé sont inclus dans les résultats de recherche lorsque d’autres propriétés de message ou de document, indexées et pouvant faire l’objet d’une recherche, correspondent aux critères de recherche. Les propriétés des messages qui sont indexées pour la recherche comprennent les dates d’envoi et de réception, l’expéditeur et le destinataire, le nom de fichier d’une pièce jointe et le texte dans le corps du message. Les propriétés de document indexées pour la recherche comprennent les dates de création et de modification. Ainsi, même si une pièce jointe de message peut être un élément partiellement indexé, le message est inclus dans les résultats de recherche standard si la valeur d’autres propriétés de message ou de document correspond aux critères de recherche.
  
Pour obtenir la liste des propriétés d’e-mail et de document que vous pouvez rechercher à l’aide des outils eDiscovery dans le portail de conformité, consultez [Requêtes par mot clé et conditions de recherche pour eDiscovery](keyword-queries-and-search-conditions.md).
  
> [!NOTE]
> Si un élément de boîte aux lettres est déplacé d’un dossier indexé vers un dossier qui n’est pas indexé, un indicateur est défini pour annuler l’indexation de l’élément et l’élément est supprimé de l’index et ne peut pas faire l’objet d’une recherche. Plus tard, si ce même élément est déplacé vers un dossier indexé, l’indicateur n’est pas réinitialisé. Cela signifie que l’élément reste non indexé et ne peut pas faire l’objet d’une recherche.

## <a name="partially-indexed-items-included-in-the-search-results"></a>Éléments partiellement indexés inclus dans les résultats de la recherche

Votre organisation peut être tenue d’identifier et d’effectuer une analyse supplémentaire sur les éléments partiellement indexés pour déterminer ce qu’ils sont, ce qu’ils contiennent et s’ils sont pertinents pour une investigation spécifique. Comme expliqué précédemment, les éléments partiellement indexés dans les emplacements de contenu recherchés sont automatiquement inclus avec les résultats de recherche estimés. Vous avez la possibilité d’inclure ces éléments partiellement indexés lorsque vous exportez des résultats de recherche ou préparez les résultats de recherche pour eDiscovery (Premium).
  
Gardez à l’esprit les éléments partiellement indexés :
  
- Lorsque vous exécutez une recherche eDiscovery, le nombre total et la taille des éléments Exchange partiellement indexés (retournés par la requête de recherche) sont affichés dans les statistiques de recherche de la page de menu volant et étiquetés comme **éléments non indexés**. Les statistiques relatives aux éléments partiellement indexés affichés sur la page de menu volant n’incluent pas les éléments partiellement indexés dans les sites SharePoint ou les comptes OneDrive.
- Si la recherche à partir de laquelle vous exportez les résultats était une recherche d’emplacements de contenu spécifiques ou de tous les emplacements de contenu de votre organisation, seuls les éléments non indexés des emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. La raison en est que l’exportation d’éléments partiellement indexés à partir de nombreux emplacements de l’organisation peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps nécessaire à l’exportation et au téléchargement des résultats de la recherche.

    Pour exporter des éléments partiellement indexés à partir de tous les emplacements de contenu d’une recherche, configurez la recherche pour renvoyer tous les éléments (en supprimant les mots clés de la requête de recherche), puis exportez uniquement les éléments partiellement indexés lorsque vous exportez les résultats de la recherche (en cliquant sur **Seuls les éléments dont le format n’est pas reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons** sous **Options de sortie**).

- Si vous choisissez d’inclure tous les éléments de boîte aux lettres dans les résultats de la recherche, ou si une requête de recherche ne spécifie aucun mot clé ou spécifie uniquement une plage de dates, les éléments partiellement indexés risquent de ne pas être copiés dans le fichier PST qui contient les éléments partiellement indexés. Cela est dû au fait que tous les éléments, y compris les éléments partiellement indexés, seront automatiquement inclus dans les résultats de la recherche standard.
- Les éléments partiellement indexés ne peuvent pas être aperçus. Vous devez exporter les résultats de la recherche pour afficher les éléments partiellement indexés retournés par la recherche.

   En outre, lorsque vous exportez des résultats de recherche et que vous incluez des éléments partiellement indexés dans l’exportation, les éléments partiellement indexés à partir d’éléments SharePoint sont exportés vers un dossier nommé **Uncrawllable**. Lorsque vous exportez des éléments Exchange partiellement indexés, ils sont exportés différemment selon que les éléments partiellement indexés correspondent à la requête de recherche et à la configuration des paramètres d’exportation.

- Le tableau suivant indique le comportement d’exportation des éléments indexés et partiellement indexés et indique si chacun d’eux est inclus ou non pour les différents paramètres de configuration d’exportation.

  |**Exporter la configuration**|**Éléments indexés qui correspondent à la requête de recherche**|**Éléments partiellement indexés qui correspondent à la requête de recherche**|**Éléments partiellement indexés qui ne correspondent pas à la requête de recherche**|
  |:-----|:-----|:-----|:-----|
  |exporter uniquement les éléments indexés ;  <br/> |Exported<br/> |Exporté (inclus avec les éléments indexés exportés)<br/>  |Non exporté <br/>|
  |Exporter uniquement les éléments partiellement indexés  <br/> |Non exporté  <br/> |Exporté (en tant qu’éléments partiellement indexés)<br/> |Exporté (en tant qu’éléments partiellement indexés)|
  |Exporter des éléments indexés et partiellement indexés  <br/> |Exported<br/> |Exporté (inclus avec les éléments indexés exportés)<br/>  |Exporté (en tant qu’éléments partiellement indexés)<br/>|
  ||||
  
## <a name="workaround-for-using-a-date-range-to-exclude-partially-indexed-items"></a>Solution de contournement pour l’utilisation d’une plage de dates pour exclure des éléments partiellement indexés

Dans Recherche de contenu et Microsoft Purview eDiscovery (Standard), vous ne pouvez pas utiliser une plage de dates pour exclure les éléments partiellement indexés d’être retournés par une requête de recherche. En d’autres termes, les éléments partiellement indexés qui se trouvent en dehors d’une plage de dates sont toujours inclus en tant qu’éléments partiellement indexés dans les statistiques de recherche et lorsque vous exportez des éléments partiellement indexés. Dans eDiscovery (Premium), vous pouvez exclure des éléments partiellement indexés à l’aide d’une plage de dates dans une requête de recherche.

Pour contourner cette limitation, nous vous recommandons la procédure suivante.

1. Créez et exécutez une recherche à l’aide d’une requête de recherche qui répond à vos besoins et retourne les résultats souhaités.

2. Exportez les résultats de la recherche à partir de l’étape 1, mais n’incluez pas d’éléments partiellement indexés dans l’exportation. Pour ce faire, vous devez sélectionner l’option **d’exportation Tous les éléments, à l’exception de ceux dont le format n’est pas reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons** . <sup>1</sup>

   ![Exporter les options de sortie.](../media/ExportOutputOptions.png)

3. Créez et exécutez une deuxième recherche qui utilise la même requête de recherche (et recherche les mêmes emplacements) que vous avez utilisée à l’étape 1. Ajoutez la clause suivante à la requête d’origine à l’aide de l’opérateur **AND** :

   ```text
   <original query> AND ((IndexingErrorCode>0 OR IndexingErrorCode<0) AND sent:date1..date2)
   ```

   L’ajout de cette clause retourne les éléments partiellement indexés qui correspondent à votre requête de recherche d’origine et qui se trouvent dans une plage de dates spécifique. <sup>2</sup>

4. Exportez les résultats de la recherche à partir de l’étape 3 et incluez cette fois des éléments partiellement indexés dans l’exportation. Pour ce faire, vous devez sélectionner l’option **d’exportation Tous les éléments, y compris ceux dont le format n’est pas reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons** .

   > [!NOTE]
   > <sup>1</sup> La sortie de l’étape 2 entraîne l’exportation des éléments indexés uniquement.<br/>
   > <sup>2</sup> La condition utilisée à l’étape 3 identifie uniquement les éléments présentant des erreurs d’indexation qui se trouvent dans la plage de dates spécifiée. Il ne retourne aucun élément qui est entièrement indexé. Cela signifie que les éléments exportés à l’étape 4 incluent uniquement les éléments non indexés qui entrent dans la plage de dates. L’exportation n’inclut pas les éléments indexés. Par conséquent, la sortie combinée de l’étape 2 et de l’étape 4 contient tous les éléments indexés et non indexés qui se trouvent dans la plage de dates spécifiée.

Utilisez la deuxième recherche que vous avez créée à l’étape 3 et l’exportation correspondante pour afficher et comprendre les éléments partiellement indexés qui correspondent à votre requête de recherche d’origine. L’exportation de la deuxième recherche inclut également tous les éléments partiellement indexés qui ont été exportés afin que vous puissiez les consulter si nécessaire.

> [!TIP]
> Dans la procédure précédente, vous pouvez exporter les résultats de recherche réels ou exporter uniquement un rapport.

## <a name="indexing-limits-for-messages"></a>Limites d’indexation des messages

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le renvoi d’un e-mail en tant qu’élément partiellement indexé dans une recherche eDiscovery dans Microsoft 365.
  
Pour obtenir la liste des limites d’indexation des documents SharePoint, voir [Limites de recherche pour SharePoint Online](/sharepoint/search-limits).
  
|**Limite d’indexation**|**Commentaires**|**Description**|
|:-----------------|:----------------|:--------------|
|Taille maximale des pièces jointes (à l’exception des fichiers Excel)  <br/> |150 Mo  <br/> |Taille maximale d’une pièce jointe à analyser pour l’indexation. Toute pièce jointe supérieure à cette limite ne sera pas analysée pour l’indexation, et le message avec la pièce jointe sera marqué comme partiellement indexé.  <br/><br/> **Note:** L’analyse est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères inutiles tels que la ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé tokenisation), qui sont ensuite stockés dans l’index.           |
|Taille maximale des fichiers Excel  <br/> |4 Mo  <br/> |Taille maximale d’un fichier Excel situé sur un site ou attaché à un message électronique qui sera analysé pour l’indexation. Tout fichier Excel supérieur à cette limite ne sera pas analysé, et le fichier ou l’e-mail du message contenant la pièce jointe sera marqué comme non indexé.  <br/> |
|Nombre maximal de pièces jointes  <br/> |250  <br/> |Nombre maximal de fichiers joints à un e-mail qui seront analysés pour l’indexation. Si un message comporte plus de 250 pièces jointes, les 250 premières pièces jointes sont analysées et indexées, et le message est marqué comme partiellement indexé, car il contient des pièces jointes supplémentaires qui n’ont pas été analysées.  <br/> |
|Profondeur maximale de la pièce jointe  <br/> |30  <br/> |Nombre maximal de pièces jointes imbriquées analysées. Par exemple, si un message électronique comporte un autre message joint et que le message joint a un document Word joint, le document Word et le message joint sont indexés. Ce comportement se poursuit pour jusqu’à 30 pièces jointes imbriquées.  <br/> |
|Nombre maximal d’images attachées  <br/> |0  <br/> |Une image jointe à un e-mail est ignorée par l’analyseur et n’est pas indexée.  <br/> |
|Temps maximal consacré à l’analyse d’un élément  <br/> |30 secondes  <br/> |Un maximum de 30 secondes est consacré à l’analyse d’un élément pour l’indexation. Si le temps d’analyse dépasse 30 secondes, l’élément est marqué comme partiellement indexé.  <br/> |
|Sortie maximale de l’analyseur  <br/> |2 millions de caractères  <br/> |Quantité maximale de sortie de texte de l’analyseur indexé. Par exemple, si l’analyseur a extrait 8 millions de caractères d’un document, seuls les 2 premiers millions de caractères sont indexés.  <br/> |
|Nombre maximal de jetons d’annotation  <br/> |2 millions  <br/> |Lorsqu’un message électronique est indexé, chaque mot est annoté avec des instructions de traitement différentes qui spécifient comment ce mot doit être indexé. Chaque ensemble d’instructions de traitement est appelé jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions de jetons d’annotation pour un e-mail.  <br/> |
|Taille maximale du corps dans l’index  <br/> |67 millions de caractères  <br/> |Nombre total de caractères dans le corps d’un message électronique et de toutes ses pièces jointes. Lorsqu’un e-mail est indexé, tout le texte dans le corps du message et dans toutes les pièces jointes est concaténé en une seule chaîne. La taille maximale de cette chaîne indexée est de 67 millions de caractères.  <br/> |
|Nombre maximal de jetons uniques dans le corps  <br/> |1 million  <br/> |Comme expliqué précédemment, les jetons sont le résultat de l’extraction de texte du contenu, de la suppression de la ponctuation et des espaces, puis de sa division en mots (appelés jetons) qui sont stockés dans l’index. Par exemple, l’expression  `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seulement 4 d’entre eux sont des jetons uniques. Il existe une limite de 1 million de jetons uniques par e-mail, ce qui permet d’éviter que l’index ne soit trop volumineux avec des jetons aléatoires.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Plus d’informations sur les éléments partiellement indexés

- Comme indiqué précédemment, étant donné que les propriétés de message et de document et leurs métadonnées sont indexées, une recherche par mot clé peut retourner des résultats si ce mot clé apparaît dans les métadonnées indexées. Cependant, cette même recherche par mot clé peut ne pas renvoyer le même élément si le mot clé apparaît uniquement dans le contenu d’un élément dont le type de fichier n’est pas pris en charge. Dans ce cas, l’élément est retourné en tant qu’élément partiellement indexé.

- Si un élément partiellement indexé est inclus dans les résultats de la recherche parce qu’il correspond aux critères de requête de recherche, il n’est pas inclus en tant qu’élément partiellement indexé dans les statistiques de recherche estimées. En outre, il ne sera pas inclus avec les éléments partiellement indexés lorsque vous exportez les résultats de la recherche.

- Bien qu’un type de fichier soit pris en charge pour l’indexation et qu’il soit indexé, il peut y avoir des erreurs d’indexation ou de recherche qui entraînent le retour d’un fichier en tant qu’élément partiellement indexé. Par exemple, la recherche dans un fichier Excel volumineux peut être partiellement réussie (car les 4 premiers Mo sont indexés), mais échoue car la limite de taille de fichier est dépassée. Dans ce cas, il est possible que le même fichier soit retourné avec les résultats de la recherche et en tant qu’élément partiellement indexé.

- Les fichiers chiffrés avec les [technologies de chiffrement Microsoft](encryption.md) et joints à un message électronique qui correspond aux critères d’une recherche peuvent être prévisualisés et déchiffrés lors de l’exportation. À ce stade, les fichiers chiffrés avec les technologies de chiffrement Microsoft (et stockés dans SharePoint ou OneDrive Entreprise) sont partiellement indexés. 

- Email messages chiffrés avec S/MIME sont partiellement indexés. Il s'agit des messages chiffrés avec ou sans pièces jointes.

- Email messages protégés à l’aide de Azure Rights Management sont indexés et inclus dans les résultats de la recherche s’ils correspondent à la requête de recherche. Les messages électroniques protégés par des droits sont déchiffrés et peuvent être prévisualisés et exportés. Cette fonctionnalité nécessite que vous ayez le rôle Decrypt RMS, qui est attribué par défaut au groupe de rôles Gestionnaire eDiscover.

- Si vous créez une conservation basée sur une requête associée à un cas eDiscovery, tous les éléments partiellement indexés sont mis en attente. Cela inclut les éléments partiellement indexés qui ne correspondent pas aux critères de requête de recherche pour la conservation. Pour plus d’informations sur la création de conservations eDiscovery basées sur des requêtes, consultez [Créer une conservation eDiscovery](create-ediscovery-holds.md).
