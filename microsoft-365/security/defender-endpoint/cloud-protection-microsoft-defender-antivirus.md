---
title: Protection par le cloud et antivirus Microsoft Defender
description: En savoir plus sur la protection et les Antivirus Microsoft Defender
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, antivirus de nouvelle génération, apprentissage automatique, logiciel anti-programme malveillant, sécurité, defender, cloud, protection cloud
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: shwjha
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 06/03/2021
ms.openlocfilehash: ce54f8205e62b953022fd2518caac058f4f9bab2
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52788798"
---
# <a name="cloud-delivered-protection-and-microsoft-defender-antivirus"></a>Protection par le cloud et antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Les technologies de nouvelle génération Antivirus Microsoft Defender fournissent une protection automatisée et quasi instantanée contre les menaces nouvelles et émergentes. Pour identifier les nouvelles menaces de manière dynamique, les technologies de nouvelle génération fonctionnent avec de grands ensembles de données interconnectées dans le Graph Microsoft Intelligent Security et des systèmes d’intelligence artificielle (IA) puissants pilotés par des modèles d’apprentissage automatique avancés. Antivirus Microsoft Defender utilise plusieurs technologies de détection et de prévention pour offrir une protection précise, en temps réel et intelligente. 

> [!TIP]
> Vous souhaitez en savoir plus ? Consultez le billet de blog, Découvrez les technologies avancées au cœur de Microsoft Defender pour la protection nouvelle génération de [point de terminaison.](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

Antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud de Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, offrant sans doute la meilleure défense antivirus. 

> [!NOTE]
> Le Antivirus Microsoft Defender cloud est un mécanisme permettant de fournir une protection mise à jour à votre réseau et points de terminaison. En tant que service cloud, il ne s’agit pas simplement de la protection des fichiers stockés dans le cloud . Au lieu de cela, le service cloud utilise des ressources distribuées et l’apprentissage automatique pour fournir une protection à vos points de terminaison à un taux beaucoup plus rapide que les mises à jour d’informations de sécurité traditionnelles.

Grâce à la protection fournie par le cloud, les technologies de nouvelle génération permettent d’identifier rapidement les nouvelles menaces, parfois même avant l’infection d’un seul ordinateur. Les billets de blog suivants illustrent le fonctionnement de la protection cloud :

- [Pourquoi Antivirus Microsoft Defender est le plus déployé dans l’entreprise](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 
- [L’analyse du comportement combinée à l’apprentissage automatique a pour effet de sar une campagne massive de minage de pièces](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)
- [Comment l’intelligence artificielle a arrêté une épidémie « Emotet »](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)
- [Détonation d’une mauvaise attaque : Antivirus Microsoft Defender défenses d’apprentissage automatique à plusieurs niveaux](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)
- [Antivirus Microsoft Defender service de protection cloud : défense avancée en temps réel contre les programmes malveillants jamais vus](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 
 
## <a name="how-to-get-cloud-delivered-protection"></a>Comment obtenir une protection cloud 

La protection cloud est activée par défaut. Toutefois, vous devrez peut-être le réactiver s’il a été désactivé dans le cadre des stratégies organisationnelles précédentes. Pour plus d’informations, voir [Activer la protection cloud.](enable-cloud-protection-microsoft-defender-antivirus.md)

Les organisations exécutant Windows 10 E5 peuvent également tirer parti des mises à jour d’urgence de l’intelligence dynamique, qui offrent une protection quasi en temps réel contre les menaces émergentes. Lorsque vous mettez en place la protection cloud, les correctifs aux problèmes de programmes malveillants peuvent être remis via le cloud en quelques minutes, au lieu d’attendre la prochaine mise à jour. Configurez Antivirus Microsoft Defender pour recevoir automatiquement de nouvelles mises à jour de [protection basées sur les rapports de notre service cloud.](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates)

> [!TIP]
> Visitez le site Windows Defender Testground sur [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que la fonctionnalité fonctionne et voir comment elle fonctionne.

## <a name="next-steps"></a>Étapes suivantes

1. [Activer la protection cloud.](enable-cloud-protection-microsoft-defender-antivirus.md) Vous pouvez activer la protection cloud avec Microsoft Endpoint Manager (qui inclut désormais Microsoft Endpoint Configuration Manager et Microsoft Intune), une stratégie de groupe ou des cmdlets PowerShell.

2. [Spécifiez le niveau de protection remis par le cloud.](specify-cloud-protection-level-microsoft-defender-antivirus.md) Vous pouvez spécifier le niveau de protection proposé par le cloud à l’aide de Microsoft Endpoint Manager ou d’une stratégie de groupe. Le niveau de protection affecte la quantité d’informations partagées avec le cloud et le blocage agressif des nouveaux fichiers.

3. [Configurez et validez les connexions réseau pour Antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md). Votre réseau et vos points de terminaison doivent pouvoir se connecter à certaines URL Microsoft pour que la protection cloud fonctionne efficacement. Cet article répertorie les URL qui doivent être autorisées via le pare-feu ou les règles de filtrage réseau, et des instructions pour vérifier que votre réseau est correctement inscrit dans la protection cloud.

4. [Configurez la fonctionnalité « Bloquer à la première vue ».](configure-block-at-first-sight-microsoft-defender-antivirus.md) La fonctionnalité « Bloquer à la première vue » peut bloquer les nouveaux programmes malveillants en quelques secondes, sans avoir à attendre les heures d’attente des renseignements de sécurité traditionnels. Vous pouvez l’activer et le configurer à l’aide Microsoft Endpoint Manager ou d’une stratégie de groupe.

5. [Configurez le délai d’attente du blocage du cloud.](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) Antivirus Microsoft Defender bloquer l’exécution de fichiers suspects pendant qu’il interroge notre service de protection livré par le cloud. Vous pouvez configurer la durée d’empêchement de l’exécution du fichier à l’aide de Microsoft Endpoint Manager ou d’une stratégie de groupe.