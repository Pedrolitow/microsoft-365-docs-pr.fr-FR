---
title: Supprimer un utilisateur de votre organisation
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
- SPO_Content
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Découvrez comment supprimer un compte d'utilisateur. Décidez de l'utilisation du courrier électronique de l'utilisateur et du contenu OneDrive. Et décidez s'il faut conserver la licence de produit ou arrêter de payer pour elle.
ms.openlocfilehash: 0069577b83c318fa57eaceddccc93b5832e634e0
ms.sourcegitcommit: 223a36a86753fe9cebee96f05ab4c9a144133677
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51759917"
---
# <a name="delete-a-user-from-your-organization"></a>Supprimer un utilisateur de votre organisation
  
**Vous cherchez à supprimer votre *propre compte* d'utilisateur Microsoft 365 que vous utilisez au travail ou à l'école ? Contactez le support technique de votre entreprise ou de votre université pour suivre ces étapes à votre place.**

## <a name="what-you-need-to-know-about-deleting-users"></a>Ce que vous devez savoir sur la suppression des utilisateurs

- Seules les personnes qui ont des autorisations d'administrateur global ou de gestion des utilisateurs [Microsoft 365](about-admin-roles.md) pour l'entreprise ou l'établissement scolaire peuvent supprimer des comptes d'utilisateur.
- Vous disposez de 30 jours pour [restaurer](restore-user.md) le compte avant que les données de l'utilisateur ne soient définitivement supprimées.
- Si vous voulez conserver les données OneDrive de l'utilisateur, déplacez-le à un autre emplacement. Vous pouvez même déplacer les données jusqu'à 30 jours après la suppression du compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md). Vous ne devez pas déplacer ses fichiers SharePoint ; vous y aurez toujours accès.
- Si vous souhaitez conserver les courriers de l'utilisateur, **AVANT** de supprimer le compte, déplacez les courriers vers un autre emplacement. Si vous avez déjà supprimé le compte depuis moins de 30 jours, vous pouvez le restaurer, déplacer les courriers, puis supprimer le compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md).
- Si vous avez un abonnement Entreprise comme Office 365 Entreprise E3, vous pouvez conserver les données de boîte aux lettres d'un compte d'utilisateur supprimé en le transformant en boîte aux lettres *inactive.* Pour en savoir plus, voir [Gestion des boîtes aux lettres inactives dans Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Administrateur global : supprimer un utilisateur, arrêter de payer pour sa licence et choisir ce qu'il faut faire avec son courrier électronique et son contenu OneDrive

Si vous êtes un administrateur général, lorsque vous supprimez un utilisateur, vous pouvez également accorder à un autre utilisateur l'accès à son courrier électronique et choisir l'utilisation de son contenu OneDrive.

### <a name="things-to-consider"></a>Éléments à prendre en considération...

Avant de commencer, réfléchissez à ce que vous voulez faire avec le courrier électronique de l'utilisateur et le contenu OneDrive, et si vous souhaitez conserver la licence ou arrêter de payer pour celle-ci.
  
|Élément | Description |
|:-----|:-----|
|Licences de produits  <br/> |Vous pouvez supprimer la licence de l'utilisateur et la supprimer de vos abonnements pour arrêter de payer pour cette licence. Si vous sélectionnez cette option, la licence sera automatiquement supprimée de vos abonnements.  <br/><br/> **Vous ne pouvez pas supprimer la licence si** vous l'avez achetée via un partenaire ou une licence en volume. Si vous payez pour une offre annuelle ou si vous êtes au milieu d'un cycle de facturation, vous ne pourrez pas supprimer la licence de votre abonnement tant que votre engagement n'est pas terminé.  <br/> |
|Contenu OneDrive  <br/> |Si l'utilisateur a enregistré ses fichiers dans OneDrive, vous pouvez accorder à un autre utilisateur l'accès à ces fichiers.  <br/><br/> Vous devez déplacer les fichiers que vous souhaitez conserver pendant la période de rétention définie pour les fichiers OneDrive. **Par défaut, la période de rétention est de 30 jours.** Si vous ne déplacez pas les fichiers au cours de la période de rétention après la suppression de l'utilisateur, le contenu OneDrive est supprimé définitivement. Pour augmenter le nombre de jours de conservation des fichiers OneDrive pour les comptes supprimés, voir Définir la rétention OneDrive pour [les utilisateurs supprimés.](/onedrive/set-retention)  <br/><br/> **Important !** Si l'utilisateur supprimé a utilisé un ordinateur personnel pour télécharger des fichiers à partir de SharePoint et OneDrive, vous ne pouvez pas effacer les fichiers qu'il a stockés sur son ordinateur. Ils continueront d'avoir accès à tous les fichiers qui ont été synchronisés à partir de OneDrive.           |
|E-mail  <br/> | Donner à un autre utilisateur l'accès au courrier électronique de l'utilisateur supprimé convertira la boîte aux lettres de l'utilisateur supprimé en boîte aux lettres partagée. Le nouveau propriétaire de la boîte aux lettres peut ensuite accéder à la boîte aux lettres et surveiller les nouveaux messages électroniques. Vous avez également les options suivantes :  <br/>  <br/>Modifier le nom complet : nous vous recommandons de modifier le nom d'affichage afin qu'il soit facile d'identifier la boîte aux lettres partagée dans la **liste** des utilisateurs actifs.  <br/>  Activer les réponses automatiques : nous avons déjà écrit une réponse automatique polie pour vous. Vous pouvez envoyer différentes réponses automatiques à des personnes au sein de votre organisation et à des personnes extérieures à votre organisation.  <br/> <br/> Nettoyer les alias : les alias sont des adresses de messagerie supplémentaires pour les utilisateurs. Certaines organisations ne les utilisent pas, donc si vous n'en avez pas, vous n'avez rien d'autre à faire ici. Si l'utilisateur a des alias, nous vous recommandons de les supprimer afin de pouvoir réutiliser ces adresses e-mail. Sinon, vous ne pouvez pas réutiliser ces adresses de messagerie tant que la période de rétention des boîtes aux lettres supprimées n'est pas écoulée. Par défaut, une boîte aux lettres supprimée est récupérable pendant 30 jours. Pour plus d'informations, voir [Supprimer ou restaurer des boîtes aux lettres utilisateur dans Exchange Online.](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox) <br/> |
|Active Directory  <br/> |Si votre entreprise utilise **Active Directory** qui se synchronise avec Azure Active Directory, vous devez supprimer le compte d'utilisateur d'Active Directory. Vous ne pouvez pas le faire via Office 365. Pour obtenir des instructions, [voir Supprimer un compte d'utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))  <br/> |

### <a name="get-started"></a>Démarrer

Étant donné que l'expérience guidée parcourt les étapes de suppression d'un utilisateur, voici comment commencer.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez l'utilisateur à supprimer, puis sélectionnez **Supprimer l'utilisateur.**

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrateur de gestion des utilisateurs : supprimer un ou plusieurs utilisateurs d'Office 365

> [!IMPORTANT]
> Ne supprimez pas le compte d'un utilisateur si vous l'avez converti en boîte aux lettres partagée ou si vous avez installé le forwarding de courrier sur le compte. [](../email/convert-user-mailbox-to-shared-mailbox.md) Ces fonctions ont toujours besoin du compte. Une boîte aux lettres partagée ne nécessite pas de licence. Si vous avez converti le compte en boîte aux lettres partagée, vous pouvez arrêter de [payer pour la licence.](#stop-paying-for-the-license) Si vous avez installé le forwarding de courrier sur le compte, vous ne pouvez pas supprimer la licence. Cela arrête le forwarding du courrier électronique et désactive la boîte aux lettres.
  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, sélectionnez **Plus d'options** (**...**), puis choisissez **Supprimer l'utilisateur.**

   Bien que vous avez supprimé le compte de l'utilisateur, **vous payez toujours pour la licence.** Consultez la procédure suivante pour arrêter de payer pour la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à quelqu'un.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, puis dans le volet **Actions** en bloc, choisissez **Supprimer des utilisateurs.**

   Bien que vous avez supprimé le compte de l'utilisateur, **vous payez toujours pour la licence.** Consultez la procédure suivante pour arrêter de payer pour la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à quelqu'un.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, puis dans le volet **Actions** en bloc, choisissez **Supprimer des utilisateurs.**

   Bien que vous avez supprimé le compte de l'utilisateur, **vous payez toujours pour la licence.** Consultez la procédure suivante pour arrêter de payer pour la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à quelqu'un.

::: moniker-end

### <a name="stop-paying-for-the-license"></a>Arrêter de payer la licence

La réduction du nombre de licences est une étape distincte qui ne peut être effectuée que par l'administrateur global ou l'administrateur de facturation.
  
::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>. Si cette option n'est pas disponible, vous n'êtes pas un administrateur global ou un administrateur de facturation et vous ne pouvez pas faire cette étape.

2. Sous **l'onglet** Produits, sélectionnez l'abonnement dont vous souhaitez supprimer des licences.

3. Sur la page des informations de l’abonnement, sélectionnez **Supprimer les licences**.

4. Dans le **volet Supprimer des licences,** sous Nouvelle **quantité,** dans la zone Nombre total de **licences,** entrez le nombre total de licences que vous souhaitez pour cet abonnement. Par exemple, si vous avez 100 licences et que vous souhaitez en supprimer cinq, entrez 95.

5. Sélectionnez **Enregistrer**.

Plus tard, lorsque vous suivrez les étapes pour ajouter une autre personne à votre entreprise, vous serez invité à acheter une licence en même temps, en une seule étape !

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>. Si cette option n'est pas disponible, vous n'êtes pas un administrateur global ou un administrateur de facturation et vous ne pouvez pas faire cette étape.

2. Sélectionnez l'abonnement (si vous en avez plusieurs), puis sélectionnez **Ajouter/Supprimer** des licences pour supprimer la licence afin de ne pas payer tant que vous n'avez pas embauché une autre personne.  

   Plus tard, lorsque vous suivrez les étapes pour ajouter une autre personne à votre entreprise, vous serez invité à acheter une licence en même temps, en une seule étape !

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>. Si cette option n'est pas disponible, vous n'êtes pas un administrateur global ou un administrateur de facturation et vous ne pouvez pas faire cette étape.

2. Sélectionnez l'abonnement (si vous en avez plusieurs), puis sélectionnez **Ajouter/Supprimer** des licences pour supprimer la licence afin de ne pas payer tant que vous n'avez pas embauché une autre personne.  

   Plus tard, lorsque vous suivrez les étapes pour ajouter une autre personne à votre entreprise, vous serez invité à acheter une licence en même temps, en une seule étape !

::: moniker-end

## <a name="delete-many-users-at-the-same-time"></a>Supprimer plusieurs utilisateurs en même temps

Voir [l'cmdlet Remove-MsolUser](https://go.microsoft.com/fwlink/p/?linkid=842230) PowerShell.

## <a name="fix-issues-with-deleting-a-user"></a>Résoudre les problèmes de suppression d'un utilisateur

Voici les problèmes les plus courants rencontrés par les utilisateurs lors de la suppression d'un utilisateur :
  
- **Un message d'erreur du type « Nous ne pouvons pas supprimer l'utilisateur. Merci de réessayer plus tard. » apparaît.** Vérifiez si le compte dispose d'un système de forwarding de courrier ou s'il a été converti en boîte aux lettres partagée. Ces deux situations peuvent être à l'origine de cette erreur. Ne supprimez pas le compte s'il a été converti en boîte aux lettres partagée ou s'il a été converti en boîte aux lettres partagée.

- **Vous n'avez pas les autorisations appropriées pour supprimer un utilisateur**. Seules les personnes qui sont des administrateurs globaux [Microsoft 365](about-admin-roles.md) ou des administrateurs de gestion des utilisateurs peuvent supprimer des utilisateurs. Il s'agit généralement du support technique de votre établissement scolaire ou de votre entreprise.

- **Lorsque vous supprimez l'utilisateur, son nom apparaît toujours dans votre carnet d'adresses global**. Cela se produit lorsqu'une entreprise utilise Active Directory. Vous devez supprimer le compte d'utilisateurs d'Active Directory. Pour obtenir des instructions, [voir Supprimer un compte d'utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Voulez-vous supprimer Microsoft 365 de votre ordinateur ? Go to [Cancel your subscription](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-articles"></a>Articles connexes

[Restaurer un utilisateur](restore-user.md)
  
[Supprimer définitivement une boîte aux lettres](/exchange/permanently-delete-a-mailbox-exchange-2013-help)

[Supprimer un ancien employé d'Office 365](remove-former-employee.md)

[Ajouter un nouvel employé à Office 365](add-new-employee.md)

[Supprimer un compte d'utilisateur](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)): utilisez ces instructions si votre entreprise utilise **Active Directory** qui se synchronise avec Azure AD. Vous ne pouvez pas utiliser Office 365.