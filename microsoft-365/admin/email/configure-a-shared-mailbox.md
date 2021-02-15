---
title: Configurer les paramètres de boîte aux lettres partagée
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
description: Une fois que vous avez créé une boîte aux lettres partagée, vous pouvez configurer certains paramètres pour ses utilisateurs, tels que le forwarding des messages électroniques et les réponses automatiques. Par la suite, vous voudrez peut-être modifier d’autres paramètres, tels que le nom ou les membres de la boîte aux lettres.
ms.openlocfilehash: fe5d35be556b8edf5456bc2c0b820dc0ce77e323
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49926605"
---
# <a name="configure-shared-mailbox-settings"></a>Configurer les paramètres de boîte aux lettres partagée

Une fois que vous [avez](create-a-shared-mailbox.md)créé une boîte aux lettres partagée, vous pouvez configurer certains paramètres pour les utilisateurs de la boîte aux lettres, tels que le forwarding des messages électroniques et les réponses automatiques. Par la suite, vous pouvez modifier d’autres paramètres, tels que le nom de la boîte aux lettres, les membres ou les autorisations des membres. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Modifier le nom ou l’alias de messagerie d’une boîte aux lettres partagée ou modifier l’adresse de messagerie principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **Modifier** en plus du nom, de la messagerie, des **alias de messagerie.**

3. Entrez un nouveau nom ou ajoutez un autre alias. Si vous souhaitez modifier l’adresse de messagerie principale, votre boîte aux lettres doit avoir plusieurs alias de messagerie.

4. Sélectionnez **Enregistrer**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Transférer des courriers qui sont envoyés à une boîte aux lettres partagée

Il n’est pas nécessaire d’attribuer une licence à la boîte aux lettres partagée pour pouvoir envoyer le courrier électronique qui lui est envoyé. Vous pouvez envoyer les messages à n’importe quelle adresse de messagerie ou liste de distribution valide.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **Modifier le courrier** \> **électronique.**
    
3. Définissez le basculement sur **Sur,** puis entrez une adresse de messagerie à qui les messages sont transmis. Il peut s’y trouver n’importe quelle adresse de messagerie valide. Pour le faire, vous devez créer un groupe de [distribution](https://docs.microsoft.com/office365/admin/setup/create-distribution-lists) pour les adresses, puis entrer le nom du groupe dans cette zone.
    
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

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier les réponses automatiques.** \> 
    
3. Définissez le basculement sur **Sur** et choisissez d’envoyer la réponse à des personnes à l’intérieur de votre organisation ou à l’extérieur de votre organisation.

4. Entrez la réponse que vous voulez envoyer aux personnes internes à votre organisation. Vous ne pouvez pas ajouter d'images, seulement du texte.

5. Si vous souhaitez *également* envoyer une réponse à des personnes extérieures à votre organisation, cochez la case, qui vous souhaitez obtenir la réponse, puis tapez le texte. Vous ne pouvez pas envoyer la réponse uniquement à des personnes externes à votre organisation sans l'envoyer à des personnes internes à votre organisation.

6. Sélectionnez **Enregistrer**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Autoriser tout le monde à voir le courrier envoyé (les réponses)

Par défaut, les courriers envoyés à partir de la boîte aux lettres partagée ne sont pas enregistrés dans le dossier Éléments envoyés de la boîte aux lettres partagée. En revanche, ils sont enregistrés dans le dossier Éléments envoyés de la personne qui a envoyé le courrier.

Si vous souhaitez autoriser tout le monde à voir le courrier envoyé, dans le centre d’administration, modifiez les paramètres de boîte aux lettres partagée, puis sélectionnez **Éléments envoyés** \> **Modifier**.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Choisir les applications qu’une boîte aux lettres partagée peut utiliser pour accéder à la messagerie électronique Microsoft

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier les applications de** \> **messagerie.**

3. Définissez le basculement sur **Sur pour** toutes les applications que vous souhaitez que les membres puissent utiliser pour accéder à la boîte aux lettres partagée. Définissez le basculement sur **Off** pour toutes les applications que vous ne souhaitez pas qu’elles utilisent. 

4. Sélectionnez **Enregistrer**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Placer une boîte aux lettres partagée en attente pour litige

Pour en savoir plus sur la attente pour litige, voir [Créer une attente pour litige.](https://docs.microsoft.com/microsoft-365/compliance/create-a-litigation-hold)

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier la mise en attente pour** \> **litige.**

3. Définissez le basculement sur **Sur**. 

4. Éventuellement, entrez une durée, une note sur la attente et une URL avec plus d’informations.  

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

2. Sélectionnez la boîte aux lettres  partagée que vous souhaitez modifier, puis sélectionnez \> **Modifier les membres.**

3. Effectuez l’une des opérations suivantes :
   - Pour ajouter des membres, **sélectionnez Ajouter des membres,** recherchez ou sélectionnez un membre à ajouter, puis sélectionnez **Enregistrer.**
   - Pour supprimer des membres, utilisez la zone de recherche pour rechercher le membre si nécessaire, sélectionnez **le X** en côté du nom du membre, puis sélectionnez **Enregistrer**. 

4. Sélectionnez **Enregistrer à** nouveau.

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

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Personnaliser** \> **les autorisations des membres.**

3. Sélectionnez **Modifier** en plus de l’autorisation que vous souhaitez modifier pour un membre. 

4. Effectuez l’une des opérations suivantes :
   - Pour accorder cette autorisation à un membre supplémentaire, sélectionnez Ajouter des **autorisations,** recherchez ou sélectionnez un membre à ajouter, puis sélectionnez **Enregistrer.**
   - Pour supprimer l’autorisation d’un membre, utilisez la zone De recherche pour rechercher le membre si nécessaire, sélectionnez **le X** en de côté du nom du membre, puis sélectionnez **Enregistrer**. 

4. Sélectionnez **Enregistrer à** nouveau.

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Afficher ou masquer une boîte aux lettres partagée dans la liste d’adresses globale

Si vous choisissez de ne pas afficher la boîte aux lettres partagée dans la liste d’adresses globale, la boîte aux lettres n’apparaîtra pas dans la liste d’adresses de votre organisation, mais elle recevra toujours des messages électroniques qui lui seront envoyés. 

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

::: moniker-end 

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Groupes** > **Boîtes aux lettres partagées**. 

::: moniker-end

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Afficher dans la liste d’adresses globale** \> **Modifier.**

3. Définissez le toggle sur **On**  ou **Off**. 

4. Sélectionnez **Enregistrer**.

> [!NOTE]
> Le fait de masquer une boîte aux lettres partagée dans la liste d’adresses empêche les nouveaux membres de la boîte aux lettres partagée d’ajouter la boîte aux lettres masquée à leur profil Outlook tant que la boîte aux lettres partagée n’est pas de nouveau affichée dans la liste d’adresses. 

## <a name="related-articles"></a>Articles connexes

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md)

[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md)

[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md)

[Supprimer une licence à partir d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md)

[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md)
