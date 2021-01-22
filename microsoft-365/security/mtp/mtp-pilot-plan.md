---
title: Planification de votre projet Pilote Microsoft 365 Defender
description: Planifiez votre projet Microsoft 365 Defender pilote avec les parties prenantes pour gérer les attentes et garantir un résultat réussi.
keywords: Pilote de la Protection Microsoft contre les menaces, planifier le projet pilote Protection Microsoft contre les menaces, évaluer la Protection Microsoft contre les menaces en production, projet pilote de protection Microsoft contre les menaces, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareils, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 8037b71fc41fb7fb0bdbfc829bad2ece1de6849b
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930173"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>Planification de votre projet Pilote Microsoft 365 Defender 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

|![Planification](../../media/phase-diagrams/1-planning.png)<br/>Planification|[![Préparation](../../media/phase-diagrams/2-prepare.png)](prepare-mtpeval.md)<br/>[Préparation](prepare-mtpeval.md) | [![Simuler une attaque](../../media/phase-diagrams/3-simluate.png)](mtp-pilot-simulate.md)<br/>[Simuler une attaque](mtp-pilot-simulate.md) | [![Fermer et synthétiser](../../media/phase-diagrams/4-summary.png)](mtp-pilot-close.md)<br/>[Fermer et synthétiser](mtp-pilot-close.md)|
|--|--|--|--|
|*Vous êtes là !*| | | |

Vous êtes actuellement en phase de planification.

Pour garantir la réussite de votre projet pilote, il est essentiel de planifier minutieusement et d’obtenir les approbations de vos parties prenantes au début. Les éléments de planification incluent l’identification de l’étendue, des cas d’utilisation, des exigences et des critères de réussite.

Ce guide vous guide tout au long de la façon de planifier votre projet pilote. 

>[!IMPORTANT]
>Pour obtenir des résultats optimaux, suivez les instructions pilotes aussi étroitement que possible.


## <a name="scope"></a>Portée

L’étendue du projet pilote déterminera la portée du test, en fonction de votre environnement et des méthodes de test acceptables. Voici quelques exemples d’étendues à prendre en compte :
- Environnement de développement ou de test qui inclut des points de terminaison, des serveurs, des contrôleurs de domaine.
- Environnement de production avec Microsoft 365, Azure, services Active Directory, points de terminaison et serveurs

>[!NOTE]
>Si vous n’avez pas encore les licences complètes, vous pouvez obtenir des licences d’évaluation pour évaluer [Microsoft 365 Defender](https://aka.ms/mtp-trial-lab) : planifiez, préparez, configurez, configurez et exécutez votre projet pilote. Vos parties prenantes jouent un rôle important pour faciliter le processus du début à la fin.

Les types de systèmes d’exploitation à évaluer doivent également être définis en fonction de la composition organisationnelle. Cela peut inclure les points de terminaison [Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements), serveurs [Linux](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements), points de terminaison [Windows 10](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions), [Windows Server 2016](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>Cas d’utilisation

Les cas d’utilisation représentent des instructions sur la façon dont l’outil testé est destiné à être utilisé par ses utilisateurs prévus. Elles peuvent être formulées sous forme d’articles d’utilisateur du point de vue d’un personnage particulier, tel qu’un analyste SOC. Par exemple :
- En tant qu’analyste SOC, je dois afficher, corréler, évaluer et gérer les alertes et les événements sur les appareils, les utilisateurs et les boîtes aux lettres dans mon réseau. [Gestion des incidents]
- En tant qu’analyste SOC, je dois avoir l’outil et le processus permettant d’examiner et de répondre automatiquement aux événements malveillants dans mon réseau. [Ir automatique]
- En tant qu’analyste SOC, je dois rechercher des données à partir de mon environnement pour rechercher des menaces connues et potentielles, ainsi que des activités suspectes. [Recherche avancée]

N’oubliez pas que ces cas d’utilisation doivent être créés dans les paramètres de l’étendue définie. Si, par exemple, l’étendue des tests n’inclut pas d’évaluation d’outils tels que Microsoft Cloud App Security, les cas d’utilisation qui s’appuient sur cette source de données ne doivent pas être créés.

## <a name="requirements"></a>Conditions requises

Dans la liste des cas d’utilisation, vous pouvez commencer à créer des conditions requises. Les conditions requises incluent des fonctionnalités qu’un outil doit avoir pour satisfaire les cas d’utilisation. Ces exigences peuvent être décomposées en catégories telles que la configuration et la maintenance, la prise en charge des intégrations et les exigences spécifiques aux fonctionnalités telles que la capacité de recherche et la possibilité de créer des alertes personnalisées.

## <a name="test-plan"></a>Plan de test

Selon les exigences, différentes méthodes de test peuvent être appropriées. Par exemple, si l’exigence consiste à évaluer l’efficacité de la correction automatisée, le plan de test doit inclure des étapes pour générer le ou les comportements qui déclencheraient une action de correction automatisée dans Microsoft 365 Defender. Si l’exigence consiste à détecter un comportement ou une attaque particulier, le test peut impliquer d’autres étapes. L’objectif est de mettre en place un plan pour un test précis par rapport à vos besoins.

## <a name="success-criteria"></a>Critères de réussite

Les critères de réussite sont en fin de compte l’ensemble de barres à mesurer par rapport à ce que vous testez. Que vous testiez Microsoft 365 Defender (ou toute autre technologie d’ailleurs) par rapport à d’autres outils ou par lui-même, il doit y avoir des critères quantifiables pour déterminer la valeur que l’outil fournit. En fonction de l’étendue, des exigences et du plan de test, les critères de réussite déterminent comment évaluer le test. Il doit s’agit de moins d’une passe ou d’un échec et d’une notation pondérée en fonction de vos besoins. Par exemple, pour réussir, un outil devra peut-être obtenir un score supérieur à 80 % dans certains domaines critiques que vous identifiez.

## <a name="scorecard"></a>Carte de performance

Une façon de rassembler tous les éléments de votre plan peut être de créer une carte de performance. Voir un exemple de carte de performance ci-dessous :

| Cas d’utilisation | Conditions requises | Configuration requise | Plan de test | Résultat attendu | État du test | Niveau | Notes |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|Gestion des incidents|- Microsoft 365 Defender  </br></br>- Microsoft Defender pour l’identité </br></br>- Microsoft Defender pour point de terminaison </br></br>- Microsoft Cloud App Security (facultatif)|Pour plus [d’informations,](https://aka.ms/mtp-trial-lab) voir les conditions préalables à la préparation, à la configuration et à la configuration |[Simuler une attaque](mtp-pilot-simulate.md) <br></br>[Examiner l’incident](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#investigate-an-incident) |Les enquêteurs peuvent comprendre l’étendue et l’impact de l’incident et gérer l’incident||||
|AutoIR|- Microsoft 365 Defender </br></br>- Microsoft Defender pour l’identité </br></br>- Microsoft Defender pour point de terminaison |Pour plus [d’informations,](https://aka.ms/mtp-trial-lab) voir les conditions préalables à la préparation, à la configuration et à la configuration <br>Activer autoIR  |[Simuler une attaque](mtp-pilot-simulate.md) <br></br>[Examen automatisé](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#automated-investigation-and-remediation) |Les alertes et les incidents sont automatiquement corrigés par Microsoft 365 Defender||||
|Repérage avancé|- Microsoft 365 Defender </br></br>- Microsoft Defender pour point de terminaison </br></br>-Microsoft Defender pour Office 365 |Pour plus [d’informations,](https://aka.ms/mtp-trial-lab) voir les conditions préalables à la préparation, à la configuration et à la configuration|[Scénario de recherche avancée](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-pilot-simulate#advanced-hunting-scenario) |Les enquêteurs peuvent trouver des données par le biais d’un repérage avancé, d’un pivoting vers des entités impactées et de la création de détections personnalisées||||



## <a name="next-step"></a>Étape suivante
|![Phase de préparation](../../media/mtp/prep.png) <br>[Phase de préparation](prepare-mtpeval.md) | Préparer votre environnement pilote Microsoft 365 Defender
|:-------|:-----|
