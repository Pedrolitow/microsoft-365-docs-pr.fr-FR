---
title: Afficher et débloquer les messages mis en quarantaine à partir de boîtes aux lettres partagées
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Les utilisateurs peuvent apprendre à afficher et agir sur les messages mis en quarantaine qui ont été envoyés aux boîtes aux lettres partagées auxquelles ils ont des autorisations.
ms.openlocfilehash: 34a401d3bff66926acd3e04d7144ce465dfa3dbb
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688028"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Afficher et débloquer les messages mis en quarantaine à partir de boîtes aux lettres partagées

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont actuellement en version préliminaire, ne sont pas disponibles pour tous les utilisateurs et peuvent faire l’objet de modifications.

Les utilisateurs peuvent gérer les messages mis en quarantaine lorsqu’il s’agit de l’un des destinataires, comme décrit dans la rubrique [Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md). Qu’en est-il des boîtes aux lettres partagées dans lesquelles l’utilisateur dispose des autorisations accès total et envoyer en tant que ou envoyer en tant que pour la boîte aux lettres, comme décrit dans la rubrique [boîtes aux lettres partagées dans Exchange Online](https://docs.microsoft.com/exchange/collaboration-exo/shared-mailboxes)?

Auparavant, la possibilité pour les utilisateurs de gérer les messages mis en quarantaine envoyés à une boîte aux lettres partagée a demandé aux administrateurs de laisser le mappage automatique activé pour la boîte aux lettres partagée (il est activé par défaut lorsqu’un administrateur accorde à un utilisateur l’accès à une autre boîte aux lettres). Toutefois, en fonction de la taille et du nombre de boîtes aux lettres auxquelles l’utilisateur a accès, les performances peuvent souffrir de l’ouverture de *toutes les* boîtes aux lettres auxquelles l’utilisateur a accès. Pour cette raison, de nombreux administrateurs choisissent de [supprimer le mappage automatique pour les boîtes aux lettres partagées](https://docs.microsoft.com/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Désormais, le mappage automatique n’est plus nécessaire pour que les utilisateurs puissent gérer les messages mis en quarantaine qui ont été envoyés à des boîtes aux lettres partagées. Elle fonctionne uniquement. Il existe deux méthodes différentes pour accéder aux messages mis en quarantaine qui ont été envoyés à une boîte aux lettres partagée :

- Si l’administrateur a [activé les notifications de courrier indésirable de l’utilisateur final](https://docs.microsoft.com/microsoft-365/security/office-365-security/configure-your-spam-filter-policies) dans les stratégies de blocage du courrier indésirable, tous les utilisateurs ayant accès aux notifications de courrier indésirable de l’utilisateur final dans la boîte aux lettres partagée peuvent cliquer sur le bouton **examiner** dans la notification pour accéder à la quarantaine dans le centre de sécurité & Compliance Center. Notez que cette méthode permet uniquement aux utilisateurs de gérer les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée. Les utilisateurs ne peuvent pas gérer leurs propres messages de mise en quarantaine dans ce contexte.

- L’utilisateur peut [passer en quarantaine dans le centre de sécurité & conformité](find-and-release-quarantined-messages-as-a-user.md). Par défaut, seuls les messages qui ont été envoyés à l’utilisateur sont affichés. Toutefois, l’utilisateur peut modifier les **résultats du tri** (le **bouton ID du message** par défaut) en adresse de messagerie du **destinataire**, entrer l’adresse de messagerie de la boîte aux lettres partagée, puis cliquer sur **Actualiser** pour afficher les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée.

  ![Tri des messages mis en quarantaine par adresse de messagerie de destinataire.](../../media/quarantine-sort-results-by-recipient-email-address.png)

Quelle que soit la méthode, les utilisateurs peuvent éviter toute confusion en incluant la colonne **Recipient** pour les messages mis en quarantaine. Le nombre maximal de colonnes à afficher est de 7, de sorte que l’utilisateur doit cliquer sur **modifier les colonnes**, supprimer une colonne existante (par exemple, **type de stratégie**), sélectionner le **destinataire**, puis cliquer sur **Enregistrer** ou **Enregistrer comme valeur par défaut**.

  ![Supprimez la colonne type de stratégie et ajoutez la colonne destinataire en quarantaine.](../../media/quarantine-add-recipient-column.png)

## <a name="things-to-keep-in-mind"></a>Éléments à garder à l’esprit

- Le premier utilisateur qui agira sur le message en quarantaine décide le devenir du message pour toutes les personnes qui utilisent la boîte aux lettres partagée. Par exemple, si 10 utilisateurs accèdent à une boîte aux lettres partagée et qu’un utilisateur décide de supprimer le message de mise en quarantaine, le message est supprimé pour les 10 utilisateurs. De même, si un utilisateur décide de libérer le message, il est publié dans la boîte aux lettres partagée et accessible par tous les autres utilisateurs de la boîte aux lettres partagée.

- Actuellement, le bouton **bloquer l’expéditeur** n’est pas disponible dans la fenêtre mobile des **Détails** pour les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée.

- Pour gérer les messages mis en quarantaine pour la boîte aux lettres partagée dans [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell), l’utilisateur final doit utiliser la cmdlet [Get-QuarantineMessage avec une](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage) adresse de messagerie de boîte aux lettres partagée pour la valeur du paramètre _destinatairel’adresse_ afin d’identifier les messages. Par exemple :

  ```powershell
  Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com
  ```

  Ensuite, l’utilisateur final peut sélectionner un message en quarantaine dans la liste pour l’afficher ou effectuer une action.

  Cet exemple montre tous les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée, puis libère le premier message de la liste en quarantaine (le premier message de la liste est 0, le second est 1, et ainsi de suite).

  ```powershell
  $SharedMessages = Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantinedMessage -Identity $SharedMessages[0]
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez les rubriques suivantes :

  - [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessageheader)
  - [Aperçu-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/release-quarantinemessage)
