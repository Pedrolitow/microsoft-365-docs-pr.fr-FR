---
title: Activer l’archivage illimité - Aide de l’administrateur
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: e2a789f2-9962-4960-9fd4-a00aa063559e
description: 'Pour les administrateurs : découvrez comment activer l’archivage à extension automatique, qui offre à vos utilisateurs un espace de stockage illimité pour leurs boîtes aux lettres Exchange Online. Vous pouvez activer l’archivage à extension automatique pour l’ensemble de votre organisation ou uniquement pour des utilisateurs spécifiques.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f95d635c6f6dc89e91b98e9219b491ec34a3e5d7
ms.sourcegitcommit: c1f9a1b2a34146c51c9e33c4119a388b249ce7a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "49867992"
---
# <a name="enable-unlimited-archiving---admin-help"></a>Activer l’archivage illimité - Aide de l’administrateur

Vous pouvez utiliser la fonctionnalité d’archivage à extension automatique Exchange Online pour activer un espace de stockage illimité pour les boîtes aux lettres d’archivage. Lorsque l’archivage à extension automatique est allumé, un espace de stockage supplémentaire est automatiquement ajouté à la boîte aux lettres d’archivage d’un utilisateur lorsqu’il approche de la limite de stockage. Le résultat est une capacité de stockage de boîte aux lettres illimitée. Vous pouvez activer l’archivage à extension automatique pour tous les membres de votre organisation ou uniquement pour des utilisateurs spécifiques. Pour plus d’informations sur l’archivage à extension automatique, voir Vue d’ensemble de l’archivage illimité [dans Office 365.](unlimited-archiving.md)

## <a name="before-you-enable-auto-expanding-archiving"></a>Avant d’activer l’archivage à extension automatique

- Vous devez être administrateur général de votre organisation ou membre du groupe de rôles Gestion de l’organisation dans votre organisation Exchange Online pour activer l’archivage à extension automatique pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Vous devez également être membre d’un groupe de rôles affecté au rôle Destinataires de messagerie pour activer l’archivage à extension automatique pour des utilisateurs spécifiques.

- La boîte aux lettres d’archivage d’un utilisateur doit être activée avant de pouvoir activer l’archivage à extension automatique. Une licence Exchange Online Plan 2 doit être attribuée à un utilisateur pour activer la boîte aux lettres d’archivage. Si une licence Exchange Online Plan 1 est attribuée à un utilisateur, vous devez lui attribuer une licence Archivage Exchange Online pour activer sa boîte aux lettres d’archivage. Voir [Activer les boîtes aux lettres d’archivage](enable-archive-mailboxes.md)dans le Centre de sécurité & conformité.

- Vous pouvez également utiliser PowerShell pour activer les boîtes aux lettres d’archivage. Consultez la section [Plus](#more-information) d’informations pour obtenir un exemple de commande PowerShell que vous pouvez utiliser pour activer les boîtes aux lettres d’archivage pour tous les utilisateurs de votre organisation.

- L’archivage à extension automatique prend aussi en charge les boîtes aux lettres partagées. Pour activer l’archive d’une boîte aux lettres partagée, une licence Exchange Online Plan 2 ou une licence Exchange Online Plan 1 avec une licence Archivage Exchange Online est requise.

- L’archivage à extension automatique vous empêche de récupérer ou de restaurer une boîte aux lettres [inactive.](inactive-mailboxes-in-office-365.md#what-are-inactive-mailboxes) Cela signifie que si vous activez l’archivage à extension automatique pour une boîte aux lettres et que la boîte aux lettres devient inactive à une date ultérieure, vous ne pourrez pas récupérer la boîte aux lettres [inactive](recover-an-inactive-mailbox.md) (en la convertissant en boîte aux lettres active) ni la restaurer [(en](restore-an-inactive-mailbox.md) fusionnant le contenu dans une boîte aux lettres existante). Si l’archivage à extension automatique est activé sur une boîte aux lettres inactive, la seule façon de récupérer des données consiste à utiliser l’outil de recherche de contenu dans le Centre de conformité Microsoft 365 pour exporter les données de la boîte aux lettres et les importer vers une autre boîte aux lettres. Pour plus d’informations, voir la section « Boîtes aux lettres inactives et archives à extension automatique » dans Vue d’ensemble [des boîtes aux lettres inactives.](inactive-mailboxes-in-office-365.md#inactive-mailboxes-and-auto-expanding-archives)

- Vous ne pouvez pas utiliser le Centre d’administration Exchange ou le Centre de sécurité & conformité pour activer l’archivage à extension automatique. Vous devez utiliser Exchange Online PowerShell. Pour vous connecter à votre organisation Exchange Online à l’aide de PowerShell à distance, consultez La connexion [à Exchange Online PowerShell.](https://go.microsoft.com/fwlink/p/?linkid=396554)

## <a name="enable-auto-expanding-archiving-for-your-entire-organization"></a>Activer l’archivage à extension automatique pour l’ensemble de votre organisation

Vous pouvez activer l’archivage à extension automatique pour l’ensemble de votre organisation. Une fois l’archivage activé, l’archivage à extension automatique est activé pour les boîtes aux lettres utilisateur existantes et pour les nouvelles boîtes aux lettres utilisateur créées. Lorsque vous créez des boîtes aux lettres utilisateur, assurez-vous d’activer la boîte aux lettres d’archivage principale de l’utilisateur afin que la fonctionnalité d’archivage à extension automatique fonctionne pour la nouvelle boîte aux lettres utilisateur.
  
1. [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554)

2. Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’archivage à extension automatique pour l’ensemble de votre organisation.

    ```powershell
    Set-OrganizationConfig -AutoExpandingArchive
    ```

## <a name="enable-auto-expanding-archiving-for-specific-users"></a>Activer l’archivage à extension automatique pour des utilisateurs spécifiques

Au lieu d’activer l’archivage à extension automatique pour chaque utilisateur de votre organisation, vous pouvez l’activer uniquement pour des utilisateurs spécifiques. Vous pouvez le faire, car seuls certains utilisateurs peuvent avoir besoin d’une grande capacité de stockage d’archivage.
  
Lorsque vous activez l’archivage à extension automatique pour un utilisateur spécifique et que la boîte aux lettres de l’utilisateur est en conservation ou affectée à une stratégie de rétention, les deux modifications de configuration suivantes sont apportées :
  
- Le quota de stockage de la boîte aux lettres d’archivage principale de l’utilisateur est augmenté de 10 Go (de 100 Go à 110 Go). Le quota d’avertissement d’archivage est également augmenté de 10 Go (de 90 Go à 100 Go).

- Le quota de stockage du dossier Éléments récupérables dans la boîte aux lettres principale de l’utilisateur est augmenté de 10 Go (également de 100 Go à 110 Go). Le quota d’avertissement des éléments récupérables est également augmenté de 10 Go (de 90 Go à 100 Go). Ces modifications ne sont applicables que si la boîte aux lettres est en conservation ou affectée à une stratégie de rétention.

Cet espace supplémentaire est ajouté pour éviter les problèmes de stockage qui peuvent se produire avant la mise en service de l’archive à extension automatique. Aucun espace de  *stockage supplémentaire*  n’est ajouté lorsque vous activez l’archivage à extension automatique pour l’ensemble de votre organisation, comme décrit dans la section précédente.
  
1. [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554)

2. Exécutez la commande suivante dans Exchange Online PowerShell pour activer l’archivage à extension automatique pour un utilisateur spécifique. Comme indiqué précédemment, la boîte aux lettres d’archivage de l’utilisateur (archive principale) doit être activée avant de pouvoir activer l’archivage à extension automatique pour cet utilisateur.

    ```powershell
    Enable-Mailbox <user mailbox> -AutoExpandingArchive
    ```

> [!IMPORTANT]
> Dans un déploiement Exchange hybride, vous ne pouvez pas utiliser la commande **Enable-Mailbox -AutoExpandingArchive** pour activer l’archivage à extension automatique pour un utilisateur spécifique dont la boîte aux lettres principale est en local et dont la boîte aux lettres d’archivage est en nuage. Pour activer l’archivage à extension automatique pour les boîtes aux lettres d’archivage informatiques dans un déploiement hybride Exchange, vous devez exécuter la commande **Set-OrganizationConfig -AutoExpandingArchive** dans Exchange Online PowerShell pour activer l’archivage à extension automatique pour l’ensemble de l’organisation. Si les boîtes aux lettres principale et d’archivage d’un utilisateur sont toutes deux en nuage, vous pouvez utiliser la commande **Enable-Mailbox -AutoExpandingArchive** pour activer l’archivage à extension automatique pour cet utilisateur spécifique.
  
## <a name="verify-that-auto-expanding-archiving-is-enabled"></a>Vérifier que l’archivage à extension automatique est activé

Pour vérifier que l’archivage à extension automatique est activé pour votre organisation, exécutez la commande suivante dans Exchange Online PowerShell.

```powershell
Get-OrganizationConfig | FL AutoExpandingArchiveEnabled
```

La valeur indique que l’archivage à extension  `True` automatique est activé pour l’organisation. 
  
Pour vérifier que l’archivage à extension automatique est activé pour un utilisateur spécifique, exécutez la commande suivante dans Exchange Online PowerShell.
  
```powershell
Get-Mailbox <user mailbox> | FL AutoExpandingArchiveEnabled
```

La valeur indique que l’archivage à extension  `True` automatique est activé pour l’utilisateur.
  
Pour déterminer si l’archivage à extension automatique est activé pour les boîtes aux lettres inactives, exécutez la commande suivante dans Exchange Online PowerShell.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL UserPrincipalName,AutoExpandingArchiveEnabled
```

La valeur indique que l’archivage à extension automatique est  `True` activé pour la boîte aux lettres inactive. La valeur indique que l’archivage à `False` extension automatique n’est pas activé.

Gardez les points suivants à l’esprit après avoir activé l’archivage à extension automatique :
  
- Si vous exécutez la commande **Set-OrganizationConfig -AutoExpandingArchive** pour activer l’archivage à extension automatique pour votre organisation, vous n’avez pas besoin d’exécuter l’archivage **Enable-Mailbox -AutoExpandingArchive** sur des boîtes aux lettres individuelles. L’exécution de la cmdlet **Set-OrganizationConfig** pour activer l’archivage à extension automatique pour votre organisation ne modifie pas la propriété  *AutoExpandingArchiveEnabled*  sur les boîtes aux lettres utilisateur en `True` .

- De même, les valeurs des propriétés de boîte aux lettres  *ArchiveQuota*  et  *ArchiveWarningQuota*  ne sont pas modifiées lorsque vous activez l’archivage à extension automatique. En fait, lorsque vous activez l’archivage à extension automatique pour une boîte aux lettres utilisateur et que la propriété  *AutoExpandingArchiveEnabled*  est définie sur , les propriétés  `True`  *ArchiveQuota*  et  *ArchiveWarningQuota*  sont ignorées. Voici un exemple de ces propriétés de boîte aux lettres après l’extension automatique de l’archivage pour la boîte aux lettres d’un utilisateur. 

    ![Les propriétés ArchiveQuota et ArchiveWarningQuota sont ignorées après l’extension automatique de l’archivage](../media/6a1c1b69-5c4c-4267-aac8-53577667f03e.png)

## <a name="more-information"></a>Plus d’informations

- Vous pouvez également utiliser PowerShell pour activer les boîtes aux lettres d’archivage. Par exemple, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell pour activer les boîtes aux lettres d’archivage pour tous les utilisateurs dont la boîte aux lettres d’archivage n’est pas encore activée.

    ```powershell
    Get-Mailbox -Filter {ArchiveStatus -Eq "None" -AND RecipientTypeDetails -eq "UserMailbox"} | Enable-Mailbox -Archive
    ```

- Après avoir activer l’archivage à extension automatique pour votre organisation ou pour un utilisateur spécifique, une boîte aux lettres d’archivage est convertie en archive à extension automatique lorsque la boîte aux lettres d’archivage (y compris le dossier Éléments récupérables) atteint 90 Go. La mise en service de l’espace de stockage supplémentaire peut prendre jusqu’à 30 jours.

- Une fois que vous avez désactivé l’archivage à extension automatique, il ne peut pas être désactivé. En outre, les administrateurs ne peuvent pas ajuster le quota de stockage pour l’archivage à extension automatique.

- L’archivage à extension automatique est pris en charge pour les boîtes aux lettres d’archivage informatiques dans un déploiement Hybride Exchange pour les utilisateurs qui ont une boîte aux lettres principale sur site. Toutefois, une fois que l’archivage à extension automatique est activé pour une boîte aux lettres d’archivage informatique, vous ne pouvez pas dévenir de cette boîte aux lettres d’archivage à l’organisation Exchange sur site. L’archivage à extension automatique n’est pas pris en charge pour les boîtes aux lettres sur site dans n’importe quelle version de Exchange Server.

- Pour obtenir la liste des clients Outlook que les utilisateurs peuvent utiliser pour accéder aux éléments de l’espace de stockage supplémentaire de leur boîte aux lettres d’archivage, consultez la section « Conditions requises pour Outlook pour accéder aux éléments dans une archive à extension automatique » dans Vue d’ensemble de l’archivage [illimité.](unlimited-archiving.md#outlook-requirements-for-accessing-items-in-an-auto-expanded-archive)

- Comme indiqué précédemment, 10 Go sont ajoutés au quota de stockage de la boîte aux lettres d’archivage principale de l’utilisateur (et au dossier Éléments récupérables si la boîte aux lettres est en attente) lorsque vous exécutez la commande **Enable-Mailbox -AutoExpandingArchive.** Cela fournit un espace de stockage supplémentaire jusqu’à ce que l’espace de stockage développé automatiquement soit mis en service (ce qui peut prendre jusqu’à 30 jours). Cet espace de stockage supplémentaire n’est pas ajouté lorsque vous exécutez **l’archivage Set-OrganizationConfig -AutoExpandingArchive** pour activer l’archivage à extension automatique pour toutes les boîtes aux lettres de votre organisation. Si vous avez activé l’archivage à extension automatique pour l’ensemble de l’organisation, mais que vous devez ajouter 10 Go d’espace de stockage supplémentaires pour un utilisateur spécifique, vous pouvez exécuter la commande **Enable-Mailbox -AutoExpandingArchive** sur cette boîte aux lettres. Vous recevrez un message d’erreur vous disant que l’archivage à extension automatique a déjà été activé, mais que l’espace de stockage supplémentaire sera ajouté à la boîte aux lettres.

> [!IMPORTANT]
> L’archivage à extension automatique est uniquement pris en charge pour les boîtes aux lettres utilisées pour des utilisateurs individuels ou des boîtes aux lettres partagées avec un taux de croissance qui ne dépasse pas 1 Go par jour. L’utilisation de la journalation, des règles de transport ou des règles de transport automatique pour copier des messages dans une boîte aux lettres d’archivage à des fins d’archivage n’est pas autorisée. La boîte aux lettres d'archivage d'un utilisateur est destinée uniquement à cet utilisateur. Microsoft se réserve le droit de refuser l’archivage illimité dans les cas où la boîte aux lettres d’archivage d’un utilisateur sert à stocker les données d’archivage d’autres utilisateurs ou dans d’autres cas d’utilisation inappropriée.
