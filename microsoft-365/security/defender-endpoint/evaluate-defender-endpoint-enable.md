---
title: Évaluation de Pilot Defender for Endpoint
description: Activez votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote.
keywords: Microsoft 365 Defender essai, essayez Microsoft 365 Defender, évaluez Microsoft 365 Defender, laboratoire d’évaluation Microsoft 365 Defender, pilote Microsoft 365 Defender, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4345ac0a2758e87160be83c6abd96cdbaa6822dc
ms.sourcegitcommit: 718759c7146062841f7eb4a0a9a8bdddce0139b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2021
ms.locfileid: "53458189"
---
# <a name="pilot-mde-evaluation"></a>Évaluation MDE pilote

>[!NOTE]
>Pour vous guider tout au long d’un déploiement classique, ce scénario couvre uniquement l’utilisation des Microsoft Endpoint Configuration Manager. Defender pour le point de terminaison prend en charge l’utilisation d’autres outils d’intégration, mais ne couvre pas ces scénarios dans le guide de déploiement. Pour plus d’informations, [voir Onboard devices to Microsoft Defender for Endpoint](onboard-configure.md).

## <a name="step-1-check-license-state"></a>Étape 1. Vérifier l’état de la licence

La vérification de l’état de la licence et si elle a été correctement mise en service peut être effectuée via le Centre d’administration ou via **le portail Microsoft Azure.**

1. Pour afficher vos licences, accédez au portail **Microsoft Azure et** accédez à la section [Microsoft Azure licences du portail.](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products)

   ![Image de la page de gestion des licences Azure](images/atp-licensing-azure-portal.png)

1. Vous pouvez également accéder aux abonnements de facturation dans le Centre  >  **d’administration.**

    Sur l’écran, vous verrez toutes les licences provisionées et leur état **actuel.**

    ![Image des licences de facturation](images/atp-billing-subscriptions.png)

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 2. Intégrer des points de terminaison à l’aide de l’un des outils de gestion pris en charge

La [rubrique Planifier le](deployment-strategy.md) déploiement décrit les étapes générales à suivre pour déployer Defender pour Endpoint.  

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du processus d’intégration et en savoir plus sur les outils et méthodes disponibles.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

Après avoir identifié votre architecture, vous devez choisir la méthode de déploiement à utiliser. L’outil de déploiement que vous choisissez influence la façon dont vous intégrerez les points de terminaison au service.

### <a name="onboarding-tool-options"></a>Options de l’outil d’intégration

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison que vous devez intégrer.

| Point de terminaison     | Options de l’outil                       |
|--------------|------------------------------------------|
| **Windows**  |  [Script local (jusqu’à 10 appareils)](../defender-endpoint/configure-endpoints-script.md) <br> [Stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md) <br> [Microsoft Endpoint Manager/ Gestionnaire de périphériques mobiles](../defender-endpoint/configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md) <br> [Scripts VDI](../defender-endpoint/configure-endpoints-vdi.md) <br> [Intégration à Azure Defender](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender) |
| **MacOS**    | [Scripts locaux](../defender-endpoint/mac-install-manually.md) <br> [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md) <br> [JamF Pro](../defender-endpoint/mac-install-with-jamf.md) <br> [Gestion des appareils mobiles](../defender-endpoint/mac-install-with-other-mdm.md) |
| **Serveur Linux** | [Script local](../defender-endpoint/linux-install-manually.md) <br> [Sondent](../defender-endpoint/linux-install-with-puppet.md) <br> [Ansible](../defender-endpoint/linux-install-with-ansible.md)|
| **iOS**      | [Basée sur l’application](../defender-endpoint/ios-install.md)                                |
| **Android**  | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)               |