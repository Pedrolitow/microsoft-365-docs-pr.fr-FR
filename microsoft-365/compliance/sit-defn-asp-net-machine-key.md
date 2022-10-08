---
title: ASP.NET définition d’entité de clé de machine (préversion)
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
description: ASP.NET définition d’entité de type d’information sensible de clé de machine.
ms.openlocfilehash: 1fe8616229bca7a00581d026a318db4029fc2200
ms.sourcegitcommit: fa570d90b00ed1bb40e1ca27b11c66a84c4204e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2022
ms.locfileid: "68476384"
---
# <a name="aspnet-machine-key-preview"></a>ASP.NET clé de machine (préversion)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="format"></a>Format

Clés symétriques dans la configuration XML.

## <a name="pattern"></a>Modèle

Différents formats de clé symétrique en XML, par exemple :

```xml
<machineKey decryptionKey="******** </br> 
<machineKey validationKey="********
```
## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition


Ce SIT est conçu pour correspondre aux informations de sécurité utilisées pour chiffrer ou hacher des données dans [ASP.NET](/dotnet/api/system.web.security.machinekey?view=netframework-4.8) l’authentification et l’état d’affichage des formulaires. 

Il utilise plusieurs ressources principales :

- Modèles de contexte de clé symétrique dans les fichiers xml.
- Modèles de CredentialName, CredentialFeatures, AccountIdentityName, AccountIdentityValue, ResourceType, ResourceName.

Les modèles sont conçus pour correspondre aux informations d’identification réelles avec une confiance raisonnable. Les modèles ne correspondent pas aux informations d’identification mises en forme en tant qu’exemples. Les valeurs de maquette, les valeurs redépliquées et les espaces réservés, tels que le type d’informations d’identification ou les descriptions d’utilisation, dans la position où une valeur secrète réelle doit être présente ne seront pas mises en correspondance.


## <a name="keywords"></a>Mots-clés

### <a name="keyword_symmetrickeycontextinxml"></a>Keyword_SymmetricKeyContextInXml :

- mot de passe
- clé
- Connectionstring

