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
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: ''
ms.openlocfilehash: 01dd5feab17c68eed1da9d66c4310c50e90032c6
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114224"
---
# <a name="learn-about-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles

L'identification et la classification des éléments sensibles qui sont sous le contrôle de votre organisation est la première étape de la [protection des informations.](./information-protection.md)  Microsoft 365 propose trois façons d'identifier les éléments afin qu'ils soient classés :

- manuellement par les utilisateurs
- reconnaissance automatique des modèles, comme les types d'informations sensibles
- [apprentissage automatique](classifier-learn-about.md)

Les types d'informations sensibles sont des classifieurs basés sur des modèles. Ils détectent les informations sensibles telles que la sécurité sociale, la carte bancaire ou les numéros de compte bancaire pour identifier les éléments [sensibles. Voir Définitions d'entités des types d'informations sensibles](sensitive-information-type-entity-definitions.md)

## <a name="sensitive-information-types-are-used-in"></a>Les types d'informations sensibles sont utilisés dans

- [Stratégies de protection contre la perte de données](dlp-learn-about-dlp.md) 
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](retention.md)
- [Gestion des risques internes](insider-risk-management.md)
- [Conformité des communications](communication-compliance.md)
- [Stratégies de étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)

## <a name="fundamental-parts-of-a-sensitive-information-type"></a>Parties fondamentales d'un type d'informations sensibles

Chaque entité de type d'informations sensibles est définie par les champs ci-après :

- name: how the sensitive information type is referred to
- description : décrit ce que le type d'informations sensibles recherche
- modèle : un modèle définit ce qu'un type d'informations sensibles détecte. Il se compose des composants suivants :
    - Élément principal : élément principal que le type d'informations sensibles recherche. Il peut s'agit **d'une expression** régulière avec ou sans validation de la liste de contrôle, d'une liste de mots **clés,** d'un dictionnaire de mots clés **ou** d'une **fonction.**
    - Élément de prise en charge : éléments qui agissent en tant que preuves justificatives qui contribuent à augmenter la confiance de la correspondance. Par exemple, le mot clé « SSN » à proximité d'un numéro SSN. Il peut s'agit d'une expression régulière avec ou sans validation de la liste de contrôle, d'une liste de mots clés, d'un dictionnaire de mots clés.
    - Niveau de confiance : les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves justificatives détectées avec l'élément principal. Plus la preuve justificative qu'un élément contient est importante, plus la confiance qu'un élément correspond contient les informations sensibles que vous recherchez.
    - Proximité : nombre de caractères entre l'élément principal et l'élément de prise en charge

![Diagramme de la fenêtre de proximité et de preuves probantes](../media/dc68e38e-dfa1-45b8-b204-89c8ba121f96.png)

En savoir plus sur les niveaux de confiance dans cette vidéo


 > [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hx60]  

### <a name="example-sensitive-information-type"></a>Exemple de type d'informations sensibles


## <a name="argentina-national-identity-dni-number"></a>Numéro d'identité nationale (DNI) argentine

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

Une stratégie DLP a un niveau de confiance moyen qu'elle a détecté ce type d'informations sensibles si, dans une proximité de 300 caractères :
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
- Carte d'identité nationale d'identification 
- DNI 
- Registre national des personnes de la NIC 
- Documento Nacional de Identidad 
- Registro Nacional de las Personas 
- Identidad 
- Identificación 

### <a name="more-on-confidence-levels"></a>Plus d'informations sur les niveaux de confiance

Dans une définition d'entité  de type d'informations sensibles, le niveau de confiance reflète la quantité de preuves justificatives détectées en plus de l'élément principal. Plus la preuve justificative qu'un élément contient est importante, plus la confiance qu'un élément correspond contient les informations sensibles que vous recherchez. Par exemple, les correspondances avec un niveau de confiance élevé contiennent davantage de preuves justificatives à proximité immédiate de l'élément principal, tandis que les correspondances avec un niveau de confiance faible contiennent peu ou pas de preuves à proximité. 

Un niveau de confiance élevé renvoie le moins de faux positifs, mais peut entraîner davantage de faux négatifs. Les niveaux de confiance faibles ou moyens renvoient plus de faux positifs, mais peu à zéro faux négatifs.

- **faible niveau de** confiance : valeur 65, les éléments qui correspondent contiennent le moins de faux négatifs, mais le plus de faux positifs. Une confiance faible renvoie toutes les correspondances de confiance faible, moyenne et élevée.
- **confiance moyenne**: valeur de 75, les éléments qui correspondent contiennent une quantité moyenne de faux positifs et de faux négatifs. Une confiance moyenne renvoie toutes les correspondances de confiance moyenne et élevée.  
- **niveau de confiance** élevé : valeur 85, les éléments qui correspondent contiennent le moins de faux positifs, mais le plus de faux négatifs. Un niveau de confiance élevé renvoie uniquement des correspondances à haut niveau de confiance.  

Vous devez utiliser des modèles de niveau de confiance élevé avec de faibles nombres, par ex. 5 à 10, et des modèles de confiance faible avec des nombres plus élevés, par ex. 20 ou plus.

> [!NOTE]
> Si vous avez des stratégies existantes ou des types d'informations sensibles personnalisés (SIT) définis à l'aide de niveaux de confiance basés sur le nombre (également défini comme précision), ils seront automatiquement mappés aux trois niveaux de confiance discrets ; confiance faible, confiance moyenne et confiance élevée, dans l'interface utilisateur du Centre de sécurité @ conformité.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance entre 76 et 100 seront mappées à un niveau de confiance élevé. 
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance entre 66 et 75 seront mappées à un niveau de confiance moyen.
> - Toutes les stratégies avec une précision minimale ou des modèles SIT personnalisés avec des niveaux de confiance inférieurs ou égaux à 65 seront mappées à un niveau de confiance faible. 

## <a name="creating-custom-sensitive-information-types"></a>Création de types d’informations sensibles personnalisés

Pour créer des types d’informations sensibles personnalisés dans le Centre de sécurité et conformité, vous disposez des options suivantes :

- **Utiliser l’interface utilisateur** Vous pouvez configurer un type d’informations sensibles personnalisé à l’aide de l’interface utilisateur du Centre de sécurité et de conformité. Cette méthode vous permet d’utiliser des expressions régulières, des mots clés et des dictionnaires de mots clés. Pour en savoir plus, voir [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md).

- **Utiliser EDM** Vous pouvez configurer des types d’informations sensibles personnalisés à l’aide d’une classification de correspondance exacte des données (EDM). Cette méthode vous permet de créer un type d’informations sensibles dynamique à l’aide d’une base de données sécurisée que vous pouvez actualiser régulièrement. Voir l’article sur la [création d’un type d’informations sensibles personnalisé à l’aide d’une classification de correspondance exacte des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md).

- **Utiliser PowerShell** vous pouvez configurer des types d’informations sensibles personnalisés à l’aide de PowerShell. Bien que cette méthode soit plus complexe que celle de l’interface utilisateur, elle offre davantage d’options de configuration. Voir [Créer un type d’informations sensibles personnalisé dans l’interface PowerShell du Centre de sécurité et conformité](create-a-custom-sensitive-information-type-in-scc-powershell.md).



> [!NOTE]
> Des niveaux de confiance améliorés sont disponibles pour une utilisation immédiate dans le cadre de la protection contre la perte de données pour les services Microsoft 365, la Protection des informations Microsoft pour les services Microsoft 365, la conformité des communications, la gouvernance des informations et la gestion des enregistrements.

> Microsoft 365 Information Protection prend désormais en charge, en préversion, les langues de jeu de caractères à double octets pour :
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese

>Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

## <a name="for-further-information"></a>Pour plus d'informations
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
- [Créer un type d'informations sensibles personnalisé dans PowerShell](create-a-custom-sensitive-information-type-in-scc-powershell.md)

<!-- fwlink for this topic https://go.microsoft.com/fwlink/?linkid=2135644-->