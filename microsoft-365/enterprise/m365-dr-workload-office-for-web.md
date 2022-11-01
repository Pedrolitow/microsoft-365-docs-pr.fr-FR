---
title: Data Residency pour Office pour le web
description: Data Residency pour Office pour le web
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: ed0c8f67eedf666c7a20d2169d64bc2fad41f576
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805348"
---
# <a name="data-residency-for-office-for-the-web"></a>Data Residency pour Office pour le web

## <a name="overview"></a>Vue d’ensemble

Documentation du service : [description du service Office sur le Web - Descriptions des services](/office365/servicedescriptions/office-online-service-description/office-online-service-description)

Résumé des fonctionnalités : Office sur le Web (anciennement Office Web Apps) ouvre les documents Word, Excel et PowerPoint dans votre navigateur web. Office sur le Web facilite le travail et le partage de fichiers Office en tout lieu avec une connexion Internet, à partir de presque n’importe quel appareil. Les clients Microsoft 365 disposant de Word, Excel ou PowerPoint peuvent afficher, créer et modifier des fichiers en déplacement.

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement _Advanced Data Residency_ valide pour tous les utilisateurs du _locataire_.
1. Les données client de l’abonnement Office pour le web sont approvisionnées dans _Région locale Geography_ ou _Zone géographique de la région locale étendue_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#office-for-the-web) pour connaître l’engagement spécifique des données client au repos pour Office pour le web.

### <a name="migration"></a>Migration

Le cache des documents n’est pas migré vers la nouvelle _zone géographique_ et sera rétabli à mesure que les utilisateurs travaillent sur des documents.

### <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Nous sommes en train de mettre à jour l’emplacement réel des données dans _le Centre Administration client_. Une fois cette modification terminée, le locataire peut voir l’emplacement réel des données, pour les données de l’étendue, en accédant à Administration| Paramètres | Paramètres de l’organisation| Profil d’organisation| Emplacement des données. Tant que cette modification n’est pas visible, vous pouvez afficher les données Exchange Online ou les informations d’emplacement SharePoint Online afin de comprendre où les données de l’étendue sont stockées pour ce service.
