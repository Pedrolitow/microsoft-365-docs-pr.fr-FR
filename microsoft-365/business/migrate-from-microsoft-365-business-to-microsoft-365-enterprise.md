---
title: Migration de Microsoft 365 Entreprise vers Microsoft 365 E3
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 5b4ba843-24b8-4526-8e1f-f9b9eab89d06
description: Découvrez comment faire passer votre entreprise de Microsoft 365 Business Premium entreprise à Microsoft 365 E3.
ms.openlocfilehash: 10630671f3deb7eff0ad0f601d301b90743ee35f
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51164510"
---
# <a name="migrate-from-microsoft-365-business-premium-to-microsoft-365-e3"></a>Migration de Microsoft 365 Business Premium vers Microsoft 365 E3

Microsoft 365 Business Premium dispose de tout ce dont vous avez besoin pour votre petite entreprise, en combinant les applications de productivité basées sur le cloud les plus classes avec une gestion et une sécurité d’appareils simples qui permettent à vos employés d’améliorer leur travail. Dans certains cas, toutefois, vous devrez peut-être migrer votre abonnement Microsoft 365 Business Premium vers Microsoft 365 E3. 

Par exemple, votre entreprise a évolué et a besoin de plus de 300 licences (félicitations, par ailleurs).

Ou, votre entreprise a besoin de fonctionnalités d’entreprise, telles que Applications Microsoft 365 pour les grandes entreprises, Windows 10 Entreprise E3 ou Enterprise licences d’accès au client (CAL).

La mise à niveau est simple : vous pouvez commencer la mise à [niveau à partir du Centre d’administration.](../commerce/subscriptions/upgrade-to-different-plan.md) Toutes vos données et configuration dans votre abonnement actuel sont conservées. Vous n’avez rien à faire pour préparer la migration et rien à faire par la suite, sauf tirer parti des nouvelles fonctionnalités.

>[!Note]
>Vous pouvez également utiliser un abonnement Microsoft 365 Business Premium jusqu’à 300 licences et obtenir un abonnement Microsoft 365 E3 pour plus de 300 sièges. Toutefois, Microsoft Defender pour Office 365 n’est pas inclus dans Microsoft 365 E3. Pour une protection continue contre les menaces, vous devez ajouter des licences Defender pour Office 365 supplémentaires afin que tous les utilisateurs dans l’étendue de votre police Defender pour Office 365 soient titulaires d’une licence.
>

## <a name="differences-between-microsoft-365-business-premium-and-microsoft-365-enterprise"></a>Différences entre Microsoft 365 Business Premium et Microsoft 365 Entreprise

Ce tableau présente les différences entre Microsoft 365 Business Premium et Microsoft 365 E3.

| Fonctionnalité    | Prise en charge dans Microsoft 365 Business Premium    | Prise en charge dans Microsoft 365 E3 | 
|:-------|:-----|:-----|
| **Sur site**        | | | 
| Windows 10    | Windows 10 Business  |     Windows 10 Entreprise E3| 
| Office applications*    | [Applications Microsoft 365 pour les entreprises](#office-365-business)    | Applications Microsoft 365 for entreprise | 
| **Applications de productivité cloud**        | | | 
| Exchange Online et Outlook    | Limite de stockage de 50 Go par boîte aux lettres et archivage Exchange Online illimité    | Limite de stockage de 100 Go par boîte aux lettres et archivage Exchange Online illimité | 
| Teams    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| OneDrive Entreprise    | Limite de stockage de 1 To par utilisateur    | Illimité | 
| Yammer, SharePoint Online, Planner, Stream    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Protection contre les menaces**        | | | 
| Fonctionnalités de réduction de la surface d’attaque    | [Voir cette liste](#threat-protection) | Enterprise gestion de l’isolation matérielle pour les Microsoft Edge | 
| Microsoft Defender pour Office 365 Plan 1 | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | Non inclus, mais peut être ajouté sur | 
| **Gestion des identités**        | | | 
| Réinitialisation du mot de passe en libre-service pour les comptes Azure Active Directory hybrides (Azure AD), authentification multifacteur Azure AD (MFA), accès conditionnel, écriture écriture par mot de passe pour les identités locales|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Découverte d’applications cloud, Azure AD Connecter santé    |     | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Azure AD Office 365 applications mono-Sign-On (SSO) : 10 applications par utilisateur (applications SaaS de galerie telles que Salesforce)* | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Azure AD Premium 1 SSO : aucune limite (applications locales via le proxy d’application Azure AD et les applications non galerie à l’aide de modèles d’intégration Self-Service applications)    |     | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Données de gestion des appareils et des applications**        | | | 
| Microsoft Intune, Windows Autopilot|     ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
|Virtual Desktop Access (VDA)    |  |     ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
|Windows Virtual Desktop (WVD)    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png) |     ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
|Activation d’ordinateurs partagés (SCA)    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png) |     ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Package d’optimisation du bureau Microsoft    | |     ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Protection des informations**        | | | 
| Office 365 Protection contre la perte de données, Azure Information Protection Plan 1    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Protection des informations de fenêtre pour le point de terminaison DLP    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Licence d’accès client (droits cal)**    | | |     
| Enterprise CAL Suite (Exchange, SharePoint, Skype, Windows, Microsoft Endpoint Configuration Manager, Windows Rights Management)| |         ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Conformité**        | | | 
| Archivage illimité du courrier électronique    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Gestionnaire de conformité    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| eDiscovery    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| In-place hold and litigation hold    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Gestion des enregistrements de messagerie, balises de rétention et stratégies de rétention    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
||||

\* Les utilisateurs qui se sont vus attribuer l’accès aux applications SaaS peuvent accéder à 10 applications au plus. Les administrateurs peuvent configurer l' utilisateur unique et modifier l’accès des utilisateurs à différentes applications SaaS, mais l’accès à l' utilisateur unique n’est autorisé que pour 10 applications par utilisateur à la fois. Toutes Office 365 applications sont comptabilisées comme une seule application.

## <a name="migration"></a>Migration

Pour migrer, travaillez avec votre partenaire pour déplacer votre abonnement Microsoft 365 Business Premium et vos licences vers un abonnement Microsoft 365 E3 avec ses licences.

Les sections suivantes décrivent les modifications que vous devez apporter, le cas nécessaire, et ce que vous pouvez faire après la migration.

### <a name="microsoft-365-subscription-configuration-and-data"></a>Microsoft 365 de configuration et de données d’abonnement

Vous n’avez pas besoin d’apporter des modifications à votre abonnement ou données actuels avant la migration, notamment :

- Configuration de l’abonnement, telle que les noms de domaine DNS.
- Comptes d’utilisateur et de groupe et paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Configurations du service de productivité et leurs données, telles que les Teams, les boîtes aux lettres Exchange Online, les sites SharePoint Online, les dossiers OneDrive Entreprise et les blocs-OneNote portables.

Vos utilisateurs peuvent désormais bénéficier d’un espace de stockage illimité dans Exchange Online boîtes aux lettres et OneDrive Entreprise dossiers.

Vous pouvez commencer à utiliser la découverte d’applications cloud, Azure AD Connecter Health et l' sso pour plus de 10 applications.

<a name="threat-protection"></a>
### <a name="threat-protection"></a>Protection contre les menaces

Windows 10 Business comprend les protections ci-après :

- Application de l’intégrité du processus de démarrage du système d’exploitation
- Application de l’intégrité des composants d’exploitation sensibles
- Vulnérabilité avancée et atténuations des attaques zero-day
- Protection réseau basée sur la réputation pour Microsoft Edge, Internet Explorer et Chrome
- Pare-feu basé sur l’hôte
- Atténuations des ransomware
- Isolation matérielle pour les Microsoft Edge
- Contrôle d’application optimisé par l’intelligent Security Graph
- Contrôle d’appareil (USB)
- Protection réseau contre les menaces basées sur le web
- Règles de prévention des intrusions hôtes

Windows 10 Entreprise E3 inclut également la gestion d’entreprise de l’isolation matérielle pour Microsoft Edge.

>[!Note]
>Les utilisateurs migrés vers Microsoft 365 E3 nécessiteront chacun une licence Microsoft Defender Office 365 pour une protection continue contre les menaces. N’oubliez pas d’acheter des licences Defender supplémentaires pour Office 365 de sorte que tous les utilisateurs dans l’étendue de votre defender pour Office 365 polices soient titulaires d’une licence. 
>

### <a name="device-management-with-intune"></a>Gestion des appareils avec Intune

Vous n’avez pas besoin d’apporter des modifications à votre configuration Intune actuelle avant la migration, ce qui inclut les appareils inscrits, ainsi que les paramètres des appareils et des applications.

### <a name="windows-10"></a>Windows 10

Microsoft 365 Business Premium inclut Windows 10 Business, que vous pouvez installer avec Windows AutoPilot. Lorsque vous migrez vers Microsoft 365 E3, chaque licence utilisateur inclut Windows 10 Entreprise E3, que vous pouvez également installer avec Windows Autopilot.

<a name="office-365-business"></a>
###  <a name="microsoft-365-apps-for-business"></a>Applications Microsoft 365 pour les entreprises

Votre client Applications Microsoft 365 pour les PME installé sur vos appareils commence automatiquement à utiliser les fonctionnalités de Applications Microsoft 365 pour les grandes entreprises. Après la migration, vous pouvez désormais utiliser :

 - Prise en charge des stratégies de groupe
 - Comparer et interroger une feuille de calcul
 - Aide à la décision

