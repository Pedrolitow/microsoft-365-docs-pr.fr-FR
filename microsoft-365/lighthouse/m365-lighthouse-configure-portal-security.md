---
title: Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment configurer la sécurité du portail.
ms.openlocfilehash: 8f8ec851d2ce6795565530e120f3704128336ea2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323120"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise

La protection de l’accès aux données client lorsqu’un fournisseur de services gérés (MSP) a délégué des autorisations d’accès à ses clients est une priorité de cybersécurité. Microsoft 365 Lighthouse est disponible avec les fonctionnalités requises et facultatives pour vous aider à configurer la sécurité du portail de portail de portail. Vous devez configurer des rôles spécifiques avec l’authentification multifacteur (MFA) activée avant de pouvoir accéder à l’authentification multifacteur. Vous pouvez éventuellement configurer Azure AD Privileged Identity Management (PIM) et l’accès conditionnel.

## <a name="set-up-multifactor-authentication-mfa"></a>Configurer l’authentification multifacteur (MFA)

Comme mentionné dans le billet de blog [, votre $word n’a pas d’importance](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984) :

> « Votre mot de passe n’a pas d’importance, mais c’est l’fa MFA qui l’est. D’après nos études, votre compte est moins susceptible d’être compromis à plus de 99,9 % si vous utilisez l’mf. »

Lorsque les utilisateurs accèdent à l’mf pour la première fois, ils sont invités à configurer l’mfmf si leur compte Microsoft 365 ne l’a pas déjà configuré. Les utilisateurs ne pourront pas accéder à l’installation de l’ermfa MFA tant que l’étape de configuration requise n’aura pas été terminée. Pour en savoir plus sur les méthodes d’authentification, voir [Configurer votre Microsoft 365 pour l’authentification multifacteur](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Configurer le contrôle d’accès basé sur un rôle

Le contrôle d’accès basé sur un rôle (RBAC) accorde l’accès aux ressources ou aux informations en fonction des rôles utilisateur. L’accès aux données et paramètres du client dans le centre d’informations est limité à des rôles spécifiques du programme fournisseur de solutions Cloud (CSP). Pour configurer des rôles RBAC dans le contrôle d’accès, nous vous recommandons d’utiliser des privilèges d’administration délégués granulaires (GDAP) pour implémenter des affectations granulaires pour les utilisateurs.

Pour commencer à travailler avec GDAP, voir [Configurer des rôles pour gérer les clients](m365-lighthouse-set-up-roles.md).

Les techniciens MSP peuvent également accéder à l’aide de rôles d’agent d’administration ou d’agent du service d’aide via des privilèges d’administration délégués( DAP).

Pour les actions non liées au client dans le domaine de l’intégration (par exemple, l’intégration, la désactivation/réactivation par le client, la gestion des balises, l’examen des journaux), les techniciens MSP doivent avoir un rôle attribué dans le client partenaire. Le lien de l’article précédent détaille ces rôles et leurs autorisations dans le Journal.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Configurer Azure AD Privileged Identity Management (PIM)

Les MSP peuvent réduire le nombre de personnes qui disposent d’un accès à un rôle à privilège élevé pour sécuriser des informations ou des ressources à l’aide de PIM. PIM réduit le risque qu’une personne malveillante accède à des ressources ou à des utilisateurs autorisés par inadvertance, ce qui a un impact sur une ressource sensible. Les MSP peuvent également accorder aux utilisateurs des rôles de privilège élevé juste-à-temps pour accéder aux ressources, apporter des modifications importantes et surveiller ce que les utilisateurs désignés font avec leur accès privilégié. 

> [!NOTE]
> L’Azure AD PIM nécessite une licence Azure AD Premium P2 client partenaire.

Les étapes suivantes élèvent les utilisateurs clients partenaires à des rôles de privilège supérieurs dans le temps à l’aide de PIM :

1. Créez un groupe à attribuer aux rôles, comme décrit dans l’article Créer un groupe pour [l’attribution](/azure/active-directory/roles/groups-create-eligible) de rôles dans Azure Active Directory.

2. Go to [Azure AD – All Groups](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) and add the new group as a member of a security group for high-privilege roles (for example, Admin Agents security group for DAP or a similarly respective security group for GDAP roles).

3. Configurer l’accès privilégié au nouveau groupe comme décrit dans l’article Affecter des propriétaires et des membres éligibles pour [les groupes d’accès privilégiés](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Pour en savoir plus sur PIM, [consultez La Privileged Identity Management ?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Configurer l’accès conditionnel basé sur Azure AD risque

Les MSP peuvent utiliser l’accès conditionnel basé sur les risques pour s’assurer que les membres de leur personnel prouvent leur identité à l’aide de l’ation MFA et en modifiant leur mot de passe lorsqu’ils sont détectés comme utilisateur à risque (avec des informations d’identification divulguées ou des renseignements sur les menaces Azure AD). Les utilisateurs doivent également se connecter à partir d’un emplacement familier ou d’un appareil inscrit lorsqu’ils sont détectés comme étant à risque. Les autres comportements à risque incluent la signature à partir d’une adresse IP malveillante ou anonyme ou d’un lieu de voyage inhabituel ou impossible, l’utilisation d’un jeton anormal, l’utilisation d’un mot de passe à partir d’une pulvérisation de mot de passe ou l’affichage d’un autre comportement inhabituel de se connecter. Selon le niveau de risque d’un utilisateur, les MSP peuvent également choisir de bloquer l’accès lors de la signature. Pour en savoir plus sur les risques, voir [Qu’est-ce qu’un risque ?](/azure/active-directory/identity-protection/concept-identity-protection-risks) 

> [!NOTE]
> L’accès conditionnel nécessite Azure AD Premium P2 licence dans le client partenaire. Pour configurer l’accès conditionnel, voir [Configuring Azure Active Directory Conditional Access](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Contenu associé

[Autorisations de réinitialisation de mot](/azure/active-directory/roles/permissions-reference#password-reset-permissions) de passe (article)\
[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)\
[Vue d’Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)\
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)