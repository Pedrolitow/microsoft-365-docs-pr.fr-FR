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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- SPO_Content
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Découvrez comment supprimer un compte d’utilisateur Microsoft 365, comment faire avec l’e-mail de l’utilisateur et OneDrive contenu, et s’il faut conserver la licence de produit.
ms.openlocfilehash: faa971fa8419f6bcc80855fd9dcd559a542e00a8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436776"
---
# <a name="delete-a-user-from-your-organization"></a>Supprimer un utilisateur de votre organisation
  
**Vous recherchez comment supprimer votre *propre* compte d’utilisateur Microsoft 365 que vous utilisez au travail ou à l’école ? Contactez le support technique de votre travail ou de votre université pour effectuer ces étapes à votre place.**

## <a name="before-you-begin"></a>Avant de commencer

- Seules les personnes qui disposent [d’Microsoft 365 autorisations d’administrateur général](about-admin-roles.md) ou de gestion des utilisateurs pour l’entreprise ou l’école peuvent supprimer des comptes d’utilisateur.
- Vous disposez de 30 jours pour [restaurer](restore-user.md) le compte avant que les données de l'utilisateur ne soient définitivement supprimées.
- Si vous voulez conserver les données OneDrive de l'utilisateur, déplacez-le à un autre emplacement. Vous pouvez même déplacer les données jusqu’à 30 jours après la suppression du compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md). Vous ne devez pas déplacer ses fichiers SharePoint ; vous y aurez toujours accès.
- Si vous souhaitez conserver les courriers de l'utilisateur, **AVANT** de supprimer le compte, déplacez les courriers vers un autre emplacement. Si vous avez déjà supprimé le compte depuis moins de 30 jours, vous pouvez le restaurer, déplacer les courriers, puis supprimer le compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md).
- Si vous avez un abonnement Enterprise comme Office 365 Entreprise E3, vous pouvez conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé en le transformant en *boîte aux lettres inactive*. Pour en savoir plus, voir [Gestion des boîtes aux lettres inactives dans Exchange Online](../../compliance/inactive-mailboxes-in-office-365.md).

## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Administrateur général : Supprimer un utilisateur, arrêter de payer sa licence et choisir ce qu’il faut faire avec son e-mail et OneDrive contenu

Si vous êtes administrateur général, lorsque vous supprimez un utilisateur, vous pouvez également accorder à un autre utilisateur l’accès à son courrier électronique et choisir ce qu’il faut faire avec son contenu OneDrive.

### <a name="things-to-consider"></a>Informations importantes

Avant de commencer, réfléchissez à ce que vous voulez faire avec l’e-mail de l’utilisateur et OneDrive contenu, et si vous souhaitez conserver la licence ou arrêter de payer pour elle.
  
|Élément | Description |
|:-----|:-----|
|Licences de produit  <br/> |Vous pouvez supprimer la licence de l’utilisateur et la supprimer de vos abonnements pour arrêter de payer cette licence. Si vous sélectionnez cette option, la licence sera supprimée automatiquement de vos abonnements.  <br/><br/> **Vous ne pouvez pas supprimer la licence** si vous l’avez achetée par le biais d’un partenaire ou d’une licence en volume. Si vous payez pour un plan annuel ou si vous êtes au milieu d’un cycle de facturation, vous ne pourrez pas supprimer la licence de votre abonnement tant que votre engagement n’est pas terminé.  <br/> |
|contenu OneDrive  <br/> |Si l’utilisateur a enregistré ses fichiers dans OneDrive, vous pouvez accorder à un autre utilisateur l’accès à ces fichiers.  <br/><br/> Vous devez déplacer les fichiers que vous souhaitez conserver dans la période de rétention définie pour OneDrive fichiers. **Par défaut, la période de rétention est de 30 jours.** Si vous ne déplacez pas les fichiers dans la période de rétention après la suppression de l’utilisateur, le OneDrive de l’utilisateur supprimé est déplacé vers la corbeille de la collection de sites, où elle est conservée pendant 93 jours. Pendant ce temps, les utilisateurs ne pourront plus accéder à du contenu partagé dans le OneDrive. Pour restaurer la OneDrive, vous devez utiliser PowerShell. Pour plus d’informations, consultez [Restaurer un OneDrive supprimé](/onedrive/restore-deleted-onedrive).<br/><br/> Pour augmenter le nombre de jours pendant lesquels vous conservez OneDrive fichiers pour les comptes supprimés, consultez [Définir la rétention OneDrive pour les utilisateurs supprimés](/onedrive/set-retention).  <br/><br/> **Important!** Si l’utilisateur supprimé a utilisé un ordinateur personnel pour télécharger des fichiers à partir de SharePoint et OneDrive, il n’existe aucun moyen de réinitialiser les fichiers qu’il a stockés sur son ordinateur. Ils continueront d’avoir accès à tous les fichiers qui ont été synchronisés à partir de OneDrive.           |
|E-mail  <br/> | Accorder à un autre utilisateur l’accès à l’e-mail de l’utilisateur supprimé convertit la boîte aux lettres de l’utilisateur supprimé en boîte aux lettres partagée. Le nouveau propriétaire de boîte aux lettres peut ensuite accéder à la boîte aux lettres et surveiller le nouvel e-mail. Vous disposez également des options suivantes :  <br/>  <br/>Modifier le nom d’affichage : nous vous recommandons de modifier le nom d’affichage afin qu’il soit facile d’identifier la boîte aux lettres partagée dans la liste **des utilisateurs actifs** .  <br/>  <br/>  Activer les réponses automatiques : nous avons déjà écrit une réponse automatique polie pour vous. Vous pouvez envoyer différentes réponses automatiques à des personnes au sein de votre organisation et à des personnes extérieures à votre organisation. <br/> <br/> [Supprimez toutes les autorisations de calendrier existantes](/powershell/module/exchange/remove-mailboxfolderpermission?view=exchange-ps) à l’aide de PowerShell. <br/> <br/> Nettoyer les alias : les alias sont des adresses e-mail supplémentaires pour les utilisateurs. Certaines organisations ne les utilisent pas, donc si vous n’en avez pas, vous n’avez rien à faire d’autre ici. Si l’utilisateur a des alias, nous vous recommandons de les supprimer afin que vous puissiez réutiliser ces adresses e-mail. Sinon, vous ne pouvez pas réutiliser ces adresses e-mail tant que la période de rétention des boîtes aux lettres supprimées n’est pas passée. Par défaut, une boîte aux lettres supprimée peut être récupérée pendant 30 jours. Pour plus d’informations, consultez [Supprimer ou restaurer des boîtes aux lettres utilisateur dans Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Si votre entreprise utilise **Active Directory** qui se synchronise avec Azure Active Directory, vous devez supprimer le compte d'utilisateur d'Active Directory. Vous ne pouvez pas le faire via Office 365. Pour obtenir des instructions, consultez [Supprimer un compte d’utilisateur](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).  <br/> |

### <a name="get-started"></a>Prise en main

Étant donné que l’expérience guidée décrit les étapes de suppression d’un utilisateur, voici comment commencer.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez l’utilisateur à supprimer, puis **sélectionnez Supprimer l’utilisateur**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrateur de gestion des utilisateurs : Supprimer un ou plusieurs utilisateurs de Office 365

> [!IMPORTANT]
> Ne supprimez pas le compte d’un utilisateur si vous l’avez [converti en boîte aux lettres partagée](../email/convert-user-mailbox-to-shared-mailbox.md) ou si vous avez configuré le transfert de courrier sur le compte. Ces fonctions ont toujours besoin du compte. Une boîte aux lettres partagée ne nécessite pas de licence. Si vous avez converti le compte en boîte aux lettres partagée, vous pouvez [arrêter de payer pour la licence](#stop-paying-for-the-license). Si vous avez configuré le transfert d’e-mail sur le compte, vous ne pouvez pas supprimer la licence. Cela permet d’arrêter le transfert d’e-mail et de désactiver la boîte aux lettres.
  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, sélectionnez les trois points (autres actions), puis choisissez  **Supprimer l’utilisateur**.

   Bien que vous ayez supprimé le compte de l’utilisateur, **vous payez toujours la licence**. Consultez la procédure suivante pour arrêter le paiement de la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à quelqu’un.

### <a name="stop-paying-for-the-license"></a>Arrêter de payer la licence

La réduction du nombre de licences est une étape distincte qui ne peut être effectuée que par l’administrateur général ou l’administrateur de facturation.
  
::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.
::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Produits</a>.
::: moniker-end

2. Sous l’onglet **Produits** , sélectionnez l’abonnement pour lequel vous souhaitez supprimer les licences.

3. Sur la page des informations de l’abonnement, sélectionnez **Supprimer les licences**.

4. Dans le volet **Supprimer les licences** , sous **Nouvelle quantité**, dans la zone **Total des licences** , entrez le nombre total de licences souhaitées pour cet abonnement. Par exemple, si vous avez 100 licences et que vous souhaitez en supprimer cinq, entrez 95.

5. Sélectionnez **Enregistrer**.

Plus tard, lorsque vous passerez par les étapes pour ajouter une autre personne à votre entreprise, vous serez invité à acheter une licence en même temps, avec une seule étape!

## <a name="delete-many-users-at-the-same-time"></a>Supprimer de nombreux utilisateurs en même temps

Consultez l’applet [de commande PowerShell Remove-MsolUser](/powershell/module/msonline/remove-msoluser) .

## <a name="fix-issues-with-deleting-a-user"></a>Résoudre les problèmes de suppression d'un utilisateur

Voici les problèmes les plus courants rencontrés lors de la suppression d’un utilisateur :
  
- **Un message d'erreur du type « Nous ne pouvons pas supprimer l'utilisateur. Merci de réessayer plus tard. » apparaît.** Vérifiez si le transfert de courrier électronique est configuré sur le compte ou s’il a été converti en boîte aux lettres partagée. Ces deux situations peuvent être à l'origine de cette erreur. Ne supprimez pas le compte s’il a été transféré par e-mail ou s’il a été converti en boîte aux lettres partagée.

- **Vous n'avez pas les autorisations appropriées pour supprimer un utilisateur**. Seules les personnes qui sont [Microsoft 365 administrateurs généraux ou administrateurs de gestion des utilisateurs](about-admin-roles.md) peuvent supprimer des utilisateurs. Il s'agit généralement du support technique de votre établissement scolaire ou de votre entreprise.

- **Lorsque vous supprimez l'utilisateur, son nom apparaît toujours dans votre carnet d'adresses global**. Cela se produit lorsqu'une entreprise utilise Active Directory. Vous devez supprimer le compte d’utilisateurs d’Active Directory. Pour obtenir des instructions, consultez [Supprimer un compte d’utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))

**Voulez-vous supprimer Microsoft 365 de votre ordinateur ? Accédez à [Annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).**

## <a name="related-content"></a>Contenu connexe

[Restaurer un utilisateur](restore-user.md) (article)\
[Supprimer définitivement une boîte aux lettres](/exchange/permanently-delete-a-mailbox-exchange-2013-help) (article)\
[Supprimer un ancien employé de Office 365](remove-former-employee.md) (article)\
[Ajouter un nouvel employé à Office 365](add-new-employee.md) (article)\
[Supprimer un compte d’utilisateur](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)) : suivez ces instructions si votre entreprise utilise **Active Directory** qui se synchronise avec Azure AD. Vous ne pouvez pas utiliser Office 365. (article)
