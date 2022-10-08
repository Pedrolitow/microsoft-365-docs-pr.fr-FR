---
title: Planifier le déploiement de Microsoft Defender pour point de terminaison
description: Sélectionner la meilleure stratégie de déploiement Microsoft Defender pour point de terminaison pour votre environnement
keywords: deploy, plan, deployment strategy, cloud native, management, on prem, evaluation, onboarding, local, group policy, gp, endpoint manager, mem
search.product: eADQiWindows 10XVcnh
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
- tier1
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: cf22bb16d4275ef195fa01377fb9b791b4cad90e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68180228"
---
# <a name="plan-your-microsoft-defender-for-endpoint-deployment"></a>Planifier le déploiement de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

Planifiez votre déploiement Microsoft Defender pour point de terminaison afin de maximiser les fonctionnalités de sécurité au sein de la suite et de mieux protéger votre entreprise contre les cybermenaces.

Cette solution fournit des conseils sur la façon d’identifier l’architecture de votre environnement, de sélectionner le type d’outil de déploiement qui répond le mieux à vos besoins, ainsi que des conseils sur la configuration des fonctionnalités.

:::image type="content" source="images/deployment-guide-plan.png" alt-text="Flux de déploiement" lightbox="images/deployment-guide-plan.png":::

## <a name="step-1-identify-architecture"></a>Étape 1 : Identifier l’architecture

Nous comprenons que chaque environnement d’entreprise est unique, nous avons donc fourni plusieurs options pour vous donner la flexibilité de choisir comment déployer le service.

Selon votre environnement, certains outils conviennent mieux à certaines architectures.

Utilisez le matériel suivant pour sélectionner l’architecture Defender pour point de terminaison appropriée qui convient le mieux à votre organisation.

| Élément | Description |
|:-----|:-----|
|[:::image type="content" source="images/mde-deployment-strategy.png" alt-text="Stratégie de déploiement de Defender pour point de terminaison" lightbox="images/mde-deployment-strategy.png":::](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)<br/> [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf)  \| [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) | Le matériel architectural vous aide à planifier votre déploiement pour les architectures suivantes : <ul><li> Cloud-natif </li><li> Cogestion </li><li> Sur site</li><li>Évaluation et intégration locale</li>

## <a name="step-2-select-deployment-method"></a>Étape 2 : Sélectionner la méthode de déploiement

Le tableau suivant répertorie les points de terminaison pris en charge et l’outil de déploiement correspondant que vous pouvez utiliser pour planifier le déploiement de manière appropriée.

|Point de terminaison|Outil de déploiement|
|---|---|
|**Fenêtres**|[Script local (jusqu’à 10 appareils)](configure-endpoints-script.md) <br>  [Stratégie de groupe](configure-endpoints-gp.md) <br>  [Microsoft Endpoint Manager/ Mobile Gestionnaire de périphériques](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [Scripts VDI](configure-endpoints-vdi.md) |
|**MacOS**|[Script local](mac-install-manually.md) <br> [Microsoft Endpoint Manager](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](mac-install-with-other-mdm.md)|
|**Serveur Linux**|[Script local](linux-install-manually.md) <br> [Marionnette](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md)|
|**iOS**|[Basé sur l’application](ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](android-intune.md)|

## <a name="step-3-configure-capabilities"></a>Étape 3 : Configurer les fonctionnalités

Après l’intégration des points de terminaison, configurez les fonctionnalités de sécurité dans Defender pour point de terminaison afin de maximiser la protection de sécurité robuste disponible dans la suite. Les fonctionnalités incluent :

- Détection et réponse du point de terminaison
- Protection de nouvelle génération
- Réduction de la surface d'attaque

## <a name="related-topics"></a>Voir aussi

- [Phases de déploiement](deployment-phases.md)
