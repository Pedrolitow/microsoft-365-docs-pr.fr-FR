---
title: Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Découvrez comment convertir une boîte aux lettres privée en boîte aux lettres partagée accessible par plusieurs personnes au lieu d’une seule personne. '
ms.openlocfilehash: 9fa1b0c3d5ee3735b73a25607cf663edff69928b
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726351"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée

Lorsque vous convertissez la boîte aux lettres d’un utilisateur en boîte aux lettres partagée, tous les courriers électroniques et calendriers existants sont conservés. Ce n’est que maintenant qu’il se trouve dans une boîte aux lettres partagée où plusieurs personnes pourront y accéder au lieu d’une seule personne. À une date ultérieure, vous pourrez reconverti une boîte aux lettres partagée en boîte aux lettres utilisateur (privée).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="before-you-begin"></a>Avant de commencer

**Voici quelques éléments très importants que vous devez savoir** :

- La boîte aux lettres utilisateur a besoin d’une licence qui lui est affectée avant de la convertir en boîte aux lettres partagée. Sinon, vous ne verrez pas l’option permettant de convertir la boîte aux lettres. Si vous avez supprimé la licence, rajoutez-la pour pouvoir convertir la boîte aux lettres. Après avoir converti la boîte aux lettres de l’utilisateur en boîte aux lettres partagée, vous pouvez supprimer la licence du compte de l’utilisateur.

- Sans licence, les boîtes aux lettres partagées sont limitées à 50 Go. Vous devrez peut-être supprimer un ensemble de messages volumineux (par exemple, des messages avec pièces jointes) de la boîte aux lettres partagée pour la réduire afin de pouvoir supprimer la licence.

  Pour augmenter la limite de taille à 100 Go, attribuez une licence Exchange Online Plan 2 à la boîte aux lettres partagée.

  Si vous attribuez une licence Exchange Online Plan 1 et une licence de module complémentaire Archivage Exchange Online à la boîte aux lettres partagée, vous pouvez activer l’archivage à extension automatique pour une capacité de stockage d’archivage supplémentaire.

- Ne supprimez pas le compte de l’ancien utilisateur, car le compte est requis pour ancrer la boîte aux lettres partagée. Si vous avez déjà supprimé le compte d’utilisateur, consultez [Convertir la boîte aux lettres d’un utilisateur supprimé](#convert-the-mailbox-of-a-deleted-user).

- Vous n’avez pas besoin de réinitialiser le mot de passe du compte de la boîte aux lettres de l’utilisateur. Toutefois, si vous ne réinitialisez pas le mot de passe, **le nom d’utilisateur et le mot de passe d’origine continueront de fonctionner sur la boîte aux lettres partagée** une fois la conversion terminée.

- Les règles de boîte de réception sont conservées après la conversion de la boîte aux lettres utilisateur en boîte aux lettres partagée.

- Pour placer une conservation In-Place ou une conservation pour litige sur une boîte aux lettres partagée, vous devez attribuer une licence Exchange Online Plan 2 *ou* une licence Exchange Online Plan 1 et une licence d’extension Archivage Exchange Online à la boîte aux lettres partagée.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Utiliser le Centre d’administration Exchange classique pour convertir une boîte aux lettres

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange classique</a>.

2. Sélectionnez **Destinataires** \> **boîtes aux lettres**.

3. Sélectionnez la boîte aux lettres de l’utilisateur. Sous **Convertir en boîte aux lettres partagée**, sélectionnez **Convertir**.

4. Si la boîte aux lettres est inférieure à 50 Go, vous pouvez supprimer la [licence de l’utilisateur](../manage/remove-licenses-from-users.md) et arrêter de la payer. Ne supprimez pas le compte de l’utilisateur. La boîte aux lettres partagée en a besoin comme ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Pour plus d’informations, consultez [Supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).

Pour tout ce que vous devez savoir sur les boîtes aux lettres partagées, consultez [À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) et [Créer une boîte aux lettres partagée](create-a-shared-mailbox.md).

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Utiliser le Nouveau centre d’administration Exchange pour convertir une boîte aux lettres

1. Accédez au <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> Centre d’administration Exchange</a>.

2. Sélectionnez **Destinataires** \> **boîtes aux lettres**.

3. Sélectionnez la boîte aux lettres de l’utilisateur. Sous l’onglet **Autres** , sélectionnez **Convertir en boîte aux lettres partagée**.

4. Si la boîte aux lettres est inférieure à 50 Go, vous pouvez supprimer la [licence de l’utilisateur](../manage/remove-licenses-from-users.md) et arrêter de la payer. Ne supprimez pas le compte de l’utilisateur. La boîte aux lettres partagée en a besoin comme ancre. Si vous convertissez la boîte aux lettres d’un employé qui quitte votre organisation, vous devez prendre des mesures supplémentaires pour vous assurer qu’il ne peut plus se connecter. Consultez [Supprimer un ancien employé de Microsoft 365](../add-users/remove-former-employee.md).

Pour tout ce que vous devez savoir sur les boîtes aux lettres partagées, consultez [À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) et [Créer une boîte aux lettres partagée](create-a-shared-mailbox.md).

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Convertir la boîte aux lettres d’un utilisateur supprimé

Après avoir supprimé un compte d’utilisateur, procédez comme suit pour convertir son ancienne boîte aux lettres en boîte aux lettres de partage :

1. [Restaurez le compte de l’utilisateur](../add-users/restore-user.md).

2. Vérifiez qu’une licence Microsoft 365 lui est affectée.

3. Réinitialisez le mot de passe de l’utilisateur.

4. Attendez 20 à 30 minutes que leur boîte aux lettres soit recréé.

5. Une fois la boîte aux lettres recréé, supprimez la licence de la boîte aux lettres de l’utilisateur. Ne supprimez pas l’ancienne boîte aux lettres de l’utilisateur. La boîte aux lettres partagée en a besoin comme ancre.

6. Ajoutez des membres à la boîte aux lettres partagée.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Convertir une boîte aux lettres partagée en boîte aux lettres (privée) d’un utilisateur

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Sélectionnez **Destinataires** \> **partagés**.

3. Sélectionnez la boîte aux lettres partagée. Sous **Convertir en boîte aux lettres standard**, sélectionnez **Convertir**.

4. Retour au centre d’administration. Sous **Utilisateurs**, choisissez le compte d’utilisateur associé à l’ancienne boîte aux lettres partagée. Attribuez une licence au compte, puis réinitialisez le mot de passe.

   La configuration de la boîte aux lettres prend quelques minutes, mais après cela, la personne qui va utiliser ce compte est prête à partir. Lorsqu’ils se connectent, ils voient les éléments de courrier électronique et de calendrier qui se trouveraient auparavant dans la boîte aux lettres partagée.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Convertir la boîte aux lettres d’un utilisateur dans un environnement hybride

Pour plus d’informations sur la conversion d’une boîte aux lettres utilisateur en boîte aux lettres partagée dans un environnement Exchange hybride, consultez :

- [Applets de commande pour créer ou modifier une boîte aux lettres partagée distante dans un environnement Exchange local](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
- [Les boîtes aux lettres partagées sont converties de manière inattendue en boîtes aux lettres utilisateur après l’exécution de la synchronisation d’annuaires dans un déploiement hybride Exchange](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)

> [!NOTE]
> Si vous êtes membre du groupe de rôles Gestion de l’organisation ou Gestion des destinataires, vous pouvez utiliser Exchange Management Shell pour remplacer une boîte aux lettres utilisateur par une boîte aux lettres partagée localement. Par exemple : `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
