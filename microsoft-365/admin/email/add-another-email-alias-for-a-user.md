---
title: Ajouter un autre alias de courrier pour un utilisateur
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
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'Découvrez comment vous pouvez avoir plusieurs adresses e-mail, appelées alias de messagerie, associées à votre compte Microsoft 365 pour les entreprises. '
ms.openlocfilehash: 9c7d8c8b028ad196601af0c62a99aa16c9d5a382
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718177"
---
# <a name="add-another-email-alias-for-a-microsoft-365-business-subscription-user"></a>Ajouter un autre alias de messagerie pour un utilisateur d’abonnement Microsoft 365 Entreprise
  
Cet article est destiné aux administrateurs Microsoft 365 qui ont des abonnements professionnels. Il ne s'adresse pas aux particuliers.
  
Une adresse e-mail principale dans Microsoft 365 est généralement l’adresse e-mail attribuée à un utilisateur lors de la création de son compte. Lorsque l'utilisateur envoie du courrier à une autre personne, son adresse de courrier principale est celle qui apparaît généralement dans le champ  *De*  dans les applications de courrier. Ils peuvent également avoir plusieurs adresses e-mail associées à leur compte Microsoft 365 pour les entreprises. Les adresses supplémentaires sont appelées alias. 
  
Par exemple, supposons que Jenna a l’adresse e-mail jenna@contosoco.com, mais qu’elle souhaite également recevoir un e-mail à jen@contosoco.com parce que certaines personnes lui font référence par ce nom. Vous pouvez créer des alias pour elle afin que les deux adresses e-mail soient envoyées à la boîte de réception de Jenna.
  
Vous pouvez créer jusqu'à 400 alias par utilisateur. Vous ne devez pas acquérir de licence supplémentaire et cela n'occasionne aucun frais.
  
> [!Tip]
> Si vous souhaitez que plusieurs personnes gèrent les e-mails envoyés à une seule adresse e-mail comme info@NodPublishers.com ou sales@NodPublishers.com, créez une boîte aux lettres partagée. Pour plus d’informations, consultez [Créer une boîte aux lettres partagée](create-a-shared-mailbox.md).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.
  
## <a name="add-email-aliases-to-a-user"></a>Ajouter des alias de courrier à un utilisateur

Vous devez disposer des droits Administration globaux pour ajouter des alias de messagerie à un utilisateur.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Dans la page **Utilisateurs actifs** , sélectionnez l’utilisateur > **Gérer le nom d’utilisateur et l’e-mail**. Vous ne verrez pas cette option si la personne n’a pas de licence qui lui est attribuée. 
    
3. Sélectionnez **+ Ajouter un alias** et entrez un nouvel alias pour l’utilisateur.   
    
    > [!Important] 
    > Si vous recevez le message d’erreur « **Impossible de trouver un paramètre qui correspond au nom du paramètre ' EmailAddresses** », cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre locataire, ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
    
  
    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 


   > [!IMPORTANT]
   >  Si vous recevez le message d’erreur **Cet utilisateur est synchronisé avec votre annuaire Active Directory local. Certains détails peuvent être modifiés uniquement via votre active directory local**. Cela signifie que Active Directory fait autorité pour les attributs sur les utilisateurs synchronisés, vous devez modifier les attributs dans votre Active Directory local.
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, consultez [Ajouter un domaine à Microsoft 365](../setup/add-domain.md). 
  
     
5. Lorsque vous avez terminé, choisissez **Enregistrer les modifications**.
    
6. Attendez 24 heures que les nouveaux alias soient renseignés dans Microsoft 365.
    
    L’utilisateur dispose désormais d’une adresse principale et d’un alias. Par exemple, tous les courriers envoyés à l’adresse principale d’Eliza Hoffman, Eliza@NodPublishers.com, et son alias, Sales@NodPublishers.com, seront envoyés à la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *De* dépend de son client Outlook. Outlook sur le web utiliserez l’alias auquel l’e-mail a été reçu (nous appellerons cela le principe du ping-pong). Le bureau Outlook utilise son alias de messagerie principal.** Par exemple, supposons qu’un message soit envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Quand Eliza répond au message à l’aide du bureau Outlook, son adresse e-mail principale apparaît comme Eliza@NodPublishers.com, et non Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Avez-vous obtenu « Impossible de trouver un paramètre qui correspond au nom du paramètre EmailAddresses » ?

Si vous recevez le message d’erreur « **Impossible de trouver un paramètre qui correspond au nom de paramètre EmailAddresses** », cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre locataire, ou votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Avez-vous acheté votre abonnement auprès de GoDaddy ou d'un autre partenaire ?


Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal.

## <a name="sending-email-from-the-proxy-address-easily"></a>Envoi facile d’e-mails à partir de l’adresse proxy

Une nouvelle fonctionnalité est en cours de déploiement en juillet 2021 qui permet aux utilisateurs d’envoyer facilement à partir de leurs alias lorsqu’ils utilisent Outlook sur le web. Lorsque la fonctionnalité est déployée dans une location où l’administrateur du locataire utilise l’applet `Set-OrganizationConfig -SendFromAliasEnabled $true` de commande , les utilisateurs de la location ont accès à une liste de cases à cocher où chaque entrée correspond à un alias dans leurs paramètres Outlook. La sélection d’un alias s’affiche dans la liste déroulante De du formulaire Composer.
  
## <a name="related-content"></a>Contenu associé

[Envoyer un e-mail à partir d’une autre adresse](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (article)

[Modifier un nom d’utilisateur et une adresse e-mail](../add-users/change-a-user-name-and-email-address.md) (article)

[Configurer le transfert des e-mails dans Microsoft 365](configure-email-forwarding.md) (article)
