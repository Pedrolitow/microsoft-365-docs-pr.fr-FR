---
title: Configurations d’évaluation des bases de référence de sécurité
description: Fournit des informations sur les configurations d’évaluation des bases de référence de sécurité qui extraient des données « Gestion des vulnérabilités Microsoft Defender ». Il existe différents appels d’API pour obtenir différents types de données. En général, chaque appel d’API contient les données requises pour les appareils de votre organisation.
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 3905d083652af5ed06c0624e069e32a50cef759f
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642500"
---
# <a name="list-security-baselines-assessment-configurations"></a>Liste des configurations d’évaluation des lignes de base de sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Gestion des vulnérabilités de Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Gestion des vulnérabilités Microsoft Defender ? En savoir plus sur la façon dont vous pouvez vous inscrire à la [Gestion des vulnérabilités Microsoft Defender préversion publique](../defender-vulnerability-management/get-defender-vulnerability-management.md).

## <a name="1-get-all-security-baselines-assessment-configurations"></a>1. Obtenir toutes les configurations d’évaluation des bases de référence de sécurité

Cette API récupère une liste de toutes les configurations et paramètres d’évaluation des bases de référence de sécurité possibles pour tous les benchmarks disponibles.

### <a name="11-parameters"></a>1.1 Paramètres

- Prend en charge les requêtes OData V4
- Opérateurs OData pris en charge :
  - `$filter`on: `id`, `category`, `name``CCE`
  - `$top` avec une valeur maximale de 10 000
  - `$skip`

### <a name="12-http-request"></a>1.2 Requête HTTP

```http
GET /api/baselineConfigurations 
```

### <a name="13-request-headers"></a>1.3 En-têtes de demande

Nom|Type|Description
:---|:---|:---
Autorisation|Chaîne|Porteur {token}. **Obligatoire**.

### <a name="14-response"></a>1.4 Réponse

Si elle réussit, cette méthode retourne 200 OK avec la liste des configurations de base dans le corps.

### <a name="15-properties"></a>1.5 Propriétés

|Propriété | Type | Description |
|:---|:---|:---|
|ID | Chaîne | Identificateur unique de la configuration spécifique dans le benchmark de référence.
|nom | Chaîne | Le nom de configuration qui s’y trouve apparaît dans le benchmark.
|description | Chaîne | Description de la configuration tel qu’elle apparaît dans le benchmark.
|category | String | Catégorie de configuration tel qu’elle apparaît dans le benchmark.
|complianceLevel|Chaîne|Niveau de conformité du benchmark où cette configuration apparaît.
|`cce`|Int|CCE pour cette configuration telle qu’elle apparaît dans le benchmark.
|Justification |Chaîne|Justification de cette configuration telle qu’elle apparaît dans le benchmark. Pour le benchmark STIG, cela n’est pas fourni pour cette configuration.

## <a name="16-example"></a>Exemple 1.6

### <a name="151-request-example"></a>Exemple de demande 1.5.1

```http
GET https://api.securitycenter.microsoft.com/api/baselineConfigurations
```

### <a name="162-response-example"></a>1.6.2 Exemple de réponse

```json
{
    "@odata.context": " https://api-df.securitycenter.microsoft.com/api/$metadata#BaselineConfigurations ", 
    "value": [
        {
            "id": "1.1.8", 
            "name": "(L1) Ensure 'Allow importing of payment info' is set to 'Disabled'",
            "description": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">This policy setting controls whether users are able to import payment information from another browser into Microsoft Edge as well as whether payment information is imported on first use.</p>",
            "category": "Microsoft Edge",
            "complianceLevels": [
                "Level 1 (L1) - Corporate/Enterprise Environment (general use)",
                "Level 2 (L2) - High Security/Sensitive Data Environment (limited functionality)"
            ],
            "cce": "",
            "rationale": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">Having payment information automatically imported or allowing users to import payment data from another browser into Microsoft Edge could allow for sensitive data to be imported into Edge.</p>",
            "remediation": "<div xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">\r\n  <p>\r\n    <p>\r\nTo establish the recommended configuration via GP, set the following UI path to                 <span class=\"inline_block\">Disabled</span></p>\r\n    <code class=\"code_block\">Computer Configuration\\Policies\\Administrative Templates\\Microsoft Edge\\Allow importing of payment info\r\n</code>\r\n    <p>\r\n      <strong>Note:</strong>\r\n This Group Policy path may not exist by default. It is provided by the Group Policy template                 <span class=\"inline_block\">MSEdge.admx/adml</span>\r\n that can be downloaded from Microsoft                 <a href=\"https://www.microsoft.com/en-us/edge/business/download\">here</a>\r\n.              </p>\r\n    <p class=\"bold\">Impact:</p>\r\n    <p>\r\n      <p>Users will be unable to perform a payment information import from other browsers into Microsoft Edge.</p>\r\n    </p>\r\n  </p>\r\n</div>",
            "benchmarkName": "CIS"
"recommendedValue": [ 
                "Equals '0'" 
            ], 
            "source": [ 
                "hkey_local_machine\\software\\policies\\microsoft\\windows\\eventlog\\security\\retention" 
            ]
        }, 
    ] 
} 
```

## <a name="see-also"></a>Voir aussi

- [Évaluation des bases de la sécurité des exportations](export-security-baseline-assessment.md)
- [Obtenir les profils d’évaluation des bases de référence de sécurité](get-security-baselines-assessment-profiles.md)
