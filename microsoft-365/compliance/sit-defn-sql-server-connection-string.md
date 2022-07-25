---
title: SQL Server définition d’entité de chaîne de connexion
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
description: SQL Server définition d’entité de type d’information sensible de chaîne de connexion.
ms.openlocfilehash: 503b2bae244cec8de5da29228f6517433a162ca1
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66997060"
---
# <a name="sql-server-connection-string"></a>chaîne de connexion SQL Server

## <a name="format"></a>Format

`User Id`Chaîne , `User ID`ou `uid``UserId` suivie des caractères et des chaînes décrits dans le modèle ci-dessous.

## <a name="pattern"></a>Modèle

- la chaîne `User Id`, `User ID`, `uid`ou `UserId`
- toute combinaison d’entre 1 et 200 lettres minuscules ou majuscules, chiffres, symboles, caractères spéciaux ou espaces
- `Password` chaîne ou `pwd` où `pwd` n’est pas précédée d’une lettre minuscule
- un signe égal (=)
- tout caractère qui n’est pas un signe dollar ($), un symbole de pourcentage (%), supérieur au symbole (>), au symbole (@), au guillemet (« ), au point-virgule (;), accolade gauche([) ou crochet gauche ({)
- toute combinaison de 7 à 128 caractères qui ne sont pas un point-virgule (;), barre oblique (/) ou guillemet (« )
- point-virgule (;) ou guillemet (« )

## <a name="checksum"></a>Somme de contrôle

Non

## <a name="definition"></a>Définition

Une stratégie DLP a une confiance élevée ayant détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :

- L’expression régulière `CEP_Regex_SQLServerConnectionString` trouve un contenu qui correspond au modèle.
- Un mot clé est `CEP_GlobalFilter` introuvable.
- L’expression `CEP_PasswordPlaceHolder` régulière ne trouve pas de contenu qui correspond au modèle.
- L’expression `CEP_CommonExampleKeywords` régulière ne trouve pas de contenu qui correspond au modèle.

```sql
<!---SQL Server Connection String>
<Entity id="e76b6205-d3cb-46f2-bd63-c90153f2f97d" patternsProximity="300" recommendedConfidence="85">
  <Pattern confidenceLevel="85">
        <IdMatch idRef="CEP_Regex_SQLServerConnectionString" />
        <Any minMatches="0" maxMatches="0">
            <Match idRef="CEP_GlobalFilter" />
            <Match idRef="CEP_PasswordPlaceHolder" />
            <Match idRef="CEP_CommonExampleKeywords" />
        </Any>
    </Pattern>
</Entity>
```

## <a name="keywords"></a>Mots-clés

### <a name="cep_globalfilter"></a>CEP_GlobalFilter

- certains mots de passe
- somepassword
- secretPassword
- Échantillon

### <a name="cep_passwordplaceholder"></a>CEP_PasswordPlaceHolder

Ce type d’informations sensibles identifie ces mots clés à l’aide d’une expression régulière, et non d’une liste de mots clés.

- `Password` ou `pwd` suivi de 0-2 espaces, d’un signe égal (=), de 0-2 espaces et d’un astérisque (*) -OR-
- `Password` ou `pwd` suivi de :
    - Un signe égal (=)
    - Symbole inférieur à (<)
    - Toute combinaison de 1 à 200 caractères qui sont des lettres majuscules ou minuscules, des chiffres, un astérisque (*), un trait d’union (-), un trait d’union (_), un trait de soulignement (_) ou un caractère d’espace blanc
    - Supérieur au symbole (>)

### <a name="cep_commonexamplekeywords"></a>CEP_CommonExampleKeywords

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