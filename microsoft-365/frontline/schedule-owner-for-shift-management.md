---
title: Gérer les propriétaires de planification pour la gestion de shift
author: lanachin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
- Microsoft Cloud for Retail
description: Découvrez comment gérer les propriétaires de shifts pour la gestion des planifications. Vous pouvez définir une stratégie pour élever l’autorisation d’un membre de l’équipe à un propriétaire de planification.
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
- highpri
- microsoftcloud-healthcare
- microsoftcloud-retail
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 2a9174b1cb9e9090b7010798041c539608ace616
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68077445"
---
# <a name="schedule-owner-for-shift-management"></a>Planifier le propriétaire pour la gestion des shifts

## <a name="overview"></a>Vue d’ensemble

La fonctionnalité Planifier le propriétaire vous permet d’élever les autorisations d’un membre de l’équipe afin qu’il puisse gérer les planifications sans faire de l’employé un propriétaire d’équipe. Avec les autorisations Planifier le propriétaire, un employé peut gérer le planning de son équipe sans pouvoir modifier d’autres propriétés d’équipe telles que la mise à jour, la modification ou la suppression de canaux d’équipe.

Que peut faire un utilisateur disposant d’autorisations de propriétaire de planification ?

- Créez, modifiez et publiez des planifications pour gérer les affectations de shift de l’équipe’.
- Affichez et approuvez les demandes de shift, y compris les demandes d’échange de shifts et de shifts ouverts.
- Gérez les paramètres dans Shifts pour activer certaines fonctionnalités pour l’équipe.
- Affichez et modifiez la feuille de temps de l’équipe pour traiter les paies des employés.

## <a name="why-schedule-owner"></a>Pourquoi planifier le propriétaire ?

Sans la fonctionnalité Planifier le propriétaire, les fonctions métier quotidiennes peuvent être interrompues. Bien que le propriétaire de l’équipe aide à gérer l’équipe, il peut ne pas nécessairement être la personne responsable de la planification quotidienne. Dans ce cas, le transfert de la responsabilité de gestion de planification uniquement à un autre membre de l’équipe simplifie les opérations quotidiennes au sein de l’équipe et élimine la confusion de deux membres de l’équipe disposant des mêmes privilèges d’accès.

## <a name="scenario"></a>Scénario

Voici un exemple de la façon dont votre organisation peut utiliser la fonctionnalité Planifier le propriétaire.

Vous travaillez dans une grande organisation où les responsables de service envoient des rapports directement au responsable du magasin. Le responsable de magasin dispose de plus d’autorité au sein de votre entreprise et est le propriétaire de l’équipe dans Shifts. En revanche, les responsables de service ne sont ajoutés qu’à Shifts en tant que membres de l’équipe. Bien que les responsables de magasins aient plus d’ancienneté que les responsables de service, il est plus judicieux pour les responsables de service de gérer la planification quotidienne des employés de leur équipe’.

*Sans Propriétaire de planification*, les responsables de service doivent disposer exactement des mêmes privilèges que le propriétaire de l’équipe. Récemment, les responsables de service ont déplacé des informations et modifié le nom des canaux, ce qui a entraîné des complications avec le travail du responsable du magasin. Le responsable du magasin souhaite que les responsables de service puissent organiser leurs plannings, mais ne souhaite pas qu’ils puissent changer quoi que ce soit d’autre au sein de l’équipe, en dehors de Shifts.

*Avec le propriétaire* de la planification, les responsables de service peuvent recevoir des privilèges de planification, sans aucun autre privilège de propriétaire d’équipe.

## <a name="manage-schedule-ownership"></a>Gérer la propriété de la planification

En tant qu’administrateur, vous utilisez des stratégies pour contrôler la propriété de gestion de planification dans votre organisation. Vous gérez ces stratégies à l’aide des applets de commande PowerShell suivantes :

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy?view=teams-ps)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy?view=teams-ps)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy?view=teams-ps)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy?view=teams-ps)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy?view=teams-ps)

### <a name="example-1"></a>Exemple 1

Ici, nous créons une stratégie nommée ScheduleOwnerPolicy avec la fonctionnalité Schedule Owner activée.

```powershell
New-CsTeamsShiftsPolicy –Identity ScheduleOwnerPolicy  -EnableScheduleOwnerPermissions $true -AccessType UnrestrictedAccess_TeamsApp
```

### <a name="example-2"></a>Exemple 2

Dans cet exemple, nous assignons une stratégie nommée ScheduleOwnerPolicy à un utilisateur nommé remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName ScheduleOwnerPolicy
```

## <a name="related-articles"></a>Articles connexes

- [Gérer l’application Shifts pour votre organisation dans Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [Gérer l'accès par shift dans Teams pour les travailleurs de première ligne](manage-shift-based-access-flw.md)
