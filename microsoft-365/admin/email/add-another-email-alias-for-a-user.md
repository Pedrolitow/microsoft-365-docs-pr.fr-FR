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
description: 'Découvrez comment vous pouvez avoir plus d’une adresse e-mail, appelée alias e-mail, associée à votre Microsoft 365 compte d’entreprise. '
ms.openlocfilehash: ec5bc69a42c5183413f11649b7d7ec6baaf40b01
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572104"
---
# <a name="add-another-email-alias-for-a-user"></a>Ajouter un autre alias de courrier pour un utilisateur
  
Cet article s’adresse Microsoft 365 administrateurs qui ont des abonnements d’entreprise. Il ne s'adresse pas aux particuliers.
  
Une adresse e-mail principale dans Microsoft 365 est généralement l’adresse e-mail qu’un utilisateur a été affecté lors de la création de son compte. Lorsque l'utilisateur envoie du courrier à une autre personne, son adresse de courrier principale est celle qui apparaît généralement dans le champ  *De*  dans les applications de courrier. Ils peuvent également avoir plus d’une adresse e-mail associée à leur Microsoft 365 compte d’entreprise. Les adresses supplémentaires sont appelées alias. 
  
Par exemple, disons que Jenna a l’adresse e-mail jenna@contosoco.com, mais elle veut aussi recevoir des e-mails à jen@contosoco.com parce que certaines personnes se réfèrent à elle par ce nom. Vous pouvez créer des alias pour elle afin que les deux adresses e-mail vont à la boîte de réception de Jenna.
  
Vous pouvez créer jusqu'à 400 alias par utilisateur. Vous ne devez pas acquérir de licence supplémentaire et cela n'occasionne aucun frais.
  
> [!Tip]
> Si vous souhaitez que plusieurs personnes gèrent les e-mails envoyés à une seule adresse e-mail info@NodPublishers.com ou sales@NodPublishers.com, créez une boîte aux lettres partagée. Pour en savoir plus, consultez [Créer une boîte aux lettres partagée](create-a-shared-mailbox.md).
  
## <a name="add-email-aliases-to-a-user"></a>Ajouter des alias de courrier à un utilisateur

Vous devez avoir des [autorisations administratives](../add-users/about-admin-roles.md) pour ce faire. 

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sur la page **Utilisateurs actifs,** sélectionnez l’utilisateur pour gérer > **nom d’utilisateur et l’e-mail**. Vous ne verrez pas cette option si la personne n’a pas de licence qui lui est attribuée. 
    
3. Sélectionnez **+ Ajoutez un alias** et entrez un nouvel alias pour l’utilisateur.   
    
    > [!Important] 
    > Si vous obtenez le message d’erreur "**Un paramètre ne peut pas être trouvé qui correspond au nom de paramètre 'EmailAddresses',** cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre locataire, ou votre domaine personnalisé si vous avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
    
  
    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, [voir Ajouter un domaine à Microsoft 365](../setup/add-domain.md). 
  
     
5. Lorsque vous avez terminé, choisissez Enregistrer **les modifications**.
    
6. Attendez 24 heures pour que les nouveaux alias peuplent tout au long de Microsoft 365.
    
    L’utilisateur aura désormais une adresse principale et un alias. Par exemple, tout le courrier envoyé à l’adresse principale d’Eliza Hoffman, Eliza@NodPublishers.com, et son alias, Sales@NodPublishers.com, iront à la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, *l’adresse* From dépend de son Outlook client. Outlook sur le web utilisera l’alias à partir duquel l’e-mail a été reçu (nous appellerons cela le principe du ping-pong). Outlook bureau utilisera son alias e-mail principal.** Par exemple, supposons qu’un message soit envoyé à Sales@NodPublishers.com, et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au message à l’aide Outlook bureau, son adresse e-mail principale apparaîtra comme Eliza@NodPublishers.com, pas Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Avez-vous eu « Un paramètre ne peut pas être trouvé qui correspond au nom de paramètre EmailAddresses »?

Si vous obtenez le message d’erreur "**Un paramètre ne peut pas être trouvé qui correspond au nom de paramètre EmailAddresses**" cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre locataire, ou votre domaine personnalisé si vous avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Avez-vous acheté votre abonnement auprès de GoDaddy ou d'un autre partenaire ?


Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal.

## <a name="sending-email-from-the-proxy-address-easily"></a>Envoi d’e-mail à partir de l’adresse proxy facilement

Une nouvelle fonctionnalité est en cours de déploiement en avril 2021 qui permet aux utilisateurs d’envoyer facilement à partir de leurs alias lors de l’utilisation Outlook sur le web. Lorsque la fonctionnalité est mise en œil dans une location où l’administrateur locataire `Set-OrganizationConfig -SendFromAliasEnabled $true` utilise le cmdlet, les utilisateurs de la location auront accès à une liste de caisses où chaque entrée correspond à un alias dans leurs paramètres de Outlook. La sélection d’un alias le fera apparaître dans le dropdown From sous la forme Composer.
  
## <a name="related-content"></a>Contenu connexe

[Envoyer un e-mail à partir d’une autre](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) adresse (article)

[Modification d’un nom d’utilisateur et d’une adresse e-mail](../add-users/change-a-user-name-and-email-address.md) (article)

[Configurer l’envoi d’e-Microsoft 365 dans](configure-email-forwarding.md) Microsoft 365 (article)
