---
title: Définition d’entité de chaîne de connexion Azure IoT (préversion)
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles de chaîne de connexion Azure IoT.
ms.openlocfilehash: 89d2ab0170000285dc2c274f50ff9a5106b5bc59
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997570"
---
# <a name="azure-iot-connection-string-preview"></a>Chaîne de connexion Azure IoT (préversion)

### <a name="format"></a>Format

`HostName` Chaîne suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris les chaînes `azure-devices.net` et `SharedAccessKey`.

## <a name="pattern"></a>Modèle

- la chaîne `HostName`
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- chaîne « azure-devices.<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne `SharedAccessKey`
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison de 43 lettres minuscules ou majuscules, chiffres, barre oblique (/) ou signe plus (+)
- un signe égal (=)

## <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_AzureIoTConnectionString` trouve un contenu qui correspond au modèle.
- L’expression `CEP_CommonExampleKeywords` régulière ne trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure IoT Connection String-->
<Entity id="0b34bec3-d5d6-4974-b7b0-dcdb5c90c29d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureIoTConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
  </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net
