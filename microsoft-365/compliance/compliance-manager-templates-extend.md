---
title: Étendre les modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Découvrez comment étendre des modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview pour ajouter et modifier des contrôles.
ms.openlocfilehash: b4cf642e7b5a9dac47cd513251c05a802f16b77b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630452"
---
# <a name="extend-assessment-templates-in-microsoft-purview-compliance-manager"></a>Étendre les modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview

Le Gestionnaire de conformité offre la possibilité d’ajouter vos propres contrôles et actions d’amélioration à un modèle existant. Ce processus est appelé extension d’un modèle.

Pour étendre un modèle, vous allez utiliser des instructions spéciales pour modifier les données de modèle, selon que vous étendez des modèles d’évaluation Microsoft ou des modèles d’évaluation universels.

## <a name="extend-microsoft-assessment-templates"></a>Étendre les modèles d’évaluation Microsoft

Lorsque vous étendez un modèle Microsoft, tel qu’un modèle créé pour une utilisation avec Microsoft 365, il peut toujours recevoir des mises à jour publiées par Microsoft. Mises à jour peut se produire en cas de modifications apportées à la réglementation ou au produit associé (voir [Accepter les mises à jour des évaluations](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Préparer des données de modèle et créer une extension

Pour vous préparer, vous devez assembler une feuille de calcul Excel spécialement mise en forme pour importer les données de modèle nécessaires. Les fichiers Excel suivent le même format que celui décrit dans [Formater les données du modèle d’évaluation avec Excel](compliance-manager-templates-format-excel.md), mais il existe des exigences spéciales pour les extensions. Consultez ces points supplémentaires pour éviter les erreurs :

- Votre feuille de calcul doit contenir uniquement les actions et les contrôles que vous souhaitez ajouter à l’évaluation.
- La feuille de calcul ne peut contenir aucun des contrôles ou actions qui existent déjà dans l’évaluation que vous souhaitez modifier.
- Envisagez d’inclure « extension » dans le titre de votre modèle, par exemple « RGPD – [nom de votre entreprise] extension ». Cela facilite l’identification dans la liste de la page **de vos modèles d’évaluation** comme étant différente du modèle standard fourni par Microsoft ou d’un modèle personnalisé portant un nom similaire.

Après avoir mis en forme votre feuille de calcul, suivez les étapes ci-dessous.

1. Accédez à la page **Modèles d’évaluation** , puis **sélectionnez Créer un nouveau modèle**. Un Assistant Création de modèle s’ouvre.

2. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, sélectionnez **Étendre un modèle Microsoft**, puis **sélectionnez le modèle Microsoft**.

3. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran, affichant la liste de tous les modèles et leur état actif ou inactif. Votre compteur **de modèles activés** indique le nombre de modèles actuellement utilisés sur le nombre total disponible à utiliser. Si vous dépassez votre limite, une barre de messages vous avertira.

4. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran. Utiliser **la recherche** pour appliquer des filtres pour localiser le modèle souhaité

5. Une fois que vous avez localisé votre modèle, sélectionnez la case d’option à gauche de son nom, puis **sélectionnez Enregistrer**.

6. L’écran suivant montre le modèle que vous avez sélectionné. Si c’est le cas, sélectionnez **Suivant**. (Si ce n’est pas correct, **choisissez Sélectionner un autre modèle** à choisir à nouveau.)

7. Dans l’écran **Charger un fichier** , **sélectionnez Parcourir** pour rechercher et charger votre fichier Excel mis en forme contenant toutes les données de modèle requises.

8. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier chargé. Sélectionnez **Suivant** pour continuer (si vous devez modifier le fichier, **sélectionnez Charger un autre fichier**).

    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger et charger à nouveau votre fichier. Des erreurs se produit si la mise en forme de votre feuille de calcul est incorrecte ou s’il existe des informations non valides dans certains champs.

9. L’écran **Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant**. (Si vous devez apporter des modifications, **sélectionnez Charger un autre fichier**.)

10. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.

11. Vous arriverez à la page de détails de votre nouveau modèle. À partir de là, vous pouvez créer votre évaluation en sélectionnant **Créer une évaluation**. Pour obtenir des conseils, consultez [Générer et gérer des évaluations](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Étendre les modèles d’évaluation universels

Les versions universelles des modèles peuvent également être étendues pour personnaliser vos évaluations spécifiques au produit. Vous recevrez un modèle d’extension spécial lorsque vous créez une évaluation à l’aide d’un modèle universel et que l’évaluation a une combinaison de produit et de certification unique. Ce fichier peut être modifié pour répondre à vos besoins. Pour obtenir des conseils sur la modification du modèle, consultez les instructions sur la [modification d’un modèle](compliance-manager-templates-modify.md).

Lors de la modification d’un modèle universel, tout le contenu du modèle peut être modifié, mais cela interrompt l’héritage avec le modèle parent. Cela signifie qu’il ne recevra plus automatiquement les mises à jour de Microsoft si le modèle parent est actualisé.
