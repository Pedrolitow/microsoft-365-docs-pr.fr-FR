---
title: Mettre en forme des données de modèle d’évaluation dans Excel pour le Gestionnaire de conformité Microsoft Purview
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
description: Découvrez comment utiliser des données Excel pour les modèles d’évaluation dans le Gestionnaire de conformité Microsoft Purview.
ms.openlocfilehash: 6c94d79fec8ff59419854c34755a7402f841cfe8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631224"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-purview-compliance-manager"></a>Mettre en forme des données de modèle d’évaluation dans Excel pour le Gestionnaire de conformité Microsoft Purview

Lorsque vous [créez](compliance-manager-templates-create.md), [modifiez](compliance-manager-templates-modify.md) ou [étendez](compliance-manager-templates-extend.md) des modèles d’évaluation dans le Gestionnaire de conformité, vous travaillez avec des feuilles de calcul Excel qui utilisent un format et un schéma spécifiques. Ces spécifications doivent être suivies pour que les fichiers soient importés correctement.

## <a name="download-example-spreadsheet"></a>Exemple de feuille de calcul de téléchargement

Pour afficher un exemple de feuille de calcul, [téléchargez un exemple de fichier](https://go.microsoft.com/fwlink/?linkid=2124865). Vous pouvez l’utiliser pour référencer la création de votre propre fichier.

Si vous envisagez de modifier un modèle existant, commencez par afficher les détails du modèle dans le Gestionnaire de conformité et télécharger son fichier Excel.

## <a name="spreadsheet-format"></a>Format de feuille de calcul

La feuille de calcul Excel contient quatre onglets, dont trois sont requis :

1. [Modèle](#template-tab) (obligatoire)
2. [ControlFamily](#controlfamily-tab) (obligatoire)
3. [Actions](#actions-tab) (obligatoires)
4. [Dimensions](#dimensions-tab) (facultatif)

Lorsque vous remplissez votre feuille de calcul avec des données de modèle, celle-ci **doit inclure les onglets dans l’ordre indiqué ci-dessus**, sinon vos données ne seront pas correctement importées dans un modèle.

### <a name="template-tab"></a>Onglet Modèle

L’onglet **Modèle** est requis. Les informations contenues dans cet onglet fournissent des métadonnées sur le modèle. Quatre colonnes sont requises. Les colonnes doivent conserver l’ordre dans la feuille Excel, comme indiqué ci-dessous. Vous pouvez ajouter votre propre colonne **après** les quatre colonnes pour fournir vos propres dimensions. Si vous effectuez cette opération, veillez à les ajouter à l’onglet **Dimensions** .

- **title**: Il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le Gestionnaire de conformité, y compris vos propres modèles ou un modèle gestionnaire de conformité.

- **produit** : il s’agit d’une dimension obligatoire. Répertoriez le produit associé au modèle.

- **certification** : il s’agit du règlement que vous utilisez pour le modèle.

- **inScopeServices** : il s’agit des services dans le produit que cette évaluation traite (par exemple, si vous avez indiqué Office 365 comme produit, Microsoft Teams peut être un service dans l’étendue). Vous pouvez répertorier plusieurs services séparés par deux points-virgules.

> [!NOTE]
> Les données que vous insérez dans les cellules de **produit** et de **certification** ne peuvent pas être modifiées après avoir importé la feuille de calcul pour créer ou personnaliser un modèle. En outre, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison **produit/certification** . Vous pouvez avoir plusieurs modèles avec la même combinaison produit/certification.

### <a name="controlfamily-tab"></a>Onglet ControlFamily

L’onglet **ControlFamily** est requis.  Les colonnes requises dans cet onglet, qui doivent suivre l’ordre fourni dans l’exemple de feuille de calcul, sont les suivantes :

- **controlName** : il s’agit du nom de contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms de contrôle doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles portant le même nom dans la feuille de calcul.

- **controlFamily** : fournissez un mot ou une expression pour controlFamily, qui identifie un grand regroupement de contrôles. Une controlFamily n’a pas besoin d’être unique ; il peut être répertorié plusieurs fois dans une feuille de calcul. La même controlFamily peut également être répertoriée dans plusieurs modèles, bien qu’elles n’aient aucune relation les unes avec les autres. Chaque controlFamily doit être mappé à au moins un contrôle.

- **controlTitle** : fournissez un titre pour le contrôle. Alors que controlName est un code de référence, le titre est un format de texte enrichi généralement vu dans les réglementations.

- **controlDescription** : fournissez une description du contrôle.

- **controlActionTitle** : ce champ lie votre contrôle à une ou plusieurs actions, répertoriées par leur actionTitle. Vous pouvez ajouter plusieurs actions en les séparant par deux points-virgules sans espace entre les deux. Chaque contrôle que vous répertoriez doit inclure au moins une action existante, et l’action peut être définie sous l’onglet **Actions** de la même feuille de calcul, être dans un modèle différent ou être créée par Microsoft. Différents contrôles peuvent référencer la même action.

### <a name="actions-tab"></a>Onglet Actions

L’onglet **Actions** est requis.  Il désigne les actions d’amélioration gérées par votre organisation et non celles de Microsoft, qui existent déjà dans le Gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent suivre l’ordre fourni dans l’exemple de feuille de calcul, sont les suivantes :

- **actionTitle** : il s’agit du titre de votre action et d’un champ obligatoire. Le titre que vous fournissez doit être unique. **Important** : si vous référencez une action que vous possédez déjà (par exemple dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications se propagent à la même action dans d’autres modèles.

- **implementationType** : dans ce champ obligatoire, répertoriez l’un des trois types d’implémentation suivants : 
  1) **Opérationnel** : actions implémentées par les personnes et les processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des ressources, des données et du personnel (par exemple, la sensibilisation à la sécurité et la formation).      
  2) **Technique** : actions effectuées à l’aide de la technologie et des mécanismes contenus dans les composants matériels, logiciels ou microprogrammes du système d’information afin de protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels et des données (par exemple, l’authentification multifacteur).
  3) **Documentation** : actions implémentées par le biais de stratégies et de procédures documentées établissant et définissant les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des ressources, des données et du personnel (par exemple, une stratégie de sécurité des informations).

- **actionScore** : dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. La valeur doit être un nombre entier compris entre 1 et 99 ; il ne peut pas être égal à 0, null ou vide. Plus le nombre est élevé, plus sa valeur est élevée pour améliorer votre posture de conformité. L’image ci-dessous montre comment le Gestionnaire de conformité évalue les contrôles :

  ![Le Gestionnaire de conformité contrôle les valeurs de point.](../media/compliance-score-action-scoring.png "Le Gestionnaire de conformité contrôle les valeurs de point")

- **actionDescriptionTitle** : il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et d’afficher une description différente dans chaque modèle.  Ce champ vous aide à clarifier le modèle auquel la description fait référence. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription** : fournissez une description de l’action. Vous pouvez appliquer une mise en forme telle que du texte gras et des liens hypertexte. Ce champ est obligatoire.

- **Dimension-Action Purpose** : il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension- ». Toutes les dimensions que vous incluez ici sont utilisées comme filtres dans le Gestionnaire de conformité et apparaissent dans la page des détails des actions d’amélioration dans le Gestionnaire de conformité.

### <a name="dimensions-tab"></a>Onglet Dimensions

L’onglet **Dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: list as « product », « certifications », « action purpose »
- **dimensionValue** : exemples : Office 365, HIPPA, Préventif, Détective

Lorsque vous exportez un modèle existant, la feuille de calcul exportée a l’onglet **Dimensions** , qui répertorie toutes les dimensions utilisées dans le modèle.
