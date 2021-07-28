---
title: Étape 2. Effectuer une évaluation de la préparation à l’intégration SOC à l’aide de l’infrastructure De confiance zéro
description: Les principes de base de l’évaluation de la préparation à l’intégration SOC à l’aide de l’infrastructure de confiance zéro lors de l’intégration Microsoft 365 Defender vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyber-attaque, secops, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 27cbc0ec7286812cebc500952bc68adad3586eb8
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53623844"
---
# <a name="step-2-perform-a-soc-integration-readiness-assessment-using-the-zero-trust-framework"></a>Étape 2. Effectuer une évaluation de la préparation à l’intégration SOC à l’aide de l’infrastructure De confiance zéro

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Une fois que les principales fonctions de l’équipe du Centre des opérations de sécurité (SOC) sont définies, l’étape suivante pour votre organisation consiste à préparer l’adoption de Microsoft Defender par le biais d’une approche de confiance [zéro](/security/zero-trust/). L’adoption peut vous aider à déterminer les conditions requises pour le déploiement d’Microsoft 365 Defender à l’aide de pratiques modernes de pointe du secteur, tout en évaluant les fonctionnalités de Defender par rapport à votre environnement. 

Cette approche repose sur une base solide de protections et inclut des domaines clés tels que l’identité, les points de terminaison (appareils), les données, les applications, l’infrastructure et la mise en réseau. L’équipe d’évaluation de la préparation déterminera les domaines où une exigence fondamentale pour l’activation de Microsoft 365 Defender n’a pas encore été satisfaite et devra être mise à jour. 

Voici quelques-uns des éléments qui devront être corrigés pour que la SOC optimise pleinement les processus dans le SOC :

- **Identité :**     Domaines AD DS (Active Directory Domain Services) locaux hérités, aucun plan mfa, aucun inventaire des comptes privilégiés, etc.
- **Points de terminaison (appareils) :**  Grand nombre de systèmes d’exploitation hérités, inventaire limité des appareils, etc.
- **Données et applications :**    Absence de normes de gouvernance des données, pas d’inventaire des applications personnalisées qui ne s’intègrent pas.
- **Infrastructure :**   Grand nombre de licences SaaS non autorisées, aucune sécurité de conteneur, etc.
- **Mise en réseau :**   Problèmes de performances dus à une bande passante faible, à un réseau plat, à des problèmes de sécurité sans fil, etc.

Les organisations doivent également suivre [l’Microsoft 365 Defender](m365d-enable.md) l’article pour capturer l’ensemble de référence des exigences de configuration. Ces étapes déterminent à leur tour les activités de correction que les équipes SOC devront effectuer pour développer efficacement des cas d’utilisation. 

Les procédures d’adoption et la création de cas d’utilisation sont décrites aux étapes 3 et 4.

## <a name="next-step"></a>Étape suivante

[Étape 3. Planifier l’intégration Microsoft 365 Defender avec votre catalogue de services SOC](integrate-microsoft-365-defender-secops-services.md)
