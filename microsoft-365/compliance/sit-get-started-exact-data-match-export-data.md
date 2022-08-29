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
description: Découvrez comment exporter des données sources pour un type d’informations sensibles basé sur des correspondances de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4c79123ab44e9be20a96d19c058df6aecfb6aeeb
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359862"
---
# <a name="export-source-data-for-exact-data-match-based-sensitive-information-type"></a>Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données

## <a name="applies-to"></a>S’applique à

- [Nouvelle expérience](sit-create-edm-sit-unified-ux-workflow.md)
- [Expérience classique](sit-create-edm-sit-classic-ux-workflow.md)

La table de données sensibles est un fichier texte contenant des lignes de valeurs par rapport auquel vous allez comparer le contenu de vos documents pour identifier les données sensibles. Ces valeurs peuvent être des informations d’identification personnelle, des enregistrements de produit ou d’autres données sensibles sous forme de texte que vous souhaitez détecter dans le contenu et prendre des mesures de protection.

Une fois que les données ont été exportées dans l’un des formats pris en charge, vous pouvez procéder à la création d’un schéma EDM.

## <a name="defining-your-edm-sensitive-type"></a>Définition de votre type sensible EDM

Lors de la définition de votre type sensible EDM, l’une des décisions les plus critiques consiste à définir les champs qui seront des champs principaux. Les champs principaux doivent suivre un modèle détectable et être définis en tant que champs pouvant faire l’objet d’une recherche (colonnes) dans votre schéma EDM. Les champs secondaires n’ont pas besoin de suivre un modèle, car ils seront comparés à tous les texte qui entourent les correspondances avec les champs principaux.

Utilisez ces règles pour déterminer les colonnes que vous devez utiliser comme champs principaux :

- Si vous devez détecter des données sensibles en fonction de la présence d’une valeur unique correspondant à un champ dans votre table de données sensibles, quelle que soit la présence d’autres données sensibles qui l’entourent, cette colonne doit être définie comme élément principal pour un type EDM. 
- Si plusieurs combinaisons de différents champs de votre table de données sensibles doivent être détectées dans le contenu, identifiez les colonnes communes à la plupart de ces combinaisons et désignez-les comme éléments principaux et combinaisons des autres champs en tant qu’éléments secondaires.
- Si une colonne que vous souhaitez utiliser comme champ principal ne suit pas un modèle détectable, comme toute chaîne de texte ou suit des modèles détectables qui seraient présents quelque part dans un grand pourcentage de documents ou d’e-mails, essayez de choisir d’autres colonnes mieux structurées comme éléments principaux.

Par exemple, si vous avez les colonnes `full name`, `date of birth`, `account number`et `Social Security Number`, même si les prénoms et les noms sont les colonnes qui seront communes aux différentes combinaisons de données que vous souhaitez détecter, ces chaînes ne suivent pas des modèles facilement identifiables et peuvent être difficiles à définir en tant que type d’informations sensibles. Cela est dû au fait que certains noms peuvent même ne pas commencer par des majuscules, ils peuvent être formés par deux, trois mots ou plus et peuvent même contenir des nombres ou d’autres caractères non alphabétiques. La date de naissance peut être plus facilement identifiée, mais étant donné que chaque e-mail et la plupart des documents contiendront au moins une date, il n’est pas non plus un bon candidat. Les numéros de sécurité sociale et les numéros de compte sont de bons candidats pour être utilisés comme champ principal.

## <a name="save-sensitive-data-in-csv-tsv-or-pipe-separated-format"></a>Enregistrer des données sensibles au format .csv, .tsv ou séparés par des canaux

1. Identifiez les informations sensibles que vous voulez utiliser. Exportez les données vers une application telle que Microsoft Excel et enregistrez le fichier dans un fichier texte. Le fichier peut être enregistré au format .csv (valeurs séparées par des virgules), .tsv (valeurs séparées par des tabulations) ou séparés par des canaux (|). Le format .tsv est recommandé dans les cas où vos valeurs de données peuvent inclure des virgules, telles que des adresses postales.
Le fichier de données peut inclure au maximum :
   - 100 millions de lignes de données sensibles
   - 32 colonnes (champs) par source de données
   - 5 colonnes (champs) marquées comme pouvant faire l’objet d’une recherche

2. Structurez les données sensibles dans le fichier .csv ou .tsv de telle sorte que la première ligne inclut les noms des champs utilisés pour la classification basée sur EDM. Dans votre fichier, vous pouvez avoir des noms de champs tels que « ssn », « birthdate », « firstname », « lastname ». Les noms d’en-tête de colonne ne peuvent pas contenir des espaces ni des traits de soulignement. Par exemple, le fichier .csv utilisé dans cet exemple est appelé *PatientRecords.csv*. Ses colonnes incluent *PatientID*, *MRN*, *LastName*, *FirstName*, *SSN*, etc.

3. Faites attention au format des champs de données sensibles ; en particulier, les champs qui peuvent contenir des virgules dans leur contenu. Par exemple, une adresse postale qui contient la valeur « Seattle, WA » est analysée en tant que deux champs distincts lorsqu’elle est analysée si le format .csv est sélectionné. Pour éviter cela, utilisez le format .tsv ou entourez la virgule contenant des valeurs par des guillemets doubles dans la table de données sensible. Si les virgules contenant des valeurs contiennent également des espaces, vous devez créer un SIT personnalisé qui correspond au format correspondant. Par exemple, un SIT qui détecte une chaîne à plusieurs mots avec des virgules et des espaces.

## <a name="next-step"></a>Étape suivante

- **Pour une nouvelle expérience** : [créer un exemple de fichier SIT EDM pour la nouvelle expérience](sit-create-edm-sit-unified-ux-sample-file.md)

ou

- **Pour une expérience classique** : [créer le schéma pour les types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-create-schema.md)

## <a name="see-also"></a>Voir aussi

- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md#get-started-with-exact-data-match-based-sensitive-information-types)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
