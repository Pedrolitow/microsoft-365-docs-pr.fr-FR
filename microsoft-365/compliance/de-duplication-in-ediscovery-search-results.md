---
title: Déduplication dans les résultats de recherche eDiscovery
description: Découvrez comment éliminer les résultats de recherche eDiscovery en double afin qu’une seule copie d’un message électronique soit exportée.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 12/21/2016
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
ms.custom:
- seo-marvel-apr2020
ms.openlocfilehash: 814e2f5f2c84712aec2baebaa6b21ca53f450b43
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688475"
---
# <a name="de-duplication-in-ediscovery-search-results"></a>Déduplication dans les résultats de recherche eDiscovery

Cet article décrit le fonctionnement de la déduplication des résultats de recherche eDiscovery et explique les limitations de l’algorithme de déduplication.
  
Lorsque vous utilisez des outils eDiscovery pour exporter les résultats d’une recherche eDiscovery, vous avez la possibilité de dédupliquer les résultats exportés. Qu’est-ce que cela signifie ? Lorsque vous activez la déduplication (par défaut, la déduplication n’est pas activée), une seule copie d’un e-mail est exportée même si plusieurs instances du même message peuvent avoir été trouvées dans les boîtes aux lettres qui ont fait l’objet d’une recherche. La déduplication vous permet de gagner du temps en réduisant le nombre d’éléments que vous devez examiner et analyser après l’exportation des résultats de la recherche. Toutefois, il est important de comprendre le fonctionnement de la déduplication et de savoir qu’il existe des limitations à l’algorithme qui peuvent entraîner la marque d’un élément unique comme doublon pendant le processus d’exportation.

Les informations contenues dans cet article s’appliquent lors de l’exportation des résultats de recherche à l’aide de l’un des outils eDiscovery suivants :

- [Recherche de contenu](/microsoft-365/compliance/search-for-content) dans le portail de conformité Microsoft Purview
- [Découverte électronique inaltérable dans Exchange Online](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)
- Centre [eDiscovery dans SharePoint Online](/sharepoint/dev/general-development/ediscovery-in-sharepoint)
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-duplicate-messages-are-identified"></a>Comment les messages en double sont identifiés

Les outils eDiscovery utilisent une combinaison des propriétés d’e-mail suivantes pour déterminer si un message est un doublon :
  
- **InternetMessageId** : cette propriété spécifie l’identificateur de message Internet d’un message électronique, qui est un identificateur global unique qui fait référence à une version spécifique d’un message spécifique. Cet ID est généré par le programme client de messagerie de l’expéditeur ou le système de messagerie hôte qui envoie le message. Si une personne envoie un message à plusieurs destinataires, l’ID de message Internet est le même pour chaque instance du message. Les révisions suivantes du message d’origine recevront un identificateur de message différent.
- **ConversationTopic** : cette propriété spécifie l’objet du thread de conversation d’un message. La valeur de la propriété **ConversationTopic** est la chaîne qui décrit l’article global de la conversation. Une conversation se compose d’un message initial et de tous les messages envoyés en réponse au message initial. Les messages au sein d’une même conversation ont la même valeur pour la propriété **ConversationTopic** . La valeur de cette propriété est généralement la ligne Objet du message initial qui a généré la conversation.
- **BodyTagInfo** : il s’agit d’une propriété de magasin Exchange interne. La valeur de cette propriété est calculée en vérifiant différents attributs dans le corps du message. Cette propriété est utilisée pour identifier les différences dans le corps des messages.

Pendant le processus d’exportation eDiscovery, ces trois propriétés sont comparées pour chaque message qui correspond aux critères de recherche. Si ces propriétés sont identiques pour deux messages (ou plus), ces messages sont déterminés comme étant des doublons, et le résultat est qu’une seule copie du message est exportée si la déduplication est activée. Le message exporté est appelé « élément source ». Les informations sur les messages en double sont incluses dans les **rapportsResults.csv** et **Manifest.xml** qui sont inclus dans les résultats de recherche exportés. Dans le fichier **Results.csv** , un message en double est identifié par une valeur dans la colonne **Dupliquer en élément** . La valeur de cette colonne correspond à la valeur dans la colonne **Identité de l’élément** pour le message qui a été exporté.
  
Les graphiques suivants montrent comment les messages en double sont affichés dans les **rapportsResults.csv** et **Manifest.xml** exportés avec les résultats de la recherche. Ces rapports n’incluent pas les propriétés d’e-mail décrites précédemment, qui sont utilisées dans l’algorithme de déduplication. Au lieu de cela, les rapports incluent la propriété **Item Identity** qui est affectée aux éléments par le magasin Exchange. 
  
### <a name="resultscsv-report-viewed-in-excel"></a>Results.csv rapport (consulté dans Excel)
  
![Affichage des informations sur les éléments en double dans le rapport Results.csv.](../media/e3d64004-3b91-4cba-b6f3-934b46cbdcdb.png)
  
### <a name="manifestxml-report-viewed-in-excel"></a>Manifest.xml rapport (consulté dans Excel)
  
![Affichage des informations sur les éléments en double dans le rapport Manifest.xml.](../media/69aa4786-9883-46ff-bcae-b35e0daf4a6d.png)
  
En outre, d’autres propriétés des messages en double sont incluses dans les rapports d’exportation. Cela inclut la boîte aux lettres dans laquelle se trouve le message en double, si le message a été envoyé à un groupe de distribution et si le message a été cccc’d à un autre utilisateur.
  
## <a name="limitations-of-the-de-duplication-algorithm"></a>Limitations de l’algorithme de déduplication

Il existe certaines limitations connues de l’algorithme de déduplication qui peuvent entraîner la marque d’éléments uniques en tant que doublons. Il est important de comprendre ces limitations afin de pouvoir décider d’utiliser ou non la fonctionnalité de déduplication facultative.
  
Il existe une situation dans laquelle la fonctionnalité de déduplication peut identifier par erreur un message en tant que doublon et ne pas l’exporter (mais toujours le citer comme doublon dans les rapports d’exportation). Il s’agit de messages qu’un utilisateur modifie mais n’envoie pas. Par exemple, supposons qu’un utilisateur sélectionne un message dans Outlook, copie le contenu du message, puis le colle dans un nouveau message. Ensuite, l’utilisateur modifie l’une des copies en supprimant ou en ajoutant une pièce jointe, ou en modifiant la ligne d’objet ou le corps lui-même. Si ces deux messages correspondent à la requête d’une recherche eDiscovery, un seul des messages est exporté si la déduplication est activée lorsque les résultats de la recherche sont exportés. Ainsi, même si le message d’origine ou le message copié a été modifié, aucun des messages révisés n’a été envoyé et, par conséquent, les valeurs des propriétés **InternetMessageId**, **ConversationTopic** et **BodyTagInfo** n’ont pas été mises à jour. Mais comme expliqué précédemment, les deux messages seront répertoriés dans les rapports d’exportation 
  
Les messages uniques peuvent également être marqués comme des doublons lorsque la fonctionnalité de protection de page copie en écriture est activée, comme dans le cas d’une boîte aux lettres en attente pour litige ou In-Place mise en attente. La fonctionnalité Copie sur écriture copie le message d’origine (et l’enregistre dans le dossier Versions du dossier Éléments récupérables de l’utilisateur) avant l’enregistrement de la révision de l’élément d’origine. Dans ce cas, la copie révisée et le message d’origine (dans le dossier Éléments récupérables) peuvent être considérés comme des messages en double et, par conséquent, un seul d’entre eux est exporté.
  
> [!IMPORTANT]
> Si les limitations de l’algorithme de déduplication peuvent avoir un impact sur la qualité de vos résultats de recherche, vous ne devez pas activer la déduplication lorsque vous exportez des éléments. Si les situations décrites dans cette section sont peu susceptibles d’être un facteur dans vos résultats de recherche et que vous souhaitez réduire le nombre d’éléments les plus susceptibles d’être des doublons, vous devez envisager d’activer la déduplication. 
  
## <a name="more-information"></a>Plus d’informations

Pour plus d’informations sur l’exportation des résultats de recherche, consultez :

- [Exporter la recherche de contenu](export-search-results.md)
- [Exporter un rapport de recherche de contenu](export-a-content-search-report.md)
- [Exporter In-Place résultats de la recherche eDiscovery vers un fichier PST](/exchange/security-and-compliance/in-place-ediscovery/export-search-results)
- [Exporter du contenu et créer des rapports dans le centre eDiscovery](/SharePoint/governance/export-content-and-create-reports-in-the-ediscovery-center)
