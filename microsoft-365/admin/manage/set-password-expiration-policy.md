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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: "Découvrez comment configurer une stratégie d'expiration des mots de passe pour votre organisation dans le Centre d'administration Microsoft 365. "
ms.openlocfilehash: dd925ee3a5d2aadb07dceed5a0e896e77921e2a1
ms.sourcegitcommit: b6c4b514b2cb6739af949780d7e2a5a5c8dcc161
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "43901009"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Définir la stratégie d’expiration des mots de passe pour votre organisation

Cet article s’adresse aux personnes responsables de la stratégie d’expiration des mots de passe au sein d’une entreprise, d’une école ou d’une association.  

Si vous êtes un utilisateur, vous ne disposez pas de l'autorisation pour paramétrer votre mot de passe afin qu'il reste valide dans le temps. Demandez au support technique de votre bureau ou de votre école d’effectuer les opérations indiquées dans cet article pour vous.

En tant qu'administrateur, vous pouvez faire en sorte qu'ils expirent après un certain nombre de jours ou qu'ils n'expirent jamais. 

> [!Tip]
> Par défaut, les mots de passe sont définis pour expirer après 90 jours. Des recherches actuelles indiquent sans équivoque que les changements de mot de passe imposés ne sont pas forcément bénéfiques. Ils poussent les utilisateurs à choisir des mots de passe peu fiables, à réutiliser des mots de passe ou à mettre à jour d'anciens mots de passe de façon qu'ils sont facilement devinables de la part des pirates. Si le mot de passe est paramétré de façon à ce qu'il n’expire jamais, nous vous recommandons d’activer [l'authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md)d’authentification.

Si vous voulez que les mots de passe utilisateur expirent après un certain temps, suivez la procédure ci-dessous.
> [!IMPORTANT]
> Seuls les [administrateurs généraux](../add-users/about-admin-roles.md) peuvent effectuer ces étapes.
  
1. Dans le centre d’administration, cliquez sur la page **Paramètres** \> **Paramètres**.

2. Accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">Sécurité & confidentialité</a>.
 Si vous n’êtes pas un administrateur général, l’option Sécurité et confidentialité n’est pas visible.
  
3. Sélectionnez **Stratégie d’expiration du mot de passe**.
  
4. Si vous ne souhaitez pas que les utilisateurs soient contraints de changer leur mot de passe, activez la case à cocher près de **Configurer les mots de passe utilisateur pour qu’ils expirent après un certain nombre de jours**.
  
5. Tapez la fréquence à laquelle les mots de passe doivent expirer. Choisissez un nombre de jours compris entre 14 et 730.
  
6. Dans la seconde zone, indiquez à quel moment les utilisateurs doivent être avisés de l'expiration prochaine du mot de passe, puis sélectionnez **Enregistrer**. Choisissez un nombre de jours compris entre 1 et 30.
    
7. Lorsque le mot de passe de l’utilisateur expire, ce dernier reçoit une notification qui s’affiche dans le coin inférieur droit de l’écran.
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Points importants dont vous devez tenir compte concernant la fonctionnalité d’expiration de mot de passe

Voici quelques points dont vous devez tenir compte concernant le fonctionnement actuel de cette fonctionnalité à compter du mois de janvier 2018 :
  
- Les personnes qui utilisent uniquement l’application Outlook ne sont pas obligées de réinitialiser leur mot de passe Microsoft 365 tant que ce dernier n’a pas expiré dans le cache. Cela peut se produire quelques jours après la date d’expiration. Il n’existe aucune solution de contournement à ce problème pour les administrateurs.
    
- Les utilisateurs ne reçoivent pas de notification par courrier indiquant que leur mot de passe expire dans X jours. Voulez-vous utiliser cette fonctionnalité ? **[Votez ici !](https://office365.uservoice.com/forums/273493-office-365-admin/suggestions/15028344-office-365-password-email-notification)**
    
## <a name="prevent-last-password-from-being-used-again"></a>Empêcher la réutilisation du dernier mot de passe

Si vous le souhaitez, vous pouvez empêcher vos utilisateurs de recycler d’anciens mots de passe à partir d’Azure Active Directory. Voir [Appliquer l'historique des mots de passe](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/enforce-password-history).

De plus, si un employé a utilisé un appareil mobile pour accéder à Microsoft 365, vous pouvez réinitialiser le mot de passe afin de vous assurer qu’il n’est plus stocké et recyclé à partir de cet emplacement. Pour plus d'informations, voir [Réinitialiser et bloquer l’appareil mobile d’un ancien employé](https://docs.microsoft.com/office365/admin/add-users/remove-former-employee?view=o365-worldwide#wipe-and-block-a-former-employees-mobile-device).


## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synchroniser les hachages de mots de passe utilisateur à partir d’une instance Active Directory locale vers une instance Azure AD (Microsoft 365)

Cet article est consacré à la définition de la stratégie d’expiration pour les utilisateurs exclusivement cloud (Azure AD). Il ne s’applique pas aux utilisateurs d’identité hybride utilisant la synchronisation par hachage du mot de passe, l’authentification directe ou la Fédération locale telle que ADFS.
  
Pour découvrir comment synchroniser les hachages de mot de passe utilisateur d'Active Directory local avec Azure Active Directory, voir [Implémenter la synchronisation du hachage de mot de passe avec la synchronisation Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).
