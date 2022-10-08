---
title: Accorder des autorisations de boîte aux lettres à un autre utilisateur – Aide de l’administrateur
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1dbcf12f-a9de-4d1d-b0b3-a227f8a736d8
description: Accorder à un utilisateur de Microsoft 365 le droit d'accéder à la boîte aux lettres d'un autre utilisateur, ce qui permet à l'utilisateur de lire et d'envoyer des e-mails à partir de la boîte aux lettres de l'autre utilisateur.
ms.openlocfilehash: 6370e147ad63b7400627ea222f98f94bdd2638c8
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203418"
---
# <a name="give-mailbox-permissions-to-another-microsoft-365-user---admin-help"></a>Accorder des autorisations de boîte aux lettres à un autre utilisateur Microsoft 365 – Aide de l’administrateur

As the admin, you may have company requirements to allow some users access to another user's mailbox. For example, you may want to enable an assistant to send or read email from their manager's mailbox, or one of your user's the ability to send email on behalf of another user. This topic shows you how to accomplish this.
  
Si vous cherchez des informations concernant la création et la gestion de boîtes aux lettres partagées, consultez l’article [Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.
    
## <a name="looking-to-set-up-mailbox-permissions"></a>Vous cherchez à configurer des autorisations de boîte aux lettres ?

Mailbox permissions allow you to give read/write access to a mailbox to another user. The articles below might give you the help you need to set up and use this feature:
  
 **Configuration des autorisations :**
  
pour configurer des autorisations, la première étape consiste à décider des actions que vous voulez autoriser l’autre utilisateur à pouvoir effectuer dans la boîte aux lettres donnée. Vous pouvez autoriser un utilisateur à lire des courriers dans la boîte aux lettres, à envoyer des courriers de la part d’un autre utilisateur et à envoyer des courriers comme s’ils étaient envoyés à partir de cette boîte aux lettres. Consultez les articles suivants pour configurer chaque type d’autorisation :
  
- [Lire du courrier à partir de la boîte aux lettres d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#read-email-in-another-users-mailbox)
    
- [Envoyer du courrier à partir de la boîte aux lettres d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#send-email-from-another-users-mailbox)

- [Envoyer un e-mail de la part d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#send-email-on-behalf-of-another-user)
    
 **Propagation des modifications :**
  
lorsque vous avez défini les autorisations, la propagation des modifications dans le système et leur application peut prendre jusqu’à 60 minutes.
  
 **Comment utiliser une boîte aux lettres une fois les autorisations configurées :**
  
Lorsque vous avez reçu l’accès à une boîte aux lettres, plusieurs méthodes s’offrent à vous pour y accéder. Pour obtenir de l’aide sur cette fonction, consultez cet article : [Accéder à la boîte aux lettres d’une autre personne](https://support.microsoft.com/office/A909AD30-E413-40B5-A487-0EA70B763081).

> [!NOTE]
> Les autorisations peuvent être configurées uniquement dans le locataire actuel de l’organisation. Il n’est pas possible de configurer des autorisations de boîte aux lettres pour les utilisateurs de locataire.
  
## <a name="send-email-from-another-users-mailbox"></a>Envoyer du courrier à partir de la boîte aux lettres d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  
    
2. Sélectionnez le nom de l’utilisateur (auquel vous envisagez d’accorder une autorisation d’envoi) pour ouvrir le volet de ses propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.

4. À côté de **Envoyer en tant que**, sélectionnez **Modifier**. 

5. Sélectionnez **Ajouter des autorisations**, puis choisissez le nom de la personne à laquelle vous voulez que cet utilisateur puisse Envoyer en tant que. 
    
6. Sélectionnez **Ajouter**.
 
::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer en tant que**, sélectionnez **Modifier**. 

4. Sélectionnez **Ajouter des autorisations**, puis choisissez le nom de la personne à laquelle vous voulez que cet utilisateur puisse Envoyer en tant que. 
    
5. Sélectionnez **Ajouter**.

::: moniker-end
  
## <a name="read-email-in-another-users-mailbox"></a>Lire du courrier dans la boîte aux lettres d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  
    
2. Sélectionnez le nom de l’utilisateur (dont vous voulez autoriser la lecture de la boîte aux lettres) pour ouvrir son volet de propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.
    
4. À côté de **Lire et gérer**, sélectionnez **Modifier**. 
    
5. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à lire du courrier à partir de cette boîte aux lettres.

6. Sélectionnez **Ajouter**.


> [!NOTE]
> Les autorisations **Lecture** et **Gestion** sont appelées autorisations **Accès complet** lorsqu’elles sont accordées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Cette autorisation permet à la boîte aux lettres de l’utilisateur affecté de lire et de gérer les e-mails dans la boîte aux lettres utilisateur bénéficiant de l’autorisation. L’autorisation Accès total n’accorde pas les autorisations **Envoyer en tant que** ou **Envoyer de la part de**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 
  
2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.
    
3. À côté de **Lire et gérer**, sélectionnez **Modifier**. 
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à lire du courrier à partir de cette boîte aux lettres.

5. Sélectionnez **Ajouter**.

::: moniker-end


## <a name="send-email-on-behalf-of-another-user"></a>Envoyez du courrier de la part d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez le nom de l’utilisateur (auquel vous envisagez d’accorder une autorisation **Envoyer de la part de**) pour ouvrir le volet de ses propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.
    
4. À côté de **Envoyer de la part de**, sélectionnez **Modifier**.

5. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à envoyer du courrier pour le compte de cette boîte aux lettres.

6. Sélectionnez **Ajouter**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer de la part de**, sélectionnez **Modifier**.
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à envoyer du courrier pour le compte de cette boîte aux lettres.

5. Sélectionnez **Ajouter**.

::: moniker-end

> [!NOTE]
> Les autorisations **Envoyer en tant que** et **Envoyer de la part de** ne fonctionnent pas dans le client de bureau Outlook avec le paramètre *HiddenFromAddressListsEnabled* sur la boîte aux lettres définie sur **True**, car elles nécessitent que la boîte aux lettres soit visible dans Outlook via la liste d’adresses globale.

## <a name="related-content"></a>Contenu associé
  
[Gérer les éléments du courrier et du calendrier d'une autre personne](https://support.microsoft.com/office/afb79d6b-2967-43b9-a944-a6b953190af5) (article)\   
[Envoyer un e-mail d'une autre personne ou d'un groupe](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) (article)\
[Modifier un nom d'utilisateur et une adresse électronique ](../add-users/change-a-user-name-and-email-address.md)(vidéo)

