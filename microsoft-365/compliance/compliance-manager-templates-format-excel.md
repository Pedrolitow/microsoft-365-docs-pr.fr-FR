---
title: Formater les données du modèle d’évaluation Excel le Gestionnaire de conformité Microsoft
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
description: Comprendre comment utiliser les données Excel pour les modèles d’évaluation dans le Gestionnaire de conformité Microsoft.
ms.openlocfilehash: fc7e54089bc0d2445c45c785ba426cce95651351
ms.sourcegitcommit: 81533e5d3e1aee0823539a7c9bdc20dba6541a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60223531"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-compliance-manager"></a>Formater les données du modèle d’évaluation Excel le Gestionnaire de conformité Microsoft

Lorsque [vous créez,](compliance-manager-templates-create.md) [modifiez](compliance-manager-templates-modify.md)ou étendez des modèles d’évaluation dans le Gestionnaire de conformité, vous utiliserez des feuilles de calcul Excel qui utilisent un format et un schéma spécifiques. [](compliance-manager-templates-extend.md) Ces spécifications doivent être suivies pour que les fichiers soient importés correctement.

## <a name="download-example-spreadsheet"></a>Télécharger un exemple de feuille de calcul

Pour afficher un exemple de feuille de calcul, [téléchargez un exemple de fichier.](https://go.microsoft.com/fwlink/?linkid=2124865) Vous pouvez l’utiliser comme référence pour créer votre propre fichier.

Si vous prévoyez de modifier un modèle existant, commencez par afficher les détails du modèle dans le Gestionnaire de conformité et téléchargez son fichier Excel.

## <a name="spreadsheet-format"></a>Format de feuille de calcul

La feuille Excel contient quatre onglets, dont trois sont obligatoires :

1. [Modèle](#template-tab) (obligatoire)
2. [ControlFamily](#controlfamily-tab) (obligatoire)
3. [Actions](#actions-tab) (obligatoires)
4. [Dimensions](#dimensions-tab) (facultatif)

Lorsque vous remplissez votre feuille de calcul avec des données de modèle, la feuille de calcul doit inclure les **onglets** dans l’ordre répertorié ci-dessus, sinon vos données ne seront pas correctement importées dans un modèle.

### <a name="template-tab"></a>Onglet Modèle

**L’onglet** Modèle est obligatoire. Les informations de cet onglet fournissent des métadonnées sur le modèle. Il existe quatre colonnes obligatoires. Les colonnes doivent conserver l’ordre dans la feuille Excel comme répertorié ci-dessous. Vous pouvez ajouter votre propre colonne **après les** quatre colonnes pour fournir vos propres dimensions. Si vous le faites, n’oubliez pas de les ajouter à **l’onglet Dimensions.**

- **titre**: il s’agit du titre de votre modèle, qui doit être unique. Il ne peut pas partager un nom avec un autre modèle que vous avez dans le Gestionnaire de conformité, y compris vos propres modèles ou un modèle gestionnaire de conformité.

- **produit**: il s’agit d’une dimension obligatoire. Liste du produit associé au modèle.

- **certification**: il s’agit de la réglementation que vous utilisez pour le modèle.

- **inScopeServices**: il s’agit des services au sein du produit que cette évaluation traite (par exemple, si vous avez répertorié Office 365 comme produit, Microsoft Teams peut être un service dans l’étendue). Vous pouvez lister plusieurs services séparés par deux points-virgules.

> [!NOTE]
> Les données que  vous insérez dans les cellules de produit et de **certification** ne peuvent pas être modifiées après avoir importé la feuille de calcul pour créer ou personnaliser un modèle. En outre, un groupe ne peut pas contenir deux évaluations qui ont la même combinaison **produit/certification.** Vous pouvez avoir plusieurs modèles avec la même combinaison produit/certification.

### <a name="controlfamily-tab"></a>Onglet ControlFamily

**L’onglet ControlFamily** est obligatoire.  Les colonnes requises dans cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **controlName :** il s’agit du nom du contrôle de la certification, de la norme ou de la réglementation, qui est généralement un type d’ID. Les noms des contrôles doivent être uniques dans un modèle. Vous ne pouvez pas avoir plusieurs contrôles du même nom dans la feuille de calcul.

- **controlFamily**: fournissez un mot ou une expression pour le controlFamily, qui identifie un groupe étendu de contrôles. Un controlFamily n’a pas besoin d’être unique ; Il peut être répertorié plusieurs fois dans une feuille de calcul. Le même controlFamily peut également être répertorié dans plusieurs modèles, bien qu’ils n’ont aucune relation les uns avec les autres. Chaque controlFamily doit être mappé sur au moins un contrôle.

- **controlTitle**: fournir un titre pour le contrôle. Alors que controlName est un code de référence, le titre est un format de texte enrichi généralement vu dans les réglementations.

- **controlDescription**: fournir une description du contrôle.

- **controlActionTitle :** ce champ relie votre contrôle à une ou plusieurs actions, répertoriées par leur actionTitle. Vous pouvez ajouter plusieurs actions en les séparant par deux points-virgules sans espace. Chaque contrôle que vous listez doit inclure au moins une action existante, et l’action peut être définie dans l’onglet **Actions** de la même feuille de calcul, se trouver dans un autre modèle ou être créée par Microsoft. Différents contrôles peuvent faire référence à la même action.

### <a name="actions-tab"></a>Onglet Actions

**L’onglet Actions** est obligatoire.  Il désigne les actions d’amélioration gérées par votre organisation et non celles de Microsoft, qui existent déjà dans le Gestionnaire de conformité. Les colonnes requises pour cet onglet, qui doivent suivre l’ordre indiqué dans l’exemple de feuille de calcul, sont les suivants :

- **actionTitle**: il s’agit du titre de votre action et d’un champ obligatoire. Le titre que vous fournissez doit être unique. **Important**: si vous référencez une action que vous possédez qui existe déjà (par exemple dans un autre modèle) et que vous modifiez l’un de ses éléments dans les colonnes suivantes, ces modifications se propagent à la même action dans d’autres modèles.

- **implementationType**: dans ce champ obligatoire, listez l’un des trois types d’implémentation ci-dessous :
- **Opérationnel** : actions implémentées par les personnes et les processus pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des ressources, des données et du personnel (exemple : sensibilisation et formation en matière de sécurité)
- **Technique** : actions effectuées à l’aide de la technologie et des mécanismes contenus dans le matériel, les logiciels ou les composants du microprogramme du système d’information pour protéger la confidentialité, l’intégrité et la disponibilité des données et des systèmes organisationnels (exemple : authentification multifacteur)
- **Documentation** : actions implémentées par le biais de stratégies et de procédures documentées établissant et définissant les contrôles requis pour protéger la confidentialité, l’intégrité et la disponibilité des systèmes organisationnels, des biens, des données et du personnel (exemple : une stratégie de sécurité des informations)

- **actionScore**: dans ce champ obligatoire, fournissez une valeur de score numérique pour votre action. La valeur doit être un nombre entier compris entre 1 et 99 ; il ne peut pas être 0, null ou vide. Plus le nombre est élevé, plus sa valeur est grande pour améliorer votre posture de conformité. L’image ci-dessous montre comment le Gestionnaire de conformité contrôle les scores :

  ![Le Gestionnaire de conformité contrôle les valeurs de points.](../media/compliance-score-action-scoring.png "Le Gestionnaire de conformité contrôle les valeurs de point")

- **actionDescriptionTitle**: il s’agit du titre de la description et est obligatoire. Ce titre de description vous permet d’avoir la même action dans plusieurs modèles et d’en faire une description différente dans chaque modèle.  Ce champ vous aide à clarifier le modèle référent de la description. Dans la plupart des cas, vous pouvez placer le nom du modèle que vous créez dans ce champ.

- **actionDescription**: fournir une description de l’action. Vous pouvez appliquer une mise en forme telle que du texte gras et des liens hypertexte. Ce champ est obligatoire.

- **dimension-Action Purpose**: il s’agit d’un champ facultatif. Si vous l’incluez, l’en-tête doit inclure le préfixe « dimension - ». Toutes les dimensions que vous incluez ici seront utilisées comme filtres dans le Gestionnaire de conformité et apparaîtront dans la page détails des actions d’amélioration dans le Gestionnaire de conformité.

### <a name="dimensions-tab"></a>Onglet Dimensions

**L’onglet Dimensions** est facultatif. Toutefois, si vous référencez une dimension ailleurs, vous devez la spécifier ici si elle n’existe pas dans un modèle que vous avez déjà créé ou dans un modèle Microsoft. Les colonnes de cet onglet sont répertoriées ci-dessous :

- **dimensionKey**: liste en tant que « produit », « certifications », « objectif de l’action »
- **dimensionValue :** exemples : Office 365, HIPPA, Préventive, Inspecteur

Lorsque vous exportez un modèle existant, la feuille de calcul exportée a l’onglet **Dimensions,** qui répertorie toutes les dimensions utilisées dans le modèle.
