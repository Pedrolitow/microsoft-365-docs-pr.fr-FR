---
title: API Microsoft Defender pour point de terminaison prise en charge
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
ms.openlocfilehash: 77491620f7efa88f8ab249c2b76cd2532ba679dd
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51198320"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>API Microsoft Defender pour point de terminaison prise en charge

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :** [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)

- Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

## <a name="endpoint-uri-and-versioning"></a>URI et version des points de terminaison

### <a name="endpoint-uri"></a>URI du point de terminaison :            

> L’URI de base du service est : https://api.securitycenter.microsoft.com
> 
> Les requêtes basées sur OData ont le préfixe « /api ». Par exemple, pour obtenir des alertes, vous pouvez envoyer une requête GET à https://api.securitycenter.microsoft.com/api/alerts

### <a name="versioning"></a>Contrôle de version :

> L’API prend en charge le gestion des versions.
> 
> La version actuelle **est V1.0**.
> 
> Pour utiliser une version spécifique, utilisez ce format : `https://api.securitycenter.microsoft.com/api/{Version}` . Par exemple : `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
> 
> Si vous ne spécifiez aucune version (par exemple), vous allez obtenir https://api.securitycenter.microsoft.com/api/alerts la dernière version.


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


En savoir plus sur les entités individuelles pris en charge dans laquelle vous pouvez exécuter des appels d’API et des détails tels que les valeurs de requête HTTP, les en-têtes de requête et les réponses attendues.

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
Recherche avancée | Exécuter des requêtes à partir de l’API.
Alertes | Exécutez des appels d’API tels que obtenir des alertes, créer une alerte, mettre à jour une alerte, etc.
Domaines | Exécutez des appels d’API tels que l’get domain-related devices, domain statistics and more.
Fichiers | Exécutez des appels d’API tels que obtenir des informations sur les fichiers, des alertes liées aux fichiers, des périphériques liés aux fichiers et des statistiques sur les fichiers.
IPs | Exécutez des appels d’API tels que l’get IP-related alerts and get IP statistics.
Ordinateurs | Exécutez des appels d’API tels que obtenir des appareils, obtenir des appareils par ID, des informations sur les utilisateurs connectés, modifier des balises, etc.
Actions de l’ordinateur | Exécutez un appel d’API tel que Isolation, Exécuter une analyse antivirus et bien plus encore.
Indicateurs | Exécutez un appel d’API tel que créer un indicateur, obtenir des indicateurs et supprimer des indicateurs.
Utilisateurs | Exécutez des appels d’API tels que l’accès à des alertes liées à l’utilisateur et à des appareils liés à l’utilisateur.
Niveau | Exécutez des appels d’API tels que obtenir le score d’exposition ou obtenir le score de sécurité de l’appareil.
Logiciels | Exécutez des appels d’API tels que des vulnérabilités de liste par logiciel.
Vulnérabilité | Exécutez des appels d’API tels que des périphériques de liste par vulnérabilité.
Recommandation | Exécutez des appels d’API tels que Obtenir une recommandation par ID.

## <a name="see-also"></a>Voir aussi
- [API Microsoft Defender pour point de terminaison](apis-intro.md)
