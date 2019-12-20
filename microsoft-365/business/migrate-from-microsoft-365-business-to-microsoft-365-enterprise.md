---
title: Migrer de Microsoft 365 Business vers Microsoft 365 E3
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
search.appverid:
- BCS160
- MET150
ms.assetid: 5b4ba843-24b8-4526-8e1f-f9b9eab89d06
description: Découvrez comment déplacer votre entreprise de Microsoft 365 Business vers Microsoft 365 E3.
ms.openlocfilehash: dc715bbf4cef8a742a28a6452e83b6e8d2f7cdd8
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40805617"
---
# <a name="migrate-from-microsoft-365-business-to-microsoft-365-e3"></a>Migrer de Microsoft 365 Business vers Microsoft 365 E3

Microsoft 365 Business offre tout ce dont vous avez besoin pour votre petite entreprise, en combinant les meilleures applications de productivité en nuage avec une simple gestion des périphériques et une sécurité qui permet à vos employés d’effectuer leurs meilleures tâches. Toutefois, dans certains cas, il se peut que vous deviez migrer votre abonnement Microsoft 365 Business vers Microsoft 365 E3. 

Par exemple, votre entreprise a grandi et a besoin de plus de 300 licences (félicitations).

Votre entreprise a besoin de fonctionnalités d’entreprise, telles que Office 365 ProPlus, Windows 10 entreprise E3 ou des licences d’accès client (CAL) entreprise.

La mise à niveau est facile : vous pouvez démarrer la mise à niveau [à partir du centre d’administration](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/upgrade-to-different-plan?view=o365-worldwide). Toutes les données et la configuration de votre abonnement actuel sont conservées. Il n’y a rien à faire pour vous préparer à la migration et rien à faire par la suite, sauf tirer parti des nouvelles fonctionnalités. 

>[!Note]
>Vous pouvez également utiliser un abonnement Microsoft 365 Business pour un maximum de 300 postes et obtenir un abonnement Microsoft 365 E3 pour plus de 300 places. Toutefois, Office 365 ATP n’est pas inclus dans Microsoft 365 E3. Pour une protection permanente contre les menaces, vous devez ajouter des licences Office 365 ATP supplémentaires afin que tous les utilisateurs de votre police Office 365 ATP soient titulaires d’une licence.
>

## <a name="differences-between-microsoft-365-business-and-microsoft-365-enterprise"></a>Différences entre Microsoft 365 entreprise et Microsoft 365 entreprise

Ce tableau présente les différences entre Microsoft 365 entreprise et Microsoft 365 E3.

| Fonctionnalité   | Prise en charge dans Microsoft 365 Business | Prise en charge dans Microsoft 365 E3 | 
|:-------|:-----|:-----|
| **En local**       | | | 
| Windows 10    | Windows 10 Business  |    Windows 10 entreprise E3| 
| Applications Office *  | [Office 365 Business](#office-365-business)   | Office 365 ProPlus | 
| **Applications de productivité sur le Cloud**       | | | 
| Exchange Online et Outlook   | limite de stockage de 50 Go par boîte aux lettres et archivage Exchange Online illimité   | limite de stockage de 100 Go par boîte aux lettres et archivage Exchange Online illimité | 
| Teams | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| OneDrive Entreprise | limite de stockage de 1 to par utilisateur   | Illimité | 
| Yammer, SharePoint Online, planificateur, flux    | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| StaffHub  | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Gestionnaire de clients Outlook, MileIQ  | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | | 
| **Protection contre les menaces**     | | | 
| Fonctionnalités de réduction de la surface d’attaque | [Voir la liste suivante](#threat-protection) | Gestion d’entreprise de l’isolation matérielle pour Microsoft Edge | 
| Office 365 Advanced Threat Protection (ATP) plan 1 | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)  | Non inclus, mais peut être ajouté sur | 
| **Gestion des identités**       | | | 
| Réinitialisation du mot de passe en libre-service pour les comptes hybrides Azure Active Directory (Azure AD), Azure Multi-Factor Authentication (MFA), l’accès conditionnel, l’écriture différée de mot de passe pour les identités locales|    ![Inclus avec Microsoft 365 Business](./media/check-mark.png) | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Découverte des applications Cloud, Azure AD Connect Health  |   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Authentification unique (SSO) pour les applications Azure AD Office 365 (SSO) : 10 applications par utilisateur (Galerie applications SaaS telles que Salesforce) * | ![Inclus avec Microsoft 365 Business](./media/check-mark.png) | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Azure AD Premium 1 SSO : pas de limite (applications locales via un proxy d’application Azure AD et applications non-Galerie utilisant des modèles d’intégration d’applications en libre-service)  |   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| **Gestion des appareils et des applications**     | | | 
| Microsoft Intune, Windows AutoPilot|  ![Inclus avec Microsoft 365 Business](./media/check-mark.png) | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
|Accès au bureau virtuel (VDA)   |  |    ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
|Bureau virtuel Windows (WVD)  | ![Inclus avec Microsoft 365 Business](./media/check-mark.png) |     ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
|Activation d’ordinateurs partagés (SCA)   | ![Inclus avec Microsoft 365 Business](./media/check-mark.png) |     ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Package d’optimisation du bureau Microsoft    | |     ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| **Protection des informations**        | | | 
| Office 365 protection contre la perte de données, plan Azure information protection 1  | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Protection des informations de fenêtre pour le point de terminaison DLP    | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| **Licence d’accès client (CAL)**    | | |   
| Suite CAL Enterprise (Exchange, SharePoint, Skype, Windows, System Center Configuration Manager, gestion des droits Windows)| |        ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| **Conformité**        | | | 
| Archivage de courrier électronique illimité | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Gestionnaire de conformité    | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| eDiscovery    | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Conservation inaltérable et conservation pour litige | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
| Gestion des enregistrements de messagerie, balises de rétention et stratégies de rétention  | ![Inclus avec Microsoft 365 Business](./media/check-mark.png)   | ![Inclus avec Microsoft 365 E3](./media/check-mark.png) | 
||||

\*Les utilisateurs auxquels un accès aux applications SaaS a été attribué peuvent obtenir un accès SSO à 10 applications. Les administrateurs peuvent configurer l’authentification unique et modifier l’accès utilisateur à différentes applications SaaS, mais l’accès SSO est uniquement autorisé pour 10 applications par utilisateur à la fois. Toutes les applications Office 365 sont comptées comme une seule application.

## <a name="migration"></a>Migration

Pour migrer, collaborez avec votre partenaire pour déplacer votre abonnement et vos licences Microsoft 365 Business vers un abonnement Microsoft 365 E3 approprié avec ses licences.

Les sections suivantes décrivent les modifications que vous devez effectuer, le cas échéant, et ce que vous pouvez faire après la migration.

### <a name="microsoft-365-subscription-configuration-and-data"></a>Données et configuration de l’abonnement Microsoft 365

Vous n’avez pas besoin de modifier votre abonnement ou vos données actuelles avant la migration, ce qui inclut :

- La configuration des abonnements, tels que les noms de domaine DNS.
- Les comptes d’utilisateur et de groupe et les paramètres d’authentification, tels que l’authentification multifacteur ou les stratégies d’accès conditionnel.
- Les configurations de service de productivité et leurs données, telles que les équipes, les boîtes aux lettres Exchange Online, les sites SharePoint Online, les dossiers OneDrive entreprise et les blocs-notes OneNote.

Vos utilisateurs peuvent désormais bénéficier d’un stockage illimité dans les boîtes aux lettres Exchange Online et dans les dossiers OneDrive entreprise.

Vous pouvez commencer à utiliser la découverte d’applications Cloud, Azure AD Connect Health et l’authentification unique (SSO) pour plus de 10 applications.

>[!Note]
>Les utilisateurs migrés vers Microsoft 365 E3 ne peuvent plus utiliser le gestionnaire de clients Outlook ni MileIQ.
>

<a name="threat-protection"></a>
### <a name="threat-protection"></a>Protection contre les menaces

Windows 10 Business inclut les protections suivantes :

- Mise en œuvre de l’intégrité du processus de démarrage du système d’exploitation
- Application d’intégrité des composants d’exploitation sensibles
- Atténuation des vulnérabilités et des exploits « Zero-Day »
- Protection du réseau basé sur la réputation pour Microsoft Edge, Internet Explorer et chrome
- Pare-feu basé sur l’hôte
- Atténuations de ransomware
- Isolation matérielle pour Microsoft Edge
- Contrôle d’application alimenté par le graphique de sécurité intelligent
- Pilotage de matériel (USB)
- Protection réseau pour les menaces basées sur le Web
- Règles Host Intrusion Prevention

Windows 10 entreprise E3 inclut également la gestion de l’isolation matérielle pour Microsoft Edge.

>[!Note]
>Les utilisateurs migrés vers Microsoft 365 E3 auront chacun une licence Office 365 ATP pour la protection continue contre les menaces. N’oubliez pas d’acheter des licences Office 365 ATP supplémentaires afin que tous les utilisateurs de l’étendue de vos stratégies de protection avancée contre les menaces Office 365 soient titulaires d’une licence. 
>

### <a name="device-management-with-intune"></a>Gestion des appareils avec Intune

Vous n’avez pas besoin d’effectuer des modifications dans votre configuration Intune actuelle avant de procéder à la migration, ce qui inclut les périphériques et les paramètres d’application et d’appareil.

### <a name="windows-10"></a>Windows 10

Microsoft 365 Business comprend Windows 10 Business, que vous pouvez installer avec Windows AutoPilot. Lorsque vous migrez vers Microsoft 365 E3, chaque licence utilisateur comprend Windows 10 entreprise E3, que vous pouvez également installer avec Windows AutoPilot.

<a name="office-365-business"></a>
### <a name="office-365-business"></a>Office 365 Business

Votre client Office 365 Business installé sur vos appareils commencera automatiquement à utiliser les fonctionnalités d’Office 365 ProPlus. Après la migration, vous pouvez désormais utiliser les éléments suivants :

 - Activation en volume via la stratégie de groupe
 - Télémétrie d’application
 - Mettre à jour les contrôles
 - Comparaison et recherche dans une feuille de calcul
 - Aide à la décision

