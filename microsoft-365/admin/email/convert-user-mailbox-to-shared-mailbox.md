---
title: Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Découvrez comment convertir une boîte aux lettres privée en boîte aux lettres partagée accessible par plusieurs utilisateurs. '
ms.openlocfilehash: f716bbd16be9f67189b19358ddf16a289f57f8e7
ms.sourcegitcommit: a8f3c633714e934f9ad026c3bc72157ed535dcfc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2020
ms.locfileid: "49737964"
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

2. Sélectionnez  \> **boîtes aux lettres** de destinataires.

3. Sélectionnez la boîte aux lettres utilisateur. Sous **convertir en boîte aux lettres partagée**, sélectionnez **convertir**.

4. Si la taille de la boîte aux lettres est inférieure à 50 Go, vous pouvez supprimer la [licence de l’utilisateur](../manage/remove-licenses-from-users.md)et cesser de le payer. Ne supprimez pas le compte de l’utilisateur. La boîte aux lettres partagée en a besoin en tant qu’ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Consultez [la rubrique supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Il n’est pas nécessaire de réinitialiser le mot de passe de l’utilisateur pendant la conversion de boîte aux lettres. Toutefois, si le mot de passe n’est pas réinitialisé, **le nom d’utilisateur et le mot de passe d’origine continuent de fonctionner** une fois la conversion de boîte aux lettres terminée.

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

Pour plus d’informations sur la conversion d’une boîte aux lettres utilisateur en boîte aux lettres partagée dans un environnement hybride Exchange, voir :

 - [Cmdlets permettant de créer ou de modifier une boîte aux lettres partagée distante dans un environnement Exchange local](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
 - [Les boîtes aux lettres partagées sont converties de manière inattendue en boîtes aux lettres utilisateur après l’exécution de la synchronisation d’annuaires dans un déploiement hybride Exchange](https://docs.microsoft.com/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)
 

> [!NOTE]
> Si vous êtes membre du groupe de rôles gestion de l’organisation ou gestion des destinataires, vous pouvez utiliser l’environnement de commande Exchange Management Shell pour modifier une boîte aux lettres utilisateur en boîte aux lettres partagée locale. Par exemple, `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
