---
title: Ajouter un autre alias de courrier pour un utilisateur
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'Découvrez comment vous pouvez avoir plusieurs adresses de messagerie, appelée alias de messagerie, associées à votre compte Microsoft 365 pour les entreprises. '
ms.openlocfilehash: 3c97640f4bb16876ec028a1af2b361a21a0decab
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126404"
---
# <a name="add-another-email-alias-for-a-user"></a>Ajouter un autre alias de courrier pour un utilisateur

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).

::: moniker-end
  
Cet article est réservé aux administrateurs Microsoft 365 qui ont des abonnements pour les entreprises. Il ne s'adresse pas aux particuliers.
  
Une adresse de messagerie principale dans Microsoft 365 est généralement l’adresse de messagerie attribuée à un utilisateur lors de la création de son compte. Lorsque l'utilisateur envoie du courrier à une autre personne, son adresse de courrier principale est celle qui apparaît généralement dans le champ  *De*  dans les applications de courrier. Ils peuvent également avoir plusieurs adresses de messagerie associées à leur compte Microsoft 365 pour les entreprises. Les adresses supplémentaires sont appelées alias. 
  
Par exemple, supposons que Son adresse de messagerie soit jenna@contosoco.com, mais qu’elle souhaite également recevoir des messages électroniques sur jen@contosoco.com car certaines personnes lui font référence par ce nom. Vous pouvez créer des alias pour elle afin que les deux adresses de messagerie se placent dans la boîte de réception de Celle-là.
<br><br>  
  
Vous pouvez créer jusqu'à 400 alias par utilisateur. Vous ne devez pas acquérir de licence supplémentaire et cela n'occasionne aucun frais.
  
> [!Tip]
> Si vous souhaitez que plusieurs personnes gèrent les messages électroniques envoyés à une seule adresse de messagerie, comme info@NodPublishers.com ou sales@NodPublishers.com, créez une boîte aux lettres partagée. Pour plus d’informations, voir [Créer une boîte aux lettres partagée.](create-a-shared-mailbox.md)
  
## <a name="add-email-aliases-to-a-user"></a>Ajouter des alias de courrier à un utilisateur
<a name="AddEmailPreview"> </a>

Vous devez avoir [des autorisations d’administrateur](../add-users/about-admin-roles.md) pour le faire. 

  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Dans la page **Utilisateurs** actifs, sélectionnez l’utilisateur > **gérer les alias de messagerie.** Vous ne verrez pas cette option si la personne n’a pas de licence qui lui est attribuée. 
    
3. Sélectionnez **+ Ajoutez un alias** et entrez un nouvel alias pour l’utilisateur.   
    
    > [!Important] 
    > Si vous obtenez le message d’erreur « Impossible de trouver un paramètre qui correspond au nom du paramètre **« EmailAddresses**», cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
    
  
    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, voir [Ajouter un domaine à Microsoft 365.](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) 
  
     
5. Lorsque vous avez terminé, sélectionnez **Enregistrer les modifications.**
    
6. Patientez 24 heures pour que les nouveaux alias se remplissent dans Microsoft 365.
    
    L’utilisateur aura désormais une adresse principale et un alias. Par exemple, tous les messages envoyés à l’adresse principale d’Eliza Eliza@NodPublishers.com et son alias, Sales@NodPublishers.com, seront acheminés vers la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *De*  est son alias de messagerie principal.** Par exemple, supposons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 
    
::: moniker-end

::: moniker range="o365-germany"
    
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>. 
    
    
2. Dans la page **Utilisateurs actifs**, sélectionnez le nom de la personne à modifier.

3. En de côté **du nom d’utilisateur/des alias de messagerie,** **sélectionnez Modifier.**

    > [!Important] 
    > Si le message d’erreur « Un paramètre qui correspond au nom de paramètre «**EmailAddresses**» s’ajoute, cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.

4. Dans la zone de texte sous **Alias,** tapez la première partie du nouvel alias de messagerie. Si vous avez ajouté votre domaine à Microsoft 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante. Puis sélectionnez **Ajouter**.

    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, voir [Ajouter un domaine à Microsoft 365.](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) 

5. Lorsque vous avez terminé, sélectionnez **Enregistrer**.

6. Patientez 24 heures pour que les nouveaux alias se remplissent dans Microsoft 365. 
    
    L’utilisateur aura désormais une adresse principale et un alias. Par exemple, tous les messages envoyés à l’adresse principale d’Eliza Eliza@NodPublishers.com et son alias, Sales@NodPublishers.com, seront acheminés vers la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *De*  est son alias de messagerie principal.** Par exemple, supposons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

    
2. Dans la page **Utilisateurs actifs**, sélectionnez le nom de la personne à modifier.

3. En de côté **du nom d’utilisateur/des alias de messagerie,** **sélectionnez Modifier.**

    > [!Important] 
    > Si le message d’erreur « Un paramètre qui correspond au nom de paramètre «**EmailAddresses**» s’ajoute, cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.

4. Dans la zone de texte sous **Alias,** tapez la première partie du nouvel alias de messagerie. Si vous avez ajouté votre domaine à Microsoft 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante. Puis sélectionnez **Ajouter**.

    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, voir [Ajouter un domaine à Microsoft 365.](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) 

5. Lorsque vous avez terminé, sélectionnez **Enregistrer**.

6. Patientez 24 heures pour que les nouveaux alias se remplissent dans Microsoft 365. 
    
    L’utilisateur aura désormais une adresse principale et un alias. Par exemple, tous les messages envoyés à l’adresse principale d’Eliza Eliza@NodPublishers.com et son alias, Sales@NodPublishers.com, seront acheminés vers la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *De*  est son alias de messagerie principal.** Par exemple, supposons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 

::: moniker-end


## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Avez-vous reçu « Un paramètre indessable qui correspond au nom de paramètre EmailAddresses » ?


Si vous recevez le message d’erreur « Impossible de trouver un paramètre qui correspond au nom de paramètre **EmailAddresses**», cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Avez-vous acheté votre abonnement auprès de GoDaddy ou d'un autre partenaire ?


Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal.
  
## <a name="related-articles"></a>Articles connexes

[Envoyer des courriers à partir d'une adresse différente](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e)

[Modifier un nom d'utilisateur et une adresse de courrier](../add-users/change-a-user-name-and-email-address.md)
  

