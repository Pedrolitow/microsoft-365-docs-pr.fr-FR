---
title: Rechercher les problèmes d’état d’intégrité de l’agent
description: En savoir plus sur les valeurs renvoyées lors de l’exécution de la commande d’état d’état mdatp
keywords: mdatp health, command, health, status, command, onboarding status
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
ms.openlocfilehash: 13407c78f89058efe15ed0f5d8f23272716e0237
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61937363"
---
# <a name="investigate-agent-health-issues"></a>Rechercher les problèmes d’état d’intégrité de l’agent

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Le tableau suivant fournit des informations sur les valeurs renvoyées lorsque vous exécutez `mdatp health` la commande et leurs descriptions correspondantes.

<br>

****

|Valeur|Description|
|---|---|
|automatic_definition_update_enabled|True si les mises à jour automatiques des définitions antivirus sont activées, false dans le cas contraire.|
|cloud_automatic_sample_submission_consent|Niveau d’envoi actuel de l’exemple. Peut être l’une des valeurs suivantes : <ul><li>**Aucun**: aucun échantillon suspect n’est envoyé à Microsoft.</li><li>**Coffre**: seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut pour ce paramètre.</li><li>**Tous**: tous les échantillons suspects sont envoyés à Microsoft.</li></ul>|
|cloud_diagnostic_enabled|True si la collecte de données de diagnostic facultative est activée, false dans le cas contraire. Pour plus d’informations sur Defender for Endpoint et d’autres produits et services tels que Antivirus Microsoft Defender et Windows, voir déclaration de [confidentialité Microsoft.](https://go.microsoft.com/fwlink/?linkid=827576)|
|cloud_enabled|True si la protection cloud est activée, false dans le cas contraire.|
|conflicting_applications|Liste des applications qui peuvent être en conflit avec Microsoft Defender pour le point de terminaison. Cette liste inclut, sans s’y limiter, d’autres produits de sécurité et autres applications connues pour provoquer des problèmes de compatibilité.|
|definitions_status|État des définitions antivirus.|
|definitions_updated|Date et heure de la dernière mise à jour des définitions antivirus.|
|definitions_updated_minutes_ago|Nombre de minutes depuis la dernière mise à jour des définitions antivirus.|
|definitions_version|Version de définition antivirus.|
|edr_client_version|Version du client PEPT’exécution sur l’appareil.|
|edr_configuration_version|PEPT version de configuration.|
|edr_device_tags|Liste des balises associées à l’appareil.|
|edr_group_ids|ID de groupe associé à l’appareil.|
|edr_machine_id|Identificateur d’appareil utilisé dans Microsoft 365 Defender.|
|engine_version|Version du moteur antivirus.|
|healthy|True si le produit est sain, false dans le cas contraire.|
|licensed|True si l’appareil est intégré à un client, false dans le cas contraire.|
|log_level|Niveau de journal actuel du produit.|
|machine_guid|Identificateur unique de l’ordinateur utilisé par le composant antivirus.|
|network_protection_status|État du composant de protection réseau (macOS uniquement). Peut être l’une des valeurs suivantes : <ul><li>**démarrage** : la protection réseau démarre</li><li>**failed_to_start** - Impossible de démarrer la protection réseau en raison d’une erreur</li><li>**démarré** - La protection du réseau est en cours d’exécution sur l’appareil</li><li>**redémarrage** : la protection du réseau est en cours de redémarrage</li><li>**arrêt :** la protection du réseau s’arrête</li><li>**arrêté -** La protection du réseau n’est pas en cours d’exécution</li></ul>|
|org_id|Organisation à qui l’appareil est intégré. Si l’appareil n’est pas encore intégré à une organisation, l’impression est indisponible. Pour plus d’informations sur l’intégration, voir [Onboard to Microsoft Defender for Endpoint](onboarding.md).|
|passive_mode_enabled|True si le composant antivirus est définie pour s’exécuter en mode passif, false dans le cas contraire.|
|product_expiration|Date et heure d’expiration de la prise en charge de la version actuelle du produit.|
|real_time_protection_available|True si le composant de protection en temps réel est sain, false dans le cas contraire.|
|real_time_protection_enabled|True si la protection antivirus en temps réel est activée, false dans le cas contraire.|
|real_time_protection_subsystem|Sous-système utilisé pour assurer la protection en temps réel. Si la protection en temps réel ne fonctionne pas comme prévu, l’impression est indisponible.|
|release_ring|Anneau de libération. Pour plus d’informations, voir [Anneaux de déploiement.](deployment-rings.md)|
|
