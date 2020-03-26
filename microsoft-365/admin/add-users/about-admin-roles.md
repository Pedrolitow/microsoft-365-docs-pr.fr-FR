---
title: Les rôles d'administration dans le Centre d’administration Microsoft 365
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: da585eea-f576-4f55-a1e0-87090b6aaa9d
description: Les rôles d’administrateur correspondent à des fonctions professionnelles et accordent l'autorisation d'effectuer des tâches spécifiques dans le centre d’administration. Par exemple, l’administrateur du service ouvre les tickets de support avec Microsoft.
ms.custom: okr_smb
ms.openlocfilehash: 22693bbf8acdf8872b621ae214dd8d7a62b98b40
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929549"
---
# <a name="about-admin-roles"></a>À propos des rôles d’administrateur

Votre abonnement inclut un ensemble de rôles d’administrateur que vous pouvez attribuer aux utilisateurs de votre organisation. Chaque rôle d’administrateur correspond à des fonctions d’entreprise courantes et donne aux personnes concernées dans votre organisation des autorisations pour effectuer des tâches spécifiques dans les centres d’administration. Pour plus d’informations, voir [Affecter des rôles d’administrateur](assign-admin-roles.md).

> [!TIP] 
> Vous recherchez des descriptions de rôles détaillées ? Voir [Autorisations des rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).

## <a name="things-to-consider"></a>Éléments à prendre en considération...

Étant donné que les administrateurs ont accès à des fichiers et données sensibles, nous vous recommandons de suivre ces instructions afin de renforcer la sécurité des données au sein de votre organisation.

| Recommandation                  | Pourquoi est-ce important ?                 |
| :------------------- | :------------------- |
| Avoir de deux à quatre administrateurs généraux  | Dans la mesure où seul un autre administrateur général peut réinitialiser le mot de passe d’un administrateur général, nous vous recommandons d’avoir au moins deux administrateurs généraux dans votre organisation en cas de verrouillage de compte. Cependant, il faut note que l’administrateur général dispose d’un accès quasi illimité aux paramètres de votre organisation et à la plupart des données. Nous vous recommandons donc également de ne pas avoir plus de 4 administrateurs généraux, car il s’agit d’une menace du point de vue de la sécurité. |
| Attribuer le rôle *le moins permissif*    | L’attribution du rôle le *moins permissif* signifie que vous ne donnez aux administrateurs qu'un rôle d'accès à ce dont ils ont besoin pour accomplir leurs tâches. Par exemple, si vous voulez qu’une personne réinitialise les mots de passe des employés, vous devez attribuer un rôle d’administrateur général limité, tel que administrateur de mots de passe ou administrateur du support technique. Cela vous permet de sécuriser vos données.                 |
| Exiger une authentification multifacteur pour les administrateurs                  |    Il est recommandé d’exiger l’authentification multifacteur (MFA) pour l’ensemble de vos utilisateurs, et les administrateurs devraient clairement être obligés d’utiliser l’authentification multifacteur pour se connecter. L’authentification multifacteur demande aux utilisateurs d’entrer une deuxième méthode d’identification pour vérifier leur identité. Les administrateurs peuvent avoir accès à un grand nombre de données sur les clients et les employés. Si vous exigez une authentification multifacteur, le mot de passe est inutilisable sans la deuxième forme d’identification, même si le mot de passe administrateur est compromis.  <br><br>Lorsque vous activez l’authentification multifacteur, lors de la connexion suivante de l'utilisateur, il doit fournir une adresse de messagerie alternative et un numéro de téléphone pour la récupération de compte.  <br> [Configurer l’authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md)          |

  
## <a name="some-roles-are-missing-from-active-users--manage-admin-roles-where-did-they-go"></a>Certains rôles sont absents à partir des utilisateurs actifs > Gérer les rôles d’administrateur. Où sont-ils passés ?
Par défaut, les rôles les plus utilisés par les organisations s'affichent en premier. Si le rôle recherché est introuvable, accédez au bas de la liste et sélectionnez **Voir d'autres rôles**.

## <a name="how-can-i-tell-which-permissions-are-assigned-to-me"></a>Comment savoir quelles autorisations m'ont été affectées ?
Si vous recevez un message dans le centre d’administration vous indiquant que vous n’êtes pas autorisé à modifier un paramètre ou une page, cela signifie que le rôle attribué ne dispose pas de cette autorisation.

## <a name="what-about-the-azure-active-directory-roles"></a>Qu’en est-il des rôles Azure Active Directory ? 

Le portail Azure possède davantage de rôles que ceux disponibles dans le Centre d’administration Microsoft 365. Si vous avez une grande entreprise, certains rôles dans le Portail Microsoft Azure peuvent répondre aux besoins de votre organisation.

Pour obtenir la liste de tous les rôles Azure Active Directory ainsi que leur description, voir [Autorisations de rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).

Un utilisateur doté d’un rôle d’administrateur disposera du même niveau d'accès vers les services cloud auxquels votre organisation est abonnée, que vous lui ayez attribué le rôle dans le Centre d’administration Microsoft 365 ou le portail Azure, ou à l’aide du module Azure AD pour Windows PowerShell.
  
## <a name="roles-available-in-the-microsoft-365-admin-center"></a>Rôles d'administration disponibles dans le Centre d’administration Microsoft 365

Le Centre d’administration Microsoft 365 vous permet de gérer plus de 30 rôles Azure AD. Toutefois, ces rôles sont un sous-ensemble des rôles disponibles sur le Portail Microsoft Azure.

::: moniker range="o365-worldwide"

Dans le centre d’administration, vous pouvez accéder à **Rôles**, puis sélectionner un rôle quelconque pour ouvrir le volet Détails. Sélectionnez l’onglet **Autorisations** pour afficher la liste détaillée des autorisations attribuées à ce rôle d'administrateur particulier.

::: moniker-end

Vous devrez probablement affecter les rôles suivants au sein de votre organisation. (pour plus d’informations, notamment sur les applets de commande associées à un rôle, voir les [Autorisations de rôle d'administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles)).

|Rôle d’administrateur     |À qui doit être affecté ce rôle ?  |
|---------|---------|
|Administrateur Exchange     |   Attribuez le rôle d’administrateur Exchange aux utilisateurs qui doivent afficher et gérer les boîtes aux lettres de messagerie de vos utilisateurs, les groupes Office 365 et Exchange Online. <br><br> Les administrateurs Exchange peuvent aussi :<br> – Récupérer des éléments supprimés dans la boîte aux lettres d’un utilisateur <br> – Configurer les délégués « Envoyer en tant que » et « Envoyer de la part de » <br>  |
|Administrateur global     |   Attribuez le rôle d’administrateur général aux utilisateurs qui doivent avoir un accès global à la plupart des fonctionnalités de gestion et des données dans les services Microsoft Online. <br><br> Le fait de donner un accès global à un grand nombre d’utilisateurs représente un risque pour la sécurité et nous vous recommandons de n’avoir que 2 à 4 administrateurs généraux. <br><br> Seuls les administrateurs généraux peuvent :<br> – Réinitialiser les mots de passe pour l'ensemble des utilisateurs <br> – Ajouter et gérer des domaines <br> <br> **Remarque :** la personne qui s’est inscrite aux services Microsoft Online devient automatiquement un administrateur général. |
|Lecteur général    |   Attribuez le rôle de lecteur global aux utilisateurs qui doivent afficher les fonctionnalités et paramètres d’administration dans des centres d’administration que l’administrateur général peut afficher. Un administrateur lecteur global n'est pas autorisé à modifier des paramètres.   |
|Administrateur de groupes     |   Attribuez le rôle d’administrateur de groupes aux utilisateurs qui doivent gérer tous les paramètres de groupes dans les centres d’administration, y compris le centre d’administration Microsoft 365 et le portail Azure Active Directory. <br><br> Les administrateurs de groupe peuvent :<br> – Créer, modifier, supprimer et restaurer des Groupes Office 365 <br> – Créer et mettre à jour les stratégies de création, d’expiration et de désignation de groupes <br> – Créer, modifier, supprimer et restaurer des groupes de sécurité Azure Active Directory| 
|Administrateur du support technique     |   Attribuez le rôle d’administrateur du support technique aux utilisateurs qui doivent effectuer les opérations suivantes :<br> – Réinitialiser des mots de passe <br> – Forcer les utilisateurs à se déconnecter <br> – Gérer des demandes de service <br> – Surveiller l’état d’intégrité des services <br> <br> **Remarque**: l’administrateur du support technique peut uniquement aider des utilisateurs sans rôle d'administrateur et les utilisateurs ayant ces rôles : lecteur d’annuaire, invités hôtes, administrateur du support technique, lecteur de centre de messages et lecteur de rapports.      |
|Administrateur d'applications Office    |   Attribuez le rôle d’administrateur d'applications Office aux utilisateurs qui doivent effectuer les opérations suivantes : <br> – Utiliser le service de stratégie cloud Office pour créer et gérer des stratégies basées sur le cloud pour Office <br> – Créer et gérer des demandes de service <br> – Gérer le contenu des nouveautés que les utilisateurs peuvent afficher dans les applications Office   <br> – Surveiller l’état d’intégrité des services  |
|Administrateur de service    |   Attribuez le rôle d’administrateur de service à un rôle supplémentaire pour les administrateurs ou les utilisateurs dont le rôle n’inclut pas les éléments suivants, bien qu'ils doivent effectuer les opérations suivantes : <br> – Ouvrir et gérer des demandes de service <br> – Afficher et partager des billets du centre de messages   |
|Administrateur SharePoint    |   Attribuez le rôle d’administrateur SharePoint aux utilisateurs qui doivent accéder et gérer le centre d’administration SharePoint Online. <br><br>Les administrateurs SharePoint peuvent également : <br> – Créer et supprimer des sites <br> – Gérer les collections de sites et les paramètres globaux de SharePoint   |
|Administrateur du service Teams    |   Attribuez le rôle d’administrateur du service Teams aux utilisateurs qui doivent accéder et gérer le centre d’administration Teams. <br><br>Les administrateurs du service Teams peuvent également : <br> – Gérer des réunions <br> – Gérer les ponts de conférence <br> – Gérer tous les paramètres à l’échelle de l’organisation, notamment la fédération, la mise à jour de Teams et les paramètres du client Teams   |
|Administrateur d’utilisateurs     |    Attribuez le rôle d’administrateur d'utilisateurs aux ceux qui doivent effectuer les opérations suivantes pour l'ensemble des utilisateurs : <br> – Ajouter des utilisateurs et des groupes <br> – Attribuer des licences <br> – Gérer la plupart des propriétés des utilisateurs <br> – Créer et gérer les affichages utilisateur <br> – Mettre à jour les stratégies d’expiration des mots de passe <br> – Gérer des demandes de service <br> – Surveiller l’état d’intégrité des services <br><br>  L’administrateur d’utilisateurs peut également effectuer les actions suivantes pour les utilisateurs qui ne sont pas administrateurs et pour ceux auxquels les rôles suivants sont attribués : lecteur de répertoire, inviteur d'invités, administrateur du support technique, lecteur du centre de messages, lecteur de rapports : <br> – Gérer les noms d’utilisateur<br> – Supprimer et restaurer des d’utilisateurs<br> – Réinitialiser des mots de passe <br> – Forcer les utilisateurs à se déconnecter <br> – Mettre à jour les clés d'appareils (FIDO)   |

### <a name="all-roles"></a>Tous les rôles

 Voici la liste de tous les rôles d'administrateur disponibles dans le Centre d’administration Microsoft 365.

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
|Administrateur Intune     | Accès total à Intune, gère les utilisateurs et les appareils pour associer des stratégies, crée et gère des groupes.      |
|Administrateur Kaizala     |    Accès total à la gestion de toutes les fonctionnalités et données de Kaizala, gère les demandes de service.     |
|Administrateur de licences     |     Attribue et retire les licences d’utilisateurs et modifie leur lieu d’utilisation.    |
|Lecteur de confidentialité du Centre de messages     |    Accès aux messages de confidentialité des données dans le Centre de messages, reçoit des notifications par courrier électronique.     |
|Lecteur du Centre de messages     | Lit et partage des messages ordinaires dans le Centre de messages, reçoit des résumés hebdomadaires par courrier, dispose d'un accès en lecture seule aux utilisateurs, groupes, domaines et abonnements.     |
|Administrateur d'applications Office    |   Gère les stratégies basées sur le cloud pour Office et le contenu des nouveautés que les utilisateurs affichent dans leurs applications Office.   |
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
|Administrateur SharePoint     |    Accès total à Exchange Online, crée et gère des groupes Office 365, gère les demandes de service et surveille l’état d’intégrité du service.     |
|Administrateur pour Skype Entreprise     | Accès total à toutes les fonctionnalités Skype et Teams, aux attributs utilisateur Skype, gère les demandes de service et surveille l'état d’intégrité du service.      |
|Administrateur Teams     |    Accès total au centre d'administration Skype et Teams, gère les groupes Office 365 et les demandes de service, et surveille l’état d’intégrité du service.     |
|Gestionnaire de communication Teams     |    Attribue des numéros de téléphone, crée et gère des stratégies de voix et de réunion, et lit les analyses d'appels.     |
|Ingénieur du support de communication Teams     |    Lit les détails de l’enregistrement d’appel pour tous les participants à un appel afin de résoudre les problèmes de communication.     |
|Spécialiste du support de communication Teams     |    Lit les détails d'appel d'un utilisateur spécifique uniquement afin de résoudre les problèmes de communication.|
|Administrateur d’utilisateurs     |   Réinitialise le mot de passe des utilisateurs, crée et gère les utilisateurs et les groupes, y compris les filtres, gère les demandes de service et surveille l’état d’intégrité du service.|

## <a name="delegated-administration-for-microsoft-partners"></a>Administration déléguée pour les partenaires Microsoft

Si vous travaillez avec un partenaire Microsoft, vous pouvez lui attribuer un rôle d’administrateur. Il peut à son tour attribuer des rôles d'administrateur aux utilisateurs de votre entreprise ou de la sienne. Par exemple, vous souhaiterez peut-être qu’il le fasse s’il est chargé de configurer et de gérer votre organisation en ligne pour vous.
  
Un partenaire peut attribuer ces rôles : 
  
- Administration totale, dont les privilèges sont équivalents à ceux d’un administrateur général, sauf en matière de gestion de l’authentification multifacteur via l'Espace partenaires.
    
- Administration limitée, dont les privilèges sont équivalents à ceux d’un administrateur du support technique.

Pour que le partenaire puisse attribuer ces rôles à des utilisateurs, vous devez ajouter le partenaire en tant qu’administrateur délégué de votre compte. Ce processus est initié par un partenaire autorisé. Le partenaire vous envoie un e-mail pour vous demander l’autorisation d’agir en tant qu’administrateur délégué. Pour consulter des instructions, voir [Autoriser ou supprimer des relations de partenaire](https://support.office.com/article/201ccb3b-6011-4bf1-a6b2-84e7cc1ee2d0.aspx).
  
## <a name="related-articles"></a>Articles connexes

[Attribuer des rôles d'administrateur](assign-admin-roles.md)
  
[Rapports d’activité dans le Centre d’administration Microsoft 365](../activity-reports/activity-reports.md)
