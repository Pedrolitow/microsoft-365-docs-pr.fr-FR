---
title: Gérer les stratégies de revendication automatique
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: yinggiy, pablom
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
description: Découvrez comment créer et gérer des stratégies de revendication automatique qui attribuent automatiquement des licences aux utilisateurs pour certaines applications.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: 94bfcb3e9d7b210a6ca794e0e7fa88e0161de848
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68534781"
---
# <a name="manage-microsoft-teams-auto-claim-policies"></a>Gérer les stratégies de revendication automatique Microsoft Teams

Une stratégie de revendication automatique permet aux utilisateurs de réclamer automatiquement une licence pour un produit la première fois qu’ils se connectent à une application. En tant qu’administrateur, vous attribuez généralement des licences aux utilisateurs manuellement ou à l’aide de licences basées sur un groupe. En utilisant des stratégies de revendication automatique, vous gérez les produits pour lesquels les utilisateurs peuvent réclamer automatiquement des licences. Vous pouvez également contrôler les produits dont proviennent ces licences.

> [!IMPORTANT]
> Les stratégies de revendication automatique sont actuellement disponibles uniquement pour Microsoft Teams. D’autres produits seront disponibles à l’avenir.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général pour créer et gérer des stratégies de revendication automatique. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Activer ou désactiver la fonctionnalité de stratégie de revendication automatique

Par défaut, la fonctionnalité de stratégie de revendication automatique est désactivée. Avant de pouvoir utiliser la fonctionnalité, vous devez d’abord l’activer. Après avoir activé la fonctionnalité, vous pouvez créer une stratégie de revendication automatique.

### <a name="turn-on-auto-claim-policies"></a>Activer les stratégies de revendication automatique

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Au centre de la page, sélectionnez le bouton **Activer le paramètre** .

### <a name="turn-off-auto-claim-policies"></a>Désactiver les stratégies de revendication automatique

Seul un administrateur général peut désactiver un paramètre de stratégie de revendication automatique.

1. Dans le Centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">de l’organisation</a> .
2. En bas du tableau, sélectionnez **Applications et services appartenant à l’utilisateur**.
3. Dans le volet droit, décochez la case **permettant aux utilisateurs de réclamer automatiquement des licences la première fois qu’ils se connectent**.

Si vous disposez déjà d’une stratégie active, mais que vous ne souhaitez pas que d’autres utilisateurs demandent des licences, [désactivez la stratégie](#turn-a-policy-on-or-off). Lorsque vous désactivez une stratégie de revendication automatique, plus aucun utilisateur ne peut demander de licence à partir de ce point. Les utilisateurs qui ont déjà revendiqué une licence ne perdent pas leur licence.

## <a name="create-an-auto-claim-policy"></a>Créer une stratégie de revendication automatique

L’onglet <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Stratégie de revendication automatique répertorie</a> les stratégies que vous créez. Sous cet onglet, vous pouvez voir : le nom de la stratégie, l’application associée à la stratégie, le produit affecté à la stratégie, le nombre de licences disponibles et l’état de la stratégie.

Lorsque vous créez une stratégie de revendication automatique, vous pouvez y ajouter un produit de sauvegarde. Si le produit principal n’a plus de licences, le produit de sauvegarde est utilisé pour attribuer des licences aux utilisateurs. Vous pouvez ajouter jusqu’à quatre produits de sauvegarde et [modifier l’ordre dans lequel ils sont utilisés](#change-the-assigning-order-for-backup-products). Pour en savoir plus, consultez [Ajouter ou supprimer des produits de sauvegarde](#add-or-remove-backup-products).

> [!NOTE]
> Actuellement, vous ne pouvez créer qu’une seule stratégie de revendication automatique. Le nombre de stratégies que vous pouvez créer augmente à mesure que davantage de produits sont en mesure d’utiliser cette fonctionnalité.

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez **Ajouter une stratégie**.
3. Dans la page **Nommer cette stratégie de revendication automatique** , entrez un nom pour la stratégie, puis sélectionnez **Suivant**.
4. Dans la page **Définir une application de revendication automatique et un produit** , sélectionnez une application et l’abonnement à partir de laquelle attribuer des licences.
5. Si vous souhaitez ajouter un produit de sauvegarde, sélectionnez **Ajouter un produit de sauvegarde à cette stratégie**, puis sélectionnez le produit dans la liste.
6. Sélectionnez **Suivant**.
7. Dans la page **Sélectionner des applications, désactivez** ou sélectionnez les zones à exclure ou à inclure avec la licence, puis sélectionnez **Suivant**.
8. Si vous avez ajouté un ou plusieurs produits de sauvegarde, répétez l’étape 7 pour chaque produit. Sinon, passez à l’étape 9.
9. Dans la page **Révision et fin** , vérifiez les nouvelles informations de stratégie, apportez les modifications nécessaires, puis sélectionnez **Créer une stratégie**.
10. Sélectionnez **Fermer**.

## <a name="turn-a-policy-on-or-off"></a>Activer ou désactiver une stratégie

Lorsque vous désactivez une stratégie, les utilisateurs ne peuvent plus réclamer de licences en vertu de cette stratégie. La modification n’affecte pas les utilisateurs qui ont déjà revendiqué des licences en vertu de cette stratégie.

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, sous **Activer ou désactiver cette stratégie**, activez ou désactivez la case à cocher.
4. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

## <a name="edit-the-policy-friendly-name"></a>Modifier le nom convivial de la stratégie

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, dans la section **Nom** de la stratégie, **sélectionnez Modifier**.
4. Entrez un nouveau nom de stratégie, puis **sélectionnez Enregistrer**.
5. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

## <a name="add-or-remove-backup-products"></a>Ajouter ou supprimer des produits de sauvegarde

Lorsque vous créez une stratégie, vous y ajoutez un produit. Les licences sont ensuite automatiquement attribuées aux utilisateurs de ce pool de licences. Vous pouvez ajouter ou supprimer des produits pour une stratégie de revendication automatique à tout moment. Si vous avez déjà un produit associé à la stratégie, tous les produits que vous ajoutez sont considérés comme des produits de sauvegarde. Lorsque le nombre de licences disponibles du premier produit est épuisé, la stratégie utilise le produit de sauvegarde suivant sur la liste pour attribuer des licences. Vous [pouvez réorganiser la liste des produits](#change-the-assigning-apps-and-services) comme vous le souhaitez.

Lorsque vous supprimez un produit de sauvegarde, il n’est plus utilisé pour attribuer des licences. Les utilisateurs disposant d’une licence existante disposent toujours de cette licence, mais aucun nouvel utilisateur ne peut recevoir de licences pour ce produit.

> [!NOTE]
> Une stratégie de revendication automatique doit contenir au moins un produit. Vous ne pouvez pas supprimer tous les produits d’une stratégie. Si vous ne souhaitez plus attribuer de licences à partir d’une stratégie de revendication automatique spécifique, [désactivez la stratégie](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Ajouter un produit de sauvegarde

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, en bas, sélectionnez **Ajouter un produit de sauvegarde à cette stratégie**.
    > [!NOTE]
    > Si vous ne voyez pas ce lien, c’est que vous n’avez qu’un seul produit associé à votre compte.
4. Dans le volet **Ajouter un produit** , utilisez la liste déroulante pour choisir un produit à ajouter à la stratégie, puis sélectionnez **Ajouter**.
5. Sélectionnez **Enregistrer** pour fermer le volet d’informations.

### <a name="remove-a-backup-product"></a>Supprimer un produit de sauvegarde

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, en bas, **sélectionnez Supprimer un produit**.
4. Dans le volet **Supprimer un produit du volet de** stratégie, sélectionnez la zone correspondant à la stratégie à supprimer, puis **sélectionnez Enregistrer**.
5. Fermez le volet d’informations.

## <a name="change-the-assigning-apps-and-services"></a>Modifier l’affectation d’applications et de services

Chaque produit est associé à une collection d’applications et de services. Pour chaque produit de votre stratégie de revendication automatique, vous pouvez spécifier les applications et services à inclure lorsqu’une licence lui est automatiquement attribuée.

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, sous **Applications et services**, **sélectionnez Modifier**.
4. Dans le volet **Applications et services** , dans la liste déroulante **Produit** , sélectionnez un seul produit ou **tous les produits**.
5. Cochez ou désactivez les cases pour les applications et services auxquels vous souhaitez que les utilisateurs aient ou non accès.
6. Lorsque vous avez terminé, **sélectionnez Enregistrer**, puis fermez le volet d’informations.

## <a name="change-the-assigning-order-for-backup-products"></a>Modifier l’ordre d’affectation des produits de sauvegarde

Si des produits de sauvegarde sont affectés à la stratégie, vous pouvez modifier l’ordre dans lequel ils sont utilisés pour attribuer des licences lorsque les utilisateurs se connectent à l’application.

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez la stratégie à modifier.
3. Dans le volet d’informations, dans la section **Licences du produit** , sélectionnez la zone en regard du produit que vous souhaitez déplacer, puis **sélectionnez Monter** ou **Descendre**.
4. Répétez l’étape 3 pour chaque produit que vous souhaitez réorganiser.
5. Lorsque vous avez terminé de réorganiser les produits, **sélectionnez Enregistrer** pour fermer le volet d’informations.

## <a name="view-an-auto-claim-policy-report"></a>Afficher un rapport de stratégie de revendication automatique

1. Dans le Centre d’administration, accédez à la page **Licences** de **facturation**\>, puis sélectionnez l’onglet Stratégie <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">de revendication automatique</a>.
2. Sélectionnez **Afficher le rapport**. La page **du rapport de stratégie de revendication automatique répertorie** toutes les licences attribuées à partir de chaque stratégie au cours des 90 derniers jours. Par défaut, la page affiche les 90 derniers jours.
3. Pour modifier la période indiquée, sélectionnez la liste déroulante **des 30 derniers jours** . Vous pouvez afficher les rapports des 1, 7, 30 et 90 derniers jours.

## <a name="next-steps"></a>Prochaines étapes

Vous pouvez revenir régulièrement à l’onglet **Stratégie de revendication automatique** pour afficher la liste des utilisateurs qui ont revendiqué des licences sous les stratégies que vous avez créées.

## <a name="related-content"></a>Contenu associé

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Acheter ou supprimer des licences d’abonnement](buy-licenses.md) (article)\
[Comprendre les abonnements et les licences](subscriptions-and-licenses.md) (article)
