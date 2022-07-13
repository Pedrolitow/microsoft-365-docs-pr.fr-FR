---
title: Microsoft Defender pour point de terminaison pilote
description: Découvrez comment exécuter un pilote pour Microsoft Defender pour point de terminaison(MDE), notamment en vérifiant le groupe pilote et en essayant des fonctionnalités.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: c12d1bca36884a7b43580b0685f38df99e51ba1d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750404"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Microsoft Defender pour point de terminaison pilote

Cet article vous guidera dans le processus d’exécution d’un pilote pour Microsoft Defender pour point de terminaison. 

Utilisez les étapes suivantes pour configurer le pilote pour Microsoft Defender pour point de terminaison. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-pilot-steps.png" alt-text="Étapes d’ajout de Microsoft Defender pour Identity à l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-endpoint-pilot-steps.png":::

- Étape 1. Vérifier le groupe pilote
- Étape 2. Tester les fonctionnalités

Lorsque vous pilotez Microsoft Defender pour point de terminaison, vous pouvez choisir d’intégrer quelques appareils au service avant d’intégrer l’ensemble de votre organisation.  

Vous pouvez ensuite tester les fonctionnalités disponibles, telles que l’exécution de simulations d’attaque et la façon dont Defender pour point de terminaison expose des activités malveillantes et vous permet d’effectuer une réponse efficace. 

## <a name="step-1-verify-pilot-group"></a>Étape 1. Vérifier le groupe pilote
Une fois les étapes d’intégration décrites dans la section [Activer l’évaluation](eval-defender-endpoint-enable-eval.md) , vous devez voir les appareils dans la liste d’inventaire des appareils environ après une heure. 

Lorsque vous voyez vos appareils intégrés, vous pouvez continuer à tester les fonctionnalités. 

## <a name="step-2-try-out-capabilities"></a>Étape 2. Tester les fonctionnalités
Maintenant que vous avez terminé l’intégration de certains appareils et vérifié qu’ils signalent au service, familiarisez-vous avec le produit en essayant les fonctionnalités puissantes disponibles dès le départ.

Pendant le pilote, vous pouvez facilement commencer à essayer certaines des fonctionnalités pour voir le produit en action sans passer par des étapes de configuration complexes.

Commençons par consulter les tableaux de bord.

### <a name="view-the-device-inventory"></a>Afficher l’inventaire des appareils
L’inventaire des appareils affiche la liste des points de terminaison, des appareils réseau et des appareils IoT dans votre réseau. Non seulement il vous fournit une vue des appareils de votre réseau, mais il fournit également des informations détaillées sur ces appareils, telles que le domaine, le niveau de risque, la plateforme du système d’exploitation et d’autres informations pour faciliter l’identification des appareils les plus à risque.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Afficher le tableau de bord de gestion des menaces et des vulnérabilités 
La gestion des menaces et des vulnérabilités vous aide à vous concentrer sur les faiblesses qui posent les risques les plus urgents et les plus élevés pour l’organisation. À partir du tableau de bord, obtenez une vue générale du score d’exposition de l’organisation, du degré de sécurisation Microsoft pour les appareils, de la distribution de l’exposition des appareils, des principales recommandations de sécurité, des logiciels les plus vulnérables, des principales activités de correction et des données d’appareil les plus exposées. 

### <a name="run-a-simulation"></a>Exécuter une simulation
Microsoft Defender pour point de terminaison est fourni avec [des scénarios d’attaque « Do It Yourself »](https://securitycenter.windows.com/tutorials) que vous pouvez exécuter sur vos appareils pilotes.  Chaque document inclut les exigences du système d’exploitation et de l’application, ainsi que des instructions détaillées spécifiques à un scénario d’attaque. Ces scripts sont sécurisés, documentés et faciles à utiliser. Ces scénarios reflètent les fonctionnalités de Defender pour point de terminaison et vous guident tout au long de l’expérience d’investigation.

Pour exécuter l’une des simulations fournies, vous avez besoin [d’au moins un appareil intégré](../defender-endpoint/onboard-configure.md).

1. Dans Les simulations **d’aide** > **& didacticiels**, sélectionnez les scénarios d’attaque disponibles que vous souhaitez simuler :

   - **Scénario 1 : La porte dérobée du document** simule la remise d’un document d’attrait socialement conçu. Le document lance une porte dérobée spécialement conçue qui permet aux attaquants de contrôler.

   - **Scénario 2 : Script PowerShell dans une attaque sans fichier** : simule une attaque sans fichier qui s’appuie sur PowerShell, présentant la réduction de la surface d’attaque et la détection de l’apprentissage de la mémoire malveillante par l’appareil.

   - **Scénario 3 : Réponse automatisée aux incidents** : déclenche une investigation automatisée, qui recherche et corrige automatiquement les artefacts de violation pour mettre à l’échelle votre capacité de réponse aux incidents.

2. Téléchargez et lisez le document de procédure pas à pas correspondant fourni avec votre scénario sélectionné.

3. Téléchargez le fichier de simulation ou copiez le script de simulation en accédant aux didacticiels **d’aide** > **sur les simulations &**. Vous pouvez choisir de télécharger le fichier ou le script sur l’appareil de test, mais ce n’est pas obligatoire.

4. Exécutez le fichier de simulation ou le script sur l’appareil de test, comme indiqué dans le document de procédure pas à pas.

> [!NOTE]
> Les fichiers ou scripts de simulation imitent l’activité d’attaque, mais ils sont en fait bénins et n’endommagent pas ou ne compromettent pas l’appareil de test.

## <a name="next-steps"></a>Prochaines étapes
[Évaluer Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
