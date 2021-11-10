---
title: Planifier des analyses antivirus à l’aide de stratégie de groupe
description: Utiliser une stratégie de groupe pour configurer des analyses antivirus
keywords: analyse rapide, analyse complète, planification, stratégie de groupe, antivirus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 11/10/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 85bd15d4babec45ba368370dc33b3428cc5c1b67
ms.sourcegitcommit: 6722f66915dfe30c3d0ade97b3e9080a9592251b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2021
ms.locfileid: "60899617"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planifier des analyses antivirus à l’aide de stratégie de groupe

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Cet article explique comment configurer des analyses programmées à l’aide de la stratégie de groupe. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, voir Configurer des analyses rapides ou [complètes Antivirus Microsoft Defender planification.](schedule-antivirus-scans.md) 

## <a name="configure-antivirus-scans-using-group-policy"></a>Configurer les analyses antivirus à l’aide de la stratégie de groupe

1. Sur votre ordinateur de gestion des stratégies de groupe, dans l’Éditeur de stratégie de groupe, allez à Modèles d’administration de **configuration** ordinateur \>  \> **Windows composants** \>  \> **Antivirus Microsoft Defender’analyse.**

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis sélectionnez **Modifier.**

3. Spécifiez les paramètres de l’objet de stratégie de groupe, puis sélectionnez **OK**. 

4. Répétez les étapes 1 à 4 pour chaque paramètre à configurer.

5. Déployez votre objet de stratégie de groupe comme vous le faites normalement. Si vous avez besoin d’aide sur les objets de stratégie de groupe, voir [Créer un objet de stratégie de groupe.](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object)

> [!NOTE]
> Lors de la configuration des analyses programmées, le paramètre Démarrer l’analyse programmée uniquement lorsque l’ordinateur est activé mais pas en cours d’utilisation, ce qui est activé par défaut, peut avoir un impact sur l’heure prévue en exigeant que l’ordinateur soit inactif en premier.
>
> Pour les analyses hebdomadaires, le comportement par défaut sur Windows Server consiste à analyser en dehors de la maintenance automatique lorsque l’ordinateur est inactif. La valeur par défaut Windows 10 et ultérieures consiste à analyser pendant la maintenance automatique lorsque l’ordinateur est inactif. Pour modifier ce comportement, modifiez les paramètres en **désactivant ScanOnlyIfIdle,** puis définissez une planification.

Pour plus d’informations, voir Gérer quand les mises à jour de la protection doivent être téléchargées et [appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) et empêcher ou autoriser les utilisateurs à modifier localement les [paramètres](configure-local-policy-overrides-microsoft-defender-antivirus.md) de stratégie.

## <a name="group-policy-settings-for-scheduling-scans"></a>Paramètres de stratégie de groupe pour la planification des analyses

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Spécifier le type d’analyse à utiliser pour une analyse programmée | Analyse rapide |
| Analyser | Spécifier le jour de la semaine pour exécuter une analyse programmée | Spécifiez le jour (ou jamais) d’exécuter une analyse. | Jamais |
| Analyser | Spécifier l’heure de la journée pour exécuter une analyse programmée | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin). | 2 h 00 |
| Root | Randomize scheduled task times |In Antivirus Microsoft Defender, randomize the start time of the scan to any interval from 0 to 23 hours. <p>Dans [SCEP](/mem/intune/protect/certificates-scep-configure), rendre aléatoires les analyses à n’importe quel intervalle plus ou moins 30 minutes. Cela peut être utile dans les machines virtuelles ou les déploiements VDI. | Activé |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>Paramètres de stratégie de groupe pour la planification des analyses lorsqu’un point de terminaison n’est pas utilisé

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Démarrer l’analyse programmée uniquement lorsque l’ordinateur est en cours d’utilisation | Les analyses programmées ne s’exécutent pas, sauf si l’ordinateur est en cours d’utilisation | Activé |

> [!NOTE]
> Lorsque vous programmez des analyses à des moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirez pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>Paramètres de stratégie de groupe pour la planification des analyses requises pour la correction

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|---|---|---|---|
| Correction | Spécifier le jour de la semaine pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le jour (ou jamais) d’exécuter une analyse. | Jamais |
| Correction | Spécifier l’heure de la journée pour exécuter une analyse complète programmée afin de terminer la correction | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>Paramètres de stratégie de groupe pour la planification des analyses quotidiennes

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Spécifier l’intervalle pour exécuter des analyses rapides par jour | Spécifiez le nombre d’heures devant s’écoulée avant la prochaine analyse rapide. Par exemple, pour exécuter toutes les deux heures, entrez **2**, pour une fois par jour, **entrez 24**. Entrez **0 pour** ne jamais exécuter une analyse rapide quotidienne. | Jamais |
| Analyser | Spécifier l’heure d’une analyse rapide quotidienne | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 h 00) | 2 h 00 |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>Paramètres de stratégie de groupe pour la planification des analyses après les mises à jour de la protection

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré)|
|:---|:---|:---|:---|
| Mises à jour des signatures | Activer l’analyse après la mise à jour des informations de sécurité | Une analyse se produit immédiatement après le téléchargement d’une nouvelle mise à jour de la protection | Activé |

