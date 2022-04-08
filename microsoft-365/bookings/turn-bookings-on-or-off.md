---
title: Activer ou désactiver Microsoft bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Découvrez comment accéder à Microsoft Bookings dans Microsoft 365.
ms.openlocfilehash: a2ab25b3b187ba45dfe460991b91e77d70a2bb70
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715272"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Activer ou désactiver Microsoft bookings

> [!NOTE]
> Cet article vous aide à interagir avec la dernière version de Microsoft Bookings. Les versions précédentes seront mises hors service dans les prochains mois.

Cet article s’adresse aux administrateurs. 

Bookings peut être activé ou désactivé pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous activez Bookings pour les utilisateurs, ils peuvent créer une page Bookings, créer un calendrier et autoriser d’autres personnes à réserver du temps avec eux.

> [!NOTE]
> Les contrôles d’administration décrits dans ces sections ne sont pas disponibles pour Office 365 Exploité par les clients 21Vianet (Chine).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Activez ou désactivez Bookings pour votre organisation à l’aide de la Centre d'administration Microsoft 365

1. Connectez-vous au Centre d'administration Microsoft 365 en tant qu’administrateur général.

2. Dans le centre d’administration, accédez à  **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Paramètres de l’organisation**</a>.

3. Cochez la case **Autoriser votre organisation à utiliser Bookings** pour activer ou désactiver Bookings pour votre organisation.

   > [!NOTE]
   > La désactivation de Bookings désactive tout accès au service, y compris la création et la gestion des pages Bookings.

4. Sélectionnez **Enregistrer les modifications**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver Bookings pour votre organisation à l’aide de PowerShell

Pour activer ou désactiver Bookings pour votre organisation à l’aide de l’applet de commande PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécuter la commande suivante :

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="granular-controls"></a>Contrôles granulaires

Utilisez les paramètres ci-dessous pour contrôler qui peut utiliser Bookings, déterminer les informations Bookings sont partagées et si le personnel a besoin d’une approbation avant de pouvoir les ajouter à un calendrier Booking.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Capture d’écran : Paramètres qui vous permettent de contrôler qui peut utiliser Bookings, de déterminer les informations Bookings partagées et l’approbation du personnel":::

### <a name="block-bookings-from-outside-your-organization"></a>Bloquer les réservations en dehors de votre organisation

Vous pouvez configurer Bookings afin que seules les personnes de votre organisation puissent prendre des rendez-vous. Seuls les utilisateurs de votre organisation qui se sont connectés et qui sont authentifiés peuvent réserver des rendez-vous.

### <a name="block-social-sharing-options"></a>Bloquer les options de partage social

Vous pouvez contrôler la façon dont les pages de réservation sont partagées sur les réseaux sociaux. Ce paramètre est disponible dans le Centre d'administration Microsoft 365 sous les **paramètres** ->  **Paramètres** ->  Org **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Bloquer le partage des détails du personnel avec les clients

Les détails du personnel, tels que les coordonnées, ne seront jamais envoyés aux clients par e-mail ou toute autre communication.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Exiger l’approbation du personnel avant de partager des informations de disponibilité

Vous pouvez demander aux employés de votre organisation de s’inscrire avant que leurs informations de disponibilité ne soient partagées via Bookings et avant qu’elles puissent être réservées via une page de réservation.

Lorsque ce paramètre est activé, les personnes ajoutées en tant que personnel dans les calendriers de réservation reçoivent un e-mail avec un lien pour **approuver/rejeter** la demande.

## <a name="restrict-collection-of-customer-data"></a>Restreindre la collecte des données client

Pour des raisons de conformité, il se peut que vous ne souhaitiez pas collecter certaines informations client. Si vous cochez une case pour l’une de ces options, ces champs ne seront pas inclus dans les formulaires présentés à vos clients ou clients.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Capture d’écran : cochez les cases pour empêcher les clients de partager des données sensibles avec vous":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Activer ou désactiver Bookings pour les utilisateurs individuels

Vous pouvez désactiver Bookings pour les utilisateurs individuels.

1. Accédez à la Centre d'administration Microsoft 365, puis sélectionnez **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.

1. Sélectionnez l’utilisateur souhaité, puis sélectionnez **Licences et applications**.

1. Développez **Applications** et désactivez la case à cocher pour Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Autoriser uniquement les utilisateurs sélectionnés à créer des calendriers Bookings

En utilisant des restrictions de stratégie, vous pouvez empêcher les utilisateurs sous licence de créer des calendriers Bookings. Vous devez d’abord activer Bookings pour l’ensemble de votre organisation. Tous les utilisateurs de votre organisation disposeront de licences Bookings, mais seules celles incluses dans la stratégie peuvent créer Bookings calendriers et avoir un contrôle total sur les personnes qui peuvent accéder aux calendriers qu’ils créent.

Les utilisateurs inclus dans cette stratégie peuvent créer de nouveaux calendriers Bookings et peuvent être ajoutés en tant que personnel dans n’importe quelle capacité (y compris le rôle d’administrateur) aux calendriers Bookings existants. Les utilisateurs qui ne sont pas inclus dans cette stratégie ne pourront pas créer de calendriers Bookings et recevront un message d’erreur s’ils tentent de le faire.

Vous devez exécuter les commandes suivantes à l’aide de Exchange Online PowerShell. Pour plus d’informations sur l’exécution d’applets de commande Exchange Online, consultez [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Les étapes ci-dessous supposent qu’aucune autre stratégie de boîte aux lettres Outlook Web App (OWA) n’a été créée dans votre organisation.

1. Créez une stratégie de boîte aux lettres pour les utilisateurs qui doit être autorisée à créer Bookings calendriers. (Bookings création de calendrier est autorisée par défaut par les nouvelles stratégies de boîte aux lettres.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Pour plus d’informations, consultez [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Affectez cette stratégie aux utilisateurs concernés en exécutant cette commande pour chaque utilisateur que vous souhaitez accorder l’autorisation de créer Bookings calendriers.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Pour plus d'informations, consultez la rubrique [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Facultatif : exécutez cette commande si vous souhaitez désactiver Bookings pour tous les autres utilisateurs de votre organisation.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Pour plus d'informations, voir [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Pour plus d’informations sur les stratégies de boîte aux lettres OWA, consultez les rubriques suivantes :

- [Créer une stratégie de boîte aux lettres Outlook sur le web dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Appliquer ou supprimer une stratégie de boîte aux lettres Outlook sur le web sur une boîte aux lettres dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
