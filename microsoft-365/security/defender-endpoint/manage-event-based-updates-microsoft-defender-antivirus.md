---
title: Appliquer Antivirus Microsoft Defender mises à jour après certains événements
description: Gérez la façon dont Antivirus Microsoft Defender applique les mises à jour du renseignement de sécurité après le démarrage ou la réception de rapports de détection fournis par le cloud.
keywords: mises à jour, protection, mises à jour de force, événements, démarrage, recherche des dernières notifications
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 813dfe410a3e6cf198d6d4a36afd6d2987f6d376
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415593"
---
# <a name="manage-event-based-forced-updates"></a>Gérer les mises à jour forcées en fonction des événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Antivirus Microsoft Defender vous permet de déterminer si les mises à jour doivent (ou ne doivent pas) se produire après certains événements, tels qu’au démarrage ou après avoir reçu des rapports spécifiques du service de protection fourni par le cloud.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Rechercher les mises à jour de protection avant d’exécuter une analyse

Vous pouvez utiliser Microsoft Endpoint Configuration Manager, stratégie de groupe, les applets de commande PowerShell et WMI pour forcer Antivirus Microsoft Defender à vérifier et télécharger les mises à jour de protection avant d’exécuter une analyse planifiée.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser Configuration Manager pour rechercher les mises à jour de protection avant d’exécuter une analyse

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant que vous souhaitez modifier (cliquez sur **Ressources et conformité** dans le volet de navigation à gauche, puis développez l’arborescence sur **Vue d’ensemble** \> **Endpoint Protection** \> **stratégies anti-programme malveillant**)

2. Accédez à la section **Analyses planifiées** et **définissez Vérifier les dernières mises à jour du renseignement de sécurité avant d’exécuter une analyse** sur **Oui**.

3. Cliquez sur **OK**.

4. [Déployez la stratégie mise à jour comme d’habitude](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Utilisez stratégie de groupe pour rechercher les mises à jour de protection avant d’exécuter une analyse

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **Analyser**.

5. Double-cliquez sur **Vérifier les dernières définitions de virus et de logiciels espions avant d’exécuter une analyse planifiée et définissez** l’option **sur Activé**.

6. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser les applets de commande PowerShell pour rechercher les mises à jour de protection avant d’exécuter une analyse

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour configurer et exécuter l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [Applets de commande de l’antivirus Defender](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser Windows Management Instruction (WMI) pour rechercher les mises à jour de protection avant d’exécuter une analyse

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
CheckForSignaturesBeforeRunningScan
```

Pour plus d’informations, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>Rechercher les mises à jour de protection au démarrage

Vous pouvez utiliser stratégie de groupe pour forcer Antivirus Microsoft Defender à vérifier et télécharger les mises à jour de protection au démarrage de l’ordinateur.

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **mises à jour du renseignement de sécurité**.

5. Double-cliquez sur **Vérifier les dernières définitions de virus et de logiciels espions au démarrage** et définissez l’option **sur Activé**.

6. Cliquez sur **OK**.

Vous pouvez également utiliser stratégie de groupe, PowerShell ou WMI pour configurer Antivirus Microsoft Defender afin de rechercher des mises à jour au démarrage, même quand elle n’est pas en cours d’exécution.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser stratégie de groupe pour télécharger les mises à jour lorsque Antivirus Microsoft Defender n’est pas présent

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **mises à jour du renseignement de sécurité**.

5. Double-cliquez sur **Lancer la mise à jour du renseignement de sécurité au démarrage** et **définissez** l’option sur Activé.

6. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser les applets de commande PowerShell pour télécharger les mises à jour lorsque Antivirus Microsoft Defender n’est pas présent

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Pour plus d’informations, consultez [Utiliser les applets de commande PowerShell pour gérer Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) et les [applets de commande antivirus Defender](/powershell/module/defender/index) pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser Windows Management Instruction (WMI) pour télécharger les mises à jour lorsque Antivirus Microsoft Defender n’est pas présent

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Pour plus d’informations, consultez [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Autoriser les modifications ad hoc de la protection en fonction de la protection fournie par le cloud

Microsoft Defender AV peut apporter des modifications à sa protection en fonction de la protection fournie par le cloud. Ces modifications peuvent se produire en dehors des mises à jour de protection normales ou planifiées.

Si vous avez activé la protection fournie par le cloud, Microsoft Defender AV envoie des fichiers suspects sur le cloud Windows Defender. Si le service cloud signale que le fichier est malveillant et que le fichier est détecté dans une mise à jour de protection récente, vous pouvez utiliser stratégie de groupe pour configurer Microsoft Defender AV afin de recevoir automatiquement cette mise à jour de protection. D’autres mises à jour de protection importantes peuvent également être appliquées.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Utiliser stratégie de groupe pour télécharger automatiquement les mises à jour récentes en fonction de la protection fournie par le cloud

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. À l’aide de **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **mises à jour du renseignement de sécurité**.

5. Double-cliquez sur **Autoriser les mises à jour du renseignement de sécurité en temps réel en fonction des rapports à Microsoft MAPS** et définissez l’option **sur Activé**. Cliquez ensuite sur **OK**.

6. **Autorisez les notifications à désactiver les rapports basés sur des définitions sur Microsoft MAPS** et définissez l’option **sur Activé**. Cliquez ensuite sur **OK**.

> [!NOTE]
> **Autoriser les notifications à désactiver les rapports basés sur des définitions** permet à Microsoft MAPS de désactiver ces définitions connues pour provoquer des rapports faux positifs. Vous devez configurer votre ordinateur pour qu’il rejoigne Microsoft MAPS pour que cette fonction fonctionne.

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

- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
