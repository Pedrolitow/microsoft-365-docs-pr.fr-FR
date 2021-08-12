---
title: Éléments partiellement indexés dans la recherche de contenu et d’autres outils eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnindexedItemsLearnMore
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: d1691de4-ca0d-446f-a0d0-373a4fc8487b
description: Découvrez les éléments nonndex dans Exchange et SharePoint que vous pouvez inclure dans une recherche de découverte électronique que vous exécutez dans le Centre de conformité Microsoft 365.
ms.openlocfilehash: a43873b52ad4cf76c694b4666761b6904ab4126c5c7b79a6ca530ef00af5c688
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53835750"
---
# <a name="partially-indexed-items-in-ediscovery"></a>Éléments partiellement indexés dans eDiscovery

Une recherche de découverte électronique que vous exécutez à partir du Centre de conformité Microsoft 365 inclut automatiquement des éléments partiellement indexés dans les résultats de recherche estimés lorsque vous exécutez une recherche. Les éléments partiellement indexés sont des Exchange de boîtes aux lettres et des documents sur des sites SharePoint et OneDrive Entreprise qui, pour une raison quelconque, n’ont pas été complètement indexés pour la recherche. Dans Exchange, un élément partiellement indexé contient généralement un fichier (d’un type de fichier qui ne peut pas être indexé) joint à un message électronique. Voici d’autres raisons pour lesquelles les éléments ne peuvent pas être indexés pour la recherche et sont renvoyés en tant qu’éléments partiellement indexés lorsque vous exécutez une recherche de découverte électronique :
  
- Le type de fichier n’est paspris en charge ou est désactivé pour l’indexation.

- Les messages ont un fichier joint sans un handler valide, tel que des fichiers image ; Il s’agit de la cause la plus courante des éléments de courrier partiellement indexés.

- Le type de fichier est pris en charge pour l’indexation, mais une erreur d’indexation s’est produite pour un fichier spécifique.

- Le nombre de fichiers joints à un message électronique est trop important.

- Un fichier joint à un message électronique est trop volumineux.

- Un fichier est chiffré avec des technologies autres que Microsoft.

- Un fichier est protégé par mot de passe.

> [!NOTE]
> La plupart des organisations ont moins de 1 % du contenu par volume et moins de 12 % par taille partiellement indexée. La différence entre le volume et la taille est dû au fait que les fichiers plus volumineux ont une probabilité plus élevée de contenir du contenu qui ne peut pas être complètement indexé.
  
Pour les enquêtes juridiques, votre organisation peut être tenue de réviser les éléments partiellement indexés. Vous pouvez également spécifier s’il faut inclure des éléments partiellement indexés lorsque vous exportez des résultats de recherche vers un ordinateur local ou lorsque vous préparez les résultats pour analyse avec Advanced eDiscovery. Pour plus d’informations, voir [Investigating partially indexed items in eDiscovery](investigating-partially-indexed-items-in-ediscovery.md).
  
## <a name="file-types-not-indexed-for-search"></a>Types de fichier non indexés pour la recherche

Certains types de fichier, tels que les fichiers Bitmap ou MP3, ne comportent pas de contenu pouvant être indexé. Par conséquent, les serveurs d’indexation de recherche dans Exchange et SharePoint n’effectuent pas d’indexation en texte intégral sur ces types de fichiers. Ces types de fichier sont considérés comme non pris en charge. Il existe également des types de fichier pour lesquels l’indexation de texte intégral a été désactivée, soit par défaut, soit par un administrateur. Les types de fichiers non pris en mesure et désactivés sont étiquetés en tant qu’éléments nonndex dans les recherches de contenu. Comme indiqué précédemment, les éléments partiellement indexés peuvent être inclus dans l’ensemble des résultats de recherche lorsque vous exécutez une recherche, que vous exportez les résultats de la recherche vers un ordinateur local ou que vous préparez les résultats de recherche pour Advanced eDiscovery.
  
Pour obtenir une liste de formats de fichier pris en charge et désactivés, consultez les rubriques suivantes :
  
- **Exchange**  -  [Formats de fichiers indexés par la recherche Exchange recherche](/exchange/file-formats-indexed-by-exchange-search-exchange-2013-help)

- **Exchange**  -  [Get-SearchDocumentFormat](/powershell/module/exchange/get-searchdocumentformat)

- **SharePoint**  -  [Extensions de nom de fichier et types de](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) fichiers analyse par défaut dans SharePoint
  
## <a name="messages-and-documents-with-partially-indexed-file-types-can-be-returned-in-search-results"></a>Les messages et les documents dont les types de fichiers sont partiellement indexés peuvent être renvoyés dans les résultats de la recherche

Tous les messages électroniques avec une pièce jointe partiellement indexée ou tous les documents SharePoint partiellement indexés ne sont pas automatiquement renvoyés en tant qu’élément partiellement indexé. En effet, d’autres propriétés de message ou de document, telles que la propriété **Subject** dans les messages électroniques et les propriétés **Title** ou **Author** des documents sont indexées et peuvent faire l’objet d’une recherche. Par exemple, une recherche par mot clé « financial » retourne les éléments avec une pièce jointe partiellement indexée si ce mot clé apparaît dans l’objet d’un message électronique ou dans le nom de fichier ou le titre d’un document. Toutefois, si le mot clé apparaît uniquement dans le corps du fichier, le message ou le document est renvoyé sous forme d’élément partiellement indexé.
  
De même, les messages avec des pièces jointes partiellement indexées et des documents d’un type de fichier partiellement indexé sont inclus dans les résultats de la recherche lorsque d’autres propriétés de message ou de document, indexées et utilisables dans une recherche, correspondent aux critères de recherche. Les propriétés des messages qui sont indexées pour la recherche comprennent les dates d’envoi et de réception, l’expéditeur et le destinataire, le nom de fichier d’une pièce jointe et le texte dans le corps du message. Les propriétés de document indexées pour la recherche comprennent les dates de création et de modification. Par conséquent, même si une pièce jointe de message peut être un élément partiellement indexé, le message sera inclus dans les résultats de recherche ordinaires si la valeur d’autres propriétés de message ou de document correspond aux critères de recherche.
  
Pour obtenir la liste des propriétés de courrier électronique et de document que vous pouvez rechercher à l’aide de la fonctionnalité de recherche dans le Centre de sécurité & conformité, voir Requêtes par mots clés et conditions de recherche pour [eDiscovery](keyword-queries-and-search-conditions.md).
  
## <a name="partially-indexed-items-included-in-the-search-results"></a>Éléments partiellement indexés inclus dans les résultats de la recherche

Votre organisation peut être tenue d’identifier et d’effectuer une analyse supplémentaire sur les éléments partiellement indexés pour déterminer ce qu’ils sont, ce qu’ils contiennent et s’ils sont pertinents pour un examen spécifique. Comme indiqué précédemment, les éléments partiellement indexés dans les emplacements de contenu recherchés sont automatiquement inclus dans les résultats de recherche estimés. Vous avez la possibilité d’inclure ces éléments partiellement indexés lorsque vous exportez des résultats de recherche ou préparez les résultats de la recherche pour Advanced eDiscovery.
  
Gardez les éléments suivants à l’esprit concernant les éléments partiellement indexés :
  
- Lorsque vous exécutez une recherche de découverte électronique, le nombre total et la taille des éléments de Exchange partiellement indexés (renvoyés par la requête de recherche) sont affichés dans les statistiques de recherche sur la page volante et étiquetés en tant qu’éléments non indexés. Les statistiques sur les éléments partiellement indexés affichés sur la page volante n’incluent pas d’éléments partiellement indexés dans des sites SharePoint ou des comptes OneDrive.

- Si la recherche dont vous exportez les résultats était une recherche d’emplacements de contenu spécifiques ou de tous les emplacements de contenu de votre organisation, seuls les éléments nonndex provenant d’emplacements de contenu qui contiennent des éléments qui correspondent aux critères de recherche seront exportés. In other words, if no search results are found in a mailbox or site, then any unindexed items in that mailbox or site won't be exported. En effet, l’exportation d’éléments partiellement indexés à partir de nombreux emplacements de l’organisation peut augmenter la probabilité d’erreurs d’exportation et augmenter le temps d’exportation et de téléchargement des résultats de la recherche.

    Pour exporter des éléments partiellement indexés à partir de tous les emplacements de contenu pour une recherche, configurez la recherche pour qu’elle retourne tous les éléments (en supprimant les mots clés de la requête de recherche), puis exportez uniquement les éléments partiellement indexés lorsque vous exportez les résultats de la recherche (en cliquant sur Uniquement les éléments dont le **format n’est** pas reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons sous **les options** de sortie).

- Si vous choisissez d’inclure tous les éléments de boîte aux lettres dans les résultats de la recherche, ou si une requête de recherche ne spécifie aucun mot clé ou spécifie uniquement une plage de dates, les éléments partiellement indexés peuvent ne pas être copiés dans le fichier PST qui contient les éléments partiellement indexés. En effet, tous les éléments, y compris les éléments partiellement indexés, seront automatiquement inclus dans les résultats de recherche ordinaires.

- Les éléments partiellement indexés ne peuvent pas être prévisualiser. Vous devez exporter les résultats de la recherche pour afficher les éléments partiellement indexés renvoyés par la recherche.

   En outre, lorsque vous exportez des résultats de recherche et incluez des éléments partiellement indexés dans l’exportation, les éléments partiellement indexés des éléments SharePoint sont exportés vers un dossier nommé **Uncrawlable**. Lorsque vous exportez des éléments Exchange partiellement indexés, ils sont exportés différemment selon que les éléments partiellement indexés correspondent ou non à la requête de recherche et à la configuration des paramètres d’exportation. 

- Le tableau suivant indique le comportement d’exportation des éléments indexés et partiellement indexés et indique si chacun d’eux est inclus ou non pour les différents paramètres de configuration d’exportation.

  |**Exporter la configuration**|**Éléments indexés qui correspondent à la requête de recherche**|**Éléments partiellement indexés qui correspondent à la requête de recherche**|**Éléments partiellement indexés qui ne correspondent pas à la requête de recherche**|
  |:-----|:-----|:-----|:-----|
  |exporter uniquement les éléments indexés ;  <br/> |Exported<br/> |Exporté (inclus avec les éléments indexés qui sont exportés)<br/>  |Non exporté <br/>|
  |Exporter uniquement les éléments partiellement indexés  <br/> |Non exporté  <br/> |Exporté (en tant qu’éléments partiellement indexés)<br/> |Exporté (en tant qu’éléments partiellement indexés)|
  |Exporter des éléments indexés et partiellement indexés  <br/> |Exported<br/> |Exporté (inclus avec les éléments indexés qui sont exportés)<br/>  |Exporté (en tant qu’éléments partiellement indexés)<br/>|
  ||||
  
## <a name="indexing-limits-for-messages"></a>Limites d’indexation pour les messages

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le retour d’un message électronique en tant qu’élément partiellement indexé dans une recherche eDiscovery dans Microsoft 365.
  
Pour obtenir la liste des limites d’indexation pour SharePoint documents, voir Limites de recherche [pour SharePoint Online.](/sharepoint/search-limits)
  
|**Limite d’indexation**|**Commentaires**|**Description**|
|:-----|:-----|:-----|
|Taille maximale des pièces jointes (à l’Excel fichiers)  <br/> |150 Mo  <br/> |Taille maximale d’une pièce jointe de courrier électronique qui sera l’indexation. Les pièces jointes dont la taille est supérieure à cette limite ne seront pas indexées et le message avec la pièce jointe sera marqué comme partiellement indexé.  <br/><br/> **Remarque :** L’examen est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères inutiles tels que les signes de ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé tokenization), qui sont ensuite stockés dans l’index.           |
|Taille maximale des fichiers Excel fichiers  <br/> |4 Mo  <br/> |Taille maximale d’un Excel situé sur un site ou joint à un message électronique qui sera indexé. Tout fichier Excel qui est supérieur à cette limite n’est pas en cours d’examen et le fichier ou l’e-mail du message avec la pièce jointe est marqué comme non indexé.  <br/> |
|Nombre maximal de pièces jointes  <br/> |250  <br/> |Nombre maximal de fichiers joints à un message électronique qui seront à l’indexation. Si un message a plus de 250 pièces jointes, les 250 premières pièces jointes sont parées et indexées, et le message est marqué comme partiellement indexé car il avait des pièces jointes supplémentaires qui n’ont pas été l’ont été.  <br/> |
|Profondeur maximale des pièces jointes  <br/> |30  <br/> |Nombre maximal de pièces jointes imbrmbrées qui sont parsées. Par exemple, si un message électronique est joint à un autre message et que le message joint contient un document Word joint, le document Word et le message joint sont indexés. Ce comportement se poursuit pour jusqu’à 30 pièces jointes imbrmbrées.  <br/> |
|Nombre maximal d’images jointes  <br/> |0  <br/> |Une image jointe à un message électronique est ignorée par l’asseur et n’est pas indexée.  <br/> |
|Temps maximal passé à l’d’un élément  <br/> |30 secondes  <br/> |Un maximum de 30 secondes est consacré à l’indexation d’un élément. Si le temps d’indexation dépasse 30 secondes, l’élément est marqué comme partiellement indexé.  <br/> |
|Sortie maximale de l’parseur  <br/> |2 millions de caractères  <br/> |Quantité maximale de texte provenant de l’indexeur indexé. Par exemple, si l’utilisateur a extrait 8 millions de caractères d’un document, seuls les 2 premiers millions de caractères sont indexés.  <br/> |
|Nombre maximal de jetons d’annotation  <br/> |2 millions  <br/> |Lorsqu’un message électronique est indexé, chaque mot est annoté avec différentes instructions de traitement qui spécifient comment ce mot doit être indexé. Chaque ensemble d’instructions de traitement est appelé jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions de jetons d’annotation pour un message électronique.  <br/> |
|Taille maximale du corps dans l’index  <br/> |67 millions de caractères  <br/> |Nombre total de caractères dans le corps d’un message électronique et toutes ses pièces jointes. Lorsqu’un message électronique est indexé, tout le texte du corps du message et de toutes les pièces jointes est concaté en une seule chaîne. La taille maximale de cette chaîne indexée est de 67 millions de caractères.  <br/> |
|Nombre maximal de jetons uniques dans le corps  <br/> |1 million  <br/> |Comme indiqué précédemment, les jetons sont le résultat de l’extraction de texte à partir du contenu, de la suppression des signes de ponctuation et des espaces, puis de sa division en mots (appelés jetons) stockés dans l’index. Par exemple, l’expression  `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seuls 4 d’entre eux sont des jetons uniques. Il existe une limite de 1 million de jetons uniques par message électronique, ce qui permet d’éviter que l’index ne soit trop grand avec des jetons aléatoires.  <br/> |
||||

## <a name="more-information-about-partially-indexed-items"></a>Plus d’informations sur les éléments partiellement indexés

- Comme indiqué précédemment, étant donné que les propriétés de message et de document et leurs métadonnées sont indexées, une recherche par mot clé peut renvoyer des résultats si ce mot clé apparaît dans les métadonnées indexées. Cependant, cette même recherche par mot clé peut ne pas renvoyer le même élément si le mot clé apparaît uniquement dans le contenu d’un élément dont le type de fichier n’est pas pris en charge. Dans ce cas, l’élément est renvoyé en tant qu’élément partiellement indexé.

- Si un élément partiellement indexé est inclus dans les résultats de la recherche car il correspond aux critères de requête de recherche, il ne sera pas inclus en tant qu’élément partiellement indexé dans les statistiques de recherche estimées. En outre, il n’est pas inclus avec les éléments partiellement indexés lorsque vous exportez des résultats de recherche.

- Bien qu’un type de fichier soit pris en charge pour l’indexation et qu’il soit indexé, il peut y avoir des erreurs d’indexation ou de recherche qui entraînent le retour d’un fichier en tant qu’élément partiellement indexé. Par exemple, la recherche dans un fichier Excel très grand peut être partiellement réussie (car les 4 premiers Mo sont indexés), mais échoue ensuite car la limite de taille de fichier est dépassée. Dans ce cas, il est possible que le même fichier soit renvoyé avec les résultats de la recherche et en tant qu’élément partiellement indexé.

- Les fichiers chiffrés avec les technologies de chiffrement [Microsoft](encryption.md) et joints à un message électronique qui correspond aux critères d’une recherche peuvent être prévisualisations et déchiffrés lors de l’exportation. Pour l’instant, les fichiers chiffrés avec les technologies de chiffrement Microsoft (et stockés dans SharePoint ou OneDrive Entreprise) sont partiellement indexés.

- Les messages électroniques chiffrés avec S/MIME sont partiellement indexés. Il s'agit des messages chiffrés avec ou sans pièces jointes.

- Les messages électroniques protégés à l Azure Rights Management sont indexés et seront inclus dans les résultats de la recherche s’ils correspondent à la requête de recherche. Les messages électroniques protégés par des droits sont déchiffrés et peuvent être aperçus et exportés. Cette fonctionnalité nécessite que le rôle déchiffrement RMS, qui est attribué par défaut au groupe de rôles Gestionnaire de découverte électronique, vous soit attribué.

- Si vous créez une mise en attente basée sur une requête associée à un cas eDiscovery, tous les éléments partiellement indexés sont mis en attente. Cela inclut les éléments partiellement indexés qui ne correspondent pas aux critères de requête de recherche pour la attente. Pour plus d’informations sur la création de holds eDiscovery basés sur des requêtes, voir Créer une mise en attente [eDiscovery.](create-ediscovery-holds.md)

## <a name="see-also"></a>Voir aussi

[Recherche d’éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)