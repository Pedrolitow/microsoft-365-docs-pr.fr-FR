---
title: Pourquoi la protection cloud doit être activée pour l’antivirus Microsoft Defender
description: Découvrez pourquoi la protection cloud doit être activée pour l’antivirus Microsoft Defender. Il aide de nombreuses fonctionnalités de sécurité dans Microsoft Defender pour point de terminaison travail
keywords: Antivirus Microsoft Defender, protection cloud, fonctionnalités de sécurité, soumission d’exemples
search.product: ''
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
ms.date: 10/22/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
search.appverid: met150
ms.openlocfilehash: c999380c35ac8bad59c35fa73d6430f4110ce0a7
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67682578"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Pourquoi la protection cloud doit être activée pour l’antivirus Microsoft Defender

**S’applique à :**

- Antivirus Microsoft Defender
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Plateformes**
- Windows

La protection cloud de l’Antivirus Microsoft Defender vous permet de vous protéger contre les programmes malveillants sur vos points de terminaison et sur votre réseau. Nous vous recommandons de maintenir la protection cloud activée, car certaines fonctionnalités de sécurité dans Microsoft Defender pour point de terminaison fonctionnent uniquement lorsque la protection cloud est activée. 

[![alt-text="Diagramme montrant des éléments qui dépendent de la protection cloud](images/mde-cloud-protection.png#lightbox)](enable-cloud-protection-microsoft-defender-antivirus.md)

Le tableau suivant récapitule les fonctionnalités et fonctionnalités qui dépendent de la protection cloud : <br/><br/>

| Fonctionnalité/fonctionnalité  | Configuration requise pour l’abonnement |  Description  |
|---------|---------|--------|
| Vérification des métadonnées dans le cloud  | Microsoft Defender pour point de terminaison plan 1 ou plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E3 ou E5) | Le service cloud de l’Antivirus Microsoft Defender utilise des modèles Machine Learning comme couche supplémentaire de défense. Ces modèles Machine Learning incluent des métadonnées. Par conséquent, lorsqu’un fichier suspect ou malveillant est détecté, ses métadonnées sont vérifiées. <br/><br/>Pour en savoir plus, consultez [blog : Découvrez les technologies avancées au cœur de Microsoft Defender pour point de terminaison protection de nouvelle génération](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Protection cloud et soumission d’échantillons | Microsoft Defender pour point de terminaison plan 1 ou plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E3 ou E5) | Les fichiers et les exécutables peuvent être envoyés au service cloud antivirus Microsoft Defender à des fins de détonation et d’analyse. <br/><br/>Pour en savoir plus, consultez [la protection cloud et l’exemple de soumission dans l’Antivirus Microsoft Defender](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**REMARQUE** : La soumission automatique d’exemples repose sur la protection cloud, bien qu’elle puisse également être configurée en tant que paramètre autonome.         |
| Protection contre les falsifications | Microsoft Defender pour point de terminaison plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E5) | La protection contre les falsifications vous permet de vous protéger contre les modifications indésirables apportées aux paramètres de sécurité de votre organisation. Pour appliquer la protection contre les falsifications dans le portail Microsoft 365 Defender, la protection cloud doit être activée. <br/><br/>Pour en savoir plus, consultez [Protéger les paramètres de sécurité avec la protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md).        |
| Bloquer à la première consultation | Microsoft Defender pour point de terminaison plan 1 ou plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E3 ou E5) | Bloquer à la première consultation détecte les nouveaux programmes malveillants et les bloque en quelques secondes. Lorsqu’un fichier suspect ou malveillant est détecté, les fonctionnalités de blocage à la première consultation interrogent le serveur principal de protection cloud et appliquent l’heuristique, l’apprentissage automatique et l’analyse automatisée du fichier pour déterminer s’il s’agit d’une menace.<br/><br/>Pour en savoir plus, voir [Qu’est-ce que « bloquer à la première consultation » ?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)   |
| Mises à jour de signature d’urgence | Microsoft Defender pour point de terminaison plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E5) | Lorsque du contenu malveillant est détecté, des mises à jour et des correctifs de signature d’urgence sont déployés. Au lieu d’attendre la prochaine mise à jour régulière, vous pouvez recevoir ces correctifs et mises à jour en quelques minutes.   |
| Détection et réponse de point de terminaison (EDR) en mode bloc | Microsoft Defender pour point de terminaison plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E5) | L’EDR en mode bloc offre une protection supplémentaire lorsque l’antivirus Microsoft Defender n’est pas le produit antivirus principal sur un appareil. L’EDR en mode bloc corrige les artefacts trouvés lors des analyses générées par EDR que la solution antivirus principale non Microsoft a peut-être manquée. Lorsqu’il est activé pour les appareils avec l’Antivirus Microsoft Defender comme solution antivirus principale, EDR en mode bloc offre l’avantage supplémentaire de corriger automatiquement les artefacts identifiés lors des analyses générées par EDR. <br/><br/>Pour en savoir plus, consultez [EDR en mode bloc](edr-in-block-mode.md).|
| Règles de réduction des surfaces d'attaque | Microsoft Defender pour point de terminaison plan 1 ou plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E3 ou E5) | La réduction de la surface d’attaque consiste à réduire les emplacements et les moyens dont les points de terminaison de votre organisation sont vulnérables à une cyberattaque. Les règles de réduction de la surface d’attaque sont des règles intelligentes que vous pouvez configurer pour aider à arrêter les programmes malveillants. Certaines règles nécessitent que la protection cloud soit activée pour fonctionner pleinement. Ces règles sont les suivantes : <br/>- Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de liste approuvée <br/>- Utiliser une protection avancée contre les ransomware <br/>- Empêcher les programmes non approuvés de s’exécuter à partir de lecteurs amovibles <br/><br/>Pour plus d’informations, consultez [Utiliser les règles de réduction de la surface d’attaque pour prévenir l’infection des programmes malveillants](attack-surface-reduction.md).  |
| Indicateurs de compromission | Microsoft Defender pour point de terminaison plan 2 (autonome ou inclus dans un plan comme Microsoft 365 E5) | Les IoCs dans Defender pour point de terminaison peuvent être configurés pour définir la détection, la prévention et l’exclusion des entités. Par exemple, les indicateurs « autoriser » peuvent être utilisés pour définir des exceptions aux analyses et actions de correction de l’Antivirus Microsoft Defender dans Defender pour point de terminaison. Par ailleurs, les indicateurs « alerte et bloc » peuvent être utilisés pour empêcher l’exécution de fichiers ou de processus, et pour suivre ces activités avec des alertes visibles dans le portail Microsoft 365 Defender. <br/><br/>Pour plus d’informations, consultez [Créer des indicateurs](manage-indicators.md).    |

> [!TIP]
> Pour en savoir plus sur les plans Defender pour point de terminaison, consultez [Microsoft Defender pour point de terminaison Plan 1 et Plan 2](defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez une vue d’ensemble de la protection cloud et de son rôle dans l’antivirus Microsoft Defender, voici quelques étapes suivantes :

1. **[Activez la protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md)**. Vous pouvez activer la protection cloud avec Microsoft Endpoint Manager (qui inclut désormais microsoft Endpoint Configuration Manager et Microsoft Intune), stratégie de groupe ou les applets de commande PowerShell.

2. **[Spécifiez le niveau de protection cloud](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Vous pouvez spécifier le niveau de protection offert par le cloud à l’aide de Microsoft Endpoint Manager ou stratégie de groupe. Le niveau de protection affecte la quantité d’informations partagées avec le cloud et la manière dont les nouveaux fichiers sont bloqués de manière agressive.

3. **[Configurez et validez les connexions réseau pour l’antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)**. Il existe certaines URL Microsoft auxquelles votre réseau et vos points de terminaison doivent pouvoir se connecter pour que la protection cloud fonctionne efficacement. Cet article répertorie les URL qui doivent être autorisées par le biais de règles de filtrage de pare-feu ou de réseau, ainsi que des instructions pour confirmer que votre réseau est correctement inscrit dans la protection cloud.

4. **[Configurez la fonctionnalité « bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)** ». La fonctionnalité « bloquer à la première consultation » peut bloquer de nouveaux programmes malveillants en quelques secondes, sans avoir à attendre des heures pour les informations de sécurité traditionnelles. Vous pouvez l’activer et le configurer à l’aide de Microsoft Endpoint Manager ou stratégie de groupe.

5. **[Configurez le délai d’expiration du bloc cloud](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)**. L’Antivirus Microsoft Defender peut empêcher l’exécution de fichiers suspects pendant qu’il interroge notre service de protection cloud. Vous pouvez configurer la durée pendant laquelle le fichier ne sera pas exécuté à l’aide de Microsoft Endpoint Manager ou stratégie de groupe.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)