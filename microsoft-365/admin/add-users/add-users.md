---
title: Ajouter des utilisateurs et attribuer des licences dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier1
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- VSBFY23
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- MET150
description: Découvrez comment attribuer un compte d’utilisateur à chaque membre de l’équipe afin qu’il puisse disposer de licences Microsoft 365, d’informations d’identification de connexion et de boîtes aux lettres Microsoft 365.
ms.date: 07/01/2020
ms.openlocfilehash: e0485ac1ed66c40b19ec4645fc8b00dc85b686a7
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722129"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Ajouter des utilisateurs et attribuer des licences simultanément

Consultez [l’aide de Microsoft 365 petite entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

The people on your team each need a user account before they can sign in and access [Microsoft 365 for business](https://www.microsoft.com/microsoft-365/business). The easiest way to add user accounts is to add them one at a time in the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 admin center</a>. After you do this step, your users have Microsoft 365 licenses, sign in credentials, and Microsoft 365 mailboxes.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général, de licences ou d’utilisateurs pour attribuer des licences. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>Vidéo : Ajouter des utilisateurs dans l’affichage du tableau de bord

Regardez cette vidéo et d’autres encore sur notre [chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198205).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> Les étapes illustrées dans la vidéo partent d’un point différent pour procéder à l’ajout d’utilisateurs, cependant les étapes restantes sont les mêmes que celles décrites ci-dessous.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Ajouter un utilisateur à la fois dans l’affichage du tableau de bord

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Capture d’écran : affichage du tableau de bord du Centre d'administration":::

::: moniker range="o365-worldwide"

1. Accédez au centre d’administration sur<https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Accédez à **Utilisateurs**  >  **Utilisateurs actifs** puis sélectionnez **Ajouter un utilisateur**.
3. Dans le volet **Configurer les informations de base**, renseignez les informations de base de l’utilisateur, puis sélectionnez **Suivant**.
    - **Nom** Renseignez le nom complet, le nom d'affichage et le nom d'utilisateur.
    - **Domain** Choose the domain for the user's account. For example, if the user's username is Jakob, and the domain is contoso.com, they'll sign in by using jakob@contoso.com.
    - **Paramètres du mot de passe** Choisissez d’utiliser un mot de passe généré automatiquement ou un mot de passe fort que vous aurez créé pour l’utilisateur.
    - The user must change their password after 90 days. Or you can choose to **Require this user to change their password when they first sign in**.
    - Indiquez si le mot de passe doit être envoyé par e-mail lorsque l’utilisateur est ajouté.
4. Dans le volet **Attribuer des licences de produits**, sélectionnez l’emplacement et la licence adaptée à l’utilisateur. Si vous n’avez pas de licence disponible, vous pouvez toujours ajouter un utilisateur et acheter des licences supplémentaires. Développez l’onglet **Applications** et sélectionnez ou désélectionnez les applications pour lesquelles attribuer les licences à l’utilisateur. Sélectionnez **Suivant**.
5. Dans le volet **Paramètres facultatifs**, développez l’onglet **Rôles** et promouvez cet utilisateur au rôle d’administrateur. Développez l’onglet **Informations du profil** pour ajouter plus d’informations sur l’utilisateur.
6. Sélectionnez **Suivant**, passez en revue les paramètres du nouvel utilisateur, effectuez les changements que vous souhaitez, puis sélectionnez **Finaliser l’ajout**, puis **Fermer**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Ajouter un utilisateur dans le mode simplifié administrateur

Si vous voyez cette page dans le Centre d'administration, vous êtes dans le **mode simplifié administrateur**. Suivez les étapes ci-dessous permettant d’ajouter un utilisateur.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Capture d’écran : mode simplifié du Centre d'administration":::

::: moniker range="o365-worldwide"

1. Accédez au centre d’administration sur <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Sélectionnez **Créer un compte pour une autre personne**.
3. Sur la page **Ajouter un compte utilisateur**, remplissez le prénom et le nom, le nom d'affichage et le nom d'utilisateur qu’il utilisera pour se connecter.
4. Ajoutez l’adresse e-mail de l’utilisateur dans la zone de texte **Jusqu’à 5 adresses e-mail...**. Ceci permettra de s’assurer que le nouvel utilisateur reçoive les informations dont il a besoin pour se connecter aux services Microsoft 365.
5. Sélectionnez **Ajouter un utilisateur**, puis **Télécharger les informations de connexion** si vous souhaitez les enregistrer.

## <a name="add-multiple-users-at-the-same-time"></a>Ajouter plusieurs utilisateurs simultanément

Toutes les méthodes suivantes permettent d’ajouter de multiples utilisateurs simultanément :

- **Utiliser une feuille de calcul pour ajouter des utilisateurs en bloc.** Consultez la rubrique [Ajouter plusieurs utilisateurs simultanément](../../enterprise/add-several-users-at-the-same-time.md).
- **Automate adding accounts and assigning licenses.** See [Create user accounts with Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Choose this method if you're already familiar with using Windows PowerShell cmdlets.
- **Using ActiveDirectory?** [Set up directory synchronization for Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Use the Azure AD Connect tool to replicate Active Directory user accounts (and other Active Directory objects) in Microsoft 365. The sync only adds the user accounts. You must assign licenses to the synced users before they can use email and other Office apps.
- **Si vous effectuez une migration depuis Exchange** Consultez la rubrique [Méthodes de migration de comptes de messagerie multiples vers Office 365](/Exchange/mailbox-migration/mailbox-migration). Lorsque vous migrez plusieurs boîtes aux lettres vers Microsoft 365 en utilisant une méthode de migration à basculement, intermédiaire ou Exchange hybride, vous ajoutez automatiquement des utilisateurs dans le cadre de la migration. La migration ajoute uniquement les comptes d'utilisateurs. Vous devrez attribuer des licences aux utilisateurs pour qu'ils puissent utiliser le courrier et les autres applications Office. Si vous n’attribuez pas de licence à un utilisateur, sa boîte aux lettres est désactivée à la fin de la période de grâce de 30 jours. Découvrez comment [attribuer des licences à des utilisateurs](../manage/assign-licenses-to-users.md) dans le centre d'administration Microsoft 365.

## <a name="create-edit-or-delete-custom-user-views"></a>Créer, modifier ou supprimer des vues utilisateur personnalisées

Si vous êtes administrateur général ou administrateur de gestion des utilisateurs d’un abonnement Microsoft 365 pour les entreprises, vous pouvez créer jusqu’à 50 vues utilisateur personnalisées pour afficher des sous-ensembles d’utilisateurs. Ces vues s’ajoutent à l’ensemble standard de vues. Vous pouvez créer, modifier ou supprimer des vues utilisateur personnalisées, et les vues personnalisées que vous créez sont disponibles pour tous les administrateurs.

Lorsque vous créez, modifiez ou supprimez un affichage utilisateur personnalisé, les modifications sont affichées dans la liste **Filtre** que tous les administrateurs de votre entreprise voient lorsqu’ils accèdent à la page **Utilisateurs** .

> [!TIP]
> Les vues utilisateur standard sont affichées par défaut dans la liste déroulante **Filtres** . Les filtres standard incluent **Tous les utilisateurs**, **Utilisateurs sous licence**, **Utilisateurs invités**,  **Connexion autorisée**, **Connexion bloquée**, **Utilisateurs sans licence**, **Utilisateurs avec erreurs**, **Administrateurs de facturation**, **Administrateurs généraux**, **Administrateurs du support technique**, **Administrateurs de service** et **Administrateurs de gestion des utilisateurs**. Vous ne pouvez pas modifier ou supprimer des vues standard. 

Voici quelques points à noter sur les vues standard : 

- Certaines vues standard affichent une liste non triée si la liste contient plus de 2 000 utilisateurs. Pour localiser des utilisateurs spécifiques dans cette liste, utilisez la zone de recherche. 
- Si vous n’avez pas acheté Microsoft 365 auprès de Microsoft, **les administrateurs de facturation** n’apparaissent pas dans la liste des affichages standard. Pour plus d'informations, consultez la rubrique [Affectation de rôles d'administrateur](assign-admin-roles.md). 
  
### <a name="choose-the-filters-for-your-custom-user-view"></a>Choisir les filtres de votre vue utilisateur personnalisée

Vous pouvez créer et modifier vos vues personnalisées dans le volet **Filtre personnalisé** . Si vous sélectionnez plusieurs options de filtre, vous obtenez des résultats qui contiennent des utilisateurs qui correspondent à tous les critères sélectionnés. L’exemple suivant montre comment créer une vue personnalisée nommée « Utilisateurs canadiens » qui affiche tous les utilisateurs d’un domaine spécifique qui se trouvent au Canada. 

 **A - Domaine** Si vous avez plusieurs domaines pour votre organisation, vous pouvez choisir parmi une liste déroulante de domaines disponibles. 
  
 **B - État de la connexion** Choisissez les utilisateurs autorisés ou bloqués. 
  
 **C - Emplacement** Choisissez un emplacement dans une liste déroulante de pays. 
  
 **D - Licence de produit affectée** Choisissez dans une liste déroulante des licences disponibles dans votre organisation. Utilisez ce filtre pour afficher les utilisateurs auxquels la licence que vous avez sélectionnée leur a été attribuée. Les utilisateurs peuvent également disposer de licences supplémentaires. 
  
Vous pouvez également filtrer par des détails de profil utilisateur supplémentaires utilisés dans votre organisation, tels que le département, la ville, l’état ou la province, le pays ou la région ou la fonction.
  
 **Autres conditions :**
  
- **Utilisateurs synchronisés uniquement** Cochez cette case pour afficher tous les utilisateurs qui ont été synchronisés avec l’Active Directory local, que les utilisateurs aient été activés ou non. 

- **Utilisateurs avec des erreurs** Cochez cette case pour afficher les utilisateurs qui peuvent avoir des erreurs d’approvisionnement. 

- **Utilisateurs sans licence** Cochez cette case pour rechercher tous les utilisateurs à qui aucune licence n’a été attribuée. Les résultats de cette vue peuvent également inclure des utilisateurs qui disposent d’une boîte aux lettres Exchange, mais qui n’ont pas de licence. Pour suivre spécifiquement ces utilisateurs, utilisez le filtre **Utilisateurs sans licence avec des boîtes aux lettres ou des archives Exchange**. Les résultats de cette vue peuvent également inclure des utilisateurs qui disposent d’une archive Exchange, mais qui n’ont pas de licence.

- **Utilisateurs sans licence avec des boîtes aux lettres ou des archives Exchange** Cochez cette case pour afficher les comptes d’utilisateur créés dans Exchange Online et disposant d’une boîte aux lettres Exchange, mais qui n’ont pas reçu de licence Microsoft 365. Les résultats de ce filtre incluent les utilisateurs qui ont ou qui ont reçu une archive Exchange. 

> [!NOTE]
> Le filtre **Utilisateurs sans licence avec boîtes aux lettres Exchange** fonctionne dans les cas suivants :

1. La boîte aux lettres a été récemment convertie de **partagée** en **utilisateur** et elle n’a pas de licence.
2. La boîte aux lettres a récemment été migrée vers Microsoft 365, mais aucune licence n’a été attribuée.
3. La boîte aux lettres a été créée à l’aide de PowerShell et aucune licence n’a été attribuée.
4. Une boîte aux lettres créée localement avec une applet de commande New-RemoteMailbox est provisionnée pour l’utilisateur.

> [!TIP]
> Si vous créez une vue personnalisée qui retourne plus de 2 000 utilisateurs, la liste d’utilisateurs obtenue n’est pas triée. Dans ce cas, utilisez la zone de recherche pour rechercher des utilisateurs ou modifiez votre vue personnalisée pour affiner votre recherche. 
  
### <a name="create-a-custom-user-view"></a>Créer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.  

::: moniker-end
    
2. Dans la page **Utilisateurs actifs** , sélectionnez **Filtres** , puis **Nouveau filtre**.
  
3. Dans la page **Filtre personnalisé** , entrez le nom de votre filtre, choisissez les conditions de votre filtre personnalisé, puis sélectionnez **Ajouter**. Votre vue personnalisée est désormais incluse dans la liste déroulante des filtres.

### <a name="edit-or-delete-a-custom-user-view"></a>Modifier ou supprimer un affichage utilisateur personnalisé

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

::: moniker-end 
    
2. Dans la page **Utilisateurs actifs** , sélectionnez **Filtrer**, sélectionnez le filtre que vous souhaitez modifier, puis sélectionnez **Modifier le filtre**. 
    
    > [!TIP]
    > Vous pouvez modifier uniquement les vues personnalisées. 
  
3. Dans la page **Filtre personnalisé** , modifiez les informations en fonction des besoins, puis sélectionnez **Enregistrer**. Ou, pour supprimer le filtre, en bas de la page, sélectionnez **Supprimer**.

## <a name="next-steps"></a>Étapes suivantes

Après avoir ajouté un utilisateur, vous recevez une notification par courrier de Microsoft. Ce courrier électronique contient l’identifiant de l’utilisateur et son mot de passe à lui faire parvenir pour qu’il puisse se connecter à Microsoft 365. Nous vous conseillons d'utiliser le processus habituel pour communiquer les nouveaux mots de passe. Partagez le [guide de démarrage rapide pour les employés](../setup/employee-quick-setup.md) avec vos nouveaux utilisateurs pour mettre certaines choses en place, en leur faisant par exemple découvrir [comment télécharger et installer des applications Office sur un PC ou Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) ou [comment configurer les applications Office et la messagerie électronique sur un appareil mobile](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Contenu connexe

[Ajouter un nouvel employé dans Microsoft 365](add-new-employee.md) (article)\
[Ajouter plusieurs utilisateurs simultanément dans Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (article)\
[Rétablir un utilisateur dans Microsoft 365](restore-user.md) (article)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)\
[Supprimer un utilisateur de votre organisation](delete-a-user.md) (article)
