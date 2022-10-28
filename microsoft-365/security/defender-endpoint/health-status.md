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
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 0d8fe040f8fb8bc28343ee758d0fd58ae307ecd9
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768102"
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
|automatic_definition_update_enabled|True si les mises à jour automatiques des définitions antivirus sont activées; sinon, false.|
|cloud_automatic_sample_submission_consent|Niveau d’envoi de l’exemple actuel. Peut être l’une des valeurs suivantes : <ul><li>**Aucun** : aucun échantillon suspect n’est envoyé à Microsoft.</li><li>**Sécurisé** : seuls les échantillons suspects qui ne contiennent pas d’informations d’identification personnelle (PII) sont envoyés automatiquement. Il s’agit de la valeur par défaut de ce paramètre.</li><li>**Tout** : tous les échantillons suspects sont envoyés à Microsoft.</li></ul>|
|cloud_diagnostic_enabled|True si la collecte de données de diagnostic facultative est activée; sinon, false. Pour plus d’informations sur Defender pour point de terminaison et d’autres produits et services tels que Microsoft Defender Antivirus et Windows, consultez [la Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=827576).|
|cloud_enabled|True si la protection fournie par le cloud est activée; sinon, false.|
|conflicting_applications|Liste des applications susceptibles d’être en conflit avec Microsoft Defender pour point de terminaison. Cette liste inclut, sans s’y limiter, d’autres produits de sécurité et d’autres applications connus pour provoquer des problèmes de compatibilité.|
|definitions_status|État des définitions antivirus.|
|definitions_updated|Date et heure de la dernière mise à jour de la définition antivirus.|
|definitions_updated_minutes_ago|Nombre de minutes depuis la dernière mise à jour de la définition antivirus.|
|definitions_version|Version de la définition de l’antivirus.|
|edr_client_version|Version du client EDR en cours d’exécution sur l’appareil.|
|edr_configuration_version|Version de configuration EDR.|
|edr_device_tags|Liste des balises associées à l’appareil.|
|edr_group_ids|ID de groupe auquel l’appareil est associé.|
|edr_machine_id|Identificateur d’appareil utilisé dans Microsoft 365 Defender.|
|engine_version|Version du moteur antivirus.|
|Sain|True si le produit est sain; sinon, false.|
|Autorisé|True si l’appareil est intégré à un locataire; sinon, false.|
|log_level|Niveau de journal actuel pour le produit.|
|machine_guid|Identificateur de machine unique utilisé par le composant antivirus.|
|network_protection_status|État du composant de protection réseau (macOS uniquement). Peut être l’une des valeurs suivantes : <ul><li>**démarrage** : la protection du réseau démarre</li><li>**failed_to_start** : la protection réseau n’a pas pu être démarrée en raison d’une erreur</li><li>**démarré** : la protection réseau est en cours d’exécution sur l’appareil</li><li>**redémarrage : la** protection réseau est en cours de redémarrage</li><li>**arrêt :** la protection réseau s’arrête</li><li>**arrêté** - La protection réseau n’est pas en cours d’exécution</li></ul>|
|org_id|Organisation à laquelle l’appareil est intégré. Si l’appareil n’est pas encore intégré à une organisation, cela n’est pas disponible. Pour plus d’informations sur l’intégration, consultez [Intégrer à Microsoft Defender pour point de terminaison](onboarding.md).|
|passive_mode_enabled|True si le composant antivirus est défini pour s’exécuter en mode passif; sinon, false.|
|product_expiration|Date et heure de fin du support de la version actuelle du produit.|
|real_time_protection_available|True si le composant de protection en temps réel est sain; sinon, false.|
|real_time_protection_enabled|True si la protection antivirus en temps réel est activée; sinon, false.|
|real_time_protection_subsystem|Sous-système utilisé pour servir la protection en temps réel. Si la protection en temps réel ne fonctionne pas comme prévu, cette opération n’est pas disponible.|
|release_ring|Anneau de libération. Pour plus d’informations, consultez [Anneaux de déploiement](deployment-rings.md).|
|

## <a name="component-specific-health"></a>Intégrité spécifique du composant

Vous pouvez obtenir des informations plus détaillées sur l’intégrité des différentes fonctionnalités de Defender avec `mdatp health --details <feature>`. Par exemple :

    ```bash
    mdatp health --details edr
    ```

    ```
    edr_early_preview_enabled                   : "disabled"
    edr_device_tags                             : []
    edr_group_ids                               : ""
    edr_configuration_version                   : "20.199999.main.2022.10.25.03-514032a834557bdd31ac415be6df278d9c2a4c25"
    edr_machine_id                              : "a47ba049f43319ac669b6291ce73275cd445c9cd"
    edr_sense_guid                              : "298a1a8c-04dd-4929-8efd-3bb14cb54b94"
    edr_preferred_geo                           : "unitedstates"
    ```

Vous pouvez exécuter `mdatp health --help` sur des versions récentes pour répertorier tous les s pris en charge `feature`.
