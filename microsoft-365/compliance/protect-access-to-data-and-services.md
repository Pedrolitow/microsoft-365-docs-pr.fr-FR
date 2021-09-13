---
title: Protéger l’accès aux appareils et l’accès des utilisateurs
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Découvrez comment protéger l’accès des utilisateurs et des appareils aux Microsoft 365 et aux services et se défendre contre la perte de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: bd8bbb62bc87ff59594e2fb2a3e21311c2452d9f
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209390"
---
# <a name="protect-user-and-device-access"></a>Protéger l’accès aux appareils et l’accès des utilisateurs

La protection de l’accès Microsoft 365 données et services de votre entreprise est essentielle pour la protection contre les cyberattaques et la protection contre la perte de données. Les mêmes protections peuvent être appliquées à d’autres applications SaaS dans votre environnement et même aux applications sur site publiées avec Azure Active Directory proxy d’application.
  
## <a name="step-1-review-recommendations"></a>Étape 1 : Examiner les recommandations

Découvrez les fonctionnalités recommandées relatives à la protection des identités et des appareils qui accèdent à Office 365, aux autres services SaaS et applications locales publiées avec le proxy d’application Azure AD.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) | [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) | [Plus de langues](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Étape 2 : Protéger les comptes d’administrateur et l’accès
Les comptes d’administration que vous utilisez pour administrer Microsoft 365 environnement de gestion incluent des privilèges élevés. Ce sont des cibles précieuses pour les pirates informatiques et les cyberattaques. 

Commencez par utiliser des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent avoir un compte d’utilisateur distinct pour une utilisation normale et non administrative et utiliser leur compte administratif uniquement si nécessaire pour effectuer une tâche associée à leur fonction.

Protégez vos comptes d’administrateur avec l’authentification multifacteur et l’accès conditionnel. Pour plus d’informations, [voir Protection des comptes d’administrateur.](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts) 

Ensuite, configurez la gestion des accès privilégiés dans Office 365. La gestion des accès privilégiés permet de contrôler l’accès de manière granulaire sur les tâches d’administration privilégiée dans Office 365. Il peut aider à protéger votre organisation contre les violations qui peuvent utiliser des comptes d’administrateur privilégiés existants avec un accès permanent aux données sensibles ou à des paramètres de configuration critiques.

- [Vue d’ensemble de la gestion des accès privilégiés](privileged-access-management-overview.md)
- [Configurer la gestion des accès privilégiés](privileged-access-management-configuration.md)

Une autre recommandation consiste à utiliser des stations de travail spécialement configurées pour le travail administratif. Il s’agit d’appareils dédiés qui sont utilisés uniquement pour les tâches administratives. Voir [Sécurisation de l’accès privilégié.](/windows-server/identity/securing-privileged-access/securing-privileged-access)

Enfin, vous pouvez atténuer l’impact d’un manque accidentel d’accès administratif en créant au moins deux comptes d’accès d’urgence dans votre client. Voir [Gérer les comptes d’accès d’urgence dans Azure AD.](/azure/active-directory/users-groups-roles/directory-emergency-access) 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Étape 3 : Configurer les stratégies recommandées d’accès aux identités et aux appareils
L’authentification multifacteur (MFA) et les stratégies d’accès conditionnel sont des outils puissants pour atténuer les comptes compromis et l’accès non autorisé. Nous vous recommandons d’implémenter un ensemble de stratégies qui ont été testées ensemble. Pour plus d’informations, y compris sur les étapes de déploiement, voir [Configurations d’identité et d’accès aux appareils.](../security/office-365-security/microsoft-365-policies-configurations.md)

 Ces stratégies implémentent les fonctionnalités suivantes :
- Authentification multifacteur
- Accès conditionnel
- Protection des applications Intune (protection des applications et des données pour les appareils)
- Conformité des appareils Intune
- Azure AD Identity Protection

L’implémentation de la conformité des appareils Intune nécessite l’inscription de l’appareil. La gestion des appareils vous permet de vous assurer qu’ils sont sains et conformes avant de leur permettre d’accéder aux ressources de votre environnement. Voir [Inscrire des appareils pour la gestion dans Intune](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Étape 4 : Configurer les stratégies SharePoint’accès aux appareils

Microsoft vous recommande de protéger le contenu des sites SharePoint avec du contenu sensible et hautement réglementé avec des contrôles d’accès aux appareils. Pour plus d’informations, voir [recommandations de stratégie pour la sécurisation SharePoint sites et fichiers.](../security/office-365-security/sharepoint-file-access-policies.md)



