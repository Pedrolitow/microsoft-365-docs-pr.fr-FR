---
title: Configurer la correction pour la détection d’antivirus Microsoft Defender
description: Configurer ce que Antivirus Microsoft Defender devez faire lorsqu’il détecte une menace et la durée pendant laquelle les fichiers mis en quarantaine doivent être conservés dans le dossier de quarantaine
keywords: correction, correction, suppression, menaces, quarantaine, analyse, restauration
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 257a3bfc4fc9dcb6353bb158bc3cd4296891ae76
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790149"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Configurer la correction pour la détection d’antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Lorsque Antivirus Microsoft Defender exécute une analyse, elle tente de corriger ou de supprimer les menaces détectées. Vous pouvez configurer la façon dont Antivirus Microsoft Defender devez traiter certaines menaces, si un point de restauration doit être créé avant la correction et quand les menaces doivent être supprimées.

Cet article explique comment configurer ces paramètres à l’aide de stratégie de groupe, mais vous pouvez également utiliser [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) et [Microsoft Intune](/intune/device-restrictions-configure).

Vous pouvez également utiliser [l’applet de commande PowerShell ou la`Set-MpPreference` classe](/powershell/module/defender/set-mppreference) WMI pour configurer ces paramètres.[`MSFT_MpPreference`](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="configure-remediation-options"></a>Configurer les options de correction

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **La configuration de l’ordinateur** et sélectionnez **Modèles d’administration**.

3. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender**.

4. À l’aide du tableau ci-dessous, sélectionnez un emplacement, puis modifiez la stratégie en fonction des besoins.

5. Sélectionnez **OK**.

<br/><br/>

|Emplacement|Paramètre|Description|Paramètre par défaut (s’il n’est pas configuré)|
|---|---|---|---|
|Analyser|Créer un point de restauration système|Un point de restauration système est créé chaque jour avant la tentative de nettoyage ou d’analyse|Désactivé|
|Analyser|Activer la suppression d’éléments du dossier d’historique d’analyse|Spécifier le nombre de jours pendant lesquels les éléments doivent être conservés dans l’historique d’analyse|30 jours|
|Racine|Désactiver la correction de routine|Vous pouvez spécifier si Antivirus Microsoft Defender corrige automatiquement les menaces ou si elle doit demander à l’utilisateur de point de terminaison ce qu’il faut faire.|Désactivé (les menaces sont corrigées automatiquement)|
|Quarantaine|Configurer la suppression d’éléments du dossier De quarantaine|Spécifier le nombre de jours pendant lesquels les éléments doivent être conservés en quarantaine avant d’être supprimés|90 jours|
|Menaces|Spécifier les niveaux d’alerte de menace auxquels l’action par défaut ne doit pas être effectuée lorsqu’elle est détectée|Chaque menace détectée par Antivirus Microsoft Defender se voit attribuer un niveau de menace (faible, moyen, élevé ou grave). Vous pouvez utiliser ce paramètre pour définir la façon dont toutes les menaces pour chacun des niveaux de menace doivent être corrigées (mises en quarantaine, supprimées ou ignorées)|Non applicable|
|Menaces|Spécifier les menaces sur lesquelles l’action par défaut ne doit pas être effectuée lorsqu’elle est détectée|Spécifiez comment corriger des menaces spécifiques (à l’aide de leur ID de menace). Vous pouvez spécifier si la menace spécifique doit être mise en quarantaine, supprimée ou ignorée|Non applicable|

> [!IMPORTANT]
> Antivirus Microsoft Defender détecte et corrige les fichiers en fonction de nombreux facteurs. Parfois, l’exécution d’une correction nécessite un redémarrage. Même si la détection est ultérieurement déterminée comme un faux positif, le redémarrage doit être effectué pour s’assurer que toutes les étapes de correction supplémentaires ont été effectuées.
>
> Si vous êtes certain Antivirus Microsoft Defender mis en quarantaine un fichier en fonction d’un faux positif, vous pouvez restaurer le fichier à partir de la mise en quarantaine après le redémarrage de l’appareil. Consultez [Restaurer les fichiers mis en quarantaine dans Antivirus Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> Pour éviter ce problème à l’avenir, vous pouvez exclure les fichiers des analyses. Consultez [Configurer et valider les exclusions pour les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

Consultez également [Configurer les analyses de Antivirus Microsoft Defender complètes planifiées de correction](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) pour obtenir d’autres paramètres liés à la correction.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Configurer des analyses Antivirus Microsoft Defender planifiées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md)
- [Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
- [Configurer l’interaction Antivirus Microsoft Defender utilisateur final](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et examiner les résultats des analyses et des corrections Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
