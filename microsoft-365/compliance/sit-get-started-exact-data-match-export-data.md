---
title: Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment exporter des données sources pour un type d’informations sensibles basé sur une correspondance exacte de données.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9a1ee56708018ddfddf141499bf4cf5f9ee02449
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526261"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données


La table de données sensibles est un fichier texte contenant des lignes de valeurs par rapport à laquelle vous comparerez le contenu de vos documents pour identifier les données sensibles. Ces valeurs peuvent être des informations d’identification personnelle, des enregistrements de produits ou d’autres données sensibles sous forme de texte que vous souhaitez détecter dans le contenu et prendre des mesures de protection.

Une fois que les données ont été exportées dans l’un des formats pris en charge, vous pouvez procéder à la création d’un schéma EDM.

## <a name="defining-your-edm-sensitive-type"></a>Définition de votre type sensible EDM

Lors de la définition de votre type sensible EDM, l’une des décisions les plus importantes consiste à déterminer les champs qui seront des champs principaux. Les champs principaux doivent suivre un modèle détectable et être définis en tant que champs utilisables dans une recherche (colonnes) dans votre schéma EDM. Les champs secondaires n’ont pas besoin de suivre un modèle, car ils seront comparés à tout le texte qui entoure les correspondances avec les champs principaux.

Utilisez ces règles pour vous aider à déterminer les colonnes que vous devez utiliser comme champs principaux :

- Si vous devez détecter des données sensibles en fonction de la présence d’une valeur unique correspondant à un champ dans votre table de données sensibles, quelle que soit la présence d’autres données sensibles qui l’entourent, cette colonne doit être définie comme élément principal pour un type EDM. 
- Si plusieurs combinaisons de champs différents dans votre table de données sensibles doivent être détectées dans le contenu, identifiez les colonnes communes à la plupart de ces combinaisons et désignez-les comme éléments principaux et combinaisons des autres champs en tant qu’éléments secondaires.
- Si une colonne que vous souhaitez utiliser comme champ principal ne suit pas un modèle détectable, comme une chaîne de texte ou des modèles détectables qui seraient présents dans un grand pourcentage de documents ou d’e-mails, essayez de choisir d’autres colonnes mieux structurées comme éléments principaux.

Par exemple, `full name`si vous avez les colonnes , `date of birth`et `account number``Social Security Number`, même si le prénom et le nom sont les colonnes communes aux différentes combinaisons de données que vous souhaitez détecter, ces chaînes ne suivent pas facilement des modèles identifiables et peuvent être difficiles à définir en tant que type d’informations sensibles. Cela est dû au fait que certains noms peuvent ne pas commencer par des lettres en minuscules, ils peuvent être constitués de deux, trois mots ou plus et peuvent même contenir des nombres ou d’autres caractères non alphabétiques. La date de naissance peut être identifiée plus facilement, mais comme chaque e-mail et la plupart des documents contiennent au moins une date, il ne s’agit pas non plus d’un bon candidat. Les numéros de sécurité sociale et les numéros de compte sont de bons candidats pour une utilisation en tant que champ principal.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Enregistrer des données sensibles au format .csv, .tsv ou séparés par des pipelines

1. Identifiez les informations sensibles que vous voulez utiliser. Exportez les données vers une application, telle que Microsoft Excel, et enregistrez le fichier dans un fichier texte. Le fichier peut être enregistré au format .csv (valeurs séparées par des virgules), .tsv (valeurs séparées par des tabulations) ou séparés par des |. Le format .tsv est recommandé dans les cas où vos valeurs de données peuvent inclure des virgules, telles que des adresses postales.
Le fichier de données peut inclure au maximum :
   - 100 millions de lignes de données sensibles
   - 32 colonnes (champs) par source de données
   - 5 colonnes (champs) marquées comme pouvant faire l’objet d’une recherche

2. Structurez les données sensibles dans le fichier .csv ou .tsv afin que la première ligne inclut les noms des champs utilisés pour la classification EDM. Dans votre fichier, vous pouvez avoir des noms de champ tels que « ssn », « birthdate », « firstname », « lastname ». Les noms d’en-tête de colonne ne peuvent pas contenir des espaces ni des traits de soulignement. Par exemple, le fichier .csv utilisé dans cet exemple est appelé *PatientRecords.csv*. Ses colonnes incluent *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN*, etc.

3. Prêtez attention au format des champs de données sensibles. En particulier, les champs qui peuvent contenir des virgules dans leur contenu, par exemple, une adresse de rue qui contient la valeur « Seattle,WA » sera évaluée en tant que deux champs distincts lors de l'.csv si le format .csv est sélectionné. Pour éviter cela, utilisez le format .tsv ou entourez la virgule contenant des valeurs par des guillemets doubles dans la table de données sensibles. Si des virgules contenant des valeurs contiennent également des espaces, vous devez créer un sit personnalisé qui correspond au format correspondant. Par exemple, un SIT qui détecte une chaîne à plusieurs mots avec des virgules et des espaces.

## <a name="next-step"></a>Étape suivante

- [Créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)

## <a name="see-also"></a>Voir aussi

- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
