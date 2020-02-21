---
title: Utilisateurs de la gestion des risques internes
description: En savoir plus sur les utilisateurs de la gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 322cd0aa8b72ea2c81792b36614e87d97db87d7c
ms.sourcegitcommit: 87cc278ea2ddcd536ecfaa3dfae9a5ddaa502cf9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "42179105"
---
# <a name="insider-risk-management-users"></a>Utilisateurs de la gestion des risques internes

Les utilisateurs de la gestion des risques internes sont des employés de votre organisation qui sont inclus dans une ou plusieurs stratégies de gestion des risques Insiders. Utilisez le **tableau de bord utilisateurs** pour examiner rapidement les informations relatives aux risques des employés et pour ajouter un employé à une stratégie de gestion des risques inSided existante. Chaque utilisateur inclus dans une stratégie de gestion des risques inSided dispose des informations suivantes affichées dans le **tableau de bord utilisateurs**:

- **Users**: nom d’utilisateur d’un utilisateur.
- **Niveau de risque**: niveau de risque calculé actuel de l’utilisateur. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur.
- **Alertes actives**: nombre d’alertes actives pour toutes les stratégies.
- **Violations confirmées**: nombre de cas résolus comme *violation de stratégie confirmée* pour l’utilisateur.
- **Cas**: dossier actif actuel de l’utilisateur.

![Tableau de bord des utilisateurs de gestion des risques Insiders](../media/insider-risk-users-dashboard.png)

## <a name="view-user-details"></a>Afficher les détails de l’utilisateur

Pour afficher plus de détails sur l’activité des risques pour un utilisateur, ouvrez le volet Détails de l’utilisateur en double-cliquant sur un utilisateur dans le **tableau de bord utilisateurs**. Dans le volet d’informations, vous pouvez afficher les informations suivantes :

- Onglet **profil utilisateur**
    - **Nom et titre**: le nom et le titre de la position de l’utilisateur.
    - Adresse de messagerie de l' **utilisateur**: adresse de messagerie de l’utilisateur.
    - **Alias**: alias réseau de l’utilisateur.
    - **Organisation ou service**: organisation ou service de l’utilisateur.

- Onglet **activité utilisateur**
    - **Historique des activités des utilisateurs récents**: répertorie les événements de déclenchement de la stratégie et les indicateurs de risque pour les activités de l’utilisateur. Un événement déclencheur peut être l’acceptation d’une date de départ ou la dernière date de travail prévue pour l’employé. Les indicateurs de risque sont des activités qui sont considérées comme ayant un élément de risque et qui sont mises en correspondance avec des stratégies auxquelles l’utilisateur est inclus. Les événements et les activités de risque sont répertoriés avec l’élément le plus récent répertorié en premier.

## <a name="add-a-user-to-a-policy"></a>Ajouter un utilisateur à une stratégie

Pour ajouter un utilisateur à une stratégie de gestion des risques Insiders, utilisez l’Assistant Nouvelle stratégie ou l’onglet **utilisateurs** de la solution de **gestion des risques inSided** dans le centre de conformité Microsoft 365.

Procédez comme suit pour ajouter un utilisateur à une stratégie d’Insider existante :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **utilisateurs** .
2. Sélectionnez **Ajouter un utilisateur à une stratégie** dans la barre d’outils.
3. Dans la boîte de dialogue **Ajouter un nouvel utilisateur** , commencez à taper un nom d’utilisateur dans le champ **utilisateur** . Sélectionnez l’utilisateur que vous souhaitez ajouter à une stratégie.
4. Sélectionnez la flèche déroulante pour le champ de **stratégie** afin d’afficher les stratégies de gestion des risques d’Insider configurées. Sélectionnez la stratégie à laquelle ajouter l’utilisateur.
5. Utilisez le contrôle Slider de la **fenêtre d’activation** pour définir la durée pendant laquelle la stratégie est active pour cet utilisateur et elle est déclenchée lorsque l’utilisateur effectue la première activité correspondant à la stratégie. La plage de la fenêtre de surveillance est comprise entre 5 et 30 jours.
6. Sélectionnez **Ajouter** , puis **confirmez** l’ajout de l’utilisateur à la stratégie.
