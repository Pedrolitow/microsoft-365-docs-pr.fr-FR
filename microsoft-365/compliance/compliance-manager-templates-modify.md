---
title: Modifier les modèles d’évaluation dans le Gestionnaire de conformité Microsoft
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
description: Comprendre comment modifier les modèles d’évaluation dans le Gestionnaire de conformité Microsoft.
ms.openlocfilehash: 846c3bc02105a50863afa7caca6041d9f72a5d95
ms.sourcegitcommit: 81533e5d3e1aee0823539a7c9bdc20dba6541a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60223524"
---
# <a name="modify-assessment-templates-in-microsoft-compliance-manager"></a>Modifier les modèles d’évaluation dans le Gestionnaire de conformité Microsoft

Lorsque vous travaillez avec des évaluations dans le Gestionnaire de conformité, vous pouvez modifier un modèle d’évaluation que vous avez créé. Le processus est [](compliance-manager-templates-create.md) similaire au processus de création de modèle dans la façon dont vous allez télécharger un fichier Excel formaté avec vos données de modèle.

Toutefois, vous devez connaître certains détails lorsque vous formatez votre fichier avec les modifications apportées aux données de modèle existantes. **Nous vous recommandons de consulter attentivement ces instructions pour vous assurer que vous n’avez pas de données existantes à conserver.**

Pour en savoir plus sur le format de cette feuille de calcul, voir [Formater vos](compliance-manager-templates-format-excel.md)données de modèle avec Excel .

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Mettre en forme Excel fichier pour modifier un modèle existant

Dans la page **de vos modèles d’évaluation,** sélectionnez le modèle que vous souhaitez modifier, ce qui   fera monter sa page de détails. Ensuite, **sélectionnez Exporter Excel**. Un Excel avec toutes vos données de modèle sera téléchargé. Enregistrez le fichier sur votre ordinateur local.

Pour travailler avec ce fichier, allez dans la section ci-dessous pour trouver rapidement les instructions dont vous avez besoin :

- [Modifier les attributs du modèle principal](#edit-the-main-template-attributes)
- [Ajouter une action d’amélioration](#add-an-improvement-action)
- [Modifier les informations d’une action d’amélioration](#edit-an-improvement-actions-information)
- [Modifier le nom d’une action d’amélioration](#change-an-improvement-actions-name)
- [Supprimer une action d’amélioration](#remove-an-improvement-action)
- [Supprimer un contrôle](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Modifier les attributs du modèle principal

Sous **l’onglet Modèles,** vous  pouvez modifier n’importe quoi dans la colonne de titre, la colonne **inScopeServices** et dans toute autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes **de** **produit ou de certification.**

### <a name="add-an-improvement-action"></a>Ajouter une action d’amélioration

1. Go to the **Actions** tab. Ajoutez vos informations dans les champs obligatoires de la première ligne vide sous vos actions existantes.
2. Go to your **ControlFamily** tab. Recherchez la ligne contenant le contrôle sur lequel votre action d’amélioration est m interactive. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions de ce champ par deux points-virgules, sans espace entre les deux).
3. Enregistrez votre feuille de calcul.

### <a name="edit-an-improvement-actions-information"></a>Modifier les informations d’une action d’amélioration

Vous pouvez modifier les informations de n’importe quelle action d’amélioration *à l’exception de son titre.* Vous pouvez modifier n’importe quelle cellule à partir des colonnes B et, lorsque vous importez de nouveau le fichier dans le modèle, les actions d’amélioration de ce modèle contiennent désormais les données mises à jour.

Vous ne pouvez pas modifier **l’actionTitle** (colonne A), car si vous le faites, le Gestionnaire de conformité considère qu’il s’agit d’une nouvelle action d’amélioration. Si vous souhaitez modifier le nom d’une action d’amélioration, consultez les instructions ci-dessous.

### <a name="change-an-improvement-actions-name"></a>Modifier le nom d’une action d’amélioration

Si vous souhaitez modifier le nom d’une action d’amélioration, vous devez indiquer explicitement dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Procédez comme suit :

1. Dans **l’onglet Actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne A.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placez comme en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place vos titres d’action d’amélioration existants, qui sont ce que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de votre action d’amélioration.

Notez que les titres d’action, à la fois pour vos actions d’amélioration et pour les actions Microsoft, doivent être écrits en anglais pour être reconnus lorsqu’ils sont référencés dans les contrôles.

### <a name="remove-an-improvement-action"></a>Supprimer une action d’amélioration

Pour supprimer une action d’amélioration d’un modèle, vous devez la supprimer de chaque contrôle qui le référence. Suivez les étapes ci-dessous pour modifier votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le titre de l’action d’amélioration à supprimer.
2. Supprimez le titre de l’action d’amélioration dans les cellules où elle apparaît. Si l’action d’amélioration est la seule action sur cette ligne, supprimez la ligne entière (ce qui supprime le contrôle).
3. Sous **l’onglet Actions,** supprimez la ligne qui contient l’action d’amélioration que vous supprimez.
4. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre action d’amélioration est supprimée du modèle.

La suppression d’une action d’amélioration d’un modèle ne supprime pas complètement l’action d’amélioration du Gestionnaire de conformité. Cette action peut toujours être référencé par un autre modèle.

### <a name="remove-a-control"></a>Supprimer un contrôle

Pour supprimer un contrôle, modifiez votre feuille de calcul en suivant les étapes ci-dessous, puis ré-importez votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le contrôle à supprimer dans la **colonne controlName.**
2. Supprimez la ligne de ce contrôle.
    - Si ce contrôle supprimé contient des actions d’amélioration qui ne sont référencés par aucun autre contrôle, vous devez supprimer ces actions d’amélioration de **l’onglet Actions.** Sinon, vous recevrez une erreur de validation.

3. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre contrôle est supprimé du modèle.

## <a name="modify-template-info-in-compliance-manager"></a>Modifier les informations du modèle dans le Gestionnaire de conformité

Une fois que Excel fichier est terminé et enregistré, suivez ces étapes.

1. Ouvrez à nouveau la page du modèle d’évaluation et sélectionnez votre modèle. Sur la page de détails de votre modèle, **sélectionnez Modifier le modèle** pour lancer l’Assistant Modification.
2. Dans le **Télécharger de fichier,** sélectionnez **Parcourir** pour rechercher et télécharger Excel fichier.
3. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. **Sélectionnez** Suivant pour continuer (si vous devez modifier le fichier, **sélectionnez Télécharger un autre fichier).**
    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou si certaines informations ne sont pas valides dans certains champs.

4. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant.**
5. Le dernier écran confirme que le modèle a été modifié. Sélectionnez **Terminé** pour quitter l’Assistant.

Votre modèle inclut désormais les modifications que vous avez apportées. Toutes les évaluations qui utilisent ce modèle modifié afficheront désormais les mises à jour en attente, et vous devrez accepter les mises à jour des évaluations pour refléter les modifications apportées dans le modèle. En savoir plus sur [les mises à jour des évaluations.](compliance-manager-assessments.md#accept-updates-to-assessments)

> [!NOTE]
> Si vous utilisez le Gestionnaire de conformité dans une langue autre que l’anglais, vous remarquerez qu’un texte s’affiche en anglais lorsque vous exportez un modèle vers Excel. Les titres des actions (vos actions d’amélioration et, le cas échéant, les actions Microsoft) doivent être en anglais pour être reconnus par les contrôles. Si vous modifiez un titre d’action, veillez à l’écrire en anglais afin que le fichier importe correctement.
