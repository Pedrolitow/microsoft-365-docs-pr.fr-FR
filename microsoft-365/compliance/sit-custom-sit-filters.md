---
title: Référence des filtres de types d’informations sensibles personnalisés
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Cet article présente une liste des filtres qui peuvent être codés dans des types d’informations sensibles personnalisés.
ms.openlocfilehash: 8cf5e60aeb27ff7426837b8885597a7d03e9e868073262bed263a7f70bbb301b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53879192"
---
# <a name="custom-sensitive-information-type-filters-reference"></a>Référence de filtres de type d’informations sensibles personnalisé

Dans Microsoft, vous pouvez définir des filtres ou des vérifications supplémentaires lors de la création d’un type d’informations sensibles personnalisé (SIT).

## <a name="list-of-supported-filters-and-use-cases"></a>Liste des filtres et cas d’utilisation pris en charge

### <a name="alldigitssame-exclude"></a>AllDigitsSame Exclude

Description : vous permet d’exclure les correspondances qui ont tous les chiffres comme chiffres en double, comme 111111111 ou 111-111-111

Définition des filtres
```xml
<Filters id="ssn_filters">
    <Filter type="AllDigitsSameFilter"></Filter>
</Filters>
```

L’utiliser dans le package de règles au niveau de l’entité
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85"  filters="ssn_filters">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

L’utiliser dans le package de règles au niveau du modèle
```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="ssn_filters">
        <IdMatch idRef="Func_ssn" />
      </Pattern>
</Entity>
```

### <a name="textmatchfilter-startswith"></a>TextMatchFilter StartsWith 

Description : vous permet de définir les caractères de départ de l’entité. Il a deux variantes , inclure et exclure.

Par exemple, pour exclure les numéros commençant par 0500, 91, 091, 010 dans une liste comme celle-ci :

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

vous pouvez utiliser ce xml

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>
</Filters>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```
Par exemple, pour inclure les numéros commençant par 0500, 91, 091, 0100 dans une liste comme celle-ci : 

- 0500-4500-027
- 91564721450
- 91-8523697410
- 700-8956-7844
- 1000-3265-9874
- 0100-7892-3012

vous pouvez utiliser ce xml

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction="StartsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-endswith"></a>TextMatchFilter EndsWith 

Description : vous permet de définir les caractères de fin de l’entité. 

Par exemple, pour exclure les numéros se terminant par 0500 91 091 0100 dans une liste comme celle-ci :

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

vous pouvez utiliser ce xml

```xml
<Filters id="phone_number_filters_exc">
    <Filter type="TextMatchFilter" direction="EndsWith" logic="Exclude" textProcessorId="Keyword_false_positives_sw">
</Filter>

  <Keyword id="Keyword_false_positives_sw">
    <Group matchStyle="string">
      <Term>0500</Term>
      <Term>91</Term>
      <Term>091</Term>
      <Term>0100</Term>
    </Group>
  </Keyword>
```

Par exemple, pour inclure les numéros se terminant par 0500, 91, 091, 0100, dans une liste comme celle-ci :

- 1234567891
- 1234-5678-0091
- 1234.4567.7091
- 1234-8091-4564

vous pouvez utiliser ce xml

```xml
<Filters id="phone_filters_inc">
    <Filter type="TextMatchFilter" direction=" EndsWith" logic="Include" textProcessorId="Keyword_false_positives_sw">
</Filter>
```

### <a name="textmatchfilter-full"></a>TextMatchFilter Full

Description : vous permet d’interdire certaines correspondances pour les empêcher de déclencher la règle. Par exemple, excluez 4111111111111111 de la liste des correspondances de carte de crédit valides.

Par exemple, pour exclure des numéros de carte de crédit tels 4111111111111111 et 3241891031113111 dans une liste comme celle-ci :

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

vous pouvez utiliser ce xml

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Full" logic="Exclude" textProcessorId="Keyword_false_positives_full">
</Filter>

  <Keyword id="Keyword_false_positives_full">
    <Group matchStyle="string">
      <Term>4111111111111111</Term>
      <Term>3241891031113111</Term>
    </Group>
  </Keyword>
```

Par exemple, pour inclure des numéros de carte de crédit tels 4111111111111111 et 3241891031113111 dans une liste comme celle-ci :

- 4485 3647 3952 7352
- 4111111111111111
- 3241891031113111

vous pouvez utiliser ce xml

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_false_positives_full">
</Filter>
```

### <a name="textmatchfilter-prefix"></a>Préfixe TextMatchFilter

Description : vous permet de définir les caractères précédents qui doivent toujours être inclus ou exclus. Par exemple, si le numéro de carte de crédit est précédé de « ID de commande : » supprimez la correspondance des correspondances valides.

Par exemple, pour exclure les occurrences de numéros  de téléphone qui ont Téléphone **numéro** et m’appeler à des chaînes avant le numéro de téléphone, dans une liste comme celle-ci :

- numéro de téléphone 091-8974-653278
- Téléphone 45-124576532-123
- 45-124576532-123

vous pouvez utiliser ce xml

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_prefix">
</Filter>
  <Keyword id="Keyword_false_positives_prefix">
    <Group matchStyle="string">
      <Term>phone number</Term>
      <Term>call me at</Term>
    </Group>
  </Keyword>
```

Par exemple, pour inclure  les occurrences qui ont des chaînes de carte de crédit et de carte **#** avant le numéro de carte de crédit, dans une liste comme celle-ci :

- Carte de crédit 45-124576532-123 
- 45-124576532-123 (qui peut être un numéro de téléphone)

vous pouvez utiliser ce xml

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_prefix">
</Filter>

  <Keyword id="Keyword_true_positives_prefix">
    <Group matchStyle="string">
      <Term>credit card</Term>
      <Term>card #</Term>
    </Group>
  </Keyword
```

### <a name="textmatchfilter-suffix"></a>Suffixe TextMatchFilter

Description : vous permet de définir les caractères suivants qui doivent toujours être inclus ou exclus. Par exemple, si le numéro de carte de crédit est suivi de « /xuid », supprimez la correspondance des correspondances valides.

Par exemple, les occurrences les plus exclues s’il y a 5 instances de quatre chiffres en plus comme suffixe dans une liste comme celle-ci :

- 1234-5678-9321 4500 9870 6321 48925566
- 1234-5678-9321

vous pouvez utiliser ce xml

```xml
<Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Regex_false_positives_suffix">
</Filter>

  <Regexid="Regex_false_positives_suffix">(\d{4}){5,}</Regex>
```
Par exemple, pour exclure les occurrences si elles sont **suivies par /xuidsuffix,** comme une dans cette liste :

- 1234-5678-9321 /xuid
- 1234-5678-9321

vous pouvez utiliser ce xml

''xml <Filters id="cc_number_filters_exc">
    <Filter type="TextMatchFilter" direction="Prefix" logic="Exclude" textProcessorId="Keyword_false_positives_suffix">
</Filter>

  <Keyword id="Keyword_false_positives_suffix"> <Group matchStyle="string">
      <Term>/xuid</Term>
    </Group> </Keyword>
```

For example, to include an occurrence only if it is followed by **cvv** or **expires**, like two in this list:

- 45-124576532-123 
- 45-124576532-123  cvv 966
- 45-124576532-123  expires 03/23

you can use this xml

```xml
<Filters id="cc_filters_inc">
    <Filter type="TextMatchFilter" direction="Full" logic="Include" textProcessorId="Keyword_true_positives_suffix">
</Filter>

  <Keyword id="Keyword_true_positives_suffix">
    <Group matchStyle="string">
      <Term>cvv</Term>
      <Term>expires</Term>
    </Group>
  </Keyword>
```

## <a name="using-filters-in-rule-packages"></a>Utilisation de filtres dans des packages de règles

Les filtres peuvent être définis sur l’intégralité de la fonction SIT ou sur un modèle. Voici quelques exemples d’extraits de code. 

### <a name="at-sensitive-information-type-level"></a>Au niveau du type d’informations sensibles

Filtres au niveau de l’entité : couvrira tous les modèles enfants

Les filtres seront appliqués sur **toutes les** instances classées par l’un des modèles de ce type d’entité/sensible

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
```

### <a name="at-the-individual-pattern-of-the-sensitive-information-type-level"></a>Au niveau du modèle individuel du niveau de type d’informations sensibles

Filtre uniquement au niveau du modèle.

Le filtre sera appliqué sur les instances qui correspondent au modèle.

```xml
<Entity id="50842eb7-edc8-4019-85dd-5a5c1f2bb085" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85"  filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Keyword_cc_verification" />
      </Pattern>
</Entity>
```


### <a name="at-sensitive-information-type-level-and-an-additional-filter-on-some-of-the-patterns-of-that-entity"></a>Au niveau du type d’informations sensibles et un filtre supplémentaire sur certains modèles de cette entité

Filtres au niveau de l’entité + modèle

Les filtres seront appliqués sur **toutes les** instances classées par l’un des modèles de cette entité/type sensible. Le filtre de niveau modèle filtre les instances qui correspondent à ce modèle.

```xml
<Entity id="6443b88f-2808-482a-8e1a-3ae5026645e1" patternsProximity="300" recommendedConfidence="85" filters="CompositeFiltersAtEntityLevel">
      <Pattern confidenceLevel="85" filters="CompositeFiltersAtPattern">
        <IdMatch idRef="Regex_denmark_id" />
      </Pattern>
</Entity>
``` 

 

## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

- [Éléments recherchés par les fonctions DLP](what-the-dlp-functions-look-for.md)
