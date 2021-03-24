---
title: Vue d’ensemble des API Microsoft 365 Defender
description: En savoir plus sur les API disponibles dans Microsoft 365 Defender
keywords: api, api, vue d’ensemble, incident, incidents, recherche de menace, microsoft 365 defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 14553f3891fd81a672b62fa0575f6c253fbb0224
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056666"
---
# <a name="overview-of--microsoft-365-defender-apis"></a>Vue d’ensemble des API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft 365 Defender repose sur une plateforme prête à l’intégration.

Utilisez les API Microsoft 365 Defender pour automatiser les flux de travail en fonction de l’incident partagé et des tables de recherche avancées.

- **[File d’attente d’incidents combinés](api-incident.md)** : concentrez-vous sur les éléments critiques en groupant l’étendue d’attaque complète et tous les biens touchés ensemble sous l’API d’incident.

- Recherche de menaces entre produits : tirez parti des connaissances organisationnelles de votre équipe de sécurité pour chercher des signes de compromission, en créant vos propres requêtes personnalisées pour passer en **[arrière-plan](api-advanced-hunting.md)** les données brutes collectées dans plusieurs produits de protection.

En plus de ces API propres à Microsoft 365 [](api-articles.md) Defender, chacun de nos autres produits de sécurité expose des API supplémentaires pour vous aider à tirer parti de leurs fonctionnalités uniques.

## <a name="learn-more"></a>En savoir plus

| **Comprendre comment accéder aux API** |
|-|
| [En savoir plus sur les quotas d’API et les licences](api-terms.md) |
| [Accéder aux API Microsoft 365 Defender](api-access.md) |
| **Créer des applications** |
| [Créer une application « Hello World »](api-hello-world.md) |
| [Créer une application pour accéder aux API Microsoft 365 Defender au nom d’un utilisateur](api-create-app-user-context.md) |
| [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md) |
| [Créer une application avec un accès partenaire multi-locataire aux API Microsoft 365 Defender](api-partner-access.md) |
| **Résoudre les problèmes et gérer vos applications** |
| [Comprendre les codes d’erreur de l’API](api-error-codes.md) |
| [Gérer les secrets dans vos applications avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implémenter l’autorisation OAuth 2.0 pour la signature utilisateur](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |