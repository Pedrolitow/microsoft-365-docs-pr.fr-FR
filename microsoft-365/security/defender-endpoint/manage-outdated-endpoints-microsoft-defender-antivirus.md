---
title: Appliquer Antivirus Microsoft Defender mises à jour de protection aux points de terminaison obsolètes
description: Définissez quand et comment les mises à jour doivent être appliquées pour les points de terminaison qui n’ont pas été mis à jour depuis un certain temps.
keywords: mises à jour, protection, obsolète, obsolète, ancien, de rattrapage
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fcf13258b8012bfd2a5875b52b8d844040aee73e
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623490"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>Gérer les mises à jour de l'antivirus Microsoft Defender et les analyses des points de terminaison qui ne sont pas à jour

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**

- Windows

Avec Antivirus Microsoft Defender, votre équipe de sécurité peut définir la durée pendant laquelle un point de terminaison peut éviter une mise à jour ou le nombre d’analyses qu’il peut manquer avant de recevoir la mise à jour et d’exécuter une analyse. Cette fonctionnalité est particulièrement utile dans les environnements où les appareils ne sont pas souvent connectés à un réseau d’entreprise ou externe, ou pour les appareils qui ne sont pas utilisés quotidiennement.

Par exemple, un employé qui utilise un ordinateur particulier prend trois jours de congé et ne se connecte pas à son ordinateur pendant ce temps. Lorsque l’employé retourne au travail et se connecte à son ordinateur, Antivirus Microsoft Defender vérifie et télécharge immédiatement les dernières mises à jour de protection, puis exécute une analyse.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>Configurer des mises à jour de protection de rattrapage pour les points de terminaison qui n’ont pas été mis à jour depuis un certain temps

Si Antivirus Microsoft Defender n’avez pas téléchargé les mises à jour de protection pendant une période spécifiée, vous pouvez la configurer pour vérifier et télécharger automatiquement la dernière mise à jour la prochaine fois qu’une personne se connecte à un point de terminaison. Cette configuration est utile si vous avez [désactivé globalement les téléchargements de mises à jour automatiques au démarrage](manage-event-based-updates-microsoft-defender-antivirus.md).

Vous pouvez utiliser l’une des méthodes suivantes pour configurer les mises à jour de protection de rattrapage :

- [Configuration Manager](#use-configuration-manager-to-configure-catch-up-protection-updates)
- [Stratégie de groupe](#use-group-policy-to-enable-and-configure-the-catch-up-update-feature)
- [Cmdlets PowerShell](#use-powershell-cmdlets-to-configure-catch-up-protection-updates)
- [Windows Management Instruction (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates)

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>Utiliser Configuration Manager pour configurer les mises à jour de la protection contre le rattrapage

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant que vous souhaitez modifier (sélectionnez **Ressources et conformité** dans le volet de navigation à gauche, puis développez l’arborescence sur **Vue d’ensemble** \> **Endpoint Protection** \> **Stratégies anti-programme malveillant**)

2. Accédez à la section **Mises à jour security intelligence** et configurez les paramètres suivants :

    - Définissez **Forcer une mise à jour du renseignement de sécurité si l’ordinateur client est hors connexion pendant plus de deux mises à jour planifiées consécutives** sur **Oui**.
    - Pour le **si Configuration Manager est utilisé comme source pour les mises à jour du renseignement de sécurité...**, spécifiez les heures avant lesquelles les mises à jour de protection fournies par Configuration Manager doivent être considérées comme obsolètes. Ce paramètre entraîne l’utilisation de l’emplacement de mise à jour suivant, en fonction de [l’ordre de source de secours](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) défini.

3. Sélectionnez **OK**.

4. [Déployez la stratégie mise à jour comme d’habitude](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>Utiliser stratégie de groupe pour activer et configurer la fonctionnalité de mise à jour de rattrapage

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Sélectionnez **Stratégies** , puis **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants > Antivirus Microsoft Defender > mises à jour de signature**.

5. Double-cliquez sur **définir le nombre de jours après lesquels une mise à jour du renseignement de sécurité de rattrapage est requise** et définissez l’option **sur Activé**. Entrez le nombre de jours après lesquels vous souhaitez Antivirus Microsoft Defender rechercher et télécharger la dernière mise à jour de protection.

6. Sélectionnez **OK**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>Utiliser des applets de commande PowerShell pour configurer les mises à jour de la protection contre le rattrapage

Utilisez l’applet de commande suivante :

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, consultez les articles suivants :

- [Utiliser des applets de commande PowerShell pour configurer et exécuter Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Applets de commande antivirus Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>Utiliser Windows Management Instruction (WMI) pour configurer les mises à jour de la protection contre le rattrapage

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureUpdateCatchupInterval
```

Pour plus d’informations et les paramètres autorisés, consultez l’article suivant :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>Définir le nombre de jours avant que la protection ne soit signalée comme obsolète

Vous pouvez également spécifier le nombre de jours après lesquels Antivirus Microsoft Defender protection est considérée comme ancienne ou obsolète. Après le nombre de jours spécifié, le client se signale comme « obsolète » et affiche une erreur à l’utilisateur du point de terminaison. Lorsqu’un point de terminaison est considéré comme obsolète, Antivirus Microsoft Defender pouvez tenter de télécharger une mise à jour à partir d’autres sources (en fonction de [l’ordre de source de secours](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) défini).

Vous pouvez utiliser stratégie de groupe pour spécifier le nombre de jours après lesquels endpoint protection est considéré comme obsolète.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>Utilisez stratégie de groupe pour spécifier le nombre de jours avant que la protection ne soit considérée comme obsolète

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Sélectionnez **Stratégies** , puis **Modèles d’administration**.

4. Développez l’arborescence pour **Windows composants > Antivirus Microsoft Defender > mises à jour de signature** et configurez les paramètres suivants :

    1. Double-cliquez sur **Définir le nombre de jours avant que les définitions de logiciels espions ne soient considérées comme obsolètes** et définissez l’option **sur Activé**. Entrez le nombre de jours après lesquels vous souhaitez Antivirus Microsoft Defender considérer que le renseignement de sécurité des logiciels espions est obsolète.

    2. Sélectionnez **OK**.

    3. Double-cliquez sur **Définir le nombre de jours avant que les définitions de virus ne soient considérées comme obsolètes** et définissez l’option **sur Activé**. Entrez le nombre de jours après lesquels vous souhaitez Antivirus Microsoft Defender considérer que le renseignement de sécurité sur les virus est obsolète.

    4. Sélectionnez **OK**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>Configurer des analyses de rattrapage pour les points de terminaison qui n’ont pas été analysés depuis un certain temps

Vous pouvez définir le nombre d’analyses planifiées consécutives qui peuvent être manquées avant que Antivirus Microsoft Defender force une analyse.

Le processus d’activation de cette fonctionnalité est le suivante :

1. Configurez au moins une analyse planifiée (consultez l’article [Analyses planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).

2. Activez la fonctionnalité d’analyse de rattrapage.

3. Définissez le nombre d’analyses qui peuvent être ignorées avant qu’une analyse de rattrapage se produise.

Cette fonctionnalité peut être activée pour les analyses complètes et rapides. 

> [!TIP]
> Nous vous recommandons d’utiliser des analyses rapides pour la plupart des situations. Pour en savoir plus, consultez [Analyse rapide, analyse complète et analyse personnalisée](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan). 

Vous pouvez utiliser l’une des méthodes suivantes pour configurer des analyses de rattrapage :

- [Stratégie de groupe](#use-group-policy-to-enable-and-configure-the-catch-up-scan-feature)
- [Utiliser des applets de commande PowerShell pour configurer des analyses de rattrapage](#use-powershell-cmdlets-to-configure-catch-up-scans)
- [Windows Management Instruction (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-scans)
- [Configuration Manager](#use-configuration-manager-to-configure-catch-up-scans)

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>Utiliser stratégie de groupe pour activer et configurer la fonctionnalité d’analyse de rattrapage

1. Vérifiez que vous avez configuré au moins une analyse planifiée.

2. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

4. Sélectionnez **Stratégies** , puis **Modèles d’administration**.

5. Développez l’arborescence pour **Windows composants > Antivirus Microsoft Defender > Analyser** et configurez les paramètres suivants :

    - Si vous avez configuré des analyses rapides planifiées, double-cliquez sur le paramètre **Activer l’analyse rapide de rattrapage** et définissez l’option **sur Activé**.
    - Si vous avez configuré des analyses complètes planifiées, double-cliquez sur le paramètre **Activer l’analyse complète de rattrapage** et définissez l’option **sur Activé**. Sélectionnez **OK**.
    - Double-cliquez sur **Définir le nombre de jours après lesquels une analyse de rattrapage est forcée** et définissez l’option **sur Activé**.
    - Entrez le nombre d’analyses qui peuvent être manquées avant l’exécution automatique d’une analyse lorsque l’utilisateur se connecte ensuite sur le point de terminaison. Le type d’analyse exécuté est déterminé par le **type d’analyse à utiliser pour une analyse planifiée** (consultez l’article [Planifier les analyses](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). Sélectionnez **OK**.

> [!NOTE]
> Le titre du paramètre stratégie de groupe fait référence au nombre de jours. Toutefois, le paramètre est appliqué au nombre d’analyses (et non aux jours) avant l’exécution de l’analyse de rattrapage.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>Utiliser des applets de commande PowerShell pour configurer des analyses de rattrapage

Utilisez les applets de commande suivantes :

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

Pour plus d’informations sur l’utilisation de PowerShell avec Antivirus Microsoft Defender, consultez les articles suivants :

- [Utiliser des cmdlets PowerShell pour gérer l’antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) 
- [Applets de commande antivirus Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>Utiliser Windows Management Instruction (WMI) pour configurer les analyses de rattrapage

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

Pour plus d’informations et les paramètres autorisés, consultez l’article suivant :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>Utiliser Configuration Manager pour configurer les analyses de rattrapage

1. Sur votre console Microsoft Endpoint Manager, ouvrez la stratégie anti-programme malveillant que vous souhaitez modifier (sélectionnez **Ressources et conformité** dans le volet de navigation à gauche, puis développez l’arborescence sur **Vue d’ensemble** \> **Endpoint Protection** \> **Stratégies anti-programme malveillant**)

2. Accédez à la section **Analyses planifiées** et **forcez une analyse du type d’analyse sélectionné si l’ordinateur client est hors connexion...** sur **Oui**.

3. Sélectionnez **OK**.

4. [Déployez la stratégie mise à jour comme d’habitude](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer le moment où les mises à jour de protection doivent être téléchargées et appliquées](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
