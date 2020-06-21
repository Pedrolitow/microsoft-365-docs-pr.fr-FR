---
title: Configurer les paramètres de boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Une fois que vous avez créé une boîte aux lettres partagée, vous pouvez configurer certains paramètres pour ses utilisateurs, tels que le transfert de courrier électronique et les réponses automatiques. Par la suite, vous pouvez modifier d’autres paramètres, tels que le nom de la boîte aux lettres ou les membres.
ms.openlocfilehash: 3bde856f4db80192f5ed058a18c7942aa6a724b2
ms.sourcegitcommit: 9ea67fd2e02af760d4fb62e3d09c93b446173f9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44739205"
---
# <a name="configure-shared-mailbox-settings"></a>Configurer les paramètres de boîte aux lettres partagée

Une fois que vous avez [créé une boîte aux lettres partagée](create-a-shared-mailbox.md), vous pouvez configurer certains paramètres pour les utilisateurs de boîtes aux lettres, tels que le transfert de courrier électronique et les réponses automatiques. Par la suite, vous souhaiterez peut-être modifier d’autres paramètres, tels que le nom de la boîte aux lettres, les membres ou les autorisations des membres. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Modifier le nom ou l’alias de messagerie d’une boîte aux lettres partagée, ou modifier l’adresse de messagerie principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis cliquez sur **modifier** en regard de **nom, adresse de messagerie, alias de messagerie**.

3. Entrez un nouveau nom ou ajoutez un autre alias. Si vous souhaitez modifier l’adresse de messagerie principale, votre boîte aux lettres doit avoir plusieurs alias de messagerie.

4. Sélectionnez **Enregistrer**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Transférer des courriers qui sont envoyés à une boîte aux lettres partagée

Il n’est pas nécessaire d’attribuer une licence à la boîte aux lettres partagée afin de transférer le courrier électronique qui lui a été envoyé. Vous pouvez transférer les messages vers n’importe quelle adresse de messagerie ou liste de distribution valide.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis cliquez sur modifier le **transfert du courrier** \> **Edit**.
    
3. Définissez le bouton bascule **sur activé**, puis entrez une adresse de messagerie à laquelle transférer les messages. Il peut s’agir de n’importe quelle adresse de messagerie valide. Pour transférer vers plusieurs adresses, vous devez [créer un groupe de distribution](https://docs.microsoft.com/office365/admin/setup/create-distribution-lists?view=o365-worldwide) pour les adresses, puis entrer le nom du groupe dans cette zone.
    
4. Sélectionnez **Enregistrer**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Envoyer des réponses automatiques à partir d'une boîte aux lettres partagée

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez modification des **réponses automatiques** \> **Edit**.
    
3. Définissez le bouton bascule **sur activé**, puis indiquez si vous souhaitez envoyer la réponse à des personnes au sein de votre organisation ou à l’extérieur de votre organisation.

4. Entrez la réponse que vous voulez envoyer aux personnes internes à votre organisation. Vous ne pouvez pas ajouter d'images, seulement du texte.

5. Si vous souhaitez *également* envoyer une réponse à des personnes extérieures à votre organisation, activez la case à cocher, qui vous souhaitez obtenir la réponse, puis tapez le texte. Vous ne pouvez pas envoyer la réponse uniquement à des personnes externes à votre organisation sans l'envoyer à des personnes internes à votre organisation.

6. Sélectionnez **Enregistrer**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Autoriser tout le monde à voir le courrier envoyé (les réponses)

By default, messages sent from the shared mailbox aren't saved to the Sent Items folder of the shared mailbox. Instead, they are saved to the Sent Items folder of the person who sent the message.

Si vous souhaitez autoriser tout le monde à voir le courrier envoyé, dans le centre d’administration, modifiez les paramètres de boîte aux lettres partagée, puis sélectionnez **éléments envoyés** \> **Edit**.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Choisir les applications qu’une boîte aux lettres partagée peut utiliser pour accéder à la messagerie Microsoft

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **applications de messagerie** \> **modifier**.

3. Définissez le bouton bascule **sur activé** pour toutes les applications que vous souhaitez que les membres puissent utiliser pour accéder à la boîte aux lettres partagée. **Désactivez** le bouton bascule pour toutes les applications que vous ne voulez pas utiliser. 

4. Sélectionnez **Enregistrer**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Placer une boîte aux lettres partagée en conservation pour litige

Pour en savoir plus sur la conservation pour litige, consultez [la rubrique Création d’une conservation pour litige](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold).

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez Modifier la **conservation pour litige** \> **Edit**.

3. Définissez le bouton bascule **sur activé**. 

4. Si vous le souhaitez, entrez une durée, la note de la suspension et une URL avec davantage d’informations.  

5. Sélectionnez **Enregistrer**.


## <a name="add-or-remove-members"></a>Ajouter ou supprimer des membres

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **membres** \> **modifier**.

3. Effectuez l’une des opérations suivantes :
   - Pour ajouter des membres, sélectionnez **Ajouter des membres**, recherchez ou sélectionnez un membre à ajouter, puis sélectionnez **Enregistrer**.
   - Pour supprimer des membres, utilisez la zone de recherche pour rechercher le membre si nécessaire, sélectionnez le **X** en regard du nom du membre, puis sélectionnez **Enregistrer**. 

4. Sélectionnez de nouveau **Enregistrer** .

## <a name="add-or-remove-permissions-of-members"></a>Ajouter ou supprimer des autorisations de membres

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **membres** \> **personnaliser les autorisations**.

3. Sélectionnez **modifier** en regard de l’autorisation que vous souhaitez modifier pour un membre. 

4. Effectuez l’une des opérations suivantes :
   - Pour accorder cette autorisation à un membre supplémentaire, sélectionnez **Ajouter des autorisations**, Rechercher ou sélectionner un membre à ajouter, puis sélectionnez **Enregistrer**.
   - Pour supprimer l’autorisation d’un membre, utilisez la zone de recherche pour rechercher le membre si nécessaire, sélectionnez le **X** en regard du nom du membre, puis sélectionnez **Enregistrer**. 

4. Sélectionnez de nouveau **Enregistrer** .

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Afficher ou masquer une boîte aux lettres partagée dans la liste d’adresses globale

Si vous choisissez de ne pas afficher la boîte aux lettres partagée dans la liste d’adresses globale, celle-ci n’apparaît pas dans la liste d’adresses de votre organisation, mais elle reçoit toujours le courrier envoyé. 

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **afficher dans la modification de la liste d’adresses globale** \> **Edit**.

3. Activer ou **Désactiver**le bouton **On** bascule. 

4. Sélectionnez **Enregistrer**.

> [!NOTE]
> Le masquage d’une liste d’adresses à partir d’une boîte aux lettres partagée empêche les nouveaux membres de la boîte aux lettres partagée d’ajouter la boîte aux lettres masquée à leur profil Outlook jusqu’à ce que la boîte aux lettres partagée s’affiche à nouveau dans la liste d’adresses. 

## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
