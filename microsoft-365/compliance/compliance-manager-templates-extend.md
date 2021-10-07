---
title: Étendre les modèles d’évaluation dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment étendre les modèles d’évaluation dans le Gestionnaire de conformité Microsoft pour ajouter et modifier des contrôles.
ms.openlocfilehash: a255b3787a1da66be5882f00854d5a73cfe0352e
ms.sourcegitcommit: 81533e5d3e1aee0823539a7c9bdc20dba6541a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60223516"
---
# <a name="extend-assessment-templates-in-microsoft-compliance-manager"></a>Étendre les modèles d’évaluation dans le Gestionnaire de conformité Microsoft

Le Gestionnaire de conformité offre la possibilité d’ajouter vos propres contrôles et actions d’amélioration à un modèle existant. Ce processus est appelé extension d’un modèle.

Pour étendre un modèle, vous allez utiliser des instructions spéciales pour modifier les données des modèles, selon que vous étendez des modèles d’évaluation Microsoft 365 ou universels.

## <a name="extend-microsoft-365-assessment-templates"></a>Étendre Microsoft 365 modèles d’évaluation

Lorsque vous étendez un modèle Microsoft 365, il peut toujours recevoir des mises à jour publiées par Microsoft, ce qui peut se produire lorsque des modifications sont [apportées](compliance-manager-assessments.md#accept-updates-to-assessments)à la réglementation ou au produit associé (voir Accepter les mises à jour des évaluations).

### <a name="prepare-template-data-and-create-extension"></a>Préparer les données de modèle et créer une extension

Pour vous préparer, vous devez assembler une feuille de calcul Excel spécialement mise en forme pour importer les données de modèle nécessaires. Les fichiers Excel suivent le même format décrit dans les données du modèle d’évaluation de format avec [Excel,](compliance-manager-templates-format-excel.md)mais il existe des exigences spéciales pour les extensions. Consultez ces points supplémentaires pour éviter les erreurs :

- Votre feuille de calcul doit contenir uniquement les actions et les contrôles que vous souhaitez ajouter à l’évaluation.
- La feuille de calcul ne peut contenir aucun des contrôles ou actions qui existent déjà dans l’évaluation que vous souhaitez modifier.
- Envisagez d’inclure « extension » dans le titre de votre modèle, par exemple, « R GDPR – extension [nom de votre société] ». Cela facilite l’identification, dans la liste de vos **modèles** d’évaluation, du modèle standard fourni par Microsoft ou d’un modèle personnalisé avec un nom similaire.

Après avoir formaté votre feuille de calcul, suivez les étapes ci-dessous.

1. Go to your **Assessment templates** page and select **Create new template**. Un Assistant Création de modèle s’ouvre.

2. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Étendre un modèle Microsoft,** puis **sélectionnez Modèle Microsoft.**

3. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran, affichant la liste de tous les modèles et leur statut d’actif ou inactif. Votre **compteur de modèles activés** indique le nombre de modèles actuellement utilisés sur le nombre total disponible. Si vous avez terminé votre limite, une barre de messages vous fournira un avis.

4. Un volet volant de sélection de modèle s’affiche sur le côté droit de votre écran. Utiliser **la recherche** pour appliquer des filtres pour localiser le modèle de votre recherche

5. Une fois que vous avez localisé votre modèle, sélectionnez la radio à gauche de son nom, puis sélectionnez **Enregistrer**.

6. L’écran suivant montre le modèle que vous avez sélectionné. Si la réponse est correcte, sélectionnez **Suivant.** (Si ce n’est pas le cas, **sélectionnez Sélectionner** un autre modèle à choisir à nouveau.)

7. Dans le **Télécharger** de fichiers,  sélectionnez Parcourir pour rechercher et télécharger votre fichier Excel formaté contenant toutes les données de modèle requises.

8. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. Sélectionnez Suivant pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).** 

    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devrez corriger et charger à l’autre votre fichier. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.

9. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant**. (Si vous devez apporter des modifications, **sélectionnez Télécharger fichier différent.)**

10. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.

11. Vous arrivez à la page de détails de votre nouveau modèle. À partir de là, vous pouvez créer votre évaluation en sélectionnant **Créer une évaluation.** Pour obtenir des conseils, [voir Créer et gérer des évaluations.](compliance-manager-assessments.md#create-assessments)

## <a name="extend-universal-assessment-templates"></a>Étendre les modèles d’évaluation universels

Les versions universelles des modèles peuvent également être étendues pour personnaliser vos évaluations spécifiques à vos produits. Vous recevrez un modèle d’extension spécial lorsque vous créerez une évaluation à l’aide d’un modèle universel et que l’évaluation possède une combinaison de produit et de certification unique. Ce fichier peut être modifié pour répondre à vos besoins. Pour obtenir des instructions sur la modification du modèle, consultez les instructions sur [la modification d’un modèle.](compliance-manager-templates-modify.md)

Lors de la modification d’un modèle universel, tout le contenu du modèle peut être modifié, mais cela va rompre l’héritage avec le modèle parent. Cela signifie qu’il ne recevra plus automatiquement les mises à jour de Microsoft si le modèle parent est actualisé.
