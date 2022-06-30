---
title: Gérer les données pour le Tableau blanc Microsoft
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Découvrez la conservation des données pour le Tableau blanc Microsoft dans Azure et OneDrive Entreprise.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 2537750a43b10617251ee1da670f6ebd78e5ce82
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2022
ms.locfileid: "66553860"
---
# <a name="manage-data-for-microsoft-whiteboard"></a>Gérer les données pour le Tableau blanc Microsoft

Le contenu du tableau blanc est stocké dans Azure et dans OneDrive Entreprise. Les nouveaux tableaux blancs seront stockés dans OneDrive Entreprise ; la seule exception est que les tableaux blancs démarrés à partir d’un Surface Hub seront stockés dans Azure (qui seront déplacés vers OneDrive Entreprise à l’avenir). Pour plus d’informations, consultez [Gérer le partage dans le Tableau blanc](manage-sharing-organizations.md).

## <a name="azure-storage-overview"></a>Vue d’ensemble du stockage Azure

Le tableau blanc stocke actuellement le contenu en toute sécurité dans Azure. Les données peuvent être stockées à différents emplacements, en fonction du pays et du moment où le Tableau blanc est passé au stockage de nouveau contenu dans ces emplacements. Pour savoir où les nouvelles données sont créées, consultez [l’emplacement de stockage de vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). 

Le contenu dans Azure ne prend pas en charge la protection contre la perte de données (DLP), la découverte électronique, les stratégies de rétention et les fonctionnalités similaires. Le contenu peut être géré à l’aide [d’applets de commande PowerShell de tableau blanc](/powershell/module/whiteboard/) et, au fil du temps, ce contenu doit être migré vers OneDrive Entreprise ou supprimé.

### <a name="if-a-user-account-is-deleted-in-azure"></a>Si un compte d’utilisateur est supprimé dans Azure

Nous modifions la façon dont les tableaux blancs sont stockés lorsque le compte d’un utilisateur est supprimé dans Azure. Avant la modification, lorsque le compte d’un utilisateur a été supprimé, les tableaux blancs appartenant à l’utilisateur ont également été supprimés, mais les tableaux blancs qui ont été partagés avec d’autres utilisateurs n’ont pas été supprimés.

>[!NOTE]
> Les tableaux blancs stockés dans OneDrive Entreprise sont gérés comme tout autre contenu dans OneDrive Entreprise. Pour plus d’informations, consultez [Définir la rétention OneDrive pour les utilisateurs supprimés](/onedrive/set-retention).

Depuis **le 1er juin 2022**, le comportement des tableaux blancs sur Azure a changé. Tous les tableaux blancs partagés avec d’autres utilisateurs seront supprimés.

Si vous souhaitez conserver les tableaux blancs d’un utilisateur supprimé, *avant* de supprimer le compte, vous pouvez transférer la propriété. Vous pouvez transférer un tableau blanc unique ou l’ensemble d’entre eux à un autre utilisateur. 

- Suivez ces instructions pour [transférer tous les tableaux blancs](/powershell/module/whiteboard/invoke-transferallwhiteboards).

- Pour plus d’informations sur la suppression de comptes d’utilisateur, consultez [Supprimer un utilisateur de votre organisation](/microsoft-365/admin/add-users/delete-a-user).

Assurez-vous que tout processus de suppression ou script gère cette modification. Si les tableaux blancs sont supprimés, aucune action n’est nécessaire. 

## <a name="onedrive-for-business-storage-overview"></a>vue d’ensemble du stockage OneDrive Entreprise

Les tableaux blancs seront créés dans le dossier OneDrive Entreprise de la personne qui démarre le tableau blanc (SharePoint n’est pas encore pris en charge). Ce processus s’applique à tous les tableaux blancs créés dans les applications de tableau blanc autonomes, ainsi qu’aux réunions, conversations et canaux Microsoft Teams. La seule exception est que les tableaux blancs démarrés à partir d’un Surface Hub seront stockés dans Azure (qui seront déplacés vers OneDrive Entreprise à l’avenir).

Les utilisateurs qui n’ont pas OneDrive Entreprise approvisionnés ne pourront plus créer de tableaux blancs lorsque cette modification sera implémentée. Toutefois, ils peuvent toujours modifier leurs tableaux créés précédemment. Ils peuvent également collaborer sur tous les tableaux blancs partagés avec eux par d’autres personnes qui ont OneDrive Entreprise.

Un tableau blanc moyen peut avoir une taille comprise entre 50 Ko et 1 Mo et se trouver où se trouve votre contenu OneDrive Entreprise. Pour savoir où sont stockées les données de votre locataire, consultez [l’emplacement où sont stockées vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Examinez ensuite l’emplacement de OneDrive Entreprise.

### <a name="controls-for-onedrive-for-business-storage"></a>Contrôles pour le stockage OneDrive Entreprise 

Vous pouvez gérer les données de tableau blanc à l’aide de contrôles OneDrive Entreprise existants. Pour plus d’informations, consultez le [guide OneDrive pour les entreprises](/onedrive/plan-onedrive-enterprise).

Vous pouvez utiliser des outils OneDrive Entreprise existants pour répondre aux demandes des personnes concernées (DSR) relatives au Règlement général sur la protection des données (RGPD). Si vous souhaitez vous assurer que toutes les modifications précédentes sont supprimées du fichier, vous devez supprimer l’intégralité du fichier.

Les fichiers tableau blanc peuvent être déplacés de la même façon que d’autres contenus dans OneDrive Entreprise. Toutefois, il se peut que les liens et les autorisations de partage ne se déplacent pas.

Contrôles de données pris en charge aujourd’hui :

- Stratégies de rétention
- Quota
- Conservation légale
- DLP
- EDiscovery de base : les fichiers .whiteboard sont stockés sous forme de fichiers dans le OneDrive Entreprise du créateur. Ils sont indexés pour la recherche de mots clés et de types de fichiers, mais ne sont pas disponibles pour la préversion ou la révision. Lors de l’exportation, un administrateur doit charger le fichier vers OneDrive Entreprise pour afficher le contenu. Un soutien supplémentaire est prévu pour l’avenir.

Contrôles de données prévus pour les versions ultérieures :

- Étiquettes de confidentialité
- Analyse
- Prise en charge d’eDiscovery supplémentaire

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc](manage-whiteboard-access-organizations.md)

[Gérer le partage pour le tableau blanc](manage-sharing-organizations.md)

[Déployer le tableau blanc sur Windows](deploy-on-windows-organizations.md)


