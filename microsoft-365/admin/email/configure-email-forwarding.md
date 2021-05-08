---
title: Configurer le transfert des e-mails
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: Configurer le forwarding de courrier vers un ou plusieurs comptes de messagerie à l’aide d’Office 365.
ms.openlocfilehash: b5612a915fce21e9e9865fca6cb2275d8af17bd2
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52242407"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>Configurer le forwarding du courrier électronique dans Microsoft 365

En tant qu’administrateur d’une organisation, vous pouvez avoir des exigences d’entreprise pour configurer le transport de courrier pour la boîte aux lettres d’un utilisateur. Le forwarding de courrier vous permet de forwarder les messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers la boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de votre organisation.

> [!IMPORTANT]
> Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le forwarding automatique vers des destinataires externes. Pour plus d’informations, voir [Control automatic external email forwarding in Microsoft 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/external-email-forwarding?view=o365-worldwide&preserve-view=true#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

## <a name="configure-email-forwarding"></a>Configurer le transfert des e-mails

Avant de configurer le forwarding du courrier électronique, notez les remarques suivantes :

- Une fois que vous avez mis en place  le forwarding du courrier, seuls les nouveaux **messages** électroniques envoyés à partir de la boîte aux lettres sont transmis.

- Le forwarding de courrier nécessite que le  *compte de*  provenance dispose d’une licence. Si vous avez mis en place le forwarding du courrier électronique parce que l’utilisateur a quitté votre organisation, une autre option consiste à convertir sa boîte aux lettres [en boîte aux lettres partagée.](convert-user-mailbox-to-shared-mailbox.md) De cette façon, plusieurs personnes peuvent y accéder. Toutefois, une boîte aux lettres partagée ne peut pas dépasser 50 Go.

Vous devez être administrateur Exchange administrateur général ou administrateur général Microsoft 365 pour pouvoir suivre ces étapes. Pour plus d’informations, voir la rubrique [à propos des rôles d’administrateur.](../add-users/about-admin-roles.md)

1. Dans le centre d’administration, allez à la page **Utilisateurs** \> **[actifs.](https://go.microsoft.com/fwlink/p/?linkid=834822)**

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez envoyer le courrier électronique pour ouvrir la page de propriétés.

3. Sous **l’onglet** Courrier, **sélectionnez Gérer le forwarding de courrier.**

4. Dans la page De forwarding de courrier, sélectionnez Forward **all emails sent to this mailbox,** enter the forwarding address, and choose whether you want to keep a copy of forwarded emails. Si cette option n’est pas disponible, assurez-vous qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer les modifications**.

    **Pour le forward vers plusieurs adresses** e-mail, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour le forward aux adresses. Pour plus d’informations, voir [Utiliser des règles pour envoyer automatiquement des messages.](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746)

     Ou bien, dans le Centre d’administration, créez un groupe de [distribution,](../setup/create-distribution-lists.md)ajoutez-y les [adresses,](add-user-or-contact-to-distribution-list.md)puis définissez le forwarding pour qu’il pointe vers la DL en suivant les instructions de cet article.

5. Ne supprimez pas le compte de l’utilisateur de messagerie que vous êtes en train de forwarder ou supprimez sa licence !  Si vous le faites, le forwarding du courrier électronique s’arrête.