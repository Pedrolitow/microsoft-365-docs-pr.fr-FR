---
title: Microsoft Defender for Cloud Apps dans Microsoft 365 Defender (préversion)
description: En savoir plus sur les modifications apportées à la Microsoft Defender for Cloud Apps à Microsoft 365 Defender
keywords: Bien démarrer avec Microsoft 365 Defender, Microsoft Defender for Cloud Apps
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 08/04/2022
audience: ITPro
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: a6064137a5a8a7eefc233501707de1de6ae3afe8
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68794034"
---
# <a name="microsoft-defender-for-cloud-apps-in-microsoft-365-defender-preview"></a>Microsoft Defender for Cloud Apps dans Microsoft 365 Defender (préversion)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Cloud Apps](/defender-cloud-apps/)

Microsoft Defender for Cloud Apps fait maintenant partie de Microsoft 365 Defender. Le portail Microsoft 365 Defender permet aux administrateurs de sécurité d’effectuer leurs tâches de sécurité dans un emplacement unique. Cela simplifie les flux de travail et ajoute les fonctionnalités des autres services Microsoft 365 Defender. Microsoft 365 Defender sera la base de la surveillance et de la gestion de la sécurité de vos identités, données, appareils, applications et infrastructure Microsoft.

Les analystes SOC pourront trier, examiner et rechercher toutes les charges de travail Microsoft 365 Defender, y compris les applications cloud.
Les alertes Defender for Cloud Apps continueront d’apparaître dans la file d’attente d’incidents et la file d’attente des alertes de Microsoft 365 Defender, mais désormais avec du contenu pertinent dans les pages d’alerte disponibles dans le portail Microsoft 365 Defender, dans un format unifié avec les adaptations appropriées à chaque type d’alerte.

Jetez un coup d’œil dans Microsoft 365 Defender à <https://security.microsoft.com>.

En savoir plus sur les avantages : [Vue d’ensemble des Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="quick-reference"></a>Informations de référence rapides

Les images et les tableaux ci-dessous répertorient les modifications apportées à la navigation entre Microsoft Defender for Cloud Apps et Microsoft 365 Defender.

### <a name="discover"></a>Découvrir

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender-discover.png" alt-text="Nouveaux emplacements pour les fonctionnalités Cloud Discovery dans le portail Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender-discover.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Tableau de bord Cloud Discover | Applications cloud -> Cloud Discovery |
| Applications découvertes | onglet de la page Cloud Discovery |
| Ressources découvertes | onglet de la page Cloud Discovery |
| Adresses IP | onglet de la page Cloud Discovery |
| Utilisateurs | onglet de la page Cloud Discovery |
| Appareils | onglet de la page Cloud Discovery |
| Catalogue d’applications cloud |  Applications cloud -> Catalogue d’applications cloud |
| Créer un rapport d’instantané Cloud Discovery | Dans la page Cloud Discovery, sous Actions |

### <a name="investigate"></a>Examiner

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender-investigate.png" alt-text="Nouveaux emplacements pour les fonctionnalités d’investigation dans le portail Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender-investigate.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Journal d’activité | Applications cloud -> Journal d’activité |
| Fichiers | Applications cloud -> Files |
| Utilisateurs et comptes | Ressources -> identités |
| Configuration de la sécurité | disponible dans [Microsoft Defender pour le cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) |
| Posture de sécurité des identités | [Évaluations de la sécurité des identités de Microsoft Defender for Identity](/defender-for-identity/isp-overview) |
| Applications OAuth | Applications cloud -> applications OAuth |
| Applications connectées | Paramètres -> Applications cloud -> Applications connectées |

### <a name="control"></a>Contrôle

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender-control.png" alt-text="Nouveaux emplacements pour les fonctionnalités de contrôle dans le portail Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender-control.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Politiques | Applications cloud -> Gestion des stratégies |
| Modèles | Applications cloud - modèles de stratégie > |

### <a name="settings"></a>Paramètres

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender-settings.png" alt-text="Nouveaux emplacements pour Paramètres dans le portail Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender-settings.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Paramètres | Paramètres -> Applications cloud |
| Paramètres/Journal de gouvernance | Applications cloud -> Journal de gouvernance |
| Extensions de sécurité -> Playbooks | Paramètres -> Applications cloud |
| Extensions de sécurité -> agents SIEM | Paramètres -> Applications cloud |
| Extensions de sécurité -> DLP externe | Paramètres -> Applications cloud |
| Extensions de sécurité -> jetons d’API | Paramètres -> Applications cloud |
| Gérer l’accès administrateur -> Administration rôles | Autorisations > rôles > applications cloud |
| Gérer l’accès administrateur -> autorisations de confidentialité de l’activité | Autorisations- > Applications cloud > Autorisations de confidentialité de l’activité |
| Rapports exportés | Rapports -> Applications cloud -> Rapports exportés |
| Déploiement et confidentialité délimités | Paramètres -> Cloud Apps -> Déploiement et confidentialité délimités |
| Applications connectées / Connecteurs d’application | Paramètres -> Cloud Apps -> Applications connectées -> Connecteurs d’application |
| Contrôle d’application d’accès conditionnel | Paramètres -> Applications cloud -> Applications connectées -> applications de contrôle d’application par accès conditionnel |
| Plages d'adresses IP              | Paramètres -> Applications cloud                                      |
| Groupes d’utilisateurs                    | Paramètres -> Applications cloud                                      |

## <a name="limitations"></a>Limites

- La nouvelle expérience Defender for Cloud Apps dans le portail Microsoft 365 Defender est actuellement disponible pour tous les utilisateurs décrits dans [Gérer l’accès administrateur](/defender-cloud-apps/manage-admins), à l’exception des éléments suivants :
  - **Administrateur d’application/d’instance**, **administrateur de groupe** d’utilisateurs, **administrateur général Cloud Discovery** et **administrateur de rapports Cloud Discovery**, comme défini dans [Rôles d’administrateur intégrés dans Defender pour les applications cloud](/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps).
  - Groupes de confidentialité des utilisateurs tels que définis dans [Confidentialité de l’activité](/defender-cloud-apps/activity-privacy)

- La nouvelle expérience est actuellement disponible pour les licences Microsoft Defender for Cloud Apps complètes uniquement.
- Les nouveaux clients doivent d’abord se connecter au portail Microsoft Defender for Cloud Apps.
- Certains liens peuvent vous rediriger vers le portail Defender for Cloud Apps.

## <a name="whats-changed"></a>Fonctionnalités modifiées

Découvrez les modifications apportées à l’intégration de Defender for Cloud Apps et de Microsoft 365 Defender.

### <a name="global-search"></a>Recherche globale

La recherche globale dans Microsoft 365 Defender (à l’aide de la barre de recherche en haut de la page) inclut désormais une entité pouvant faire l’objet d’une recherche supplémentaire : elle vous permet de rechercher des applications connectées dans Defender for Cloud Apps.

:::image type="content" source="../../media/global-search-apps.png" alt-text="Recherchez les applications connectées.":::

### <a name="assets-and-identities"></a>Ressources et identités

Dans le cadre de la création d’une section **Ressources** dédiée qui couvre l’ensemble de l’expérience Microsoft 365 Defender, la section **Utilisateurs et comptes** de Defender for Cloud Apps est renommée section **Identités**. Aucune modification des fonctionnalités n’est attendue.

## <a name="related-videos"></a>Vidéos connexes

- [Protection des applications cloud dans Microsoft 365 Defender](https://www.microsoft.com/videoplayer/embed/RE59yVU)

## <a name="related-information"></a>Informations connexes

- [Microsoft 365 Defender](microsoft-365-defender.md)
