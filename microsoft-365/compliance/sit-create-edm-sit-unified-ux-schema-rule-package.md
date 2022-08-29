---
title: Créer EDM SIT à l’aide de la nouvelle expérience
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Créer une nouvelle expérience de package de règle SIT EDM
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5a948b00127098faf25419e75a1920ee70c01536
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67360576"
---
# <a name="create-edm-sit-using-the-new-experience"></a>Créer EDM SIT à l’aide de la nouvelle expérience

Vous pouvez créer le schéma EDM et le type d’informations sensibles (ou package de règles) à l’aide de la nouvelle expérience dans le portail de conformité.

## <a name="applies-to"></a>S’applique à

- Nouvelle expérience

Si vous souhaitez créer un sit EDM à l’aide de l’expérience classique, [créez un workflow d’expérience EDM SIT classique](sit-create-edm-sit-classic-ux-workflow.md). Si vous avez besoin d’aide pour choisir celui à utiliser, consultez [Choisir l’expérience de création SIT EDM appropriée pour vous](sit-get-started-exact-data-match-based-sits-overview.md#choosing-the-right-edm-sit-creation-experience-for-you).

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous d’avoir effectué les étapes décrites dans ces articles avant de commencer les procédures décrites dans cet article.

1. [Exporter les données sources pour le type d’informations sensibles basé sur la correspondance exacte des données](sit-get-started-exact-data-match-export-data.md)
1. [Créer un exemple de fichier SIT EDM pour la nouvelle expérience](sit-create-edm-sit-unified-ux-sample-file.md)

Si vous n’êtes pas familiarisé avec les services SES basés sur EDM ou leur implémentation, il est essentiel que vous vous familiarisiez avec les concepts dans :

- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types).
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Démarrage avec des types d’informations sensibles basés sur des correspondances de données exactes](sit-get-started-exact-data-match-based-sits-overview.md)
- [Créer une nouvelle expérience de type de données exactes correspondant à des informations sensibles](sit-create-edm-sit-unified-ux-workflow.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

### <a name="permissions"></a>Autorisations

- Vous devez avoir une autorisation d’administrateur général ou d’administrateur de conformité pour créer, tester et déployer un type d’informations sensibles personnalisé via l’interface utilisateur. [Consultez À propos des rôles d’administrateur dans Office 365](/office365/admin/add-users/about-admin-roles).

## <a name="create-your-edm-schema-and-sit"></a>Créer votre schéma EDM et SIT

> [!IMPORTANT]
> Le système suggère un mappage entre un SIT existant et votre élément principal. Vous devez passer en revue les [SIT existants](sensitive-information-type-entity-definitions.md) pour avoir une idée de ceux qui répondront à vos besoins. Assurez-vous que le SIT existant détecte exactement les chaînes que vous souhaitez sélectionner, et n’inclut aucun caractère environnant ou exclut une partie valide de la chaîne stockée dans votre table d’informations sensibles.

> [!NOTE]
> Toutes les données sont conservées lorsque vous naviguez vers l’avant et vers l’arrière à travers l’interface utilisateur. La navigation vers l’arrière (en sélectionnant **Précédent**) prend uniquement en charge le passage d’une page de niveau supérieur à une page de niveau supérieur et d’une sous-page à une sous-page. Vous ne pouvez pas naviguer vers l’arrière de la page de niveau supérieur vers la sous-page précédente ou d’une sous-page vers une page de niveau supérieur précédente. 

1. Dans le portail de conformité Microsoft Purview de votre locataire, accédez à la **classification** > **des données Correspondances exactes des données**.

1. Vérifiez que la **nouvelle expérience EDM** est **activée.**

1. Sélectionnez **+ Créer un classifieur EDM**.

1. Nommez le SIT et ajoutez une description. Le nom que le système génère pour le schéma sera le nom SIT que vous entrez ici concaténé avec *le schéma*. Il s’affiche à la fin du flux. Sélectionnez **Suivant**.

1. Sélectionnez la méthode que vous souhaitez utiliser pour définir votre schéma, **chargez un fichier contenant des exemples de données** ou **définissez manuellement votre structure de données**. Nous vous recommandons d’utiliser l’option charger l’exemple de fichier de données et le reste de cette procédure suppose que vous avez choisi de charger votre exemple de fichier. Sélectionnez **Suivant**.

> [!NOTE]
> Quelle que soit l’option que vous sélectionnez, vous utiliserez les informations de l’exemple de fichier que vous avez créé dans [l’exemple de fichier Create EDM SIT pour la nouvelle expérience](sit-create-edm-sit-unified-ux-sample-file.md).

6. Sélectionnez votre exemple de fichier, **sélectionnez Charger le fichier** , puis **sélectionnez Suivant**. Si vous obtenez des erreurs pendant le chargement, réessayez.

7. Une fois vos données chargées, elles s’affichent sur la page **Vérifier que vos exemples de données sont corrects** . Inspectez les noms de colonnes et les exemples de données, puis choisissez **Suivant**.

8. Sélectionnez vos principaux éléments en fonction des recommandations présentées. Examinez les valeurs de la colonne **De validation de** correspondance pour obtenir des conseils et choisissez **Suivant**.

> [!TIP]
> - Sélectionnez les éléments principaux dont les valeurs rendent cette ligne unique dans la table. Par exemple, ne sélectionnez pas de champs tels que *FirstName* ou *DateOfBirth* , car il y aura probablement de nombreuses duplications de prénoms ou de dates de naissance dans votre fichier de données sensibles réel. Au lieu de cela, choisissez des éléments tels que *Social Security Number* et *BankAccountNumber* dont la valeur sera unique dans votre table et, par conséquent, rendre la ligne unique dans la table.
> - Vous devez choisir un élément principal, mais pas plus de cinq éléments principaux. Si vous disposez d’un champ de données corroborant à plusieurs jetons, vous devez également le mapper à un sit de base. Plus vous pouvez choisir des valeurs uniques dans votre table de données sensibles réelle, plus la précision de votre sit EDM sera élevée. Il améliorera également les performances et évitera les délais d’expiration causés par la surcharge de processus. 
> - Sélectionnez un type d’informations sensibles qui correspond étroitement au format du contenu que vous souhaitez trouver. La sélection d’un SIT qui correspond à du contenu inutile, comme celui qui correspond à toutes les chaînes de texte, ou tous les nombres peut entraîner une charge excessive dans le système, ce qui peut entraîner l’absence d’informations sensibles.

9. Dans les **paramètres Configurer pour les champs de données** , vous pouvez indiquer comment EDM traite la casse et quels délimiteurs ignorer. Vous pouvez définir cette valeur pour les valeurs de tous les éléments ou spécifier les paramètres de chaque élément individuellement. Cliquez sur **Suivant**.

> [!IMPORTANT]
Si vous avez sélectionné l’option Délimiteurs ignorés pour la colonne d’élément principal dans votre schéma, assurez-vous que le sit que vous mappez correspondra aux données avec et sans les délimiteurs sélectionnés.

10. EDM génère automatiquement une règle de détection pour chacun des éléments principaux que vous avez identifiés. EDM crée une règle de confiance élevée et une règle de confiance moyenne. Les règles de confiance élevée ont plus d’exigences qui doivent être satisfaites que les règles moyennes. De même, les règles de confiance moyenne ont plus d’exigences que les règles de confiance faible si vous choisissez de créer une règle de confiance faible. Vous pouvez examiner et modifier ces règles dans la page **Configurer les règles de détection pour les éléments principaux** . Choose **Submit**.

> [!TIP]
> Tous les éléments qui ne sont pas sélectionnés comme éléments principaux peuvent toujours être utilisés comme preuves corroborantes ou à l’appui. Plus les éléments de prise en charge trouvés se trouvent dans une proximité définie avec les éléments principaux, plus la confiance que l’élément est un vrai positif.

> [!NOTE]
Lorsque vous **sélectionnez Envoyer**, EDM crée le package de schéma et de règle. Le nom du schéma se trouve sur la page finale du flux de création.  


## <a name="next-step"></a>Étape suivante

- **Pour une nouvelle expérience** : [Hachez et chargez la table source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md)

