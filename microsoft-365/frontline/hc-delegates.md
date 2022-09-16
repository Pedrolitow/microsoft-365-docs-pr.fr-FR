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
ms.openlocfilehash: 33622e118bfb19a927dad8c4c559bdc234ff0937
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67736759"
---
# <a name="message-delegation"></a>Délégation de messages

Les utilisateurs de Microsoft Teams peuvent définir leur état sur Absent ou Ne pas déranger, et inclure un message d’état de texte personnalisé. Un utilisateur qui va être absent peut affecter une personne en tant que délégué que les personnes peuvent contacter à la place. La fonctionnalité de délégation de message fonctionne comme suit :

1. L’utilisateur qui sera absent @mentions un autre utilisateur (le délégué) dans son message d’état pour indiquer aux utilisateurs de contacter le délégué à la place pendant son absence.

    ![Capture d’écran d’un message d’état avec un utilisateur défini comme délégué.](media/message-delegation.png)

1. L’utilisateur qui a été @mentioned est averti qu’il a été nommé délégué.
1. Lorsqu’une personne ouvre une conversation avec l’utilisateur absent et voit son message d’état, elle peut pointer sur le délégué et lui transmettre facilement un message à la place.

Les utilisateurs peuvent lancer le processus eux-mêmes, et aucune participation de l’administrateur n’est requise pour activer la fonctionnalité.

## <a name="delegation-use-scenario-in-healthcare"></a>Scénario d’utilisation de la délégation dans Healthcare

**Exemple d’utilisation sans définition de délégués**

Le Dr Franco Piccio est de garde au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’un de ses pairs du service de radiologie, le Dr Lena Ehrle, de le couvrir pendant qu’il est parti. Il remet de manière informelle sa page au Dr Ehrle, qui écoute les messages urgents et les pings sur le pagine et y répond au nom du Dr Piccio en plus de ses responsabilités actuelles. D’autres membres de l’équipe ne se rendent peut-être pas compte que la délégation informelle s’est produite. La confusion s’ensuivit avec les soins d’un patient.

**Exemple d’utilisation avec la définition de délégués**

Le Dr Franco Piccio est de garde au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’un de ses pairs du service de radiologie, le Dr Lena Ehrle, de le couvrir pendant qu’il est parti. Il modifie son message d’état personnalisé pour dire « Je ne suis pas disponible pour les prochaines heures. Veuillez contacter @DrEhrle pour toute urgence. »  D’autres membres de l’équipe se rendent compte que la délégation s’est produite alors qu’ils tentent de contacter le Dr Piccio. Peu ou pas de confusion s’ensuivit avec les soins d’un patient.

## <a name="impact-of-co-existence-modes-on-user-status-in-the-teams-client"></a>Impact des modes de coexistence sur l’état de l’utilisateur dans le client Teams

Les notes d’état et les comportements de mention de délégation dépendent en partie du mode de coexistence d’un utilisateur. Cette matrice présente les possibilités suivantes :

|mode Co-Existence | Comportement attendu|
|---|---|
|TeamsOnly |Les utilisateurs peuvent définir une note uniquement à partir de Teams. <br> La note Teams de l’utilisateur est visible dans Teams & SfB. |
|Île | Note de l’utilisateur dans Teams visible uniquement dans Teams. <br> Ensemble de notes de l’utilisateur dans SfB visible uniquement dans SfB |
|Modes SfB* | Les utilisateurs peuvent définir une note uniquement à partir de SfB. <br> La note SfB de l’utilisateur est visible dans SfB & Teams.  |

Un utilisateur ne peut définir une note dans Teams que si son mode est TeamsOnly ou Islands.  

### <a name="displaying-notes-set-in-skype-for-business"></a>Affichage des notes définies dans Skype Entreprise
  
Rien n’indique visuellement qu’une note a été définie à partir de Skype Entreprise.

Skype Entreprise n’applique pas de limite de caractères aux notes d’état. Toutefois, Microsoft Teams affiche uniquement les 280 premiers caractères d’un jeu de notes à partir de Skype Entreprise. Un point de suspension (...) à la fin d’une note indique qu’il a été tronqué.
  
Skype Entreprise ne prend pas en charge les délais d’expiration des notes.

La migration des notes de Skype Entreprise vers Teams n’est pas prise en charge lorsqu’un utilisateur est mis à niveau vers le mode TeamsOnly.

## <a name="related-topics"></a>Voir aussi

[Mer informasjon sur la coexistence avec Skype Entreprise](/microsoftteams/coexistence-chat-calls-presence).
