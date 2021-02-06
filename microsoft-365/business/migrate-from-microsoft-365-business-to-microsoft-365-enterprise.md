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
description: Découvrez comment déplacer votre entreprise de Microsoft 365 Business Premium vers Microsoft 365 E3.
ms.openlocfilehash: 019a422bb879389f42a32cf30f9a8094f776078a
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126198"
---
# <a name="migrate-from-microsoft-365-business-premium-to-microsoft-365-e3"></a>Migration de Microsoft 365 Business Premium vers Microsoft 365 E3

Microsoft 365 Business Premium offre tout ce dont vous avez besoin pour votre petite entreprise, en combinant les applications de productivité basées sur le cloud les plus classes avec une gestion et une sécurité d’appareils simples qui permettent à vos employés d’améliorer leur travail. Dans certains cas, toutefois, vous devrez peut-être migrer votre abonnement Microsoft 365 Business Premium vers Microsoft 365 E3. 

Par exemple, votre entreprise a évolué et a besoin de plus de 300 licences (félicitations, par ailleurs).

Ou, votre entreprise a besoin de fonctionnalités d’entreprise, telles que les applications Microsoft 365 pour les entreprises, Windows 10 Entreprise E3 ou les licences d’accès au client d’entreprise.

La mise à niveau est simple : vous pouvez commencer la mise à [niveau à partir du Centre d’administration.](../commerce/subscriptions/upgrade-to-different-plan.md) Toutes vos données et configuration dans votre abonnement actuel sont conservées. Vous n’avez rien à faire pour préparer la migration et rien à faire par la suite, sauf tirer parti des nouvelles fonctionnalités.

>[!Note]
>Vous pouvez également utiliser un abonnement Microsoft 365 Business Premium pour 300 licences au plus et obtenir un abonnement Microsoft 365 E3 pour plus de 300 sièges. Toutefois, Microsoft Defender pour Office 365 n’est pas inclus dans Microsoft 365 E3. Pour une protection continue contre les menaces, vous devez ajouter des licences Defender supplémentaires pour Office 365 afin que tous les utilisateurs dans l’étendue de vos polices Defender pour Office 365 soient titulaires d’une licence.
>

## <a name="differences-between-microsoft-365-business-premium-and-microsoft-365-enterprise"></a>Différences entre Microsoft 365 Business Premium et Microsoft 365 Entreprise

Ce tableau présente les différences entre Microsoft 365 Business Premium et Microsoft 365 E3.

| Fonctionnalité    | Prise en charge dans Microsoft 365 Business Premium    | Prise en charge dans Microsoft 365 E3 | 
|:-------|:-----|:-----|
| **Sur site**        | | | 
| Windows 10    | Windows 10 Business  |     Windows 10 Entreprise E3| 
| Applications Office*    | [Applications Microsoft 365 pour les entreprises](#office-365-business)    | Applications Microsoft 365 for entreprise | 
| **Applications de productivité cloud**        | | | 
| Exchange Online et Outlook    | Limite de stockage de 50 Go par boîte aux lettres et archivage Exchange Online illimité    | Limite de stockage de 100 Go par boîte aux lettres et archivage Exchange Online illimité | 
| Teams    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| OneDrive Entreprise    | Limite de stockage de 1 To par utilisateur    | Illimité | 
| Yammer, SharePoint Online, Planificateur, Stream    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| MileIQ    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | | 
| **Protection contre les menaces**        | | | 
| Fonctionnalités de réduction de la surface d’attaque    | [Voir cette liste](#threat-protection) | Gestion d’entreprise de l’isolation matérielle pour Microsoft Edge | 
| Defender pour Office 365 Plan 1 | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | Non inclus, mais peut être ajouté sur | 
| **Gestion des identités**        | | | 
| Réinitialisation du mot de passe en libre-service pour les comptes Azure Active Directory (Azure AD) hybrides, authentification multifacteur Azure AD (MFA), accès conditionnel, écriture d’écriture de mot de passe pour les identités locales|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| Découverte d’applications cloud, Azure AD Connect Health    |     | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| Applications Azure AD Office 365 single Sign-On (SSO) : 10 applications par utilisateur (applications SaaS de galerie telles que Salesforce)* | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| SSO Azure AD Premium 1 : aucune limite (applications locales via le proxy d’application Azure AD et les applications non galerie à l’aide de modèles d’intégration Self-Service application)    |     | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| **Données de gestion des appareils et des applications**        | | | 
| Microsoft Intune, Windows Autopilot|     ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
|Virtual Desktop Access (VDA)    |  |     ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
|Windows Virtual Desktop (WVD)    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png) |     ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
|Activation d’ordinateurs partagés (SCA)    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png) |     ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Package d’optimisation du bureau Microsoft    | |     ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| **Protection des informations**        | | | 
| Protection contre la perte de données Office 365, Azure Information Protection Plan 1    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| Protection des informations de fenêtre pour le point de terminaison DLP    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Licence d’accès client (droits cal)**    | | |     
| Enterprise CAL Suite (Exchange, SharePoint, Skype, Windows, Microsoft Endpoint Configuration Manager, Windows Rights Management)| |         ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| **Conformité**        | | | 
| Archivage illimité du courrier électronique    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| Gestionnaire de conformité    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| eDiscovery    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
| In-place hold and litigation hold    | ![Inclus dans Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus avec Microsoft 365 E3](../media/check-mark.png) | 
| Gestion des enregistrements de messagerie, balises de rétention et stratégies de rétention    | ![Inclus avec Microsoft 365 Business Premium](../media/check-mark.png)    | ![Inclus dans Microsoft 365 E3](../media/check-mark.png) | 
||||

\* Les utilisateurs qui se sont vus attribuer l’accès aux applications SaaS peuvent accéder à 10 applications au plus. Les administrateurs peuvent configurer l' utilisateur unique et modifier l’accès des utilisateurs à différentes applications SaaS, mais l’accès à l' utilisateur unique n’est autorisé que pour 10 applications par utilisateur à la fois. Toutes les applications Office 365 sont comptabilisées comme une seule application.

## <a name="migration"></a>Migration

Pour migrer, travaillez avec votre partenaire pour déplacer votre abonnement et vos licences Microsoft 365 Business Premium vers un abonnement Microsoft 365 E3 approprié avec ses licences.

Les sections suivantes décrivent les modifications que vous devez apporter, le cas nécessaire, et ce que vous pouvez faire après la migration.

### <a name="microsoft-365-subscription-configuration-and-data"></a>Configuration et données de l’abonnement Microsoft 365

Vous n’avez pas besoin d’apporter des modifications à votre abonnement ou données actuels avant la migration, notamment :

- Configuration de l’abonnement, telle que les noms de domaine DNS.
- Comptes d’utilisateur et de groupe et paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Configurations du service de productivité et leurs données, telles que Teams, boîtes aux lettres Exchange Online, sites SharePoint Online, dossiers OneDrive Entreprise et blocs-notes OneNote.

Vos utilisateurs peuvent désormais bénéficier d’un espace de stockage illimité dans les boîtes aux lettres Exchange Online et les dossiers OneDrive Entreprise.

Vous pouvez commencer à utiliser la découverte d’applications cloud, Azure AD Connect Health et l' sso pour plus de 10 applications.

>[!Note]
>Les utilisateurs migrés vers Microsoft 365 E3 ne peuvent plus utiliser MileIQ.
>

<a name="threat-protection"></a>
### <a name="threat-protection"></a>Protection contre les menaces

Windows 10 Business inclut les protections ci-après :

- Application de l’intégrité du processus de démarrage du système d’exploitation
- Application de l’intégrité des composants d’exploitation sensibles
- Vulnérabilité avancée et atténuations des attaques zero-day
- Protection réseau basée sur la réputation pour Microsoft Edge, Internet Explorer et Chrome
- Pare-feu basé sur l’hôte
- Atténuations des ransomware
- Isolation matérielle pour Microsoft Edge
- Contrôle d’application optimisé par Intelligent Security Graph
- Contrôle d’appareil (USB)
- Protection réseau contre les menaces basées sur le web
- Règles de prévention des intrusions hôtes

Windows 10 Entreprise E3 inclut également la gestion d’entreprise de l’isolation matérielle pour Microsoft Edge.

>[!Note]
>Les utilisateurs migrés vers Microsoft 365 E3 auront chacun besoin d’une licence Microsoft Defender pour Office 365 pour assurer une protection continue contre les menaces. N’oubliez pas d’acheter des licences Defender supplémentaires pour Office 365 afin que tous les utilisateurs dans l’étendue de vos polices Defender pour Office 365 soient titulaires d’une licence. 
>

### <a name="device-management-with-intune"></a>Gestion des appareils avec Intune

Vous n’avez pas besoin d’apporter de modifications à votre configuration Intune actuelle avant la migration, ce qui inclut les appareils inscrits, ainsi que les paramètres des appareils et applications.

### <a name="windows-10"></a>Windows 10

Microsoft 365 Business Premium inclut Windows 10 Business, que vous pouvez installer avec Windows AutoPilot. Lorsque vous migrez vers Microsoft 365 E3, chaque licence utilisateur inclut Windows 10 Entreprise E3, que vous pouvez également installer avec Windows Autopilot.

<a name="office-365-business"></a>
###  <a name="microsoft-365-apps-for-business"></a>Applications Microsoft 365 pour les entreprises

Votre client Microsoft 365 Apps for business installé sur vos appareils commencera automatiquement à utiliser les fonctionnalités de Microsoft 365 Apps for enterprise. Après la migration, vous pouvez désormais utiliser :

 - Prise en charge des stratégies de groupe
 - Comparer et interroger une feuille de calcul
 - Aide à la décision

