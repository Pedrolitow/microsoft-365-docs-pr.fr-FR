---
title: Définition d’entité de clé d’API de service web Azure Machine Learning
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
ms.openlocfilehash: 0f0ee89c7968baa95b53593216c921ec18844386
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503135"
---
# <a name="azure-machine-learning-web-service-api-key"></a>clé API de service web Azure Machine Learning 

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

Ce SIT est également inclus dans le sit [groupé Toutes les informations d’identification](sit-defn-all-creds.md) .

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

## <a name="credential-example"></a>Exemple d’informations d’identification 

`host: account.azureml.net/services/01234567-abcd-abcd-abcd-abcdef012345/workspaces/01234567-abcd-abcd-abcd-abcdef012345/; apikey: abcdefghijklmnopqrstuvwxyz0123456789/+ABCDEabcdefghijklmnopqrstuvwxyz0123456789/+ABCDE==;`

## <a name="checksum"></a>Somme de contrôle

Non

Les SIT qui ont des sommes de contrôle utilisent un calcul unique pour vérifier si les informations sont valides. Cela signifie que lorsque la valeur **de somme de contrôle** est **Oui**, le service peut effectuer une détection positive basée sur les données sensibles uniquement. Lorsque la valeur de somme de **contrôle** est Aucun élément (secondaire) supplémentaire **ne** doit également être détecté pour que le service effectue une détection positive.

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
