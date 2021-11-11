---
title: Tester un type d’informations sensibles de correspondance exacte de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: configurer les services
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3030a97e3ed80524d2170e74b3d35f897b6ed74c
ms.sourcegitcommit: 8410a49995a084e4cc9b3f7286c8d506b7a85d79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2021
ms.locfileid: "60914812"
---
# <a name="test-an-exact-data-match-sensitive-information-type"></a>Tester un type d’informations sensibles de correspondance exacte de données

Une fois que votre type d’informations sensibles EDM (EDM) a été créé et une heure après avoir vérifié que le téléchargement et l’indexation de votre table d’informations sensibles sont terminés, vous pouvez vérifier qu’il détecte les informations que vous souhaitez détecter à l’aide de la fonction de test dans la section types d’informations sensibles du Centre de conformité.
 
>[! REMARQUE :] La propagation des modifications dans un sit EDM déjà créé peut prendre un certain temps dans le système. Si vous a apporté des modifications dans un type d’informations sensibles EDM pour résoudre les problèmes de détection, veillez à attendre au moins une heure après avoir apporté ces modifications avant d’utiliser la fonction de test pour valider leur impact.

## <a name="test-your-edm-sit-in-the-compliance-center"></a>Tester votre sit EDM dans le Centre de conformité

1. Ouvrez **le Centre de conformité** Types  >  **d’informations**  >  **sensibles de classification des données.**

2. Sélectionnez votre sit EDM dans la liste, puis **sélectionnez Tester** dans le volet volant. Cette option est uniquement présente dans la sit pour les types d’informations sensibles.
 
3. Télécharger un élément qui contient les données que vous souhaitez détecter. Par exemple, créez un élément qui contient un sous-ensemble des lignes de votre table d’informations sensibles. Si vous avez utilisé la fonctionnalité de correspondance configurable dans votre schéma pour définir des délimiteur ignorés, assurez-vous que l’élément inclut des exemples avec et sans ces délimiteurs.

4. Une fois le fichier téléchargé et analysé, recherchez les correspondances avec votre sit EDM.

5. Si la **fonction Test** dans la fonction SIT détecte une correspondance, validez qu’elle ne le coupe pas ou ne l’extrait pas de manière incorrecte. Par exemple, en extrayant uniquement une sous-chaîne de la chaîne complète qu’elle est supposée détecter, ou en sélectionnant uniquement le premier mot d’une chaîne de plusieurs mots, ou en incluant des symboles ou des caractères supplémentaires dans l’extraction. Voir [Langage des expressions régulières - Référence rapide pour](/dotnet/standard/base-types/regular-expression-language-quick-reference) la référence du langage d’expression régulière. 

5. Vous pouvez également utiliser l’cmdlet PowerShell suivante :

```powershell
Test-DataClassification  -ClassificationNames “[Your EDM sensitive info type]” -TexttoClassify “[your own text to scan for matches]” 
```

> [!NOTE]
 Lorsque vous créez ou modifiez un type d’informations sensibles EDM ou la fonction SIT principale sur laquelle est basé un type EDM, tout le contenu et le contenu modifiés après les modifications apportées aux sits seront analyser pour le texte qui correspond aux nouvelles définitions, mais le contenu existant ne sera pas analyser tant que les modifications ou réindexations n’auront pas été apportées. 

Pour forcer la ré-analyse du contenu existant dans un site ou une bibliothèque SharePoint ou dans OneDrive, suivez les instructions de la requête manuelle d’analyse et de [ré-indexation](/sharepoint/crawl-site-content)d’un site, d’une bibliothèque ou d’une liste.

## <a name="test-your-edm-sit-in-mip-policies"></a>Tester votre sit EDM dans les stratégies MIP

Vous pouvez voir où votre sit EDM est utilisé et comment il est précis en production en les utilisant dans les stratégies :

1. Créez une [stratégie d’étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) et exécutez-la dans **simulation.**

1. Ajoutez du contenu qui déclenchera l’EDM SIT et du contenu qui ne déclenchera pas l’EDM SIT à un emplacement que votre stratégie surveille.

1. Ouvrez **l’onglet Éléments pour vérifier** les correspondances.

1. A tune your policies as appropriate. 

Une fois que vous êtes satisfait des résultats de vos tests et de votre réglage, votre sit personnalisé basé sur EDM est prêt à être utilisé dans les stratégies de protection des informations, telles que :

- [Stratégies de protection contre la perte de données](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)
- [Stratégies de étiquetage automatique](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)
- [Microsoft Cloud App Security de fichiers](/cloud-app-security/data-protection-policies)

## <a name="troubleshooting-tips"></a>Conseils de dépannage

Si vous ne trouvez aucune correspondance, essayez ce qui suit :

- Confirmez que vos données sensibles ont été téléchargées correctement à l’aide des commandes expliquées dans les instructions de téléchargement de vos données sensibles à l’aide de l’outil EDM.

- Vérifiez que les exemples que vous avez entrés dans l’élément sont présents dans votre table d’informations sensibles et que les délimiteur ignorés sont corrects.

- Testez la fonction SIT que vous avez utilisée lorsque vous avez configuré l’élément principal dans chacun de vos modèles. Cela permettra de confirmer que la sit est en mesure de correspondre aux exemples de l’élément. L’utilisation d’un sit incorrectement défini comme élément de classification d’un type d’informations sensibles EDM est la cause la plus courante des échecs de détection dans EDM. 

- Si le sit que vous avez sélectionné pour un élément principal dans le type EDM ne trouve pas de correspondance dans l’élément ou trouve moins de correspondances que prévu, vérifiez qu’il prend en charge les séparateurs et les délimiteurs qui se trouvent dans le contenu. N’oubliez pas d’inclure les délimiteur ignorés définis dans votre schéma.

- Si la fonction Test ne détecte aucun contenu, vérifiez si la fonction SIT que vous avez sélectionnée inclut des exigences pour des mots clés supplémentaires ou d’autres validations. Pour les sits intégrées, voir définitions d’entités de type Informations [sensibles](sensitive-information-type-entity-definitions.md#sensitive-information-type-entity-definitions) pour vérifier les conditions minimales requises pour la correspondance de chaque type.

- Si la fonctionnalité Test fonctionne mais que vos éléments SharePoint ou OneDrive ne sont pas détectés dans les règles DLP ou d’adage automatique, vérifiez si les documents que vous souhaitez mettre en correspondance s’affiche dans l’Explorateur de contenu. S’ils ne sont pas là, n’oubliez pas que seul le contenu créé après les modifications apportées au type d’informations sensibles s’affiche sous forme de correspondances. Vous devez ré-analyser les sites et les bibliothèques pour que les éléments pré-existants s’afficheront. Voir [demande manuellement l’analyse](/sharepoint/crawl-site-content) et la ré-indexation d’un site, d’une bibliothèque ou d’une liste pour plus d’informations sur la ré-analyse SharePoint et OneDrive. 

- Si les règles DLP ou d’adage automatique qui nécessitent plusieurs correspondances ne se déclenchent pas, vérifiez que les exigences de proximité pour votre type EDM et les types d’informations sensibles de base sont respectées. Par exemple, si la distance maximale entre l’élément principal et les mots clés de prise en charge est de 300 caractères, mais que les mots clés ne sont présents que dans la première ligne d’un tableau long, seules les premières lignes de valeurs correspondantes sont susceptibles de répondre aux exigences de proximité. Modifiez vos définitions SIT pour prendre en charge des règles de proximité plus relâchées ou utilisez l’option n’importe où dans le document pour les conditions de preuve supplémentaires. 

- Si la détection d’un type EDM est incohérente ou incohérente, vérifiez que le type d’informations sensibles que vous avez utilisé comme base pour l’élément principal dans votre type EDM ne détecte pas le contenu inutile. L’utilisation d’un sit qui correspond à trop de contenu non lié, comme n’importe quel mot, n’importe quel nombre, toutes les adresses de messagerie peuvent saturer le service et ignorer les correspondances pertinentes. Vérifiez le nombre d’éléments de contenu qui correspondent au type sensible que vous avez utilisé pour vos éléments principaux dans l’Explorateur de contenu. Pour estimer si la sit correspond à trop de contenu :
    1. Divisant le nombre d’éléments de contenu dans l’Explorateur de contenu par le nombre de jours depuis la création du type sensible.
    2. Si le nombre de correspondances par jour est de l’une des centaines de milliers ou des millions, il est possible que la sit principale soit trop large. Voir [En savoir plus sur les types](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) d’informations sensibles basés sur les correspondances de données exactes pour obtenir des recommandations et des meilleures pratiques sur la sélection du type d’informations sensibles pour un type EDM. 

- Confirmez que vos données sensibles ont été téléchargées correctement à l’aide des commandes expliquées dans [hachage](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)et téléchargez la table des sources d’informations sensibles pour obtenir des types d’informations sensibles de correspondance exacte.

- Si le sit que vous avez sélectionné pour un élément principal dans le type EDM ne trouve pas de correspondance dans l’élément ou trouve moins de correspondances que prévu, vérifiez qu’il prend en charge les séparateurs et les délimiteurs qui existent dans le contenu. N’oubliez pas d’inclure les délimiteur ignorés définis dans votre schéma. 

