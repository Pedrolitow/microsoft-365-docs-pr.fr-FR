---
title: Activer les boîtes aux lettres d’archivage pour la conformité Microsoft 365
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
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: Découvrez comment activer ou désactiver les boîtes aux lettres d’archivage pour prendre en charge la conservation des messages, la découverte électronique et les exigences de conservation de votre organisation.
ms.openlocfilehash: 9e30178dcab731ae61a9db5374218a608e4e47af
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738355"
---
# <a name="enable-archive-mailboxes-in-the-compliance-center"></a>Activer des boîtes aux lettres d’archivage dans le Centre conformité

L’archivage dans Microsoft 365 (également appelé *Archivage inaltérable*) fournit aux utilisateurs de l’espace de stockage de boîtes aux lettres supplémentaire. Pour plus d’informations, consultez [En savoir plus sur les boîtes aux lettres d’archivage](archive-mailboxes.md).

Utilisez les informations de cet article pour activer ou désactiver une boîte aux lettres d’archivage dans le Centre de conformité Microsoft 365 ou à l’aide de PowerShell. Découvrez également comment exécuter une vérification de diagnostic automatisée sur la boîte aux lettres d’archivage d’un utilisateur pour identifier les problèmes et suggestions de résolution.

## <a name="get-the-necessary-permissions"></a>Obtenir les autorisations nécessaires

Le rôle Destinataires du courrier doit vous être attribué dans Exchange Online pour activer ou désactiver les boîtes aux lettres d’archivage. Par défaut, ce rôle est attribué aux groupes de rôles Gestion des destinataires et Gestion de l’organisation sur la page **Autorisations** du <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. 

Si vous ne voyez pas la page **Archive** dans le Centre de conformité Microsoft 365, demandez à votre administrateur de vous attribuer les autorisations nécessaires.

## <a name="enable-an-archive-mailbox"></a>Activer une boîte aux lettres d’archivage

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>, puis connectez-vous.

2. Dans le volet gauche du Centre de conformité Microsoft 365, cliquez sur **Gouvernance des informations**, puis sur l’onglet **Archive**.

   La page **Archive** s’affiche. La colonne **Boîte aux lettres d’archivage** indique si une boîte aux lettres d’archivage est activée ou désactivée pour chaque utilisateur.

   > [!NOTE]
   > La page **Archive** affiche au maximum 500 utilisateurs.

3. Dans la liste des boîtes aux lettres, sélectionnez l’utilisateur pour lequel vous voulez activer la boîte aux lettres d’archivage, et sélectionnez **Archiver l’archivage**.

   ![Cliquer sur Activer dans le volet d’informations de l’utilisateur sélectionné pour activer la boîte aux lettres d’archivage.](../media/8b53cdec-d5c9-4c28-af11-611f95c37b34.png)


   Un avertissement s'affiche indiquant que si vous activez la boîte aux lettres d'archivage, les éléments de la boîte aux lettres de l'utilisateur qui sont plus anciens que la stratégie d'archivage attribuée à la boîte aux lettres seront déplacés vers la nouvelle boîte aux lettres d'archivage. La stratégie d'archivage par défaut qui fait partie de la stratégie de rétention attribuée aux boîtes aux lettres Exchange Online déplace les éléments vers la boîte aux lettres d'archivage deux ans après la date à laquelle l'élément a été remis à la boîte aux lettres ou créé par l'utilisateur. Pour plus d'informations, consultez la section **Plus d'informations** de cet article.

5. Sélectionnez **Activer** pour activer la boîte aux lettres d’archivage.

   La création de la boîte aux lettres d'archivage peut prendre quelques instants. Lorsqu'il est créé, **Archiver la boîte aux lettres : activé** s'affiche dans le volet de détails pour l'utilisateur sélectionné. Vous devrez peut-être cliquer sur **Actualiser** ![icône Actualiser.](../media/O365-MDM-Policy-RefreshIcon.gif) pour mettre à jour les informations dans le volet de détails.

> [!TIP]
> Vous pouvez également activer des boîtes aux lettres d’archivage en bloc en sélectionnant plusieurs utilisateurs dont les boîtes aux lettres sont désactivées (à l’aide de la touche Maj ou Ctrl). Une fois les boîtes aux lettres sélectionnées, cliquez sur **Activer** dans le volet des détails.

## <a name="disable-an-archive-mailbox"></a>Désactiver une boîte aux lettres d’archivage

Vous pouvez également utiliser la page **Archiver** dans le centre de conformité Microsoft 365 pour désactiver la boîte aux lettres d'archivage d'un utilisateur. Après avoir désactivé une boîte aux lettres d'archivage, vous pouvez la reconnecter à la boîte aux lettres principale de l'utilisateur dans les 30 jours suivant sa désactivation. Dans ce cas, le contenu d'origine de la boîte aux lettres d'archivage est restauré. Après 30 jours, le contenu de la boîte aux lettres d'archive d'origine est définitivement supprimé et ne peut pas être récupéré. Ainsi, si vous réactivez l'archive plus de 30 jours après l'avoir désactivée, une nouvelle boîte aux lettres d'archive est créée.

La stratégie d’archivage par défaut affectée aux boîtes aux lettres des utilisateurs déplace les éléments dans la boîte aux lettres d’archivage deux ans après la date de remise de l’élément. Si vous désactivez la boîte aux lettres d’archivage d’un utilisateur, aucune action n’est effectuée sur les éléments de boîte aux lettres et ceux-ci resteront dans la boîte aux lettres principale de l’utilisateur.

Pour désactiver une boîte aux lettres d’archivage :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Centre de conformité Microsoft 365</a>, puis connectez-vous.

2. Dans le volet gauche du Centre de conformité Microsoft 365, cliquez sur **Gouvernance des informations**, puis sur l’onglet **Archive**.

   La page **Archive** s’affiche. La colonne **Boîte aux lettres d’archivage** indique si une boîte aux lettres d’archivage est activée ou désactivée pour chaque utilisateur.

   > [!NOTE]
   > La page **Archive** affiche au maximum 500 utilisateurs.

3. Dans la liste des boîtes aux lettres, sélectionnez l’utilisateur pour lequel vous voulez désactiver la boîte aux lettres d’archivage **Désactiver l’archivage**.


   Un message d’avertissement s’affiche, indiquant que vous avez 30 jours pour réactiver la boîte aux lettres d’archivage et qu’à l’issue de ce délai, toutes les informations contenues dans l’archive seront définitivement supprimées.

5. Sélectionnez **Désactiver** pour désactiver la boîte aux lettres d’archivage.

   La désactivation de la boîte aux lettres d'archivage peut prendre quelques instants. Lorsqu'il est désactivé, **Archiver la boîte aux lettres : désactivé** s'affiche dans le volet de détails pour l'utilisateur sélectionné. Vous devrez peut-être cliquer sur **Actualiser** ![icône Actualiser.](../media/O365-MDM-Policy-RefreshIcon.gif) pour mettre à jour les informations dans le volet de détails.

> [!TIP]
> Vous pouvez également désactiver des boîtes aux lettres d’archivage en bloc en sélectionnant plusieurs utilisateurs dont les boîtes aux lettres sont activées (à l’aide de la touche Maj ou Ctrl). Une fois les boîtes aux lettres sélectionnées, cliquez sur **Désactiver** dans le volet des détails.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>Utiliser Exchange Online PowerShell pour activer ou désactiver les boîtes aux lettres d’archivage

Vous pouvez également utiliser Exchange Online PowerShell pour activer les boîtes aux lettres d’archivage. La principale raison d'utiliser PowerShell est que vous pouvez activer rapidement la boîte aux lettres d'archivage pour tous les utilisateurs de votre organisation.

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

## <a name="next-steps"></a>Prochaines étapes

Envisagez d’activer [l’archivage à extension automatique](autoexpanding-archiving.md) pour un espace de stockage supplémentaire. Pour obtenir des instructions, voir [Activer l’archivage à extension automatique](enable-autoexpanding-archiving.md).
