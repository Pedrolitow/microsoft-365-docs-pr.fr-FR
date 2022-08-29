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
ms.openlocfilehash: eced8c769f7c1b8f35fd0eb4524d3518ea891881
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360060"
---
# <a name="learn-about-exact-data-match-based-sensitive-information-types"></a>En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données

[Les types d’informations sensibles](sensitive-information-type-learn-about.md) sont utilisés pour aider à identifier les éléments sensibles afin que vous puissiez les empêcher d’être partagés par inadvertance ou de manière inappropriée. Ils sont également utilisés pour aider à localiser les données pertinentes dans eDiscovery et à appliquer des actions de gouvernance à certains types d’informations. Vous définissez un type d’informations sensibles personnalisé (SIT) en fonction des éléments suivants :

- modèles
- preuve de mot clé, comme *un employé*, un *numéro de sécurité sociale* ou un *ID*
- caractère à proximité de la preuve dans un modèle particulier
- niveaux de confiance

Mais que se passe-t-il si vous souhaitez un type d’informations sensibles personnalisé (SIT) qui utilise des valeurs de données exactes ou presque exactes, au lieu d’un type qui a trouvé des correspondances basées sur des modèles génériques ? Avec la classification EDM (Exact Data Match), vous pouvez créer un type d’informations sensibles personnalisé conçu pour :

- être dynamique et actualisé facilement ;
- entraîner moins de faux positifs ;
- utiliser des données sensibles structurées ;
- gérer les informations sensibles de manière plus sécurisée, sans les partager avec quiconque, y compris Microsoft
- être utilisé avec différents services de cloud computing Microsoft.

![Classification basée sur EDM.](../media/EDMClassification.png)

La classification EDM vous permet de créer des types d’informations sensibles personnalisés qui font référence à des valeurs exactes dans une base de données d’informations sensibles. La base de données peut être actualisée quotidiennement et peut contenir jusqu’à 100 millions de lignes de données. À mesure que des employés, patients ou clients vont et viennent, et que les enregistrements changent, vos types d’informations sensibles personnalisés restent à jour et valides. De plus, vous pouvez utiliser la classification basée sur EDM avec des stratégies, telles que des [stratégies de protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md) ou [des stratégies de fichiers Microsoft Cloud App Security](/cloud-app-security/data-protection-policies).

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

La table source d’informations sensibles contient les valeurs que le SIT EDM recherche. Il est constitué de colonnes et de lignes. Les en-têtes de colonne sont les noms de champs, les lignes sont une instance d’élément et chaque cellule contient les valeurs de cette instance d’élément pour ce champ.

Voici un exemple simple de table source d’informations sensibles.

|Prénom|Nom|Date of Birth|
|---|---|---|
|Esaïe|Langer| 05-05-1960|
|Ana|Bowman|11-24-1971|
|Oscar|Ward|02-12-1998|

### <a name="rule-package"></a>Package de règles

Chaque SIT a un package de règles. Vous utilisez le package de règles dans un sit EDM pour définir :

- Correspond, qui spécifient le champ qui sera l’élément principal à utiliser dans la recherche exacte. Il peut s’agir d’une expression régulière avec ou sans validation de somme de contrôle, d’une liste de mots clés, d’un dictionnaire de mots clés ou d’une fonction.
- Classification, qui spécifie la correspondance de type d’informations sensibles qui déclenche une recherche EDM.
- Élément de prise en charge, qui sont des éléments qui, lorsqu’ils sont trouvés, fournissent des preuves qui aident à augmenter la confiance de la correspondance. Par exemple, l’occurrence du mot clé « SSN » à proximité d’un numéro de sécurité sociale réel. Un élément de prise en charge peut être une expression régulière avec ou sans validation de somme de contrôle, liste de mots clés ou dictionnaire de mots clés.
- Les niveaux de confiance (élevé, moyen, faible) reflètent la quantité de preuves à l’appui détectées en plus de l’élément principal. Plus un élément contient de preuves à l’appui, plus la confiance qu’un élément correspondant contient contient les informations sensibles que vous recherchez. Pour plus d’informations sur les niveaux de confiance, consultez les [parties fondamentales d’un type d’informations sensibles](sensitive-information-type-learn-about.md#fundamental-parts-of-a-sensitive-information-type) .
- Proximité : nombre de caractères entre l’élément principal et l’élément de prise en charge.

### <a name="you-supply-your-own-schema-and-data"></a>Vous fournissez votre propre schéma et vos propres données

[Microsoft Purview est fourni avec de nombreux SIÈGES prédéfinis](sensitive-information-type-entity-definitions.md). Ces ÉLÉMENTS SONT fournis avec des schémas, des modèles d’expression régulière, des mots clés et des niveaux de confiance. Toutefois, avec les SIT EDM, vous êtes responsable de la définition du schéma, ainsi que des champs principaux et secondaires qui identifient les éléments sensibles. Étant donné que le schéma et les valeurs de données primaires et secondaires sont hautement sensibles, vous les chiffrez via une fonction de [hachage](/dotnet/standard/security/ensuring-data-integrity-with-hash-codes) qui inclut une valeur [salt](https://en.wikipedia.org/wiki/Salt_(cryptography)#:~:text=The%20salt%20value%20is%20generated%20at%20random%20and,the%20salt%20value%20and%20hashed%20value%20are%20stored.) générée de manière aléatoire ou auto-fournie. Seules les valeurs hachées sont chargées sur le service, de sorte que vos données sensibles ne sont jamais ouvertes.

### <a name="primary-and-secondary-support-elements"></a>Éléments de support principal et secondaire

Lorsque vous créez un sit EDM, vous définissez un champ *d’élément principal* dans le package de règles. Tout le contenu sera recherché pour l’élément principal. EDM requiert que l’élément principal soit détectable via un SIT existant. 

> [!NOTE]
> Consultez les [définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md) pour obtenir la liste complète des SIT disponibles.  

Vous devez trouver un SIT prédéfini qui détecte les informations sensibles que vous souhaitez que votre sit EDM détecte. Par exemple, si votre schéma SIT EDM comporte le numéro de sécurité sociale des États-Unis comme élément principal, lorsque vous créez votre schéma EDM, vous l’avez associé au [numéro de sécurité sociale (SSN) SIT des États-Unis](sit-defn-us-social-security-number.md) . Les éléments principaux doivent suivre un modèle défini pour être détectés.

Lorsque l’élément principal est trouvé dans un élément analysé, EDM recherche ensuite les éléments *secondaires* ou de prise en charge. Les éléments secondaires n’ont pas besoin de suivre un modèle, mais doivent se trouver à une certaine proximité de l’élément principal.

## <a name="how-matching-works"></a>Fonctionnement de la correspondance

EDM fonctionne en comparant les chaînes de vos documents et e-mails avec les valeurs de la table source d’informations sensibles pour voir si les valeurs du contenu analysé sont présentes dans la table. La comparaison est effectuée en comparant des hachages de chiffrement unidirectionnels.


> [!TIP]
> Vous pouvez utiliser les SIT EDM et les SIT prédéfinis sur lesquels ils sont basés, ensemble, dans les règles DLP pour une meilleure détection. Utilisez l’EDM SIT avec des niveaux de confiance plus élevés et le SIT prédéfini avec des niveaux de confiance inférieurs. Par exemple, utilisez un SIT EDM qui recherche le numéro de sécurité sociale et d’autres données de prise en charge avec des exigences strictes avec une confiance élevée. L’utilisation de la confiance élevée génère une correspondance DLP lorsque peu d’instances sont détectées. Utilisez ensuite un SIT prédéfini, comme le numéro de sécurité sociale des États-Unis, avec des niveaux de confiance inférieurs qui déclencheront une correspondance DLP lorsque des nombres plus élevés d’occurrences sont détectés.  

## <a name="services-that-edm-supports"></a>Services pris en charge par EDM


|Service  |Emplacements  |
|---------|---------|
| Protection contre la perte de données Microsoft Purview    | - SharePoint online </br>- OneDrive Entreprise </br>- Conversation Teams </br>- Exchange Online </br>- Appareils       |
|Microsoft Defender for Cloud Apps     | - SharePoint Online </br>- OneDrive Entreprise        |
|Étiquetage automatique (côté service)     |- SharePoint online </br>- OneDrive Entreprise </br>- Exchange Online         |
|Étiquetage automatique (côté client)     |- Word </br>- Excel </br>- PowerPoint </br>- Clients de bureau Exchange         |
|Clé gérée par le client     |- SharePoint online </br>- OneDrive Entreprise </br>- Conversation Teams </br>- Exchange Online </br>- Word </br>- Excel </br>- PowerPoint </br>- Clients de bureau Exchange </br>- Appareils         |
|eDiscovery     |- SharePoint online </br>- OneDrive Entreprise </br>- Conversation Teams </br>- Exchange Online </br>- Word </br>- Excel </br>- PowerPoint </br>- Clients de bureau Exchange  |
|Gestion des risques internes     |- SharePoint online </br>- OneDrive Entreprise </br>- Conversation Teams </br>- Exchange Online </br>- Word </br>- Excel </br>- PowerPoint </br>- Clients de bureau Exchange      |

## <a name="see-also"></a>Voir aussi

- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
