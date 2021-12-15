---
title: Partager des calendriers avec des utilisateurs externes
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd
description: Activez le partage de calendrier dans le Centre d'administration Microsoft 365 afin que les utilisateurs peuvent partager leurs calendriers avec toute personne à l’intérieur ou à l’extérieur de l’organisation.
ms.openlocfilehash: 00ae4b96c54ae6b1471a90f598b9f96821947db3
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61530450"
---
# <a name="share-calendars-with-external-users"></a>Partager des calendriers avec des utilisateurs externes

Il est parfois nécessaire pour vos utilisateurs de planifier des réunions avec des personnes extérieures à votre organisation. Pour simplifier le processus de recherche des heures de réunion courantes, Microsoft 365 vous permet de mettre les calendriers à la disposition de ces personnes. Ce sont des personnes qui ont besoin de consulter les heures de libre et de occupé pour les utilisateurs de votre organisation, mais qui n’ont pas de comptes d’utilisateur pour Microsoft 365 organisation.

Vous pouvez activer le partage de calendrier pour tous les utilisateurs de votre organisation dans le Centre d'administration Microsoft 365. Une fois le partage activé, vos utilisateurs peuvent utiliser Outlook Web App pour partager leurs calendriers avec toute personne à l’intérieur ou à l’extérieur de l’organisation. Les membres de l’organisation peuvent afficher le calendrier partagé avec leur propre calendrier. Les personnes extérieures à l’organisation seront envoyées à une URL qu’elles pourront utiliser pour afficher le calendrier. Les utilisateurs de votre organisation décident quand partager et combien partager.

> [!NOTE]
> Si vous souhaitez partager des calendriers avec une organisation qui utilise Exchange Server 2013 (une solution sur site), l’administrateur Exchange devra configurer une relation d’authentification avec le cloud. C’est ce que l’on appelle la fédération et doit satisfaire la exigences logicielle minimale. Pour plus [d’informations,](/exchange/sharing-exchange-2013-help) voir Partage.
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Activer le partage de calendrier à l’aide Centre d'administration Microsoft 365

1. Dans le Centre d’administration,  Paramètres paramètres de l’organisation, puis sous l’onglet \>  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank"> **Services,**</a>sélectionnez **Calendrier.**
  
3. Dans **la** page Calendrier, choisissez si vous souhaitez laisser les utilisateurs partager leurs calendriers avec des personnes extérieures à votre organisation qui ont des Microsoft 365 ou Exchange. Choisissez si vous souhaitez autoriser les utilisateurs anonymes (utilisateurs sans informations d’identification) à accéder aux calendriers via une invitation par courrier électronique.

4. Choisissez le type d’informations de calendrier à mettre à la disposition des utilisateurs. Vous pouvez autoriser toutes les informations ou les limiter uniquement à l’heure, à l’objet et à l’emplacement.

## <a name="external-sharing-sync-interval"></a>Intervalle de synchronisation de partage externe

La synchronisation instantanée pour le partage en dehors de votre client n’est pas prise en charge actuellement. Bien que vous pouvez partager ces configurations, la synchronisation aura lieu régulièrement. Il existe deux types de partage entre les locataires :

1. Microsoft 365 à un autre **utilisateur Microsoft 365 (si** le partage externe est activé) : un calendrier entièrement partagé est créé, mais la synchronisation se produit environ toutes les trois heures. La synchronisation instantanée sera finalement activée pour cette configuration.

2. Microsoft 365 à un **utilisateur Outlook.com**: si le partage externe est désactivé, le partage à un autre utilisateur Microsoft 365 également dans ce groupe. Une URL ICS est générée lors du partage, que le destinataire peut utiliser pour l’ajouter à n’importe quel service de calendrier. Avec un abonnement ICS, le service calendrier du destinataire choisit quand synchroniser l’abonnement ICS pour recevoir de nouvelles mises à jour. Si le destinataire est un Outlook.com ou un utilisateur Microsoft 365, la synchronisation a lieu environ toutes les trois heures.

## <a name="invite-people-to-access-calendars"></a>Inviter des personnes à accéder à des calendriers

Une fois le partage activé, les propriétaires de calendrier peuvent étendre les invitations à des utilisateurs spécifiques. Pour obtenir des instructions, [voir Partager votre calendrier dans Outlook Web App.](https://support.microsoft.com/office/7ecef8ae-139c-40d9-bae2-a23977ee58d5)

## <a name="related-content"></a>Contenu associé

[Activer ou désactiver le partage externe pour un site](/sharepoint/change-external-sharing-site) (article)\
[Vue d’ensemble Centre d'administration Microsoft 365](../admin-overview/admin-center-overview.md) (vidéo)\
[Gérer les courriers électroniques et les calendriers](/admin) (page de liens)

