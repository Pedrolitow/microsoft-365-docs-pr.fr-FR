---
title: Tester un type d’informations sensibles correspondant exactement aux données
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
description: configurer les services
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9078748e1f0106de72257a11333f2a4c34732dd6
ms.sourcegitcommit: 1c8f54f9e7a7665bc10b5ef4a3d8c36e3e48f44c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2022
ms.locfileid: "66078455"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Tester un type d’informations sensibles correspondant exactement aux données

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois votre type d’informations sensibles (SIT) EDM (Exact Data Match) créé et une heure après avoir vérifié que votre table d’informations sensibles a terminé le chargement et l’indexation, vous pouvez tester qu’elle détecte les informations que vous souhaitez détecter à l’aide de la fonction de test dans la section Types d’informations sensibles du Centre de conformité.
 
>[! REMARQUE :] La propagation des modifications dans un sit EDM déjà créé peut prendre un certain temps sur le système. Si vous apportez des modifications dans un type d’informations sensibles EDM pour résoudre les problèmes de détection, veillez à attendre au moins une heure après avoir apporté ces modifications avant d’utiliser la fonction de test pour valider leur impact.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Tester votre sit EDM dans le Centre de conformité

1. Ouvrez les **types d’informations sensibles** de **classification** >  des données **du Centre** >  de conformité.

2. Sélectionnez votre sit EDM dans la liste, puis sélectionnez **Tester** dans le volet de menu volant. Cette option est présente uniquement sous les types d’informations sensibles.
 
3. Télécharger un élément qui contient des données que vous souhaitez détecter. Par exemple, créez un élément qui contient un sous-ensemble des lignes de votre table d’informations sensibles. Si vous avez utilisé la fonctionnalité de correspondance configurable dans votre schéma pour définir des délimiteurs ignorés, assurez-vous que l’élément inclut des exemples avec et sans ces délimiteurs.

4. Une fois le fichier chargé et analysé, recherchez les correspondances avec votre sit EDM.

5. Si la fonction **test** dans le SIT détecte une correspondance, vérifiez qu’elle ne la coupe pas ou ne l’extrait pas de manière incorrecte. Par exemple, en extrayant uniquement une sous-chaîne de la chaîne complète qu’il est censé détecter, ou en ramassant uniquement le premier mot dans une chaîne à plusieurs mots, ou en incluant des symboles ou des caractères supplémentaires dans l’extraction. Consultez [Le langage d’expression régulière - Référence rapide](/dotnet/standard/base-types/regular-expression-language-quick-reference) pour la référence du langage d’expression régulière. 

5. Vous pouvez également utiliser l’applet de commande PowerShell suivante :

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Lorsque vous créez ou modifiez un type d’informations sensibles EDM, ou le sit principal sur lequel est basé un type EDM, tous les nouveaux contenus et contenus modifiés après les modifications apportées aux SIT sont analysés pour rechercher du texte qui correspond aux nouvelles définitions, mais le contenu préexistant ne sera pas analysé tant que le texte n’est pas modifié ou réindexé. 

Pour forcer une nouvelle analyse du contenu existant dans un site ou une bibliothèque SharePoint ou dans OneDrive, suivez les instructions fournies dans [demander manuellement l’analyse et la réindexation d’un site, d’une bibliothèque ou d’une liste](/sharepoint/crawl-site-content).

## <a name="test-your-edm-sit-with-information-protection-policies"></a>Tester votre sit EDM avec des stratégies de protection des informations

Vous pouvez voir où votre sit EDM est utilisé et comment il est précis en production en les utilisant dans des stratégies :

1. Créez une [stratégie d’étiquetage automatique et exécutez-la](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) dans la **vue d’ensemble de simulation**.

1. Ajoutez du contenu qui déclenchera le SIT EDM et du contenu qui ne déclenchera pas le SIT EDM à un emplacement que votre stratégie surveille.

1. Ouvrez l’onglet **Éléments à examiner** pour vérifier les correspondances.

1. Ajustez vos stratégies en fonction des besoins. 

Une fois que vous êtes satisfait des résultats de vos tests et réglages, votre SIT personnalisé basé sur EDM est prêt à être utilisé dans les stratégies de protection des informations, par exemple :

- [Stratégies de protection contre la perte de données](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Defender for Cloud Apps](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Conseils de dépannage

Si vous ne trouvez pas de correspondances, voici quelques conseils de dépannage.

|Problème  |Conseil de dépannage  |
|---------|---------|
|Aucune correspondance trouvée     |  Vérifiez que vos données sensibles ont été chargées correctement à l’aide des commandes expliquées dans [le hachage et chargez la table source d’informations sensibles pour les données exactes correspondant aux types d’informations sensibles](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|
|Aucune correspondance trouvée   | Testez le SIT que vous avez utilisé lorsque vous avez configuré l’élément principal dans chacun de vos modèles. Cela confirme que le SIT est en mesure de faire correspondre les exemples de l’élément. L’utilisation d’un SIT mal défini comme élément de classification d’un type d’informations sensibles EDM est la cause la plus courante des échecs de détection dans EDM.         |
|Le SIT que vous avez sélectionné pour un élément principal dans le type EDM ne trouve pas de correspondance dans l’élément ou trouve moins de correspondances que prévu    |  Vérifiez qu’il prend en charge les séparateurs et les délimiteurs qui se trouvent dans le contenu. Veillez à inclure les délimiteurs ignorés définis dans votre schéma.       |
|L’élément principal SIT trouve des correspondances dans un élément, mais ce n’est pas le cas de l’élément SIT EDM.     | - Vérifiez vos instructions REGEX pour le démarrage ou la fin de la capture des délimiteurs d’espaces blancs, tels que \s. L’espace blanc ne correspond pas à la valeur hachée dans la table de données. Utilisez plutôt un séparateur de mots comme \b. </br> - Vérifiez vos instructions REGEX pour vous assurer qu’elles capturent la chaîne entière que vous souhaitez capturer, et pas seulement une sous-chaîne. Par exemple, ce modèle pour les adresses e-mail \b[a-zA-Z]{2,30}@[a-zA-Z]{2,20}.[ a-zA-Z]{2,3}\b correspond correctement *à user@contoso.com* mais capture uniquement *user@contoso.co.jp* sous une forme incomplète.
|Un sit EDM avec des éléments principaux et aucun élément secondaire défini détecte les éléments, mais ne détecte pas ou détecte moins de correspondances que prévu lorsque des éléments principaux et secondaires sont requis.  | Si les valeurs d’une colonne utilisées pour la preuve secondaire ne sont pas composées d’un seul mot ou de chaînes qui ne contiennent pas d’espaces, de virgules ou d’autres séparateurs de mots, vous devez les associer à un type d’informations sensibles qui utilise un REGEX conçu pour détecter les chaînes multi-mots qui suivent le modèle souhaité (par exemple, un nombre fixe de mots consécutifs commençant par un caractère majuscule),  ou un dictionnaire de mots clés qui répertorie toutes les valeurs uniques de cette colonne. Par exemple, s’il existe une colonne de preuve supplémentaire pour la ville ou la résidence d’une personne, vous pouvez créer une liste avec tous les noms de villes uniques de la table et l’utiliser pour créer un type d’informations sensibles basé sur un dictionnaire. Utilisez ce SIT comme élément de classification pour la colonne correspondante dans votre type d’informations sensibles EDM en exportant et en modifiant la définition SIT EDM dans XML. Consultez [Créer un package de règles manuellement](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually).|
|La fonction de test SIT ne détecte aucune correspondance.   | Vérifiez si le SIT que vous avez sélectionné inclut des exigences pour des mots clés supplémentaires ou d’autres validations. Pour les SIT intégrés, consultez les [définitions d’entité de type Informations sensibles](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) pour vérifier quelles sont les exigences minimales pour la correspondance de chaque type.        |
|La fonctionnalité de test fonctionne, mais vos éléments SharePoint ou OneDrive ne sont pas détectés dans les règles DLP ou d’étiquetage automatique     | Vérifiez si les documents que vous souhaitez mettre en correspondance s’affichent dans l’Explorateur de contenu. S’ils ne sont pas présents, n’oubliez pas que seul le contenu créé après les modifications apportées au type d’informations sensibles s’affichera sous forme de correspondances. Vous devez recrawl les sites et les bibliothèques pour que les éléments préexistants s’affichent. Consultez [manuellement la demande d’analyse et de réindexation d’un site, d’une bibliothèque ou d’une liste](/sharepoint/crawl-site-content) pour plus d’informations sur la recrawling SharePoint et OneDrive.        |
|Les règles DLP ou d’étiquetage automatique qui nécessitent plusieurs correspondances ne se déclenchent pas     |Vérifiez que les exigences de proximité pour votre type EDM et les types d’informations sensibles de base sont remplies. Par exemple, si la distance maximale entre l’élément principal et les mots clés de prise en charge est de 300 caractères, mais que les mots clés sont présents uniquement dans la première ligne d’une longue table, seules les premières lignes de valeurs correspondantes sont susceptibles de répondre aux exigences de proximité. Modifiez vos définitions SIT pour prendre en charge des règles de proximité plus souples ou utilisez l’option de document n’importe où pour les conditions de preuve supplémentaires.         |
|La détection d’un type EDM est incohérente ou erratique     |Vérifiez que le type d’informations sensibles que vous avez utilisé comme base pour l’élément principal dans votre type EDM ne détecte pas le contenu inutile. L’utilisation d’un SIT qui correspond à trop de contenu non lié, comme n’importe quel mot, n’importe quel nombre ou toutes les adresses e-mail, peut amener le service à saturer et à ignorer les correspondances pertinentes. Vérifiez le nombre de parties de contenu qui correspondent au type sensible que vous avez utilisé pour vos éléments principaux dans l’Explorateur de contenu. </br> Pour estimer si le SIT correspond à trop de contenu : </br> - Division du nombre d’éléments de contenu dans l’Explorateur de contenu par le nombre de jours écoulés depuis la création du type sensible. </br> - Si le nombre de correspondances par jour est de l’ordre de centaines de milliers ou de millions, il est possible que le sit principal soit trop large. Consultez [En savoir plus sur les types d’informations sensibles basés sur des correspondances de données exactes](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) pour obtenir des recommandations et des meilleures pratiques sur la sélection du type d’informations sensibles approprié pour un type EDM.         |
