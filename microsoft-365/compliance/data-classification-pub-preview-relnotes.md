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
ms.openlocfilehash: 2b9302cfa49f9445d3cbeb5109aef70e0c8d8f7f
ms.sourcegitcommit: 47de4402174c263ae8d70c910ca068a7581d04ae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "49663039"
---
# <a name="data-classification-release-notes"></a>Notes de publication pour la classification des données


## <a name="exchange-mailbox-count"></a>Nombre de boîtes aux lettres Exchange

Vous remarquerez qu’une petite info-bulle apparaît lorsque vous explorez des boîtes aux lettres Exchange. Il s'agit là d'évoquer le fait que le nombre agrégé affiché pour le type d’information sensible, l’étiquette de confidentialité et l’étiquette de rétention ne correspondent pas parfaitement au nombre d’éléments que vous trouverez dans la boîte aux lettres. Cela est dû au fait que descendre dans la hiérarchie du dossier permet de récupérer l’affichage en direct du contenu, lequel est classé, alors que le nombre agrégé est calculé.


## <a name="rendering-of-encrypted-documents"></a>Rendu de documents chiffrés

L'affichage des fichiers SharePoint, Exchange et OneDrive chiffrés n'a pas lieu dans l’explorateur de contenu. Il s’agit d’un problème sensible qui nécessite un équilibre entre le besoin d'afficher le contenu de fichiers dans l’explorateur de contenu et la nécessité de conserver les contenus chiffrés. Avec les autorisations accordées par les groupes de rôle de la **visionneuse de liste de l’explorateur de contenu** et la **visionneuse de contenu de l’explorateur de contenu**, un affichage de la liste des fichiers, des métadonnées de fichier et un lien que vous pouvez utiliser pour accéder au contenu via le client web.

## <a name="supported-characters-in-retention-label-names-in-sharepoint-search"></a>Caractères pris en charge dans les noms d'étiquettes de rétention de la recherche SharePoint

La recherche SharePoint ne prend pas en charge les noms d’étiquettes de rétention qui contiennent `-` ou `_`. Par exemple, `Label-MIP` et `Label_MIP` ne sont pas pris en charge. La recherche SharePoint prend en charge ces caractères dans les noms d’étiquettes de confidentialité et les noms de type information sensible.

## <a name="onedrive-remains-in-preview"></a>OneDrive reste en mode aperçu

Merci pour vos précieux commentaires sur l’intégration de OneDrive pendant notre programme de préversion. À mesure que nous travaillons sur les détails, vous pouvez constater des données/flux incohérents. Nous continuerons à proposer OneDrive en préversion jusqu’à ce que tous les correctifs soient en place. Nous apprécions votre soutien constant.


## <a name="see-also"></a>Voir aussi

- [Prise en main de la classification des données (préversion)](data-classification-overview.md)
- [Afficher l’activité des étiquettes (aperçu)](data-classification-activity-explorer.md)
- [Afficher le contenu étiqueté (aperçu)](data-classification-content-explorer.md)
- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)