---
title: Contenu stocké dans des boîtes aux lettres Exchange Online pour eDiscovery
description: Le contenu produit par les applications cloud dans Microsoft 365 est stocké ou associé à la boîte aux lettres Exchange Online d’un utilisateur. Vous pouvez rechercher ce contenu à l’aide des outils Microsoft eDiscovery.
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
- MED150
- MET150
ms.openlocfilehash: d848d25989def72d8a9056c39c9871bbd095ad05
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687821"
---
# <a name="content-stored-in-exchange-online-mailboxes-for-ediscovery"></a>Contenu stocké dans des boîtes aux lettres Exchange Online pour eDiscovery

Une boîte aux lettres dans Exchange Online est principalement utilisée pour stocker des éléments liés à l’e-mail tels que des messages, des éléments de calendrier, des tâches et des notes. Mais cela change, car de plus en plus d’applications basées sur le cloud stockent également leurs données dans la boîte aux lettres d’un utilisateur. L’un des avantages du stockage des données dans une boîte aux lettres est que vous pouvez utiliser les outils de recherche dans la recherche de contenu, Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium) pour rechercher, afficher et exporter les données à partir de ces applications cloud. 

Les données de certaines de ces applications sont stockées dans des dossiers masqués situés dans une sous-arborescence de message non-personnel (non-IPM) dans la boîte aux lettres. Les données d’autres applications cloud peuvent ne pas être stockées _dans_ la boîte aux lettres, mais elles sont _associées à_ la boîte aux lettres et sont retournées dans les recherches (si ces données correspondent à la requête de recherche). Que les données basées sur le cloud soient stockées ou associées à une boîte aux lettres utilisateur, les données ne sont généralement pas visibles dans un client de messagerie lorsqu’un utilisateur ouvre sa boîte aux lettres.

Le tableau suivant répertorie les applications qui stockent ou associent des données à une boîte aux lettres basée sur le cloud. Le tableau décrit également le type de contenu produit par chaque application.

|Application Microsoft 365|Description|
|:----------------|:----------|
|Formes<sup>*</sup>|Les formulaires et les réponses à un formulaire sont stockés dans des fichiers joints à des messages électroniques et stockés dans un dossier masqué de la boîte aux lettres de l’utilisateur qui a créé le formulaire. Les formulaires créés avant avril 2020 sont stockés sous forme de fichier PDF. Les formulaires créés après 2020 sont stockés sous forme de fichier JSON. Les réponses à un formulaire sont stockées dans un fichier CSV. Lorsque vous exportez du contenu à partir de Formulaires dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** dans un sous-dossier nommé avec le GUID (global unique identifié) suivant : **c9a559d2-7aab-4f13-a6ed-e7e9c52aec87**.|
|Groupes Microsoft 365|Email messages, éléments de calendrier, contacts (Personnes), notes et tâches sont stockés dans la boîte aux lettres associée à un groupe Microsoft 365.|
|Outlook/Exchange Online|Email messages, éléments de calendrier, contacts (Personnes), notes et tâches sont stockés dans la boîte aux lettres d’un utilisateur.|
|Personnes|Les contacts de l’application Personnes (qui sont les mêmes que ceux accessibles dans Outlook) sont stockés dans la boîte aux lettres d’un utilisateur.|
|Planification des classes|Les plans créés dans la planification de classes sont stockés dans la boîte aux lettres du groupe Microsoft 365 correspondant qui est approvisionné lors de la création d’un plan. L’alias de la boîte aux lettres de groupe est le nom du plan.|
|Skype Entreprise|Les conversations dans Skype Entreprise sont stockées dans le dossier Historique des conversations de la boîte aux lettres d’un utilisateur. Si la boîte aux lettres d’un participant à une réunion Skype est placée en attente pour litige ou affectée à une stratégie de rétention, les fichiers joints à une réunion sont conservés dans la boîte aux lettres des participants.|
|Sway<sup>*</sup>|Les Sways sont stockés sous la forme d’un fichier HTML joint à un e-mail et stockés dans un dossier masqué dans la boîte aux lettres de l’utilisateur qui a créé le sway. Lorsque vous exportez du contenu à partir de Sway dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** dans un sous-dossier nommé avec le GUID suivant : **905fcf26-4eb7-48a0-9ff0-8dcc7194b5ba**.|
|Tâches|Les tâches de l’application Tâches (qui sont les mêmes que celles accessibles dans Outlook) sont stockées dans la boîte aux lettres d’un utilisateur.|
|Teams|Les conversations qui font partie d’un canal Teams sont associées à la boîte aux lettres Teams. Les conversations qui font partie de la liste des conversations dans Teams (également *appelées 1 x N conversations*) sont associées à la boîte aux lettres des utilisateurs qui participent à la conversation. En outre, les informations récapitulatives pour les réunions et les appels dans un canal Teams sont associées aux boîtes aux lettres des utilisateurs qui se sont connectés à la réunion ou à l’appel. Par conséquent, lors de la recherche de contenu Teams, vous devez rechercher dans la boîte aux lettres Teams du contenu dans les conversations de canal et rechercher du contenu dans les boîtes aux lettres des utilisateurs dans 1 x N conversations.|
|À faire|Les tâches ( *appelées tâches*, qui sont enregistrées dans des listes de tâches) de l’application To-Do sont stockées dans la boîte aux lettres d’un utilisateur.|
|Yammer|Les conversations et les commentaires au sein d’une communauté Yammer sont associés à la boîte aux lettres du groupe Microsoft 365, ainsi qu’à la boîte aux lettres utilisateur de l’auteur et des destinataires nommés (utilisateurs @ mentionnés ou cc). Les messages privés envoyés en dehors d’une communauté Yammer sont stockés dans la boîte aux lettres des utilisateurs qui participent au message privé.|
|

> [!NOTE]
> <sup>*</sup> À ce stade, si une conservation est placée sur une boîte aux lettres (en utilisant des conservations dans les cas eDiscovery (Standard) ou eDiscovery (Premium), le contenu de cette application ne sera pas conservé par la conservation.
