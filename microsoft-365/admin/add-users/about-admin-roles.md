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
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: da585eea-f576-4f55-a1e0-87090b6aaa9d
description: Les rôles d’administrateur correspondent à des fonctions professionnelles et accordent l'autorisation d'effectuer des tâches spécifiques dans le centre d’administration. Par exemple, l’administrateur du service peut ouvrir les tickets de support via le centre d’administration.
ms.openlocfilehash: e0155ee9e263d4b62dced0e2bd943781ccf93a4c
ms.sourcegitcommit: 437bdbf3f99610869811e80432a59b5f244f7a87
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51644254"
---
# <a name="about-admin-roles"></a>À propos des rôles d’administrateur

L’abonnement Microsoft 365 ou Office 365 inclut un ensemble de rôles d’administrateur que vous pouvez attribuer aux utilisateurs de votre organisation à l’aide du Centre d’administration Microsoft 365. Chaque rôle d’administrateur correspond à des fonctions d’entreprise courantes et donne aux personnes concernées dans votre organisation des autorisations pour effectuer des tâches spécifiques dans les centres d’administration.

Le Centre d’administration Microsoft 365 vous permet de gérer les rôles Azure AD et Microsoft Intune. Toutefois, ces rôles sont un sous-ensemble des rôles disponibles sur le Portail Azure AD et le Centre d’administration Intune.

## <a name="before-you-begin"></a>Avant de commencer

Vous recherchez la liste complète des descriptions de rôle Azure AD détaillées que vous pouvez gérer dans le centre d’administration Microsoft 365 ? Consultez la page Autorisations des rôles d’administrateur dans Azure Active Directory. [Autorisations des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles).

Vous recherchez la liste complète des descriptions de rôle Intune détaillées que vous pouvez gérer dans le centre d’administration Microsoft 365 ?  Consultez la page [Contrôle d’accès basé sur un rôle dans Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Si vous souhaitez en savoir plus sur l’attribution de rôles dans le Centre d’administration Microsoft 365, consultez la page [Attribuer des rôles d’administrateur](assign-admin-roles.md).

### <a name="watch-what-is-an-admin"></a>Regardez : qu’est-ce qu’un administrateur ?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

## <a name="security-guidelines-for-assigning-roles"></a>Directives de sécurité pour l'attribution des rôles

Étant donné que les administrateurs ont accès à des fichiers et données sensibles, nous vous recommandons de suivre ces instructions afin de renforcer la sécurité des données au sein de votre organisation.

| Recommandation                  | Pourquoi est-ce important ?                 |
| :------------------- | :------------------- |
| Avoir de deux à quatre administrateurs généraux  | Dans la mesure où seul un autre administrateur général peut réinitialiser le mot de passe d’un administrateur général, nous vous recommandons d’avoir au moins deux administrateurs généraux dans votre organisation en cas de verrouillage de compte. Cependant, il faut note que l’administrateur général dispose d’un accès quasi illimité aux paramètres de votre organisation et à la plupart des données. Nous vous recommandons donc également de ne pas avoir plus de 4 administrateurs généraux, car il s’agit d’une menace du point de vue de la sécurité. |
| Attribuer le rôle *le moins permissif*    | L’attribution du rôle le *moins permissif* signifie que vous ne donnez aux administrateurs qu'un rôle d'accès à ce dont ils ont besoin pour accomplir leurs tâches. Par exemple, si vous voulez qu’une personne réinitialise les mots de passe des employés, vous devez attribuer un rôle d’administrateur général limité, tel que administrateur de mots de passe ou administrateur du support technique. Cela vous permet de sécuriser vos données.                 |
| Exiger une authentification multifacteur pour les administrateurs                  |    Il est recommandé d’exiger l’authentification multifacteur (MFA) pour l’ensemble de vos utilisateurs, et les administrateurs devraient clairement être obligés d’utiliser l’authentification multifacteur pour se connecter. L’authentification multifacteur demande aux utilisateurs d’entrer une deuxième méthode d’identification pour vérifier leur identité. Les administrateurs peuvent avoir accès à un grand nombre de données sur les clients et les employés. Si vous exigez une authentification multifacteur, le mot de passe est inutilisable sans la deuxième forme d’identification, même si le mot de passe administrateur est compromis.  <br><br>Lorsque vous activez l’authentification multifacteur, lors de la connexion suivante de l'utilisateur, il doit fournir une adresse de messagerie alternative et un numéro de téléphone pour la récupération de compte.  <br> [Configurer l’authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Si vous recevez un message dans le centre d’administration vous indiquant que vous n’êtes pas autorisé à modifier un paramètre ou une page, cela signifie que le rôle attribué ne dispose pas de cette autorisation.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Rôles communément utilisés dans le centre d’administration 365 Microsoft

::: moniker range="o365-worldwide"

Dans le Centre d’administration Microsoft 365, vous pouvez accéder à **Rôles**, puis sélectionner un rôle pour ouvrir le volet Détails. Sélectionnez l’onglet **Autorisations** pour afficher la liste détaillée des autorisations attribuées à ce rôle d'administrateur. Sélectionnez l’onglet **Attribué** ou **Administrateurs affectés** pour ajouter des utilisateurs aux rôles.

::: moniker-end

Vous devrez probablement attribuer les rôles suivants au sein de votre organisation. Par défaut, les rôles les plus utilisés par les organisations s'affichent en premier. Si le rôle recherché est introuvable, accédez au bas de la liste et sélectionnez **Afficher tout par catégorie**. (pour plus d’informations, notamment sur les applets de commande associées à un rôle, voir les [Autorisations de rôle d'administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles)).

|Rôle d’administrateur     |À qui doit être affecté ce rôle ?  |
|---------|---------|
|Administrateur de facturation     |   Affectez aux utilisateurs un administrateur de facturation qui peut effectuer des achats, gérer des demandes d’abonnement et de services et surveiller l’intégrité des services. <br><br> Les administrateurs de facturation peuvent également :<br> – Gérer tous les aspects de la facturation <br> – Créer et gérer des tickets au support dans le Portail Azure <br>  |
|Administrateur Exchange     |   Attribuez le rôle d’administrateur Exchange aux utilisateurs qui doivent afficher et gérer les boîtes aux lettres de messagerie de vos utilisateurs, les groupes Microsoft 365 et Exchange Online. <br><br> Les administrateurs Exchange peuvent aussi :<br> – Récupérer des éléments supprimés dans la boîte aux lettres d’un utilisateur <br> – Configurer les délégués « Envoyer en tant que » et « Envoyer de la part de » <br>  |
|Administrateur global     |   Attribuez le rôle d’administrateur général aux utilisateurs qui doivent avoir un accès global à la plupart des fonctionnalités de gestion et des données dans les services Microsoft Online. <br><br> Le fait de donner un accès global à un grand nombre d’utilisateurs représente un risque pour la sécurité et nous vous recommandons de n’avoir que 2 à 4 administrateurs généraux. <br><br> Seuls les administrateurs généraux peuvent :<br> – Réinitialiser les mots de passe pour l'ensemble des utilisateurs <br> – Ajouter et gérer des domaines <br> <br> **Remarque :** la personne qui s’est inscrite aux services Microsoft Online devient automatiquement un administrateur général. |
|Lecteur général    |   Attribuez le rôle de lecteur global aux utilisateurs qui doivent afficher les fonctionnalités et paramètres d’administration dans des centres d’administration que l’administrateur général peut afficher. Un administrateur lecteur global n'est pas autorisé à modifier des paramètres.   |
|Administrateur de groupes     |   Attribuez le rôle d’administrateur de groupes aux utilisateurs qui doivent gérer tous les paramètres de groupes dans les centres d’administration, y compris le centre d’administration Microsoft 365 et le portail Azure Active Directory. <br><br> Les administrateurs de groupe peuvent :<br> – créer, modifier, supprimer et restaurer les groupes Microsoft 365 <br> – Créer et mettre à jour les stratégies de création, d’expiration et de désignation de groupes <br> – Créer, modifier, supprimer et restaurer des groupes de sécurité Azure Active Directory| 
|Administrateur du support technique     |   Attribuez le rôle d’administrateur du support technique aux utilisateurs qui doivent effectuer les opérations suivantes :<br> – Réinitialiser des mots de passe <br> – Forcer les utilisateurs à se déconnecter <br> – Gérer des demandes de service <br> – Surveiller l’état d’intégrité des services <br> <br> **Remarque**: l’administrateur du support technique peut uniquement aider des utilisateurs sans rôle d'administrateur et les utilisateurs ayant ces rôles : lecteur d’annuaire, invités hôtes, administrateur du support technique, lecteur de centre de messages et lecteur de rapports.      |
|Administrateur de licences    |   Affectez le rôle d’administrateur de licences aux utilisateurs qui doivent attribuer et supprimer des licences d’utilisateurs et modifier leur localisation d’utilisation. <br/><br/> Les administrateurs de licences peuvent également : <br> – Retraiter les affectations de licences pour les licences basées sur des groupes <br> – Affecter des licences produit aux groupes pour les licences basées sur des groupes  |
|Administrateur d'applications Office    |   Attribuez le rôle d’administrateur d'applications Office aux utilisateurs qui doivent effectuer les opérations suivantes : <br> – Utiliser le service de stratégie cloud Office pour créer et gérer des stratégies basées sur le cloud pour Office <br> – Créer et gérer des demandes de service <br> – Gérer le contenu des nouveautés que les utilisateurs peuvent afficher dans les applications Office   <br> – Surveiller l’état d’intégrité des services  |
|Administrateur de mots de passe  |   Affectez le rôle d'administrateur de mots de passe à un utilisateur qui doit réinitialiser des mots de passe pour les non administrateurs et les administrateurs de mots de passe.   |
|Administrateur de support de service   |   Affectez le rôle d’administrateur de support de service en tant que rôle supplémentaire aux administrateurs ou aux utilisateurs qui doivent effectuer ce qui suit en complément de leur rôle d’administrateur habituel : <br> – Ouvrir et gérer des demandes de service <br> – Afficher et partager des billets du centre de messages <br> – Surveiller l’état d’intégrité des services   |
|Administrateur SharePoint    |   Attribuez le rôle d’administrateur SharePoint aux utilisateurs qui doivent accéder et gérer le centre d’administration SharePoint Online. <br><br>Les administrateurs SharePoint peuvent également : <br> – Créer et supprimer des sites <br> – Gérer les collections de sites et les paramètres globaux de SharePoint   |
|Administrateur du service Teams    |   Attribuez le rôle d’administrateur du service Teams aux utilisateurs qui doivent accéder et gérer le centre d’administration Teams. <br><br>Les administrateurs du service Teams peuvent également : <br> – Gérer des réunions <br> – Gérer les ponts de conférence <br> – Gérer tous les paramètres à l’échelle de l’organisation, notamment la fédération, la mise à jour de Teams et les paramètres du client Teams   |
|Administrateur d’utilisateurs     |    Attribuez le rôle d’administrateur d'utilisateurs aux ceux qui doivent effectuer les opérations suivantes pour l'ensemble des utilisateurs : <br> – Ajouter des utilisateurs et des groupes <br> – Attribuer des licences <br> – Gérer la plupart des propriétés des utilisateurs <br> – Créer et gérer les affichages utilisateur <br> – Mettre à jour les stratégies d’expiration des mots de passe <br> – Gérer des demandes de service <br> – Surveiller l’état d’intégrité des services <br><br>  L’administrateur d’utilisateurs peut également effectuer les actions suivantes pour les utilisateurs qui ne sont pas administrateurs et pour ceux auxquels les rôles suivants sont attribués : lecteur de répertoire, inviteur d'invités, administrateur du support technique, lecteur du centre de messages, lecteur de rapports : <br> – Gérer les noms d’utilisateur<br> – Supprimer et restaurer des d’utilisateurs<br> – Réinitialiser des mots de passe <br> – Forcer les utilisateurs à se déconnecter <br> – Mettre à jour les clés d'appareils (FIDO)   |

## <a name="delegated-administration-for-microsoft-partners"></a>Administration déléguée pour les partenaires Microsoft

Si vous travaillez avec un partenaire Microsoft, vous pouvez lui attribuer un rôle d’administrateur. Il peut à son tour attribuer des rôles d'administrateur aux utilisateurs de votre entreprise ou de la sienne. Par exemple, vous souhaiterez peut-être qu’il le fasse s’il est chargé de configurer et de gérer votre organisation en ligne pour vous.
  
Un partenaire peut attribuer ces rôles : 
  
- **Agent d’administration**, dont les privilèges sont équivalents à ceux d’un administrateur général, sauf en matière de gestion de l’authentification multifacteur via l'Espace partenaires.

- **Agent de support technique**, dont les privilèges sont équivalents à ceux d’un administrateur du support technique.

Pour que le partenaire puisse attribuer ces rôles à des utilisateurs, vous devez ajouter le partenaire en tant qu’administrateur délégué de votre compte. Ce processus est initié par un partenaire autorisé. Le partenaire vous envoie un e-mail pour vous demander l’autorisation d’agir en tant qu’administrateur délégué. Pour consulter des instructions, voir [Autoriser ou supprimer des relations de partenaire](../misc/add-partner.md).
  
## <a name="related-articles"></a>Articles connexes

[Attribuer des rôles administrateur](assign-admin-roles.md)

[Les rôles d'administration Azure AD dans le Centre d’administration Microsoft 365](azure-ad-roles-in-the-mac.md)

[Rôle d’administrateur Exchange Online](about-exchange-online-admin-role.md)
  
[Rapports d’activité dans le Centre d’administration Microsoft 365](../activity-reports/activity-reports.md)
