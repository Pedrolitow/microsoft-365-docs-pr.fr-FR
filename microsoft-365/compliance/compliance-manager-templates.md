---
title: Utiliser des modèles d’évaluation dans le Gestionnaire de conformité Microsoft
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Comprendre comment utiliser et gérer des modèles pour la création d’évaluations dans le Gestionnaire de conformité Microsoft. Créez et modifiez des modèles à l’aide d’un fichier Excel formaté.
ms.openlocfilehash: 34adb79392b235152cc0e00f5b7d661e90c9005e
ms.sourcegitcommit: 00d231bf0100e843a5a93161695e87ceff9e1349
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49849608"
---
# <a name="working-with-assessment-templates-in-compliance-manager"></a>Utiliser des modèles d’évaluation dans le Gestionnaire de conformité

**Dans cet article :** Comprendre **comment fonctionnent les modèles** et **comment les gérer** à partir de votre page de modèles d’évaluation. Obtenez des instructions pour **créer** des modèles,  modifier des modèles existants, mettre en forme vos données de modèle avec **Excel** et exporter des rapports de **modèles.**

> [!IMPORTANT]
> Les modèles d’évaluation disponibles pour votre organisation dépendent de votre contrat de licence. [Examinez les détails.](https://go.microsoft.com/fwlink/?linkid=2132371)

## <a name="templates-overview"></a>Vue d’ensemble des modèles

Un modèle est une infrastructure permettant de créer une évaluation dans le Gestionnaire de conformité. Ils contiennent les contrôles pour répondre aux exigences d’une certification à l’aide d’un produit spécifique. Le Gestionnaire de conformité fournit un ensemble complet de modèles pour aider votre organisation à se conformer aux exigences nationales, régionales et propres au secteur régissant la collecte et l’utilisation des données.

## <a name="list-of-pre-built-templates-for-assessments"></a>Liste des modèles pré-créés pour les évaluations

Le Gestionnaire de conformité fournit des modèles pour la création d’évaluations afin de vous aider à vous conformer à différentes réglementations et normes. Affichez [la liste des modèles fournis](compliance-manager-templates-list.md) par le Gestionnaire de conformité. De nouveaux modèles sont ajoutés régulièrement. Vérifiez donc souvent la liste.

## <a name="viewing-and-managing-templates-from-the-assessment-templates-page"></a>Affichage et gestion des modèles à partir de la page modèles d’évaluation

La page modèles d’évaluation dans le Gestionnaire de conformité affiche une liste de modèles et de détails clés. La liste inclut les modèles fournis par le Gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle basé sur la certification, l’étendue du produit, le pays, l’industrie, qui l’a créé et si le modèle est activé pour la création d’évaluation.

Sélectionnez un modèle dans sa ligne pour faire monter sa page de détails. Cette page contient une description du modèle et des informations supplémentaires sur la certification, l’étendue et les détails des contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

## <a name="creating-and-modifying-templates-overview"></a>Vue d’ensemble de la création et de la modification des modèles

Pour modifier un modèle existant ou créer votre propre modèle, vous allez utiliser[](https://go.microsoft.com/fwlink/?linkid=2124865)une feuille de calcul Excel spécialement mise en forme (téléchargez un exemple) pour assembler les données de contrôle nécessaires. Après avoir terminé la feuille de calcul, vous l’importez dans le Gestionnaire de conformité pendant le processus de création ou de modification d’un modèle.

> [!NOTE]
> La feuille de calcul possède un format et un schéma spécifiques qui doivent être utilisés, sinon elle ne sera pas importée correctement dans le Gestionnaire de conformité. Les [instructions de mise en forme sont](#formatting-your-template-data-with-excel) ci-dessous.

**Rôles requis**

Seuls les utilisateurs qui détiennent un rôle d’administrateur général ou d’administration du Gestionnaire de conformité peuvent créer et modifier des modèles. En savoir plus sur [les rôles et les autorisations.](compliance-manager-setup.md#set-user-permissions-and-assign-roles)

## <a name="create-a-new-template"></a>Créer un modèle

Pour créer votre propre modèle (utilisé pour créer des évaluations personnalisées), suivez les étapes ci-dessous.

1. Go to your **assessment templates** page in Compliance Manager.
2. Sélectionnez **Créer un modèle.** Un Assistant Création de modèle s’ouvre.
3. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, **sélectionnez Créer un modèle personnalisé,** puis **sélectionnez Suivant**.
4. Dans **l’écran** Télécharger un fichier, sélectionnez **Parcourir** pour rechercher et télécharger votre fichier Excel mis en forme contenant toutes les données de modèle requises (voir les instructions pour mettre correctement en forme [votre fichier).](#formatting-your-template-data-with-excel)
5. En l’absence de problème avec votre fichier, le nom du fichier téléchargé s’affiche. Sélectionnez **Suivant** pour continuer. (Si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).**
    - En cas d’erreur avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs (reportez-vous à nouveau aux [instructions de mise en forme).](#formatting-your-template-data-with-excel)  
    
6. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, **sélectionnez Créer un modèle.** (Si vous devez apporter des modifications, sélectionnez **Retour.)**
7. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **Terminé** pour quitter l’Assistant.
8. Vous arrivez à la page de détails de votre nouveau modèle, où vous pouvez [créer votre évaluation.](compliance-manager-assessments.md#create-your-own-custom-assessment)

## <a name="formatting-your-template-data-with-excel"></a>Mise en forme de vos données de modèle avec Excel

La feuille de calcul Excel utilisée pour créer des modèles contient quatre onglets, dont trois sont requis :

1. [Modèle](#template-tab) (obligatoire)
2. [ControlFamily](#controlfamily-tab) (obligatoire)
3. [Actions](#actions-tab) (obligatoires)
4. [Dimensions](#dimensions-tab) (facultatif)

Lorsque vous remplissez votre feuille de calcul avec des données de modèle, la feuille de calcul doit inclure les  **onglets** dans l’ordre répertorié ci-dessus, sinon vos données ne seront pas correctement importées dans un modèle.

##### <a name="template-tab"></a>Onglet Modèle

**L’onglet** Modèle est obligatoire. Les informations de cet onglet fournissent des métadonnées sur le modèle. Il existe quatre colonnes obligatoires. Les colonnes doivent conserver l’ordre dans la feuille Excel, comme répertorié ci-dessous. Vous pouvez ajouter votre propre colonne **après les** quatre colonnes pour fournir vos propres dimensions. Si vous le faites, n’oubliez pas de les ajouter à l’onglet **Dimensions** en suivant les [instructions ci-dessous.](#dimensions-tab)

- **titre**: il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le Gestionnaire de conformité, y compris vos propres modèles ou un modèle gestionnaire de conformité.

- **produit**: il s’agit d’une dimension obligatoire. Liste du produit associé au modèle.

- **certification**: il s’agit de la réglementation que vous utilisez pour le modèle.

- **inScopeServices**: il s’agit des services dans le produit que cette évaluation traite (par exemple, si vous avez répertorié Office 365 comme produit, Microsoft Teams peut être un service dans l’étendue). Vous pouvez lister plusieurs services séparés par deux points-virgules.

> [!NOTE]
> Les données que  vous insérez dans les cellules de produit et de **certification** ne peuvent pas être modifiées après avoir importé la feuille de calcul pour créer ou personnaliser un modèle. En outre, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison **produit/certification.** Vous pouvez avoir plusieurs modèles avec la même combinaison produit/certification.

##### <a name="controlfamily-tab"></a>Onglet ControlFamily

**L’onglet ControlFamily** est obligatoire.  Les colonnes requises dans cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **controlName :** il s’agit du nom du contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms des contrôles doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles du même nom dans la feuille de calcul.

- **controlFamily**: fournissez un mot ou une expression pour le controlFamily, qui identifie un groupe étendu de contrôles. Un controlFamily n’a pas besoin d’être unique ; Il peut être répertorié plusieurs fois dans une feuille de calcul. Le même controlFamily peut également être répertorié dans plusieurs modèles, bien qu’ils n’ont aucune relation les uns avec les autres. Chaque controlFamily doit être mappé sur au moins un contrôle.

- **controlTitle**: fournir un titre pour le contrôle. Alors que controlName est un code de référence, le titre est un format de texte enrichi généralement vu dans les réglementations.

- **controlDescription**: fournir une description du contrôle.

- **controlActionTitle**: il s’agit du titre d’une action que vous souhaitez mettre en relation avec ce contrôle. Vous pouvez ajouter plusieurs actions en les séparant par deux points-virgules sans espace. Chaque contrôle que vous listez doit inclure au moins une action et l’action doit exister (ce qui signifie que vous pouvez lister une action que vous avez répertoriée sous l’onglet **Actions** de la même feuille de calcul, une action qui existe dans un autre modèle ou une action créée par Microsoft). Différents contrôles peuvent faire référence à la même action.

##### <a name="actions-tab"></a>Onglet Actions

**L’onglet Actions** est obligatoire.  Il désigne les actions d’amélioration gérées par votre organisation et non celles de Microsoft, qui existent déjà dans le Gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **actionTitle**: il s’agit du titre de votre action et d’un champ obligatoire. Le titre que vous fournissez doit être unique. **Important**: si vous référencez une action que vous possédez qui existe déjà (par exemple dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications se propagent à la même action dans d’autres modèles.

- **implementationType**: dans ce champ obligatoire, listez l’un des trois types d’implémentation ci-dessous :
    - **Opérationnel** : actions implémentées par les personnes et les processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des ressources, des données et du personnel (exemple : sensibilisation et formation en matière de sécurité)
    - Technique **:** actions effectuées par le biais de l’utilisation de la technologie et des mécanismes contenus dans les composants matériels, logiciels ou microprogrammes du système d’information pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes et données de l’organisation (exemple : authentification multifacteur)
    - **Documentation** : actions implémentées par le biais de stratégies et de procédures documentées établissant et définissant les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des biens, des données et du personnel (par exemple, une stratégie de sécurité des informations)

- **actionScore**: dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. Il doit s’agit d’un nombre entier compris entre 1 et 99 ; il ne peut pas être 0, null ou vide. Plus le nombre est élevé, plus sa valeur est grande pour améliorer votre posture de conformité. L’image ci-dessous montre comment le Gestionnaire de conformité contrôle les scores :

![Le Gestionnaire de conformité contrôle les valeurs de point](../media/compliance-score-action-scoring.png "Le Gestionnaire de conformité contrôle les valeurs de point")

- **actionDescriptionTitle**: il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et d’en faire une description différente dans chaque modèle.  Ce champ vous aide à clarifier le modèle référent de la description. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription**: fournir une description de l’action. Vous pouvez appliquer une mise en forme telle que du texte gras et des liens hypertexte. Ce champ est obligatoire.

- **dimension-Action Purpose**: il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension - ». Toutes les dimensions que vous incluez ici seront utilisées comme filtres dans le Gestionnaire de conformité et apparaîtront dans la page détails des actions d’amélioration dans le Gestionnaire de conformité.

##### <a name="dimensions-tab"></a>Onglet Dimensions

**L’onglet Dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: liste en tant que « produit », « certifications », « objectif de l’action »
- **dimensionValue :** exemples : Office 365, HIPPA, Préventive, Inspecteur

Vous pouvez afficher vos dimensions existantes en allant dans **Gestion** des clients et en sélectionnant l’onglet **Dimensions.** En outre, chaque fois que vous exportez un modèle existant, la feuille de calcul exportée aura l’onglet **Dimensions,** qui répertorie toutes les dimensions utilisées dans le modèle.

## <a name="modify-a-template"></a>Modifier un modèle

Vous pouvez modifier un modèle que vous avez déjà créé, par exemple pour ajouter des contrôles ou ajouter ou supprimer des actions d’amélioration. Le processus est similaire au processus de création de modèle dans la façon dont vous allez charger le fichier Excel mis en forme avec vos données de modèle.

Toutefois, il existe des détails particuliers à prendre en compte lorsque vous formatez votre fichier avec les modifications apportées aux données de modèle existantes. **Nous vous recommandons de consulter attentivement ces instructions pour vous assurer que vous n’avez pas de données existantes à conserver.**

### <a name="template-modification-process-steps"></a>Étapes du processus de modification des modèles

Pour modifier un modèle, suivez les étapes ci-dessous :

1. Dans la page **de vos modèles d’évaluation,** sélectionnez le modèle que vous souhaitez modifier, ce qui fera monter sa page de détails.
2. Sélectionnez **Exporter vers Excel.** Un fichier Excel avec toutes vos données de modèle sera téléchargé. Enregistrez le fichier sur votre ordinateur local.
3. A apporter des modifications à votre modèle [en modifiant le fichier Excel à l’aide des instructions ci-dessous.](#formatting-your-excel-file-to-modify-a-template)
4. Lorsque vous avez terminé d’apporter des modifications à votre fichier Excel, enregistrez-le.
5. Sur la page de détails de votre modèle, **sélectionnez Modifier le modèle** pour lancer l’Assistant Modification. 
6. Dans **l’écran Télécharger** un fichier, **sélectionnez Parcourir** pour rechercher et télécharger votre fichier Excel.
7. S’il n’y a aucun problème avec votre fichier, l’écran suivant affiche le nom du fichier téléchargé. Sélectionnez Suivant pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier).** 
    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui ne va pas. Vous devez corriger votre fichier et le charger à nouveau. Des erreurs se résultent si votre feuille de calcul n’est pas correctement mise en forme ou s’il existe des informations non valides dans certains champs.

8. **L’écran Révision et fin** affiche le nombre d’actions et de contrôles d’amélioration et le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **Suivant.**
9. Le dernier écran confirme que le modèle a été modifié. Sélectionnez **Terminé** pour quitter l’Assistant.

Votre modèle inclut désormais les modifications que vous avez apportées. Toutes les évaluations qui utilisent ce modèle modifié afficheront désormais les mises à jour en attente, et vous devrez accepter les mises à jour des évaluations pour refléter les modifications apportées dans le modèle. En savoir plus sur [les mises à jour des évaluations.](compliance-manager-assessments.md#accepting-updates-to-assessments)

> [!NOTE]
> Si vous utilisez le Gestionnaire de conformité dans une langue autre que l’anglais, vous remarquerez qu’un texte s’affiche en anglais lorsque vous exportez un modèle vers Excel. Les titres des actions (vos actions d’amélioration et les actions Microsoft) doivent être en anglais pour être reconnus par les contrôles. Si vous modifiez un titre d’action, veillez à l’écrire en anglais afin que le fichier importe correctement.

### <a name="formatting-your-excel-file-to-modify-a-template"></a>Mise en forme de votre fichier Excel pour modifier un modèle

Pour trouver rapidement les instructions dont vous avez besoin, voir la section ci-dessous :

- [Modifier les attributs du modèle principal](#edit-the-main-template-attributes)
- [Ajouter une action d’amélioration](#add-an-improvement-action)
- [Modifier les informations d’une action d’amélioration](#edit-an-improvement-actions-information)
- [Modifier le nom d’une action d’amélioration](#change-an-improvement-actions-name)
- [Supprimer une action d’amélioration](#remove-an-improvement-action)
- [Supprimer un contrôle](#remove-a-control)

#### <a name="edit-the-main-template-attributes"></a>Modifier les attributs du modèle principal

Sous **l’onglet Modèles,** vous  pouvez modifier n’importe quoi dans la colonne de titre, la colonne **inScopeServices** et dans toute autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes **de** **produit ou de certification.**

#### <a name="add-an-improvement-action"></a>Ajouter une action d’amélioration

1. Go to the **Actions** tab. Ajoutez vos informations dans les champs obligatoires de la première ligne vide sous vos actions existantes.
2. Go to your **ControlFamily** tab. Recherchez la ligne contenant le contrôle sur lequel votre action d’amélioration est m interactive. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions de ce champ par deux points-virgules, sans espace entre les deux).
3. Enregistrez votre feuille de calcul.

#### <a name="edit-an-improvement-actions-information"></a>Modifier les informations d’une action d’amélioration

Vous pouvez modifier les informations de n’importe quelle action d’amélioration *à l’exception de son titre.* Vous pouvez modifier n’importe quelle cellule à partir des colonnes B et, lorsque vous importez de nouveau le fichier dans le modèle, les actions d’amélioration de ce modèle contiennent désormais les données mises à jour.

Vous ne pouvez pas modifier **actionTitle** (colonne A), car si vous le faites, le Gestionnaire de conformité considère qu’il s’agit d’une nouvelle action d’amélioration. Si vous souhaitez modifier le nom d’une action d’amélioration, consultez les instructions ci-dessous.

#### <a name="change-an-improvement-actions-name"></a>Modifier le nom d’une action d’amélioration

Si vous souhaitez modifier le nom d’une action d’amélioration, vous devez indiquer explicitement dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Procédez comme suit :

1. Dans **l’onglet Actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne A.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placez comme en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place vos titres d’action d’amélioration existants, qui sont ce que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de votre action d’amélioration.

Notez que les titres d’action, à la fois pour vos actions d’amélioration et pour les actions Microsoft, doivent être écrits en anglais pour être reconnus lorsqu’ils sont référencés dans les contrôles.

#### <a name="remove-an-improvement-action"></a>Supprimer une action d’amélioration

Pour supprimer une action d’amélioration d’un modèle, vous devez la supprimer de chaque contrôle qui le référence. Suivez les étapes ci-dessous pour modifier votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le titre de l’action d’amélioration à supprimer.
2. Supprimez le titre de l’action d’amélioration dans les cellules où elle apparaît. Si l’action d’amélioration est la seule action sur cette ligne, supprimez la ligne entière (ce qui supprime le contrôle).
3. Sous **l’onglet Actions,** supprimez la ligne qui contient l’action d’amélioration que vous supprimez.
4. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre action d’amélioration est supprimée du modèle.

La suppression d’une action d’amélioration d’un modèle ne supprime pas complètement l’action d’amélioration du Gestionnaire de conformité. Cette action peut toujours être référencé par un autre modèle.

#### <a name="remove-a-control"></a>Supprimer un contrôle

Pour supprimer un contrôle, modifiez votre feuille de calcul en suivant les étapes ci-dessous, puis ré-importez votre feuille de calcul :

1. Sous **l’onglet ControlFamily,** recherchez le contrôle à supprimer dans la **colonne controlName.**
2. Supprimez la ligne de ce contrôle.
    - Si ce contrôle supprimé contient des actions d’amélioration qui ne sont référencés par aucun autre contrôle, vous devez supprimer ces actions d’amélioration de **l’onglet Actions.** Sinon, vous recevrez une erreur de validation.

3. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre contrôle est supprimé du modèle.

## <a name="export-a-template"></a>Exporter un modèle

Vous pouvez exporter un fichier Excel qui contient toutes les données d’un modèle. Vous devez exporter un modèle pour modifier le modèle, car il s’agit du fichier Excel que vous modifiez et téléchargez dans le processus [de modification.](#modify-a-template)

Pour exporter votre modèle, allez sur la page de détails de votre modèle et sélectionnez le bouton **Exporter vers Excel.**

Notez que lors de l’exportation d’un modèle que vous avez étendu à partir d’un modèle gestionnaire de conformité, le fichier exporté contient uniquement les attributs que vous avez ajoutés au modèle. Le fichier exporté n’inclut pas les données de modèle d’origine fournies par Microsoft. Pour obtenir un tel rapport, consultez les instructions d’exportation [d’un rapport d’évaluation.](compliance-manager-assessments.md#export-an-assessment-report)