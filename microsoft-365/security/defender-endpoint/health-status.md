---
title: Rechercher les problèmes d’état d’intégrité de l’agent
description: En savoir plus sur les valeurs retournées lors de l’exécution de la commande mdatp health
keywords: mdatp health, command, health, status, command, onboarding status
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: cfd86b27acfa359e4446d608c276601daf46e623
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233395"
---
# <a name="investigate-agent-health-issues"></a>Rechercher les problèmes d’état d’intégrité de l’agent

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Le tableau suivant fournit des informations sur les valeurs retournées lorsque vous exécutez la `mdatp health` commande et leurs descriptions correspondantes.

<br>

****

|Valeur|Description|
|---|---|
|automatic_definition_update_enabled|True si les mises à jour automatiques de définition d’antivirus sont activées, false dans le cas contraire.|
|cloud_automatic_sample_submission_consent|Niveau d’envoi de l’exemple actuel. Peut être l’une des valeurs suivantes : <ul><li>**Aucun** : aucun exemple suspect n’est envoyé à Microsoft.</li><li>**Sécurisé** : seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut pour ce paramètre.</li><li>**Tous** : tous les exemples suspects sont envoyés à Microsoft.</li></ul>|
|cloud_diagnostic_enabled|True si la collecte de données de diagnostic facultative est activée, false dans le cas contraire. Pour plus d’informations sur Defender pour point de terminaison et d’autres produits et services tels que Microsoft Defender Antivirus et Windows, consultez [la Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|True si la protection fournie par le cloud est activée, sinon false.|
|conflicting_applications|Liste des applications susceptibles d’entrer en conflit avec Microsoft Defender pour point de terminaison. Cette liste inclut, sans s’y limiter, d’autres produits de sécurité et d’autres applications connus pour provoquer des problèmes de compatibilité.|
|definitions_status|État des définitions antivirus.|
|definitions_updated|Date et heure de la dernière mise à jour de la définition de l’antivirus.|
|definitions_updated_minutes_ago|Nombre de minutes depuis la dernière mise à jour de la définition de l’antivirus.|
|definitions_version|Version de définition de l’antivirus.|
|edr_client_version|Version du client EDR en cours d’exécution sur l’appareil.|
|edr_configuration_version|Version de configuration EDR.|
|edr_device_tags|Liste des balises associées à l’appareil.|
|edr_group_ids|ID de groupe auquel l’appareil est associé.|
|edr_machine_id|Identificateur d’appareil utilisé dans Microsoft 365 Defender.|
|engine_version|Version du moteur antivirus.|
|Sain|True si le produit est sain, false sinon.|
|Autorisé|True si l’appareil est intégré à un locataire, false dans le cas contraire.|
|log_level|Niveau de journal actuel pour le produit.|
|machine_guid|Identificateur de machine unique utilisé par le composant antivirus.|
|network_protection_status|État du composant de protection réseau (macOS uniquement). Peut être l’une des valeurs suivantes : <ul><li>**démarrage** - La protection réseau démarre</li><li>**failed_to_start** - Impossible de démarrer la protection réseau en raison d’une erreur</li><li>**démarré** : la protection réseau est en cours d’exécution sur l’appareil</li><li>**redémarrage** - La protection réseau est en cours de redémarrage</li><li>**arrêt** - La protection réseau s’arrête</li><li>**arrêté** - La protection réseau n’est pas en cours d’exécution</li></ul>|
|org_id|Organisation à laquelle l’appareil est intégré. Si l’appareil n’est pas encore intégré à une organisation, il n’est pas disponible. Pour plus d’informations sur l’intégration, consultez [Intégrer à Microsoft Defender pour point de terminaison](onboarding.md).|
|passive_mode_enabled|True si le composant antivirus est défini pour s’exécuter en mode passif, false dans le cas contraire.|
|product_expiration|Date et heure auxquelles la version actuelle du produit atteint la fin du support.|
|real_time_protection_available|True si le composant de protection en temps réel est sain, sinon false.|
|real_time_protection_enabled|True si la protection antivirus en temps réel est activée, false dans le cas contraire.|
|real_time_protection_subsystem|Sous-système utilisé pour la protection en temps réel. Si la protection en temps réel ne fonctionne pas comme prévu, elle n’est pas disponible.|
|release_ring|Anneau de libération. Pour plus d’informations, consultez [Anneaux de déploiement](deployment-rings.md).|
|
