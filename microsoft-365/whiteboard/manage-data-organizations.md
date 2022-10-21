---
title: Gérer les données pour le Tableau blanc Microsoft
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
description: Découvrez la conservation des données pour Le Tableau blanc Microsoft dans Azure et OneDrive Entreprise.
ms.openlocfilehash: 136506afcec7fe067a270e0577678b5b6a9ec9ff
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662838"
---
# <a name="manage-data-for-microsoft-whiteboard"></a>Gérer les données pour le Tableau blanc Microsoft

Le contenu du tableau blanc est stocké dans OneDrive Entreprise et Azure. OneDrive Entreprise est le stockage par défaut pour tous les nouveaux tableaux blancs. Les tableaux blancs créés à l’origine dans Azure et les tableaux blancs qui ont été initiés sur un Surface Hub ou un appareil Salles Microsoft Teams sont stockés dans Azure.

Pour gérer les données, vous devez d’abord vous assurer que le Tableau blanc est activé pour votre organisation. Pour plus d’informations, consultez [Gérer l’accès au tableau blanc](manage-whiteboard-access-organizations.md).

## <a name="azure-storage-overview"></a>Vue d’ensemble du stockage Azure

>[!NOTE]
> Les informations suivantes s’appliquent aux tableaux blancs stockés dans Azure.

Le tableau blanc stocke actuellement le contenu en toute sécurité dans Azure. Les données peuvent être stockées dans différents emplacements, selon le pays et le moment où le Tableau blanc a basculé vers le stockage du nouveau contenu dans ces emplacements. Pour vérifier où les nouvelles données sont [créées, consultez Où vos données client Microsoft 365 sont stockées](/microsoft-365/enterprise/o365-data-locations).

Le contenu dans Azure ne prend pas en charge la protection contre la perte de données (DLP), l’eDiscovery, les stratégies de rétention et les fonctionnalités similaires. Ce contenu peut être géré à l’aide [d’applets de commande Whiteboard PowerShell](/powershell/module/whiteboard/). À terme, les tableaux blancs stockés dans Azure devront être migrés vers OneDrive Entreprise ou supprimés.

### <a name="if-a-user-account-is-deleted-in-azure"></a>Si un compte d’utilisateur est supprimé dans Azure

Nous modifions la façon dont les tableaux blancs sont stockés lorsque le compte d’un utilisateur est supprimé dans Azure. Avant la modification, tous les tableaux blancs appartenant au compte d’un utilisateur supprimé ont également été supprimés. Toutefois, les tableaux blancs partagés avec d’autres personnes n’ont pas été supprimés.

>[!NOTE]
> Les tableaux blancs stockés dans OneDrive Entreprise seront gérés comme tout autre contenu dans OneDrive Entreprise. Pour plus d’informations, consultez [Définir la rétention OneDrive pour les utilisateurs supprimés](/onedrive/set-retention).

Depuis le **1er juin 2022**, le comportement des tableaux blancs sur Azure a changé. Tous les tableaux blancs partagés avec d’autres utilisateurs seront supprimés.

Si vous souhaitez conserver les tableaux blancs d’un utilisateur supprimé, *vous* pouvez transférer la propriété avant de supprimer le compte. Vous pouvez transférer un tableau blanc unique ou tous ces éléments à un autre utilisateur.

- Suivez ces instructions pour [transférer tous les tableaux blancs](/powershell/module/whiteboard/invoke-transferallwhiteboards).

- Pour plus d’informations sur la suppression de comptes d’utilisateur, consultez [Supprimer un utilisateur de votre organisation](/microsoft-365/admin/add-users/delete-a-user).

Vérifiez que tout processus de suppression ou script gère cette modification. Si les tableaux blancs sont supprimés, aucune action n’est nécessaire.

## <a name="onedrive-for-business-storage-overview"></a>Vue d’ensemble du stockage OneDrive Entreprise

Les tableaux blancs sont créés dans le dossier OneDrive Entreprise de la personne qui démarre le tableau blanc. SharePoint n’est pas encore pris en charge. Ce processus s’applique à tous les tableaux blancs créés dans les applications tableau blanc autonomes et dans les réunions, conversations et canaux Microsoft Teams. La seule exception est que les tableaux blancs démarrés à partir d’un Surface Hub seront stockés dans Azure, bien qu’ils soient déplacés vers OneDrive Entreprise à l’avenir.

Les utilisateurs qui n’ont pas OneDrive Entreprise approvisionnés ne pourront plus créer de tableaux blancs lorsque cette modification sera implémentée. Toutefois, ils peuvent toujours modifier leurs tableaux créés précédemment. Ils peuvent également collaborer sur tous les tableaux blancs partagés avec eux par d’autres personnes qui ont OneDrive Entreprise.

Un tableau blanc moyen peut avoir une taille comprise entre 50 Ko et 1 Mo et se trouver où se trouve votre contenu OneDrive Entreprise. Pour vérifier où sont stockées les données de votre locataire, consultez [Où sont stockées vos données client Microsoft 365](/microsoft-365/enterprise/o365-data-locations). Examinez ensuite l’emplacement pour OneDrive Entreprise.

### <a name="controls-for-onedrive-for-business-storage"></a>Contrôles pour le stockage OneDrive Entreprise

Vous pouvez gérer les données du tableau blanc à l’aide de contrôles OneDrive Entreprise existants. Pour plus d’informations, consultez [guide OneDrive pour les entreprises](/onedrive/plan-onedrive-enterprise).

Vous pouvez utiliser des outils de OneDrive Entreprise existants pour répondre aux demandes des personnes concernées (DSR) dans le cadre du Règlement général sur la protection des données (RGPD). Si vous souhaitez vous assurer que toutes les modifications précédentes sont supprimées du fichier, vous devez supprimer le fichier entier.

Les fichiers de tableau blanc peuvent être déplacés de la même façon que d’autres contenus dans OneDrive Entreprise. Toutefois, les liens de partage et les autorisations peuvent ne pas être déplacés.

Contrôles de données pris en charge aujourd’hui :

- Stratégies de rétention
- Quota
- Conservation légale
- DLP
- eDiscovery de base : les fichiers .whiteboard sont stockés sous forme de fichiers dans le OneDrive Entreprise du créateur. Ils sont indexés pour la recherche de mot clé et de type de fichier, mais ne sont pas disponibles pour l’aperçu ou la révision. Lors de l’exportation, un administrateur doit charger le fichier dans OneDrive Entreprise pour afficher le contenu. D’autres soutiens sont prévus pour l’avenir.

Contrôles de données prévus pour les versions ultérieures :

- Étiquettes de confidentialité
- Analyse
- Plus de prise en charge d’eDiscovery

## <a name="see-also"></a>Voir aussi

[Gérer l’accès au Tableau blanc](manage-whiteboard-access-organizations.md)

[Gérer le partage pour le tableau blanc](manage-sharing-organizations.md)

[Déployer le Tableau blanc sur Windows](deploy-on-windows-organizations.md)
