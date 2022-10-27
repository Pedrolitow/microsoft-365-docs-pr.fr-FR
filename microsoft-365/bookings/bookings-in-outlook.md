---
title: Bookings avec moi
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
ROBOTS: NO INDEX, NO FOLLOW
description: Utilisez Bookings avec moi pour permettre à d’autres personnes de planifier des réunions avec vous dans Outlook.
ms.openlocfilehash: 6b35d422a12e346df30551e303a0426ea6b200c0
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730334"
---
# <a name="bookings-with-me"></a>Bookings avec moi

**Bookings with me dans** Outlook est une page web de planification personnelle qui s’intègre aux informations de disponibilité de votre calendrier Outlook. Bookings with me permet de planifier une réunion ou un rendez-vous avec vous. Vous pouvez créer des types de réunion personnalisés à partager avec d’autres personnes afin qu’elles puissent facilement planifier l’heure avec vous en fonction de votre disponibilité et de vos préférences. Vous recevez tous les deux une confirmation par e-mail et les participants peuvent mettre à jour ou annuler les réunions planifiées avec vous à partir de votre page Bookings with me.

Bookings avec moi a deux vues différentes :

- [Réservations avec moi : configuration et partage](https://support.microsoft.com/office/bookings-with-me-setup-and-sharing-ad2e28c4-4abd-45c7-9439-27a789d254a2) Une page de réservation personnelle dans laquelle vous pouvez créer des types de réunion que d’autres personnes peuvent réserver avec vous. Les types de réunion personnalisés vous permettent de personnaliser le moment où vous souhaitez vous réunir et comment ce type de réunion est partagé avec d’autres personnes. Vous contrôlez si chaque type de réunion est public pour votre page de planification ou est privé et n’est accessible qu’à un groupe de personnes sélectionné. Vous pouvez également choisir d’ajouter une réunion Teams à toutes les réunions réservées via votre page Réservations avec moi. Vous pouvez accéder à votre page Bookings with me via Outlook sur le web. Après avoir configuré votre page et l’avoir publiée, vous pouvez la partager avec d’autres personnes. Par exemple, vous pouvez l’ajouter à votre signature Outlook.

- [Vue des participants](https://support.microsoft.com/office/select-a-meeting-time-in-bookings-with-me-8f3bbe5b-4bc6-4073-bf61-57383c00b43a) Lorsque vous partagez votre page Bookings avec moi avec d’autres personnes, ils voient l’affichage du participant. Si l’organisateur a partagé son lien de page Bookings avec moi avec vous, vous serez en mesure de voir tous ses types de réunions publiques. Si l’organisateur a partagé un lien de réunion, vous pouvez uniquement afficher cette réunion.
  - Les réunions publiques peuvent être consultées et planifiées par toute personne qui a votre lien de page Bookings avec moi. Vous contrôlez les personnes avec qui vous partagez ce lien. Tous les types de réunions publiques seront visibles par toute personne ayant votre lien de page Bookings avec moi.
  - Les réunions privées ne peuvent être consultées que par les personnes disposant du lien pour ce type de réunion. La différence entre les réunions publiques et les réunions privées est que les réunions privées peuvent avoir des liens différents et les liens expirent après 90 jours. Vous pouvez également définir des liaisons privées pour qu’elles expirent après une réservation unique. Lors de l’accès à l’affichage planification d’une réunion privée, seul ce type de réunion est visible.

## <a name="when-to-use-bookings-with-me"></a>Quand utiliser Bookings avec moi

Bookings with me est une solution idéale pour les entreprises, les petites entreprises et les utilisateurs de l’éducation pour planifier des réunions 1:1 avec ceux qui sont à l’extérieur et à l’intérieur de leur organisation. Voici quelques exemples d’utilisation de Bookings avec moi.

- Planifier des entrevues avec des candidats externes
- Configurer des réunions client et client
- Planifier le support technique
- Configurer les heures de bureau
- Configurer les heures de mentorat
- Réunions 1:1 avec rapports directs
- Pauses déjeuner et café

## <a name="before-you-begin"></a>Avant de commencer

Les réservations avec moi peuvent être activées ou désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous activez Bookings pour les utilisateurs, ils peuvent créer une page Bookings, partager leur page avec d’autres personnes et permettre à d’autres personnes de réserver du temps avec eux. Cet article est destiné aux propriétaires et administrateurs qui gèrent Bookings avec moi pour leurs organisations.

Bookings with me est disponible dans les abonnements suivants :

- Office 365 : A3, A5, E1, E3, E5, F1, F3
- Microsoft 365 : A3, A5, E1, E3, E5, F1, F3, Business Basic, Business Standard, Business Premium

Bookings with me est activé par défaut pour les utilisateurs disposant de ces abonnements.

Bookings avec moi a besoin de **l’application Microsoft Bookings (plan de service)** attribuée aux utilisateurs pour qu’ils puissent accéder à Bookings. Ce plan de service peut être activé/désactivé par les administrateurs de locataire. Par conséquent, si **Microsoft Bookings** ne leur est pas attribué, l’accès à Bookings sera refusé aux utilisateurs, même s’ils se trouvent dans l’une des références SKU répertoriées précédemment.

Pour plus d’informations, consultez [l’article Feuille de route Microsoft 365 bookings with me](https://go.microsoft.com/fwlink/?linkid=328648).

### <a name="prerequisites-for-using-bookings-with-me"></a>Conditions préalables à l’utilisation de Bookings avec moi

1. Bookings avec moi et Bookings partagent le même modèle de licence. Toutefois, Il n’est pas obligé d’activer Bookings pour que l’organisation utilise les paramètres de locataire pour que les utilisateurs puissent accéder à Bookings avec moi. L’application Bookings doit être activée pour que les utilisateurs aient accès à Bookings avec moi.

   Pour activer Bookings avec moi sans accès à Bookings, bloquez l’accès à Microsoft Bookings à l’aide de la [commande PowerShell de stratégie de boîte aux lettres OWA](/powershell/module/exchange/set-owamailboxpolicy) ou suivez les instructions ici : [Activer ou désactiver Microsoft Bookings](turn-bookings-on-or-off.md).

2. Le partage de calendrier GratuitBusy Anonyme doit être activé pour utiliser Bookings avec moi. Cela permet à la page Bookings d’accéder aux informations de disponibilité dans votre calendrier Outlook. Utilisez PowerShell pour vérifier l’état.

   ```PowerShell
     Get-SharingPolicy -Identity "Default Sharing Policy" | fl Domains 
   ```

    Anonymous:SharingPolicyAction doit être l’un des domaines dans la réponse. La valeur SharingPolicyAction peut être CalendarSharingFreeBusySimple, CalendarSharingFreeBusyDetail ou CalendarSharingFreeBusyReviewer (par défaut).

   Pour activer le partage anonyme, utilisez la commande suivante.

   ```PowerShell
     Set-SharingPolicy "Default Sharing Policy" -Domains @{Add="Anonymous:CalendarSharingFreeBusySimple"}
   ```
3.  Pour les boîtes aux lettres auxquelles une stratégie de partage personnalisée est affectée, la stratégie doit avoir Anonymous:SharingPolicyActio comme l’un des domaines.

   ```Powershell:
      get-mailbox adam@contoso.com | Format-List SharingPolicy
   ```

   Si la commande retourne :

   `SharingPolicy        : "contoso.onmicrosoft.com\Default Sharing (CONTOSO)"`

   Vous devez mettre à jour la stratégie avec l’un des domaines requis :

   ```Powershell
   Set-SharingPolicy "Default Sharing (CONTOSO)" -Domains @{Add="Anonymous:CalendarSharingFreeBusySimple"}
   ```

Pour plus d’informations, consultez [Set-SharingPolicy](/powershell/module/exchange/set-sharingpolicy).

## <a name="turn-bookings-with-me-on-or-off"></a>Activer ou désactiver Bookings avec moi

Les réservations avec moi peuvent être activées ou désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque Bookings with me est activé, les utilisateurs peuvent créer une page Bookings with me et partager des liens avec d’autres personnes à l’intérieur ou à l’extérieur de votre organisation.

### <a name="turn-bookings-with-me-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver Bookings with me pour votre organisation à l’aide de PowerShell

Vous devez exécuter les commandes suivantes à l’aide de Exchange Online PowerShell. Pour plus d’informations sur l’exécution des applets de commande Exchange Online, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour activer ou désactiver Bookings avec moi pour votre organisation à l’aide de l’applet de commande PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez les commandes suivantes.

Utilisez les commandes **Get-OrganizationConfig** et **Set-OrganizationConfig** pour connaître l’état et activer ou désactiver Bookings avec moi pour votre organisation.

> [!NOTE]
> Il faut généralement environ 30 à 60 minutes pour que les commandes Set-OrganizationConfig prennent effet pour vos utilisateurs.

1. Vérifiez le contrôle d’accès EWS en exécutant la commande suivante.

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsEnabled
   ```

    Si la commande retourne « EwsEnabled: **$true** », passez à l’étape 2.

    Si la commande retourne « EwsEnabled: » (vide est la valeur par défaut), activez, mais uniquement si vous avez besoin de bloquer « Bookings with », puis passez à l’étape 2.
    Sinon, les valeurs par défaut de EwsEnabled sont suffisantes pour laisser « Bookings with me » activée, aucune autre modification n’est nécessaire.

   ```PowerShell
   Set-OrganizationConfig -EwsEnabled: $true
   ```

2. Vérifiez votre EwsApplicationAccessPolicy en exécutant la commande suivante :

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans **EwsAllowList** sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour votre organisation, supprimez **MicrosoftOWSPersonalBookings**, le cas échéant, **d’EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi pour votre organisation, vous devez définir **EwsApplicationAccessPolicy** sur **EnforceAllowList** et ajouter **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsApplicationAccessPolicy:EnforceAllowList
   ```
   
   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.

    - Pour désactiver Bookings with me pour votre organisation, ajoutez **MicrosoftOWSPersonalBookings** en exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi en cas de blocage, supprimez **MicrosoftOWSPersonalBookings** en exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur de **EwsApplicationAccessPolicy** est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings with me pour votre organisation, définissez la stratégie **EnforceBlockList** et ajoutez **MicrosoftOWSPersonalBookings** à la liste de blocages en exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsApplicationAccessPolicy EnforceBlockList -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```
   
  > [!NOTE]
  > Le paramètre EwsApplicationAccessPolicy définit les applications autres qu’Entourage, Outlook et Outlook pour Mac qui peuvent accéder à EWS.

### <a name="turn-bookings-with-me-off-or-on-for-individual-users"></a>Désactiver ou activer Bookings avec moi pour les utilisateurs individuels

Utilisez les commandes **Get-CASMailbox** et **Set-CASMailbox** pour vérifier l’état de l’utilisateur et activer ou désactiver Bookings avec moi pour les utilisateurs individuels de votre organisation.

1. Vérifiez l’accès au contrôle EWS de l’individu en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsEnabled
   ```

    **R**. Si la commande retourne « **EwsEnabled: $true** », passez à l’étape 2.

2. Vérifiez la stratégie **EwsApplicationAccessPolicy** de l’individu en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans EwsAllowList sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings avec moi pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, le cas échéant, **d’EwsAllowList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Activez Bookings avec moi pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.  

    - Pour désactiver Bookings with me pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EnforceBlockList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings avec moi pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, le cas échéant, d’EnforceBlockList en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur de EwsApplicationAccessPolicy est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings with me pour cet utilisateur, définissez la stratégie **EnforceBlockList** et ajoutez **MicrosoftOWSPersonalBookings** à EWSBlockList en exécutant la commande suivante :

    ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsApplicationAccessPolicy EnforceBlockList -EWSBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

### <a name="create-bookings-with-me"></a>Créer bookings avec moi

1. Ouvrez [Outlook sur le web](https://go.microsoft.com/fwlink/p/?LinkID=402333).
2. Sélectionnez **Calendrier**.
3. Sélectionnez le lien **Créer une page de réservations** qui s’affiche dans votre calendrier pour créer Bookings avec moi.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="what-is-the-difference-between-bookings-and-bookings-with-me"></a>Quelle est la différence entre Bookings et Bookings avec moi ?

Bookings avec moi s’intègre à votre calendrier Outlook et ne peut être utilisé que pour les réunions 1:1. Bookings with me est destiné à planifier des heures de réunion avec des utilisateurs individuels. Bookings est destiné à gérer la planification d’un groupe de personnes.

En outre, Bookings avec moi ne crée pas de boîte aux lettres pour chaque page Bookings avec moi.

### <a name="why-is-bookings-with-me-in-preview"></a>Pourquoi Bookings est-il avec moi en préversion ?

Bookings with me est disponible en préversion pour tous les utilisateurs d’entreprise du monde entier. Nous collectons des commentaires et apportons des améliorations pendant qu’ils sont intégrés aux expériences de planification dans Bookings et Outlook.  

### <a name="who-can-access-my-public-bookings-page"></a>Qui peut accéder à ma page de réservations publique ?

Les types de réunions publiques sont accessibles à toute personne ayant votre adresse de page Bookings with me. Vous décidez avec qui vous partagez votre adresse de page Bookings avec moi. Pour plus d’informations, consultez [Sélectionner une heure de réunion dans Bookings avec moi](https://support.microsoft.com/office/select-a-meeting-time-in-bookings-with-me-8f3bbe5b-4bc6-4073-bf61-57383c00b43a).

### <a name="what-is-the-difference-between-public-and-private-meeting-types"></a>Quelle est la différence entre les types de réunions publiques et privées ?

Les types de réunion peuvent être publics ou privés. Les types de réunions publiques sont disponibles pour toute personne avec laquelle vous partagez le lien de votre page Bookings. Les types de réunion privée sont disponibles uniquement pour les personnes avec lesquelles vous partagez le type de réunion privée individuel.  

Les types de réunions privées peuvent également générer des liens à usage unique. Les liens à usage unique expirent après leur première réservation. Pour plus d’informations, consultez [Configurer les types de réunion Bookings avec moi](https://support.microsoft.com/office/bookings-with-me-setup-and-sharing-ad2e28c4-4abd-45c7-9439-27a789d254a2).

### <a name="do-people-need-to-have-a-microsoft-account-or-bookings-license-to-schedule-time-with-me"></a>Les utilisateurs doivent-ils disposer d’un compte Microsoft ou d’une licence Bookings pour planifier l’heure avec moi ?

Non. Tout le monde peut planifier du temps avec vous à l’aide de votre page Bookings avec moi, même s’il n’a pas de compte Microsoft. Vous avez besoin d’une licence Bookings pour créer une page Bookings with me.

## <a name="privacy"></a>Confidentialité

### <a name="where-is-bookings-with-me-data-stored"></a>Où sont stockées les données de Bookings avec moi ?

Bookings with me est une fonctionnalité d’Outlook optimisée par Bookings. Toutes les données sont stockées dans la plateforme Microsoft 365 et dans Exchange. Bookings with me suit les stratégies de stockage des données définies par Microsoft, qui sont les mêmes que toutes les applications Office. Toutes les données client (y compris les informations fournies par les participants lors de la réservation) sont capturées dans Bookings et stockées dans Exchange. Pour plus d’informations, consultez [Confidentialité : Tout est à propos de vous](https://www.microsoft.com/en-us/trust-center/privacy).
