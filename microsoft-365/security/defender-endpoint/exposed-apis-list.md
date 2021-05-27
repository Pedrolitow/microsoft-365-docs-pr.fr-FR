---
title: API prises en charge Microsoft Defender pour point de terminaison.
ms.reviewer: ''
description: Découvrez les entités Microsoft Defender for Endpoint spécifiques pris en charge dans laquelle vous pouvez créer des appels d’API.
keywords: api, api pris en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier, requêtes avancées, recherche avancée
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f7a620ad56496b1a26e193a18fa93f4d217431df
ms.sourcegitcommit: a6fb731fdf726d7d9fe4232cf69510013f2b54ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684146"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>API prises en charge Microsoft Defender pour point de terminaison.

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>URI et version des points de terminaison

### <a name="endpoint-uri"></a>URI de point de terminaison

> L’URI de base du service est : [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> Les requêtes basées sur OData ont le préfixe « /api ». Par exemple, pour obtenir des alertes, vous pouvez envoyer une requête GET à [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Gestion des versions

> L’API prend en charge le gestion des versions.
>
> La version actuelle **est V1.0**.
>
> Pour utiliser une version spécifique, utilisez ce format : `https://api.securitycenter.microsoft.com/api/{Version}` . Par exemple : `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Si vous ne spécifiez aucune version (par exemple), vous allez obtenir `https://api.securitycenter.microsoft.com/api/alerts` la dernière version.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

En savoir plus sur les entités individuelles pris en charge dans laquelle vous pouvez exécuter des appels d’API et des détails tels que les valeurs de requête HTTP, les en-têtes de requête et les réponses attendues.

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Repérage avancé](run-advanced-query-api.md) | Exécuter des requêtes à partir de l’API.
[Méthodes et propriétés de l’alerte](alerts.md) | Exécutez des appels d’API tels \- que obtenir des alertes, créer une alerte, mettre à jour une alerte, etc.
[Exporter les méthodes et propriétés d’évaluation par appareil](get-assessmnt-1methods-properties.md) | Exécutez des appels d’API tels que l’exportation de l’évaluation de la configuration sécurisée, l’évaluation de l’inventaire logiciel et l’évaluation des vulnérabilités \- logicielles.
[Méthodes et propriétés d’investigation automatisée](investigation.md) | Exécutez des appels d’API tels \- que obtenir la collection d’examens.
[Obtenir des alertes liées au domaine](get-domain-related-alerts.md) | Exécutez des appels d’API tels \- que l’get domain-related devices, domain statistics and more.
[Soumettre des méthodes et propriétés](files.md) | Exécutez des appels d’API tels que obtenir des informations sur les fichiers, des alertes liées aux fichiers, des \- périphériques liés aux fichiers et des statistiques sur les fichiers.
[Méthodes et propriétés des indicateurs](ti-indicator.md) | Exécutez un appel d’API tel que obtenir des indicateurs, créer un \- indicateur et supprimer des indicateurs.
[Obtenir des alertes liées à l’IP](get-ip-related-alerts.md) | Exécutez des appels d’API tels \- que l’get IP-related alerts and get IP statistics.
[Méthodes et propriétés de l’ordinateur](machine.md) | Exécutez des appels d’API tels que obtenir des appareils, obtenir des appareils par ID, des informations sur les utilisateurs connectés, modifier des \- balises, etc.
[Méthodes et propriétés de l’action de l’ordinateur](machineaction.md) | Exécutez un appel d’API tel \- que Isolation, Exécuter une analyse antivirus et bien plus encore.
[Méthodes et propriétés de l’action d'amélioration](recommendation.md) | Exécutez des appels d’API tels \- que obtenir une recommandation par ID.
[Méthodes et propriétés des activités de correction](get-remediation-methods-properties.md) | Exécutez un appel d’API comme obtenir toutes les tâches de correction, obtenir une tâche de correction des appareils exposés et obtenir une tâche de correction \- par ID.
[Méthodes et propriétés du score](score.md) | Exécutez des appels d’API tels \- que obtenir le score d’exposition ou obtenir le score de sécurité de l’appareil.
[Méthodes et propriétés du logiciel](software.md) | Exécutez des appels d’API tels que \- des vulnérabilités de liste par logiciel.
[Méthodes de l’utilisateur](user.md) | Exécutez des appels d’API tels que l’accès à des \- alertes liées à l’utilisateur et à des appareils liés à l’utilisateur.
[Méthodes et propriétés de la vulnérabilité](vulnerability.md) | Exécutez des appels d’API tels \- que des périphériques de liste par vulnérabilité.

## <a name="see-also"></a>Voir aussi

- [API Microsoft Defender pour point de terminaison](apis-intro.md)

- [Notes de publication de l’API Microsoft Defender for Endpoint](api-release-notes.md)
