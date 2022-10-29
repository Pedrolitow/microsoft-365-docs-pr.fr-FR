---
title: Utiliser un message d’état Teams pour affecter un délégué
author: samanro
ms.author: samanro
manager: pamgreen
audience: ITPro
ms.topic: how-to
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
- highpri
- EngageScoreSep2022
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: acolonna
description: Découvrez comment un utilisateur avec l’état Absent ou Ne pas déranger peut définir explicitement un autre utilisateur comme délégué dans son message d’état.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 799e5c4976d8725a8be5ddeff5e924fd4a3248e2
ms.sourcegitcommit: 0ad7edcfdcdd11d02fa8a14ffe4b36e120d92deb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2022
ms.locfileid: "68786472"
---
# <a name="use-a-teams-status-message-to-assign-a-delegate"></a>Utiliser un message d’état Teams pour affecter un délégué

Les utilisateurs de Microsoft Teams peuvent définir leur statut sur Absent ou Ne pas déranger, et inclure un message d’état texte personnalisé. Un utilisateur qui va être absent peut affecter quelqu’un en tant que délégué que les personnes peuvent contacter à la place. La fonctionnalité de délégation de message fonctionne comme suit :

1. L’utilisateur qui va être absent @mentions un autre utilisateur (le délégué) dans son message d’état pour indiquer aux utilisateurs de contacter le délégué à la place pendant l’absence de l’utilisateur.

    ![Capture d’écran d’un message d’état avec un utilisateur défini comme délégué.](media/message-delegation.png)

1. L’utilisateur qui a été @mentioned reçoit une notification indiquant qu’il a été nommé délégué.
1. Lorsqu’une personne ouvre une conversation avec l’utilisateur absent et voit son message d’état, elle peut pointer sur le délégué et lui envoyer facilement un message à la place.

Les utilisateurs peuvent lancer le processus eux-mêmes, et aucune intervention de l’administrateur n’est requise pour activer la fonctionnalité.

> [!NOTE]
> Les notes d’état et les comportements de mention de délégation sont également disponibles dans Skype Entreprise, mais leur disponibilité dépend du mode de coexistence de l’utilisateur. Skype Entreprise n’applique pas de limite de caractères sur les notes d’état. Toutefois, Microsoft Teams affiche uniquement les 280 premiers caractères d’un jeu de notes de Skype Entreprise. Une ellipse (...) à la fin d’une note indique qu’elle a été tronquée. Skype Entreprise ne prend pas en charge les délais d’expiration des notes. <br>Skype Entreprise Online a été mis hors service le 31 juillet 2021. [Découvrez comment effectuer une mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here).

## <a name="delegation-use-scenario-in-healthcare"></a>Scénario d’utilisation de la délégation dans le secteur de la santé

**Exemple d’utilisation sans définition de délégués**

Le Dr Franco Piccio est de garde au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’une de ses collègues du département de radiologie, le Dr Lena Ehrle, de couvrir pour lui pendant qu’il est parti. De façon informelle, il remet son radiomessagerie au Dr Ehrle, qui écoute les messages urgents et fait un ping sur le radiomessagerie et y répond au nom du Dr Piccio en plus de ses responsabilités actuelles. D’autres membres de l’équipe peuvent ne pas se rendre compte que la délégation informelle a eu lieu. Une confusion s’ensuit avec les soins d’un patient.

**Exemple d’utilisation avec la définition de délégués**

Le Dr Franco Piccio est de garde au service de radiologie. Il reçoit un appel personnel urgent et doit s’éloigner pour les prochaines heures. Il demande à l’une de ses collègues du département de radiologie, le Dr Lena Ehrle, de le couvrir pendant qu’il est parti. Il change son message d’état personnalisé pour dire « Je ne suis pas disponible pour les prochaines heures. Veuillez contacter @DrEhrle en cas d’urgence. »  D’autres membres de l’équipe se rendent compte que la délégation s’est produite alors qu’ils essayaient de contacter le Dr Piccio. Peu ou pas de confusion s’ensuit avec les soins d’un patient.
