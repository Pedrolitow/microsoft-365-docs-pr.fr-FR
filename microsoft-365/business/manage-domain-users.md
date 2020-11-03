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
description: Synchroniser les utilisateurs contrôlés par le domaine avec Microsoft 365 pour les entreprises.
ms.openlocfilehash: b40a995a1723808d2fd171c534e9131a891840ba
ms.sourcegitcommit: e56894917d2aae05705c3b9447388d10e2156183
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48841356"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synchroniser les utilisateurs de domaine avec Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. préparer la synchronisation d’annuaires 

Avant de synchroniser vos utilisateurs et ordinateurs à partir du domaine Active Directory local, consultez la [préparation de la synchronisation d’annuaires avec Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/prepare-for-directory-synchronization). En particulier :

   - Assurez-vous qu’il n’existe pas de doublons dans votre répertoire pour les attributs suivants : **mail** , **proxyAddresses** et **userPrincipalName** . Ces valeurs doivent être uniques et les doublons doivent être supprimés.
   
   - Nous vous recommandons de configurer l’attribut **userPrincipalName** (UPN) de chaque compte d’utilisateur local de sorte qu’il corresponde à l’adresse de messagerie principale correspondant à l’utilisateur Microsoft 365 sous licence. Par exemple : *Mary.Shelley@contoso.com* plutôt que *Mary@contoso. local*
   
   - Si le domaine Active Directory se termine par un suffixe non routable comme *. local* ou *. LAN* , au lieu d’un suffixe routable Internet tel que *. com* ou *. org* , ajustez d’abord le suffixe UPN des comptes d’utilisateurs locaux comme décrit dans [Prepare a non routable domain for Directory Synchronization](https://docs.microsoft.com/microsoft-365/enterprise/prepare-a-non-routable-domain-for-directory-synchronization). 

Le **IdFix exécuter** à l’étape quatre (4) ci-dessous permet de s’assurer que votre annuaire Active Directory local est prêt pour la synchronisation d’annuaires.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. installer et configurer Azure AD Connect

Pour synchroniser vos utilisateurs, groupes et contacts à partir de l’Active Directory local avec Azure Active Directory, installez Azure Active Directory Connect et configurez la synchronisation d’annuaires. 

 1. Dans le [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=2024339), sélectionnez **configuration** dans le volet de navigation de gauche.

 2. Sous **connexion et sécurité** , choisissez **affichage**  sous **synchroniser les utilisateurs dans le répertoire de votre organisation** .

 3. Sur la page **synchroniser les utilisateurs à partir de l’annuaire de votre organisation** , sélectionnez **prise en main** .

 4. Dans la première étape, exécutez l’outil IdFix pour préparer la synchronisation d’annuaires.

 5. Suivez les étapes de l’Assistant pour télécharger Azure AD Connect et utilisez-le pour synchroniser vos utilisateurs sous contrôle de domaine avec Microsoft 365.


Pour plus d’informations, reportez-vous à la rubrique [configurer la synchronisation d’annuaires pour Microsoft 365](https://docs.microsoft.com/microsoft-365/enterprise/set-up-directory-synchronization) .

Lorsque vous configurez vos options pour Azure AD Connect, nous vous recommandons d’activer la **synchronisation de mot de passe** , l' **authentification unique transparente** et la fonctionnalité d' **écriture différée de mot de passe** , qui est également prise en charge dans Microsoft 365 pour les entreprises.

> [!NOTE]
> Il existe quelques étapes supplémentaires pour l’écriture différée de mot de passe au-delà de la case à cocher dans Azure AD Connect. Pour plus d’informations, voir [procédure : configurer l’écriture différée de mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-writeback). 

Si vous souhaitez également gérer les appareils Windows 10 associés à un domaine, consultez la rubrique [Enable Domain-Joining Domain 10 Devices to be Managed Microsoft 365 Business Premium](manage-windows-devices.md) pour configurer une participation hybride Azure ad. 