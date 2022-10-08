---
title: Étape 2. Effectuer une évaluation de la préparation de l’intégration SOC à l’aide de Confiance nulle Framework
description: Principes de base de l’exécution d’une évaluation de la préparation de l’intégration SOC à l’aide de Confiance nulle Framework lors de l’intégration de Microsoft 365 Defender dans vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque, étendues, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-m365dsecops
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: c4c01f98f38097e45b53cec763419dbdd1209ec8
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051583"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>Étape 2. Effectuer une évaluation de la préparation de l’intégration SOC à l’aide de Confiance nulle Framework

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Une fois que les principales fonctions de l’équipe du Centre des opérations de sécurité (SOC) sont définies, l’étape suivante pour votre organisation consiste à préparer l’adoption de Microsoft 365 Defender par le biais d’une [approche Confiance nulle](/security/zero-trust/). L’adoption peut vous aider à déterminer les exigences nécessaires au déploiement de Microsoft 365 Defender à l’aide de pratiques modernes de pointe, tout en évaluant les fonctionnalités de Microsoft 365 Defender par rapport à votre environnement.

Cette approche repose sur une base solide de protections et inclut des domaines clés tels que l’identité, les points de terminaison (appareils), les données, les applications, l’infrastructure et la mise en réseau. L’équipe Readiness Assessment déterminera les domaines où une exigence fondamentale pour l’activation de Microsoft 365 Defender n’a pas encore été satisfaite et nécessitera une correction.

Voici quelques-uns des éléments qui devront être corrigés pour que le SOC optimise entièrement les processus dans le SOC :

- **Identité:** Domaines Active Directory local Domain Services (AD DS) hérités, aucun plan MFA, aucun inventaire des comptes privilégiés, etc.
- **Points de terminaison (appareils) :** Grand nombre de systèmes d’exploitation hérités, inventaire limité des appareils, etc.
- **Données et applications :**  Absence de normes de gouvernance des données, aucun inventaire des applications personnalisées qui ne seront pas intégrées.
- **Infrastructure:** Grand nombre de licences SaaS non approuvées, aucune sécurité de conteneur, etc.
- **Réseautage:** Problèmes de performances dus à une bande passante faible, à un réseau plat, à des problèmes de sécurité sans fil, etc.

Les organisations doivent également suivre l’article [d’activation Microsoft 365 Defender](m365d-enable.md) pour capturer l’ensemble de référence des exigences de configuration. Ces étapes détermineront à leur tour les activités de correction que les équipes soc devront effectuer pour développer efficacement les cas d’usage. 

Les procédures d’adoption et la création de cas d’usage sont décrites dans les étapes 3 et 4.

## <a name="next-step"></a>Étape suivante

[Étape 3. Planifier l’intégration Microsoft 365 Defender à votre catalogue de services SOC](integrate-microsoft-365-defender-secops-services.md)
