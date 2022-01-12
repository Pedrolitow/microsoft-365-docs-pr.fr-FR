---
title: Pilote Microsoft Defender pour le point de terminaison
description: Découvrez comment exécuter un pilote pour Microsoft Defender for Endpoint(MDE), notamment en vérifiant le groupe pilote et en essayant des fonctionnalités.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7008b78ae5b01925e97143841b453a2c5c573fcc
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61941069"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Pilote Microsoft Defender pour le point de terminaison

Cet article vous guide dans le processus d’exécution d’un pilote pour Microsoft Defender pour Endpoint. 

Utilisez les étapes suivantes pour configurer le pilote de Microsoft Defender pour Endpoint. 

![Étapes d’ajout de Microsoft Defender for Identity à l’environnement d’évaluation Defender.](../../media/defender/m365-defender-endpoint-pilot-steps.png)

- Étape 1. Vérifier le groupe pilote
- Étape 2. Tester les fonctionnalités

Lorsque vous pilotez Microsoft Defender pour endpoint, vous pouvez choisir d’intégrer quelques appareils au service avant d’intégrer l’ensemble de votre organisation.  

Vous pouvez ensuite essayer des fonctionnalités disponibles, telles que l’exécution de simulations d’attaques et l’analyse de la façon dont Defender pour le point de terminaison surface les activités malveillantes et vous permet d’effectuer une réponse efficace. 

## <a name="step-1-verify-pilot-group"></a>Étape 1. Vérifier le groupe pilote
Après avoir effectué les étapes d’intégration décrites dans la [section](eval-defender-endpoint-enable-eval.md) Activer l’évaluation, vous devez voir les appareils dans la liste d’inventaire des appareils environ après une heure. 

Lorsque vous voyez vos appareils intégrés, vous pouvez passer aux fonctionnalités d’essai. 

## <a name="step-2-try-out-capabilities"></a>Étape 2. Tester les fonctionnalités
Maintenant que vous avez terminé l’intégration de certains appareils et vérifié qu’ils font des rapports au service, familiarisez-vous avec le produit en essayant les fonctionnalités puissantes qui sont disponibles immédiatement.

Pendant le projet pilote, vous pouvez facilement commencer à essayer certaines fonctionnalités pour voir le produit en action sans passer par des étapes de configuration complexes.

Commençons par consulter les tableaux de bord.

### <a name="view-the-device-inventory"></a>Afficher l’inventaire des appareils
L’inventaire des appareils vous permet de voir la liste des points de terminaison, des périphériques réseau et des appareils IoT dans votre réseau. Non seulement elle vous fournit une vue des appareils de votre réseau, mais elle fournit également des informations détaillées sur ces appareils, telles que le domaine, le niveau de risque, la plateforme de système d’exploitation et d’autres détails pour faciliter l’identification des appareils les plus exposés.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Afficher le tableau de bord Menaces gestion des vulnérabilités tableau de bord 
Les menaces gestion des vulnérabilités vous aident à vous concentrer sur les faiblesses qui posent le risque le plus urgent et le plus élevé pour l’organisation. À partir du tableau de bord, obtenez une vue d’ensemble du score d’exposition de l’organisation, du Degré de sécurisation Microsoft pour les appareils, de la distribution de l’exposition des appareils, des principales recommandations en matière de sécurité, des logiciels les plus vulnérables, des principales activités de correction et des données d’appareils les plus exposées. 

### <a name="run-a-simulation"></a>Exécuter une simulation
Microsoft Defender pour point de terminaison est livré avec des [scénarios](https://securitycenter.windows.com/tutorials) d’attaque « Faites-le vous-même » que vous pouvez exécuter sur vos appareils pilotes.  Chaque document inclut les exigences en matière de système d’exploitation et d’application, ainsi que des instructions détaillées propres à un scénario d’attaque. Ces scripts sont sûrs, documentés et faciles à utiliser. Ces scénarios reflèteront les fonctionnalités de Defender for Endpoint et vous feront découvrir l’expérience d’examen.

Pour exécuter l’une des simulations fournies, vous avez besoin d’au moins [un appareil intégré.](../defender-endpoint/onboard-configure.md)

1. Dans **les**  >  **simulations d'& didacticiels,** sélectionnez les scénarios d’attaque disponibles que vous souhaitez simuler :

   - **Scénario 1 : le document abandonne la porte dérobée** : simule la remise d’un document leurre d’ingénierie sociale. Le document lance une porte dérobée spécialement conçue pour donner le contrôle aux attaquants.

   - **Scénario 2** : script PowerShell dans une attaque sans fichier : simule une attaque sans fichier qui s’appuie sur PowerShell, présentant la réduction de la surface d’attaque et la détection de l’apprentissage de l’activité de mémoire malveillante.

   - **Scénario 3 : réponse** automatisée aux incidents : déclenche une enquête automatisée, qui recherche et remédie automatiquement aux artefacts de violation pour mettre à l’échelle votre capacité de réponse aux incidents.

2. Téléchargez et lisez le document de la walkthrough correspondant fourni avec votre scénario sélectionné.

3. Téléchargez le fichier de simulation ou copiez le script de simulation en naviguant vers l’aide  >  **simulations & didacticiels**. Vous pouvez choisir de télécharger le fichier ou le script sur le périphérique de test, mais ce n’est pas obligatoire.

4. Exécutez le fichier ou le script de simulation sur le périphérique de test comme indiqué dans le document pas à pas.

> [!NOTE]
> Les fichiers ou les scripts de simulation imitent l’activité d’attaque, mais sont en réalité anodins et ne compromettent pas ou ne compromettent pas le périphérique de test.

## <a name="next-steps"></a>Étapes suivantes
[Évaluer Microsoft Defender pour les applications cloud](eval-defender-mcas-overview.md)

Revenir à la vue d’ensemble [de l’évaluation de Microsoft Defender pour le point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)
