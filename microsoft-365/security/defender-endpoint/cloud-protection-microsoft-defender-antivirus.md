---
title: Protection cloud et Antivirus Microsoft Defender
description: En savoir plus sur la protection cloud et l’antivirus Microsoft Defender
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, av nouvelle génération, machine learning, logiciel anti-programme malveillant, sécurité, defender, cloud, protection cloud
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: e19923d0e41d5c573a0d911550cc0544f4920363
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67468402"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>Protection cloud et Antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Les technologies de nouvelle génération de l’Antivirus Microsoft Defender offrent une protection quasi instantanée et automatisée contre les menaces nouvelles et émergentes. Pour identifier dynamiquement les nouvelles menaces, les technologies de nouvelle génération fonctionnent avec de grands ensembles de données interconnectées dans Microsoft Intelligent Security Graph et de puissants systèmes d’intelligence artificielle (IA) pilotés par des modèles machine learning avancés. La protection cloud fonctionne avec l’antivirus Microsoft Defender pour fournir une protection précise, en temps réel et intelligente. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="Diagramme montrant le fonctionnement de la protection cloud avec l’Antivirus Microsoft Defender" lightbox="images/mde-cloud-protection.png":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Nous vous recommandons de maintenir la protection cloud activée. Pour en savoir plus, consultez [Pourquoi la protection cloud doit être activée pour l’antivirus Microsoft Defender](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>Fonctionnement de la protection cloud

L’antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard. Avec la protection cloud, les technologies de nouvelle génération permettent d’identifier rapidement les nouvelles menaces, parfois même avant qu’un seul point de terminaison ne soit infecté. 

Les billets de blog suivants illustrent le fonctionnement de la protection cloud :

- [Découvrez les technologies avancées au cœur de Microsoft Defender pour point de terminaison protection de nouvelle génération](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [Pourquoi l’Antivirus Microsoft Defender est le plus déployé dans l’entreprise](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [La surveillance du comportement associée à l’apprentissage automatique gâche une campagne d’exploration de pièces massive](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [Comment l’intelligence artificielle a arrêté une épidémie d’emotet](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [Détonation d’un mauvais lapin : Antivirus Microsoft Defender et défenses de Machine Learning en couches](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [Service de protection cloud de l’Antivirus Microsoft Defender : Défense avancée en temps réel contre les programmes malveillants jamais vus](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> Le service cloud antivirus Microsoft Defender est un mécanisme permettant de fournir une protection mise à jour à votre réseau et à vos points de terminaison. En tant que service cloud, il ne s’agit pas simplement d’une protection pour les fichiers stockés dans le cloud ; Au lieu de cela, le service cloud utilise des ressources distribuées et le Machine Learning pour fournir une protection à vos points de terminaison à un rythme beaucoup plus rapide que les mises à jour traditionnelles du renseignement de sécurité.

## <a name="how-to-get-cloud-protection"></a>Comment obtenir la protection cloud 

La protection cloud est activée par défaut. Toutefois, vous devrez peut-être le réactiver s’il a été désactivé dans le cadre des stratégies organisationnelles précédentes. Pour plus d’informations, consultez [Activer la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md).

Si votre abonnement inclut Windows 10 E5, vous pouvez tirer parti des mises à jour dynamiques d’urgence, qui offrent une protection quasiment en temps réel contre les menaces émergentes. Lorsque vous activez la protection cloud, les correctifs pour les problèmes liés aux programmes malveillants peuvent être fournis via le cloud en quelques minutes, au lieu d’attendre la prochaine mise à jour. Consultez [Configurer l’antivirus Microsoft Defender pour recevoir automatiquement de nouvelles mises à jour de protection basées sur les rapports de notre service cloud](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez une vue d’ensemble de la protection cloud dans l’Antivirus Microsoft Defender, voici quelques étapes suivantes :

1. Découvrez [pourquoi la protection cloud doit être activée pour l’antivirus Microsoft Defender](why-cloud-protection-should-be-on-mdav.md).

2. Passez à [Activer la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)