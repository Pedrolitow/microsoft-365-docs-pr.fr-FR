---
title: Récupérer une boîte aux lettres inactive
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
ms.assetid: 35d0ecdb-7cb0-44be-ad5c-69df2f8f8b25
description: 'Si un ancien employé revient à votre organisation, ou si un nouvel employé est embauché pour prendre en charge les responsabilités d’un employé à l’origine de la demande, vous pouvez récupérer le contenu de la boîte aux lettres inactive dans Office 365. Lorsque vous récupérez une boîte aux lettres inactive, elle est convertie en une nouvelle boîte aux lettres qui contient le contenu de la boîte aux lettres inactive. '
ms.openlocfilehash: 63d71d2f6e23af55d94f006e772f35747c83d59c
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44678970"
---
# <a name="recover-an-inactive-mailbox"></a>Récupérer une boîte aux lettres inactive

Une boîte aux lettres inactive (c'est-à-dire un type de boîte aux lettres supprimée (récupérable)) sert à conserver les courriers électroniques d'un ancien employé après qu'il a quitté votre organisation. Si cet employé revient à votre organisation ou si un autre employé assume les responsabilités de l’ancien employé, il existe deux façons de mettre le contenu de la boîte aux lettres inactive à la disposition de l’utilisateur : 
  
- **Récupérer une boîte aux lettres inactive.** Si l’ancien employé revient à votre organisation ou si un nouvel employé est embauché pour prendre les responsabilités de l’ancien employé, vous pouvez récupérer le contenu de la boîte aux lettres inactive. Cette méthode convertit la boîte aux lettres inactive en une nouvelle boîte aux lettres active qui contient le contenu de la boîte aux lettres inactive. Une fois récupérée, la boîte aux lettres inactive n'existe plus. Les procédures présentées dans cette rubrique décrivent cette méthode. 
    
- **Restaurez une boîte aux lettres inactive.** Si un autre employé assume les responsabilités de l’ancien employé ou si un autre utilisateur a besoin d’accéder au contenu de la boîte aux lettres inactive, vous pouvez restaurer (ou fusionner) le contenu de la boîte aux lettres inactive vers une boîte aux lettres existante. Vous pouvez également restaurer l'archive d'une boîte aux lettres inactive. Pour connaître les procédures de cette méthode, consultez la rubrique [restaurer une boîte aux lettres inactive dans Office 365](restore-an-inactive-mailbox.md).

Consultez la section [Plus d'informations](#more-information) pour obtenir d'autres détails concernant les différences entre la restauration et la récupération d'une boîte aux lettres inactive et une description de la récupération d'une boîte aux lettres inactive.
  
## <a name="before-you-begin"></a>Avant de commencer

- Vous devez utiliser Exchange Online PowerShell pour récupérer une boîte aux lettres inactive. Vous ne pouvez pas utiliser le Centre d'administration Exchange (CAE). Pour obtenir des instructions détaillées, consultez la rubrique [connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=396554).
    
- Exécutez la commande suivante pour obtenir les informations d'identité pour les boîtes aux lettres inactives de votre organisation. 

    ```powershell
    Get-Mailbox -InactiveMailboxOnly | FL Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
    ```

    Utilisez les informations renvoyées par cette commande pour récupérer une boîte aux lettres inactive spécifique.

## <a name="recover-an-inactive-mailbox"></a>Récupérer une boîte aux lettres inactive

Utilisez la cmdlet **New-Mailbox** avec le paramètre *InactiveMailbox* pour récupérer une boîte aux lettres inactive. 
  
1. Créez une variable contenant les propriétés de la boîte aux lettres inactive. 
    
    ```powershell
    $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
    ```

    > [!IMPORTANT]
    > Dans la commande précédente, utilisez la valeur de la propriété **DistinguishedName** ou **ExchangeGUID** pour identifier la boîte aux lettres inactive. Ces propriétés sont uniques pour chaque boîte aux lettres de votre organisation, alors qu'une boîte aux lettres active et une boîte aux lettres inactive peuvent avoir la même adresse SMTP principale. 
  
2. Cet exemple utilise les propriétés obtenues grâce à la commande précédente et récupère la boîte aux lettres inactive dans une boîte aux lettres active pour l'utilisateur Ann Beebe. Assurez-vous que les valeurs spécifiées pour les paramètres *Name* et *MicrosoftOnlineServicesID* sont uniques au sein de votre organisation. 

    ```powershell
    New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
    ```

    L’adresse SMTP principale de la boîte aux lettres inactive Récupérée aura la même valeur que celle spécifiée par le paramètre *MicrosoftOnlineServicesID* . 
    
Une fois que vous avez récupéré une boîte aux lettres inactive, un nouveau compte d’utilisateur est également créé. Vous devez activer ce compte d'utilisateur en lui attribuant une licence. Pour attribuer une licence dans le centre d’administration 365 de Microsoft, reportez-vous à la rubrique [attribuer ou supprimer des licences pour microsoft 365 pour les entreprises](https://go.microsoft.com/fwlink/p/?LinkId=276798).
  
## <a name="more-information"></a>Plus d’informations

- **Quelle est la principale différence entre la récupération et la restauration d'une boîte aux lettres inactive ?** Lorsque vous récupérez une boîte aux lettres inactive, la boîte aux lettres est convertie en une nouvelle boîte aux lettres, le contenu et la structure de dossiers de la boîte aux lettres inactive sont conservés et la boîte aux lettres est liée à un nouveau compte d'utilisateur. Une fois récupérée, la boîte aux lettres inactive n'existe plus et les modifications apportées au contenu dans la nouvelle boîte aux lettres affectent le contenu placé en attente dans la boîte aux lettres inactive. À l'inverse, lorsque vous restaurez une boîte aux lettres inactive, le contenu est simplement copié vers une autre boîte aux lettres. La boîte aux lettres inactive est conservée et reste une boîte aux lettres inactive. Toute modification apportée au contenu de la boîte aux lettres cible n'affecte pas le contenu d'origine conservé dans la boîte aux lettres inactive. La boîte aux lettres inactive peut toujours faire l'objet d'une recherche à l'aide de la découverte électronique inaltérable, son contenu peut être restauré vers une autre boîte aux lettres ou il peut être récupéré ou supprimé ultérieurement. 

- **Que se passe-t-il lorsque vous récupérez une boîte aux lettres inactive ?** La récupération d'une boîte aux lettres inactive entraîne les événements suivants : 

   - La conservation appliquée à une boîte aux lettres inactive est modifiée ou supprimée en fonction du type de conservation appliqué à la boîte aux lettres inactive avant sa récupération.
  
     - **Conservation pour litige.** Si la conservation pour litige a été activée pour la boîte aux lettres inactive, elle est supprimée de la boîte aux lettres récupérée.
  
     - **Conservation** inaltérable Les conservations inaltérables sont supprimées de la boîte aux lettres récupérée. Cela signifie que la boîte aux lettres Récupérée est supprimée en tant que boîte aux lettres source d’une conservation inaltérable ou d’une recherche de découverte électronique inaltérable.
     
     - **Stratégie de rétention Microsoft 365 avec verrouillage de conservation.** Si la boîte aux lettres inactive a été affectée à une stratégie de rétention avec un verrou de conservation (appelé *stratégie de rétention verrouillée*), la boîte aux lettres Récupérée est affectée à la même stratégie de rétention verrouillée. Pour plus d’informations sur les stratégies de rétention verrouillées, voir [en savoir plus sur les stratégies de rétention](retention-policies.md#use-preservation-lock-to-comply-with-regulatory-requirements).
  
     - **Stratégie de rétention Microsoft 365 sans verrou de conservation.** La boîte aux lettres inactive est supprimée de toutes les stratégies de rétention Microsoft 365 déverrouillées qui lui ont été appliquées. Toutefois, la conservation pour litige est activée sur la boîte aux lettres Récupérée afin d’empêcher la suppression du contenu d’une boîte aux lettres basée sur des stratégies de rétention à l’échelle de l’organisation qui suppriment le contenu antérieur à un âge donné. Vous pouvez conserver la conservation pour litige ou la supprimer. Pour plus d’informations, consultez [la rubrique créer une conservation pour litige](create-a-litigation-hold.md).

  - La période de récupération d'élément unique (définie par la propriété de boîte aux lettres **RetainDeletedItemsFor** ) est paramétrée sur 30 jours. En général, lorsqu'une boîte aux lettres est créée dans Exchange Online, cette période de rétention est définie sur 14 jours. En définissant ce paramètre sur la valeur maximale de 30 jours, vous gagnez du temps pour récupérer toutes les données définitivement supprimées (ou purgées) de la boîte aux lettres inactive. Vous pouvez également désactiver la récupération d'élément unique ou redéfinir la période de récupération d'élément unique sur la valeur par défaut de 14 jours. Pour plus d'informations, consultez la rubrique [Enable or disable single item recovery for a mailbox](https://go.microsoft.com/fwlink/?linkid=856769).
  
  - Le blocage de rétention est activé et la durée du blocage de rétention est définie sur 30 jours. Cela signifie que la stratégie de rétention Exchange par défaut, ainsi que toutes les stratégies de rétention Microsoft 365 à l’échelle de l’organisation ou à l’échelle de l’organisation qui sont affectées à la nouvelle boîte aux lettres ne seront pas traitées pendant 30 jours. L'employé de retour ou le nouveau propriétaire de la boîte aux lettres inactive récupérée a ainsi le temps de gérer les anciens messages. Dans le cas contraire, la stratégie de rétention Exchange ou Microsoft 365 peut supprimer les anciens éléments de boîte aux lettres (ou déplacer les éléments vers la boîte aux lettres d’archivage si elle est activée) qui ont expiré en fonction des paramètres configurés pour les stratégies de rétention Exchange ou Microsoft 365. Après 30 jours, le blocage de rétention expire, la propriété de boîte aux lettres **RetentionHoldEnabled** est définie sur **false**et l’Assistant dossier géré commence à traiter les stratégies attribuées à la boîte aux lettres. Si vous n'avez pas besoin de ce temps supplémentaire, il vous suffit de supprimer le blocage de rétention. Vous pouvez également augmenter la durée du blocage de rétention à l'aide de la commande **Set-Mailbox -EndDateForRetentionHold**. Pour plus d'informations, consultez la rubrique [Place a mailbox on retention hold](https://go.microsoft.com/fwlink/?linkid=856300).

- **Placez une conservation sur la boîte aux lettres récupérée si vous devez conserver l'état d'origine de la boîte aux lettres inactive.** Pour empêcher le nouveau propriétaire de la boîte aux lettres ou la stratégie de rétention de supprimer définitivement les messages de la boîte aux lettres inactive Récupérée, vous pouvez placer la boîte aux lettres en conservation pour litige. Pour plus d'informations, voir [Placement d'une boîte aux lettres en conservation pour litige](https://go.microsoft.com/fwlink/?linkid=856286).
    
- **Quel identifiant utilisateur pouvez-vous utiliser pour récupérer une boîte aux lettres inactive ?** Lorsque vous récupérez une boîte aux lettres inactive, la valeur que vous spécifiez pour le paramètre *MicrosoftOnlineServicesID* peut être différente de l’image d’origine associée à la boîte aux lettres inactive. Vous pouvez également utiliser l'identifiant utilisateur d'origine. Toutefois, comme indiqué précédemment, assurez-vous que les valeurs utilisées pour *Name* et *MicrosoftOnlineServicesID* sont uniques au sein de votre organisation lorsque vous récupérez la boîte aux lettres inactive. 
    
- **Que faire si la période de rétention de la boîte aux lettres inactive n'a pas expiré ?** Si une boîte aux lettres inactive a été supprimée (récupérable) il y a moins de 30 jours, vous ne pouvez pas utiliser la commande **New-Mailbox -InactiveMailbox** pour la récupérer. Vous devez le récupérer en restaurant le compte d’utilisateur correspondant. Pour plus d'informations, consultez la rubrique [Supprimer ou restaurer des utilisateurs](https://go.microsoft.com/fwlink/p/?LinkId=279162).
    
- **Comment savoir si la période de rétention de boîte aux lettres supprimée (récupérable) pour une boîte aux lettres inactive a expiré ?** Exécutez la commande suivante. 
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | FL ExternalDirectoryObjectId
  ```

    Si la propriété **ExternalDirectoryObjectId** n'a pas de valeur, la période de rétention de boîte aux lettres a expiré et vous pouvez récupérer la boîte aux lettres inactive en exécutant la commande **New-Mailbox -InactiveMailbox**. S’il existe une valeur pour la propriété **ExternalDirectoryObjectId** , la période de rétention de boîte aux lettres supprimée (récupérable) n’a pas expiré et vous devez récupérer la boîte aux lettres en restaurant le compte d’utilisateur. Consultez la rubrique [Supprimer ou restaurer des utilisateurs](https://go.microsoft.com/fwlink/p/?LinkId=279162)
    
- **Pensez à activer la boîte aux lettres d'archivage après avoir récupéré une boîte aux lettres inactive.** Ainsi, l'utilisateur qui revient ou le nouvel employé peut déplacer les anciens messages vers la boîte aux lettres d'archivage. Lorsque le blocage de rétention expire, la stratégie d’archivage qui fait partie de la stratégie de rétention Exchange par défaut affectée aux boîtes aux lettres Exchange Online déplace les éléments datant de deux ans ou plus dans la boîte aux lettres d’archivage. Si vous n'activez pas la boîte aux lettres d'archivage, les éléments antérieurs à deux ans restent dans la boîte aux lettres principale de l'utilisateur. Pour plus d’informations, consultez la rubrique [activation des boîtes aux lettres d’archivage](enable-archive-mailboxes.md).
 