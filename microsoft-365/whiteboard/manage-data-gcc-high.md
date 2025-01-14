---
title: Gérer les données du tableau blanc Microsoft dans les environnements GCC High
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.service: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez comment activer, désactiver et gérer l’accès au Tableau blanc.
ms.openlocfilehash: fd41a4280d6f4b9fd243ee82551496281de9be18
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67596289"
---
# <a name="manage-data-for-microsoft-whiteboard-in-gcc-high-environments"></a>Gérer les données du tableau blanc Microsoft dans les environnements GCC High

>[!NOTE]
> Ces conseils s’appliquent aux environnements US Government Community Cloud (GCC) High.

Les données sont stockées sous forme de fichiers .whiteboard dans OneDrive Entreprise. Un tableau blanc moyen peut avoir une taille comprise entre 50 Ko et 1 Mo et se trouver où se trouve votre contenu OneDrive Entreprise. Pour savoir où les nouvelles données sont créées, consultez [l’emplacement de stockage de vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Examinez l’emplacement de OneDrive Entreprise. Toutes les propriétés qui s’appliquent aux fichiers généraux dans OneDrive Entreprise s’appliquent également au tableau blanc, à l’exception du partage externe.

Pour gérer les données, vous devez d’abord vous assurer que le tableau blanc est activé pour votre organisation. Pour plus d’informations, consultez [Gérer l’accès au Tableau blanc dans les environnements GCC High](manage-whiteboard-access-gcc-high.md).

Vous pouvez gérer les données de tableau blanc à l’aide de contrôles OneDrive Entreprise existants. Pour plus d’informations, consultez le [guide OneDrive pour les entreprises](/onedrive/plan-onedrive-enterprise).

Vous pouvez utiliser des outils OneDrive Entreprise existants pour répondre aux demandes des personnes concernées (DSR) relatives au Règlement général sur la protection des données (RGPD). Les fichiers tableau blanc peuvent être déplacés de la même façon que d’autres contenus dans OneDrive Entreprise. Toutefois, il se peut que les liens et les autorisations de partage ne se déplacent pas.

## <a name="data-controls-supported"></a>Contrôles de données pris en charge

Les contrôles de données suivants sont actuellement pris en charge dans le Tableau blanc :

- Stratégies de rétention
- Quota
- DLP
- eDiscovery
- Conservation légale

## <a name="data-controls-planned"></a>Contrôles de données planifiés

Les contrôles de données suivants sont prévus pour les versions ultérieures du Tableau blanc :

- Étiquettes de confidentialité
- Audit
- Analyse
- Stockage de tableaux blancs dans des sites SharePoint

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc - GCC High](manage-whiteboard-access-gcc-high.md)

[Gérer le partage pour le tableau blanc - GCC High](manage-sharing-gcc-high.md)

[Gérer les clients pour le Tableau blanc - GCC High](manage-clients-gcc-high.md)
