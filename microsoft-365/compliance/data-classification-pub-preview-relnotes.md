---
title: Notes de la publication préliminaire sur la notification de données (préversion)
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
description: Notes de publication préliminaire pour la préversion publique sur la classification des données.
ms.openlocfilehash: fecf643d12cf544c16570c173b15bb1e0dc043f0
ms.sourcegitcommit: 3d17c1d6b80672719b1878e2f321f0de39595226
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "41887335"
---
# <a name="data-classification-public-preview-release-notes-preview"></a>Notes de publication préliminaire publique sur la notification de données (préversion)

Cette publication préliminaire publique présente de nouvelles fonctionnalités dans lesquelles l’analyse de votre contenu sensible et du contenu étiqueté commence *avant* la création de vos stratégies. Cette opération est appelée **zéro gestion des modifications**. Cela vous permet de voir l’impact de toutes les étiquettes de rétention et de confidentialité sur votre environnement, et de vous aider à évaluer vos besoins en matière de protection et de stratégie de gouvernance.

Consultez ces notes de publication pour bénéficier d’une expérience optimale avec cette version d’évaluation publique. Nous nous concentrerons sur la résolution de ces points entre maintenant et la mise en disponibilité générale (GA).

## <a name="permissions-for-accessing-content-explorer"></a>Autorisations d’accès à l’explorateur de contenu

L’accès à l’explorateur de contenu est fortement restreint, car il vous permet de lire le contenu de fichiers numérisés. L’accès à l’explorateur de contenu nécessite de l’appartenance aux groupes de rôles **Visionneuse de listes de l'explorateur de contenu** et **Visionneuse de contenu de l'explorateur de contenu**. Aucun compte n’a accès à l’explorateur de contenu. Consultez [Utilisation de l’explorateur de contenu de la classification des données (préversion)](data-classification-content-explorer.md#permissions). Un administrateur général, un administrateur de conformité ou un administrateur de données peut attribuer l'appartenance nécessaire au groupe de rôle de la **visionneuse de liste de l’explorateur de contenu** et de la **visionneuse de contenu de l'explorateur de contenu**.

> [!TIP]
> Les groupes de rôle de la **visionneuse de liste de l'explorateur de contenu**et de la **visionneuse de contenu de l’explorateur de contenu** peuvent ne pas s’afficher sur la page des autorisations lorsque les Contrôles d’accès basés sur les rôles (RBAC) sont déployés dans le monde entier. S'ils n’apparaissent pas dans la page autorisations, vous devez créer un groupe de rôles personnalisé et attribuer le rôle `data classification list viewer` ou des rôles `data classification content viewer` à votre groupe de rôles personnalisé.

## <a name="exchange-mailbox-count"></a>Nombre de boîtes aux lettres Exchange

Vous remarquerez qu’une petite info-bulle apparaît lorsque vous explorez des boîtes aux lettres Exchange. Il s'agit là d'évoquer le fait que le nombre agrégé affiché pour le type d’information sensible, l’étiquette de confidentialité et l’étiquette de rétention ne correspondent pas parfaitement au nombre d’éléments que vous trouverez dans la boîte aux lettres. Cela est dû au fait que la descente dans la hiérarchie du dossier permet de récupérer l’affichage en direct du contenu, lequel est classifié, alors que le nombre agrégé est calculé.

## <a name="seeing-guids-instead-of-label-names"></a>Affichage de GUID au lieu des noms d’étiquettes

Les clients disposant d'une préversion privée ont remarqué des instances dans lesquelles la suppression d’une étiquette qui a déjà été marquée a des résultats dans les noms d’étiquettes, ce qui a pour effet de causer un GUID 32 bits dans l’explorateur de contenu et l’explorateur d’activités au lieu du nom de l’étiquette. 

## <a name="rendering-of-encrypted-documents"></a>Rendu de documents chiffrés

L'affichage des fichiers SharePoint, Exchange et OneDrive chiffrés n'a pas lieu dans l’explorateur de contenu. Il s’agit d’un problème sensible qui nécessite un équilibre entre le besoin d'afficher le contenu de fichiers dans l’explorateur de contenu et la nécessité de conserver les contenus chiffrés. Avec les autorisations accordées par les groupes de rôle de la **visionneuse de liste de l’explorateur de contenu**et la **visionneuse de contenu de l’explorateur de contenu**, un affichage de la liste des fichiers, des métadonnées de fichier et un lien que vous pouvez utiliser pour accéder au contenu via le client web.

## <a name="supported-characters-in-retention-label-names-in-sharepoint-search"></a>Caractères pris en charge dans les noms d'étiquettes de rétention de la recherche SharePoint

La recherche SharePoint ne prend pas en charge les noms d’étiquettes de rétention avec `-` ou `_` dans celles-ci. Par exemple, `Label-MIP` et `Label_MIP` ne sont pas pris en charge. La recherche SharePoint prend en charge ces caractères dans les noms d’étiquettes de confidentialité et les noms de type information sensible.

## <a name="see-also"></a>Voir aussi

- [Prise en main de la classification des données (préversion)](data-classification-overview.md)
- [Afficher l’activité des étiquettes (aperçu)](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté (aperçu)](data-classification-content-explorer.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](labels.md)
- [Éléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md)

