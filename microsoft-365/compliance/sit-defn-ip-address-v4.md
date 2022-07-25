---
title: Définition d’entité d’adresse IP v4
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
description: Définition d’entité de type d’informations sensibles d’adresse IP v4.
ms.openlocfilehash: e145b4342c5b276b66d0ed463a2094b7ada47b01
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996940"
---
# <a name="ip-address-v4"></a>Adresse IP v4

## <a name="format"></a>Format

Modèle complexe qui prend en compte les versions mises en forme (périodes) et non mises en forme (aucune période) des adresses IPv4.

## <a name="pattern"></a>Modèle

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_ipv4_address` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_ipaddress` est trouvé.

Une stratégie DLP a une confiance moyenne ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `Regex_ipv4_address` trouve un contenu qui correspond au modèle.

```xml
      <!-- IP Address v4-->
      <Entity id="a7dd5e5f-e7f9-4626-a2c6-86a8cb6830d2" patternsProximity="300" recommendedConfidence="75" relaxProximity="true">
        <Pattern confidenceLevel="85">
          <IdMatch idRef="Regex_ipv4_address" />
          <Match idRef="Keyword_ipaddress" />
        </Pattern>
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_ipv4_address" />
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (respect de la casse)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה