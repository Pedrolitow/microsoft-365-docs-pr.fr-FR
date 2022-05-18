---
title: Envoyer un e-mail en tant que liste de distribution
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
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a7c98273-067e-4162-b3a1-4ba081796012
description: Envoyez un e-mail en tant que liste de distribution dans Microsoft 365 de sorte que lorsqu’un membre répond à un message, il semble qu’il provienne de la liste de distribution.
ms.openlocfilehash: dd6e1f906481fe1c04bfa7cd275bd108ab558d59
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468457"
---
# <a name="send-microsoft-365-email-as-a-distribution-list"></a>Envoyer Microsoft 365 e-mail en tant que liste de distribution

Dans Microsoft 365, vous pouvez envoyer un e-mail en tant que liste de distribution. Lorsqu’une personne membre de la liste de distribution répond à un message envoyé à la liste de distribution, l’e-mail semble être issu de la liste de distribution, et non de l’utilisateur individuel. Cette rubrique vous montre comment procéder.
  
## <a name="before-you-begin"></a>Avant de commencer

Avant d’effectuer ces étapes, assurez-vous que vous avez été ajouté à une liste de distribution Microsoft 365 et que vous avez reçu l’autorisation Envoyer en tant qu’autorisation sur celle-ci.
  
 **Administrateurs** : assurez-vous d’avoir suivi les étapes de l’ajout [d’un utilisateur ou d’un contact Microsoft 365 à une liste](../email/add-user-or-contact-to-distribution-list.md) et [d’autoriser les membres à envoyer des e-mails en tant que rubriques de groupe Microsoft 365](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md#allow-members-to-send-email-as-a-group), et d’ajouter les personnes appropriées à la liste de distribution.
  
## <a name="outlook-on-the-web"></a>Outlook sur le web

1. Ouvrez Outlook sur le web et accédez à votre boîte de réception. 
    
2. Ouvrez un message qui a été envoyé à la liste de distribution. 
    
3. Sélectionnez **Répondre**. 
    
4. En bas du message, sélectionnez **Plus** \> **d’affichage**.<br/> ![Sélectionnez Plus, puis sélectionnez Afficher à partir de.](../../media/534f13b7-9f15-48ea-8835-ea2ed1863ece.png)
  
5. Cliquez avec le bouton droit sur l’adresse De, par `Ina@weewalter.me` exemple, et **choisissez Supprimer**.<br/> ![Remove the FROM alias.](../../media/9b8d8e8f-dc46-499c-89bd-0a480603bf1f.png)
  
6. Tapez ensuite l’adresse de la liste de distribution, telle que support@contoso.com, puis envoyez le message. La prochaine fois que vous répondez à partir de la liste de distribution, son adresse apparaîtra en tant qu’option dans la liste **De** .<br/>![L’alias de la boîte aux lettres partagée s’affiche.](../../media/f7632a9a-9cab-446c-9e37-23ef50c5b975.png)

## <a name="outlook"></a>Outlook

1. Ouvrez Outlook client de bureau.

2. Composez un nouvel e-mail. Cliquez sur le champ **De** et sélectionnez **Autre adresse e-mail**. Si vous ne voyez pas le champ De, accédez à **Options** et sélectionnez **À partir** de la section Afficher les champs.

3. Sélectionnez l’adresse **de la liste de distribution** dans la liste d’adresses globale.

4. Envoyez l’e-mail.

## <a name="related-content"></a>Contenu connexe

[Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../email/create-edit-or-delete-a-security-group.md) (article)\
[Collaboration par e-mail](../email/email-collaboration.md) (article)\
[Ajouter un utilisateur ou un contact à un groupe de distribution](../email/add-user-or-contact-to-distribution-list.md) (article)