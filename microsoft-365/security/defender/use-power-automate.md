---
title: Utiliser Microsoft Power Automate
description: Découvrez l’automatisation de l’alimentation Microsoft 365 Defender comment les utiliser.
keywords: repérage avancé, repérage de menace, repérage de cybermenace, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, copies
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 9d6b786076a218a5257bbd12669f62064ae51f2a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180904"
---
# <a name="use-power-automate-in-microsoft-365-defender"></a>Utiliser Power Automate dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Les équipes d’opérations de sécurité modernes (SecOps) ont besoin d’automatisation pour fonctionner efficacement. Pour se concentrer sur le recherche et l’investigation des menaces réelles, les équipes SecOps utilisent Power Automate pour trier la liste des alertes et éliminer ceux qui ne sont pas des menaces.  

## <a name="criteria-for-resolving-alerts"></a>Critères de résolution des alertes

- Le message d’in-office de l’utilisateur est allumé

- L’utilisateur n’est pas marqué comme étant à risque élevé

Si les deux sont vraies, SecOps marque l’alerte comme un voyage légitime et la résout. Une notification est publiée dans Microsoft Teams une fois l’alerte résolue. 

## <a name="connect-power-automate-to-microsoft-cloud-app-security"></a>Connecter Power Automate à Microsoft Cloud App Security

Pour créer l’automatisation, vous aurez besoin d’un jeton d’API avant de pouvoir vous connecter Power Automate à Microsoft Cloud App Security (MCAS). 

1. Cliquez **Paramètres,** sélectionnez **Extensions de sécurité,** puis cliquez sur Ajouter un jeton **dans** **l’onglet Jetons d’API.** 

2. Fournissez un nom pour votre jeton, puis cliquez sur **Générer.** Enregistrez le jeton, car vous en aurez besoin ultérieurement.

## <a name="create-an-automated-flow"></a>Créer un flux automatisé

Pour obtenir un processus détaillé pas à pas, regardez la vidéo [ici.](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn) 

Cette vidéo décrit également comment connecter l’automatisation de l’alimentation à MCAS. 

## <a name="related-information"></a>Informations connexes

- [Intégrer des Power Automate avec Microsoft Cloud App Security](https://aka.ms/flow-integration)

- [Documentation microsoft Power Automate](https://aka.ms/power-automate-docs)