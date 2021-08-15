---
title: En savoir plus sur la classification des données
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
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Le tableau de bord de classification des données vous permet de consulter les données sensibles qui ont été trouvées et classifiées au sein de votre organisation.
ms.openlocfilehash: c85129d13b836b8eab8b15fa5fcbbc3813d908e2c49f11ca70d887b283944370
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53860873"
---
# <a name="learn-about-data-classification"></a>En savoir plus sur la classification des données

En tant qu'administrateur Microsoft 365 ou administrateur de conformité, vous pouvez évaluer puis baliser le contenu de votre organisation afin de contrôler où il va, de le protéger où qu'il soit et de vous assurer qu'il est préservé et supprimé en fonction des besoins de votre organisation. Pour ce faire, vous devez utiliser les [étiquettes de confidentialité](sensitivity-labels.md), les [étiquettes de rétention](retention.md#retention-labels) et la classification des informations sensibles par types. Plusieurs méthodes s’offrent à vous pour effectuer la découverte, l’évaluation et le balisage, mais le résultat final est de disposer d’un grand nombre de documents et de messages électroniques balisés et classifiés avec ces étiquettes. Après avoir appliqué vos étiquettes de rétention et vos étiquettes de confidentialité, vous souhaiterez voir de quelle manière elles sont utilisées par vos clients. La page classification des données fournit une visibilité dans ce corps de contenu, notamment :

- le nombre d’éléments qui ont été classifiés en tant que types d’informations sensibles et la nature de ces classifications
- les étiquettes de confidentialité les plus utilisées dans Microsoft 365 et Azure Information Protection
- les étiquettes de rétention les plus utilisées
- la synthèse des activités que les utilisateurs effectuent sur votre contenu sensible
- les emplacements de vos données sensibles et conservées

Vous pouvez également gérer ces fonctionnalités sur la page classification de données :

- [classifieurs avec capacité d’apprentissage](classifier-learn-about.md)
- [types d’informations sensibles](sensitive-information-type-learn-about.md)
- [correspondances exactes des données](create-custom-sensitive-information-types-with-exact-data-match-based-classification.md)
- [Explorateur de contenu](data-classification-content-explorer.md)
- [Explorateur d’activités](data-classification-activity-explorer.md)

Vous trouverez la classification des données dans le **Centre de conformité Microsoft 365** ou le **Centre de sécurité Microsoft 365** > **Classification** > **Classification de données**.

Suivez une visite guidée par vidéo sur nos fonctionnalités de classification de données.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

La classification de données analyse votre contenu sensible et le contenu étiqueté avant votre création de stratégies. Cette opération est appelée **zéro gestion des modifications**. Cela vous permet de voir l’impact de toutes les étiquettes de rétention et de confidentialité sur votre environnement, et de vous aider à évaluer vos besoins en matière de protection et de stratégie de gouvernance.

## <a name="prerequisites"></a>Configuration requise

Un certain nombre d’abonnements différents prennent en charge le DLP du Point de Terminaison. Pour afficher les options d’acquisition de la licence du DLP du Point de Terminaison, consultez [ Acquisition de la licence de Protection de l’Information à titre indicatif](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection). 

### <a name="permissions"></a>Autorisations

 Pour accéder à la page de classification de données, un compte doit être affecté à une appartenance dans l’un de ces rôles ou groupes de rôles.

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur des données de conformité

> [!NOTE]
> Il est recommandé de toujours utiliser le rôle avec le moins de privilèges pour garantir l’accès à la classification des données de Microsoft 365.

## <a name="sensitive-information-types-used-most-in-your-content"></a>Types d’informations sensibles utilisés le plus fréquemment dans votre contenu

Microsoft 365 fournit de nombreuses définitions des types d’informations sensibles, par exemple un élément contenant un numéro de sécurité sociale ou un numéro de carte bancaire. Pour plus d’informations sur les types d’informations sensibles, voir les [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md).

La carte type d’informations sensibles présente les principaux types d’informations sensibles qui ont été détectés et étiquetés au sein de votre organisation.

![principaux types d’informations sensibles](../media/data-classification-sens-info-types-card.png)

Pour déterminer le nombre d’éléments dans une catégorie de classification donnée, pointez sur la barre pour la catégorie.

![détail de pointage des principaux types d’informations sensibles](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Si la carte affiche le message « Aucune donnée détectée avec des informations sensibles ». Cela signifie qu’il n’y a aucun élément de votre organisation classifié comme étant un type d’informations sensibles ou aucun élément analysé. Pour commencer à utiliser les étiquettes, voir :
>- [Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md)
>- [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md)
>- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>Principales étiquettes de confidentialité appliquées au contenu

Lorsque vous appliquez une étiquette de confidentialité à un élément via Microsoft 365 ou Azure information protection (AIP), deux événements se produisent :

- une balise qui indique que la valeur de l’élément pour votre organisation est incorporée dans le document et qu’elle le suivra partout
- la présence de la balise permet différents comportements de protection, tels que le filigrane ou le chiffrement obligatoires. Lorsque la protection de point de terminaison est activée, vous pouvez même empêcher un élément de quitter votre contrôle organisationnel.

Pour plus d’informations sur les étiquettes de confidentialité, voir : [En savoir plus sur les étiquettes de confidentialité](sensitivity-labels.md).

Les étiquettes de confidentialité doivent être activées pour les fichiers stockés dans SharePoint et OneDrive pour que les données correspondantes apparaissent dans la page de classification des données. Pour plus d’informations, voir [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

La carte d’étiquette de confidentialité affiche le nombre d’éléments (adresse de messagerie ou document) par niveau de confidentialité.

![répartition du contenu par capture d’écran de l’espace réservé pour la classification des étiquettes de confidentialité](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Si vous n’avez pas créé ou publié d’étiquettes de confidentialité ou si aucune étiquette de confidentialité n’a été appliquée à votre contenu, cette carte affiche le message « Aucune étiquette de confidentialité détectée ». Pour commencer à utiliser les étiquettes de confidentialité, consultez :
>- [Commencez avec les étiquettes de sensibilité](get-started-with-sensitivity-labels.md) ou pour AIP [Configurer la politique de protection des informations sur Azure](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>Principales étiquettes de rétention appliquées au contenu

Les étiquettes de rétention sont utilisées pour gérer la disposition du contenu au sein de votre organisation. Lorsqu’elles sont appliquées, elles peuvent être utilisées pour contrôler la durée de conservation d’un document avant sa suppression, s’il doit être révisé avant sa suppression, la date d’expiration de sa période de rétention, ou s’il doit être marqué comme un enregistrement. Pour plus d’informations, voir [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md).

La carte étiquettes de rétention les plus utilisées vous indique le nombre d’éléments ayant une étiquette de rétention donnée.

![capture d’écran de l’espace réservé pour les étiquettes de rétention les plus utilisées](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Si cette carte affiche le message, « Aucune étiquette de rétention détectée », cela veut dire que vous n’avez pas créé ou publié d’étiquettes de rétention ou qu’aucun contenu n’a eu d’étiquette appliquée. Pour commencer à utiliser les étiquettes de confidentialité, consultez :
>- [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md)

## <a name="top-activities-detected"></a>Principales activités détectées

Cette carte décrit brièvement les actions les plus courantes que les utilisateurs effectuent sur les éléments étiquetés comme sensibles. Vous pouvez utiliser [L’explorateur d’activité](data-classification-activity-explorer.md) pour explorer en profondeur les différentes activités que Microsoft 365 suit sur le contenu étiqueté et le contenu qui se trouve sur les points de terminaison de Windows 10.

> [!NOTE]
> Si cette carte affiche le message « Aucune activité détectée », cela signifie qu’il n’y a eu aucune activité sur les fichiers, ou que l’audit de l’utilisateur et de l’administrateur n’est pas activé. Pour activer les journaux d’audit, consultez :
>- [Effectuer des recherches dans le journal d’audit depuis le centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Données étiquetées confidentielles ou retenues par emplacement

L’objectif de la création de rapports sur la classification des données est de fournir une visibilité sur le nombre d’éléments qui ont une étiquette, ainsi que leur emplacement. Ces cartes vous permettent de connaître le nombre d’éléments étiquetés dans Exchange, SharePoint, OneDrive, etc.

> [!NOTE]
> Si cette carte affiche le message, « Aucun emplacement détecté », cela veut dire que vous n’avez pas créé ou publié d’étiquettes de confidentialité ou qu’aucune étiquette de confidentialité n’a été appliquée à votre contenu. Pour commencer à utiliser les étiquettes de confidentialité, consultez :
>- [Étiquettes de confidentialité](sensitivity-labels.md)

## <a name="see-also"></a>Voir aussi

- [Afficher l’activité des étiquettes](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté](data-classification-content-explorer.md)
- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Découvrez les classificateurs de formation (préversion)](classifier-learn-about.md)

Pour découvrir comment utiliser la classification des données afin de respecter les réglementations en matière de confidentialité des données, voir [Déployer la protection des informations pour les réglementations relatives à la confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md)  (aka.ms/m365dataprivacy).