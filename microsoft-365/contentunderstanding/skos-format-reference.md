---
title: Référence de format SKOS pour la taxonomie SharePoint
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ms.localizationpriority: high
description: Référence de format SKOS pour la taxonomie SharePoint
ms.openlocfilehash: 95183b64d76a70f69d08cd5a3c9dcf76f4e83bce
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60747655"
---
# <a name="skos-format-reference-for-sharepoint-taxonomy"></a>Référence de format SKOS pour la taxonomie SharePoint

Cet article comprend le vocabulaire RDF utilisé pour représenter la [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) et est basé sur [SKOS](https://www.w3.org/TR/skos-primer/). Pour la sérialisation de cette syntaxe RDF, utilisez RDF [TURTLE](https://www.w3.org/TR/turtle/).

Le tableau suivant affiche les équivalents [SKOS](https://www.w3.org/TR/skos-primer/) pour le vocabulaire de [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy). SharePoint ne prend pas en charge les valeurs [SKOS](https://www.w3.org/TR/skos-primer/) qui n’ont pas d’équivalent de taxonomie SharePoint.

|Taxonomie SharePoint|Équivalent SKOS|
|:-----------------|:--------------|
|sharepoint-taxonomy:Term|skos:Concept|
|sharepoint-taxonomy:TermSet|skos:ConceptScheme|
|sharepoint-taxonomy:inTermSet|skos:inScheme|
|sharepoint-taxonomy:hasTopLevelTerm|skos:hasTopConcept|
|sharepoint-taxonomy:topLevelTermOf|skos:topConceptOf|
|sharepoint-taxonomy:defaultLabel|skos:prefLabel|
|sharepoint-taxonomy:termSetName|skos:prefLabel|
|sharepoint-taxonomy:propertyName|skos:prefLabel|
|sharepoint-taxonomy:otherLabel|skos:altLabel|
|sharepoint-taxonomy:description|skos:definition|
|sharepoint-taxonomy:parent|skos:broader|
|sharepoint-taxonomy:child|skos:narrower|

Le tableau suivant affiche les entités du vocabulaire de taxonomie SharePoint dérivé de [OWL](https://www.w3.org/TR/owl2-primer/).

|Vocabulaire de taxonomie SharePoint|Dérivé de OWL|
|:-----------------------------|:----------------------|
|sharepoint-taxonomy:isAvailableForTagging|owl:datatypeproperty|
|sharepoint-taxonomy:SharedCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taxonomy:LocalCustomPropertyForTerm|owl:ObjectProperty|
|sharepoint-taxonomy:CustomPropertyForTermSet|owl:ObjectProperty|

## <a name="sharepoint-taxonomy-vocabulary"></a>Vocabulaire de taxonomie SharePoint

Une taxonomie est un système de classification formel. Une taxonomie regroupe les mots, les étiquettes et les termes qui décrivent quelque chose, puis classe ces groupes dans une hiérarchie.

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

- sharepoint-taxonomy:defaultLabel
- sharepoint-taxonomy:inTermSet

Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) peut :

- être lié de manière hiérarchique à un autre [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à condition que les deux [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) appartiennent au même [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
- avoir plusieurs [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) enfants, mais un seul [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent.
- ne pas avoir de [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent défini, s’il s’agit d’un topLevelTermOf d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).
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

- sharepoint-taxonomy:termSetName

Dans le cas où le termSetName fourni n’est pas unique dans le [TermGroup](/dotnet/api/microsoft.sharepoint.taxonomy.group), SharePoint ajoute un numéro à la fin du nom pour maintenir l’unicité du ou des termSetName.

**sharepoint-taxonomy:hasTopLevelTerm**

SharePoint utilise cette propriété pour mapper le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) supérieur dans le [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), qui est le point d’entrée de la hiérarchie des [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) dans un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Il s’agit d’une relation inverse à sharepoint-taxonomy:topLevelTermOf.

La syntaxe pour définir ceci est :

```SKOS
ex:TermSetA    sharepoint-taxonomy:hasTopLevelTerm    ex:TermA.
```

> [!NOTE]
> Vous ne pouvez pas définir le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) supérieur d’un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent.

**sharepoint-taxonomy:topLevelTermOf**

Sharepoint-taxonomy:topLevelTermOf est l’inverse de sharepoint-taxonomy:hasTopLevelTerm

La syntaxe pour définir ceci est :

```SKOS
ex:TermA    sharepoint-taxonomy:topLevelTermOf    ex:TermSetA.
```

**sharepoint-taxonomy:inTermSet**

Utilisez ceci pour mapper un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ne peut exister que dans un seul [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). SharePoint requiert cette propriété lors de la [définition d’un terme](https://github.com/MicrosoftDocs/microsoft-365-docs-pr/blob/3a3cd54dd076b18bdff1d43b3e342897f8704c23/microsoft-365/contentunderstanding/skos-format-reference.md#term).

## <a name="required-labels"></a>Étiquettes requises

Votre organisation peut souhaiter effectuer une planification minutieuse avant de commencer à utiliser des métadonnées gérées. La quantité de planification que vous devez effectuer dépend de la formalité de votre taxonomie. Cela dépend également du degré de contrôle que vous souhaitez imposer aux métadonnées. À chaque niveau de la hiérarchie, vous devez configurer les étiquettes requises pour un Terme ou un TermSet.

Un Terme peut avoir une ou plusieurs étiquettes dans la langue par défaut et zéro ou plusieurs étiquettes dans la langue autre que celle par défaut. Si le terme a des étiquettes dans une langue, l’une des étiquettes doit être l’étiquette par défaut.

**sharepoint-taxonomy:defaultLabel**

Utilisez cette étiquette lexicale par défaut pour un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) qui est un paramètre obligatoire pour un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term). Utilisez pour représenter visuellement le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term).

La syntaxe pour définir un defaultLabel est :

```SKOS
ex:TermA    sharepoint-taxonomy:defaultLabel    “Term A”@en-us.
```

Le defaultLabel contient deux parties : la chaîne et la balise de langue. La langue doit être l’une des langues de travail du [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Le defaultLabel doit être unique pour tous les [Termes](/dotnet/api/microsoft.sharepoint.taxonomy.term) du même [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), au même niveau hiérarchique.

**sharepoint-taxonomy:termSetName**

Obtient et définit le nom de l’objet TermSet actuel.

Il s’agit de l’étiquette lexicale d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), dans une langue de travail [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore). Il s’agit d’un paramètre obligatoire pour un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset). Utilisez-la pour représenter visuellement un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset).

La syntaxe pour définir un termSetName est :

```SKOS
ex:TermA    sharepoint-taxonomy:TermSetName    “Term Set A”@en-us.
```

**sharepoint-taxonomy:propertyName**

Obtient et définit le nom de propriété de l’objet TermSet actuel.

Il s’agit d’une étiquette lexicale pour sharepoint-taxonomy:SharedCustomPropertyForTerm, sharepoint-taxonomy:LocalCustomPropertyForTerm et sharepoint-taxonomy:CustomPropertyForTermSet dans une langue de travail [TermStore](/dotnet/api/microsoft.sharepoint.taxonomy.termstore).

Le sharepoint-taxonomy:propertyName est traité comme la clé de CustomProperty.

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

Ceci relie hiérarchiquement un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) à un autre [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term). Un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) peut être un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) supérieur d’un [TermSet](/dotnet/api/microsoft.sharepoint.taxonomy.termset), mais si ce n’est pas le cas, il doit avoir un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) parent.

La syntaxe pour définir un parent est :

```SKOS
ex:TermA1    sharepoint-taxonomy:parent    ex:TermA.
```

Cela signifie que TermA est le parent et TermA est l’enfant.

**sharepoint-taxonomy:child**

L’objet contient une ou plusieurs instances TermSet enfants, accessibles via la propriété TermSets. Cette classe fournit également des méthodes pour créer de nouveaux objets TermSet enfants. Les autorisations de modification des instances de Term et de TermSet enfants sont spécifiées sur le groupe.

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

Si la propriété personnalisée d’un [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) n’a pas besoin d’être transportée avec le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term), lorsque vous réutilisez le [Terme](/dotnet/api/microsoft.sharepoint.taxonomy.term) ailleurs, vous devez le définir sous LocalCustomPropertyForTerm.

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

Scénarios [SKOS](https://www.w3.org/TR/skos-primer/) valides que la [taxonomie SharePoint](/dotnet/api/microsoft.sharepoint.taxonomy) n’autorise pas :

- Redondance hiérarchique : un concept [SKOS](https://www.w3.org/TR/skos-primer/) peut être attaché à plusieurs concepts plus larges en même temps, mais sharepoint-taxonomy:Term ne peut avoir qu’un seul sharepoint-taxonomy:parent, donc la dépendance cyclique des Termes n’est pas non plus autorisé.
- Les termes orphelins ne sont pas autorisés dans la taxonomie SharePoint. Chaque sharepoint-taxonomy:Term doit soit avoir un sharepoint-taxonomy:parent, soit être le sharepoint-taxonomy:topLevelTermOf d'un TermSet.
- La taxonomie SharePoint ne prend pas en charge les relations associatives.
- La taxonomie SharePoint n’autorise que 2 types de relations hiérarchiques : sharepoint-taxonomy:parent et sharepoint-Taxonomy:child.
- Contrairement à [SKOS](https://www.w3.org/TR/skos-primer/), la relation hiérarchique dans le vocabulaire de la taxonomie SharePoint ne peut être établie qu’avec des Termes dans le même TermSet.

## <a name="see-also"></a>Voir aussi

[Importer un ensemble de termes avec un format basé sur SKOS](import-term-set-skos.md)