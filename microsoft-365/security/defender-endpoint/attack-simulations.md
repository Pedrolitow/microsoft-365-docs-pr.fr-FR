---
title: Expérience de Microsoft Defender ATP par le biais d’attaques simulées
description: Exécutez les simulations de scénario d’attaque fournies pour découvrir comment Microsoft Defender ATP peut détecter, examiner et répondre aux violations.
keywords: wdatp, test, scénario, attaque, simulation, simulation, course, Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.technology: mde
ms.openlocfilehash: b3fb862ac6e845ed4a3f5b72bae902f00c125b53
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51498299"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Expérience de Microsoft Defender pour point de terminaison par le biais d’attaques simulées 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-attacksimulations-abovefoldlink)

>[!TIP]
>- Découvrez les dernières améliorations apportées à Microsoft Defender ATP : Nouveautés [de Defender pour Endpoint ?](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/)
>- Defender pour le point de terminaison a démontré les fonctionnalités d’optique et de détection de pointe du secteur dans l’évaluation MITRE récente. Read: [Insights from the MITRE ATT&CK-based evaluation](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

Vous souhaitez peut-être faire l’expérience de Defender for Endpoint avant d’intégrer plusieurs appareils au service. Pour ce faire, vous pouvez exécuter des simulations d’attaques contrôlées sur quelques périphériques de test. Après avoir réalisé les attaques simulées, vous pouvez examiner la façon dont Defender pour le point de terminaison fait face à une activité malveillante et découvrir comment elle permet une réponse efficace.

## <a name="before-you-begin"></a>Avant de commencer

Pour exécuter l’une des simulations fournies, vous avez besoin d’au moins [un appareil intégré.](onboard-configure.md) 

Lisez le document pas à pas fourni avec chaque scénario d’attaque. Chaque document inclut les exigences en matière de système d’exploitation et d’application, ainsi que des instructions détaillées propres à un scénario d’attaque.

## <a name="run-a-simulation"></a>Exécuter une simulation

1. Dans **les**  >  **simulations d'& didacticiels,** sélectionnez les scénarios d’attaque disponibles que vous souhaitez simuler :

   - **Scénario 1 : le document abandonne la porte dérobée** : simule la remise d’un document leurre d’ingénierie sociale. Le document lance une porte dérobée spécialement conçue pour donner le contrôle aux attaquants.

   - **Scénario 2** : script PowerShell dans une attaque sans fichier : simule une attaque sans fichier qui s’appuie sur PowerShell, présentant la réduction de la surface d’attaque et la détection de l’apprentissage de l’activité de mémoire malveillante.
    
   - **Scénario 3 : réponse** automatisée aux incidents : déclenche une enquête automatisée, qui recherche et remédie automatiquement aux artefacts de violation pour mettre à l’échelle votre capacité de réponse aux incidents.

2. Téléchargez et lisez le document de la walkthrough correspondant fourni avec votre scénario sélectionné.

3. Téléchargez le fichier de simulation ou copiez le script de simulation en naviguant vers l’aide  >  **simulations & didacticiels**. Vous pouvez choisir de télécharger le fichier ou le script sur le périphérique de test, mais ce n’est pas obligatoire.

4. Exécutez le fichier ou le script de simulation sur le périphérique de test comme indiqué dans le document pas à pas.

> [!NOTE]
> Les fichiers ou scripts de simulation imitent l’activité d’attaque, mais sont en réalité anodins et ne compromettent pas ou ne compromettent pas le périphérique de test.
> 
> 
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-attacksimulations-belowfoldlink)


## <a name="related-topics"></a>Voir aussi

- [Appareils intégrés](onboard-configure.md)
- [Intégrer des appareils Windows 10](configure-endpoints.md)
