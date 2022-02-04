---
title: Microsoft 365 identité cloud uniquement
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
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
  - Ent_O365
  - M365-identity-device-management
search.appverid:
  - MET150
  - MOP150
  - MOE150
  - MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment créer des utilisateurs et des groupes lorsque votre abonnement Microsoft 365 utilise l’identité cloud uniquement.
---

# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 identité cloud uniquement

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez choisi le modèle d’identité cloud uniquement, vous avez déjà un client Azure Active Directory (Azure AD) pour votre abonnement Microsoft 365 pour stocker tous vos utilisateurs, groupes et contacts. Après avoir mis en place la protection des comptes d’administrateur à l’étape [2](protect-your-global-administrator-accounts.md) et des comptes d’utilisateur à l’étape [3](microsoft-365-secure-sign-in.md) de cette solution, vous êtes maintenant prêt à commencer à créer les comptes et les groupes dont votre organisation a besoin.

Voici les composants de base de l’identité cloud uniquement.
 
![Composants de base de l’identité cloud uniquement.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Les utilisateurs et leurs comptes d’utilisateurs dans les organisations peuvent être classés de plusieurs façons. Par exemple, certains sont des employés et ont un statut permanent. Certains sont des fournisseurs, des sous-traitants ou des partenaires qui ont un statut temporaire. Certains sont des utilisateurs externes qui n’ont pas de compte d’utilisateur, mais qui doivent tout de même avoir accès à des services et des ressources spécifiques pour prendre en charge l’interaction et la collaboration. Par exemple :

- Les comptes client représentent les utilisateurs au sein de votre organisation auxquels vous octroyez une licence pour les services cloud

- Les comptes B2B représentent les utilisateurs externes à votre organisation que vous invitez à participer à la collaboration

Faites le point sur les types d’utilisateurs de votre organisation. Quels sont les regroupements ? Par exemple, vous pouvez grouper des utilisateurs par fonction ou objectif de haut niveau pour votre organisation.

Par ailleurs, certains services cloud peuvent être partagés avec des utilisateurs externes à votre organisation sans comptes d’utilisateur. Vous devrez identifier ces groupes d’utilisateurs également.

Vous pouvez utiliser des groupes dans Azure AD à plusieurs fins qui simplifient la gestion de votre environnement cloud. Par exemple, avec Azure AD groupes, vous pouvez :

- Utilisez la gestion des licences basée sur les groupes pour attribuer des licences Microsoft 365 à vos comptes d’utilisateurs automatiquement dès qu’elles sont ajoutées en tant que membres.
- Ajoutez dynamiquement des comptes d’utilisateur à des groupes spécifiques en fonction des attributs de compte d’utilisateur, tels que le nom du service.
- Approvisionnement automatique des utilisateurs pour les applications SaaS (Software as a Service) et pour protéger l’accès à ces applications à l’aide de l’authentification multifacteur (MFA) et d’autres stratégies d’accès conditionnel.
- Fournir des autorisations et des niveaux d’accès pour les équipes et SharePoint sites d’équipe en ligne.

## <a name="next-steps-for-cloud-only-identity"></a>Étapes suivantes pour l’identité cloud uniquement

- [Gérer les comptes d’utilisateurs](manage-microsoft-365-accounts.md)
- [Attribution de licences aux comptes d’utilisateurs](assign-licenses-to-user-accounts.md)
- [Gérer les groupes et l’appartenance aux groupes](manage-microsoft-365-groups.md)
- [Gérer les mots de passe de compte d’utilisateur](manage-microsoft-365-passwords.md)
