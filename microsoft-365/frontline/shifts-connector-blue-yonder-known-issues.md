---
title: Problèmes connus liés au connecteur Teams Shifts pour Blue Yonder
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Répertorie les problèmes connus lors de l’utilisation du connecteur Team Shifts pour Blue Yonder pour intégrer Shifts à Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 3873a6a3d62d7f09aeba55a2680854d45dac56f5
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68234226"
---
# <a name="known-issues-teams-shifts-connector-for-blue-yonder"></a>Problèmes connus : Connecteur Teams Shifts pour Blue Yonder

Cet article répertorie les problèmes connus du [connecteur Microsoft Teams Shifts pour Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder).

## <a name="you-can-map-an-instance-to-more-than-one-team-using-powershell-or-microsoft-graph"></a>Vous pouvez mapper une instance à plusieurs équipes à l’aide de PowerShell ou de Microsoft Graph

Une instance de Workforce Management blue Yonder ne doit être mappée qu’à une seule équipe à un moment donné dans une connexion.

Toutefois, lorsque vous utilisez PowerShell ou Microsoft Graph pour configurer une connexion, il est possible de mapper une instance à plusieurs équipes. Nous vous recommandons d’éviter de mapper une instance à plusieurs équipes, car cela peut entraîner des problèmes de synchronisation et un comportement inattendu.

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [Utiliser PowerShell pour connecter Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)
- [Utilisez le Centre d'administration Microsoft 365 pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-blue-yonder-admin-center-manage.md)
- [Utilisez PowerShell pour gérer votre connexion Shifts à Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
