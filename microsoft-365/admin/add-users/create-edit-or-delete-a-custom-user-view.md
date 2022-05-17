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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 4fe7f6ac-be8e-4b57-9e13-24ff889a4b28
description: Si vous êtes administrateur général ou de gestion des utilisateurs d’un abonnement Microsoft 365 pour les entreprises, vous pouvez utiliser des filtres pour créer, modifier ou supprimer un affichage utilisateur personnalisé.
ms.openlocfilehash: d90d324690d153fa708dbe7c36a9f41d349f8588
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436732"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Créer, modifier ou supprimer une vue utilisateur personnalisée

Si vous êtes administrateur général ou de gestion des utilisateurs d’un abonnement Microsoft 365 entreprise, vous pouvez créer des vues utilisateur personnalisées pour afficher un sous-ensemble spécifique d’utilisateurs. Ces vues s’ajoutent à l’ensemble standard de vues. Vous pouvez créer, modifier ou supprimer des vues utilisateur personnalisées, et les vues personnalisées que vous créez sont disponibles pour tous les administrateurs.
  
## <a name="custom-user-views-in-the-admin-center"></a>Vues utilisateur personnalisées dans le centre d’administration

Lorsque vous créez, modifiez ou supprimez un affichage utilisateur personnalisé, les modifications s’affichent dans la liste **Filtre** que tous les administrateurs de votre entreprise voient lorsqu’ils accèdent à la page **Utilisateurs** . Vous pouvez créer jusqu’à 50 vues personnalisées. 

> [!TIP]
>  Les vues utilisateur standard sont affichées par défaut dans la liste déroulante **Filtres** . Les filtres standard incluent **tous les utilisateurs**, **utilisateurs sous licence**, **utilisateurs invités**,  **connexion autorisée**, **connexion bloquée**, **utilisateurs sans licence**, **utilisateurs avec erreurs**, **administrateurs de facturation**, **administrateurs généraux**, **administrateurs du support** technique, **administrateurs de service** et **administrateurs de gestion des utilisateurs**. Vous ne pouvez pas modifier ou supprimer des vues standard. 

Quelques points à noter sur les vues standard : 

- Certaines vues standard affichent une liste non triée s’il y a plus de 2 000 utilisateurs dans la liste. Pour localiser des utilisateurs spécifiques dans cette liste, utilisez la zone de recherche. 
- Si vous n’avez pas acheté Microsoft 365 auprès de Microsoft, **les administrateurs de facturation** n’apparaissent pas dans la liste des affichages standard. Pour plus d'informations, consultez la rubrique [Affectation de rôles d'administrateur](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Choisir les filtres de votre affichage utilisateur personnalisé

Vous pouvez créer et modifier vos vues personnalisées dans le volet **Filtre personnalisé** . Si vous sélectionnez plusieurs options de filtre, vous obtenez des résultats qui contiennent des utilisateurs qui correspondent à tous les critères sélectionnés. L’exemple suivant vous montre comment créer une vue personnalisée nommée « Utilisateurs canadiens » qui montre tous les utilisateurs d’un domaine spécifique qui se trouvent au Canada. 

  
 **A - Domaine** Si vous disposez de plusieurs domaines pour votre organisation, vous pouvez choisir parmi une liste déroulante des domaines disponibles. 
  
 **B - État de connexion** Choisissez les utilisateurs autorisés ou bloqués. 
  
 **C - Emplacement** Choisissez un emplacement dans une liste déroulante de pays. 
  
 **D - Licence de produit affectée** Choisissez parmi une liste déroulante de licences disponibles dans votre organisation. Utilisez ce filtre pour afficher les utilisateurs auxquels la licence que vous avez sélectionnée leur a été attribuée. Les utilisateurs peuvent également avoir des licences supplémentaires. 
  
Vous pouvez également filtrer en fonction des détails de profil utilisateur supplémentaires utilisés dans votre organisation, tels que le département, la ville, l’état ou la province, le pays ou la région, ou le titre du travail.
  
 **Autres conditions :**
  
- **Utilisateurs synchronisés uniquement** Sélectionnez cette zone pour afficher tous les utilisateurs qui ont été synchronisés avec l’Active Directory local, que les utilisateurs aient été activés ou non. 
    
- **Utilisateurs avec des erreurs** Sélectionnez cette zone pour afficher les utilisateurs susceptibles d’avoir des erreurs d’approvisionnement. 
    
- **Utilisateurs sans licence** Sélectionnez cette zone pour rechercher tous les utilisateurs qui n’ont pas reçu de licence. Les résultats de cette vue peuvent également inclure des utilisateurs qui ont une boîte aux lettres Exchange, mais qui n’ont pas de licence. Pour suivre ces utilisateurs spécifiquement, utilisez le filtre **Utilisateurs sans licence avec Exchange boîtes aux lettres ou archives**. Les résultats de cette vue peuvent également inclure des utilisateurs qui disposent d’une archive Exchange, mais qui n’ont pas de licence.
    
- **Utilisateurs sans licence avec Exchange boîtes aux lettres ou archives** Sélectionnez cette zone pour afficher les comptes d’utilisateur qui ont été créés dans Exchange Online et qui ont une boîte aux lettres Exchange, mais qui n’ont pas reçu de licence Microsoft 365. Les résultats de ce filtre incluent les utilisateurs qui ont ou qui ont reçu une archive Exchange. 

> [!NOTE]
> Le filtre **des utilisateurs sans licence avec Exchange boîtes aux lettres** fonctionne quand :
1. La boîte aux lettres a été récemment convertie de **partagé** en **utilisateur** et n’a pas de licence.
2. La boîte aux lettres a été récemment migrée vers Microsoft 365, mais aucune licence n’a été attribuée.
3. La boîte aux lettres a été créée à l’aide de PowerShell et aucune licence n’a été attribuée.
4. Une nouvelle boîte aux lettres créée localement avec une applet de commande New-RemoteMailbox est provisionnée pour l’utilisateur.
    
> [!TIP]
> Si vous créez une vue personnalisée qui retourne plus de 2 000 utilisateurs, la liste d’utilisateurs obtenue n’est pas triée. Dans ce cas, utilisez la zone de recherche pour rechercher des utilisateurs ou modifiez votre vue personnalisée pour affiner votre recherche. 
  
## <a name="create-a-custom-user-view"></a>Créer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs</a>.  

::: moniker-end
    
2. Dans la page **Utilisateurs actifs** , sélectionnez **Filtres** , puis **Nouveau filtre**.
  
3. Dans la page **Filtre personnalisé** , entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre vue personnalisée est désormais incluse dans la liste déroulante des filtres.

## <a name="edit-or-delete-a-custom-user-view"></a>Modifier ou supprimer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs</a>. 

::: moniker-end 
    
2. Dans la page **Utilisateurs actifs** , sélectionnez **Filtrer**, sélectionnez le filtre à modifier, puis **sélectionnez Modifier le filtre**. 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les vues personnalisées. 
  
3. Dans la page **Filtre personnalisé** , modifiez les informations en fonction des besoins, puis **sélectionnez Enregistrer**. Ou, pour supprimer le filtre, en bas de la page, **sélectionnez Supprimer**. 

## <a name="related-content"></a>Contenu connexe

[Vue d’ensemble de la Centre d'administration Microsoft 365](../admin-overview/admin-center-overview.md) (vidéo)\
[À propos des rôles d’administrateur](../add-users/about-admin-roles.md) (vidéo)\
[Personnaliser le thème Microsoft 365 pour votre organisation](../setup/customize-your-organization-theme.md) (article)


     
