---
title: Supprimer la licence de boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: bb229ee9-e7be-4990-b3eb-354e75740496
description: 'Supprimer une licence d’une boîte aux lettres partagée pour l’affecter à un autre utilisateur. '
ms.openlocfilehash: 9ba411c614fee93e37ac45e58fd40bf246a9c2ab
ms.sourcegitcommit: f6840dfcfdbcadc53cda591fd6cf9ddcb749d303
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44327241"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Supprimer une licence d’une boîte aux lettres partagée

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

En règle générale, les boîtes aux lettres partagées ne nécessitent pas de licence. Suivez ces instructions pour supprimer une licence d’une boîte aux lettres partagée afin de pouvoir l’attribuer à un utilisateur ou renvoyer la licence afin de ne pas payer une licence dont vous n’avez pas besoin.

> [!NOTE]
> Une licence est requise dans les scénarios suivants :
> 1. La boîte aux lettres partagée dispose de plus de 50 Go d’espace de stockage.
> 2. La boîte aux lettres partagée utilise l’archivage inaltérable.
> 3. La boîte aux lettres partagée est placée en conservation pour litige.

  
## <a name="remove-the-license"></a>Supprimer la licence

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

   > [!NOTE]
   > Vous devez supprimer la licence de la page utilisateurs actifs. Vous ne pouvez pas supprimer la licence de la page de boîte aux lettres partagée car les licences sont des paramètres utilisateur. 
  
2. Sélectionnez la boîte aux lettres partagée.

3. Dans l’onglet **licences et applications** , développez **licences** et désactivez la case à cocher correspondant à la licence que vous souhaitez supprimer.

4. Sélectionnez **Enregistrer les modifications**.

5. Lorsque vous revenez à la page **utilisateurs actifs** , l’état de la boîte aux lettres partagée est sans **licence**.

6. Vous payez toujours pour cette licence. Pour ne plus payer, [supprimez la licence de votre abonnement](../../commerce/licenses/remove-licenses-from-subscription.md).

::: moniker-end

::: moniker range="o365-germany"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

   > [!NOTE]
   > Vous devez supprimer la licence de la page utilisateurs actifs. Vous ne pouvez pas supprimer la licence de la page de boîte aux lettres partagée car les licences sont des paramètres utilisateur.

2. Sélectionnez la boîte aux lettres partagée, puis cliquez sur **modifier** en regard de **licences de produit**.

3. Sur la page **licences de produits** , définissez le bouton bascule sur **désactivé** pour la licence que vous souhaitez supprimer.

4. Sélectionnez **Enregistrer**.

5. Lorsque vous revenez à la page **utilisateurs actifs** , l’état de la boîte aux lettres partagée est sans **licence**.

6. Vous payez toujours pour cette licence. Pour ne plus payer, [supprimez la licence de votre abonnement](../../commerce/licenses/remove-licenses-from-subscription.md).

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

   > [!NOTE]
   > Vous devez supprimer la licence de la page utilisateurs actifs. Vous ne pouvez pas supprimer la licence de la page de boîte aux lettres partagée car les licences sont des paramètres utilisateur.

2. Sélectionnez la boîte aux lettres partagée, puis cliquez sur **modifier** en regard de **licences de produit**.

3. Sur la page **licences de produits** , définissez le bouton bascule sur **désactivé** pour la licence que vous souhaitez supprimer.

4. Sélectionnez **Enregistrer**.

5. Lorsque vous revenez à la page **utilisateurs actifs** , l’état de la boîte aux lettres partagée est sans **licence**.

6. Vous payez toujours pour cette licence. Pour ne plus payer, [supprimez la licence de votre abonnement](../../commerce/licenses/remove-licenses-from-subscription.md).

::: moniker-end 

## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
