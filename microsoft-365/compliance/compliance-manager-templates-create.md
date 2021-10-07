---
title: Créer des modèles d’évaluation dans le Gestionnaire de conformité Microsoft
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
description: Comprendre comment créer des modèles d’évaluations dans le Gestionnaire de conformité Microsoft. Créez et modifiez des modèles à l’aide d’un fichier Excel formaté.
ms.openlocfilehash: 5db58b1032f5c654f1c02b81c7d1b6929a9078c7
ms.sourcegitcommit: 81533e5d3e1aee0823539a7c9bdc20dba6541a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60223523"
---
# <a name="create-an-assessment-template-in-microsoft-compliance-manager"></a>Créer un modèle d’évaluation dans le Gestionnaire de conformité Microsoft

Pour créer votre propre modèle d’évaluations personnalisées dans le Gestionnaire de conformité, vous allez utiliser une feuille de calcul Excel spécialement mise en forme pour assembler les données de contrôle nécessaires. Après avoir terminé la feuille de calcul, vous l’importez dans le Gestionnaire de conformité.

Pour en savoir plus sur la mise en forme de votre feuille de calcul, voir [Formater](compliance-manager-templates-format-excel.md)les données de modèle d’évaluation Excel .

## <a name="required-roles"></a>Rôles requis

Seuls les utilisateurs qui détiennent un rôle d’administrateur général ou d’administration du Gestionnaire de conformité peuvent créer et modifier des modèles. En savoir plus sur [les rôles et les autorisations.](compliance-manager-setup.md#set-user-permissions-and-assign-roles)

## <a name="create-new-template-in-compliance-manager"></a>Créer un modèle dans le Gestionnaire de conformité

1. Go to your **assessment templates** page in Compliance Manager.
2. Sélectionnez **Créer un modèle.** Un Assistant Création de modèle s’ouvre.
3. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Créer un modèle personnalisé,** puis sélectionnez **Suivant.**
4. Dans le **Télécharger** de fichiers,  sélectionnez Parcourir pour rechercher et télécharger votre fichier Excel formaté contenant toutes les données de modèle requises.
5. En l’absence de problème avec votre fichier, le nom du fichier téléchargé s’affiche. Sélectionnez **Suivant** pour continuer. (Si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).**
    - En cas d’erreur avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.
6. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, **sélectionnez Créer un modèle.** (Si vous devez apporter des modifications, sélectionnez **Retour.)**
7. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.
8. Vous arrivez à la page de détails de votre nouveau modèle, où vous pouvez [créer votre évaluation.](compliance-manager-assessments.md#create-assessments)
