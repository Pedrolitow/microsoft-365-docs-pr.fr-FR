---
title: Comment utiliser le tableau de bord de classification des données Microsoft
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- tier1
- highpri
- purview-compliance
- m365solution-mip
- m365initiative-compliance
- highpri
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Le tableau de bord de classification de conformité microsoft Purview fournit une visibilité sur la quantité de données sensibles trouvées et classifiées dans votre organisation.
ms.openlocfilehash: 07bad3c98cd5df9fa4d3265808bb25f401f7d972
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68794223"
---
# <a name="how-to-use-the-microsoft-data-classification-dashboard"></a>Comment utiliser le tableau de bord de classification des données Microsoft

En tant qu’administrateur Microsoft 365 ou administrateur de conformité, vous pouvez évaluer et baliser le contenu de votre organisation afin de contrôler sa circulation, de le protéger peut importe son emplacement et vous assurer qu’il est conservé et supprimé selon les besoins de votre organisation. Pour ce faire, vous devez utiliser les [étiquettes de confidentialité](sensitivity-labels.md), les [étiquettes de rétention](retention.md#retention-labels) et la classification des informations sensibles par types. Il existe différentes façons de procéder à la découverte, l’évaluation et le balisage, mais au final, vous pouvez avoir un très grand nombre de documents et d’e-mails marqués et classés avec l’une de ces étiquettes, ou les deux. Après avoir appliqué vos étiquettes de rétention et vos étiquettes de confidentialité, vous souhaiterez voir de quelle manière elles sont utilisées par vos clients. La page classification des données fournit une visibilité dans ce corps de contenu, notamment :

- le nombre d’éléments qui ont été classifiés en tant que types d’informations sensibles et la nature de ces classifications
- les étiquettes de confidentialité les plus utilisées dans Microsoft 365 et Azure Information Protection
- les étiquettes de rétention les plus utilisées
- la synthèse des activités que les utilisateurs effectuent sur votre contenu sensible
- les emplacements de vos données sensibles et conservées

Vous pouvez également gérer ces fonctionnalités sur la page classification de données :

- [classifieurs avec capacité d’apprentissage](classifier-learn-about.md)
- [types d’informations sensibles](sensitive-information-type-learn-about.md)
- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Explorateur de contenu](data-classification-content-explorer.md)
- [Explorateur d’activités](data-classification-activity-explorer.md)

Vous trouverez la classification des données dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> ou <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">le portail Microsoft 365 Defender</a> > **Classification** > **Classification des données**.

Suivez une visite guidée par vidéo sur nos fonctionnalités de classification de données.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

La classification de données analyse votre contenu sensible et le contenu étiqueté avant votre création de stratégies. Cette opération est appelée **zéro gestion des modifications**. Cela vous permet de voir l’impact de toutes les étiquettes de rétention et de confidentialité sur votre environnement, et de vous aider à évaluer vos besoins en matière de protection et de stratégie de gouvernance.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="prerequisites"></a>Configuration requise

### <a name="permissions"></a>Autorisations

 Pour accéder à la page de classification de données, un compte doit être affecté à une appartenance dans l’un de ces rôles ou groupes de rôles.

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

> [!NOTE]
> Il est recommandé de toujours utiliser le rôle avec le moins de privilèges pour garantir l’accès à la classification des données de Microsoft 365.

#### <a name="roles-and-role-groups"></a>Rôles et groupes de rôles

Il existe des rôles et des groupes de rôles en préversion que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles applicables qui sont en préversion. Pour en savoir plus à leur sujet, consultez [Autorisations dans la portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

- Administrateur Information Protection
- Analyste Information Protection
- Enquêteur Information Protection
- Lecteur Information Protection

Voici une liste des groupes de rôles applicables en préversion. Pour en savoir plus à leur sujet, consultez [Autorisations dans la portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

- Protection des informations
- Administrateurs Information Protection
- Analystes Information Protection
- Enquêteurs Information Protection
- Lecteurs Information Protection

## <a name="sensitive-information-types-used-most-in-your-content"></a>Types d’informations sensibles utilisés le plus fréquemment dans votre contenu

Microsoft 365 fournit de nombreuses définitions des types d’informations sensibles, par exemple un élément contenant un numéro de sécurité sociale ou un numéro de carte bancaire. Pour plus d’informations sur les types d’informations sensibles, voir les [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md).

La carte type d’informations sensibles présente les principaux types d’informations sensibles qui ont été détectés et étiquetés au sein de votre organisation.

![principaux types d’informations sensibles](../media/data-classification-sens-info-types-card.png)

Pour déterminer le nombre d’éléments dans une catégorie de classification donnée, pointez sur la barre pour la catégorie.

![détail de pointage des principaux types d’informations sensibles.](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> If the card displays the message "No data found with sensitive information", it means that there are no items in your organization that have been classified as being a sensitive information type or no items that have been crawled. To get started with labels, see:
>- [Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md)
>- [Prise en main de la gestion des enregistrements](get-started-with-records-management.md)
>- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>Principales étiquettes de confidentialité appliquées au contenu

Lorsque vous appliquez une étiquette de confidentialité à un élément via Microsoft 365 ou Azure information protection (AIP), deux événements se produisent :

- Une balise qui indique que la valeur de l’élément pour votre organisation est incorporée dans le document et qu’elle le suivra partout.
- La présence de la balise permet différents comportements de protection, tels que le filigrane ou le chiffrement obligatoires. Lorsque la protection de point de terminaison est activée, vous pouvez même empêcher un élément de quitter votre contrôle organisationnel.

Pour plus d’informations sur les étiquettes de confidentialité, voir : [En savoir plus sur les étiquettes de confidentialité](sensitivity-labels.md).

Les étiquettes de confidentialité doivent être activées pour les fichiers stockés dans SharePoint et OneDrive pour que les données correspondantes apparaissent dans la page de classification des données. Pour plus d’informations, voir [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

La carte d’étiquette de confidentialité affiche le nombre d’éléments (adresse de messagerie ou document) par niveau de confidentialité.

![répartition du contenu par capture d’écran de l’espace réservé pour la classification des étiquettes de confidentialité.](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> If you haven't created or published any sensitivity labels or no content has had a sensitivity label applied, this card will display the message "No sensitivity labels detected". To get started with sensitivity labels, see:
>- [Commencez avec les étiquettes de sensibilité](get-started-with-sensitivity-labels.md) ou pour AIP [Configurer la politique de protection des informations sur Azure](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>Principales étiquettes de rétention appliquées au contenu

Les étiquettes de rétention sont utilisées pour gérer la disposition du contenu au sein de votre organisation. Lorsqu’elles sont appliquées, elles peuvent être utilisées pour contrôler la durée de conservation d’un document avant sa suppression, s’il doit être révisé avant sa suppression, la date d’expiration de sa période de rétention, ou s’il doit être marqué comme un enregistrement. Pour plus d’informations, voir [En savoir plus sur les stratégies et les étiquettes de rétention](retention.md).

La carte étiquettes de rétention les plus utilisées vous indique le nombre d’éléments ayant une étiquette de rétention donnée.

![capture d’écran de l’espace réservé pour les étiquettes de rétention les plus utilisées.](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> If this card displays the message, "No retention labels detected", it means you haven't created or published any retention labels or no content has had a retention label applied. To get started with retention labels, see:
>- [Prise en main de la gestion du cycle de vie des données](get-started-with-data-lifecycle-management.md)

## <a name="top-activities-detected"></a>Principales activités détectées

Cette carte décrit brièvement les actions les plus courantes que les utilisateurs effectuent sur les éléments étiquetés comme sensibles. Vous pouvez utiliser [L’explorateur d’activité](data-classification-activity-explorer.md) pour explorer en profondeur les différentes activités que Microsoft 365 suit sur le contenu étiqueté et le contenu qui se trouve sur les points de terminaison de Windows 10.

> [!NOTE]
> If this card displays the message, "No activity detected" it means that there's been no activity on the files or that user and admin auditing isn't turned on. To turn the audit logs on , see:
>- [Rechercher dans le journal d’audit dans le portail de conformité Microsoft Purview](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Données étiquetées confidentielles ou retenues par emplacement

L’objectif de la création de rapports sur la classification des données est de fournir une visibilité sur le nombre d’éléments qui ont une étiquette, ainsi que leur emplacement. Ces cartes vous permettent de connaître le nombre d’éléments étiquetés dans Exchange, SharePoint, OneDrive, etc.

> [!NOTE]
> If this card displays the message, "No locations detected, it means you haven't created or published any sensitivity labels or no content has had a retention label applied. To get started with sensitivity labels, see:
>- [Étiquettes de confidentialité](sensitivity-labels.md)

## <a name="public-preview-release-notes"></a>Notes de publication de la préversion publique 

> [!NOTE]
> **Nombre de boîtes aux lettres Exchange**: vous remarquerez qu’une petite info-bulle s’affiche lorsque vous explorez les boîtes aux lettres Exchange. Il s'agit là d'évoquer le fait que le nombre agrégé affiché pour le type d’information sensible, l’étiquette de confidentialité et l’étiquette de rétention ne correspondent pas parfaitement au nombre d’éléments que vous trouverez dans la boîte aux lettres. Cela est dû au fait que l’exploration vers le bas dans le dossier extrait la vue dynamique du contenu, qui est classifié, tandis que le nombre agrégé est calculé. Informations que l’utilisateur doit remarquer même en cas d’écrémage

> [!NOTE]
> **Le rendu des documents chiffrés**: les fichiers SharePoint, Exchange et OneDrive chiffrés ne s’affichent pas dans l’Explorateur de contenu. Il s’agit d’un problème sensible qui nécessite un équilibre entre le besoin d'afficher le contenu de fichiers dans l’explorateur de contenu et la nécessité de conserver les contenus chiffrés. Avec les autorisations accordées par les groupes de rôles **Visionneuse de listes de l’Explorateur de contenu** et **Afficheur de contenu**, vous verrez une vue de liste des fichiers, des métadonnées de fichier et un lien que vous pouvez utiliser pour accéder au contenu via le client web. Informations que l’utilisateur doit remarquer même en cas d’écrémage

> [!NOTE]
> **Caractères pris en charge dans les noms d’étiquette de rétention dans la recherche SharePoint** : la recherche SharePoint ne prend pas en charge les noms d’étiquette de rétention avec `-`ou `_` . Par exemple, `Label-MIP` et `Label_MIP` ne sont pas pris en charge. La recherche SharePoint prend en charge ces caractères dans les noms d’étiquettes de confidentialité et les noms de type information sensible.

> [!NOTE]
> **OneDrive reste en préversion**: nous vous remercions pour vos précieux commentaires sur l’intégration de OneDrive pendant notre programme de préversion. À mesure que nous travaillons sur les détails, vous pouvez constater des données/flux incohérents. Nous continuerons à proposer OneDrive en préversion jusqu’à ce que tous les correctifs soient en place. Nous apprécions votre soutien constant.

## <a name="see-also"></a>Voir aussi

- [Afficher l’activité des étiquettes](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté](data-classification-content-explorer.md)
- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Découvrez les classificateurs de formation (préversion)](classifier-learn-about.md)

Pour découvrir comment utiliser la classification des données afin de respecter les réglementations en matière de confidentialité des données, voir [Déployer la protection des informations pour les réglementations relatives à la confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md)  (aka.ms/m365dataprivacy).
