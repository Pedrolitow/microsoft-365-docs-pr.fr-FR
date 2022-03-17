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
description: Découvrez les types d’informations sensibles exacts basés sur les correspondances de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 21e6f3c12d7c401562a1ee1915e1e1c266724b1b
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526919"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données

Les [types](sensitive-information-type-learn-about.md) d’informations sensibles permettent d’identifier les éléments sensibles afin de pouvoir les empêcher d’être partagés par inadvertance ou de manière inappropriée, pour faciliter la recherche de données pertinentes dans eDiscovery et pour appliquer des actions de gouvernance à certains types d’informations. Vous définissez un type d’informations sensibles personnalisé (SIT) basé sur :

- modèles
- preuve de mot clé telle *que l’employé*, *le numéro de sécurité sociale* *ou l’ID*
- caractère à proximité de la preuve dans un modèle particulier
- niveaux de confiance

Mais que se passe-t-il si vous souhaitez un type d’informations sensibles personnalisé qui utilise des valeurs de données exactes ou presque exactes, au lieu d’un type qui trouve des correspondances basées sur des modèles génériques ? Avec la classification EDM (Exact Data Match), vous pouvez créer un type d’informations sensibles personnalisé conçu pour :

- être dynamique et actualisé facilement ;
- être plus évolutif ;
- entraîner moins de faux positifs ;
- utiliser des données sensibles structurées ;
- gérer les informations sensibles de manière plus sécurisée, sans les partager avec personne, y compris Microsoft
- être utilisé avec différents services de cloud computing Microsoft.

![Classification basée sur EDM.](../media/EDMClassification.png)

La classification EDM vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. La base de données peut être actualisée quotidiennement et peut contenir jusqu’à 100 millions de lignes de données. À mesure que des employés, patients ou clients vont et viennent, et que les enregistrements changent, vos types d’informations sensibles personnalisés restent à jour et valides. Vous pouvez également utiliser la classification basée sur EDM avec des stratégies, telles [que les stratégies de protection contre la perte de données](dlp-learn-about-dlp.md) ou [les stratégies de fichier de Microsoft Cloud App Security](/cloud-app-security/data-protection-policies).

> [!NOTE]
> Microsoft 365 Information Protection prend désormais en charge, les langues de jeu de caractères à double octets pour :
>
> - Chinois (simplifié)
> - Chinois (traditionnel)
> - Korean
> - Japanese
>
> Cette prise en charge est disponible pour les types d’informations sensibles. Si vous souhaitez en savoir plus, consultez l’article [Prise en charge de la protection des informations pour les jeux de caractères à double octets (préversion)](mip-dbcs-relnotes.md).

## <a name="whats-different-in-an-edm-sit"></a>Différences dans un sit EDM

Lorsque vous travaillez avec des sits EDM, il est utile de comprendre quelques concepts qui leur sont propres.  

### <a name="schema"></a>Schéma

Le schéma est un fichier xml qui définit :

- Nom du schéma, appelé *datastore*. 
- Noms de champ que contient votre table de sources d’informations sensibles. Il existe un mappage 1:1 du nom du champ de schéma au nom de colonne de la table source d’informations sensibles.
- Champs utilisables dans une recherche.
- Tous les paramètres de modification de recherche, appelés correspondance *configurables*, tels que l’ignorer les délimiteurs et la cas dans les valeurs de recherche.

### <a name="sensitive-information-source-table"></a>Tableau des sources d’informations sensibles

La table source sensible contient les valeurs d’informations sensibles que l’EDM SIT recherchera. Il est composé de colonnes et de lignes. Les en-têtes de colonne sont les noms de champ, les lignes sont une instance de données et chaque cellule contient les valeurs de cette instance pour ce champ.

Voici un exemple simple de tableau de sources d’informations sensibles.

|Prénom  |Nom  |Date of Birth  |
|---------|---------|---------|
|Isa sous   |Langer  | 05-05-1960 |
|Ana   |Bowman         |11-24-1971 |
|Oscar   |Sons         |02-12-1998 |


### <a name="rule-package"></a>Package de règles

Chaque sit dispose d’un package de règles. Vous utilisez le package de règles dans un sit EDM pour définir :

- Correspond, qui spécifient le champ qui sera l’élément principal à utiliser dans la recherche exacte. Il peut s’agit d’une expression régulière avec ou sans validation de la liste de contrôle, d’une liste de mots clés, d’un dictionnaire de mots clés ou d’une fonction.
- Classification, qui spécifie la correspondance de type sensible qui déclenche la recherche EDM.
- Élément de prise en charge qui sont des éléments qui, lorsqu’ils sont trouvés, fournissent des preuves à l’appui qui permettent d’augmenter la confiance de la correspondance. Par exemple, le mot clé « SSN » à proximité d’un numéro SSN. Il peut s’agit d’une expression régulière avec ou sans validation de la liste de contrôle, d’une liste de mots clés, d’un dictionnaire de mots clés.
- Les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves justificatives détectées avec l’élément principal. Plus la preuve justificative qu’un élément contient est importante, plus la confiance qu’un élément correspond contient les informations sensibles que vous recherchez. Pour plus [d’informations](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) sur les niveaux de confiance, voir les parties fondamentales d’un type d’informations sensibles.
Proximité : nombre de caractères entre l’élément principal et l’élément de prise en charge

### <a name="you-supply-your-own-schema-and-data"></a>Vous fournissez vos propres schémas et données

[Microsoft 365 est livré avec plus de 200 SITS](sensitive-information-type-entity-definitions.md) avec des schémas prédéfinits, des modèles regex, des mots clés et des niveaux de confiance. Avec les sits EDM, vous êtes responsable de la définition du schéma, ainsi que des champs principaux et secondaires qui identifient les éléments sensibles. Étant donné que le schéma et les valeurs de données principales et secondaires sont hautement sensibles, vous les chiffrez [](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) via une fonction de hachage qui inclut une valeur salt générée de [](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) manière aléatoire ou fournie automatiquement. Ces valeurs hachées sont ensuite téléchargées vers le service, afin que vos données sensibles ne soient jamais ouvertes.

### <a name="primary-and-secondary-support-elements"></a>Éléments de prise en charge principaux et secondaires

Lorsque vous créez un sit EDM, vous définissez un champ *d’élément principal* dans le package de règles. Les champs principaux sont les éléments pour lesquels tout votre contenu sera recherché et qui doivent suivre un modèle défini pour être identifiés. Lorsque l’élément principal est trouvé dans les éléments analysés, EDM recherche ensuite les éléments  secondaires ou de prise en charge, qui n’ont pas besoin de suivre un modèle, et leur proximité par rapport à l’élément principal. EDM nécessite que l’élément principal soit tout d’abord découvrable via un SIT existant. Consultez les [définitions d’entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md) pour obtenir la liste complète des sits disponibles. Vous devez trouver l’une de celles qui détectent la classe que votre EDM SIT doit détecter. Par exemple, si votre schéma SIT EDM a le numéro de sécurité sociale américain comme élément principal, lorsque vous créez votre schéma EDM, vous l’avez associé au numéro de sécurité sociale [(SSN)](sensitive-information-type-entity-definitions.md#us-social-security-number-ssn) SIT des États-Unis.


## <a name="how-matching-works"></a>Fonctionnement de la correspondance

EDM trouve des correspondances en comparant le contenu qu’il trouve à une table de données sensibles que vous définissez. Le test de correspondance est effectué à l’aide d’une combinaison de règles et de modèles traditionnels pour vous assurer que les données de correspondance sont une instance réelle des données que vous souhaitez rechercher et protéger. EDM fonctionne en comparant les chaînes de vos documents et e-mails aux valeurs d’une table de données sensibles que vous fournissez pour savoir si les valeurs de votre contenu sont présentes dans le tableau en comparant les hchéthages cryptographiques à sens seul.

> [!TIP]
> Une pratique courante consiste à combiner l’utilisation de types d’informations sensibles EDM et les types d’informations sensibles réguliers sur lesquels ils sont basés dans des règles DLP, avec des seuils différents. Par exemple, vous pouvez utiliser un type d’informations sensibles EDM qui recherche des numéros de sécurité sociale et d’autres données, avec des exigences strictes et une faible tolérance où une ou plusieurs correspondances entraînent une alerte DLP et utilisez le type d’informations sensibles normal, comme le numéro de sécurité sociale américain intégré, pour un nombre plus élevé.  

## <a name="see-also"></a>Voir aussi

- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
   
