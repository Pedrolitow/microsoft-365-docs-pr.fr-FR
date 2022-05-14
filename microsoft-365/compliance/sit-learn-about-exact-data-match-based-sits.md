---
title: En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez les types d’informations sensibles basés sur des correspondances de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0574c11751898b31b22da4642f2d5dd415991732
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415923"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Les types d’informations sensibles](sensitive-information-type-learn-about.md) sont utilisés pour aider à identifier les éléments sensibles afin que vous puissiez les empêcher d’être partagés par inadvertance ou de manière inappropriée, pour faciliter la localisation des données pertinentes dans eDiscovery et pour appliquer des actions de gouvernance à certains types d’informations. Vous définissez un type d’informations sensibles personnalisé (SIT) en fonction des éléments suivants :

- modèles
- preuve de mot clé, comme *un employé*, un *numéro de sécurité sociale* ou un *ID*
- caractère à proximité de la preuve dans un modèle particulier
- niveaux de confiance

Mais que se passe-t-il si vous souhaitez un type d’informations sensibles personnalisé (SIT) qui utilise des valeurs de données exactes ou presque exactes, au lieu d’un type qui a trouvé des correspondances basées sur des modèles génériques ? Avec la classification EDM (Exact Data Match), vous pouvez créer un type d’informations sensibles personnalisé conçu pour :

- être dynamique et actualisé facilement ;
- être plus évolutif ;
- entraîner moins de faux positifs ;
- utiliser des données sensibles structurées ;
- gérer les informations sensibles de manière plus sécurisée, sans les partager avec quiconque, y compris Microsoft
- être utilisé avec différents services de cloud computing Microsoft.

![Classification basée sur EDM.](../media/EDMClassification.png)

La classification EDM vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. La base de données peut être actualisée quotidiennement et peut contenir jusqu’à 100 millions de lignes de données. À mesure que des employés, patients ou clients vont et viennent, et que les enregistrements changent, vos types d’informations sensibles personnalisés restent à jour et valides. De plus, vous pouvez utiliser la classification basée sur EDM avec des stratégies, telles que [Microsoft Purview des stratégies de protection contre la perte de données](dlp-learn-about-dlp.md) ou [des stratégies de fichiers Microsoft Cloud App Security](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Protection des données Microsoft Purview prend en charge les langues de jeu de caractères sur deux octets pour :
>
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
> Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

## <a name="whats-different-in-an-edm-sit"></a>Ce qui est différent dans un SIT EDM

Lorsque vous travaillez avec des SIT EDM, il est utile de comprendre quelques concepts qui leur sont propres.  

### <a name="schema"></a>Schéma

Le schéma est un fichier xml qui définit :

- Nom du schéma, appelé ultérieurement Magasin de *données*. 
- Noms de champs que votre table source d’informations sensibles contient. Il existe un mappage 1:1 du nom du champ de schéma au nom de colonne de la table source d’informations sensibles.
- Champs pouvant faire l’objet d’une recherche.
- Toute recherche modifiant des paramètres, appelée *correspondance configurable*, comme l’ignorance des délimiteurs et de la casse dans les valeurs recherchées.

### <a name="sensitive-information-source-table"></a>Table source d’informations sensibles

La table source sensible contient les valeurs d’informations sensibles que le SIT EDM recherche. Il est constitué de colonnes et de lignes. Les en-têtes de colonne sont les noms de champs, les lignes sont une instance de données et chaque cellule contient les valeurs de cette instance pour ce champ.

Voici un exemple simple de table source d’informations sensibles.

|Prénom|Nom|Date of Birth|
|---|---|---|
|Esaïe|Langer| 05-05-1960|
|Ana|Bowman|11-24-1971|
|Oscar|Ward|02-12-1998|

### <a name="rule-package"></a>Package de règles

Chaque SIT a un package de règles. Vous utilisez le package de règles dans un sit EDM pour définir :

- Correspond, qui spécifient le champ qui sera l’élément principal à utiliser dans la recherche exacte. Il peut s’agir d’une expression régulière avec ou sans validation de somme de contrôle, d’une liste de mots clés, d’un dictionnaire de mots clés ou d’une fonction.
- Classification, qui spécifie la correspondance de type sensible qui déclenche la recherche EDM.
- Élément de soutien qui sont des éléments qui, s’ils sont trouvés, fournissent des preuves de soutien qui contribuent à accroître la confiance de la correspondance. Par exemple, le mot clé « SSN » à proximité d’un numéro SSN. Il peut s’agir d’une expression régulière avec ou sans validation de somme de contrôle, liste de mots clés, dictionnaire de mots clés.
- Les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves à l’appui détectées avec l’élément principal. Plus un élément contient de preuves à l’appui, plus la confiance qu’un élément correspondant contient contient les informations sensibles que vous recherchez. Pour plus d’informations sur les niveaux de confiance, consultez les [parties fondamentales d’un type d’informations sensibles](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) .
Proximité : nombre de caractères entre l’élément principal et l’élément de prise en charge

### <a name="you-supply-your-own-schema-and-data"></a>Vous fournissez votre propre schéma et vos propres données

[Microsoft Purview est fourni avec plus de 200 SITS](sensitive-information-type-entity-definitions.md) avec des schémas prédéfinis, des modèles regex, des mots clés et des niveaux de confiance. Avec les SIT EDM, vous êtes responsable de la définition du schéma, ainsi que des champs principaux et secondaires qui identifient les éléments sensibles. Étant donné que le schéma et les valeurs de données primaires et secondaires sont hautement sensibles, vous les chiffrez via une fonction de [hachage](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) qui inclut une valeur [salt](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) générée de manière aléatoire ou auto-fournie. Ces valeurs hachées sont ensuite chargées sur le service, de sorte que vos données sensibles ne sont jamais ouvertes.

### <a name="primary-and-secondary-support-elements"></a>Éléments de support principal et secondaire

Lorsque vous créez un sit EDM, vous définissez un champ *d’élément principal* dans le package de règles. Les champs principaux sont les éléments pour lesquels tout votre contenu sera recherché et qui doivent suivre un modèle défini pour être identifiés. Lorsque l’élément principal est trouvé dans les éléments analysés, EDM recherche ensuite les éléments *secondaires* ou de prise en charge, qui n’ont pas besoin de suivre un modèle et leur proximité avec l’élément principal. EDM requiert que l’élément principal soit d’abord détectable via un SIT existant. Consultez les [définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md) pour obtenir la liste complète des SIT disponibles. Vous devez trouver l’une de celles qui détectent la classe que vous souhaitez que votre sit EDM détecte. Par exemple, si votre schéma SIT EDM comporte le numéro de sécurité sociale des États-Unis comme élément principal, lorsque vous créez votre schéma EDM, vous l’avez associé au [numéro de sécurité sociale (SSN) SIT des États-Unis](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) .


## <a name="how-matching-works"></a>Fonctionnement de la correspondance

EDM recherche des correspondances en comparant le contenu qu’il trouve à une table de données sensibles que vous définissez. Le test de correspondance est effectué à l’aide d’une combinaison de règles et de modèles traditionnels pour vous assurer que les données correspondantes sont une instance réelle de données que vous souhaitez rechercher et protéger. À la base, EDM fonctionne en comparant les chaînes de vos documents et e-mails aux valeurs d’une table de données sensibles que vous fournissez pour déterminer si les valeurs de votre contenu sont présentes dans la table en comparant des hachages de chiffrement unidirectionnels.

> [!TIP]
> Une pratique courante consiste à combiner l’utilisation de types d’informations sensibles EDM et les types d’informations sensibles standard sur lesquels ils sont basés dans les règles DLP, avec différents seuils. Par exemple, vous pouvez utiliser un type d’informations sensibles EDM qui recherche des numéros de sécurité sociale et d’autres données, avec des exigences strictes et une faible tolérance où une ou plusieurs correspondances entraînent une alerte DLP, et utiliser le type d’informations sensibles standard, comme le numéro de sécurité sociale intégré aux États-Unis pour des nombres plus élevés.  

## <a name="see-also"></a>Voir aussi

- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
