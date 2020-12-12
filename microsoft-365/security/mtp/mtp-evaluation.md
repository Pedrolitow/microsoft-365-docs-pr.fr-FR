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
ms.openlocfilehash: 8504b036203e1f73dc9e0a0d79a228425fb88bfa
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659632"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Création d’un laboratoire d’évaluation ou d’un environnement pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


Ce guide vous aide à configurer un environnement de laboratoire avec des utilisateurs et des groupes, puis vous guide tout au long de la configuration des fonctionnalités dans Microsoft 365 Defender afin que vous puissiez imiter une attaque de menace et obtenir un résultat d’évaluation significatif. 

L’objectif de la création de ce laboratoire d’évaluation ou de cet environnement pilote est d’illustrer les fonctionnalités complètes et intégrées de Microsoft 365 Defender. Découvrez comment cette solution de sécurité intelligente détecte, empêche, recherche automatiquement les menaces avancées de votre organisation et y répond. 


Vous serez guidé lors de la procédure de démarrage de votre évaluation de Microsoft 365 Defender en fonction des chemins de déploiement recommandés. L’objectif est de vous aider à configurer la solution de sécurité dans un environnement de laboratoire avec un compte d’évaluation ou dans un environnement pilote en production avec une licence complète. La préparation de votre laboratoire d’évaluation ou de votre environnement pilote peut vous aider à présenter des cas d’utilisation des opérations de sécurité pour les décideurs de votre organisation. Lorsque vous avez terminé d’exécuter vos simulations d’attaque et que vous êtes satisfait du résultat, vous pouvez le déployer et l’utiliser entièrement dans votre organisation à l’aide des professionnels techniques ou des experts de votre organisation. 

Ce guide vous aidera à :
- Configurer le serveur et les ordinateurs de l’atelier
- Configurer Active Directory avec des utilisateurs et des groupes
- Installer et configurer Microsoft Defender pour l’identité, Microsoft Defender pour Office 365, Microsoft Defender pour le point de terminaison et sécurité des applications Cloud Microsoft
- Configurer des stratégies locales pour votre serveur et vos ordinateurs
- Imiter une attaque de menace pour générer un incident ou une alerte de test dans Microsoft 365 Defender

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez autant que possible les instructions de configuration de l’atelier.


## <a name="deployment-phases"></a>Phases de déploiement

Il existe trois phases pour créer un environnement de laboratoire de test Microsoft 365 Defender.

![Phases de déploiement : Prepare, Setup, Onboard](../../media/evaluation-guide-phases.png)

|Phase | Description | 
|:-------|:-----|
|[Phase 1 : préparer](prepare-mtpeval.md)| Découvrez ce que vous devez prendre en compte lors du déploiement de Microsoft 365 Defender dans un laboratoire d’évaluation ou un environnement pilote : <br><br>-Parties prenantes et déconnexion <br> -Considérations sur l’environnement <br>-Accès <br>-Installation d’Azure Active Directory <br> -Ordre de configuration
|[Phase 2 : configuration](setup-mtpeval.md)|  Suivez les étapes initiales pour accéder au centre de sécurité Microsoft 365 afin de configurer votre laboratoire d’évaluation ou votre environnement pilote Microsoft 365 Defender. Vous serez guidé pour :<br><br>-Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 <br>  -Configurer le domaine<br>-Affecter les licences Microsoft 365 E5<br>-Exécutez l’Assistant Installation dans le portail.|
|[Phase 3 : configurer & Onboard](config-mtpeval.md) | Configurez chaque pilier Microsoft 365 Defender et les points de terminaison intégrés. Vous serez guidé pour :<br><br>-Configurer Microsoft Defender pour Office 365<br>-Configurer la sécurité des applications Cloud Microsoft<br>-Configurer Microsoft Defender pour l’identité<br>-Configurer Microsoft Defender pour le point de terminaison


Une fois que vous avez terminé ce guide, vous auriez identifié les parties prenantes impliquées et les approbations requises, disposez des autorisations d’accès appropriées, inscrites pour les domaines configurés et chacun des piliers de Microsoft 365 Defender, et vos points de terminaison seront intégrés au service.

## <a name="key-capabilities"></a>Fonctionnalités clés

Bien que Microsoft 365 Defender offre de nombreuses fonctionnalités, l’objectif principal de ce guide de déploiement est de vous aider à commencer par les appareils d’intégration. En plus de l’intégration, ces instructions vous permettent de commencer à utiliser les fonctionnalités suivantes.


Fonctionnalité | Description 
:---|:---
Microsoft Defender pour Office 365 | Permet de protéger l’ensemble de votre environnement Office 365 des menaces actuelles
Microsoft Defender pour l’identité | Identifie et détecte les menaces liées aux identités compromises et aux actions malveillantes.
Microsoft Cloud App Security | Offre une visibilité enrichie, un contrôle des déplacements de données et la détection des cyber dans les services Cloud.
Microsoft Defender pour point de terminaison | Empêche, détecte et offre des fonctionnalités de réponse aux menaces avancées avec une sécurité de point de terminaison complète.


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
    -   Microsoft Defender pour l’identité
    -   Microsoft Cloud App Security
    -   Microsoft Defender pour point de terminaison

## <a name="out-of-scope"></a>Non compris

Ce guide de déploiement ne comporte pas les éléments suivants :

-   Configuration de solutions tierces qui peuvent s’intégrer à Microsoft 365 Defender
-   Test de pénétration dans l’environnement de production

## <a name="next-step"></a>Étape suivante
[Phase 1 : préparer](prepare-mtpeval.md) 
<br> Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender
