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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Apprenez à convertir une boîte aux lettres privée en boîte aux lettres partagée accessible par plusieurs personnes et non par une seule personne. '
ms.openlocfilehash: caf3935b1ffb36989b2884c6811111531a061098
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53393966"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée

Lorsque vous convertissez la boîte aux lettres d’un utilisateur en boîte aux lettres partagée, l’ensemble du courrier électronique et du calendrier existants est conservé. Ce n’est que maintenant que dans une boîte aux lettres partagée que plusieurs personnes pourront y accéder au lieu d’une seule personne. À une date ultérieure, vous pouvez reconverti une boîte aux lettres partagée en boîte aux lettres utilisateur (privée).

## <a name="before-you-begin"></a>Avant de commencer

**Voici quelques éléments essentiels que vous devez connaître :**

- La boîte aux lettres utilisateur que vous convertissez a besoin d’une licence qui lui est attribuée avant de la convertir en boîte aux lettres partagée. Sinon, vous ne verrez pas l’option de conversion de la boîte aux lettres. Si vous avez supprimé la licence, rajoutez-la afin de pouvoir convertir la boîte aux lettres. Après avoir converti la boîte aux lettres en une boîte aux lettres partagée, vous pouvez supprimer la licence du compte de l’utilisateur.

- Les boîtes aux lettres partagées peuvent avoir jusqu’à 50 Go de données sans licence qui leur est attribuée. Pour contenir davantage de données, vous avez besoin d’une licence qui lui est attribuée. Vous devrez peut-être supprimer un grand nombre de messages électroniques volumineux (par ex., ceux avec pièces jointes) de la boîte aux lettres partagée pour la réduire afin de pouvoir supprimer la licence.

- Ne supprimez pas le compte de l’ancien utilisateur. Cette valeur est requise pour ancrer la boîte aux lettres partagée. Si vous avez déjà supprimé le compte d’utilisateur, voir Convertir la boîte aux lettres [d’un utilisateur supprimé.](#convert-the-mailbox-of-a-deleted-user)

- Les règles sont intactes après la conversion de la boîte aux lettres en boîte aux lettres partagée.

## <a name="use-the-exchange-admin-center-to-convert-a-mailbox"></a>Utiliser le centre Exchange’administration pour convertir une boîte aux lettres
 
1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Sélectionnez **Les boîtes aux lettres** de \> **destinataires.**

3. Sélectionnez la boîte aux lettres de l’utilisateur. Sous **Convertir en boîte aux lettres partagée,** sélectionnez **Convertir.**

4. Si la boîte aux lettres est plus petite que 50 Go, vous pouvez supprimer la licence de l’utilisateur [et](../manage/remove-licenses-from-users.md)arrêter de payer pour celle-ci. Ne supprimez pas le compte de l’utilisateur. La boîte aux lettres partagée en a besoin comme ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Veuillez consulter [Supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Il n’est pas nécessaire de réinitialiser le mot de passe de l’utilisateur lors de la conversion de boîte aux lettres. Toutefois, si le mot  de passe n’est pas réinitialisé, le nom d’utilisateur et le mot de passe d’origine continuent de fonctionner une fois la conversion de la boîte aux lettres terminée.

Pour tout ce que vous devez savoir [](about-shared-mailboxes.md) sur les boîtes aux lettres partagées, voir à propos des boîtes aux lettres partagées et [créer une boîte aux lettres partagée.](create-a-shared-mailbox.md)

> [!NOTE]
> Les boîtes aux lettres partagées ne nécessitent pas de licence distincte. Toutefois, si vous souhaitez activer une boîte aux lettres d'archivage ou placer une conservation inaltérable ou une conservation pour litige sur une boîte aux lettres partagée, vous devez affecter une licence Exchange Online Plan 1 avec l'Archivage Exchange Online ou une licence Exchange Online Plan 2 à la boîte aux lettres.

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Convertir la boîte aux lettres d’un utilisateur supprimé

Supposons que vous avez supprimé un compte d’utilisateur et que vous voulez maintenant convertir son ancienne boîte aux lettres en boîte aux lettres de partage. Voici ce que vous devez faire :

1. [Restituer le compte de l’utilisateur.](../add-users/restore-user.md)

2. Assurez-vous qu Microsoft 365 licence est affectée.

3. Réinitialisez le mot de passe de l’utilisateur.
    
4. Attendez 20 à 30 minutes que leur boîte aux lettres soit recréée.
    
5. Suivez maintenant les instructions de cette page pour convertir leur boîte aux lettres en boîte aux lettres partagée.
    
6. Une fois cette chose effectuée, vous pouvez supprimer la licence de la boîte aux lettres de l’utilisateur. Ne supprimez pas l’ancienne boîte aux lettres de l’utilisateur. La boîte aux lettres partagée en a besoin comme ancre.
    
7. Ajoutez des membres à la boîte aux lettres partagée.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Reconvertissent une boîte aux lettres partagée en boîte aux lettres (privée) d’un utilisateur

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.
   
2. Sélectionnez **Destinataires** \> **partagés.**

3. Sélectionnez la boîte aux lettres partagée. Sous **Convertir en boîte aux lettres normale,** sélectionnez **Convertir.**

4. Revenir au Centre d’administration. Sous **Utilisateurs,** choisissez le compte d’utilisateur associé à l’ancienne boîte aux lettres partagée. Attribuez une licence au compte et réinitialisez le mot de passe.

   La mise en place de la boîte aux lettres prendra quelques minutes, mais après cela, la personne qui utilisera ce compte est prête à l’emploi. Lorsqu’ils se connectent, ils voient les éléments de courrier électronique et de calendrier qui se trouveraient dans la boîte aux lettres partagée.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Convertir la boîte aux lettres d’un utilisateur dans un environnement hybride

Pour plus d’informations sur la conversion d’une boîte aux lettres utilisateur en boîte aux lettres partagée dans un environnement Exchange hybride, voir :

 - [Cmdlets pour créer ou modifier une boîte aux lettres partagée à distance dans un environnement Exchange local](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
 - [Les boîtes aux lettres partagées sont converties de manière inattendue en boîtes aux lettres utilisateur après l’installation de la synchronisation d’annuaires dans Exchange déploiement hybride](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)
 

> [!NOTE]
> Si vous êtes membre du groupe de rôles Gestion de l’organisation ou Gestion des destinataires, vous pouvez utiliser l’Exchange Management Shell pour modifier une boîte aux lettres utilisateur en boîte aux lettres partagée en local. Par exemple, `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)