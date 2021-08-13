---
title: Définir la stratégie d’expiration des mots de passe pour votre organisation
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: Découvrez comment un administrateur peut définir une stratégie d’expiration des mots de passe pour votre entreprise, votre établissement scolaire ou votre association dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: e33ab836f914f799db4279990f3263120a1f602d94dbc5af9bf796212d7b9cd7
ms.sourcegitcommit: 14a8a80aa85d501d3a77f6cdd3aba6750e6775e5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2021
ms.locfileid: "57834520"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Définir la stratégie d’expiration des mots de passe pour votre organisation

## <a name="before-you-begin"></a>Avant de commencer

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../../business-video/admin-center-overview.md)

En tant qu'administrateur, vous pouvez faire en sorte qu'ils expirent après un certain nombre de jours ou qu'ils n'expirent jamais. Par défaut, les mots de passe sont configurés pour ne jamais expirer dans votre organisation.

Des recherches actuelles indiquent sans équivoque que les changements de mot de passe imposés ne sont pas forcément bénéfiques. Ils poussent les utilisateurs à choisir des mots de passe peu fiables, à réutiliser des mots de passe ou à mettre à jour d'anciens mots de passe de façon qu'ils sont facilement devinables de la part des pirates. Nous vous recommandons d’activer [Authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md). Pour en savoir plus sur la stratégie de mot de passe, vérifiez les [recommandations sur la stratégie de mot de passe ](../misc/password-policy-recommendations.md).

Vous devez être un [Administrateur général](../add-users/about-admin-roles.md) pour procéder à ces étapes.

Si vous êtes un utilisateur, vous n'avez pas les autorisations pour paramétrer votre mot de passe pour qu'il n'expire jamais. Demandez au support technique de votre bureau ou de votre école d'effectuer les opérations de cet article pour vous.

## <a name="set-password-expiration-policy"></a>Définir la stratégie d’expiration de mot de passe

Si vous voulez que les mots de passe utilisateur expirent après un certain temps, suivez la procédure ci-dessous.

1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> **Paramètres de l’organisation**.

2. Accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">Sécurité & confidentialité</a>.
 Si vous n’êtes pas un administrateur général, l’option Sécurité et confidentialité n’est pas visible.
  
3. Sélectionnez **Stratégie d’expiration du mot de passe**.
  
4. Si vous ne voulez pas que les utilisateurs soient contraints de changer de mot de passe, décochez la case à côté de **Définir l’expiration des mots de passe d’utilisateur après un certain nombre de jours**.
  
5. Entrez la fréquence d'expiration des mots de passe. Choisissez un nombre de jours compris entre 14 et 730.
  
6. Dans la seconde zone, indiquez à quel moment les utilisateurs doivent être avisés de l'expiration prochaine du mot de passe, puis sélectionnez **Enregistrer**. Choisissez un nombre de jours compris entre 1 et 30.

> [!NOTE]
> Les notifications d’expiration de mot de passe ne sont plus prises en charge dans le portail Office 365 ou Applications Office à l’exception de Outlook.
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Points importants dont vous devez tenir compte concernant la fonctionnalité d’expiration de mot de passe
  
Les personnes qui utilisent uniquement l’application Outlook ne sont pas obligées de réinitialiser leur mot de passe Microsoft 365 tant que ce dernier n’a pas expiré dans le cache. Cela peut se produire quelques jours après la date d’expiration. Il n’existe aucune solution de contournement à ce problème pour les administrateurs.

## <a name="prevent-last-password-from-being-used-again"></a>Empêcher la réutilisation du dernier mot de passe

Si vous le souhaitez, vous pouvez empêcher vos utilisateurs de recycler d’anciens mots de passe en appliquant l’historique de mot de passe dans Active Directory (AD) local. Voir [Créer une stratégie de mot de passe personnalisée](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

Dans Azure AD, le dernier mot de passe ne peut pas être réutilisé lorsque l’utilisateur modifie un mot de passe. La stratégie de mot de passe est appliquée à tous les comptes d’utilisateurs qui sont créés et gérés directement dans Azure AD. Cette stratégie de mot de passe ne peut pas être modifiée. Consultez [Stratégies de mot de passe Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synchroniser les hachages de mots de passe utilisateur à partir d’une instance Active Directory locale vers une instance Azure AD (Microsoft 365)

Cet article est consacré à la définition de la stratégie d’expiration pour les utilisateurs exclusivement cloud (Azure AD). Il ne s’applique pas aux utilisateurs d’identité hybride utilisant la synchronisation par hachage du mot de passe, l’authentification directe ou la fédération locale telle que ADFS.
  
Pour découvrir comment synchroniser les hachages de mot de passe utilisateur d'Active Directory local avec Azure Active Directory, voir [Implémenter la synchronisation du hachage de mot de passe avec la synchronisation Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Stratégies de mot de passe et restrictions de compte dans Azure Active Directory

Vous pouvez spécifier d’autres stratégies et restrictions de mot de passe dans Azure Active Directory. Consultez [Stratégies de mot de passe et restrictions de compte dans Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) pour en savoir plus.

## <a name="update-password-policy"></a>Mise à jour de la stratégie de mot de passe

L’applet de commande Set-MsolPasswordPolicy met à jour la stratégie de mot de passe d’un domaine ou d’un client spécifié. Deux paramètres sont requis. La premier consiste à indiquer la durée pendant laquelle un mot de passe reste valide avant qu’il ne soit modifié et que le deuxième indique le nombre de jours avant la date d’expiration du mot de passe qui s’affiche lorsque les utilisateurs reçoivent la première notification leur indiquant que leur mot de passe arrive bientôt à expiration.

Si vous souhaitez obtenir plus d’informations sur la mise à jour de la stratégie de mot de passe pour un domaine ou un client spécifique, consultez [Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Contenu connexe

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)\

[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)
