---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: microsoft-365-frontline
ms.openlocfilehash: 6531024304774ce8d4316156dd7c83f42b1e0c65
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68222647"
---
Pour suivre les étapes décrites dans cet article, vous devez être administrateur général Microsoft 365 ou administrateur du connecteur Shifts.

 Le rôle d’administrateur du connecteur Shifts est un rôle personnalisé que vous créez dans Azure AD et que vous affectez à un utilisateur. Le nom du rôle doit être « Administrateur du connecteur Shifts ». Le rôle n’a pas besoin d’avoir d’autorisations spécifiques, même si au moins une autorisation doit être définie lors de sa création. Le service s’appuie sur la présence du rôle sur l’utilisateur, et non sur ses autorisations.  Pour en savoir plus, consultez [Créer et attribuer un rôle personnalisé dans Azure Active Directory](/azure/active-directory/roles/custom-create) et [Attribuer des rôles Azure AD aux utilisateurs](/azure/active-directory/roles/manage-roles-portal). N’oubliez pas que la création et l’application du rôle à un utilisateur peuvent prendre jusqu’à 24 heures.