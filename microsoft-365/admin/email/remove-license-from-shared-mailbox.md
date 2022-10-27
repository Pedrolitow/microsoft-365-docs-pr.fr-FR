---
title: Supprimer la licence de boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
ms.reviewer: sinakassaw, nicholak
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: 'Supprimez une licence d’une boîte aux lettres partagée pour l’attribuer à un autre utilisateur ou renvoyez la licence afin que vous ne la payiez pas. '
ms.date: 04/22/2022
ms.openlocfilehash: bc54065556b7c23e135c774f446bf8f8776be5ce
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727430"
---
# <a name="remove-a-license-from-a-shared-mailbox"></a>Supprimer une licence d’une boîte aux lettres partagée

Les boîtes aux lettres partagées ne nécessitent généralement pas de licence. Suivez ces instructions pour supprimer une licence d’une boîte aux lettres partagée afin de pouvoir l’attribuer à un utilisateur ou retourner la licence afin de ne pas payer pour une licence dont vous n’avez pas besoin.

> [!NOTE]
>
> Une licence Exchange Online Plan 2 est requise dans les scénarios suivants :
>
> - La boîte aux lettres partagée a plus de 50 Go de stockage en cours d’utilisation.
> - La boîte aux lettres partagée utilise l’archivage sur place.
> - La boîte aux lettres partagée est placée en attente pour litige.
> 
> Pour obtenir des instructions pas à pas sur l’attribution de licences, consultez [Attribuer des licences à des utilisateurs](/microsoft-365/admin/manage/assign-licenses-to-users). 


## <a name="remove-the-license"></a>Supprimer la licence

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

   > [!NOTE]
   > Vous devez supprimer la licence de la page Utilisateurs actifs. Vous ne pouvez pas supprimer la licence de la page Boîte aux lettres partagée, car les licences sont des paramètres utilisateur.
  
2. Sélectionnez la boîte aux lettres partagée.

3. Dans l’onglet **Licences et applications** , développez **Licences** et décochez la case de la licence que vous souhaitez supprimer.

4. Sélectionnez **Enregistrer les modifications**.

5. Lorsque vous revenez à la page **Utilisateurs actifs** , l’état de la boîte aux lettres partagée est **Sans licence**.

6. Vous payez toujours pour la licence. Pour arrêter de payer, [supprimez la licence de votre abonnement](../../commerce/licenses/buy-licenses.md).

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
