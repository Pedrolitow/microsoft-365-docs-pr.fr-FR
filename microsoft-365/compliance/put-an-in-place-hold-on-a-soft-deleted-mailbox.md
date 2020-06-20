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
ms.openlocfilehash: 4dcd6539519675094da9a05c7701b9f8511ce9a1
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818863"
---
# <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-in-exchange-online"></a>Placer une conservation inaltérable dans une boîte aux lettres supprimée (récupérable) dans Exchange Online

Learn how to create an In-Place Hold for a soft-deleted mailbox to make it inactive and preserve its contents. Then you can use Microsoft eDiscovery tools to search the inactive mailbox.

> [!IMPORTANT]
> À mesure que nous continuons à investir de différentes manières pour conserver le contenu de la boîte aux lettres, nous annonçaons le retrait des conservations inaltérables dans le centre d’administration Exchange. À partir du 1er juillet 2020 vous ne pourrez pas créer de nouvelles conservations inaltérables dans Exchange Online. Toutefois, vous pourrez toujours gérer les conservations inaltérables dans le centre d’administration Exchange ou à l’aide de la cmdlet **Set-MailboxSearch** dans Exchange Online PowerShell. Toutefois, à partir du 1er octobre 2020, vous ne pourrez pas gérer les conservations inaltérables. Vous ne les supprimerez que dans le centre d’administration Exchange ou à l’aide de la cmdlet **Remove-MailboxSearch** . Pour plus d’informations sur le retrait des conservations inaltérables, consultez la rubrique [déclassement des outils eDiscovery hérités](legacy-ediscovery-retirement.md).
  
You might have a situation where a person has left your organization, and their corresponding user account and mailbox were deleted. Afterwards, you realize there's information in the mailbox that needs to be preserved. What can you do? If the deleted mailbox retention period hasn't expired, you can put an In-Place Hold on the deleted mailbox (called a  soft-deleted mailbox ) and make it an inactive mailbox. An  *inactive mailbox*  is used to preserve a former employee's email after he or she leaves your organization. The contents of an inactive mailbox are preserved for the duration of the In-Place Hold that was is placed on the soft-deleted mailbox when it was made inactive. Une fois la boîte aux lettres inactive, vous pouvez effectuer une recherche dans la boîte aux lettres en utilisant la découverte électronique inaltérable dans Exchange Online, la recherche de contenu dans le centre de sécurité & conformité ou le centre eDiscovery dans SharePoint Online. 
  
> [!NOTE]
> In Exchange Online, a soft-deleted mailbox is a mailbox that's been deleted but can be recovered within a specific retention period. The soft-deleted mailbox retention period in Exchange Online is 30 days. This means that the mailbox can be recovered (or made an inactive mailbox) within 30 days of being deleted. After 30 days, a soft-deleted mailbox is marked for permanent deletion and can't be recovered or made inactive. 
  
## <a name="requirements-for-in-place-holds"></a>Conditions requises pour les conservations inaltérables

- You have to use the **New-MailboxSearch** cmdlet in Windows PowerShell to put an In-Place Hold on a soft-deleted mailbox. You can't use the Exchange admin center (EAC) or the eDiscovery Center in SharePoint Online. 

- Pour apprendre à utiliser Windows PowerShell afin de vous connecter à Exchange Online, consultez la rubrique [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).

- Exécutez la commande suivante pour obtenir les informations d'identité sur les boîtes aux lettres supprimées (récupérables) de votre organisation. 

  ```powershell
  Get-Mailbox -SoftDeletedMailbox | FL Name,WhenSoftDeleted,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

- Pour plus d’informations sur les boîtes aux lettres inactives, consultez la rubrique [vue d’ensemble des boîtes aux lettres inactives dans Office 365](inactive-mailboxes-in-office-365.md).

## <a name="put-an-in-place-hold-on-a-soft-deleted-mailbox-to-make-it-an-inactive-mailbox"></a>Placer une conservation inaltérable sur une boîte aux lettres supprimée (récupérable) pour rendre la boîte aux lettres inactive

Use the **New-MailboxSearch** cmdlet to make a soft-deleted mailbox an inactive mailbox. For more information, see [New-MailboxSearch](https://technet.microsoft.com/library/74303b47-bb49-407c-a43b-590356eae35c.aspx).
  
1. Créez une variable contenant les propriétés de la boîte aux lettres supprimée (récupérable).

   ```powershell
   $SoftDeletedMailbox = Get-Mailbox -SoftDeletedMailbox -Identity <identity of soft-deleted mailbox>
   ```

    > [!IMPORTANT]
    > In the previous command, use the value of the **DistinguishedName** or **ExchangeGuid** property to identify the soft-deleted mailbox. These properties are unique for each mailbox in your organization, whereas it's possible that an active mailbox and a soft-deleted mailbox might have the same primary SMTP address. 
  
2. Create an In-Place Hold and place it on the soft-deleted mailbox. In this example, no hold duration is specified. This means items will be held indefinitely or until the hold is removed from the inactive mailbox.

   ```powershell
   New-MailboxSearch -Name "InactiveMailboxHold" -SourceMailboxes $SoftDeletedMailbox.DistinguishedName -InPlaceHoldEnabled $true
    ```

   You can also specify a hold duration when you create the In-Place Hold. This example holds items in the inactive mailbox for approximately 7 years.

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

After you make a soft-deleted mailbox an inactive mailbox, there are a number of ways you can manage the mailbox. For more information, see:
  
- [Modifier la durée de conservation pour une boîte aux lettres inactive](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Récupérer une boîte aux lettres inactive](recover-an-inactive-mailbox.md)

- [Restaurer une boîte aux lettres inactive](restore-an-inactive-mailbox.md)

- [Supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md) (en supprimant la conservation)
