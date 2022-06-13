---
title: En savoir plus sur les types d’informations sensibles
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Cet article donne une vue d’ensemble des types d’informations sensibles et de la façon dont ils détectent les informations sensibles telles que la sécurité sociale, les numéros de carte de crédit ou les numéros de compte bancaire pour identifier les éléments sensibles
ms.openlocfilehash: d814bd413fc95a02bc35ab05a804c544d9b84b1e
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014231"
---
# <a name="learn-about-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

L’identification et la classification des éléments sensibles qui sont sous le contrôle de votre organisation est la première étape de la [discipline Information Protection](./information-protection.md).  Microsoft Purview offre trois façons d’identifier les éléments afin qu’ils puissent être classés :

- manuellement par les utilisateurs
- reconnaissance automatisée des modèles, comme les types d’informations sensibles
- [Machine Learning](classifier-learn-about.md)

Les types d’informations sensibles (SIT) sont des classifieurs basés sur des modèles. Ils détectent des informations sensibles telles que les numéros de sécurité sociale, de carte de crédit ou de compte bancaire pour identifier les éléments sensibles. Pour obtenir la liste complète de tous les SIT, consultez [les définitions d’entités des types d’informations](sensitive-information-type-entity-definitions.md) sensibles.

Microsoft fournit un grand nombre de SIT préconfigurés ou vous pouvez créer les vôtres.

## <a name="sensitive-information-types-are-used-in"></a>Les types d’informations sensibles sont utilisés dans

- [Stratégies de protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](retention.md)
- [Gestion des risques internes](insider-risk-management.md)
- [Conformité des communications](communication-compliance.md)
- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Catégories de types d’informations sensibles

### <a name="built-in-sensitive-information-types"></a>Types d’informations sensibles intégrés

Par défaut, ces SIT sont créés par Microsoft dans la console de conformité. Ces SIT ne peuvent pas être modifiés, mais ils peuvent être utilisés comme modèles et copiés pour créer des types d’informations sensibles personnalisés. Consultez les [définitions d’entité de type Informations sensibles](sensitive-information-type-entity-definitions.md) pour une liste complète de tous les SIT.

### <a name="named-entity-sensitive-information-types"></a>Types d’informations sensibles d’entité nommés

Les SIT d’entité nommée s’affichent également dans la console de conformité par défaut. Ils détectent les noms des personnes, les adresses physiques et les conditions médicales. Ils ne peuvent pas être modifiés ou copiés. Pour plus [d’informations, consultez l’article En savoir plus sur les entités nommées ](named-entities-learn.md#learn-about-named-entities) . Les SIT d’entité nommée sont de deux types :

**un-bundled**

Ces SIT d’entité nommées ont un focus plus étroit, comme un seul pays ou une seule classe de termes. Utilisez-les lorsque vous avez besoin d’une stratégie DLP avec une étendue de détection plus étroite. Voir, [Exemples de SIT d’entité nommée](named-entities-learn.md#examples-of-named-entity-sits).

**Livré**

Les SIT d’entité nommée groupées détectent toutes les correspondances possibles dans une classe, comme toutes les adresses physiques. Utilisez-les comme critères généraux dans vos stratégies DLP pour détecter les éléments sensibles. Voir, [Exemples de SIT d’entité nommée](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Types d’informations sensibles personnalisés

Si les types d’informations sensibles préconfigurés ne répondent pas à vos besoins, vous pouvez créer vos propres types d’informations sensibles personnalisés que vous définissez entièrement ou copier l’un des types intégrés et les modifier. Pour plus d’informations, voir [Créer un type d’informations sensibles personnalisé dans le Centre de conformité](create-a-custom-sensitive-information-type.md) .

### <a name="exact-data-match-sensitive-information-types"></a>Les données exactes correspondent aux types d’informations sensibles

Tous les SIT basés sur EDM sont créés à partir de zéro. Vous les utilisez pour détecter les éléments qui ont des valeurs exactes que vous définissez dans une base de données d’informations sensibles. Pour plus [d’informations, consultez l’article En savoir plus sur les types d’informations sensibles basés sur des correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) .

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Parties fondamentales d’un type d’informations sensibles

Chaque entité de type d’informations sensibles est définie par les champs suivants :

- nom : comment le type d’informations sensibles est référencé
- description : décrit ce que recherche le type d’informations sensibles
- modèle : un modèle définit ce qu’un type d’informations sensibles détecte. Il se compose des composants suivants.
  - Élément principal : élément principal recherché par le type d’informations sensibles. Il peut s’agir d’une **expression régulière** avec ou sans validation de somme de contrôle, **d’une liste de mots clés**, d’un **dictionnaire de mots clés** ou d’une **fonction**.
  - Élément de soutien : éléments qui servent de preuves qui contribuent à accroître la confiance de la correspondance. Par exemple, le mot clé « SSN » à proximité d’un numéro SSN. Il peut s’agir d’une expression régulière avec ou sans validation de somme de contrôle, liste de mots clés, dictionnaire de mots clés.
  - Niveau de confiance : les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves à l’appui détectées avec l’élément principal. Plus un élément contient de preuves à l’appui, plus la confiance qu’un élément correspondant contient contient les informations sensibles que vous recherchez.
  - Proximité : nombre de caractères entre l’élément principal et l’élément de prise en charge.

![Diagramme des preuves corroborantes et de la fenêtre de proximité.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

Découvrez-en plus sur les niveaux de confiance dans cette courte vidéo.

 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]

### <a name="example-sensitive-information-type"></a>Exemple de type d’informations sensibles

#### <a name="argentina-national-identity-dni-number"></a>Numéro d’identité nationale argentine (DNI)

### <a name="format"></a>Format

Huit chiffres séparés par des points

### <a name="pattern"></a>Modèle

Huit chiffres :

- deux chiffres
- un point
- trois chiffres
- un point
- trois chiffres

### <a name="checksum"></a>Somme de contrôle

Non

### <a name="definition"></a>Définition

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, à proximité de 300 caractères :

- L’expression régulière Regex_argentina_national_id trouve un contenu qui correspond au modèle.
- Un mot clé figurant dans la liste Keyword_argentina_national_id est trouvé.

```xml
<!-- Argentina National Identity (DNI) Number -->
<Entity id="eefbb00e-8282-433c-8620-8f1da3bffdb2" recommendedConfidence="75" patternsProximity="300">
   <Pattern confidenceLevel="75">
      <IdMatch idRef="Regex_argentina_national_id"/>
      <Match idRef="Keyword_argentina_national_id"/>
  </Pattern>
</Entity>
```

### <a name="keywords"></a>Mots-clés

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity number
- Identité
- Carte d’identité nationale d’identification
- DNI
- Registre national des personnes de la carte réseau
- Documento Nacional de Identidad
- Registro Nacional de las Personas
- Identidad
- Identificación

### <a name="more-on-confidence-levels"></a>En savoir plus sur les niveaux de confiance

Dans une définition d’entité de type d’informations sensibles, le **niveau de confiance** reflète la quantité de preuves de prise en charge détectées en plus de l’élément principal. Plus un élément contient de preuves à l’appui, plus la confiance qu’un élément correspondant contient contient les informations sensibles que vous recherchez. Par exemple, les correspondances avec un niveau de confiance élevé contiendront des preuves plus justifiantes à proximité de l’élément principal, tandis que les correspondances avec un niveau de confiance faible contiendraient peu ou pas de preuves à l’appui à proximité étroite.

Un niveau de confiance élevé retourne le moins de faux positifs, mais peut entraîner plus de faux négatifs. Les niveaux de confiance faibles ou moyens retournent plus de faux positifs, mais peu ou pas de faux négatifs.

- **faible confiance** : les éléments mis en correspondance contiennent le moins de faux négatifs, mais le plus grand nombre de faux positifs. Une confiance faible retourne toutes les correspondances de confiance faibles, moyennes et élevées. Le niveau de confiance faible a une valeur de 65.
- **confiance moyenne** : les éléments mis en correspondance contiennent une quantité moyenne de faux positifs et de faux négatifs. La confiance moyenne retourne toutes les correspondances de confiance moyennes et élevées. Le niveau de confiance moyen a une valeur de 75.
- **confiance élevée** : les éléments mis en correspondance contiennent le moins de faux positifs, mais le plus grand nombre de faux négatifs. Une confiance élevée retourne uniquement des correspondances de confiance élevées et a une valeur de 85.

Vous devez utiliser des modèles de niveau de confiance élevés avec des nombres faibles, par exemple cinq à dix, et des modèles de confiance faible avec des nombres plus élevés, par exemple 20 ou plus.

> [!NOTE]
> Si vous avez des stratégies existantes ou des types d’informations sensibles personnalisés (SIT) définis à l’aide de niveaux de confiance basés sur les nombres (également connus sous le nom de précision), ils sont automatiquement mappés aux trois niveaux de confiance discrets ; confiance faible, confiance moyenne et confiance élevée dans l’interface utilisateur security @ Compliance Center.
>
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance compris entre 76 et 100 seront mappées à une confiance élevée.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance compris entre 66 et 75 seront mappées à une confiance moyenne.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance inférieurs ou égaux à 65 seront mappées à une faible confiance.

## <a name="creating-custom-sensitive-information-types"></a>Création de types d’informations sensibles personnalisés

Vous pouvez choisir parmi plusieurs options pour créer des types d’informations sensibles personnalisés dans le Centre de conformité.

- **Utilisez l’interface utilisateur** : vous pouvez configurer un type d’informations sensibles personnalisé à l’aide de l’interface utilisateur du Centre de conformité. Cette méthode vous permet d’utiliser des expressions régulières, des mots clés et des dictionnaires de mots clés. Pour en savoir plus, voir [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md).

- **Utiliser EDM** : vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de la classification EDM (Exact Data Match). Cette méthode vous permet de créer un type d’informations sensibles dynamique à l’aide d’une base de données sécurisée que vous pouvez actualiser régulièrement. Consultez [En savoir plus sur les types d’informations sensibles basés sur des correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Utiliser PowerShell** : vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de PowerShell. Bien que cette méthode soit plus complexe que celle de l’interface utilisateur, elle offre davantage d’options de configuration. Consultez [Créer un type d’informations sensibles personnalisé dans Security & Compliance PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Des niveaux de confiance améliorés sont disponibles pour une utilisation immédiate dans les services de protection contre la perte de données Microsoft Purview, la protection des informations, la conformité des communications, la gestion du cycle de vie des données et la gestion des enregistrements.
> Information Protection prend désormais en charge les langues de jeu de caractères sur deux octets pour :
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
> Cette prise en charge est disponible pour les types d’informations sensibles. Pour plus d’informations, consultez la [prise en charge de la protection des informations pour les jeux de caractères doubles octets](mip-dbcs-relnotes.md) .

> [!TIP]
> Pour détecter les modèles contenant des caractères chinois/japonais et des caractères d’octet unique ou pour détecter les modèles contenant du chinois/le japonais et l’anglais, définissez deux variantes du mot clé ou de regex.
>
> - Par exemple, pour détecter un mot clé tel que « 机密的document », utilisez deux variantes du mot clé ; l’un avec un espace entre le texte japonais et anglais et l’autre sans espace entre le texte japonais et l’anglais. Par conséquent, les mots clés à ajouter dans le SIT doivent être « 机密的 document » et « 机密的document ». De la même façon, pour détecter une expression « 東京オリンピック2020 », deux variantes doivent être utilisées : « 東京オリンピック 2020 » et « 東京オリンピック2020 ».
>
> Avec les caractères chinois/japonais/double octets, si la liste des mots clés/expressions contient également des mots non chinois/japonais (comme l’anglais uniquement), vous devez créer deux dictionnaires/listes de mots clés. Un pour les mots clés contenant des caractères chinois/japonais/sur deux octets et un autre pour l’anglais uniquement.
>
> - Par exemple, si vous souhaitez créer un dictionnaire/liste de mots clés avec trois expressions « Hautement confidentiel », « 機密性が高い » et « 机密的document », vous devez créer deux listes de mots clés.
>     1. Extrêmement confidentiel
>     2. Document 機密性が高い, 机密的 et document 机密的
>
> Lorsque vous créez une regex en utilisant un trait d'union à double octet ou un point à double octet, assurez-vous d'échapper les deux caractères comme on le ferait pour un trait d'union ou un point dans une regex. Voici un exemple regex pour référence :
>
> `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Nous vous recommandons d’utiliser une correspondance de chaîne au lieu d’une correspondance de mot dans une liste de mots clés.

## <a name="for-further-information"></a>Pour plus d’informations

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Pour savoir comment utiliser des types d’informations sensibles pour se conformer aux réglementations sur la confidentialité des données, consultez [Déployer la protection des informations pour les réglementations de confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
