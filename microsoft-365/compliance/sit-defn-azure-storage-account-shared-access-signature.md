---
title: Définition d’entité de signature d’accès partagé du compte stockage Azure (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de signature d’accès partagé du compte stockage Azure.
ms.openlocfilehash: 5db8f87ce50f45ed5ce50d4f9badaee7e56d3346
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476638"
---
# <a name="azure-storage-account-shared-access-signature-preview"></a>Signature d’accès partagé du compte stockage Azure (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 44 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison d’un maximum de 76 caractères composés de lettres, de chiffres et de caractères spéciaux.


## <a name="pattern"></a>Modèle

Toute combinaison de 43 caractères comprenant :
 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- se termine par un signe égal (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDE=`

or

Combinaison de 43 à 73 caractères composée de :
 
- a-z (non sensible à la casse)
- 0-9
- ou signes de pourcentage (%)
- se termine par un suffixe « %3d » (non sensible à la casse)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789%2F%2BABCDE%3D`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour accorder des droits d’accès restreints aux [ressources stockage Azure](/rest/api/storageservices/delegate-access-with-shared-access-signature). 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 256 bits encodée en Base64.
- Modèles de clé symétrique 256 bits encodée par URL.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, ID.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey256"></a>Keyword_SymmetricKey256 :

- SharedAccessKey
- AccountKey

### <a name="keyword_symmetrickey256urlencoded"></a>Keyword_SymmetricKey256UrlEncoded :

- sig=
- clé
- jeton
- Secret
- mot de passe
