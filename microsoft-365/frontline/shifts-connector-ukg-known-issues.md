---
title: Problèmes connus liés au connecteur Team Shifts pour les dimensions UKG
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Répertorie les problèmes connus lors de l’utilisation du connecteur Team Shifts pour les dimensions UKG pour intégrer Shifts à UKG Dimensions.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 10c1f0aff03fb302cc12cae78cf003d2f337a01a
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68234186"
---
# <a name="known-issues-team-shifts-connector-for-ukg-dimensions"></a>Problèmes connus : Connecteur Team Shifts pour les dimensions UKG

[!INCLUDE [preview-feature](includes/preview-feature.md)]

Cet article répertorie les problèmes connus du [connecteur Microsoft Teams Shifts pour les dimensions UKG](shifts-connectors.md#microsoft-teams-shifts-connector-for-ukg-dimensions).

## <a name="you-can-map-an-instance-to-more-than-one-team-using-powershell-or-microsoft-graph"></a>Vous pouvez mapper une instance à plusieurs équipes à l’aide de PowerShell ou de Microsoft Graph

Une instance UKG Dimensions ne doit être mappée qu’à une seule équipe à un moment donné dans une connexion.

Toutefois, lorsque vous utilisez PowerShell ou Microsoft Graph pour configurer une connexion, il est possible de mapper une instance à plusieurs équipes. Nous vous recommandons d’éviter de mapper une instance à plusieurs équipes, car cela peut entraîner des problèmes de synchronisation et un comportement inattendu.

## <a name="frontline-managers-can-select-a-time-zone-for-a-schedule-in-shifts-thats-different-from-the-time-zone-thats-set-in-ukg-dimensions"></a>Les responsables de première ligne peuvent sélectionner un fuseau horaire pour une planification dans Shifts différente du fuseau horaire défini dans les dimensions UKG

Le paramètre de fuseau horaire des planifications dans Shifts est synchronisé à partir des dimensions UKG. Toutefois, il est possible pour les responsables de première ligne de modifier le fuseau horaire d’une planification dans Shifts en un fuseau horaire différent de celui configuré dans UKG Dimensions. Cela peut entraîner des problèmes de synchronisation et un comportement inattendu.

Pour contourner ce problème, conservez le paramètre de fuseau horaire tel qu’il est.

## <a name="nothing-happens-when-users-select-the-start-a-break-and-end-break-buttons-in-shifts-to-start-or-end-a-break"></a>Rien ne se produit lorsque les utilisateurs sélectionnent les boutons « Démarrer un arrêt » et « Arrêter le saut » dans Shifts pour démarrer ou mettre fin à une interruption

La fonctionnalité d’arrêt de début et de fin de la fonctionnalité d’horloge temporelle n’est pas prise en charge dans une intégration à UKG Dimensions. Les utilisateurs ne seront pas en mesure d’expirer ou de faire une pause, même si les boutons sont affichés dans Shifts.

## <a name="a-user-cant-perform-some-actions-in-shifts-in-the-teams-web-app-after-signing-in-with-a-different-account"></a>Un utilisateur ne peut pas effectuer certaines actions dans Shifts dans l’application web Teams après s’être connecté avec un autre compte

Ce problème peut se produire si un utilisateur disposant de plusieurs comptes dans Teams effectue des actions dans Shifts qui nécessitent l’authentification unique (SSO) dans UKG Dimensions et que cet utilisateur change de compte dans l’application web Teams dans le même navigateur.

Par exemple, un utilisateur se connecte à Teams, approuve une demande de congé, puis se déconnecte. L’utilisateur se connecte ensuite à Teams à l’aide d’un autre compte et tente d’effectuer une autre action dans Shifts qui nécessite l’authentification unique dans UKG Dimensions.

Dans ce scénario, un problème de mise en cache se produit dans lequel l’utilisateur est connecté à Teams et Shifts sur un compte et connecté à UKG Dimensions sur l’autre compte.

Pour contourner ce problème, effectuez l’une des opérations suivantes :

- Effacez les cookies et les données de site pour le site mykronos.com dans le navigateur. Pour plus d’informations, consultez [Supprimer les cookies dans Microsoft Edge](https://support.microsoft.com/microsoft-edge/delete-cookies-in-microsoft-edge-63947406-40ac-c3b8-57b9-2a946a29ae09) ou [Effacer, activer et gérer les cookies dans Chrome](https://support.google.com/chrome/answer/95647).
- Utilisez l’application web Teams dans une fenêtre InPrivate dans Microsoft Edge ou en mode Incognito dans Google Chrome.

## <a name="related-articles"></a>Articles connexes

- [Connecteurs de Plannings](shifts-connectors.md)
- [Utiliser l’Assistant Connecteur Shifts pour connecter Shifts aux dimensions UKG](shifts-connector-wizard-ukg.md)
- [Utiliser PowerShell pour connecter shifts aux dimensions UKG](shifts-connector-ukg-powershell-setup.md)
- [Utilisez la Centre d'administration Microsoft 365 pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-admin-center-manage.md)
- [Utiliser PowerShell pour gérer votre connexion Shifts aux dimensions UKG](shifts-connector-ukg-powershell-manage.md)
- [Gérer l’application Shifts](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
