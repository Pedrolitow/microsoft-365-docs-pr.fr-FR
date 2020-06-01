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
- okr_smb
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'Découvrez comment vous pouvez avoir plusieurs adresses de messagerie, appelées alias de messagerie, associées à votre compte Microsoft 365 pour les entreprises. '
ms.openlocfilehash: bab4ace6d497bac8892a29c76b6f2d05c4fa018f
ms.sourcegitcommit: a005395165db8896f4109674443b5e5e9209861d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2020
ms.locfileid: "44432324"
---
# <a name="add-another-email-alias-for-a-user"></a>Ajouter un autre alias de courrier pour un utilisateur

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end
  
Cet article est destiné aux administrateurs de Microsoft 365 qui ont des abonnements d’entreprise. Il ne s'adresse pas aux particuliers.
  
Une adresse de messagerie principale dans Microsoft 365 correspond généralement à l’adresse de messagerie à laquelle un utilisateur a été affecté lors de la création de son compte. Lorsque l'utilisateur envoie du courrier à une autre personne, son adresse de courrier principale est celle qui apparaît généralement dans le champ  *De*  dans les applications de courrier. Ils peuvent également avoir plus d’une adresse de messagerie associée à leur compte Microsoft 365 pour les entreprises. Les adresses supplémentaires sont appelées alias. 
  
Par exemple, supposons que Jenna a l’adresse de messagerie jenna@contosoco.com, mais qu’il souhaite également recevoir des courriers électroniques sur jen@contosoco.com car certaines personnes y font référence par ce nom. Vous pouvez créer des alias pour lui afin que les deux adresses de messagerie soient placées dans la boîte de réception de Jenna.
<br><br>  
  
Vous pouvez créer jusqu'à 400 alias par utilisateur. Vous ne devez pas acquérir de licence supplémentaire et cela n'occasionne aucun frais.
  
> [!Tip]
> Si vous souhaitez que plusieurs personnes gèrent les courriers électroniques envoyés à une adresse de messagerie unique telle que info@NodPublishers.com ou sales@NodPublishers.com, créez une boîte aux lettres partagée. Pour en savoir plus, consultez [la rubrique créer une boîte aux lettres partagée](create-a-shared-mailbox.md).
  
## <a name="add-email-aliases-to-a-user"></a>Ajouter des alias de courrier à un utilisateur
<a name="AddEmailPreview"> </a>

Pour ce faire, vous devez disposer des [autorisations d’administrateur](../add-users/about-admin-roles.md) . 

  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sur la page **utilisateurs actifs** , sélectionnez l’utilisateur > **gérer les alias de messagerie**. Cette option ne s’affiche pas si la personne ne dispose pas d’une licence. 
    
3. Sélectionnez **+ Ajouter un alias** et entrez un nouvel alias pour l’utilisateur.   
    
    > [!Important] 
    > Si vous obtenez le message d’erreur «**Impossible de trouver un paramètre correspondant au nom de paramètre «EmailAddresses**», cela signifie qu’il prend un peu plus de temps pour terminer la configuration de votre client ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
    
  
    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, reportez-vous à la rubrique [Ajouter un domaine à Office 365](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain). 
  
     
5. Lorsque vous avez fini, choisissez **enregistrer les modifications**.
    
6. Patientez 24 heures pour que les nouveaux alias soient renseignés dans Office 365.
    
    L’utilisateur dispose désormais d’une adresse principale et d’un alias. Par exemple, tous les messages envoyés à l’adresse principale de Eliza Hoffman, Eliza@NodPublishers.com, et son alias, Sales@NodPublishers.com, sont redirigés vers la boîte de réception de Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *de provenance* correspond à son alias de messagerie principal.** Par exemple, imaginons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 
    
::: moniker-end

::: moniker range="o365-germany"
    
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>. 
    
    
2. Dans la page **Utilisateurs actifs**, sélectionnez le nom de la personne à modifier.

3. En regard de **nom d’utilisateur/alias de messagerie**, sélectionnez **modifier**.

    > [!Important] 
    > Si vous obtenez le message d’erreur «**Impossible de trouver un paramètre correspondant au nom de paramètre «EmailAddresses**», cela signifie qu’il prend un peu plus de temps pour terminer la configuration de votre client ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.

4. Dans la zone de texte sous **alias**, tapez la première partie du nouvel alias de messagerie. Si vous avez ajouté votre domaine à Office 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante. Puis sélectionnez **Ajouter**.

    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, reportez-vous à la rubrique [Ajouter un domaine à Office 365](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain). 

5. Lorsque vous avez fini, sélectionnez **Enregistrer**.

6. Patientez 24 heures pour que les nouveaux alias soient renseignés dans Office 365. 
    
    L’utilisateur dispose désormais d’une adresse principale et d’un alias. Par exemple, tous les messages envoyés à l’adresse principale de Eliza Hoffman, Eliza@NodPublishers.com, et son alias, Sales@NodPublishers.com, sont redirigés vers la boîte de réception de Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *de provenance* correspond à son alias de messagerie principal.** Par exemple, imaginons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

    
2. Dans la page **Utilisateurs actifs**, sélectionnez le nom de la personne à modifier.

3. En regard de **nom d’utilisateur/alias de messagerie**, sélectionnez **modifier**.

    > [!Important] 
    > Si vous obtenez le message d’erreur «**Impossible de trouver un paramètre correspondant au nom de paramètre «EmailAddresses**», cela signifie qu’il prend un peu plus de temps pour terminer la configuration de votre client ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.

4. Dans la zone de texte sous **alias**, tapez la première partie du nouvel alias de messagerie. Si vous avez ajouté votre domaine à Office 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante. Puis sélectionnez **Ajouter**.

    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, reportez-vous à la rubrique [Ajouter un domaine à Office 365](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain). 

5. Lorsque vous avez fini, sélectionnez **Enregistrer**.

6. Patientez 24 heures pour que les nouveaux alias soient renseignés dans Office 365. 
    
    L’utilisateur dispose désormais d’une adresse principale et d’un alias. Par exemple, tous les messages envoyés à l’adresse principale de Eliza Hoffman, Eliza@NodPublishers.com, et son alias, Sales@NodPublishers.com, sont redirigés vers la boîte de réception de Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *de provenance* correspond à son alias de messagerie principal.** Par exemple, imaginons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au courrier, son adresse de courrier principale s'affiche en tant qu'expéditeur, au lieu de Sales@NodPublishers.com. 

::: moniker-end


## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Est-ce que vous obtenez « impossible de trouver un paramètre correspondant au nom de paramètre EmailAddresses » ?


Si vous obtenez le message d’erreur «**Impossible de trouver un paramètre correspondant au nom de paramètre EmailAddresses**» cela signifie qu’il prend un peu plus de temps pour terminer la configuration de votre client ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Avez-vous acheté votre abonnement auprès de GoDaddy ou d'un autre partenaire ?


Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal.
  
## <a name="related-articles"></a>Articles connexes

[Envoyer des courriers à partir d'une adresse différente](https://support.office.com/article/ccba89cb-141c-4a36-8c56-6d16a8556d2e.aspx)

[Modifier un nom d'utilisateur et une adresse de courrier](../add-users/change-a-user-name-and-email-address.md)
  

