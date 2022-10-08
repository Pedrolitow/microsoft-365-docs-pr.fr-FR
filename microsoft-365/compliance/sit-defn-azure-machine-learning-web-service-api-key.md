---
title: Définition d’entité de clé d’API de service web Azure Machine Learning (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de clé de service web Azure Machine Learning.
ms.openlocfilehash: 531befbda54224cddc4a1d4d391469a2ef1b2ff8
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476922"
---
# <a name="azure-machine-learning-web-service-api-key-preview"></a>Clé API du service web Azure Machine Learning (préversion) 

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 88 caractères composés de lettres, de chiffres et de caractères spéciaux se terminant par deux signes égaux (==).

## <a name="pattern"></a>Modèle

N’importe quelle combinaison de 86 caractères :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour se connecter aux [services web Azure Machine Learning](/azure/machine-learning/classic/consume-web-services). 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 512 bits encodée en Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID, AccountName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512 :

- SharedAccessKey
- AccountKey
