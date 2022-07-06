---
title: Protéger l’accès aux appareils et l’accès des utilisateurs
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Découvrez comment protéger l’accès des utilisateurs et des appareils aux données et services Microsoft 365 et vous défendre contre la perte de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f8b6b266d037e8bbc185643e530bf7a2f6919038
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623700"
---
# <a name="protect-user-and-device-access"></a>Protéger l’accès aux appareils et l’accès des utilisateurs

La protection de l’accès à vos données et services Microsoft 365 est essentielle pour la défense contre les cyberattaques et la protection contre la perte de données. Les mêmes protections peuvent être appliquées à d’autres applications SaaS dans votre environnement et même à des applications locales publiées avec Azure Active Directory Proxy d'application.
  
## <a name="step-1-review-recommendations"></a>Étape 1 : Passer en revue les recommandations

Découvrez les fonctionnalités recommandées relatives à la protection des identités et des appareils qui accèdent à Office 365, aux autres services SaaS et applications locales publiées avec le proxy d’application Azure AD.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) | [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) | [Plus de langues](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Étape 2 : Protéger les comptes d’administrateur et l’accès

Les comptes d’administration que vous utilisez pour administrer votre environnement Microsoft 365 incluent des privilèges élevés. Il s’agit de cibles précieuses pour les pirates informatiques et les cyberattaques.

Commencez par utiliser des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent disposer d’un compte d’utilisateur distinct pour une utilisation régulière et non administrative et utiliser uniquement leur compte d’administration si nécessaire pour effectuer une tâche associée à leur fonction de travail.

Protégez vos comptes d’administrateur avec l’authentification multifacteur et l’accès conditionnel. Pour plus d’informations, consultez [Protection des comptes d’administrateur](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Ensuite, configurez Microsoft Purview Privileged Access Management. La gestion des accès privilégiés permet de contrôler l’accès de manière granulaire sur les tâches d’administration privilégiée dans Office 365. Il peut aider à protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administrateur privilégiés existants avec un accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques.

- [Vue d’ensemble de la gestion des accès privilégiés](privileged-access-management.md)
- [Configurer la gestion des accès privilégiés](privileged-access-management-configuration.md)

Une autre recommandation principale consiste à utiliser des stations de travail spécialement configurées pour le travail administratif. Il s’agit d’appareils dédiés qui sont utilisés uniquement pour les tâches administratives. Consultez [Sécurisation de l’accès privilégié](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Enfin, vous pouvez atténuer l’impact d’un manque d’accès administratif par inadvertance en créant au moins deux comptes d’accès d’urgence dans votre locataire. Consultez [Gérer les comptes d’accès d’urgence dans Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Étape 3 : Configurer les stratégies d’accès aux identités et aux appareils recommandées

L’authentification multifacteur (MFA) et les stratégies d’accès conditionnel sont des outils puissants pour atténuer les comptes compromis et l’accès non autorisé. Nous vous recommandons d’implémenter un ensemble de stratégies qui ont été testées ensemble. Pour plus d’informations, notamment les étapes de déploiement, consultez [Les configurations d’identité et d’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md).

 Ces stratégies implémentent les fonctionnalités suivantes :

- Authentification multifacteur
- Accès conditionnel
- protection des applications Intune (protection des applications et des données pour les appareils)
- Conformité des appareils Intune
- Azure AD Identity Protection

L’implémentation Intune conformité des appareils nécessite l’inscription des appareils. La gestion des appareils vous permet de vous assurer qu’ils sont intègres et conformes avant de leur permettre d’accéder aux ressources de votre environnement. Voir [Inscrire des appareils pour la gestion dans Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Étape 4 : Configurer les stratégies d’accès aux appareils SharePoint

Microsoft vous recommande de protéger le contenu des sites SharePoint avec du contenu sensible et hautement réglementé avec des contrôles d’accès aux appareils. Pour plus d’informations, consultez [les recommandations de stratégie pour la sécurisation des sites et fichiers SharePoint](../security/office-365-security/sharepoint-file-access-policies.md).
