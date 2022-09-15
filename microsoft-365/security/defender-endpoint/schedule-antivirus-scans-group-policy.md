---
title: Planifier des analyses antivirus à l’aide de stratégie de groupe
description: Utiliser stratégie de groupe pour configurer des analyses antivirus
keywords: analyse rapide, analyse complète, planification, stratégie de groupe, antivirus
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.topic: how-to
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 3e98b12ab84729d6263ecf680ff244c93c208e72
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67704081"
---
# <a name="schedule-antivirus-scans-using-group-policy"></a>Planifier des analyses antivirus à l’aide de stratégie de groupe

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Cet article explique comment configurer des analyses planifiées à l’aide de stratégie de groupe. Pour en savoir plus sur la planification des analyses et sur les types d’analyse, consultez [Configurer les analyses antivirus Microsoft Defender rapides ou complètes planifiées](schedule-antivirus-scans.md). 

## <a name="configure-antivirus-scans-using-group-policy"></a>Configurer des analyses antivirus à l’aide de stratégie de groupe

1. Sur votre machine de gestion stratégie de groupe, dans l’éditeur stratégie de groupe, accédez à **l’analyse** **antivirus** \> Microsoft Defender des **composants** \> \> Windows des modèles **d’administration** de configuration \> de l’ordinateur.

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Spécifiez les paramètres de l’objet stratégie de groupe, puis sélectionnez **OK**. 

4. Répétez les étapes 1 à 4 pour chaque paramètre que vous souhaitez configurer.

5. Déployez votre objet stratégie de groupe comme d’habitude. Si vous avez besoin d’aide sur les objets stratégie de groupe, consultez [Créer un objet stratégie de groupe](/windows/security/threat-protection/windows-firewall/create-a-group-policy-object).

> [!NOTE]
> Lors de la configuration des analyses planifiées, le paramètre **Démarrer l’analyse planifiée uniquement lorsque l’ordinateur est activé mais non utilisé**, ce qui est activé par défaut, peut avoir un impact sur l’heure planifiée attendue en exigeant que l’ordinateur soit d’abord inactif.
>
> Pour les analyses hebdomadaires, le comportement par défaut sur Windows Server consiste à analyser en dehors de la maintenance automatique lorsque l’ordinateur est inactif. La valeur par défaut sur Windows 10 et versions ultérieures consiste à analyser pendant la maintenance automatique lorsque l’ordinateur est inactif. Pour modifier ce comportement, modifiez les paramètres en désactivant **ScanOnlyIfIdle**, puis définissez une planification.

Pour plus d’informations, consultez [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md) , et [Empêcher ou autoriser les utilisateurs à modifier localement les rubriques des paramètres de stratégie](configure-local-policy-overrides-microsoft-defender-antivirus.md) .

## <a name="group-policy-settings-for-scheduling-scans"></a>stratégie de groupe paramètres de planification des analyses

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Spécifier le type d’analyse à utiliser pour une analyse planifiée | Analyse rapide |
| Analyser | Spécifier le jour de la semaine pour exécuter une analyse planifiée | Spécifiez le jour (ou jamais) pour exécuter une analyse. | Jamais |
| Analyser | Spécifier l’heure de la journée d’exécution d’une analyse planifiée | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin). | 2 h du matin |
| Racine | Durées aléatoires des tâches planifiées |Dans l’Antivirus Microsoft Defender, aléatoirez l’heure de début de l’analyse sur un intervalle de 0 à 23 heures. <p>Dans [SCEP](/mem/intune/protect/certificates-scep-configure), les analyses aléatoires à n’importe quel intervalle plus ou moins 30 minutes. Cela peut être utile dans les machines virtuelles ou les déploiements VDI. | Activé |

## <a name="group-policy-settings-for-scheduling-scans-for-when-an-endpoint-is-not-in-use"></a>stratégie de groupe paramètres de planification des analyses lorsqu’un point de terminaison n’est pas utilisé

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Démarrer l’analyse planifiée uniquement lorsque l’ordinateur est activé mais qu’il n’est pas utilisé | Les analyses planifiées ne s’exécutent pas, sauf si l’ordinateur est activé mais qu’il n’est pas en cours d’utilisation | Activé |

> [!NOTE]
> Lorsque vous planifiez des analyses pour les moments où les points de terminaison ne sont pas utilisés, les analyses ne respectent pas la configuration de limitation du processeur et tirent pleinement parti des ressources disponibles pour effectuer l’analyse aussi rapidement que possible.

## <a name="group-policy-settings-for-scheduling-remediation-required-scans"></a>stratégie de groupe paramètres de planification des analyses correctives requises

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|---|---|---|---|
| Assainissement | Spécifier le jour de la semaine pour exécuter une analyse complète planifiée pour terminer la correction | Spécifiez le jour (ou jamais) pour exécuter une analyse. | Jamais |
| Assainissement | Spécifier l’heure de la journée d’exécution d’une analyse complète planifiée pour terminer la correction | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin) | 2 h du matin |

## <a name="group-policy-settings-for-scheduling-daily-scans"></a>stratégie de groupe paramètres de planification des analyses quotidiennes

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
| Analyser | Spécifier l’intervalle pour exécuter des analyses rapides par jour | Spécifiez le nombre d’heures qui doivent s’écouler avant la prochaine analyse rapide. Par exemple, pour exécuter toutes les deux heures, entrez **2**, pour une fois par jour, entrez **24**. Entrez **0** pour ne jamais exécuter une analyse rapide quotidienne. | Jamais |
| Analyser | Spécifier l’heure d’une analyse rapide quotidienne | Spécifiez le nombre de minutes après minuit (par exemple, entrez **60** pour 1 heure du matin) | 2 h du matin |

## <a name="group-policy-settings-for-scheduling-scans-after-protection-updates"></a>stratégie de groupe paramètres de planification des analyses après les mises à jour de protection

| Emplacement | Setting | Description | Paramètre par défaut (s’il n’est pas configuré)|
|:---|:---|:---|:---|
| Mises à jour des signatures | Activer l’analyse après la mise à jour du renseignement de sécurité | Une analyse se produit immédiatement après le téléchargement d’une nouvelle mise à jour de la protection | Activé |

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)