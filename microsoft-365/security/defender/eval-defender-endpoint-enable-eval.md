---
title: Activer l’évaluation Microsoft Defender pour point de terminaison
description: Activez votre laboratoire d’essai Microsoft 365 Defender ou votre environnement pilote, notamment la vérification de l’état de la licence et l’intégration des points de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
ms.topic: conceptual
ms.openlocfilehash: d441c2c5d985ebf19a20af68ce9924106b5259c6
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67480380"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>Activer Microsoft Defender pour point de terminaison environnement d’évaluation


Cet article vous guide tout au long des étapes de configuration de l’environnement d’évaluation pour Microsoft Defender pour point de terminaison à l’aide d’appareils de production. 


> [!TIP]
> Microsoft Defender pour point de terminaison est également fourni avec un laboratoire d’évaluation dans le produit où vous pouvez ajouter des appareils préconfigurés et exécuter des simulations pour évaluer les fonctionnalités de la plateforme. Le labo est fourni avec une expérience de configuration simplifiée qui peut vous aider à démontrer rapidement la valeur de Microsoft Defender pour point de terminaison y compris des conseils pour de nombreuses fonctionnalités telles que la chasse avancée et l’analyse des menaces. Pour plus d’informations, consultez [Évaluer les fonctionnalités](../defender-endpoint/evaluation-lab.md). <br> La principale différence entre les instructions fournies dans cet article et le laboratoire d’évaluation est que l’environnement d’évaluation utilise des appareils de production, tandis que le laboratoire d’évaluation utilise des appareils hors production. 

Utilisez les étapes suivantes pour activer l’évaluation de Microsoft Defender pour point de terminaison.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="Étapes permettant d’activer Microsoft Defender pour point de terminaison dans l’environnement d’évaluation Microsoft Defender" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [Étape 1. Vérifier l’état de la licence](#step-1-check-license-state)
- [Étape 2. Intégrer des points de terminaison](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>Étape 1. Vérifier l’état de la licence

Vous devez d’abord vérifier l’état de la licence pour vérifier qu’elle a été correctement approvisionnée. Pour ce faire, vous pouvez utiliser le Centre d’administration ou le **Portail Azure Microsoft**.


1. Pour afficher vos licences, accédez à **Microsoft Portail Azure** et accédez à la [section licence Microsoft Portail Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="Page Licences Azure dans le portail Microsoft 365 Defender" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. Vous pouvez également accéder aux **abonnements** de **facturation** >  dans le Centre d’administration.

    À l’écran, vous verrez toutes les licences approvisionnées et leur **état** actuel.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="Page Licences de facturation dans microsoft Portail Azure" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>Étape 2. Intégrer des points de terminaison à l’aide des outils de gestion pris en charge

Après avoir vérifié que l’état de la licence a été correctement approvisionné, vous pouvez commencer à intégrer des appareils au service. 

Pour évaluer Microsoft Defender pour point de terminaison, nous vous recommandons de choisir deux appareils Windows sur lesquels effectuer l’évaluation.

Vous pouvez choisir d’utiliser l’un des outils de gestion pris en charge, mais Intune fournit une intégration optimale. Pour plus d’informations, consultez [Configurer Microsoft Defender pour point de terminaison dans Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

La rubrique [Planifier le déploiement](../defender-endpoint/deployment-strategy.md) décrit les étapes générales à suivre pour déployer Defender pour point de terminaison.  

Regardez cette vidéo pour obtenir une vue d’ensemble rapide du processus d’intégration et découvrez les outils et méthodes disponibles.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>Options de l’outil d’intégration

Le tableau suivant répertorie les outils disponibles en fonction du point de terminaison à intégrer.

Point de terminaison | Options de l’outil
:---|:---
**Fenêtres** | [Script local (jusqu’à 10 appareils)](../defender-endpoint/configure-endpoints-script.md), [stratégie de groupe](../defender-endpoint/configure-endpoints-gp.md), [Microsoft Endpoint Manager/Mobile Gestionnaire de périphériques](../defender-endpoint/configure-endpoints-mdm.md), [Configuration Manager de point de terminaison Microsoft](../defender-endpoint/configure-endpoints-sccm.md), [scripts VDI](../defender-endpoint/configure-endpoints-vdi.md), [intégration à Microsoft Defender pour le cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)
**MacOS** | [Scripts locaux](../defender-endpoint/mac-install-manually.md), [Microsoft Endpoint Manager](../defender-endpoint/mac-install-with-intune.md), [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md), [Mobile Gestion des appareils](../defender-endpoint/mac-install-with-other-mdm.md)
**Serveur Linux** | [Script local](../defender-endpoint/linux-install-manually.md),  [Puppet](../defender-endpoint/linux-install-with-puppet.md),  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [Basé sur l’application](../defender-endpoint/ios-install.md)
**Android** | [Microsoft Endpoint Manager](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>Étape suivante
[Configurer le pilote pour Microsoft Defender pour point de terminaison](eval-defender-endpoint-pilot.md)
 
Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
