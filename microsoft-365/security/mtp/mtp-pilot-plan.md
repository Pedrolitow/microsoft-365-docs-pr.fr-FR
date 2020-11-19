---
title: Planification de votre projet pilote Microsoft 365 Defender
description: Planifiez votre projet pilote Microsoft 365 Defender avec les parties prenantes pour gérer les attentes et garantir le bon déroulement de l’opération.
keywords: Microsoft Threat Protection Pilot, planifier le projet pilote de protection des menaces Microsoft, évaluer la protection de Microsoft contre les menaces en production, projet pilote Microsoft Threat Protection, protection contre la vulnérabilité, protection avancée contre les menaces, sécurité de l’entreprise, périphériques, appareil, identité, utilisateurs, données, applications, incidents, analyse automatisée et correction, recherche avancée
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
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.openlocfilehash: 649f3e777a330e1b60faf4f3513a470b51e56a80
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49356978"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>Planification de votre projet pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

|![Planification](../../media/phase-diagrams/1-planning.png)<br/>Planification|[![Préparation](../../media/phase-diagrams/2-prepare.png)](prepare-mtpeval.md)<br/>[Préparation](prepare-mtpeval.md) | [![Simuler une attaque](../../media/phase-diagrams/3-simluate.png)](mtp-pilot-simulate.md)<br/>[Simuler une attaque](mtp-pilot-simulate.md) | [![Fermer et synthétiser](../../media/phase-diagrams/4-summary.png)](mtp-pilot-close.md)<br/>[Fermer et synthétiser](mtp-pilot-close.md)|
|--|--|--|--|
|*Vous êtes là !*| | | |

Vous êtes actuellement à la phase de planification.

Pour vous assurer que votre projet pilote a réussi, il est essentiel de planifier soigneusement et d’obtenir des approbations de vos parties prenantes au début. Les éléments de la planification incluent l’identification de l’étendue, des cas d’utilisation, des exigences et des critères de réussite.

Ce guide vous guide tout au long de la planification de votre projet pilote. 

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez les instructions de pilote aussi étroitement que possible.


## <a name="scope"></a>Portée

L’étendue du projet pilote détermine la portée du test, en fonction de votre environnement et des méthodes de test acceptables. Voici quelques exemples d’étendues à prendre en compte :
- Environnement de développement ou de test qui inclut des points de terminaison, des serveurs, des contrôleurs de domaine.
- Environnement de production avec Microsoft 365, Azure, services Active Directory, points de terminaison et serveurs

>[!NOTE]
>Si vous ne disposez pas encore de toutes les licences, vous pouvez obtenir des licences d’évaluation pour [évaluer Microsoft 365 Defender](https://aka.ms/mtp-trial-lab) – planification, préparation, configuration, configuration et exécution de votre projet pilote. Vos parties prenantes joueront un rôle important en facilitant le processus du début à la fin.

Les types de systèmes d’exploitation à évaluer doivent également être définis en fonction de la composition de l’organisation. Cela peut être le suivant : [points de terminaison Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements), [serveurs Linux](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements), [points de terminaison windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions), [Windows Server 2016](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>Cas d’utilisation

Les cas d’utilisation représentent des instructions expliquant comment l’outil testé est destiné à être consommé par les utilisateurs prévus. Celles-ci peuvent être formulées sous la forme de récits utilisateur du point de vue d’un personnage particulier, tel qu’un analyste SOC. Par exemple :
- En tant qu’analyste SOC, je dois afficher, corréler, évaluer et gérer les alertes et les événements sur les appareils, les utilisateurs et les boîtes aux lettres de mon réseau. [Gestion des incidents]
- En tant qu’analyste SOC, j’ai besoin de l’outil et du processus pour examiner et répondre automatiquement aux événements malveillants de mon réseau. [Auto IR]
- En tant qu’analyste SOC, je dois Rechercher des données dans mon environnement pour trouver des menaces connues et potentielles, ainsi que des activités suspectes. [Chasse avancée]

N’oubliez pas que ces cas d’utilisation doivent être créés dans les paramètres de l’étendue définie. Si, par exemple, l’étendue du test n’inclut pas une évaluation des outils tels que Microsoft Cloud App Security, alors les cas d’utilisation qui s’en reposent en tant que source de données ne doivent pas être créés.

## <a name="requirements"></a>Configuration requise

Dans la liste des cas d’utilisation, vous pouvez commencer à créer des exigences. Les conditions requises incluent les fonctionnalités dont doit disposer un outil pour satisfaire les cas d’utilisation. Ces exigences peuvent être divisées en catégories telles que la configuration et la maintenance, la prise en charge des intégrations et les exigences spécifiques aux fonctionnalités telles que la possibilité de la chasse et la possibilité de créer des alertes personnalisées.

## <a name="test-plan"></a>Plan de test

Selon les exigences, différentes méthodes de test peuvent être appropriées. Par exemple, si l’impératif est d’évaluer l’efficacité de la correction automatisée, le plan de test doit inclure des étapes pour générer le ou les comportements qui déclencheraient une action de correction automatisée dans Microsoft 365 Defender. Si la nécessité est de détecter un comportement ou une attaque particulière, le test peut impliquer davantage d’étapes. Le point doit disposer d’un plan en place pour tester précisément votre configuration requise.

## <a name="success-criteria"></a>Critères de réussite

Les critères de réussite correspondent finalement à la barre de mesure par rapport à ce que vous testez. Que vous testiez Microsoft 365 Defender (ou toute autre technologie) contre d’autres outils ou par lui-même, il doit exister des critères quantifiables pour déterminer la valeur fournie par l’outil. En fonction de l’étendue, des exigences et du plan de test, les critères de réussite déterminent le score du test. Cela doit être inférieur à la réussite ou à l’échec, ainsi qu’à un score pondéré en fonction de vos besoins. Par exemple, pour réussir, un outil peut avoir besoin d’un score supérieur à 80% dans certaines zones critiques que vous identifiez.

## <a name="scorecard"></a>Prospectif

Une façon de rassembler tous les éléments de votre plan peut consister à créer une carte de performance. Voir un exemple de carte de performance ci-dessous :

| Cas d’utilisation | Configuration requise | Configuration requise | Plan de test | Résultat attendu | État du test | Niveau | Notes |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|Gestion des incidents|-Microsoft 365 Defender  </br></br>-Microsoft Defender pour l’identité </br></br>-Microsoft Defender pour le point de terminaison </br></br>-Sécurité des applications Cloud Microsoft (facultatif)|Voir les [conditions préalables](https://aka.ms/mtp-trial-lab) pour la préparation, l’installation et la configuration pour plus de détails |[Simuler une attaque](mtp-pilot-simulate.md) <br></br>[Examen de l’incident](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#investigate-an-incident) |Les investigateurs peuvent comprendre l’étendue et l’impact de l’incident et gérer l’incident.||||
|AutoIR|-Microsoft 365 Defender </br></br>-Microsoft Defender pour l’identité </br></br>-Microsoft Defender pour le point de terminaison |Voir les [conditions préalables](https://aka.ms/mtp-trial-lab) pour la préparation, l’installation et la configuration pour plus de détails <br>Activer AutoIR  |[Simuler une attaque](mtp-pilot-simulate.md) <br></br>[Enquête automatisée](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#automated-investigation-and-remediation) |Les alertes et les incidents sont automatiquement résolus par Microsoft 365 Defender||||
|Repérage avancé|-Microsoft 365 Defender </br></br>-Microsoft Defender pour le point de terminaison </br></br>-Microsoft Defender pour Office 365 |Voir les [conditions préalables](https://aka.ms/mtp-trial-lab) pour la préparation, l’installation et la configuration pour plus de détails|[Scénario de chasse avancé](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#advanced-hunting-scenario) |Les investigateurs peuvent trouver des données par le biais d’une recherche avancée, d’un pivotement vers des entités affectées et en créant des détections personnalisées.||||



## <a name="next-step"></a>Étape suivante
|![Phase de préparation](../../media/mtp/prep.png) <br>[Phase de préparation](prepare-mtpeval.md) | Préparation de votre environnement pilote Microsoft 365 Defender
|:-------|:-----|
