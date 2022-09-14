---
title: Vue d’ensemble du déploiement Microsoft Defender pour point de terminaison
description: Découvrez comment déployer Microsoft Defender pour point de terminaison en préparant, en configurant et en intégrant des points de terminaison à ce service
keywords: déployer, préparer, configurer, intégrer, phase, déploiement, déploiement, adoption, configuration
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-overview
- highpri
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: b5e664fb40d549d669d1b3bba6d55feb96ccc843
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67679150"
---
# <a name="microsoft-defender-for-endpoint-deployment-overview"></a>Vue d’ensemble du déploiement Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Découvrez comment déployer Microsoft Defender pour point de terminaison afin que votre entreprise puisse tirer parti de la protection préventive, de la détection post-violation, de l’investigation automatisée et de la réponse.

Ce guide vous aide à travailler entre les parties prenantes pour préparer votre environnement, puis intégrer des appareils de manière méthodique, passant de l’évaluation à un pilote significatif, au déploiement complet.

Chaque section correspond à un article distinct de cette solution.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="Phases de déploiement avec les détails de la table" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="Récapitulatif des phases de déploiement : préparer, configurer, intégrer" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|Phase|Description|
|---|---|
|[Phase 1 : préparation](prepare-deployment.md)|Découvrez ce que vous devez prendre en compte lors du déploiement de Defender pour point de terminaison, comme les approbations des parties prenantes, les considérations relatives à l’environnement, les autorisations d’accès et l’ordre d’adoption des fonctionnalités.|
|[Phase 2 : configuration](production-deployment.md)|Obtenez des conseils sur les étapes initiales à suivre pour accéder au portail, comme la validation des licences, l’exécution de l’Assistant Configuration et la configuration réseau.|
|[Phase 3 : intégration](onboarding.md)|Découvrez comment utiliser les anneaux de déploiement, les outils d’intégration pris en charge en fonction du type de point de terminaison et la configuration des fonctionnalités disponibles.|
|

Une fois ce guide terminé, vous êtes configuré avec les autorisations d’accès appropriées, vos points de terminaison sont intégrés et signalent les données de capteur au service, et des fonctionnalités telles que la protection de nouvelle génération et la réduction de la surface d’attaque sont en place.

Quelle que soit l’architecture de l’environnement et la méthode de déploiement que vous choisissez décrites dans les conseils de [déploiement du plan](deployment-strategy.md) , ce guide vous aide à intégrer des points de terminaison.

## <a name="key-capabilities"></a>Fonctionnalités clés

Bien que Microsoft Defender pour point de terminaison offre de nombreuses fonctionnalités, l’objectif principal de ce guide de déploiement est de vous aider à démarrer en intégrant des appareils. En plus de l’intégration, ces conseils vous permettent de commencer avec les fonctionnalités suivantes.

<br>

****

|Fonctionnalité|Description|
|---|---|
|Détection et réponse du point de terminaison|Les fonctionnalités de détection et de réponse des points de terminaison sont mises en place pour détecter, examiner et répondre aux tentatives d’intrusion et aux violations actives.|
|Protection de nouvelle génération|Pour renforcer davantage le périmètre de sécurité de votre réseau, Microsoft Defender pour point de terminaison fait appel à une protection nouvelle génération conçue pour intercepter tous les types de menaces émergentes.|
|Réduction de la surface d'attaque|Fournissez la première ligne de défense dans la pile. En veillant à ce que les paramètres de configuration soient correctement définis et que les techniques d’atténuation des attaques soient appliquées, ces fonctionnalités résistent aux attaques et à l’exploitation.|
|

Toutes ces fonctionnalités sont disponibles pour Microsoft Defender pour point de terminaison titulaires de licence. Pour plus d’informations, consultez [Les exigences en matière de licences](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>Portée

### <a name="in-scope"></a>Dans l’étendue

- Utilisation de Microsoft Endpoint Manager et du point de terminaison Microsoft Configuration Manager pour intégrer des points de terminaison dans le service et configurer des fonctionnalités
- Activation des fonctionnalités de détection et de réponse de point de terminaison Defender pour point de terminaison (EDR)
- Activation des fonctionnalités de la plateforme de protection des points de terminaison Defender pour point de terminaison (PPE)
  - Protection de nouvelle génération
  - Réduction de la surface d'attaque

### <a name="out-of-scope"></a>Non compris

Les éléments suivants ne sont pas inclus dans ce guide de déploiement :

- Configuration de solutions tierces qui peuvent s’intégrer à Defender pour point de terminaison
- Test de pénétration dans un environnement de production

## <a name="see-also"></a>Voir aussi

- [Phase 1 : préparation](prepare-deployment.md)
- [Phase 2 : configuration](production-deployment.md)
- [Phase 3 : intégration](onboarding.md)
- [Planifier le déploiement](deployment-strategy.md)
