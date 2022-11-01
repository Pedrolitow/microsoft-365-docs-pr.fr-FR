---
title: Data Residency pour Viva Connections
description: Data Residency pour Viva Connections
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
ms.openlocfilehash: ce1bb0dc936c57493c5fd16e4301adda9e214c8d
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805381"
---
# <a name="data-residency-for-viva-connections"></a>Data Residency pour Viva Connections

## <a name="overview"></a>Vue d’ensemble

Documentation du service : [Vue d’ensemble : Viva Connections](/viva/connections/viva-connections-overview)

Résumé de la capacité : Microsoft Viva Connections est votre passerelle vers une expérience d’employé moderne conçue pour maintenir l’engagement et l’information de chacun. Viva Connections est une application personnalisable dans Microsoft Teams qui offre à chacun une destination personnalisée pour découvrir des nouvelles pertinentes, des conversations et les outils dont ils ont besoin pour réussir.  Le stockage de données est lié aux composants Viva Connections suivants : tableau de bord et flux.

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_.
1. Les données client de l’abonnement Viva Connections sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#viva-connections) pour connaître l’engagement spécifique des données client au repos pour Viva Connections.

### <a name="migration"></a>Migration

Les données sont stockées dans Exchange Online, SharePoint Online et Microsoft Teams.  Les processus de migration sont gérés par les charges de travail applicables/pertinentes.

### <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Nous sommes en train de mettre à jour l’emplacement réel des données dans _le Centre Administration client_.  Une fois cette modification terminée, vous pouvez voir l’emplacement réel des données, pour les données validées, en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil de l’organisation->Emplacement des données.  Tant que cette modification n’est pas visible, vous pouvez afficher les informations d’emplacement des données Exchange Online, SharePoint Online et Microsoft Teams afin de comprendre où vos données validées sont stockées pour ce service.
