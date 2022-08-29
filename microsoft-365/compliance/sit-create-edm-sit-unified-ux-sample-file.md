---
title: Créer un exemple de fichier SIT EDM pour la nouvelle expérience
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
description: Créez l’exemple de fichier à utiliser dans la nouvelle expérience.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d14a336602a2945bcf19b182c22784c12489cdba
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360594"
---
# <a name="create-edm-sit-sample-file-for-the-new-experience"></a>Créer un exemple de fichier SIT EDM pour la nouvelle expérience

La création et la mise à disposition d’un type d’informations sensibles basé sur EDM (EDM) sont un processus en plusieurs phases. Ils peuvent être utilisés dans les stratégies de protection contre la perte de données Microsoft Purview, eDiscovery et certaines tâches de gouvernance du contenu Cet article décrit le flux de travail et les liens vers les procédures pour chaque phase à l’aide de l’expérience classique.

## <a name="applies-to"></a>S’applique à

- Nouvelle expérience

Si vous souhaitez créer un sit EDM à l’aide de l’expérience classique, [créez l’expérience classique EDM SIT](sit-create-edm-sit-classic-ux-workflow.md).

## <a name="before-you-begin"></a>Avant de commencer

- Assurez-vous d’avoir effectué les étapes [d’exportation des données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md).

## <a name="formatting-the-sample-file"></a>Mise en forme de l’exemple de fichier

Le système extrait les noms de colonnes de l’exemple de fichier pour créer le schéma et recommande des SIT de base pour mapper les exemples de données de champ. Il doit être mis en forme de manière identique à votre fichier de table d’informations sensibles source et doit contenir des valeurs synthétiques représentatives de vos données réelles. Le fichier peut être enregistré au format .csv (valeurs séparées par des virgules), .tsv (valeurs séparées par des tabulations) ou séparés par des canaux (|), mais doit être identique à votre fichier de table d’informations sensibles source réel. Le format .tsv est recommandé dans les cas où vos valeurs de données peuvent inclure des virgules, telles que des adresses postales.

- Utilisez environ 10 à 20 lignes de données pour vous assurer que le système dispose de suffisamment d’échantillons pour fonctionner.
- Les valeurs de champ qui contiennent des virgules doivent être placées entre guillemets *«* .
- La première ligne doit être la ligne d’en-tête et contenir des noms de colonnes.
- Le fichier doit contenir au moins une ligne de données.
- Chaque ligne de données doit contenir le nombre correct de champs correspondant aux en-têtes.
- L’exemple de fichier contient jusqu’à 32 colonnes.
- La taille de l’exemple de fichier peut dépasser 2,5 Mo.
- Les noms de colonne (champ) doivent commencer par une lettre, comporter au moins trois caractères et se composer uniquement de caractères alphanumériques (A-Z, a-z, 0-9) et ne peuvent pas inclure d’espaces, de traits de soulignement ou d’autres caractères spéciaux. 

Par exemple, si vos données réelles ressemblent à ceci et utilisent le format délimité par un onglet (.tsv)

![image montrant une table séparée par un onglet avec quatre colonnes et trois lignes de données de données réelles artificielles](../media/sit-edm-tsv-actual-file.png)

Ensuite, votre exemple de fichier doit avoir les mêmes en-têtes de colonne, mais utiliser des valeurs synthétiques pour les lignes, comme ceci

![image montrant une table séparée par un onglet avec quatre colonnes et trois lignes de données représentatives synthétiques](../media/sit-edm-tsv-sample-file.png)

> [!TIP]
> Dans la nouvelle expérience, vous choisissez entre charger l’exemple de fichier ou entrer manuellement les valeurs d’exemple de fichier. Dans les deux cas, nous vous recommandons de créer l’exemple de fichier.

## <a name="next-step"></a>Étape suivante

- **Pour une nouvelle expérience** : [Créer un schéma sit EDM et un package de règles](sit-create-edm-sit-unified-ux-schema-rule-package.md)