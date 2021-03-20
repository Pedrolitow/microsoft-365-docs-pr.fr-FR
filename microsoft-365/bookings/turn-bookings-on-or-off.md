---
title: Activer ou désactiver Microsoft bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: Découvrez comment accéder à Microsoft Bookings dans Microsoft 365.
ms.openlocfilehash: 7b1582a480ac4fdcd5a131febcc59450aa13e299
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50913765"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>Activer ou désactiver Microsoft bookings

Les réservations peuvent être désactivées pour l’ensemble de votre organisation ou pour des utilisateurs spécifiques. Lorsque vous allumez Bookings pour les utilisateurs, ils peuvent créer une page Bookings, créer un calendrier et autoriser d’autres personnes à réserver du temps avec eux.

> [!NOTE]
> Les contrôles d’administration décrits dans ces sections ne sont pas disponibles pour les clients Office 365 géré par 21Vianet (Chine).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>Activer ou désactiver bookings pour votre organisation à l’aide du Centre d’administration Microsoft 365

1. Connectez-vous au Centre d’administration Microsoft 365 en tant qu’administrateur global.

2. Dans le centre d’administration, sélectionnez  ****   \> **Paramètres de** l’organisation paramètres et **sélectionnez Réservations.**

3. Activez la case à **cocher autoriser votre organisation** à utiliser Bookings pour activer ou désactiver Bookings pour votre organisation.

   > [!NOTE]
   > La désactivation de Bookings désactive tout accès au service, y compris la création et la gestion des pages Bookings.

4. Sélectionnez **Enregistrer les modifications.**

## <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>Activer ou désactiver bookings pour votre organisation à l’aide de PowerShell

Pour activer ou désactiver Bookings pour votre organisation à l’aide de la cmdlet PowerShell [Set-OrganizationConfig, connectez-vous](/powershell/module/exchange/set-organizationconfig)à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="turn-bookings-on-or-off-for-individual-users"></a>Activer ou désactiver les réservations pour des utilisateurs individuels

Vous pouvez désactiver les réservations pour des utilisateurs individuels.

1. Go to the Microsoft 365 admin center, then select **Users** \> **Active users**.

1. Sélectionnez l’utilisateur souhaité, puis **sélectionnez Licences et applications.**

1. Développez **Applications** et cochez la case pour Microsoft Bookings.

## <a name="require-staff-approvals-before-sharing-freebusy-information"></a>Exiger l’approbation du personnel avant de partager des informations de libre/occupé

Les administrateurs peuvent demander aux employés de leur organisation de s’y rendre avant que leurs informations de disponibilité soient partagées par le biais de Bookings et avant qu’ils ne soient bookables via une page de réservation. Ce paramètre est disponible dans le Centre  d’administration Microsoft 365 sous \> **Paramètres Paramètres** \> **Réservations.**

Lorsque ce paramètre est activé, les employés ajoutés en tant que membres du personnel dans les calendriers de réservation trouveront un lien Approuver/Rejeter dans la notification par courrier électronique qu’ils reçoivent.

Cette fonctionnalité est progressivement étendue aux clients Microsoft 365. Si cette option n’est pas disponible dans le Centre d’administration Microsoft 365, consultez-la prochainement.

## <a name="block-social-sharing-options"></a>Bloquer les options de partage social

Les administrateurs peuvent contrôler la façon dont les pages de réservation sont partagées sur les réseaux sociaux. Ce paramètre est disponible dans le Centre  d’administration Microsoft 365 sous \> **Paramètres Paramètres** \> **Réservations.**

Cette fonctionnalité est progressivement étendue aux clients Microsoft 365. Si cette option n’est pas disponible dans le Centre d’administration Microsoft 365, consultez-la prochainement.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>Autoriser uniquement les utilisateurs sélectionnés à créer des calendriers Bookings

En utilisant des restrictions de stratégie, vous pouvez empêcher les utilisateurs titulaires d’une licence de créer des calendriers Bookings. Vous devez d’abord activer Bookings pour l’ensemble de votre organisation. Tous les utilisateurs de votre organisation auront des licences Bookings, mais seuls ceux inclus dans la stratégie peuvent créer des calendriers Bookings et avoir un contrôle total sur les personnes autorisées à accéder aux calendriers qu’ils créent.

Les utilisateurs inclus dans cette stratégie peuvent créer de nouveaux calendriers Bookings et peuvent être ajoutés en tant que membres du personnel à n’importe quelle capacité (y compris le rôle d’administrateur) aux calendriers Bookings existants. Les utilisateurs qui ne sont pas inclus dans cette stratégie ne pourront pas créer de calendriers Bookings et recevront un message d’erreur s’ils essaient de le faire.

Vous devez exécuter les commandes suivantes à l’aide d’Exchange Online PowerShell. Pour plus d’informations sur l’exécution des cmdlets Exchange Online, voir [Se connecter à Exchange Online PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)

> [!IMPORTANT]
> Les étapes ci-dessous supposent qu’aucune autre stratégie de boîte aux lettres Outlook Web App (OWA) n’a été créée dans votre organisation.

1. Créez une stratégie de boîte aux lettres pour les utilisateurs qui doivent être autorisés à créer des calendriers Bookings. (La création de calendrier Bookings est autorisée par défaut par les nouvelles stratégies de boîte aux lettres.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   Pour plus d’informations, [voir New-OwaMailboxPolicy.](/powershell/module/exchange/new-owamailboxpolicy)

2. Affectez cette stratégie aux utilisateurs concernés en exécutant cette commande pour chaque utilisateur que vous souhaitez accorder l’autorisation de créer des calendriers Bookings.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   Pour plus d'informations, consultez la rubrique [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. Facultatif : exécutez cette commande si vous souhaitez désactiver Bookings pour tous les autres utilisateurs de votre organisation.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   Pour plus d'informations, voir [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

Pour plus d’informations OWA stratégies de boîte aux lettres, consultez les rubriques suivantes :

- [Créer une stratégie de boîte aux lettres Outlook sur le web dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [Appliquer ou supprimer une stratégie de boîte aux lettres Outlook sur le web sur une boîte aux lettres dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)