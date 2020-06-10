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
description: Apprenez à utiliser des filtres pour créer, modifier ou supprimer des affichages utilisateur personnalisés dans Microsoft 365.
ms.openlocfilehash: 598a167b9845f763ddab57d3c5ba36e431aa751c
ms.sourcegitcommit: a3ec91423c352cd5fbf79b46ccd9c169455a03ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44664573"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Créer, modifier ou supprimer une vue utilisateur personnalisée

Si vous êtes un administrateur général ou un administrateur de gestion des utilisateurs d’un abonnement Microsoft 365 pour les entreprises, vous pouvez créer des affichages utilisateur personnalisés pour afficher un sous-ensemble spécifique d’utilisateurs. Ces affichages s’ajoutent à l’ensemble standard d’affichages. Vous pouvez créer, modifier ou supprimer des affichages utilisateur personnalisés, et les vues personnalisées que vous créez sont disponibles pour tous les administrateurs.
  
## <a name="custom-user-views-in-the-admin-center"></a>Vues utilisateur personnalisées dans le centre d’administration

::: moniker range="o365-worldwide"

Lorsque vous créez, modifiez ou supprimez une vue utilisateur personnalisée, les modifications s’affichent dans la liste de **filtres** que tous les administrateurs de votre société voient quand ils accèdent à la page **utilisateurs** . Vous pouvez créer jusqu’à 50 affichages personnalisés. 

::: moniker-end

::: moniker range="o365-germany"

Lorsque vous créez, modifiez ou supprimez une vue utilisateur personnalisée, les modifications apparaissent dans la liste des **affichages** que tous les administrateurs de votre société voient quand ils accèdent à la page **utilisateurs** . Vous pouvez créer jusqu’à 50 affichages personnalisés. 

::: moniker-end

::: moniker range="o365-21vianet"

Lorsque vous créez, modifiez ou supprimez une vue utilisateur personnalisée, les modifications apparaissent dans la liste des **affichages** que tous les administrateurs de votre société voient quand ils accèdent à la page **utilisateurs** . Vous pouvez créer jusqu’à 50 affichages personnalisés. 

::: moniker-end

> [!TIP]
>  Les affichages standard des utilisateurs sont affichés par défaut dans la liste déroulante **filtres** . Les filtres standard incluent **tous les utilisateurs**, **les utilisateurs sous licence**, **les utilisateurs invités**, la **connexion autorisée**, les **utilisateurs**qui ne disposent **pas de**licence, les **utilisateurs avec des erreurs, les administrateurs de** **facturation**, les administrateurs **globaux**, les administrateurs de service d' **assistance**, les administrateurs de **service**et les administrateurs de **gestion des utilisateurs**. Vous ne pouvez pas modifier ou supprimer des affichages standard. 

Voici quelques points à noter concernant les vues standard : 

- Certains affichages standard affichent une liste non triée s’il y a plus de 2 000 utilisateurs dans la liste. Pour rechercher des utilisateurs spécifiques dans cette liste, utilisez la zone de recherche. 
- Si vous n’avez pas acheté Microsoft 365 auprès de Microsoft, les **administrateurs de facturation** n’apparaissent pas dans la liste des affichages standard. Pour plus d'informations, consultez la rubrique [Affectation de rôles d'administrateur](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Choisir les filtres pour votre vue utilisateur personnalisée

Vous pouvez créer et modifier vos affichages personnalisés dans le volet **filtre personnalisé** . Si vous sélectionnez plusieurs options de filtre, vous obtenez des résultats qui contiennent les utilisateurs qui répondent à tous les critères sélectionnés. L’exemple suivant montre comment créer une vue personnalisée nommée « Users canadien » qui affiche tous les utilisateurs d’un domaine spécifique au Canada. 

  
 **A-domaine** Si votre organisation dispose de plusieurs domaines, vous pouvez choisir dans une liste déroulante des domaines disponibles. 
  
 **B-état de connexion** Choisissez les utilisateurs autorisés ou bloqués. 
  
 **Emplacement C** Choisissez un emplacement dans une liste déroulante de pays. 
  
 **D-licence de produit attribuée** Faites votre choix dans la liste déroulante des licences disponibles dans votre organisation. Utilisez ce filtre pour montrer aux utilisateurs qui disposent de la licence que vous avez sélectionnée. Les utilisateurs peuvent également avoir des licences supplémentaires. 
  
Vous pouvez également filtrer par des détails de profil utilisateur supplémentaires utilisés dans votre organisation, tels que service, ville, État ou province, pays ou région, ou fonction.
  
 **Autres conditions :**
  
- **Utilisateurs synchronisés uniquement** Activez cette case à cocher pour afficher tous les utilisateurs qui ont été synchronisés avec l’annuaire Active Directory local, que les utilisateurs aient été activés ou non. 
    
- **Utilisateurs avec des erreurs** Activez cette case à cocher pour afficher les utilisateurs qui peuvent avoir des erreurs de mise en service. 
    
- **Utilisateurs sans licence** Activez cette case à cocher pour rechercher tous les utilisateurs qui n’ont pas reçu de licence. Les résultats de cette vue peuvent également inclure des utilisateurs qui disposent d’une boîte aux lettres Exchange mais qui n’ont pas de licence. Pour effectuer le suivi de ces utilisateurs en particulier, utilisez le filtre **utilisateurs sans licence avec des boîtes aux lettres ou des archives Exchange**. Les résultats de cette vue peuvent également inclure des utilisateurs qui disposent d’une archive Exchange, mais qui n’ont pas de licence.
    
- **Utilisateurs sans licence avec des boîtes aux lettres ou des archives Exchange** Activez cette case à cocher pour afficher les comptes d’utilisateur qui ont été créés dans Exchange Online et qui disposent d’une boîte aux lettres Exchange, mais auxquels aucune licence Microsoft 365 n’a été attribuée. Les résultats de ce filtre incluent les utilisateurs qui disposent ou non d’une archive Exchange. 

> [!NOTE]
> Le filtre **utilisateurs sans licence avec boîtes aux lettres Exchange fonctionne dans** les cas suivants :
1. La boîte aux lettres a été récemment convertie de **partagé** à **utilisateur** et n’a pas de licence.
2. La boîte aux lettres a été récemment migrée vers Microsoft 365, mais aucune licence n’a été attribuée.
3. La boîte aux lettres a été créée à l’aide de PowerShell et aucune licence n’a été attribuée.
4. Une nouvelle boîte aux lettres créée sur site avec une cmdlet New-RemoteMailbox est configurée pour l’utilisateur.
    
> [!TIP]
> Si vous créez un affichage personnalisé qui renvoie plus de 2 000 utilisateurs, la liste d’utilisateurs obtenue n’est pas triée. Dans ce cas, utilisez la zone de recherche pour rechercher des utilisateurs ou modifier votre vue personnalisée pour affiner votre recherche. 
  
## <a name="create-a-custom-user-view"></a>Créer une vue utilisateur personnalisée

::: moniker range="o365-worldwide"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a>.
    
2. Sur la page **utilisateurs actifs** , sélectionnez **filtres** , puis **nouveau filtre**.
  
3. Sur la page **filtre personnalisé** , entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre vue personnalisée est désormais incluse dans la liste déroulante des filtres.
    
::: moniker-end

::: moniker range="o365-germany"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">actifs</a>.  

2. Sur la page **utilisateurs actifs** , sélectionnez **affichages** et sélectionnez **Ajouter un affichage personnalisé**.
  
3. Sur la page **affichage personnalisé** , entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre vue personnalisée est désormais incluse dans la liste déroulante des filtres.

::: moniker-end


::: moniker range="o365-21vianet"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs</a>. 

2. Sur la page **utilisateurs actifs** , sélectionnez **affichages** et sélectionnez **Ajouter un affichage personnalisé**.
  
3. Sur la page **affichage personnalisé** , entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre vue personnalisée est désormais incluse dans la liste déroulante des filtres.

::: moniker-end
    

## <a name="edit-or-delete-a-custom-user-view"></a>Modifier ou supprimer une vue utilisateur personnalisée

::: moniker range="o365-worldwide"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a>.
    
2. Sur la page **utilisateurs actifs** , sélectionnez **filtre**, sélectionnez le filtre à modifier, puis sélectionnez **modifier le filtre**. 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les vues personnalisées. 
  
3. Sur la page **filtre personnalisé** , modifiez les informations selon vos besoins, puis sélectionnez **Enregistrer**. Sinon, pour supprimer le filtre, dans la partie inférieure de la page, sélectionnez **supprimer**. 
    
::: moniker-end

::: moniker range="o365-germany"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">actifs</a>.  

2. Sur la page **utilisateurs actifs** , sélectionnez **affichages**, sélectionnez le filtre à modifier, puis cliquez sur **modifier cet affichage**. 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les vues personnalisées. 
  
3. Sur la page **vue personnalisée** , modifiez les informations selon vos besoins, puis sélectionnez **Enregistrer**. Sinon, pour supprimer le filtre, dans la partie inférieure de la page, sélectionnez **Supprimer l’affichage personnalisé**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le **Centre d’administration, accédez à utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">actifs</a>. 

2. Sur la page **utilisateurs actifs** , sélectionnez **affichages**, sélectionnez le filtre à modifier, puis cliquez sur **modifier cet affichage**. 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les vues personnalisées. 
  
3. Sur la page **vue personnalisée** , modifiez les informations selon vos besoins, puis sélectionnez **Enregistrer**. Sinon, pour supprimer le filtre, dans la partie inférieure de la page, sélectionnez **Supprimer l’affichage personnalisé**. 

::: moniker-end


     