---
title: Définir la stratégie d’expiration des mots de passe pour votre organisation
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier1
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: Découvrez comment un administrateur peut définir une stratégie d’expiration des mots de passe pour votre entreprise, votre établissement scolaire ou votre association dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: a30ff554f1a171d85268252a43554a18db5abd68
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735526"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Définir la stratégie d’expiration des mots de passe pour votre organisation

## <a name="before-you-begin"></a>Avant de commencer

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](/microsoft-365/admin/add-users/about-admin-roles)

As an admin, you can make user passwords expire after a certain number of days, or set passwords to never expire. By default, passwords are set to never expire for your organization.

Des recherches actuelles indiquent sans équivoque que les changements de mot de passe imposés ne sont pas forcément bénéfiques. Ils poussent les utilisateurs à choisir des mots de passe peu fiables, à réutiliser des mots de passe ou à mettre à jour d'anciens mots de passe de façon qu'ils sont facilement devinables de la part des pirates. Nous vous recommandons d’activer [Authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md). Pour en savoir plus sur la stratégie de mot de passe, vérifiez les [recommandations sur la stratégie de mot de passe ](../misc/password-policy-recommendations.md).

Vous devez être un [Administrateur général](../add-users/about-admin-roles.md) pour procéder à ces étapes.

If you're a user, you don't have the permissions to set your password to never expire. Ask your work or school technical support to do the steps in this article for you.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="set-password-expiration-policy"></a>Définir la stratégie d’expiration de mot de passe

Si vous voulez que les mots de passe utilisateur expirent après un certain temps, suivez la procédure ci-dessous.

1. Dans le Centre d’administration Microsoft 365, accédez à l’onglet <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sécurité et confidentialité**</a>.

    Si vous n’êtes pas un administrateur de sécurité ou général, l’option Sécurité et confidentialité n’est pas visible.
  
1. Sélectionnez **Stratégie d’expiration du mot de passe**.
  
1. Si vous ne voulez pas que les utilisateurs aient à modifier les mots de passe, décochez la case en regard de **Définir les mots de passe pour qu’ils n’expirent jamais**.

1. Tapez la fréquence à laquelle les mots de passe doivent expirer. Choisissez un nombre de jours compris entre 14 et 730.
 
> [!IMPORTANT]
> Les notifications d’expiration de mot de passe ne sont plus prises en charge dans les Centre d'administration Microsoft 365 et les applications Office ou les applications web Office.
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Points importants dont vous devez tenir compte concernant la fonctionnalité d’expiration de mot de passe
  
People who only use the Outlook app won't be forced to reset their Microsoft 365 password until it expires in the cache. This can be several days after the actual expiration date. There's no workaround for this at the admin level.

## <a name="prevent-last-password-from-being-used-again"></a>Empêcher la réutilisation du dernier mot de passe

If you want to prevent your users from recycling old passwords, you can do so by enforcing password history in on-premises Active Directory (AD). See [Create a custom password policy](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

Dans Azure AD, le dernier mot de passe ne peut pas être réutilisé lorsque l’utilisateur modifie un mot de passe. La stratégie de mot de passe est appliquée à tous les comptes d’utilisateurs qui sont créés et gérés directement dans Azure AD. Cette stratégie de mot de passe ne peut pas être modifiée. Consultez [Stratégies de mot de passe Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synchroniser les hachages de mots de passe utilisateur à partir d’une instance Active Directory locale vers une instance Azure AD (Microsoft 365)

Cet article est consacré à la définition de la stratégie d’expiration pour les utilisateurs exclusivement cloud (Azure AD). Il ne s’applique pas aux utilisateurs d’identité hybride utilisant la synchronisation par hachage du mot de passe, l’authentification directe ou la fédération locale telle que ADFS.
  
Pour découvrir comment synchroniser les hachages de mot de passe utilisateur d'Active Directory local avec Azure Active Directory, voir [Implémenter la synchronisation du hachage de mot de passe avec la synchronisation Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Stratégies de mot de passe et restrictions de compte dans Azure Active Directory

Vous pouvez spécifier d’autres stratégies et restrictions de mot de passe dans Azure Active Directory. Consultez [Stratégies de mot de passe et restrictions de compte dans Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) pour en savoir plus.

## <a name="update-password-policy"></a>Mise à jour de la stratégie de mot de passe

La cmdlet Set-MsolPasswordPolicy met à jour la stratégie de mot de passe d’un domaine ou d’un client spécifié et indique la durée de validité d’un mot de passe avant qu’il ne soit modifié.

Si vous souhaitez obtenir plus d’informations sur la mise à jour de la stratégie de mot de passe pour un domaine ou un client spécifique, consultez [Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Contenu connexe

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)\

[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)
