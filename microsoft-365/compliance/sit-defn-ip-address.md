---
title: Définition d’entité d’adresse IP
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
description: Définition d’entité de type d’informations sensibles d’adresse IP.
ms.openlocfilehash: 19c883cccdc45682514bcd553f1b8e4a09d90e12
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996930"
---
# <a name="ip-address"></a>Adresse IP

## <a name="format"></a>Format

### <a name="ipv4"></a>IPv4 :
Modèle complexe qui prend en compte les versions mises en forme (périodes) et non mises en forme (sans périodes) des adresses IPv4

### <a name="ipv6"></a>IPv6 :
Modèle complexe qui prend en compte les nombres IPv6 mis en forme (y compris les deux-points)

## <a name="pattern"></a>Modèle

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Pour IPv6, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière `Regex_ipv6_address` trouve un contenu qui correspond au modèle.
- Aucun mot clé n’est `Keyword_ipaddress` trouvé.

Pour IPv4, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière `Regex_ipv4_address` trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste `Keyword_ipaddress` est trouvé.

Pour IPv6, une stratégie DLP a une grande confiance dans le fait qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière `Regex_ipv6_address` trouve un contenu qui correspond au modèle.
- Aucun mot clé n’est `Keyword_ipaddress` trouvé.

```xml
    <!-- IP Address -->
    <Entity id="1daa4ad5-e2dd-4ca4-a788-54722c09efb2" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="0" maxMatches="0">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv4_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
      <Pattern confidenceLevel="95">
        <IdMatch idRef="Regex_ipv6_address" />
        <Any minMatches="1">
          <Match idRef="Keyword_ipaddress" />
        </Any>
      </Pattern>
    </Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="keyword_ipaddress"></a>Keyword_ipaddress

- IP (ce mot clé respecte la casse)
- ip address
- adresses IP
- protocole internet
- IP-כתובת ה