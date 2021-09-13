---
title: Vue d’ensemble Microsoft 365 Defender API
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
ms.openlocfilehash: 2ca601c3c68df9f9f1cc4fb90bcfbe907850ce91
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204546"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Vue d’ensemble Microsoft 365 Defender API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft 365 Defender repose sur une plateforme prête à l’intégration.

Utilisez les API Microsoft 365 Defender pour automatiser les flux de travail en fonction de l’incident partagé et des tables de recherche avancées.

- **[File d’attente d’incidents combinés](api-incident.md)** : concentrez-vous sur ce qui est critique en groupant l’étendue d’attaque complète et toutes les ressources impactées sous l’API d’incident.

- Recherche de menaces entre produits : tirez parti des connaissances organisationnelles de votre équipe de sécurité pour chercher des signes de compromission, en créant vos propres requêtes personnalisées pour passer en **[arrière-plan](api-advanced-hunting.md)** les données brutes collectées sur plusieurs produits de protection.

Utilisez [l’API de diffusion en](../defender-endpoint/raw-data-export.md) continu pour expédier des événements et des alertes en temps réel à partir d’instances telles qu’elles se produisent dans un flux de données unique.

Parallèlement à ces MICROSOFT 365 DEFENDER spécifiques, chacun de nos [](api-articles.md) autres produits de sécurité expose des API supplémentaires pour vous aider à tirer parti de leurs fonctionnalités uniques.

> [!NOTE]
> La transition vers le portail unifié ne doit pas affecter les tableaux de bord PowerBi basés sur les API Microsoft Defender for Endpoint. Vous pouvez continuer à travailler avec les API existantes, quelle que soit la transition du portail interactif.

## <a name="learn-more"></a>En savoir plus

| **Comprendre comment accéder aux API** |
|-|
| [En savoir plus sur les quotas d’API et les licences](api-terms.md) |
| [Accéder aux API Microsoft 365 Defender de données](api-access.md) |
| **Créer des applications** |
| [Créer une application « Hello World »](api-hello-world.md) |
| [Créer une application pour accéder Microsoft 365 Defender API au nom d’un utilisateur](api-create-app-user-context.md) |
| [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md) |
| [Créer une application avec un accès partenaire multi-locataire aux API Microsoft 365 Defender client](api-partner-access.md) |
| **Résoudre les problèmes et gérer vos applications** |
| [Comprendre les codes d’erreur de l’API](api-error-codes.md) |
| [Gérer les secrets dans vos applications avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implémenter l’autorisation OAuth 2.0 pour la signature utilisateur](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |