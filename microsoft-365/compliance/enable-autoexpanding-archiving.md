---
title: Activer l'archivage à expansion automatique
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: e2a789f2-9962-4960-9fd4-a00aa063559e
description: 'Pour les administrateurs : découvrez comment activer l’archivage à extension automatique, qui fournit à vos utilisateurs un stockage supplémentaire pour leurs boîtes aux lettres Exchange Online. Vous pouvez activer l’archivage à extension automatique pour l’ensemble de votre organisation ou uniquement pour des utilisateurs spécifiques.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7edb246d2a2b9f765bcce6db8f8afa0485c423b3
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359577"
---
# <a name="enable-auto-expanding-archiving"></a>Activer l'archivage à expansion automatique

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Vous pouvez utiliser la Exchange Online fonctionnalité d’archivage à extension automatique pour activer un espace de stockage supplémentaire pour les boîtes aux lettres d’archivage. Lorsque l’archivage de développement automatique est activé, un espace de stockage supplémentaire est automatiquement ajouté à la boîte aux lettres d’archivage d’un utilisateur jusqu’à ce qu’il atteigne la limite de stockage de 1,5 To. Vous pouvez activer l’archivage de développement automatique pour tous les membres de votre organisation ou uniquement pour des utilisateurs spécifiques. Pour plus d’informations sur le développement automatique de l’archivage, consultez [En savoir plus sur l’archivage à extension automatique](autoexpanding-archiving.md).

## <a name="before-you-enable-auto-expanding-archiving"></a>Avant d’activer l’archivage à développement automatique

- Comprenez les restrictions suivantes : 

    - Une fois que vous avez activé l’archivage de développement automatique pour votre organisation ou pour un utilisateur spécifique, il ne peut pas être désactivé. Les administrateurs ne peuvent pas non plus ajuster le quota de stockage pour l’archivage à extension automatique.
    
    - Le développement automatique de l’archivage vous empêche de récupérer ou de restaurer une [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes). Cela signifie que si vous activez l’archivage de développement automatique pour une boîte aux lettres et que la boîte aux lettres est rendue inactive à une date ultérieure, vous ne pourrez pas [récupérer la boîte aux lettres inactive](recover-an-inactive-mailbox.md) (en la convertissant en boîte aux lettres active) ou la [restaurer](restore-an-inactive-mailbox.md) (en fusionnant le contenu en une boîte aux lettres existante). 
        
        Si l’archivage à extension automatique est activé sur une boîte aux lettres inactive, la seule façon de récupérer des données consiste à utiliser l’outil de recherche de contenu dans le portail de conformité Microsoft Purview pour exporter les données de la boîte aux lettres et les importer vers une autre boîte aux lettres. Pour plus d’informations, consultez les [boîtes aux lettres inactives et les archives à extension automatique](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives).

- Vous devez être un administrateur général de votre organisation ou un membre du groupe de rôles Gestion de l’organisation dans votre organisation Exchange Online pour activer l’archivage à extension automatique. Vous devez également être membre d’un groupe de rôles auquel est attribué le rôle Destinataires du courrier pour activer l’archivage à extension automatique pour des utilisateurs spécifiques.

- La boîte aux lettres d’un utilisateur doit déjà être [activée pour l’archivage avant](enable-archive-mailboxes.md) de pouvoir activer l’archivage à extension automatique.

- Une fois que vous avez activé l’archivage à extension automatique, une boîte aux lettres d’archivage est convertie en archive à extension automatique lorsque la boîte aux lettres d’archivage (y compris le dossier Éléments récupérables) atteint 90 Go. La mise en service de l’espace de stockage supplémentaire peut prendre jusqu’à 30 jours.

- L’archivage à extension automatique prend aussi en charge les boîtes aux lettres partagées.

- Vous ne pouvez pas utiliser le Centre d’administration Exchange ou le portail de conformité Microsoft Purview pour activer l’archivage à extension automatique. Vous devez utiliser Exchange Online PowerShell.

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Activer l’archivage à extension automatique pour l’ensemble de votre organisation

Vous pouvez activer l’archivage à extension automatique pour l’ensemble de votre organisation. Après l’avoir activé, l’archivage à développement automatique est activé pour les boîtes aux lettres utilisateur existantes et pour les nouvelles boîtes aux lettres utilisateur créées. Lorsque vous créez des boîtes aux lettres utilisateur, veillez à activer la boîte aux lettres d’archivage principale de l’utilisateur afin que la fonctionnalité d’archivage à extension automatique fonctionne pour la nouvelle boîte aux lettres utilisateur.
  
1. [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’archivage à extension automatique pour l’ensemble de votre organisation.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Activer l’archivage de développement automatique pour des utilisateurs spécifiques

Au lieu d’activer l’archivage à extension automatique pour chaque utilisateur de votre organisation, vous pouvez l’activer uniquement pour des utilisateurs spécifiques. Vous pouvez le faire, car seuls certains utilisateurs peuvent avoir besoin d’une grande capacité de stockage d’archive.
  
Lorsque vous activez l’archivage de développement automatique pour un utilisateur spécifique et la boîte aux lettres de l’utilisateur en attente ou affectée à une stratégie de rétention, les deux modifications de configuration suivantes sont apportées :
  
- Le quota de stockage pour la boîte aux lettres d’archive principale de l’utilisateur est augmenté de 10 Go (de 100 Go à 110 Go). Le quota d’avertissement d’archive est également augmenté de 10 Go (de 90 Go à 100 Go).

- Le quota de stockage pour le dossier Éléments récupérables dans la boîte aux lettres principale de l’utilisateur est augmenté de 10 Go (également de 100 Go à 110 Go). Le quota d’avertissement Éléments récupérables est également augmenté de 10 Go (de 90 Go à 100 Go). Ces modifications s’appliquent uniquement si la boîte aux lettres est en attente ou affectée à une stratégie de rétention.

Cet espace supplémentaire est ajouté pour éviter les problèmes de stockage qui peuvent se produire avant l’approvisionnement de l’archive à expansion automatique. L’espace de stockage supplémentaire  *n’est pas*  ajouté lorsque vous activez l’archivage à extension automatique pour l’ensemble de votre organisation, comme décrit dans la section précédente.
  
1. [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’archivage de développement automatique pour un utilisateur spécifique. Comme expliqué précédemment, la boîte aux lettres d’archivage de l’utilisateur (archive principale) doit être activée avant de pouvoir activer l’archivage de développement automatique pour cet utilisateur.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> Dans un déploiement hybride Exchange, vous ne pouvez pas utiliser la commande **Enable-Mailbox -AutoExpandingArchive** pour activer l’archivage à extension automatique pour un utilisateur spécifique dont la boîte aux lettres principale est locale et dont la boîte aux lettres d’archivage est basée sur le cloud. Pour activer l’archivage à extension automatique pour les boîtes aux lettres d’archivage basées sur le cloud dans un déploiement hybride Exchange, vous devez exécuter la commande **Set-OrganizationConfig -AutoExpandingArchive** dans Exchange Online PowerShell afin d’activer l’archivage de développement automatique pour l’ensemble de l’organisation. Si les boîtes aux lettres primaires et d’archivage d’un utilisateur sont basées sur le cloud, vous pouvez utiliser la commande **Enable-Mailbox -AutoExpandingArchive** pour activer l’archivage de développement automatique pour cet utilisateur spécifique.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Vérifier que l’archivage à développement automatique est activé

Pour vérifier que l’archivage à extension automatique est activé pour votre organisation, exécutez la commande suivante dans Exchange Online PowerShell.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

La valeur indique  `True` que l’archivage à extension automatique est activé pour l’organisation. 
  
Pour vérifier que l’archivage à développement automatique est activé pour un utilisateur spécifique, exécutez la commande suivante dans Exchange Online PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

La valeur indique  `True` que l’archivage à développement automatique est activé pour l’utilisateur.
  
Pour déterminer si l’archivage à extension automatique est activé pour les boîtes aux lettres inactives, exécutez la commande suivante dans Exchange Online PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

La valeur indique que l’archivage  `True` à développement automatique est activé pour la boîte aux lettres inactive. La valeur indique `False` que l’archivage à développement automatique n’est pas activé.

Gardez à l’esprit les éléments suivants après avoir activé l’archivage à développement automatique :
  
- Si vous exécutez la commande **Set-OrganizationConfig -AutoExpandingArchive** pour activer l’archivage à extension automatique pour votre organisation, vous n’avez pas besoin d’exécuter **enable-mailbox -AutoExpandingArchive** sur des boîtes aux lettres individuelles. L’exécution de l’applet de commande **Set-OrganizationConfig** pour activer l’archivage de développement automatique pour votre organisation ne modifie pas la propriété  *AutoExpandingArchiveEnabled*  sur les boîtes aux lettres `True`utilisateur en .

- De même, les valeurs des propriétés de boîte aux lettres  *ArchiveQuota*  et  *ArchiveWarningQuota*  ne sont pas modifiées lorsque vous activez l’archivage à développement automatique. En fait, lorsque vous activez l’archivage de développement automatique pour une boîte aux lettres utilisateur et que la propriété  *AutoExpandingArchiveEnabled*  est définie  `True`sur , les propriétés  *ArchiveQuota*  et  *ArchiveWarningQuota*  sont ignorées. Voici un exemple de ces propriétés de boîte aux lettres après l’activation de l’archivage de développement automatique pour la boîte aux lettres d’un utilisateur. 

    ![Les propriétés ArchiveQuota et ArchiveWarningQuota sont ignorées après avoir activé l’archivage à développement automatique.](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Plus d’informations

- Vous pouvez également utiliser PowerShell pour activer les boîtes aux lettres d’archivage. Par exemple, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell pour activer les boîtes aux lettres d’archivage pour tous les utilisateurs dont la boîte aux lettres d’archivage n’est pas déjà activée.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- L’archivage à extension automatique est pris en charge pour les boîtes aux lettres d’archivage basées sur le cloud dans un déploiement hybride Exchange pour les utilisateurs disposant d’une boîte aux lettres principale locale. Toutefois, une fois l’archivage auto-développé activé pour une boîte aux lettres d’archivage basée sur le cloud, vous ne pouvez pas désintégrant cette boîte aux lettres d’archivage dans l’organisation Exchange locale. L’archivage à extension automatique n’est pris en charge pour les boîtes aux lettres locales dans aucune version de Exchange Server.

- Pour obtenir la liste des clients Outlook que les utilisateurs peuvent utiliser pour accéder aux éléments de la zone de stockage supplémentaire dans leur boîte aux lettres d’archivage, consultez la section « Conditions requises d’Outlook pour accéder aux éléments d’une archive développée automatiquement » dans [En savoir plus sur l’archivage à extension automatique](autoexpanding-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive).

- Comme expliqué précédemment, 10 Go sont ajoutés au quota de stockage de la boîte aux lettres d’archive principale de l’utilisateur (et au dossier Éléments récupérables si la boîte aux lettres est en attente) lorsque vous **exécutez la commande Enable-Mailbox -AutoExpandingArchive** . Cela fournit un stockage supplémentaire jusqu’à ce que l’espace de stockage développé automatiquement soit approvisionné (ce qui peut prendre jusqu’à 30 jours). Cet espace de stockage supplémentaire n’est pas ajouté lorsque vous **exécutez Set-OrganizationConfig -AutoExpandingArchive** pour activer l’archivage à extension automatique pour toutes les boîtes aux lettres de votre organisation. Si vous avez activé l’archivage de développement automatique pour l’ensemble de l’organisation, mais que vous devez ajouter 10 Go d’espace de stockage supplémentaire pour un utilisateur spécifique, vous pouvez exécuter la commande **Enable-Mailbox -AutoExpandingArchive** sur cette boîte aux lettres. Vous recevrez une erreur indiquant que l’archivage de développement automatique a déjà été activé, mais que l’espace de stockage supplémentaire sera ajouté à la boîte aux lettres.

> [!IMPORTANT]
> L’archivage à extension automatique est pris en charge uniquement pour les boîtes aux lettres utilisées par des utilisateurs individuels ou pour les boîtes aux lettres partagées avec un taux de croissance qui ne dépasse pas 1 Go par jour. L’utilisation de règles de journalisation, de transport ou de transfert automatique pour copier des messages dans une boîte aux lettres d’archivage n’est pas autorisée. La boîte aux lettres d'archivage d'un utilisateur est destinée uniquement à cet utilisateur. Microsoft se réserve le droit de refuser l’archivage supplémentaire dans les cas où la boîte aux lettres d’archivage d’un utilisateur est utilisée pour stocker des données d’archivage pour d’autres utilisateurs ou dans d’autres cas d’utilisation inappropriée.
