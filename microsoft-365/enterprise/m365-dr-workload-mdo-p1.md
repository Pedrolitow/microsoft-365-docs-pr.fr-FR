---
title: Data Residency pour Microsoft Defender pour Office P1
description: En savoir plus sur Data Residency pour Microsoft Defender pour Office P1
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
ms.openlocfilehash: 4e4c002ca4748b2d125c0b8043e6198ac962115f
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805437"
---
# <a name="data-residency-for-microsoft-defender-for-office-p1"></a>Data Residency pour Microsoft Defender pour Office P1

## <a name="overview"></a>Vue d’ensemble

Documentation du service : [sécurité Office 365, y compris Microsoft Defender pour Office 365 et Exchange Online Protection](/microsoft-365/security/office-365-security/defender-for-office-365)

Résumé de la fonctionnalité : protège les e-mails et la collaboration contre les programmes malveillants zero-day, les hameçonnages et la compromission des e-mails professionnels.  MDO P1 s’appuie sur Exchange Online Protection (EOP).  

## <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_
1. Les données client de l’abonnement MDO P1 sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#microsoft-defender-for-office-p1) pour connaître l’engagement spécifique des données client au repos pour Microsoft Defender pour Office P1.

Autres informations

En outre, le traitement des données nécessaires à l’analyse des menaces et à l’inspection des e-mails, documents, messages et liens suspects est effectué dans un environnement de bac à sable et effectué dans la _région locale geography_ ou _la région locale étendue_.

## <a name="exchange-online-protection"></a>Exchange Online Protection

### <a name="overview"></a>Vue d’ensemble

Documentation du service : [vue d’ensemble du Exchange Online Protection (EOP)](/microsoft-365/security/office-365-security/exchange-online-protection-overview)

Résumé des fonctionnalités : Exchange Online Protection (EOP) est le service de filtrage basé sur le cloud qui protège votre organisation contre le courrier indésirable, les programmes malveillants et d’autres menaces de messagerie.

### <a name="data-residency-commitments-available"></a>Data Residency engagements disponibles

#### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_
1. Les données client de l’abonnement EOP sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_

**Engagement:**

Reportez-vous à la page [Engagement Data Residency avancé](m365-dr-commitments.md) pour connaître l’engagement spécifique des données client au repos pour Exchange Online Protection.

## <a name="migration"></a>Migration

Les données client EOP sont migrées pendant la migration Exchange Online. MDO P1 n’a pas de données client à migrer.

## <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Nous sommes en train de mettre à jour l’emplacement réel des données dans le Centre de Administration _locataire_. Une fois cette modification terminée, vous pouvez voir l’emplacement réel des données pour les charges de travail validées en accédant à Administration| Paramètres | Paramètres de l’organisation| Profil d’organisation| Emplacement des données. Tant que cette modification n’est pas visible, vous pouvez afficher les informations d’emplacement des données Exchange Online afin de comprendre où vos données client dans l’étendue sont stockées pour ce service.
