---
title: Créer une boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 871a246d-3acd-4bba-948e-5de8be0544c9
description: Créez une boîte aux lettres partagée pour permettre à plusieurs personnes au sein de votre entreprise de partager la responsabilité de la lecture du courrier électronique envoyé à une adresse et de la réponse à ces courriers.
ms.openlocfilehash: 53e82d0cdd1fb9f11ab15ce4a2fbdc4b0c0ac980
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59775587"
---
# <a name="create-a-shared-mailbox"></a>Créer une boîte aux lettres partagée 

> [!NOTE]
> Si votre organisation utilise un environnement hybride Exchange, vous devez utiliser le Centre d’administration Exchange (CAE) local pour créer et gérer des boîtes aux lettres partagées. Consultez la rubrique [Créer des boîtes aux lettres partagées dans le Centre d’administration Exchange](/Exchange/collaboration/shared-mailboxes/create-shared-mailboxes?preserve-view=true.&view=exchserver-2019)
>
> Si vous n'êtes pas sûr de devoir créer une boîte aux lettres partagée ou un groupe Microsoft 365 pour Outlook, voir [Comparer les groupes](../create-groups/compare-groups.md) pour plus de conseils. Sachez qu’il n’est pour l'instant pas possible de migrer une boîte aux lettres partagée vers un groupe Microsoft 365. Si vous le souhaitez, dites-le nous en [votant ici](https://go.microsoft.com/fwlink/?linkid=871518).

Vous pouvez facilement créer des boîtes aux lettres partagées de sorte qu’un groupe de personnes puisse surveiller et envoyer facilement du courrier électronique à partir d’une adresse de courrier commune, comme info@contoso.com. Quand une personne du groupe répond à un courrier envoyé à la boîte aux lettres partagée, la réponse semble provenir de la boîte aux lettres partagée et non de la personne.

Les boîtes aux lettres partagées incluent un calendrier partagé. Beaucoup de petites entreprises utilisent le calendrier partagé pour permettre à leurs employés d'y entrer leurs rendez-vous. Par exemple, si vous avez trois commerciaux qui effectuent des visites chez les clients, ces trois personnes peuvent utiliser le calendrier partagé pour saisir leurs rendez-vous. Tout le monde sait ainsi où elles se trouvent.

Avant de créer une boîte aux lettres partagée, assurez-vous de lire la section [À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) pour plus d'informations.

## <a name="create-a-shared-mailbox-and-add-members"></a>Créer une boîte aux lettres partagée et ajouter des membres
  
1. Connectez-vous à l’aide d’un compte d’administrateur général ou d’un compte d’administrateur Exchange. Si vous recevez le message « **Vous ne disposez pas des autorisations requises pour accéder à cette page ou effectuer cette action** », cela signifie que vous n’êtes pas un administrateur. 

::: moniker range="o365-worldwide"

2. Dans le Centre d’administration, allez à la page **Teams et groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end

::: moniker range="o365-germany"

2. Dans le [centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=848041), allez à la page **Teams et groupes** \> **Boîtes aux lettres partagées**.

::: moniker-end

::: moniker range="o365-21vianet"

2. Dans le [centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=850627), allez à la page **Teams et groupes** \> **Boîtes aux lettres partagées**.

::: moniker-end
    
3. Dans la page **Boîtes aux lettres partagées,** sélectionnez **+ Ajouter une boîte aux lettres partagée**. Entrez le nom de la boîte aux lettres partagée. Le choisit l’adresse e-mail, mais vous pouvez la modifier si nécessaire.
    
    ![Donnez un nom à votre boîte aux lettres partagée.](../../media/e3035132-8986-4ec7-b7c0-f2752080d2c0.png)
  
4. Sélectionnez **Enregistrer les modifications**. Quelques minutes peuvent être nécessaires avant que vous ne puissiez ajouter des membres.

5. Sous **Étapes suivantes**, sélectionnez **Ajouter des membres à cette boîte aux lettres**. Les membres représentent les personnes qui sont en mesure de consulter les courriers entrants dans cette boîte aux lettres partagée, ainsi que les réponses sortantes.

   ![Sélectionnez Ajouter des membres.](../../media/a2a72e3d-6170-40fe-a94f-0af8fbef8ab2.png)

6. Sélectionnez le bouton **+Ajouter des membres**. Cochez la case à côté des personnes que vous souhaitez autoriser à utiliser cette boîte aux lettres partagée, puis sélectionnez **Enregistrer**.

   ![Associer des membres à la boîte aux lettres partagée](../../media/e6c58953-f6d7-4f0b-97ba-308516bf2a94.png)

7. Sélectionnez **Fermer**.

Vous bénéficiez à présent d’une boîte aux lettres partagée dotée d’un calendrier partagé. Passez à l’étape suivante : [Bloquer la connexion pour le compte de boîte aux lettres partagée](#block-sign-in-for-the-shared-mailbox-account).

## <a name="which-permissions-should-you-use"></a>Quelles autorisations devez-vous utiliser ?

Vous pouvez utiliser les autorisations suivantes avec une boîte aux lettres partagée :

- **Accès total** : l'autorisation Accès total permet à un utilisateur d'ouvrir la boîte aux lettres partagée et d'agir comme le propriétaire de cette boîte aux lettres. Après avoir accédé à la boîte aux lettres partagée, un utilisateur peut créer des éléments de calendrier, lire, afficher, supprimer et modifier des courriers électroniques, créer des tâches et contacts de calendrier. Toutefois, un utilisateur doté d'une autorisation Accès total ne peut pas envoyer de messages à partir de la boîte aux lettres partagée à moins de disposer de l'autorisation Envoyer en tant que ou Envoyer de la part de.

- **Envoyer en tant que**: l'autorisation Envoyer en tant que permet à un utilisateur d'emprunter l'identité du propriétaire de la boîte aux lettres partagée pour envoyer des messages. Par exemple, si Katerina se connecte à la boîte aux lettres partagée du service Marketing et envoie un message, le service Marketing semblera en être l'expéditeur.

- **Envoyer de la part de** : l’autorisation Envoyer de la part de permet à l’utilisateur d’envoyer des messages de la part de la boîte aux lettres partagée. Par exemple, si John se connecte à la boîte aux lettres partagée Reception Building 32 et envoie un message, ce dernier semblera avoir été envoyé par « John de la part de Reception Building 32 ». Vous ne pouvez pas utiliser le Centre d’administration Exchange pour accorder l’autorisation « Envoyer de la part de ». Pour ce faire, vous devez utiliser l’applet de commande **Set-Mailbox** avec le paramètre _GrantSendonBehalf_.

### <a name="use-the-eac-to-edit-shared-mailbox-delegation"></a>Utiliser le CAE pour modifier la délégation de boîte aux lettres partagée

1. Dans le CAE, accédez à **Destinataires** \> **Partagé**. Sélectionnez la boîte aux lettres partagée, puis sélectionnez **Modifier** ![Icône Modifier.](../../media/ITPro-EAC-EditIcon.png).

2. Sélectionnez **Délégation de boîte aux lettres**.

3. Pour accorder ou supprimer les autorisations Accès total et Envoyer en tant que, sélectionnez **Ajouter** ![Ajouter une icône](../../media/ITPro-EAC-AddIcon.png) ou sur **Supprimer** ![Supprimer une icône](../../media/ITPro-EAC-RemoveIcon.gif), puis sélectionnez les utilisateurs auxquels vous souhaitez accorder ou retirer les autorisations.

   > [!NOTE]
   > L'autorisation Accès total permet aux utilisateurs d'ouvrir la boîte aux lettres, d'y créer des éléments et de les modifier. L'autorisation Envoyer en tant que permet à toute personne autre que le propriétaire de la boîte aux lettres d'envoyer des courriers électroniques à partir de cette boîte aux lettres partagée. Les deux autorisations sont requises pour que la boîte aux lettres partagée fonctionne.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.


## <a name="block-sign-in-for-the-shared-mailbox-account"></a>Bloquez la connexion pour le compte de boîte aux lettres partagée.

Chaque boîte aux lettres partagée a un compte d'utilisateur correspondant. Vous n'avez pas été invité à fournir un mot de passe lors de la création de la boîte aux lettres partagée ? Le compte a un mot de passe qui est généré par le système (inconnu). Vous n'êtes pas censé utiliser le compte pour vous connecter à la boîte aux lettres partagée.

Mais que se passe-t-il si un administrateur se contente de réinitialiser le mot de passe du compte d'utilisateur de la boîte aux lettres partagée ? Ou que se passe-t-il si un utilisateur malveillant accède aux informations d’identification du compte de boîte aux lettres partagée ? Cela permettrait au compte d’utilisateur de se connecter à la boîte aux lettres partagée et d'envoyer des courriers électroniques. Pour empêcher cela, vous devez bloquer la connexion pour le compte qui est associé à la boîte aux lettres partagée.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

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

La création de votre boîte aux lettres partagée entraîne automatiquement la création d’un calendrier partagé. Nous vous recommandons d’utiliser ce calendrier plutôt qu’un calendrier SharePoint pour effectuer le suivi de vos rendez-vous et de la localisation de vos contacts. Un calendrier partagé est intégré avec Outlook et est beaucoup plus facile à utiliser que celui de SharePoint.

1. Dans l'application Outlook, accédez à l'affichage Calendrier, puis sélectionnez la boîte aux lettres partagée.

2. Lorsque vous entrez des rendez-vous, chaque membre de la boîte aux lettres partagée peut les voir.

3. N’importe quel membre de la boîte aux lettres partagée peut créer, afficher et gérer des rendez-vous dans le calendrier, tout comme ils le feraient leurs rendez-vous personnels. Tous les membres de la boîte aux lettres partagée peuvent voir les modifications apportées au calendrier partagé.

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Configurer une boîte aux lettres partagée](configure-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)
