---
title: Gestion du consentement de l’utilisateur pour les applications dans Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Découvrez le consentement de l’utilisateur aux applications et comment les activer pour permettre aux applications tierces d’accéder aux informations Microsoft 365 des utilisateurs.
ms.openlocfilehash: d194303f0c0c94495f723c80a8aaa3e38a01ea7a
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68731214"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Gestion du consentement de l’utilisateur pour les applications dans Microsoft 365

Ce paramètre détermine si les utilisateurs peuvent donner ce consentement aux applications qui utilisent OpenID Connect et OAuth 2.0 pour la connexion et les demandes d’accès aux données. Une application peut être créée à partir de votre propre organisation ou provenir d’une autre organisation Office 365 ou d’un tiers.

Si vous activez ce paramètre, ces applications demandent aux utilisateurs l’autorisation d’accéder aux données de votre organisation, et les utilisateurs peuvent choisir de l’autoriser ou non. Si vous désactivez ce paramètre, les administrateurs doivent donner leur consentement à ces applications avant que les utilisateurs puissent les utiliser. Dans ce cas, envisagez de configurer un flux de travail de consentement administrateur dans le Portail Azure afin que les utilisateurs puissent envoyer une demande d’approbation de l’administrateur pour utiliser une application bloquée.

Un utilisateur peut autoriser uniquement les applications dont il est propriétaire à accéder à ses informations Office 365. Il ne peut pas autoriser une application à accéder aux informations d'un autre utilisateur.

## <a name="turning-user-consent-on-or-off"></a>Activation ou désactivation du consentement de l’utilisateur

Voici comment activer ou désactiver le consentement de l’utilisateur pour les applications.

1. Dans le Centre d’administration, accédez à [la page](https://go.microsoft.com/fwlink/p/?linkid=2053743) **Paramètres** \> Services **paramètres** >  de l’organisation, puis sélectionnez **Consentement de l’utilisateur pour les applications**.

2. Dans la page **Consentement de l’utilisateur pour les applications** , sélectionnez l’option pour activer ou désactiver le consentement de l’utilisateur.

## <a name="related-content"></a>Contenu associé 

[Configurer le flux de travail de consentement administrateur](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (article)\
[Gestion du consentement aux applications et évaluation des demandes de consentement](/azure/active-directory/manage-apps/manage-consent-requests) (article)