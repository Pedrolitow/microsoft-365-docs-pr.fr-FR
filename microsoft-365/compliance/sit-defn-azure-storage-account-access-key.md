---
title: Définition d’entité de clé d’accès au compte de stockage Azure (préversion)
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
description: Définition d’entité de type d’entité de type clé sensible d’accès au compte de stockage Azure.
ms.openlocfilehash: a671e350f7834d0454762d2f6c9fad9d333cddda
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996650"
---
# <a name="azure-storage-account-access-key-preview"></a>Clé d’accès au compte de stockage Azure (préversion)

## <a name="format"></a>Format

Combinaison d’un maximum de 20 000 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 88 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison d’un maximum de 20 000 caractères comprenant :
 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)
- Jusqu’à 2
- signes égaux (=)

par exemple :

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM` Ou

Toute combinaison de 86 caractères composée de :

a-z (non sensible à la casse) 0-9 barres obliques (/) ou signes plus (+) se termine par deux signes égaux (=)

par exemple :

`abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==`


## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour effectuer une requête auprès [des services stockage Azure](/rest/api/storageservices/authorize-with-shared-key), tels que les services Blob, File d’attente, Table et Fichier. 

Il utilise plusieurs ressources principales :

- Modèles du littéral de chaîne encodé en Base64.
- Modèles de clé symétrique codée en Base64 de 512 bits.
- Modèles d’CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName, Id, AccountName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral :

- MII

### <a name="keyword_symmetrickey512"></a>Keyword_SymmetricKey512 :

- SharedAccessKey
- AccountKey
