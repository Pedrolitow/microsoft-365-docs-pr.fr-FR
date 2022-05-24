---
title: Afficher et libérer des messages mis en quarantaine à partir de boîtes aux lettres partagées
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Les utilisateurs peuvent apprendre à afficher et à agir sur les messages mis en quarantaine envoyés aux boîtes aux lettres partagées auxquelles ils disposent d’autorisations.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2613d3b8be200db3a9107355a27b0dd79ce537d3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647338"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Afficher et libérer des messages mis en quarantaine à partir de boîtes aux lettres partagées

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les utilisateurs peuvent gérer les messages mis en quarantaine où ils sont l’un des destinataires, comme décrit dans [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md). Mais qu’en est-il **des boîtes aux lettres partagées** où l’utilisateur dispose d’autorisations d’accès complet et d’envoi en tant que ou en nom à la boîte aux lettres, comme décrit dans [les boîtes aux lettres partagées dans Exchange Online](/exchange/collaboration-exo/shared-mailboxes) ?

Auparavant, la possibilité pour les utilisateurs de gérer les messages mis en quarantaine envoyés à une boîte aux lettres partagée obligeait les administrateurs à laisser le mappage automatique activé pour la boîte aux lettres partagée (il est activé par défaut lorsqu’un administrateur donne à un utilisateur l’accès à une autre boîte aux lettres). Toutefois, selon la taille et le nombre de boîtes aux lettres auxquelles l’utilisateur a accès, les performances peuvent être affectées lorsque Outlook tente d’ouvrir _toutes les_ boîtes aux lettres auxquelles l’utilisateur a accès. Pour cette raison, de nombreux administrateurs choisissent de [supprimer le mappage automatique pour les boîtes aux lettres partagées](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

À présent, le mappage automatique n’est plus nécessaire pour que les utilisateurs gèrent les messages mis en quarantaine qui ont été envoyés aux boîtes aux lettres partagées. Ça marche. Il existe deux méthodes différentes pour accéder aux messages mis en quarantaine qui ont été envoyés à une boîte aux lettres partagée :

- Si l’administrateur a configuré des [stratégies de quarantaine](quarantine-policies.md) pour autoriser les notifications de quarantaine (anciennement les notifications de courrier indésirable de l’utilisateur final), tout utilisateur ayant accès aux notifications de mise en quarantaine dans la boîte aux lettres partagée peut cliquer sur le bouton **Révision** dans la notification pour accéder à la mise en quarantaine dans le portail Microsoft 365 Defender. Notez que cette méthode permet uniquement aux utilisateurs de gérer les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée. Les utilisateurs ne peuvent pas gérer leurs propres messages de quarantaine dans ce contexte.
- L’utilisateur peut [accéder à la mise en quarantaine dans le portail Microsoft 365 Defender](find-and-release-quarantined-messages-as-a-user.md) et cliquer sur **Filtrer** pour filtrer les résultats par **adresse de destinataire** (adresse e-mail de la boîte aux lettres partagée). Dans la page **de mise en quarantaine** principale, vous pouvez cliquer sur la colonne **Destinataire** pour trier par messages envoyés à la boîte aux lettres partagée.

## <a name="things-to-keep-in-mind"></a>Éléments à garder à l’esprit

- _Les stratégies de quarantaine_ définissent ce que les utilisateurs sont autorisés à faire ou non aux messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prises en charge). Les stratégies de quarantaine par défaut appliquent les fonctionnalités historiques qui permettent aux destinataires d’afficher et d’agir sur les messages. Les administrateurs peuvent créer et appliquer des stratégies de quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- Le premier utilisateur à agir sur le message mis en quarantaine détermine le sort du message pour toutes les personnes qui utilisent la boîte aux lettres partagée. Par exemple, si 10 utilisateurs accèdent à une boîte aux lettres partagée et qu’un utilisateur décide de supprimer le message de quarantaine, le message est supprimé pour les 10 utilisateurs. De même, si un utilisateur décide de libérer le message, il est publié dans la boîte aux lettres partagée et est accessible par tous les autres utilisateurs de la boîte aux lettres partagée.

- Actuellement, le bouton **Bloquer l’expéditeur** n’est pas disponible dans le menu volant Détails pour les messages mis en quarantaine qui ont été envoyés à la boîte aux **lettres** partagée.

- En ce qui concerne les opérations de quarantaine pour les boîtes aux lettres partagées, si vous utilisez des groupes de sécurité imbriqués pour accorder l’accès à une boîte aux lettres partagée, nous vous recommandons de ne pas dépasser deux niveaux de groupes imbriqués. Par exemple, le groupe A est membre du groupe B, qui est membre du groupe C. Pour attribuer des autorisations à une boîte aux lettres partagée, n’ajoutez pas l’utilisateur au groupe A, puis affectez le groupe C à la boîte aux lettres partagée.  

- Pour gérer les messages mis en quarantaine pour la boîte aux lettres partagée dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), l’utilisateur final doit utiliser l’applet de commande [Get-QuarantineMessage avec adresse e-mail](/powershell/module/exchange/get-quarantinemessage) de boîte aux lettres partagée pour la valeur du paramètre _RecipientAddress_ afin d’identifier les messages. Par exemple :

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  Ensuite, l’utilisateur final peut sélectionner un message mis en quarantaine dans la liste pour afficher ou prendre des mesures.

  Cet exemple montre tous les messages mis en quarantaine qui ont été envoyés à la boîte aux lettres partagée, puis libère le premier message de la liste de la mise en quarantaine (le premier message de la liste est 0, le second est 1, etc.).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez les rubriques suivantes :

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
