---
title: Exécuter votre projet Pilote Microsoft 365 Defender
description: Exécutez votre projet Pilote Microsoft 365 Defender en production pour déterminer efficacement les avantages et l’adoption de Microsoft 365 Defender.
keywords: Pilote de la Protection Microsoft contre les menaces, exécutez le projet pilote Protection Microsoft contre les menaces, évaluez la Protection Microsoft contre les menaces en production, projet pilote de protection Microsoft contre les menaces, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareils, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 9c0635058539e464a76f1720f041c205a05fa9b2
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49933029"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Exécuter votre projet Pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


Ce guide vous aide à exécuter un projet pilote en fournissant des pointeurs pour vous assurer que vous disposez d’un plan bien structuré, en vous guidant à l’aide de la fonctionnalité de simulation d’attaque et en terminant le projet pilote avec des éléments clés à prendre en compte et documenter les résultats.

![Phases d’exécution d’un pilote Microsoft 365 Defender](../../media/pilotphases.png)


L’exécution d’un pilote vous permet de déterminer efficacement les avantages de l’adoption de Microsoft 365 Defender. Avant d’activer Microsoft 365 Defender dans votre environnement de production et de commencer vos cas d’utilisation, il est préférable de planifier les tâches à accomplir pour votre projet pilote et de définir les critères de réussite. 


## <a name="how-to-use-this-pilot-playbook"></a>Utilisation de ce manuel pilote

Ce guide fournit une vue d’ensemble de Microsoft 365 Defender et des instructions détaillées sur la façon de configurer votre projet pilote. 

Microsoft 365 Defender est une suite unifiée de défense d’entreprise avant et après la violation qui coordonne en natif la protection, la détection, la prévention, l’examen et la réponse entre les points de terminaison, les identités, le courrier électronique et les applications afin de fournir une protection intégrée contre les attaques sophistiquées. Pour ce faire, elle combine et orchestre les fonctionnalités suivantes dans une solution de sécurité unique :
  - Microsoft Defender pour le point de terminaison, nouveau nom de Microsoft Defender - Protection avancée contre les menaces (points de terminaison)
  - Microsoft Defender pour Office 365, nouveau nom d’Office 365 ATP (courrier électronique) 
  - Microsoft Defender pour l’identité, le nouveau nom d’Azure ATP (identité) 
  - Microsoft Cloud App Security (applications)

![Image of_Microsoft solution 365 Defender pour les utilisateurs, Microsoft Defender pour l’identité, pour les points de terminaison Microsoft Defender pour endpoint, pour les applications cloud, Microsoft Cloud App Security et pour les données, Microsoft Defender pour Office 365](../../media/mtp/m365pillars.png)

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender pour identité et Microsoft Cloud App Security reçoivent, et déterminer l’étendue et l’impact complets de la menace, la façon dont il est entré dans l’environnement, ce qu’il est affecté et son impact actuel sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés. Pour plus d’informations, voir la vue d’ensemble de [Microsoft 365 Defender.](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection)



L’exemple de chronologie suivant varie selon que vous disposez des ressources appropriées dans votre environnement. Certaines détections et flux de travail peuvent avoir besoin de plus de temps d’apprentissage que les autres.

![Exemple de chronologie lors de l’exécution d’un pilote Microsoft 365 Defender](../../media/phase-diagrams/pilot-phases.png)

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez les instructions pilotes aussi étroitement que possible.


### <a name="pilot-playbook-phases"></a>Phases de lecture pilote 

L’exécution d’un pilote Microsoft 365 Defender se fait en quatre phases :

|Phase | Description | 
|:-------|:-----|
| [Planification](mtp-pilot-plan.md)<br> ~ 1 jour| Découvrez ce que vous devez prendre en compte avant d’exécutez votre projet pilote Microsoft 365 Defender : <br><br>- Étendue <br> - Cas d’utilisation <br>- Conditions requises : <br>- Plan de test <br> - Critères de réussite <br> - Carte de performance 
| [Préparation](mtp-evaluation.md) <br>~2 jours|  Accédez au Centre de sécurité Microsoft 365 pour configurer votre environnement pilote Microsoft 365 Defender. Vous serez guidé vers :<br><br>- Identifier les parties prenantes et demander la signature de votre projet pilote <br> - Considérations sur l’environnement <br>- Access <br>- Configuration d’Azure Active Directory <br> - Ordre de configuration <br> - S’inscrire à la version d’essai de Microsoft 365 E5 <br> - Configurer un domaine <br>- Attribuer des licences Microsoft 365 E5 <br> - Terminer l’Assistant Installation dans le portail|
| [Simulation d’attaque](mtp-pilot-simulate.md) <br>~2 jours| Pour simuler une attaque, vous serez guidé vers :<br><br>- Vérifier les conditions requises pour l’environnement de test <br>- Exécuter la simulation <br>- Examiner un incident <br>- résoudre l’incident 
| [Fermeture et résumé](mtp-pilot-close.md) <br>~ 1 jour| Lorsque vous aurez atteint la fin du processus, vous serez guidé vers :<br><br>- Passer par votre résultat final<br>- Présenter votre résultat à vos parties prenantes <br>- Fournir des commentaires <br>- Prendre les étapes suivantes 

## <a name="next-step"></a>Étape suivante
|[Phase de planification](mtp-pilot-plan.md) | Planifier votre projet pilote Microsoft 365 Defender 
|:-------|:-----|
