---
title: Prise en main de l’Explorateur d’activités
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
description: L’Explorateur d’activités vous permet de voir et de filtrer les actions que les utilisateurs effectuent sur votre contenu étiqueté.
ms.openlocfilehash: c33ff2653eef6813caf9b9281903b7248af12359
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917999"
---
# <a name="get-started-with-activity-explorer"></a>Prise en main de l’explorateur d’activités

La [vue d’ensemble de la classification des données](data-classification-overview.md) et les onglets [de l’Explorateur de contenu](data-classification-content-explorer.md) vous donnent une visibilité sur le contenu qui a été découvert et étiqueté, ainsi que l’emplacement de ce contenu. L’explorateur d’activité complète cette suite de fonctionnalités en vous permettant de contrôler les opérations effectuées avec votre contenu étiqueté. L’Explorateur d’activités fournit une vue historique des activités sur votre contenu étiqueté. Les informations d’activité sont collectées à partir des journaux d’audit unifiés Microsoft 365, transformées et mises à disposition dans l’interface utilisateur de l’Explorateur d’activités. L’Explorateur d’activités fournit des rapports sur jusqu’à 30 jours de données.

![Capture d’écran de la capture d’écran de l’explorateur d’activités de l’espace réservé.](../media/data-classification-activity-explorer-1.png)

Plus de 30 filtres différents sont à votre disposition. Parmi ceux-ci, figurent :

- Plage de dates
- Type d’activité
- Emplacement
- Utilisateur
- Étiquette de confidentialité
- Étiquette de rétention
- File path
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

Un compte doit se voir attribuer explicitement l’appartenance à l’un de ces groupes de rôles ou lui accorder explicitement le rôle.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en préversion

Il existe des rôles et des groupes de rôles en préversion que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles applicables qui sont en préversion. Pour en savoir plus sur ces rôles, consultez [Rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrateur Information Protection
- Analyste Information Protection
- Enquêteur Information Protection
- Lecteur Information Protection

Voici une liste des groupes de rôles applicables en préversion. Pour en savoir plus, consultez [Groupes de rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Protection des informations
- Administrateurs Information Protection
- Analystes Information Protection
- Enquêteurs Information Protection
- Lecteurs Information Protection

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

**Rôles Microsoft 365**

- Administrateur de conformité
- Administrateur de sécurité
- Lecteur de sécurité

## <a name="activity-types"></a>Types d’activités

L’Explorateur d’activités collecte des informations d’activité à partir des journaux d’audit sur plusieurs sources d’activités. Pour plus d’informations sur l’activité d’étiquetage dans l’Explorateur d’activités, consultez [Événements d’étiquetage disponibles dans l’Explorateur d’activités](data-classification-activity-explorer-available-events.md).

Activités **d’étiquette de confidentialité** et **activités d’étiquetage de rétention à partir d’applications natives** Office, client et scanneur d’étiquetage unifié Azure Information Protection (AIP), SharePoint Online, Exchange Online (étiquettes de confidentialité uniquement) et OneDrive. En voici quelques exemples :

- Étiquette appliqué
- Étiquette modifiée (mise à niveau, rétrogradée ou supprimé)
- Simulation d’étiquetage automatique
- Fichier lu

**Scanneur Azure Information Protection (AIP) et clients AIP**

- Protection appliquée
- Protection modifiée
- Protection supprimée
- Fichiers découverts

L’Explorateur d’activités collecte également les **événements de correspondance de stratégie DLP** à partir de Exchange Online, SharePoint Online, OneDrive, Teams Chat and Channel (préversion), des bibliothèques et des dossiers SharePoint locaux, ainsi que des partages de fichiers locaux et Windows 10 appareils via **la protection contre la perte de données de point de terminaison (DLP).** Voici quelques exemples d’événements de Windows 10 appareils :

- Suppressions
- Créations
- Copié dans le Presse-papiers
- Modified
- Lecture
- Imprimé
- Renommé
- Copié dans un partage réseau
- Accès par l’application non autorisée 

Comprendre les actions effectuées avec votre contenu étiqueté sensible vous permet de voir si les contrôles que vous avez en place, tels que [les stratégies Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md) sont efficaces ou non. Si ce n’est pas le cas ou si vous découvrez quelque chose d’inattendu tel qu’un grand nombre d’éléments qui sont étiquetés `highly confidential`et sont rétrogradés`general` vous pouvez gérer vos différentes stratégies et entreprendre de nouvelles actions pour limiter le comportement indésirable.

> [!NOTE]
> L’explorateur d’activité ne suit pas actuellement les activités de rétention pour Exchange Online.

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [En savoir plus sur les types d’informations confidentielles](sensitive-information-type-learn-about.md).
- [En savoir plus sur la classification des données](data-classification-overview.md)
