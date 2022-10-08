---
title: Identité microsoft 365 cloud uniquement
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- scotvorg
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment créer des utilisateurs et des groupes lorsque votre abonnement Microsoft 365 utilise une identité cloud uniquement.
ms.openlocfilehash: 17298d6f6c07ddfa571610d6038326bcf9ec91cf
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68198490"
---
# <a name="microsoft-365-cloud-only-identity"></a>Identité microsoft 365 cloud uniquement

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez choisi le modèle d’identité cloud uniquement, vous disposez déjà d’un locataire Azure Active Directory (Azure AD) pour votre abonnement Microsoft 365 afin de stocker tous vos utilisateurs, groupes et contacts. Après avoir configuré la protection des comptes d’administrateur à [l’étape 2](protect-your-global-administrator-accounts.md) et des comptes d’utilisateur à [l’étape 3](microsoft-365-secure-sign-in.md) de cette solution, vous êtes maintenant prêt à commencer à créer les nouveaux comptes et groupes dont votre organisation a besoin.

Voici les composants de base de l’identité cloud uniquement.
 
![Composants de base de l’identité cloud uniquement.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Les utilisateurs et leurs comptes d’utilisateur dans les organisations peuvent être classés de plusieurs façons. Par exemple, certains sont des employés et ont un statut permanent. Certains sont des fournisseurs, des sous-traitants ou des partenaires qui ont un statut temporaire. Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent quand même avoir accès à des services et ressources spécifiques pour prendre en charge l’interaction et la collaboration. Par exemple :

- Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud

- Les comptes B2B représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration

Faites le point sur les types d’utilisateurs de votre organisation. Quels sont les regroupements ? Par exemple, vous pouvez regrouper des utilisateurs par fonction ou objectif de haut niveau auprès de votre organisation.

Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.

Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins qui simplifient la gestion de votre environnement cloud. Par exemple, avec des groupes Azure AD, vous pouvez :

- Utilisez les licences basées sur des groupes pour attribuer automatiquement des licences pour Microsoft 365 à vos comptes d’utilisateurs dès qu’ils sont ajoutés en tant que membres.
- Ajoutez des comptes d’utilisateur à des groupes spécifiques dynamiquement en fonction des attributs de compte d’utilisateur, tels que le nom du service.
- Provisionnez automatiquement les utilisateurs pour les applications SaaS (Software as a Service) et protégez l’accès à ces applications avec l’authentification multifacteur (MFA) et d’autres stratégies d’accès conditionnel.
- Provisionnez les autorisations et les niveaux d’accès pour les équipes et les sites d’équipe SharePoint Online.

## <a name="next-steps-for-cloud-only-identity"></a>Étapes suivantes pour l’identité cloud uniquement

- [Gérer les comptes d’utilisateurs](manage-microsoft-365-accounts.md)
- [Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
- [Gérer les groupes et l’appartenance aux groupes](manage-microsoft-365-groups.md)
- [Gérer les mots de passe de compte d’utilisateur](manage-microsoft-365-passwords.md)
