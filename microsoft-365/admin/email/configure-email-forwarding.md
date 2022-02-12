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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: Le forwarding de courrier vous permet de forwarder les messages électroniques envoyés à une boîte aux lettres Microsoft 365 utilisateur vers une autre boîte aux lettres à l’intérieur ou à l’extérieur de votre organisation.
ms.openlocfilehash: 5522d9202732ca54d1a395a83e99ae2442b68eb9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62766571"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>Configurer le forwarding du courrier électronique dans Microsoft 365

En tant qu’administrateur d’une organisation, vous pouvez avoir des exigences d’entreprise pour configurer le transport de courrier pour la boîte aux lettres d’un utilisateur. Le forwarding de courrier vous permet de forwarder les messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers la boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de votre organisation.

> [!IMPORTANT]
> Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le forwarding automatique vers des destinataires externes. Pour plus d’informations, voir [Control automatic external email forwarding in Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de collaborer avec [un spécialiste microsoft des petites entreprises](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Business Assist, vous et vos employés accédez 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="configure-email-forwarding"></a>Configurer le transfert des e-mails

Avant de configurer le forwarding du courrier électronique, notez les remarques suivantes :

- Autoriser l’envoi automatique de messages à des personnes sur le domaine distant. Pour [plus d’informations, voir](/exchange/mail-flow-best-practices/remote-domains/manage-remote-domains) Gérer les domaines distants.

- Une fois que vous avez mis en place le forwarding du courrier **, seuls** les nouveaux messages électroniques envoyés à partir de la boîte aux lettres sont transmis.

- Le forwarding de courrier électronique nécessite que le  *compte de*  provenance dispose d’une licence. Si vous avez mis en place le forwarding du courrier électronique parce que l’utilisateur a quitté votre organisation, une autre option consiste à convertir sa boîte aux lettres [en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md). De cette façon, plusieurs personnes peuvent y accéder. Toutefois, une boîte aux lettres partagée ne peut pas dépasser 50 Go.

Vous devez être administrateur Exchange administrateur général ou administrateur général Microsoft 365 pour pouvoir suivre ces étapes. Pour plus d’informations, voir la rubrique [Sur les rôles d’administrateur](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> **[actifs](https://go.microsoft.com/fwlink/p/?linkid=834822)** .

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez qu’il soit transmis, puis ouvrez la page des propriétés.

3. Sous **l’onglet Courrier** , **sélectionnez Gérer le forwarding du courrier** électronique.

4. Dans la page De forwarding de courrier, sélectionnez Forward **all emails sent to this mailbox**, enter the forwarding address, and choose whether you want to keep a copy of forwarded emails. Si cette option n’est pas disponible, assurez-vous qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer les modifications**.

    **Pour le forwarder vers plusieurs adresses** e-mail, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour le faire. 
    
    1.  Ouvrir **outlook** > **Home** >  **Rules >** Select **Manage Rules & Alerts**
    1. Select **New Rule** > **Select Apply rule on message I receive** located near bottom of list, then click **Next**.
    1. Cliquez **sur Oui** lorsque vous y êtes invité. Cette règle s’applique à chaque message que vous recevez. 
    1. Dans la liste suivante, sélectionnez les actions pour les rediriger vers des personnes ou un **groupe public** et **arrêter le traitement d’autres règles**
    1. Cliquez sur l’expression **soulignée personnes ou groupe public** dans la partie inférieure de la fenêtre.
    1. Tapez **l’adresse de** messagerie à qui envoyer le courrier dans le champ À, puis cliquez sur **OK**.
    1. Sélectionner **Terminer**
    

     Ou bien, dans le Centre d’administration, créez un groupe de [distribution](../setup/create-distribution-lists.md), ajoutez-y les adresses, puis configurer le forwarding pour qu’il pointe vers la DL en suivant les [instructions](add-user-or-contact-to-distribution-list.md) de cet article.

5. Ne supprimez pas le compte de l’utilisateur de messagerie que vous êtes en train de forwarder ou supprimez sa licence !  Si vous le faites, le forwarding du courrier électronique s’arrête.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> **[actifs](https://go.microsoft.com/fwlink/p/?linkid=850628)** .

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez qu’il soit transmis pour ouvrir la page de propriétés.

3. **Développez les paramètres de messagerie**, puis, dans la section **De forwarding de** courrier, sélectionnez **Modifier**.

4. Dans la page De forwarding de courrier électronique, définissez le basculement sur **Sur**, entrez l’adresse de forwarding et choisissez si vous souhaitez conserver une copie des e-mails transmis. Si cette option n’est pas disponible, assurez-vous qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer**.

   **Pour le forwarder vers plusieurs adresses** e-mail, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour le faire. Pour plus d’informations, voir [Utiliser des règles pour envoyer automatiquement des messages](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746).

   Ou bien, dans le Centre d’administration, créez un groupe de [distribution](../setup/create-distribution-lists.md), ajoutez-y les adresses, puis configurer le forwarding pour qu’il pointe vers la DL en suivant les [instructions](add-user-or-contact-to-distribution-list.md) de cet article.

5. Ne supprimez pas le compte de l’utilisateur de messagerie que vous êtes en train de forwarder ou supprimez sa licence ! Si vous le faites, le forwarding du courrier électronique s’arrête.

::: moniker-end

## <a name="related-content"></a>Contenu associé 

[Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md) (article)\
[Envoyer des courriers électroniques à partir d’une adresse différente](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (article)\
[Modifier un nom d’utilisateur et une adresse e-mail](../add-users/change-a-user-name-and-email-address.md) (article)\
[Contrôler le forwarding automatique du courrier externe dans Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding) (article)


