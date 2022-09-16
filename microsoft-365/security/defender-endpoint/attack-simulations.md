---
title: Expérience Pertahanan Microsoft untuk Titik Akhir par le biais d’attaques simulées
description: Exécutez les simulations de scénario d’attaque fournies pour découvrir comment Pertahanan Microsoft untuk Titik Akhir pouvez détecter, examiner et répondre aux violations.
keywords: test, scénario, attaque, simulation, simulé, diy, Pertahanan Microsoft untuk Titik Akhir
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.openlocfilehash: 20ad6f155a0b9e5dbfc6ff00154f2d4012b80079
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67743369"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>Expérience Pertahanan Microsoft untuk Titik Akhir par le biais d’attaques simulées 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-abovefoldlink)

> [!TIP]
>
> - Découvrez les dernières améliorations apportées à Pertahanan Microsoft untuk Titik Akhir : [Nouveautés de Defender pour point de terminaison.](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/)
> - Defender pour point de terminaison a démontré des fonctionnalités d’optique et de détection de pointe dans l’évaluation MITRE récente. Lire : [Informations tirées de l’évaluation de MITRE basée sur ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

Vous souhaiterez peut-être découvrir Defender pour point de terminaison avant d’intégrer plusieurs appareils au service. Pour ce faire, vous pouvez exécuter des simulations d’attaque contrôlées sur quelques appareils de test. Après avoir exécuté les attaques simulées, vous pouvez examiner comment Defender pour point de terminaison expose une activité malveillante et découvrir comment il permet une réponse efficace.

## <a name="before-you-begin"></a>Avant de commencer

Pour exécuter l’une des simulations fournies, vous avez besoin [d’au moins un appareil intégré](onboard-configure.md).

Lisez le document pas à pas fourni avec chaque scénario d’attaque. Chaque document inclut les exigences du système d’exploitation et de l’application, ainsi que des instructions détaillées spécifiques à un scénario d’attaque.

## <a name="run-a-simulation"></a>Exécuter une simulation

1. Dans **Endpoints** \> **Evaluation & didacticiels tutoriels** \> **& simulations**, sélectionnez les scénarios d’attaque disponibles que vous souhaitez simuler :
   - **Scénario 1 : La porte dérobée du document** simule la remise d’un document d’attrait socialement conçu. Le document lance une porte dérobée spécialement conçue qui permet aux attaquants de contrôler.
   - **Scénario 2 : Script PowerShell dans une attaque sans fichier** : simule une attaque sans fichier qui s’appuie sur PowerShell, présentant la réduction de la surface d’attaque et la détection de l’apprentissage de la mémoire malveillante par l’appareil.
   - **Scénario 3 : Réponse automatisée aux incidents** : déclenche une investigation automatisée, qui recherche et corrige automatiquement les artefacts de violation pour mettre à l’échelle votre capacité de réponse aux incidents.

2. Téléchargez et lisez le document de procédure pas à pas correspondant fourni avec votre scénario sélectionné.

3. Téléchargez le fichier de simulation ou copiez le script de simulation en accédant aux **didacticiels d’évaluation & didacticiels** \> **& simulations**. Vous pouvez choisir de télécharger le fichier ou le script sur l’appareil de test, mais ce n’est pas obligatoire.

4. Exécutez le fichier de simulation ou le script sur l’appareil de test, comme indiqué dans le document de procédure pas à pas.

> [!NOTE]
> Les fichiers ou scripts de simulation imitent l’activité d’attaque, mais ils sont en fait bénins et n’endommagent pas ou ne compromettent pas l’appareil de test.
>
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-belowfoldlink)

## <a name="related-topics"></a>Voir aussi

- [Intégrer des appareils](onboard-configure.md)
- [Intégrer des appareils Windows 10](configure-endpoints.md)
