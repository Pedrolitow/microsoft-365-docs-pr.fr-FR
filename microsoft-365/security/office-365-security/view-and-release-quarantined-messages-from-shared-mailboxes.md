---
title: Afficher et libérer les messages mis en quarantaine à partir de boîtes aux lettres partagées
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Les utilisateurs peuvent apprendre à afficher et à agir sur les messages mis en quarantaine qui ont été envoyés à des boîtes aux lettres partagées pour qui ils ont des autorisations.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3efccca375745b0850c91039165b72a7d6f0bcb3
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49931445"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Afficher et libérer les messages mis en quarantaine à partir de boîtes aux lettres partagées

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont actuellement en prévisualisation, ne sont pas disponibles pour tout le monde et peuvent faire l’objet de changements.

Les utilisateurs peuvent gérer les messages mis en quarantaine lorsqu’ils sont l’un des destinataires, comme décrit dans Rechercher et libérer les messages mis en quarantaine en tant qu’utilisateur [dans EOP.](find-and-release-quarantined-messages-as-a-user.md) Mais qu’en est-il des boîtes aux lettres partagées où l’utilisateur dispose des autorisations Accès total et Envoyer en tant que ou Envoyer de la part de la boîte aux lettres comme décrit dans les boîtes aux lettres partagées [dans Exchange Online](https://docs.microsoft.com/exchange/collaboration-exo/shared-mailboxes)?

Auparavant, la possibilité pour les utilisateurs de gérer les messages mis en quarantaine envoyés à une boîte aux lettres partagée nécessitait aux administrateurs de laisser le mappage automatique activé pour la boîte aux lettres partagée (il est activé par défaut lorsqu’un administrateur donne à un utilisateur l’accès à une autre boîte aux lettres). Toutefois, en fonction de la taille et du nombre de boîtes aux lettres  à qui l’utilisateur a accès, les performances peuvent être réduites lorsque Outlook tente d’ouvrir toutes les boîtes aux lettres à l’accès de l’utilisateur. Pour cette raison, de nombreux administrateurs choisissent de [supprimer le mappage automatique pour les boîtes aux lettres partagées.](https://docs.microsoft.com/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox)

À présent, le mappage automatique n’est plus nécessaire pour que les utilisateurs gèrent les messages mis en quarantaine qui ont été envoyés à des boîtes aux lettres partagées. Cela fonctionne simplement. Il existe deux méthodes différentes pour accéder aux messages mis en quarantaine qui ont été envoyés à une boîte aux lettres partagée :

- Si l’administrateur a activé les notifications de courrier indésirable pour l’utilisateur final dans les [stratégies](https://docs.microsoft.com/microsoft-365/security/office-365-security/configure-your-spam-filter-policies) anti-courrier indésirable, tout utilisateur qui a accès aux notifications de courrier indésirable de l’utilisateur final dans la boîte aux lettres partagée peut cliquer sur le bouton Réviser dans la notification pour passer en quarantaine dans le Centre de sécurité & conformité.  Notez que cette méthode permet uniquement aux utilisateurs de gérer les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée. Les utilisateurs ne peuvent pas gérer leurs propres messages de mise en quarantaine dans ce contexte.

- L’utilisateur peut être mis en quarantaine dans le Centre de [sécurité & conformité.](find-and-release-quarantined-messages-as-a-user.md) Par défaut, seuls les messages envoyés à l’utilisateur sont affichés. Toutefois, l’utilisateur peut modifier les résultats du tri **(le** bouton **ID** de message par  défaut) en adresse de messagerie du **destinataire,** entrer l’adresse de messagerie de la boîte aux lettres partagée, puis cliquer sur Actualiser pour voir les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée.

  ![Tri des messages mis en quarantaine par adresse de messagerie du destinataire.](../../media/quarantine-sort-results-by-recipient-email-address.png)

Quelle que soit la méthode utilisée, les utilisateurs peuvent éviter toute confusion en incluant la colonne **Destinataire** pour les messages mis en quarantaine. Le nombre maximal de colonnes à afficher est de 7. L’utilisateur doit donc cliquer sur Modifier les  **colonnes,** supprimer une colonne existante (par exemple, **type** de stratégie), sélectionner le **destinataire,** puis cliquer sur Enregistrer ou enregistrer par **défaut.**

  ![Supprimez la colonne Type de stratégie et ajoutez la colonne Destinataire en quarantaine.](../../media/quarantine-add-recipient-column.png)

## <a name="things-to-keep-in-mind"></a>Éléments à garder à l’esprit

- Le premier utilisateur à agir sur le message mis en quarantaine décide de la fin du message pour toutes les personnes qui utilisent la boîte aux lettres partagée. Par exemple, si une boîte aux lettres partagée est accessible par 10 utilisateurs et qu’un utilisateur décide de supprimer le message de mise en quarantaine, le message est supprimé pour les 10 utilisateurs. De même, si un utilisateur décide de libérer le message, il est publié dans la boîte aux lettres partagée et est accessible par tous les autres utilisateurs de la boîte aux lettres partagée.

- Actuellement, le bouton Bloquer **l’expéditeur** n’est pas disponible dans le volant Détails pour les messages mis en quarantaine qui ont été **envoyés** à la boîte aux lettres partagée.

- Pour gérer les messages mis en quarantaine pour la boîte aux lettres partagée dans [Exchange Online PowerShell,](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)l’utilisateur final doit utiliser la cmdlet [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage) avec une adresse de messagerie de boîte aux lettres partagée pour la valeur du paramètre _RecipientAddress_ pour identifier les messages. Par exemple :

  ```powershell
  Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com
  ```

  Ensuite, l’utilisateur final peut sélectionner un message mis en quarantaine dans la liste pour afficher ou prendre des mesures.

  Cet exemple montre tous les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée, puis libère le premier message de la liste de la quarantaine (le premier message de la liste est 0, le deuxième est 1, et ainsi de suite).

  ```powershell
  $SharedMessages = Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantinedMessage -Identity $SharedMessages[0]
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez les rubriques suivantes :

  - [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/release-quarantinemessage)
