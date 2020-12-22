---
title: Accorder des autorisations de boîte aux lettres à un autre utilisateur – Aide de l’administrateur
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1dbcf12f-a9de-4d1d-b0b3-a227f8a736d8
description: "Découvrez comment accorder le droit à un utilisateur d'accéder à la boîte aux lettres d'un autre utilisateur. Cela permet à l’utilisateur de lire et d’envoyer des messages électroniques à partir de la boîte aux lettres d'un autre utilisateur. "
ms.openlocfilehash: af12cfe3acad9e12ca3983c9fa13f52b72f0a467
ms.sourcegitcommit: 16e018f8b6eef5dad48eabf179691ead3cebe533
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "49725152"
---
# <a name="give-mailbox-permissions-to-another-user---admin-help"></a>Accorder des autorisations de boîte aux lettres à un autre utilisateur – Aide de l’administrateur

En tant qu’administrateur, certaines exigences de votre entreprise vous entraînent à autoriser certains utilisateurs à accéder à la boîte aux lettres d’un autre utilisateur. Par exemple, vous souhaitez peut-être autoriser un assistant à envoyer ou à lire du courrier dans la boîte aux lettres de son responsable ou donner la possibilité à un de vos utilisateurs d’envoyer du courrier de la part d’un autre utilisateur. Cette rubrique vous explique comment procéder pour y parvenir.
  
Si vous cherchez des informations concernant la création et la gestion de boîtes aux lettres partagées, consultez l’article [Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md).
    
## <a name="looking-to-set-up-mailbox-permissions"></a>Vous cherchez à configurer des autorisations de boîte aux lettres ?

Les autorisations de boîte aux lettres vous permettent d’accorder un accès en lecture/écriture à une boîte aux lettres à un utilisateur autre que son propriétaire. L’article qui suit vous fournira les informations dont vous avez besoin pour configurer et utiliser cette fonctionnalité :
  
 **Configuration des autorisations :**
  
pour configurer des autorisations, la première étape consiste à décider des actions que vous voulez autoriser l’autre utilisateur à pouvoir effectuer dans la boîte aux lettres donnée. Vous pouvez autoriser un utilisateur à lire des courriers dans la boîte aux lettres, à envoyer des courriers de la part d’un autre utilisateur et à envoyer des courriers comme s’ils étaient envoyés à partir de cette boîte aux lettres. Consultez les articles suivants pour configurer chaque type d’autorisation :
  
- [Lire du courrier à partir de la boîte aux lettres d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#read-email-in-another-users-mailbox)
    
- [Envoyer du courrier à partir de la boîte aux lettres d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#send-email-from-another-users-mailbox)

- [Envoyer un e-mail de la part d’un autre utilisateur](give-mailbox-permissions-to-another-user.md#send-email-on-behalf-of-another-user)
    
 **Propagation des modifications :**
  
lorsque vous avez défini les autorisations, la propagation des modifications dans le système et leur application peut prendre jusqu’à 60 minutes.
  
 **Comment utiliser une boîte aux lettres une fois les autorisations configurées :**
  
Lorsque vous avez reçu l’accès à une boîte aux lettres, plusieurs méthodes s’offrent à vous pour y accéder. Pour obtenir de l’aide sur cette fonction, consultez cet article : [Accéder à la boîte aux lettres d’une autre personne](https://support.microsoft.com/office/A909AD30-E413-40B5-A487-0EA70B763081).

> [!NOTE]
> Les autorisations peuvent être configurées uniquement dans le locataire actuel de l’organisation. Il n’est pas possible de configurer des autorisations de boîte aux lettres pour les utilisateurs de locataire.
  
## <a name="send-email-from-another-users-mailbox"></a>Envoyer du courrier à partir de la boîte aux lettres d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  
    
2. Sélectionnez le nom de l’utilisateur (auquel vous envisagez d’accorder une autorisation d’envoi) pour ouvrir le volet de ses propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.

4. À côté de **Envoyer en tant que**, sélectionnez **Modifier**. 

5. Sélectionnez **Ajouter des autorisations**, puis choisissez le nom de la personne à laquelle vous voulez que cet utilisateur puisse Envoyer en tant que. 
    
6. Cliquez sur **Enregistrer**.
 
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer en tant que**, sélectionnez **Modifier**. 

4. Sélectionnez **Ajouter des autorisations**, puis choisissez le nom de la personne à laquelle vous voulez que cet utilisateur puisse Envoyer en tant que. 
    
5. Cliquez sur **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer en tant que**, sélectionnez **Modifier**. 

4. Sélectionnez **Ajouter des autorisations**, puis choisissez le nom de la personne à laquelle vous voulez que cet utilisateur puisse Envoyer en tant que. 
    
5. Cliquez sur **Enregistrer**.

::: moniker-end
  
## <a name="read-email-in-another-users-mailbox"></a>Lire du courrier dans la boîte aux lettres d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  
    
2. Sélectionnez le nom de l’utilisateur (dont vous voulez autoriser la lecture de la boîte aux lettres) pour ouvrir son volet de propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.
    
4. À côté de **Lire et gérer**, sélectionnez **Modifier**. 
    
5. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à lire du courrier à partir de cette boîte aux lettres.

6. Cliquez sur **Enregistrer**.


> [!NOTE]
> Les autorisations **Lecture** et **Gestion** sont appelées autorisations **Accès complet** lorsqu’elles sont accordées dans le centre d’administration Exchange. L’autorisation Accès complet n’octroie pas les autorisations **Envoyer en tant que** ou **Envoyer de la part de**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  
  
2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.
    
3. À côté de **Lire et gérer**, sélectionnez **Modifier**. 
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à lire du courrier à partir de cette boîte aux lettres.

5. Cliquez sur **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 
  
2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.
    
3. À côté de **Lire et gérer**, sélectionnez **Modifier**. 
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à lire du courrier à partir de cette boîte aux lettres.

5. Cliquez sur **Enregistrer**.

::: moniker-end


## <a name="send-email-on-behalf-of-another-user"></a>Envoyez du courrier de la part d’un autre utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez le nom de l’utilisateur (auquel vous envisagez d’accorder une autorisation **Envoyer de la part de**) pour ouvrir le volet de ses propriétés.
    
3. Sous l’onglet **Courrier**, sélectionnez **Gérer les autorisations de boîte aux lettres**.
    
4. À côté de **Envoyer de la part de**, sélectionnez **Modifier**.

5. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à envoyer du courrier pour le compte de cette boîte aux lettres.

6. Cliquez sur **Enregistrer**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer de la part de**, sélectionnez **Modifier**.
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à envoyer du courrier pour le compte de cette boîte aux lettres.

5. Cliquez sur **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur souhaité, développez les **Paramètres de courrier**, puis sélectionnez **Modifier** à côté des **Autorisations de boîte aux lettres**.

3. À côté de **Envoyer de la part de**, sélectionnez **Modifier**.
    
4. Sélectionnez **Ajouter des autorisations**, puis entrez le nom de l’utilisateur ou des utilisateurs que vous souhaitez autoriser à envoyer du courrier pour le compte de cette boîte aux lettres.

5. Cliquez sur **Enregistrer**.

::: moniker-end


## <a name="send-and-read-from-outlook-and-outlook-on-the-web-for-business"></a>Envoyer et lire du courrier à partir d’Outlook et d’Outlook sur le web pour les clients professionnels


Vous voulez savoir comment envoyer du courrier à partir de la boîte aux lettres d’un autre utilisateur ? Consultez les rubriques suivantes :
  
- [Gérer les éléments de courrier et de calendrier d’une autre personne](https://support.microsoft.com/office/afb79d6b-2967-43b9-a944-a6b953190af5)
    
- [Envoyer du courrier pour le compte d’une autre personne ou d’un groupe](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)
