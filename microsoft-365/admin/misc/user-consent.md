---
title: Gestion du consentement de l’utilisateur aux applications dans Microsoft 365
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
description: Découvrez le consentement de l’utilisateur aux applications et comment les activer pour autoriser des applications tierces à accéder aux informations Microsoft 365 des utilisateurs.
ms.openlocfilehash: 66cfd821f51624790b6c1e73e0d156da6dfd2380
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68204736"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Gestion du consentement de l’utilisateur aux applications dans Microsoft 365

Ce paramètre contrôle si les utilisateurs peuvent donner ce consentement aux applications qui utilisent OpenID Connect et OAuth 2.0 pour la connexion et les demandes d’accès aux données. Une application peut être créée à partir de votre propre organisation, ou elle peut provenir d’une autre organisation Office 365 ou d’un tiers.

Si vous activez ce paramètre, ces applications demandent aux utilisateurs l’autorisation d’accéder aux données de votre organisation, et les utilisateurs peuvent choisir de les autoriser. Si vous désactivez ce paramètre, les administrateurs doivent donner leur consentement à ces applications pour que les utilisateurs puissent les utiliser. Dans ce cas, envisagez de configurer un flux de travail de consentement administrateur dans le Portail Azure afin que les utilisateurs puissent envoyer une demande d’approbation de l’administrateur afin d’utiliser n’importe quelle application bloquée.

Un utilisateur peut autoriser uniquement les applications dont il est propriétaire à accéder à ses informations Office 365. Il ne peut pas autoriser une application à accéder aux informations d'un autre utilisateur.

## <a name="turning-user-consent-on-or-off"></a>Activation ou désactivation du consentement de l’utilisateur

Voici comment activer ou désactiver le consentement de l’utilisateur aux applications.

1. Dans le centre d’administration, accédez à la page [Services](https://go.microsoft.com/fwlink/p/?linkid=2053743) **paramètres** \> **de l’organisation des paramètres** > , puis sélectionnez **Le consentement de l’utilisateur pour les applications**.

2. Dans la page **Consentement de l’utilisateur aux applications** , sélectionnez l’option permettant d’activer ou de désactiver le consentement de l’utilisateur.

## <a name="related-content"></a>Contenu associé 

[Configurer le flux de travail de consentement administrateur](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (article)\
[Gestion du consentement aux applications et évaluation des demandes de consentement](/azure/active-directory/manage-apps/manage-consent-requests) (article)