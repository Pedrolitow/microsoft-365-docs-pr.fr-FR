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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Créez une boîte aux lettres partagée et configurez certains paramètres pour ses utilisateurs, tels que le transfert de courrier électronique et les réponses automatiques.
ms.openlocfilehash: b3de51a8407c8f9786d6a1677137f2a564744ac0
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437148"
---
# <a name="configure-microsoft-365-shared-mailbox-settings"></a>Configurer Microsoft 365 paramètres de boîte aux lettres partagée

Une fois que vous avez [créé une boîte aux lettres partagée](create-a-shared-mailbox.md), vous devez configurer certains paramètres pour les utilisateurs de la boîte aux lettres, tels que le transfert de courrier électronique et les réponses automatiques. Par la suite, vous souhaiterez peut-être modifier d’autres paramètres, tels que le nom de la boîte aux lettres, les membres ou les autorisations de membre. 

## <a name="change-the-name-or-email-alias-of-a-shared-mailbox-or-change-the-primary-email-address"></a>Modifier le nom ou l’alias de messagerie d’une boîte aux lettres partagée, ou modifier l’adresse e-mail principale

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis **sélectionnez Modifier** en regard du **nom, de l’e-mail et des alias de messagerie**.

3. Entrez un nouveau nom ou ajoutez un autre alias. Si vous souhaitez modifier l’adresse e-mail principale, votre boîte aux lettres doit avoir plusieurs alias de messagerie.

4. Sélectionnez **Enregistrer**.

## <a name="forward-emails-that-are-sent-to-a-shared-mailbox"></a>Transférer des courriers qui sont envoyés à une boîte aux lettres partagée

Vous n’avez pas besoin d’attribuer une licence à la boîte aux lettres partagée pour transférer l’e-mail qui lui est envoyé. Vous pouvez transférer les messages vers n’importe quelle adresse e-mail ou liste de distribution valide.

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier** **le transfert de** \> courrier électronique.
    
3. Définissez le bouton bascule **sur Activé** et entrez une adresse e-mail vers laquelle transférer les messages. Il peut s’agir de n’importe quelle adresse e-mail valide. Pour transférer vers plusieurs adresses, vous devez [créer un groupe de distribution](/office365/admin/setup/create-distribution-lists) pour les adresses, puis entrer le nom du groupe dans cette zone.
    
4. Sélectionnez **Enregistrer**.

## <a name="send-automatic-replies-from-a-shared-mailbox"></a>Envoyer des réponses automatiques à partir d'une boîte aux lettres partagée

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier les réponses automatiques**\>.
    
3. Définissez le bouton bascule **sur Activé** et choisissez d’envoyer la réponse à des personnes au sein de votre organisation ou à l’extérieur de votre organisation.

4. Entrez la réponse que vous voulez envoyer aux personnes internes à votre organisation. Vous ne pouvez pas ajouter d'images, seulement du texte.

5. Si vous souhaitez *également* envoyer une réponse à des personnes extérieures à votre organisation, activez la case à cocher, qui vous souhaitez obtenir la réponse, puis tapez le texte. Vous ne pouvez pas envoyer la réponse uniquement à des personnes externes à votre organisation sans l'envoyer à des personnes internes à votre organisation.

6. Sélectionnez **Enregistrer**.

## <a name="allow-everyone-to-see-the-sent-email-the-replies"></a>Autoriser tout le monde à voir le courrier envoyé (les réponses)

Par défaut, les courriers envoyés à partir de la boîte aux lettres partagée ne sont pas enregistrés dans le dossier Éléments envoyés de la boîte aux lettres partagée. En revanche, ils sont enregistrés dans le dossier Éléments envoyés de la personne qui a envoyé le courrier.

Si vous souhaitez autoriser tout le monde à voir l’e-mail envoyé, dans le centre d’administration, modifiez les paramètres de boîte aux lettres partagée, puis sélectionnez **Éléments envoyés** \> **Modifier**.


## <a name="choose-the-apps-that-a-shared-mailbox-can-use-to-access-microsoft-email"></a>Choisir les applications qu’une boîte aux lettres partagée peut utiliser pour accéder à la messagerie Microsoft

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Modifier** les **applications** \> de messagerie.

3. Définissez le bouton bascule **sur Activé** pour toutes les applications que vous souhaitez que les membres puissent utiliser pour accéder à la boîte aux lettres partagée. Définissez le bouton bascule **sur Désactivé** pour toutes les applications que vous ne souhaitez pas qu’elles utilisent. 

4. Sélectionnez **Enregistrer**.


## <a name="put-a-shared-mailbox-on-litigation-hold"></a>Mettre une boîte aux lettres partagée en attente de litige

Pour en savoir plus sur la conservation des litiges, consultez [Créer une conservation des litiges](../../compliance/create-a-litigation-hold.md).

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée que vous souhaitez modifier, puis sélectionnez **Modifier la conservation** \> des **litiges**.

3. Définissez le bouton bascule **sur Activé**. 

4. Si vous le souhaitez, entrez une durée, une note de suspension et une URL contenant plus d’informations.  

5. Sélectionnez **Enregistrer**.


## <a name="add-or-remove-members"></a>Ajouter ou supprimer des membres

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Membres** \> **modifier**.

3. Effectuez l'une des opérations suivantes :
   - Pour ajouter des membres, **sélectionnez Ajouter des membres**, recherchez ou sélectionnez un membre à ajouter, puis **sélectionnez Enregistrer**.
   - Pour supprimer des membres, utilisez la zone de recherche pour rechercher le membre si nécessaire, sélectionnez le **X** en regard du nom du membre, puis **sélectionnez Enregistrer**. 

4. Sélectionnez **Enregistrer** à nouveau.

## <a name="add-or-remove-permissions-of-members"></a>Ajouter ou supprimer des autorisations de membres

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis sélectionnez **Membres** \> **Personnaliser les autorisations**.

3. Sélectionnez **Modifier** en regard de l’autorisation que vous souhaitez modifier pour un membre. 

4. Effectuez l'une des opérations suivantes :
   - Pour accorder cette autorisation à un membre supplémentaire, sélectionnez **Ajouter des autorisations**, recherchez ou sélectionnez un membre à ajouter, puis **sélectionnez Enregistrer**.
   - Pour supprimer l’autorisation d’un membre, utilisez la zone de recherche pour rechercher le membre si nécessaire, sélectionnez le **X** en regard du nom du membre, puis **sélectionnez Enregistrer**. 

4. Sélectionnez **Enregistrer** à nouveau.

## <a name="show-or-hide-a-shared-mailbox-in-the-global-address-list"></a>Afficher ou masquer une boîte aux lettres partagée dans la liste d’adresses globale

Si vous choisissez de ne pas afficher la boîte aux lettres partagée dans la liste d’adresses globale, la boîte aux lettres n’apparaît pas dans la liste d’adresses de votre organisation, mais elle reçoit toujours un e-mail qui lui est envoyé. 

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2066847" target="_blank">Boîtes aux lettres partagées</a>.

2. Sélectionnez la boîte aux lettres partagée à modifier, puis **sélectionnez Afficher dans la liste d’adresses** \> globale **Modifier**.

3. Définissez le bouton bascule **sur Activé**  ou **Désactivé**. 

4. Sélectionnez **Enregistrer**.

> [!NOTE]
> Le masquage d’une boîte aux lettres partagée dans la liste d’adresses empêche les nouveaux membres de boîte aux lettres partagées d’ajouter la boîte aux lettres masquée à leur profil Outlook jusqu’à ce que la boîte aux lettres partagée apparaisse à nouveau dans la liste d’adresses. 

## <a name="related-content"></a>Contenu associé

[À propos des boîtes aux lettres partagées](about-shared-mailboxes.md) (article)\
[Créer une boîte aux lettres partagée](create-a-shared-mailbox.md) (article)\
[Convertir une boîte aux lettres utilisateur en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md) (article)\
[Supprimer une licence d’une boîte aux lettres partagée](remove-license-from-shared-mailbox.md) (article)\
[Résoudre les problèmes liés aux boîtes aux lettres partagées](resolve-issues-with-shared-mailboxes.md) (article)