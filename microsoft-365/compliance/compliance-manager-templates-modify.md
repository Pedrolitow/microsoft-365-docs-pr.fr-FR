---
title: Modifier des modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview
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
description: Découvrez comment modifier des modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview.
ms.openlocfilehash: f21ff61f6bb06f00d1db8381e3760e7c4b5343aa
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630408"
---
# <a name="modify-assessment-templates-in-microsoft-purview-compliance-manager"></a>Modifier des modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview

Lorsque vous travaillez avec des évaluations dans le Gestionnaire de conformité, vous pouvez modifier un modèle d’évaluation que vous avez créé. Le processus est similaire au processus de [création de modèle](compliance-manager-templates-create.md) , dans le cas où vous allez charger un fichier Excel mis en forme avec vos données de modèle.

Toutefois, il existe des détails à prendre en compte lorsque vous mettez en forme votre fichier avec des modifications apportées aux données de modèle existantes. **Nous vous recommandons de consulter attentivement ces instructions pour vous assurer que vous ne remplacez pas les données existantes que vous souhaitez conserver.**

Pour en savoir plus sur le format de cette feuille de calcul, consultez [Mettre en forme vos données de modèle avec Excel](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Mettre en forme votre fichier Excel pour modifier un modèle existant

Dans la page **des modèles d’évaluation** , sélectionnez le modèle à modifier, qui affichera sa page de détails. Sélectionnez Ensuite **Exporter vers Excel**. Un fichier Excel avec toutes vos données de modèle sera téléchargé. Enregistrez le fichier sur votre ordinateur local.

Pour utiliser ce fichier, accédez à une section ci-dessous pour trouver rapidement les instructions dont vous avez besoin :

- [Modifier les attributs de modèle principaux](#edit-the-main-template-attributes)
- [Ajouter une action d’amélioration](#add-an-improvement-action)
- [Modifier les informations d’une action d’amélioration](#edit-an-improvement-actions-information)
- [Modifier le nom d’une action d’amélioration](#change-an-improvement-actions-name)
- [Supprimer une action d’amélioration](#remove-an-improvement-action)
- [Supprimer un contrôle](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Modifier les attributs de modèle principaux

Sous l’onglet **Modèles** , vous pouvez modifier n’importe quel élément de la colonne **de titre** , de la colonne **inScopeServices** et de toute autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes **de produit** ou **de certification** .

### <a name="add-an-improvement-action"></a>Ajouter une action d’amélioration

1. Accédez à l’onglet **Actions** . Ajoutez vos informations dans les champs requis dans la première ligne vide sous vos actions existantes.
2. Accédez à l’onglet **ControlFamily** . Recherchez la ligne contenant le contrôle auquel votre action d’amélioration est mappée. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions dans ce champ par deux points-virgules, aucun espace entre les deux).
3. Enregistrez votre feuille de calcul.

### <a name="edit-an-improvement-actions-information"></a>Modifier les informations d’une action d’amélioration

Vous pouvez modifier les informations de n’importe quelle action d’amélioration *à l’exception de son titre*. Vous pouvez modifier n’importe quelle cellule à partir des colonnes B et, lorsque vous importez le fichier dans le modèle, les actions d’amélioration de ce modèle contiendront désormais les données mises à jour.

Vous ne pouvez pas modifier **l’actionTitle** (colonne A), car si c’est le cas, le Gestionnaire de conformité considère qu’il s’agit d’une nouvelle action d’amélioration. Si vous souhaitez modifier le nom d’une action d’amélioration, consultez les instructions ci-dessous.

### <a name="change-an-improvement-actions-name"></a>Modifier le nom d’une action d’amélioration

Si vous souhaitez modifier le nom d’une action d’amélioration, vous devez désigner explicitement dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Procédez comme suit :

1. Sous l’onglet **Actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne A.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placez son en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place vos titres d’action d’amélioration existants, qui sont ce que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de votre action d’amélioration.

Notez que les titres des actions, à la fois pour vos actions d’amélioration et pour les actions Microsoft, doivent être écrits en anglais afin d’être reconnus lorsqu’ils sont référencés dans des contrôles.

### <a name="remove-an-improvement-action"></a>Supprimer une action d’amélioration

Pour supprimer une action d’amélioration d’un modèle, vous devez la supprimer de chaque contrôle qui le référence. Suivez les étapes ci-dessous pour modifier votre feuille de calcul :

1. Sous l’onglet **ControlFamily** , recherchez le titre de l’action d’amélioration à supprimer.
2. Supprimez le titre de l’action d’amélioration dans les cellules où elle apparaît. Si l’action d’amélioration est la seule action sur cette ligne, supprimez la ligne entière (ce qui supprime le contrôle).
3. Sous l’onglet **Actions** , supprimez la ligne qui contient l’action d’amélioration que vous supprimez.
4. Enregistrez votre feuille de calcul.

Lorsque vous importez votre feuille de calcul dans le modèle, votre action d’amélioration est supprimée du modèle.

La suppression d’une action d’amélioration d’un modèle ne supprime pas complètement l’action d’amélioration du Gestionnaire de conformité. Cette action peut toujours être référencée par un autre modèle.

### <a name="remove-a-control"></a>Supprimer un contrôle

Pour supprimer un contrôle, modifiez votre feuille de calcul en suivant les étapes ci-dessous, puis réimportez votre feuille de calcul :

1. Sous l’onglet **ControlFamily** , recherchez le contrôle à supprimer dans la colonne **controlName** .
2. Supprimez la ligne de ce contrôle.
    - Si ce contrôle supprimé contient des actions d’amélioration qui ne sont référencées par aucun autre contrôle, vous devez supprimer ces actions d’amélioration de l’onglet **Actions** . Sinon, vous recevrez une erreur de validation.

3. Enregistrez votre feuille de calcul.

Lorsque vous importez votre feuille de calcul dans le modèle, votre contrôle est supprimé du modèle.

## <a name="modify-template-info-in-compliance-manager"></a>Modifier les informations de modèle dans le Gestionnaire de conformité

Une fois votre fichier Excel terminé et enregistré, procédez comme suit.

1. Rouvrez la page du modèle d’évaluation et sélectionnez votre modèle. Dans la page de détails de votre modèle, sélectionnez **Modifier le modèle** pour lancer l’Assistant modification.
2. Dans l’écran **Charger un fichier** , **sélectionnez Parcourir** pour rechercher et charger votre fichier Excel.
3. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier chargé. Sélectionnez **Suivant** pour continuer (si vous devez modifier le fichier, **sélectionnez Charger un autre fichier**).
    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se produit si la mise en forme de votre feuille de calcul est incorrecte ou s’il existe des informations non valides dans certains champs.

4. L’écran **Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant**.
5. Le dernier écran confirme que le modèle a été modifié. Sélectionnez **Terminé** pour quitter l’Assistant.

Votre modèle inclut désormais les modifications que vous avez apportées. Toutes les évaluations qui utilisent ce modèle modifié affichent désormais les mises à jour en attente, et vous devez accepter les mises à jour des évaluations pour refléter les modifications apportées dans le modèle. En savoir plus sur [les mises à jour des évaluations](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Si vous utilisez le Gestionnaire de conformité dans une langue autre que l’anglais, vous remarquerez que du texte apparaît en anglais lorsque vous exportez un modèle vers Excel. Les titres des actions (à la fois vos actions d’amélioration et, le cas échéant, les actions Microsoft) doivent être en anglais pour être reconnus par les contrôles. Si vous apportez des modifications à un titre d’action, veillez à l’écrire en anglais afin que le fichier soit importé correctement.
