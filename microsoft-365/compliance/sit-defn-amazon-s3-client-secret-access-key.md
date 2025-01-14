---
title: Définition d’entité de clé d’accès secrète client Amazon S3 (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de clé secrète client Amazon S3.
ms.openlocfilehash: 6a3df751075a58b257532f9cff8d41143f325c51
ms.sourcegitcommit: edc9d4dec92ca81cff39bbf9590f1cd3a75ec436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2022
ms.locfileid: "68484561"
---
# <a name="amazon-s3-client-secret-access-key-preview"></a>Clé d’accès secrète client Amazon S3 (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Combinaison de 40 caractères composés de lettres, de chiffres et de caractères spéciaux. 

## <a name="pattern"></a>Modèle

Numéro à 13 chiffres :

Combinaison de 40 caractères composée des éléments suivants : 

- a-z (non sensible à la casse) 
- 0-9 
- barre oblique (/) ou signe plus (+) 

par exemple : 

`AWS Secret: abcdefghijklmnopqrst0123456789/+ABCDEFGH;`

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour accéder à [Amazon Web Services.](/toolkit-for-eclipse/v1/user-guide/setup-credentials.html)


Il utilise plusieurs ressources principales : 
 
- Modèles de clé symétrique 240 bits encodée en Base64. 
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName. 
- Modèles de valeurs de maquette, de réactions et d’espaces réservés. 
- Dictionnaire de mots de vocabulaire.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance. 

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey240"></a>Keyword_SymmetricKey240 : 

- Secret 
- clé 
