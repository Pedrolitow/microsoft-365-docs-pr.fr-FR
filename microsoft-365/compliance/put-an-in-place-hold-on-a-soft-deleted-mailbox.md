---
title: Placer une conservation inaltérable dans une boîte aux lettres supprimée (récupérable) dans Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: ''
ms.assetid: 421f72bd-dd43-4be1-82f5-0ae9ac43bd00
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment créer une conservation inaltérable pour une boîte aux lettres supprimée (récupérable) pour la rendre inactive et conserver son contenu.
ms.openlocfilehash: 906ae8aded9bdf996f89c01db5ada6a36b00d77e
ms.sourcegitcommit: f358e321f7e81eff425fe0f0db1be0f3348d2585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2021
ms.locfileid: "58507541"
---
# <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-in-exchange-online"></a>Placer une conservation inaltérable dans une boîte aux lettres supprimée (récupérable) dans Exchange Online

Découvrez comment créer une conservation inaltérable pour une boîte aux lettres supprimée (récupérable) pour la rendre inactive et conserver son contenu. Vous pouvez ensuite utiliser les outils de découverte électronique Microsoft pour rechercher la boîte aux lettres inactive.

> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes façons pour conserver le contenu des boîtes aux lettres, nous andélisons le retrait des conservations In-Place dans le Centre d’administration Exchange (EAC). À compter du 1er juillet 2020, vous ne pourrez plus créer de In-Place de Exchange Online. Toutefois, vous pourrez toujours gérer les In-Place dans le EAC ou à l’aide de la cmdlet **Set-MailboxSearch** dans Exchange Online PowerShell. Toutefois, à compter du 1er octobre 2020, vous ne pourrez plus gérer les In-Place' Vous ne les supprimerez que dans le EAC ou à l’aide de la cmdlet **Remove-MailboxSearch.** Pour plus d’informations sur le retrait des In-Place, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)

You might have a situation where a person has left your organization, and their corresponding user account and mailbox were deleted. Afterwards, you realize there's information in the mailbox that needs to be preserved. What can you do? Si la période de rétention de la boîte aux lettres supprimée n’a pas expiré, vous pouvez placer une conservation In-Place sur la boîte aux lettres supprimée (appelée boîte aux lettres supprimée (suppression possible) et en faire une boîte aux lettres inactive. An  *inactive mailbox*  is used to preserve a former employee's email after he or she leaves your organization. The contents of an inactive mailbox are preserved for the duration of the In-Place Hold that was is placed on the soft-deleted mailbox when it was made inactive. Une fois la boîte aux lettres inactive, vous pouvez effectuer une recherche dans la boîte aux lettres à l’aide d’un outil eDiscovery dans le Centre de conformité Microsoft 365.

> [!NOTE]
> Dans Exchange Online, une boîte aux lettres supprimée (récupérable) est une boîte aux lettres qui a été supprimée mais qui peut être récupérée pendant une période de rétention spécifique. Le délai de rétention d'une boîte aux lettres supprimée (récupérable) dans Exchange Online est de 30 jours. Ainsi, la boîte aux lettres peut être récupérée (ou rendue inactive) dans les 30 jours qui suivent le moment où elle a été supprimée (récupérable). Après 30 jours, une boîte aux lettres supprimée (récupérable) est marquée pour suppression définitive et ne peut pas être récupérée ou rendue inactive.

## <a name="requirements-for-in-place-holds"></a>Conditions requises pour les In-Place de sécurité

- Vous devez utiliser l'applet de commande **New-MailboxSearch** dans Windows PowerShell pour placer une conservation inaltérable sur une boîte aux lettres supprimée (récupérable). Vous ne pouvez pas utiliser le Centre d'administration Exchange (CAE) ni le centre de découverte électronique SharePoint Online.

- Pour apprendre à utiliser Windows PowerShell afin de vous connecter à Exchange Online, consultez la rubrique [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Exécutez la commande suivante pour obtenir les informations d'identité sur les boîtes aux lettres supprimées (récupérables) de votre organisation.

  ```powershell
  Get-Mailbox -SoftDeletedMailbox | FL Name,WhenSoftDeleted,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

- Pour plus d’informations sur les boîtes aux lettres inactives, voir Vue d’ensemble des boîtes aux lettres [inactives Office 365](inactive-mailboxes-in-office-365.md).

## <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-to-make-it-an-inactive-mailbox"></a>Placer une conservation inaltérable sur une boîte aux lettres supprimée (récupérable) pour rendre la boîte aux lettres inactive

Utilisez l'applet de commande **New-MailboxSearch** pour rendre inactive une boîte aux lettres supprimée (récupérable). Pour plus d'informations, voir [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch).

1. Créez une variable contenant les propriétés de la boîte aux lettres supprimée (récupérable).

   ```powershell
   $SoftDeletedMailbox = Get-Mailbox -SoftDeletedMailbox -Identity <identity of soft-deleted mailbox>
   ```

    > [!IMPORTANT]
    > Dans la commande précédente, utilisez la valeur de la propriété **DistinguishedName** ou **ExchangeGuid** pour identifier la boîte aux lettres supprimée (récupérable). Ces propriétés sont uniques pour chaque boîte aux lettres de votre organisation, alors qu'une boîte aux lettres active et une boîte aux lettres supprimée (récupérable) peuvent avoir la même adresse SMTP principale.

2. Créez une conservation inaltérable et placez-la sur la boîte aux lettres supprimée (récupérable). Dans cet exemple, aucune durée de suspension n'est spécifiée. Cela signifie que les éléments seront suspendus indéfiniment ou jusqu'à ce que la suspension soit supprimée de la boîte aux lettres inactive.

   ```powershell
   New-MailboxSearch -Name "InactiveMailboxHold" -SourceMailboxes $SoftDeletedMailbox.DistinguishedName -InPlaceHoldEnabled $true
    ```

   Vous pouvez également spécifier une durée de suspension lorsque vous créez la conservation inaltérable. Cet exemple conserve des éléments de la boîte aux lettres inactive pendant environ sept ans.

   ```powershell
   New-MailboxSearch -Name "InactiveMailboxHold" -SourceMailboxes $SoftDeletedMailbox.DistinguishedName -InPlaceHoldEnabled $true -ItemHoldPeriod 2777
   ```

3. Après un certain temps, exécutez l'une des commandes suivantes pour vérifier que la boîte aux lettres supprimée (récupérable) est une boîte aux lettres inactive.

   ```powershell
   Get-Mailbox -InactiveMailboxOnly
   ```

    Ou

   ```powershell
   Get-Mailbox -InactiveMailboxOnly -Identity $SoftDeletedMailbox.DistinguishedName  | FL IsInactiveMailbox
   ```

## <a name="more-information"></a>Plus d’informations

Une fois la boîte aux lettres supprimée (récupérable) devenue inactive, il existe plusieurs façons de gérer la boîte aux lettres. Pour plus d’informations, voir :

- [Modifier la durée de conservation pour une boîte aux lettres inactive](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Récupérer une boîte aux lettres inactive](recover-an-inactive-mailbox.md)

- [Restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md)

- [Supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md) (en supprimant la boîte aux lettres en attente)