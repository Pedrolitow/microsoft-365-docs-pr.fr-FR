---
title: API prises en charge Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Découvrez les entités Microsoft Defender pour point de terminaison prises en charge spécifiques auxquelles vous pouvez créer des appels d’API.
keywords: api, api prises en charge, acteur, alertes, appareil, utilisateur, domaine, ip, fichier, requêtes avancées, repérage avancé
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 7f732b38c108d50b2c8950cdc5e30ba1153944b3
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67324383"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>API prises en charge Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :** 
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/index.yml)

> [!IMPORTANT]
> Les fonctionnalités de chasse avancées ne sont pas incluses dans Defender entreprise. Consultez [Comparer les Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison plans 1 et 2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>URI de point de terminaison et contrôle de version

### <a name="endpoint-uri"></a>URI de point de terminaison

> L’URI de base de service est : [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> Les données OData basées sur les requêtes ont le préfixe « /api ». Par exemple, pour obtenir des alertes, vous pouvez envoyer une requête GET à [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>Gestion des versions

> L’API prend en charge le contrôle de version.
>
> La version actuelle est **V1.0**.
>
> Pour utiliser une version spécifique, utilisez ce format : `https://api.securitycenter.microsoft.com/api/{Version}`. Par exemple : `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> Si vous ne spécifiez aucune version (par exemple `https://api.securitycenter.microsoft.com/api/alerts`), vous accédez à la dernière version.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

En savoir plus sur les entités prises en charge individuelles dans lesquelles vous pouvez exécuter des appels d’API et des détails tels que les valeurs de requête HTTP, les en-têtes de demande et les réponses attendues.

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[**Méthodes de chasse avancées**](run-advanced-query-api.md) | Exécutez des requêtes à partir de l’API.
[Méthodes et propriétés **d’alerte**](alerts.md) | Exécutez des appels d’API tels que \- obtenir des alertes, créer une alerte, mettre à jour l’alerte, etc.
[Exporter des méthodes et des propriétés **d’évaluation** par appareil](get-assessment-methods-properties.md) | Exécutez des appels d’API pour collecter des évaluations des vulnérabilités par appareil, par exemple : \- exporter l’évaluation de la configuration sécurisée, exporter l’évaluation de l’inventaire logiciel, exporter l’évaluation des vulnérabilités logicielles et exporter delta des vulnérabilités logicielles.
[Méthodes et propriétés **d’investigation automatisées**](investigation.md) | Exécutez des appels d’API tels que \- la collecte get d’Investigation.
[Méthodes et propriétés de l'état de santé de l'appareil d'exportation](device-health-api-methods-properties.md) | Exécutez des appels d’API tels que - GET /api/public/avdeviceshealth.
[Alertes liées au **domaine**](get-domain-related-alerts.md) | Exécutez des appels d’API tels que \- l’obtention d’appareils liés au domaine, de statistiques de domaine, etc.
[Méthodes et propriétés **de fichier**](files.md) | Exécutez des appels d’API tels que \- l’obtention d’informations sur les fichiers, les alertes liées aux fichiers, les appareils liés aux fichiers et les statistiques de fichier.
[**Méthodes et propriétés des indicateurs**](ti-indicator.md) | Exécutez un appel d’API tel que \- obtenir des indicateurs, créer un indicateur et supprimer des indicateurs.
[**Alertes liées à l’adresse IP**](get-ip-related-alerts.md) | Exécutez des appels d’API tels que \- l’obtention d’alertes liées à l’adresse IP et l’obtention de statistiques IP.
[**Méthodes** et propriétés de l’ordinateur](machine.md) | Exécutez des appels d’API tels que \- l’obtention d’appareils, l’obtention d’appareils par ID, des informations sur les utilisateurs connectés, la modification des étiquettes, etc.
[**Propriétés et méthodes d’action** de machine](machineaction.md) | Exécutez un appel d’API tel que \- Isolation, Exécuter une analyse antivirus et bien plus encore.
[**Méthodes** et propriétés de recommandation](recommendation.md) | Exécutez des appels d’API, comme \- obtenir une recommandation par ID.
[Méthodes et propriétés **de l’activité de correction**](get-remediation-methods-properties.md) | Exécutez un appel d’API comme \- obtenir toutes les tâches de correction, obtenir la tâche de correction des appareils exposés et obtenir une tâche de correction par ID.
[**Méthodes** et propriétés de score](score.md) | Exécutez des appels d’API tels que \- obtenir un score d’exposition ou obtenir le score de sécurité de l’appareil.
[Méthodes et propriétés **logicielles**](software.md) | Exécutez des appels d’API tels que \- des vulnérabilités de liste par logiciel.
[**Méthodes** et propriétés utilisateur](user.md) | Exécutez des appels d’API tels que \- l’obtention d’alertes liées à l’utilisateur et d’appareils liés à l’utilisateur.
[Méthodes et propriétés **de vulnérabilité**](vulnerability.md) | Exécutez des appels d’API tels que \- la liste des appareils par vulnérabilité.

## <a name="see-also"></a>Voir aussi

- [API Microsoft Defender pour point de terminaison](apis-intro.md)

- [notes de publication de l’API Microsoft Defender pour point de terminaison](api-release-notes.md)
