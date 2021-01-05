---
title: Contenu stocké dans les boîtes aux lettres Exchange Online
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
ROBOTS: NOINDEX, NOFOLLOW
description: Les données générées par les applications basées sur le nuage dans Microsoft 365 sont stockées ou associées à la boîte aux lettres Exchange Online d’un utilisateur.
ms.openlocfilehash: f7bd5b00e8219f382078eb2d4f8aa25bd4c54d69
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49750745"
---
# <a name="content-stored-in-exchange-online-mailboxes"></a>Contenu stocké dans les boîtes aux lettres Exchange Online

Une boîte aux lettres dans Exchange Online est principalement utilisée pour stocker des éléments liés au courrier électronique, tels que des messages, des éléments de calendrier, des tâches et des notes. En revanche, il en est de même pour les applications en nuage qui stockent leurs données dans la boîte aux lettres d’un utilisateur. L’un des avantages du stockage de données dans une boîte aux lettres est que vous pouvez utiliser les outils de recherche dans la recherche de contenu, Core eDiscovery, Advanced eDiscovery pour rechercher, afficher et exporter les données à partir de ces applications basées sur le Cloud. Les données de certaines de ces applications sont stockées dans des dossiers cachés situés dans une sous-arborescence non de message interpersonnel (non-IPM) dans la boîte aux lettres. Les données d’autres applications Cloud peuvent ne pas être stockées _dans_ la boîte aux lettres, mais elles sont _associées à_ la boîte aux lettres et sont renvoyées dans les recherches (si ces données correspondent à la requête de recherche). Que les données basées sur le Cloud soient stockées dans ou associées à une boîte aux lettres utilisateur, les données ne sont généralement pas visibles dans un client de messagerie lorsqu’un utilisateur ouvre sa boîte aux lettres.

Le tableau suivant répertorie les applications qui stockent ou associent des données à une boîte aux lettres basée sur un nuage. Le tableau décrit également le type de contenu généré par chaque application.

|Application Microsoft 365|Description|
|:---------|:---------|
|Formulaires|Les formulaires et les réponses à un formulaire sont stockés dans des fichiers joints aux messages électroniques et stockés dans un dossier masqué dans la boîte aux lettres de l’utilisateur qui a créé le formulaire. Les formulaires créés avant le 2020 avril sont stockés sous forme de fichier PDF. Les formulaires créés après 2020 sont stockés en tant que fichiers JSON.  Les réponses à un formulaire sont stockées dans un fichier CSV. Lorsque vous exportez du contenu à partir de formulaires dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** d’un sous-dossier nommé avec le GUID suivant : **c9a559d2-7aab-4F13-A6ED-e7e9c52aec87**.|
|Groupes Microsoft 365|Les messages électroniques, les éléments de calendrier, les contacts (personnes), les notes et les tâches sont stockés dans la boîte aux lettres associée à un groupe Microsoft 365.|
|Outlook/Exchange Online|Les messages électroniques, les éléments de calendrier, les contacts (personnes), les notes et les tâches sont stockés dans la boîte aux lettres d’un utilisateur.|
|Personnes|Les contacts dans l’application contacts (qui sont les mêmes contacts que ceux accessibles dans Outlook) sont stockés dans la boîte aux lettres d’un utilisateur.|
|Planification de la classe|Les plans créés au cours de la planification de classe sont stockés dans la boîte aux lettres du groupe Microsoft 365 correspondant qui est mis en service lors de la création d’un plan. L’alias de la boîte aux lettres de groupe est le nom du plan.|
|Skype Entreprise|Les conversations dans Skype entreprise sont stockées dans le dossier historique des conversations dans la boîte aux lettres d’un utilisateur. Si la boîte aux lettres d’un participant à une réunion Skype est placée en conservation pour litige ou affectée à une stratégie de rétention, les fichiers joints à une réunion sont conservés dans la boîte aux lettres des participants.|
|Sway|Les Sways sont stockés sous forme de fichier HTML joint à un message électronique et stockés dans un dossier masqué dans la boîte aux lettres de l’utilisateur qui a créé le Sway. Lorsque vous exportez du contenu à partir de Sway dans un fichier PST, ces données se trouvent dans le dossier **ApplicationDataRoot** dans un sous-dossier nommé avec le GUID suivant) **905fcf26-4EB7-48A0-9ff0-8dcc7194b5ba**.|
|Tâches|Les tâches de l’application tâches (qui sont les mêmes que celles qui sont accessibles dans Outlook) sont stockées dans la boîte aux lettres d’un utilisateur.|
|Teams|Les conversations qui font partie d’un canal teams sont associées à la boîte aux lettres de teams. Les conversations qui font partie de la liste des conversations dans Teams (également appelées « *conversations 1 x N*) » sont associées à la boîte aux lettres des utilisateurs qui participent à la conversation. De plus, les informations de synthèse pour les réunions et les appels dans un canal teams sont associées aux boîtes aux lettres des utilisateurs qui ont composé la réunion ou l’appel. Par conséquent, lorsque vous recherchez du contenu de teams, vous recherchez dans la boîte aux lettres de teams du contenu dans les conversations de canal et des boîtes aux lettres utilisateur de recherche de contenu dans des conversations 1 x N.| 
|À faire|Les tâches (appelées *actions*, qui sont enregistrées dans les listes de tâches) de l’application To-Do sont stockées dans la boîte aux lettres d’un utilisateur.|
|Yammer|Les conversations et les commentaires au sein d’une communauté Yammer sont associés à la boîte aux lettres de groupe Microsoft 365, ainsi qu’à la boîte aux lettres utilisateur de l’auteur et des destinataires nommés (@mentioned ou utilisateurs cc). Les messages privés envoyés en dehors d’une communauté Yammer sont stockés dans la boîte aux lettres des utilisateurs qui participent au message privé.|  
||||

> [!NOTE]
> Pour l’instant, si une boîte aux lettres est placée en conservation (en utilisant des suspensions dans la découverte électronique et des cas avancés de découverte électronique), le contenu des formulaires et de Sway ne sera pas préservé par la suspension. 
