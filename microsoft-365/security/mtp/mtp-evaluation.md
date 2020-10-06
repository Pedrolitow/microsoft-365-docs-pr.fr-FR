---
title: Évaluer la Protection Microsoft contre les menaces
description: Configurez votre laboratoire de test Microsoft Threat Protection ou votre environnement pilote pour tester la solution de protection coordonnée contre les menaces conçue pour protéger les périphériques, l’identité, les données et les applications qui peuvent aider votre organisation
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
- m365solution-evalutatemtp
ms.topic: conceptual
ms.openlocfilehash: 3768937fc882fee8d6a744e4fb504095882c7e81
ms.sourcegitcommit: 9d8d071659e662c266b101377e24549963e43fef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "48368058"
---
# <a name="create-a-microsoft-threat-protection-trial-lab-or-pilot-environment"></a>Créer un laboratoire d’évaluation de la protection contre les menaces Microsoft ou un environnement pilote 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

L’objectif de la création de ce laboratoire d’évaluation ou de cet environnement pilote est d’illustrer les fonctionnalités complètes, intégrées et intelligentes de Microsoft Threat Protection dans le cadre de la détection, de la prévention, de l’enquête et de la réponse que vous pouvez utiliser dans votre organisation. 

Ce guide décrit les étapes à suivre pour commencer votre évaluation de la protection contre les menaces Microsoft en fonction des chemins de déploiement recommandés. L’objectif est de vous aider à configurer les services intégrés de protection contre les menaces Microsoft dans un environnement de laboratoire lors de l’utilisation d’un compte d’évaluation ou dans un environnement pilote en production lors de l’utilisation d’une licence complète. Les résultats qui seront utiles pour la présentation des cas d’utilisation des opérations de sécurité pour les décideurs de la solution de sécurité dans votre organisation. Lorsque vous avez terminé d’exécuter vos simulations d’attaque et que vous êtes satisfait du résultat, vous pouvez le déployer entièrement et l’utiliser dans votre organisation avec l’aide des professionnels techniques de Microsoft ou des experts de votre organisation. 

Ce guide vous aidera à :
- Configurer le serveur et les ordinateurs de l’atelier
- Configurer Active Directory avec des utilisateurs et des groupes
- Installer et configurer Azure ATP, Office ATP, Microsoft Defender ATP et Microsoft Cloud App Security
- Configurer des stratégies locales pour votre serveur et vos ordinateurs
- Imiter une attaque de menace pour générer un incident ou une alerte de test dans la protection contre les menaces Microsoft

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez autant que possible les instructions de configuration de l’atelier.


## <a name="deployment-phases"></a>Phases de déploiement

Il existe trois phases pour créer un environnement de laboratoire de test de la protection contre les menaces Microsoft et le déployer :

|Phase | Description | 
|:-------|:-----|
| ![Phase 1 : préparer](../../media/prepare.png)<br>[Phase 1 : préparer](prepare-mtpeval.md)| Découvrez ce que vous devez prendre en compte lors du déploiement de la protection contre les menaces Microsoft dans un laboratoire d’évaluation ou un environnement pilote : <br><br>-Parties prenantes et déconnexion <br> -Considérations sur l’environnement <br>-Accès <br>-Installation d’Azure Active Directory <br> -Ordre de configuration
|  ![Phase 2 : configuration](../../media/setup.png) <br>[Phase 2 : configuration](setup-mtpeval.md)|  Suivez les étapes initiales pour accéder au centre de sécurité Microsoft 365 afin de configurer votre laboratoire d’évaluation ou votre environnement pilote Microsoft Threat Protection. Vous serez guidé pour :<br><br>-Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 <br>  -Configurer le domaine<br>-Affecter les licences Microsoft 365 E5<br>-Exécutez l’Assistant Installation dans le portail.|
|  ![Phase 3 : configurer & Onboard](../../media/config-onboard.png) <br>[Phase 3 : configurer & Onboard](config-mtpeval.md) | Configurez chaque pilier de protection contre les menaces Microsoft et les points de terminaison intégrés. Vous serez guidé pour :<br><br>-Configurer la protection avancée contre les menaces d’Office 365<br>-Configurer la sécurité des applications Cloud Microsoft<br>-Configurer Azure protection avancée contre les menaces<br>-Configurer Microsoft Defender-protection avancée contre les menaces 


## <a name="in-scope"></a>Dans l’étendue

Les tâches suivantes sont dans l’étendue de ce guide :
-   Configurer Azure Active Directory
-   Configuration de la protection contre les menaces Microsoft
    -   Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 ou utilisez votre licence complète si vous exécutez un projet pilote.
    -   Configurer le domaine
    -   Affecter des licences Microsoft 365 E5
    -   Fin de l’Assistant Installation dans le portail
-   Configurer tous les piliers de protection contre les menaces Microsoft en fonction des meilleures pratiques
    -   Office 365 – Protection avancée contre les menaces
    -   Azure Advanced Threat Protection
    -   Microsoft Cloud App Security
    -   Microsoft Defender – Protection avancée contre les menaces

## <a name="out-of-scope"></a>Non compris

Ce guide de déploiement ne comporte pas les éléments suivants :

-   Configuration de solutions tierces qui peuvent s’intégrer à la protection contre les menaces Microsoft
-   Test de pénétration dans l’environnement de production

## <a name="next-step"></a>Étape suivante
![Phase 1 : préparer](../../media/prepare.png) <br>[Phase 1 : préparer](prepare-mtpeval.md) 
<br> Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection
