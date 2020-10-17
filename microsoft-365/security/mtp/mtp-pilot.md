---
title: Exécuter votre projet pilote de protection contre les menaces Microsoft
description: Exécutez votre projet pilote Microsoft Threat Protection dans production pour déterminer efficacement les avantages et l’adoption de Microsoft Threat Protection (MTP).
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
ms.openlocfilehash: f49f1afe5461a4f2eff0a3049f1d14d1892f70ce
ms.sourcegitcommit: 22755cebfbfa2c4dc3f8b4f54ccb23636a211ee5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2020
ms.locfileid: "48477019"
---
# <a name="run-your-pilot-microsoft-threat-protection-project"></a>Exécuter votre projet pilote de protection contre les menaces Microsoft 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Pour déterminer efficacement l’avantage et l’adoption de Microsoft Threat Protection (MTP), vous pouvez exécuter un projet pilote. Avant d’activer la protection Microsoft contre les menaces dans votre environnement de production et de démarrer vos cas d’utilisation, il est préférable d’envisager de déterminer les tâches à accomplir pour votre projet pilote et de définir les critères de réussite. 


## <a name="how-to-use-this-pilot-playbook"></a>Utilisation de ce manuel pilote

Ce guide fournit une vue d’ensemble de la protection contre les menaces Microsoft et des instructions détaillées sur la configuration de votre projet pilote. 

Microsoft Threat Protection est une suite unifiée de défense d’entreprise pré-et post-violation qui coordonne de manière native la protection, la détection, la prévention, l’enquête et la réponse au-delà des points de terminaison, des identités, de la messagerie et des applications, afin de fournir une protection intégrée contre les attaques sophistiquées. Pour ce faire, il combine et orchestre les fonctionnalités suivantes dans une solution de sécurité unique :
  - Microsoft Defender pour le point de terminaison, le nouveau nom de la protection avancée contre les menaces Microsoft Defender (points de terminaison)
  - Microsoft Defender pour Office 365, le nouveau nom pour Office 365 ATP (courrier électronique) 
  - Microsoft Defender for Identity, le nouveau nom pour Azure ATP (Identity) 
  - Sécurité des applications Cloud Microsoft (applications)

![Solution d’image of_Microsoft de protection contre les menaces pour les utilisateurs, Azure Advanced Threat Protection, pour les points de terminaison Microsoft Defender Advanced Threat Protection, pour les applications Cloud, Microsoft Cloud App Security et for Data, Office 365 Advanced Threat Protection  ](../../media/mtp/m365pillars.png)

Avec la solution de protection Microsoft contre les menaces intégrée, les professionnels de la sécurité peuvent associer les signaux de menace que la protection avancée contre les menaces Microsoft Defender, Office 365 ATP, Azure ATP et la sécurité des applications Cloud Microsoft reçoivent, et déterminer l’étendue et l’impact de la menace, la façon dont elle entre dans l’environnement, ce qu’elle affecte, et comment elle influe actuellement sur l’Organisation Microsoft Threat Protection effectue une action automatique pour empêcher ou bloquer les boîtes aux lettres, les points de terminaison et les identités utilisateur affectés autoréparation. Pour plus d’informations, voir la [vue d’ensemble de la protection de Microsoft contre les menaces](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) .

![Phases de l’exécution d’un programme pilote Microsoft Threat Protection](../../media/pilotphases.png)

L’exemple de chronologie suivant varie en fonction de l’utilisation des ressources appropriées dans votre environnement. Certains éléments détectés et les flux de travail peuvent nécessiter plus de temps d’apprentissage que les autres.

![Exemple de chronologie dans l’exécution d’un programme pilote Microsoft Threat Protection](../../media/pilotimeline.png)

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez les instructions de pilote aussi étroitement que possible.


### <a name="pilot-playbook-phases"></a>Phases du projet pilote 

L’exécution d’un programme pilote Microsoft Threat Protection a quatre phases :

|Phase | Description | 
|:-------|:-----|
| ![Planification](../../media/mtp/plan.png)<br>[Planification](mtp-pilot-plan.md)| Découvrez ce que vous devez prendre en compte avant d’exécuter votre projet pilote Microsoft Threat Protection : <br><br>-Étendue <br> Cas d’utilisation <br>- Conditions requises : <br>-Plan de test <br> -Critères de réussite <br> -Scorecard 
| ![Préparation](../../media/mtp/prep.png) <br>[Préparation](mtp-evaluation.md)|  Accédez au centre de sécurité Microsoft 365 pour configurer votre environnement pilote Microsoft Threat Protection. Vous serez guidé pour :<br><br>-Identifier les parties prenantes et se déconnecter pour votre projet pilote <br> -Considérations sur l’environnement <br>-Accès <br>-Installation d’Azure Active Directory <br> -Ordre de configuration <br> -Inscrivez-vous à la version d’évaluation de Microsoft 365 E5 <br> -Configurer le domaine <br>-Affecter les licences Microsoft 365 E5 <br> -Exécutez l’Assistant Installation dans le portail.|
| ![Simulation d’attaque](../../media/mtp/run-sim.png) <br>[Simulation d’attaque](mtp-pilot-simulate.md) | Pour simuler une attaque, vous serez guidé pour :<br><br>-Vérifier les conditions requises pour l’environnement de test <br>-Exécuter la simulation <br>-Enquêter sur un incident <br>-résoudre l’incident 
| ![Fermeture et résumé](../../media/mtp/close.png) <br>[Fermeture et résumé](mtp-pilot-close.md) | Une fois que vous avez atteint la fin de ce processus, vous serez guidé pour :<br><br>-Passer par le résultat final<br>-Présenter votre sortie à vos parties prenantes <br>-Fournir des commentaires <br>-Suivre les étapes suivantes 

## <a name="next-step"></a>Étape suivante
|![Phase de planification](../../media/mtp/plan.png) <br>[Phase de planification](mtp-pilot-plan.md) | Planification de votre projet pilote Microsoft Threat Protection 
|:-------|:-----|
