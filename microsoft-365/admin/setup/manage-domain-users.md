---
title: Synchroniser les utilisateurs de domaine avec Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: Synchronisez les utilisateurs contrôlés par un domaine avec Microsoft 365 pour les entreprises.
ms.openlocfilehash: d3a797f1de079108e58194f731d51b089f3d6c23
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727650"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>Synchroniser les utilisateurs de domaine avec Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. Préparer la synchronisation d’annuaires 

Avant de synchroniser vos utilisateurs et ordinateurs à partir du domaine Active Directory local, consultez [Préparer la synchronisation d’annuaires vers Microsoft 365](../../enterprise/prepare-for-directory-synchronization.md). En particulier :

   - Assurez-vous qu’il n’existe aucun doublon dans votre répertoire pour les attributs suivants : **mail**, **proxyAddresses** et **userPrincipalName**. Ces valeurs doivent être uniques et tous les doublons doivent être supprimés.
   
   - Nous vous recommandons de configurer **l’attribut userPrincipalName** (UPN) pour chaque compte d’utilisateur local pour qu’il corresponde à l’adresse e-mail principale qui correspond à l’utilisateur Microsoft 365 sous licence. Par exemple : *mary.shelley@contoso.com* plutôt *qu’mary@contoso.local*
   
   - Si le domaine Active Directory se termine par un suffixe non routable comme *.local* ou *.lan*, au lieu d’un suffixe routable Internet tel que *.com* ou *.org*, ajustez d’abord le suffixe UPN des comptes d’utilisateur locaux, comme décrit dans [Préparer un domaine non routable pour la synchronisation d’annuaires](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md). 

**Le paramètre Run IdFix** à l’étape 4 (4) ci-dessous garantit également que votre Active Directory local est prêt pour la synchronisation d’annuaires.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. Installer et configurer Azure AD Connect

Pour synchroniser vos utilisateurs, groupes et contacts de l’Active Directory local vers Azure Active Directory, installez Azure Active Directory Connect et configurez la synchronisation d’annuaires. 

 1. Dans le [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=2024339), sélectionnez **Configurer** dans la navigation de gauche.

 2. Sous **Connexion et sécurité**, sélectionnez **Ajouter ou synchroniser des utilisateurs avec votre compte Microsoft**.

 3. Dans la page **Ajouter ou synchroniser des utilisateurs à votre compte Microsoft** , choisissez **Prise en main**.

 4. Dans la première étape, exécutez l’outil IdFix pour préparer la synchronisation d’annuaires.

 5. Suivez les étapes de l’Assistant pour télécharger Azure AD Connect et l’utiliser pour synchroniser vos utilisateurs contrôlés par domaine avec Microsoft 365.


Pour en savoir plus, consultez [Configurer la synchronisation d’annuaires pour Microsoft 365](../../enterprise/set-up-directory-synchronization.md) .

Lorsque vous configurez vos options pour Azure AD Connect, nous vous recommandons d’activer **la synchronisation de mot de passe**, **l’authentification unique transparente** et la fonctionnalité de **réécriture du mot de passe** , qui est également prise en charge dans Microsoft 365 pour les entreprises.

> [!NOTE]
> Il existe des étapes supplémentaires pour la réécriture du mot de passe au-delà de la case à cocher dans Azure AD Connect. Pour plus d’informations, consultez [Guide pratique : configurer la réécriture du mot de passe](/azure/active-directory/authentication/howto-sspr-writeback). 

Si vous souhaitez également gérer des appareils Windows 10 joints à un domaine, consultez [Activer la gestion des appareils Windows 10 de domaine par Microsoft 365 Business Premium](../../business-premium/m365bp-manage-windows-devices.md) pour configurer une jonction Azure AD hybride.
