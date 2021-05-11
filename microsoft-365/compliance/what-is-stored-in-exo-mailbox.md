---
title: Contenu stocké dans des boîtes Exchange Online aux lettres
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: ''
description: Le contenu produit par les applications basées sur le cloud Microsoft 365 est stocké ou associé à la boîte aux lettres Exchange Online’un utilisateur. Ce contenu peut être recherché à l’aide des outils eDiscovery de Microsoft.
ms.openlocfilehash: 3490571a31ea69c5a8ee641a4ccc46077aced014
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52311003"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Contenu stocké dans Exchange Online boîtes aux lettres pour eDiscovery

Une boîte aux lettres dans Exchange Online est principalement utilisée pour stocker des éléments liés à la messagerie, tels que des messages, des éléments de calendrier, des tâches et des notes. Mais cela change à mesure que de plus en plus d’applications basées sur le cloud stockent également leurs données dans la boîte aux lettres d’un utilisateur. L’un des avantages du stockage des données dans une boîte aux lettres est que vous pouvez utiliser les outils de recherche dans la recherche de contenu, core eDiscovery et Advanced eDiscovery pour rechercher, afficher et exporter les données à partir de ces applications basées sur le cloud. Les données de certaines de ces applications sont stockées dans des dossiers masqués situés dans une sous-arbre de message non interpersonnel (non IPM) de la boîte aux lettres. Les données d’autres applications basées  sur le cloud peuvent  ne pas être stockées dans la boîte aux lettres, mais elles sont associées à la boîte aux lettres et sont renvoyées dans les recherches (si ces données sont associées à la requête de recherche). Que les données informatiques soient stockées ou associées à une boîte aux lettres utilisateur, elles ne sont généralement pas visibles dans un client de messagerie lorsqu’un utilisateur ouvre sa boîte aux lettres.

Le tableau suivant répertorie les applications qui stockent ou associent des données à une boîte aux lettres en nuage. Le tableau décrit également le type de contenu que chaque application produit.

|Microsoft 365 application|Description|
|:---------|:---------|
|Formulaires<sup>*</sup>|Les formulaires et les réponses à un formulaire sont stockés dans des fichiers joints à des messages électroniques et stockés dans un dossier masqué dans la boîte aux lettres de l’utilisateur qui a créé le formulaire. Les formulaires créés avant avril 2020 sont stockés sous forme de fichier PDF. Les formulaires créés après 2020 sont stockés en tant que fichier JSON.  Les réponses à un formulaire sont stockées dans un fichier CSV. Lorsque vous exportez du contenu à partir de formulaires dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** dans un sous-dossier nommé avec le GUID global unique suivant : **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**. |
|Groupes Microsoft 365|Les messages électroniques, les éléments de calendrier, les contacts (contacts), les notes et les tâches sont stockés dans la boîte aux lettres associée à un groupe Microsoft 365 de messagerie.|
|Outlook/Exchange Online|Les messages électroniques, les éléments de calendrier, les contacts (personnes), les notes et les tâches sont stockés dans la boîte aux lettres d’un utilisateur.|
|Personnes|Les contacts dans l’application Contacts (qui sont les mêmes contacts que ceux accessibles dans Outlook) sont stockés dans la boîte aux lettres d’un utilisateur.|
|Planification de classe|Les plans créés dans le Planning de classe sont stockés dans la boîte aux lettres du groupe Microsoft 365 correspondant qui est mis en service lors de la création d’un plan. L’alias de la boîte aux lettres de groupe est le nom du plan.|
|Skype Entreprise|Les conversations Skype Entreprise sont stockées dans le dossier Historique des conversations de la boîte aux lettres d’un utilisateur. Si la boîte aux lettres d’un participant à une réunion Skype est placée en conservation pour litige ou affectée à une stratégie de rétention, les fichiers joints à une réunion sont conservés dans la boîte aux lettres des participants.|
|Sway<sup>*</sup>|Les Sways sont stockés en tant que fichier HTML joint à un message électronique et stockés dans un dossier masqué dans la boîte aux lettres de l’utilisateur qui a créé le sway. Lorsque vous exportez du contenu à partir de Sway dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** dans un sous-dossier nommé avec le GUID suivant :  **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Tâches|Les tâches de l’application Tâches (qui sont les mêmes que les tâches accessibles dans Outlook) sont stockées dans la boîte aux lettres d’un utilisateur.|
|Teams|Les conversations qui font partie d’un canal Teams sont associées à la boîte aux lettres Teams’utilisateur. Les conversations qui font partie de la liste de conversation dans Teams (également appelées conversations *1 x N)* sont associées à la boîte aux lettres des utilisateurs qui participent à la conversation. En outre, les informations récapitulatifs pour les réunions et les appels dans un canal Teams sont associées aux boîtes aux lettres des utilisateurs qui ont appelé la réunion ou l’appel. Ainsi, lorsque vous recherchez Teams contenu, vous recherchez dans la boîte aux lettres Teams du contenu dans les conversations de canal et dans les boîtes aux lettres utilisateur de recherche de contenu dans les conversations 1 x N.|
|À faire|Les tâches (appelées tâches, qui sont enregistrées dans les listes de tâches) dans l’application To-Do sont *stockées* dans la boîte aux lettres d’un utilisateur.|
|Yammer|Les conversations et commentaires au sein d’une communauté Yammer sont associés à la boîte aux lettres de groupe Microsoft 365, ainsi qu’à la boîte aux lettres de l’utilisateur de l’auteur et aux destinataires nommés (utilisateurs @ mentionnés ou cc’ed). Les messages privés envoyés en dehors d Yammer communauté sont stockés dans la boîte aux lettres des utilisateurs qui participent au message privé.|  
||||

> [!NOTE]
> <sup>*</sup>Pour l’instant, si une conservation est placée sur une boîte aux lettres (à l’aide de conservations dans core eDiscovery ou des cas Advanced eDiscovery), le contenu de cette application ne sera pas conservé par la conservation.