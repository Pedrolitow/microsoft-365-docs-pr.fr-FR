---
title: Microsoft Defender for Cloud Apps dans Microsoft 365 Defender (préversion)
description: En savoir plus sur les modifications apportées à la Microsoft Defender for Cloud Apps à Microsoft 365 Defender
keywords: Bien démarrer avec Microsoft 365 Defender, Microsoft Defender for Cloud Apps
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dacurwin
author: dcurwin
manager: dansimp
ms.date: 08/21/2022
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 13d178f77efa19ed53c93afa454ddaf6e481a8a6
ms.sourcegitcommit: 7374c7b013890744d74e5214f7f8d69ca7874466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67408416"
---
# <a name="microsoft-defender-for-cloud-apps-in-microsoft-365-defender-preview"></a>Microsoft Defender for Cloud Apps dans Microsoft 365 Defender (préversion)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Cloud Apps](/defender-cloud-apps/)

Microsoft Defender for Cloud Apps fait désormais partie de Microsoft 365 Defender. Le portail Microsoft 365 Defender permet aux administrateurs de sécurité d’effectuer leurs tâches de sécurité à un emplacement unique. Cela simplifie les flux de travail et ajoute les fonctionnalités des autres services Microsoft 365 Defender. Microsoft 365 Defender sera le point d’accueil de la surveillance et de la gestion de la sécurité sur vos identités, données, appareils, applications et infrastructure Microsoft.

Les analystes SOC pourront trier, examiner et rechercher toutes les charges de travail Microsoft 365 Defender, y compris les applications cloud.
Les alertes Defender pour Cloud Apps continueront d’apparaître dans la file d’attente d’incidents et la file d’attente d’alertes de Microsoft 365 Defender, mais maintenant avec le contenu approprié dans les pages d’alerte disponibles dans le portail Microsoft 365 Defender, dans un format unifié avec les adaptations appropriées à chaque type d’alerte.

Jetez un coup d’œil dans Microsoft 365 Defender à <https://security.microsoft.com>.

En savoir plus sur les avantages : [Vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="quick-reference"></a>Référence rapide

L’image et le tableau ci-dessous répertorient les modifications apportées à la navigation entre Microsoft Defender for Cloud Apps et Microsoft 365 Defender.

> [!NOTE]
> Certaines pages n’ont pas encore été migrées et doivent être accessibles à partir du portail Defender pour Cloud Apps.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/defender-cloud-apps-m365-defender.png" alt-text="Nouveaux emplacements dans le portail Microsoft 365 Defender" lightbox="../../media/defender-cloud-apps-m365-defender.png":::

| Defender for Cloud Apps | Microsoft 365 Defender |
|---------|---------|
| Tableau de bord Cloud Discover | Applications cloud -> cloud discovery |
| Applications découvertes | onglet sur la page Cloud Discovery |
| Ressources découvertes | onglet sur la page Cloud Discovery |
| Adresses IP | onglet sur la page Cloud Discovery |
| Utilisateurs | onglet sur la page Cloud Discovery |
| Appareils | onglet sur la page Cloud Discovery |
| Catalogue d’applications cloud |  Applications cloud -> catalogue d’applications cloud |
| Créer un rapport d’instantané Cloud Discovery | Dans la page Cloud Discovery, sous Actions |
| Journal d’activité | Applications cloud -> journal d’activité |
| Fichiers | reste dans le portail Defender pour Cloud Apps |
| Utilisateurs et comptes | Ressources -> identités |
| Configuration de la sécurité | reste dans le portail Defender pour Cloud Apps |
| Posture de sécurité des identités | [Évaluations de la sécurité des identités de Microsoft Defender for Identity](/defender-for-identity/isp-overview) |
| Applications OAuth | Applications cloud -> applications OAuth |
| Applications connectées | reste dans le portail Defender pour Cloud Apps |

> [!NOTE]
> La nouvelle expérience Defender pour Cloud Apps dans le portail Microsoft 365 Defender est actuellement disponible pour tous les utilisateurs détaillés dans [Gérer l’accès administrateur](/defender-cloud-apps/manage-admins), à l’exception des éléments suivants :
>
> - **Administrateur d’applications/instances**, **administrateur de groupe d’utilisateurs**, **administrateur général cloud discovery** et **administrateur de rapports Cloud Discovery**, tels que définis dans les [rôles d’administrateur intégrés dans Defender pour Cloud Apps](/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps).
> - Groupes de confidentialité des utilisateurs tels que définis dans la [confidentialité de l’activité](/defender-cloud-apps/activity-privacy)

## <a name="whats-changed"></a>Fonctionnalités modifiées

Découvrez les modifications apportées à l’intégration de Defender pour Cloud Apps et Microsoft 365 Defender.

### <a name="global-search"></a>Recherche globale

La recherche globale dans Microsoft 365 Defender (à l’aide de la barre de recherche en haut de la page) inclut désormais une entité pouvant faire l’objet d’une recherche supplémentaire : elle vous permet de rechercher des applications connectées dans Defender pour Cloud Apps.

:::image type="content" source="../../media/global-search-apps.png" alt-text="Recherchez des applications connectées.":::

### <a name="assets-and-identities"></a>Ressources et identités

Dans le cadre de la création d’une section **Ressources** dédiées couvrant l’ensemble de l’expérience Microsoft 365 Defender, la section **Utilisateurs et comptes** de Defender pour Cloud Apps est renommée en tant que section **Identités**. Aucune modification des fonctionnalités n’est attendue.

## <a name="related-information"></a>Informations connexes

- [Microsoft 365 Defender](microsoft-365-defender.md)
