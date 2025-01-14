---
title: Attribuer des rôles d’administrateur au Centre d'administration Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- okr_smb
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: eac4d046-1afd-4f1a-85fc-8219c79e1504
description: Découvrez comment attribuer des rôles d’administrateur à un utilisateur ou plusieurs utilisateurs de votre entreprise afin qu’ils puissent effectuer des tâches spécifiques dans le centre d’administration.
ms.openlocfilehash: 51dfca82e4e11d57f3c70e2a821ab5deaba8bb08
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722063"
---
# <a name="assign-admin-roles-in-the-microsoft-365-admin-center"></a>Attribuer des rôles d’administrateur dans le Centre d'administration Microsoft 365

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Si vous êtes la personne qui a acheté votre abonnement Microsoft Business, vous êtes l’administrateur général. Cela signifie que vous disposez d’un contrôle illimité sur les produits de vos abonnements et que vous pouvez accéder à la plupart des données.

Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](about-admin-roles.md).

Lorsque vous ajoutez de nouveaux utilisateurs, si vous ne leur attribuez pas de rôle d’administrateur, ils sont dans le *rôle d’utilisateur* et n’ont pas de privilèges d’administrateur sur l’un des centres d’administration Microsoft. Toutefois, si vous avez besoin d’aide, vous pouvez attribuer un rôle d’administrateur à un utilisateur. Par exemple, si vous avez besoin d’une personne pour réinitialiser les mots de passe, vous ne devez pas lui attribuer le rôle d’administrateur général, mais lui attribuer le rôle d’administrateur de mot de passe. Le fait d’avoir un trop grand nombre d’administrateurs généraux, avec un accès illimité à vos données et à votre entreprise en ligne, constitue un risque pour la sécurité.

## <a name="watch-add-an-admin"></a>Regarder : Ajouter un administrateur

Regardez cette vidéo et d’autres encore sont disponibles sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198030).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfO] 

1. Lorsque vous vous inscrivez à Microsoft 365 Business, vous devenez automatiquement administrateur général. Pour faciliter la gestion de l’entreprise, vous pouvez également faire d’autres personnes des administrateurs. 
1. Dans la Centre d'administration Microsoft 365, sélectionnez **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.
1. Choisissez l’utilisateur que vous souhaitez désigner comme administrateur, puis sélectionnez **Gérer les rôles**.

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="assign-admin-roles"></a>Attribuer des rôles d’administrateur 

Vous pouvez attribuer des utilisateurs à un rôle de deux manières différentes :

- Vous pouvez accéder aux détails de l’utilisateur et **Gérer les rôles** pour attribuer un rôle à l’utilisateur.
- Vous pouvez également accéder à **Rôles** et sélectionner le rôle, puis y ajouter plusieurs utilisateurs.

### <a name="assign-admin-roles-to-users-using-roles"></a>Attribuer des rôles d’administrateur aux utilisateurs à l’aide de rôles

1. Dans le centre d’administration, accédez à <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Attributions de rôles**</a>. Choisissez les onglets **Azure AD** ou **Intune** pour afficher les rôles d’administrateur disponibles pour votre organisation.
2. Sélectionnez le rôle d’administrateur auquel vous souhaitez affecter l’utilisateur.
3. Sélectionnez **Administrateurs affectés** > **Ajouter**.
4. Tapez le **nom d’affichage** ou le **nom d’utilisateur** de l’utilisateur, puis sélectionnez l’utilisateur dans la liste des suggestions.
5. Ajoutez plusieurs utilisateurs jusqu’à ce que vous ayez terminé.
6. Sélectionnez **Enregistrer**, puis l’utilisateur sera ajouté à la liste des administrateurs affectés.

### <a name="assign-a-user-to-an-admin-role-from-active-users"></a>Attribuer un rôle d’administrateur à un utilisateur via l’option Utilisateurs actifs

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Utilisateurs** > [utilisateurs actifs](https://go.microsoft.com/fwlink/p/?linkid=834822) .

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Dans la page **Utilisateurs** actifs, sélectionnez l’utilisateur dont vous souhaitez modifier le rôle d’administrateur. Dans le volet volant, sous **Rôles**, **sélectionnez Gérer les rôles**.

3. Sélectionnez le rôle d’administrateur que vous voulez attribuer à l’utilisateur. Si vous ne voyez pas le rôle que vous recherchez, sélectionnez **Afficher tout** en bas de la liste.

## <a name="assign-admin-roles-to-multiple-users"></a>Attribuer des rôles d'administrateur à plusieurs utilisateurs

Si vous connaissez PowerShell, consultez [Attribuer des rôles à des comptes d’utilisateur avec PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md). Cet environnement est idéal pour attribuer des rôles à des centaines d'utilisateurs.
  
Utilisez les instructions suivantes pour attribuer des rôles à des dizaines d'utilisateurs.

## <a name="check-admin-roles-in-your-organization"></a>Vérifier les rôles d’administrateur dans votre organisation

Vous ne disposez peut-être pas des autorisations appropriées pour attribuer des rôles d’administrateur à d’autres utilisateurs. Vérifiez que vous disposez des autorisations appropriées ou demandez à un autre administrateur de vous attribuer des rôles.

Vous pouvez vérifier les autorisations de rôle d’administrateur de 2 façons différentes :

- Vous pouvez accéder aux détails de l’utilisateur et regarder sous **Rôles** dans la page **Compte** .
- Vous pouvez également accéder à **Rôles** et sélectionner le rôle d’administrateur, puis sélectionner administrateurs attribués pour voir quels utilisateurs sont affectés.

## <a name="related-content"></a>Contenu associé

[À propos des rôles d’administrateur Microsoft 365](about-admin-roles.md) (article)\
[Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference) (article)\
[Attribuer des rôles à des comptes d’utilisateur avec PowerShell](../../enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell.md) (article)\
[Autoriser ou supprimer des relations de partenaires](../misc/add-partner.md) (article)