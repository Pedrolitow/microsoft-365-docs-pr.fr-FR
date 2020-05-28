---
title: Supprimer un utilisateur de votre organisation
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
- SPO_Content
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: d5155593-3bac-4d8d-9d8b-f4513a81479e
description: Découvrez comment supprimer un compte d’utilisateur. Déterminez ce qu’il convient de faire avec le courrier électronique de l’utilisateur, le contenu OneDrive, et s’il faut conserver la licence de produit ou cesser de le payer.
ms.openlocfilehash: 4102fe4ac297a1f426b3bf575e748a72b323ebb6
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44387188"
---
# <a name="delete-a-user-from-your-organization"></a>Supprimer un utilisateur de votre organisation
  
||
|:-----|
|**Vous recherchez comment supprimer votre *propre* compte d’utilisateur Microsoft 365 que vous utilisez au travail ou à l’école ? Contactez le support technique de votre entreprise ou de votre Université pour effectuer ces étapes pour vous.**|
   
## <a name="what-you-need-to-know-about-deleting-users"></a>Ce que vous devez savoir sur la suppression des utilisateurs

- Seules les personnes disposant des autorisations d' [administrateur général Microsoft 365](about-admin-roles.md) ou de gestion des utilisateurs de l’entreprise ou de l’établissement scolaire peuvent supprimer des comptes d’utilisateur. 
    
- Vous disposez de 30 jours pour [restaurer](restore-user.md) le compte avant que les données de l'utilisateur ne soient définitivement supprimées. 
    
- Si vous voulez conserver les données OneDrive de l'utilisateur, déplacez-le à un autre emplacement. Vous pouvez même effectuer cette opération 30 jours après la suppression du compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md). Vous ne devez pas déplacer ses fichiers SharePoint ; vous y aurez toujours accès.
    
- Si vous souhaitez conserver les courriers de l'utilisateur, **AVANT** de supprimer le compte, déplacez les courriers vers un autre emplacement. Si vous avez déjà supprimé le compte depuis moins de 30 jours, vous pouvez le restaurer, déplacer les courriers, puis supprimer le compte. Voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md).
    
- Si vous disposez d’un abonnement Enterprise comme Office 365 entreprise E3, vous pouvez conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé en le transformant en *boîte aux lettres inactive*. Pour en savoir plus, voir [Gestion des boîtes aux lettres inactives dans Exchange Online](https://docs.microsoft.com/microsoft-365/compliance/inactive-mailboxes-in-office-365).


## <a name="global-admin-delete-a-user-stop-paying-for-their-license-and-choose-what-to-do-with-their-email-and-onedrive-content"></a>Administrateur général : supprimez un utilisateur, arrêtez le paiement de sa licence, puis choisissez ce qu’il faut faire avec sa messagerie électronique et son contenu OneDrive

Si vous êtes un administrateur général, lorsque vous supprimez un utilisateur, vous pouvez également accorder à un autre utilisateur l’accès à sa messagerie et choisir ce qu’il doit faire avec son contenu OneDrive. 

  
### <a name="things-to-consider"></a>Éléments à prendre en considération...

Avant de commencer, réfléchissez à ce que vous voulez faire avec le courrier électronique de l’utilisateur et le contenu OneDrive, et si vous souhaitez conserver la licence ou cesser de le payer.
  
|||
|:-----|:-----|
|Licences de produits  <br/> |Vous pouvez supprimer la licence de l’utilisateur et la supprimer de vos abonnements pour arrêter le paiement de cette licence. Si vous sélectionnez cette option, la licence est automatiquement supprimée de vos abonnements.  <br/><br/> **Vous ne pouvez pas supprimer la licence** si vous l’avez achetée par le biais d’un partenaire ou d’une licence en volume. Si vous payez un forfait annuel ou si vous êtes au milieu d’un cycle de facturation, vous ne pourrez pas supprimer la licence de votre abonnement tant que votre engagement n’est pas terminé.  <br/> |
|Contenu OneDrive  <br/> |Si l’utilisateur a enregistré ses fichiers dans OneDrive, vous pouvez donner un accès à ces fichiers à un autre utilisateur.  <br/><br/> Vous devez déplacer les fichiers que vous souhaitez conserver pendant la période de rétention définie pour les fichiers OneDrive. **Par défaut, la période de rétention est de 30 jours.** Si vous ne déplacez pas les fichiers pendant la période de rétention après la suppression de l’utilisateur, le contenu OneDrive sera définitivement supprimé. Pour augmenter le nombre de jours de conservation des fichiers OneDrive pour les comptes supprimés, consultez [la rubrique Set the onedrive Retention for Deleted Users](https://docs.microsoft.com/onedrive/set-retention).  <br/><br/> **Indispensables!** Si l’utilisateur supprimé a utilisé un ordinateur personnel pour télécharger des fichiers à partir de SharePoint et OneDrive, il n’existe aucun moyen d’effacer les fichiers qu’ils stockent sur leur ordinateur. Ils continueront à avoir accès à tous les fichiers qui ont été synchronisés à partir de OneDrive.           |
|E-mail  <br/> | Accorder à un autre utilisateur l’accès au courrier électronique de l’utilisateur supprimé convertira la boîte aux lettres de l’utilisateur supprimé en boîte aux lettres partagée. Le nouveau propriétaire de la boîte aux lettres peut ensuite accéder à la boîte aux lettres et surveiller les nouveaux messages. Vous disposez également des options suivantes :  <br/>  <br/>Modifier le nom d’affichage : nous vous recommandons de modifier le nom complet afin qu’il soit facile d’identifier la boîte aux lettres partagée dans la liste des utilisateurs actifs.  <br/>  Activer les réponses automatiques : nous avons déjà écrit une réponse automatique poli pour vous. Vous pouvez envoyer des réponses automatiques différentes à des personnes au sein de votre organisation et à des personnes externes à votre organisation.  <br/> <br/> Nettoyer les alias : les alias sont des adresses de messagerie supplémentaires pour les utilisateurs. Certaines organisations ne les utilisent pas, donc si vous n’avez pas besoin d’effectuer d’autres actions ici. Si l’utilisateur possède des alias, nous vous recommandons de les supprimer afin de pouvoir réutiliser ces adresses de messagerie. Dans le cas contraire, vous ne pouvez pas réutiliser ces adresses de messagerie jusqu’à ce que la période de rétention des boîtes aux lettres supprimées soit passée. Par défaut, une boîte aux lettres supprimée est récupérable pendant 30 jours. Pour plus d’informations, consultez la rubrique [supprimer ou restaurer des boîtes aux lettres utilisateur dans Exchange Online](https://docs.microsoft.com/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes#delete-a-user-mailbox). <br/> |
|Active Directory  <br/> |Si votre entreprise utilise **Active Directory** qui se synchronise avec Azure Active Directory, vous devez supprimer le compte d'utilisateur d'Active Directory. Vous ne pouvez pas le faire via Office 365. Pour obtenir des instructions, consultez [la rubrique supprimer un compte d’utilisateur](https://go.microsoft.com/fwlink/p/?linkid=841808).  <br/> |
   
### <a name="get-started"></a>Prise en main

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

::: moniker-end

Étant donné que l’expérience guidée décrit les étapes de suppression d’un utilisateur, voici comment commencer.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez l’utilisateur à supprimer, puis **Supprimer l’utilisateur**.

## <a name="user-management-admin-delete-one-or-more-users-from-office-365"></a>Administrateur de gestion des utilisateurs : supprimer un ou plusieurs utilisateurs d’Office 365


> [!IMPORTANT]
> Ne supprimez pas le compte d’un utilisateur si vous l’avez [converti en boîte aux lettres partagée](../email/convert-user-mailbox-to-shared-mailbox.md) ou si vous avez configuré le transfert du courrier sur le compte. Ces fonctions ont toujours besoin du compte. Une boîte aux lettres partagée ne nécessite pas de licence. Si vous avez converti le compte en boîte aux lettres partagée, vous pouvez [arrêter le paiement de la licence](#stop-paying-for-the-license). Si vous avez configuré le transfert du courrier sur le compte, vous ne pouvez pas supprimer la licence. Cette opération arrêtera le transfert du courrier et désactivera la boîte aux lettres.
  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, sélectionnez **autres options** (**...**), puis **Supprimer l’utilisateur**.

   Même si vous avez supprimé le compte de l’utilisateur, **vous payez toujours pour la licence**. Consultez la procédure suivante pour cesser de payer la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à une personne.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, puis dans le volet **actions en bloc** , choisissez **supprimer des utilisateurs**.

   Même si vous avez supprimé le compte de l’utilisateur, **vous payez toujours pour la licence**. Consultez la procédure suivante pour cesser de payer la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à une personne.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les noms des utilisateurs que vous souhaitez supprimer, puis dans le volet **actions en bloc** , choisissez **supprimer des utilisateurs**.

   Même si vous avez supprimé le compte de l’utilisateur, **vous payez toujours pour la licence**. Consultez la procédure suivante pour cesser de payer la licence.  Vous pouvez également attribuer la licence à un autre utilisateur. Il ne sera pas attribué automatiquement à une personne.

::: moniker-end

### <a name="stop-paying-for-the-license"></a>Arrêter de payer la licence

La réduction du nombre de licences est une étape distincte qui ne peut être effectuée que par l’administrateur général ou l’administrateur de facturation. 
  
::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>. Si vous ne voyez pas cette option, vous n’êtes pas un administrateur général ni un administrateur de facturation, et vous ne pouvez pas effectuer cette étape.

2. Sélectionnez l’abonnement (si vous en avez plusieurs), puis sélectionnez **Ajouter/supprimer des licences** pour supprimer la licence afin de ne pas en payer avant d’embaucher une autre personne.  

   Plus tard, lorsque vous suivez les étapes pour ajouter une autre personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>. Si vous ne voyez pas cette option, vous n’êtes pas un administrateur général ni un administrateur de facturation, et vous ne pouvez pas effectuer cette étape.

2. Sélectionnez l’abonnement (si vous en avez plusieurs), puis sélectionnez **Ajouter/supprimer des licences** pour supprimer la licence afin de ne pas en payer avant d’embaucher une autre personne.  

   Plus tard, lorsque vous suivez les étapes pour ajouter une autre personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>. Si vous ne voyez pas cette option, vous n’êtes pas un administrateur général ni un administrateur de facturation, et vous ne pouvez pas effectuer cette étape.

2. Sélectionnez l’abonnement (si vous en avez plusieurs), puis sélectionnez **Ajouter/supprimer des licences** pour supprimer la licence afin de ne pas en payer avant d’embaucher une autre personne.  

   Plus tard, lorsque vous suivez les étapes pour ajouter une autre personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape.

::: moniker-end 

## <a name="delete-many-users-at-the-same-time"></a>Supprimer plusieurs utilisateurs en même temps

Voir la cmdlet PowerShell [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?linkid=842230) .

## <a name="fix-issues-with-deleting-a-user"></a>Résoudre les problèmes de suppression d'un utilisateur

Voici les problèmes les plus fréquemment rencontrés lors de la suppression d’un utilisateur :
  
- **Un message d'erreur du type « Nous ne pouvons pas supprimer l'utilisateur. Merci de réessayer plus tard. » apparaît.** Vérifiez si le transfert du courrier a été configuré sur le compte ou si le compte a été converti en boîte aux lettres partagée. Ces deux situations peuvent être à l'origine de cette erreur. Ne supprimez pas le compte s’il a été transféré vers une boîte aux lettres partagée.

- **Vous n'avez pas les autorisations appropriées pour supprimer un utilisateur**. Seules les personnes qui sont des administrateurs [globaux Microsoft 365 ou des administrateurs de gestion](about-admin-roles.md) des utilisateurs peuvent supprimer des utilisateurs. Il s'agit généralement du support technique de votre établissement scolaire ou de votre entreprise.

- **Lorsque vous supprimez l'utilisateur, son nom apparaît toujours dans votre carnet d'adresses global**. Cela se produit lorsqu'une entreprise utilise Active Directory. Vous devez supprimer le compte utilisateur dans Active Directory. Pour obtenir des instructions, consultez l'article TechNet suivant : [Supprimer un compte utilisateur.](https://go.microsoft.com/fwlink/p/?linkid=841808)

||
|:-----|
|**Voulez-vous supprimer Microsoft 365 de votre ordinateur ? Accédez à [annuler votre abonnement](../../commerce/subscriptions/cancel-your-subscription.md).**|
   
## <a name="related-articles"></a>Articles connexes

[Restaurer un utilisateur](restore-user.md)
  
[Supprimer définitivement une boîte aux lettres](https://technet.microsoft.com/library/jj863440%28v=exchg.150%29.aspx)

[Supprimer un ancien employé d'Office 365](remove-former-employee.md)

[Ajouter un nouvel employé à Office 365](add-new-employee.md)

[Supprimer un compte d’utilisateur](https://go.microsoft.com/fwlink/p/?linkid=841808): suivez ces instructions si votre entreprise utilise **Active Directory** qui se synchronise avec Azure ad. Vous ne pouvez pas utiliser Office 365.