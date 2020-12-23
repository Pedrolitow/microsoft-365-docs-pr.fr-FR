---
title: Limites de recherche de contenu dans le centre de sécurité & conformité
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 78fe3147-1979-4c41-83bb-aeccf244368d
description: Découvrez les limites en vigueur pour la fonctionnalité de recherche de contenu dans le centre de sécurité & conformité dans Office 365, comme le nombre maximal de recherches simultanées.
ms.openlocfilehash: c62476b8cb50ca8931e62159ea946ec209ee491c
ms.sourcegitcommit: 5713e69770ffbce4a98701579f467134dbc4bc0a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "49727730"
---
# <a name="limits-for-content-search-in-the-security--compliance-center"></a>Limites de recherche de contenu dans le centre de sécurité & conformité

> [!NOTE]
> Les limites de cette rubrique sont différentes des limites actuelles pour In-Place eDiscovery dans Exchange Online et pour le centre eDiscovery dans SharePoint Online.
  
Différentes limites sont appliquées à la fonctionnalité de recherche de contenu dans le centre de sécurité & conformité. Cela inclut les recherches exécutées sur la page de **recherche de contenu** et les recherches associées à un cas de découverte électronique. Ces limites contribuent à maintenir l’intégrité et la qualité des services fournis aux organisations. Il existe également des limites liées à l’indexation des messages électroniques dans Exchange Online pour la recherche. Vous ne pouvez pas modifier la recherche de contenu ou les limites d’indexation de messagerie, mais vous devez en tenir compte pour pouvoir prendre ces limites en considération lors de la planification, de l’exécution et du dépannage des recherches de contenu.
  
## <a name="content-search-limits"></a>Limites de la recherche de contenu

Le tableau suivant répertorie les limites de recherche dans le centre de sécurité & conformité.
  
| Description de la limite | Limite |
|:-----|:-----|
|Nombre maximal de boîtes aux lettres ou de sites qui peuvent être recherchées dans une recherche de contenu unique  <br/> |Pas de limite <sup>1</sup> <br/> |
|Nombre maximal de recherches de contenu pouvant être exécutées en même temps dans votre organisation.  <br/> |0,30  <br/> |
|Nombre maximal de recherches de contenu qu’un utilisateur peut démarrer simultanément. Cette limite est probablement atteinte lorsque l’utilisateur tente de démarrer plusieurs recherches à l’aide de la commande **Get-ComplianceSearch \| Start-ComplianceSearch** dans la sécurité & PowerShell du centre de conformité.  <br/> |10   <br/> |
|Nombre maximal d’éléments par boîte aux lettres utilisateur qui s’affichent dans la page d’aperçu lors de la prévisualisation des résultats de la recherche de contenu.  <br/> |100  <br/> |
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres utilisateur qui s’affichent dans la page d’aperçu lors de la prévisualisation des résultats de la recherche de contenu. Les éléments les plus récents sont affichés.  <br/> |1 000  <br/> |
|Nombre maximal de boîtes aux lettres d’utilisateur dont vous pouvez afficher un aperçu des résultats de recherche. S'il existe plus de 1 000 boîtes aux lettres dont le contenu correspond à la requête de recherche, seules les 1 000 premières boîtes aux lettres contenant la majorité des résultats seront disponibles pour l'aperçu.  <br/> |1 000  <br/> |
|Nombre maximal d’éléments trouvés dans SharePoint et de sites OneDrive entreprise affichés dans la page d’aperçu lors de la prévisualisation des résultats de la recherche de contenu. Les éléments les plus récents sont affichés.  <br/> |200  <br/> |
|Nombre maximal de sites (dans SharePoint et OneDrive entreprise) pouvant être prévisualisés pour les résultats de la recherche. S’il existe plus de 200 total de sites qui contiennent du contenu correspondant à la requête de recherche, seuls les premiers sites 200 avec le plus de résultats de recherche seront disponibles pour l’aperçu.  <br/> |200  <br/> |
|Nombre maximal d’éléments par boîte aux lettres de dossiers publics affichés dans la page d’aperçu lors de la prévisualisation des résultats de la recherche de contenu.  <br/> |100  <br/> |
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres de dossiers publics qui s’affichent dans la page d’aperçu lors de la prévisualisation des résultats de la recherche de contenu.  <br/> |200  <br/> |
|Nombre maximal de boîtes aux lettres publiques pouvant être prévisualisées pour les résultats de la recherche. S’il y a plus de 500 boîtes aux lettres de dossiers publics qui contiennent du contenu correspondant à la requête de recherche, seules les 500 premières boîtes aux lettres de dossiers publics avec le plus de résultats de recherche seront disponibles pour l’aperçu.  <br/> |500  <br/> |
|Nombre maximal de caractères pour la requête de recherche (y compris les opérateurs et les conditions) pour une recherche de contenu.  <br/><br/> **Remarque :** Cette limite prend effet après l’extension de la requête, ce qui signifie que la requête est développée par rapport à chacun des mots clés. Par exemple, si une requête de recherche comporte 15 Mots clés et des paramètres et conditions supplémentaires, la requête est développée 15 fois, chacune avec les autres paramètres et conditions de la requête. Par conséquent, même si le nombre de caractères dans la requête de recherche est inférieur à la limite, il s’agit de la requête étendue susceptible de contribuer au dépassement de cette limite.  <br/> |**Boîtes aux lettres :** 10 000  <br/> **Sites :** 4 000 lors de la recherche sur tous les sites ou 2 000 lors de la recherche sur 20 sites <sup>2</sup> <br/> |
|Nombre maximal de variantes renvoyées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte dans une requête de recherche ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur de **proximité** .  <br/> |10 000 <sup>3</sup> <br/> |
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple,  `time*` ,  `one*` ou  `set*` .  <br/> |3   <br/> |
|Nombre maximal de boîtes aux lettres dans une recherche de contenu que vous pouvez supprimer des éléments à l’aide d’une action de recherche et de purge (à l’aide de la commande **New-ComplianceSearchAction-purge** ). Si la recherche de contenu pour laquelle vous effectuez une action de vidage pour a plus de boîtes aux lettres source que cette limite, l’action de vidage échouera. Pour plus d’informations sur la recherche et le vidage, voir [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).  <br/> |50 000  <br/> |
|Nombre maximal d’emplacements dans une recherche de contenu à partir desquels vous pouvez exporter des éléments. Si la recherche de contenu que vous exportez comporte plus de emplacements que cette limite, l’exportation échouera. Pour plus d’informations, consultez la rubrique [exporter des résultats de recherche de contenu](export-search-results.md).  <br/> |100 000  <br/> |

> [!NOTE]
> <sup>1</sup> bien que vous puissiez effectuer une recherche dans un nombre illimité de boîtes aux lettres dans une seule recherche, vous pouvez uniquement télécharger les résultats de recherche exportés à partir d’un maximum de 100 000 boîtes aux lettres à l’aide de l’outil d’exportation de découverte électronique dans Office 365 Security & Centre de conformité ou le centre de conformité Microsoft 365. Pour télécharger les résultats de la recherche à partir de plus de 100 000 boîtes aux lettres, vous devez utiliser la sécurité & PowerShell du centre de conformité. Pour plus d’informations et pour obtenir un exemple de script, consultez la rubrique [Exporting results from more 100 000 mailboxes](export-search-results.md#exporting-results-from-more-than-100000-mailboxes). <br/><br/> <sup>2</sup> lors de la recherche de sites SharePoint et OneDrive entreprise, les caractères des URL des sites en cours de recherche sont comptabilisés par rapport à cette limite. <br/><br/> <sup>3</sup> pour les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela indique qu’un mot a lieu dans un document, mais pas à son emplacement dans le document. Pour effectuer une requête d’expression (valeur de mot clé avec des guillemets doubles), nous devons comparer la position dans le document pour les mots de l’expression. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expression. Dans ce cas, nous développons la requête en interne avec tous les mots que le préfixe développe ; par exemple,  `"time*"` peut se développer sur  `"time OR timer OR times OR timex OR timeboxed OR …"` . Le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête, est de 10 000. Il n’existe pas de limite supérieure pour les termes autres que les expressions. 
  
## <a name="indexing-limits-for-email-messages"></a>Limites d’indexation pour les messages électroniques

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le renvoi d’un message électronique sous la forme d’un élément non indexé ou partiellement indexé dans les résultats d’une recherche de contenu.
  
| Limite d’indexation | Valeur maximale | Description |
|:-----|:-----|:-----|
|Taille maximale de pièce jointe|150 Mo  <br/> |Taille maximale d’une pièce jointe de courrier électronique qui analysera l’indexation. Toute pièce jointe dont la taille est supérieure à cette limite n’est pas analysée pour l’indexation et le message avec la pièce jointe est marqué comme partiellement indexé.  <br/> <br/>**Remarque :** L’analyse est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères superflus, tels que la ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé « tokening »), qui sont ensuite stockés dans l’index.           |
|Nombre maximal de pièces jointes  <br/> |250  <br/> |Nombre maximal de fichiers joints à un message électronique qui seront analysés pour l’indexation. Si un message contient plus de 250 pièces jointes, les 250 premières pièces jointes sont analysées et indexées, et le message est marqué comme partiellement indexé car il contient des pièces jointes supplémentaires qui n’ont pas été analysées.  <br/> |
|Profondeur maximale des pièces jointes  <br/> |0,30  <br/> |Nombre maximal de pièces jointes imbriquées qui sont analysées. Par exemple, si un message électronique est associé à un autre message et que le message joint contient un document Word joint, le document Word et le message joint sont indexés. Ce comportement se poursuivra pendant jusqu’à 30 pièces jointes imbriquées.  <br/> |
|Nombre maximal d’images attachées  <br/> |0  <br/> |Une image jointe à un message électronique est ignorée par l’analyseur et n’est pas indexée.  <br/> |
|Temps maximal passé à analyser un élément  <br/> |30 secondes  <br/> |Un maximum de 30 secondes est passé à analyser un élément pour l’indexation. Si la durée d’analyse est supérieure à 30 secondes, l’élément est marqué comme partiellement indexé.  <br/> |
|Sortie maximale de l’analyseur  <br/> |2 millions de caractères  <br/> |Quantité maximale de sortie de texte de l’analyseur qui est indexée. Par exemple, si l’analyseur a extrait 8 millions caractères d’un document, seuls les 2 millions premiers caractères sont indexés.  <br/> |
|Nombre maximal de jetons d’annotation  <br/> |2 millions  <br/> |Lorsqu’un message électronique est indexé, chaque mot est annoté avec des instructions de traitement différentes qui définissent le mode d’indexation de Word. Chaque ensemble d’instructions de traitement est appelé un jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions jetons d’annotation pour un message électronique.  <br/> |
|Taille maximale du corps dans l’index  <br/> |67 millions caractères  <br/> |Nombre total de caractères dans le corps d’un message électronique et toutes ses pièces jointes. Lorsqu’un message électronique est indexé, tout le texte dans le corps du message et dans toutes les pièces jointes est concaténé dans une chaîne unique. La taille maximale de cette chaîne indexée est de 67 millions caractères.  <br/> |
|Nombre maximal de jetons uniques dans le corps  <br/> |1 million  <br/> |Comme expliqué précédemment, les jetons sont le résultat de l’extraction de texte du contenu, la suppression de la ponctuation et des espaces, puis sa division en mots (appelés jetons) stockés dans l’index. Par exemple, l’expression  `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seulement 4 sont des jetons uniques. Il existe une limite de 1 million jetons uniques par message électronique, ce qui permet d’éviter que l’index soit trop volumineux avec des jetons aléatoires.  <br/> |
  
## <a name="more-information"></a>Informations supplémentaires

Il existe des limites supplémentaires liées à différents aspects de la recherche de contenu, telles que l’exportation des résultats de recherche et l’indexation du contenu. Pour obtenir une description de ces limites, consultez les rubriques suivantes :
  
- [Exporter les résultats de la recherche de contenu](export-search-results.md#export-limits)

- [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md)

- [Étude des éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)

- [Limites de recherche pour SharePoint Online](https://docs.microsoft.com/sharepoint/search-limits)

Pour plus d’informations sur les recherches de contenu, voir :
  
- [Recherche de contenu dans Microsoft 365](content-search.md)

- [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)
