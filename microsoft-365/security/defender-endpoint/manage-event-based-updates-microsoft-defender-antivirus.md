---
title: Appliquer les mises à jour de l'Antivirus Microsoft Defender après certains événements
description: Gérer la façon dont l'Antivirus Microsoft Defender applique les mises à jour de l'intelligence de sécurité après le démarrage ou la réception de rapports de détection remis par le cloud.
keywords: mises à jour, protection, forcer les mises à jour, événements, démarrage, vérifier les dernières mises à jour, notifications
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.openlocfilehash: b9f09878c645d54aadca21fe01749a0e73939c5f
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690435"
---
# <a name="manage-event-based-forced-updates"></a>Gérer les mises à jour forcées basées sur des événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

L'Antivirus Microsoft Defender vous permet de déterminer si des mises à jour doivent (ou ne doivent pas) se produire après certains événements, par exemple au démarrage ou après la réception de rapports spécifiques du service de protection livré par le cloud.

## <a name="check-for-protection-updates-before-running-a-scan"></a>Vérifier les mises à jour de la protection avant d'exécution d'une analyse

Vous pouvez utiliser Microsoft Endpoint Configuration Manager, la stratégie de groupe, les cmdlets PowerShell et WMI pour forcer l'Antivirus Microsoft Defender à vérifier et télécharger les mises à jour de la protection avant d'exécution d'une analyse programmée.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser Configuration Manager pour vérifier les mises à jour de la protection avant d'exécution d'une analyse

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant à modifier (cliquez sur Ressources et conformité dans le volet de navigation sur la gauche, puis développez l'arborescence Vue d'ensemble des **stratégies** anti-programme malveillant  >  **endpoint Protection)**  >  

2. Go to the **Scheduled scans** section and set **Check for the latest security intelligence updates before running a scan** to **Yes**.

3. Cliquez sur **OK**.

4. [Déployez la stratégie mise à jour comme d'habitude.](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers)

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser la stratégie de groupe pour vérifier les mises à jour de la protection avant d'exécution d'une analyse

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Stratégies** **puis Modèles d'administration.**

4. Développez l'arborescence **des composants Windows**  >  **Analyse antivirus Microsoft Defender.**  >  

5. Double-cliquez sur Vérifier les dernières définitions de virus et de **logiciels espions** avant d'exécutez une analyse programmée et définissez l'option **sur Activé.**

6. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser les cmdlets PowerShell pour vérifier les mises à jour de la protection avant d'exécution d'une analyse

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

Pour plus d'informations, voir [Utiliser les cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter l'Antivirus Microsoft Defender et [les cmdlets Defender.](/powershell/module/defender/index)

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>Utiliser Windows Management Instruction (WMI) pour vérifier les mises à jour de la protection avant d'exécution d'une analyse

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
CheckForSignaturesBeforeRunningScan
```

Pour plus d'informations, [voir Windows Defender API WMIv2.](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="check-for-protection-updates-on-startup"></a>Vérifier les mises à jour de la protection au démarrage

Vous pouvez utiliser la stratégie de groupe pour forcer l'Antivirus Microsoft Defender à vérifier et télécharger les mises à jour de la protection lorsque l'ordinateur est démarré.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Stratégies** **puis Modèles d'administration.**

4. Développez l'arborescence des **composants Windows**  >  **microsoft Defender Antivirus** Security Intelligence  >  **Updates.**

5. Double-cliquez sur Vérifier les dernières définitions de virus et de **logiciels espions** au démarrage et définissez l'option **sur Activé.** 

6. Cliquez sur **OK**.

Vous pouvez également utiliser la stratégie de groupe, PowerShell ou WMI pour configurer l'Antivirus Microsoft Defender afin de vérifier les mises à jour au démarrage, même lorsqu'il n'est pas en cours d'exécution.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser la stratégie de groupe pour télécharger les mises à jour lorsque l'Antivirus Microsoft Defender n'est pas présent

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À l'aide **de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Stratégies** **puis Modèles d'administration.**

4. Développez l'arborescence **des composants Windows**  >  **microsoft Defender Antivirus** Security Intelligence  >  **Updates.**

5. Double-cliquez sur **Lancer la mise à jour de l'intelligence** de sécurité au démarrage et définissez l'option sur **Activé.**

6. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser les cmdlets PowerShell pour télécharger les mises à jour lorsque l'Antivirus Microsoft Defender n'est pas présent

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

Pour plus d'informations, consultez les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour gérer l'Antivirus Microsoft Defender et les [cmdlets Defender](/powershell/module/defender/index) pour plus d'informations sur l'utilisation de PowerShell avec l'Antivirus Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>Utiliser Windows Management Instruction (WMI) pour télécharger les mises à jour lorsque l'Antivirus Microsoft Defender n'est pas présent

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

Pour plus d'informations, [voir Windows Defender API WMIv2.](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>Autoriser des modifications ad hoc à la protection basée sur la protection fourni par le cloud

L'Antivirus Microsoft Defender peut apporter des modifications à sa protection en fonction de la protection livrée par le cloud. De telles modifications peuvent se produire en dehors des mises à jour de protection normales ou programmées.

Si vous avez activé la protection cloud, l'Antivirus Microsoft Defender envoie les fichiers qu'il suspecte au cloud Windows Defender cloud. Si le service cloud signale que le fichier est malveillant et qu'il est détecté dans une mise à jour de protection récente, vous pouvez utiliser la stratégie de groupe pour configurer Microsoft Defender AV afin qu'il reçoive automatiquement cette mise à jour de protection. D'autres mises à jour de protection importantes peuvent également être appliquées.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>Utiliser la stratégie de groupe pour télécharger automatiquement les mises à jour récentes en fonction de la protection du cloud

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. À **l'aide de l'Éditeur de gestion des stratégies de** groupe, go to **Computer configuration**.

3. Cliquez **sur Stratégies** **puis Modèles d'administration.**

4. Développez l'arborescence **des composants Windows**  >  **microsoft Defender Antivirus** Security Intelligence  >  **Updates.**

5. Double-cliquez sur Autoriser les mises à jour d'informations de sécurité en temps réel **basées** sur les rapports de Microsoft MAPS et définissez l'option **sur Activé.** Cliquez ensuite sur **OK**.

6. **Autoriser les notifications à désactiver les rapports** basés sur des définitions pour Microsoft MAPS et définir l'option sur **Activé**. Cliquez ensuite sur **OK**.
    
> [!NOTE]
> **Autoriser les notifications à désactiver les** rapports basés sur des définitions permet à Microsoft MAPS de désactiver ces définitions connues pour provoquer des rapports faux positifs. Vous devez configurer votre ordinateur pour qu'il rejoigne Microsoft MAPS pour que cette fonction fonctionne.

## <a name="see-also"></a>Voir aussi

- [Déployer l'Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de l'Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Gérer les mises à jour des points de terminaison qui ne sont pas à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les périphériques mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)