---
title: Gestion du consentement de l’utilisateur pour les applications dans Microsoft 365
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Découvrez le consentement de l’utilisateur pour les applications et comment l’activer pour permettre aux applications tierces d’accéder aux informations Microsoft 365.
ms.openlocfilehash: df81d2cf3e1d796e462d2b9240b8288273ed5372
ms.sourcegitcommit: ff1af42b036bfdf75729db8c78f10cf4642616ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "44477171"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Gestion du consentement de l’utilisateur pour les applications dans Microsoft 365

Ce paramètre contrôle si les utilisateurs peuvent accorder cette consentement aux applications qui utilisent OpenID Connect et OAuth 2,0 pour la connexion et les demandes d’accès aux données. Une application peut être créée au sein de votre organisation ou peut provenir d’une autre organisation Office 365 ou d’une tierce partie.

Si vous activez ce paramètre, ces applications demandent aux utilisateurs l’autorisation d’accéder aux données de votre organisation, et les utilisateurs peuvent choisir de les autoriser ou non. Si vous désactivez ce paramètre, les administrateurs doivent consentir à ces applications avant que les utilisateurs puissent les utiliser. Dans ce cas, envisagez de configurer un flux de travail de consentement administratif dans le portail Azure pour permettre aux utilisateurs d’envoyer une demande d’approbation à l’administrateur afin d’utiliser une application bloquée.

Un utilisateur peut autoriser uniquement les applications dont il est propriétaire à accéder à ses informations Office 365. Il ne peut pas autoriser une application à accéder aux informations d'un autre utilisateur.

## <a name="turning-user-consent-on-or-off"></a>Activation ou désactivation du consentement de l’utilisateur
<a name="__toc379982114"> </a>

Voici comment activer ou désactiver le consentement de l’utilisateur pour les applications.

1. Dans le centre d’administration, accédez à la page **paramètres** d’organisation des paramètres, puis \> **Org settings**  >  [Services](https://go.microsoft.com/fwlink/p/?linkid=2053743) sélectionnez **consentement de l’utilisateur pour les applications**.

2. Sur la page de **consentement de l’utilisateur pour les applications** , sélectionnez l’option permettant d’activer ou de désactiver les applications intégrées.

## <a name="more-info"></a>Plus d’informations
<a name="__toc379982114"> </a>

Pour en savoir plus sur la configuration de vos paramètres de consentement dans Azure Active Directory, consultez [la rubrique Configurer le flux de travail de consentement de l’administrateur](https://docs.microsoft.com/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Pour en savoir plus sur la gestion du consentement de l’utilisateur pour les applications, consultez la rubrique [gestion du consentement sur les applications et évaluation des demandes de consentement](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-consent-requests).