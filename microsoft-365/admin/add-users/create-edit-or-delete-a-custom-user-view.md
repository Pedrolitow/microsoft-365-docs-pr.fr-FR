---
title: Créer, modifier ou supprimer une vue utilisateur personnalisée
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 4fe7f6ac-be8e-4b57-9e13-24ff889a4b28
description: Apprenez à utiliser des filtres pour créer, modifier ou supprimer un affichage utilisateur personnalisé dans Microsoft 365.
ms.openlocfilehash: b4177a561d13d76f6d5a0a1077fe8037d469ee48
ms.sourcegitcommit: a6fb731fdf726d7d9fe4232cf69510013f2b54ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52683222"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Créer, modifier ou supprimer une vue utilisateur personnalisée

Si vous êtes un administrateur global ou de gestion des utilisateurs d’un abonnement Microsoft 365 entreprise, vous pouvez créer des affichages utilisateur personnalisés pour afficher un sous-ensemble spécifique d’utilisateurs. Ces affichages s’ajoutent à l’ensemble standard d’affichages. Vous pouvez créer, modifier ou supprimer des affichages utilisateur personnalisés, et les affichages personnalisés que vous créez sont disponibles pour tous les administrateurs.
  
## <a name="custom-user-views-in-the-admin-center"></a>Affichages utilisateur personnalisés dans le Centre d’administration

Lorsque vous créez, modifiez ou supprimez un affichage  utilisateur personnalisé, les modifications s’afficheront dans la liste De filtres que tous les administrateurs de votre entreprise voient lorsqu’ils vont sur la **page** Utilisateurs. Vous pouvez créer jusqu’à 50 affichages personnalisés. 

> [!TIP]
>  Les affichages utilisateur standard sont affichés par défaut dans **la** liste de listes listes des filtres. Les filtres standard incluent tous les utilisateurs, les utilisateurs sous **licence,** les utilisateurs invités, les utilisateurs autorisés à se connecter, les **utilisateurs bloqués,** les utilisateurs sans **licence,** les utilisateurs avec erreur, les **administrateurs** de facturation, les **administrateurs** globaux, les administrateurs du **helpdesk,** les **administrateurs** de service et les administrateurs de gestion des **utilisateurs.** Vous ne pouvez pas modifier ou supprimer des affichages standard. 

Quelques éléments à noter concernant les affichages standard : 

- Certains affichages standard affichent une liste non triée s’il y a plus de 2 000 utilisateurs dans la liste. Pour localiser des utilisateurs spécifiques dans cette liste, utilisez la zone de recherche. 
- Si vous n’avez pas acheté Microsoft 365 microsoft, les administrateurs de facturation n’apparaissent pas dans la liste des **affichages** standard. Pour plus d'informations, consultez la rubrique [Affectation de rôles d'administrateur](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Choisir les filtres pour votre affichage utilisateur personnalisé

Vous pouvez créer et modifier vos affichages personnalisés dans le **volet** Filtre personnalisé. Si vous sélectionnez plusieurs options de filtre, vous obtenez des résultats qui contiennent des utilisateurs qui correspondent à tous les critères sélectionnés. L’exemple suivant vous montre comment créer un affichage personnalisé nommé « Utilisateurs canadien » qui affiche tous les utilisateurs d’un domaine spécifique qui sont au Canada. 

  
 **A - Domaine** Si vous avez plusieurs domaines pour votre organisation, vous pouvez choisir parmi une liste de domaines disponibles. 
  
 **B - État de la signature** Choisissez les utilisateurs autorisés ou bloqués. 
  
 **C - Emplacement** Choisissez un emplacement dans une liste de pays. 
  
 **D - Licence de produit attribuée** Choisissez dans une liste des licences disponibles au niveau de votre organisation. Utilisez ce filtre pour afficher les utilisateurs qui ont la licence que vous avez sélectionnée. Les utilisateurs peuvent également avoir des licences supplémentaires. 
  
Vous pouvez également filtrer en fonction des informations de profil utilisateur supplémentaires utilisées dans votre organisation, telles que le service, la ville, l’état ou la province, le pays ou la région, ou la fonction.
  
 **Autres conditions :**
  
- **Utilisateurs synchronisés uniquement** Activez cette case pour afficher tous les utilisateurs qui ont été synchronisés avec Active Directory local, que les utilisateurs soient activés ou non. 
    
- **Utilisateurs avec erreurs** Sélectionnez cette zone pour afficher les utilisateurs qui peuvent avoir des erreurs d’approvisionnement. 
    
- **Utilisateurs sans permis** Sélectionnez cette case pour rechercher tous les utilisateurs qui n’ont pas reçu de licence. Les résultats de cette vue peuvent également inclure les utilisateurs qui ont une boîte aux lettres Exchange mais qui n’ont pas de licence. Pour suivre ces utilisateurs spécifiquement, utilisez le filtre Utilisateurs sans permis Exchange boîtes aux lettres **ou d’archives.** Les résultats de cette vue peuvent également inclure les utilisateurs qui ont une archive Exchange, mais n’ont pas de licence.
    
- **Utilisateurs sans permis avec des boîtes aux lettres Exchange ou des archives** Sélectionnez cette zone pour afficher les comptes d’utilisateur qui ont été créés dans Exchange Online et qui ont une boîte aux lettres Exchange, mais qui n’ont pas été affectés à Microsoft 365 licence. Les résultats de ce filtre incluent les utilisateurs qui ont ou qui ont été affectés à Exchange archive. 

> [!NOTE]
> Le **filtre des utilisateurs** sans Exchange boîtes aux lettres fonctionne dans les cas ci-après :
1. La boîte aux lettres  a été récemment convertie en utilisateur et **n’a** pas de licence.
2. La boîte aux lettres a été récemment mig Microsoft 365 mais une licence n’a pas été attribuée.
3. La boîte aux lettres a été créée à l’aide de PowerShell et une licence n’a pas été attribuée.
4. Une nouvelle boîte aux lettres qui a été créée en local avec une cmdlet New-RemoteMailbox est mise en service pour l’utilisateur.
    
> [!TIP]
> Si vous créez un affichage personnalisé qui renvoie plus de 2 000 utilisateurs, la liste d’utilisateurs résultante n’est pas triée. Dans ce cas, utilisez la zone de recherche pour rechercher des utilisateurs ou modifiez votre affichage personnalisé pour affiner votre recherche. 
  
## <a name="create-a-custom-user-view"></a>Créer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs.</a>
  
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">actifs.</a> 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs.</a>  

::: moniker-end
    
2. Dans la page **Utilisateurs** actifs, sélectionnez **Filtres** et **Nouveau filtre.**
  
3. Dans la page **Filtre personnalisé,** entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre affichage personnalisé est désormais inclus dans la liste de listes de filtres.

## <a name="edit-or-delete-a-custom-user-view"></a>Modifier ou supprimer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs.</a>

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">actifs.</a> 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, allez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs.</a> 

::: moniker-end 
    
2. Dans la page **Utilisateurs** actifs, **sélectionnez Filtrer,** sélectionnez le filtre à modifier, puis sélectionnez **Modifier le filtre.** 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les affichages personnalisés. 
  
3. Dans la page **Filtre personnalisé,** modifiez les informations selon vos besoins, puis sélectionnez **Enregistrer.** Ou, pour supprimer le filtre, en bas de la page, sélectionnez **Supprimer**. 

## <a name="related-content"></a>Contenu associé

[Vue d’ensemble Microsoft 365 centre d’administration de l’utilisateur](../../business-video/admin-center-overview.md) (vidéo)\
[À propos des rôles d’administrateur](../add-users/about-admin-roles.md) (vidéo)\
[Personnaliser le thème Microsoft 365 pour votre organisation](../setup/customize-your-organization-theme.md) (article)


     