---
title: Data Residency pour Viva Topics
description: Data Residency pour Viva Topics
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
ms.openlocfilehash: 416e6dccca24e4c79c0853cbed886b2d4e977c31
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805380"
---
# <a name="data-residency-for-viva-topics"></a>Data Residency pour Viva Topics

## <a name="summary"></a>Résumé

Documentation du service : [vue d’ensemble de Microsoft Viva Topics](/viva/topics/topic-experiences-overview)

Résumé des fonctionnalités : Viva Topics utilise la technologie d’intelligence artificielle Microsoft, Microsoft 365, Microsoft Graph, la recherche et d’autres composants et services pour apporter des connaissances à vos utilisateurs dans les applications Microsoft 365 qu’ils utilisent quotidiennement, en commençant par les pages modernes SharePoint, Outlook, Microsoft Search et La recherche dans Word, PowerPoint et Excel.

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_.
1. Les données client de l’abonnement Viva Topics sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#viva-topics) pour connaître l’engagement spécifique des données client au repos pour Viva Topics.

## <a name="migration"></a>Migration

Les données sont stockées dans Exchange Online, SharePoint Online et Microsoft Teams.  Les processus de migration sont gérés par les charges de travail applicables/pertinentes.

## <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Nous sommes en train de mettre à jour l’emplacement réel des données dans _le Centre Administration client_.  Une fois cette modification terminée, vous pouvez voir l’emplacement réel des données, pour les données validées, en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil de l’organisation->Emplacement des données.  Tant que cette modification n’est pas visible, vous pouvez afficher les informations d’emplacement des données Exchange Online afin de comprendre où vos données validées sont stockées pour ce service.
