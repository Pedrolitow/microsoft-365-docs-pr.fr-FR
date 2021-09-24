---
title: Planifier des analyses rapides et complètes régulières avec Antivirus Microsoft Defender
description: Configurer des analyses périodiques (programmées), notamment quand elles doivent s’exécuter et s’ils s’exécutent en tant qu’analyses complètes ou rapides
keywords: analyse rapide, analyse complète, rapide ou complète, analyse de planification, quotidienne, hebdomadaire, heure, programmée, périodique, régulière
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/09/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 255162daf05801e5162fd036e2c4e470b79b38ee
ms.sourcegitcommit: 584445b62cb82218597b62495fb76fcb5b12af9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59498015"
---
# <a name="configure-scheduled-quick-or-full-microsoft-defender-antivirus-scans"></a>Configurer des analyses antivirus Microsoft Defender rapides ou complètes

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Outre les analyses antivirus en temps [](run-scan-microsoft-defender-antivirus.md) réel et toujours en temps réel, vous pouvez configurer des analyses antivirus régulières et programmées. Vous pouvez configurer le type d’analyse, le moment où l’analyse doit se produire et si l’analyse doit se produire après une mise à jour de [la protection](manage-protection-updates-microsoft-defender-antivirus.md) ou lorsqu’un point de terminaison n’est pas utilisé. Vous pouvez également configurer des analyses spéciales pour effectuer des actions de correction si nécessaire.

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

- [En savoir plus sur les analyses rapides, les analyses complètes et les analyses personnalisées](#quick-scan-full-scan-and-custom-scan)
- [Utiliser une stratégie de groupe pour planifier des analyses antivirus](schedule-antivirus-scans-group-policy.md)
- [Utiliser Windows PowerShell pour planifier des analyses antivirus](schedule-antivirus-scans-powershell.md)
- [Utiliser Windows Management Instrumentation pour planifier des analyses antivirus](schedule-antivirus-scans-wmi.md)

## <a name="keep-the-following-points-in-mind"></a>Gardez les points suivants à l’esprit

- Par défaut, Antivirus Microsoft Defender recherche une mise à jour 15 minutes avant l’heure des analyses programmées. Vous pouvez [gérer la planification du téléchargement](manage-protection-update-schedule-microsoft-defender-antivirus.md) et de l’application des mises à jour de la protection pour remplacer cette valeur par défaut.

- Si un appareil est débranché et s’exécute sur batterie pendant une analyse complète programmée, l’analyse programmée s’arrête avec l’événement 1002, qui indique que l’analyse s’est arrêtée avant la fin. Antivirus Microsoft Defender exécutera une analyse complète à l’heure prévue suivante.

## <a name="quick-scan-full-scan-and-custom-scan"></a>Analyse rapide, analyse complète et analyse personnalisée

Lorsque vous définissez des analyses programmées, vous pouvez spécifier si l’analyse doit être complète ou rapide. Dans la plupart des cas, une analyse rapide est recommandée.

<br>

****

|Analyse rapide|Analyse complète|Analyse personnalisée|
|---|---|---|
|(Recommandé) Une analyse rapide examine tous les emplacements où des programmes malveillants peuvent être enregistrés pour démarrer avec le système, tels que les clés de Registre et les dossiers de démarrage Windows connus. <p> Combinée à une protection toujours en temps réel, qui examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur navigue vers un dossier, une analyse rapide permet de fournir une protection forte contre les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. <p> Dans la plupart des cas, une analyse rapide est suffisante et constitue l’option recommandée pour les analyses programmées.|Une analyse complète commence par l’exécution d’une analyse rapide, puis se poursuit avec une analyse séquentielle de tous les disques fixes montés et des lecteurs amovibles/réseau (si l’analyse complète est configurée pour le faire). <p> L’analyse complète peut prendre quelques heures ou jours, en fonction de la quantité et du type de données à analyser. <p> Une fois l’analyse complète terminée, de nouvelles informations de sécurité sont disponibles et une nouvelle analyse est ensuite nécessaire pour s’assurer qu’aucune autre menace n’est détectée avec la nouvelle intelligence de sécurité. <p> En raison du temps et des ressources impliqués dans une analyse complète, en général, Microsoft ne recommande pas la planification d’analyses complètes.|Une analyse personnalisée est une analyse rapide qui s’exécute sur les fichiers et dossiers que vous spécifiez. Par exemple, vous pouvez choisir d’analyser un lecteur USB ou un dossier spécifique sur le lecteur local de votre appareil.|
|

> [!NOTE]
> Par défaut, les analyses rapides s’exécutent sur des appareils amovibles montés, tels que des lecteurs USB.

## <a name="how-do-i-know-which-scan-type-to-choose"></a>Comment savoir quel type d’analyse choisir ?

Utilisez le tableau suivant pour choisir un type d’analyse.

<br>

****

|Scénario|Type d’analyse recommandé|
|---|---|
|Vous souhaitez configurer des analyses régulières et programmées|Analyse rapide <p> Une analyse rapide vérifie les processus, la mémoire, les profils et certains emplacements de l’appareil. Combinée à [une protection en](configure-real-time-protection-microsoft-defender-antivirus.md)temps réel toujours en cours, une analyse rapide permet d’assurer une couverture forte à la fois pour les programmes malveillants qui commencent par le système et les programmes malveillants au niveau du noyau. La protection en temps réel examine les fichiers lorsqu’ils sont ouverts et fermés, et chaque fois qu’un utilisateur navigue vers un dossier.|
|Les menaces, telles que les programmes malveillants, sont détectées sur un appareil individuel|Analyse rapide <p> Dans la plupart des cas, une analyse rapide permet de détecter et de nettoyer les programmes malveillants détectés.|
|Vous souhaitez exécuter une [analyse à la demande](run-scan-microsoft-defender-antivirus.md)|Analyse rapide|
|Vous souhaitez vous assurer qu’un appareil portable, tel qu’un lecteur USB, ne contient pas de programmes malveillants.|Analyse personnalisée <p> Une analyse personnalisée vous permet de sélectionner des emplacements, dossiers ou fichiers spécifiques et exécute une analyse rapide.|
|

## <a name="what-else-do-i-need-to-know-about-quick-and-full-scans"></a>Que dois-je savoir d’autre sur les analyses rapides et complètes ?

- Les fichiers malveillants peuvent être stockés dans des emplacements qui ne sont pas inclus dans une analyse rapide. Toutefois, la protection en temps réel toujours en cours examine tous les fichiers ouverts et fermés, ainsi que tous les fichiers qui se contiennent dans des dossiers accessibles par un utilisateur. La combinaison d’une protection en temps réel et d’une analyse rapide permet de fournir une protection forte contre les programmes malveillants.

- La protection à l’accès avec une protection assurée par le [cloud](cloud-protection-microsoft-defender-antivirus.md) permet de s’assurer que tous les fichiers accessibles sur le système sont analysés avec les derniers modèles d’intelligence de sécurité et d’apprentissage automatique dans le Cloud.

- Lorsque la protection en temps réel détecte des programmes malveillants et que l’étendue des fichiers affectés n’est pas déterminée initialement, Antivirus Microsoft Defender lance une analyse complète dans le cadre du processus de correction.

- Une analyse complète peut détecter des fichiers malveillants qui n’ont pas été détectés par d’autres analyses, telles qu’une analyse rapide. Toutefois, une analyse complète peut prendre un certain temps et utiliser des ressources système précieuses pour se terminer.

- Si un appareil est hors connexion pendant une période prolongée, une analyse complète peut prendre plus de temps.
