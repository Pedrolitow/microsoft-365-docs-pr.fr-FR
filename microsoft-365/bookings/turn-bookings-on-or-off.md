---
title: Activer ou désactiver les réservations Microsoft
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Découvrez comment accéder à Microsoft bookings dans Microsoft 365.
ms.openlocfilehash: 7e4eaa1e474f3f49807b842097c855193f028af0
ms.sourcegitcommit: 0402d3275632fceda9137b6abc3ce48c8020172a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49126590"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Activer ou désactiver les réservations Microsoft

Les réservations peuvent être activées ou désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous activez les réservations pour les utilisateurs, ils peuvent créer une page livres, créer un calendrier et autoriser d’autres personnes à réserver des heures.

> [!NOTE]
> Les contrôles d’administration décrits dans ces sections ne sont pas disponibles pour les clients Office 365 gérés par 21Vianet (Chine).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Activer ou désactiver les réservations pour votre organisation à l’aide du centre d’administration Microsoft 365

1. Connectez-vous au centre d’administration Microsoft 365 en tant qu’administrateur général.

2. Dans le centre d’administration, accédez à  **paramètres** d'   \> **organisation** paramètres et sélectionnez **réservations**.

3. Activez cette case à cocher pour **permettre à votre organisation d’utiliser des réservations** d’activation ou de désactivation des réservations pour votre organisation.

   > [!NOTE]
   > La désactivation des réservations désactive tout accès au service, y compris la création et la gestion des pages de livres.

4. Sélectionnez **enregistrer les modifications**.

## <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver les réservations pour votre organisation à l’aide de PowerShell

Pour activer ou désactiver les réservations de votre organisation à l’aide de la cmdlet PowerShell [Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig), [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Activer ou désactiver les réservations pour des utilisateurs individuels

Vous pouvez désactiver les réservations pour des utilisateurs individuels.

1. Accédez au centre d’administration Microsoft 365, **puis sélectionnez utilisateurs** \> **actifs**.

1. Sélectionnez l’utilisateur de votre choix, puis sélectionnez **licences et applications**.

1. Développez **applications** et désactivez la case à cocher Microsoft bookings.

## <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Exiger l’approbation du personnel avant de partager les informations de disponibilité

Les administrateurs peuvent demander aux employés de leur organisation de s’abonner avant que leurs informations de disponibilité soient partagées via les réservations et qu’ils puissent être réservables via une page de réservation. Ce paramètre est disponible dans le centre d’administration Microsoft 365 **sous** \> books **Settings** \> **bookings**.

Lorsque ce paramètre est activé, les employés ajoutés en tant que personnel dans les calendriers de réservation trouveront un lien approbation/rejet dans la notification par e-mail qu’ils reçoivent.

Cette fonctionnalité est progressivement déployée dans le monde entier pour les clients Microsoft 365. Si vous ne voyez pas cette option dans le centre d’administration 365 de Microsoft, consultez-la prochainement.

## <a name="block-social-sharing-options"></a>Bloquer les options de partage social

Les administrateurs peuvent contrôler la manière dont les pages de réservation sont partagées sur des réseaux sociaux. Ce paramètre est disponible dans le centre d’administration Microsoft 365 **sous** \> books **Settings** \> **bookings**.

Cette fonctionnalité est progressivement déployée dans le monde entier pour les clients Microsoft 365. Si vous ne voyez pas cette option dans le centre d’administration 365 de Microsoft, consultez-la prochainement.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Autoriser uniquement les utilisateurs sélectionnés à créer des calendriers de livres

À l’aide de restrictions de stratégie, vous pouvez limiter les utilisateurs titulaires d’une licence à la possibilité de créer des calendriers de livres. Vous devez d’abord activer les réservations pour l’ensemble de votre organisation. Tous les utilisateurs de votre organisation auront des licences de livres, mais seules celles incluses dans la stratégie peuvent créer des calendriers de livrets et disposer d’un contrôle total sur qui peut accéder aux calendriers qu’ils créent.

Les utilisateurs inclus dans cette stratégie peuvent créer des calendriers de réservations et être ajoutés en tant que personnel de n’importe quelle capacité (y compris le rôle d’administrateur) à des calendriers de réservations existants. Les utilisateurs qui ne sont pas inclus dans cette stratégie ne pourront pas créer de nouveaux calendriers de livres comptables et recevront un message d’erreur s’ils essaient de le faire.

Vous devrez exécuter les commandes suivantes à l’aide d’Exchange Online PowerShell. Pour plus d’informations sur l’exécution des cmdlets Exchange Online, consultez la rubrique [connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> Les étapes ci-dessous supposent qu’aucune autre stratégie de boîte aux lettres Outlook Web App (OWA) n’ait été créée dans votre organisation.

1. Créez une stratégie de boîte aux lettres pour les utilisateurs qui doivent être autorisés à créer des calendriers de livres. (La création de calendrier livres est autorisée par défaut par de nouvelles stratégies de boîte aux lettres.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Pour plus d’informations, consultez la rubrique [New-OWAMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/new-owamailboxpolicy).

2. Affectez cette stratégie aux utilisateurs concernés en exécutant cette commande pour chaque utilisateur auquel vous souhaitez accorder l’autorisation de créer des calendriers de livres.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Pour plus d'informations, consultez la rubrique [Set-CASMailbox](https://docs.microsoft.com/powershell/module/exchange/set-casmailbox).

3. Facultatif : exécutez cette commande si vous souhaitez désactiver les réservations pour tous les autres utilisateurs de votre organisation.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Pour plus d'informations, voir [Set-OwaMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/set-owamailboxpolicy).

Pour plus d’informations sur les stratégies de boîte aux lettres OWA, consultez les rubriques suivantes :

- [Créer une stratégie de boîte aux lettres Outlook sur le Web dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Appliquer ou supprimer une stratégie de boîte aux lettres Outlook sur le Web sur une boîte aux lettres dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
