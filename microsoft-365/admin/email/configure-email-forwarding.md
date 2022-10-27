---
title: Configurer le transfert des e-mails
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
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
description: Email transfert vous permet de transférer les messages électroniques envoyés à une boîte aux lettres utilisateur Microsoft 365 vers une autre boîte aux lettres à l’intérieur ou à l’extérieur de votre organisation.
ms.openlocfilehash: 02998623c682f44203199c9cf2738d8b3a3fff37
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68725867"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>Configurer le transfert d’e-mails dans Microsoft 365

En tant qu’administrateur d’une organisation, vous pouvez avoir des exigences de l’entreprise pour configurer le transfert de courrier électronique pour la boîte aux lettres d’un utilisateur. Email transfert vous permet de transférer les messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers la boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de votre organisation.

> [!IMPORTANT]
> Vous pouvez utiliser des stratégies de filtre de courrier indésirable sortant pour contrôler le transfert automatique vers des destinataires externes. Pour plus d’informations, consultez [Contrôler le transfert automatique d’e-mails externes dans Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="configure-email-forwarding"></a>Configurer le transfert des e-mails

Avant de configurer le transfert d’e-mails, notez les points suivants :

- Autoriser l’envoi automatique de messages à des personnes sur le domaine distant. Pour plus d’informations, consultez [Gérer les domaines distants](/exchange/mail-flow-best-practices/remote-domains/manage-remote-domains) .

- Une fois que vous avez configuré le transfert des e-mails, seuls les **nouveaux** e-mails envoyés à la boîte aux lettres  *à partir de*  sont transférés.

- Email transfert nécessite que le compte *from* dispose d’une licence. Si vous configurez le transfert de courrier électronique parce que l’utilisateur a quitté votre organisation, une autre option consiste à [convertir sa boîte aux lettres en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md). De cette façon, plusieurs personnes peuvent y accéder. Toutefois, une boîte aux lettres partagée ne peut pas dépasser 50 Go.

Vous devez être administrateur Exchange ou Administrateur général dans Microsoft 365 pour effectuer ces étapes. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> **[utilisateurs actifs](https://go.microsoft.com/fwlink/p/?linkid=834822)** .

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez transférer l’e-mail, puis ouvrez la page de propriétés.

3. Sous l’onglet **Courrier** , sélectionnez **Gérer le transfert de courrier**.

4. Dans la page de transfert des e-mails, sélectionnez **Transférer tous les e-mails envoyés à cette boîte aux lettres**, entrez l’adresse de transfert et indiquez si vous souhaitez conserver une copie des e-mails transférés. Si vous ne voyez pas cette option, vérifiez qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer les modifications**.

    **Pour transférer vers plusieurs adresses de messagerie**, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour la transférer aux adresses. 
    
    1.  Ouvrir les **règles** **d’accueil** >**outlook** > > sélectionner **Gérer les règles & alertes**  
    1. Sélectionnez **Nouvelle règle** > **Sélectionnez Appliquer la règle sur le message que je reçois** en bas de la liste, puis cliquez sur **Suivant**.
    1. Cliquez sur **Oui** lorsque vous y êtes invité Cette règle sera appliquée à chaque message que vous recevez. 
    1. Dans la liste suivante, sélectionnez les actions **qui le redirigent vers des personnes ou un groupe public** et **arrêtez le traitement d’autres règles**
    1. Cliquez sur l’expression soulignée **personnes ou groupe public** dans la partie inférieure de la fenêtre.
    1. Tapez **l’adresse e-mail** à laquelle transférer le courrier dans le champ À, puis cliquez sur **OK**.
    1. Sélectionner **Terminer**
    

     Ou, dans le centre d’administration, [créez un groupe de distribution](../setup/create-distribution-lists.md), [ajoutez-y les adresses](add-user-or-contact-to-distribution-list.md), puis configurez le transfert pour pointer vers la DL en suivant les instructions de cet article.

5. Ne supprimez pas le compte de l’utilisateur qui est l’adresse e-mail que vous transférez ou ne supprimez pas sa licence !  Si c’est le cas, le transfert des e-mails s’arrête.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> **[utilisateurs actifs](https://go.microsoft.com/fwlink/p/?linkid=850628)** .

2. Sélectionnez le nom de l’utilisateur dont vous souhaitez transférer l’e-mail pour ouvrir la page de propriétés.

3. Développez **Paramètres de** messagerie, puis, dans la section **Email transfert**, sélectionnez **Modifier**.

4. Dans la page de transfert d’e-mail, définissez le bouton bascule **sur Activé**, entrez l’adresse de transfert et choisissez si vous souhaitez conserver une copie des e-mails transférés. Si vous ne voyez pas cette option, vérifiez qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer**.

   **Pour transférer vers plusieurs adresses de messagerie**, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour la transférer aux adresses. Pour plus d’informations, consultez [Utiliser des règles pour transférer automatiquement des messages](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746).

   Ou, dans le centre d’administration, [créez un groupe de distribution](../setup/create-distribution-lists.md), [ajoutez-y les adresses](add-user-or-contact-to-distribution-list.md), puis configurez le transfert pour pointer vers la DL en suivant les instructions de cet article.

5. Ne supprimez pas le compte de l’utilisateur qui est l’adresse e-mail que vous transférez ou ne supprimez pas sa licence ! Si c’est le cas, le transfert des e-mails s’arrête.

::: moniker-end

## <a name="related-content"></a>Contenu associé 

[Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md) (article)\
[Envoyer un e-mail à partir d’une autre adresse](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (article)\
[Modifier un nom d’utilisateur et une adresse e-mail](../add-users/change-a-user-name-and-email-address.md) (article)\
[Contrôler le transfert automatique d’e-mails externes dans Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding) (article)


