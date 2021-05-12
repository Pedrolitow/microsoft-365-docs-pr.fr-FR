---
title: Gérer les stratégies de revendication automatique
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.review: yinggiy, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_licensing
description: Découvrez comment créer et gérer des stratégies de revendication automatique qui attribuent automatiquement des licences à des utilisateurs pour certaines applications.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: b104700905b3753466036411368951f12a7012d8
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52331645"
---
# <a name="manage-auto-claim-policies"></a>Gérer les stratégies de revendication automatique

Une stratégie de revendication automatique permet aux utilisateurs de demander automatiquement une licence pour un produit la première fois qu’ils se connectent à une application. En tant qu’administrateur, vous attribuez généralement des licences aux utilisateurs manuellement ou à l’aide de licences basées sur des groupes. À l’aide des stratégies de revendication automatique, vous gérez les produits pour lesquels les utilisateurs peuvent automatiquement demander des licences. Vous pouvez également contrôler les produits d’où proviennent ces licences.

Après avoir créé une stratégie de revendication automatique, vous pouvez effectuer les tâches suivantes pour gérer la stratégie :

- [Activer ou désactiver la stratégie](#turn-a-policy-on-or-off)
- [Modifier le nom convivial de la stratégie](#edit-the-policy-friendly-name)
- [Ajouter ou supprimer des produits de sauvegarde](#add-or-remove-backup-products)
- [Gérer l’affectation d’applications et de services](#change-the-assigning-apps-and-services)
- [Modifier l’ordre d’affectation](#change-the-assigning-order-for-backup-products)
- [Afficher un rapport de stratégie](#view-an-auto-claim-policy-report)

> [!IMPORTANT]
> Les stratégies de revendication automatique sont actuellement disponibles uniquement pour Microsoft Teams. D’autres produits seront disponibles à l’avenir.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général, utilisateur ou administrateur de licence pour créer et gérer des stratégies de revendication automatique. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Activer ou désactiver la fonctionnalité de stratégie de revendication automatique

Par défaut, la fonctionnalité de stratégie de revendication automatique est désactivée. Avant de pouvoir utiliser la fonctionnalité, vous devez d’abord l’activer. Après avoir activer la fonctionnalité, vous pouvez créer une stratégie de revendication automatique.

### <a name="turn-on-auto-claim-policies"></a>Activer les stratégies de revendication automatique

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Au centre de la page, sélectionnez le **bouton Activer le paramètre.**

### <a name="turn-off-auto-claim-policies"></a>Désactiver les stratégies de revendication automatique

Seul un administrateur général peut désactiver un paramètre de stratégie de revendication automatique.

1. Dans le Centre d’administration, allez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Org.</a>
2. Dans la partie inférieure du tableau, sélectionnez les applications et services dont l’utilisateur **est propriétaire.**
3. Dans le volet droit, videz la case pour laisser les utilisateurs se réclamer automatiquement des licences la première fois **qu’ils se connectent.**

Si vous avez déjà une stratégie active, mais que vous ne souhaitez plus que les utilisateurs revendication de licences, [désactiver la stratégie](#turn-a-policy-on-or-off). Lorsque vous désactiverez une stratégie de revendication automatique, plus aucun utilisateur ne peut demander de licence à partir de ce stade. Les utilisateurs qui ont déjà revendiqué une licence ne perdent pas leur licence.

## <a name="create-an-auto-claim-policy"></a>Créer une stratégie de revendication automatique

<a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">L’onglet Stratégie de revendication automatique</a> répertorie les stratégies que vous créez. Sous cet onglet, vous pouvez voir : le nom de la stratégie, l’application associée à la stratégie, le produit affecté à la stratégie, le nombre de licences disponibles et l’état de la stratégie.

Lorsque vous créez une stratégie de revendication automatique, vous pouvez y ajouter un produit de sauvegarde. Si le produit principal n’a pas de licences, le produit de sauvegarde est utilisé pour attribuer des licences aux utilisateurs. Vous pouvez ajouter jusqu’à quatre produits de sauvegarde et [modifier l’ordre dans lequel ils sont utilisés.](#change-the-assigning-order-for-backup-products) Pour plus d’informations, voir [Ajouter ou supprimer des produits de sauvegarde.](#add-or-remove-backup-products)

> [!NOTE]
> Actuellement, vous ne pouvez créer qu’une seule stratégie de revendication automatique. Le nombre de stratégies que vous pouvez créer augmente à mesure que de plus en plus de produits peuvent utiliser cette fonctionnalité.

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez **Ajouter une stratégie.**
3. Dans la page **Nom de cette stratégie de revendication** automatique, entrez un nom pour la stratégie, puis sélectionnez **Suivant**.
4. Dans la page **Définir une application à** revendication automatique et un produit, sélectionnez une application et l’abonnement pour attribuer des licences.
5. Si vous souhaitez ajouter un produit de sauvegarde, sélectionnez Ajouter un produit de sauvegarde à cette **stratégie,** puis sélectionnez le produit dans la liste.
6. Sélectionnez **Suivant**.
7. Dans la page **Sélectionner des** applications, clear or select the boxes for the apps to exclude or include with the license, then select **Next**.
8. Si vous avez ajouté un ou plusieurs produits de sauvegarde, répétez l’étape 7 pour chaque produit. Dans le cas contraire, allez à l’étape 9.
9. Dans la page **Révision et fin,** vérifiez les nouvelles informations de stratégie, a apporté les modifications nécessaires, puis **sélectionnez Créer une stratégie.**
10. Sélectionnez **Fermer**.

## <a name="turn-a-policy-on-or-off"></a>Activer ou désactiver une stratégie

Lorsque vous désactiver une stratégie, plus aucun utilisateur ne peut demander de licences dans le cadre de cette stratégie. La modification n’affecte pas les utilisateurs qui ont déjà revendiqué des licences dans le cadre de cette stratégie.

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, sous **Activer** ou désactiver cette stratégie, cochez ou clearez la case.
4. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

## <a name="edit-the-policy-friendly-name"></a>Modifier le nom convivial de la stratégie

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, dans la section **Nom de la** stratégie, sélectionnez **Modifier**.
4. Entrez un nouveau nom de stratégie, puis sélectionnez **Enregistrer.**
5. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

## <a name="add-or-remove-backup-products"></a>Ajouter ou supprimer des produits de sauvegarde

Lorsque vous créez une stratégie, vous y ajoutez un produit. Les licences sont ensuite automatiquement attribuées aux utilisateurs de ce pool de licences. Vous pouvez ajouter ou supprimer des produits pour une stratégie de revendication automatique à tout moment. Si vous avez déjà un produit associé à la stratégie, tous les produits que vous ajoutez sont considérés comme des produits de sauvegarde. Lorsque le nombre disponible de licences du premier produit est utilisé, la stratégie utilise le produit de sauvegarde suivant de la liste pour attribuer des licences. Vous [pouvez réorder la liste des produits](#change-the-assigning-apps-and-services) comme vous le souhaitez.

Lorsque vous supprimez un produit de sauvegarde, il n’est plus utilisé pour attribuer des licences. Les utilisateurs titulaires d’une licence existante ont toujours cette licence, mais aucun nouvel utilisateur ne peut recevoir de licences pour ce produit.

> [!NOTE]
> Une stratégie de revendication automatique doit contenir au moins un produit. Vous ne pouvez pas supprimer tous les produits d’une stratégie. Si vous ne souhaitez plus attribuer de licences à partir d’une stratégie de revendication automatique spécifique, désactiver [la stratégie.](#view-an-auto-claim-policy-report)

### <a name="add-a-backup-product"></a>Ajouter un produit de sauvegarde

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, en bas, sélectionnez Ajouter un produit **de sauvegarde à cette stratégie.**
    > [!NOTE]
    > Si vous ne voyez pas ce lien, c’est parce qu’un seul produit est associé à votre compte.
4. Dans le **volet Ajouter un** produit, utilisez la zone de drop-down pour choisir un produit à ajouter à la stratégie, puis sélectionnez **Ajouter**.
5. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

### <a name="remove-a-backup-product"></a>Supprimer un produit de sauvegarde

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, en bas, sélectionnez **Supprimer un produit.**
4. Dans le volet Supprimer **un produit** du volet stratégie, sélectionnez la zone de stratégie à supprimer, puis sélectionnez **Enregistrer.**
5. Fermez le volet d’informations.

## <a name="change-the-assigning-apps-and-services"></a>Modifier les applications et services qui leur sont attribués

Chaque produit est associé à une collection d’applications et de services.
Pour chaque produit de votre stratégie de revendication automatique, vous pouvez spécifier les applications et services à inclure lorsqu’une licence est automatiquement attribuée à un utilisateur pour ce produit.

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, sous **Applications et services,** sélectionnez **Modifier.**
4. Dans le volet Applications et  **services,** dans la zone de la zone produit, sélectionnez un seul produit ou tous les **produits.**
5. Cochez ou clearez les cases pour les applications et les services que vous souhaitez que les utilisateurs ont ou n’ont pas accès.
6. Lorsque vous avez terminé, **sélectionnez Enregistrer,** puis fermez le volet d’informations.

## <a name="change-the-assigning-order-for-backup-products"></a>Modifier l’ordre d’affectation des produits de sauvegarde

Si des produits de sauvegarde sont affectés à la stratégie, vous pouvez modifier l’ordre dans lequel ils sont utilisés pour attribuer des licences lorsque les utilisateurs se connectent à l’application.

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, dans la section **Licences** de produits, sélectionnez la  case à côté du produit que vous souhaitez déplacer, puis sélectionnez Monter ou **Descendre.**
4. Répétez l’étape 3 pour chaque produit que vous souhaitez réorder.
5. Lorsque vous avez terminé de réorder les produits, sélectionnez **Enregistrer** pour fermer le volet d’informations.

## <a name="view-an-auto-claim-policy-report"></a>Afficher un rapport de stratégie de revendication automatique

1. Dans le Centre d’administration, allez sur la page  \> **Licences de facturation,** puis sélectionnez l’onglet Stratégie de <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">revendication</a> automatique.
2. Select **View report**. La page **rapport de stratégie de revendication** automatique répertorie toutes les licences attribuées à partir de chaque stratégie au cours des 90 derniers jours. Par défaut, la page affiche les 90 derniers jours.
3. Pour modifier la période affichée, sélectionnez la liste de listes des **30** derniers jours. Vous pouvez afficher les rapports des 1, 7, 30 et 90 derniers jours.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez régulièrement revenir à **l’onglet** Stratégie de revendication automatique pour voir la liste des utilisateurs qui ont revendiqué des licences sous les stratégies que vous avez créées.

## <a name="related-content"></a>Contenu connexe

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Acheter ou supprimer des licences d’abonnement](buy-licenses.md) (article)\
[Comprendre les abonnements et les licences](subscriptions-and-licenses.md) (article)