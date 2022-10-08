---
title: Référence de format SKOS pour la taxonomie SharePoint
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
description: Référence de format SKOS pour la taxonomie SharePoint
ms.openlocfilehash: 0c40109f11d904db399effc874c24d3efd776a39
ms.sourcegitcommit: cbb9a89499d42f4a029e18780bee408946e1671d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68026049"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Référence de format SKOS pour la taxonomie SharePoint

Cet article comprend le vocabulaire RDF utilisé pour représenter la [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) et est basé sur [SKOS](https://www.w3.org/TR/skos-primer/). Pour la sérialisation de cette syntaxe RDF, utilisez RDF [TURTLE](https://www.w3.org/TR/turtle/).

Le tableau suivant affiche les équivalents [SKOS](https://www.w3.org/TR/skos-primer/) pour le vocabulaire de [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint ne prend pas en charge les valeurs [SKOS](https://www.w3.org/TR/skos-primer/) qui n’ont pas d’équivalent de taxonomie SharePoint.

|Taxonomie SharePoint|Équivalent SKOS|
|:-----------------|:--------------|
|sharepoint-taxonomy: Term|skos: Concept|
|sharepoint-taxonomy: TermSet|skos: ConceptScheme|
|sharepoint-taxonomy: inTermSet|skos: inScheme|
|sharepoint-taxonomy: hasTopLevelTerm|skos: hasTopConcept|
|sharepoint-taxonomy: topLevelTermOf|skos: topConceptOf|
|sharepoint-taxonomy: defaultLabel|skos: prefLabel|
|sharepoint-taxonomy: termSetName|skos: prefLabel|
|sharepoint-taxonomy: propertyName|skos: prefLabel|
|sharepoint-taxonomy: otherLabel|skos: altLabel|
|sharepoint-taxonomy: description|skos : définition|
|sharepoint-taxonomy: parent|skos: plus large|
|sharepoint-taxonomy: child|skos: plus étroit|

Le tableau suivant affiche les entités du vocabulaire de taxonomie SharePoint dérivé de [OWL](https://www.w3.org/TR/owl2-primer/).

|Vocabulaire de taxonomie SharePoint|Dérivé de OWL|
|:-----------------------------|:----------------------|
|sharepoint-taxonomy: isAvailableForTagging|hibou : datatypeproperty|
|sharepoint-taxonomy: SharedCustomPropertyForTerm|hibou: ObjectProperty|
|sharepoint-taxonomy: LocalCustomPropertyForTerm|hibou: ObjectProperty|
|sharepoint-taxonomy: CustomPropertyForTermSet|hibou: ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>Vocabulaire de taxonomie SharePoint

A taxonomy is a formal classification system. A taxonomy groups the words, labels, and terms that describe something, and then arranges the groups into a hierarchy.

**sharepoint-taxonomy:Term**

Représente un Terme ou un Mot-clé dans une hiérarchie de métadonnées gérées.

Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) est l’unité atomique d’un [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) SharePoint. Chaque [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) appartient à un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) qui appartient à un [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group).

La syntaxe pour définir un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) est la suivante :

```SKOS
ex:TermA    a    sharepoint-taxonomy:Term;
    sharepoint-taxonomy:inTermSet    ex:TermSetA;
    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA;
    sharepoint-taxonomy:child    ex:TermA1;
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharePoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) se trouve obligatoirement dans un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). DefaultLabel est le nom du [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) tel qu’il apparaît dans la représentation visuelle. Les champs obligatoires pour définir un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) incluent :

- sharepoint-taxonomy: defaultLabel
- sharepoint-taxonomy: inTermSet

Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) peut :

- être lié de manière hiérarchique à un autre [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à condition que les deux [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) appartiennent au même [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- avoir plusieurs [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) enfants, mais un seul [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent.
- Aucun [terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent n’est défini, s’il s’agit d’un topLevelTermOf d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- avoir un defaultLabel par langue de travail [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore).
- ne pas exister s’il ne contient ni un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent, ni le topLevelTermOf d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- avoir seulement un defaultLabel unique dans le même niveau hiérarchique.

**sharepoint-taxonomy:TermSet**

Représente un ensemble hiérarchique ou plat d’objets Terme appelé « TermSet ».

Comme son nom l’indique, TermSet est un ensemble de [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term). Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) dans un [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) doit appartenir à un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Aucun [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ne peut exister indépendamment.

La syntaxe pour définir un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) est :

```SKOS
ex:TermSetA    a    sharepoint-taxonomy:TermSet;
    sharepoint-taxonomy:termSetName    “TermSet A";
    sharepoint-taxonomy:isAvailableForTagging    “true”^^xsd:Boolean;
    sharepoint-taxonomy:hasTopLevelTerm    Ex:Term A.
```

Les [TermSets](/dotnet/api/microsoft.sharepoint.taxonomy.termset) sont regroupés de façon logique dans les [TermGroups](/dotnet/api/microsoft.sharepoint.taxonomy.group). Le champ obligatoire pour définir un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) est :

- sharepoint-taxonomy: termSetName

Si le termSetName fourni n’est pas unique dans [le TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), SharePoint ajoute un nombre à la fin du nom pour conserver l’unicité du ou des termSetName.

**sharepoint-taxonomy:hasTopLevelTerm**

SharePoint utilise cette propriété pour mapper le [terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) le plus haut dans le [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), qui est le point d’entrée à la hiérarchie des [termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) dans un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Il s’agit d’une relation inverse avec la taxonomie sharepoint : topLevelTermOf.

La syntaxe pour définir ceci est :

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Vous ne pouvez pas définir le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) supérieur d’un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent.

**sharepoint-taxonomy:topLevelTermOf**

Taxonomie Sharepoint : topLevelTermOf est l’inverse de sharepoint-taxonomie : hasTopLevelTerm

La syntaxe pour définir ceci est :

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taxonomy:inTermSet**

Utilisez ceci pour mapper un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ne peut exister que dans un seul [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint requiert cette propriété lors de la [définition d’un terme](#sharepoint-taxonomy-vocabulary).

## <a name="required-labels"></a>Étiquettes requises

Votre organisation peut souhaiter effectuer une planification minutieuse avant de commencer à utiliser des métadonnées gérées. La quantité de planification que vous devez effectuer dépend de la formalité de votre taxonomie. Cela dépend également du degré de contrôle que vous souhaitez imposer aux métadonnées. À chaque niveau de la hiérarchie, vous devez configurer les étiquettes requises pour un Terme ou un TermSet.

Un Terme peut avoir une ou plusieurs étiquettes dans la langue par défaut et zéro ou plusieurs étiquettes dans la langue autre que celle par défaut. Si le terme a des étiquettes dans une langue, l’une des étiquettes doit être l’étiquette par défaut.

**sharepoint-taxonomy:defaultLabel**

Use this default lexical label for a [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term) that is a required parameter for a [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term). Use to visually representing the [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe pour définir un defaultLabel est :

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Le defaultLabel contient deux parties : la chaîne et la balise de langue. La langue doit être l’une des langues de travail du [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Le defaultLabel doit être unique pour tous les [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) du même [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), au même niveau hiérarchique.

**sharepoint-taxonomy:termSetName**

Obtient et définit le nom de l’objet TermSet actuel.

Il s’agit de l’étiquette lexicale d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), dans un langage [de travail TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore) . Il s’agit d’un paramètre obligatoire pour un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Utilisez-la pour représenter visuellement un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

La syntaxe pour définir un termSetName est :

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taxonomy:propertyName**

Obtient et définit le nom de propriété de l’objet TermSet actuel.

Il s’agit d’une étiquette lexicale pour sharepoint-taxonomy:SharedCustomPropertyForTerm, sharepoint-taxonomy:LocalCustomPropertyForTerm et sharepoint-taxonomy:CustomPropertyForTermSet dans une langue de travail [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore).

La taxonomie sharepoint : propertyName est traitée comme la clé de CustomProperty.

La syntaxe pour définir un propetyName est :

```SKOS
ex:SharedCustomProperty1    sharepoint-taxonomy:propertyName    “Shared Custom Property Key 1”@en-us.
```

## <a name="optional-labels"></a>Étiquettes facultatives

Vous pouvez également ajouter des étiquettes facultatives à votre taxonomie.

**sharepoint-taxonomy:otherLabel**

Il s’agit de l’étiquette lexicale alternative pour un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe pour définir un otherLabel est :

```SKOS
ex:TermA    sharepoint-taxonomy:otherLabel    “Term A”@en-us.
```

## <a name="semantic-relationships"></a>Relations sémantiques

Les taxonomies ont une relation hiérarchique et parfois une simple relation associative de « terme apparenté », mais certaines ont des « relations sémantiques » ou des relations créées sur mesure.

**sharepoint-taxonomy:parent**

This hierarchically relates a [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term) to another [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term). A [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term) could be a top level [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term) of a [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), but in case it doesn’t it must have a parent [Term](/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe pour définir un parent est :

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Cela signifie que TermA est le parent et TermA est l’enfant.

**sharepoint-taxonomy:child**

L’objet contient une ou plusieurs instances TermSet enfants, accessibles via la propriété TermSets. Cette classe fournit également des méthodes pour créer de nouveaux objets TermSet enfants. Les autorisations de modification des instances Term et TermSet enfants sont spécifiées sur le groupe.

Cela relie hiérarchiquement un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à un autre [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe pour définir un enfant est :

```SKOS
ex:TermA    sharepoint-taxonomy:child    ex:TermA1.
```

Cela signifie que TermA est le parent et TermA est l’enfant.

## <a name="documentation-notes"></a>Notes de documentation

Cette section décrit la taxonomie détaillée dans Microsoft.SharePoint.Taxonomy Namespace.

**sharepoint-taxonomy:description**

Il s’agit d’une explication détaillée des entités de vocabulaire de la [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy).

La syntaxe pour ajouter une description est :

```SKOS
ex:TermA    sharepoint-taxonomy:description    “Term A is the top level term of TermSetA”@en-us.
```

## <a name="custom-properties"></a>Propriétés personnalisées

Obtient la collection d’objets de propriété personnalisés pour l’objet Term actuel à partir du dictionnaire en lecture seule.

Les propriétés personnalisées sont des paires de valeurs-clés qui peuvent être définies pour un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ou un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), pour approfondir la description du [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ou d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint spécifie la clé de la propriété personnalisée à l’aide de propertyName.

**sharepoint-taxonomy:CustomPropertyForTermSet**

La syntaxe pour définir ceci est :

```SKOS
ex:CustomProp1    rdf:type    sharepoint-taxonomy:CustomPropertyForTermSet;
    sharepoint-taxonomy:propertyName “Colour”.

ex:TermSetA    ex:CustomProp1    “Red”@en-us.
```

**sharepoint-taxonomy:SharedCustomPropertyForTerm**

Si la propriété personnalisée d’un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) doit être transportée avec le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term), lorsque vous réutilisez le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ailleurs, vous devez le définir sous SharedCustomPropertyForTerm.

La syntaxe pour définir ceci est :

```SKOS
ex:CustomProp2    rdf:type sharepoint-taxonomy:SharedCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “Length”.

ex:TermA    ex:CustomProp2    “5 cm”@en-us.
```
**sharepoint-taxonomy:LocalCustomPropertyForTerm**

Si la propriété personnalisée d’un [terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) n’a pas besoin d’être portée avec le [terme](/dotnet/api/microsoft.sharepoint.taxonomy.term), lorsque vous réutilisez le [terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ailleurs, vous devez la définir sous LocalCustomPropertyForTerm.

La syntaxe pour définir ceci est :

```SKOS
ex:CustomProp3    rdf:type sharepoint-taxonomy:LocalCustomPropertyForTerm;
    sharepoint-taxonomy:propertyName “width”.

ex:TermA    ex:CustomProp3    “5 cm”@en-us.
```

## <a name="data-properties"></a>Propriétés des données

À chaque niveau de la hiérarchie, vous pouvez configurer des propriétés de données spécifiques pour un Term ou TermSet.

**sharepoint-taxonomy:isAvailableForTagging**

Utilisez cette option pour spécifier si un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ou un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset) est disponible dans les listes et bibliothèques SharePoint.

La syntaxe pour cela est :

```SKOS
ex:TermA    sharepoint-taxonomy:isAvailableForTagging     "true"^^xsd:Boolean;
```

## <a name="domain-and-range"></a>Domaine et plage

Le tableau ci-dessous décrit le domaine et la plage du vocabulaire de taxonomie SharePoint.

|Prédicats/verbe|Signification|Domaine|Plage|
|:--------------|:------|:-----|:----|
inTermSet|Dans l’ensemble de termes|Term|Ensemble de Termes|
inTermGroup|Dans le groupe de termes|TermSet|TermGroup|
topLevelTermOf|Est le Terme de niveau supérieur de|Term|TermSet|
hasTopLevelTerm|A un terme de niveau supérieur|Ensemble de Termes|Term|
termSetName|L’ensemble de Termes a un nom|Term|Littéral simple|
defaultLabel|Le Terme a une étiquette par défaut|Term|Littéral simple|
otherLabel|Le Terme a une autre étiquette|Term|Littéral simple|
propertyName|A une étiquette de propriété|SharedCustomPropertyForTerm, LocalCustomPropertyForTerm, CustomPropertyForTermSet |Booléen, chaîne, entier, décimal, double|
|description|A une description|Tous|Littéral simple|
|parent|A un parent|Term|Term|
|enfant|a un enfant|Term|Term|
|isAvailableForTagging|Est disponible pour le marquage|Terme, Ensemble de Termes|Booléen|
|SharedCustomPropertyForTerm|A partagé une propriété personnalisée|Term|Booléen, chaîne, entier, décimal, double|
|LocalCustomPropertyForTerm|Possède une propriété personnalisée locale|Term|Booléen, chaîne, entier, décimal, double|
|CustomPropertyForTermSet|Possède une propriété personnalisée|TermSet|Booléen, chaîne, entier, décimal, double|

Scénarios valides [SKOS](https://www.w3.org/TR/skos-primer/) que la [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) n’autorise pas :

- Redondance hiérarchique : un concept [SKOS](https://www.w3.org/TR/skos-primer/) peut être attaché à plusieurs concepts plus larges en même temps, mais une taxonomie sharepoint :terme ne peut avoir qu’une seule taxonomie sharepoint :parent, donc dépendance cyclique, des termes ne sont pas non plus autorisés.
- Les termes orphelins ne sont pas autorisés dans la taxonomie SharePoint. Chaque taxonomie sharepoint : le terme doit avoir une taxonomie sharepoint : parent ou il doit s’agir de la taxonomie sharepoint : topLevelTermOf a TermSet.
- La taxonomie SharePoint ne prend pas en charge les relations associatives.
- La taxonomie SharePoint autorise uniquement deux types de relations hiérarchiques : sharepoint-taxonomie : parent et sharepoint-taxonomie : enfant.
- Contrairement à [SKOS](https://www.w3.org/TR/skos-primer/), la relation hiérarchique dans le vocabulaire de la taxonomie SharePoint ne peut être établie qu’avec des Termes dans le même TermSet.

## <a name="see-also"></a>Voir aussi

[Importer un ensemble de termes avec un format basé sur SKOS](import-term-set-skos.md)
