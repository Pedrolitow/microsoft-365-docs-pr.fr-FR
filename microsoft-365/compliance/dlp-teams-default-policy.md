---
title: En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préviersion)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Découvrez la stratégie de protection contre la perte de données par défaut dans Microsoft Teams
ms.openlocfilehash: 8f021031bd1dc3672a7aa7123ce01d4c6536fe77
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58567735"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préviersion)

[Les fonctionnalités de protection](dlp-learn-about-dlp.md) contre la perte de données ont été étendues pour inclure Microsoft Teams messages de conversation et de canal, y compris les messages de canal privé. Dans le cadre de cette version, nous avons créé une stratégie DLP par défaut pour Microsoft Teams clients pour la première fois dans le Centre de conformité.

## <a name="applies-to"></a>S’applique à

Tout client titulaire d’une licence avec une ou plusieurs des licences ci-dessous et ayant des utilisateurs Teams actifs
 
- ME5, 
- MA5, 
- Conformité E5/A5, 
- IP+G, 
- OE5, 
- Conformité avancée O365 
- EMS E5


## <a name="what-does-the-default-policy-do"></a>Que fait la stratégie par défaut ?

La stratégie DLP par défaut pour Teams tous les numéros de carte de crédit partagés en interne et en externe dans l’organisation. Cette stratégie est en cours d’utilisation par défaut pour tous les utilisateurs du client. Il ne génère aucun conseil de stratégie pour les utilisateurs finaux, mais génère un événement d’alerte et déclenche également un e-mail de faible gravité à l’administrateur (ajouté dans la stratégie). L’administrateur peut afficher les activités et modifier les détails des stratégies en se connectant au Centre de conformité.

Les administrateurs peuvent afficher [](https://compliance.microsoft.com/compliancesettings) cette stratégie dans le Centre de conformité et > stratégies de protection contre la perte de données.


> [!div class="mx-imgBorder"]
> ![par Teams stratégie DLP.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Modifier ou supprimer la stratégie par défaut

Pour [modifier la stratégie par défaut afin d’améliorer les performances](create-test-tune-dlp-policy.md#tune-a-dlp-policy)ou pour la supprimer, utilisez simplement un compte avec les autorisations de gestion de la conformité **DLP.** Pour plus d’informations, voir [Autorisations.](create-test-tune-dlp-policy.md#permissions)

