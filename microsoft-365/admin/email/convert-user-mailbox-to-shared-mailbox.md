---
title: Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
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
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Découvrez comment convertir une boîte aux lettres privée en boîte aux lettres partagée accessible par plusieurs utilisateurs. '
ms.openlocfilehash: 7ae00c1d9c901378798f063554a44a3e5b741442
ms.sourcegitcommit: 41eb898143286755cd36df9f7e769de641263d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45391529"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée

Lorsque vous convertissez la boîte aux lettres d’un utilisateur en boîte aux lettres partagée, tout le courrier et le calendrier existants sont conservés. Il se trouve maintenant uniquement dans une boîte aux lettres partagée où plusieurs personnes peuvent y accéder au lieu d’une personne. À une date ultérieure, vous pouvez reconvertir une boîte aux lettres partagée en boîte aux lettres utilisateur (privée).

**Voici quelques éléments vraiment importants que vous devez savoir :**

- La boîte aux lettres utilisateur que vous convertissez nécessite une licence qui lui est attribuée avant de la convertir en boîte aux lettres partagée. Dans le cas contraire, vous ne verrez pas l’option permettant de convertir la boîte aux lettres. Si vous avez supprimé la licence, rajoutez-la afin de pouvoir convertir la boîte aux lettres. Après avoir converti la boîte aux lettres en une boîte aux lettres partagée, vous pouvez supprimer la licence du compte de l’utilisateur.

- Les boîtes aux lettres partagées peuvent avoir jusqu’à 50 Go de données sans qu’une licence lui soit attribuée. Pour conserver plus de données que cela, vous devez disposer d’une licence. Il se peut que vous deviez supprimer un lot de messages volumineux (par exemple, ceux contenant des pièces jointes) de la boîte aux lettres partagée afin de le réduire afin de pouvoir supprimer la licence.

- Ne supprimez pas le compte de l’ancien utilisateur. Cela est nécessaire pour ancrer la boîte aux lettres partagée. Si vous avez déjà supprimé le compte d’utilisateur, reportez-vous à [la rubrique Conversion de la boîte aux lettres d’un utilisateur supprimé](#convert-the-mailbox-of-a-deleted-user).

- Les règles sont intactes une fois que la boîte aux lettres est convertie en boîte aux lettres partagée.

## <a name="use-the-exchange-admin-center-to-convert-a-mailbox"></a>Utiliser le centre d’administration Exchange pour convertir une boîte aux lettres
 
1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Sélectionnez **Recipients** \> **boîtes aux lettres**de destinataires.

3. Sélectionnez la boîte aux lettres utilisateur. Sous **convertir en boîte aux lettres partagée**, sélectionnez **convertir**.

4. Si la taille de la boîte aux lettres est inférieure à 50 Go, vous pouvez supprimer la [licence de l’utilisateur](../manage/remove-licenses-from-users.md)et cesser de le payer. Ne supprimez pas le compte de l’utilisateur. La boîte aux lettres partagée en a besoin en tant qu’ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Consultez [la rubrique supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).
    
5. Pour tout ce que vous devez savoir sur les boîtes aux lettres partagées, consultez la rubrique [à propos des boîtes aux lettres partagées](about-shared-mailboxes.md) et [créez une boîte aux lettres partagée](create-a-shared-mailbox.md).

## <a name="use-the-microsoft-365-admin-center-to-convert-a-mailbox"></a>Utiliser le centre d’administration Microsoft 365 pour convertir une boîte aux lettres

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez convertir la boîte aux lettres.

3. Réinitialisez le mot de passe de l’utilisateur.

> [!NOTE]
> Il n’est pas nécessaire de réinitialiser le mot de passe de l’utilisateur pendant la conversion de boîte aux lettres. Toutefois, si le mot de passe n’est pas réinitialisé, **le nom d’utilisateur et le mot de passe d’origine continuent de fonctionner** une fois la conversion de boîte aux lettres terminée.

4. Dans l’onglet **messagerie** , sous **autres actions**, sélectionnez **convertir en boîte aux lettres partagée**. 

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’utilisateur dont vous souhaitez convertir la boîte aux lettres.

3. Dans le volet droit, développez **paramètres de messagerie**. En regard de **paramètres supplémentaires**, sélectionnez **convertir en boîte aux lettres partagée**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’utilisateur dont vous souhaitez convertir la boîte aux lettres.

3. Dans le volet droit, développez **paramètres de messagerie**. En regard de **paramètres supplémentaires**, sélectionnez **convertir en boîte aux lettres partagée**.

::: moniker-end


Si la taille de la boîte aux lettres est inférieure à 50 Go, vous pouvez [Supprimer la licence de l’utilisateur](../manage/remove-licenses-from-users.md)et cesser de le payer. Ne supprimez pas l’ancienne boîte aux lettres de l’utilisateur. La boîte aux lettres partagée en a besoin en tant qu’ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Consultez [la rubrique supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).
    
Pour tout ce que vous devez savoir sur les boîtes aux lettres partagées, consultez la rubrique [à propos des boîtes aux lettres partagées](about-shared-mailboxes.md) et [créez une boîte aux lettres partagée](create-a-shared-mailbox.md).

> [!NOTE]
> Les boîtes aux lettres partagées ne nécessitent pas de licence distincte. Toutefois, si vous souhaitez activer une boîte aux lettres d'archivage ou placer une conservation inaltérable ou une conservation pour litige sur une boîte aux lettres partagée, vous devez affecter une licence Exchange Online Plan 1 avec l'Archivage Exchange Online ou une licence Exchange Online Plan 2 à la boîte aux lettres.


## <a name="convert-the-mailbox-of-a-deleted-user"></a>Convertir la boîte aux lettres d’un utilisateur supprimé

Imaginons que vous ayez supprimé un compte d’utilisateur et que vous vouliez convertir son ancienne boîte aux lettres en boîte aux lettres de partage. Voici ce que vous devez faire :

1. [Restaurez le compte de l’utilisateur](../add-users/restore-user.md).

2. Assurez-vous qu’une licence Microsoft 365 lui est affectée.

3. Réinitialisez le mot de passe de l’utilisateur.
    
4. Patientez 20-30 minutes avant que la boîte aux lettres ne soit recréée.
    
5. Suivez maintenant les instructions de cette page pour convertir leur boîte aux lettres en boîte aux lettres partagée.
    
6. Une fois cette opération terminée, vous pouvez supprimer la licence de la boîte aux lettres de l’utilisateur. Ne supprimez pas l’ancienne boîte aux lettres de l’utilisateur. La boîte aux lettres partagée en a besoin en tant qu’ancre.
    
7. Ajoutez des membres à la boîte aux lettres partagée.


## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Convertir une boîte aux lettres partagée en boîte aux lettres (privée) d’un utilisateur

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.
   
2. Sélectionnez **destinataires** \> **partagés**.

3. Sélectionnez la boîte aux lettres partagée. Sous **convertir en boîte aux lettres normale**, sélectionnez **convertir**.

4. Revenez au centre d’administration. Sous **utilisateurs**, sélectionnez le compte d’utilisateur associé à l’ancienne boîte aux lettres partagée. Attribuer une licence au compte et réinitialiser le mot de passe.

   La configuration de la boîte aux lettres peut prendre quelques minutes, mais cette fois-ci, la personne qui va utiliser ce compte est prête à être utilisée. Lorsqu’ils se connectent, ils voient les éléments de courrier et de calendrier utilisés comme étant dans la boîte aux lettres partagée.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Convertir la boîte aux lettres d’un utilisateur dans un environnement hybride

Si cette boîte aux lettres partagée se trouve dans un environnement hybride, nous **vous recommandons vivement** (presque nécessaire !) de déplacer la boîte aux lettres utilisateur vers l’organisation locale, de convertir la boîte aux lettres d’utilisateur en boîte aux lettres partagée, puis de replacer la boîte aux lettres partagée dans le Cloud.

Voici pourquoi : Si vous convertissez la boîte aux lettres dans le Cloud, elle peut être convertie, mais en local, la boîte aux lettres est toujours la boîte aux lettres de l’utilisateur, car la nouvelle réalité n’est pas synchronisée en local.

En règle générale, il ne s’agit pas d’un problème, mais il existe des scénarios dans lesquels les attributs locaux (ce qui signifie que la boîte aux lettres est la boîte aux lettres de l’utilisateur) peuvent remplacer les nouvelles versions Cloud de ces attributs et, par conséquent, la boîte aux lettres peut être reconvertie. Il s’agit d’un problème car les boîtes aux lettres des utilisateurs nécessitent **des licences ou sont supprimées de manière récupérable au bout de 30 jours**!

Nous avons résolu la plupart des raisons de ce problème, mais cela peut toujours se produire, bien que rarement. Il est préférable d’être sûr et de déplacer la boîte aux lettres vers l’ordinateur local.

> [!NOTE]
> Si vous faites partie de la gestion de l’organisation ou de la gestion des destinataires, vous pouvez utiliser l’environnement de commande Exchange Management Shell pour modifier une boîte aux lettres utilisateur en une boîte aux lettres partagée locale. Par exemple, `Set-Mailbox -Identity mailbox1@contoso.onmicrosoft.com -Type Shared`.

> [!TIP]
> Consultez la solution de contournement dans cette solution de support pour les instances lorsque [les boîtes aux lettres partagées sont converties de manière inattendue en boîtes aux lettres utilisateur](https://support.microsoft.com/help/2710029/shared-mailboxes-are-unexpectedly-converted-to-user-mailboxes-after-di)
  
## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
