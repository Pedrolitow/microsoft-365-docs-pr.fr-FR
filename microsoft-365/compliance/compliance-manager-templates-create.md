---
title: Créer des modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview
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
description: Découvrez comment créer des modèles pour les évaluations dans le Gestionnaire de conformité Microsoft Purview. Créez et modifiez des modèles à l’aide d’un fichier Excel mis en forme.
ms.openlocfilehash: f7198d9b7bb9c30d388924d9c1b16a79e86bb8ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638651"
---
# <a name="create-an-assessment-template-in-microsoft-purview-compliance-manager"></a>Créer un modèle d’évaluation dans le Gestionnaire de conformité Microsoft Purview

Pour créer votre propre modèle pour les évaluations personnalisées dans le Gestionnaire de conformité, vous allez utiliser une feuille de calcul Excel spécialement mise en forme pour assembler les données de contrôle nécessaires. Une fois la feuille de calcul terminée, vous l’importerez dans le Gestionnaire de conformité.

Pour en savoir plus sur la mise en forme de votre feuille de calcul, consultez [Formater les données du modèle d’évaluation avec Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Rôles requis

Seuls les utilisateurs qui détiennent un rôle Administrateur général ou Administration du Gestionnaire de conformité peuvent créer et modifier des modèles. En savoir plus sur les [rôles et les autorisations](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>Créer un modèle dans le Gestionnaire de conformité

1. Accédez à la page **des modèles d’évaluation** dans le Gestionnaire de conformité.
2. Sélectionnez **Créer un modèle**. Un Assistant Création de modèle s’ouvre.
3. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, sélectionnez **Créer un modèle personnalisé**, puis **Sélectionnez Suivant**.
4. Dans l’écran **Charger un fichier** , **sélectionnez Parcourir** pour rechercher et charger votre fichier Excel mis en forme contenant toutes les données de modèle requises.
5. S’il n’y a aucun problème avec votre fichier, le nom du fichier chargé s’affiche. Sélectionnez **Suivant** pour continuer. (Si vous devez modifier le fichier, **sélectionnez Charger un autre fichier**).
    - En cas d’erreur avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se produit si la mise en forme de votre feuille de calcul est incorrecte ou s’il existe des informations non valides dans certains champs.
6. L’écran **Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Créer un modèle.** (Si vous devez apporter des modifications, sélectionnez **Précédent**.)
7. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.
8. Vous accédez à la page de détails de votre nouveau modèle, où vous pouvez [créer votre évaluation](compliance-manager-assessments.md#create-assessments).
