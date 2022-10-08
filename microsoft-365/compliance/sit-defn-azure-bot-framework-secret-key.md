---
title: Définition d’entité de clé secrète Azure Bot Framework
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
description: Définition d’entité de type d’entité de type clé secrète Azure Bot Framework.
ms.openlocfilehash: bb515b37f16dfe4e810ea38ef30a09563b966693
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503403"
---
# <a name="azure-bot-framework-secret-key"></a>Clé secrète Azure Bot Framework

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Combinaison de 55 caractères composés de lettres, de chiffres et de caractères spéciaux.

ou

Combinaison de 63 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison de 55 caractères :

- a-z (non sensible à la casse)
- 0-9
- soulignements (_)
- ou points (.)


`abcdefghijklmnopqrstuvwxyz.0123456789_ABCDEabcdefghijkl`

ou pour les 63 caractères

Combinaison de 11 caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de trois caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de trois caractères :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)
- un point

Combinaison de 43 caractères

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- ou soulignements (_)

par exemple :

`abcdefghijk.lmn.opq.rstuvwxyz0123456789-_ABCDEFGHIJKLMNOPQRSTUV`


## <a name="credential-example"></a>Exemple d’informations d’identification 

`host: webchat.botframework.com/?s=abcdefghijklmnopqrstuvwxyz.0123456789_ABCDEabcdefghijkl&`

## <a name="checksum"></a>Somme de contrôle

Non

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour se connecter aux [canaux WebChat à partir des services Azure Bot.](/azure/bot-service/bot-service-channel-connect-webchat?view=azure-bot-service-4.0) 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique codée en 328 bits de l’URL Base64.
- Modèles de clé symétrique codée en 360 bits de l’URL Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey328url"></a>Keyword_SymmetricKey328Url :

- botframework
- clé

### <a name="keyword_symmetrickey360url"></a>Keyword_SymmetricKey360Url :

- botframework
- clé
