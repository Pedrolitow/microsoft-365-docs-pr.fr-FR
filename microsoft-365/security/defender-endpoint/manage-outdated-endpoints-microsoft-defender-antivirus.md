---
title: Appliquer les mises à jour de la protection de Microsoft Defender AV aux points de terminaison hors date
description: Définir quand et comment les mises à jour doivent être appliquées aux points de terminaison qui n’ont pas été mis à jour depuis un certain temps.
keywords: mises à jour, protection, obsolètes, obsolètes, ancien, rattrapage
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 4199f55488ef0dc5989af88e8be83a3d51190d1f
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52275059"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Gérer les mises à jour de l'antivirus Microsoft Defender et les analyses des points de terminaison qui ne sont pas à jour

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Antivirus Microsoft Defender vous permet de définir la durée pendant combien de temps un point de terminaison peut éviter une mise à jour ou le nombre d’analyses qu’il peut manquer avant d’être tenu de se mettre à jour et de s’analyser lui-même. Cela est particulièrement utile dans les environnements où les appareils ne sont pas souvent connectés à un réseau d’entreprise ou externe, ou les appareils qui ne sont pas utilisés quotidiennement.

Par exemple, un employé qui utilise un PC particulier est en pause pendant trois jours et ne se connecte pas à son PC pendant cette période.

Lorsque l’utilisateur revient au travail et se connecte à son PC, Antivirus Microsoft Defender vérifie et télécharge immédiatement les dernières mises à jour de la protection et exécute une analyse.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Configurer des mises à jour de protection de rattrapage pour les points de terminaison qui n’ont pas été mis à jour pendant un certain temps

Si Antivirus Microsoft Defender n’a pas téléchargé les mises à jour de protection pendant une période spécifiée, vous pouvez la configurer pour vérifier et télécharger automatiquement la dernière mise à jour lors de la prochaine connexion. Cela est utile si vous avez désactivé globalement les téléchargements de mises à jour [automatiques au démarrage.](manage-event-based-updates-microsoft-defender-antivirus.md)

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Utiliser Configuration Manager pour configurer des mises à jour de protection de rattrapage

1.  Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant à modifier (cliquez sur Ressources et conformité dans le volet de navigation à gauche, puis développez l’arborescence Vue d’ensemble Endpoint Protection **Stratégies**  >    >  **anti-programme** malveillant)

2.  Go to the **Security intelligence updates** section and configure the following settings:

    1. Définir forcer une mise à jour de l’intelligence de la sécurité si l’ordinateur client est hors connexion pendant plus de deux mises à jour **programmées consécutives** sur **Oui**.
    2. Pour le paramètre If Configuration Manager est utilisé comme source pour les mises à jour d’informations de  **sécurité...**, spécifiez les heures avant lesquelles les mises à jour de protection livrées par Configuration Manager doivent être considérées comme étant hors date. Cela entraîne l’utilisation de l’emplacement de mise à jour suivant, en fonction de l’ordre [de source de base défini.](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)

3. Cliquez sur **OK**.

4.  [Déployez la stratégie mise à jour comme d’habitude.](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers)

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Utiliser la stratégie de groupe pour activer et configurer la fonctionnalité de mise à jour de rattrapage

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Stratégies** **puis Modèles d’administration.**

4. Développez l’arborescence **Windows composants > Antivirus Microsoft Defender > mises à jour des signatures.**

5. Double-cliquez sur **le** paramètre Définir le nombre de jours après lequel une mise à jour de l’intelligence de sécurité de rattrapage est requise et définissez l’option **sur Activé.** Entrez le nombre de jours après lesquels vous souhaitez que Microsoft Defender AV vérifie et télécharge la dernière mise à jour de la protection.

6. Cliquez sur **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Utiliser les cmdlets PowerShell pour configurer les mises à jour de la protection de rattrapage

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, voir utiliser les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour configurer et exécuter des [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Utiliser Windows Management Instruction (WMI) pour configurer des mises à jour de protection de rattrapage

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureUpdateCatchupInterval
```

Pour plus d’informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)


## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Définir le nombre de jours avant que la protection ne soit signalée comme non à jour

Vous pouvez également spécifier le nombre de jours après lesquels la protection Antivirus Microsoft Defender est considérée comme ancienne ou non à jour. Après le nombre de jours spécifié, le client se signale comme étant à jour et affiche une erreur à l’utilisateur du PC. Cela peut également entraîner une tentative de Antivirus Microsoft Defender de télécharger une mise à jour à partir d’autres sources (en fonction de l’ordre de [source](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)de base défini), par exemple lors de l’utilisation de MMPC comme source secondaire après avoir défini WSUS ou Microsoft Update comme première source.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Utiliser une stratégie de groupe pour spécifier le nombre de jours avant que la protection ne soit considérée comme non à jour

1.  Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

3.  Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

4.  Cliquez **sur Stratégies** **puis Modèles d’administration.**

5.  Développez l’arborescence **Windows composants > Antivirus Microsoft Defender > mises** à jour des signatures et configurez les paramètres suivants :

    1.  Double-cliquez sur Définir le nombre de jours avant que les définitions de **logiciels espions** ne soient considérées comme étant à jour et définissez l’option **sur Activé.** Entrez le nombre de jours après lesquels vous souhaitez que Microsoft Defender AV considère les logiciels espions comme étant à jour.

    2. Cliquez sur **OK**.

    3.  Double-cliquez sur Définir le nombre de jours avant que les **définitions de virus** ne soient considérées comme étant à jour et définissez l’option **sur Activé.** Entrez le nombre de jours après lesquels vous souhaitez que l’Antivirus Microsoft Defender considère l’intelligence de sécurité antivirus comme étant à jour.

    4. Cliquez sur **OK**.


## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Configurer des analyses de rattrapage pour les points de terminaison qui n’ont pas été analysés pendant un certain temps

Vous pouvez définir le nombre d’analyses programmées consécutives qui peuvent être manquées avant Antivirus Microsoft Defender forcer une analyse.

Le processus d’activation de cette fonctionnalité est :

1. Configurer au moins une analyse programmée (voir la rubrique Planifier [les analyses).](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
2. Activez la fonctionnalité d’analyse de rattrapage.
3. Définissez le nombre d’analyses qui peuvent être ignorées avant qu’une analyse de rattrapage ne se produise.

Cette fonctionnalité peut être activée pour les analyses complètes et rapides.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Utiliser la stratégie de groupe pour activer et configurer la fonctionnalité d’analyse de rattrapage

1.  Assurez-vous d’avoir installé au moins une analyse programmée.

2.  Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

3.  Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

4.  Cliquez **sur Stratégies** **puis Modèles d’administration.**

5.  Développez l’arborescence **Windows composants > Antivirus Microsoft Defender > scan et** configurez les paramètres suivants :

    1.  Si vous avez installé des analyses rapides programmées, **double-cliquez** sur le paramètre Activer l’analyse rapide de rattrapage et définissez l’option **sur Activé.** 
    2. Si vous avez installé des analyses complètes  programmées, double-cliquez sur le paramètre Activer l’analyse complète de rattrapage et définissez l’option **sur Activé.** Cliquez sur **OK**.
    3. Double-cliquez sur **Définir le nombre** de jours après lequel une analyse de rattrapage est forcée et définissez l’option sur **Activé.** 
    4. Entrez le nombre d’analyses qui peuvent être manquées avant qu’une analyse soit automatiquement exécuté lorsque l’utilisateur se connecte ensuite au PC. Le type d’analyse qui est exécuté est déterminé par la spécification du **type** d’analyse à utiliser pour une analyse programmée (voir la rubrique Planification [des analyses).](scheduled-catch-up-scans-microsoft-defender-antivirus.md) Cliquez sur **OK**.

> [!NOTE]
> Le titre du paramètre de stratégie de groupe fait référence au nombre de jours. Le paramètre, toutefois, est appliqué au nombre d’analyses (et non de jours) avant l’application de l’analyse de rattrapage.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Utiliser les cmdlets PowerShell pour configurer des analyses de rattrapage

Utilisez les cmdlets suivantes :

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, consultez les [cmdlets PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) pour gérer les [cmdlets](/powershell/module/defender/) Antivirus Microsoft Defender et Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Utiliser Windows Management Instruction (WMI) pour configurer des analyses de rattrapage

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Pour plus d’informations et les paramètres autorisés, voir les informations suivantes :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)


### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Utiliser Configuration Manager pour configurer des analyses de rattrapage

1.  Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant à modifier (cliquez sur Ressources et conformité dans le volet de navigation à gauche, puis développez l’arborescence Vue d’ensemble Endpoint Protection **Stratégies**  >    >  **anti-programme** malveillant)

2.  Go to the **Scheduled scans** section and **Force a scan of the selected scan type if client computer is offline...** to **Yes**. 

3. Cliquez sur **OK**.

4.  [Déployez la stratégie mise à jour comme d’habitude.](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers)

## <a name="related-articles"></a>Articles connexes

- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)