---
title: Pourquoi la protection cloud doit-elle être activée pour Antivirus Microsoft Defender
description: Découvrez pourquoi la protection cloud doit être Antivirus Microsoft Defender. Il aide à travailler sur de nombreuses fonctionnalités de sécurité dans Microsoft Defender pour le point de terminaison
keywords: Antivirus Microsoft Defender, protection cloud, fonctionnalités de sécurité, soumission d’exemples
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 09/21/2021
ms.openlocfilehash: 0f0937ef59b74ea30f673aa1d05c4b75e3e5bbcc
ms.sourcegitcommit: b295c60d5aa69781a20c59b9cdf2ed91c62b21af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2021
ms.locfileid: "59480783"
---
# <a name="why-cloud-protection-should-be-enabled-for-microsoft-defender-antivirus"></a>Pourquoi la protection cloud doit-elle être activée pour Antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Antivirus Microsoft Defender protection cloud permet de se protéger contre les programmes malveillants sur vos points de terminaison et sur votre réseau. Nous vous recommandons de maintenir la protection cloud activée, car certaines fonctionnalités de sécurité dans Microsoft Defender pour le point de terminaison fonctionnent uniquement lorsque la protection cloud est activée. 

[:::image type="content" source="mde-cloud-protection.png" alt-text="Diagramme montrant comment la protection cloud fonctionne avec Antivirus Microsoft Defender":::](enable-cloud-protection-microsoft-defender-antivirus.md)

Le tableau suivant récapitule les fonctionnalités et fonctionnalités qui dépendent de la protection cloud : <br/><br/>

| Fonctionnalité/fonctionnalité  | Abonnement |  Description  |
|---------|---------|--------|
| Vérification des métadonnées dans le cloud  | Microsoft 365 E5 ou E3 | Le service Antivirus Microsoft Defender cloud utilise des modèles d’apprentissage automatique comme couche de défense supplémentaire. Ces modèles d’apprentissage automatique incluent des métadonnées. Ainsi, lorsqu’un fichier suspect ou malveillant est détecté, ses métadonnées sont vérifiées. <br/><br/>Pour en savoir plus, consultez le blog : Découvrir les technologies avancées au cœur de la protection nouvelle génération de [Microsoft Defender pour Endpoint](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)  |
| Protection cloud et soumission d’échantillons | Microsoft 365 E5 ou E3 | Les fichiers et les fichiers exécutables peuvent être envoyés au service cloud Antivirus Microsoft Defender pour détonation et analyse. <br/><br/>Pour plus d’informations, voir [Protection cloud et soumission d’exemples dans Antivirus Microsoft Defender](cloud-protection-microsoft-antivirus-sample-submission.md).<br/><br/>**REMARQUE**: l’envoi automatique d’échantillons repose sur la protection cloud, bien qu’elle puisse également être configurée en tant que paramètre autonome.         |
| Protection contre la falsification | Microsoft 365 E5 | La protection contre la falsification permet de se protéger contre les modifications indésirables apportées aux paramètres de sécurité de votre organisation. Pour appliquer la protection contre la falsification dans le portail Microsoft 365 Defender, la protection cloud doit être activée. <br/><br/>Pour plus d’informations, voir [Protéger les paramètres de sécurité avec la protection contre la falsification.](prevent-changes-to-security-settings-with-tamper-protection.md)        |
| Bloquer à la première consultation | Microsoft 365 E5 ou E3 | Bloquer à la première vue détecte de nouveaux programmes malveillants et les bloque en quelques secondes. Lorsqu’un fichier suspect ou malveillant est détecté, les fonctionnalités bloquer à la première vue interrogent le système de protection cloud et appliquent des heuristiques, l’apprentissage automatique et une analyse automatisée du fichier pour déterminer s’il s’agit d’une menace.<br/><br/>Pour en savoir plus, [voir qu’est-ce que « bloquer à la première vue](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)» ?   |
| Mises à jour des signatures d’urgence | Microsoft 365 E5 | Lorsque du contenu malveillant est détecté, des correctifs et des mises à jour de signature d’urgence sont déployés. Au lieu d’attendre la prochaine mise à jour régulière, vous pouvez recevoir ces correctifs et mises à jour en quelques minutes.   |
| Détection et réponse de point de terminaison (EDR) en mode bloc | Microsoft 365 E5 | PEPT mode blocage offre une protection supplémentaire lorsque Antivirus Microsoft Defender n’est pas le produit antivirus principal sur un appareil. PEPT en mode blocage remédie aux artefacts trouvés pendant les analyses générées PEPT générées que la solution antivirus principale autre que Microsoft a peut-être manquées. Lorsqu’elle est activée pour les appareils avec Antivirus Microsoft Defender comme solution antivirus principale, PEPT en mode blocage offre l’avantage de corriger automatiquement les artefacts identifiés lors des analyses générées par PEPT. <br/><br/>Pour plus d’informations, [voir PEPT en mode bloc.](edr-in-block-mode.md)|
| Règles de réduction de la surface d’attaque | Microsoft 365 E5 ou E3 | La réduction de la surface d’attaque consiste à réduire les lieux et les moyens dont les points de terminaison de votre organisation sont vulnérables à une cyberattaque. Les règles de réduction de la surface d’attaque sont des règles intelligentes que vous pouvez configurer pour aider à arrêter les programmes malveillants. Certaines règles exigent que la protection cloud soit allumée pour fonctionner entièrement. Ces règles sont les suivantes : <br/>- Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à des critères de prévalence, d’âge ou de listes fiables <br/>- Utiliser la protection avancée contre les ransomware <br/>- Bloquer l’exécution de programmes nontrus à partir de lecteurs amovibles <br/><br/>Pour plus d’informations, voir Utiliser les règles de réduction [de la surface d’attaque pour empêcher l’infection par des programmes malveillants.](attack-surface-reduction.md)  |
| Indicateurs de compromis (IOC) | Microsoft 365 E5  | Les IoCs dans Defender pour point de terminaison peuvent être configurés pour définir la détection, la prévention et l’exclusion des entités. Par exemple, les indicateurs « autoriser » peuvent être utilisés pour définir des exceptions pour Antivirus Microsoft Defender analyses et des actions de correction dans Defender for Endpoint. Autre exemple , les indicateurs « alerte et blocage » peuvent être utilisés pour empêcher l’exécution de fichiers ou de processus, et pour suivre ces activités avec des alertes qui sont consultables dans le portail Microsoft 365 Defender. <br/><br/>Pour plus d’informations, voir [Créer des indicateurs.](manage-indicators.md)    |


## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez une vue d’ensemble de la protection cloud et de son rôle dans Antivirus Microsoft Defender, voici quelques étapes suivantes :

1. **[Activer la protection cloud.](enable-cloud-protection-microsoft-defender-antivirus.md)** Vous pouvez activer la protection cloud avec Microsoft Endpoint Manager (qui inclut désormais Microsoft Endpoint Configuration Manager et Microsoft Intune), une stratégie de groupe ou des cmdlets PowerShell.

2. **[Spécifiez le niveau de protection cloud](specify-cloud-protection-level-microsoft-defender-antivirus.md)**. Vous pouvez spécifier le niveau de protection proposé par le cloud à l’aide de Microsoft Endpoint Manager ou d’une stratégie de groupe. Le niveau de protection affecte la quantité d’informations partagées avec le cloud et le blocage agressif des nouveaux fichiers.

3. **[Configurez et validez les connexions réseau pour Antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md)**. Votre réseau et vos points de terminaison doivent pouvoir se connecter à certaines URL Microsoft pour que la protection cloud fonctionne efficacement. Cet article répertorie les URL qui doivent être autorisées via le pare-feu ou les règles de filtrage réseau, et des instructions pour vérifier que votre réseau est correctement inscrit dans la protection cloud.

4. **[Configurez la fonctionnalité « Bloquer à la première vue ».](configure-block-at-first-sight-microsoft-defender-antivirus.md)** La fonctionnalité « Bloquer à la première vue » peut bloquer les nouveaux programmes malveillants en quelques secondes, sans avoir à attendre les heures d’attente des renseignements de sécurité traditionnels. Vous pouvez l’activer et le configurer à l’aide Microsoft Endpoint Manager ou d’une stratégie de groupe.

5. **[Configurez le délai d’attente du blocage du cloud.](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)** Antivirus Microsoft Defender bloquer l’exécution de fichiers suspects pendant qu’il interroge notre service de protection cloud. Vous pouvez configurer la durée d’empêchement de l’exécution du fichier à l’aide de Microsoft Endpoint Manager ou d’une stratégie de groupe.
