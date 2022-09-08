---
title: Bookings avec moi
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ROBOTS: NO INDEX, NO FOLLOW
description: Utilisez Bookings avec moi pour permettre à d’autres personnes de planifier des réunions avec vous dans Outlook.
ms.openlocfilehash: 5de348a45ca7e38d6ee20cdcce4137247c63bfd7
ms.sourcegitcommit: 02a9c7f915d3a795a373b62dbdee2925966703f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2022
ms.locfileid: "67623556"
---
# <a name="bookings-with-me"></a>Bookings avec moi

**Bookings with me** in Outlook est une page de planification personnelle basée sur le web qui s’intègre aux informations de disponibilité de votre calendrier Outlook. Les réservations avec moi permettent aux gens de planifier une réunion ou un rendez-vous avec vous. Vous pouvez créer des types de réunion personnalisés à partager avec d’autres personnes afin qu’elles puissent facilement planifier du temps avec vous en fonction de votre disponibilité et de vos préférences. Vous recevez une confirmation par e-mail et les participants peuvent mettre à jour ou annuler des réunions planifiées avec vous à partir de votre page Bookings avec moi.

> [!NOTE]
> Bookings avec moi est disponible dans le monde entier en préversion. Les fonctionnalités incluses dans la préversion peuvent ne pas être complètes et peuvent subir des modifications avant d’être disponibles dans la version publique.

Bookings avec moi a deux vues différentes :

- **Mode Organisateur** Page de réservation personnelle dans laquelle vous pouvez créer des types de réunion que d’autres personnes peuvent réserver avec vous. Les types de réunion personnalisés vous permettent de personnaliser le moment où vous souhaitez vous rencontrer et la façon dont ce type de réunion est partagé avec d’autres personnes. Vous contrôlez si chaque type de réunion est public pour votre page de planification ou est privé et n’est accessible qu’à un groupe de personnes sélectionné. Vous pouvez également choisir d’ajouter une réunion Teams à toutes les réunions réservées via votre page Bookings with me. Vous pouvez accéder à votre page Bookings avec moi via Outlook sur le web. Une fois votre page configurée et publiée, vous pouvez la partager avec d’autres personnes. Par exemple, vous pouvez l’ajouter à votre signature Outlook.

- **Vue des participants** Lorsque vous partagez votre page Bookings avec moi avec d’autres personnes, l’affichage des participants s’affiche. Si l’organisateur a partagé son lien de page Bookings avec moi avec vous, vous pourrez voir tous ses types de réunions publiques. Si l’organisateur a partagé un lien de réunion, vous ne pourrez afficher cette réunion que.
  - Les réunions publiques peuvent être consultées et planifiées par toute personne disposant de votre lien de page Bookings with me. Vous contrôlez avec qui vous partagez ce lien. Tous les types de réunions publiques seront visibles par toute personne disposant de votre lien de page Bookings avec moi.
  - Les réunions privées peuvent uniquement être consultées par les personnes qui ont le lien pour ce type de réunion. La différence entre les réunions publiques et les réunions privées est que les réunions privées peuvent avoir des liens différents et que les liens expirent après 90 jours. Vous pouvez également définir des liaisons privées pour qu’ils expirent après une réservation unique. Lorsque vous accédez à la vue de planification d’une réunion privée, seul ce type de réunion est visible.

## <a name="when-to-use-bookings-with-me"></a>Quand utiliser Bookings avec moi

Bookings avec moi est une solution idéale pour les entreprises, les petites entreprises et les utilisateurs de l’éducation pour planifier des réunions 1:1 avec les personnes extérieures et internes à leur organisation. Voici quelques exemples de la façon dont vous pouvez utiliser Bookings avec moi.

- Planifier des entretiens avec des candidats externes
- Configurer des réunions client et client
- Planifier le support technique
- Configurer les heures de bureau
- Configurer des heures de mentorat
- Réunions 1:1 avec des rapports directs
- Déjeuner et pauses-café

## <a name="before-you-begin"></a>Avant de commencer

Les réservations avec moi peuvent être activées ou désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous activez Bookings pour les utilisateurs, ils peuvent créer une page Bookings, partager leur page avec d’autres personnes et autoriser d’autres personnes à réserver du temps avec eux. Cet article s’applique aux propriétaires et administrateurs qui gèrent Bookings avec moi pour leur organisation.

Les réservations avec moi sont disponibles dans les abonnements suivants :

- Office 365 : A3, A5, E1, E3, E5, F1, F3
- Microsoft 365 : A3, A5, E1, E3, E5, F1, F3, Business Basic, Business Standard, Business Premium

Les réservations avec moi sont activées par défaut pour les utilisateurs disposant de ces abonnements.

Bookings avec moi a besoin de **l’application Microsoft Bookings (plan de service)** affectée aux utilisateurs pour qu’ils puissent accéder à Bookings. Ce plan de service peut être activé/désactivé par les administrateurs de locataires. Par conséquent, si **Microsoft Bookings** ne leur est pas attribué, l’accès Bookings sera refusé aux utilisateurs même s’ils se trouvent dans l’une des références SKU répertoriées précédemment.

Pour plus d’informations, consultez [l’élément de feuille de route Microsoft 365 bookings with me](https://go.microsoft.com/fwlink/?linkid=328648).

### <a name="prerequisites-for-using-bookings-with-me"></a>Conditions préalables à l’utilisation de Bookings avec moi

1. Bookings avec moi et Bookings partagent le même modèle de licence. Toutefois, Bookings n’a pas besoin d’être activé pour l’organisation à l’aide des paramètres de locataire pour que les utilisateurs puissent accéder à Bookings avec moi. L’application Bookings doit être activée pour que les utilisateurs aient accès à Bookings avec moi.

   Pour activer Bookings avec moi sans accès à Bookings, bloquez l’accès à Microsoft Bookings à l’aide de la [commande PowerShell de stratégie de boîte aux lettres OWA](/powershell/module/exchange/set-owamailboxpolicy) ou suivez les instructions ici : [Activez ou désactivez Microsoft Bookings](turn-bookings-on-or-off.md).

2. Le partage anonyme FreeBusy du calendrier doit être activé pour utiliser Bookings avec moi. Cela permet à la page Bookings d’avoir accès aux informations de disponibilité dans votre calendrier Outlook. Utilisez PowerShell pour vérifier l’état.

   ```PowerShell
     Get-SharingPolicy -Identity "Default Sharing Policy" | fl Domains 
   ```

    Anonymous:SharingPolicyAction doit être l’un des domaines de la réponse. La valeur SharingPolicyAction peut être CalendarSharingFreeBusySimple, CalendarSharingFreeBusyDetail ou CalendarSharingFreeBusyReviewer (valeur par défaut).

   Pour activer le partage anonyme, utilisez la commande suivante.

   ```PowerShell
     Set-SharingPolicy "Default Sharing Policy" -Domains @{Add="Anonymous:CalendarSharingFreeBusySimple"}
   ```
  
  Pour plus d’informations, consultez [Set-SharingPolicy](/powershell/module/exchange/set-sharingpolicy).

## <a name="turn-bookings-with-me-on-or-off"></a>Activer ou désactiver Bookings avec moi

Les réservations avec moi peuvent être activées ou désactivées pour l’ensemble de votre organisation ou utilisateurs spécifiques. Lorsque Bookings avec moi est activé, les utilisateurs peuvent créer une page Bookings avec moi et partager des liens avec d’autres personnes à l’intérieur ou à l’extérieur de votre organisation.

### <a name="turn-bookings-with-me-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver Bookings avec moi pour votre organisation à l’aide de PowerShell

Vous devez exécuter les commandes suivantes à l’aide de Exchange Online PowerShell. Pour plus d’informations sur l’exécution Exchange Online applets de commande, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour activer ou désactiver Bookings avec moi pour votre organisation à l’aide de l’applet de commande PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez les commandes suivantes.

Utilisez les commandes **Get-OrganizationConfig** et **Set-OrganizationConfig** pour connaître l’état et activer ou désactiver Bookings pour votre organisation.

> [!NOTE]
> Il faut généralement environ 30 à 60 minutes pour que Set-OrganizationConfig commandes prennent effet pour vos utilisateurs.

1. Vérifiez l’accès au contrôle EWS en exécutant la commande suivante.

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsEnabled
   ```

    Si la commande retourne « EwsEnabled : **$true** », passez à l’étape 2.

    Si la commande retourne « EwsEnabled: » (vide est la valeur par défaut), activez, mais uniquement si nécessaire pour bloquer « Bookings with », puis passez à l’étape 2.
    Sinon, les valeurs par défaut d’EwsEnabled sont suffisantes pour laisser « Bookings with me » activé, aucune autre modification n’est nécessaire.

   ```PowerShell
   Set-OrganizationConfig -EwsEnabled: $true
   ```

2. Vérifiez votre EwsApplicationAccessPolicy en exécutant la commande suivante :

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans **EwsAllowList** sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour votre organisation, **supprimez MicrosoftOWSPersonalBookings**, le cas échéant, de **EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi pour votre organisation, ajoutez **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.

    - Pour désactiver Bookings avec moi pour votre organisation, ajoutez **MicrosoftOWSPersonalBookings en** exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi en cas de blocage, **supprimez MicrosoftOWSPersonalBookings en** exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur de **EwsApplicationAccessPolicy** est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour votre organisation, **définissez la stratégie EnforceBlockList** et ajoutez **MicrosoftOWSPersonalBookings** à la liste rouge en exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsApplicationAccessPolicy EnforceBlockList -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```
   
  > [!NOTE]
  > Le paramètre EwsApplicationAccessPolicy définit les applications autres que Entourage, Outlook et Outlook pour Mac peuvent accéder à EWS.

### <a name="turn-bookings-with-me-off-or-on-for-individual-users"></a>Activer ou désactiver Bookings pour les utilisateurs individuels

Utilisez les commandes **Get-CASMailbox** et **Set-CASMailbox** pour vérifier l’état de l’utilisateur et activer ou désactiver Bookings pour les utilisateurs individuels de votre organisation.

1. Vérifiez l’accès au contrôle EWS de la personne en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsEnabled
   ```

    **R**. Si la commande retourne « **EwsEnabled : $true** », passez à l’étape 2.

2. Vérifiez **l’EwsApplicationAccessPolicy** de la personne en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans EwsAllowList sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, s’il est présent dans **EwsAllowList** , en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Activez Bookings avec moi pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.  

    - Pour désactiver Bookings avec moi pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EnforceBlockList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, s’il est présent dans EnforceBlockList, en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur de EwsApplicationAccessPolicy est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour cet utilisateur, **définissez la stratégie EnforceBlockList** et ajoutez **MicrosoftOWSPersonalBookings** à EWSBlockList en exécutant la commande suivante :

    ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsApplicationAccessPolicy EnforceBlockList -EWSBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

## <a name="frequently-asked-questions"></a>Forum aux questions

### <a name="what-is-the-difference-between-bookings-and-bookings-with-me"></a>Quelle est la différence entre Bookings et Bookings avec moi ?

Bookings avec moi s’intègre à votre calendrier Outlook et ne peut être utilisé que pour les réunions 1:1. Les réservations avec moi sont destinées à planifier des heures de réunion avec des utilisateurs individuels. Bookings est destiné à gérer la planification d’un groupe de personnes.

En outre, Bookings avec moi ne créera pas de boîte aux lettres pour chaque page Bookings avec moi.

### <a name="why-is-bookings-with-me-in-preview"></a>Pourquoi Bookings avec moi est-il en préversion ?

Bookings avec moi est en préversion pour tous les utilisateurs d’entreprise dans le monde entier. Nous recueillons des commentaires et apportons des améliorations pendant qu’ils sont intégrés aux expériences de planification dans Bookings et Outlook.  

### <a name="who-can-access-my-public-bookings-page"></a>Qui peut accéder à ma page Bookings publique ?

Les types de réunions publiques sont accessibles par toute personne disposant de votre page Bookings avec moi. Vous décidez avec qui vous partagez votre page Bookings avec moi.

### <a name="what-is-the-difference-between-public-and-private-meeting-types"></a>Quelle est la différence entre les types de réunions publiques et privées ?

Les types de réunions peuvent être publics ou privés. Les types de réunions publiques sont accessibles à toute personne avec laquelle vous partagez le lien de votre page Bookings. Les types de réunions privées sont uniquement disponibles pour les personnes avec lesquelles vous partagez le type de réunion privé individuel.  

Les types de réunions privées peuvent également générer des liens à usage unique. Les liens à usage unique expirent après leur première réservation.

### <a name="do-people-need-to-have-a-microsoft-account-or-bookings-license-to-schedule-time-with-me"></a>Les utilisateurs doivent-ils disposer d’un compte Microsoft ou d’une licence Bookings pour planifier de l’heure avec moi ?

Non. Tout le monde peut planifier l’heure avec vous à l’aide de votre page Bookings avec moi, même s’ils n’ont pas de compte Microsoft. Vous avez besoin d’une licence Bookings pour créer une page Bookings avec moi.

## <a name="privacy"></a>Confidentialité

### <a name="where-is-bookings-with-me-data-stored"></a>Où sont stockées les données Bookings avec moi ?

Bookings avec moi est une fonctionnalité d’Outlook optimisée par Bookings. Toutes les données sont stockées dans la plateforme Microsoft 365 et dans Exchange. Bookings avec moi suit les stratégies de stockage de données définies par Microsoft, qui sont les mêmes stratégies que toutes les applications Office. Toutes les données client (y compris les informations fournies par les participants lors de la réservation) sont capturées dans Bookings et stockées dans Exchange. Pour plus d’informations, consultez [Privacy: It’s all about you](https://www.microsoft.com/en-us/trust-center/privacy).
