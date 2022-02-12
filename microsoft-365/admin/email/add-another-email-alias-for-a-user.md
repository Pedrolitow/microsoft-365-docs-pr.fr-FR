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
ms.localizationpriority: medium
ms.collection:
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
description: 'Découvrez comment vous pouvez avoir plusieurs adresses de messagerie, appelées alias de messagerie, associées à votre compte Microsoft 365 entreprise. '
ms.openlocfilehash: f5adc9e48110aa1e2a2e6c87f2c2f7847986d741
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62766367"
---
# <a name="add-another-email-alias-for-a-user"></a>Ajouter un autre alias de courrier pour un utilisateur
  
Cet article s’Microsoft 365 administrateurs qui ont des abonnements d’entreprise. Il ne s'adresse pas aux particuliers.
  
Une adresse de messagerie principale dans Microsoft 365 est généralement l’adresse de messagerie attribuée à un utilisateur lors de la création de son compte. Lorsque l'utilisateur envoie du courrier à une autre personne, son adresse de courrier principale est celle qui apparaît généralement dans le champ  *De*  dans les applications de courrier. Ils peuvent également avoir plusieurs adresses de messagerie associées à leur compte Microsoft 365 entreprise. Les adresses supplémentaires sont appelées alias. 
  
Par exemple, supposons que Son adresse de messagerie soit jenna@contosoco.com, mais qu’elle souhaite également recevoir des messages électroniques sur jen@contosoco.com car certaines personnes lui font référence par ce nom. Vous pouvez créer des alias pour elle afin que les deux adresses de messagerie se placent dans la boîte de réception de Celle-là.
  
Vous pouvez créer jusqu'à 400 alias par utilisateur. Vous ne devez pas acquérir de licence supplémentaire et cela n'occasionne aucun frais.
  
> [!Tip]
> Si vous souhaitez que plusieurs personnes gèrent les messages électroniques envoyés à une seule adresse de messagerie telle que info@NodPublishers.com ou sales@NodPublishers.com, créez une boîte aux lettres partagée. Pour plus d’informations, voir [Créer une boîte aux lettres partagée](create-a-shared-mailbox.md).

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de collaborer avec [un spécialiste microsoft des petites entreprises](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Business Assist, vous et vos employés accédez 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.
  
## <a name="add-email-aliases-to-a-user"></a>Ajouter des alias de courrier à un utilisateur

Vous devez avoir des droits d’administrateur global pour ajouter des alias de messagerie à un utilisateur.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Dans la page **Utilisateurs** actifs, sélectionnez l’utilisateur > **gérer le nom d’utilisateur et le courrier électronique**. Vous ne verrez pas cette option si la personne n’a pas de licence qui lui est attribuée. 
    
3. **Sélectionnez + Ajoutez un alias** et entrez un nouvel alias pour l’utilisateur.   
    
    > [!Important] 
    > Si vous obtenez le message d’erreur « Impossible de trouver un paramètre qui correspond au nom du paramètre **« EmailAddresses** », cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
    
  
    > [!IMPORTANT]
    > Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal. 


   > [!IMPORTANT]
   >  Si vous obtenez le message d’erreur **, cet utilisateur est synchronisé avec votre annuaire Active Directory local. Certains détails peuvent être modifiés** uniquement par le biais de votre active directory local, cela signifie qu’Active Directory fait autorité pour les attributs sur les utilisateurs synchronisés, vous devez modifier les attributs dans votre Active Directory local.
  
    > [!TIP]
    > L'alias de courrier doit se terminer par un domaine figurant dans la liste déroulante. Pour ajouter un autre nom de domaine à la liste, voir [Ajouter un domaine à Microsoft 365](../setup/add-domain.md). 
  
     
5. Lorsque vous avez terminé, sélectionnez **Enregistrer les modifications**.
    
6. Patientez 24 heures pour que les nouveaux alias se rempliront tout au long Microsoft 365.
    
    L’utilisateur aura désormais une adresse principale et un alias. Par exemple, tous les messages envoyés à l’adresse principale d’Eliza Eliza@NodPublishers.com et à son alias, Sales@NodPublishers.com, seront acheminés vers la boîte de réception d’Eliza.
    
  
7. **Lorsque l’utilisateur répond, l’adresse *de* l’utilisateur dépend de Outlook client. Outlook sur le web utilisera l’alias auquel l’e-mail a été reçu (nous appellerons cela le principe ping-domaine). Outlook bureau utilise son alias de messagerie principal.** Par exemple, supposons qu’un message est envoyé à Sales@NodPublishers.com et qu’il arrive dans la boîte de réception d’Eliza. Lorsque Eliza répond au message à l’aide Outlook bureau, son adresse de messagerie principale s’affiche sous la Eliza@NodPublishers.com, et non Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Avez-vous reçu « Un paramètre indessable qui correspond au nom de paramètre EmailAddresses » ?

Si vous obtenez le message d’erreur « Impossible de trouver un paramètre qui correspond au nom de paramètre **EmailAddresses** », cela signifie qu’il faut un peu plus de temps pour terminer la configuration de votre client ou de votre domaine personnalisé si vous en avez récemment ajouté un. Le processus de configuration peut prendre jusqu'à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le support technique qui se chargera d'effectuer une synchronisation complète pour vous.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Avez-vous acheté votre abonnement auprès de GoDaddy ou d'un autre partenaire ?


Si vous achetez votre abonnement auprès de GoDaddy ou d'un autre partenaire, vous devez accéder à la console de gestion de GoDaddy ou du partenaire pour définir le nouvel alias comme alias principal.

## <a name="sending-email-from-the-proxy-address-easily"></a>Envoi aisément d’e-mails à partir de l’adresse proxy

Une nouvelle fonctionnalité est en cours de déploiement en juillet 2021 qui permet aux utilisateurs d’envoyer facilement des messages à partir de leurs alias lors de l’utilisation Outlook sur le web. Lorsque la fonctionnalité est mise en place dans une location où l’administrateur client utilise la cmdlet, les utilisateurs `Set-OrganizationConfig -SendFromAliasEnabled $true` au sein de la location ont accès à une liste de case à cocher où chaque entrée correspond à un alias dans leurs paramètres Outlook. La sélection d’un alias l’affiche dans ladown From du formulaire Composer.
  
## <a name="related-content"></a>Contenu associé

[Envoyer des messages électroniques à partir d’une adresse différente](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (article)

[Modifier un nom d’utilisateur et une adresse e-mail](../add-users/change-a-user-name-and-email-address.md) (article)

[Configurer le transfert des e-mails dans Microsoft 365](configure-email-forwarding.md) (article)
