---
title: Définition d’entité de clé secrète client Azure AD
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
description: Définition d’entité de type d’entité de type secret client Azure AD.
ms.openlocfilehash: b94130c5ec5a7125890c8fdd2fad4529e461bc5b
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503443"
---
# <a name="azure-ad-client-secret"></a>: clé secrète client Azure AD

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

 ## <a name="format"></a>Format

Combinaison d’un maximum de 40 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison d’un maximum de 40 caractères comprenant :

- a-z (non sensible à la casse)
- 0-9
- tirets (-)
- soulignements (_)
- points (.) 
- ou des accents tilde (~)

par exemple :

`abc7Q~defghijklmnopqrs0t123456789-_.~`

## <a name="credential-example"></a>Exemple d’informations d’identification 

`"AppId=01234567-abcd-abcd-abcd-abcdef012345;AppSecret=abc7Q~defghijklmnopqrstuvwxyz-_.~0123"`

## <a name="checksum"></a>Somme de contrôle

Oui

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité [utilisées pour sécuriser les principaux de service Azure Active Directory](/azure/active-directory/fundamentals/service-accounts-principal). 

Il utilise plusieurs ressources principales :

- Modèles de clé secrète client avec un format spécifique.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_appsecret"></a>Keyword_AppSecret :

- Secret
- mot de passe
- clé

