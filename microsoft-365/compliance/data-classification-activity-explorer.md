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
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: L’explorateur d’activité complète les fonctionnalités de classification des données en vous permettant de voir et de filtrer les actions que les utilisateurs effectuent sur votre contenu étiqueté.
ms.openlocfilehash: 63ecb84c0ae658b0fd3463dba10d56059352910b
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45126643"
---
# <a name="get-started-with-activity-explorer"></a>Prise en main de l’explorateur d’activité

Les onglets vue d’ensemble de la classification des données et explorateur de contenu vous permettent de voir quel contenu a été découvert et étiqueté, ainsi que son emplacement. L’explorateur d’activité complète cette suite de fonctionnalités en vous permettant de contrôler les opérations effectuées avec votre contenu étiqueté. L’Explorateur d’activité permet de voir votre historique.

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

### <a name="permissions"></a>Autorisations

 Pour accéder à l’onglet d’explorateur d’activité, un compte doit être affecté à une appartenance dans l’un de ces rôles ou groupes de rôles.

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

## <a name="activity-type"></a>Type d’activité

Microsoft 365 contrôle et signale les types d’activités dans SharePoint Online, OneDrive, tels que :

- étiquette appliqué
- étiquette modifiée (mise à niveau, rétrogradée ou supprimée)
- simulation d’étiquetage automatique

L’intérêt de comprendre quelles actions sont accomplies avec votre contenu marqué par des étiquettes de confidentialité est de voir si les moyens de contrôle que vous avez déjà mis en place, comme les [stratégies de prévention de perte des données](data-loss-prevention-policies.md) sont efficaces ou non. Si ce n’est pas le cas ou si vous découvrez quelque chose d’inattendu tel qu’un grand nombre d’éléments qui sont étiquetés `highly confidential`et sont rétrogradés`general` vous pouvez gérer vos différentes stratégies et entreprendre de nouvelles actions pour limiter le comportement indésirable.

> [!NOTE]
> L’explorateur d’activité ne suit pas actuellement les activités de rétention pour Exchange Online.

## <a name="see-also"></a>Voir aussi
- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

