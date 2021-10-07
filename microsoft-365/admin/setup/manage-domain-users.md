---
title: Synchroniser les utilisateurs de domaine avec Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Synchronisez les utilisateurs contrôlés par domaine avec Microsoft 365 entreprise.
ms.openlocfilehash: 9b15179a48905e6ab9f8e6a44ebd7a0d62dc2bea
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60153905"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synchroniser les utilisateurs de domaine avec Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Préparer la synchronisation d’annuaires 

Avant de synchroniser vos utilisateurs et ordinateurs à partir du domaine Active Directory local, examinez Préparer la synchronisation d’annuaires [Microsoft 365](../../enterprise/prepare-for-directory-synchronization.md). En particulier :

   - Assurez-vous qu’il n’existe aucun doublon dans votre répertoire pour les attributs suivants : **mail,** **proxyAddresses** et **userPrincipalName**. Ces valeurs doivent être uniques et les doublons doivent être supprimés.
   
   - Nous vous recommandons de configurer l’attribut **userPrincipalName** (UPN) pour chaque compte d’utilisateur local afin qu’il corresponde à l’adresse de messagerie principale correspondant à l’utilisateur Microsoft 365 sous licence. Par exemple : *mary.shelley@contoso.com* au lieu *de mary@contoso.local*
   
   - Si le domaine Active Directory se termine par un suffixe non routable tel que *.local* ou *.lan,* au lieu d’un suffixe routable Internet tel *que .com* ou *.org,* ajustez d’abord le suffixe UPN des comptes d’utilisateurs locaux, comme décrit dans Préparer un domaine [non routable](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md)pour la synchronisation d’annuaires. 

**L’IdFix** d’exécuter à l’étape 4 (4) ci-dessous permet également de s’assurer que votre annuaire Active Directory local est prêt pour la synchronisation d’annuaires.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Installer et configurer Azure AD Connecter

Pour synchroniser vos utilisateurs, groupes et contacts à partir d’Active Directory local dans Azure Active Directory, installez Azure Active Directory Connecter et configurer la synchronisation d’annuaires. 

 1. Dans le centre [d’administration,](https://go.microsoft.com/fwlink/p/?linkid=2024339)sélectionnez **Le programme d’installation** dans le navigation gauche.

 2. Under **Sign-in and security**, choose **View**  under Sync users from **your org’s directory**.

 3. On the **Sync users from your org’s directory** page, choose Get **started**.

 4. Lors de la première étape, exécutez l’outil IdFix pour préparer la synchronisation d’annuaires.

 5. Suivez les étapes de l’Assistant pour télécharger Azure AD Connecter et l’utiliser pour synchroniser vos utilisateurs contrôlés par un domaine avec Microsoft 365.


Voir [Configurer la synchronisation d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md) pour en savoir plus.

Lorsque vous configurez vos options pour Azure AD Connecter, nous vous recommandons d’activer la  synchronisation de mot de **passe,** l’personnalisation transparente et la fonctionnalité d’écriture écriture par mot de passe, qui est également prise en charge dans Microsoft 365 entreprise.

> [!NOTE]
> Il existe quelques étapes supplémentaires pour l’écriture de mot de passe au-delà de la case à cocher dans Azure AD Connecter. Pour plus d’informations, [voir How-to: configure password writeback](/azure/active-directory/authentication/howto-sspr-writeback). 

Si vous souhaitez également gérer les appareils Windows 10 joints à un domaine, voir Activer les appareils Windows 10 joints à un domaine à gérer par [Microsoft 365 Business Premium](manage-windows-devices.md) pour configurer une jointation Azure AD hybride.