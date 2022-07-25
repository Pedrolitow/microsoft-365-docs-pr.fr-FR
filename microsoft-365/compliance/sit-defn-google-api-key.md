---
title: Définition d’entité de clé API Google (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de clé d’API Google.
ms.openlocfilehash: 5aef61e28dee6624620d1f254434fb860f28f1af
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996569"
---
# <a name="google-api-key-preview"></a>Clé API Google (préversion)

## <a name="format"></a>Format

Combinaison de 39 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Un préfixe de jeton (respectant la casse) 'AIza'

Combinaison de 35 caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- soulignements (_) ou barres obliques descendantes (\)

par exemple :

`AIzaefgh0123456789_-ABCDEFGHIJKLMNOPQRS`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées en tant que chaîne chiffrée simple qui identifie un [client d’API REST Google](https://cloud.google.com/docs/authentication/api-keys) sans principal utilisé pour associer des demandes d’API à votre projet pour le quota et la facturation. 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique de 210 bits encodée en Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey210"></a>Keyword_SymmetricKey210 :

- Aiza
