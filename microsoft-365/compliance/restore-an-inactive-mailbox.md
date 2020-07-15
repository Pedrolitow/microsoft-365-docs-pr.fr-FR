---
title: Restaurer une boîte aux lettres inactive
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 97e06a7a-ef9a-4ce8-baea-18b9e20449a3
description: Découvrez comment restaurer (ou fusionner) le contenu d’une boîte aux lettres inactive dans une boîte aux lettres existante dans Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 34965832c32bfd4139f4b9a54d3999313aace476
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45127451"
---
# <a name="restore-an-inactive-mailbox"></a>Restaurer une boîte aux lettres inactive

Une boîte aux lettres inactive (qui est un type de boîte aux lettres supprimée (récupérable)) est utilisée pour conserver le courrier électronique d’un ancien employé une fois qu’il quitte votre organisation. Si un autre employé assume les responsabilités de l'employé qui est parti ou si ce dernier réintègre votre organisation, deux méthodes vous permettent de mettre à disposition le contenu de la boîte aux lettres inactive :
  
- **Restore an inactive mailbox** If another employee takes on the job responsibilities of the departed employee, or if another user needs access to the contents of the inactive mailbox, you can restore (or merge) the contents of the inactive mailbox to an existing mailbox. You can also restore the archive from an inactive mailbox. After it's restored, the inactive mailbox is preserved and is retained as an inactive mailbox. This topic describes the procedures for restoring an inactive mailbox.

- **Récupérer une boîte aux lettres inactive** Si l'employé qui est parti réintègre votre organisation, ou si un nouvel employé est embauché pour assumer les responsabilités de l'employé parti, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Cette méthode convertit la boîte aux lettres inactive en une nouvelle boîte aux lettres qui renferme le contenu de la boîte aux lettres inactive. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Pour connaître les procédures pas à pas, reportez-vous à la rubrique [récupérer une boîte aux lettres inactive dans Office 365](recover-an-inactive-mailbox.md).

Pour plus d’informations sur les différences entre la restauration et la récupération d’une boîte aux lettres inactive, reportez-vous à la section **plus d’informations** de cet article.
  
## <a name="requirements-to-restore-an-inactive-mailbox"></a>Conditions requises pour restaurer une boîte aux lettres inactive

- Vous devez utiliser Exchange Online PowerShell pour restaurer une boîte aux lettres inactive. Vous ne pouvez pas utiliser le Centre d'administration Exchange (CAE). Pour obtenir des instructions détaillées, consultez la rubrique [connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=396554).

- Exécutez la commande suivante dans Exchange Online PowerShell pour obtenir des informations d’identité pour les boîtes aux lettres inactives dans votre organisation.

    ```powershell
    Get-Mailbox -InactiveMailboxOnly | FL Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
    ```

     Utilisez les informations renvoyées par cette commande pour restaurer une boîte aux lettres inactive spécifique.

- Pour plus d’informations sur les boîtes aux lettres inactives, consultez la rubrique [inactive mailboxes in Office 365](inactive-mailboxes-in-office-365.md).

## <a name="restore-an-inactive-mailbox"></a>Restaurer une boîte aux lettres inactive

Use the **New-MailboxRestoreRequest** cmdlet with the  _SourceMailbox_ and  _TargetMailbox_ parameters to restore the contents of an inactive mailbox to an existing mailbox. For more information about using this cmdlet, see [New-MailboxRestoreRequest](https://go.microsoft.com/fwlink/?linkid=856298).
  
1. Créez une variable contenant les propriétés de la boîte aux lettres inactive.

    ```powershell
    $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
    ```

    > [!IMPORTANT]
    > In the previous command, use the value of the **DistinguishedName** or **ExchangeGUID** property to identify the inactive mailbox. These properties are unique for each mailbox in your organization, whereas it's possible that an active and an inactive mailbox might have the same primary SMTP address.
  
2. Restore the contents of the inactive mailbox to an existing mailbox. The contents of the inactive mailbox (source mailbox) will be merged into the corresponding folders in the existing mailbox (target mailbox).

    ```powershell
    New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox newemployee@contoso.com -AllowLegacyDNMismatch
    ```

   Alternatively, you can specify a top-level folder in the target mailbox in which to restore the contents from the inactive mailbox. If the specified target folder or target folder structure doesn't already exist in the target mailbox, it is created during the restore process. 

    Cet exemple copie les éléments et sous-dossiers depuis une boîte aux lettres inactive vers un dossier intitulé « Boîte aux lettres inactive » dans la structure de dossiers de premier niveau de la boîte aux lettres cible.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox newemployee@contoso.com -TargetRootFolder "Inactive Mailbox" -AllowLegacyDNMismatch
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Restaurer l'archive d'une boîte aux lettres inactive

If an inactive mailbox has an archive mailbox, you can also restore it to the archive mailbox of an existing mailbox. To restore the archive from an inactive mailbox, you have to add the  _SourceIsArchive_ and  _TargetIsAchive_ switches to the command used to restore an inactive mailbox.
  
1. Créez une variable contenant les propriétés de la boîte aux lettres inactive.

    ```powershell
    $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
    ```

    > [!NOTE]
    > In the previous command, use the value of the **DistinguishedName** or **ExchangeGUID** property to identify the inactive mailbox. These properties are unique for each mailbox in your organization, whereas it's possible that an active and an inactive mailbox might have the same primary SMTP address. 
  
2. Restore the contents of the archive from the inactive mailbox (source archive) to the archive of an existing mailbox (target archive). In this example, the contents from the source archive are copied to a folder named "Inactive Mailbox Archive" in the archive of the target mailbox.

    ```powershell
    New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox newemployee@contoso.com -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive" -AllowLegacyDNMismatch
    ```

## <a name="more-information"></a>Plus d’informations

- **Quelle est la principale différence entre la récupération et la restauration d'une boîte aux lettres inactive ?** Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est généralement convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d'utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus et les modifications apportées au contenu dans la nouvelle boîte aux lettres affectent le contenu placé en attente dans la boîte aux lettres inactive. À l'inverse, lorsque vous restaurez une boîte aux lettres inactive, le contenu est simplement copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. Toute modification apportée au contenu de la boîte aux lettres cible n'affecte pas le contenu d'origine conservé dans la boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l’objet d’une recherche à l’aide de l' [outil de recherche de contenu](content-search.md), son contenu peut être restauré vers une autre boîte aux lettres ou il peut être récupéré ou supprimé ultérieurement.

- **How do you find inactive mailboxes?** To get a list of the inactive mailboxes in your organization and display information that is useful for restoring an inactive mailbox, you can run this command.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | FL Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Utilisez une conservation pour litige ou une stratégie de rétention Microsoft 365 pour conserver le contenu de boîte aux lettres inactive.** Si vous souhaitez conserver l’état d’une boîte aux lettres inactive après sa restauration, vous pouvez placer la boîte aux lettres cible en [conservation pour litige](https://go.microsoft.com/fwlink/?linkid=856286) ou appliquer une [stratégie de rétention Microsoft 365](retention.md) avant de restaurer la boîte aux lettres inactive. Cela empêche la suppression définitive des éléments provenant de la boîte aux lettres inactive après leur restauration dans la boîte aux lettres cible.

- **Activez le blocage de rétention pour la boîte aux lettres cible avant de restaurer une boîte aux lettres inactive.** Comme les éléments provenant d'une boîte aux lettres inactive peuvent être anciens, vous pouvez envisager d'activer le blocage de rétention pour la boîte aux lettres cible avant de restaurer une boîte aux lettres inactive. Lorsque vous placez une boîte aux lettres en blocage de rétention, la stratégie de rétention qui lui est affectée n'est pas traitée jusqu'à ce que le blocage de rétention soit supprimé ou jusqu'à ce que la période de blocage de rétention soit écoulée. Ainsi, le propriétaire de la boîte aux lettres cible dispose d'un certain temps pour gérer les anciens messages de la boîte aux lettres inactive. Sinon, la stratégie de rétention risque de supprimer d'anciens éléments (ou de déplacer des éléments vers la boîte aux lettres d'archivage, si elle est activée) qui ont expiré d'après les paramètres de rétention configurés pour la boîte aux lettres cible. Pour plus d’informations, consultez [la rubrique placer une boîte aux lettres sur le blocage de rétention dans Exchange Online](https://go.microsoft.com/fwlink/?linkid=856300).

- **Que fait le commutateur AllowLegacyDNMismatch ?** Dans les précédents exemples pour restaurer une boîte aux lettres inactive, le commutateur **AllowLegacyDNMismatch** sert à autoriser la restauration de la boîte aux lettres inactive vers une boîte aux lettres cible différente. Dans un scénario de restauration classique, l'objectif consiste à restaurer du contenu pour lequel les boîtes aux lettres source et cible sont la même boîte aux lettres. Par défaut, l’applet **de commande New-MailboxRestoreRequest** vérifie que la valeur de la propriété **legacyExchangeDN** des boîtes aux lettres source et cible est identique. Cette vérification vous empêche de restaurer accidentellement une boîte aux lettres source vers la mauvaise boîte aux lettres cible. Si vous essayez de restaurer une boîte aux lettres inactive sans utiliser le commutateur **AllowLegacyDNMismatch**, la commande peut échouer si les boîtes aux lettres source et cible ont des valeurs différentes pour la propriété **LegacyExchangeDN**.

- **You can use other parameters with the New-MailboxRestoreRequest cmdlet to implement different restore scenarios for inactive mailboxes.** For example, you can run this command to restore the archive from the inactive mailbox into the primary mailbox of the target mailbox. 

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive" -AllowLegacyDNMismatch
  ```

  Vous pouvez également restaurer la boîte aux lettres principale inactive vers l'archive de la boîte aux lettres cible en exécutant cette commande.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox" -AllowLegacyDNMismatch
  ```

- **What does the TargetRootFolder parameter do?** As previously explained, you can use the **TargetRootFolder** parameter to specify a folder in the top of the folder structure (also called the root) in the target mailbox in which to restore the contents of the inactive mailbox. If you don't use this parameter, mailbox items from the inactive mailbox are merged into the corresponding default folders of the target mailbox, and custom folders are re-created in the root of the target mailbox. The following illustrations highlight these differences between not using and using the **TargetRootFolder** parameter.

    **Hiérarchie des dossiers dans la boîte aux lettres cible lorsque le paramètre TargetRootFolder n'est pas utilisé**

    ![Capture d'écran lorsque le paramètre TargetRootFolder n'est pas utilisé](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)
  
    **Hiérarchie des dossiers dans la boîte aux lettres cible lorsque le paramètre TargetRootFolder est utilisé**

    ![Capture d'écran lorsque le paramètre TargetRootFolder est utilisé](../media/300da592-7323-48db-b8a4-07012259d113.png)
