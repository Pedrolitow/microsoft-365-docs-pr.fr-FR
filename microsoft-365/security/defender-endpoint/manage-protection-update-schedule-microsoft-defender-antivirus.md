---
title: Planifier les mises à jour de la protection antivirus Microsoft Defender
description: Planifier le jour, l’heure et l’intervalle de téléchargement des mises à jour de protection
keywords: mises à jour, bases de référence de sécurité, planification des mises à jour
ms.service: microsoft-365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.subservice: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 6222ea1102fd57a9cba3cfca5d4f2f8bc90bd20b
ms.sourcegitcommit: 228fa13973bf7c2d91504703fab757f552ae40dd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67521156"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>Gérer le calendrier de téléchargement et d’application des mises à jour de protection

> [!IMPORTANT]
> Les clients qui ont appliqué la mise à jour du moteur Microsoft Defender de mars 2022 (**1.1.19100.5**) ont peut-être rencontré une utilisation élevée des ressources (processeur et/ou mémoire). Microsoft a publié une mise à jour (**1.1.19200.5**) qui résout les bogues introduits dans la version antérieure. Il est recommandé aux clients de mettre à jour cette nouvelle version du moteur antivirus (**1.1.19200.5**). Pour vous assurer que les problèmes de performances sont entièrement résolus, il est recommandé de redémarrer les ordinateurs après l’application de la mise à jour. Pour plus d’informations, consultez [les versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

L’Antivirus Microsoft Defender vous permet de déterminer quand il doit rechercher et télécharger des mises à jour.

Vous pouvez planifier des mises à jour pour vos points de terminaison en :

- Spécification du jour de la semaine pour vérifier les mises à jour de la protection
- Spécification de l’intervalle de vérification des mises à jour de protection
- Spécification du délai de vérification des mises à jour de protection

Vous pouvez également aléatoirement les moments où chaque point de terminaison vérifie et télécharge les mises à jour de protection. Pour plus d’informations, consultez la rubrique [Planifier les analyses](scheduled-catch-up-scans-microsoft-defender-antivirus.md) .

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>Utiliser Configuration Manager pour planifier les mises à jour de protection

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant que vous souhaitez modifier (cliquez sur **Ressources et conformité** dans le volet de navigation à gauche, puis développez l’arborescence sur **Vue d’ensemble** \> des stratégies **anti-programme malveillant** **Endpoint Protection**\>)

2. Accédez à la section **Mises à jour du renseignement de sécurité** .

3. Pour vérifier et télécharger les mises à jour à un moment précis :
      1. **Définissez check for Endpoint Protection security intelligence updates at a specific interval...** to **0**.
      2. **Définissez La vérification des mises à jour du renseignement de sécurité Endpoint Protection quotidiennement au moment** où les mises à jour doivent être vérifiées.
      3
4. Pour vérifier et télécharger les mises à jour sur un intervalle continu, **définissez La vérification des mises à jour du renseignement de sécurité Endpoint Protection à un intervalle spécifique...** sur le nombre d’heures qui doivent se produire entre les mises à jour.

5. [Déployez la stratégie mise à jour comme d’habitude](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>Utiliser stratégie de groupe pour planifier les mises à jour de la protection

> [!IMPORTANT]
> Par défaut, « SignatureScheduleDay » est défini sur « 8 » et « SignatureUpdateInterval » est défini sur « 0 » afin que l’Antivirus Microsoft Defender ne planifie pas les mises à jour de protection.
L’activation de ces paramètres remplace cette valeur par défaut.

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence sur **les composants** \> Windows microsoft **Defender Antivirus** \> **Signature Mises à jour** et configurez les paramètres suivants :

    1. Double-cliquez sur **Spécifier le jour de la semaine pour rechercher le paramètre des mises à jour du renseignement de sécurité** et définissez l’option **sur Activé**. Entrez le jour de la semaine pour rechercher les mises à jour. Cliquez sur **OK**.

    2. Double-cliquez sur **Spécifier l’intervalle pour rechercher le paramètre des mises à jour de définition** et définissez l’option **sur Activé**. Entrez le nombre d’heures entre les mises à jour. Cliquez sur **OK**.

    3. Double-cliquez sur **Spécifier le temps nécessaire pour rechercher le paramètre des mises à jour de définition** et définissez l’option **sur Activé**. Entrez l’heure à laquelle les mises à jour doivent être vérifiées. L’heure est basée sur l’heure locale du point de terminaison. Cliquez sur **OK**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>Utiliser des applets de commande PowerShell pour planifier des mises à jour de protection

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

Pour plus d’informations sur l’utilisation de [PowerShell avec l’antivirus Microsoft Defender, voir Utiliser les applets de commande PowerShell pour configurer et exécuter l’Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)  et [defender](/powershell/module/defender/) .

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>Utiliser l’instruction de gestion Windows (WMI) pour planifier les mises à jour de la protection

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

Pour plus d’informations et les paramètres autorisés, consultez les rubriques suivantes :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)

## <a name="related-articles"></a>Articles connexes

- [Déployer l’antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10 et 11](microsoft-defender-antivirus-in-windows-10.md)
