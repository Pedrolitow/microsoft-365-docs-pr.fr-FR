---
title: Transférer des utilisateurs vers un autre abonnement
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- manage_licenses
search.appverid: MET150
description: Découvrez comment déplacer des utilisateurs d’un abonnement à l’autre.
ms.date: 05/12/2022
ms.openlocfilehash: 230996448d333076d150a0ff051f268e72d55363
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719445"
---
# <a name="move-users-to-a-different-subscription"></a>Transférer des utilisateurs vers un autre abonnement

Si vous avez plusieurs produits, que vous avez des utilisateurs disposant d’une licence pour un produit, mais que vous souhaitez les déplacer vers un autre produit, vous pouvez remplacer leur licence existante par une autre.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général, une licence ou un administrateur d’utilisateur pour attribuer des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md).

## <a name="move-users-to-a-different-subscription"></a>Transférer des utilisateurs vers un autre abonnement

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Cochez les cases en regard des noms des utilisateurs pour lesquels vous souhaitez remplacer les licences existantes.

3. Dans la partie supérieure, sélectionnez **Gérer des licences de produits**.

4. Dans le volet **Gérer les licences de produit** , sélectionnez **Remplacer**  , puis sélectionnez les licences que vous souhaitez attribuer aux utilisateurs.

5. En bas, sélectionnez **Enregistrer les modifications** \> **Fermer**.

## <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>Sauvegarder les données avant de changer de plan Microsoft 365 pour les entreprises

Si un utilisateur passe à un autre abonnement qui a moins de services liés aux données ou qu’un utilisateur quitte l’organisation, vous pouvez télécharger une copie de ses données stockées dans Microsoft 365 avant de passer au nouvel abonnement.

Si vous déplacez un utilisateur vers un abonnement qui a le même ou plusieurs services, vous n’avez pas besoin de sauvegarder les données utilisateur.
  
### <a name="save-a-copy-of-outlook-information"></a>Enregistrer une copie des informations Outlook

Si les utilisateurs disposent d’Outlook, ils peuvent [exporter ou sauvegarder des e-mails, des contacts et du calendrier dans un fichier .pst Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) avant que leur plan ne soit basculé.
  
Une fois le passage au nouveau plan terminé, les utilisateurs peuvent [importer des e-mails, des contacts et du calendrier à partir d’un fichier .pst Outlook](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
### <a name="save-files-stored-in-onedrive-for-business"></a>Enregistrer les fichiers stockés dans OneDrive Entreprise

Avant de passer à un autre abonnement, les utilisateurs peuvent [télécharger des fichiers et des dossiers à partir de OneDrive ou SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) vers un autre emplacement, tel qu’un dossier sur le disque dur de leur ordinateur ou un partage de fichiers sur le réseau de l’organisation.
  
### <a name="save-yammer-information"></a>Enregistrer les informations Yammer

Les administrateurs peuvent exporter tous les messages, notes, fichiers, rubriques, utilisateurs et groupes vers un fichier .zip. Pour plus d’informations, consultez [Exporter des données à partir de Yammer Entreprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). Les développeurs peuvent également utiliser [l’API Yammer](https://go.microsoft.com/fwlink/p/?linkid=842495) pour ce faire.
  
### <a name="how-to-save-sharepoint-information"></a>Comment enregistrer des informations SharePoint

Si un utilisateur passe d’un abonnement avec SharePoint Online à un abonnement qui ne l’a pas, la vignette **SharePoint** n’apparaît plus dans son menu Microsoft 365.
  
Toutefois, tant que le nouvel abonnement se trouve dans la même organisation que celle à partir de laquelle ils sont transférés, les utilisateurs peuvent toujours accéder au site d’équipe SharePoint. Ils peuvent afficher et mettre à jour des notebooks, des documents, des tâches et des calendriers à l’aide de l’URL directe du site d’équipe.
  
> [!TIP]
> Nous recommandons aux utilisateurs d’accéder au site d’équipe avant le basculement de leur abonnement et d’enregistrer l’URL en tant que favori ou signet dans leur navigateur.
  
Par défaut, l’URL du site web d’équipe se présente sous la forme suivante :
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

où  _\<orgDomain\>_ est l’URL de l’organisation.
  
Par exemple, si le domaine de l’organisation est contoso.onmicrosoft.com, l’URL directe vers le site d’équipe est `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
Bien entendu, les utilisateurs peuvent également télécharger des documents SharePoint Online à partir du site d’équipe SharePoint sur leur ordinateur local ou à un autre emplacement à tout moment.

## <a name="next-steps"></a>Prochaines étapes

Si vous n’envisagez pas de [réaffecter les licences inutilisées à d’autres utilisateurs](../../managed-desktop/get-started/assign-licenses.md), envisagez de [supprimer les licences de votre abonnement](../../commerce/licenses/buy-licenses.md) afin de ne pas payer plus de licences que nécessaire.

## <a name="related-content"></a>Contenu associé

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Supprimer des licences de votre abonnement](../licenses/buy-licenses.md) (article)\
[Modifier les plans manuellement](change-plans-manually.md) (article)\
[Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises](../licenses/subscriptions-and-licenses.md) (article)\
[Acheter un autre abonnement Microsoft 365 pour les entreprises](../try-or-buy-microsoft-365.md) (article)
