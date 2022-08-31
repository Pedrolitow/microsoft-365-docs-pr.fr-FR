---
title: Vue d’ensemble des API Microsoft 365 Defender
description: En savoir plus sur les API disponibles dans Microsoft 365 Defender
keywords: api, api, vue d’ensemble, incidents, incidents, chasse aux menaces, microsoft 365 defender
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.custom: api
ms.openlocfilehash: efa0f6a14915078a87d5b337a2ac523bc11bab26
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479266"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>Vue d’ensemble des API Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Microsoft 365 Defender repose sur une plateforme prête pour l’intégration.

Utilisez les API Microsoft 365 Defender pour automatiser les flux de travail en fonction de l’incident partagé et des tables de repérage avancées.

- **[File d’attente d’incidents combinée :](api-incident.md)** concentrez-vous sur ce qui est critique en regroupant l’étendue complète des attaques et toutes les ressources affectées sous l’API d’incident.

- **[Repérage des menaces inter-produits](api-advanced-hunting.md)** : tirez parti des connaissances organisationnelles de votre équipe de sécurité pour rechercher des signes de compromission, en créant vos propres requêtes personnalisées pour passer au crible les données brutes collectées sur plusieurs produits de protection.

- **[API de streaming d’événements](streaming-api.md)** : envoyez des événements et des alertes en temps réel dans un flux de données unique au fur et à mesure qu’ils se produisent.

Avec ces API spécifiques à Microsoft 365 Defender, chacun de nos autres produits de sécurité expose [des API supplémentaires](api-articles.md) pour vous aider à tirer parti de leurs fonctionnalités uniques.

> [!NOTE]
> La transition vers le portail unifié ne doit pas affecter les tableaux de bord PowerBi en fonction des API Microsoft Defender pour point de terminaison. Vous pouvez continuer à travailler avec les API existantes, quelle que soit la transition du portail interactif.

Regardez cette courte vidéo pour découvrir comment utiliser Microsoft 365 Defender pour automatiser les flux de travail et intégrer des applications.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M?rel=0]

## <a name="learn-more"></a>En savoir plus

| **Comprendre comment accéder aux API** |
|-|
| [En savoir plus sur les quotas d’API et les licences](api-terms.md) |
| [Accéder aux API Microsoft 365 Defender](api-access.md) |
| **Créer des applications** |
| [Créer une application « Hello World »](api-hello-world.md) |
| [Créer une application pour accéder aux API Microsoft 365 Defender pour le compte d’un utilisateur](api-create-app-user-context.md) |
| [Créer une application pour accéder à Microsoft 365 Defender sans utilisateur](api-create-app-web.md) |
| [Créer une application avec un accès partenaire multilocataire aux API Microsoft 365 Defender](api-partner-access.md) |
| **Résoudre et gérer vos applications** |
| [Comprendre les codes d’erreur de l’API](api-error-codes.md) |
| [Gérer les secrets dans vos applications avec Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [Implémenter l’autorisation OAuth 2.0 pour la connexion utilisateur](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
