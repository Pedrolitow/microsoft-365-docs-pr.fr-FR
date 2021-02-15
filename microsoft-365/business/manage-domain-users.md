---
title: Synchroniser les utilisateurs de domaine avec Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: M365-subscription-management
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
description: Synchronisez les utilisateurs contrôlés par un domaine avec Microsoft 365 pour les entreprises.
ms.openlocfilehash: b40a995a1723808d2fd171c534e9131a891840ba
ms.sourcegitcommit: e56894917d2aae05705c3b9447388d10e2156183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48841356"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synchroniser les utilisateurs de domaine avec Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Préparer la synchronisation d’annuaires 

Avant de synchroniser vos utilisateurs et ordinateurs à partir du domaine Active Directory local, voir Préparer la synchronisation d’annuaires [avec Microsoft 365.](https://docs.microsoft.com/microsoft-365/enterprise/prepare-for-directory-synchronization) En particulier :

   - Assurez-vous qu’il n’existe aucun doublon dans votre répertoire pour les attributs suivants : **mail,** **proxyAddresses** et **userPrincipalName**. Ces valeurs doivent être uniques et les doublons doivent être supprimés.
   
   - Nous vous recommandons de configurer l’attribut **userPrincipalName** (UPN) pour chaque compte d’utilisateur local afin qu’il corresponde à l’adresse de messagerie principale correspondant à l’utilisateur Sous licence Microsoft 365. Par exemple : *mary.shelley@contoso.com* au lieu *de mary@contoso.local*
   
   - Si le domaine Active Directory se termine par un suffixe non routable tel que *.local* ou *.lan,* au lieu d’un suffixe routable Internet tel *que .com* ou *.org,* ajustez d’abord le suffixe UPN des comptes d’utilisateurs locaux comme décrit dans Préparer un domaine [non routable](https://docs.microsoft.com/microsoft-365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization)pour la synchronisation d’annuaires. 

**L’IdFix** d’exécuter à l’étape quatre (4) ci-dessous permet également de s’assurer que votre annuaire Active Directory local est prêt pour la synchronisation d’annuaires.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Installer et configurer Azure AD Connect

Pour synchroniser vos utilisateurs, groupes et contacts à partir d’Active Directory local dans Azure Active Directory, installez Azure Active Directory Connect et installez la synchronisation d’annuaires. 

 1. Dans le centre [d’administration,](https://go.microsoft.com/fwlink/p/?linkid=2024339)sélectionnez **Le programme d’installation** dans le navigation gauche.

 2. Under **Sign-in and security**, choose **View**  under Sync users from **your org’s directory**.

 3. On the **Sync users from your org’s directory** page, choose Get **started**.

 4. Lors de la première étape, exécutez l’outil IdFix pour préparer la synchronisation d’annuaires.

 5. Suivez les étapes de l’Assistant pour télécharger Azure AD Connect et l’utiliser pour synchroniser vos utilisateurs contrôlés par un domaine avec Microsoft 365.


Pour en savoir plus, voir Configurer la synchronisation d’annuaires [pour Microsoft 365.](https://docs.microsoft.com/microsoft-365/enterprise/set-up-directory-synchronization)

Lorsque vous configurez vos options pour Azure AD Connect, nous vous recommandons d’activer la synchronisation de mot de **passe,** l’personnalisation transparente et la fonctionnalité d’écriture sur écriture automatique du mot de passe, qui est également prise en charge dans Microsoft 365 pour les entreprises. 

> [!NOTE]
> Il existe quelques étapes supplémentaires pour l’écriture de mot de passe au-delà de la case à cocher dans Azure AD Connect. Pour plus d’informations, [voir How-to: configure password writeback](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). 

Si vous souhaitez également gérer les appareils Windows 10 joints à un domaine, voir Activer les appareils Windows 10 joints à un domaine à gérer par [Microsoft 365 Business Premium](manage-windows-devices.md) pour configurer une jointation Azure AD hybride. 