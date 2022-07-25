---
title: Chaîne de connexion de base de données Azure IAAS et définition d’entité de chaîne de connexion Azure SQL
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
description: Chaîne de connexion de base de données Azure IAAS et Azure SQL définition d’entité de type d’information sensible de chaîne de connexion.
ms.openlocfilehash: 894a849c318ad15ab9baac8343192428d633ce1b
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66996460"
---
# <a name="azure-iaas-database-connection-string-and-azure-sql-connection-string"></a>Chaîne de connexion de base de données Azure IAAS et chaîne de connexion Azure SQL

## <a name="format"></a>Format

`Server`Chaîne , `server`ou `data source` suivie des caractères et des chaînes décrits dans le modèle ci-dessous, y compris la chaîne `cloudapp.azure.com` ou `cloudapp.azure.net` ou `database.windows.net`, et la chaîne `Password` ou `pwd``password` .

## <a name="pattern"></a>Modèle

- la chaîne `Server`, `server`ou `data source`
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- Chaîne « cloudapp.azure.<!--no-hyperlink-->com », « cloudapp.azure.<!--no-hyperlink-->net », ou « database.windows.<!--no-hyperlink-->net »
- toute combinaison d’entre 1 et 300 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- la chaîne `Password`, `password`ou `pwd`
- de zéro à deux espaces blancs
- un signe égal (=)
- de zéro à deux espaces blancs
- un ou plusieurs caractères qui ne sont pas un point-virgule (;), guillemets (« ) ou apostrophe (')
- un point-virgule (;), guillemet (« ), ou apostrophe (')

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_AzureConnectionString` trouve un contenu qui correspond au modèle.
- L’expression `CEP_CommonExampleKeywords` régulière ne trouve pas de contenu qui correspond au modèle.

```xml
<!--Azure IAAS Database Connection String and Azure SQL Connection String-->
<Entity id="ce1a126d-186f-4700-8c0c-486157b953fd" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_AzureConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="cep_common_example_keywords"></a>CEP_common_example_keywords

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- Contoso
- Fabrikam
- Northwind
- Sandbox
- Onebox
- Localhost
- 127.0.0.1
- testacs.<!--no-hyperlink-->Com
- s-int.<!--no-hyperlink-->Net
