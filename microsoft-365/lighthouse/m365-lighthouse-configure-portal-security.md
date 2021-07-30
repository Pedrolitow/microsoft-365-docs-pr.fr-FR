---
title: Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment configurer la sécurité du portail.
ms.openlocfilehash: 1e67903fc6c3dfd4e1949ef8c3e80ad4af12ad5c
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53395202"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

La protection de l’accès aux données client lorsqu’un fournisseur de services gérés (MSP) a délégué des autorisations d’accès à ses clients est une priorité de cybersécurité. Microsoft 365 Lighthouse est disponible avec les fonctionnalités requises et facultatives pour vous aider à configurer la sécurité Microsoft 365 Lighthouse portail.

## <a name="set-up-multifactor-authentication-mfa"></a>Configurer l’authentification multifacteur (MFA)

Comme mentionné dans le billet de [blog, votre $word n’a pas d’importance](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> « Votre mot de passe n’a pas d’importance, mais c’est l’fa MFA qui l’est. D’après nos études, votre compte est moins susceptible d’être compromis à plus de 99,9 % si vous utilisez l’mf. »

Lorsque les utilisateurs accèdent à Microsoft 365 Lighthouse pour la première fois, ils sont invités à configurer l’mfmf si leur compte Microsoft 365 ne l’a pas déjà configuré. Les utilisateurs ne pourront pas accéder aux Microsoft 365 Lighthouse tant que l’étape de configuration MFA requise n’est pas terminée. Pour en savoir plus sur les méthodes d’authentification, voir [Configurer votre Microsoft 365 pour l’authentification multifacteur.](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)

## <a name="set-up-roles-to-manage-customer-tenants"></a>Configurer des rôles pour gérer les clients

L’accès aux données et paramètres du client dans Microsoft 365 Lighthouse est limité aux rôles Agent d’administration et Agent du service d’assistance du programme Fournisseur de solutions Cloud (CSP).

Vous pouvez vérifier quels utilisateurs du client partenaire ont les rôles Agent d’administration et Agent du helpdesk en vérifiant les appartenances aux groupes de sécurité sur la page [Azure AD – Tous](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) les groupes. Pour découvrir comment attribuer des rôles de programme CSP et d’autres autorisations aux utilisateurs, voir Attribuer des rôles et des [autorisations aux utilisateurs.](/partner-center/permissions-overview) En tant que MSP, si vous n’avez pas encore délégué des privilèges d’accès aux clients, découvrez comment les obtenir dans l’article Obtenir des autorisations pour gérer le service ou [l’abonnement d’un](/partner-center/customers-revoke-admin-privileges)client.

Le tableau suivant répertorie les différentes pages Microsoft 365 Lighthouse et les autorisations requises pour afficher et agir sur les données client et les paramètres des rôles Agent d’administration et Agent du service d’assistance.<br><br>

| Microsoft 365 Lighthouse page | Autorisations de l’agent administrateur | Autorisations de l’agent du helpdesk |
|--|--|--|
| Accueil | <ul><li>Afficher tout </li></ul> | <ul><li>Afficher tout </li></ul> |
| Clients | <ul><li>Afficher tout </li><li>Mettre à jour les contacts client et le site web</li><li>Afficher et appliquer des plans de déploiement</li></ul> | <ul><li>Afficher tout </li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li></ul> |
| Utilisateurs | <ul><li>Afficher tout </li><li>Réinitialiser le mot de passe</li><li>Bloquer la sign-in</li><li>Activer l’mfmf</li></ul> | <ul><li>Afficher tout </li><li>Réinitialiser le mot de passe</li><li>Bloquer la sign-in</li></ul> |
| Appareils | <ul><li>Afficher tout </li></ul> | <ul><li>Afficher tout </li></ul> |
| Menaces | <ul><li>Afficher tout </li><li>Exécuter une analyse rapide</li><li>Exécuter une analyse complète</li><li>Redémarrer l’appareil</li><li>Mettre à jour un antivirus</li></ul> | <ul><li>Afficher tout </li></ul> |
| Lignes de base | <ul><li>Afficher tout </li></ul> | <ul><li>Afficher tout </li></ul> |
| L’intégrité du service | <ul><li>Afficher tout*</li></ul> | <ul><li>Afficher tout*</li></ul> |

> [!NOTE]
> Actuellement, pour prendre les actions marquées avec * dans le tableau, les utilisateurs doivent également avoir le rôle Azure AD dans le client partenaire avec la propriété suivante définie : **microsoft.office365.serviceHealth/allEntities/allTasks**. Pour obtenir la liste des rôles Azure AD, voir [rôles intégrés Azure AD.](/azure/active-directory/roles/permissions-reference)

Étant donné les autorisations étendues associées au rôle Agent d’administration, nous vous suggérons d’adhérer au principe d’accès le moins privilégié lors de la désignation d’un utilisateur client partenaire en tant qu’agent administrateur ou agent du helpdesk. [](/azure/active-directory/develop/secure-least-privileged-access) Pour ce faire, vous pouvez attribuer le rôle d’agent du helpdesk aux utilisateurs du client partenaire requis. Cela leur permet d’afficher les données et les paramètres des clients, mais pas d’apporter de grandes modifications. Ensuite, si nécessaire, utilisez les fonctionnalités d’approbation d’accès juste-à-temps d’Azure AD Privileged Identity Management (PIM) pour donner aux utilisateurs un rôle d’agent d’administration limité dans le temps.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Configurer Azure AD Privileged Identity Management (PIM)

Les MSP peuvent réduire le nombre de personnes ayant accès à des informations ou des ressources sécurisées à l’aide d’Azure AD Privileged Identity Management (PIM). PIM réduit le risque qu’une personne malveillante accède à des ressources ou à des utilisateurs autorisés par inadvertance, ce qui a un impact sur une ressource sensible. Les MSP peuvent également accorder aux utilisateurs un accès privilégié juste-à-temps aux ressources et surveiller ce que les utilisateurs désignés font avec leur accès privilégié.

> [!NOTE]
> L’utilisation d’Azure AD PIM nécessite Azure AD Premium P2 licence dans le client partenaire.

Les étapes suivantes élèvent les utilisateurs clients partenaires à des rôles d’agent d’administration dans le temps à l’aide d’Azure AD PIM :

1. Créez un groupe à attribuer aux rôles, comme décrit dans l’article Créer un groupe pour [l’attribution](/azure/active-directory/roles/groups-create-eligible)de rôles dans Azure Active Directory .

2. Go to [Azure AD – All Groups](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) and add the new group as a member of the Admin Agents group.

3. Configurer l’accès privilégié au nouveau groupe comme décrit dans l’article Affecter des propriétaires et des membres éligibles pour [les groupes d’accès privilégiés.](/azure/active-directory/privileged-identity-management/groups-assign-member-owner)

Pour en savoir plus, [consultez La Privileged Identity Management ?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="other-roles-and-permissions"></a>Autres rôles et autorisations

Le tableau suivant répertorie les rôles des clients partenaires et leurs autorisations associées.<br><br>

| Rôles des locataires partenaires | Autorisations au sein du client partenaire |
|--|--|
| Administrateur général du client partenaire | <ul><li>Inscrivez-vous Microsoft 365 Lighthouse dans le Centre d’administration Microsoft 365.</li><li>Accepter les modifications apportées au contrat partenaire lors de la première expérience d’utilisateur.</li><li>Afficher les clients sur la page Clients.\*</li><li>Activer et désactiver un client.\*</li><li>Mettez à jour les contacts client et le site web.\*</li><li>Créer, mettre à jour et supprimer des balises.\*</li><li>Affecter et supprimer des balises d’un client.\*</li></ul> |
| Administrateur du client partenaire avec au moins un<br> Rôle Azure AD attribué avec le jeu de propriétés suivant :<br> **microsoft.office365.supportTickets/allEntities/allTasks**<br> (Pour obtenir la liste des rôles Azure AD, voir rôles intégrés [Azure AD.)](/azure/active-directory/roles/permissions-reference) | <ul><li>Créez Microsoft 365 Lighthouse de service.</li></ul> |

> [!NOTE]
> Actuellement, pour prendre les actions marquées avec * dans la table, l’administrateur général doit assumer le rôle Agent d’administration.

## <a name="related-content"></a>Contenu associé

[Vue d’Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)\
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)