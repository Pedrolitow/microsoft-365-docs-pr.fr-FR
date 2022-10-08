---
title: Créer une boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 871a246d-3acd-4bba-948e-5de8be0544c9
description: Créez une boîte aux lettres partagée pour permettre à plusieurs personnes au sein de votre entreprise de partager la responsabilité de la lecture du courrier électronique envoyé à une adresse et de la réponse à ces courriers.
ms.openlocfilehash: 80ff53bc6c98760fe59001574f3e334f7d6dd738
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68198072"
---
# <a name="create-a-shared-mailbox"></a>Créer une boîte aux lettres partagée 

> [!NOTE]
> If your organization uses a hybrid Exchange environment, you should use the on-premises <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange admin center</a> to create and manage shared mailboxes. See [Create shared mailboxes in the Exchange admin center](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Si vous n'êtes pas sûr de devoir créer une boîte aux lettres partagée ou un groupe Microsoft 365 pour Outlook, voir [Comparer les groupes](../create-groups/compare-groups.md) pour plus de conseils. Sachez qu’il n’est pour l'instant pas possible de migrer une boîte aux lettres partagée vers un groupe Microsoft 365. Si vous le souhaitez, dites-le nous en [votant ici](https://go.microsoft.com/fwlink/?linkid=871518).

It's easy to create shared mailboxes so a group of people can monitor and send email from a common email addresses, like info@contoso.com. When a person in the group replies to a message sent to the shared mailbox, the email appears to be from the shared mailbox, not from the individual user.

Shared mailboxes include a shared calendar. A lot of small businesses like to use the shared calendar as a place for everyone to enter their appointments. For example, if you have 3 people who do customer visits, all can use the shared calendar to enter the appointments. This is an easy way to keep everyone informed where people are.

Avant de créer une boîte aux lettres partagée, assurez-vous de lire la section [À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) pour plus d'informations.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="create-a-shared-mailbox-and-add-members"></a>Créer une boîte aux lettres partagée et ajouter des membres
  
1. Sign in with a global admin account or Exchange admin account. If you get the message "**You don't have permission to access this page or perform this action**," then you aren't an admin. 

::: moniker range="o365-worldwide"

2. Dans le Centre d’administration, allez à la page **Teams et groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end

::: moniker range="o365-21vianet"

2. Dans le [centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=850627), allez à la page **Teams et groupes** \> **Boîtes aux lettres partagées**.

::: moniker-end
    
3. Dans la page **Boîtes aux lettres partagées,** sélectionnez **+ Ajouter une boîte aux lettres partagée**. Entrez le nom de la boîte aux lettres partagée. L’adresse e-mail est ainsi choisie, mais vous pouvez la modifier si nécessaire.
    
    ![Donnez un nom à votre boîte aux lettres partagée.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Select **Save changes**. It may take a few minutes before you can add members.

5. Under **Next steps**, select **Add members to this mailbox**. Members are the people who will be able to view the incoming mail to this shared mailbox, and the outgoing replies.

   ![Sélectionnez Ajouter des membres.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Select the **+Add members** button. Put a check mark next to the people who you want to use this shared mailbox, and then select **Save**.

   ![Associer des membres à la boîte aux lettres partagée](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Sélectionnez **Fermer**.

Vous bénéficiez à présent d’une boîte aux lettres partagée dotée d’un calendrier partagé. Passez à l’étape suivante : [Bloquer la connexion pour le compte de boîte aux lettres partagée](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Quelles autorisations devez-vous utiliser ?

Vous pouvez utiliser les autorisations suivantes avec une boîte aux lettres partagée :

- **Full Access**: The Full Access permission lets a user open the shared mailbox and act as the owner of that mailbox. After accessing the shared mailbox, a user can create calendar items, read, view, delete, and change email messages, and create tasks and calendar contacts. However, a user with Full Access permission can't send email from the shared mailbox unless they also have Send As or Send on Behalf permission.

- **Send As**: The Send As permission lets a user impersonate the shared mailbox when sending mail. For example, if Katerina logs into the shared mailbox Marketing Department and sends an email, it will look like the Marketing Department sent the email.

- **Send on Behalf**: The Send on Behalf permission lets a user send email on behalf of the shared mailbox. For example, if John logs into the shared mailbox Reception Building 32 and sends an email, it will look like the mail was sent by "John on behalf of Reception Building 32". You can't use the EAC to grant Send on Behalf permissions, you must use the **Set-Mailbox** cmdlet with the _GrantSendonBehalf_ parameter.

> [!NOTE]
> Les autorisations **Envoyer en tant que** et **Envoyer de la part de** ne fonctionnent pas dans le client de bureau Outlook avec le paramètre *HiddenFromAddressListsEnabled* sur la boîte aux lettres définie sur **True**, car elles nécessitent que la boîte aux lettres soit visible dans Outlook via la liste d’adresses globale.

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Utiliser le CAE pour modifier la délégation de boîte aux lettres partagée

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d'administration Exchange</a>, accédez à **Destinataires** \> **Boîtes aux lettres**. Sélectionnez la boîte aux lettres partagée, puis sélectionnez **Modifier** ![Icône Modifier.](../../media/ITPro-EAC-EditIcon.png).

2. Sous **Autorisations de boîte aux lettres**, sélectionnez **Gérer la délégation de boîte aux lettres**.

3. To grant or remove Full Access and Send As permissions, select **Add** ![Add Icon.](../../media/ITPro-EAC-AddIcon.png) or **Remove** ![Remove icon](../../media/ITPro-EAC-RemoveIcon.gif) and then select the users you want to grant permissions to.

   > [!NOTE]
   > The Full Access permission allows a user to open the mailbox as well as create and modify items in it. The Send As permission allows anyone other than the mailbox owner to send email from this shared mailbox. Both permissions are required for successful shared mailbox operation.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Bloquez la connexion pour le compte de boîte aux lettres partagée.

Chaque boîte aux lettres partagée a un compte d'utilisateur correspondant. Vous n'avez pas été invité à fournir un mot de passe lors de la création de la boîte aux lettres partagée ? Le compte a un mot de passe qui est généré par le système (inconnu). Vous n'êtes pas censé utiliser le compte pour vous connecter à la boîte aux lettres partagée.

Mais que se passe-t-il si un administrateur se contente de réinitialiser le mot de passe du compte d'utilisateur de la boîte aux lettres partagée ? Ou que se passe-t-il si un utilisateur malveillant accède aux informations d’identification du compte de boîte aux lettres partagée ? Cela permettrait au compte d’utilisateur de se connecter à la boîte aux lettres partagée et d'envoyer des courriers électroniques. Pour empêcher cela, vous devez bloquer la connexion pour le compte qui est associé à la boîte aux lettres partagée.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
::: moniker-end

2. Dans la liste des comptes d’utilisateurs, recherchez le compte de la boîte aux lettres partagée (par exemple, remplacez le filtre par **Utilisateurs sans licence**).

3. Sélectionnez l’utilisateur pour ouvrir son volet de propriétés, puis sélectionnez l’icône **Bloquer cet utilisateur** ![Capture d’écran de l’icône Bloquer cet utilisateur](../../media/block-user-icon.png).

   > [!NOTE]
   > Si le compte est déjà bloqué, **La connexion est bloquée** est inscrit en haut et l’icône affiche **Débloquer cet utilisateur**.

4. Dans le volet **Bloquer cet utilisateur ?**, sélectionnez **Empêcher l'utilisateur de se connecter**, puis sélectionnez **Enregistrer les modifications**.

Pour obtenir des instructions sur la manière de bloquer des comptes d’utilisateurs avec Azure AD PowerShell (y compris de nombreux comptes en même temps), voir [Bloquer des comptes d’utilisateurs avec Office 365 PowerShell](../../enterprise/block-user-accounts-with-microsoft-365-powershell.md).

## <a name="add-the-shared-mailbox-to-outlook"></a>Ajouter la boîte aux lettres partagée à Outlook

Si le mappage automatique est activé dans votre entreprise (par défaut, la plupart des personnes utilisent cette option), la boîte aux lettres partagée apparaîtra automatiquement dans l’application Outlook de vos utilisateurs, après qu’ils auront fermé et redémarré Outlook. 

Le mappage automatique est défini sur les boîtes aux lettres des utilisateurs, et non sur la boîte aux lettres partagée.   Par conséquent, si vous essayez d'utiliser un groupe de sécurité pour gérer les personnes autorisées à accéder à la boîte aux lettres partagée, le mappage automatique ne fonctionnera pas. Par conséquent, si vous voulez utiliser le mappage automatique, vous devez attribuer des autorisations de manière explicite. Le mappage automatique est activé par défaut. Pour découvrir comment désactiver ce service, voir [Supprimer le mappage automatique d’une boîte aux lettres partagée](/office365/troubleshoot/administration/remove-automapping-for-shared-mailbox).

Pour plus d’informations sur les boîtes aux lettres partagées dans Outlook, voir :

- <a href="https://support.microsoft.com/office/d94a8e9e-21f1-4240-808b-de9c9c088afd" target="_blank">Ouvrir et utiliser une boîte aux lettres partagée dans Outlook</a>

- <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Ajouter une boîte aux lettres partagée dans Outlook sur le web</a>

- <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Ajoutez une boîte aux lettres partagée dans Outlook Mobile</a>

- <a href="https://support.microsoft.com/office/6ecc39c5-5577-4a1d-b18c-bbdc92972cb2" target="_blank">Ouvrir un dossier ou une boîte aux lettres partagée dans Outlook pour Mac</a>

- <a href="https://support.microsoft.com/office/b0963400-2a51-4c64-afc7-b816d737d164" target="_blank">Ajouter des règles de boîte aux lettres partagée</a>

## <a name="use-a-shared-mailbox-on-a-mobile-device-phone-or-tablet"></a>Utiliser une boîte aux lettres partagée sur un appareil mobile (téléphone ou tablette)

Vous pouvez accéder à une boîte aux lettres partagée sur un appareil mobile de deux manières :
- Ajoutez la boîte aux lettres partagée dans l'<a href="https://apps.apple.com/us/app/microsoft-outlook/id951937596" target="_blank">application Outlook pour iOS</a> ou l'<a href="https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en_US" target="_blank">application mobile Outlook pour Android</a>. 
    
    Pour les instructions, voir <a href="https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f" target="_blank">Ajouter une boîte aux lettres partagée dans Outlook Mobile</a>.

- Ouvrez votre navigateur, connectez-vous, puis accédez à Outlook sur le web. À partir d’Outlook sur le web, vous pouvez accéder à la boîte aux lettres partagée.

    Pour les instructions, voir <a href="https://support.microsoft.com/office/98b5a90d-4e38-415d-a030-f09a4cd28207" target="_blank">Ajouter une boîte aux lettres partagée dans Outlook sur le web</a>.
    
> [!NOTE]
> Une boîte aux lettres partagée peut uniquement être ajoutée à l’application Outlook pour iOS ou à l’application mobile Outlook pour Android

## <a name="use-the-shared-calendar"></a>Utiliser le calendrier partagé

When you created the shared mailbox, you automatically created a shared calendar. We like the shared mailbox calendar rather than a SharePoint calendar for keeping track of appointments and where people are. A shared calendar is integrated with Outlook and it's much easier to use than a SharePoint calendar.

1. Dans l'application Outlook, accédez à l'affichage Calendrier, puis sélectionnez la boîte aux lettres partagée.

2. Lorsque vous entrez des rendez-vous, chaque membre de la boîte aux lettres partagée peut les voir.

3. N’importe quel membre de la boîte aux lettres partagée peut créer, afficher et gérer des rendez-vous dans le calendrier, tout comme ils le feraient leurs rendez-vous personnels. Tous les membres de la boîte aux lettres partagée peuvent voir les modifications apportées au calendrier partagé.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
