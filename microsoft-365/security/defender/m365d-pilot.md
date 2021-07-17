---
title: Exécuter votre projet pilote Microsoft 365 Defender projet
description: Exécutez votre projet pilote Microsoft 365 Defender production pour déterminer efficacement les avantages et l’adoption de Microsoft 365 Defender.
keywords: Microsoft 365 Defender pilote, exécuter le projet Microsoft 365 Defender pilote, évaluer les Microsoft 365 Defender en production, projet pilote Microsoft 365 Defender, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fd84ef93d679be6e1e42f823dcac1f2d5181f1e9
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53458419"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Exécuter votre projet pilote Microsoft 365 Defender projet 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


Ce guide vous aide à exécuter un projet pilote en fournissant des pointeurs pour vous assurer que vous disposez d’un plan bien structuré, en vous guidant à l’aide de la fonctionnalité de simulation d’attaque et en terminant le projet pilote avec des éléments clés à prendre en compte et documenter les résultats.

![Phases d’exécution d’Microsoft 365 Defender pilote](../../media/pilotphases.png)


L’exécution d’un projet pilote vous permet de déterminer efficacement les avantages de l’adoption Microsoft 365 Defender. Avant d’activer Microsoft 365 Defender dans votre environnement de production et de commencer vos cas d’utilisation, il est préférable de planifier les tâches à accomplir pour votre projet pilote et de définir les critères de réussite. 


## <a name="how-to-use-this-pilot-playbook"></a>Utilisation de ce manuel pilote

Ce guide fournit une vue d’Microsoft 365 Defender des instructions détaillées sur la façon de configurer votre projet pilote. 

Microsoft 365 Defender est une suite unifiée de défense d’entreprise avant et après la violation qui coordonne en natif la protection, la détection, la prévention, l’examen et la réponse entre les points de terminaison, les identités, le courrier électronique et les applications afin de fournir une protection intégrée contre les attaques sophistiquées. Pour ce faire, elle combine et orchestre les fonctionnalités suivantes dans une solution de sécurité unique :

- Microsoft Defender pour les points de terminaison (points de terminaison)
- Microsoft Defender pour Office 365 (e-mail)
- Microsoft Defender pour l’identité (identité)
- Microsoft Cloud App Security (applications)

![Image of_Microsoft solution 365 Defender pour les utilisateurs, Microsoft Defender pour l’identité, pour les points de terminaison Microsoft Defender pour le point de terminaison, pour les applications cloud, Microsoft Cloud App Security et pour les données, Microsoft Defender pour Office 365](../../media/mtp/m365pillars.png)

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour identité et Microsoft Cloud App Security reçoivent, et déterminer l’étendue et l’impact complets de la menace, la façon dont elle est entrée dans l’environnement, ce qu’elle est affectée et son impact actuel sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés. Pour plus [d’Microsoft 365 Defender, voir](microsoft-365-defender.md) la vue d’ensemble du programme.

L’exemple de chronologie suivant varie selon que vous disposez des ressources appropriées dans votre environnement. Certaines détections et flux de travail peuvent avoir besoin de plus de temps d’apprentissage que les autres.

![Exemple de chronologie lors de l’exécution d Microsoft 365 Defender pilote](../../media/phase-diagrams/pilot-phases.png)

> [!IMPORTANT]
> Pour obtenir des résultats optimaux, suivez les instructions pilotes aussi étroitement que possible.

### <a name="pilot-playbook-phases"></a>Phases de lecture pilote

Il existe quatre phases pour l’exécution d’Microsoft 365 Defender pilote :

|Phase | Description |
|:-------|:-----|
| [Planification](m365d-pilot-plan.md)<br> ~ 1 jour| Découvrez ce que vous devez prendre en compte avant d’Microsoft 365 Defender projet pilote : <br><br>- Étendue <br> - Cas d’utilisation <br>- Conditions requises : <br>- Plan de test <br> - Critères de réussite <br> - Carte de performance 
| [Préparation](m365d-evaluation.md) <br>~2 jours|  Accédez Microsoft 365 centre de sécurité pour configurer votre environnement Microsoft 365 Defender pilote. Vous serez guidé vers :<br><br>- Identifier les parties prenantes et demander la signature de votre projet pilote <br> - Considérations sur l’environnement <br>- Access <br>- configuration Azure Active Directory’installation <br> - Ordre de configuration <br> - S’inscrire à Microsoft 365 E5 d’essai <br> - Configurer un domaine <br>- Attribuer Microsoft 365 E5 licences <br> - Terminer l’Assistant Installation dans le portail|
| [Simulation d’attaque](m365d-pilot-simulate.md) <br>~2 jours| Pour simuler une attaque, vous serez guidé vers :<br><br>- Vérifier les conditions requises pour l’environnement de test <br>- Exécuter la simulation <br>- Examiner un incident <br>- résoudre l’incident 
| [Fermeture et résumé](m365d-pilot-close.md) <br>~ 1 jour| Lorsque vous aurez atteint la fin du processus, vous serez guidé vers :<br><br>- Passer par votre résultat final<br>- Présenter votre résultat à vos parties prenantes <br>- Fournir des commentaires <br>- Prendre les étapes suivantes 

## <a name="next-step"></a>Étape suivante

|[Phase de planification](m365d-pilot-plan.md) | Planifier votre projet Microsoft 365 Defender projet pilote 
|:-------|:-----|
