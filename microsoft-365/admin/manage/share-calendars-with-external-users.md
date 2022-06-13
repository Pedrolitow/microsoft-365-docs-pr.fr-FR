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
description: Activez le partage de calendrier dans le Centre d'administration Microsoft 365 afin que les utilisateurs puissent partager leurs calendriers avec n’importe qui à l’intérieur ou à l’extérieur de l’organisation.
ms.openlocfilehash: b3ca1d4f2a6ef24a6958b4fe805ccf617c0984e7
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043141"
---
# <a name="share-microsoft-365-calendars-with-external-users"></a>Partager des calendriers Microsoft 365 avec des utilisateurs externes

Il est parfois nécessaire pour vos utilisateurs de planifier des réunions avec des personnes extérieures à votre organisation. Pour simplifier le processus de recherche d’horaires de réunion courants, Microsoft 365 vous permet de mettre des calendriers à la disposition de ces personnes. Il s’agit de personnes qui doivent voir les heures de disponibilité des utilisateurs de votre organisation, mais qui n’ont pas de comptes d’utilisateur pour votre organisation Microsoft 365.

Vous pouvez activer le partage de calendrier pour tous les utilisateurs de votre organisation dans le Centre d'administration Microsoft 365. Une fois le partage activé, vos utilisateurs peuvent utiliser Outlook Web App pour partager leurs calendriers avec n’importe qui à l’intérieur ou à l’extérieur de l’organisation. Les personnes au sein de l’organisation peuvent afficher le calendrier partagé avec leur propre calendrier. Les personnes extérieures à l’organisation recevront une URL qu’elles peuvent utiliser pour afficher le calendrier. Les utilisateurs de votre organisation décident quand partager et combien ils doivent partager.

> [!NOTE]
> Si vous souhaitez partager des calendriers avec une organisation qui utilise Exchange Server 2013 (une solution locale), l’administrateur Exchange doit configurer une relation d’authentification avec le cloud. Il s’agit d’une fédération qui doit répondre aux exigences logicielles minimales. Pour plus d’informations, consultez [Partage](/exchange/sharing-exchange-2013-help) .
  
## <a name="enable-calendar-sharing-using-the-microsoft-365-admin-center"></a>Activer le partage de calendrier à l’aide de la Centre d'administration Microsoft 365

1. Connectez-vous en tant **qu’administrateur général** au centre d’administration, accédez à **Paramètres** \> **Paramètres de l’organisation**, puis sous l’onglet <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>, sélectionnez **Calendrier**.
  
3. Dans la page **Calendrier**, indiquez si vous souhaitez permettre aux utilisateurs de partager leurs calendriers avec des personnes extérieures à votre organisation qui ont Microsoft 365 ou Exchange. Indiquez si vous souhaitez autoriser les utilisateurs anonymes (utilisateurs sans informations d’identification) à accéder aux calendriers via une invitation par e-mail.

4. Choisissez le type d’informations de calendrier à mettre à la disposition des utilisateurs. Vous pouvez autoriser toutes les informations ou les limiter au temps uniquement ou à l’heure, à l’objet et à l’emplacement uniquement.

## <a name="external-sharing-sync-interval"></a>Intervalle de synchronisation de partage externe

La synchronisation instantanée pour le partage en dehors de votre locataire n’est pas prise en charge actuellement. Bien que vous puissiez partager ces configurations, la synchronisation se produit régulièrement. Il existe deux types de partage entre locataires :

1. **Microsoft 365 à un autre utilisateur Microsoft 365 (si le partage externe est activé)** : un calendrier entièrement partagé est créé, mais la synchronisation se produit environ toutes les trois heures. La synchronisation instantanée sera éventuellement activée pour cette configuration.

2. **Microsoft 365 à un utilisateur Outlook.com** : si le partage externe est désactivé, le partage vers un autre utilisateur Microsoft 365 appartient également à ce groupe. Une URL ICS est générée lors du partage, que le destinataire peut utiliser pour ajouter à n’importe quel service de calendrier. Avec un abonnement ICS, le service de calendrier du destinataire choisit quand synchroniser l’abonnement ICS pour recevoir de nouvelles mises à jour. Si le destinataire est un utilisateur Outlook.com ou Microsoft 365, la synchronisation se produit environ toutes les trois heures.

## <a name="invite-people-to-access-calendars"></a>Inviter des personnes à accéder à des calendriers

Une fois le partage activé, les propriétaires de calendrier peuvent étendre les invitations à des utilisateurs spécifiques.

1. Ouvrez [Outlook sur le Web](https://outlook.office365.com).

2. En haut de la page, sélectionnez le lanceur d’applications, **puis calendrier.** Par défaut, votre calendrier principal est appelé « Calendrier ». Si vous avez créé d’autres calendriers, vous pouvez en sélectionner un à partager à la place. Vous ne pouvez pas partager des calendriers appartenant à d’autres personnes.

3. Entrez le nom ou l’adresse e-mail de la personne avec laquelle vous souhaitez partager votre calendrier dans la **boîte de messagerie Envoyer une invitation de partage** .

4. Choisissez la quantité d’informations que vous souhaitez que cette personne voie :

     - **Peut afficher quand je suis occupé** permet à la personne de voir quand vous êtes occupé, mais n’inclut pas de détails tels que l’emplacement de l’événement.

     - **Peut afficher les titres et les emplacements** permet à la personne de voir quand vous êtes occupé, ainsi que le titre et l’emplacement des événements.

     - **Peut afficher tous les détails** permet à la personne de voir tous les détails de vos événements.

     - **Peut modifier** permet à la personne de voir tous les détails de vos événements et de modifier votre calendrier (disponible uniquement lors du partage avec des personnes de votre organisation).

5. Sélectionnez **Partager**. 

## <a name="related-content"></a>Contenu connexe

[Activer ou désactiver le partage externe pour un site](/sharepoint/change-external-sharing-site) (article)\
[Vue d’ensemble de la Centre d'administration Microsoft 365](../admin-overview/admin-center-overview.md) (vidéo)\
[Gérer les courriers électroniques et les calendriers](/admin) (page de liens)

