---
title: Bookings dans Outlook
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ROBOTS: NO INDEX, NO FOLLOW
description: Utilisez Bookings dans Outlook pour permettre à d’autres personnes de planifier des réunions avec vous dans Outlook.
ms.openlocfilehash: fb74b345a9c1985388ed4754b3f9913a46e5d9de
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363041"
---
# <a name="bookings-in-outlook"></a>Bookings dans Outlook

Bookings dans Outlook est une page de planification personnelle basée sur le web qui s’intègre aux informations de disponibilité de votre calendrier Outlook. Bookings dans Outlook permet aux utilisateurs de planifier une réunion ou un rendez-vous avec vous. Vous pouvez créer des types de réunion personnalisés à partager avec d’autres personnes afin qu’elles puissent facilement planifier du temps avec vous en fonction de votre disponibilité et de vos préférences. Vous recevez une confirmation par e-mail et les participants peuvent mettre à jour ou annuler des réunions planifiées avec vous à partir de votre Bookings dans Outlook page.

> [!NOTE]
> Bookings dans Outlook est disponible uniquement en préversion.

Bookings dans Outlook a deux vues différentes :

- **Mode Organisateur** Page de réservation personnelle dans laquelle vous pouvez créer des types de réunion que d’autres personnes peuvent réserver avec vous. Les types de réunion personnalisés vous permettent de personnaliser le moment où vous souhaitez vous rencontrer et la façon dont ce type de réunion est partagé avec d’autres personnes. Vous contrôlez si chaque type de réunion est public pour votre page de planification ou est privé et n’est accessible qu’à un groupe de personnes sélectionné. Vous pouvez également choisir d’ajouter une réunion Teams à toutes les réunions réservées via votre Bookings dans Outlook page. Vous pouvez accéder à votre Bookings dans Outlook page via Outlook sur le web ou en accédant à [https://outlook.office.com/bookwithme/](https://outlook.office.com/bookwithme/). Une fois votre page configurée et publiée, vous pouvez la partager avec d’autres personnes. Par exemple, vous pouvez l’ajouter à votre signature Outlook.

- **Affichage planification** Lorsque vous partagez vos Bookings dans Outlook page avec d’autres personnes, l’affichage de planification s’affiche. Les réunions affichées dans l’affichage planification varient selon que vous avez partagé le lien vers votre Bookings dans Outlook page avec des réunions publiques ou si vous avez partagé un lien privé pour une réunion individuelle.
    - Les réunions publiques peuvent être affichées et planifiées par toute personne disposant de votre Bookings dans Outlook lien de page. Vous contrôlez avec qui vous partagez ce lien. Tous les types de réunions publiques sont visibles par toute personne disposant de votre Bookings dans Outlook lien de page.
    - Les réunions privées peuvent uniquement être consultées par les personnes qui ont le lien pour ce type de réunion. La différence entre les réunions publiques et les réunions privées est que les réunions privées peuvent avoir des liens différents et que les liens expirent après 90 jours. Vous pouvez également définir des liaisons privées pour qu’ils expirent après une réservation unique. Lorsque vous accédez à la vue de planification d’une réunion privée, seul ce type de réunion est visible.

## <a name="before-you-begin"></a>Avant de commencer

Bookings dans Outlook est disponible dans les abonnements suivants :

- Office 365 : A3, A5, E1, E3, E5, F1, F3
- Microsoft 365 : A3, A5, E1, E3, E5, F1, F3, Business Basic, Business Standard, Business Premium

Bookings dans Outlook est activée par défaut pour les utilisateurs disposant de ces abonnements.

Pour plus d’informations, consultez [l’Bookings dans Outlook Microsoft 365 élément feuille de route](https://go.microsoft.com/fwlink/?linkid=328648).

## <a name="turn-bookings-in-outlook-on-or-off"></a>Activer ou désactiver Bookings dans Outlook  

Bookings dans Outlook peuvent être activées ou désactivées pour l’ensemble de votre organisation ou utilisateurs spécifiques. Lorsque Bookings dans Outlook est activée, les utilisateurs peuvent créer une Bookings dans Outlook page et partager des liens avec d’autres personnes à l’intérieur ou à l’extérieur de votre organisation.

### <a name="turn-bookings-in-outlook-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver Bookings dans Outlook pour votre organisation à l’aide de PowerShell

Vous devez exécuter les commandes suivantes à l’aide de Exchange Online PowerShell. Pour plus d’informations sur l’exécution d’applets de commande Exchange Online, consultez [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour activer ou désactiver Bookings dans Outlook pour votre organisation à l’aide de l’applet de commande PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécuter les commandes suivantes.

Utilisez les commandes **Get-OrganizationConfig** et **Set-OrganizationConfig** pour déterminer l’état et activer ou désactiver Bookings dans Outlook pour votre organisation.

> [!NOTE]
> Il faut généralement environ 30 à 60 minutes pour que Set-OrganizationConfig commandes prennent effet pour vos utilisateurs.

1. Vérifiez l’accès au contrôle EWS en exécutant la commande suivante.

   ```PowerShell
   Get-Organizationconfig | Format-List EwsEnabled
   ```

    Si la commande retourne « EwsEnabled : **$true** », passez à l’étape 2.

    Si la commande retourne « EwsEnabled: » (vide est la valeur par défaut), activez et passez à l’étape 2.

   ```PowerShell
   Set-OrganizationConfig -EwsEnabled: $true
   ```

2. Vérifiez votre EwsApplicationAccessPolicy en exécutant la commande suivante :

   ```PowerShell
   Get-OrganizationConfig | Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans **EwsAllowList** sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings dans Outlook pour votre organisation, supprimez **MicrosoftOWSPersonalBookings**, le cas échéant, **d’EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings dans Outlook pour votre organisation, ajoutez **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :  

   ```PowerShell
   Set-OrganizationConfig -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.

    - Pour désactiver Bookings dans Outlook de votre organisation, ajoutez **MicrosoftOWSPersonalBookings en** exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings dans Outlook en cas de blocage, **supprimez MicrosoftOWSPersonalBookings en** exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur  **deEwsApplicationAccessPolicyis**  est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings dans Outlook pour votre organisation, **définissez la stratégie EnforceBlockList** et ajoutez **MicrosoftOWSPersonalBookings** à la liste rouge en exécutant la commande suivante :

   ```PowerShell
   Set-OrganizationConfig -EwsApplicationAccessPolicy EnforceBlockList -EwsBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

### <a name="turn-bookings-in-outlook-off-or-on-for-individual-users"></a>Désactiver ou activer Bookings dans Outlook pour les utilisateurs individuels

Utilisez les commandes **Get-CASMailbox** et **Set-CASMailbox** pour vérifier l’état de l’utilisateur et activer ou désactiver Bookings dans Outlook pour les utilisateurs individuels de votre organisation.

1. Vérifiez EwsApplicationAccessPolicy d’une personne en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com | Format-List EwsEnabled
   ```

    **R**. Si la commande retourne « **EwsEnabled : $true** », passez à l’étape 2.

2. Vérifiez **l’EwsApplicationAccessPolicy** de la personne en exécutant la commande suivante :

   ```PowerShell
   Get-CASMailbox -Identity adam@contoso.com| Format-List EwsApplicationAccessPolicy,Ews*List
   ```

    **R**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceAllowList**, seules les applications spécifiées dans EwsAllowList sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings dans Outlook pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, s’il est présent dans **EwsAllowList**, en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    - Activez Bookings dans Outlook pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EwsAllowList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsAllowList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    **B**. Si la valeur de **EwsApplicationAccessPolicy** est **EnforceBlockList**, toutes les applications sont autorisées à accéder à EWS et REST, sauf celles spécifiées dans **EwsBlockList**.  

    - Pour désactiver Bookings dans Outlook pour cet utilisateur, ajoutez **MicrosoftOWSPersonalBookings** à **EnforceBlockList** en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsApplicationAccessPolicy  EnforceBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```

    - Pour activer Bookings dans Outlook pour cet utilisateur, supprimez **MicrosoftOWSPersonalBookings**, s’il est présent dans EnforceBlockList, en exécutant la commande suivante :

   ```PowerShell
   Set-CASMailbox -Identity adam@contoso.com -EwsBlockList @{Remove="MicrosoftOWSPersonalBookings"}
   ```

    **C**. Si la valeur de EwsApplicationAccessPolicy est vide, toutes les applications sont autorisées à accéder à EWS et REST.

    - Pour désactiver Bookings dans Outlook pour cet utilisateur, définissez la stratégie **EnforceBlockList** et  **addMicrosoftOWSPersonalBookingsto**  EWSBlockList en exécutant la commande suivante :

    ```PowerShell
   Set-CASMailbox -Identity Adam -EwsApplicationAccessPolicy  EnforceBlockList -EWSBlockList @{Add="MicrosoftOWSPersonalBookings"}
   ```
