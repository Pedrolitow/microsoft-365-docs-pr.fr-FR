---
title: Gestion des destinataires dans Exchange Online Protection (EOP)
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2014
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 2921f544-8257-4bae-8e3a-ce9250e9f162
description: Microsoft Exchange Online Protection (EOP) vous propose plusieurs façons de gérer vos destinataires de message. En tant qu’administrateur, vous pouvez effectuer certaines tâches de gestion dans le centre d’administration Exchange ou à l’aide de Windows PowerShell à distance et vérifier les autres tâches de gestion effectuées dans le centre d’administration 365 de Microsoft.
ms.openlocfilehash: f1bac7d19b52d175589f63216b49ce3b0985307c
ms.sourcegitcommit: cbf117a4cd92a907115c9f10752f3c557361e586
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "37441471"
---
# <a name="manage-recipients-in-eop"></a>Gestion des destinataires dans Exchange Online Protection (EOP)

Microsoft Exchange Online Protection (EOP) vous propose plusieurs façons de gérer vos destinataires de message. En tant qu’administrateur, vous pouvez effectuer certaines tâches de gestion dans le centre d’administration Exchange ou à l’aide de Windows PowerShell à distance et vérifier les autres tâches de gestion effectuées dans le centre d’administration 365 de Microsoft.

EOP prend en charge les types de destinataires suivants :

- **Utilisateurs de messagerie**: les utilisateurs de messagerie sont des destinataires de vos domaines gérés EOP. Ces destinataires ont des informations d’identification d’ouverture de session dans votre organisation Office 365, mais elles ont des adresses de messagerie externes, ce qui signifie que leurs boîtes aux lettres de destinataire se trouvent en dehors de votre organisation en nuage.

  Vous pouvez ajouter des utilisateurs de messagerie afin qu’ils puissent recevoir des messages et que vous puissiez également créer des règles de flux de messagerie (également appelées règles de transport) pour des utilisateurs spécifiques. Vous pouvez également attribuer des rôles aux utilisateurs de messagerie de votre organisation ; les utilisateurs disposant de privilèges de groupe de rôles de gestion peuvent accéder au centre d’administration Exchange et effectuer certaines tâches de gestion. Pour en savoir plus sur les rôles d’utilisateur et sur l’attribution de rôles d’utilisateur dans EOP, consultez la rubrique [Manage admin Role Group Permissions in EOP](manage-admin-role-group-permissions-in-eop.md).

  Pour plus d'informations sur la gestion des utilisateurs de messagerie dans EOP, consultez la rubrique [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

- **Groupes**: les utilisateurs de messagerie peuvent être regroupés dans des groupes de distribution ou des groupes de sécurité.

Pour plus d'informations sur la gestion des groupes dans EOP, consultez la rubrique [Gestion des groupes dans Exchange Online Protection (EOP)](manage-groups-in-eop.md).
