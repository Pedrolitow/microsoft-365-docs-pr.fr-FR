---
title: Prise en main de la classification des données (aperçu)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Le tableau de bord de classification des données vous permet de consulter les données sensibles qui ont été trouvées et classifiées au sein de votre organisation.
ms.openlocfilehash: d16167f33be1858733173026b09f268d9cf67d62
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929416"
---
# <a name="know-your-data---data-classification-overview-preview"></a>Connaissez vos données : vue d’ensemble de la classification des données (aperçu)

En tant qu’administrateur Microsoft 365 ou administrateur de conformité, vous pouvez évaluer et baliser les contenus de votre organisation afin de contrôler leur destination, de les protéger où qu’ils soient et de vous assurer qu’ils sont conservés et supprimés en fonction des besoins de votre organisation. Pour ce faire, vous devez utiliser les [étiquettes de confidentialité](sensitivity-labels.md), les [étiquettes de rétention](labels.md) et la classification des informations sensibles par types. Plusieurs méthodes s’offrent à vous pour effectuer la découverte, l’évaluation et le balisage, mais le résultat final est de disposer d’un grand nombre de documents et de messages électroniques balisés et classifiés avec ces étiquettes. Après avoir appliqué vos étiquettes de rétention et vos étiquettes de sensibilité, vous souhaiterez voir de quelle manière elles sont utilisées par vos clients. La page classification des données fournit une visibilité dans ce corps de contenu, notamment :

- le nombre d’éléments qui ont été classifiés en tant que types d’informations sensibles et la nature de ces classifications
- les étiquettes de confidentialité les plus utilisées dans Microsoft 365 et Azure Information Protection
- les étiquettes de rétention les plus utilisées
- la synthèse des activités que les utilisateurs effectuent sur votre contenu sensible
- les emplacements de vos données sensibles et conservées

Vous trouverez la classification des données dans le **Centre de conformité Microsoft 365** ou le **Centre de sécurité Microsoft 365** > **Classification** > **Classification des données**.

## <a name="sensitive-information-types-used-most-in-your-content"></a>Types d’informations sensibles utilisés le plus fréquemment dans votre contenu

Microsoft 365 fournit de nombreuses définitions des types d’informations sensibles, par exemple un élément contenant un numéro de sécurité sociale ou un numéro de carte bancaire. Pour plus d’informations sur les types d’informations sensibles, voir [Eléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md).

La carte type d’informations sensibles présente les principaux types d’informations sensibles qui ont été détectés et étiquetés au sein de votre organisation.

![principaux types d’informations sensibles](../media/data-classification-sens-info-types-card.png)

Pour déterminer le nombre d’éléments dans une catégorie de classification donnée, pointez sur la barre pour la catégorie.

![détail de pointage des principaux types d’informations sensibles](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Si la carte affiche le message « Aucune donnée détectée avec des informations sensibles ». Cela signifie qu’il n’y a aucun élément de votre organisation classifié comme étant un type d’informations sensibles ou aucun élément analysé. Pour commencer à utiliser les étiquettes, voir :
>- [Étiquettes de confidentialité](sensitivity-labels.md)
>- [Étiquettes de rétention](labels.md)
>- [Éléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>Principales étiquettes de confidentialité appliquées au contenu

Lorsque vous appliquez une étiquette de confidentialité à un élément via Microsoft 365 ou Azure information protection (AIP), deux événements se produisent :

- une balise qui indique que la valeur de l’élément pour votre organisation est incorporée dans le document et qu’elle le suivra partout
- la présence de la balise permet différents comportements de protection, tels que le filigrane ou le chiffrement obligatoires. Lorsque la protection de point de terminaison est activée, vous pouvez même empêcher un élément de quitter votre contrôle organisationnel.

Pour plus d’informations sur les étiquettes de confidentialité, voir : [En savoir plus sur les étiquettes de confidentialité](sensitivity-labels.md).

Les étiquettes de confidentialité doivent être activées pour les fichiers stockés dans SharePoint et OneDrive pour que les données correspondantes apparaissent dans la page de classification des données. Pour en savoir plus, consulter [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](sensitivity-labels-sharepoint-onedrive-files.md).

La carte d’étiquette de confidentialité affiche le nombre d’éléments (adresse de messagerie ou document) par niveau de confidentialité.

![répartition du contenu par capture d’écran de l’espace réservé pour la classification des étiquettes de confidentialité](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Si vous n’avez pas créé ou publié d’étiquettes de confidentialité ou si aucune étiquette de confidentialité n’a été appliquée à votre contenu, cette carte affiche le message « Aucune étiquette de confidentialité détectée ». Pour commencer à utiliser les étiquettes, voir :
>- [étiquettes de confidentialité](sensitivity-labels.md) ou pour AIP [configurer la stratégie Azure Information Protection](https://docs.microsoft.com/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>Principales étiquettes de rétention appliquées au contenu

Les étiquettes de rétention sont utilisées pour gérer la disposition du contenu au sein de votre organisation. Lorsqu’elles sont appliquées, elles peuvent être utilisées pour contrôler la durée de conservation d’un document avant sa suppression, s’il doit être révisé avant sa suppression, la date d’expiration de sa période de rétention, ou s’il doit être marqué comme un enregistrement qui ne peut pas être supprimé. Pour plus d’informations, voir[Vue d’ensemble des étiquettes de rétention](labels.md).

La carte étiquettes de rétention les plus utilisées vous indique le nombre d’éléments ayant une étiquette de rétention donnée.

![capture d’écran de l’espace réservé pour les étiquettes de rétention les plus utilisées](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Si cette carte affiche le message, « Aucune étiquette de rétention détectée », cela veut dire que vous n’avez pas créé ou publié d’étiquettes de rétention ou qu’aucune étiquette de rétention n’a été appliquée à votre contenu. Pour commencer à utiliser les étiquettes de rétention, voir :
>- [Vue d’ensemble des étiquettes de rétention](labels.md)

## <a name="top-activities-detected"></a>Principales activités détectées

Cette carte décrit brièvement les actions les plus courantes que les utilisateurs effectuent sur les éléments étiquetés comme sensibles. Vous pouvez utiliser [L’explorateur d’activité](data-classification-activity-explorer.md) pour explorer en profondeur huit activités différentes que Microsoft 365 suit sur le contenu étiqueté et le contenu qui se trouve sur les points de terminaison de Windows 10.

> [!NOTE]
> Si cette carte affiche le message « Aucune activité détectée », cela signifie qu’il n’y a eu aucune activité sur les fichiers, ou que l’audit de l’utilisateur et de l’administrateur n’est pas activé. Pour activer les journaux d’audit, voir :
>- [Effectuer des recherches dans le journal d’audit depuis le centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Données étiquetées confidentielles ou retenues par emplacement

L’objectif de la création de rapports sur la classification des données est de fournir une visibilité sur le nombre d’éléments qui ont une étiquette, ainsi que leur emplacement. Ces cartes vous permettent de connaître le nombre d’éléments étiquetés dans Exchange, SharePoint, OneDrive, etc.

> [!NOTE]
> Si cette carte affiche le message, « Aucun emplacement détecté », cela veut dire que vous n’avez pas créé ou publié d’étiquettes de confidentialité ou qu’aucune étiquette de confidentialité n’a été appliquée à votre contenu. Pour commencer à utiliser les étiquettes de confidentialité, voir :
>- [Étiquettes de confidentialité](sensitivity-labels.md)

## <a name="see-also"></a>Voir aussi

- [Afficher l’activité des étiquettes (aperçu)](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté (aperçu)](data-classification-content-explorer.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](labels.md)
- [Éléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md)
- [Vue d’ensemble des stratégies de rétention](retention-policies.md)
