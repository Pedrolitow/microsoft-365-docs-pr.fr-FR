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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: L’Explorateur d’activités vous permet de voir et de filtrer les actions que les utilisateurs prennent sur votre contenu étiqueté.
ms.openlocfilehash: 73e0d135112d109370aa4f3cdc75d30a8ab087a3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61874039"
---
# <a name="get-started-with-activity-explorer"></a>Prise en main de l’explorateur d’activités

La [vue d’ensemble](data-classification-overview.md) de la classification des données et les onglets de l’Explorateur de contenu vous donnent une visibilité sur le contenu qui a été découvert et étiqueté, ainsi que sur l’endroit où il se trouve. [](data-classification-content-explorer.md) L’explorateur d’activité complète cette suite de fonctionnalités en vous permettant de contrôler les opérations effectuées avec votre contenu étiqueté. L’Explorateur d’activités fournit un affichage historique des activités sur votre contenu étiqueté. Les informations d’activité sont collectées à partir Microsoft 365 journaux d’audit unifiés, transformées et disponibles dans l’interface utilisateur de l’Explorateur d’activités. L’Explorateur d’activités signale jusqu’à 30 jours de données.

![capture d’écran de l’explorateur d’activités d’espace réservé.](../media/data-classification-activity-explorer-1.png)

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

Chaque compte qui accède et utilise la classification de données doit posséder une licence pour l’un des abonnements suivants :

- Microsoft 365 (E5)
- Office 365 (E5)
- Complément Conformité avancée (E5)
- Complément Threat Intelligence avancé (E5)
- Microsoft 365 E5/A5, Protection des informations et gouvernance
- Conformité Microsoft 365 E5/A5

### <a name="permissions"></a>Autorisations

Un compte doit être explicitement affecté à l’un de ces groupes de rôles ou avoir été explicitement attribué au rôle.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en prévisualisation

Il existe des rôles et des groupes de rôles en prévisualisation que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles Protection des données Microsoft (MIP) en prévisualisation. Pour en savoir plus à ce sujet, voir [Rôles](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) dans le Centre de sécurité & conformité

- Administrateur de la protection des informations
- Analyste de la protection des informations
- Enquêteur de la protection des informations
- Lecteur de protection des informations

Voici une liste des groupes de rôles MIP en prévisualisation. Pour en savoir plus sur les groupes de rôles, voir Groupes de [rôles dans le Centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Protection des informations
- Administrateurs de la protection des informations
- Analystes de la protection des informations
- Enquêteurs de la protection des informations
- Lecteurs de protection des informations

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

**Microsoft 365 rôles**

- Administrateur de conformité
- Administrateur de sécurité
- Lecteur de sécurité

## <a name="activity-types"></a>Types d’activité

L’Explorateur d’activités collecte des informations d’activité à partir des journaux d’audit sur plusieurs sources d’activités. Pour plus d’informations sur l’activité d’étiquetage dans l’Explorateur d’activités, voir événements [d’étiquetage disponibles dans l’Explorateur d’activités.](data-classification-activity-explorer-available-events.md)

 Activités des étiquettes  de niveau de sensibilité et activités d’étiquetage de rétention à partir d’applications natives Office, du add-in Azure Information Protection, de SharePoint Online, de Exchange Online (étiquettes de sensibilité uniquement) et de OneDrive. En voici quelques exemples :

- étiquette appliqué
- étiquette modifiée (mise à niveau, rétrogradée ou supprimée)
- simulation d’étiquetage automatique
- lecture de fichier 

**Scanneur Azure Information Protection (AIP) et clients AIP**

- protection appliquée
- protection modifiée
- protection supprimée
- fichiers découverts 

L’Explorateur d’activités rassemble également la stratégie DLP qui correspond aux **événements** de Exchange Online, SharePoint Online, OneDrive, Teams Chat et Canal (prévisualisation), des dossiers et bibliothèques SharePoint locaux, ainsi que des partages de fichiers locaux et des appareils Windows 10 via **Protection contre la perte de données (DLP)** de point de terminaison. Voici quelques exemples d’événements Windows 10'appareils mobiles sont des fichiers :

- suppressions
- creations
- copié dans le Presse-papiers
- modifié
- read
- imprimé
- renommé
- copié sur le partage réseau
- accès par une application non autorisé 

Comprendre les actions entreprises avec votre contenu étiqueté sensible vous permet de voir [](dlp-learn-about-dlp.md) si les contrôles en place, tels que les stratégies de protection contre la perte de données, sont efficaces ou non. Si ce n’est pas le cas ou si vous découvrez quelque chose d’inattendu tel qu’un grand nombre d’éléments qui sont étiquetés `highly confidential`et sont rétrogradés`general` vous pouvez gérer vos différentes stratégies et entreprendre de nouvelles actions pour limiter le comportement indésirable.

> [!NOTE]
> L’explorateur d’activité ne suit pas actuellement les activités de rétention pour Exchange Online.

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [En savoir plus sur la classification des données](data-classification-overview.md)
