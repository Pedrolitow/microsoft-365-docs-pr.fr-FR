---
title: Utilisation des modèles d’évaluation dans le gestionnaire de conformité Microsoft
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
description: Découvrez comment utiliser et gérer des modèles pour la création d’évaluations dans le gestionnaire de conformité Microsoft. Créez et modifiez des modèles à l’aide d’un fichier Excel mis en forme.
ms.openlocfilehash: 95cd6e90454b04f34014830008b9e7fbec04c38e
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48204343"
---
# <a name="working-with-assessment-templates-in-compliance-manager"></a>Utilisation des modèles d’évaluation dans le gestionnaire de conformité

**Dans cet article :** Comprendre **Comment fonctionnent les modèles** et **les gérer** à partir de votre page modèles d’évaluation. Obtenir des instructions pour la **création** de nouveaux modèles, la **modification** de modèles existants, **la mise en forme de vos données de modèle avec Excel et l'** exportation de **rapports**de modèle.

> [!IMPORTANT]
> Les modèles d’évaluation disponibles pour votre organisation dépendent de votre contrat de licence. [Passez en revue les détails](https://go.microsoft.com/fwlink/?linkid=2132371).

## <a name="templates-overview"></a>Vue d’ensemble des modèles

Un modèle est une infrastructure pour la création d’une évaluation dans le gestionnaire de conformité. Ils contiennent les contrôles permettant de satisfaire aux exigences d’une certification à l’aide d’un produit spécifique. Le gestionnaire de conformité fournit un ensemble complet de modèles pour aider votre organisation à se conformer aux exigences nationales, régionales et sectorielles régissant la collecte et l’utilisation des données.

## <a name="list-of-pre-built-templates-for-assessments"></a>Liste des modèles prédéfinis pour les évaluations

Le gestionnaire de conformité fournit des modèles pour la création d’évaluations afin de vous aider à respecter les différentes réglementations et normes. Affichez la [liste des modèles](compliance-manager-templates-list.md) fournis par le gestionnaire de conformité. Les nouveaux modèles étant ajoutés régulièrement, vérifiez la liste souvent.

## <a name="viewing-and-managing-templates-from-the-assessment-templates-page"></a>Affichage et gestion des modèles à partir de la page modèles d’évaluation

La page modèles d’évaluation dans le gestionnaire de conformité affiche une liste de modèles et de détails clés. La liste inclut des modèles fournis par le gestionnaire de conformité, ainsi que tous les modèles que votre organisation a modifiés ou créés. Vous pouvez appliquer des filtres pour rechercher un modèle en fonction de la certification, de l’étendue du produit, du pays, de l’industrie, de son auteur et du fait que le modèle est activé pour la création de l’évaluation.

Sélectionnez un modèle à partir de sa ligne pour afficher sa page de détails. Cette page contient une description du modèle, ainsi que des informations supplémentaires sur la certification, l’étendue et les contrôles. À partir de cette page, vous pouvez sélectionner les boutons appropriés pour créer une évaluation, exporter les données du modèle vers Excel ou modifier le modèle.

## <a name="creating-and-modifying-templates-overview"></a>Vue d’ensemble de la création et de la modification des modèles

Pour modifier un modèle existant ou pour créer votre propre modèle, vous utiliserez une feuille de calcul Excel spécialement mise en forme ([Télécharger un exemple](https://go.microsoft.com/fwlink/?linkid=2124865)) pour assembler les données de contrôle nécessaires. Une fois que vous avez terminé la feuille de calcul, vous l’importez dans le gestionnaire de conformité lors du processus de création ou de modification d’un modèle.

> [!NOTE]
> La feuille de calcul a un format et un schéma spécifiques qui doivent être utilisés, ou elle ne peut pas être correctement importée dans le gestionnaire de conformité. Les [instructions de mise en forme](#formatting-your-template-data-with-excel) sont indiquées ci-dessous.

**Rôles requis**

Seuls les utilisateurs qui disposent d’un rôle d’administration d’administrateur général ou de gestionnaire de conformité peuvent créer et modifier des modèles. En savoir plus sur [les rôles et les autorisations](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-a-new-template"></a>Créer un nouveau modèle

Pour créer votre propre modèle (utilisé pour la création d’évaluations personnalisées), suivez les étapes ci-dessous.

1. Accédez à la page des **modèles d’évaluation** dans le gestionnaire de conformité.
2. Sélectionnez **créer un nouveau modèle**. Un assistant de création de modèle s’ouvre.
3. Choisissez le type de modèle que vous souhaitez créer. Dans ce cas, sélectionnez **créer un modèle personnalisé**, puis **suivant**.
4. Dans l’écran **charger un fichier** , sélectionnez **Parcourir** pour trouver et charger votre fichier Excel mis en forme contenant toutes les données de modèle requises (reportez-vous à la rubrique [instructions pour la mise en forme correcte de votre fichier](#formatting-your-template-data-with-excel)).
5. S’il n’y a aucun problème avec votre fichier, le nom du fichier téléchargé s’affiche. Sélectionnez **suivant** pour continuer. (Si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier**).
    - S’il y a une erreur avec votre fichier, un message d’erreur en haut explique ce qui est incorrect. Vous devrez corriger votre fichier et le télécharger à nouveau. Des erreurs se produisent si votre feuille de calcul est mise en forme de manière incorrecte ou s’il existe des informations non valides dans certains champs (reportez-vous à la rubrique [instructions de mise en forme](#formatting-your-template-data-with-excel)).  
    
6. L’écran **vérifier et terminer** indique le nombre d’actions et de contrôles d’amélioration, ainsi que le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **créer un modèle.** (Si vous avez besoin d’effectuer des modifications, sélectionnez **retour**).
7. Le dernier écran confirme qu’un nouveau modèle a été créé. Sélectionnez **terminé** pour quitter l’Assistant.
8. Vous arrivez sur la page des détails de votre nouveau modèle, dans laquelle vous pouvez [créer votre évaluation](compliance-manager-assessments.md#create-your-own-custom-assessment).

## <a name="formatting-your-template-data-with-excel"></a>Mise en forme de vos données de modèle avec Excel

La feuille de calcul Excel utilisée pour créer des modèles contient quatre onglets, dont trois sont obligatoires :

1. [Modèle](#template-tab) (obligatoire)
2. [ControlFamily](#controlfamily-tab) (obligatoire)
3. [Actions](#actions-tab) (obligatoire)
4. [Dimensions](#dimensions-tab) (facultatif)

Lorsque vous remplissez votre feuille de calcul avec des données de modèle, la feuille  **de calcul doit inclure les onglets dans l’ordre indiqué ci-dessus**, sinon vos données ne peuvent pas être correctement importées dans un modèle.

##### <a name="template-tab"></a>Onglet modèle

L’onglet **modèle** est obligatoire. Les informations de cet onglet fournissent des métadonnées sur le modèle. Il y a quatre colonnes obligatoires. Les colonnes doivent conserver la commande sur la feuille Excel, comme indiqué ci-dessous. Vous pouvez ajouter votre propre colonne **après** les quatre colonnes pour fournir vos propres dimensions. Si vous procédez ainsi, veillez à les ajouter à l’onglet **dimensions** en suivant les [instructions ci-dessous](#dimensions-tab).

- **titre**: il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le gestionnaire de conformité, y compris vos propres modèles ou un modèle gestionnaire de conformité.

- **Product**: il s’agit d’une dimension obligatoire. Répertoriez le produit associé au modèle.

- **certification**: il s’agit de la règle que vous utilisez pour le modèle.

- **inScopeServices**: il s’agit des services du produit que cette évaluation adresse (par exemple, si vous avez répertorié Office 365 comme produit, Microsoft teams pourrait être un service dans l’étendue). Vous pouvez répertorier plusieurs services séparés par deux points-virgules.

> [!NOTE]
> Les données que vous insérez dans le **produit** et les cellules de **certification** ne peuvent pas être modifiées une fois la feuille de calcul importée pour créer ou personnaliser un modèle. De plus, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison de **produit/certification** . Vous pouvez avoir plusieurs modèles avec la même combinaison de produit/certification.

##### <a name="controlfamily-tab"></a>Onglet ControlFamily

L’onglet **ControlFamily** est obligatoire.  Les colonnes obligatoires de cet onglet, qui doivent respecter l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivantes :

- **nomcontrôle**: nom de contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms de contrôle doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles portant le même nom dans la feuille de calcul.

- **controlFamily**: fournissez un mot ou une expression pour le controlFamily, qui identifie un large regroupement de contrôles. Un controlFamily ne doit pas nécessairement être unique ; elle peut être affichée plusieurs fois dans une feuille de calcul. Le même controlFamily peut également être mis en vente dans plusieurs modèles, même s’ils n’ont pas de relation les uns avec les autres. Chaque controlFamily doit être mappé à au moins un contrôle.

- **controlTitle**: fournissez un titre pour le contrôle. Alors que NomContrôle est un code de référence, le titre est un format de texte enrichi généralement visible dans les réglementations.

- **controlDescription**: fournissez une description du contrôle.

- **controlActionTitle**: il s’agit du titre d’une action que vous souhaitez associer à ce contrôle. Vous pouvez ajouter plusieurs actions en séparant par deux points-virgules sans espace. Chaque contrôle que vous répertoriez doit inclure au moins une action, et l’action doit exister (ce qui signifie que vous pouvez répertorier une action que vous répertoriez sous l’onglet **actions** de la même feuille de calcul, une action qui existe dans un autre modèle ou une action créée par Microsoft). Différents contrôles peuvent faire référence à la même action.

##### <a name="actions-tab"></a>Onglet actions

L’onglet **actions** est obligatoire.  Il désigne les actions d’amélioration gérées par votre organisation et non celles de Microsoft, qui existent déjà dans le gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent respecter l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivantes :

- **actionTitle**: il s’agit du titre de votre action et est un champ obligatoire. Le titre que vous fournissez doit être unique. **Important**: Si vous faites référence à une action que vous possédez déjà (par exemple, dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications seront répercutées dans la même action dans d’autres modèles.

- **implementationType**: dans ce champ obligatoire, répertoriez l’un des trois types d’implémentation ci-dessous :
    - **Opérations-actions** mises en œuvre par des personnes et des processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes, des biens, des données et du personnel de l’organisation (exemple : sensibilisation et formation à la sécurité)
    - **Techniques** : actions accomplies via l’utilisation de technologies et de mécanismes contenus dans les composants matériels, logiciels ou microprogrammes du système d’information afin de protéger la confidentialité, l’intégrité et la disponibilité des systèmes et des données de l’organisation (exemple : authentification multifacteur)
    - **Documentation** -actions mises en œuvre via des stratégies et des procédures documentées qui établissent et définissent les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes, des biens, des données et du personnel de l’organisation (exemple : une stratégie de sécurité des informations)

- **actionScore**: dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. Il doit être un nombre entier compris entre 1 et 99 ; il ne peut pas être égal à 0, null ou vide. Plus le nombre est élevé, plus sa valeur augmente pour améliorer la conformité. L’image ci-dessous montre comment le gestionnaire de conformité vérifie les contrôles :

![Contrôle du gestionnaire de conformité-valeurs de points](../media/compliance-score-action-scoring.png "Contrôle du gestionnaire de conformité-valeurs de points")

- **actionDescriptionTitle**: il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et de faire apparaître une description différente dans chaque modèle.  Ce champ vous permet de clarifier le modèle référencé par la description. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription**: fournissez une description de l’action. Vous pouvez appliquer une mise en forme telle que le texte gras et les liens hypertexte. Champ obligatoire.

- **dimension-action d’action**: il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension- ». Toutes les dimensions que vous incluez ici seront utilisées en tant que filtres dans le gestionnaire de conformité et apparaissent sur la page des détails des actions d’amélioration dans le gestionnaire de conformité.

##### <a name="dimensions-tab"></a>Onglet dimensions

L’onglet **dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: liste en tant que « produit », « certifications », « objectif de l’action »
- **dimensionValue**: exemples : Office 365, HIPPA, préventive, détective

Vous pouvez afficher vos dimensions existantes en accédant à **gestion des clients** et en sélectionnant l’onglet **dimensions** . Par ailleurs, chaque fois que vous exportez un modèle existant, la feuille de calcul exportée aura l’onglet **dimensions** , qui répertorie toutes les dimensions utilisées dans le modèle.

## <a name="modify-a-template"></a>Modifier un modèle

Vous pouvez modifier un modèle que vous avez déjà créé, par exemple pour ajouter des contrôles, ou pour ajouter ou supprimer des actions d’amélioration. Le processus est similaire au processus de création de modèle dans le sens où vous téléchargez le fichier Excel mis en forme avec vos données de modèle.

Toutefois, il existe des détails particuliers à prendre en compte lors de la mise en forme de votre fichier avec les modifications apportées aux données de modèle existantes. **Nous vous recommandons de consulter attentivement ces instructions afin de vous assurer que vous ne remplacez pas les données existantes que vous souhaitez conserver.**

### <a name="template-modification-process-steps"></a>Étapes du processus de modification de modèle

Pour modifier un modèle, suivez les étapes ci-dessous :

1. Dans la page **modèles d’évaluation** , sélectionnez le modèle à modifier, qui affichera sa page Détails.
2. Sélectionnez **Exporter vers Excel**. Un fichier Excel avec toutes vos données de modèle seront téléchargés. Enregistrez le fichier sur votre ordinateur local.
3. Apportez les modifications de votre modèle en [modifiant le fichier Excel en suivant les instructions ci-dessous](#formatting-your-excel-file-to-modify-a-template).
4. Lorsque vous avez terminé d’apporter des modifications à votre fichier Excel, enregistrez le fichier.
5. Sur la page des détails de votre modèle, sélectionnez **modifier le modèle** pour lancer l’Assistant modification. 
6. Dans l’écran **Télécharger un fichier** , sélectionnez **Parcourir** pour rechercher et télécharger votre fichier Excel.
7. S’il n’y a aucun problème avec votre fichier, l’écran suivant indique le nom du fichier téléchargé. Sélectionnez **suivant** pour continuer (si vous devez modifier le fichier, sélectionnez **Télécharger un autre fichier**).
    - En cas de problème avec votre fichier, un message d’erreur en haut explique ce qui est incorrect. Vous devrez corriger votre fichier et le télécharger à nouveau. Des erreurs se produisent si votre feuille de calcul est mise en forme de manière incorrecte ou s’il existe des informations non valides dans certains champs.

8. L’écran **vérifier et terminer** indique le nombre d’actions et de contrôles d’amélioration, ainsi que le score maximal pour le modèle. Lorsque vous êtes prêt à approuver, sélectionnez **suivant**.
9. Le dernier écran confirme que le modèle a été modifié. Sélectionnez **terminé** pour quitter l’Assistant.

Votre modèle inclut désormais les modifications que vous avez apportées. Toutes les évaluations qui utilisent ce modèle modifié affichent désormais les mises à jour en attente et vous devez accepter les mises à jour des évaluations pour refléter les modifications apportées dans le modèle. En savoir plus sur les [mises à jour des évaluations](compliance-manager-assessments.md#accepting-updates-to-assessments).

> [!NOTE]
> Si vous utilisez le gestionnaire de conformité dans une langue autre que l’anglais, vous remarquerez que du texte s’affiche en anglais lorsque vous exportez un modèle vers Excel. Les titres des actions (à la fois les actions d’amélioration et les actions de Microsoft) doivent être en anglais pour être reconnus par les contrôles. Si vous modifiez un titre d’action, veillez à l’écrire en anglais afin que le fichier s’importe correctement.

### <a name="formatting-your-excel-file-to-modify-a-template"></a>Mise en forme de votre fichier Excel pour modifier un modèle

Accédez à une section ci-dessous pour trouver rapidement les instructions dont vous avez besoin :

- [Modifier les attributs de modèle principaux](#edit-the-main-template-attributes)
- [Ajouter une action d’amélioration](#add-an-improvement-action)
- [Modifier les informations d’une action d’amélioration](#edit-an-improvement-actions-information)
- [Modifier le nom d’une action d’amélioration](#change-an-improvement-actions-name)
- [Supprimer une action d’amélioration](#remove-an-improvement-action)
- [Supprimer un contrôle](#remove-a-control)

#### <a name="edit-the-main-template-attributes"></a>Modifier les attributs de modèle principaux

Sous l’onglet **modèles** , vous pouvez modifier n’importe quel élément dans la colonne **titre** , la colonne **inScopeServices** , ainsi que dans n’importe quelle autre colonne que vous avez peut-être ajoutée. Toutefois, vous ne pouvez rien modifier dans les colonnes de **produit** ou de **certification** .

#### <a name="add-an-improvement-action"></a>Ajouter une action d’amélioration

1. Accédez à l’onglet **actions** . Ajoutez vos informations dans les champs obligatoires de la première ligne vide sous vos actions existantes.
2. Accédez à l’onglet **ControlFamily** . Recherchez la ligne contenant le contrôle auquel votre action d’amélioration est mappée. Ajoutez votre nouvelle action à la colonne **controlActionTitle** de cette ligne (n’oubliez pas de séparer plusieurs actions de ce champ par deux points-virgules, sans espace entre).
3. Enregistrez votre feuille de calcul.

#### <a name="edit-an-improvement-actions-information"></a>Modifier les informations d’une action d’amélioration

Vous pouvez modifier les informations de l’action d’amélioration *, à l’exception de son titre*. Vous pouvez modifier une cellule à partir des colonnes B et, lorsque vous réimportez le fichier dans le modèle, les actions d’amélioration dans ce modèle contiendront désormais les données mises à jour.

Vous ne pouvez pas modifier le **actionTitle** (colonne A) car si vous le faites, le gestionnaire de conformité considère qu’il s’agit d’une nouvelle action d’amélioration. Si vous souhaitez modifier le nom d’une action d’amélioration, consultez les instructions immédiatement en dessous.

#### <a name="change-an-improvement-actions-name"></a>Modifier le nom d’une action d’amélioration

Si vous souhaitez modifier le nom d’une action d’amélioration, vous devez explicitement indiquer dans la feuille de calcul que vous remplacez un nom existant par un nouveau nom. Procédez comme suit :

1. Dans l’onglet **actions** de votre feuille de calcul, ajoutez une nouvelle colonne à la feuille de calcul après la colonne a.
2. Dans cette nouvelle colonne, qui est maintenant la colonne B, placée en tant qu’en-tête dans la ligne 1 : **oldActionTitle**.
3. Copiez le contenu de la colonne A et collez-le dans la colonne B. Cela place vos titres d’action d’amélioration existants, qui sont les éléments que vous souhaitez modifier, dans la colonne B.
4. Dans la colonne A, **actionTitle**, supprimez l’ancien nom et remplacez-le par le nouveau nom de votre action d’amélioration.

Notez que les titres d’action, à la fois pour vos actions d’amélioration et pour les actions Microsoft, doivent être rédigés en anglais afin d’être reconnus lorsqu’ils sont référencés dans des contrôles.

#### <a name="remove-an-improvement-action"></a>Supprimer une action d’amélioration

La suppression d’une action d’amélioration à partir d’une ligne dans une feuille de calcul **ne supprime pas** l’action du modèle que vous modifiez. Au lieu de cela, suivez la procédure ci-dessous :

1. Sous l’onglet **actions** , insérez une nouvelle colonne en tant que colonne a **et put dans** la ligne d’en-tête, qui est le numéro de ligne 1.
2. Sur la ligne correspondant à l’action d’amélioration que vous souhaitez supprimer, placez **supprimer** dans la colonne A pour cette ligne.
3. Assurez-vous que cette action d’amélioration n’est plus référencée par un contrôle. Accédez à l’onglet **ControlFamily** et recherchez le titre de votre action d’amélioration dans la colonne F, qui est **controlActionTitle**.
4. Une fois que vous avez trouvé votre action d’amélioration figurant dans la colonne **controlActionTitle** , supprimez-le.
5. Enregistrez votre feuille de calcul.

Lorsque vous importez de nouveau votre feuille de calcul dans le modèle, votre action est supprimée du modèle. La suppression d’une action d’un modèle ne supprime pas complètement l’action. Cette action peut toujours être référencée par un autre modèle.

Si vous supprimez la dernière action d’amélioration référencée par un contrôle, vous devez supprimer le contrôle.

#### <a name="remove-a-control"></a>Supprimer un contrôle

Pour supprimer un contrôle, suivez le même processus de suppression d’une action d’amélioration, comme indiqué ci-dessus. Dans l’onglet **ControlFamily** , ajoutez une colonne **opération** et placez la **suppression** en regard du contrôle que vous souhaitez supprimer.

## <a name="export-a-template"></a>Exporter un modèle

Vous pouvez exporter un fichier Excel qui contient toutes les données d’un modèle. Vous devrez exporter un modèle pour modifier le modèle, car il s’agira du fichier Excel que vous modifiez et téléchargez dans le processus de [modification](#modify-a-template).

Pour exporter votre modèle, accédez à la page de détails de votre modèle et sélectionnez le bouton **Exporter vers Excel** .

Notez que lorsque vous exportez un modèle que vous avez étendu à partir d’un modèle de gestionnaire de conformité, le fichier exporté ne contiendra que les attributs que vous avez ajoutés au modèle. Le fichier exporté n’inclut pas les données de modèle d’origine fournies par Microsoft. Pour obtenir ce rapport, reportez-vous aux instructions d' [exportation d’un rapport d’évaluation](compliance-manager-assessments.md#export-an-assessment-report).