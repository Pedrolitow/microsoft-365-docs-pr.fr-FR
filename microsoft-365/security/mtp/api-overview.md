---
title: Vue d’ensemble des API Microsoft 365 Defender
description: En savoir plus sur les API disponibles dans Microsoft 365 Defender
keywords: API, API, vue d’ensemble, incident, incidents, chasse aux menaces, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 1a75a561e60c05208e8ea302505f9644ac0bc044
ms.sourcegitcommit: d6b1da2e12d55f69e4353289e90f5ae2f60066d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "49719189"
---
# <a name="overview-of--microsoft-365-defender-apis"></a>Vue d’ensemble des API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations se rapportent à des produits précommercialisés susceptibles d’être modifiés de manière substantielle avant leur publication commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft 365 Defender est basé sur une plateforme compatible avec l’intégration.

Utilisez les API Microsoft 365 Defender pour automatiser les flux de travail en fonction de l’incident partagé et des tableaux de la chasse avancée.

- Mise en **[file d’attente des incidents combinés](api-incident.md)** : focalisation sur ce qui est essentiel en regroupant l’étendue d’attaque complète et tous les actifs affectés ensemble sous l’API incidente.

- Recherche des **[menaces entre les produits](api-advanced-hunting.md)** : Tirez parti des connaissances de l’organisation de votre équipe de sécurité pour rechercher des signes de compromission, en créant vos propres requêtes personnalisées pour passer en revue les données brutes collectées sur plusieurs produits de protection.

Outre ces API propres à Microsoft 365 Defender, chacun de nos autres produits de sécurité expose des [API supplémentaires](api-articles.md) pour vous aider à tirer parti de leurs fonctionnalités uniques.

## <a name="learn-more"></a>En savoir plus

| **Comprendre comment accéder aux API** |
|-|
| [En savoir plus sur les quotas d’API et la gestion des licences](api-terms.md) |
| [Accéder aux API Microsoft 365 Defender](api-access.md) |
| **Créer des applications** |
| [Créer une application « Hello World »](api-hello-world.md) |
| [Créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur](api-create-app-user-context.md) |
| [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md) |
| [Créer une application avec un accès partenaire mutualisée aux API Microsoft 365 Defender](api-partner-access.md) |
| **Dépanner et gérer vos applications** |
| [Comprendre les codes d’erreur d’API](api-error-codes.md) |
| [Gérer les secrets dans vos applications avec Azure Key Vault](https://docs.microsoft.com/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implémentation de l’autorisation OAuth 2,0 pour la connexion de l’utilisateur](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
