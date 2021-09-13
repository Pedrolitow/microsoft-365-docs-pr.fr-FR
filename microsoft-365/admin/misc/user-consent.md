---
title: Gestion du consentement des utilisateurs aux applications dans Microsoft 365
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Découvrez le consentement des utilisateurs aux applications et comment les activer pour autoriser des applications tierces à accéder aux informations d’Microsoft 365 utilisateurs.
ms.openlocfilehash: 629e64494c6d72a13c3b155370a8f47505e9fa20
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59178755"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Gestion du consentement des utilisateurs aux applications dans Microsoft 365

Ce paramètre contrôle si les utilisateurs peuvent donner ce consentement aux applications qui utilisent OpenID Connecter et OAuth 2.0 pour la signature et les demandes d’accès aux données. Une application peut être créée à partir de votre propre organisation, ou elle peut être créée à partir d’une autre Office 365 organisation ou d’un tiers.

Si vous activer ce paramètre, ces applications demandent aux utilisateurs l’autorisation d’accéder aux données de votre organisation, et les utilisateurs peuvent choisir s’ils le souhaitent. Si vous la désactiver, les administrateurs doivent consentir à ces applications avant que les utilisateurs ne les utilisent. Dans ce cas, envisagez de définir un flux de travail de consentement administrateur dans le portail Azure afin que les utilisateurs peuvent envoyer une demande d’approbation d’administrateur pour utiliser n’importe quelle application bloquée.

Un utilisateur peut autoriser uniquement les applications dont il est propriétaire à accéder à ses informations Office 365. Il ne peut pas autoriser une application à accéder aux informations d'un autre utilisateur.

## <a name="turning-user-consent-on-or-off"></a>Autorisation de l’utilisateur sur ou hors de l’utilisateur

Voici comment activer ou désactiver le consentement de l’utilisateur pour les applications.

1. Dans le Centre d’administration, allez à la page **Paramètres** Services de paramètres de l’organisation, puis sélectionnez Consentement de \>   >  [](https://go.microsoft.com/fwlink/p/?linkid=2053743) **l’utilisateur pour les applications.**

2. Dans la page **Consentement de l’utilisateur aux applications,** sélectionnez l’option pour activer ou désactiver le consentement de l’utilisateur.

## <a name="related-content"></a>Contenu associé 

[Configurer le flux de travail de consentement de l’administrateur](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (article)\
[Gestion du consentement aux applications et évaluation des demandes de consentement](/azure/active-directory/manage-apps/manage-consent-requests) (article)