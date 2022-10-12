---
title: Antivirus Microsoft Defender dans Windows
description: Découvrez comment gérer, configurer et utiliser l’Antivirus Microsoft Defender, une protection antivirus et un logiciel anti-programme malveillant intégrés.
keywords: Antivirus Microsoft Defender, windows defender, logiciel anti-programme malveillant, scep, system center endpoint protection, system center configuration manager, virus, programme malveillant, menace, détection, protection, sécurité
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.date: 10/03/2022
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: 27d7665fb275531457e90b418a2053fb978d7ead
ms.sourcegitcommit: 8d3c027592a638f411f87d89772dd3d39e92aab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537091"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Antivirus Microsoft Defender dans Windows

**S’applique à :**

- Plans 1 et 2 de Microsoft Defender pour points de terminaison
- Microsoft Defender pour les PME
- Antivirus Microsoft Defender

**Plateformes**
- Windows 

L’Antivirus Microsoft Defender est disponible dans Windows 10 et Windows 11, et dans les versions de Windows Server.

Antivirus Microsoft Defender est un composant majeur de votre protection nouvelle génération dans Microsoft Defender pour point de terminaison. Cette protection regroupe le Machine Learning, l’analyse big data, la recherche approfondie sur la résistance aux menaces et l’infrastructure cloud Microsoft pour protéger les appareils (ou les points de terminaison) de votre organisation. Antivirus Microsoft Defender est intégré à Windows et fonctionne avec Microsoft Defender pour point de terminaison pour fournir une protection sur votre appareil et dans le cloud.

## <a name="compatibility-with-other-antivirus-products"></a>Compatibilité avec d’autres produits antivirus

Si vous utilisez un produit antivirus/anti-programme malveillant non Microsoft sur votre appareil, vous pourrez peut-être exécuter Antivirus Microsoft Defender en mode passif en même temps que la solution antivirus non-Microsoft. Cela dépend du système d’exploitation utilisé et de l’intégration de votre appareil à Defender pour point de terminaison. Pour plus d’informations, consultez [Compatibilité Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Comparaison du mode actif, du mode passif et du mode désactivé

Le tableau suivant décrit à quoi s’attendre lorsque Antivirus Microsoft Defender est en mode actif, passif ou désactivé.

| Mode | Action exécutée |
|---|---|
| Mode actif | En mode actif, Antivirus Microsoft Defender est utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés, les menaces corrigées et les menaces détectées sont répertoriées dans les rapports de sécurité de votre organisation et dans votre application Sécurité Windows. |
| Mode passif | En mode passif, Antivirus Microsoft Defender n’est pas utilisé comme application antivirus principale sur l’appareil. Les fichiers sont analysés et les menaces détectées sont signalées, mais les menaces ne sont pas corrigées par Antivirus Microsoft Defender. <br/><br/> **IMPORTANT** : Microsoft Defender Antivirus peut fonctionner en mode passif uniquement sur les points d'extrémité qui sont intégrés à Microsoft Defender pour point de terminaison. Voir [Configuration requise pour que Microsoft Defender Antivirus fonctionne en mode passif ](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Désactivé ou désinstallé | En cas de désinstallation ou de désinstallation, Antivirus Microsoft Defender n’est pas utilisé. Les fichiers ne sont pas analysés et les menaces ne sont pas corrigées. En général, nous vous déconseillons de désactiver ou de désinstaller Antivirus Microsoft Defender. |

Pour plus d’informations, consultez [Compatibilité Antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Vérifier l’état des Antivirus Microsoft Defender sur votre appareil

Vous pouvez utiliser l’une des différentes méthodes, telles que l’application Sécurité Windows ou Windows PowerShell, pour vérifier l’état de Antivirus Microsoft Defender sur votre appareil.

> [!IMPORTANT]
> À partir de [la plateforme version 4.18.2208.0 et ultérieure](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions) : si un serveur a été intégré à Microsoft Defender pour point de terminaison, le paramètre de stratégie de [groupe](configure-endpoints-gp.md#update-endpoint-protection-configuration) « Désactiver Windows Defender » ne désactive plus complètement Windows Defender Antivirus activé Windows Server 2012 R2 et versions ultérieures. Au lieu de cela, il le place en mode passif. En outre, la fonctionnalité [de protection contre les falsifications](prevent-changes-to-security-settings-with-tamper-protection.md) permet de basculer en mode actif, mais pas en mode passif.
> 
> - Si « Désactiver Windows Defender » est déjà en place avant l’intégration à Microsoft Defender pour point de terminaison, aucune modification n’est apportée et l’antivirus Defender reste désactivé.
> - Pour basculer l’antivirus Defender en mode passif, même s’il a été désactivé avant l’intégration, vous pouvez appliquer la [configuration ForceDefenderPassiveMode](switch-to-mde-phase-2.md#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) avec la valeur .`1` Pour la placer en mode actif, basculez vers cette valeur à la `0` place.
> 
> Notez la logique modifiée pour `ForceDefenderPassiveMode` le moment où la protection contre les falsifications est activée : une fois que Microsoft Defender Antivirus est activé en mode actif, la protection contre les falsifications l’empêche de revenir en mode passif, même lorsque `ForceDefenderPassiveMode` la valeur est définie `1`sur .

### <a name="use-the-windows-security-app-to-check-the-status-of-microsoft-defender-antivirus"></a>Utiliser l’application Sécurité Windows pour vérifier l’état de Antivirus Microsoft Defender

1. Sur votre appareil Windows, sélectionnez le menu **Démarrer** et commencez à taper `Security`. Ouvrez ensuite l’application Sécurité Windows dans les résultats.

2. Sélectionnez **Protection contre les virus et les menaces**.

3. Sous **Qui me protège ?**, choisissez **Gérer les fournisseurs**.

Le nom de votre solution antivirus/anti-programme malveillant apparaît sur la page des paramètres.

### <a name="use-powershell-to-check-the-status-of-microsoft-defender-antivirus"></a>Utiliser PowerShell pour vérifier l’état de Antivirus Microsoft Defender

1. Sélectionnez le menu **Démarrer**, puis commencez à taper `PowerShell`. Ouvrez ensuite Windows PowerShell dans les résultats.

2. Tapez `Get-MpComputerStatus`.

3. Dans la liste des résultats, examinez la ligne **AMRunningMode**.

   - **Normal** signifie que Antivirus Microsoft Defender s’exécute en mode actif.

   - **Le mode passif** signifie Antivirus Microsoft Defender en cours d’exécution, mais n’est pas le produit antivirus/anti-programme malveillant principal sur votre appareil. Le mode passif est uniquement disponible pour les appareils qui sont intégrés à Microsoft Defender pour point de terminaison et qui répondent à certaines exigences. Pour en savoir plus, voir [Configuration requise pour que Microsoft Defender Antivirus fonctionne en mode passif ](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **Le mode de blocage EDR** signifie que Antivirus Microsoft Defender est en cours d’exécution et qu’une fonctionnalité de [Microsoft Defender pour point de terminaison appelée EDR en mode bloc](edr-in-block-mode.md) est activée. Vérifiez la clé de Registre **ForceDefenderPassiveMode** . Si sa valeur est 0, elle s’exécute en mode normal ; sinon, il s’exécute en mode passif.

   - **Le mode passif SxS** signifie Microsoft Defender Antivirus s’exécute en même temps qu’un autre produit antivirus/anti-programme malveillant, et une [analyse périodique limitée est utilisée](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Pour en savoir plus sur l’applet de commande PowerShell Get-MpComputerStatus, consultez l’article de référence [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Obtenir les mises à jour de votre plateforme antivirus/anti-programme malveillant

Il est important de maintenir à jour Antivirus Microsoft Defender (ou toute solution antivirus/anti-programme malveillant). Microsoft publie régulièrement des mises à jour pour vous assurer que vos appareils disposent des dernières technologies pour se protéger contre les nouveaux programmes malveillants et techniques d’attaque. Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Configuration et gestion d’Antivirus Microsoft Defender](configuration-management-reference-microsoft-defender-antivirus.md)
- [Évaluer la protection de l’Antivirus Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
