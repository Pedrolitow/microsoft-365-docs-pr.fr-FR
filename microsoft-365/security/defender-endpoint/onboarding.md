---
title: Intégrer au service Microsoft Defender pour point de terminaison
description: Découvrez comment intégrer des points de terminaison à Microsoft Defender pour point de terminaison service
keywords: microsoft defender pour point de terminaison, intégrer, déployer
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-endpointprotect
- m365solution-scenario
- m365-initiative-defender-endpoint
- highpri
- tier1
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: d4bb3297fda9f748a17a8d1018a18f71527d9293
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637791"
---
# <a name="onboard-to-the-microsoft-defender-for-endpoint-service"></a>Intégrer au service Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Découvrez les différentes phases de déploiement de Microsoft Defender pour point de terminaison et comment configurer les fonctionnalités au sein de la solution.


Voici les étapes à suivre pour déployer Defender pour point de terminaison :

- Étape 1 : Intégrer des points de terminaison au service
- Étape 2 : Configurer les fonctionnalités

:::image type="content" source="images/deployment-steps.png" alt-text="Étapes de déploiement" lightbox="images/deployment-steps.png":::




## <a name="step-1-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 1 : Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge

La rubrique [Planifier le déploiement](deployment-strategy.md) décrit les étapes générales à suivre pour déployer Defender pour point de terminaison.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du processus d’intégration et découvrez les outils et méthodes disponibles.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Après avoir identifié votre architecture, vous devez choisir la méthode de déploiement à utiliser. L’outil de déploiement que vous choisissez influence la façon dont vous intègrez des points de terminaison au service.

### <a name="onboarding-tool-options"></a>Options de l’outil d’intégration

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison à intégrer.

| Point de terminaison     | Options de l’outil                       |
|--------------|------------------------------------------|
| **Fenêtres**  |  [Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Gestionnaire de périphériques](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](azure-server-integration.md) |
| **MacOS**    | [Scripts locaux](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](linux-install-manually.md) <br> [Marionnette](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
| **iOS**      | [Microsoft Endpoint Manager](ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](android-intune.md)               | 


## <a name="step-2-configure-capabilities"></a>Étape 2 : Configurer les fonctionnalités
Après avoir intégré les points de terminaison, vous allez configurer les fonctionnalités. Le tableau suivant répertorie les composants que vous pouvez configurer. Choisissez les composants que vous souhaitez utiliser et supprimez les composants qui ne s’appliquent pas.

| Fonctionnalité | Description |
|-|-|
| [Endpoint Detection & Response (EDR)](overview-endpoint-detection-response.md) | Les fonctionnalités de détection et de réponse des points de terminaison Defender pour point de terminaison fournissent des détections d’attaque avancées qui sont quasiment en temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces. |
| [Gestion des vulnérabilités Microsoft Defender (MDVM)](next-gen-threat-and-vuln-mgt.md) | La gestion des vulnérabilités Defender est un composant de Microsoft Defender pour point de terminaison et fournit aux administrateurs de la sécurité et aux équipes des opérations de sécurité une valeur unique, notamment : - Des insights en temps réel sur la détection et la réponse des points de terminaison (EDR) corrélés aux vulnérabilités de point de terminaison - Contexte de vulnérabilité d’appareil précieux pendant les enquêtes sur les incidents - Correction intégrée processus via Microsoft Intune et Microsoft System Center Configuration Manager.  |
| [Protection de nouvelle génération (NGP)](microsoft-defender-antivirus-windows.md) | Microsoft Defender Antivirus est une solution anti-programme malveillant intégrée qui fournit une protection de nouvelle génération pour les ordinateurs de bureau, les ordinateurs portables et les serveurs. L’antivirus Microsoft Defender inclut les éléments suivants :<br> <br>- Protection fournie par le cloud pour la détection quasi instantanée et le blocage des menaces nouvelles et émergentes. Tout comme l’apprentissage automatique et le système Intelligent Security Graph, la protection fournie par le cloud fait partie des technologies nouvelle génération intégrées à l’antivirus Microsoft Defender.<br> <br> - Analyse en permanence à l’aide de la surveillance avancée du comportement des fichiers et des processus et d’autres heuristiques (également appelées « protection en temps réel »).<br><br> - Mises à jour de protection dédiées basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, ainsi que la recherche approfondie sur la résistance aux menaces. |
| [Réduction de la surface d’attaque (ASR)](overview-attack-surface-reduction.md) | Les fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison aident à protéger les appareils et les applications de l’organisation contre les menaces nouvelles et émergentes. |
| [Correction d'& d’investigation automatique (AIR)](automated-investigations.md) | Microsoft Defender pour point de terminaison utilise des investigations automatisées pour réduire considérablement le volume d’alertes qui doivent être examinées individuellement. La fonctionnalité d’investigation automatisée utilise différents algorithmes d’inspection et processus utilisés par les analystes (tels que les playbooks) pour examiner les alertes et prendre des mesures de correction immédiates pour résoudre les violations. Cela réduit considérablement les volumes d’alertes, ce qui permet aux experts en matière de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives de grande valeur. |
| [experts Microsoft Defender](microsoft-threat-experts.md) | Microsoft Defender Experts est un service de chasse managé qui fournit aux centres d’opérations de sécurité (SOC) une surveillance et une analyse de niveau expert pour les aider à s’assurer que les menaces critiques dans leurs environnements uniques ne sont pas manquées.      |

Après avoir intégré les points de terminaison, vous allez configurer les différentes fonctionnalités telles que la détection et la réponse des points de terminaison, la protection de nouvelle génération et la réduction de la surface d’attaque.

## <a name="example-deployments"></a>Exemples de déploiements

Dans ce guide de déploiement, nous allons vous guider tout au long de l’utilisation de deux outils de déploiement pour intégrer des points de terminaison et comment configurer des fonctionnalités.

Les outils dans les exemples de déploiements sont les suivants :

- [Intégration à l'aide de Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Intégration à l'aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

À l’aide des outils de déploiement mentionnés ci-dessus, vous serez ensuite guidé dans la configuration des fonctionnalités Defender pour point de terminaison suivantes :

- Détection de point de terminaison et configuration de la réponse
- Configuration de la protection de nouvelle génération
- Configuration de la réduction de la surface d’attaque

## <a name="related-topics"></a>Voir aussi

- [Intégration à l'aide de Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [Intégration à l'aide de Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
- [Documents sécurisés dans Microsoft 365 E5](../office-365-security/safe-docs.md)
