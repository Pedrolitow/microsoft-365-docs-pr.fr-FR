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
ms.openlocfilehash: 583a07eee97024d59efc8d81c1d7a9fd02d176ff
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526455"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Tester un type d’informations sensibles correspondant exactement aux données

Après avoir créé votre type d’informations sensibles EDM (Sensitive Information Type) et une heure après avoir vérifié que le chargement et l’indexation de votre table d’informations sensibles sont terminés, vous pouvez vérifier qu’il détecte les informations que vous souhaitez détecter à l’aide de la fonction de test dans la section types d’informations sensibles du Centre de conformité.
 
>[! REMARQUE :] La propagation des modifications dans un sit EDM déjà créé peut prendre un certain temps dans le système. Si vous a apporté des modifications dans un type d’informations sensibles EDM pour résoudre les problèmes de détection, veillez à attendre au moins une heure après avoir apporté ces modifications avant d’utiliser la fonction de test pour valider leur impact.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Tester votre sit EDM dans le Centre de conformité

1. **Ouvrez le Centre de** >  **conformitéData** **classificationSensitive** >  Information Types.

2. Sélectionnez votre sit EDM dans la liste, puis **sélectionnez Tester** dans le volet volant. Cette option n’est présente que sous les types d’informations sensibles.
 
3. Télécharger un élément qui contient les données que vous souhaitez détecter. Par exemple, créez un élément qui contient un sous-ensemble des lignes de votre table d’informations sensibles. Si vous avez utilisé la fonctionnalité de correspondance configurable dans votre schéma pour définir des délimiteur ignorés, assurez-vous que l’élément inclut des exemples avec et sans ces délimiteurs.

4. Une fois le fichier téléchargé et analysé, recherchez les correspondances avec votre sit EDM.

5. Si la **fonction Test** dans la fonction SIT détecte une correspondance, validez qu’elle ne le coupe pas ou ne l’extrait pas de manière incorrecte. Par exemple, en extrayant uniquement une sous-chaîne de la chaîne complète qu’elle est supposée détecter, ou en sélectionnant uniquement le premier mot d’une chaîne à plusieurs mots, ou en incluant des symboles ou des caractères supplémentaires dans l’extraction. Voir [Langage des expressions régulières - Référence rapide pour](/dotnet/standard/base-types/regular-expression-language-quick-reference) la référence du langage d’expression régulière. 

5. Vous pouvez également utiliser l’cmdlet PowerShell suivante :

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Lorsque vous créez ou modifiez un type d’informations sensibles EDM ou la fonction SIT principale sur laquelle est basé un type EDM, tout le contenu et le contenu modifiés après les modifications apportées aux sits seront analyser pour le texte qui correspond aux nouvelles définitions, mais le contenu existant ne sera pas analyser tant que les modifications ou réindexations n’auront pas été apportées. 

Pour forcer la ré-analyse du contenu existant dans un site ou une bibliothèque SharePoint ou dans OneDrive, suivez les instructions de demande manuelle d’analyse et de [réindexation](/sharepoint/crawl-site-content) d’un site, d’une bibliothèque ou d’une liste.

## <a name="test-your-edm-sit-in-mip-policies"></a>Tester votre sit EDM dans les stratégies MIP

Vous pouvez voir où votre sit EDM est utilisé et comment il est précis en production en les utilisant dans les stratégies :

1. Créez une [stratégie d’étiquetage automatique et exécutez-la](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) dans **simulation**.

1. Ajoutez du contenu qui déclenchera l’EDM SIT et du contenu qui ne déclenchera pas l’EDM SIT à un emplacement que votre stratégie surveille.

1. Ouvrez **l’onglet Éléments pour vérifier** les correspondances.

1. A tune your policies as appropriate. 

Une fois que vous êtes satisfait des résultats de vos tests et de votre réglage, votre sit personnalisé basé sur EDM est prêt à être utilisé dans les stratégies de protection des informations, telles que :

- [Stratégies de protection contre la perte de données](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Stratégies d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Cloud App Security de fichiers](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Conseils de dépannage

Si vous ne trouvez aucune correspondance, voici quelques conseils de dépannage.


|Problème  |Conseil de dépannage  |
|---------|---------|
|Aucune correspondance trouvée     |  Confirmez que vos données sensibles ont été téléchargées correctement à l’aide des commandes expliquées dans hachage et téléchargez la [table des sources](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) d’informations sensibles pour obtenir des types d’informations sensibles de correspondance exacte|
|Aucune correspondance trouvée   | Testez la fonction SIT que vous avez utilisée lorsque vous avez configuré l’élément principal dans chacun de vos modèles. Cela permettra de confirmer que la sit est en mesure de correspondre aux exemples de l’élément. L’utilisation d’un sit incorrectement défini comme élément de classification d’un type d’informations sensibles EDM est la cause la plus courante des échecs de détection dans EDM.         |
|La fonction SIT que vous avez sélectionnée pour un élément principal dans le type EDM ne trouve pas de correspondance dans l’élément ou trouve moins de correspondances que prévu    |  Vérifiez qu’il prend en charge les séparateurs et les délimiteurs qui se retrouvent dans le contenu. N’oubliez pas d’inclure les délimiteur ignorés définis dans votre schéma.       |
|L’élément principal SIT trouve des correspondances dans un élément, mais ce n’est pas le cas de l’EDM SIT.     | - Vérifiez vos instructions REGEX pour démarrer ou mettre fin à un délimiteur d’espace blanc de capture, comme /s. L’espace blanc ne correspond pas à la valeur de hachage dans la table de données. Utilisez plutôt un délimiteur de mots comme /b. </br> - Vérifiez vos instructions REGEX pour vous assurer qu’elles capturent la chaîne entière que vous souhaitez capturer, et pas seulement une sous-chaîne. Par exemple, ce modèle pour les adresses de messagerie [a-zA-Z]{30}@[a-zA-Z]{20}.[ a-zA-Z] *correspondra*{2,3} user@contoso.com et *user@contoso.co.jp*.  |
|Un sit EDM avec des éléments principaux et aucun élément secondaire défini ne détecte les éléments, mais ne détecte pas, ou ne détecte pas moins que prévu, lorsque des éléments principaux et secondaires sont requis.  | Assurez-vous que les valeurs des preuves secondaires sont composées d’un seul mot ou d’une chaîne qui ne contient pas d’espaces ou utilisez des instructions REGEX qui détectent des chaînes à plusieurs mots. Par exemple, \b[A-Z][a-z]{1,25}([ -][A-Z][a-z]{1,25}){0,4}\b, qui correspond à toute séquence d’un à cinq mots consécutifs qui commence par un caractère en minuscules. Utilisez cette sit comme élément de classification pour les conditions de preuve supplémentaires dans votre type d’informations sensibles EDM XML. Voir [Créer un package de règles manuellement](sit-get-started-exact-data-match-create-rule-package.md#create-a-rule-package-manually)|
|La fonction de test SIT ne détecte aucune correspondance.   | Vérifiez si le sit que vous avez sélectionné inclut des exigences pour des mots clés supplémentaires ou d’autres validations. Pour les sits intégrées, voir définitions d’entités de [type informations sensibles](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) pour vérifier les conditions minimales requises pour la correspondance de chaque type.        |
|La fonctionnalité Test fonctionne, mais vos éléments SharePoint ou OneDrive ne sont pas détectés dans les règles d’étiquetage automatique ou DLP     | Vérifiez si les documents que vous prévoyez de mettre en correspondance s’affiche dans l’Explorateur de contenu. S’ils ne sont pas là, n’oubliez pas que seul le contenu créé après les modifications apportées au type d’informations sensibles s’affichera sous forme de correspondances. Vous devez réaxer les sites et les bibliothèques pour que les éléments pré-existants s’afficheront. Voir [demande manuellement l’analyse et la réindexation](/sharepoint/crawl-site-content) d’un site, d’une bibliothèque ou d’une liste pour plus d’informations sur l’analyse SharePoint et OneDrive.        |
|Les règles d’étiquetage automatique ou DLP qui nécessitent plusieurs correspondances ne se déclenchent pas     |Vérifiez que les exigences de proximité pour votre type EDM et les types d’informations sensibles de base sont remplies. Par exemple, si la distance maximale entre l’élément principal et les mots clés de prise en charge est de 300 caractères, mais que les mots clés ne sont présents que dans la première ligne d’un tableau long, seules les premières lignes de valeurs correspondantes sont susceptibles de répondre aux exigences de proximité. Modifiez vos définitions SIT pour prendre en charge des règles de proximité plus relâchées ou utilisez l’option n’importe où dans le document pour les conditions de preuve supplémentaires.         |
|La détection d’un type EDM est incohérente ou incohérente     |Vérifiez que le type d’informations sensibles que vous avez utilisé comme base pour l’élément principal dans votre type EDM ne détecte pas le contenu inutile. L’utilisation d’une fonction SIT qui correspond à trop de contenu non lié, comme n’importe quel mot, n’importe quel nombre ou toutes les adresses de messagerie, peut saturer le service et ignorer les correspondances pertinentes. Vérifiez le nombre d’éléments de contenu qui correspondent au type sensible que vous avez utilisé pour vos éléments principaux dans l’Explorateur de contenu. </br> Pour estimer si la sit correspond à trop de contenu : </br> - Divisant le nombre d’éléments de contenu dans l’Explorateur de contenu par le nombre de jours depuis la création du type sensible. </br> - Si le nombre de correspondances par jour est de l’une des centaines de milliers ou des millions, il est possible que la sit principale soit trop large. Voir [En savoir plus sur les types](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) d’informations sensibles basés sur les correspondances de données exactes pour obtenir des recommandations et des meilleures pratiques sur la sélection du type d’informations sensibles pour un type EDM.         |