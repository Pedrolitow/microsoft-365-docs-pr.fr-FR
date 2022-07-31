---
title: Délégation de messages
author: samanro
ms.author: samanro
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: acolonna
description: Découvrez comment un utilisateur avec l’état Absent ou Ne pas déranger peut définir explicitement un autre utilisateur en tant que délégué dans son message d’état.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 190b1f8bfdcf06c124163d97ecf77465f66ad67c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66992255"
---
# <a name="message-delegation"></a>Délégation de messages

Un utilisateur peut déjà définir explicitement son état sur Absent ou Ne pas déranger, et fournir du texte personnalisé. La fonctionnalité de délégation de message fonctionne comme suit :

1. Un utilisateur @username mentionne un autre utilisateur dans une partie d’un message d’état texte, ce qui suggère que, lorsqu’il s’agit de personnes non disponibles qui souhaitent les contacter à la place, contactez l’utilisateur mentionné @username.
2. La personne qui a été assignée en tant que déléguée est informée qu’elle a été nommée déléguée.
3. Une personne qui tente de contacter le premier utilisateur peut alors pointer sur le délégué désigné et lui envoyer facilement un message.  

Il s’agit d’un processus initié par l’utilisateur dans le client, et aucune participation Administration n’est requise pour activer la fonctionnalité. 

## <a name="delegation-use-scenario-in-healthcare"></a>Scénario d’utilisation de la délégation dans Healthcare

*Exemple d’utilisation sans définition de délégués :*  Le Dr Franco Piccio est sur appel au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’un de ses pairs du département de radiologie, le Dr Lena Ehrle, de le couvrir pendant qu’il est parti. Il remet de manière informelle sa page au Dr Ehrle, qui écoute les messages urgents et les pings sur le pagine et y répond au nom du Dr Piccio en plus de ses responsabilités actuelles. D’autres membres de l’équipe peuvent ne pas se rendre compte que la délégation informelle s’est produite, et la confusion s’ensuivit avec les soins d’un patient.

*Exemple d’utilisation avec la définition de délégués :* Le Dr Franco Piccio est sur appel au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’un de ses pairs du service de radiologie, le Dr Lena Ehrle, de le couvrir pendant qu’il est parti. Il modifie son message d’état personnalisé pour dire quelque chose de similaire à « Je ne suis pas disponible pour les prochaines heures. Veuillez contacter @DrEhrle pour toute urgence. »  D’autres membres de l’équipe se rendent compte que la délégation s’est produite alors qu’ils tentent de contacter le Dr Piccio. Peu ou pas de confusion s’ensuivit avec les soins d’un patient.

## <a name="impact-of-co-existence-modes-on-user-status-in-the-teams-client"></a>Impact des modes de coexistence sur l’état de l’utilisateur dans le client Teams

Les administrateurs doivent savoir que les notes d’état et les comportements de mention de délégation dépendent en partie du mode de coexistence d’un utilisateur. Cette matrice présente les possibilités suivantes :

|mode Co-Existence | Comportement attendu|
|---|---|
|TeamsOnly |Les utilisateurs peuvent définir une note uniquement à partir de Teams. <br> La note Teams de l’utilisateur est visible dans Teams & SfB. |
|Île | Note de l’utilisateur dans Teams visible uniquement dans Teams. <br> Ensemble de notes de l’utilisateur dans SfB visible uniquement dans SfB |
|Modes SfB* | Les utilisateurs peuvent définir une note uniquement à partir de SfB. <br> La note SfB de l’utilisateur est visible dans SfB & Teams.  |
|||

Un utilisateur ne peut définir une note dans Teams que si son mode est TeamsOnly ou Islands.  

### <a name="displaying-notes-set-in-skype-for-business"></a>Affichage des notes définies dans Skype Entreprise
  
Rien n’indique visuellement qu’une note a été définie à partir de Skype Entreprise.

Skype Entreprise n’applique pas de limite de caractères aux notes d’état. Microsoft Teams affiche uniquement les 280 premiers caractères d’un jeu de notes à partir de Skype Entreprise. Une ellipse (...) à la fin d’une note indique une troncation.
  
Skype Entreprise ne prend pas en charge les délais d’expiration des notes.

La migration des notes de Skype Entreprise vers Teams n’est pas prise en charge lorsqu’un utilisateur est mis à niveau vers le mode TeamsOnly.

## <a name="related-topics"></a>Voir aussi

[Coexistence avec Skype Entreprise](/microsoftteams/coexistence-chat-calls-presence)
