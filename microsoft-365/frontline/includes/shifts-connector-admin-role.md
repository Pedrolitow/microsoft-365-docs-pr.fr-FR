---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: 9be6e2c31177d0fbfe2b896aa5e346d2aafc3aea
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822489"
---
Pour suivre les étapes décrites dans cet article, vous devez être administrateur général Microsoft 365 ou administrateur du connecteur Shifts.

 Le rôle d’administrateur du connecteur Shifts est un rôle personnalisé que vous créez dans Azure AD et que vous affectez à un utilisateur. Le nom du rôle doit être « Administrateur du connecteur Shifts ». Le rôle n’a pas besoin d’avoir d’autorisations spécifiques, même si au moins une autorisation doit être définie lors de sa création. Le service s’appuie sur la présence du rôle sur l’utilisateur, et non sur ses autorisations.  Pour en savoir plus, consultez [Créer et attribuer un rôle personnalisé dans Azure Active Directory](/azure/active-directory/roles/custom-create) et [Attribuer des rôles Azure AD aux utilisateurs](/azure/active-directory/roles/manage-roles-portal). N’oubliez pas que la création et l’application du rôle à un utilisateur peuvent prendre jusqu’à 24 heures.