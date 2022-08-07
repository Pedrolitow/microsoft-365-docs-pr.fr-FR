---
title: Gestion de la taille des boîtes aux lettres de groupe Microsoft 365
description: Découvrez la gestion de la taille des boîtes aux lettres de groupe dans Microsoft 365.
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid: ''
ms.reviewer: ''
author: serdars
ms.author: serdars
ms.openlocfilehash: e97ed8b6f7d4d57fe993c6039b165f1a8e85eeb8
ms.sourcegitcommit: cd9df1a681265905eef99c039f7036b2fa6e8b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2022
ms.locfileid: "67277156"
---
# <a name="microsoft-365-group-mailbox-size-management"></a>Gestion de la taille des boîtes aux lettres de groupe Microsoft 365 

Chaque groupe Microsoft 365 est équipé d’une boîte aux lettres dédiée qui stocke les e-mails reçus sur le groupe. La boîte aux lettres de groupe est également utilisée par des applications telles que SharePoint Online, Yammer, Teams, etc. La boîte aux lettres de groupe est équipée d’un quota de stockage initial de 50 Go. Si le quota de boîte aux lettres de groupe est atteint, les e-mails sont envoyés aux groupes NDR. Par conséquent, il est recommandé de supprimer le contenu plus ancien des boîtes aux lettres de groupe pour s’assurer que la boîte aux lettres de groupe n’atteint pas son quota. 

Les méthodes suivantes vous aident à comprendre le fonctionnement du calcul du quota, les meilleures pratiques ou l’approche proactive adoptée pour vous assurer que la boîte aux lettres de groupe n’atteint pas son quota. Et le cours de l’action à effectuer si la boîte aux lettres de groupe a atteint ou dépassé son quota.

## <a name="proactive-approach-to-keep-group-mailbox-size-in-check"></a>Approche proactive pour maintenir la taille de boîte aux lettres de groupe en échec 

Vous pouvez créer des stratégies de rétention pour vous assurer que les anciens e-mails des groupes sont supprimés automatiquement après avoir atteint la limite de temps spécifiée. Pour plus d’informations, sur les étapes de création d’une stratégie de rétention pour le groupe Microsoft 365, consultez [Créer et configurer des stratégies de rétention](/microsoft-365/compliance/create-retention-policies). Les stratégies de rétention prennent plus de temps pour nettoyer les données. Par conséquent, elles doivent être appliquées lors de la création d’une boîte aux lettres de groupe. Les stratégies de rétention ne peuvent pas être utilisées comme outil pour vider ou supprimer immédiatement les données d’une boîte aux lettres de groupe.

## <a name="to-monitor-the-group-mailbox-size"></a>Pour surveiller la taille de la boîte aux lettres de groupe : 

Utilisez la commande suivante pour vérifier le quota actuel affecté pour la boîte aux lettres de groupe :

```PowerShell
Get-Mailbox -GroupMailbox <groupname> |ft ProhibitSendReceiveQuota,ProhibitSendQuota,IssueWarningQuota 
```

Utilisez la commande suivante pour vérifier la taille actuelle de la boîte aux lettres de groupe :

```PowerShell
Get-MailboxStatistics <groupname> | ft TotalDeletedItemSize,TotalItemSize 
```

## <a name="steps-to-follow-when-the-group-mailbox-has-reached-its-limit"></a>Étapes à suivre lorsque la boîte aux lettres de groupe a atteint sa limite :  

Comme mentionné précédemment, la boîte aux lettres de groupe est utilisée pour diverses applications afin de stocker des données. Une fois que la boîte aux lettres de groupe a atteint son quota, il est important d’identifier les dossiers qui occupent plus de données et de prendre les mesures appropriées. 

1. Commencez par la commande suivante pour confirmer que le quota de boîte aux lettres de groupe a dépassé : 

   ```PowerShell
   Get-MailboxStatistics <groupname> |ft TotalItemSize,TotalDeletedItemSize 
   ```

   La boîte aux lettres de groupe est distribuée dans différents types de boîtes aux lettres `TargetQuota`, à savoir Système, Récupérable et Utilisateur. Les dossiers correspondant `TargetQuota` à « Utilisateur » sont les seuls pris en compte dans le calcul du quota de groupe.  

2. Utilisez la commande suivante pour vérifier la taille du dossier qui occupe les données utilisateur : 

   ```PowerShell
   Get-MailboxFolderStatistics <groupname> | where { $_.TargetQuota -like 'User' } | ft Name,FolderPath,FolderType,FolderSize 

   Get-MailboxFolderStatistics <groupname> -FolderScope NonIPMRoot | where { $_.TargetQuota -like 'User' } | ft Name,FolderType,*size* 
   ```
3. Vérifiez le quota ou la taille des dossiers.

4. Si le dossier qui consomme l’espace est `SharePointWebPartsConnectorMessages`, comme indiqué dans [Utiliser le composant WebPart Connecteur, procédez](https://support.microsoft.com/en-us/office/use-the-connector-web-part-db0756aa-f78f-4b74-8b19-be5dca0420e1?ns=spostandard&version=16&syslcid=1033&uilcid=1033&appver=spo160&helpid=wssenduser_useconnectorwebpart_fl862286&ui=en-us&rs=en-us&ad=us)comme suit :

   1. Désactivez le connecteur s’il n’est pas utilisé. 

   2. Attendez que les messages soient effacés par défaut dans 90 jours. 

5. Si aucun dossier spécial n’occupe la taille de la boîte aux lettres de groupe, [appliquez la stratégie de rétention de boîte aux lettres de groupe et](/microsoft-365/compliance/create-retention-policies) attendez que la stratégie de rétention nettoie les e-mails de la boîte aux lettres de groupe. 
  

