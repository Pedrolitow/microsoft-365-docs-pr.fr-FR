---
title: Évaluation de Microsoft 365 Defender
description: Configurez votre laboratoire de test Microsoft 365 Defender ou votre environnement pilote pour tester et tester la solution de sécurité conçue pour protéger les périphériques, l’identité, les données et les applications de votre organisation.
keywords: Version d’évaluation de la protection de Microsoft contre les menaces, essayez Microsoft Threat Protection, évaluez Microsoft Threat Protection, l’atelier d’évaluation de Microsoft Threat Protection, Microsoft Threat Protection Pilot, Cyber Security, Advanced persistent, Enterprise Security, appareils, Device, Identity, Users, Data, applications, incidents, analyse automatisée et correction, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.openlocfilehash: fe0a06dd104f0f0532363ee046f4bad1c03c5400
ms.sourcegitcommit: ce46d1bd67091d4ed0e2b776dfed55e2d88cdbf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49130893"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Création d’un laboratoire d’évaluation ou d’un environnement pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

L’objectif de la création de ce laboratoire d’évaluation ou de cet environnement pilote est d’illustrer les fonctionnalités complètes et intégrées de Microsoft 365 Defender. Découvrez comment cette solution de sécurité intelligente détecte, empêche, recherche automatiquement les menaces avancées de votre organisation et y répond. 

Ce guide décrit les étapes à suivre pour démarrer votre évaluation de Microsoft 365 Defender en fonction des chemins de déploiement recommandés. L’objectif est de vous aider à configurer la solution de sécurité dans un environnement de laboratoire avec un compte d’évaluation ou dans un environnement pilote en production avec une licence complète. La préparation de votre laboratoire d’évaluation ou de votre environnement pilote peut vous aider à présenter des cas d’utilisation des opérations de sécurité pour les décideurs de votre organisation. Lorsque vous avez terminé d’exécuter vos simulations d’attaque et que vous êtes satisfait du résultat, vous pouvez le déployer et l’utiliser entièrement dans votre organisation à l’aide des professionnels techniques ou des experts de votre organisation. 

Ce guide vous aidera à :
- Configurer le serveur et les ordinateurs de l’atelier
- Configurer Active Directory avec des utilisateurs et des groupes
- Installer et configurer Microsoft Defender pour l’identité, Microsoft Defender pour Office 365, Microsoft Defender pour le point de terminaison et sécurité des applications Cloud Microsoft
- Configurer des stratégies locales pour votre serveur et vos ordinateurs
- Imiter une attaque de menace pour générer un incident ou une alerte de test dans Microsoft 365 Defender

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez autant que possible les instructions de configuration de l’atelier.


## <a name="deployment-phases"></a>Phases de déploiement

Il existe trois phases pour créer un environnement de laboratoire de test Microsoft 365 Defender et le déployer :

![Phases de déploiement : Prepare, Setup, Onboard](../../media/phase-diagrams/deployment-phases.png)

|Phase | Description | 
|:-------|:-----|
|[Phase 1 : préparer](prepare-mtpeval.md)| Découvrez ce que vous devez prendre en compte lors du déploiement de Microsoft 365 Defender dans un laboratoire d’évaluation ou un environnement pilote : <br><br>-Parties prenantes et déconnexion <br> -Considérations sur l’environnement <br>-Accès <br>-Installation d’Azure Active Directory <br> -Ordre de configuration
|[Phase 2 : configuration](setup-mtpeval.md)|  Suivez les étapes initiales pour accéder au centre de sécurité Microsoft 365 afin de configurer votre laboratoire d’évaluation ou votre environnement pilote Microsoft 365 Defender. Vous serez guidé pour :<br><br>-Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 <br>  -Configurer le domaine<br>-Affecter les licences Microsoft 365 E5<br>-Exécutez l’Assistant Installation dans le portail.|
|[Phase 3 : configurer & Onboard](config-mtpeval.md) | Configurez chaque pilier Microsoft 365 Defender et les points de terminaison intégrés. Vous serez guidé pour :<br><br>-Configurer Microsoft Defender pour Office 365<br>-Configurer la sécurité des applications Cloud Microsoft<br>-Configurer Microsoft Defender pour l’identité<br>-Configurer Microsoft Defender pour le point de terminaison


## <a name="in-scope"></a>Dans l’étendue

Les tâches suivantes sont dans l’étendue de ce guide :
-   Configurer Azure Active Directory
-   Configurer Microsoft 365 Defender
    -   Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 ou utilisez votre licence complète si vous exécutez un projet pilote.
    -   Configurer le domaine
    -   Affecter des licences Microsoft 365 E5
    -   Fin de l’Assistant Installation dans le portail
-   Configurer tous les piliers de Microsoft 365 Defender en fonction des meilleures pratiques
    -   Microsoft Defender pour Office 365
    -   Microsoft Defender pour identité
    -   Microsoft Cloud App Security
    -   Microsoft Defender pour point de terminaison

## <a name="out-of-scope"></a>Non compris

Ce guide de déploiement ne comporte pas les éléments suivants :

-   Configuration de solutions tierces qui peuvent s’intégrer à Microsoft 365 Defender
-   Test de pénétration dans l’environnement de production

## <a name="next-step"></a>Étape suivante
[Phase 1 : préparer](prepare-mtpeval.md) 
<br> Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender
