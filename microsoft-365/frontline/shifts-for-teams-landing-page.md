---
title: Shifts pour les travailleurs de première ligne
description: Obtenez les conseils d’administration dont vous avez besoin pour configurer et gérer Shifts, l’outil de gestion de planification, dans Microsoft Teams.
ms.topic: conceptual
author: LanaChin
ms.author: v-lanachin
audience: admin
manager: samanro
f1.keywords:
- NOCSH
ms.service: microsoft-365-frontline
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
- microsoftcloud-healthcare
- microsoftcloud-retail
- m365solution-frontline
- m365solution-scenario
- highpri
search.appverid: MET150
ms.localizationpriority: high
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-jun2020
ms.openlocfilehash: 8d79469cafd26cc979523ec632d6ca21cce3bf3d
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68226732"
---
# <a name="shifts-for-frontline-workers"></a>Shifts pour les travailleurs de première ligne

Shifts, l’outil de gestion des planifications dans Teams, maintient votre personnel de première ligne connecté et synchronisé. Il est conçu d’abord pour la gestion des planifications et les communications rapides et efficaces. Avec Shifts, les gestionnaires et les travailleurs de première ligne peuvent gérer de manière transparente les planifications et garder le contact.

Les responsables peuvent créer, mettre à jour et gérer les horaires de travail de leurs équipes. Ils peuvent affecter des équipes, ajouter des équipes ouvertes et approuver les demandes d'horaires des employés. Les employés peuvent consulter leur propre emploi du temps et celui de leur équipe, définir leur disponibilité, demander un changement de poste ou proposer une affectation, demander des congés et pointer.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE42FjP]

Utilisez les ressources suivantes pour vous aider à configurer et gérer Shifts dans votre organisation.

## <a name="set-up-and-manage-shifts"></a>Configurer et gérer Shifts

|&nbsp;  |&nbsp; |
|---------|---------|
|:::image type="icon" source="/office/media/icons/administrator.png":::|**[Gérer les décalages](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Obtenez une vue d’ensemble de la gestion des shifts pour votre organisation. Découvrez comment contrôler l’accès à Shifts, épingler les majs à la barre d’applications Teams pour faciliter l’accès, activer les balises basées sur les décalages, etc. |
|:::image type="icon" source="/office/media/icons/users-people.png":::|**[Gérer les propriétaires de planning pour la gestion des équipes](schedule-owner-for-shift-management.md)** Cette fonctionnalité vous permet de faire passer les autorisations d'un membre de l'équipe à un propriétaire de planning sans faire de l'employé un propriétaire d'équipe.|
|:::image type="icon" source="/office/media/icons/help.png":::| **[Faq sur les données Shifts](/microsoftteams/expand-teams-across-your-org/shifts/shifts-data-faq?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Découvrez où sont stockées les données Shifts et d’autres rubriques relatives aux données Shifts, notamment la rétention, la récupération et le chiffrement.|

## <a name="shifts-connectors"></a>Connecteurs de Plannings

Si vous utilisez un système tiers de gestion de la main-d’œuvre (WFM) pour la planification, vous pouvez l’intégrer directement à Shifts via des connecteurs Shifts gérés. Une fois que vous avez configuré une connexion, vos employés de première ligne peuvent afficher et gérer en toute transparence leurs planifications dans votre système WFM à partir de Shifts.

|&nbsp;  |&nbsp;  |
|---------|---------|
|:::image type="icon" source="/office/media/icons/connector-teams.png":::| **[Aperçu](shifts-connectors.md)** Obtenez une vue d’ensemble des connecteurs Shifts et de leur fonctionnement. Découvrez les connecteurs gérés disponibles et les systèmes WFM pris en charge.   |
|:::image type="icon" source="/office/media/icons/connector-teams.png":::| **[Connecteur Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder)** <ul><li>Découvrez comment configurer une connexion à Blue Yonder Workforce Management à l’aide de [l’Assistant Connecteur Shifts](shifts-connector-wizard.md) ou [de PowerShell](shifts-connector-blue-yonder-powershell-setup.md).</li><li>Découvrez comment gérer votre connexion à Blue Yonder Workforce Management à l’aide du [Centre d'administration Microsoft 365](shifts-connector-blue-yonder-admin-center-manage.md) ou [de PowerShell](shifts-connector-powershell-manage.md).</li></ul> |
|:::image type="icon" source="/office/media/icons/connector-teams.png":::| **[Connecteur Teams Shifts pour les dimensions UKG](shifts-connectors.md#microsoft-teams-shifts-connector-for-ukg-dimensions)** (préversion) <ul><li>Découvrez comment configurer une connexion à UKG Dimensions à l’aide de [l’Assistant Connecteur Shifts](shifts-connector-wizard-ukg.md) ou [de PowerShell](shifts-connector-ukg-powershell-setup.md).</li><li>Découvrez comment gérer votre connexion aux dimensions UKG à l’aide de la [Centre d'administration Microsoft 365](shifts-connector-ukg-admin-center-manage.md) ou [de PowerShell](shifts-connector-ukg-powershell-manage.md).</li></ul>|
|:::image type="icon" source="/office/media/icons/connector-teams.png":::| **[Connecteur Reflexis Shifts pour Microsoft Teams](shifts-connectors.md#reflexis-shifts-connector-for-microsoft-teams)** Découvrez comment intégrer Shifts au système reflexis WFM via le connecteur.|

## <a name="shifts-extensions"></a>Décale les extensions

|&nbsp;|&nbsp;|
| ------------- | ------------- |
|:::image type="icon" source="/office/media/icons/api.png":::| **[API Shift Graph](/graph/api/resources/shift)** Les API Shifts Graph vous permettent d’intégrer des données Shifts à des systèmes WFM externes. Vous aurez la possibilité de créer des expériences Shifts personnalisées dans le back end, tout en offrant aux utilisateurs une expérience frontale riche dans Teams.             |
|:::image type="icon" source="/office/media/icons/process-flow-teams.png":::| **[Shifts + Power Automate](https://github.com/OfficeDev/Microsoft-Teams-Shifts-Power-Automate-Templates)** Shifts + Power Automate vous permet de tirer des informations de Shifts et de créer des workflows personnalisés avec d’autres applications et d’effectuer des opérations à grande échelle. Automatiser les processus clés avec peu ou pas de code. Les déclencheurs et les modèles prennent en charge différents scénarios, tels que l’activation d’approbations automatiques pour les demandes de l’équipe lorsque l’approbation d’un responsable n’est pas nécessaire. |

## <a name="featured-training"></a>Formation proposée

|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|&nbsp;|
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
|:::image type="icon" source="/office/media/icons/get-started-teams.png":::  |  [Vidéo : Qu’est-ce que Shifts ?](https://support.office.com/article/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821) |:::image type="icon" source="/office/media/icons/calendar.png"::: |  [Vidéo : Créer une planification Shifts](https://support.microsoft.com/office/create-a-shifts-schedule-2b94ca38-36db-4a1c-8fee-f8f0fec9a984) |:::image type="icon" source="/office/media/icons/blocks-teams.png":::|  [Vidéo : Gérer une planification dans Shifts](https://support.microsoft.com/office/manage-and-view-a-shifts-schedule-63acda7b-ea39-441a-b1c6-c404a72e79f7) |
