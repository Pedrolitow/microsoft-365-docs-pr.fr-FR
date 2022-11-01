---
title: Activer les boîtes aux lettres d’archivage pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- purview-compliance
- tier2
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: Découvrez comment activer ou désactiver les boîtes aux lettres d’archivage pour prendre en charge la conservation des messages, la découverte électronique et les exigences de conservation de votre organisation.
ms.openlocfilehash: c9387afc4f84bc11f2d379eb1a6941f16795f4e7
ms.sourcegitcommit: 4bae15909267a70c8842bd0cd3dceb8459b4cc29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68798274"
---
# <a name="enable-archive-mailboxes-for-microsoft-365"></a>Activer les boîtes aux lettres d’archivage pour Microsoft 365

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

L’archivage dans Microsoft 365 (également appelé *Archivage local*) fournit aux utilisateurs de l’espace de stockage de boîtes aux lettres supplémentaire. Pour plus d’informations, consultez [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md).

Utilisez les informations de cet article pour activer ou désactiver une boîte aux lettres d’archivage à l’aide du portail d’administration Exchange ou de PowerShell. Découvrez également comment exécuter une vérification de diagnostic automatisée sur la boîte aux lettres d’archivage d’un utilisateur pour identifier les problèmes et suggestions de résolution.

La configuration permettant d’activer ou de désactiver les boîtes aux lettres d’archivage a récemment été déplacée de l’portail de conformité Microsoft Purview vers le [nouveau centre d’administration Exchange (EAC).](/exchange/exchange-admin-center)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="get-the-necessary-permissions"></a>Obtenir les autorisations nécessaires

Le rôle Destinataires du courrier doit vous être attribué dans Exchange Online pour activer ou désactiver les boîtes aux lettres d’archivage. Par défaut, ce rôle est attribué aux groupes de rôles Gestion des destinataires et Gestion de l’organisation sur la page **Autorisations** du <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. 


## <a name="how-to-enable-an-archive-mailbox"></a>Comment activer une boîte aux lettres d’archivage

> [!NOTE]
> Lorsque vous activez la boîte aux lettres d’archivage, les éléments de la boîte aux lettres de l’utilisateur qui sont antérieurs à la stratégie d’archivage affectée à la boîte aux lettres sont déplacés vers la nouvelle boîte aux lettres d’archivage. La stratégie d’archivage par défaut qui fait partie de la stratégie de rétention affectée aux boîtes aux lettres Online déplace les éléments vers la boîte aux lettres d’archivage deux ans après la date à laquelle ils ont été remis à la boîte aux lettres ou créés par l’utilisateur. Pour plus d’informations, consultez [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md).

1. Dans le nouveau centre d’administration Exchange, accédez à **Boîtes aux lettres** **destinataires**\>.

2. Dans la liste des boîtes aux lettres, sélectionnez l’utilisateur pour activer sa boîte aux lettres pour l’archivage.

3. Dans le volet volant, sélectionnez **Autres**, puis sous **Archive de boîtes aux lettres**, sélectionnez **Gérer l’archive de boîtes aux lettres** : 
    
   ![Gérer l’archive de boîtes aux lettres pour un utilisateur sélectionné.](../media/manage-mailbox-archive-option.png)

4. Dans le volet **Gérer l’archivage des boîtes aux lettres** , activez **Archiver les boîtes aux lettres**, puis **Enregistrer**.

La création de la boîte aux lettres d’archivage peut prendre un certain temps. Lorsqu’il est créé, **Actif** s’affiche dans la colonne **État de l’archive** pour l’utilisateur sélectionné, même si vous devrez peut-être actualiser la page pour voir le changement d’état.

## <a name="how-to-disable-an-archive-mailbox"></a>Comment désactiver une boîte aux lettres d’archivage

De même que pour activer une boîte aux lettres d’archivage, vous pouvez utiliser la même configuration dans le CENTRE d’administration Exchange pour désactiver la boîte aux lettres d’archivage d’un utilisateur. Cette fois, désactivez **l’archivage de boîtes aux lettres** dans le CENTRE d’administration Exchange.

After you disable an archive mailbox, you can reconnect it to the user's primary mailbox within 30 days of disabling it. In this case, the original contents of the archive mailbox are restored. After 30 days, the contents of the original archive mailbox are permanently deleted and can't be recovered. So if you re-enable the archive more than 30 days after disabling it, a new archive mailbox is created.

The default archive policy assigned to users' mailboxes moves items to the archive mailbox two years after the date the item is delivered. If you disable a user's archive mailbox, no action will be taken on mailbox items and they'll remain in the user's primary mailbox.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Utiliser Exchange Online PowerShell pour activer ou désactiver les boîtes aux lettres d’archivage

You can also use Exchange Online PowerShell to enable archive mailboxes. The primary reason to use PowerShell is that you can quickly enable the archive mailbox for all users in your organization.

La première étape consiste à se connecter à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Une fois que vous êtes connecté à Exchange Online, vous pouvez exécuter les commandes décrites dans les sections suivantes pour activer ou désactiver les boîtes aux lettres d’archivage.

### <a name="enable-archive-mailboxes"></a>Activer les boîtes aux lettres d’archivage

Pour activer la boîte aux lettres d’archivage pour un seul utilisateur, exécutez la commande suivante.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

Pour activer la boîte aux lettres d’archivage pour tous les utilisateurs au sein de votre organisation (dont la boîte aux lettres d’archivage n’est pas activée), exécutez la commande suivante.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>Désactiver les boîtes aux lettres d’archivage

Pour désactiver la boîte aux lettres d’archivage pour un seul utilisateur, exécutez la commande suivante.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

Pour désactiver la boîte aux lettres d’archivage pour tous les utilisateurs au sein de votre organisation (dont la boîte aux lettres d’archivage est activée), exécutez la commande suivante.

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>Exécuter des diagnostics sur des boîtes aux lettres d’archivage

Vous pouvez exécuter une vérification de diagnostic automatisée sur la boîte aux lettres d’archivage d’un utilisateur pour identifier les problèmes et les résolutions suggérées.

Pour exécuter la vérification de diagnostic, cliquez sur le bouton ci-dessous. 

> [!div class="nextstepaction"]
> [Exécuter des tests : boîte aux lettres d’archivage](https://aka.ms/PillarArchiveMailbox)

![Exécutez des diagnostics sur une boîte aux lettres d’archivage.](../media/ArchiveMailboxDiagnostics.png)

Une page volante s’ouvre dans le Centre d'administration Microsoft 365. Entrez l’adresse e-mail de la boîte aux lettres que vous souhaitez vérifier, puis cliquez sur **Exécuter les tests.**

> [!NOTE]
> Vous devez être un administrateur Microsoft 365 pour utiliser la vérification de diagnostic de boîte aux lettres d’archivage. En outre, cette fonctionnalité n’est pas disponible dans les clouds Microsoft 365 Administration, Microsoft 365 gérés par 21Vianet ou Microsoft 365 Germany.

## <a name="instructions-for-end-users"></a>Instructions pour les utilisateurs finaux

Expliquez aux utilisateurs comment fonctionne leur boîte aux lettres d’archivage et comment ils peuvent interagir avec elle dans Outlook sur Windows, macOS et sur le Web. La documentation la plus efficace sera personnalisée pour votre organisation. Mais pour obtenir des instructions de base, consultez [Gérer le stockage des e-mails avec des boîtes aux lettres d’archivage en ligne](https://prod.support.services.microsoft.com/en-us/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

## <a name="next-steps"></a>Prochaines étapes

Envisagez d’activer [l’archivage à extension automatique](autoexpanding-archiving.md) pour un espace de stockage supplémentaire. Pour obtenir des instructions, voir [Activer l’archivage à extension automatique](enable-autoexpanding-archiving.md).
