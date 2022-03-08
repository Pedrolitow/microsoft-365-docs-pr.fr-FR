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
description: Cet article donne une vue d’ensemble des types d’informations sensibles et de la façon dont ils détectent les informations sensibles telles que la sécurité sociale, la carte bancaire ou les numéros de compte bancaire pour identifier les éléments sensibles
ms.openlocfilehash: fbe23bbb6c639857367cc0b8467f6084e9116af1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318842"
---
# <a name="learn-about-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles

L’identification et la classification des éléments sensibles qui sont sous le contrôle de votre organisation est la première étape de la [protection des informations](./information-protection.md).  Microsoft 365 propose trois façons d’identifier les éléments afin qu’ils soient classés :

- manuellement par les utilisateurs
- reconnaissance automatique des modèles, comme les types d’informations sensibles
- [apprentissage automatique](classifier-learn-about.md)

Les types d’informations sensibles (SIT) sont des classifieurs basés sur des modèles. Ils détectent les informations sensibles telles que la sécurité sociale, la carte bancaire ou les numéros de compte bancaire pour identifier les éléments sensibles. Pour obtenir la liste complète de tous les sits, voir définitions d’entité des [types d’informations](sensitive-information-type-entity-definitions.md) sensibles.

Microsoft fournit un grand nombre de sits pré-configurés ou vous pouvez créer les vôtres.

## <a name="sensitive-information-types-are-used-in"></a>Les types d’informations sensibles sont utilisés dans

- [Stratégies de protection contre la perte de données](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](retention.md)
- [Gestion des risques internes](insider-risk-management.md)
- [Conformité des communications](communication-compliance.md)
- [Stratégies de étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Priva](/privacy/priva)

## <a name="categories-of-sensitive-information-types"></a>Catégories de types d’informations sensibles

### <a name="built-in-sensitive-information-types"></a>Types d’informations sensibles intégrés

Ces sits sont créées par Microsoft s’affiche dans la console de conformité par défaut. Ces sits ne peuvent pas être modifiés, mais ils peuvent être utilisés comme modèles et copiés pour créer des types d’informations sensibles personnalisés. Voir, [Définitions d’entités de type informations sensibles](sensitive-information-type-entity-definitions.md) pour une liste complète de tous les sits.

### <a name="named-entity-sensitive-information-types"></a>Types d’informations sensibles d’entité nommée

Les sits d’entité nommée s’affiche également dans la console de conformité par défaut. Ils détectent les noms de personnes, les adresses physiques et les conditions médicales. Elles ne peuvent pas être modifiées ou copiées. Pour plus [d’informations, voir en savoir plus sur](named-entities-learn.md#learn-about-named-entities-preview) les entités nommées (prévisualisation). Les sits d’entité nommée sont de deux types :

**non groupé**

Ces sits d’entité nommée ont un focus plus étroit, comme un pays unique ou une seule classe de termes. Utilisez-les lorsque vous avez besoin d’une stratégie DLP avec une portée de détection plus étroite. Voir, [Exemples de SIT d’entité nommée](named-entities-learn.md#examples-of-named-entity-sits).

**bundled**

Les sits d’entité nommée regroupées détectent toutes les correspondances possibles dans une classe, comme toutes les adresses physiques. Utilisez-les comme critères généraux dans vos stratégies DLP pour détecter les éléments sensibles. Voir, [Exemples de SIT d’entité nommée](named-entities-learn.md#examples-of-named-entity-sits).

### <a name="custom-sensitive-information-types"></a>Types d’informations sensibles personnalisés

Si les types d’informations sensibles pré-configurés ne répondent pas à vos besoins, vous pouvez créer vos propres types d’informations sensibles personnalisés que vous définissez entièrement ou vous pouvez copier l’un des types intégrés et les modifier. Pour plus [d’informations, voir Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md) dans le Centre de conformité.

### <a name="exact-data-match-sensitive-information-types"></a>Les données exactes correspondent aux types d’informations sensibles

Tous les sits basés sur EDM sont créés à partir de zéro. Vous les utilisez pour détecter les éléments qui ont des valeurs exactes que vous définissez dans une base de données d’informations sensibles. Pour plus d’informations, voir les types d’informations sensibles basés sur les [correspondances](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) de données exactes.

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Parties fondamentales d’un type d’informations sensibles

Chaque entité de type d’informations sensibles est définie par les champs ci-après :

- name: how the sensitive information type is referred to
- description : décrit ce que le type d’informations sensibles recherche
- modèle : un modèle définit ce qu’un type d’informations sensibles détecte. Il se compose des composants suivants.
    - Élément principal : élément principal que le type d’informations sensibles recherche. Il peut s’agit **d’une expression** régulière avec ou sans validation de la liste de contrôle, d’une liste de mots **clés,** d’un dictionnaire de mots clés ou d’une **fonction**.
    - Élément de prise en charge : éléments qui agissent en tant que preuves justificatives qui contribuent à augmenter la confiance de la correspondance. Par exemple, le mot clé « SSN » à proximité d’un numéro SSN. Il peut s’agit d’une expression régulière avec ou sans validation de la liste de contrôle, d’une liste de mots clés, d’un dictionnaire de mots clés.
    - Niveau de confiance : les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves justificatives détectées avec l’élément principal. Plus la preuve justificative qu’un élément contient est importante, plus la confiance qu’un élément correspond contient les informations sensibles que vous recherchez.
    - Proximité : nombre de caractères entre l’élément principal et l’élément de prise en charge.

![Diagramme de preuve corroborante et fenêtre de proximité.](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

En savoir plus sur les niveaux de confiance dans cette courte vidéo.


 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]  



### <a name="example-sensitive-information-type"></a>Exemple de type d’informations sensibles


#### <a name="argentina-national-identity-dni-number"></a>Numéro d’identité nationale (DNI) argentine

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

Une stratégie DLP a une confiance moyenne qu’elle a détecté ce type d’informations sensibles si, dans une proximité de 300 caractères :
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

### <a name="keywords"></a>Mots clés

#### <a name="keyword_argentina_national_id"></a>Keyword_argentina_national_id

- Argentina National Identity number 
- Identité 
- Carte d’identité nationale d’identification 
- DNI 
- Registre national des personnes de la NIC 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 

### <a name="more-on-confidence-levels"></a>Plus d’informations sur les niveaux de confiance

Dans une définition d’entité de type d’informations sensibles **, le** niveau de confiance reflète la quantité de preuves justificatives détectées en plus de l’élément principal. Plus la preuve justificative qu’un élément contient est importante, plus la confiance qu’un élément correspond contient les informations sensibles que vous recherchez. Par exemple, les correspondances avec un niveau de confiance élevé contiennent plus de preuves justificatives à proximité de l’élément principal, tandis que les correspondances avec un niveau de confiance faible contiennent peu ou pas de preuves justificatives à proximité immédiate. 

Un niveau de confiance élevé renvoie le moins de faux positifs, mais peut entraîner davantage de faux négatifs. Les niveaux de confiance faibles ou moyens renvoient plus de faux positifs, mais peu à zéro faux négatifs.

- **faible niveau de confiance** : les éléments qui correspondent contiennent le moins de faux négatifs, mais le plus de faux positifs. Une confiance faible renvoie toutes les correspondances de confiance faible, moyenne et élevée. Le niveau de confiance faible a une valeur de 65.
- **confiance moyenne** : les éléments qui correspondent contiennent une quantité moyenne de faux positifs et de faux négatifs. Une confiance moyenne renvoie toutes les correspondances de confiance moyenne et élevée. Le niveau de confiance moyen a une valeur de 75.
- **niveau de confiance élevé** : les éléments qui correspondent contiennent le moins de faux positifs, mais le plus de faux négatifs. Un niveau de confiance élevé renvoie uniquement des correspondances à haut niveau de confiance et a une valeur de 85.  

Vous devez utiliser des modèles de niveau de confiance élevé avec un nombre faible, par ex. 5 à 10, et des modèles de confiance faible avec des nombres plus élevés, par ex. 20 ou plus.

> [!NOTE]
> Si vous avez des stratégies existantes ou des types d’informations sensibles personnalisés (SIT) définis à l’aide de niveaux de confiance basés sur le nombre (également défini comme précision), ils seront automatiquement mappés aux trois niveaux de confiance discrets ; confiance faible, confiance moyenne et confiance élevée, dans l’interface utilisateur du Centre de sécurité @ conformité.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance entre 76 et 100 seront mappées à un niveau de confiance élevé. 
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance entre 66 et 75 seront mappées à un niveau de confiance moyen.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance inférieurs ou égaux à 65 seront mappées à un niveau de confiance faible. 

## <a name="creating-custom-sensitive-information-types"></a>Création de types d’informations sensibles personnalisés

Vous pouvez choisir parmi plusieurs options pour créer des types d’informations sensibles personnalisés dans le Centre de conformité.

- **Utilisez l’interface utilisateur** : vous pouvez configurer un type d’informations sensibles personnalisé à l’aide de l’interface utilisateur du Centre de conformité. Cette méthode vous permet d’utiliser des expressions régulières, des mots clés et des dictionnaires de mots clés. Pour en savoir plus, voir [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md).

- **Utiliser EDM** : vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de la classification EDM (Exact Data Match). Cette méthode vous permet de créer un type d’informations sensibles dynamique à l’aide d’une base de données sécurisée que vous pouvez actualiser régulièrement. Voir [En savoir plus sur les types d’informations sensibles basés sur les correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

- **Utiliser PowerShell** : vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de PowerShell. Bien que cette méthode soit plus complexe que celle de l’interface utilisateur, elle offre davantage d’options de configuration. Voir [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md).

> [!NOTE]
> Des niveaux de confiance améliorés sont disponibles pour une utilisation immédiate dans la protection contre la perte de données pour les services Microsoft 365, les Protection des données Microsoft pour les services Microsoft 365, la conformité des communications, la gouvernance des informations et la gestion des enregistrements.
> Microsoft 365 Protection des informations prend désormais en charge les langues de jeu de caractères à doubles caractères pour :
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
> 
> Cette prise en charge est disponible pour les types d’informations sensibles. Pour plus d’informations, voir la prise en charge de la protection des informations pour les [jeux de caractères à doubles caractères](mip-dbcs-relnotes.md) .

> [!TIP]
> Pour détecter les modèles contenant des caractères chinois/japonais et des caractères d’octet unique ou pour détecter les modèles contenant du chinois/le japonais et l’anglais, définissez deux variantes du mot clé ou de regex.
> - Par exemple, pour détecter un mot clé tel que « 机密的document », utilisez deux variantes du mot clé ; l’un avec un espace entre le texte japonais et anglais et l’autre sans espace entre le texte japonais et l’anglais. Par conséquent, les mots clés à ajouter dans le SIT doivent être « 机密的 document » et « 机密的document ». De la même façon, pour détecter une expression « 東京オリンピック2020 », deux variantes doivent être utilisées : « 東京オリンピック 2020 » et « 東京オリンピック2020 ».
> 
> En plus des caractères chinois/japonais/sur deux caractères d’byte, si la liste des mots clés/expressions contient également des mots non chinois/japonais (comme l’anglais uniquement), vous devez créer deux dictionnaires/listes de mots clés. Un pour les mots clés contenant des caractères chinois/japonais/sur deux octets et un autre pour l’anglais uniquement. 
> - Par exemple, si vous souhaitez créer un dictionnaire/liste de mots clés avec trois phrases « Hautement confidentiel », « 機密 « 機密sso » et « 机密sydocument », vous devez créer deux listes de mots clés. 
>     1. Extrêmement confidentiel
>     2. Document 機密性が高い, 机密的 et document 机密的
> 
> Lorsque vous créez une regex en utilisant un trait d'union à double octet ou un point à double octet, assurez-vous d'échapper les deux caractères comme on le ferait pour un trait d'union ou un point dans une regex. Voici un exemple regex pour référence :
>    - (?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}
>
> Nous vous recommandons d’utiliser une correspondance de chaîne au lieu d’une correspondance de mot dans une liste de mots clés.

## <a name="for-further-information"></a>Pour plus d’informations
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [Créer un type d’informations sensibles personnalisé dans PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

Pour découvrir comment utiliser des types d’informations sensibles pour se conformer aux réglementations en matière de confidentialité des données, voir [Deploy information protection for data privacy regulations with Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->
