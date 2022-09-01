---
title: Profils d’évaluation des bases de référence de sécurité
description: Fournit des informations sur les API de profils d’évaluation des bases de référence de sécurité qui extraient des données « Gestion des vulnérabilités Microsoft Defender ». Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.
keywords: api, api, évaluation d’exportation, évaluation par appareil, évaluation par ordinateur, rapport d’évaluation des vulnérabilités, évaluation des vulnérabilités des appareils, rapport de vulnérabilité des appareils, évaluation de la configuration sécurisée, rapport de configuration sécurisée, évaluation des vulnérabilités logicielles, rapport de vulnérabilité logicielle, rapport de vulnérabilité par ordinateur,
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
ms.custom: api
ms.openlocfilehash: 13f88b8994fc8bde379b93cc2e0507957a4361e5
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67520608"
---
# <a name="list-all-security-baselines-assessment-profiles"></a>Répertorier tous les profils d’évaluation des bases de référence de sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

## <a name="1-get-security-baselines-assessment-profiles"></a>1. Obtenir les profils d’évaluation des bases de référence de sécurité

Cette API récupère une liste de tous les profils d’évaluation des bases de référence de sécurité créés par l’organisation.

### <a name="11-parameters"></a>1.1 Paramètres

- Prend en charge les requêtes OData V4.
- Opérateurs OData pris en charge :
  - $filter sur : id,name, operatingSystem, operatingSystemVersion, status, settingsNumber, passedDevices, totalDevices
  - $top avec une valeur maximale de 10 000.
  - $skip.

### <a name="12-http-request"></a>1.2 Requête HTTP

```http
GET:/api/baselineProfiles
```

### <a name="13-request-headers"></a>1.3 En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

### <a name="14-properties"></a>1.4 Propriétés

|Propriété | Type | Description |
|:---|:---|:---|
|ID | Chaîne | Identificateur unique pour le profil de base de référence spécifique.
|nom | Chaîne | Nom du profil.
|description | Chaîne | Description du profil.
|Référence | Chaîne | Benchmark de profil.
|version | String | Version du profil.
|operatingSystem|String|Système d’exploitation applicable au profil.
|operatingSystemVersion|Chaîne|Version du système d’exploitation applicable au profil.
|status|Boolean|Indique si le profil est actif ou non
|complianceLevel|Chaîne|Niveau de conformité choisi pour le profil.
|settingsNumber|Int|Nombre de configurations sélectionnées dans le profil.
|createdBy|String|Utilisateur qui a créé ce profil.
|lastUpdatedBy|Date/heure|Dernier utilisateur à modifier ce profil.
|createdOnTimeOffset|Date/heure|Date et heure de création du profil.
|lastUpdateTimeOffset|Date/heure|Date et heure de la dernière mise à jour du profil.
|passedDevices|Int|Nombre d’appareils applicables à ce profil qui sont conformes à toutes les configurations de profil.
|totalDevices|Int|Nombre d’appareils applicables à ce profil.

## <a name="15-example"></a>1.5 Exemple

### <a name="151-request-example"></a>Exemple de demande 1.5.1

```http
GET https://api.securitycenter.microsoft.com/api/baselineProfiles
```

### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": "https:// api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicBaselineProfileDto)",
    "value":
    [
        {
            "id": "02bcbb9d-d197-479e-811e-1cd5a6f9f8fa",
            "name": "Windows 10 build 1909 CIS profile",
            "description": "important",
            "benchmark": "CIS",
            "version": "1.0.0",
            "operatingSystem": "Windows 10",
            "operatingSystemVersion": "1909",
            "status": true,
            "complianceLevel": "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
            "settingsNumber": 51,
            "createdBy": "user@org.net",
            "lastUpdatedBy": null,
            "createdOnTimestampUTC": "0001-01-01T00:00:00Z",
            "lastUpdateTimestampUTC": "0001-01-01T00:00:00Z",
            "passedDevices": 0,
            "totalDevices": 10
        }
     ]
}
```

## <a name="see-also"></a>Voir aussi

- [Évaluation des bases de la sécurité des exportations](export-security-baseline-assessment.md)
- [Obtenir les configurations d’évaluation des bases de référence de sécurité](get-security-baselines-assessment-configurations.md)
