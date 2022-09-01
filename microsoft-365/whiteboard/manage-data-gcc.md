---
title: Gérer les données du tableau blanc Microsoft dans les environnements GCC
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment activer, désactiver et gérer l’accès au Tableau blanc.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 508557253df5172c3aa89baf7b30c58886ffd73e
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497464"
---
# <a name="manage-data-for-microsoft-whiteboard-in-gcc-environments"></a>Gérer les données du tableau blanc Microsoft dans les environnements GCC

>[!NOTE]
> Ces conseils s’appliquent aux environnements cloud de la communauté du gouvernement des États-Unis (GCC).

Les données sont stockées sous forme de fichiers .whiteboard dans OneDrive Entreprise. Un tableau blanc moyen peut avoir une taille comprise entre 50 Ko et 1 Mo et se trouver où se trouve votre contenu OneDrive Entreprise. Pour savoir où les nouvelles données sont créées, consultez [l’emplacement de stockage de vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Examinez l’emplacement de OneDrive Entreprise. Toutes les propriétés qui s’appliquent aux fichiers généraux dans OneDrive Entreprise s’appliquent également au tableau blanc, à l’exception du partage externe.

Vous pouvez gérer les données de tableau blanc à l’aide de contrôles OneDrive Entreprise existants. Pour plus d’informations, consultez le [guide OneDrive pour les entreprises](/onedrive/plan-onedrive-enterprise).

Vous pouvez utiliser des outils OneDrive Entreprise existants pour répondre aux demandes des personnes concernées (DSR) relatives au Règlement général sur la protection des données (RGPD). Les fichiers tableau blanc peuvent être déplacés de la même façon que d’autres contenus dans OneDrive Entreprise. Toutefois, il se peut que les liens et les autorisations de partage ne se déplacent pas.

Pour gérer les données, vous devez d’abord vous assurer que le tableau blanc est activé pour votre organisation. Pour plus d’informations, consultez [Gérer l’accès au Tableau blanc dans les environnements GCC](manage-whiteboard-access-gcc.md).

## <a name="data-controls-supported"></a>Contrôles de données pris en charge

Les contrôles de données suivants sont actuellement pris en charge dans le Tableau blanc :

- Stratégies de rétention
- Quota
- Conservation légale
- Protection contre la perte de données (DLP)
- EDiscovery de base : les tableaux blancs sont stockés sous forme de fichiers .whiteboard dans le OneDrive Entreprise du créateur. Ils sont indexés pour la recherche de mots clés et de types de fichiers, mais ne sont pas disponibles pour la préversion/révision. Lors de l’exportation, un administrateur doit charger le fichier vers OneDrive Entreprise pour afficher le contenu. D’autres soutiens sont prévus pour l’avenir.

## <a name="data-controls-planned"></a>Contrôles de données planifiés

Les contrôles de données suivants sont prévus pour les versions ultérieures du Tableau blanc :

- Étiquettes de confidentialité
- Analyse
- Plus de prise en charge d’eDiscovery
- Stockage de tableaux blancs dans des sites SharePoint

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc - GCC](manage-whiteboard-access-gcc.md)

[Gérer le partage pour le tableau blanc - GCC](manage-sharing-gcc.md)

[Gérer les clients pour le Tableau blanc - GCC](manage-clients-gcc.md)
