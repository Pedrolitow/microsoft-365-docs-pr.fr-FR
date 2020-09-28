---
title: Référence de format SKOS pour la taxonomie SharePoint
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
description: Référence de format SKOS pour la taxonomie SharePoint
ms.openlocfilehash: eb228394b06b6e6027937ab105df7c0079875226
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295895"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Référence de format SKOS pour la taxonomie SharePoint

Cet article inclut le vocabulaire RDF utilisé pour représenter la [taxonomie SharePoint](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy) et s’appuie sur [SKOS](https://www.w3.org/TR/skos-primer/). Pour la sérialisation de cette syntaxe RDF, utilisez RDF [Turtle](https://www.w3.org/TR/turtle/).

Le tableau suivant présente les équivalents [SKOS](https://www.w3.org/TR/skos-primer/) pour le vocabulaire de [taxonomie SharePoint](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy) . SharePoint ne prend pas en charge les valeurs [SKOS](https://www.w3.org/TR/skos-primer/) qui n’ont pas d’équivalent de taxonomie SharePoint.

|Taxonomie SharePoint|Équivalent SKOS|
|:-----------------|:--------------|
|SharePoint-taxonomie : terme|SKOS : concept|
|SharePoint-taxonomie : TermSet|skos:ConceptScheme|
|SharePoint-taxonomie : inTermSet|SKOS : inscheme|
|SharePoint-taxonomie : hasTopLevelTerm|skos:hasTopConcept|
|SharePoint-taxonomie : topLevelTermOf|skos:topConceptOf|
|SharePoint-taxonomie : defaultLabel|skos:prefLabel|
|SharePoint-taxonomie : termSetName|skos:prefLabel|
|SharePoint-taxonomie : propertyName|skos:prefLabel|
|SharePoint-taxonomie : otherLabel|skos:altLabel|
|SharePoint-taxonomie : description|SKOS : définition|
|SharePoint : taxonomie : parent|SKOS : plus large|
|SharePoint-taxonomie : enfant|SKOS : plus étroit|

Le tableau suivant affiche les entités du vocabulaire de taxonomie SharePoint dérivé de [Owl](https://www.w3.org/TR/owl2-primer/).

|Vocabulaire de taxonomie SharePoint|Dérivé de OWL|
|:-----------------------------|:----------------------|
|SharePoint-taxonomie : isAvailableForTagging|owl:datatypeproperty|
|SharePoint-taxonomie : SharedCustomPropertyForTerm|Owl : ObjectProperty|
|SharePoint-taxonomie : LocalCustomPropertyForTerm|Owl : ObjectProperty|
|SharePoint-taxonomie : CustomPropertyForTermSet|Owl : ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>Vocabulaire de taxonomie SharePoint

Une taxonomie est un système de classification formel. Une taxonomie regroupe les mots, étiquettes et termes qui décrivent un article, puis réorganise les groupes dans une hiérarchie.

**SharePoint-taxonomie : terme**

Représente un terme ou un mot clé dans une hiérarchie de métadonnées gérées.

Un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) est l’unité atomique d’un [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore)SharePoint. Chaque [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) appartient à un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset) qui appartient à un [TermGroup](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.group). 

La syntaxe de définition d’un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) est la suivante :

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

[Terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) obligatoire dans un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel est le nom du [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) tel qu’il apparaît dans la représentation visuelle. Les champs requis pour la définition d’un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) sont les suivants :

- SharePoint-taxonomie : defaultLabel
- SharePoint-taxonomie : inTermSet

Un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) peut :

- Être hiérarchiquement lié à un autre [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) qui est fourni les deux [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) appartiennent au même [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Avoir plusieurs [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term)enfants, mais un seul [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term)parent.
- N’a pas de [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) parent défini, s’il s’agit d’un TopLevelTermOf un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- Avoir un defaultLabel, par [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore) de travail.
- N’existe pas s’il ne contient pas de [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term)parent et s’il n’est pas TopLevelTermOf un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). 
- Ont seulement un defaultLabel unique au même niveau hiérarchique.

**SharePoint-taxonomie : TermSet**

Représente un ensemble hiérarchique ou plat d’objets Term appelés « TermSet ».

Comme son nom l’indique, TermSet est un ensemble de [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term). Un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) dans un [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore) doit appartenir à un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). Aucun [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ne peut être indépendant. 

La syntaxe de définition d’un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset) est la suivante :

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

Les [TermSets](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset) sont regroupés de manière logique dans [TermGroups](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.group). Le champ obligatoire pour la définition d’une [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset) est le suivant :

- SharePoint-taxonomie : termSetName

Dans le cas de l’termSetName fourni n’est pas unique au sein de l' [TermGroup](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.group), mis ajoute un numéro à la fin du nom pour maintenir l’unicité de termSetName (s).

**SharePoint-taxonomie : hasTopLevelTerm**

SharePoint utilise cette propriété pour mapper le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) le plus élevé dans le [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset), qui est le point d’entrée de la hiérarchie des [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) dans un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). Il s’agit d’une relation inverse avec SharePoint-taxonomique : topLevelTermOf. 

La syntaxe de définition est la suivante :

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

>[!NOTE]
> Vous ne pouvez pas définir le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) de niveau supérieur d’un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term)parent.

**SharePoint-taxonomie : topLevelTermOf**

SharePoint : taxonomie : topLevelTermOf est l’inverse de la taxonomie SharePoint : hasTopLevelTerm

La syntaxe de définition est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**SharePoint-taxonomie : inTermSet**

Utilisez-le pour mapper un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) à un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). Un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ne peut exister que dans un seul [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint requiert cette propriété lors [de la définition d’un terme](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>Étiquettes requises

Votre organisation peut souhaiter effectuer une planification soignée avant de commencer à utiliser des métadonnées gérées. La planification que vous devez effectuer dépend de la façon dont votre taxonomie est formalisée. Elle dépend également de la proportion de contrôle que vous souhaitez imposer sur les métadonnées. À chaque niveau de la hiérarchie, vous devez configurer le lables requis pour un terme ou TermSet.

Un terme peut avoir une ou plusieurs étiquettes dans la langue par défaut, et zéro, une ou plusieurs étiquettes dans la langue non définie par défaut. Si le terme contient des étiquettes dans une langue, l’une des étiquettes doit être l’étiquette par défaut.

**SharePoint-taxonomie : defaultLabel**

Utilisez cette étiquette lexicale par défaut pour un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) qui est un paramètre obligatoire pour un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term). Utilisez pour représenter visuellement le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe de définition d’un defaultLabel est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

La defaultLabel contient deux parties : la chaîne et la balise de langue. La langue doit être l’une des langues de travail [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Le defaultLabel doit être unique pour tous les [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) du même [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset), au même niveau hiérarchique.

**SharePoint-taxonomie : termSetName**

Obtient et définit le nom de l’objet TermSet actuel.

Cette étiquette lexicale pour un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset), dans une langue de travail [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Il s’agit d’un paramètre obligatoire pour un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). Permet de représenter visuellement un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset).

La syntaxe de définition d’un termSetName est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**SharePoint-taxonomie : propertyName**

Obtient et définit le nom de la propriété pour l’objet TermSet actuel.

Il s’agit de l’étiquette lexicale pour une taxonomie SharePoint : SharedCustomPropertyForTerm, SharePoint-taxonomique : LocalCustomPropertyForTerm et SharePoint-taxonomique : CustomPropertyForTermSet dans une langue de travail [termes](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termstore) .

La taxonomie SharePoint-taxonomique : propertyName est traitée comme la clé de CustomProperty.

La syntaxe de définition d’un propetyName est la suivante :

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Étiquettes facultatives

Vous pouvez également ajouter des étiquettes facultatives à votre taxonomie.

**SharePoint-taxonomie : otherLabel**

Il s’agit de l’étiquette lexicale de remplacement pour un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term). 

La syntaxe de définition d’une otherLabel est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Relations sémantiques

Les taxonomies ont une relation associative hiérarchique et parfois un simple « terme apparenté », mais certains ont des relations de « sémantique » ou de création personnalisée. 

**SharePoint : taxonomie : parent**

Cela associe hiérarchiquement un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) à un autre [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term). Un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) peut être un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) de niveau supérieur d’un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset), mais si ce n’est pas le cas, il ne doit pas avoir de [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term)parent. 

La syntaxe de définition d’un parent est la suivante :

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Cela signifie que TermA1 a un terme parent. Inversement, cela signifie également que TermA1 est l’enfant de Terma. La relation parent-enfant est une relation inversible.

**SharePoint-taxonomie : enfant**

L’objet contient une ou plusieurs instances TermSet enfants, qui sont accessibles par le biais de la propriété TermSets. Cette classe fournit également des méthodes pour créer des objets TermSet enfants. Les autorisations permettant de modifier le terme enfant et les instances TermSet sont spécifiées dans le groupe. 

Cela associe hiérarchiquement un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) à un autre [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe de définition d’un enfant est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Cela signifie que Terma a un enfant TermA1. Inversement, cela signifie également que Terma est le parent de TermA1 Parent-Child Relationship est une relation inversible.

## <a name="documentation-notes"></a>Notes de documentation

Cette section traite de la taxonomie détaillée dans l’espace de noms Microsoft. SharePoint. taxonomique.

**SharePoint-taxonomie : description**

Il s’agit d’une explication détaillée de toute entité de vocabulaire de [taxonomie SharePoint](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy) . 

La syntaxe permettant d’ajouter une description est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Propriétés personnalisées

Obtient la collection d’objets Property personnalisés pour l’objet Term actuel à partir du dictionnaire en lecture seule.

Les propriétés personnalisées sont des paires clé-valeur qui peuvent être définies pour un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ou un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset), afin de mieux décrire le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ou un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint spécifie la clé de la propriété personnalisée avec l’aide de propertyName.

**SharePoint-taxonomie : CustomPropertyForTermSet**

La syntaxe de définition est la suivante :

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**SharePoint-taxonomie : SharedCustomPropertyForTerm**

Si la propriété personnalisée d’un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) doit être exécutée avec le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term), lorsque vous réutilisez le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ailleurs, vous devez le définir sous SharedCustomPropertyForTerm.

La syntaxe de définition est la suivante :

``` SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**SharePoint-taxonomie : LocalCustomPropertyForTerm**

Si la propriété personnalisée d’un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ne doit pas être exécutée avec le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term), lorsque vous réutilisez le [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ailleurs, vous devez le définir sous LocalCustomPropertyForTerm.

La syntaxe de définition est la suivante :

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Propriétés de données

À chaque niveau de la hiérarchie, vous pouvez configurer des propriétés de données spécifiques pour un terme ou TermSet.

**SharePoint-taxonomie : isAvailableForTagging**

Utilisez cette pour spécifier si un [terme](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.term) ou un [TermSet](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy.termset) est disponible dans les listes et les bibliothèques SharePoint.  

La syntaxe est la suivante :

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domaine et plage

Le tableau ci-dessous décrit le domaine et la plage de vocabulaire de taxonomie SharePoint.

|Prédicats/verbe|Signification|Domaine|Plage|
|:--------------|:------|:-----|:----|
inTermSet|Dans l’ensemble de termes|Term|Ensemble de termes|
inTermGroup|Dans le groupe de termes|TermSet|TermGroup|
topLevelTermOf|Est le terme de niveau supérieur de|Term|TermSet|
hasTopLevelTerm|Est un terme de niveau supérieur|Ensemble de termes|Term|
termSetName|L’ensemble de termes a le nom|Term|Littéral brut|
defaultLabel|Le terme a une étiquette par défaut|Term|Littéral brut|
otherLabel|Le terme a une autre étiquette|Term|Littéral brut|
propertyName|Possède une étiquette de propriété|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Boolean, String, Integer, Decimal, double|
|description|Comporte une description|Tous|Littéral brut|
|parent|A un parent|Term|Term|
|derniers|A un enfant|Term|Term|
|isAvailableForTagging|Est disponible pour le marquage|Terme, ensemble de termes|Boolean|
|SharedCustomPropertyForTerm|Possède une propriété personnalisée partagée|Term|Boolean, String, Integer, Decimal, double|
|LocalCustomPropertyForTerm|Possède une propriété personnalisée locale|Term|Boolean, String, Integer, Decimal, double|
|CustomPropertyForTermSet|Possède une propriété personnalisée|TermSet|Boolean, String, Integer, Decimal, double|

[SKOS](https://www.w3.org/TR/skos-primer/) les scénarios valides que la [taxonomie SharePoint](https://docs.microsoft.com/dotnet/api/microsoft.sharepoint.taxonomy) n’autorise pas :

- Redondance hiérarchique : un concept [SKOS](https://www.w3.org/TR/skos-primer/) peut être associé à plusieurs concepts plus larges en même temps, mais une taxonomie SharePoint : le terme ne peut avoir qu’une seule taxonomie SharePoint : le parent, ainsi que la dépendance cyclique, des termes ne sont pas non plus autorisés.
- Les termes orphelins ne sont pas autorisés dans la taxonomie SharePoint. Chaque taxonomie SharePoint-taxonomique : term doit disposer d’une taxonomie SharePoint : parent ou il doit s’agir de la taxonomie SharePoint : topLevelTermOf a TermSet.
- La taxonomie SharePoint ne prend pas en charge les relations associatives.
- La taxonomie SharePoint n’autorise que 2 types de relations hiérarchiques – SharePoint-taxonomie : parent et SharePoint-taxonomie : enfant. 
- Contrairement à [SKOS](https://www.w3.org/TR/skos-primer/) , la relation hiérarchique dans le vocabulaire de taxonomie SharePoint ne peut être établie qu’avec des termes appartenant à la même TermSet.

## <a name="see-also"></a>Voir aussi

[Importer un ensemble de termes à l’aide d’un format basé sur SKOS](import-term-set-skos.md)

