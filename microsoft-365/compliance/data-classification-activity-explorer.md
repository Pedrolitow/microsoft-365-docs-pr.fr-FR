---
title: Prise en main de l’explorateur d’activité
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: L’explorateur d’activité complète les fonctionnalités de classification des données en vous permettant de voir et de filtrer les actions que les utilisateurs effectuent sur votre contenu étiqueté.
ms.openlocfilehash: 414ef4e5d9f6472180a5eaef391d3eba33463b02
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114006"
---
# <a name="get-started-with-activity-explorer"></a>Prise en main de l’explorateur d’activité

La [vue d’ensemble](data-classification-overview.md) de la classification des données et les onglets de l’Explorateur de contenu vous donnent une visibilité sur le contenu qui a été découvert et étiqueté, ainsi que sur l’endroit où il se trouve. [](data-classification-content-explorer.md) L’explorateur d’activité complète cette suite de fonctionnalités en vous permettant de contrôler les opérations effectuées avec votre contenu étiqueté. L’Explorateur d’activités fournit un affichage historique des activités sur votre contenu étiqueté. Les informations d’activité sont collectées à partir Microsoft 365 journaux d’audit unifiés, transformées et disponibles dans l’interface utilisateur de l’Explorateur d’activités. 

![emplacement réservé pour la capture d’écran aperçu de l’explorateur d’activité](../media/data-classification-activity-explorer-1.png)

Plus de 30 filtres différents sont à votre disposition. Parmi ceux-ci, figurent :

- plage de dates
- type d’activité
- emplacement
- utilisateur
- étiquette de confidentialité
- étiquette de rétention
- chemin d’accès du fichier
- Stratégie DLP



## <a name="prerequisites"></a>Conditions préalables

Chaque compte qui accède et utilise la classification de données doit posséder une licence pour l’un des abonnements suivants :

- Microsoft 365 (E5)
- Office 365 (E5)
- Complément Conformité avancée (E5)
- Complément Threat Intelligence avancé (E5)
- Microsoft 365 E5/A5, Protection des informations et gouvernance
- Conformité Microsoft 365 E5/A5

### <a name="permissions"></a>Autorisations

 Pour accéder à l’onglet Explorateur d’activités, un compte doit être explicitement affecté à l’un de ces groupes de rôles ou avoir reçu explicitement le rôle.

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur des données de conformité

**Microsoft 365 rôles**

- Administrateur de conformité
- Administrateur de sécurité

## <a name="activity-types"></a>Types d’activité

L’Explorateur d’activités collecte des informations d’activité à partir des journaux d’audit sur plusieurs sources d’activités. Pour plus d’informations sur l’activité d’étiquetage dans l’Explorateur d’activités, voir événements [d’étiquetage disponibles dans l’Explorateur d’activités.](data-classification-activity-explorer-available-events.md)

 Activités des étiquettes  de niveau de sensibilité et activités d’étiquetage de rétention à partir d’applications natives Office, d’un add-in Azure Information Protection, de SharePoint Online, d’Exchange Online (étiquettes de sensibilité uniquement) et de OneDrive. En voici quelques exemples :

- étiquette appliqué
- étiquette modifiée (mise à niveau, rétrogradée ou supprimée)
- simulation d’étiquetage automatique
- lecture de fichier 

**Scanneur Azure Information Protection (AIP) et clients AIP**

- protection appliquée
- protection modifiée
- protection supprimée
- fichiers découverts 

L’Explorateur d’activités rassemble également la stratégie **DLP** qui correspond aux événements provenant de Exchange Online, SharePoint Online, OneDrive, Teams Chat et Canal (prévisualisation), des dossiers et bibliothèques SharePoint locaux, des partages de fichiers locaux et des appareils Windows 10 via la protection contre la perte de données **(DLP)** de point de terminaison. Voici quelques exemples d’événements Windows 10 appareils mobiles :

- suppressions
- creations
- copié dans le Presse-papiers
- modifié
- read
- imprimé
- renommé
- copié sur le partage réseau
- accès par une application non autorisé 

L’intérêt de comprendre quelles actions sont prises avec votre contenu étiqueté sensible est que vous [](dlp-learn-about-dlp.md) pouvez voir si les contrôles que vous avez déjà mis en place, tels que la protection contre la perte de données, sont efficaces ou non. Si ce n’est pas le cas ou si vous découvrez quelque chose d’inattendu tel qu’un grand nombre d’éléments qui sont étiquetés `highly confidential`et sont rétrogradés`general` vous pouvez gérer vos différentes stratégies et entreprendre de nouvelles actions pour limiter le comportement indésirable.

> [!NOTE]
> L’explorateur d’activité ne suit pas actuellement les activités de rétention pour Exchange Online.

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [En savoir plus sur la classification des données](data-classification-overview.md)
