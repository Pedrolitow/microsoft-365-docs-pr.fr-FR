---
title: Définition d’entité secrète d’application Azure DevOps (préversion)
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
description: Définition d’entité de type d’entité de type secret d’application Azure DevOps.
ms.openlocfilehash: d689cb184cd329d1d5686a5dde486305b5375078
ms.sourcegitcommit: 771f7bbb241f910b3e16b4d1f9bbd9c0c8c6fa34
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67309348"
---
# <a name="azure-devops-app-secret-preview"></a>Secret d’application Azure DevOps (préversion)

## <a name="format"></a>Format

Combinaison de 52 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Toute combinaison de 52 caractères composée de :
 
- a-z ou A-Z (respect de la casse)
- ou 2-7

par exemple :

`abcdefghijklmnopqrstuvwxyz234567abcdefghijklmnopqrst`


## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour authentifier les utilisateurs d’applications web pour [l’accès à l’API REST Azure DevOps.](/azure/devops/integrate/get-started/authentication/oauth?view=azure-devops) 

Il utilise plusieurs ressources principales :

- Modèles de clé symétrique 256 bits encodée en Base32.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.
- Modèles de valeurs de maquette, de réactions et d’espaces réservés.
- Dictionnaire de vocabulaire

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickey256b32"></a>Keyword_SymmetricKey256B32 :

- Pat
- jeton
- Ado
- Vsts
- azuredevops
- visualstudio.com
- dev.azure.com
