---
title: Définition d’entité de clé d’accès partagé Azure IoT
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
- tier3
- purview-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Définition d’entité de type d’entité de type d’informations sensibles de clé d’accès partagé Azure IoT.
ms.openlocfilehash: 54121aba01854f71a136dd224c3958030b8c8874
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476086"
---
# <a name="azure-iot-shared-access-key"></a>Azure IoT clé d’accès partagé  

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 44 caractères composée de lettres, de chiffres et de caractères spéciaux se terminant par un signe égal qui ne fait pas partie du modèle.

## <a name="pattern"></a>Modèle

Toute combinaison de 43 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par un signe égal (=) qui ne fait pas partie du modèle.

Par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour authentifier [les appareils et services Azure IoT](/azure/iot-fundamentals/iot-security-deployment).

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 256 bits encodée en Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256 :

- SharedAccessKey
- AccountKey
