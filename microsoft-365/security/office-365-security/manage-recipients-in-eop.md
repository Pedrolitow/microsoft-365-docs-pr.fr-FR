---
title: Gestion des destinataires dans Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2014
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 2921f544-8257-4bae-8e3a-ce9250e9f162
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous découvrirez les destinataires de messagerie pris en charge par Microsoft Exchange Online Protection (EOP).
ms.openlocfilehash: eb2855f93083c88725492be2691799c3521bbf8f
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036148"
---
# <a name="manage-recipients-in-eop"></a>Gestion des destinataires dans Exchange Online Protection (EOP)

Microsoft Exchange Online Protection (EOP) vous propose plusieurs façons de gérer vos destinataires de message. En tant qu’administrateur, vous pouvez effectuer certaines tâches de gestion dans le centre d’administration Exchange ou à l’aide de Windows PowerShell à distance et vérifier les autres tâches de gestion effectuées dans le centre d’administration 365 de Microsoft.

EOP prend en charge les types de destinataires suivants :

- **Utilisateurs de messagerie**: les utilisateurs de messagerie sont des destinataires de vos domaines gérés EOP. Ces destinataires ont des informations d’identification d’ouverture de session dans votre organisation, mais elles ont des adresses de messagerie externes, ce qui signifie que leurs boîtes aux lettres de destinataire se trouvent en dehors de votre organisation en nuage.

  Vous pouvez ajouter des utilisateurs de messagerie afin qu’ils puissent recevoir des messages et que vous puissiez également créer des règles de flux de messagerie (également appelées règles de transport) pour des utilisateurs spécifiques. Vous pouvez également attribuer des rôles aux utilisateurs de messagerie de votre organisation ; les utilisateurs disposant de privilèges de groupe de rôles de gestion peuvent accéder au centre d’administration Exchange et effectuer certaines tâches de gestion. Pour en savoir plus sur les rôles d’utilisateur et sur l’attribution de rôles d’utilisateur dans EOP, consultez la rubrique [Manage admin Role Group Permissions in EOP](manage-admin-role-group-permissions-in-eop.md).

  Pour plus d'informations sur la gestion des utilisateurs de messagerie dans EOP, consultez la rubrique [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

- **Groupes**: les utilisateurs de messagerie peuvent être regroupés dans des groupes de distribution ou des groupes de sécurité.

Pour plus d'informations sur la gestion des groupes dans EOP, consultez la rubrique [Gestion des groupes dans Exchange Online Protection (EOP)](manage-groups-in-eop.md).
