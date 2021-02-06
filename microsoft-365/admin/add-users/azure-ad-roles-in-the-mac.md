---
title: Rôles Azure Active Directory dans le Centre d’administration Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
description: Gérer ces rôles d’administrateur Azure dans le Centre d’administration Microsoft 365
ms.openlocfilehash: 7a4e28667bc16d6619fe87451cd48ea77d89c81d
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126104"
---
# <a name="azure-active-directory-roles-in-the-microsoft-365-admin-center"></a>Rôles Azure Active Directory dans le Centre d’administration Microsoft 365

Le Centre d’administration Microsoft 365 vous permet de gérer plus de 30 rôles Azure AD. Toutefois, ces rôles sont un sous-ensemble des rôles disponibles sur le Portail Microsoft Azure. Si vous avez une grande entreprise, certains rôles dans le Portail Azure peuvent répondre aux besoins de votre organisation. Vous recherchez des descriptions détaillées des rôles pour Azure AD ? Consultez la page [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).

Un utilisateur doté d’un rôle d’administrateur disposera du même niveau d'accès vers les services cloud auxquels votre organisation est abonnée, que vous lui ayez attribué le rôle dans le Centre d’administration Microsoft 365 ou le portail Azure, ou à l’aide du module Azure AD pour Windows PowerShell.

::: moniker range="o365-worldwide"

Dans le Centre d’administration Microsoft 365, vous pouvez accéder à **Rôles**, puis sélectionner un rôle pour ouvrir le volet Détails. Sélectionnez l’onglet **Autorisations** pour afficher la liste détaillée des autorisations attribuées à ce rôle d'administrateur. Sélectionnez l’onglet **Attribué** ou **Administrateurs affectés** pour ajouter des utilisateurs aux rôles. Si vous souhaitez en savoir plus sur l’attribution de rôles dans le Centre d’administration Microsoft 365, consultez la page [Attribuer des rôles d’administrateur](assign-admin-roles.md).

::: moniker-end

## <a name="all-azure-ad-roles"></a>Tous les rôles Azure AD

Voici la liste de tous les rôles d'administrateur disponibles dans le Centre d’administration Microsoft 365. Vous recherchez des descriptions de rôles détaillées des rôles d’administrateur Microsoft 365 ? Consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

|Rôle d’administrateur     |Description  |
|---------|---------|
|Administrateur d'applications     |    Accès total aux applications de l'entreprise, aux inscriptions d’applications et aux paramètres de proxy d’application.     |
|Développeur d’applications     |    Créer des inscriptions aux applications et accorder l'accès aux applications en leur nom.     |
|Administrateur d'authentification     |    Peut exiger que les utilisateurs enregistrent de nouveau l’authentification pour les informations d’identification autres que le mot de passe, telles que l’authentification multifacteur.     |
|Administrateur Azure Information Protection     |   Gère les étiquettes pour la stratégie Azure Information Protection, gère les modèles de protection et active la protection.       |
|Administrateur de la facturation     |    Effectue des achats, gère les abonnements et les demandes de service, et surveille l’intégrité des services.     |
|Administrateur d'applications cloud     | Accès total aux applications de l'entreprise et aux inscriptions d’applications. Aucun proxy d'application.     |
|Administrateur d'appareils cloud     |    Active, désactive et supprime les appareils et peut lire les clés BitLocker Windows 10.     |
|Administrateur de mise en conformité     |    Gère les exigences réglementaires et les cas eDiscovery, gère la gouvernance des données pour les emplacements, les identités et les applications.     |
|Administrateur des données de mise en conformité     |    Effectue le suivi des données, s'assure qu'elles sont protégés, obtient des informations sur les problèmes et s'efforce d'en atténuer les risques.     |
|Administrateur d'accès conditionnel     |   Gère les paramètres d’accès conditionnel Azure Active Directory, mais pas la stratégie d’accès conditionnel d’Exchange ActiveSync.      |
|Approbateur d'accès à Customer Lockbox     |      Gère les demandes Customer Lockbox et peut activer ou désactiver Customer Lockbox.   |
|Administrateur Analyses de bureau     |   Peut accéder et gérer les outils et services de gestion de bureau.      |
|Administrateur Dynamics 365     |  Accès total à Microsoft Dynamics 365 Online, gère les demandes de service, surveille l’intégrité du service.       |
|Administrateur Exchange     |  Accès total à Exchange Online, crée et gère des groupes, gère les demandes de service et surveille l’état d’intégrité du service.    |
|Administrateur des fournisseurs d'identité externes    |     Configurer les fournisseurs d’identité pour un usage dans la Fédération directe.    |
|Administrateur global     |    Dispose d’un accès illimité à toutes les fonctionnalités de gestion et à la plupart des données de tous les centres d’administration.     |
|Lecteur général     |    Dispose d’un accès en lecture seule à toutes les fonctionnalités de gestion et à la plupart des données des centres d’administration. Pour obtenir une description détaillée des droits d’accès et des limites de ce rôle, voir les [Autorisations de rôles d'administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-reader).    |
|Administrateur de groupes   |Crée des groupes et gère tous les paramètres de groupes dans les centres d’administration.|
|Inviteur d'invités     |    Gère les invitations des utilisateurs invités B2B dans Azure Active Directory.     |
|Administrateur du support technique     | Réinitialise les mots de passe et effectue une nouvelle authentification pour tous les non administrateurs et certains rôles d’administrateur, gère les demandes de service et surveille l’intégrité du service.      |
|Administrateur Insights     | Gère tous les aspects de l’application Insights de Microsoft 365, lit les informations Azure Active Directory, peut surveiller l’état du service et créer et gérer les demandes de service.      |
|Administrateur d’entreprise Insights     | Consultez des rapports et des informations dans l’application Insights de Microsoft 365.      |
|Administrateur Intune     | Accès total à Intune, gère les utilisateurs et les appareils pour associer des stratégies, crée et gère des groupes.      |
|Administrateur Kaizala     |    Accès total à la gestion de toutes les fonctionnalités et données de Kaizala, gère les demandes de service.     |
|Administrateur de licences     |     Attribue et retire les licences d’utilisateurs et modifie leur lieu d’utilisation.    |
|Lecteur de confidentialité du Centre de messages     |    Accès aux messages de confidentialité des données dans le Centre de messages, reçoit des notifications par courrier électronique.     |
|Lecteur du Centre de messages     | Lit et partage des messages ordinaires dans le Centre de messages, reçoit des résumés hebdomadaires par courrier, dispose d'un accès en lecture seule aux utilisateurs, groupes, domaines et abonnements.     |
|Administrateur d'applications Office    |   Gère les stratégies basées sur le cloud pour Office et le contenu des nouveautés que les utilisateurs affichent dans leurs applications Office.   |
|Administrateur de mots de passe    |   Réinitialisez les mots de passe des utilisateurs qui ne sont pas administrateurs ou membres des rôles suivants : lecteurs d’annuaires, Invité d'honneur et administrateur de mots de passe. Ce rôle ne peut pas accorder la possibilité de gérer les demandes de service ou d’analyser l’état d’intégrité du service.   |
|Administrateur Power BI    |   Accès complet aux tâches de gestion de Power BI, gère les demandes de service et surveille l’état d’intégrité du service.   |
|Administrateur de plateformes Power     |    Accès total aux stratégies de protection contre la perte de données, à Microsoft Dynamics 365, PowerApps et Microsoft Flow.     |
|Administrateur de rôle privilégié     |    Gère les affectations de rôle et accès total à toutes les fonctionnalités de contrôle de la Gestion des identités privilégiées.     |
|Administrateur d'authentification privilégié     |    Réinitialise les mots de passe, met à jour les informations d’identification autres que les mots de passe, oblige les utilisateurs à se déconnecter et surveille l’état d’intégrité du service et gère les demandes de service.     |
|Lecteur de rapports     |   Lit les données des rapports d’utilisation du tableau de bord des rapports, du pack de contenu Adoption de PowerBI, des rapports de connexion et de l’API de création de rapports Microsoft Graph.      |
|Administrateur de recherche     |    Accès total à la Recherche Microsoft, attribue les rôles d’administrateur de recherche et d’éditeur de recherche, gère le contenu éditorial, surveille l’intégrité du service et crée des demandes de service.     |
|Éditeur de recherche     |    Peut uniquement créer, modifier et supprimer du contenu pour la Recherche Microsoft, tel que les signets, Q&R et les emplacements.     |
|Administrateur de la sécurité     |    Contrôle la sécurité de l’organisation, gère les stratégies de sécurité, examine les rapports et les analyses de sécurité, surveille les menaces.     |
|Opérateur de sécurité     |    Recherche et répond aux alertes de sécurité, gère les fonctionnalités dans Identity Protection Center, surveille l’intégrité du service.     |
|Lecteur Sécurité     |    Accès en lecture seule aux fonctionnalités de sécurité, rapports de connexion et aux journaux d’audit.     |
|Administrateur de support de service     |    Crée des demandes de service pour Azure, Microsoft 365 et les services Office 365, et contrôle l’état d’intégrité du service.     |
|Administrateur SharePoint     |    Accès total à SharePoint Online, gère les groupes Microsoft 365, gère les demandes de service et surveille l’état d’intégrité du service.     |
|Administrateur pour Skype Entreprise     | Accès total à toutes les fonctionnalités Skype et Teams, aux attributs utilisateur Skype, gère les demandes de service et surveille l'état d’intégrité du service.      |
|Administrateur Teams     |    Accès total au centre d’administration Skype et Teams, gère les groupes Microsoft 365, les demandes de service, et surveille l’état d’intégrité du service.     |
|Gestionnaire de communication Teams     |    Attribue des numéros de téléphone, crée et gère des stratégies de voix et de réunion, et lit les analyses d'appels.     |
|Ingénieur du support de communication Teams     |    Lit les détails de l’enregistrement d’appel pour tous les participants à un appel afin de résoudre les problèmes de communication.     |
|Spécialiste du support de communication Teams     |    Lit les détails d'appel d'un utilisateur spécifique uniquement afin de résoudre les problèmes de communication.|
|Administrateur d’utilisateurs     |   Réinitialise le mot de passe des utilisateurs, crée et gère les utilisateurs et les groupes, y compris les filtres, gère les demandes de service et surveille l’état d’intégrité du service.|

## <a name="delegated-administration-for-microsoft-partners"></a>Administration déléguée pour les partenaires Microsoft

Si vous travaillez avec un partenaire Microsoft, vous pouvez lui attribuer un rôle d’administrateur. Il peut à son tour attribuer des rôles d'administrateur aux utilisateurs de votre entreprise ou de la sienne. Par exemple, vous souhaiterez peut-être qu’il le fasse s’il est chargé de configurer et de gérer votre organisation en ligne pour vous.
  
Un partenaire peut attribuer ces rôles : 

- Administration totale, dont les privilèges sont équivalents à ceux d’un administrateur général, sauf en matière de gestion de l’authentification multifacteur via l'Espace partenaires.

- Administration limitée, dont les privilèges sont équivalents à ceux d’un administrateur du support technique.

Pour que le partenaire puisse attribuer ces rôles à des utilisateurs, vous devez ajouter le partenaire en tant qu’administrateur délégué de votre compte. Ce processus est initié par un partenaire autorisé. Le partenaire vous envoie un e-mail pour vous demander l’autorisation d’agir en tant qu’administrateur délégué. Pour consulter des instructions, voir [Autoriser ou supprimer des relations de partenaire](https://docs.microsoft.com/microsoft-365/admin/misc/add-partner).
  
## <a name="related-articles"></a>Articles connexes

[À propos des rôles d’administrateur Microsoft 365](about-admin-roles.md)

[Attribuer des rôles administrateur](assign-admin-roles.md)
  
[Rapports d’activité dans le Centre d’administration Microsoft 365](../activity-reports/activity-reports.md)