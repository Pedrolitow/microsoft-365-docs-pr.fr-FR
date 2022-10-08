---
title: Configurer la sécurité du portail Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment configurer la sécurité du portail.
ms.openlocfilehash: dbadd9742e8b477bf4fa97e2556c37b0a3e3fe3b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193210"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Configurer la sécurité du portail Microsoft 365 Lighthouse

La protection de l’accès aux données client lorsqu’un fournisseur de services managés (MSP) a délégué des autorisations d’accès à ses locataires est une priorité en matière de cybersécurité. Microsoft 365 Lighthouse est fourni avec les fonctionnalités requises et facultatives pour vous aider à configurer la sécurité du portail Lighthouse. Vous devez configurer des rôles spécifiques avec l’authentification multifacteur (MFA) activée avant de pouvoir accéder à Lighthouse. Vous pouvez éventuellement configurer Azure AD Privileged Identity Management (PIM) et l’accès conditionnel.

## <a name="set-up-multifactor-authentication-mfa"></a>Configurer l’authentification multifacteur (MFA)

Comme mentionné dans le billet de blog [Votre Pa$$word n’a pas d’importance](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> « Votre mot de passe n’a pas d’importance, mais c’est le cas de l’authentification multifacteur. Selon nos études, votre compte est plus de 99,9 % moins susceptible d’être compromis si vous utilisez l’authentification multifacteur. »

Lorsque les utilisateurs accèdent à Lighthouse pour la première fois, ils sont invités à configurer l’authentification multifacteur si leur compte Microsoft 365 n’est pas déjà configuré. Les utilisateurs ne pourront pas accéder à Lighthouse tant que l’étape de configuration MFA requise n’est pas terminée. Pour en savoir plus sur les méthodes d’authentification, consultez [Configurer votre connexion Microsoft 365 pour l’authentification multifacteur](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Configurer le contrôle d’accès en fonction du rôle

Le contrôle d’accès en fonction du rôle (RBAC) accorde l’accès aux ressources ou aux informations en fonction des rôles d’utilisateur. L’accès aux données et paramètres du locataire client dans Lighthouse est limité à des rôles spécifiques à partir du programme fournisseur de solutions cloud (CSP). Pour configurer des rôles RBAC dans Lighthouse, nous vous recommandons d’utiliser GDAP (Granular Delegated Administration Privileges) pour implémenter des affectations granulaires pour les utilisateurs. Les privilèges DAP (Delegated Administration Privileges) sont toujours nécessaires pour que le locataire puisse s’intégrer correctement, mais les clients GDAP uniquement pourront bientôt s’intégrer sans dépendance vis-à-vis de DAP. Les autorisations GDAP sont prioritaires lorsque DAP et GDAP coexistent pour un client.

Pour configurer une relation GDAP, consultez [Obtenir des autorisations d’administrateur granulaires pour gérer le service d’un client](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Pour plus d’informations sur les rôles que nous recommandons d’utiliser Lighthouse, consultez [Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

Les techniciens MSP peuvent également accéder à Lighthouse à l’aide de rôles d’agent Administration ou d’agent de support technique via des privilèges DAP (Delegated Administration Privileges).

Pour les actions non liées aux locataires dans Lighthouse (par exemple, intégration, désactivation/réactivation par le client, gestion des étiquettes, examen des journaux), les techniciens MSP doivent avoir un rôle attribué dans le locataire partenaire. Pour plus [d’informations sur les rôles de locataire de partenaire, consultez Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Configurer Azure AD Privileged Identity Management (PIM)

Les MSP peuvent réduire le nombre de personnes qui disposent d’un accès à un rôle à privilèges élevés pour sécuriser des informations ou des ressources à l’aide de PIM. PIM réduit le risque qu’une personne malveillante accède à des ressources ou que des utilisateurs autorisés affectent par inadvertance une ressource sensible. Les MSP peuvent également accorder aux utilisateurs des rôles à privilèges élevés juste-à-temps pour accéder aux ressources, apporter des modifications importantes et surveiller ce que font les utilisateurs désignés avec leur accès privilégié.

> [!NOTE]
> L’utilisation d’Azure AD PIM nécessite une licence Azure AD Premium P2 dans le locataire partenaire.

Les étapes suivantes élèvent les utilisateurs du locataire partenaire aux rôles de privilèges supérieurs limités dans le temps à l’aide de PIM :

1. Créez un groupe assignable à un rôle, comme décrit dans l’article [Créer un groupe pour l’attribution de rôles dans Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Accédez à [Azure AD – Tous les groupes](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) et ajoutez le nouveau groupe en tant que membre d’un groupe de sécurité pour les rôles à privilèges élevés (par exemple, Administration groupe de sécurité Agents pour DAP ou un groupe de sécurité similairement respectif pour les rôles GDAP).

3. Configurez l’accès privilégié au nouveau groupe, comme décrit dans l’article [Affecter des propriétaires éligibles et des membres pour les groupes d’accès privilégiés](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Pour en savoir plus sur PIM, consultez [Qu’est-ce que Privileged Identity Management ?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Configurer l’accès conditionnel Azure AD basé sur les risques

Les MSP peuvent utiliser l’accès conditionnel basé sur les risques pour s’assurer que leurs membres du personnel prouvent leur identité à l’aide de l’authentification multifacteur et en modifiant leur mot de passe lorsqu’ils sont détectés en tant qu’utilisateur à risque (avec des informations d’identification divulguées ou par renseignement sur les menaces Azure AD). Les utilisateurs doivent également se connecter à partir d’un emplacement familier ou d’un appareil inscrit lorsqu’ils sont détectés comme une connexion risquée. D’autres comportements à risque incluent la connexion à partir d’une adresse IP malveillante ou anonyme ou d’un emplacement de déplacement atypique ou impossible, l’utilisation d’un jeton anormal, l’utilisation d’un mot de passe à partir d’un spray de mot de passe ou l’exposition d’autres comportements de connexion inhabituels. Selon le niveau de risque d’un utilisateur, les MSP peuvent également choisir de bloquer l’accès lors de la connexion. Pour en savoir plus sur les risques, consultez [Qu’est-ce que le risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

> [!NOTE]
> L’accès conditionnel nécessite une licence Azure AD Premium P2 dans le locataire partenaire. Pour configurer l’accès conditionnel, consultez [Configuration de l’accès conditionnel Azure Active Directory](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Contenu associé

[Autorisations de réinitialisation de mot de passe](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (article)\
[Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (article)\
[Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)\
[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Vue d’ensemble de Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)\
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)