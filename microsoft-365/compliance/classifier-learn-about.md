---
title: En savoir plus sur les classifieurs avec capacité d’apprentissage
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- highpri
- purview-compliance
- m365solution-mip
- m365initiative-compliance
- highpri
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Les classifieurs pouvant être formés peuvent reconnaître différents types de contenu pour l’étiquetage ou l’application de stratégie en lui donnant des exemples positifs et négatifs à examiner.
ms.openlocfilehash: 37dc3e1f57d4572e95eb78c9794a120f9c99d19c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630247"
---
# <a name="learn-about-trainable-classifiers"></a>En savoir plus sur les classifieurs avec capacité d’apprentissage

La catégorisation et l’étiquetage du contenu afin qu’ils puissent être protégés et gérés correctement constituent le point de départ de la discipline de protection des informations. Microsoft Purview a trois façons de classer le contenu.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="manually"></a>Manuellement

La catégorisation manuelle nécessite un jugement et une action humains. Les utilisateurs et les administrateurs classent le contenu à mesure qu’ils le rencontrent. Vous pouvez utiliser les étiquettes préexistantes et les types d’informations sensibles ou utiliser des étiquettes créées personnalisées.  Vous pouvez ensuite protéger le contenu et gérer sa destruction.

## <a name="automated-pattern-matching"></a>Mise en correspondance automatisée des modèles

Ces mécanismes de catégorisation incluent la recherche de contenu par :

- Mots clés ou valeurs de métadonnées (langage de requête de mot clé).
- Utilisation de modèles précédemment identifiés d’informations sensibles telles que les numéros de sécurité sociale, de carte de crédit ou de compte bancaire [(définitions d’entités de type Informations sensibles).](sensitive-information-type-entity-definitions.md)
- Reconnaissance d’un élément, car il s’agit d’une variante d’un modèle [(impression par doigt de document).](document-fingerprinting.md)
- Utilisation de la présence de chaînes exactes [correspondant exactement aux données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types).

Les étiquettes de confidentialité et de rétention peuvent ensuite être appliquées automatiquement pour rendre le contenu disponible pour une utilisation dans [En savoir plus sur Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md) et [appliquer automatiquement des stratégies pour les étiquettes de rétention](apply-retention-labels-automatically.md).

## <a name="classifiers"></a>Classificateurs

Cette méthode de catégorisation est bien adaptée au contenu qui n’est pas facile à identifier par les méthodes de mise en correspondance de modèle manuelles ou automatisées. Cette méthode de catégorisation consiste davantage à utiliser un classifieur pour identifier un élément en fonction de ce qu’est l’élément, et non par les éléments qui se trouvent dans l’élément (critères spéciaux). Un classifieur apprend à identifier un type de contenu en examinant des centaines d’exemples de contenu qui vous intéressent.

> [!NOTE]
> En préversion : vous pouvez afficher les classifieurs pouvant être formés dans l’Explorateur de contenu en développant les **classifieurs pouvant être entraînés** dans le panneau filtres. Les classifieurs pouvant être formés affichent automatiquement le nombre d’incidents détectés dans SharePoint, Teams et OneDrive, sans nécessiter d’étiquetage.
> Si vous ne souhaitez pas utiliser cette fonctionnalité, vous devez envoyer une demande auprès de Support Microsoft. Cela désactive l’affichage de vos données sensibles qui ne sont utilisées dans aucune stratégie d’étiquetage dans l’Explorateur de contenu. Vous pouvez également désactiver l’analyse de vos données. Si l’analyse est désactivée, l’étiquetage de sensibilité et les stratégies DLP avec ces classifieurs ne fonctionnent pas

### <a name="where-you-can-use-classifiers"></a>Où vous pouvez utiliser des classifieurs

Les classifieurs peuvent être utilisés comme condition pour :

- [Étiquetage automatique Office avec étiquettes de confidentialité](apply-sensitivity-label-automatically.md)
- [Appliquer automatiquement une stratégie d’étiquette de rétention en fonction d’une condition](apply-retention-labels-automatically.md#configuring-conditions-for-auto-apply-retention-labels)
- [Conformité des communications](communication-compliance.md)
- Les étiquettes de confidentialité peuvent utiliser des classifieurs comme conditions. [Consultez Appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md).
- [Protection contre la perte de données](dlp-learn-about-dlp.md)

> [!IMPORTANT]
> Les classifieurs fonctionnent uniquement avec des éléments qui ne sont pas chiffrés.

## <a name="types-of-classifiers"></a>Types de classifieurs

- **classifieurs préentrifiés** : Microsoft a créé et préentragé plusieurs classifieurs que vous pouvez commencer à utiliser sans les former. Ces classifieurs s’affichent avec l’état .`Ready to use`
- **classifieurs entraînés personnalisés** : si vous avez des besoins d’identification et de catégorisation de contenu qui dépassent ce que couvrent les classifieurs préentrifiés, vous pouvez créer et former vos propres classifieurs.

Consultez les [définitions des classifieurs Pouvant être formés](classifier-tc-definitions.md#trainable-classifiers-definitions) pour obtenir la liste complète de tous les classifieurs préentrifiés.

### <a name="custom-classifiers"></a>Classifieurs personnalisés

Lorsque les classifieurs préformés ne répondent pas à vos besoins, vous pouvez créer et entraîner vos propres classifieurs. Il y a davantage de travail à faire pour créer les vôtres, mais ils seront beaucoup mieux adaptés aux besoins de votre organisation.

Vous commencez à créer un classifieur entraîné personnalisé en lui fournissant des exemples qui sont certainement dans la catégorie. Une fois qu’il traite ces exemples, vous le testez en lui donnant un mélange d’exemples correspondants et non correspondants. Le classifieur effectue ensuite des prédictions quant à savoir si un élément donné appartient à la catégorie que vous créez. Vous confirmez ensuite ses résultats, en triant les vrais positifs, les vrais négatifs, les faux positifs et les faux négatifs pour améliorer la précision de ses prédictions.

Lorsque vous publiez le classifieur, il trie les éléments dans des emplacements tels que SharePoint Online, Exchange et OneDrive, puis classifie le contenu. Après avoir publié le classifieur, vous pouvez continuer à l’entraîner à l’aide d’un processus de commentaires similaire au processus de formation initial.

Par exemple, vous pouvez créer des classifieurs pouvant être formés pour :

- Documents juridiques , tels que le privilège client d’avocat, les ensembles fermants, la déclaration de travail
- Documents commerciaux stratégiques , tels que les communiqués de presse, les fusions et acquisitions, les transactions, les plans commerciaux ou marketing, la propriété intellectuelle, les brevets, les documents de conception
- Informations de tarification , telles que les factures, les devis de prix, les commandes professionnelles, les documents d’enchères
- Informations financières, telles que les investissements organisationnels, les résultats trimestriels ou annuels

#### <a name="process-flow-for-creating-custom-classifiers"></a>Flux de processus pour la création de classifieurs personnalisés

La création et la publication d’un classifieur à utiliser dans les solutions de conformité, telles que les stratégies de rétention et la supervision des communications, suivent ce flux. Pour plus d’informations sur la création d’un classifieur pouvant être entraîné personnalisé, consultez [La création d’un classifieur personnalisé](classifier-get-started-with.md).

![classifieur personnalisé de flux de processus.](../media/classifier-trainable-classifier-flow.png)

### <a name="retraining-classifiers"></a>Reformation des classifieurs

Vous pouvez aider à améliorer la précision de tous les classifieurs entraînés personnalisés et en leur fournissant des commentaires sur la précision de la classification qu’ils effectuent. Il s’agit d’un réentraînement qui suit ce flux de travail.

> [!NOTE]
> Les classifieurs préentraînés ne peuvent pas être réentraînés.

![workflow de réentraînement du classifieur.](../media/classifier-retraining-workflow.png)

## <a name="provide-matchnot-a-match-accuracy-feedback-in-trainable-classifiers"></a>Fournir un retour de précision de correspondance/non dans les classifieurs pouvant être formés

Vous pouvez afficher le nombre de correspondances d’un classifieur pouvant être formé dans **l’Explorateur de contenu** et **les lassifieurs Pouvant être formés**. Vous pouvez également fournir des commentaires sur la question de savoir si un élément est réellement une correspondance ou non à l’aide du mécanisme **de commentaires Match**, **Pas une** correspondance et utiliser ces commentaires pour ajuster vos classifieurs. Pour plus d’informations, voir [Augmenter la précision du classifieur (préversion](data-classification-increase-accuracy.md) ). 


## <a name="see-also"></a>Voir aussi

- [Étiquettes de rétention](retention.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Impression de doigts de document](document-fingerprinting.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
