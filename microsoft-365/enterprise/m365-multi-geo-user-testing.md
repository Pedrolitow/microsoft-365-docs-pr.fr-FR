---
title: Test utilisateur dans multigéographique
description: En savoir plus sur les tests utilisateur dans multigéographique
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.reviewer: dmwmsft
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: c150743b97e31e06ca1107dd3e5669b5296ad67c
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805357"
---
# <a name="user-testing-in-multi-geo"></a>Test utilisateur dans multigéographique

Deux types d’objets utilisateur sont disponibles dans Azure Active Directory (Azure AD) : les utilisateurs cloud uniquement et les utilisateurs synchronisés. Suivez les instructions appropriées pour votre type d’utilisateur.

>[!TIP]
>Nous vous recommandons de commencer les validations avec un utilisateur de test ou un petit groupe d’utilisateurs avant de déployer à plus grande échelle les fonctionnalités multigéographiques dans votre organisation.

## <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Synchroniser l’emplacement des données par défaut de l’utilisateur à l’aide d’Azure AD Connect

Si les utilisateurs de votre entreprise sont synchronisés à partir d’un système Active Directory local avec Azure AD, leur PreferredDataLocation doit être renseigné dans AD et synchronisé avec Azure AD.

Suivez le processus de <a href="/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation" target="_blank">Azure Active Directory Connect Sync : configurer l’emplacement de données par défaut pour les ressources Microsoft 365</a> pour configurer la synchronisation de l’emplacement des données par défaut à partir de vos services de domaine Active Directory (AD DS) locaux vers Azure AD.

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

>[!IMPORTANT]
>Pour les nouveaux utilisateurs sans OneDrive provisionné, attribuez une licence au compte et attendez au moins 48 heures après la synchronisation du PDL d’un utilisateur avec Azure AD pour que les modifications se propagent avant que l’utilisateur ne se connecte à OneDrive Entreprise. (Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)

## <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configurer l’emplacement des données par défaut pour les utilisateurs cloud uniquement

Si les utilisateurs de votre entreprise ne sont pas synchronisés à partir d’un système Active Directory local avec Azure AD, ce qui signifie qu'ils sont créés dans Microsoft 365 ou Azure AD, alors la PDL doit être définie à l'aide du module Microsoft Azure Active Directory pour Windows PowerShell.

Les procédures de cette section nécessitent le <a href="https://www.powershellgallery.com/packages/MSOnline/1.1.166.0" target="_blank">module Microsoft Azure Active Directory pour le module PowerShell de Windows</a>. Si ce module est déjà installé, assurez-vous que vous effectuez une mise à jour vers la dernière version.

[Connectez-vous et connectez-vous](connect-to-microsoft-365-powershell.md) avec un ensemble d’informations d’identification d’administrateur général pour votre _locataire_.

Utilisez l’applet de commande [Set-MsolUser](/powershell/module/msonline/set-msoluser) pour définir l’emplacement de données par défaut pour chacun de vos utilisateurs. Par exemple :

```PowerShell
Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
```

Vous pouvez vérifier que l’emplacement de données préféré a été correctement mis à jour à l’aide de l’applet de commande Get-MsolUser. Par exemple :

```PowerShell
Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com.PreferredDatalocation
```

Nous vous recommandons d’inclure la configuration de l’emplacement des données par défaut de l’utilisateur dans le cadre de votre flux de travail de création utilisateur standard.

>[!IMPORTANT]
>ou de nouveaux utilisateurs sans OneDrive provisionné, attribuez une licence au compte et attendez au moins 48 heures après la définition du PDL d’un utilisateur pour que les modifications se propagent avant que l’utilisateur ne se connecte à OneDrive. (Configurer l’emplacement des données par défaut avant que l’utilisateur ne se connecte pour approvisionner son OneDrive Entreprise permet de s’assurer que le nouveau OneDrive de l’utilisateur est approvisionné à l’emplacement approprié.)

## <a name="onedrive-for-business-provisioning-and-the-effect-of-pdl"></a>OneDrive Entreprise provisionnement et l’effet de pdl

Si l’utilisateur a déjà un site OneDrive Entreprise créé dans le _locataire_, la définition de son PDL ne déplacera pas automatiquement son OneDrive existant. Pour déplacer le OneDrive d’un utilisateur, consultez [OneDrive Entreprise déplacement géographique](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online déplace automatiquement la boîte aux lettres de l’utilisateur si le PLD change et que mailboxRegion ne correspond plus au code emplacement géographique de la base de lettres. Pour plus d’informations, consultez [Administration de boîtes aux lettres Exchange Online dans un environnement multigéographique](administering-exchange-online-multi-geo.md).

Si l’utilisateur n’a pas de site OneDrive Entreprise dans le _locataire_, OneDrive Entreprise seront provisionnés pour lui conformément à sa valeur PDL, en supposant que la PDL de l’utilisateur correspond à l’un des emplacements satellites de l’entreprise.
