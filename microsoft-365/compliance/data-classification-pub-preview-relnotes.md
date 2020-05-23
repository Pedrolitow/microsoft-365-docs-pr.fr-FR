---
title: Notes de publication pour la classification des données
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
description: Notes de publication pour la classification des données.
ms.openlocfilehash: bbef6729680db2c9a6aec4caa9036ec23fad6949
ms.sourcegitcommit: f6840dfcfdbcadc53cda591fd6cf9ddcb749d303
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44327603"
---
# <a name="data-classification-release-notes"></a>Notes de publication pour la classification des données

Consultez ces notes de publication pour bénéficier d’une expérience optimale avec la classification des données.

## <a name="exchange-mailbox-count"></a>Nombre de boîtes aux lettres Exchange

Vous remarquerez qu’une petite info-bulle apparaît lorsque vous explorez des boîtes aux lettres Exchange. Il s'agit là d'évoquer le fait que le nombre agrégé affiché pour le type d’information sensible, l’étiquette de confidentialité et l’étiquette de rétention ne correspondent pas parfaitement au nombre d’éléments que vous trouverez dans la boîte aux lettres. Cela est dû au fait que la descente dans la hiérarchie du dossier permet de récupérer l’affichage en direct du contenu, lequel est classifié, alors que le nombre agrégé est calculé.


## <a name="rendering-of-encrypted-documents"></a>Rendu de documents chiffrés

L'affichage des fichiers SharePoint, Exchange et OneDrive chiffrés n'a pas lieu dans l’explorateur de contenu. Il s’agit d’un problème sensible qui nécessite un équilibre entre le besoin d'afficher le contenu de fichiers dans l’explorateur de contenu et la nécessité de conserver les contenus chiffrés. Avec les autorisations accordées par les groupes de rôle de la **visionneuse de liste de l’explorateur de contenu**et la **visionneuse de contenu de l’explorateur de contenu**, un affichage de la liste des fichiers, des métadonnées de fichier et un lien que vous pouvez utiliser pour accéder au contenu via le client web.

## <a name="supported-characters-in-retention-label-names-in-sharepoint-search"></a>Caractères pris en charge dans les noms d'étiquettes de rétention de la recherche SharePoint

La recherche SharePoint ne prend pas en charge les noms d’étiquettes de rétention avec `-` ou `_` dans celles-ci. Par exemple, `Label-MIP` et `Label_MIP` ne sont pas pris en charge. La recherche SharePoint prend en charge ces caractères dans les noms d’étiquettes de confidentialité et les noms de type information sensible.

## <a name="onedrive-remains-in-preview"></a>OneDrive reste en mode aperçu

Nous avons écouté vos commentaires intéressants sur l’intégration de OneDrive pendant notre programme d’évaluation. Au fur et à mesure que nous travaillons dans les détails, vous pouvez être amené à utiliser des données/flux incohérents. Nous continuerons à présenter OneDrive en version préliminaire jusqu’à ce que tous les correctifs soient en place. Nous apprécions votre support technique.


## <a name="see-also"></a>Voir aussi

- [Prise en main de la classification des données (préversion)](data-classification-overview.md)
- [Afficher l’activité des étiquettes (aperçu)](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté (aperçu)](data-classification-content-explorer.md)
- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](labels.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)