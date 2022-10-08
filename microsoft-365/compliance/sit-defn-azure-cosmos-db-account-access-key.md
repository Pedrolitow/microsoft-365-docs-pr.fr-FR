---
title: Définition d’entité de clé d’accès au compte Azure COSMOS DB (préversion)
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
description: Définition d’entité de type d’entité de type clé sensible d’accès au compte Azure COSMOS DB.
ms.openlocfilehash: dccc5018c5d3a27f188f496cd0d13790b78707d2
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68475966"
---
# <a name="azure-cosmos-db-account-access-key-preview"></a>Clé d’accès au compte Azure COSMOS DB (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 88 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison de 86 caractères composée de :

- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour fournir l’accès aux ressources administratives pour les comptes [Azure COSMOS Database](/azure/cosmos-db/secure-access-to-data) .

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
