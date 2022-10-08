---
title: Définition d’entité de clé privée de certificat X.509 (préversion)
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
description: Définition d’entité de type d’entité de type clé privée de certificat X.509.
ms.openlocfilehash: 4b847efe2b3b7495834cb8ec8d7a7c9e8f2b8232
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503113"
---
# <a name="x509-certificate-private-key-preview"></a>Clé privée de certificat X.509 (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Combinaison d’un maximum de 20 000 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison d’un maximum de 40 caractères composée de lettres majuscules, d’espace et de tirets.

## <a name="pattern"></a>Modèle

Combinaison de 20 000 caractères maximum :
 
- a-z (non sensible à la casse)
- 0-9
- barres obliques (/)
- ou signes plus (+)

Jusqu’à deux signes égaux (==)

par exemple :

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

or

cinq tirets (-)

Et une combinaison de 30 caractères maximum :

- A-Z (respect de la casse) 
- Espaces
- 5 tirets (-)

par exemple :

`-----BEGIN PRIVATE KEY-----`


## <a name="credential-example"></a>Exemple d’informations d’identification 

`-----BEGIN PRIVATE KEY----- MIIPuQIBAzCCD38GCSqGSIb3DQEHAaCCD3AEgg9sMIIPaDCCBZ8GCSqGSIb3DQEHBqCCBZAw...`

> [!IMPORTANT]
> Cet exemple a été tronqué. Il ne s’agit pas d’un exemple détectable de ce SIT.

## <a name="checksum"></a>Somme de contrôle

Oui

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées en tant que composant privé dans [les certificats SSL.](/azure/key-vault/certificate-scenarios) 

Il utilise plusieurs ressources principales :

- Modèles du littéral de chaîne encodé en Base64.
- Modèles d’en-tête de clé privée de certificat.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral :

- Mii

### <a name="keyword_certificateprivatekeyheader"></a>Keyword_CertificatePrivateKeyHeader :

- clé
