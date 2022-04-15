---
title: Déployer Microsoft Defender pour point de terminaison en anneaux
description: Découvrez comment déployer des Microsoft Defender pour point de terminaison dans des anneaux
keywords: déployer, anneaux, évaluer, pilote, insider rapide, insider lent, configuration, intégration, phase, déploiement, déploiement, adoption, configuration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e308b1c1d8c26a4ec3d6b3044501ffe1ce92e1c7
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862871"
---
# <a name="deploy-microsoft-defender-for-endpoint-in-rings"></a>Déployer Microsoft Defender pour point de terminaison en anneaux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Le déploiement de Microsoft Defender pour point de terminaison peut être effectué à l’aide d’une approche de déploiement basée sur un anneau.

Les anneaux de déploiement peuvent être appliqués dans les scénarios suivants :

- [Nouveaux déploiements](#new-deployments)
- [Déploiements existants](#existing-deployments)

## <a name="new-deployments"></a>Nouveaux déploiements

:::image type="content" source="images/deployment-rings.png" alt-text="Anneaux de déploiement." lightbox="images/deployment-rings.png":::

Une approche basée sur un anneau est une méthode permettant d’identifier un ensemble de points de terminaison à intégrer et de vérifier que certains critères sont remplis avant de déployer le service sur un plus grand ensemble d’appareils. Vous pouvez définir les critères de sortie pour chaque anneau et vous assurer qu’ils sont satisfaits avant de passer à l’anneau suivant.

L’adoption d’un déploiement en anneau permet de réduire les problèmes potentiels qui peuvent survenir lors du déploiement du service. En pilotant un certain nombre d’appareils en premier, vous pouvez identifier les problèmes potentiels et atténuer les risques potentiels qui peuvent survenir.

Le tableau 1 fournit un exemple des anneaux de déploiement que vous pouvez utiliser.

**Tableau 1** :

|Anneau de déploiement|Description|
|---|---|
|Évaluation|Anneau 1 : Identifier 50 systèmes pour les tests pilotes|
|Pilote|Anneau 2 : Identifier les 50 à 100 points de terminaison suivants dans l’environnement de production|
|Déploiement complet|Anneau 3 : Déployer le service dans le reste de l’environnement par incréments plus importants|

### <a name="exit-criteria"></a>Critères de sortie

Voici un exemple d’ensemble de critères de sortie pour ces anneaux :

- Les appareils s’affichent dans la liste d’inventaire des appareils
- Les alertes s’affichent dans le tableau de bord
- [Exécuter un test de détection](run-detection-test.md)
- [Exécuter une attaque simulée sur un appareil](attack-simulations.md)

### <a name="evaluate"></a>Évaluation

Identifiez un petit nombre de machines de test dans votre environnement à intégrer au service. Dans l’idéal, ces machines auraient moins de 50 points de terminaison.

### <a name="pilot"></a>Pilote

Microsoft Defender pour point de terminaison prend en charge divers points de terminaison que vous pouvez intégrer au service. Dans cet anneau, identifiez plusieurs appareils à intégrer et, en fonction des critères de sortie que vous définissez, décidez de passer à l’anneau de déploiement suivant.

Le tableau suivant présente les points de terminaison pris en charge et l’outil correspondant que vous pouvez utiliser pour intégrer des appareils au service.

|Point de terminaison|Outil de déploiement|
|---|---|
|**Fenêtres**|[Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br> REMARQUE : Si vous souhaitez déployer plus de 10 appareils dans un environnement de production, utilisez plutôt la méthode stratégie de groupe ou les autres outils pris en charge répertoriés ci-dessous.<br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/Mobile Gestionnaire de périphériques](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) <br> [Intégration de à Microsoft Defender pour le cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)|
|**MacOS**|[Script local](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md)|
|**Serveur Linux**|[Script local](linux-install-manually.md) <br> [Marionnette](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Microsoft Endpoint Manager](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

### <a name="full-deployment"></a>Déploiement complet

À ce stade, vous pouvez utiliser le matériel [de déploiement du plan](deployment-strategy.md) pour vous aider à planifier votre déploiement.

Utilisez les éléments suivants pour sélectionner l’architecture Microsoft Defender pour point de terminaison appropriée qui convient le mieux à votre organisation.

|Item|Description|
|---|---|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Stratégie de déploiement Microsoft Defender pour point de terminaison." lightbox="images/mde-deployment-strategy.png":::](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx)|Le matériel architectural vous aide à planifier votre déploiement pour les architectures suivantes : <ul><li> Cloud-natif </li><li> Cogestion </li><li> Sur site</li><li>Évaluation et intégration locale</li></ul>|

## <a name="existing-deployments"></a>Déploiements existants

### <a name="windows-endpoints"></a>points de terminaison Windows

Pour Windows et/ou Windows Serveurs, vous sélectionnez plusieurs machines à tester à l’avance (avant le correctif mardi) à l’aide du **programme de validation des mises à jour de sécurité (SUVP).**

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Qu’est-ce que le programme de validation des mises à jour de sécurité ?](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/what-is-the-security-update-validation-program/ba-p/275767)
- [Programme de validation des mises à jour logicielles et établissement Centre de protection Microsoft contre les programmes malveillants - Chronologie interactive TwC, partie 4](https://www.microsoft.com/security/blog/2012/03/28/software-update-validation-program-and-microsoft-malware-protection-center-establishment-twc-interactive-timeline-part-4/)

### <a name="non-windows-endpoints"></a>Points de terminaison non Windows

Avec macOS et Linux, vous pouvez prendre quelques systèmes et les exécuter dans le canal bêta.

> [!NOTE]
> Dans l’idéal, au moins un administrateur de sécurité et un développeur sont en mesure de trouver des problèmes de compatibilité, de performances et de fiabilité avant que la build n’entre dans le canal Actuel.

Le choix du canal détermine le type et la fréquence des mises à jour proposées à votre appareil. Les appareils en version bêta sont les premiers à recevoir des mises à jour et de nouvelles fonctionnalités, suivis ultérieurement de la préversion et enfin de Current.

:::image type="content" source="images/insider-rings.png" alt-text="Les anneaux insider." lightbox="images/insider-rings.png":::

Pour afficher un aperçu des nouvelles fonctionnalités et fournir des commentaires précoces, il est recommandé de configurer certains appareils de votre entreprise pour qu’ils utilisent la version bêta ou la préversion.

> [!WARNING]
> Le changement de canal après l’installation initiale nécessite la réinstallation du produit. Pour changer de canal de produit : désinstallez le package existant, reconfigurez votre appareil pour utiliser le nouveau canal et suivez les étapes décrites dans ce document pour installer le package à partir du nouvel emplacement.
