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
ms.collection:
- Tier1
- scotvorg
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Découvrez comment accéder à Microsoft Bookings dans Microsoft 365.
ms.openlocfilehash: 52fe958d37dde7bd07602a03846566aa24c10488
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728970"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Activer ou désactiver Microsoft bookings

Les réservations peuvent être activées ou désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous activez Bookings pour les utilisateurs, ils peuvent créer une page Bookings, créer un calendrier et permettre à d’autres personnes de réserver du temps avec eux. Cet article est destiné aux propriétaires et administrateurs qui gèrent Bookings pour leur organisation.

> [!NOTE]
> Les contrôles d’administration décrits dans ces sections ne sont pas disponibles pour Office 365 gérés par les clients 21Vianet (Chine).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Activez ou désactivez Bookings pour votre organisation à l’aide de la Centre d'administration Microsoft 365

1. Connectez-vous au Centre d'administration Microsoft 365 en tant qu’administrateur général.

2. Dans le Centre d’administration, accédez à **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**de l’organisation**</a>.

3. Cochez la case **Autoriser votre organisation à utiliser Bookings** pour activer ou désactiver Bookings pour votre organisation.

   > [!NOTE]
   > La désactivation de Bookings désactive tout accès au service, y compris la création et la gestion des pages Bookings.

4. Sélectionnez **Enregistrer les modifications**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver Bookings pour votre organisation à l’aide de PowerShell

Pour activer ou désactiver Bookings pour votre organisation à l’aide de l’applet de commande PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="granular-controls"></a>Contrôles granulaires

Utilisez les paramètres ci-dessous pour contrôler qui peut utiliser Bookings, décider des informations de Bookings qui sont partagées et si le personnel doit être approuvé avant de pouvoir être ajouté à un calendrier Booking.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Capture d’écran : Paramètres qui vous permettent de contrôler qui peut utiliser Bookings, de décider quelles informations Bookings sont partagées et d’approuver le personnel":::

### <a name="block-bookings-from-outside-your-organization"></a>Bloquer les réservations provenant de l’extérieur de votre organisation

Vous pouvez configurer Bookings afin que seules les personnes de votre organisation puissent prendre rendez-vous. Seuls les utilisateurs de votre organisation qui se sont connectés et qui sont authentifiés peuvent prendre rendez-vous.

### <a name="block-social-sharing-options"></a>Bloquer les options de partage social

Vous pouvez contrôler la façon dont les pages de réservation sont partagées sur les réseaux sociaux. Ce paramètre est disponible dans le Centre d'administration Microsoft 365 sous **Paramètres Paramètres** -> **Paramètres de l’organisation** -> **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Bloquer le partage des détails du personnel avec les clients

Les informations du personnel, telles que les coordonnées, ne seront jamais envoyées aux clients par e-mail ou toute autre communication.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Exiger les approbations du personnel avant de partager les informations de disponibilité

Vous pouvez demander aux employés de votre organisation de s’inscrire avant que leurs informations de disponibilité soient partagées via Bookings et avant qu’ils puissent être réservés via une page de réservation.

Lorsque ce paramètre est activé, les personnes ajoutées en tant que personnel dans les calendriers de réservation reçoivent un e-mail avec un lien **pour Approuver/Rejeter** la demande.

## <a name="restrict-collection-of-customer-data"></a>Restreindre la collecte des données client

Pour des raisons de conformité, vous ne souhaiterez peut-être pas collecter certaines informations client. Si vous cochez une case pour l’une de ces options, ces champs ne seront pas inclus dans les formulaires présentés à vos clients ou clients.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Capture d’écran : cochez les cases pour empêcher les clients de partager des données sensibles avec vous":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Activer ou désactiver Bookings pour les utilisateurs individuels

Vous pouvez désactiver Bookings pour des utilisateurs individuels.

1. Accédez à la Centre d'administration Microsoft 365, puis sélectionnez **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a>.

1. Sélectionnez l’utilisateur souhaité, puis sélectionnez **Licences et applications**.

1. Développez **Applications** et décochez la case pour Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Autoriser uniquement les utilisateurs sélectionnés à créer des calendriers Bookings

En utilisant des restrictions de stratégie, vous pouvez empêcher les utilisateurs sous licence de créer des calendriers Bookings. Tous les utilisateurs de votre organisation auront des licences Bookings, mais seuls ceux inclus dans la stratégie peuvent créer des calendriers Bookings et avoir un contrôle total sur les personnes autorisées à accéder aux calendriers qu’ils créent.

Les utilisateurs inclus dans cette stratégie peuvent créer des calendriers Bookings et peuvent être ajoutés en tant que personnel dans n’importe quelle capacité (y compris le rôle d’administrateur) aux calendriers Bookings existants. Les utilisateurs qui ne sont pas inclus dans cette stratégie ne pourront pas créer de calendriers Bookings et recevront un message d’erreur s’ils tentent de le faire.

Vous devez exécuter les commandes suivantes à l’aide de Exchange Online PowerShell. Pour plus d’informations sur l’exécution des applets de commande Exchange Online, consultez [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Les étapes ci-dessous supposent qu’aucune autre stratégie de boîte aux lettres Outlook Web App (OWA) n’a été créée dans votre organisation.

1. Créez une stratégie de boîte aux lettres pour les utilisateurs qui doivent être autorisés à créer des calendriers Bookings. (La création de calendrier Bookings est autorisée par défaut par les nouvelles stratégies de boîte aux lettres.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Pour plus d’informations, consultez [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Affectez cette stratégie aux utilisateurs concernés en exécutant cette commande pour chaque utilisateur que vous souhaitez accorder à l’autorisation de créer des calendriers Bookings.

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
