---
title: Définition d’entité de certificat de gestion des abonnements Azure (préversion)
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
description: Définition d’entité de type d’entité de type d’informations sensibles de certificat de gestion d’abonnement Azure.
ms.openlocfilehash: 7ce7b09fdeae6f9622a3aac4f92beb446715f8df
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66995679"
---
# <a name="azure-subscription-management-certificate-preview"></a>Certificat de gestion des abonnements Azure (préversion)

## <a name="format"></a>Format

Combinaison d’un maximum de 20 000 caractères composés de lettres, de chiffres et de caractères spéciaux.

## <a name="pattern"></a>Modèle

Combinaison de 20 000 caractères maximum :
 
- a-z (non sensible à la casse)
- 0-9
- barre oblique (/) ou signe plus (+)
- Jusqu’à deux signes égaux (==)

par exemple :

`MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4EggoaMIIKFjCCBg8GCSqGSIb3DQEHAaCCBgAEggX8MIIF+DCCBfQGCyqGSIb3DQEM`

## <a name="checksum"></a>Somme de contrôle

Oui

## <a name="definition"></a>Définition

Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour s’authentifier avec le [modèle de déploiement classique](/azure/azure-resource-manager/management/deployment-models) fourni par Azure. De nombreux programmes et outils, tels que Visual Studio ou le Kit de développement logiciel (SDK) Azure, utilisent ces certificats pour automatiser la configuration et le déploiement de différents [services Azure](/azure/azure-api-management-certs). 

Il utilise plusieurs ressources principales :

- Modèles du littéral de chaîne encodé en Base64.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.

## <a name="keywords"></a>Mots-clés

### <a name="keyword_base64encodedstringliteral"></a>Keyword_Base64EncodedStringLiteral :

- MII