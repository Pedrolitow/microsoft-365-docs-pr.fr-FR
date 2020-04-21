---
title: Configurer le transfert des e-mails
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: Configurez le transfert du courrier vers un ou plusieurs comptes de messagerie à l’aide d’Office 365.
ms.openlocfilehash: 5807649fa43d094fd8f05cf63e2905d7cdb6dd7d
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43628914"
---
# <a name="configure-email-forwarding"></a>Configurer le transfert des e-mails
  
En tant qu’administrateur d’une organisation, vous pouvez avoir besoin d’une société pour configurer le transfert du courrier électronique pour la boîte aux lettres d’un utilisateur. Le transfert du courrier vous permet de transférer des messages électroniques envoyés à la boîte aux lettres d’un utilisateur vers une boîte aux lettres d’un autre utilisateur à l’intérieur ou à l’extérieur de votre organisation.

  
## <a name="configure-email-forwarding"></a>Configurer le transfert des e-mails

 Avant de configurer le transfert du courrier, notez les points suivants : 

- Une fois que vous avez configuré le transfert du courrier, seuls les **nouveaux** messages électroniques envoyés à la boîte aux lettres *de à partir de* seront fowarded. 
    
- Le transfert du courrier exige que le compte *de à partir* de dispose d’une licence. Si vous configurez le transfert du courrier, car l’utilisateur a quitté votre organisation, une autre solution consiste à [convertir sa boîte aux lettres en boîte aux lettres partagée](convert-user-mailbox-to-shared-mailbox.md). De cette manière, plusieurs personnes peuvent y accéder. Toutefois, une boîte aux lettres partagée ne peut pas dépasser 50 Go. 
    
Pour effectuer ces étapes, vous devez être administrateur Exchange ou administrateur général dans Microsoft 365. Pour plus d’informations, reportez-vous à la rubrique [à propos des rôles d’administrateur](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Sélectionnez le nom de l’utilisateur dont vous souhaitez transférer le courrier électronique pour ouvrir la page des propriétés. 
 
3. Dans l’onglet **messagerie** , sélectionnez **gérer le transfert du courrier**. 
  
4. Sur la page transfert du courrier, sélectionnez **transférer tous les messages électroniques envoyés à cette boîte aux lettres**, entrez l’adresse de transfert et indiquez si vous souhaitez conserver une copie des messages transférés. Si cette option n’est pas visible, vérifiez qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer les modifications**.
    
    **Pour transférer des adresses de messagerie à plusieurs**, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour transférer les adresses. Pour en savoir plus, consultez la rubrique [utiliser des règles pour transférer automatiquement des messages](https://support.office.com/article/use-rules-to-automatically-forward-messages-45aa9664-4911-4f96-9663-ece42816d746). 
    
     Ou, dans le centre d’administration, [créez un groupe de distribution](../setup/create-distribution-lists.md), [Ajoutez-y les adresses](add-user-or-contact-to-distribution-list.md), puis configurez le transfert pour qu’il pointe vers la LD en suivant les instructions indiquées dans cet article.
    
5. Ne supprimez pas le compte de l’utilisateur auquel est envoyé le courrier électronique que vous transférez ou supprimez sa licence.  Si vous le faites, le transfert du courrier s’arrêtera. 

::: moniker-end

::: moniker range="o365-germany"
    
 1.   Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>. 
    
2. Sélectionnez le nom de l’utilisateur dont vous souhaitez transférer le courrier électronique pour ouvrir la page des propriétés. 

3. Développez **paramètres de messagerie**, puis, dans la section **transfert de courrier** , sélectionnez **modifier**.

4. Sur la page transfert du courrier, définissez le bouton bascule sur **activé**, entrez l’adresse de transfert et indiquez si vous souhaitez conserver une copie des messages envoyés. Si cette option n’est pas visible, vérifiez qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer**.
    
    **Pour transférer des adresses de messagerie à plusieurs**, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour transférer les adresses. Pour en savoir plus, consultez la rubrique [utiliser des règles pour transférer automatiquement des messages](https://support.office.com/article/use-rules-to-automatically-forward-messages-45aa9664-4911-4f96-9663-ece42816d746). 
    
     Ou, dans le centre d’administration, [créez un groupe de distribution](../setup/create-distribution-lists.md), [Ajoutez-y les adresses](add-user-or-contact-to-distribution-list.md), puis configurez le transfert pour qu’il pointe vers la LD en suivant les instructions indiquées dans cet article.
    
5. Ne supprimez pas le compte de l’utilisateur auquel est envoyé le courrier électronique que vous transférez ou supprimez sa licence.  Si vous le faites, le transfert du courrier s’arrêtera.    

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 
    
2. Sélectionnez le nom de l’utilisateur dont vous souhaitez transférer le courrier électronique pour ouvrir la page des propriétés. 

3. Développez **paramètres de messagerie**, puis, dans la section **transfert de courrier** , sélectionnez **modifier**.

4. Sur la page transfert du courrier, définissez le bouton bascule sur **activé**, entrez l’adresse de transfert et indiquez si vous souhaitez conserver une copie des messages envoyés. Si cette option n’est pas visible, vérifiez qu’une licence est attribuée au compte d’utilisateur. Sélectionnez **Enregistrer**.
    
    **Pour transférer des adresses de messagerie à plusieurs**, vous pouvez demander à l’utilisateur de configurer une règle dans Outlook pour transférer les adresses. Pour en savoir plus, consultez la rubrique [utiliser des règles pour transférer automatiquement des messages](https://support.office.com/article/use-rules-to-automatically-forward-messages-45aa9664-4911-4f96-9663-ece42816d746). 
    
     Ou, dans le centre d’administration, [créez un groupe de distribution](../setup/create-distribution-lists.md), [Ajoutez-y les adresses](add-user-or-contact-to-distribution-list.md), puis configurez le transfert pour qu’il pointe vers la LD en suivant les instructions indiquées dans cet article.
    
5. Ne supprimez pas le compte de l’utilisateur auquel est envoyé le courrier électronique que vous transférez ou supprimez sa licence.  Si vous le faites, le transfert du courrier s’arrêtera. 

::: moniker-end 
