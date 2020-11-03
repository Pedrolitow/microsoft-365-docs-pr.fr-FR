---
title: Exécuter votre projet pilote Microsoft 365 Defender
description: Exécutez votre projet pilote Microsoft 365 Defender en production pour déterminer efficacement les avantages et l’adoption de Microsoft 365 Defender.
keywords: Microsoft Threat Protection Pilot, exécuter le projet pilote de protection contre les menaces Microsoft, évaluer la protection de Microsoft contre les menaces en production, projet pilote de protection contre les menaces Microsoft, protection contre la vulnérabilité, protection avancée contre les menaces, sécurité des entreprises, périphériques, appareil, identité, utilisateurs, données, applications, incidents, recherche et correction automatiques, chasse avancée
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
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.openlocfilehash: 350904022ec86acdbebf109dd5946598643aea83
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843659"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Exécuter votre projet pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Pour déterminer efficacement l’avantage et l’adoption de Microsoft 365 Defender, vous pouvez exécuter un projet pilote. Avant d’activer Microsoft 365 Defender dans votre environnement de production et de démarrer vos cas d’utilisation, il est préférable de planifier les tâches à accomplir pour votre projet pilote et de définir les critères de réussite. 


## <a name="how-to-use-this-pilot-playbook"></a>Utilisation de ce manuel pilote

Ce guide fournit une vue d’ensemble de Microsoft 365 Defender et des instructions détaillées sur la configuration de votre projet pilote. 

Microsoft 365 Defender est une suite de défense d’entreprise pré-et post-faille unifiée qui coordonne de manière native la protection, la détection, la prévention, l’enquête et la réponse au-delà des points de terminaison, des identités, de la messagerie et des applications, afin de fournir une protection intégrée contre les attaques sophistiquées. Pour ce faire, il combine et orchestre les fonctionnalités suivantes dans une solution de sécurité unique :
  - Microsoft Defender pour le point de terminaison, le nouveau nom de la protection avancée contre les menaces Microsoft Defender (points de terminaison)
  - Microsoft Defender pour Office 365, le nouveau nom pour Office 365 ATP (courrier électronique) 
  - Microsoft Defender for Identity, le nouveau nom pour Azure ATP (Identity) 
  - Sécurité des applications Cloud Microsoft (applications)

![Image of_Microsoft 365 Defender solution for Users, Microsoft Defender for Identity, for Endpoints Microsoft Defender for Endpoint, for Cloud Apps, Microsoft Cloud App Security, and for Data, Microsoft Defender for Office 365](../../media/mtp/m365pillars.png)

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour les identités et recevoir la sécurité de l’application Cloud Microsoft, et déterminer l’étendue et l’impact de la menace, la façon dont elle entre dans l’environnement, ce qu’elle affecte, et comment elle Microsoft 365 Defender effectue une action automatique pour empêcher ou bloquer les boîtes aux lettres affectées, les points de terminaison et les identités des utilisateurs concernés. Pour plus d’informations, consultez la [vue d’ensemble de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) .

![Phases de l’exécution d’un pilote Microsoft 365 Defender](../../media/pilotphases.png)

L’exemple de chronologie suivant varie en fonction de l’utilisation des ressources appropriées dans votre environnement. Certains éléments détectés et les flux de travail peuvent nécessiter plus de temps d’apprentissage que les autres.

![Exemple de chronologie dans l’exécution d’un pilote Microsoft 365 Defender](../../media/pilotimeline.png)

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez les instructions de pilote aussi étroitement que possible.


### <a name="pilot-playbook-phases"></a>Phases du projet pilote 

L’exécution d’un projet pilote Microsoft 365 Defender s’effectue en quatre étapes :

|Phase | Description | 
|:-------|:-----|
| ![Planification](../../media/mtp/plan.png)<br>[Planification](mtp-pilot-plan.md)| Découvrez ce que vous devez prendre en compte avant d’exécuter votre projet pilote Microsoft 365 Defender : <br><br>-Étendue <br> Cas d’utilisation <br>- Conditions requises : <br>-Plan de test <br> -Critères de réussite <br> -Scorecard 
| ![Préparation](../../media/mtp/prep.png) <br>[Préparation](mtp-evaluation.md)|  Accédez au centre de sécurité Microsoft 365 pour configurer votre environnement pilote Microsoft 365 Defender. Vous serez guidé pour :<br><br>-Identifier les parties prenantes et se déconnecter pour votre projet pilote <br> -Considérations sur l’environnement <br>-Accès <br>-Installation d’Azure Active Directory <br> -Ordre de configuration <br> -Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 <br> -Configurer le domaine <br>-Affecter les licences Microsoft 365 E5 <br> -Exécutez l’Assistant Installation dans le portail.|
| ![Simulation d’attaque](../../media/mtp/run-sim.png) <br>[Simulation d’attaque](mtp-pilot-simulate.md) | Pour simuler une attaque, vous serez guidé pour :<br><br>-Vérifier les conditions requises pour l’environnement de test <br>-Exécuter la simulation <br>-Enquêter sur un incident <br>-résoudre l’incident 
| ![Fermeture et résumé](../../media/mtp/close.png) <br>[Fermeture et résumé](mtp-pilot-close.md) | Une fois que vous avez atteint la fin de ce processus, vous serez guidé pour :<br><br>-Passer par le résultat final<br>-Présenter votre sortie à vos parties prenantes <br>-Fournir des commentaires <br>-Suivre les étapes suivantes 

## <a name="next-step"></a>Étape suivante
|![Phase de planification](../../media/mtp/plan.png) <br>[Phase de planification](mtp-pilot-plan.md) | Planification de votre projet pilote Microsoft 365 Defender 
|:-------|:-----|
