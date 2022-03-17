---
title: Configurer Microsoft 365 Business Premium
description: Découvrez comment configurer Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.service: o365-administration
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 5b6f187f93e8a135bfb67c78509553d2963b011b
ms.sourcegitcommit: b67385243fb56ad20f2a6f1c40be46f5691c1c2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63527813"
---
# <a name="set-up-microsoft-365-business-premium"></a>Configurer Microsoft 365 Business Premium

Plusieurs options s’offrent à vous pour configurer et configurer Microsoft 365 Business Premium. Vous pouvez :

- [Utiliser une expérience d’installation guidée pour l’installation et la configuration de base](#guided-process-for-basic-setup)
- [Travailler avec un partenaire, tel qu’un Fournisseur de solutions Microsoft Cloud (CSP)](#work-with-a-microsoft-partner)
- [Travailler manuellement dans le processus d’installation](#manual-setup-and-configuration)


Utilisez cet article comme guide.

## <a name="guided-process-for-basic-setup"></a>Processus guidé pour la configuration de base

Microsoft 365 Business Premium inclut un processus guidé pour la configuration de base. Les tâches incluent la connexion à un domaine personnalisé, l’ajout d’utilisateurs, l’attribution de licences, l’installation de Outlook sur des appareils mobiles, la révision des paramètres de protection des données et l’application d’une stratégie de protection des applications mobiles. 

Pour voir comment fonctionne la configuration guidée, regardez la vidéo suivante : <br/><br/>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

Une fois que vous avez terminé la configuration guidée, vous devez suivre des étapes supplémentaires pour vous assurer que vos fonctionnalités de sécurité et de conformité sont correctement configurées et appliquées. Ces étapes incluent notamment :

- [Sécurisation Windows appareils](m365bp-secure-windows-devices.md)
- [Déploiement d’Microsoft 365 applications](../admin/setup/install-applications.md)
- [Configuration et configuration de vos nouvelles fonctionnalités de Defender entreprise](../security/defender-business/mdb-setup-configuration.md)

[En savoir plus sur les différences entre le processus d’installation guidé et la page d’installation](../admin/setup/o365-setup-wizard-and-setup-page.md).

> [!TIP]
> Pour plus d’informations sur la configuration et la configuration des Microsoft 365 Business Premium, voir la section suivante.


## <a name="work-with-a-microsoft-partner"></a>Travailler avec un partenaire Microsoft

Microsoft dispose d’une liste de fournisseurs de solutions autorisés à vendre des offres, y compris Microsoft 365 Business Premium. 

Pour trouver un fournisseur de solutions dans votre région, prenez les mesures suivantes :

1. Go to the **Microsoft Solution Providers** page ([https://www.microsoft.com/solution-providers](https://www.microsoft.com/solution-providers)).
 
2. Dans la zone de recherche, remplissez l’emplacement et la taille de votre entreprise. 

3. Dans la **zone Rechercher des produits, services, compétences, secteurs** , `Microsoft 365`placez, puis sélectionnez **Go**.

4. Examinez la liste des résultats. Sélectionnez un fournisseur pour en savoir plus sur son expertise et les services qu’il fournit.

Voir également [Rechercher votre partenaire ou revendeur](../admin/manage/find-your-partner-or-reseller.md).

## <a name="manual-setup-and-configuration"></a>Configuration et configuration manuelles

Si vous préférez effectuer manuellement votre processus d’installation et de configuration, utilisez le tableau suivant comme guide :

| Phase  | Tâche  | Ressources pour en savoir plus  |
|---------|---------|---------|
| **Planification**     | Planifier votre processus d’installation et de configuration  | [Planifier votre installation de Microsoft 365 pour les entreprises](../admin/setup/plan-your-setup.md)   |
|  | Consultez la configuration requise | [Microsoft 365 Business Premium requise](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:overviewtab) |
| **Configuration de base**     | Utiliser un domaine personnalisé comme avec `rob@contoso.com` Microsoft 365 | [Ajouter un domaine à Microsoft 365](../admin/setup/add-domain.md) |
|      | Ajouter des utilisateurs et attribuer des licences dans Microsoft 365      | [Ajouter des utilisateurs et attribuer des licences simultanément](../admin/add-users/add-users.md)        |
|  | Attribuez des rôles d’administrateur aux utilisateurs qui effectueront certaines fonctions, telles que : <br/>- Gestion des fonctionnalités<br/>- Gestion des comptes d’utilisateurs<br/>- Gestion des appareils<br/>- Affichage ou gestion des informations de sécurité et de conformité de votre organisation | [En savoir plus sur les rôles d’administrateur](../admin/add-users/about-admin-roles.md) <br/><br/> [Attribuer des rôles administrateur](../admin/add-users/assign-admin-roles.md)  |
|  | Installer Microsoft 365 Apps (comme Word, Excel, PowerPoint, et bien plus encore) | [Installer les applications Office](../admin/setup/install-applications.md) |
| **Sécurisation de votre organisation** | Reportez-vous aux 10 premiers jours pour sécuriser votre abonnement Microsoft 365 abonnement |  [10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Exiger que tout le monde utilise une méthode de vérification supplémentaire lorsqu’il se connecte Microsoft 365 | [Configuration de l’authentification multifacteur](../admin/security-and-compliance/set-up-multi-factor-authentication.md) | 
| **Protection du courrier électronique et du contenu** |  Configurer une protection anti-hameçonnage avancée pour vous protéger contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres attaques par hameçonnage | [Protéger votre courrier électronique contre les attaques par hameçonnage](../admin/security-and-compliance/secure-your-business-data.md) |
|   | Configurer Coffre pièces jointes pour protéger votre organisation contre les pièces jointes de courrier malveillant | [Se protéger contre les pièces jointes et les fichiers malveillants Coffre pièces jointes](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Configurer des liens Coffre pour la protection contre les sites web malveillants (URL) dans les messages électroniques et Office documents | [Configurer des liens Coffre’équipe](../admin/security-and-compliance/secure-your-business-data.md) |
|  | Configurer des stratégies de protection contre la perte de données pour protéger les informations sensibles contre le partage | [Configurer les fonctionnalités de conformité](../admin/security-and-compliance/set-up-compliance.md) |
| **Gestion et protection des appareils** | Sécurisation des appareils de Windows organisation | [Sécuriser Windows appareils](m365bp-secure-windows-devices.md) <br/><br/>[Définir ou modifier les paramètres de protection des applications pour Windows 10 appareils](../admin/devices/protection-settings-for-windows-10-devices.md) |
|   | Sécuriser les Microsoft 365 sur les appareils mobiles | [Définir les paramètres de protection des applications pour les appareils Android ou iOS](../admin/devices/app-protection-settings-for-android-and-ios.md) |
|  | Configurer Microsoft Defender pour les entreprises (lorsqu’il est disponible pour votre client) | [Vue d’ensemble de Microsoft Defender pour les entreprises](../security/defender-business/mdb-overview.md)<br/><br/>[Utiliser l’Assistant pour configurer Defender pour les entreprises](../security/defender-business/mdb-use-wizard.md) |
| **Stockage de fichiers et migration de contenu** | Configurer le stockage de fichiers et le fonctionnement du partage pour votre organisation | [Configurer le partage et le stockage de fichiers dans Microsoft 365](../admin/setup/set-up-file-storage-and-sharing.md) |
| | Importer ou migrer le courrier électronique et les contacts | [Migrer le courrier électronique et les contacts vers Microsoft 365](../admin/setup/migrate-email-and-contacts-admin.md) |
|  | Déplacer les fichiers d’entreprise que tout le monde doit accéder à SharePoint (SharePoint remplace généralement l’utilisation d’un partage de fichiers ou d’un lecteur réseau) | [Déplacer des fichiers vers SharePoint](../admin/setup/files-to-sharepoint.md) |
|  | Déplacez vos fichiers de travail existants, tels que les fichiers de travail personnels ou les fichiers métiers sensibles, OneDrive | [Déplacer des fichiers vers OneDrive](../admin/setup/files-to-onedrive.md) |
| **Formation des administrateurs et de votre équipe de sécurité** | Découvrez comment utiliser le Centre d’administration | [Vue d’ensemble du centre d’administration Microsoft 365](../admin/admin-overview/admin-center-overview.md) |
|  | Utiliser la vidéothèque de formation gratuite pour Microsoft 365 administrateurs | [Vidéothèque de formation de l’administrateur](../admin/admin-video-library.yml)  |
|  | Découvrez comment utiliser le portail Microsoft 365 Defender web ([https://security.microsoft.com](https://security.microsoft.com)) | [Commencer à utiliser le portail Microsoft 365 Defender web](../security/defender-business/mdb-get-started.md) |

> [!TIP]
> Vous avez besoin d’aide ? Envisagez [d’obtenir des Aide aux PME avec Microsoft 365](https://support.microsoft.com/en-us/office/business-assist-for-microsoft-365-37deb8fe-61cc-4cf9-9ad1-1c8d93475070)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de Microsoft Defender entreprise](../security/defender-business/mdb-overview.md) (désormais inclus dans Microsoft 365 Business Premium !)

- [Documentation sur les abonnements et la facturation pour les entreprises](../commerce/index.yml)

- [Vue d’Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md) (pour les CSP Microsoft)

- [10 principales façons de sécuriser les Microsoft 365 pour les plans d’entreprise](../admin/security-and-compliance/secure-your-business-data.md)
