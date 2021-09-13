---
title: Microsoft 365 identité cloud uniquement
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment créer des utilisateurs et des groupes lorsque votre abonnement Microsoft 365 utilise l’identité cloud uniquement.
ms.openlocfilehash: 9b58b831f2a338e5fb79726b8de66c11bba96d0e
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183439"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 identité cloud uniquement

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Avec l’identité cloud uniquement, tous vos utilisateurs, groupes et contacts sont stockés dans le client Azure Active Directory (Azure AD) de votre abonnement Microsoft 365 client. Voici les composants de base de l’identité cloud uniquement.
 
![Composants de base de l’identité cloud uniquement.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Les utilisateurs et leurs comptes d’utilisateurs dans les organisations peuvent être classés de plusieurs façons. Par exemple, certains sont des employés et ont un statut permanent. Certains fournisseurs, sous-traitants ou partenaires ont un statut temporaire. Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent tout de même avoir accès à des services et des ressources spécifiques pour prendre en charge l’interaction et la collaboration. Par exemple :

- Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud

- Les comptes B2B représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration

Faites le point sur les types d’utilisateurs de votre organisation. Quels sont les regroupements ? Par exemple, vous pouvez grouper des utilisateurs par fonction ou objectif de haut niveau pour votre organisation.

Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.

Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins qui simplifient la gestion de votre environnement cloud. Par exemple, avec les groupes Azure AD, vous pouvez :

- Utilisez la gestion des licences basée sur les groupes pour attribuer des licences Microsoft 365 à vos comptes d’utilisateurs automatiquement dès qu’elles sont ajoutées en tant que membres.
- Ajoutez dynamiquement des comptes d’utilisateur à des groupes spécifiques en fonction des attributs de compte d’utilisateur, tels que le nom du service.
- Approvisionnement automatique des utilisateurs pour les applications SaaS (Software as a Service) et pour protéger l’accès à ces applications à l’aide de l’authentification multifacteur (MFA) et d’autres stratégies d’accès conditionnel.
- Fournir des autorisations et des niveaux d’accès pour SharePoint sites d’équipe En ligne.

## <a name="next-steps-for-cloud-only-identity"></a>Étapes suivantes pour l’identité cloud uniquement

- [Gérer les comptes d’utilisateurs](manage-microsoft-365-accounts.md)
- [Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
- [Gérer les groupes et l’appartenance à un groupe](manage-microsoft-365-groups.md)
- [Gérer les mots de passe de compte d’utilisateur](manage-microsoft-365-passwords.md)
