---
title: Évaluation de Pilot Defender for Endpoint
description: Activez votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote.
keywords: Microsoft 365 Defender d’évaluation, essayez Microsoft 365 Defender, évaluez Microsoft 365 Defender, Microsoft 365 Defender laboratoire d’évaluation, Microsoft 365 Defender  pilote, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 39af377ce71cf1ba8e5e19e8fa786ef9498ab96f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61167825"
---
# <a name="pilot-mde-evaluation"></a>Évaluation MDE pilote

**S’applique à :**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!NOTE]
> Pour vous guider tout au long d’un déploiement classique, ce scénario couvre uniquement l’utilisation des Microsoft Endpoint Configuration Manager. Defender pour le point de terminaison prend en charge l’utilisation d’autres outils d’intégration, mais ne couvre pas ces scénarios dans le guide de déploiement. Pour plus d’informations, [voir Appareils intégrés à Microsoft Defender pour le point de terminaison.](onboard-configure.md)

## <a name="step-1-check-license-state"></a>Étape 1. Vérifier l’état de la licence

La vérification de l’état de la licence et si elle a été correctement mise en service peut être effectuée via le Centre d’administration ou via **le portail Microsoft Azure.**

1. Pour afficher vos licences, accédez au portail **Microsoft Azure et** accédez à la section [Microsoft Azure licences du portail.](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products)

   ![Image de la page Gestion des licences Azure.](images/atp-licensing-azure-portal.png)

1. Vous pouvez également accéder aux  abonnements de facturation dans le Centre \> **d’administration.**

    Sur l’écran, vous verrez toutes les licences provisionées et leur état **actuel.**

    ![Image des licences de facturation.](images/atp-billing-subscriptions.png)

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 2. Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge

La [rubrique Planifier le](deployment-strategy.md) déploiement décrit les étapes générales à suivre pour déployer Defender pour Endpoint.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du processus d’intégration et en savoir plus sur les outils et méthodes disponibles.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Après avoir identifié votre architecture, vous devez choisir la méthode de déploiement à utiliser. L’outil de déploiement que vous choisissez influence la façon dont vous intégrerez les points de terminaison au service.

### <a name="onboarding-tool-options"></a>Options de l’outil d’intégration

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison que vous devez intégrer.

<br>

****

|Point de terminaison|Options de l’outil|
|---|---|
|**Fenêtres**|[Script local (jusqu’à 10 appareils)](../defender-endpoint/configure-endpoints-script.md) <p> [Stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md) <p> [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](../defender-endpoint/configure-endpoints-mdm.md) <p> [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md) <p> [Scripts VDI](../defender-endpoint/configure-endpoints-vdi.md) <p> [Intégration de à Microsoft Defender pour le cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender)|
|**MacOS**|[Scripts locaux](../defender-endpoint/mac-install-manually.md) <p> [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md) <p> [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md) <p> [Gestion des appareils mobiles](../defender-endpoint/mac-install-with-other-mdm.md)|
|**Serveur Linux**|[Script local](../defender-endpoint/linux-install-manually.md) <p> [Sondent](../defender-endpoint/linux-install-with-puppet.md) <p> [Ansible](../defender-endpoint/linux-install-with-ansible.md)|
|**iOS**|[Basée sur l’application](../defender-endpoint/ios-install.md)|
|**Android**|[Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)|
|
