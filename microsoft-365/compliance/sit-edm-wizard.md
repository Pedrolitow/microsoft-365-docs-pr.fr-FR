---
title: Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2081de887e09794350222dac3527bb3ff932837a
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49699148"
---
# <a name="use-the-exact-data-match-schema-and-sensitive-information-type-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

La [Création d’un type d’informations sensibles personnalisé à l’aide d’une classification de correspondance exacte des données (EDM)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md) implique de nombreuses étapes.  Vous pouvez utiliser cet Assistant pour créer votre schéma et votre modèle de type d’informations sensibles (package de règles) en vue de simplifier le processus.

> [!NOTE]
> L’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles est disponible uniquement pour les nuages mondiaux et GCC.

Cet Assistant peut être utilisé à la place des étapes suivantes :

- [Définir le schéma de votre base de données d’informations sensibles](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#define-the-schema-for-your-database-of-sensitive-information)
- [Configurer un modèle (package de règles)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#set-up-a-rule-package)

dans [Partie 1 : configurer la classification EDM](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#part-1-set-up-edm-based-classification).

## <a name="pre-requisites"></a>Conditions préalables

1. Familiarisez-vous avec les étapes de création d’un type d’informations sensibles personnalisées avec le [flux de travail EDM en un clin d’œil](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#the-work-flow-at-a-glance).

2. Suivez les étapes décrites dans la section [Enregistrer des données sensibles au format. csv](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#save-sensitive-data-in-csv-format).

## <a name="use-the-exact-data-match-schema-and-sensitive-information-type-pattern-wizard"></a>Utiliser l’Assistant de schéma de correspondance exacte des données et de type d’informations sensibles

1. Dans le Centre de conformité Microsoft 365 pour votre client, accédez à **Classification des données** > **Correspondances exactes des données**.

2. Choisissez **Créer un schéma EDM** pour ouvrir le menu volant de configuration de l’Assistant de schéma.

![Menu volant de configuration de l’Assistant de création de schéma EDM](../media/edm-schema-wizard-1.png)

3. Indiquez un nom **approprié** et **Description**.

4. Choisissez **Ignorer les séparateurs et ponctuations pour tous les champs du schéma** si vous souhaitez ce comportement. Pour en savoir plus sur la configuration d’EDM afin d’ignorer la casse ou les séparateurs, voir [Création d’un type d’informations sensibles personnalisé avec une classification de correspondance exacte de données (EDM)](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md).

5. Renseignez les valeurs souhaitées pour votre **Champ de schéma n° 1** et ajoutez des champs si nécessaire. 

> [!IMPORTANT]
> Au moins un champ, mais pas plus de cinq, doivent être désignés comme pouvant faire l’objet d’une recherche.

6. Cliquez sur Enregistrer. Votre schéma figure désormais dans la liste.

7. Choisissez **Types d’informations sensibles EDM** et **Créer un type d’informations sensibles EDM** pour ouvrir l’Assistant de configuration des types d’informations sensibles.

8. Choisissez **Choisir un schéma EDM existant** puis sélectionnez le schéma que vous avez créé dans les étapes 2-6 dans la liste.

9. Choisissez **Suivant**, puis **Créer un modèle**.

10. Choisissez le **Niveau de confiance** et l’**Élément principal**.  Pour en savoir plus sur la configuration d’un modèle, voir [Créer un type d’informations sensibles personnalisé dans le Centre de conformité](create-a-custom-sensitive-information-type.md).

11.  Choisissez le **Type d’informations sensibles de l’élément principal** à associer. Voir [Définitions des entités de types d’informations sensibles](sensitive-information-type-entity-definitions.md) pour en savoir plus sur les types d’informations sensibles disponibles.

12. Choisissez **Terminé**.

13. Choisissez vos **Niveau de confiance et proximité des caractères** souhaités.  Il s’agit de la valeur par défaut pour l’ensemble du type d’informations sensibles EDM.

13. Choisissez **Créer un modèle** si vous voulez créer des modèles supplémentaires pour votre type d’informations sensibles EDM.

14. Choisissez **Suivant**, puis entrez un **Nom** et une **Description pour les administrateurs**.

15. Passez en revue vos paramètres, puis sélectionnez **Envoyer**.

Vous pouvez supprimer ou modifier le modèle de type d’informations sensibles en le sélectionnant. Cela permet d’afficher les contrôles de modification et de suppression.

> [!IMPORTANT]
> Si vous voulez supprimer un schéma et que celui-ci est déjà associé à un type d’informations sensibles EDM, vous devez commencer par supprimer le type d’informations sensibles EDM. Vous pouvez ensuite supprimer le schéma.

## <a name="post-steps"></a>Étapes ultérieures

Une fois que vous avez utilisé cet Assistant pour créer vos fichiers de schéma et modèle EDM (package de règles), vous devez continuer à effectuer les étapes décrites dans [Partie 2 : hacher et charger les données sensibles](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md#part-2-hash-and-upload-the-sensitive-data) avant de pouvoir utiliser le type d’informations sensibles personnalisé EDM.