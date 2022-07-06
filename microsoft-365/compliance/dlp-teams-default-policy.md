---
title: En savoir plus sur la stratégie DLP par défaut dans Microsoft Teams (préversion)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: En savoir plus sur la stratégie de protection contre la perte de données par défaut dans Microsoft Teams
ms.openlocfilehash: 5c3a5a116da90a41abcc459808e83176dc750fe1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624220"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préviersion)

[Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md) fonctionnalités ont été étendues pour inclure les messages de conversation et de canal Microsoft Teams, y compris les messages de canal privé. Dans le cadre de cette version, nous avons créé une stratégie DLP par défaut pour Microsoft Teams pour les premiers clients du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>.

## <a name="licensing"></a>Licences

Pour obtenir des informations complètes sur les licences DLP dans Microsoft Teams, consultez [Information Protection : Protection contre la perte de données pour Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Que fait la stratégie par défaut ?

La stratégie DLP par défaut pour Teams effectue le suivi de tous les numéros de carte de crédit partagés en interne et en externe à l’organisation. Cette stratégie est activée par défaut pour tous les utilisateurs du locataire. Il ne génère pas de conseils de stratégie pour les utilisateurs finaux, mais génère un événement d’alerte et déclenche également un e-mail de gravité faible à l’administrateur (ajouté dans la stratégie). L’administrateur peut afficher les activités et modifier les détails des stratégies en se connectant au Centre de conformité.

Les administrateurs peuvent afficher cette stratégie dans la [page portail de conformité Microsoft Purview](https://compliance.microsoft.com/compliancesettings) > stratégies de protection contre la perte de données.


> [!div class="mx-imgBorder"]
> ![stratégie DLP Teams par défaut.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Modifier ou supprimer la stratégie par défaut

Pour [modifier la stratégie par défaut pour de meilleures performances ou la supprimer](create-test-tune-dlp-policy.md#tune-a-dlp-policy), utilisez simplement un compte avec des autorisations **de gestion de la conformité DLP** . Pour plus d’informations, consultez [Autorisations](create-test-tune-dlp-policy.md#permissions).

