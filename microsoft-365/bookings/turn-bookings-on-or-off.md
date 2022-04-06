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
description: Découvrez comment accéder à des Microsoft Bookings dans Microsoft 365.
ms.openlocfilehash: 09fba96265bc3d2b67db9152f0c6020e10183314
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634798"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Activer ou désactiver Microsoft bookings

Bookings peut être désactivé pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous  turn on Bookings pour les utilisateurs, ils peuvent créer une page Bookings, créer un calendrier et autoriser d’autres personnes à réserver du temps avec eux.

> [!NOTE]
> Les contrôles d’administration décrits dans ces sections ne sont pas disponibles Office 365 clients gérés par 21Vianet (Chine).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Activer Bookings ou désactiver pour votre organisation à l’aide du Centre d'administration Microsoft 365

1. Connectez-vous au Centre d'administration Microsoft 365 en tant qu’administrateur global.

2. Dans le Centre d’administration, **** Paramètres  \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**paramètres de l’organisation**</a>.

3. Activez la case à cocher Autoriser votre organisation à utiliser **Bookings** pour activer ou désactiver les Bookings pour votre organisation.

   > [!NOTE]
   > La désactivation Bookings désactive tout accès au service, y compris la création et la gestion Bookings pages.

4. Sélectionnez **Enregistrer les modifications**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Activer Bookings votre organisation à l’aide de PowerShell

Pour activer ou désactiver Bookings pour votre organisation à l’aide de l’cmdlet PowerShell [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig), [Connecter sur Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

Utilisez les paramètres ci-dessous pour contrôler qui peut utiliser Bookings, décider quelles informations Bookings sont partagées et si le personnel doit être approuvé avant de pouvoir être ajouté à un calendrier de réservation.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="Screenshot: Paramètres that allow you to control who can use Bookings, decide what Bookings info is shared and staff approval":::

### <a name="block-bookings-from-outside-your-organization"></a>Bloquer les réservations en dehors de votre organisation

Vous pouvez configurer des Bookings de sorte que seules les personnes de votre organisation peuvent prendre des rendez-vous. Seuls les utilisateurs de votre organisation qui se sont inscrits et authentifiés peuvent prendre des rendez-vous.

### <a name="block-social-sharing-options"></a>Bloquer les options de partage social

Vous pouvez contrôler le partage des pages de réservation sur les réseaux sociaux. Ce paramètre est disponible dans la Centre d'administration Microsoft 365 sous **Paramètres** ->  **Org** ->  **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>Bloquer le partage des détails du personnel avec les clients

Les informations du personnel, telles que les coordonnées, ne seront jamais envoyées aux clients par courrier électronique ou toute autre communication.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Exiger l’approbation du personnel avant de partager des informations de libre/occupé

Vous pouvez demander aux employés de votre organisation de s’y rendre avant que leurs informations de disponibilité soient partagées via Bookings et avant qu’ils ne soient accessibles en réservation via une page de réservation.

Lorsque ce paramètre est activé, les personnes ajoutées en tant que membres du personnel dans les calendriers de réservation obtiennent un courrier électronique avec un lien pour **approuver/rejeter** la demande.

## <a name="restrict-collection-of-customer-data"></a>Restreindre la collecte des données client

Pour des raisons de conformité, vous ne souhaitez peut-être pas collecter d’informations client. Si vous cochez une case pour l’une de ces options, ces champs ne seront pas inclus dans les formulaires affichés à vos clients ou clients.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="Capture d’écran : cochez les case pour empêcher les clients de partager des données sensibles avec vous":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Activer Bookings ou désactiver pour des utilisateurs individuels

Vous pouvez désactiver la Bookings pour des utilisateurs individuels.

1. Go to the Centre d'administration Microsoft 365, then select **Users** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Active users**</a>.

1. Sélectionnez l’utilisateur souhaité, puis **licences et applications**.

1. **Développez Applications** et cochez la case pour Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Autoriser uniquement les utilisateurs sélectionnés à créer Bookings calendriers

En utilisant des restrictions de stratégie, vous pouvez empêcher les utilisateurs titulaires d’une licence de créer Bookings calendriers. Vous devez d’abord activer Bookings pour l’ensemble de votre organisation. Tous les utilisateurs de votre organisation auront des licences Bookings, mais seuls ceux inclus dans la stratégie peuvent créer des calendriers Bookings et avoir un contrôle total sur les personnes autorisées à accéder aux calendriers qu’ils créent.

Les utilisateurs inclus dans cette stratégie peuvent créer de nouveaux calendriers Bookings et peuvent être ajoutés en tant que membres du personnel à n’importe quelle capacité (y compris le rôle d’administrateur) aux calendriers Bookings existants. Les utilisateurs qui ne sont pas inclus dans cette stratégie ne pourront pas créer de calendriers Bookings et recevront un message d’erreur s’ils essaient de le faire.

Vous devez exécuter les commandes suivantes à l’aide Exchange Online PowerShell. Pour plus d’informations sur l’Exchange Online des cmdlets, voir Connecter [à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Les étapes ci-dessous supposent qu’aucune Outlook de boîte aux lettres Web App (OWA) n’a été créée dans votre organisation.

1. Créez une stratégie de boîte aux lettres pour les utilisateurs qui doivent être autorisés à créer Bookings calendriers. (Bookings création de calendrier est autorisée par défaut par les nouvelles stratégies de boîte aux lettres.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Pour plus d’informations, [voir New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. Affectez cette stratégie aux utilisateurs concernés en exécutant cette commande pour chaque utilisateur que vous souhaitez accorder l’autorisation de créer Bookings calendriers.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Pour plus d'informations, consultez la rubrique [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Facultatif : exécutez cette commande si vous souhaitez désactiver la Bookings pour tous les autres utilisateurs de votre organisation.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Pour plus d'informations, voir [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Pour plus d’informations OWA stratégies de boîte aux lettres, consultez les rubriques suivantes :

- [Créer une stratégie Outlook sur le web boîte aux lettres dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Appliquer ou supprimer une stratégie Outlook sur le web boîte aux lettres d’une boîte aux lettres dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
